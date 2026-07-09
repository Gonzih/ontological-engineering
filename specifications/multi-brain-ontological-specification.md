# Multi-Brain Ontological Specification

Project observed: `/Users/feral/cc-discord-workspace/multi-brain`

Repository version observed: local working tree with untracked Rust crate files; package version `0.1.3`.

## 1. Purpose

`multi-brain` is an operating substrate for long-lived AI-agent harnesses. It provides a Rust daemon, CLI, and MCP server that let agent processes be registered, spawned, inspected, messaged, observed, stopped, and exposed to other agent workspaces without interactive prompts.

Ontologically, the project is not just a process supervisor. It is a registry and communication bus for named agent identities. It creates a shared world where separate AI harnesses can become discoverable actors with persistent configuration, runtime state, message history, event history, and MCP-callable affordances.

The central design question:

How should multiple AI agent harnesses exist as durable, addressable, observable, and governable actors inside a local development environment?

## 2. System Boundary

Inside scope:

- persistent registry of harness configurations
- daemon process that owns the live bus
- Unix socket request/response protocol
- CLI command surface
- MCP stdio server surface
- harness spawning and stopping
- message delivery to harness stdin
- structured JSONL event logs
- MCP injection into other repositories
- state and log storage under `MULTI_BRAIN_HOME` or platform data directory

Outside current scope:

- semantic interpretation of agent output
- task routing or planning intelligence
- automatic consensus between agents
- permissioned multi-user access control
- remote/networked daemon operation
- durable process resurrection after daemon restart
- typed epistemic status of agent claims
- knowledge promotion into an organizational memory system

## 3. Core Ontology

### Multi-Brain Registry

The registry is the persistent memory of known harnesses and messages. In code it is represented by `State` in `src/state.rs`, persisted as `state.json`.

Properties:

- contains `StoredHarness` records indexed by harness name
- contains `Message` records
- survives CLI/MCP request boundaries
- does not itself own live processes

Ontological role: canonical local memory of configured brains and cross-brain messages.

### Daemon

The daemon is the runtime authority. It owns:

- exclusive lock file
- Unix socket
- in-memory process table
- loaded registry state
- request handling
- harness spawning/stopping
- message delivery
- MCP config injection

Ontological role: the active governor of the local multi-brain world.

Important distinction: the registry remembers configured brains; the daemon knows which brains are currently alive.

### Harness Config

`HarnessConfig` is the durable specification for how to create a brain.

Fields:

- `name`
- `kind`
- `command`
- `args`
- `cwd`
- `personality`
- `env`

Ontological role: declarative recipe for an agent harness.

The config is not the running brain. It is the instruction set for creating one.

### Stored Harness

`StoredHarness` pairs a stable `id` with a `HarnessConfig`.

Ontological role: persistent identity binding for a configured brain.

The stable ID lets a harness keep identity across config updates, while the name remains the operational address used by CLI/MCP requests.

### Running Harness

`RunningHarness` is a live child process controlled by the daemon.

Properties:

- name
- child process
- stdin handle
- log path
- process ID
- liveness state

Ontological role: runtime embodiment of a stored harness.

Important distinction: a running harness is ephemeral. It can die, be stopped, or be replaced while its stored harness remains registered.

### Harness Kind

`HarnessKind` defines launch semantics.

Current kinds:

- `claude`
- `codex`
- `open_claw`
- `generic`

Ontological role: adapter type that maps a general harness config into concrete command arguments.

Examples:

- `claude` injects stream-json input/output flags and optional system prompt.
- `codex` launches through `codex exec <personality> --full-auto`.
- `open_claw` and `generic` pass line-oriented arguments through directly.

### Personality

The personality is the behavioral prompt or identity instruction used to shape a harness.

Ontological role: agent role specification.

The personality is currently stored as raw text and passed differently by harness kind. It is not yet versioned, structured, or linked to provenance.

### Message

`Message` records an intentional communication between named brains.

Fields:

- `from`
- `to`
- `body`
- `at_unix_ms`

Ontological role: durable trace of a cross-brain request.

Important distinction: `Message` records the social act of asking; `HarnessEvent` records process-level IO. A message may correspond to a stdin event, but they are not the same object.

### Harness Event

`HarnessEvent` records line-oriented process activity.

Fields:

- `harness`
- `stream`
- `line`
- `at_unix_ms`

Event streams:

- `stdin`
- `stdout`
- `stderr`
- `status`

Ontological role: observable runtime trace.

Events are written to per-harness JSONL logs and retrieved through CLI/MCP.

### Request

`Request` is a command sent to the daemon over the Unix socket.

Current requests:

- `Ping`
- `Register`
- `Spawn`
- `Ensure`
- `List`
- `Ask`
- `Messages`
- `Events`
- `InjectMcp`
- `Stop`

Ontological role: operational intention addressed to the daemon.

### Response

`Response` is the daemon's structured result.

Current responses:

- `Pong`
- `Registered`
- `Spawned`
- `List`
- `Asked`
- `Messages`
- `Events`
- `InjectedMcp`
- `Stopped`
- `Error`

Ontological role: authoritative report of request outcome.

### MCP Server

The MCP server is an agent-facing tool interface over the same daemon protocol.

Tools:

- `list_brains`
- `register_brain`
- `spawn_brain`
- `ensure_brain`
- `ask_brain`
- `brain_events`
- `inject_multi_brain_mcp`
- `stop_brain`

Ontological role: externalized agency surface. It lets other AI agents discover and manipulate the multi-brain world as tools.

### MCP Injection

MCP injection writes a `.mcp.json` entry into another repository, pointing that workspace back to the same global daemon through `MULTI_BRAIN_HOME`.

Ontological role: propagation of the multi-brain affordance into an agent workspace.

This is how spawned or external harnesses become able to discover and communicate with the same registry.

## 4. Identity Model

`multi-brain` uses several identity layers:

- stable harness ID: UUID generated at first registration
- harness name: human-readable operational address
- process ID: OS-level runtime identity
- log path: observable trace identity
- MCP server name: workspace-level tool identity

Identity rules:

- harness name is the key in persistent state
- re-registering an existing name preserves the stored ID
- changing config does not create a new identity
- spawning creates or reuses a running process for the named harness
- process ID is not durable identity
- messages address names, not IDs

Design implication: `name` currently carries too much operational importance. Future versions may need explicit rename semantics or ID-addressed operations.

## 5. Lifecycle Model

### Registered

A harness config exists in state.

Created by:

- CLI `register`
- CLI `ensure`
- MCP `register_brain`
- MCP `ensure_brain`

State:

- has stored ID
- has config
- may or may not be alive

### Spawned

A running child process exists for a registered harness.

Created by:

- CLI `spawn`
- CLI `ensure`
- MCP `spawn_brain`
- MCP `ensure_brain`

State:

- process exists in daemon process table
- stdout/stderr are captured
- stdin may be writable
- status event `started` is appended

### Alive

A running harness has not exited according to `try_wait`.

Observed through:

- CLI `list`
- MCP `list_brains`

### Messaged

A body is written to the running harness stdin.

Created by:

- CLI `ask`
- MCP `ask_brain`

Effects:

- writes line to harness stdin
- appends `stdin` event
- appends durable `Message` to state

Failure mode:

- target harness must be running
- closed stdin produces an error

### Observed

Recent events are read from per-harness JSONL log.

Created by:

- CLI `events`
- MCP `brain_events`

Observation is read-only and does not change state.

### Stopped

Daemon kills the child process and removes it from the process table.

Created by:

- CLI `stop`
- MCP `stop_brain`

Effects:

- attempts child kill
- appends status event `stopped`
- persistent harness config remains registered

### Forgotten

There is currently no explicit unregister/delete lifecycle state.

Design implication: the ontology has registration and stopping but lacks archival, deletion, deprecation, or retirement semantics.

## 6. Relationship Model

Core relationships:

- `Daemon owns ProcessTable`
- `Daemon loads State`
- `State contains StoredHarness`
- `StoredHarness has HarnessConfig`
- `HarnessConfig instantiates RunningHarness`
- `RunningHarness emits HarnessEvent`
- `RunningHarness receives Message body through stdin`
- `Message addresses from HarnessName to HarnessName`
- `CLI command translates to Request`
- `MCP tool translates to Request`
- `Request produces Response`
- `MCP injection creates workspace affordance`
- `Paths locate State, Socket, Lock, and Logs`

Dependency relationships:

- liveness depends on daemon process table, not state alone
- event retrieval depends on JSONL log files
- messaging depends on a running target process and open stdin
- daemon exclusivity depends on lock file
- auto-start depends on ping failure and current executable path
- MCP tool execution depends on daemon request path

## 7. Epistemic Model

`multi-brain` currently has an operational epistemology, not a semantic one.

It knows:

- which harnesses are registered
- which harnesses appear alive
- which messages were sent through the bus
- which IO/status events were observed
- which command surface produced a response

It does not know:

- whether a harness response is true
- whether a harness completed a task
- whether a message was understood
- whether stdout contains a claim, decision, or artifact
- whether one brain's output should be trusted by another
- whether a conversation should be promoted into organizational memory

This is acceptable for the current layer. The project is an agent transport and observability substrate. Semantic knowledge promotion should be a higher layer.

## 8. Governance And Safety Boundaries

Current governance:

- only one daemon can own a registry directory due to lock file
- all ordinary calls auto-start daemon when missing
- harness kind controls launch argument translation
- MCP tools expose the same operations as CLI
- messages can only be sent to running harnesses
- events provide transparency into stdin/stdout/stderr/status

Current risks:

- `claude` launch uses permission-skipping flags
- `codex` launch uses `--full-auto`
- environment variables can be injected into harness processes
- MCP injection writes `.mcp.json` into target repositories
- any agent with MCP access can spawn, ask, and stop brains
- message body is raw text with no schema, priority, or task identity
- stdout/stderr are logged without sensitivity filtering

Recommended future governance objects:

- `PermissionPolicy`
- `WorkspaceTrustBoundary`
- `HarnessCapability`
- `MessageIntent`
- `TaskContext`
- `ReviewRequirement`
- `SensitiveEvent`
- `AgentAuthorityLevel`

## 9. Specification Requirements

### Functional Requirements

- The system must persist harness configs by name.
- Re-registering an existing name must preserve stable harness ID.
- The daemon must prevent multiple daemons from owning the same registry directory.
- CLI and MCP operations must share the same request/response protocol.
- The daemon must auto-start for ordinary CLI/MCP calls when not already running.
- The system must spawn supported harness kinds with correct command semantics.
- The system must report registered harnesses with liveness, pid, personality, cwd, and log path.
- The system must send messages to running harness stdin.
- The system must persist sent messages.
- The system must append structured events for stdin, stdout, stderr, and status.
- The system must expose recent events through CLI and MCP.
- The system must inject an MCP config into a workspace with `MULTI_BRAIN_HOME`.
- The system must stop a running harness without deleting its config.

### Epistemic Requirements

- A message record must be distinguished from a process event.
- A registered harness must be distinguished from a running harness.
- A harness config must be distinguished from a harness identity.
- Liveness must be reported as observed runtime state, not persistent fact.
- Event logs must be treated as observed process output, not validated knowledge.
- MCP tool responses must preserve structured daemon responses as text content.

### Observability Requirements

- Every spawned harness should emit a `status: started` event.
- Every stopped harness should emit a `status: stopped` event.
- Every delivered message should emit a `stdin` event.
- Harness stdout and stderr should be captured line-by-line.
- Daemon headless logs should be written to `logs/daemon.log`.

### Governance Requirements

- MCP injection should preserve existing `.mcp.json` content where possible.
- Harness commands, args, cwd, personality, and env should remain inspectable.
- Future versions should support unregister/retire semantics.
- Future versions should support agent permissions for tool access.
- Future versions should support message/task IDs for traceability.

## 10. Conceptual Debt

Known conceptual debt in the current ontology:

- `brain` and `harness` are used as overlapping concepts. MCP speaks in brains; protocol/code speaks in harnesses.
- `personality` is raw text but acts as role, identity, and system instruction.
- `Message` lacks task identity, status, response correlation, priority, and threading.
- `HarnessEvent` logs raw process lines but does not classify semantic content.
- There is no unregister/archive/deprecate lifecycle.
- There is no permission model for MCP tools.
- There is no explicit workspace entity beyond `cwd` and injected `.mcp.json`.
- Process liveness is in-memory and not durable across daemon restart.
- `from` in `Ask` is free text and does not have to name a registered harness.

These are not necessarily bugs. They are the next ontology expansions if the project moves from local bus to governed multi-agent operating layer.

## 11. Future Ontological Extensions

### Brain As First-Class Actor

Introduce `Brain` as the user-facing concept:

- stable ID
- name
- kind
- role/personality
- capabilities
- workspace
- authority level
- runtime status
- memory affordances

Then treat `Harness` as the implementation mechanism for running a brain.

### Task And Conversation Objects

Add:

- `Task`
- `Conversation`
- `Turn`
- `MessageIntent`
- `ResponseExpectation`
- `CompletionStatus`

This would allow `ask_brain` to become more than stdin transport.

### Agent Authority Model

Add:

- which brains may spawn other brains
- which brains may stop other brains
- which brains may inject MCP into workspaces
- which brains may access which event logs
- which commands require human confirmation

### Knowledge Promotion Layer

Add a bridge from event logs/messages into ontological-engineering knowledge objects:

- raw event
- candidate claim
- proposed synthesis
- reviewed knowledge
- accepted decision
- specification update

This is where `multi-brain` can become an input system for a company second brain.

## 12. Traceability Map To Code

- `src/protocol.rs`: core request/response, message, harness, and event types.
- `src/state.rs`: persistent registry and message memory.
- `src/daemon.rs`: runtime authority, socket protocol, request handling, MCP injection.
- `src/harness.rs`: process spawning, command translation, stdin writing, event logging.
- `src/mcp.rs`: JSON-RPC/MCP tool surface.
- `src/config.rs`: storage path ontology.
- `src/main.rs`: CLI command surface.
- `tests/daemon_cli.rs`: CLI lifecycle behavior.
- `tests/mcp_stdio.rs`: MCP tool behavior.

## 13. Working Definition

`multi-brain` is a local multi-agent harness registry and runtime bus. It gives named AI harnesses persistent identity, spawn semantics, message transport, event observability, and MCP-callable operations.

Through the ontological-engineering lens, its next evolution is to separate `Brain` from `Harness`, add task/conversation semantics, introduce authority boundaries, and connect raw agent interactions to a knowledge promotion lifecycle.

