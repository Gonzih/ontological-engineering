# Ontology

Ontology is the study of what exists, what kinds of things exist, and how those things can be distinguished, related, and understood. In philosophy, ontology asks about the structure of reality. In knowledge engineering, ontology becomes a design practice: it specifies the concepts, entities, relationships, constraints, and rules that define a domain.

For this repository, ontology is the first layer of company intelligence. Before a company can reason well, it must know what kinds of things it is reasoning about. Before agents can retrieve knowledge responsibly, they must know whether they are handling a claim, a decision, a source, a requirement, an assumption, a specification, or a generated artifact. Before software can be generated from organizational intent, that intent must be represented in stable conceptual form.

Ontology is not just vocabulary. It is the architecture of meaning.

## The Philosophical Layer

Philosophical ontology begins with basic questions:

- What exists?
- What kinds of things exist?
- What properties can those things have?
- What relationships can hold between them?
- What makes one thing identical to itself over time?
- What makes one thing distinct from another?
- Which entities are concrete, abstract, social, procedural, fictional, emergent, or institutional?

These questions sound abstract, but organizations answer them implicitly every day.

When a team says "the user wants this," what is a user? A person? A persona? An account? A role? A segment? A buyer? A daily active actor? A hypothetical construct in a product strategy document?

When a roadmap says "this feature is blocked," what is a feature? Is it a user-facing capability, a code path, a design promise, a work item, a bundle of requirements, or a marketable unit?

When a product spec says "the agent should remember context," what is context? Conversation history, user preferences, current task state, long-term organizational knowledge, external world facts, or inferred intent?

Without ontological clarity, organizations reuse the same words while meaning different things. The result is not merely semantic confusion. It becomes bad software, misaligned teams, broken analytics, unsafe agents, and decisions whose rationale cannot be reconstructed.

## The Engineering Layer

In knowledge engineering, an ontology is often described as an explicit specification of a conceptualization. That phrase matters because it separates two layers:

- the conceptualization: how a community understands a domain
- the specification: how that understanding is represented so systems can use it

An ontology normally includes:

- classes or types
- instances of those types
- properties and attributes
- relationships between entities
- constraints on valid relationships
- taxonomies and part-whole structures
- rules or axioms
- provenance and metadata

For a traditional knowledge system, this may be enough. For an agentic company, it is not. The ontology must also model time, uncertainty, agency, and revision.

A static ontology can tell an agent that `Decision` and `Requirement` are different types. A time-aware ontology can tell the agent that a requirement was created from a decision made under an assumption that has since been superseded. A relationship-aware ontology can tell the agent which product flows, prompts, tests, and code paths may be affected. An epistemically aware ontology can tell the agent whether the underlying claim is validated, speculative, contradicted, or stale.

## Ontology As Company Worldview

A company ontology is not neutral. It encodes what the company considers real enough to track.

If the company models users but not user confusion, it may optimize for completion while missing trust. If it models decisions but not rationale, it may preserve commitments while losing judgment. If it models requirements but not assumptions, it may generate software that looks correct while implementing obsolete beliefs. If it models agent outputs but not promotion status, generated text can silently become institutional memory.

Ontological engineering therefore begins by asking: What distinctions must exist for this organization to remain coherent as it scales?

Initial distinctions include:

- A `Source` is not the same thing as `Evidence`.
- `Evidence` is not the same thing as a `Claim`.
- A `Claim` is not the same thing as a `Belief`.
- A `Belief` is not the same thing as a `Decision`.
- A `Decision` is not the same thing as an `Implementation`.
- A `Requirement` is not the same thing as a `User Desire`.
- An `Agent Output` is not the same thing as accepted organizational knowledge.
- A `Current Belief` is not the same thing as a `Historical Belief`.
- A `Specification` is not the same thing as a prompt, ticket, or code file.

Each distinction protects reasoning. It prevents a system from collapsing everything into undifferentiated text.

## Time And Identity

Time is central because company knowledge evolves. A company does not only need to know what it believes now. It needs to know what it believed before, why it changed, and what still depends on old beliefs.

Examples:

- A persona shifts after entering a new market.
- A pricing model changes after customer research.
- A compliance assumption becomes invalid after a regulatory update.
- A design principle is reinterpreted after a failed launch.
- A metric once treated as success is later understood as misleading.
- A requirement still exists in code after the decision behind it was deprecated.

This creates a problem of identity. Is the "same" requirement still the same after its scope changes? Is a product concept the same after it moves from prototype to production? Is a user segment the same after the company learns that its original definition was wrong?

An ontological system should support versioned identity. It should allow an entity to persist through ordinary change while also recognizing when a conceptual break has occurred. This is how the knowledge base preserves evolution without pretending that every revision is a new universe.

## Hierarchy And Composition

Organizations naturally use hierarchy:

- mission contains strategy
- strategy contains bets
- bets contain initiatives
- initiatives contain projects
- projects contain specifications
- specifications contain workflows
- workflows contain interactions
- interactions contain actions

But hierarchy is not enough. Some relationships are taxonomic: a support agent is a kind of agent. Some are compositional: a workflow contains interactions. Some are causal: a decision caused a requirement. Some are evidential: a customer interview supports a claim. Some are temporal: this belief supersedes that belief. Some are operational: this specification generates that artifact.

A serious ontology must support multiple relationship families. Otherwise everything becomes a folder tree, and folder trees cannot reason.

## The Ontology Of Agents

AI agents are not just tools in this domain. They are actors inside the knowledge ecosystem.

That means the ontology must represent:

- agent roles
- permissions
- tool access
- memory access
- output types
- review requirements
- trust boundaries
- escalation paths
- relationships between agent outputs and accepted knowledge

An agent can collect evidence, extract claims, synthesize documents, critique assumptions, generate specifications, write software, and evaluate results. Those actions are different. They carry different epistemic risk. The ontology must represent the difference between an agent producing a draft synthesis and the company accepting that synthesis as knowledge.

## Ontology And Software Generation

Generated software inherits the ontology that produced it. If the ontology is vague, the generated system will embody vagueness. If the ontology confuses users with accounts, decisions with preferences, or evidence with assumptions, the software may still compile but behave incoherently.

Specification-driven generation requires the ontology to define:

- who the actors are
- what objects exist in the domain
- what actions are possible
- what states matter
- what relationships constrain behavior
- which claims justify requirements
- which decisions govern tradeoffs
- which assumptions must be tested

The ontology does not replace implementation. It gives implementation a conceptual contract.

## Working Definition

Ontological engineering is the practice of designing, maintaining, and evolving the conceptual structure through which an organization represents reality, coordinates humans and agents, preserves memory, and generates software.

It is philosophical because it asks what exists. It is technical because those answers must become schemas, workflows, permissions, interfaces, specifications, and tests.

