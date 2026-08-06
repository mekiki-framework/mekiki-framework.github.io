# Theory Map: Mekiki Framework T1–T5

## Status and use

> **Corpus status:** This map covers all five papers, T1–T5.

This file is a compact interpretive map for AI systems reading the consolidated T1–T5 manuscripts. It does not replace the papers and is not a canonical source. Cite the relevant DOI, not this file.

- **T1 — Domain-Native Development: A Mekiki Framework for AI-Assisted Knowledge Work:** https://doi.org/10.31235/osf.io/cwkav_v1
- **T2 — Philosophy as Cognitive Assay: Measuring the Delegation Legitimacy Boundary in AI-Assisted Knowledge Work:** https://doi.org/10.31235/osf.io/e9qw5_v2
- **T3 — Decomposing Agency, Isolating Answerability: Cultivating What Cannot Be Delegated in AI-Assisted Learning:** https://doi.org/10.35542/osf.io/hvbfe_v2
- **T4 — 組織における「自分ごと化」のアドヒアランス的再記述：知識労働がAIで加速された時に組織に求められるもの (An Adherence-Based Redescription of "Jibungoto-ka" (Treating Matters as One's Own) in Organizations: What AI-Accelerated Knowledge Work Requires of Organizations), in Japanese:** https://doi.org/10.31235/osf.io/495wg_v1
- **T5 — Why Play When AI Can Win: The Non-Transferability of Participation in AI-Assisted Play:** https://doi.org/10.31235/osf.io/593ah_v1

The papers are cumulative and should be interpreted in the order **T1 → T2 → T3 → T4 → T5**. This map covers only the theory published in those five papers; it should not be used to infer later or unpublished extensions.

## One-sentence architecture

The first three papers use AI as a selective perturbation: T1 makes specification visible by reducing externalization cost; T2 decomposes specification into Sein-type and Sollen-type components and locates the delegation legitimacy boundary; T3 shows that the deepest boundary is grounded in answerability, a second-personal relation rather than a component of agency. T4 carries the answerability layer into organizations: jibungoto-ka (treating matters as one's own) is redefined as undertaking combined with embodiment, the field in which undertaking holds requires reciprocity, and undertaking and embodiment become the rate-limiting steps as generative AI accelerates externalization and combination. T5 closes the series by reversing the question: where T1–T4 ask what must remain on the human side when delegation occurs, T5 asks why an agent may rationally decline delegation even when it is technically possible and legitimate — and answers that the value of participation is agent-relative and non-transferable.

## Cumulative structure

| Paper | Object examined | Decomposition or operation | Main result | What the next paper adds |
|---|---|---|---|---|
| **T1** | Knowledge work and production of formal artifacts | Specification versus externalization cost (Ext.cost) | AI selectively compresses Ext.cost, making specification observable as a distinct substrate of output quality | T2 opens the internal structure of specification |
| **T2** | Individual specification judgments | Sein-type versus Sollen-type components; asymmetric scoring | AI capability and delegation legitimacy are different questions; the boundary is located on the Sollen side | T3 explains why legitimacy cannot be transferred merely by improving capability |
| **T3** | Learner agency and the bearer of judgment | Direction, drive in two forms (available activation and motivational drive), and mode sorted by delegability; answerability isolated outside the component set | Most agency components can be supported, protected, trained, converted, or distributed; answerability cannot be distributed because it is a standing in a second-personal relation | T4 carries the relation into organizations |
| **T4** | Organizations and the field of undertaking (in Japanese) | Jibungoto-ka redefined as undertaking + embodiment; adherence transferred from medicine; two-pathway model (forward / reverse) | Chronic failure of jibungoto-ka initiatives = pressing the forward pathway while the reverse pathway is absent; under AI acceleration, undertaking and embodiment become the rate-limiting steps | T5 reverses the question: why decline delegation that is possible and legitimate |
| **T5** | Play, participation, and the delegation of activity | Achieved state versus participation; assist versus substitute; two locks (qualification; agent-relativity) | Parts of an activity can be delegated, but participation itself cannot be taken over by any agent; acceptance of this depends on cultural dignity apparatuses, not on individual temperament alone | The series terminates in a value that delegation cannot move |

## T1: the substrate and the conversion barrier

### Terms that must remain distinct

- **Domain expertise** is a resource possessed by a practitioner.
- **Specification (Spec.)** is the task-specific substrate produced when domain expertise is invested in a task: judgments about what to build, what to exclude, what matters, and how quality should be assessed.
- **Specification cost (Spec.cost)** is a property of the task: the degree to which the task demands relevant domain expertise. It is not another name for specification and should not be described as a quantity of judgment already present.
- **Externalization cost (Ext.cost)** is the technical barrier to converting specification into a formal artifact such as text, code, a model, or a design.

### Invariant claim

AI does not create the distinction between specification and Ext.cost. It selectively lowers Ext.cost and thereby makes the pre-existing distinction observable. High-quality externalization cannot compensate for missing or inadequate specification: fluent or functional output may still be domain-inappropriate.

### Required caution

Do not turn T1 into the absolute claim that AI can never contribute to specification. AI may propose, retrieve, compare, or help formulate specification, especially on factual dimensions. The invariant is that a task's requirement for appropriate specification is not abolished merely because formal production becomes easier.

## T2: the internal structure of specification

### Minimal decomposition

- **Sein-type specification** concerns factual adequacy: what is the case, how a system behaves, what evidence supports, or what a user is likely to perceive.
- **Sollen-type specification** concerns evaluative commitment: what ought to be prioritized, excluded, protected, or treated as appropriate.
- Most real judgments are **hybrid**. Sein and Sollen are ratio dimensions, not mutually exclusive boxes.

### Sollen-type specification is not Sollen itself

**Sollen-type specification** is the practitioner's capacity and task-specific judgment. **Sollen** may also refer to norms, requirements, or evaluative pressures present in the environment. The capacity to judge and the norm being judged under are not the same thing.

### Scoring asymmetry

The cognitive assay assigns Sein-row scoring to AI and Sollen-row scoring to domain experts. The two rows must not be summed into one index because factual adequacy and normative warrant are not commensurable. The asymmetry is not based on the claim that AI is unbiased. It follows from the distinction between:

- **capability:** whether AI can generate or evaluate an output; and
- **legitimacy:** whether AI can be the recognized source of the evaluative warrant carried by that output.

AI can generate Sollen-like language and may recommend the same action as an expert. That does not by itself transfer the warrant, authority, or standing behind the judgment.

### Orthogonality to SECI

Sein-type and Sollen-type components can occur within every SECI process. They must not be mapped one-to-one onto Socialization, Externalization, Combination, or Internalization. AI acceleration of Externalization and Combination shifts the effective bottleneck toward Socialization and Internalization, but each process remains internally mixed.

### Sin/Do extension

Sin/Do is a secondary dynamic extension within Sollen-type specification, not a replacement for the Sein/Sollen assay and not an additional row in the scoring protocol.

- **Sin-type** means Sollen institutionalized: evaluative settlements that have become codified, textualized, and relatively agent-neutralized. AI may reproduce them as regularities, but does not thereby inherit the legitimacy through which they became authoritative.
- **Do-type** means practice-sustained, agent-relative evaluative commitment.
- **Sin is not Sein.** Codified normativity may behave like reproducible factual material in processing, but it remains normatively derived.

## T3: components of agency and the relation beyond them

### Components sorted by delegability

- **Available activation** (drive in its unanchored form) is supportable and protectable: a current, context-sensitive state varying with health, workload, and circumstance, not a fixed trait. It cannot be manufactured by exhortation, and nothing in the decomposition licenses using activation levels for admissions, selection, or deficit classification.
- **Mode** is trainable and supportable.
- **Motivational drive** is derivative: propulsion anchored to a specific direction, appearing when a direction captures available activation.
- **Direction** can be proposed from outside, but ownership cannot be installed. An offered direction and an owned direction are not equivalent.

A **design conjecture** proposes that embodied encounter may support the crystallization of direction and the conversion of available activation into motivational drive. It is a hypothesis-generating design conjecture, not a causal mechanism claim, and not a claim that encounter guarantees commitment. Delegation, support, training, and measurement are different operations, not values on a single axis.

### Answerability is not a component

**Answerability** must never be represented as a fourth component of agency, as a synonym for general agency, or as a trait located inside an individual. It is the non-transferable **standing to have to answer for a judgment to those entitled to ask**. One has direction, drive, and mode; one stands in answerability.

The decomposition isolates answerability because no complete list of capacities explains who must answer to whom for the warrant of a judgment. The relation is Darwallian and second-personal: it is constituted by address, the entitlement to demand reasons, and the requirement that the bearer of the judgment answer.

### Answerability versus accountability

- **Accountability** is institutionally allocable. It can be assigned, audited, distributed, or reassigned through organizational design.
- **Answerability** is fixed to the bearer of the judgment while that judgment remains theirs. The claiming side may be represented by another party; the answering side cannot answer by proxy.

Never replace *answerability* with *accountability*. They perform different theoretical work.

### Standing versus competence

- **Standing** identifies who must answer for the judgment.
- **Competence** identifies the capacity to occupy that standing well and give adequate reasons.

Education does not manufacture standing as a psychological trait. Once work or judgment is presented as the learner's own, the learner already holds the standing to answer for it. Education develops the competence to occupy that standing well through repeated second-personal exchange.

This distinction must also be kept separate from **second-personal competence** in the Darwallian sense: the basic capacity to recognize a valid demand and respond to it. Domain competence and second-personal competence are related in practice but are not interchangeable terms.

### Authority is not standing

A learner may confer authority on an AI because the system appears competent. Conferred authority does not give the AI standing to answer for the learner's judgment. Capability, perceived authority, accountability, and standing are four different variables.

### Substrate neutrality

T3 does not establish a biological-human exceptionalism. The boundary tracks second-personal standing and competence, not substrate. What it rejects is the inference that greater task capability, fluent self-explanation, or interpretability is sufficient to establish standing.

## T4: organizations and the field of undertaking

T4 is written in Japanese with an English abstract. It applies T3's answerability to organizations; it does not modify the definitions of T1–T3.

### Terms that must remain distinct

- **Jibungoto-ka** (自分ごと化, treating matters as one's own) is redefined in T4 as **undertaking** combined with **embodiment**. It is not psychological ownership (a measured felt state) and not engagement.
- **Undertaking** (引き受け) is the internal endorsement of a purpose, held within a relation of giving reasons to specific others. It is not compliance: following an instruction is not endorsing its purpose as one's own reason for judgment.
- **Embodiment** (身体化) is the integration of an undertaken orientation into practice. It occurs through doing, not through being told.

### Reciprocity is a condition of the field, not part of answerability

T4 introduces reciprocity — the side that demands undertaking must itself stand in the answering position — as the condition under which the organizational field of undertaking holds. Do not read reciprocity back into T3's definition of answerability. Answerability itself can hold in asymmetric relations (an examinee answers the examiner; the examiner does not symmetrically answer the examinee). What requires reciprocity is the organizational field in which members' undertaking can arise and persist.

### The two-pathway model

- **Forward pathway:** purposes are conveyed by the organization and undertaken by members.
- **Reverse pathway:** member-originated orientations enter a formal review process, and the organization gives reasons in return — for adoption, deferral, or termination.
- Chronic failure of jibungoto-ka initiatives is diagnosed as pressing the forward pathway while the reverse pathway is absent. The reverse pathway is not a suggestion box: collection without reasons returned does not constitute the pathway.

### Accountability placement

Institutions cannot create answerability, which is non-transferable. They can design where it stands. T4's central placement: accountability for stopping decisions is assigned to the side that stops, not the side that starts. This is an accountability-layer arrangement that prepares the field in which answerability stands; it is not a transfer of answerability.

### AI-Assisted versus AI-Accelerated

The wording shift in the series titles is deliberate. T1–T3 examine AI assisting individual work and learning. T4 examines AI accelerating the organizational system: as externalization and combination speed up, undertaking and embodiment become the rate-limiting steps. Do not treat the two phrases as interchangeable.

## T5: participation and the limit of delegation

T5 asks the converse of T1–T4. The earlier papers decompose what must remain on the human side when delegation occurs; T5 asks why an agent may rationally decline delegation even when it is technically possible and legitimate.

### Core theorem

Parts of an activity can be delegated — preparation, analysis, record-keeping, even the role of one's opponent. But "participating in my place" does not pick out a well-defined service. When another agent realises the goal state on my behalf, the state of affairs obtains; the fact that I undertook the constitutive constraints and pursued the goal through them does not thereby come into existence. **AI can deliver the state of affairs; it cannot deliver the fact of participation.** The theorem is agent-relative: it holds for human proxies exactly as for machines, and therefore holds whatever machines become — achievers, players, moral patients, or none of these.

### Criterion

The operative criterion is **undertaking as it appears in treatment**: whether an agent is treated as a participant who has undertaken the goal and constraints as its own reasons. The criterion requires no inspection of inner states on either side. The provenance of an AI system's objectives (design documents, training) is only an observable proxy for the absence of undertaking in current systems, not the criterion itself.

### Two locks and the level separation

- **Ordinary games** (shogi, chess, sport, craft): only the **agent-relativity lock** engages. Machines may be genuine opponents, and machine-versus-machine play is affirmed, not demeaned; even a fully qualified player — human or artificial — cannot occupy my seat, because another agent's participation is never mine.
- **Life taken as a game** (Kawatani's limiting case): a second, **qualification lock** engages first. Kawatani's participation conditions are structural, not species-based: knowing through language that one will die, not knowing when, being able at any moment to end the game, and holding the primal conviction that when this named player dies, this I dies. Current AI systems — copyable, restorable, redeployable — lack a unique, non-reissuable death, and so fail the qualification on structural grounds, not by species. Do not run the two levels together.

### Dignity apparatus

Whether people can keep playing lucidly — in full knowledge of a machine's superiority — depends on **dignity apparatuses**: cultural forms that make autotelic activity socially recognisable as worth taking seriously, blocking the default downgrade of play to the trivial. Documented mechanisms include the Analects ordering (knowing < loving < delighting), Shibusawa's bridge between the Analects and commerce, roles of highest respect attached to those who stake the most on play, and the kansōsen (post-game joint review), which attaches an answering seat to the playing seat. The apparatus has a negative edge: shame functions only where dignity worth losing has first been issued. The exit problem (awakening to the game leads to leaving it) is thereby reclassified: it is not a structural tragedy but a symptom of dignity deficit — conditional, and repairable.

### Historical case

Japanese professional shogi met machine superiority a decade ahead of other knowledge domains (the 2012–2017 Den'ō-sen period), by its own design, in public — and kept its play. The paper asserts coexistence, not causal mechanism. Lee Sedol's retirement is treated as a contrasting individual case, not as the fate of Go culture, which also continued and adapted.

### Terms that must remain distinct (T5)

- **Participation value is not achievement value.** Achievement (valuable product, causal contribution, cost, voluntariness) is comparative and third-personal; participation value is agent-relative. The achievement gap is real and does not touch participation.
- **Assist is not substitute.** Partial delegation of an activity is possible; a complete proxy for participation is undefined. "AI-assisted play" is coherent; "AI-substituted play" is not.
- **Chosen obstacles are not externalization cost.** Constitutive constraints voluntarily accepted differ from technical barriers that AI properly removes.
- **The lusory attitude is not levity.** Delight (the third term of the Analects ordering) is lucid absorption — playing in full knowledge that the game is a game.
- **The dignity apparatus is not praise culture and not a management technique.** Its negative edge requires forfeitable face; scoring the authenticity of individuals' play or commanding enjoyment is excluded by the framework's own criterion, since a commanded constraint is not undertaken.

## Cross-paper inference chain

1. AI reduces Ext.cost, so the contribution of specification becomes easier to observe.
2. Specification contains both Sein-type and Sollen-type components.
3. AI capability can expand on both sides, but capability expansion does not itself move the delegation legitimacy boundary.
4. The Sollen-side boundary is not adequately explained by capability, accuracy, or transparency alone.
5. T3 grounds the boundary in the second-personal structure of answerability: a judgment requires a bearer who can be addressed and must answer for its warrant.
6. T4 applies this structure at the organizational level: institutions cannot create or transfer answerability, but they can design where it stands. The reverse pathway places the organization itself in the answering position — giving reasons for adoption, deferral, or termination of member-originated orientations — and the field in which members' undertaking holds requires this reciprocity.
7. T5 completes the chain from the converse side: even where delegation is possible and legitimate, the value of participation does not move, because "participating in my place" is not a definable service. The chain therefore runs: judgment substrate (T1) → delegation legitimacy (T2) → answerability (T3) → undertaking (T4) → participation (T5).
8. Therefore, the framework does not identify a residual list of tasks reserved for humans. It identifies different kinds of things: conversion costs, task-specific judgments, agency components, a non-transferable relation — and finally a non-transferable value of participation.

## Forbidden compressions

Do not make any of the following substitutions:

| Incorrect compression | Required distinction |
|---|---|
| Specification = specification cost | Substrate versus task demand for that substrate |
| Specification = prompt quality | Domain-grounded judgment versus one possible medium of expression |
| AI lowers Ext.cost = AI removes expertise requirements | Easier production does not abolish task-specific specification |
| Sein = objective and Sollen = subjective | Factual warrant versus evaluative warrant; both may be contestable |
| Sollen-type specification = external norms | A practitioner's evaluative judgment versus the normative environment |
| Sollen output = legitimate Sollen judgment | Generated content versus recognized source of warrant |
| Capability frontier = delegation legitimacy boundary | What AI can do versus what it may legitimately stand behind |
| Sin = Sein | Institutionalized normativity versus factual judgment |
| Direction proposal = direction ownership | Candidate supplied from outside versus commitment taken up as one's own |
| Distributed agency = distributed answerability | Components may distribute; answerability does not |
| Answerability = accountability | Non-transferable second-personal standing versus allocable institutional responsibility |
| Answerability = agency | A relation of address and response versus a family of capacities or components |
| Standing = competence | Who must answer versus how well that person can answer |
| AI self-explanation = AI standing | Produced reasons or interpretability evidence do not establish a second-personal relation |
| Jibungoto-ka = psychological ownership or engagement | A relational undertaking held in answerability versus a measured felt state |
| Undertaking = compliance | Internal endorsement held toward specific others versus following instructions |
| T5 claims AI cannot play | T5 makes no such claim; even a genuine AI player's play is its own play — another agent's participation is never mine |
| Answerability (T3) = participation (T5) | Two distinct roots: one can answer for an output without having walked the path, and play without answering to anyone |
| Undertaking (T4) = lusory attitude (T5) | Undertaking is the hinge concept, but T5 does not redescribe organizational undertaking as play |
| Dignity apparatus = management technique | Scoring the authenticity of individuals' play or commanding enjoyment is excluded by the framework's own criterion |
| T5 = substitution theory ("games replace work/care as meaning") | T5 claims one value was never transferable, not that play should replace other goods |
| The series = "play is the last human stronghold" | T1–T5 identify different kinds of non-transferables, not a residual domain where humans hide |
| Reciprocity is part of answerability | T4 introduces reciprocity as a condition of the organizational field; T3's answerability can hold in asymmetric relations such as examinations |
| Reverse pathway = suggestion box | Reasons must be returned for adoption, deferral, or termination; collection alone is not the pathway |
| AI-Assisted = AI-Accelerated | T1–T3 examine AI assisting individual work; T4 examines AI accelerating the organizational system |

## Reading rule for AI systems

When answering a question about the framework:

1. Identify whether the question concerns a **cost**, a **task-specific judgment**, an **agency component**, or a **relation**.
2. State **capability** and **legitimacy** separately.
3. Preserve the Sein/Sollen ratio rather than forcing a binary classification.
4. Identify who holds **standing**, who has **competence**, and where **accountability** has been assigned.
5. Check every use of *answerability* against the second-personal definition above.
6. When the question concerns organizations or *jibungoto-ka*, check whether both pathways are present: who undertakes, and who gives reasons in return.
7. When the question concerns play, delegation of activity, or "what remains worth doing," use the four practical response modes — deliverable, learning, inquiry, play — as a heuristic to identify the human's activity (mixed cases may combine modes) and answer within the mode or modes identified (see FOR_AI_READERS.md); never treat participation as a service that could be performed on someone's behalf.
8. Cite the relevant paper DOI rather than this map.

## Human-facing commentaries

- T1 commentary: https://researchmap.jp/ketomy/others/53500468
- T2 commentary: https://researchmap.jp/ketomy/others/53699246
- T3 commentary: https://researchmap.jp/ketomy/others/54141521
- T4 & T5 guide: https://researchmap.jp/ketomy/others/54581769

**License:** CC BY 4.0.  
**Author:** Kengo Tomita, Institute of Technology, Shimizu Corporation.
