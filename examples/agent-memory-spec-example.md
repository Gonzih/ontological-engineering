# Example: Agent Memory Promotion Workflow

This example shows how ontological engineering turns an abstract concern into a concrete software specification.

## Raw Concern

AI agents can generate convincing summaries, claims, and decisions. If those outputs are stored in company memory without status, provenance, or review, later agents may treat generated drafts as accepted knowledge.

## Ontological Analysis

Relevant entities:

- `Agent Output`
- `Claim`
- `Evidence`
- `Source`
- `Review`
- `Promotion`
- `Accepted Knowledge`
- `Deprecated Knowledge`
- `Specification`
- `Artifact`

Key distinctions:

- An agent output is not accepted knowledge.
- A source is not evidence until interpreted in relation to a claim.
- A claim is not a decision.
- A reviewed synthesis may be accepted within a scope.
- Deprecated knowledge may remain visible but should not guide new behavior.

## Epistemic Rule

No generated synthesis may become accepted organizational knowledge without either:

- human review, or
- deterministic validation appropriate to the domain.

## Specification Sketch

```yaml
id: spec-agent-memory-promotion
title: Agent Memory Promotion Workflow
version: 0.1
status: proposed
generation_mode: iterative

purpose:
  product: prevent unreviewed agent output from becoming organizational truth
  user: help reviewers inspect, accept, reject, or revise agent-generated knowledge
  agent: provide machine-readable status boundaries for future retrieval and use
  organizational_learning: preserve provenance and promotion history

domain_concepts:
  - Agent Output
  - Claim
  - Evidence
  - Review
  - Promotion
  - Accepted Knowledge

actors:
  humans:
    - reviewer
    - knowledge owner
  agents:
    - extractor
    - synthesizer
    - critic
    - maintainer
  systems:
    - knowledge base
    - notification system

linked_claims:
  - agent-output-is-not-knowledge-by-default
  - accepted-knowledge-requires-promotion

assumptions:
  - assumption: reviewers can inspect provenance quickly enough for promotion to be practical
    confidence: medium
    revisit_trigger: review backlog grows beyond acceptable threshold

requirements:
  - id: req-status-required
    statement: every agent output must have a promotion_status
    type: epistemic
    derives_from: agent-output-is-not-knowledge-by-default
    acceptance_criteria:
      - system rejects agent outputs without promotion_status

  - id: req-provenance-required
    statement: every agent output must preserve input references and tool trace
    type: governance
    derives_from: provenance-required-for-agent-memory
    acceptance_criteria:
      - reviewer can inspect source, agent role, and input references

  - id: req-review-before-acceptance
    statement: proposed synthesis cannot become accepted knowledge without review
    type: governance
    derives_from: accepted-knowledge-requires-promotion
    acceptance_criteria:
      - accepted_knowledge transition requires reviewer or validation process

  - id: req-deprecated-visible
    statement: deprecated knowledge remains searchable with warning and replacement link
    type: interaction
    derives_from: historical-knowledge-must-remain-queryable
    acceptance_criteria:
      - deprecated records display superseding record when available

evaluation:
  behavioral_tests:
    - agent output without status is rejected
    - proposed synthesis cannot be retrieved as accepted knowledge
    - accepted knowledge records show provenance
  epistemic_tests:
    - deprecated records are not used in production generation context
    - conflicting claims are surfaced before promotion
  traceability_checks:
    - accepted claim links to source, reviewer, and promotion event
```

## Generated Software Implications

The software should include:

- status fields for agent outputs
- provenance capture
- review queue
- promotion workflow
- accepted knowledge view
- deprecated knowledge warning
- contradiction detection hooks
- traceability links from accepted claims to specifications and artifacts

## Feedback Loop

After deployment, the system should collect:

- number of agent outputs created
- number promoted
- number rejected
- average review time
- promotion reversals
- downstream artifacts generated from accepted knowledge
- incidents involving stale or unreviewed knowledge

This feedback should revise the ontology and lifecycle. For example, if reviewers cannot keep up, the system may need better critic agents, risk scoring, batching, or domain-specific validation.

## Why This Example Matters

This example demonstrates the whole doctrine:

- ontology defines the relevant entities
- epistemology defines promotion rules
- provenance explains where outputs came from
- agency defines who can review and promote
- specification translates the model into software behavior
- evaluation checks whether the implementation preserves the knowledge contract
- feedback revises the system

