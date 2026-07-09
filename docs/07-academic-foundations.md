# Academic Foundations

This document situates the repository inside existing academic work. The point is not to claim that ontological engineering appears from nowhere. The point is to show that many mature research traditions already solve parts of the problem, while the opportunity is to integrate them through a company operating lens for AI-native organizations.

Our edge is synthesis. Knowledge engineering, ontology engineering, knowledge representation, organizational memory, provenance, belief revision, design rationale, requirements engineering, and knowledge graphs all matter. Ontological engineering is the frame that connects them into one practical discipline: designing the conceptual, epistemic, temporal, and operational substrate of a company.

## Knowledge Engineering

Knowledge engineering emerged from the need to build knowledge-intensive systems. It studies how to elicit, structure, formalize, operationalize, and maintain knowledge so software can use it.

CommonKADS is one of the major methodologies in this tradition. It presents knowledge engineering as a route from organizational knowledge management through knowledge analysis and system design into knowledge-intensive software. That is close to our concern, but our emphasis shifts the center of gravity.

Traditional knowledge engineering asks: How do we model expert knowledge so a system can perform a task?

Ontological engineering asks: How do we model organizational understanding so humans and agents can continuously reason, revise, generate, and act?

The difference matters because AI-native organizations do not only build one expert system. They operate a changing network of agents, documents, decisions, code, workflows, and product specifications. The system must preserve not only task knowledge but also provenance, uncertainty, rationale, time, disagreement, and downstream software implications.

Academic anchor: CommonKADS, as described by MIT Press, covers the route from corporate knowledge management to knowledge analysis, engineering, and knowledge-intensive systems design: https://mitpress.mit.edu/9780262193009/knowledge-engineering-and-management/

## Knowledge Representation And Reasoning

Knowledge representation and reasoning asks how knowledge can be encoded so intelligent systems can reason with it. The field includes logic, semantic networks, frames, description logics, rules, production systems, and many other representational forms.

Brachman and Levesque frame knowledge representation around a powerful idea: intelligent behavior can be understood from the top down by asking what an agent needs to know and how that knowledge should be represented for reasoning.

This is directly relevant to ontological engineering. A company second brain should not only retrieve documents. It should encode enough structure that agents can reason over claims, decisions, evidence, assumptions, specifications, and artifacts.

Traditional knowledge representation often focuses on formal reasoning systems. Our version keeps that inheritance but adds organizational reality:

- not all company knowledge is formal
- much knowledge is provisional, social, and contested
- reasoning must account for trust, provenance, and lifecycle
- generated software creates feedback that changes the knowledge base
- agent memory must distinguish accepted knowledge from generated drafts

Academic anchor: Brachman and Levesque's _Knowledge Representation and Reasoning_ is a foundational synthesis for AI practitioners: https://www.sciencedirect.com/book/monograph/9781558609327/knowledge-representation-and-reasoning

## Ontology Engineering

Ontology engineering studies how to build explicit conceptual models of domains. It includes methods for ontology specification, reuse, reengineering, alignment, evaluation, and maintenance.

Gruber's definition of an ontology as an explicit specification of a conceptualization remains a useful starting point. The NeOn methodology extends the engineering view by focusing on ontology networks, reuse of resources, collaboration, dynamic evolution, scenarios, lifecycle models, and methodological guidelines.

This matters because company knowledge is not one ontology. It is an evolving ontology network:

- product ontology
- user ontology
- agent ontology
- evidence ontology
- decision ontology
- specification ontology
- artifact ontology
- feedback ontology

The company second brain needs methods for reuse, alignment, and evolution. NeOn's emphasis on ontology networks maps well to this. Our edge is applying that ontology-network thinking to company cognition and agentic software generation.

Academic anchors:

- Gruber's ontology specification work: https://tomgruber.org/writing/ontolingua-kaj-1993.pdf
- NeOn Methodology overview from the Ontology Engineering Group: https://oeg.fi.upm.es/index.php/en/methodologies/59-neon-methodology/index.html
- NeOn scenario-based methodology paper: https://journals.sagepub.com/doi/abs/10.3233/AO-150145

## Knowledge Graphs

Knowledge graphs represent entities and relationships in graph form, often combining schema, identity, context, extraction, enrichment, querying, and quality assessment. They are widely used in both academia and industry because they can integrate heterogeneous, dynamic, large-scale data.

The major academic survey by Hogan and collaborators emphasizes themes that are central for this repository: graph data models, query languages, schema, identity, context, extraction, enrichment, quality, refinement, publication, and enterprise knowledge graphs.

Ontological engineering can use knowledge graphs as an implementation substrate, but it should not be reduced to them. A graph is a representation. Ontological engineering is the discipline of deciding what should be represented, with what epistemic status, what history, what governance, and what operational consequences.

The difference:

- Knowledge graph: stores and queries connected entities.
- Ontological engineering: designs the meaning, lifecycle, trust, and actionability of those connected entities.

Academic anchor: Hogan et al., "Knowledge Graphs": https://arxiv.org/abs/2003.02320

## Provenance

Provenance studies where information came from, how it was produced, and how it changed. The W3C PROV standard and PROV-O ontology provide a formal model for representing provenance across systems and contexts.

This is crucial for agentic company memory. Without provenance, an agent output can become indistinguishable from a reviewed claim, a customer quote, a metric, or a decision. Provenance protects the knowledge base from epistemic pollution.

For ontological engineering, provenance should track:

- source
- author or agent
- time
- transformation
- derivation
- review
- promotion
- downstream usage

PROV gives us a mature foundation. Our edge is extending provenance into an operational company memory lifecycle: not only where knowledge came from, but whether it can be acted upon.

Academic anchor: W3C PROV-O Recommendation: https://www.w3.org/TR/prov-o/

## Belief Revision

Belief revision studies how a knowledge base should change when new information is introduced. It asks how to add, remove, revise, and merge beliefs while maintaining rationality and consistency. The AGM tradition is central here, distinguishing operations such as expansion, contraction, and revision.

This field is directly relevant because a company second brain is never static. New evidence can contradict old assumptions. Feedback can invalidate requirements. A decision can become obsolete. A claim can be narrowed rather than simply rejected.

Ontological engineering does not need to implement full formal belief revision on day one, but it should borrow the conceptual machinery:

- expansion: adding information without conflict
- revision: adding information while resolving conflict
- contraction: removing or weakening a belief
- merging: combining knowledge from multiple sources
- entrenchment: deciding which beliefs are harder to give up
- iterated revision: preserving history across multiple updates

Our edge is applying belief revision to organizational memory with provenance, scope, decision impact, and software dependencies. When a belief changes, the system should ask which decisions, requirements, specifications, prompts, tests, and code may now be conceptually stale.

Academic anchor: Stanford Encyclopedia of Philosophy, "Logic of Belief Revision": https://plato.stanford.edu/entries/logic-belief-revision/

## Organizational Memory

Organizational memory research studies how organizations store and use past information, decisions, interpretations, and experience. Walsh and Ungson argued that organizational memory was fragmented and underdeveloped as a concept. Stein and Zwass later framed organizational memory information systems around functions such as acquisition, retention, maintenance, search, and retrieval.

This is one of the closest academic traditions to our "company second brain" idea. The difference is that AI agents change the operating conditions. The organization no longer only needs to preserve information for human retrieval. It needs memory that agents can read, write, critique, apply, and revise under governance.

Ontological engineering upgrades organizational memory by adding:

- explicit ontology
- epistemic status
- provenance
- agent roles
- specification generation
- artifact traceability
- conceptual debt detection
- feedback-driven revision

Academic anchors:

- Walsh and Ungson, "Organizational Memory": https://www.jstor.org/stable/258607
- Stein and Zwass, "Actualizing Organizational Memory with Information Systems": https://pubsonline.informs.org/doi/10.1287/isre.6.2.85

## Design Rationale And IBIS

Design rationale research tries to capture why design decisions were made. IBIS, the Issue-Based Information System tradition, represents design discussion through issues, positions, and arguments. gIBIS brought this into hypertext systems for exploratory policy and design discussion.

This matters because company wisdom often lives in rationale, not in final artifacts. A decision record without alternatives, tradeoffs, objections, and unresolved issues is too thin. IBIS gives a precedent for representing messy deliberation as structured, navigable knowledge.

Ontological engineering should absorb this lesson. It should represent:

- questions
- candidate answers
- arguments for and against
- decisions
- rationale
- unresolved tensions
- later feedback

Our edge is connecting design rationale to agentic memory and generated software. A design rationale should not sit in an archive. It should constrain specifications, guide agents, and trigger review when assumptions change.

Academic anchors:

- IBIS overview: https://en.wikipedia.org/wiki/Issue-based_information_system
- gIBIS paper reference summary: https://eric.ed.gov/?id=EJ395526

## Requirements Engineering And Traceability

Requirements engineering studies how to elicit, analyze, specify, validate, and manage requirements. Goal-oriented requirements engineering, including KAOS, models goals, constraints, assumptions, objects, events, actions, agents, conflicts, responsibilities, and operationalization.

This is extremely close to specification-driven software. KAOS already treats requirements as more than tickets. It connects goals, agents, objects, operations, conflicts, and behavior. Requirements traceability adds the need to follow requirements through design, implementation, verification, and evolution.

Ontological engineering extends this into the AI-native context:

- requirements derive from claims, evidence, assumptions, and decisions
- specifications model both user and agent interactions
- generated artifacts link back to specification versions
- evaluation results feed back into the knowledge base
- conceptual debt is detected when artifacts depend on superseded knowledge

Academic anchors:

- KAOS goal-driven requirements engineering: https://webperso.info.ucl.ac.be/~avl/gore.php
- Requirements traceability survey: https://link.springer.com/article/10.1007/s00766-023-00408-9
- Ontology-based requirements engineering example: https://link.springer.com/article/10.1007/s10270-023-01115-3

## The Reframe: Ontological Engineering As Integration Layer

Academia has already produced strong components:

- knowledge engineering gives methods for eliciting and operationalizing knowledge
- knowledge representation gives formal reasoning foundations
- ontology engineering gives conceptual modeling and ontology lifecycle methods
- knowledge graphs give scalable entity-relationship infrastructure
- provenance gives origin and derivation semantics
- belief revision gives rational change operations
- organizational memory gives the company-level memory problem
- design rationale gives the structure of deliberation
- requirements engineering gives the bridge from goals to systems

The gap is that these are usually treated as separate disciplines. AI-native organizations need them as one operating system.

Ontological engineering is that integration layer.

It asks:

- What exists in the company's world?
- How does the company know?
- What changed over time?
- Which agents can act on which knowledge?
- Which decisions depend on which claims?
- Which specifications derive from which beliefs?
- Which artifacts implement which specifications?
- Which feedback should revise the ontology?

This is the edge. The field is not "we invented ontologies." The field is "we apply ontological thinking to the whole lifecycle of company cognition, agent governance, and software generation."

## Confidence Upgrade

This research increases confidence because it shows the idea has both depth and white space.

Depth: almost every component has serious academic precedent.

White space: the integrated AI-native company operating discipline is not yet packaged as a cohesive practice.

The thesis is therefore stronger:

Ontological engineering is the discipline of designing the explicit conceptual, epistemic, temporal, and operational structure that lets an AI-native company remember, reason, decide, generate, and revise coherently.

