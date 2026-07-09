# Company Second Brain

A company second brain is the structured memory of the organization. It is not a document archive, a wiki, a vector database, or a folder of strategy notes. Those may be components, but the second brain is the larger system that preserves organizational understanding.

Its purpose is to make intelligence durable. A company learns through conversations, customer feedback, product failures, experiments, code, market changes, research, and decisions. Most of that learning is fragile. It lives in people, scattered notes, Slack threads, pull requests, dashboards, and forgotten decks. The second brain turns that fragile learning into structured memory that humans and agents can inspect, reason over, and apply.

## From Storage To Memory

Storage keeps artifacts. Memory preserves meaning.

A storage system can answer:

- Where is the document?
- What did the transcript say?
- Which ticket mentioned this term?
- What files contain this phrase?

A memory system should answer:

- What do we currently believe?
- Why do we believe it?
- What did we believe before?
- What changed our mind?
- Which decisions depend on this claim?
- Which software still implements old assumptions?
- Which agents are allowed to act on this knowledge?
- Which unresolved questions block the next specification?

This difference is the reason ontological engineering matters. A company does not need only retrieval. It needs continuity of thought.

## The Three Awarenesses

The company second brain should be time-aware, hierarchy-aware, and relationship-aware.

Time-aware means knowledge has history. It records creation, revision, validation, deprecation, supersession, and validity windows. The system should be able to reconstruct what the company believed at a specific moment.

Hierarchy-aware means knowledge has scale. Mission, strategy, initiatives, projects, specifications, workflows, interactions, and actions can be understood at different levels of abstraction.

Relationship-aware means knowledge is connected by typed links. Claims support decisions. Decisions generate requirements. Requirements constrain specifications. Specifications generate artifacts. Artifacts produce feedback. Feedback challenges claims.

These three forms of awareness turn scattered artifacts into an evolving knowledge graph.

## Knowledge Layers

The second brain can be understood as layered memory:

1. Raw inputs: transcripts, notes, documents, logs, code, metrics, customer feedback, external references, agent outputs.
2. Extracted knowledge: entities, claims, questions, assumptions, decisions, constraints, relationships.
3. Interpreted knowledge: themes, tensions, hypotheses, models, explanations, implications.
4. Validated knowledge: accepted definitions, reviewed claims, trusted beliefs, canonical decisions.
5. Operational knowledge: specifications, workflows, policies, playbooks, agent instructions, product behavior.
6. Generated artifacts: software, designs, tests, reports, datasets, prompts, simulations.
7. Historical memory: superseded claims, deprecated assumptions, old rationales, previous specifications, failed approaches.

Each layer has a different epistemic status. Raw input is not automatically trusted. Extracted knowledge is not automatically canonical. Generated software is not automatically aligned with intent. Historical memory is not current truth but must remain available for explanation.

## Canonical Entities

A first ontology for the company second brain should include:

- `Actor`: a human, team, customer, stakeholder, agent, or system.
- `Concept`: a named idea with definition, boundary, examples, and relationships.
- `Source`: the origin of information.
- `Evidence`: material that supports or challenges a claim.
- `Claim`: an evaluable proposition.
- `Belief`: a claim accepted within a scope.
- `Assumption`: a temporary belief used for action.
- `Hypothesis`: a claim under investigation.
- `Question`: an unresolved issue.
- `Disagreement`: a structured conflict between claims or interpretations.
- `Decision`: a commitment to action.
- `Rationale`: the reasoning behind a decision.
- `Requirement`: a condition the system must satisfy.
- `Constraint`: a limit that shapes possible action.
- `Interaction`: an exchange between actors.
- `Workflow`: a repeatable sequence of interactions and transformations.
- `Specification`: a coherent model of intended behavior.
- `Artifact`: code, design, prompt, document, dataset, test, or other produced object.
- `Version`: a time-bound state of an entity.
- `Feedback`: evidence produced by real-world use or evaluation.

The important point is not the exact list. The important point is that the system distinguishes between knowledge types that have different meanings and lifecycles.

## Relationship Families

Relationships are the intelligence layer. They let the system reason across memory.

Evidential relationships:

- `supports`
- `challenges`
- `contradicts`
- `validated_by`
- `derived_from`

Temporal relationships:

- `supersedes`
- `deprecated_by`
- `valid_during`
- `revises`

Operational relationships:

- `implements`
- `generates`
- `constrains`
- `blocks`
- `enables`

Conceptual relationships:

- `defines`
- `refines`
- `is_a`
- `part_of`
- `related_to`

Accountability relationships:

- `owned_by`
- `reviewed_by`
- `approved_by`
- `authored_by`

Without typed relationships, the knowledge base becomes a pile of semantically similar chunks. With typed relationships, agents can ask what depends on what, what changed, what conflicts, and what should be reviewed.

## Wisdom Representation

The highest-value company knowledge is often not a final answer. It is the reasoning that produced the answer.

Wisdom includes:

- tradeoffs considered
- alternatives rejected
- failure modes discovered
- boundaries where a rule stops applying
- context that made a decision reasonable
- lessons learned from repeated attempts
- tensions that should remain unresolved
- assumptions that must be watched

This kind of knowledge is easy to lose because final artifacts look cleaner than the reasoning behind them. A decision record says what happened. A rationale explains why it happened. A specification says what should be built. A history explains why the specification has that shape.

The second brain should treat rationale as first-class memory. Otherwise the company can repeat the same debates without realizing it.

## Current Truth And Historical Truth

A company needs both canonical current knowledge and historical knowledge.

Current knowledge guides action. Historical knowledge explains evolution.

The system should avoid two failures:

- overwriting history whenever the current view changes
- presenting old knowledge as current truth

Superseded knowledge should remain searchable with temporal context. If an agent retrieves a deprecated belief, the system should show that it was once accepted, why it changed, what replaced it, and what artifacts may still depend on it.

This is how the second brain detects conceptual debt: software, workflows, or prompts still organized around old beliefs.

## Human And Agent Use

Humans use the second brain to understand the company: what it knows, why it acts, what remains uncertain, and where decisions came from.

Agents use the second brain to perform work: extract knowledge, critique assumptions, draft specifications, generate software, evaluate outputs, and monitor drift.

Both uses require structure. Humans need coherent narratives and inspectable reasoning. Agents need machine-readable status, relationships, permissions, and dependencies.

The second brain must therefore be both readable and computable.

## Working Definition

A company second brain is a structured, temporal, relational memory system that preserves the organization's concepts, claims, evidence, decisions, rationale, specifications, artifacts, and learning history so humans and agents can reason and act coherently.

