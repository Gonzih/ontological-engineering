# Knowledge Lifecycle

The knowledge lifecycle defines how information moves from raw input to trusted organizational memory and then back into action. It is the process layer that connects ontology, epistemology, agents, specifications, software, and feedback.

The lifecycle exists because not all information should be treated the same way. A raw transcript, an agent summary, a validated decision, a deprecated assumption, and a production requirement may all be useful, but they carry different permissions.

## Lifecycle Overview

The full cycle:

1. Raw capture
2. Extraction
3. Contextualization
4. Evaluation
5. Promotion
6. Application
7. Feedback
8. Revision
9. Historical preservation

The cycle is continuous. Knowledge is never finished; it is current within a scope and time.

## 1. Raw Capture

Material enters the system without being trusted.

Examples:

- meeting transcript
- voice note
- customer interview
- support ticket
- metric snapshot
- code comment
- external article
- agent answer
- generated code
- evaluation report

Status: `raw`

Raw capture should preserve source and time. The goal is fidelity, not interpretation.

## 2. Extraction

Agents or humans identify candidate structure:

- concepts
- claims
- questions
- assumptions
- decisions
- requirements
- relationships
- contradictions

Status: `proposed`

Extraction is lossy. The extracted object is not the same thing as the source. It should link back to the source and preserve uncertainty.

## 3. Contextualization

The object is placed into the existing knowledge system.

Required questions:

- What type of object is this?
- What domain does it belong to?
- What is its scope?
- When was it observed?
- Is it current, historical, or time-bound?
- What does it support or challenge?
- What might depend on it?
- Which agents or humans can act on it?

Contextualization prevents isolated notes from pretending to be knowledge.

## 4. Evaluation

The object is assessed for evidence quality, relevance, contradiction, actionability, and risk.

Evaluation outcomes:

- accept
- reject
- keep as hypothesis
- mark disputed
- request more evidence
- mark historical only
- mark high risk
- trigger review

Evaluation should be proportional to consequence. A low-impact exploratory claim needs less review than a claim that will generate production behavior.

## 5. Promotion

Promotion moves an object into accepted organizational memory.

Status: `accepted`

Promotion should preserve:

- source links
- reviewer or validation process
- confidence basis
- known limitations
- effective scope
- valid time window
- relationships to decisions, requirements, and artifacts

Promotion is the central epistemic gate. No agent-generated object should become accepted organizational knowledge without either deterministic validation appropriate to the domain or explicit review.

## 6. Application

Accepted knowledge is used to guide action.

Applications include:

- specifications
- agent instructions
- workflows
- product behavior
- generated code
- tests
- documentation
- strategic decisions

At this stage, downstream dependencies should be recorded. If the accepted knowledge changes later, the system needs to know what might be affected.

## 7. Feedback

Action produces new evidence.

Feedback may come from:

- user behavior
- support requests
- failed tests
- production incidents
- agent critiques
- customer interviews
- metric changes
- implementation difficulty
- external changes

Feedback should be linked to the artifacts, specifications, requirements, claims, and decisions it affects.

## 8. Revision

Revision updates current knowledge while preserving history.

Possible transitions:

- `proposed` to `accepted`
- `proposed` to `rejected`
- `accepted` to `disputed`
- `accepted` to `superseded`
- `accepted` to `deprecated`
- `hypothesis` to `accepted`
- `raw` to `historical`

Revision should trigger dependency checks. If a belief is superseded, related decisions, requirements, specifications, prompts, tests, and code may need review.

## 9. Historical Preservation

Superseded and deprecated knowledge should remain queryable, but never without temporal context.

Historical preservation answers:

- What did we believe then?
- Why did we believe it?
- What replaced it?
- Which artifacts still depend on it?
- Was the old belief wrong, narrowed, or merely no longer useful?

History is how the company avoids repeating its own learning process.

## Lifecycle Invariants

The lifecycle should enforce several invariants:

- Raw information is not accepted knowledge.
- Agent output is not accepted knowledge by default.
- Accepted knowledge has scope.
- Deprecated knowledge remains visible but not actionable.
- Decisions preserve rationale.
- Specifications link back to claims, assumptions, and decisions.
- Artifacts link back to the specification version that generated them.
- Feedback can challenge upstream knowledge.
- Revision preserves history.

## Practical Promotion Rule

An object may be promoted when:

1. Its type is clear.
2. Its source or derivation is known.
3. Its scope is explicit.
4. Its evidence basis is sufficient for its intended use.
5. Its contradictions have been checked or recorded.
6. Its downstream risk is understood.
7. A valid reviewer, process, or deterministic check has accepted it.

Promotion should be harder when the object has high decision impact, high risk, broad scope, or production consequences.

