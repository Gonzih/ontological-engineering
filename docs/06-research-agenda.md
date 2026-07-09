# Research Agenda

This repository is both philosophical inquiry and infrastructure design. The philosophical inquiry asks what a company knows, how it knows, and how that knowledge changes. The infrastructure design asks how those answers become schemas, workflows, agent roles, software specifications, and evaluation systems.

The agenda is to turn ontological engineering into a practical discipline for companies that use AI agents as participants in knowledge work and software generation.

The academic foundation is broad. Knowledge engineering gives elicitation and operationalization methods. Ontology engineering gives conceptual modeling and ontology lifecycle methods. Knowledge graphs give graph infrastructure. Provenance gives origin and derivation semantics. Belief revision gives rational change operations. Organizational memory gives the company-level memory problem. Design rationale gives structured deliberation. Requirements engineering gives the bridge from goals to implemented systems.

The research opportunity is integration. The field needs a cohesive discipline that treats these components as one AI-native company memory and software-generation system.

## The Main Research Program

The research program has one unifying question:

How can a company build a knowledge system that preserves evolving understanding, supports responsible agent action, and generates software from coherent specifications?

That question splits into several threads.

## Thread 1: Ontology Of Company Knowledge

The first task is defining what kinds of entities must exist in company memory.

Open questions:

- What is the minimal useful set of object types?
- Which distinctions are essential and which are unnecessary early complexity?
- How should concepts, claims, evidence, decisions, assumptions, requirements, specifications, and artifacts relate?
- What does it mean for a concept to preserve identity across revisions?
- When should a changed entity become a new entity rather than a new version?

The goal is not to design the largest possible ontology. The goal is to identify the smallest ontology that can preserve meaning, history, trust, and actionability.

## Thread 2: Epistemology Of Agentic Systems

The second task is defining how information becomes trusted knowledge.

Open questions:

- What statuses should knowledge objects have?
- What kinds of evidence are sufficient for different domains?
- How should confidence be represented without false precision?
- How should disagreement be preserved?
- How should agent-generated content be prevented from becoming accidental truth?
- What promotion rules should apply to high-risk claims?
- How should stale knowledge remain visible but not actionable?

The goal is to make epistemic status machine-readable so agents know whether they are exploring, proposing, applying, or depending on knowledge.

## Thread 3: Temporal Knowledge Modeling

The third task is making time a first-class part of the system.

Open questions:

- Which objects need `created_at`, `valid_from`, `valid_until`, `superseded_at`, and `reviewed_at` fields?
- How should the system reconstruct what the company believed at a past moment?
- How should old decisions be linked to current artifacts?
- How should obsolete concepts remain searchable?
- How should the system detect conceptual debt caused by old assumptions?

The goal is to preserve the evolution of thinking, not just the latest state.

## Thread 4: Relationship-Aware Reasoning

The fourth task is moving beyond semantic search.

Open questions:

- Which relationship types should be canonical?
- Which relationships should be directional?
- Which relationships require confidence or provenance?
- How should agents traverse relationships safely?
- How should contradictions be represented?
- How should dependencies be used to trigger review?

The goal is to let agents reason over typed structures: what supports what, what depends on what, what supersedes what, and what may break if a belief changes.

## Thread 5: Agent Governance

The fifth task is defining how agents participate in the knowledge ecosystem.

Open questions:

- Which agent roles are needed?
- Which roles can create, edit, link, critique, or promote objects?
- How should permissions vary by epistemic status?
- What tool traces and provenance should agent outputs preserve?
- When should human review be required?
- How should agents escalate ambiguity, contradiction, or risk?

The goal is not to constrain agents for its own sake. The goal is to make their work reliable enough to compound.

## Thread 6: Specification Generation

The sixth task is connecting knowledge representation to software.

Open questions:

- What makes a specification complete enough for one-shot generation?
- What should a specification include about users, agents, interactions, evidence, and constraints?
- How should requirements link back to claims and decisions?
- How should generated software link back to the specification version that produced it?
- How should evaluation results update the knowledge base?

The goal is to make software generation downstream of structured understanding rather than isolated prompting.

## Thread 7: Wisdom Representation

The seventh task is representing judgment.

Open questions:

- How should rationale be modeled?
- How should rejected alternatives be preserved?
- How should tradeoffs become reusable knowledge?
- How should the system preserve boundaries where a principle stops applying?
- How should it keep productive tensions alive instead of flattening them?

The goal is to prevent the second brain from becoming a database of conclusions without the reasoning that made those conclusions intelligent.

## Thread 8: Academic Synthesis

The eighth task is turning adjacent research traditions into a unified doctrine.

Open questions:

- Which parts of CommonKADS should be adapted for agentic company memory?
- Which parts of NeOn should guide ontology network evolution?
- Which knowledge graph patterns are essential for company-scale reasoning?
- Which provenance concepts should become mandatory fields?
- Which belief revision operations map cleanly to company knowledge lifecycle states?
- Which IBIS or design rationale structures should be first-class objects?
- Which requirements traceability practices should be extended for generated software?

The goal is not to cite academia for legitimacy. The goal is to mine mature work for primitives that make ontological engineering executable.

## Design Tensions

Several tensions will shape the work:

- Formality vs flexibility: too little structure prevents reasoning; too much structure freezes learning.
- Current truth vs historical trace: current beliefs guide action, but past beliefs explain evolution.
- Agent autonomy vs epistemic safety: agents need room to work, but promotion to truth must be governed.
- Search vs reasoning: retrieval finds related text, but relationships enable dependency-aware reasoning.
- Speed vs validation: generated outputs arrive quickly, but trusted memory should change carefully.
- Specification vs implementation: software implements specifications, but implementation feedback should improve specifications.
- Human judgment vs automation: agents can process scale, but humans remain responsible for meaning, tradeoffs, and authority.

## Near-Term Work

The next phase should make the system more concrete:

1. Expand the schema into example YAML records.
2. Create a specification template for generated software.
3. Create a promotion workflow for agent outputs.
4. Create a contradiction and disagreement model.
5. Create a temporal model for beliefs, decisions, and specifications.
6. Create a worked example that moves from raw voice note to ontology to specification to generated app.
7. Define initial agent roles and permissions.
8. Define evaluation criteria for specification quality.

## Long-Term Ambition

The long-term ambition is an organizational intelligence substrate: a knowledge system that can remember, reason, generate, critique, and evolve with the company.

The system should make the company more coherent over time. It should preserve not only what was built, but why it was built, what knowledge justified it, what changed, and what should happen next.
