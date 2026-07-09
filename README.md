# Ontological Engineering

This repository is a research and design space for ontological engineering as a company operating discipline.

The core premise is simple: a company does not run on documents, prompts, tickets, code, dashboards, and meetings as separate artifacts. It runs on an evolving interpretation of reality. It has concepts it uses, claims it accepts, doubts it postpones, assumptions it acts on, decisions it preserves, systems it builds, agents it authorizes, and histories it often forgets. Ontological engineering is the work of making that interpretation explicit enough that humans and AI agents can reason with it.

This repository treats ontological engineering as the design of a company's second brain: a time-aware, hierarchy-aware, relationship-aware knowledge system that preserves both what the company currently believes and how those beliefs came to exist.

## The Central Problem

AI makes it cheap to generate artifacts. It does not automatically make an organization wiser.

An agent can summarize a meeting, draft a requirement, generate code, propose a workflow, or synthesize research. But unless the organization knows how that output relates to existing concepts, evidence, decisions, and priorities, the output is just another fragment. More generation can make the company's memory noisier rather than clearer.

The central problem is therefore not "How do we store more knowledge?" It is:

How should an organization represent what it knows so that humans and agents can reason over it, revise it, generate software from it, and preserve the wisdom behind decisions rather than only their latest outputs?

## Working Thesis

Software is downstream of specification. Specification is downstream of ontology and epistemology.

Ontology defines what kinds of things exist in the company's world: users, agents, products, workflows, claims, decisions, requirements, evidence, risks, concepts, versions, and artifacts.

Epistemology defines how the company knows what it claims to know: what counts as evidence, which claims are trusted, which outputs are speculative, which assumptions are temporary, which disagreements remain open, and which decisions were justified under which conditions.

Specification translates this structured knowledge into a model of desired behavior: how users interact, how agents interact, what constraints apply, what success means, what failure modes matter, and what software should be generated or evaluated.

Ontological engineering ties these layers together. It gives the organization a way to move from raw knowledge to coherent action:

1. The world produces signals.
2. Humans and agents capture those signals.
3. The knowledge system extracts entities, claims, decisions, and relationships.
4. Epistemic processes evaluate trust, scope, confidence, and provenance.
5. The company promotes some knowledge into canonical memory.
6. Specifications are generated from that memory.
7. Software is generated, tested, and used.
8. Real-world feedback changes the knowledge system.

This loop is the foundation of an agentic company.

## What This Repository Is Building

The repository is not merely a collection of essays about ontology. It is the beginning of a design language for company intelligence.

The documents build one continuous narrative:

- [Ontology](docs/01-ontology.md) defines the categories and commitments that make structured company memory possible.
- [Epistemology](docs/02-epistemology.md) explains how claims become trusted, uncertain, rejected, superseded, or actionable.
- [Company Second Brain](docs/03-company-second-brain.md) turns ontology and epistemology into an operating model for organizational memory.
- [Agentic Knowledge Ecosystem](docs/04-agentic-knowledge-ecosystem.md) defines how AI agents participate in acquiring, transforming, validating, and applying knowledge.
- [Specification-Driven Software](docs/05-specification-driven-software.md) connects the knowledge system to generated software and iterative product development.
- [Research Agenda](docs/06-research-agenda.md) identifies the open problems required to turn this philosophy into infrastructure.
- [Glossary](docs/glossary.md) preserves shared language.
- [Knowledge Object Schema](schemas/knowledge-object.md) proposes the first structured shape for records in the second brain.
- [Knowledge Lifecycle](schemas/lifecycle.md) defines how information moves from raw input to trusted organizational memory.
- [Voice Note Seed](examples/voice-note-seed.md) shows how an initial direction-setting note can become structured knowledge.

## Design Principles

The system should be concrete, comprehensive, and cohesive.

Concrete means every philosophical distinction should eventually affect schema, workflow, software generation, agent behavior, review process, or decision quality. If a distinction never changes behavior, it is probably decorative.

Comprehensive means the system should represent more than final conclusions. It should preserve sources, context, claims, counterclaims, decisions, assumptions, rationale, versions, dependencies, failures, and revisions.

Cohesive means the documents and schemas should describe one connected system. Ontology, epistemology, agents, specifications, and software are not separate topics. They are layers of a single organizational intelligence architecture.

## Source Anchors

This work starts from three reference points:

- Stanford Encyclopedia of Philosophy, "Epistemology": https://plato.stanford.edu/entries/epistemology/
- Stanford Encyclopedia of Philosophy, "Social Epistemology": https://plato.stanford.edu/entries/epistemology-social/
- Thomas R. Gruber, "A Translation Approach to Portable Ontology Specifications": https://tomgruber.org/writing/ontolingua-kaj-1993.pdf

