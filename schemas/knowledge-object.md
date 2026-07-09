# Knowledge Object Schema

This schema is the first concrete representation layer for the company second brain. It is intentionally tool-agnostic: the same conceptual model could later be implemented in Markdown, YAML, a graph database, a document database, an event log, or a hybrid system.

The purpose of the schema is not to overformalize early thinking. The purpose is to preserve the distinctions that make organizational reasoning possible. A company knowledge object should be readable by humans, computable by agents, versionable over time, and connected to the rest of the knowledge system.

## Design Goals

The schema should support five capabilities:

1. Identify what kind of thing a record is.
2. Preserve where it came from and how it changed.
3. Represent its epistemic status.
4. Connect it to related knowledge.
5. Make it usable in specifications, agent workflows, and software generation.

If a field does not support one of these capabilities, it should be questioned. If a missing field prevents one of these capabilities, it should be added.

## Base Object

Every knowledge object should share a base structure.

```yaml
id: stable unique identifier
type: concept | source | evidence | claim | belief | assumption | hypothesis | question | disagreement | decision | rationale | requirement | constraint | interaction | workflow | specification | artifact | feedback | agent_output
title: human-readable name
summary: short description
status: raw | proposed | accepted | disputed | rejected | superseded | deprecated | historical
created_at: timestamp
created_by: human, team, agent, or system
updated_at: timestamp
scope:
  domain: relevant domain
  product: optional product or system
  team: optional owning team
  audience: optional affected audience
time:
  observed_at: optional timestamp
  valid_from: optional timestamp
  valid_until: optional timestamp
  reviewed_at: optional timestamp
  superseded_at: optional timestamp
epistemic:
  confidence: unknown | low | medium | high
  confidence_basis: explanation of confidence
  evidence_quality: unknown | weak | moderate | strong
  review_state: unreviewed | needs_review | reviewed | validated
  actionability: exploratory | advisory | operational | production
provenance:
  sources: []
  generated_by: optional agent, model, prompt, or tool trace
  extracted_from: optional source ids
  reviewed_by: []
relationships:
  supports: []
  challenges: []
  contradicts: []
  depends_on: []
  supersedes: []
  derived_from: []
  constrains: []
  implemented_by: []
  generates: []
notes: free-form notes
```

## Status Semantics

Statuses should have operational meaning.

- `raw`: captured but not interpreted or trusted.
- `proposed`: structured or interpreted but not accepted.
- `accepted`: canonical within a defined scope.
- `disputed`: actively contested by another claim, source, or interpretation.
- `rejected`: reviewed and declined.
- `superseded`: replaced by a newer object.
- `deprecated`: retained but should not guide current action.
- `historical`: preserved for context only.

Agents should treat status as a permission boundary. A proposed claim may support brainstorming. An accepted claim may support specification. A deprecated claim may explain history but should not guide new behavior.

## Concept

Concepts define the vocabulary of the company.

```yaml
type: concept
definition: precise working definition
aliases: []
broader_concepts: []
narrower_concepts: []
related_concepts: []
boundary_conditions:
  applies_when: []
  does_not_apply_when: []
examples: []
counterexamples: []
open_ambiguities: []
history:
  - changed_at: timestamp
    change: what changed
    rationale: why it changed
    superseded_definition: optional previous definition
```

Concepts should include boundary conditions because definitions alone are often too clean. The company needs to know where a concept stops applying.

## Claim

Claims are evaluable propositions.

```yaml
type: claim
proposition: clear statement that can be supported or challenged
claim_kind: empirical | analytical | strategic | normative | operational | speculative
evidence_for: []
evidence_against: []
assumptions: []
open_questions: []
disagreements: []
decision_impact: low | medium | high
revisit_trigger: condition that should cause review
```

A claim should not be promoted merely because it is well-written. It should be evaluated by source, evidence, scope, and consequence.

## Evidence

Evidence is material that changes the standing of a claim.

```yaml
type: evidence
source_type: meeting | document | user_research | metric | code | experiment | external_reference | agent_output
source_ref: link or identifier
observation: what was observed
interpretation: optional interpretation
supports_claims: []
challenges_claims: []
quality: weak | moderate | strong
limitations: []
```

Evidence should distinguish observation from interpretation. A user said something; the company interpreted it as a need. Those are different records.

## Decision

Decisions preserve commitments and their reasons.

```yaml
type: decision
decision: what was committed to
decision_maker: person, team, or process
date: timestamp
context: situation in which the decision was made
goals: []
options_considered: []
chosen_option: selected option
tradeoffs: []
assumptions: []
evidence_used: []
rationale_ref: rationale id
expected_consequences: []
downstream_requirements: []
downstream_artifacts: []
revisit_trigger: condition that should cause review
```

A decision without rationale is operationally useful but epistemically thin. The system may know what happened, but not why.

## Rationale

Rationale captures judgment.

```yaml
type: rationale
decision_ref: decision id
reasoning_summary: why the decision made sense
principles_used: []
tradeoffs: []
alternatives_rejected: []
risks_accepted: []
known_limitations: []
future_review_conditions: []
```

Rationale is where organizational wisdom accumulates. It should be linked to decisions, specifications, and later feedback.

## Specification

Specifications bridge knowledge and software.

```yaml
type: specification
purpose: what the system should accomplish
actors: []
domain_concepts: []
user_interactions: []
agent_interactions: []
requirements: []
constraints: []
assumptions: []
linked_claims: []
linked_decisions: []
success_criteria: []
failure_modes: []
open_questions: []
generation_mode: one_shot | iterative
evaluation_plan: tests, review criteria, metrics, or simulations
generated_artifacts: []
```

The specification should be versioned because each generated artifact depends on the specification state that produced it.

## Agent Output

Agent outputs must preserve role, input, and promotion status.

```yaml
type: agent_output
agent_role: collector | extractor | classifier | synthesizer | critic | historian | specifier | builder | evaluator | maintainer
input_refs: []
tool_trace: []
memory_scope: what memory the agent could access
output_summary: summary of generated content
promotion_status: raw_output | candidate_extraction | proposed_synthesis | critique | evaluation_result | accepted_knowledge | rejected | superseded | deprecated
human_review_required: true | false
risks: []
recommended_next_action: optional next step
```

The system should assume agent outputs are not canonical until promoted by a valid process.

## Artifact

Artifacts are produced objects.

```yaml
type: artifact
artifact_kind: code | design | document | prompt | test | dataset | report | simulation
produced_from: specification, decision, prompt, or agent output ids
implements_requirements: []
depends_on_claims: []
version: artifact version
evaluation_results: []
known_conceptual_debt: []
```

Artifacts should link back to the knowledge that generated them. This enables dependency review when concepts, claims, or decisions change.

## Feedback

Feedback closes the loop.

```yaml
type: feedback
feedback_source: user | agent | test | metric | incident | review | external_event
observed_behavior: what happened
expected_behavior: what was expected
affected_artifacts: []
affected_specifications: []
claims_supported: []
claims_challenged: []
recommended_revision: optional proposed change
```

Feedback is not only a product signal. It is evidence about whether the company's ontology and specifications are adequate.

