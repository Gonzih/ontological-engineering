# Specification-Driven Software

Specification-driven software begins from the claim that code is not the primary source of product meaning. Code implements meaning. The meaning comes from concepts, user goals, agent roles, constraints, decisions, assumptions, and desired interactions.

In conventional development, specifications often become thin intermediaries between idea and implementation. They are written as documents, tickets, prompts, or acceptance criteria. They may describe what to build, but they rarely preserve the full conceptual structure behind the work. In an agentic development environment, that weakness becomes more important because software can be generated quickly from incomplete or ambiguous instructions.

If generation is cheap, specification becomes the high-leverage artifact.

## Specification As A Knowledge Object

A specification should be a first-class object in the company second brain. It should not be treated as a disposable prompt or static document.

A strong specification includes:

- purpose: why the system exists
- actors: users, agents, teams, systems, and stakeholders
- domain concepts: the entities and relationships that matter
- user goals: what humans are trying to accomplish
- agent roles: what AI agents are allowed or expected to do
- interactions: the structured flows between actors
- requirements: conditions the system must satisfy
- constraints: limits imposed by policy, design, architecture, risk, or context
- assumptions: claims accepted temporarily for this design
- decisions: commitments that shape the spec
- evidence: sources and claims that justify the spec
- success criteria: how the system will be evaluated
- failure modes: what can go wrong
- open questions: what remains unresolved
- version history: how the specification evolved

This makes the specification an interface between the knowledge system and implementation.

## Interaction Before Interface

A specification should model interaction before it models screens or code.

For users, interaction modeling asks:

- What is the user trying to accomplish?
- What context are they in?
- What do they know at each step?
- What do they need to decide?
- What could confuse them?
- What should the system remember?
- Where should the system earn trust?
- What feedback should be captured?

For agents, interaction modeling asks:

- What task is the agent performing?
- What memory can it access?
- What tools can it use?
- What evidence is required?
- What output status should it produce?
- When must it ask for review?
- What is it forbidden to change?
- How should its work be evaluated?

The product is not only a user interface. It is an environment where humans and agents coordinate around structured knowledge.

## From Ontology To Requirements

Requirements should not appear from nowhere. They should derive from ontology, epistemology, and decisions.

Example:

1. The ontology defines `Agent Output`, `Claim`, `Evidence`, `Decision`, and `Specification` as different objects.
2. The epistemology says unreviewed agent outputs cannot become accepted knowledge without promotion.
3. A decision commits the company to preventing unreviewed agent synthesis from driving production behavior.
4. The specification requires every generated synthesis to carry status, provenance, and review requirements.
5. The software implements UI states, permissions, storage fields, and tests that enforce that rule.

This chain matters because it lets the company inspect why a requirement exists. If the underlying decision changes, downstream requirements and implementation can be reviewed.

## One-Shot Generation And Iterative Refinement

There are two useful generation modes.

`one_shot_generation` means the specification is mature enough that a complete artifact can be generated in one pass with high confidence. This requires stable concepts, clear constraints, known interactions, and strong evaluation criteria.

`iterative_refinement` means the domain is still being discovered. The system generates an artifact, evaluates it, learns from the mismatch, revises the specification, and generates again.

The point is not to choose one mode forever. The goal is to move more work toward one-shot generation by improving the quality of the specification and the knowledge it depends on. Iteration should deepen the ontology rather than merely patch the code.

## Evaluation

Generated software should be evaluated against more than compilation and surface behavior.

Evaluation should ask:

- Does the implementation satisfy explicit requirements?
- Does it preserve the intended user interaction?
- Does it preserve the intended agent interaction?
- Does it enforce epistemic status and permissions?
- Does it reflect current accepted concepts?
- Does it rely on stale assumptions?
- Does it link back to decisions and rationale?
- Does it capture feedback that should update the knowledge base?
- Does it create new conceptual debt?

This creates a closed loop:

1. Ontology defines the domain.
2. Epistemology defines what can be trusted.
3. The second brain preserves memory.
4. Agents transform knowledge into specifications.
5. Software is generated from specifications.
6. Evaluation reveals mismatches.
7. Feedback updates the knowledge system.

Software becomes a hypothesis about the company's understanding of its domain.

## Conceptual Debt

Technical debt is visible in code. Conceptual debt is hidden in meaning.

Examples:

- the UI uses a term differently than the ontology
- an agent instruction relies on a deprecated definition
- a workflow assumes a decision that has been superseded
- two features encode different versions of the same concept
- a requirement was generated from an unvalidated claim
- a test validates behavior that no longer matches current strategy
- a prompt contains old policy after the policy changed

Conceptual debt matters because generated systems can multiply it. If an outdated concept sits upstream in the knowledge base, every generated artifact downstream may inherit the error.

Ontological engineering should make conceptual debt observable by tracing relationships between concepts, decisions, specifications, and artifacts.

## Specifications As Evolutionary Records

A specification should preserve its own history:

- what changed
- why it changed
- which evidence caused the change
- which decisions were revised
- which requirements were added or removed
- which artifacts were generated from each version
- which evaluations succeeded or failed

This historical record allows the company to learn from software generation. A failed implementation may reveal a weak prompt, but it may also reveal a weak concept, a missing relationship, a false assumption, or an unresolved decision.

## Working Definition

Specification-driven software is the practice of generating and evaluating software from explicit, versioned models of meaning, interaction, evidence, constraints, decisions, and organizational intent.

It treats the specification as the bridge between company knowledge and executable systems.

