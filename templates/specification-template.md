# Specification Template

This template turns ontological engineering into a repeatable specification artifact. It should be used when moving from company knowledge into generated software, workflows, agent instructions, or product behavior.

## 1. Specification Identity

```yaml
id:
title:
version:
status: draft | proposed | accepted | superseded | deprecated
created_at:
created_by:
owner:
generation_mode: one_shot | iterative
```

## 2. Purpose

What is this specification trying to make true?

Include:

- business or product purpose
- user purpose
- agent purpose
- organizational learning purpose

## 3. Ontological Scope

What kinds of things exist in this specification?

```yaml
domain_concepts:
  - concept_id:
    definition:
    boundary_conditions:
actors:
  humans: []
  agents: []
  systems: []
objects:
  - name:
    type:
    states:
    relationships:
```

## 4. Epistemic Basis

Why do we believe this specification is justified?

```yaml
linked_claims: []
linked_evidence: []
linked_decisions: []
assumptions:
  - assumption:
    scope:
    confidence:
    revisit_trigger:
open_questions: []
disagreements: []
```

## 5. Interaction Model

What happens between actors?

### User Interactions

```yaml
user_interactions:
  - name:
    actor:
    goal:
    context:
    preconditions:
    steps:
    decisions:
    possible_confusions:
    trust_boundaries:
    feedback_captured:
```

### Agent Interactions

```yaml
agent_interactions:
  - name:
    agent_role:
    task:
    memory_access:
    tool_access:
    permitted_actions:
    forbidden_actions:
    required_evidence:
    output_status:
    review_required:
    escalation_conditions:
```

## 6. Requirements

Requirements should trace back to claims, assumptions, decisions, or constraints.

```yaml
requirements:
  - id:
    statement:
    type: functional | non_functional | epistemic | governance | interaction | data | security
    derives_from:
    priority:
    acceptance_criteria:
    tests:
```

## 7. Constraints

```yaml
constraints:
  - id:
    statement:
    source:
    scope:
    severity:
    affected_requirements:
```

## 8. Failure Modes

What can go wrong?

```yaml
failure_modes:
  - failure:
    cause:
    impact:
    detection:
    mitigation:
    related_assumptions:
```

## 9. Evaluation Plan

How will we know the generated artifact is good?

```yaml
evaluation:
  behavioral_tests: []
  epistemic_tests: []
  traceability_checks: []
  user_feedback_signals: []
  agent_output_checks: []
  conceptual_debt_checks: []
```

## 10. Traceability

What depends on what?

```yaml
traceability:
  upstream:
    concepts: []
    claims: []
    evidence: []
    decisions: []
    rationales: []
  downstream:
    requirements: []
    prompts: []
    code_artifacts: []
    tests: []
    docs: []
    workflows: []
```

## 11. Revision Rules

What should trigger a new version?

```yaml
revision_triggers:
  - changed_core_concept
  - superseded_decision
  - contradicted_assumption
  - failed_evaluation
  - user_feedback_pattern
  - agent_governance_violation
  - external_world_change
```

## 12. Generation Prompt Boundary

If this specification is used to generate software, the generation prompt should reference this specification as the governing artifact. The prompt may add implementation preferences, but it should not silently override ontology, epistemic status, constraints, or traceability requirements.

