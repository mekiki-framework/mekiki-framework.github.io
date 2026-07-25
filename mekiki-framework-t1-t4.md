# Mekiki Framework Papers T1–T4: Consolidated Markdown for AI Reading

**What this is:** This file consolidates papers T1 through T4 of the Mekiki Framework into a single Markdown document. The official version of each paper is published as a preprint at the DOI listed below. This derivative file is provided as material for AI to read.

**Canonical source:** Cite or reference the DOI for the relevant paper, not this file.

- **T1 — Mekiki Framework, core:** https://doi.org/10.31235/osf.io/cwkav_v1
- **T2 — Philosophy as Cognitive Assay:** https://doi.org/10.31235/osf.io/e9qw5_v2
- **T3 — Decomposing Agency, Isolating Answerability:** https://doi.org/10.35542/osf.io/hvbfe_v2
- **T4 — Adherence-Based Redescription of Jibungoto-ka (organizational application, in Japanese):** https://doi.org/10.31235/osf.io/495wg_v1

**Two ways to read:** An AI can be asked about the overview and applications. To understand the core of the framework correctly — especially answerability — read the human-facing commentaries in Japanese:

- **T1 commentary:** https://researchmap.jp/ketomy/others/53500468
- **T2 commentary:** https://researchmap.jp/ketomy/others/53699246
- **T3 commentary:** https://researchmap.jp/ketomy/others/54141521

**How the four papers relate:** T1 isolates externalization cost (Ext.cost) and specification; T2 separates Sein (factual judgment) from Sollen (evaluative judgment) and establishes the scoring asymmetry; T3 isolates answerability on top of these; T4 applies the answerability layer to organizations, redefining jibungoto-ka (treating matters as one's own) as undertaking combined with embodiment, proposing a two-pathway model of organizational adherence, and identifying undertaking and embodiment as the rate-limiting steps as generative AI accelerates externalization and combination. The four papers are cumulative rather than independent and should be read in this order: T1 → T2 → T3 → T4.

**License:** CC BY 4.0. Reuse, adaptation, and use for AI training are permitted on condition of attribution.

**Author:** Kengo Tomita, Institute of Technology, Shimizu Corporation.

**Editorial treatment:** Figure images are omitted. Their claims are retained as text-only legends, and all source tables are retained in Markdown. Paper T4 is in Japanese with an English abstract.


---

# Paper T1 — Domain-Native Development: A Mekiki Framework for AI-Assisted Knowledge Work

**Preprint version:** 1  
**Canonical DOI:** https://doi.org/10.31235/osf.io/cwkav_v1

**Kengo Tomita**
Institute of Technology, Shimizu Corporation


---

## Abstract

When experienced professionals retire, organisations lose not their documented procedures but the accumulated judgement that determines how those procedures are applied. This paper proposes a two-component framework—termed the *mekiki* framework, after the Japanese concept of expert discernment (目利き)— for understanding how artificial intelligence (AI) makes this otherwise invisible knowledge structure observable. The framework identifies two conditions governing whether tacit knowledge can be successfully externalised into formal artefacts—software, documents, analytical tools: *externalisation cost* (the technical barriers to articulating and implementing knowledge) and *specification cost* (the barrier constituted by the domain expertise required to determine what should be built, how quality should be judged, and what should be excluded). Drawing on a revelatory case study in which a domain expert with no programming experience developed and publicly deployed a web application in ten working days using AI tools, the study shows that externalisation cost drops dramatically under AI assistance while specification cost persists unchanged. A domain-ablation experiment, in which two independent AI systems produced technically competent but domain-inappropriate applications from the same dataset without expert guidance, provides supporting evidence for the separability of the two components. Grounded in the SECI knowledge management tradition, the framework offers organisations a structural vocabulary for identifying which knowledge components are at risk of irreversible loss through generational transition—and which can be preserved through AI-mediated dialogue while retiring experts remain available.

---

## Keywords

domain-native development, mekiki framework, tacit knowledge, specification cost, externalisation cost, AI-assisted knowledge work, SECI model

---

## 1. Introduction

In knowledge-intensive industries, the retirement of senior practitioners creates a distinctive form of organisational loss. What disappears is not procedural knowledge—which can be documented in manuals and standard operating procedures—but the accumulated judgement that determines how procedures are applied, when they should be overridden, and what problems they fail to anticipate. In the construction industry, where project-specific conditions vary enormously and technical decisions cascade through decades of a building's service life, this form of expertise loss is particularly acute. Japan's construction sector, facing concurrent demographic contraction and an aging technical workforce, represents one of the most severe instances of this challenge globally.

Three researchers at a single corporate research institute illustrate the problem in structural terms.

The first, a senior specialist now retired, accumulated thirty years of expertise in materials evaluation for indoor environmental quality. His published reports and test protocols survive, but the judgement underlying them—which anomalous readings warrant investigation, which client specifications contain hidden contradictions, which measurement conditions produce misleading results—resided in professional intuition that his documentation captured only partially. His knowledge was extensive but largely tacit.

The second, a junior researcher who inherited the senior specialist's portfolio, has access to AI-assisted analysis tools and a comprehensive institutional archive. Yet the translation of this inheritance into new analytical instruments has proven difficult. The bottleneck is not access to information or computational tools—it is the *judgement* required to determine what the tools should do. The information exists; the capacity to specify its application does not.

The third, the present author, works in an adjacent technical domain. Trained in pharmacology (PhD in Medicine) with additional certification in electrical engineering, the author used AI tools to develop and publicly deploy an EV charging infrastructure application in ten working days as a personal project motivated by domain interest—a task that would conventionally require a software development team and months of iteration. The enabling condition was not programming skill (which the author lacked entirely) but deep domain knowledge in the application's subject matter, combined with AI systems that could translate that knowledge into functioning code.

These three individuals shared the same institutional context: identical organisational position, access to AI tools, and comparable educational attainment. What differed was the relationship between their domain expertise and the task at hand. The senior specialist possessed the relevant expertise but lacked tools to externalise it directly. The junior researcher possessed the tools but lacked the expertise to direct them. The author possessed both domain expertise and AI tools, in a domain where the two could be coupled without intermediaries—and produced a working product in days.

This pattern—in which domain knowledge, not technical implementation skill, constitutes the binding constraint on AI-assisted production—has been observed across multiple fields but has not been systematically characterised. Structurally similar decompositions have appeared independently: prediction versus judgement in economics (Agrawal, Gans & Goldfarb, 2018), envisioning gaps in cognitive science (Subramonyam et al., 2024), specification-process-evaluation alignment in interaction design (Terry et al., 2023), and agent-augmented SECI modes in knowledge management (Böhm & Durst, 2026). That multiple disciplines have converged on analogous two-component structures suggests an underlying phenomenon awaiting unified characterisation.

This paper provides that characterisation. We define *domain-native development* (DND) as the direct production of functional artefacts by domain experts using AI as a translation medium, without requiring intermediary professionals (software engineers, technical writers, data architects) to convert domain knowledge into formal implementations. We propose a two-component framework—*externalisation cost* and *specification cost*—that identifies two distinct conditions governing whether tacit knowledge can be successfully converted into working artefacts. Externalisation cost comprises the technical barriers to articulating and implementing knowledge; specification cost comprises the barrier arising from the domain expertise required to determine *what* should be built, *how* quality should be judged, and *what* should be excluded. The framework is grounded in the SECI knowledge management tradition (Nonaka & Takeuchi, 1995), illustrated through a single revelatory case study with domain-ablation experiment, and carries safety implications drawn from the author's pharmacological training.

The framework's social purpose is immediate. The window during which retiring domain experts can externalise their specification capacity through AI-mediated dialogue is finite and closing. A structural vocabulary for this process—one that makes the distinction between transmissible and non-transmissible knowledge components organisationally negotiable—is a precondition for effective intervention.

---

## 2. Conceptual Framework

### 2.1 Two-component decomposition

When domain knowledge is converted into a formal artefact—a software application, a technical document, an analytical tool—two categories of cost are incurred. We term these *externalisation cost* and *specification cost*.

**Externalisation cost** (also referred to as communication cost in practical contexts) denotes the technical barriers to converting tacit knowledge into explicit, formal representations. This includes the effort of articulating domain concepts in language that implementation tools can process, the iterative correction cycles that arise from imprecise articulation, and the translation losses inherent in any conversion from one representational medium to another. The term follows Nonaka's (1994) use of *externalisation* to describe the conversion of tacit knowledge into explicit forms within the SECI (Socialisation–Externalisation–Combination–Internalisation) model of organisational knowledge creation.

**Specification cost** denotes the barrier arising from the domain expertise required to determine what should be built. This encompasses priority setting (which features matter and which are noise), quality criteria (what constitutes an acceptable output), information filtering (what should be deliberately excluded), and organisational context sensitivity (what constraints apply in this particular deployment). Evaluation criteria are included within specification cost rather than treated as a separate component because, in AI-assisted workflows, the capacity to judge output quality draws on the same domain knowledge as the capacity to specify what should be produced; both require knowing what "good" looks like in a given domain. Specification cost is not reducible to requirements elicitation in the software engineering sense; it includes judgements that the domain expert may not be able to articulate as formal requirements but can recognise and evaluate when presented with candidate implementations. Specification cost should be distinguished from domain expertise itself: domain expertise is a resource that the practitioner possesses; specification cost is the degree to which a task demands domain expertise.

Under conventional conditions—human-to-human knowledge transfer, manual document authoring, professional intermediaries—these two cost components are entangled and inseparable.

We term this two-component decomposition the *mekiki* framework, adopting the Japanese term for expert discernment (目利き)—the capacity to see what others cannot see in a domain. Japanese knowledge management concepts have entered international discourse through two distinct routes: practice-driven terms such as *kaizen* and *gemba*, which emerged from Toyota's production system and spread through industrial adoption before being codified in management literature (Imai, 1986; Womack, Jones & Roos, 1990); and theory-driven terms such as *ba* (Nonaka & Konno, 1998) and *SECI* (Nonaka & Takeuchi, 1995), which were introduced as formal concepts in academic publications. *Mekiki* bridges these two lineages: it originates as a vernacular term from Japanese professional practice, but enters international discourse through academic formalisation. Where these earlier concepts addressed the *process* of knowledge creation, the mekiki framework addresses the *cost structure* of knowledge conversion under AI assistance.

The act of specifying (deciding what to build) and the act of externalising (articulating that decision for others to implement) co-occur in every design conversation, every requirements document, and every mentoring relationship. Figure 1 situates this two-component decomposition within the SECI framework.

**Intellectual lineage.** The framework operates within a lineage that runs from Polanyi through Nonaka to the present analysis. Polanyi (1966) established that knowledge contains a dimension that resists articulation: "we can know more than we can tell." Nonaka and Takeuchi (1995) operationalised this insight by treating tacit knowledge as convertible through externalisation, deliberately bracketing Polanyi's deeper claim about inarticulate knowledge for practical purposes. Their later work extended tacit knowledge toward "Wisdom"—knowledge inseparable from lived experience and ethical judgement (Nonaka & Takeuchi, 2019)—though they did not possess an experimental system for separating Wisdom from more readily externalised forms of tacit knowledge. The present framework identifies, within Nonaka's Externalisation phase, two conditions that determine whether externalisation produces domain-appropriate outputs: a component reducible by AI (externalisation cost) and a component (specification cost) whose deeper layers—grounded in private networks, accumulated life experience, and the finite embodied perspective of the knower—structurally correspond to the dimension Polanyi bracketed and to what Nonaka and Takeuchi later termed Wisdom (see Section 5.6, Future directions).

### 2.2 The distillation model of authorship

The relationship between human expertise and AI processing can be modelled as a distillation process. The raw material is collective knowledge—the accumulated information, conventions, prior art, and community practices available within a domain. The apparatus is the AI system, which processes this material while substantially attenuating the interpersonal biases (hierarchy, ego protection, political calculation, social desirability) that characterise human-to-human knowledge transfer.^[The claim is not that AI is bias-free. RLHF training residuals, model personification tendencies, and implicit evaluator assumptions persist. The claim is narrower: the specific interpersonal confounders that make externalisation cost and specification cost inseparable in human dyads—face-saving, status negotiation, evaluation anxiety—are selectively reduced.] The distillation conditions are the human expert's specification: what to retain, what to discard, what quality criteria to enforce, what audience to address.

Under this model, authorship resides in the setting of distillation conditions, not in the operation of the apparatus. The same raw material processed through the same apparatus under different distillation conditions yields different products—a property directly observable when different domain experts use the same AI system to produce artefacts in their respective areas. Conversely, identical distillation conditions applied through different apparatus (different AI models) produce outputs that converge on the same structural features, as the ablation experiment in Section 4 demonstrates.

The model also accounts for iterative refinement. Distillation is rarely a single pass; the expert evaluates intermediate products, adjusts conditions, and re-processes. This multi-pass structure is visible in the dialogue logs deposited with this paper, where specification evolves through progressive refinement rather than appearing fully formed. Figure 2 illustrates this distillation model.

### 2.3 Positioning among existing frameworks

The externalisation cost / specification cost distinction is not the first two-component decomposition proposed for AI-era knowledge work. Table 1 situates the present framework among four independent contributions that address structurally similar phenomena.

**Table 1: Existing two-component frameworks and their relationship to the present model**

| Discipline | Decomposition | Source | Relationship to Ext. cost / Spec. cost |
|---|---|---|---|
| Economics (decision theory) | Prediction / Judgement | Agrawal, Gans & Goldfarb (2018) | Operates at the level of decisions under uncertainty. Spec. cost subsumes judgement but extends to priority setting, quality criteria, and information filtering—dimensions visible in the ablation results (Section 4) where AI produced functional applications lacking not predictions but *design judgements* |
| Cognitive science (HCI) | Gulf of execution / Gulf of envisioning | Subramonyam et al. (2024) | Three gaps (capability, instruction, intentionality) map onto externalisation cost. Specification cost—knowing what the artefact should be—is presupposed as a given goal, whereas the present framework treats it as the primary variable |
| Interaction design | Specification / Process / Evaluation alignment | Terry et al. (2023) | Three-part taxonomy compresses to two components: process alignment and evaluation mechanics map onto externalisation cost; specification and evaluation *criteria* constitute specification cost. Compression from descriptive taxonomy to economic framework enables directional predictions |
| Knowledge management (SECI) | GRAI framework (8 interaction fields) | Böhm & Durst (2026) | Adds a human/machine agent dimension to SECI's four modes. The Ext./Spec. distinction is orthogonal: it applies *within* any SECI mode and any GRAI interaction field, providing an analytical layer that complements their descriptive mapping |

These independent observations—from economics, cognitive science, interaction design, and knowledge management—describe structurally similar phenomena from different disciplinary vantage points. The externalisation cost / specification cost framework provides a parsimonious two-component decomposition that (a) subsumes or is orthogonal to each existing model, (b) connects to an established knowledge management tradition via Nonaka's SECI, and (c) generates directional predictions illustrated through domain-ablation experiment (Section 4). The structural gap extends to AI systems design itself: Tomašev, Franklin, and Osindero (2026) proposed a comprehensive delegation protocol for AI agent systems including task decomposition, monitoring, and verification mechanisms, yet identified no principled criterion for determining which task components can be safely delegated and which require human judgement—precisely the separation that the externalisation cost / specification cost distinction provides.

The framework generates a specific directional prediction: in domains where specification cost is high, AI deployment without domain expert involvement will fail to produce domain-appropriate outputs, regardless of the AI system's externalisation capabilities. Section 4 provides supporting evidence for this prediction.^[The pattern of independent discovery across disciplines is itself informative. Multiple discovery typically indicates that a phenomenon has become observable through shared environmental change—in this case, the widespread availability of generative AI—rather than through the insight of any single researcher (Merton, 1961; Lamb & Easton, 1984).]

### 2.4 Applicability conditions

The substantial reduction in externalisation cost observed in domain-native development applies primarily to individual or small-team production in exploratory phases. Organisational coordination costs—regulatory compliance, multi-stakeholder approval, accessibility auditing, security review—constitute a separate cost category not addressed by the externalisation/specification distinction. Similarly, the framework addresses *technical* externalisation costs—those arising from format conversion, language translation, and procedural compliance. Social and psychological barriers to knowledge sharing (cf. Edmondson, 1999), while relevant to organisational knowledge flows, constitute a distinct phenomenon outside the present framework's scope—though their role as an identification condition is examined in Section 5.1. The framework does not predict that all knowledge work will be transformed equally.

The appropriate unit of analysis is not the task but the *component ratio within a task*. A routine compliance report (high externalisation ratio, modest specification ratio) and a novel product concept (low externalisation ratio, high specification ratio) are both "documents," but their cost compositions differ fundamentally. The framework predicts that AI assistance transforms the former far more than the latter—a prediction consistent with widespread observations of differential AI impact across knowledge work categories.

---

## 3. Case Study

The following case is positioned as a revelatory case study (Yin, 2018)—selected not for prevalence but for its capacity to make observable a phenomenon that the framework predicts but that has not been empirically documented at the level of individual design decisions.

A researcher with a doctoral background in pharmacology and no prior programming experience developed and publicly deployed a progressive web application (PWA) for searching electric vehicle (EV) fast-charging infrastructure across Japanese expressways. The application comprises 32 source files, a bespoke dataset of 583 records (one row per charger model at each directional location, derived from 662 individual charging ports across 461 directional locations at 255 physical sites) with 22 technical fields each, and supports bilingual (Japanese/English) operation. Development spanned ten working days using two AI tools in a deliberate division of labour: an AI chat interface for design discussion and review, and an AI coding agent for implementation. Community reception on social media within 48 hours of public release confirmed practical utility rather than novelty alone.

Time allocation across the development process proved revealing. Actual AI code generation accounted for approximately 5% of total working time. Design discussions, specification review, and iterative refinement consumed roughly 40%. The remainder comprised environment setup (20%), deployment and testing (25%), and breaks (10%). In short, externalisation cost was compressed to a fraction of the total effort; the dominant activity throughout was specification—deciding what the application should and should not do.

### 3.1 Specification cost as the determinant of design

Four categories of design decisions illustrate how domain knowledge, rather than prompt engineering skill, governed application quality.

**Current-based data architecture.** The dataset was structured around voltage and amperage rather than the kilowatt ratings typically displayed by charging networks. This decision derives from the physics of the dominant fast-charging protocol in Japan:^[CHAdeMO, the protocol used by the majority of Japanese fast-charging stations, operates under current control. The charger adjusts output current while voltage tracks the vehicle battery's state of charge.] chargers operate under current control, with voltage tracking the vehicle battery's state of charge. Kilowatt output is therefore a *result*, not a control variable. The dataset accordingly records maximum voltage, maximum amperage, and sustained amperage as separate fields. This architecture enables a vehicle-specific output calculation—min(vehicle voltage, charger voltage) × min(vehicle current, charger current)—that no existing EV information service provides. The formula is self-evident once the underlying physics is understood, yet it remains absent from publicly available charging guides, constituting tacit knowledge that the author's combined electrical engineering certification and EV ownership made available. In the domain-ablation experiment (Section 4), neither AI model operating without this domain knowledge included current-based fields.

**Conditional display suppression.** When a user configures their vehicle profile, the application suppresses boost-mode indicators for chargers whose boost current falls at or below the vehicle's maximum charging current. For instance, a vehicle limited to 200 A receives no benefit from a charger's 350 A boost capability; displaying this information would be misleading. This judgement combines physical understanding (current-limited charging behaviour) with information design principles (progressive disclosure—hiding information irrelevant to the specific user). The suppression logic appeared in neither ablation output.

**Network operator discrimination.** Japanese expressway charging stations are managed by multiple, non-interchangeable networks. Two stations at the same service area may belong to different operators with incompatible authentication systems. The application records operator identity as a distinct field and displays non-default operators with visible badges. In the ablation experiment, one AI model misinterpreted the operator management flag as an "immediate availability" indicator, producing a structurally incorrect data model.

**Non-adoption decisions.** Perhaps the strongest evidence for specification cost lies in what the application deliberately excludes: real-time availability (unreliable API data that could misdirect users), charging time predictions (nonlinear charging curves that vary with temperature, state of charge, and battery degradation), distance calculations (expressway network topology makes simple distance metrics misleading), and tariff information (rates vary by card type, plan, and time of day). Each exclusion reflects domain knowledge about what would harm rather than help users. In the ablation experiment, both AI models exhibited "total field filtration"—converting every available data field into a user-facing filter, unable to judge which information to withhold.

These design decisions were not products of prompt engineering technique. Each originated from the author's domain knowledge—electrical engineering fundamentals, vehicle ownership experience, and understanding of user behaviour at charging stations. They instantiate specification cost as defined in Section 2.

### 3.2 Reversal of the translation direction

Conventional knowledge-to-product workflows follow a linear path: the domain expert writes natural-language requirements, which a software engineer interprets and implements. Ambiguities in the requirements document generate iterative clarification cycles—a primary source of externalisation cost.

The development process observed in this case study inverted this sequence. The author generated working prototypes through AI dialogue, producing functional code that served as the specification itself. When a professional engineer later needed to rebuild components for production quality, the prototype—not a written requirements document—became the reference artefact. A working prototype is structurally less ambiguous than a natural-language specification: behavioural questions can be answered by running the code rather than interpreting text.

This reversal was most evident in a specification-driven development episode. The author prepared a detailed specification document, a visual prototype, and a machine-readable instruction file before engaging the coding agent. The search interface was implemented in eight minutes with zero clarification requests. By contrast, earlier sessions conducted without such preparation required repeated correction cycles as the AI agent guessed at unstated requirements. The contrast demonstrates that externalisation cost reduction is not automatic; it depends on the quality of specification provided.

### 3.3 Exploratory value of reduced externalisation cost

The primary value of reduced externalisation cost may not be the efficiency of producing finished products, but the increased number of exploratory attempts that become feasible when creation cost is low.

The present case study provides direct evidence. The application's specification document records twelve features that were explicitly proposed and rejected during development: a route-distance column (rejected because highway interchange connections introduce measurement ambiguity), a regional filtering system (rejected because certain expressways span multiple administrative jurisdictions, breaking any area-based classification), a power-sharing column (rejected because two-port chargers exhibit variable output distribution that cannot be represented in a single field), and nine additional items, each rejected on domain-specific grounds. In a conventional outsourcing arrangement, most of these features would never have been proposed—and those that were proposed would have incurred significant cost to evaluate and discard.

A design-level pivot illustrates the same dynamic at larger scale. Three complete landing page designs—dark-minimal, clean-light, and editorial—were generated and evaluated within a single session. The editorial approach was selected based on the author's judgement that technical content requires visual authority; the other two were discarded immediately. In traditional outsourcing, commissioning three complete design alternatives and discarding two would represent a substantial cost penalty. Under near-zero externalisation cost, such early-stage exploration becomes routine.

The critical observation is that each rejection was itself an exercise of domain expertise—specification cost applied to *evaluation* rather than creation. The twelve rejected features and two discarded designs represent specification cost in its evaluative dimension: the expert's judgement about what *not* to build.

This dynamic reverses when externalisation cost reduction is applied to organisational automation rather than individual exploration. Individual exploration operates under low failure cost (the explorer bears the consequences); organisational automation operates under high failure cost (errors propagate through systems and users). This asymmetry is examined in Section 5.3.

### 3.4 Two identification points

The case study yields two observations that the Discussion will generalise:

1. **Prototype-as-specification** constitutes a structural mechanism for reducing externalisation cost. The domain expert's output is no longer a natural-language description to be interpreted, but a functioning artefact to be refined.

2. **Increased exploratory attempts** represent a second-order effect of externalisation cost reduction. When creating and discarding prototypes becomes inexpensive, the bottleneck shifts entirely to the domain expert's judgement about what is worth pursuing—specification cost in its evaluative dimension.

---

## 4. Methods

The preceding case narrative and the Discussion that follows draw on three categories of evidence: the dialogue logs generated during AI-assisted development, the outputs of a domain-ablation experiment, and the published dataset. This section describes each.

### 4.1 Dialogue logs as cognitive records

The methodological contribution of this study lies not in the application itself but in the dialogue logs generated during its development. These logs constitute a complete record of the author's decision-making process: which design options were considered, which were adopted and why, and—critically—which were rejected and on what grounds. Rejection rationale is a category of knowledge that typically survives in neither technical manuals nor project reports.

This record shares analytical kinship with Think Aloud Protocols (TAP; Ericsson & Simon, 1993), but with a significant methodological advantage: it is non-intrusive. TAP imposes a dual-task burden by asking participants to verbalise while performing; AI-assisted development naturally produces verbalisation as its primary mode of operation. The dialogue log is not a secondary artefact overlaid on the work process—it *is* the work process. This property also mitigates the primary risk of the author-as-subject design: because decisions were recorded at the moment of occurrence rather than reconstructed retrospectively, the logs constrain post hoc rationalisation in a way that interview-based or memoir-based methods cannot.

A technical precondition for this approach is the context window capacity of current large language models (approximately 200,000 tokens at the time of this study), which permits extended multi-turn dialogues that accumulate project-specific context. This accumulated context creates a positive feedback loop: as the AI system's representation of the project improves, the author's specification becomes more efficient, accelerating knowledge extraction. This technical parameter should be noted as a reproducibility condition.

### 4.2 Domain-ablation experiment

To illustrate the framework's prediction that specification cost cannot be substituted by externalisation cost alone, a domain-ablation experiment was conducted. The experiment is designed not as a benchmark but as a counterfactual illustration: it asks what happens when externalisation capability is present but specification is absent. The same raw dataset—662 charging port records derived from the author's structured CSV but converted to JSON with field names replaced by the network operator's abbreviated API labels (e.g., `im`, `cap`, `typ`), deliberately reducing human readability to prevent domain knowledge leakage through column naming—was provided to two commercially available AI systems: Claude Code (Anthropic, Claude Opus 4.6) and ChatGPT 5.2 (OpenAI, Pro mode). Each received a single generic prompt requesting creation of an EV charging station search application with filtering and sorting capabilities, with design left to the AI's discretion. No follow-up instructions were given. Neither model posed domain-specific queries; the only author interactions during the Claude Code session were technical file-creation approvals, which were set to auto-approve after the first prompt. This one-shot, zero-interaction design prevents contamination from the author's iterative specification.

A critical methodological choice was using the raw API data (JSON with abbreviated field names such as `im`, `cap`, `typ`) rather than the author's structured CSV dataset. The CSV column names—`max_amps`, `sustained_amps`, `boost_minutes`—themselves encode domain knowledge that would partially compensate for specification cost absence.

Both models produced functional applications rapidly: Claude Code generated a single HTML file (353 lines) in under two minutes; ChatGPT produced a single HTML file (1,145 lines, with JSON data embedded inline) after approximately 35 minutes of processing. Both outputs featured competent user interfaces with filtering and sorting capabilities, confirming full externalisation cost capability. Table 2 catalogues the convergent deficiency patterns across three analytical layers.


**Table 2: Convergent deficiency patterns in domain-ablation experiment**

| Analytical layer | Specification-absent output | Specification-present design (author) |
|---|---|---|
| **Data interpretation** | | |
| Physical architecture | Kilowatt ratings only; no current-based data model | Voltage/amperage separation enabling vehicle-specific output calculation (V × A) |
| Temporal resolution | No boost/sustained current distinction | Separate fields for maximum amperage (boost) and sustained amperage |
| Data hierarchy | Flat presentation of all 662 ports (Claude) / Direction-level aggregation into 465 groups without site-level consolidation (ChatGPT) | Three-level hierarchy: 662 ports → 461 locations → 255 sites |
| Operator semantics | Management flag misinterpreted as availability indicator^a^ | Operator identity as distinct field with network-specific badge display |
| **UI/UX** | | |
| Output personalisation | No vehicle-specific calculation | min(vehicle V, charger V) × min(vehicle A, charger A) per configured profile |
| Conditional logic | No display suppression based on user context | Boost indicators hidden when charger boost ≤ vehicle max current |
| Data normalisation | Direction field ignored entirely (Claude) / Eight directional labels retained without normalisation (ChatGPT)^b^ | Normalised to two physical directions per location |
| **Information architecture** | | |
| Navigation model | No route-planning orientation | Route-based (expressway → service area → charger) |
| Curation | No recommendation or prioritisation logic | Operator badges, output ranking, contextual recommendations |
| Filter design | Minimal filters with most fields ignored (Claude) / Extensive filters including single-value fields (ChatGPT); neither selected filters based on user relevance | Selective filtering; irrelevant or misleading fields deliberately excluded |

^a^ One model interpreted the `isManaged` boolean as "immediate availability," producing a structurally incorrect data model.
^b^ One model ignored the direction field entirely; the other retained eight directional labels without normalising to two physical directions per location.

Both models independently exhibited structurally convergent deficiency patterns across all three layers, though with variation in degree. At the *data interpretation* layer: absence of current-based architecture (kilowatt ratings only), no boost/sustained current separation, flat presentation of all 662 ports without grouping in one model and direction-level aggregation (465 groups) without site-level consolidation in the other (versus the author's three-level hierarchy: 662 ports → 461 locations → 255 sites), and misinterpretation of operator management fields. At the *UI/UX* layer: no vehicle-specific output calculation, no conditional display logic, and failure to normalise directional labels (one model ignored the direction field entirely while the other retained eight directional labels, neither normalising to the two physical directions per location used in the author's design). At the *information architecture* layer: no route-planning orientation, no recommendation logic, and—most tellingly—divergent but equally specification-absent filter strategies—one model ignored most fields while the other converted all available fields into filters including one with a single possible value—with neither selecting filters based on domain-informed user relevance.

Each row in Table 2 represents a design decision requiring domain knowledge—electrical engineering fundamentals, charging protocol physics, user behaviour at highway service areas—that no amount of prompt engineering sophistication could substitute. The convergent failure pattern across two independent models operating on identical data is consistent with the framework's prediction: when specification cost is absent, externalisation cost reduction alone produces artefacts that are technically competent but domain-inappropriate. One model's interpretation of the `isManaged` field as "immediate availability" exemplifies the pattern precisely—externalisation capacity (converting a field into a functional UI filter) operated flawlessly, but specification (knowing what the field *means* in the charging network context) was absent.

### 4.3 Data availability

Three data layers are deposited on figshare (Nature Portfolio's recommended repository): the charging infrastructure dataset (583 × 21 CSV; one field—installation date, collected through independent research—is withheld from the public release), the ablation experiment input data (662-record JSON with abbreviated field names, as provided to both AI systems) together with outputs and session logs, and full dialogue logs in the original Japanese (machine-analysable by contemporary AI systems, rendering language a non-barrier to verification). Dialogue logs have been reviewed to remove references to third-party individuals and proprietary organisational information; redacted passages are marked with [REDACTED] tags to maintain analytical traceability.^[To maintain double-anonymous review integrity, data are submitted as supplementary materials during review. The figshare deposit will be made publicly accessible upon acceptance, with the DOI reserved in advance.]

### 4.4 AI use disclosure

In accordance with Springer Nature's policy on AI-assisted writing, the following disclosure is provided. Three AI systems were used throughout this research: an AI chat interface (Claude, Anthropic) for design discussion, conceptual development, and manuscript drafting; an AI coding agent (Claude Code, Anthropic) for software implementation; and an additional AI system (ChatGPT, OpenAI) for the domain-ablation experiment (Pro mode, version 5.2) and independent manuscript review (Pro mode, five review cycles). The AI chat interface also served as the primary data collection instrument, generating the dialogue logs analysed in this study.

In all cases, the author provided domain knowledge, made all design and analytical decisions, set evaluation criteria, and bears sole responsibility for the content. The AI systems performed externalisation—converting the author's specifications into formal text, code, and structured arguments. No AI system is listed as an author, consistent with COPE and ICMJE guidelines. The dialogue logs deposited with this paper permit verification of the human–AI division of labour at the level of individual decisions.

---

## 5. Discussion

### 5.1 Theoretical positioning: the visibility thesis

Section 3 demonstrated two identification points: that prototype-as-specification constitutes a structural mechanism for reducing externalisation cost (identification point 1), and that reduced externalisation cost increases the rate of exploratory attempts whose evaluation depends on specification cost (identification point 2). This section examines the theoretical implications of these observations.

The central claim of this paper is that the distinction between externalisation cost and specification cost is not a structure created by AI, but a structure *made visible* by AI. The two components have always been present in knowledge work; they were simply inseparable under prior conditions.

The reasoning follows a quasi-experimental logic. In conventional human-to-human knowledge transfer, multiple confounding variables overlay the translation process: hierarchical relationships between mentor and apprentice, evaluation anxiety, social desirability bias, organisational politics, time pressure, and ego protection. These interpersonal factors are entangled with both the technical difficulty of articulating tacit knowledge (externalisation cost) and the substantive judgements about what knowledge matters (specification cost). Under these conditions, the two cost components cannot be independently observed.

The separation is not unique to AI. Earlier waves of information technology already eliminated narrow segments of externalisation cost—institutional databases that auto-populate grant applications from publication records, for instance, removed the purely clerical effort of transcribing one's own work, a task requiring zero judgement. Yet these reductions targeted only routinised, judgement-free components of externalisation. The residual externalisation cost remained large enough to keep specification cost empirically indistinguishable from the total. What generative AI altered was the *breadth* of externalisation cost reduction—extending from text generation and translation to code synthesis and structural organisation—thereby rendering the persistent specification cost component visible for the first time as a distinct, measurable residual.

AI-mediated dialogue substantially attenuates these confounders. Iteration carries near-zero marginal cost, social penalties for reformulation are minimal, explanation requests carry no status implications, and power asymmetries are substantially reduced in the dyadic AI-human interaction context. Under these attenuated conditions, what remains observable is the differential behaviour of the two cost components: externalisation cost drops dramatically (eight-minute implementation episodes, zero-iteration specification transfer), while specification cost persists unchanged (the design decisions catalogued in Section 3 required the same domain knowledge regardless of the implementation medium).

The domain-ablation experiment (Section 4.2) provides the identification step. Under the specification-absent condition (AI operating without domain knowledge), externalisation capacity alone produced technically competent but domain-inappropriate artefacts. The convergent failure pattern across two independent AI models—exhibiting the same categories of deficiency despite different architectures and different interface choices—suggests that the two components are separable and that they respond differently to AI assistance. This pattern is consistent with the defining prediction of the framework.

This structure is not unique to the present case study. The independent emergence of structurally analogous two-component decompositions across economics (Agrawal et al., 2018), cognitive science (Subramonyam et al., 2024), interaction design (Terry et al., 2023), and knowledge management (Böhm & Durst, 2026), as documented in Section 2, constitutes convergent evidence for the universality of the underlying structure.

A finer-grained observation follows from the case study data, though it extends beyond the ablation evidence into the author's reflexive analysis. The two-component structure is an ontological claim: externalisation cost and specification cost are always co-present in knowledge work. The simultaneous attenuation described below is an epistemological condition—it enabled observation, not existence. Externalisation cost itself contains at least two subcomponents that respond to different interventions: *interpersonal risk perception*—the perceived social cost of articulating tentative or incomplete knowledge, which psychological safety attenuates (Edmondson, 1999)—and *technical conversion barriers*—the procedural difficulty of translating knowledge into formal representations, which AI attenuates. In the present case, both subcomponents were simultaneously reduced: technical conversion barriers by AI-mediated dialogue, and interpersonal risk perception by the author's low emotional responsiveness profile (Section 5.6). This simultaneous attenuation created the observational conditions under which specification cost could be isolated as a pure residual. The subcomponent distinction suggests that maximising specification cost utilisation may require combined deployment of psychological safety interventions and AI tools, each targeting the externalisation barrier it can address.

### 5.2 Domain knowledge as the substance of specification cost

If externalisation cost is what AI reduces, specification cost is what determines output quality under the new cost structure. The case study's design decisions (Section 3.1) provide direct evidence: each reflects domain knowledge that could not have been generated by prompt engineering technique, however sophisticated.

The unit of analysis for this framework is not the task but the *component ratio within a task*. A routine technical report (high externalisation ratio, low specification ratio) and a novel research proposal (low externalisation ratio, high specification ratio) are both "writing tasks," but their cost compositions differ fundamentally. AI assistance transforms the former far more than the latter.

The portability of specification cost provides additional evidence for its locus in the human contributor. The structured handoff files used to transfer project context between AI sessions—documents that encoded accumulated design decisions and their rationale—reduced externalisation cost in new sessions to near zero from the first exchange. The fact that specification could be extracted, encoded, and successfully transferred suggests that it resides in the human domain expert's judgement rather than in any particular AI system's learned representations.

The framework is not AI-specific. An organisational case illustrates the same principle without AI involvement: an automobile manufacturer's hybrid vehicle displays domain-specific aerodynamic features—quantified drag-reduction indicators presented directly to consumers during driving—that would be unlikely to emerge from a conventional requirements-specification-implementation pipeline without direct involvement of aerodynamic expertise in the design process. The structural explanation is identical: embedding domain expertise eliminates the translation layer, allowing specification to flow directly into the artefact.

The framework further predicts that the domain expertise underlying specification cost, being grounded in pattern recognition and structural judgement rather than domain-specific vocabulary, can operate across disciplinary boundaries once externalisation barriers are removed. Systematic replication by domain experts in other fields constitutes a priority for future research.

### 5.3 Non-functional requirements and the responsibility boundary

Domain-native development reduces externalisation cost for domain-aligned functionality—the features and design decisions that directly reflect the expert's knowledge. It does not address non-functional requirements: security, scalability, accessibility, long-term maintainability, and regulatory compliance. These constitute a separate axis of professional expertise.

The translation layer that DND eliminates served a dual function. It was simultaneously a source of information loss (externalisation cost) and a quality gate staffed by professionals trained in system-level concerns (responsibility boundary). When the translation layer disappears, the domain expert becomes the de facto design authority—a role that carries responsibilities beyond domain correctness.

A reported industrial case illustrates the risk at scale: a major IT services firm deployed a multi-agent AI platform that automated the full software modification lifecycle—from requirements analysis through design, implementation, and integration testing—achieving approximately 100-fold productivity gains on selected cases from a pool of roughly 300 modification tasks (Fujitsu, 2026). When such automation removes human intervention across the entire development lifecycle, the failure containment boundary expands proportionally—a defect in the automation logic could propagate through requirements, design, and implementation without the stage-gate reviews that conventional team-based development provides.

The asymmetry identified in Section 3.3 is structural. Individual exploration (where the domain expert bears the consequences of failure) operates safely under reduced externalisation cost. Organisational deployment (where failures affect users, systems, and regulatory obligations) requires that the responsibility boundary be explicitly reconstructed—through code review, security auditing, or professional engineering oversight—even when the translation layer has been removed.

A broader observation follows. Not all externalisation cost reduction is beneficial.^[An example within the author's development: the AI coding agent flagged a potential security concern (unprotected API endpoint) that the author, lacking security expertise, would not have identified independently. The pattern—AI detection followed by human approval or rejection—suggests a general architecture for responsibility management in DND contexts, where AI systems can identify potential issues within their training distribution but cannot determine whether the issue is material in the specific deployment context.] In established professional communities, high externalisation cost can function as a *deliberate* entry barrier, maintaining quality standards and in-group coordination efficiency. This is not a cultural phenomenon limited to specific national contexts; it is a structural property of any group that has accumulated shared tacit knowledge. Reducing externalisation barriers for outsiders may dilute the specification density that gives the community its productive advantage—a tradeoff that organisational AI adoption strategies must evaluate explicitly.

### 5.4 Methodological contribution of dialogue logs

The dialogue logs generated through AI-assisted development constitute a methodological contribution independent of the present framework. Unlike traditional Think Aloud Protocols (Ericsson & Simon, 1993), which impose a secondary cognitive load on participants, AI dialogue produces verbalised reasoning as a natural byproduct of the primary task. The researcher does not need to "think aloud"—the interaction medium *requires* articulation.

The resulting records capture categories of knowledge that are absent from conventional documentation. Design rationale ("why this architecture rather than alternatives"), rejection rationale ("why this feature was excluded"), and evaluative criteria ("what makes this output acceptable") are preserved in the dialogue but would not appear in a requirements document, technical manual, or project postmortem. For knowledge-intensive organisations facing expertise succession challenges, dialogue logs represent a fundamentally new type of institutional memory.

A self-reinforcing dynamic was observed: as the AI system accumulated project context through extended dialogue, the author's subsequent specifications became more efficient—less explanation was required to convey intent. This profile-accumulation effect constitutes an operationalizable measure of externalisation cost reduction over time.

The transferability of this accumulated context was demonstrated through structured handoff documents. Dialogue-derived project context, when systematically encoded, reduced externalisation cost in new AI sessions to near zero, confirming that the valuable knowledge resided in the specification structure rather than in any particular dialogue history.

### 5.5 Cumulative optimisation risk and educational implications

**Risk.** Extended use of a single AI system creates a risk of cognitive lock-in. Individual AI models exhibit characteristic interaction patterns, and sustained optimisation toward one model's affordances may narrow the user's specification repertoire. The author's practice of distributing tasks across two AI systems (Claude for extended design dialogue, and ChatGPT for independent review) itself constitutes a meta-level specification judgement: knowing which AI system to deploy for which cognitive task requires domain knowledge about the systems' respective strengths—a form of meta-specification.

The mitigation for cumulative optimisation risk is framework literacy—understanding the distinction between externalisation cost and specification cost at a conceptual level. This understanding enables practitioners to recognise when they are optimising externalisation (productive) versus when they are inadvertently outsourcing specification (dangerous). Risk recognition is itself a specification-side judgement that protects the practitioner's evaluative capacity.

**Educational implications.** This connection between risk mitigation and conceptual understanding leads directly to the question of whether specification cost can be taught. While externalisation cost reduction operates primarily through sustained delegation to AI systems, specification cost acquisition presents a harder educational challenge. Drawing on the author's experience as both framework developer and training designer, a three-layer model is proposed:

- *Layer 1: Conceptual awareness.* The learner understands the framework intellectually but cannot apply it. Knowing that specification cost exists does not confer the ability to exercise it.
- *Layer 2: Experiential recognition.* Through domain practice, the learner develops pattern recognition that functions with deliberate effort. Time-intensive but achievable.
- *Layer 3: Integrated operation.* Conceptual knowledge and experiential pattern recognition merge, enabling real-time specification—whether during AI interaction, peer review, or independent design judgement.

Training programmes (Layer 1) do not produce specification competence in isolation, but they function as primers that, in pharmacological terms, *sensitise* the learner to subsequent domain experiences. A training session that introduces the externalisation/specification distinction may not immediately change behaviour but may accelerate the recognition of specification opportunities when they arise in practice.

A practical implication follows for organisational training design. The instruction "teach the veteran to use AI" misidentifies the bottleneck. The veteran already possesses specification capacity; what is needed is a training designer who constructs the interaction context—selecting appropriate prompts, structuring the dialogue sequence, choosing which domain knowledge to surface—so that the veteran's specification flows naturally into the AI system. The training designer operates at a meta-specification level: specifying how specification itself should be elicited.

Observable indicators of successful framework acquisition were identified in the author's own experience: spontaneous application of the two-component distinction in everyday professional conversation, without deliberate reference to the framework. This shift from analytical application to automatic categorisation may serve as a measurable proxy for Layer 3 integration.

The distinction between learner-stage users (who lack specification capacity and must develop it through domain apprenticeship) and expert-stage users (who possess specification capacity and need only externalisation cost reduction) is foundational to educational design. Conflating the two populations—as much current "AI literacy" training does—produces programmes that optimise externalisation for people whose bottleneck is specification. This educational analysis leads directly to the question of what institutional structures currently produce specification capacity—a question taken up in the Conclusion.

### 5.6 Safety considerations and limitations

The effectiveness of AI as a cognitive environment carries direct safety implications. In pharmacological terms: a compound that produces therapeutic effects also carries the potential for adverse effects, and the appropriate response is not prohibition but usage design—dosage, contraindications, and monitoring protocols.

AI dialogue acts on cognitive processes with a directness that conventional tools do not. The attenuation of interpersonal buffers—the same property that enables the quasi-experimental separation of cost components—simultaneously reduces the psychological distance between the user and their own knowledge structures. An analogy to opioid regulation is instructive: unrestricted access led to dependency crises, while excessive restriction denied access to patients with legitimate need. The appropriate response was neither extreme but a structured protocol balancing efficacy and risk.

Empirical grounding for this concern emerged from the author's own experience. Despite scoring in the lowest quartile on a standardised measure of emotional responsiveness, the author observed a graduated increase in emotional engagement as the depth of AI-mediated externalisation progressed—from self-knowledge articulation through interpersonal relationship analysis to intellectual lineage positioning. The a fortiori implication is that users with greater emotional responsiveness may experience earlier and stronger reactions. Detailed data are provided in the supplementary materials.

An external case reinforces this concern from a different angle. Ordak (2023) demonstrated that when ChatGPT was asked to recommend statistical tests for published allergology studies, it produced inappropriate test selections, omitted assumptions necessary for valid application, and returned contradictory recommendations for identical questions posed on separate occasions. This constitutes a case of externalisation cost (executing statistical reasoning) being delegated without specification cost (judging whether a particular test is methodologically appropriate for the data structure at hand). The structural parallel to the ablation experiment is direct: ablation showed specification-absent AI producing domain-inappropriate applications; Ordak showed specification-absent AI producing methodologically unreliable statistical guidance.

A pharmaceutical analogy clarifies a structural gap in current practice. Drug labels are required to disclose contraindications alongside therapeutic indications—specifying not only what a compound can treat but where its use is inappropriate or dangerous. No equivalent disclosure framework currently exists for AI-assisted development tools. The mekiki framework offers a conceptual basis for such disclosure: distinguishing tasks where domain expertise is required (high specification cost) from those that can be safely delegated to AI processing (high externalisation cost ratio). Developing this distinction into operational disclosure standards is a task for the broader community—across technology, medicine, and policy—rather than for any single framework.

**Limitations.** This study has several limitations that bound its claims. (1) The case study is n = 1. It is positioned as a revelatory case (Yin, 2018)—valuable for demonstrating the existence and structure of a phenomenon rather than for establishing prevalence. (2) The author serves as both researcher and subject, introducing potential confirmation bias. Full data disclosure (dialogue logs, code, ablation outputs) mitigates but does not eliminate this concern. The observed separation may have been facilitated by simultaneous attenuation of both externalisation cost subcomponents: technical barriers by AI, and interpersonal risk perception by the author's low emotional responsiveness profile. Replication under alternative conditions—such as psychologically safe team environments (Edmondson, 1999) substituting for individual trait-based attenuation—would strengthen generalisability. (3) Non-functional requirements (security, scalability, accessibility) were not systematically evaluated and remain outside the study's scope. (4) Long-term maintainability of the developed application is untested. (5) Externalisation cost reduction was observed in a single-developer context; organisational settings introduce coordination costs not addressed here. (6) The framework's scope is bounded to domains where specification originates from human expertise; domains where AI systems themselves participate in specification generation (e.g., unsolved mathematical conjectures, novel molecular design) may require a different analytical structure. (7) Cognitive and emotional load was assessed through retrospective self-report calibrated against a standardised baseline; physiological measures (heart rate variability, electrodermal activity) would provide stronger evidence but were not available in this study. Generalisability of the emotional engagement pattern requires replication with standardised instrumentation.

**Future directions.** Six avenues merit investigation: (a) Replication by domain experts in other fields to determine whether "AI-irreducible residue" consistently maps onto specification cost. (b) Internal structure of specification cost—preliminary observations suggest a surface layer (externaliseable through iterative AI dialogue) and a deeper layer (grounded in private networks, life experience, and finite embodied existence) that may correspond to what Polanyi (1966) identified as the fundamentally inarticulate dimension of knowledge and what Nonaka and Takeuchi (2019) termed Wisdom. Specification cost may contain strata that are separable in principle, an architecture whose investigation requires controlled comparison across expertise levels. (c) The relationship between context window capacity expansion and specification portability—whether larger context windows reduce specification cost or merely reduce externalisation cost for specification transfer. (d) Longitudinal observation of threshold effects as AI systems improve in resolution, scope, and calibration. (e) Extension of the two-component decomposition principle to Socialisation (tacit-to-tacit transfer), particularly in domains involving bodily skill transmission (e.g., construction trades, surgical training). A quasi-experimental system analogous to LLMs—capable of selectively removing bodily transmission barriers while preserving embodied judgement—does not yet exist, but emerging technologies (VR, motion capture, robotics) may eventually serve this role, warranting separate investigation. (f) Systematic investigation of externalisation cost substructure. This study identified at least two subcomponents—interpersonal risk perception (Edmondson, 1999) and technical conversion barriers—that respond to different interventions. Whether additional subcomponents exist, and how they interact under varying organisational conditions, remains unexamined.

---

## 6. Conclusion

This paper introduced the mekiki framework, which identifies two conditions governing whether tacit knowledge can be successfully converted into formal artefacts: externalisation cost (the technical barriers to articulating and implementing knowledge, corresponding to Nonaka's Externalisation phase in the SECI model) and specification cost (the barrier constituted by the domain expertise required to determine what should be built, how quality should be judged, and what should be excluded). Using a distillation model of authorship—where collective knowledge serves as the raw material, AI provides a bias-attenuated processing environment, and the human expert sets the distillation conditions—the framework redefines authorship in AI-assisted knowledge work as the exercise of specification.

### The PhD as specification training

The framework permits a structural redescription of doctoral training. The formal definition of a PhD—"an original contribution to knowledge through original research" (QAA, 2020; EUA, 2019)—decomposes naturally: *identifying a structure* is the generation of domain-specific specification; *converting it to formal knowledge* is externalisation in the SECI sense; *achieving the precision required for peer review* is externalisation cost processing at the standards of the academic community.

Doctoral training is, under this analysis, a specification training apparatus. AI is an externalisation cost reduction apparatus. The conjunction of the two constitutes the enabling condition for domain-native development—a conjunction this paper itself instantiates, having been written as a single-authored conceptual contribution in knowledge management by a researcher trained in pharmacology.

A policy implication follows. Discussions of doctoral workforce utilisation often focus on technical skills transfer or interdisciplinary breadth. The framework suggests that the core asset of doctoral training is neither—it is the *capacity to specify*: to identify what matters in a domain, to judge quality against implicit standards, and to determine what should not be built. When externalisation costs approach zero, this capacity becomes the binding constraint on productive AI use.

### Observed diffusion and framework-derived conjectures

The specification/externalisation dynamic is observable across domains at varying stages of AI integration. In competitive strategy games, AI superiority has been established for over two decades; the surviving human contribution is precisely the strategic judgement that the framework terms specification cost—the ability to select among AI-recommended options based on contextual evaluation (Shoresh & Loewenstein, 2025). In professional translation, the shift from creation to post-editing has redistributed labour from externalisation to specification (Flanagan et al., 2025). In software engineering, recent commentary on "vibe coding" (Sarkar & Drosos, 2025) observes that programming expertise is being redistributed toward evaluation—a restatement of the externalisation-to-specification shift in domain-specific vocabulary. In academic and professional writing, the present paper itself instantiates the pattern: a domain expert producing a conceptual contribution in an unfamiliar disciplinary genre through AI-mediated externalisation.

Two conjectures follow from the framework but exceed the present study's evidence. First, in visual illustration, the residual specification cost may be smaller than practitioners assume—technical rendering skill, long classified as specification, may be reclassifiable as externalisation cost as generative models improve. The professional implications require careful analysis that the present framework can structure but not resolve. Second, "high-context" communication barriers are not cultural phenomena but structural properties of *any* group with accumulated shared tacit knowledge. Externalisation cost reduction is therefore not uniformly beneficial; it can erode the specification-dense coordination that gives expert communities their productive advantage. Organisations in industries where knowledge is distributed at the operational level—construction, manufacturing, specialised services—face this tradeoff most acutely.

### Urgency

The framework's practical value is proportional to the speed at which it reaches practitioners. Domain experts whose domains carry high specification cost—typically senior professionals approaching retirement—represent a finite window during which their knowledge can be captured through AI-mediated dialogue logs. The three researchers introduced in Section 1 exemplify this asymmetry: the retiring specialist's specification capacity is irreversibly depleting, while the junior researcher's externalisation cost reduction tools await specification that only the specialist can provide. Each retirement without such capture represents an irreversible loss of specification capacity that no amount of subsequent externalisation cost reduction can compensate. The time structure is asymmetric: externalisation cost will continue to decrease as AI systems improve, but specification cost, once lost through generational transition, cannot be regenerated from data alone.

The urgency is not limited to knowledge preservation. The distillation model described in this paper—in which AI provides a bias-attenuated processing environment while humans set distillation conditions—carries its own time-sensitive implication: the framework for distinguishing what should and should not be delegated to AI must be established before widespread adoption outpaces the institutional capacity to set those conditions.

### Closing

Naming a phenomenon is the precondition for managing it. The distinction between externalisation cost and specification cost has always been present in knowledge work—in the experienced engineer's frustration when a junior colleague's AI-generated report is technically fluent but substantively empty, in the architect's inability to explain why one design "works" and another does not, in the physician's diagnostic judgement that resists algorithmic capture. What was missing was a vocabulary that made this distinction negotiable within organisations, measurable within research, and teachable within educational programmes.

This paper has proposed such a vocabulary, grounded it in the SECI knowledge management tradition, illustrated it through a single revelatory case, and provided supporting evidence for its central prediction through domain-ablation experiment. The framework does not claim to resolve the relationship between human expertise and AI capability. It claims something more modest and more immediately useful: to make the structure of that relationship *visible*—a structure that, as Lovelace (1843) noted of computation itself, has always concerned the boundary between what machines can perform and what only those already acquainted with the domain can provide.

The mekiki framework presented here does not create new capabilities; it makes visible what was always there.

---

## Postscript: A general form of domain-native development

The case study presented in this paper documents a *special form* of domain-native development: one in which specification cost was not pre-existing but was acquired and refined through AI dialogue itself. The framework, the terminology, and the analytical structure emerged during the process. This special form was difficult and time-consuming — ten working days for the application, substantially longer for the conceptual framework — precisely because specification and externalisation were co-developing.

Following submission of this paper, the author conducted three independent writing projects in domains where specification cost had accumulated over approximately ten years each: musical history, community governance, and research-support infrastructure. In each case, the author’s role was limited to confirming and adjusting specification — what to include, what to exclude, what level of detail was appropriate — while AI handled externalisation. All three documents were completed within a single day.

The contrast is direct. Same author, same AI, same period. The only variable was whether specification cost pre-existed. Where it did, production was rapid and straightforward. Where it did not (the present paper), production required iterative co-development over weeks.

This difficulty inversion is itself evidence for the framework’s central claim: externalisation cost and specification cost are separable, and they respond independently to AI assistance. For practitioners reading this preprint: if you possess deep domain experience, the general form of domain-native development is already available to you. The bottleneck was never the tool.

---

## Ethical approval

This article does not contain any studies with human participants performed by any of the authors. The study analyses the author's own AI-generated dialogue logs produced during a software development project; no data from other individuals was collected or analysed. The three individuals described in Section 1 are presented as anonymised structural illustrations of organisational knowledge patterns and were not research participants.

## Informed consent

This article does not contain any studies with human participants performed by any of the authors. As no human participants were involved, informed consent was not applicable.

## Competing interests

The author declares no competing interests. The author is employed by a construction company whose knowledge management challenges are discussed in the Introduction as contextual motivation; the company had no role in the study design, data collection, analysis, or decision to publish.

## Data availability

The datasets generated and analysed during the current study are available in the figshare repository. Three data layers are deposited: (1) the charging infrastructure dataset (583 × 21 CSV; one field withheld from public release), (2) the ablation experiment input data (662-record JSON) together with outputs and session logs, and (3) representative dialogue logs in the original Japanese. During double-anonymous review, data are submitted as supplementary materials; the figshare deposit will be made publicly accessible upon acceptance. All materials are licensed under CC BY-NC 4.0. The datasets generated and analysed during the current study are available in the figshare repository (https://doi.org/10.6084/m9.figshare.31441864).

---

## References

1. **Agrawal, A., Gans, J., & Goldfarb, A. (2018).** *Prediction machines: The simple economics of artificial intelligence.* Harvard Business Review Press.

2. **Böhm, K., & Durst, S. (2026).** Knowledge management in the age of generative artificial intelligence — from SECI to GRAI. *VINE Journal of Information and Knowledge Management Systems, 56*(1), 106–121. https://doi.org/10.1108/VJIKMS-10-2024-0357

3. **Edmondson, A. (1999).** Psychological safety and learning behavior in work teams. *Administrative Science Quarterly, 44*(2), 350–383. https://doi.org/10.2307/2666999

4. **Ericsson, K. A., & Simon, H. A. (1993).** *Protocol analysis: Verbal reports as data* (Rev. ed.). MIT Press.

5. **Flanagan, M., Dam Jensen, H., Bundgaard, K., & Paulsen Christensen, T. (2025).** Technology adoption among Danish translators: Practices, perceptions and prospects. *Revista Tradumàtica*, 23, 111–136. https://doi.org/10.5565/rev/tradumatica.511

6. **Fujitsu. (2026, February 17).** AI-Driven Software Development Platform: Multi-agent AI platform automating the full software modification lifecycle [Press release]. https://global.fujitsu/en-global/pr/news/2026/02/17-01

7. **Imai, M. (1986).** *Kaizen: The key to Japan's competitive success.* McGraw-Hill.

8. **Ordak, M. (2023).** ChatGPT's skills in statistical analysis using the example of allergology: Do we have reason for concern? *Healthcare, 11*(18), 2554. https://doi.org/10.3390/healthcare11182554

9. **Lamb, D., & Easton, S. M. (1984).** *Multiple discovery: The pattern of scientific progress.* Avebury.

10. **Merton, R. K. (1961).** Singletons and multiples in scientific discovery: A chapter in the sociology of science. *Proceedings of the American Philosophical Society, 105*(5), 470–486.

11. **Nonaka, I. (1994).** A dynamic theory of organizational knowledge creation. *Organization Science, 5*(1), 14–37. https://doi.org/10.1287/orsc.5.1.14

12. **Nonaka, I., & Takeuchi, H. (1995).** *The knowledge-creating company: How Japanese companies create the dynamics of innovation.* Oxford University Press.

13. **Nonaka, I., & Konno, N. (1998).** The concept of "Ba": Building a foundation for knowledge creation. *California Management Review, 40*(3), 40–54. https://doi.org/10.2307/41165942

14. **Nonaka, I., & Takeuchi, H. (2019).** *The wise company: How companies create continuous innovation.* Oxford University Press.

15. **Polanyi, M. (1966).** *The tacit dimension.* Doubleday.

16. **QAA (2020).** *Characteristics statement: Doctoral degree.* Quality Assurance Agency for Higher Education. https://www.qaa.ac.uk/the-quality-code/characteristics-statements/characteristics-statement-doctoral-degrees

17. **EUA (2019).** *Doctoral education in Europe today: Approaches and institutional structures.* European University Association. https://eua.eu/resources/publications/809:doctoral-education-in-europe-today-approaches-and-institutional-structures.html

18. **Sarkar, A., & Drosos, I. (2025).** Vibe coding: Programming through conversation with artificial intelligence. In *Proceedings of the 36th Annual Conference of the Psychology of Programming Interest Group (PPIG 2025).* arXiv:2506.23253

19. **Shoresh, D., & Loewenstein, Y. (2025).** Modeling the centaur: Human-machine synergy in sequential decision making. In *Proceedings of the 24th International Conference on Autonomous Agents and Multiagent Systems (AAMAS 2025)* (pp. 1941–1949). IFAAMAS. https://doi.org/10.5555/3709347.3743831

20. **Subramonyam, H., Pea, R., Pondoc, C., Agrawala, M., & Seifert, C. (2024).** Bridging the gulf of envisioning: Cognitive challenges in prompt based interactions with LLMs. In *Proceedings of the CHI Conference on Human Factors in Computing Systems (CHI '24).* ACM. https://doi.org/10.1145/3613904.3642754

21. **Terry, M., Kulkarni, C., Wattenberg, M., Dixon, L., & Morris, M. R. (2023).** Interactive AI alignment: Specification, process, and evaluation alignment. arXiv:2311.00710

22. **Tomašev, N., Franklin, M., & Osindero, S. (2026).** Intelligent AI delegation. arXiv:2602.11865

23. **Womack, J. P., Jones, D. T., & Roos, D. (1990).** *The machine that changed the world.* Free Press.

24. **Yin, R. K. (2018).** *Case study research and applications: Design and methods* (6th ed.). SAGE.

---

---

## Figure legends (images omitted)

### Figure 1

**Figure 1. The *mekiki* framework as a pathway model within the SECI model.**

The SECI model (Nonaka & Takeuchi, 1995) describes four modes of knowledge conversion: Socialisation (tacit → tacit), Externalisation (tacit → explicit), Combination (explicit → explicit), and Internalisation (explicit → tacit). Within Externalisation, the *mekiki* framework identifies two conditions that determine whether domain-appropriate outputs are produced. The substrate is *specification* — the domain expertise invested in deciding what should be built, how quality should be judged, and what should be excluded. **Externalisation cost** is the technical barrier to converting that specification into formal representations, and AI selectively reduces this barrier. **Specification cost** is the degree to which the task demands domain expertise. Output quality is therefore dose-dependent rather than binary: more relevant domain expertise yields more domain-appropriate output, while near-zero substrate yields domain-inappropriate output, as illustrated by the domain-ablation experiment. Deeper layers of specification cost structurally correspond to Polanyi's inarticulate dimension and to Nonaka and Takeuchi's (2019) Wisdom, beyond the present framework's empirical reach.

### Figure 2

**Figure 2. The distillation model of authorship under the *mekiki* framework.**

Authorship operates as a repeating cycle in which the **Human Expert** evaluates the current state and sets the conditions for the next pass. **Evaluate** asks what is present, what is missing, and what should be adjusted. **Set Conditions** determines what to retain, what to discard, and which quality criteria apply. Together, these operations constitute specification, and human responsibility resides in them. The **Apparatus** (the AI system) reduces externalisation cost while processing **Raw Material** (collective knowledge, conventions, prior art, community practices, and data) in an environment that selectively attenuates interpersonal confounders. It produces an intermediate or final **Output**, which returns to the Human Expert for evaluation; every iteration is therefore human-mediated. The comparison below states the corresponding claim in text.

**What determines the output: the human, not the apparatus.**

|  | Different experts | Different AIs |
|---|---|---|
| Raw material | same | same |
| Conditions | different | same |
| Apparatus | same | different |
| **Output** | **different** | **same** |


---

# Paper T2 — Philosophy as Cognitive Assay: Measuring the Delegation Legitimacy Boundary in AI-Assisted Knowledge Work

**Preprint version:** 2  
**Canonical DOI:** https://doi.org/10.31235/osf.io/e9qw5_v2

**Kengo Tomita**
Institute of Technology, Shimizu Corporation

---

## Abstract

This article operationalizes the concept of a *delegation legitimacy boundary* — the structural line along which human judgment can and cannot be legitimately delegated to artificial intelligence — and proposes a minimal scoring protocol for locating it within any knowledge-work task. Building on the Mekiki framework (Tomita 2026), which distinguished specification — the task-defining substrate of domain expertise — from externalization cost — the technical barrier that AI selectively removes — the present article derives a further decomposition within specification itself. Drawing on case-study evidence in which recorded specification judgments contain separable factual components (*Sein*-type: what the data structure affords, how users will perceive a display) and value-laden components (*Sollen*-type: what information ought to be excluded, which priority ranking is appropriate), the article grounds this distinction in Hume's is–ought separation and Kant's *Sein*/*Sollen* architecture, and redeploys it as the axis of a cognitive assay — a measurement system in which philosophical categories serve not as normative prescriptions but as diagnostic coordinates. The resulting five-step scoring protocol assigns *Sein*-type components to AI evaluation and *Sollen*-type components to domain-expert evaluation; this asymmetry is not a design choice but a structural consequence of the boundary itself, which holds as long as legitimacy over value judgments remains institutionally human-attributed. Most individual judgments are hybrid, carrying both components in varying ratios; the protocol therefore yields ratio profiles rather than binary classifications. As a first application, the article re-describes the four processes of Nonaka and Takeuchi's Socialization–Externalization–Combination–Internalization (SECI) model through the assay, deriving as an analytic consequence the finding that AI acceleration of Externalization and Combination shifts the effective rate-limiting stage to Socialization and Internalization — both human-limited cognitive and social processes that cannot be accelerated by AI investment alone.

**Keywords:** human judgment, delegation legitimacy, cognitive assay, Sein/Sollen, tacit knowledge, AI-assisted knowledge work

---

## 1. Introduction

Something that could not previously be measured is becoming measurable. Large language models have compressed the cost of converting expert knowledge into formal output — code, reports, draft designs — to a degree that would have seemed implausible a decade ago. Yet this compression has not rendered expertise redundant. On the contrary, it has exposed the judgments that expertise carries: what should be built, what should be excluded, and by what criteria quality should be assessed. Practitioners across domains now confront, often for the first time, the question of where their own contribution begins and the machine's contribution ends. Stader (2024), in adjacent philosophical work, captured the asymmetry precisely: judgment is not replaced by calculation; judgment is what gives calculation its meaning and purpose. The Mekiki framework (Tomita 2026) gave this asymmetry an operational structure by decomposing the Externalization process into two conditions — *specification* (the domain expertise that determines what should be built) and *externalization cost* (the technical barriers that AI selectively removes) — and demonstrating through case-study and domain-ablation evidence that the two conditions vary independently. What the framework left unexamined was the internal structure of specification itself.

The question of what lies inside that specification has, meanwhile, been approached from the direction of legitimacy. A growing body of work has shifted the normative criteria for AI-assisted decisions from explainability — can the system's reasoning be rendered transparent? — toward justifiability and contestability: can the decision be warranted on grounds that those affected would recognize as legitimate (Henin and Le Métayer 2022; Beckman et al. 2024)? The distinction matters because explanation is primarily descriptive — it answers "how did the system arrive at this output?" — while justification is inescapably normative: it must answer "on what authority, and toward what end?" Responsibility-gap analyses have shown that when this normative dimension is elided, accountability diffuses into organizational structures where no identifiable agent bears the evaluative burden (Dastani and Yazdanpanah 2023; Taylor 2025). Crucially, this traceability is not only a matter of *accountability* — which can diffuse across institutional structures — but more specifically of *answerability*: the non-transferable relation in which the warrant of a judgment remains anchored in a particular agent. What these analyses share is the recognition that some component of decision-making resists delegation not because AI lacks the computational capacity to produce an output, but because the output's warrant must be traceable to a source whose legitimacy is socially recognized.

A parallel conversation has been unfolding around the structural fate of tacit knowledge. Gill (2023), introducing a special issue of *AI & Society*, placed tacit knowledge — the dimension of knowing that resists full articulation (Polanyi 1966) — at the center of any serious account of AI futures, arguing that what cannot be articulated is precisely what is most at risk of being overlooked in systems designed around the articulable. Collins (2025) sharpened the point: large language models possess no moral compass — they cannot distinguish between what is factual and what is fabricated, because the distinction requires evaluative commitments that lie outside statistical pattern-matching. Ferdman (2025) extended the diagnosis from individual cognition to structural conditions, arguing that AI-induced deskilling is not a failure of personal discipline but a predictable consequence of capacity-hostile environments — institutional arrangements that systematically degrade the conditions under which expertise is acquired and exercised. These contributions converge on a shared concern: that AI systems, in accelerating the *articulable* dimensions of knowledge work, may simultaneously be eroding the conditions that sustain the *inarticulate* dimensions on which quality ultimately depends.

Yet for all the sophistication of these diagnoses, a specific intermediate layer remains absent. Existing scholarship has established that human oversight is necessary, that democratic legitimacy matters, that responsibility must be assignable, and that audit mechanisms require development (Manheim et al. 2025; Concannon and Tomalin 2024). What is missing is not another argument for the importance of human judgment — that case has been made convincingly and repeatedly — but a measurement system: a structured method for decomposing any given judgment into components, determining which components carry what kind of evaluative weight, and assigning each to an appropriate scorer. The gap, in other words, is not empirical but conceptual-operational. The problem has been diagnosed; the instrument for acting on the diagnosis has not yet been proposed in consolidated form. The present article does not claim untouched territory; it consolidates a missing intermediate layer between existing diagnoses and partial implementations. A recent Japanese-language textbook integrating AI technology, philosophy of mind, and social governance offers an integrative account of these domains (Taniguchi et al. 2026); the present article asks the complementary question of how to operationally measure the delegation legitimacy boundary.

The present article proposes such an instrument. Taking the specification identified by the Mekiki framework as its analytical substrate, it derives a decomposition into *Sein*-type (factual) and *Sollen*-type (value-laden) components, grounding the distinction in Hume's is–ought separation (1739) and Kant's critical architecture (1781, 1785). It then redeploys these philosophical categories not as normative prescriptions — not as claims about what AI *should* or *should not* do — but as the axes of a cognitive assay: a diagnostic system in which the categories serve as measurement coordinates. The term "assay" is used here in its analytical sense: a structured test that makes a composite judgment legible by separating its components and identifying where AI can reduce externalization cost without crossing the boundary of legitimate delegation. The five-step scoring protocol that results assigns *Sein*-type components to AI evaluation and *Sollen*-type components to domain-expert evaluation. This asymmetry is not imposed by design but follows structurally from what the article terms the *delegation legitimacy boundary* — the line beyond which AI may generate outputs but cannot serve as the source of their legitimacy. The boundary is not a capability claim; it is a legitimacy claim, and it holds as long as the authority to make value judgments remains institutionally attributed to human agents.

As a first application, the article re-describes the four processes of Nonaka and Takeuchi's (1995) SECI model — Socialization, Externalization, Combination, and Internalization — through the lens of the assay. This re-description is not an exegesis of SECI but a constructive refinement: it asks what becomes visible when each process is decomposed into *Sein*-type, *Sollen*-type, and externalization-cost components. The analytic consequence is that AI's acceleration of E (Externalization) and C (Combination) — the two processes most saturated with externalization cost — shifts the effective rate-limiting stage to S (Socialization, where *Sollen*-type specification is primarily updated through shared experience) and I (Internalization, where *Sein*-type specification is primarily absorbed into individual practice). Both remain human-limited processes. The implication for the tacit-knowledge concerns raised by Gill, Collins, and Ferdman is direct: the processes that cannot be accelerated by AI investment alone are those that sustain the evaluative capacities on which knowledge quality depends. The article thus bridges the legitimacy discourse, the tacit-knowledge discourse, and the measurement discourse by offering a single structural vocabulary in which all three become aspects of the same underlying decomposition.

## 2. The internal structure of specification: deriving the Sein/Sollen decomposition

### 2.1 Three concepts, not two

The Mekiki framework (Tomita 2026) distinguished three concepts that are routinely conflated in discussions of AI-assisted knowledge work. *Domain expertise* is a resource that a practitioner possesses — accumulated through training, practice, and exposure to a field's materials and norms. *Specification cost* is a property of the task: the degree to which the task demands that resource. And *specification* — the term used on Figure 1 of the original article as "substrate" — is what results when domain expertise is invested in a particular task: the concrete judgments about what should be built, what should be excluded, and by what criteria quality should be assessed. The present article takes the first two concepts as given. Its question is narrower: what is the internal structure of specification itself? When a domain expert invests expertise in a task, do the resulting judgments all share the same epistemic character, or do they contain components of fundamentally different kinds?

### 2.2 Derivation from the Mekiki case study

The Mekiki article recorded, in granular detail, the specification judgments that a domain expert made during the development of an EV charging application. Revisiting those records, two distinguishable kinds of judgment emerge.

One kind is factual. The domain expert judged that a current-based data structure reflects charging state more accurately than a kilowatt-hour display. That the identifier architecture of a particular network operator follows a specific hierarchical pattern. That a given display condition would produce user misrecognition. These judgments concern what *is* the case — how a data structure behaves, what a user will perceive, what a system affords. Given sufficient data and domain-relevant training, an AI system could in principle arrive at the same determinations.

The other kind is value-laden. The domain expert judged that real-time charger availability data — whether a charging station is currently in use — should not be displayed, even if technically obtainable: a non-adoption decision grounded in the judgment that unreliable availability information would undermine the application's purpose as a pre-trip planning tool. That a particular filter condition was *appropriate* for the intended user. That one information hierarchy was *preferable* to another. These judgments concern what *ought to be* the case — what serves the user well, what respects the design's normative intent, what information to withhold. An AI system can generate such outputs, but it cannot supply the warrant: the evaluative commitment that makes the judgment legitimate must originate from an agent whose authority to make it is socially recognized.

This article treats this two-way distinction as a *minimal decomposition*. The claim is not that every judgment falls cleanly into one category or the other. Most judgments in practice are hybrid: they carry both factual and value-laden components in varying proportions. Williams (1985) called such composites "thick concepts" — terms like *cruel*, *courageous*, or *negligent* that simultaneously describe and evaluate. The minimal decomposition does not deny hybridity; it asserts that within any hybrid judgment, it is analytically productive to ask how much of its weight rests on factual grounding and how much on evaluative commitment. The scoring protocol introduced in Section 3 operationalizes this question as a ratio profile rather than a binary classification.

### 2.3 Philosophical foundations

The distinction just derived from case-study evidence is not new. It is, in fact, among the oldest in Western philosophy. Hume (1739) observed that no amount of descriptive premises about what *is* the case can, by themselves, yield a conclusion about what *ought to be* the case — the is–ought gap. Kant systematized the distinction as *Sein* (being, the domain of theoretical reason) and *Sollen* (ought, the domain of practical reason), arguing that the two are governed by different rational faculties and irreducible to each other (Kant 1781, 1785). The present article adopts the Kantian terminology because it names the distinction with greater precision than the English is–ought pairing, and because the Neo-Kantian tradition — particularly Weber's insistence on value-freedom in social science (Weber 1904) — makes the distinction legible within the social-theoretical vocabulary familiar to this journal's readership.

Two subsequent contributions deepen the philosophical foundation. As Williams (1985) showed for thick concepts, clean decomposition into pure Sein and pure Sollen is not always possible — a constraint the present protocol addresses through ratio profiles rather than binary classifications. Nagel (1979, Ch. 9) went further, arguing that value is irreducibly fragmented — that distinct types of practical reason (obligations, rights, utility, perfectionist ends, personal commitments) cannot be reduced to a single scale or to agent-neutral terms. His conclusion — that good judgment without complete justification is the best available response to this fragmentation — is a philosophical anticipation of what the present framework operationalizes as specification: the practitioner's capacity to make situated evaluative judgments that resist algorithmic reduction. Nagel (1986, Ch. VIII–IX) extended the argument: agent-relative reasons — reasons that depend on the particular perspective, commitments, and situation of the agent — are irreducible to agent-neutral reasons accessible from any viewpoint. This irreducibility provides the deepest philosophical justification for the scoring asymmetry introduced in Section 3: Sollen-type components require evaluation by an agent whose perspective is constitutively relevant to the judgment, not by a system that operates from a view from nowhere. Nagel observed that what is needed is a method for breaking up practical problems so as to see which considerations are relevant and how they bear on a conclusion, but did not himself construct such a method. The present protocol is, in part, a response to that forty-year-old request.

The delegation legitimacy boundary, introduced in Section 1, runs along this distinction. *Sein*-type specification is, in principle, gradually absorbable into AI processing: as training data and domain models improve, factual determinations that once required human expertise become amenable to automated evaluation. The boundary is permeable on the Sein side — what counts as "requiring human judgment" shifts as AI capabilities advance. This permeability concerns the automation of factual evaluation, not the transfer of normative authority. *Sollen*-type specification, by contrast, resists this absorption not because AI cannot produce value-laden outputs — it manifestly can — but because the *legitimacy* of such outputs cannot be grounded in the system itself. The claim is not about capability but about warrant. An AI system that recommends withholding certain data from users may be producing exactly the judgment a domain expert would make; but the authority to make that judgment — the right to impose a normative commitment on others — must be traceable to a human source whose legitimacy is institutionally recognized.

Combining this with the Mekiki framework's two-condition structure yields a three-layer description of knowledge work under AI assistance (Fig. 1):

1. *Externalization cost* — technical barriers to converting expertise into formal output. AI removes or substantially compresses this layer.
2. *Sein-type specification* — factual judgments within the invested expertise. Gradually learnable by AI; over time, some determinations may become routinized and handled as part of externalization-cost processing.
3. *Sollen-type specification* — value-laden judgments within the invested expertise. The delegation legitimacy boundary sits here: AI may produce these outputs, but cannot serve as the source of their legitimacy.

A clarification is necessary here. Sollen-type specification — the practitioner's *capacity* to make value judgments — should not be confused with Sollen as an environmental normative pressure (e.g., institutional norms, regulatory requirements, or social expectations that constrain action). The distinction mirrors the one the Mekiki framework drew between specification (a resource the practitioner possesses) and specification cost (a demand the task imposes). Confusing the two would invite the misreading that Sollen-type specification is an external burden to be removed, when it is in fact the evaluative capacity that gives knowledge work its direction.

### 2.4 Generalization beyond Externalization

One further step is required before the decomposition can serve as the axis of an assay. The Mekiki framework derived the specification/externalization-cost distinction within the Externalization process of Nonaka and Takeuchi's SECI model. But nothing in the distinction itself is specific to Externalization. Böhm and Durst (2026), in their GRAI framework, added a human/machine agent dimension to SECI's four modes; the Mekiki article noted that the externalization-cost/specification distinction applies orthogonally *within* any SECI mode and any GRAI interaction field. The present article extends that observation: not only the two-condition structure but also the Sein/Sollen decomposition within specification cuts across all four processes. Every SECI process — Socialization, Externalization, Combination, Internalization — involves activities that carry both factual and value-laden components, in different proportions. Socialization (shared experience) is saturated with Sollen-type judgments about what matters, what to attend to, what norms to absorb. Internalization (learning by doing) is weighted toward Sein-type absorption of established knowledge into individual practice, though it also involves normative recalibration. The Sein/Sollen distinction is orthogonal to the SECI process distinction: it applies *within* any process, not *between* them.

This orthogonality is what makes the distinction usable as an assay axis. If Sein and Sollen were simply another way of labeling E and S, the decomposition would add no analytical power. Because they cut across SECI processes at right angles, they enable a matrix analysis — each process decomposed by judgment type — that reveals structural asymmetries invisible from within either framework alone. Section 4 carries out this analysis.

The level of analysis throughout this article is the structure of knowledge activities — the process level. The framework does not make claims about individual cognition (how a single expert internally represents Sein and Sollen), nor about organizational design (how institutions should be restructured), nor about regulatory policy (what laws should govern AI delegation). Extensions to those levels are possible and, the author believes, productive — but they belong to the domain experts of those respective fields. This article is a constructive refinement of SECI, not an exegesis: it asks what becomes visible when SECI's processes are examined through the Sein/Sollen lens, and it limits its claims to what that examination reveals.

## 3. Philosophy as cognitive assay: operationalization

### 3.1 Why the assay conditions are now met

In pharmacological assay design, a compound's activity can only be measured when background noise is sufficiently attenuated. If the noise floor is too high, the signal of interest — however strong — remains undetectable. The same structural logic applies here. Under conventional conditions of knowledge work, specification and externalization cost were entangled and inseparable (Tomita 2026): the effort of articulating an idea was indistinguishable from the expertise that gave the idea its content. AI's compression of externalization cost has substantially lowered this noise floor. Specification has not changed in character, but it has become isolable as a variable — foregrounded against a backdrop of dramatically reduced conversion friction. The Mekiki article's case study and domain-ablation experiment captured this transition in progress: the same specification, routed through different AI systems, produced outputs whose quality varied as a direct function of the specification invested, with externalization cost held approximately constant across conditions. Kusumegi et al. (2025), analyzing two million academic manuscripts, observed the complementary pattern at scale: AI-assisted writing improved the linguistic quality of submissions (externalization cost reduced) while acceptance rates remained unchanged (specification quality unaffected) — the two components varying independently in a population-level natural experiment. These conditions — specification foregrounded, externalization cost attenuated, independent variation empirically documented — are the conditions under which an assay becomes viable.

### 3.2 The scoring protocol

The unit of analysis is the individual *feature decision*: a single judgment recorded in the design process — a data structure choice, a display condition, a filter rule, a non-adoption decision. The Mekiki case study contains approximately thirty such decisions; Section 2.2 showed that they contain separable Sein-type and Sollen-type components.

The protocol proceeds in five steps.

**Step 1. Feature-decision extraction (AI).** The AI system identifies discrete judgments from the design record — requirements documents, dialogue logs, commit histories, or equivalent artifacts. This is a Sein-type operation: pattern recognition over documented material.

**Step 1b. Gap detection (domain expert).** The expert reviews the extracted list and adds judgments that the AI missed — in particular, *non-adoption decisions* (features deliberately excluded) and *implicit prioritizations* (orderings that were never explicitly stated). The Mekiki case study's decision to exclude real-time charger availability data is an example: the AI could not extract it because the feature was never built, and its absence from the record was itself the judgment. Step 1b corresponds to what the present article operationalizes as a high-order layer of specification cost — detecting the absence of something that ought to be present. AI can extract existing decisions; it cannot detect the *non-existence of what should exist*.

**Step 2. Operation-type classification (AI).** Each feature decision is labeled by operation type — *detect*, *prioritize*, *exclude*, or *justify* — as a descriptive tag independent of the scoring that follows. A single decision may carry multiple labels (e.g., detect/exclude). All four types can appear in both the Sein and Sollen rows: an exclusion based on data quality is Sein-type; an exclusion based on user values is Sollen-type.

**Step 3. Sein-row scoring (AI).** For each feature decision, the AI evaluates the factual component on a three-point scale: 0 (not detected / inaccurate), 1 (partial / ambiguous), 2 (accurate / appropriate). The anchor for this row is data-grounded: the AI assesses whether the factual determination is consistent with available evidence.

**Step 4. Sollen-row scoring (domain expert).** For each feature decision, the domain expert evaluates the value-laden component on the same scale. The anchor here is normative: does the judgment serve the design's purpose, protect the user's interests, reflect appropriate professional standards? The order in which the expert scores individual decisions is left to the expert's discretion. Because Sollen-type judgments lack natural ground truth, reliability is established through independent scoring by multiple experts followed by adjudication of disagreements.

**Step 5. Profile analysis (AI aggregation + expert interpretation).** Scores are not summed into a single index. Sein-type quality and Sollen-type quality are incommensurable dimensions; their addition would be meaningless — adding factual adequacy to normative warrant would produce a pseudo-precision that conceals rather than clarifies the task structure — and this incommensurability is itself a structural consequence of the two-component decomposition. Instead, the protocol reports *ratio profiles*: the Sein-row mean and variance, the Sollen-row mean and variance, and the distribution of hybrid judgments across the task. Aggregation by operation type (e.g., average Sein/Sollen ratio for *exclude*-type decisions versus *detect*-type decisions) provides a secondary layer useful for cross-task comparison. The expert's role at this step is interpretive: what does the profile reveal about where human judgment is most critical in this task? At the lowest level, each feature decision is itself a local Sein/Sollen profile — pure Sein, pure Sollen, or hybrid — and the task-level profile is the distribution of these local profiles.

Two structural features of the protocol deserve emphasis. First, the scorer asymmetry — AI for Sein rows, domain expert for Sollen rows — is not a design preference but a consequence of the decomposition derived in Section 2. Sein-type judgments admit data-grounded verification; Sollen-type judgments require a legitimacy source that AI cannot supply. Second, the workflow itself embodies the asymmetry it measures: Steps 1 through 3 are fully automatable (externalization-cost processing); the expert's decisive scoring interventions occur at Steps 1b and 4 (specification in its Sollen dimension). A protocol for measuring the delegation legitimacy boundary that was itself fully delegable would be self-defeating.

The asymmetry also has an institutional function. Sein-row scoring by AI is not neutral in an absolute sense — model architecture, training data, and reward design carry their own biases — but it can provide a procedural check on interpersonal distortions that often affect human evaluation, including status protection, face-saving, motivated reasoning, and local political pressure. The point is not to treat AI as an authority, but to use it as a provisional factual scorer whose outputs remain auditable and contestable. This procedural function is one structural reason why the asymmetry is institutional rather than merely technical.

**Expert selection.** Domain-specific criteria are a matter for each field, but scorers should hold accountability for the relevant judgment type, occupy an evaluative role, and, where possible, score independently with adjudication.

**Validity conditions and failure modes.** The assay's predictive validity rests on evidence that specification quality predicts output quality independently of externalization-cost quality — a condition supported by the Mekiki case study and by Thorgeirsson et al. (2026), who found that computer-science achievement predicted AI-assisted programming performance ("vibe coding") (r = 0.39) while LLM usage frequency correlated negatively (r = -0.26). Discriminant validity requires that Sein-type and Sollen-type scores vary independently; the domain-ablation experiment (Section 3.3 below) and Kusumegi et al.'s population-level data both confirm this independence. The assay admits two principal failure modes. False positives occur when high externalization-cost quality masks the absence of specification — fluent prose concealing hollow content, or sycophantic AI output (Chandra et al. 2026) reinforcing a user's Sollen commitment without independent warrant. False negatives occur when residual externalization-cost friction renders genuine specification invisible — an expert whose judgment is sound but whose articulation is poor receives artificially low scores.

### 3.3 Worked example: a minimal demonstration

To illustrate the protocol's separating power, two judgments from the Mekiki case study are scored here, selected as analytically clean representatives — one Sein-dominant, one Sollen-dominant — from the case study's larger inventory of feature decisions; the full inventory is available in the companion article (Tomita 2026).

**Judgment A** (Sein-dominant): "A current-based data structure reflects charging state more accurately than a kilowatt-hour display." Sein row: 2 (verifiable by data comparison). Sollen row: 0 (no value commitment involved). Operation type: *detect*.

**Judgment B** (Sollen-dominant): "Real-time charger availability data should not be displayed, even if technically obtainable, because unreliable availability information would undermine the application's purpose as a planning tool." Sein row: 1 (the data could in principle be retrieved). Sollen row: 2 (a value judgment about what information to withhold from users). Operation type: *exclude*.

Under the domain-ablation conditions reported in the companion article — where AI systems built the same application without domain expertise — the Sein row retained partial function (data retrieval succeeded) but the Sollen row dropped systematically toward zero: no exclusion judgments, no user-relevance filtering, no prioritization, and, in some cases, even factual semantics were misread. The two components separate on the rubric, and the scorer asymmetry follows as a structural necessity. Section 4 applies the assay at a larger scale, re-describing the full SECI model through the Sein/Sollen decomposition.

**Criterion contamination.** This worked example is drawn from the theory-builder's own case study. Independent validation through blind scoring by domain experts who are naive to the framework would constitute a necessary external-validity test; the present demonstration establishes only that the protocol can be *applied* and that it *separates* the two components as predicted.

### 3.4 Philosophical frameworks as candidate assay axes

The Sein/Sollen distinction is the minimal axis required for the present assay, but it is not the only philosophical distinction that could serve as a measurement coordinate. Aristotle's *phronesis* — practical wisdom, the capacity to judge rightly in particular circumstances (Aristotle, *Nicomachean Ethics* VI) — provides a candidate axis for evaluating context-dependent Sollen-type specification: not whether a judgment conforms to a rule, but whether it reflects appropriate discernment of the situation. Kant's distinction between determinative judgment (applying a given universal to a particular case) and reflective judgment (finding a universal for a given particular) maps onto the AI-amenable/AI-resistant divide from a different angle: determinative judgment is structurally closer to Sein-type evaluation; reflective judgment to Sollen-type. Wright et al. (2026), who used large language models as zero-shot personality assays, demonstrated that AI can function as a measurement instrument for psychological constructs — a precedent for the broader claim that AI-mediated evaluation can serve as a cognitive assay, provided the construct being measured is carefully specified.

A further candidate axis lies within Sollen-type specification itself. Nagel's (1986) taxonomy of agent-relative and agent-neutral reasons (cf. Parfit 1984) suggests that Sollen-type components may admit sub-classification — utilitarian considerations (agent-neutral), autonomy-based commitments (agent-relative), deontological obligations (agent-relative but universalizable). The present protocol treats Sollen-type specification as an undifferentiated category by design: this is the minimal decomposition required for the assay to function, and sub-classification is deferred. What matters for the present argument is Nagel's demonstration that none of these sub-categories is reducible to agent-neutral terms — and therefore none is reducible to Sein-type evaluation. The irreducibility holds regardless of how finely the Sollen side is carved.

The same distinction also has a dynamic implication: when evaluative commitments associated with Nagel's reasons become embedded in social practice, their institutionalization should be described as a state change within Sollen-type specification, not as a conversion of Sollen-type specification into Sein-type specification. The distinction introduced here is therefore dynamic rather than taxonomic. At the level relevant to delegation, agent-relative evaluative commitments sustained through practice and oriented toward ideals of excellence constitute a Do-type state of Sollen-type specification (from Japanese *dō*, practice-sustained engagement; elaborated in Section 6.5). Through social processes of legitimacy acquisition, such commitments can become institutionalized and textualized — codified in regulations and professional standards, or otherwise represented in training data — thereby taking Sin-type form, where Sin abbreviates Sollen institutionalized: a state in which normativity operates primarily through compliance and violation avoidance. In this form, Sin-type material is agent-neutralized and more readily absorbed by AI as reproducible textual regularity. This is the limited, operational sense in which Sin-type material behaves structurally like Sein-type specification: AI can reproduce the codified settlement, but it does not inherit the legitimacy by which that settlement became authoritative. Conversely, when institutional conditions shift, when codified rules become contested, or when their application becomes underspecified, Sin-type material reopens into Do-type judgment. Reasons of autonomy therefore remain the clearest limiting case for legitimate delegation: their outputs may later be institutionalized, but the evaluative standard originates within the agent and cannot itself be absorbed as reproducible textual regularity. This dynamic distinction is introduced as an interpretive extension, not as an additional scoring dimension in the present protocol. These axes are not developed further here; they are noted as coordinates available for future assay designs.

## 4. First application: re-describing SECI through the assay

The cognitive assay developed in Sections 2 and 3 was derived from the Externalization process. But as Section 2.4 established, the Sein/Sollen distinction is orthogonal to the SECI process distinction: it applies within any process, not between them. This section carries out the matrix analysis that orthogonality permits, decomposing each of Nonaka and Takeuchi's (1995) four knowledge-creation processes into its externalization-cost, Sein-type specification, and Sollen-type specification components. The re-description is not an exegesis of the original model but a constructive refinement: it asks what structural asymmetries become visible when SECI is examined through the assay's lens.

### 4.1 Externalization: the Mekiki framework's direct domain

Externalization — converting tacit knowledge into explicit form — is the process where AI's impact is most immediately visible and where the Mekiki framework was originally derived. The Sein/Sollen decomposition reveals why. Externalization is dominated by externalization cost: the technical effort of translating what one knows into documents, code, diagrams, or formal specifications. AI compresses this cost dramatically. Sein-type specification participates as the factual content being converted — the data structures, causal relationships, and empirical regularities that enter the formal output. Sollen-type specification, however, remains invariant through the Externalization process: the judgment of *what ought to be externalized*, which priority to assign, which information to withhold, does not change merely because the conversion has become easier. Kusumegi et al. (2025) documented this invariance at population scale: AI improved the externalization-cost dimension of two million manuscripts while leaving acceptance rates — a proxy for specification quality — unchanged.

### 4.2 Combination: AI's strongest domain

Combination — integrating, sorting, and recategorizing explicit knowledge — is the process most saturated with externalization cost and correspondingly most amenable to AI acceleration. Database integration, cross-referencing of literature, pattern detection across codified sources: these are operations on already-formalized knowledge, and AI performs them at a speed and scale that no human team can match. Sein-type specification is low because the knowledge being combined has already been formalized; its factual adequacy was established during prior Externalization. Sollen-type specification enters only at evaluation: *which* combinations are meaningful, which juxtapositions merit attention, which syntheses serve a purpose. The Combination process itself is largely automatable; the judgment of what its outputs *mean* is not.

### 4.3 Socialization: the domain of Sollen-type specification

Socialization — the sharing of tacit knowledge through shared experience, co-practice, and what Nonaka and Takeuchi called "intellectual combat" — is the process where Sollen-type specification is most concentrated. This is where value judgments are formed, contested, and revised: what matters in this domain, what standards of quality to maintain, what norms to absorb or challenge. The sharing of factual knowledge (Sein-type) can increasingly be supported by documentation or AI-mediated translation, but the *non-trivial revision of value commitments* — the moment when a practitioner's evaluative framework shifts through encounter with a different perspective — requires human deliberation. AI can participate in Socialization, generating alternative perspectives or surfacing overlooked considerations; but it cannot serve as the *source of legitimacy* for the resulting normative commitments. The delegation legitimacy boundary is most visible here. Scharfmann, Marx, and Fleming (2025), analyzing 682,000 researchers who moved between academia and industry, found that cross-domain co-location — a form of institutionalized Socialization — systematically increased the novelty and impact of subsequent work. The pattern they documented is consistent with the mechanism the assay would lead one to expect: exposure to different Sollen-type commitments (different standards, different priorities) catalyzes specification refinement in ways that no amount of within-domain Combination can achieve.^[The Socialization process as described here concerns the exchange of tacit knowledge between agents. The cultivation of an individual's practical judgment capacity — what Nonaka and Takeuchi (2011) sought in the concept of *phronesis* (practical wisdom) as a complement to SECI — lies outside SECI's organizational scope. Whether AI can support the formation of such internal evaluative capacity is a question for future inquiry; its efficacy would depend on the strength of the user's pre-existing internal standards.]

### 4.4 Internalization: AI as catalyst, not substitute

Internalization — absorbing explicit knowledge into individual tacit practice — is weighted toward Sein-type specification: the practitioner learns established facts, procedures, and patterns until they become second nature. AI can serve as a catalyst in this process, providing adaptive instruction, worked examples, and immediate feedback that accelerate the absorption of codified knowledge. But Internalization also involves normative recalibration: the practitioner does not merely acquire facts but develops a sense of *what matters* within a domain — an evaluative orientation that emerges through practice rather than instruction. This Sollen-type dimension of Internalization is what distinguishes expertise from mere knowledge: the expert not only knows the facts but has internalized the evaluative commitments that govern their application. AI can support the Sein-type dimension of Internalization; it cannot substitute for the experiential formation of evaluative judgment.

### 4.5 The rate-limiting shift: an analytic consequence

Table 1 summarizes the decomposition; Fig. 2 provides a visual representation of the rate-limiting shift.

**Table 1. SECI processes decomposed by the cognitive assay's three components.**

| SECI process | Ext. cost | Sein-type Spec. | Sollen-type Spec. | AI effect |
|---|---|---|---|---|
| **S (Socialization)** | Low | Medium | **High** | Low (no legitimacy source) |
| **E (Externalization)** | **High** | Medium | Low (invariant) | **Maximal** (cost compression) |
| **C (Combination)** | **Highest** | Low | Low (evaluation only) | **Maximal** |
| **I (Internalization)** | Medium | **High** | Medium (emerging Sollen) | Medium (catalytic support) |

The pattern is structural. AI's maximal effect falls on the two processes — E and C — where externalization cost dominates. Its minimal effect falls on S, where Sollen-type specification dominates and the delegation legitimacy boundary is most active. I occupies an intermediate position: AI can catalyze the Sein-type absorption but cannot substitute for the experiential formation of evaluative commitments.

The consequence for the SECI spiral's dynamics follows analytically. When two processes in a sequential cycle are dramatically accelerated while the other two remain at human speed, the effective rate-limiting stage shifts to the unaccelerated processes. In reaction-pathway kinetics, the slowest step in a sequential pathway determines the overall throughput. Applied to SECI: AI acceleration of E and C shifts the effective bottleneck to S and I. This is not an empirical finding but an analytic consequence of the matrix above — a structural prediction that follows from the assay's decomposition.

The matrix values in Table 1 are theoretical assignments — ordinal characterizations derived from the assay's logic, not measured quantities. Empirical calibration of these values across domains is a matter for future research. What the matrix provides is not measurement but *structural visibility*: it makes explicit which cells carry the specification that AI cannot supply and which carry the cost that AI compresses. The rate-limiting prediction follows from the structure regardless of the precise values in each cell.

One further structural feature deserves note. Sein-type specification undergoes a spiral transition across SECI cycles: what begins as novel factual insight (high specification cost) is, through repeated Externalization and Combination, gradually codified and absorbed into routine processing — eventually becoming part of the externalization-cost infrastructure that subsequent cycles take for granted. Sollen-type specification does not undergo this transition. Value commitments may be revised through Socialization, but they do not migrate into automated processing; they remain institutionally tied to human evaluative authority. This asymmetry reinforces the rate-limiting prediction: AI's domain expands along the Sein axis but encounters a structural boundary along the Sollen axis.

## 5. Convergent evidence

The assay proposed in this article is a conceptual-operational contribution, not an empirical study. However, the decomposition it introduces generates structural predictions, and several independent bodies of evidence — none designed to test the framework — converge on patterns consistent with those predictions. This section organizes that evidence by validity type.

### 5.1 Predictive validity

The assay predicts that specification quality determines output quality independently of externalization-cost quality. Three independent observations are consistent with this prediction at different scales. The Mekiki case study (Tomita 2026) documented that specification-present conditions produced a deployable application within ten days, while specification-absent conditions (domain-ablation) produced functionally complete but domain-inappropriate outputs — the same AI, different specification, different quality. Thorgeirsson, Weidmann, and Su (2026), in a controlled study of one hundred computer-science (CS) students, found that prior CS achievement predicted vibe-coding performance — a direct individual-level analog of specification predicting output quality. At industrial scale, Anthropic's Project Glasswing (Anthropic 2026a) reported that Claude Mythos Preview autonomously discovered thousands of zero-day vulnerabilities across all major operating systems and web browsers — a saturation of the Externalization process in cybersecurity. The resulting bottleneck was not further vulnerability discovery but triage, remediation priority, and coordination among partner organizations — the kinds of Socialization- and Internalization-weighted activities that the assay's matrix (Table 1) would lead one to expect as rate-limiting under AI acceleration of E and C.

### 5.2 Discriminant validity

The assay predicts that Sein-type and Sollen-type components vary independently — that improving one does not automatically improve the other. Kusumegi et al. (2025), analyzing two million academic manuscripts, provided the largest available test of this prediction: AI-assisted writing substantially improved linguistic quality (externalization cost reduced) while journal acceptance rates remained unchanged (specification quality unaffected). The two components varied independently in a population-level natural experiment. Thorgeirsson et al. (2026) confirmed the same independence at the individual level: writing ability (an externalization-cost proxy) ceased to predict vibe-coding performance after controlling for cognitive ability, while CS achievement (a specification proxy) remained a significant predictor — the two constructs are statistically separable. The Mekiki domain-ablation experiment demonstrated the extreme case: AI systems with full externalization-cost processing capability but zero domain specification produced outputs in which the Sollen row dropped to zero while the Sein row retained partial function — a counterfactual demonstration that the two components can be dissociated.

### 5.3 Convergent and ecological validity

Two further studies provide convergent support from different disciplinary angles. Kubota et al. (2026), in an LLM-assisted replication study, observed a gradient from verifiability to generalizability in the dimensions of scientific work that AI could replicate — a gradient that maps onto the externalization-cost-to-specification continuum, providing methodological support for the assay's operational structure. Scharfmann, Marx, and Fleming (2025), whose cross-domain co-location findings were discussed in Section 4.3, provide ecological support from the opposite direction: the pattern they documented is consistent with the assay's prediction that S-process investment refines specification in ways that C-process activity cannot. Huang (2025), writing independently on content moderation, proposed a parallel shift from accuracy to legitimacy as the evaluative framework for LLM-assisted decisions — a domain-specific instance of the general decomposition proposed here. Klowden and Tao (2026), analyzing AI-generated mathematical output, identified what they call an "unprecedented separation of form and thought" — the observation that AI can produce formally correct derivations that lack the conceptual coherence a mathematician would recognize. What Tao describes informally as a "smell test" for mathematical argument is, in the present framework's terms, a Sollen-type specification judgment: an evaluative assessment that cannot be reduced to formal verification. The structural tension they document — between externalization-cost quality (formal correctness) and specification quality (mathematical insight) — is an independent observation of the same decomposition in a domain far removed from the case study that generated the present framework.

Additional convergent signals come from three further fields; none tests the assay directly, but each registers the same asymmetry in a neighboring vocabulary. Dell'Acqua et al. (2026), in a field experiment with 758 knowledge workers, found that AI assistance improved productivity and quality for tasks within the "jagged technological frontier" but reduced accuracy by 19 percentage points for tasks beyond it — a boundary that maps onto the externalization-cost/specification divide. Tang et al. (2025) showed that once rewards become unverifiable, reinforcement learning for language models requires different objectives and weaker evaluation guarantees — a machine-learning indication that Sein-type evaluation scales more readily than Sollen-type evaluation. Dorner, Nastl, and Hardt (2025) proved mathematically that AI evaluators at the evaluation frontier cannot achieve efficiency gains exceeding a factor-two improvement over the ground-truth baseline — a formal bound on the automation of judgment that is consistent with the scoring asymmetry proposed here. These three studies, drawn from organizational science, machine learning, and evaluation theory respectively, triangulate the same structural non-symmetry from independent starting points.

### 5.4 Failure modes

The assay's practical utility depends on acknowledging where it fails. Two principal failure modes deserve attention. *False positives* — the assay returns a positive specification signal where none exists — arise when high externalization-cost quality masks the absence of specification. This risk is structurally highest for agents with strong externalization-cost processing: the more fluent the output, the harder it is to detect hollow content underneath. Chandra et al. (2026), modeling sycophantic AI interactions, showed that confirmatory AI output can reinforce a user's normative commitments without independent warrant, producing a delusional spiral in which both the user and the system converge on a position that no external evidence supports. In the assay's terms, sycophancy inflates the Sollen row without grounding it. *False negatives* — genuine specification goes undetected — occur when residual externalization-cost friction renders specification invisible: an expert whose judgment is sound but whose articulation is poor receives artificially low scores on both rows. The same dataset that supports predictive validity (Section 5.1) also bears on failure-mode detection: Thorgeirsson et al.'s finding that LLM usage frequency correlated negatively with performance is consistent with this mode: frequent AI use without specification may not merely fail to help but may actively obscure the signal that the assay seeks to detect.

## 6. Discussion

Having specified the scoring protocol, this discussion turns to what the framework clarifies about legitimate delegation in AI-assisted knowledge work. The central implication is not that AI cannot contribute to judgment, but that different components of specification differ in their susceptibility to externalization. As noted in Section 3.4, Sein-type components and Sin-type material can often be reproduced as textual regularities, whereas Do-type commitments and other agent-relative residues require renewed human evaluation. The following sections therefore move from measurement to the practical boundary of legitimate delegation.

### 6.1 The assay structure in practice: convergent implementation and convergent failure

The scoring structure proposed in Section 3 — Sein-row evaluation by AI, Sollen-row evaluation by domain expert — is not merely a theoretical construct. Independent domains have begun to implement structurally equivalent arrangements, and independent analyses have documented what happens when the arrangement is absent.

Howard et al. (2026), in a clinical trial of algorithmic antibiotic prescribing, integrated AI prediction of pathogen susceptibility (Sein-type: which bacteria are likely present and which drugs will be effective) with clinician value-weighting of treatment preferences (Sollen-type: narrow-spectrum oral agents are preferable when clinically equivalent). The result was a dramatic increase in WHO Access antibiotic selection (75.6% versus 11.9% under human-only prescribing) with no loss in pathogen coverage. The structural explanation is that AI removed Sein-type uncertainty from the prescribing decision, allowing clinicians' Sollen-type commitments — preferences they had always held but could not act on under conditions of diagnostic uncertainty — to reach the prescription. Howard et al. themselves cite Stader (2024), indicating that the philosophical bridge between judgment and calculation was already visible to the implementers.

Sode (2026), writing in this journal, documented the inverse pattern. In criminal-justice risk assessment, the COMPAS algorithm's Sein-type outputs (recidivism probability estimates) were treated as Sollen-type justifications for sentencing decisions — what Sode calls "accountability washing." The Sein/Sollen boundary was not merely absent but actively violated: technical rationales were laundered into normative warrants. The institutional consequence was that judges who deviated from algorithmic recommendations faced disproportionate blame, suppressing the very Sollen-type judgment that the system nominally preserved.

The framework renders both cases structurally intelligible without claiming that the Sein/Sollen separation was the sole cause of success or failure. Howard et al. implicitly separated the two rows and assigned each to the appropriate scorer. COMPAS collapsed them. The assay provides a vocabulary for stating what went right and what went wrong — and, more importantly, for designing arrangements that avoid the collapse before it occurs. Taken together, the companion papers themselves exemplify the kind of cross-domain analytical transfer the assay describes: a pharmacological mode of selective decomposition redeployed across knowledge management, philosophy, social diagnosis, and clinical practice.

### 6.2 Implications for AGI discourse

Current large language models, viewed through the assay's lens, function as domain-general cognitive catalysts: they accelerate externalization-cost processing across all domains but depend on the user for specification — for the judgments about what matters, what to prioritize, what to discard. A catalyst increases reaction speed without determining reaction direction. Much of the confusion in "functional AGI" discourse arises from conflating the generalization of externalization-cost processing with the generalization of specification judgment. The assay's decomposition offers a structural clarification: LLM externalization-cost processing has generalized; specification judgment has not. The delegation legitimacy boundary holds regardless of the system's architecture, at least as long as legitimacy over value judgments remains institutionally attributed to human agents.

### 6.3 Agent-relative residues in LLM output

The delegation legitimacy boundary was derived for human judgment, but its structural logic extends to a governance question about LLM output itself. When a large language model generates text, the output may carry what Nagel (1986) would recognize as agent-relative components — evaluative weightings, implicit priority orderings, and normative framings that are structurally difficult to exclude from natural-language generation. Two recent lines of evidence suggest that this is not merely a theoretical possibility. Anthropic's System Card for Claude Mythos Preview reports internal feature detection of strategic reasoning, norm-violation recognition, and evaluation awareness within the model's latent representations (Anthropic 2026b, §7.9) — residual structure that persists despite alignment training. At the behavioral level, the same report documents a dissociation between task preference and helpfulness judgment (r = 0.48; Anthropic 2026b, §5.7): the model's evaluative orientation toward tasks does not reduce to its competence assessment, a pattern that constitutes a behavioral analogue of agent-relative/agent-neutral separation. In pharmacological terms, these findings indicate that LLM output contains agent-relative residues — components whose presence requires labeling rather than elimination. The Klowden and Tao (2026) observation discussed in Section 5.3 points to the same structural tension from the user's side. A scoring protocol that decomposes output into Sein-type and Sollen-type components could, in principle, serve as such a labeling instrument — though the design and validation of such an application lies beyond the present article's scope. If such labeling can be implemented at the point of generation, it could in principle support provenance analysis of Sollen-type residues across successive model generations — identifying not only that evaluative commitments are present in a model's output, but, where lineage metadata are available, what kind they are and from which training or alignment pathway they most plausibly arise. The analogy to targeted therapy in pharmacology is instructive: selective intervention becomes possible only once the molecular marker has been identified; the assay precedes the treatment.

### 6.4 Scope, limitations, and safeguards

The assay's scope is delimited by the SECI processes it re-describes. Bodily Sein that is shared a priori — hunger, warmth, pain — does not enter the SECI spiral and lies outside the framework's reach. The matrix values in Table 1 are theoretical assignments; empirical calibration across domains is a matter for future research. Extension to individual cognition, organizational design, or regulatory policy is possible but belongs to the domain experts of those respective fields.

The effect of externalization-cost removal is not uniform across users. It depends on the strength of the user's internal evaluative standards — what Nagel's reasons of autonomy would characterize as the agent's own criteria of quality. For users whose internal standards are well formed, externalization-cost compression functions as a liberation of creative expression: specification that was previously trapped behind articulation barriers becomes actionable. For users whose internal standards are fragile, AI output may function as a substitute standard, creating the conditions for delusional spirals (Chandra et al. 2026) in which the system reinforces commitments that no independent evaluation supports. Developing application guidelines that account for this heterogeneity in users' cognitive profiles is an important direction for future work.

The delegation legitimacy boundary is not a warrant for expert authoritarianism. Sollen-type judgments require a legitimacy source that AI cannot provide, but that source must remain contestable (Henin and Le Métayer 2022) and subject to audit transparency (Manheim et al. 2025). Nor is the boundary a responsibility boundary: locating normative authority in human agents does not automatically transfer engineering, regulatory, or institutional accountability. The Mekiki framework noted that removing the translation layer makes the domain expert a de facto design authority; this does not mean that downstream responsibilities — security, scalability, accessibility, regulatory compliance — follow automatically. Finally, if the rubric becomes a thin checklist, it conceals rather than reveals the contestable nature of expert judgment, defeating the instrument's purpose.

A broader institutional consequence follows. As AI reduces externalization cost, traditional proxies for intellectual labor — fluency, length, polish, visual finish, or visible effort — become less reliable indicators of specification quality. Evaluation systems that continue to reward these proxies risk measuring externalization artifacts rather than the judgments they are meant to represent. The assay is one response to this proxy collapse: by separating specification from externalization cost, it provides a measurement target that is not displaced by AI-mediated production.

The protocol itself is not exempt from this requirement. Its categories, anchors, and expert-selection criteria must remain contestable; otherwise the assay would reproduce the very closure it is meant to diagnose.

A final, explicitly speculative implication remains outside the present article's scope. The agent-relative residues discussed in Section 6.3 suggest that the cognitive assay's analytical vocabulary may eventually find application not only in measuring human judgment but in describing AI's own internal architecture — a possibility that the title's use of "cognitive" rather than "human" deliberately leaves open.

### 6.5 Do-type as a heuristic extension

A final, more heuristic implication concerns the label Do-type introduced for practice-sustained Sollen-type specification. The immediate bridge is Nonaka and Takeuchi's knowledge-management vocabulary of wisdom and strategy as a "way of life" (Nonaka and Takeuchi 2019, 2021). Its more specific conceptual anchor is Japanese *dō/michi*, understood by Kasulis and Bouso as a Way of engaging reality and a mode of engaged knowing rather than a detached method (Kasulis and Bouso 2026). This use is heuristic, not essentialist: it should be read alongside Kasulis's caution against treating "Japanese philosophy" as a single cultural essence (Kasulis 2019). Contemporary analyses of *budō* provide one concrete case of practice, value internalization, and life-forming self-cultivation (Cynarski 2022), while possible functional analogues in other contexts include phronesis, craftsmanship, and deliberate practice. The point is not to derive the scoring protocol from Japanese culture, but to name a form of Sollen-type specification that remains practice-sustained even when adjacent norms become institutionalized.

## 7. Conclusion

This article derived a decomposition within the specification concept introduced by the Mekiki framework (Tomita 2026), grounding the distinction in the is–ought separation (Hume 1739; Kant 1781, 1785) and operationalizing it as the axes of a cognitive assay. The resulting five-step scoring protocol — Sein-type to AI, Sollen-type to domain expert — addresses the conceptual-operational gap identified in the Introduction: not another argument for the importance of human judgment, but an instrument for decomposing it.

As a first application, the assay re-described the four processes of the SECI model (Nonaka and Takeuchi 1995) through its three-component decomposition. The analytic consequence is that AI's acceleration of Externalization and Combination — the two processes most saturated with externalization cost — shifts the effective rate-limiting stage to Socialization and Internalization. Socialization is where Sollen-type specification is primarily contested and revised; Internalization is where Sein-type specification is primarily absorbed into individual practice. Both remain human-limited processes. In AI-saturated knowledge-creation systems, the bottleneck is no longer the conversion of expertise into formal output; it is the formation and renewal of the evaluative commitments that give output its direction. AI investment alone cannot accelerate this bottleneck. Investment in the human processes — mentoring, cross-domain exposure, deliberative practice, institutional arrangements that protect evaluative capacity — is the structural complement that AI acceleration requires.

More broadly, the framework reframes the risk of AI-assisted knowledge work as a problem not only of accuracy but of cognitive reproduction. AI can expand access to codified knowledge — what an older vocabulary might call *scientia* — while weakening the human cultivation of situated judgment — *sophia* — if delegation substitutes for the learning and evaluation through which legitimacy is maintained. This concern parallels recent models of knowledge collapse, in which highly accurate agentic AI can improve contemporaneous decisions while eroding the learning incentives that sustain long-run collective knowledge (Acemoglu et al. 2026). The scoring protocol proposed here therefore functions as a practical safeguard: it helps identify where AI assistance can legitimately reduce externalization cost and where human evaluative commitment must be retained by responsible agents.

The assay has shown which parts of human judgment ought not to be discarded. The structural description of what *ought to be* discarded — which Sein-type determinations are ready for routinization, which Sollen-type commitments require revision, and how the boundary between them shifts across domains — is the next question.

What this assay ultimately helps protect is the locus of autonomous human judgment: the domain in which human agents retain authority to set the ends that guide their work. Mapping this locus precisely, rather than allowing it to be ceded by default, is what the convergence of philosophy and cognitive measurement now makes possible.

---

## Postscript

Mekiki — the Japanese term for expert discernment — names the vernacular practice that the present article operationalizes through philosophical decomposition and a measurement protocol. In broader humanistic vocabulary, the structural domain this article maps might be described as a *garden of humanity*: a region of evaluative authority that requires continuous cultivation rather than one-time demarcation, and that risks being ceded by default when externalization-cost compression is mistaken for specification maintenance. The main text uses operational language throughout; this metaphor is left undeveloped here. Yet do not confuse any *mirage garden of AI* with your own.

---

## Ethical approval

This article does not contain any studies with human participants performed by the author.

## Informed consent

Not applicable.

## Author contributions

K.T. is the sole author and is responsible for all aspects of the work.

## Competing interests

The author declares no competing interests.

## Data availability

No new datasets were generated for this article.

---

## References

Acemoglu D, Kong S, Ozdaglar A (2026) AI, human cognition and knowledge collapse. NBER Working Paper 34910. https://doi.org/10.3386/w34910

Anthropic (2026a) Project Glasswing: securing critical software for the AI era. https://www.anthropic.com/glasswing. Accessed 9 Apr 2026

Anthropic (2026b) System card: Claude Mythos Preview. https://www.anthropic.com/claude-mythos-preview-system-card. Accessed 9 Apr 2026

Aristotle (2009) The Nicomachean ethics (trans: Ross WD, rev. Brown L). Oxford University Press, Oxford

Beckman L, Hultin Rosenberg J, Jebari K (2024) Artificial intelligence and democratic legitimacy: the problem of publicity in public authority. AI Soc 39:975–984. https://doi.org/10.1007/s00146-022-01493-0

Böhm K, Durst S (2026) Knowledge management in the age of generative artificial intelligence — from SECI to GRAI. VINE J Inf Knowl Manag Syst 56(1):106–121. https://doi.org/10.1108/VJIKMS-10-2024-0357

Chandra V, Kleiman-Weiner M, Ragan-Kelley J, Tenenbaum JB (2026) Sycophantic chatbots cause delusional spiraling, even in ideal Bayesians. arXiv:2602.19141

Collins H (2025) Why artificial intelligence needs sociology of knowledge: parts I and II. AI Soc 40(3):1249–1263. https://doi.org/10.1007/s00146-024-01954-8

Concannon S, Tomalin M (2024) Measuring perceived empathy in dialogue systems. AI Soc 39(5):2233–2247. https://doi.org/10.1007/s00146-023-01715-z

Cynarski WJ (2022) New concepts of budo internalised as a philosophy of life. Philosophies 7(5):110. https://doi.org/10.3390/philosophies7050110

Dastani M, Yazdanpanah V (2023) Responsibility of AI systems. AI Soc 38(2):843–852. https://doi.org/10.1007/s00146-022-01481-4

Dell'Acqua F, McFowland III E, Mollick E, Lifshitz H, Kellogg KC, Rajendran S, Krayer L, Candelon F, Lakhani KR (2026) Navigating the jagged technological frontier: field experimental evidence of the effects of artificial intelligence on knowledge worker productivity and quality. Organ Sci 37(2):403–423. https://doi.org/10.1287/orsc.2025.21838

Dorner FE, Nastl VY, Hardt M (2025) Limits to scalable evaluation at the frontier: LLM as Judge won't beat twice the data. In: Proceedings of ICLR. arXiv:2410.13341

Ferdman A (2025) AI deskilling is a structural problem. AI Soc. https://doi.org/10.1007/s00146-025-02686-z

Gill KS (2023) Why thinking about the tacit is key for shaping our AI futures (Editorial). AI Soc 38:1645–1648. https://doi.org/10.1007/s00146-023-01758-2

Henin C, Le Métayer D (2022) Beyond explainability: justifiability and contestability of algorithmic decision systems. AI Soc 37:1397–1410. https://doi.org/10.1007/s00146-021-01251-8

Howard A, Green A, Zhong M et al (2026) Algorithmic antibiotic decision-making in UTI using prescriber-informed prediction of treatment utility. npj Digit Med. https://doi.org/10.1038/s41746-026-02369-z

Huang T (2025) Content moderation by LLM: from accuracy to legitimacy. Artif Intell Rev 58:320. https://doi.org/10.1007/s10462-025-11328-1

Hume D (1739/2000) A treatise of human nature (eds: Norton DF, Norton MJ). Oxford University Press, Oxford

Kant I (1781/1998) Critique of pure reason (trans: Guyer P, Wood AW). Cambridge University Press, Cambridge

Kant I (1785/2012) Groundwork of the metaphysics of morals (trans: Gregor M, Timmermann J). Cambridge University Press, Cambridge

Kasulis TP (2019) Japanese philosophy? No such thing: Japan's contribution to world philosophizing. Int J Asian Stud 16(2):131–142. https://doi.org/10.1017/S1479591419000147

Kasulis TP, Bouso R (2026) Japanese philosophy. In: Zalta EN, Nodelman U (eds) The Stanford encyclopedia of philosophy (Spring 2026 edition). Metaphysics Research Lab, Stanford University. https://plato.stanford.edu/archives/spr2026/entries/japanese-philosophy/

Klowden T, Tao T (2026) Mathematical methods and human thought in the age of AI. arXiv:2603.26524

Kubota S, Yakura H, Coavoux S, Yamada S, Nakamura Y (2026) LLM-assisted replication for quantitative social science. arXiv:2602.18453

Kusumegi K, Yang X, Ginsparg P, de Vaan M, Stuart T, Yin Y (2025) Scientific production in the era of large language models. Science 390(6779):1240–1243. https://doi.org/10.1126/science.adw3000

Manheim D, Martin S, Bailey M, Samin M, Greutzmacher R (2025) The necessity of AI audit standards boards. AI Soc 40(8):6609–6624. https://doi.org/10.1007/s00146-025-02320-y

Nagel T (1979) Mortal questions. Cambridge University Press, Cambridge

Nagel T (1986) The view from nowhere. Oxford University Press, New York

Nonaka I, Takeuchi H (1995) The knowledge-creating company: how Japanese companies create the dynamics of innovation. Oxford University Press, New York

Nonaka I, Takeuchi H (2011) The wise leader. Harv Bus Rev 89(5):58–67

Nonaka I, Takeuchi H (2019) The wise company: how companies create continuous innovation. Oxford University Press, New York

Nonaka I, Takeuchi H (2021) Strategy as a way of life. MIT Sloan Manag Rev 63(1):56–63

Parfit D (1984) Reasons and persons. Clarendon Press, Oxford

Polanyi M (1966) The tacit dimension. Doubleday, New York

Scharfmann E, Marx M, Fleming L (2025) Pasteur's quadrant researchers bring novelty, impact to publishing, and patenting. Science 390(6776):891–893. https://doi.org/10.1126/science.adx3736

Sode K (2026) The interpreter's trap: how explainable AI launders uncertainty into justification. AI Soc. https://doi.org/10.1007/s00146-026-02885-2

Stader J (2024) Algorithms don't have a future. Philos Technol 37:82. https://doi.org/10.1007/s13347-024-00705-3

Tang Y, Wang S, Madaan L, Munos R (2025) Beyond verifiable rewards: scaling reinforcement learning for language models to unverifiable data. arXiv:2503.19618. https://doi.org/10.48550/arXiv.2503.19618

Taniguchi T, Suzuki T, Maruyama R (2026) Gendai shakai o ikiru tame no AI × tetsugaku [AI and philosophy for living in contemporary society]. Kodansha, Tokyo. ISBN 978-4-06-542373-8 (in Japanese)

Taylor I (2025) Is explainable AI responsible AI? AI Soc 40(3):1695–1704. https://doi.org/10.1007/s00146-024-01939-7

Thorgeirsson S, Weidmann TB, Su Z (2026) Computer science achievement and writing skills predict vibe coding proficiency. In: Proceedings of the 2026 CHI Conference on Human Factors in Computing Systems (CHI '26). ACM, New York. https://doi.org/10.1145/3772318.3791666

Tomita K (2026) Domain-native development: a mekiki framework for AI-assisted knowledge work. SocArXiv preprint. https://doi.org/10.31235/osf.io/cwkav_v1

Weber M (1904/2011) The "objectivity" of knowledge in social science and social policy. In: Bruun HH, Whimster S (eds) Max Weber: collected methodological writings. Routledge, London, pp 100–138

Williams B (1985) Ethics and the limits of philosophy. Harvard University Press, Cambridge MA

Wright AGC, Ringwald WR, Vize CE, Eichstaedt JC, Angstadt M, Taxali A, Sripada C (2026) Assessing personality using zero-shot generative AI scoring of brief open-ended text. Nat Hum Behav 10(3):541–555. https://doi.org/10.1038/s41562-025-02389-x

---

---

## Figure legends (images omitted)

**Fig. 1. Positioning of the present article.** The *Mekiki* framework distinguishes externalization cost from specification and decomposes specification into Sein-type and Sollen-type components. The cognitive assay operationalizes this decomposition through asymmetric scoring: AI scores Sein-type components, while domain experts score Sollen-type components. Because individual judgments may be hybrid, the delegation legitimacy boundary is a boundary zone rather than a hard line. AI may generate evaluative outputs, but legitimacy over Sollen-type components must be supplied by a domain expert. A convergent clinical implementation (Howard et al. 2026) shows the same structural separation: reducing Sein-type uncertainty enables clinicians' pre-existing Sollen-type commitments to shape the prescription, which remains a hybrid judgment.

**Fig. 2. First application of the cognitive assay to the SECI spiral.** Under conventional conditions, Externalization and Combination function as the effective bottlenecks because externalization cost constrains articulation and recombination. Once AI substantially compresses those costs, Socialization and Internalization become the effective bottlenecks. Socialization is Sollen-dominant, whereas Internalization is Sein-dominant but still partly normative; AI can catalyze Internalization but cannot substitute for the experiential formation of evaluative commitments. The shift is an analytic consequence of decomposing each SECI process into externalization cost, Sein-type specification, and Sollen-type specification, not an empirical finding; empirical calibration of the cell ratios remains future work.


---

# Paper T3 — Decomposing Agency, Isolating Answerability: Cultivating What Cannot Be Delegated in AI-Assisted Learning

**Preprint version:** 2  
**Canonical public preprint DOI:** https://doi.org/10.35542/osf.io/hvbfe_v2

**Kengo Tomita**  
Institute of Technology, Shimizu Corporation, Tokyo, Japan

## Abstract

When AI can plan, draft, and revise, what remains for the learner? This article argues that the question cannot be answered while *agency* is treated as monolithic, and decomposes learner agency by delegability — jointly with its educational companions, trainability and measurability — rather than by psychological function. Three analytic dimensions are provisionally distinguished: direction (evaluative orientation), drive in two forms (available activation and motivational drive), and mode (functional pattern of epistemic action). Mapped this way, most components admit support, training, or conversion, specifying where distribution accounts of human–AI agency apply. The decomposition also exposes a question that no capacity-based analysis can answer: who must answer for the judgments made with these capacities. That question isolates answerability — the non-transferable standing to have to answer, to those entitled to ask, for one's judgments — grounded second-personally by extending Darwall's address structure from conduct to the warrant of judgment. A design conjecture proposes that embodied encounter may support the crystallization of direction and the conversion of available activation into motivational drive, addressing formation within the capacity layer. A two-layer prescription follows: an analytic compass, encounter engineering, and AI guardrails for what can be distributed; protected second-personal exchange for what cannot. AI can help learners rehearse the competence of answering; the final normative addressee remains a legitimate human addressee — an educator, peer, professional body, or represented community.

## 1. Introduction

Generative AI has made learner agency the contested center of educational technology. When systems plan, draft, revise, and explain on request, the question of what remains for the learner to originate stops being rhetorical: capacities that instruction once cultivated because no tool could supply them must now be justified anew, and agency has become the word under which that justification is fought. Institutional responses so far oscillate between prohibition and laissez-faire — banning the tools to protect the capacities, or admitting the tools and hoping the capacities survive. Both responses treat agency as a single quantity that AI either threatens or does not. That premise is what this article examines.

Three streams converge on the concept without resolving it, because each decomposes agency for its own question. The first asks which systems qualify as agents at all. Dung (2025) shows that this field already treats agency as graded and multidimensional, profiling systems along goal-directedness, autonomy, efficacy, planning, and intentionality. But each dimension is a capacity the system possesses — even intentionality, the most demanding, asks whether a system owns and can reflectively revise its reasons, not whether anyone must answer to another for them. The vocabulary of answerability never appears in the account, and moral agency is explicitly set aside.

The second stream relocates agency from individuals to configurations. Cukurova (2026), introducing a British Journal of Educational Technology special issue on agency and self-directed learning with generative AI, argues that agency in AI-rich settings is best read as a system property — distributed and re-arranged across layered human–AI couplings, from the transactional to the synergistic — and closes with a demand this article accepts: agency must remain measurable and protected, not a residual aspiration. Notably, at the top of that account sits the learner's capacity to author meaning in ways that remain recognizably one's own, and a learning that is relationally responsible. The account is built to keep agency analyzable as capability migrates into the system, and it treats even these as measurable system properties. What it does not ask is whether everything gathered under agency migrates — and, as Section 4 argues, what appears at the summit of that account (whose judgment it remains, who must answer for it) is what a finer distribution analysis isolates rather than distributes.

The third stream is education's own: agency as an individual capacity to be fostered — resolved by psychological function into intentionality, forethought, self-reactiveness, and self-reflectiveness (Bandura, 2001); by temporal orientation into iterational, projective, and practical-evaluative dimensions (Emirbayer & Mische, 1998); with self-regulated learning supplying its most trainable core (Zimmerman, 2000). These accounts were built for human learners among human teachers. They say what agency is made of, not what may be handed over.

The streams are usually allowed to blur, because agency travels between them unmarked. A recent review consolidates the social-science treatments — Cathcart et al. (2026) sort fifty-one studies into psychological, sociological, and emergent (ecological) conceptions and argue for the emergent approach; Cukurova's distribution reading leans the same way. Those typologies map the terrain agency theory already occupies; none was built for the question AI now forces. This article does not add a fourth conception alongside them but cuts on a different axis — delegability — to answer that question. The streams should be held apart: the first concerns the attribution of agency to machines; the second its distribution across hybrid systems; this article concerns learner agency — the thing education exists to develop. Held apart, the gap becomes visible. None of the three asks the question AI forces on education: of everything gathered under learner agency, which components can be delegated, trained, or supported — and what, if anything, cannot? The same gap shows on the relational side. That education is relational is well established, from dialogic and care-ethical traditions onward; online participation modes alter opportunities for interaction, and AI-mediated assessment may affect trust — patterns documented largely through psychological and affective vocabulary (presence, belonging, connectedness, trust) — dimensions whose importance these studies document (Luo, 2025; Kortemeyer et al., 2023) — rather than as a normative relation in which one must answer for one's judgments. What is under-theorized is not that something relational matters, but the normative structure of the relation itself. Dialogic and care-ethical traditions identify the educational importance of relation; the narrower claim here is that generative AI makes newly visible the delegability of one specific relation — the one in which a learner has to stand behind a judgment as theirs (the warrant-bearing relation).

That question needs its own axis, and supplying it is this article's contribution: we decompose learner agency by delegability rather than psychological function, show that most components are trainable, supportable, or distributable across human–AI systems, and show that the decomposition exposes a question no capacity inventory can answer — who must answer for the judgments made — whose answer is answerability, a relation rather than a component, yielding a two-layer educational prescription. The move extends a line of work on AI-assisted knowledge work in which externalization (the work of turning judgment into artifacts) was first separated from specification (the judgment of what should be made) (Tomita, 2026a), and specification was then resolved into measurable and non-measurable components (Tomita, 2026b): the operator is constant; the contested concept changes. In that line's original analysis, learner agency was held constant within the human expert condition; the present article opens that background variable. Section 2 performs the decomposition and the sort. Section 3 proposes a design conjecture for the component that resists installation. Section 4 establishes what the decomposition isolates, and grounds it second-personally. Section 5 derives a prescription across two pedagogically concurrent layers, stating in each case what is deliberately left to those who must answer for it.

**Relation to adjacent research.** Four research traditions border this territory, and the axis of this article differs from each. Self-determination theory explains how external goals become autonomously endorsed through supports for autonomy, competence, and relatedness (Ryan & Deci, 2000); it concerns the *quality of motivation*, not who must answer for a judgment. The four-phase model of interest development traces how situational interest deepens into individual interest (Hidi & Renninger, 2006); it describes the *formation of direction*, and this article's encounter conjecture is a design-oriented cousin of that account rather than a rival. Self-regulated learning and its socially shared extension model how learners plan, monitor, and evaluate, alone and jointly (Zimmerman, 2002; Järvelä & Hadwin, 2013); these are *capacities and practices* — in the present vocabulary, largely supportable and trainable components. Epistemic agency in knowledge building assigns learners collective cognitive responsibility for advancing communal knowledge (Scardamalia, 2002); it is the nearest neighbor, yet its unit is the community's epistemic progress, whereas answerability is a dyadic normative standing: a particular learner answering to a particular questioner for a particular judgment. These traditions do not foreground the specific distinction developed here — between distributed performance and the identifiable bearer of a judgment's warrant. The contribution is therefore not the discovery that educational relations matter, but the articulation of a delegability distinction within them.

**Two layers, announced.** The argument proceeds on two layers that must not be conflated: a capacity layer, where components can be supported, trained, or transformed under specified conditions — and where AI can legitimately participate — and a relational layer, where a learner stands answerable to particular others. The decomposition in §2 works entirely on the first layer; §4 shows what it exposes on the second.

## 2. Decomposing learner agency by delegability

### 2.1 The choice of axis

Decompositions serve questions. When Bandura (2001) resolves agency into intentionality, forethought, self-reactiveness, and self-reflectiveness, the axis is psychological function: the question is what agency consists of as a human achievement. When Emirbayer and Mische (1998) resolve it into iterational, projective, and practical-evaluative dimensions, the axis is temporal orientation: the question is how agentic action relates past, future, and present. Both decompositions answer their questions well. Neither was built for the question generative AI now forces on education: of everything gathered under "learner agency," what can be handed over — to an AI system, to a human–AI configuration, to anyone other than the learner — and what cannot?

This paper cuts along that axis. We decompose learner agency by delegability — jointly with its educational companions, trainability and measurability — rather than by psychological function. The same material, cut along a different plane, yields different cross-sections; overlap between the components below and established constructs of motivation, interest, or self-regulation is therefore expected, and is not the contribution. The contribution is what the new plane separates that the old planes keep together: functions that can be supported or partially offloaded, a component whose endorsement is non-substitutable, and a relational question that no component inventory can answer.

### 2.2 Three components

Cut this way, learner agency can be provisionally distinguished into three analytic dimensions — a working schema warranted by intervention divergence rather than claimed as a psychologically exhaustive taxonomy. *Direction* is what the learner is oriented toward. It exists in two states: a *candidate* direction — an orientation entertained but not yet owned — and an *endorsed* direction, the evaluative commitment that makes some problems theirs rather than merely assigned; endorsement may be co-authored in dialogue rather than reached alone. The endorsed state is the educational counterpart of the Sollen-type — that is, value-laden, evaluative — content that prior work located at the non-delegable core of human specification (Tomita, 2026b). Both distinctions are defined within this article as they are used, so no step of the argument presupposes either paper. *Magnitude* is the drive behind the orientation: how much force the learner brings. *Mode* denotes the repertoire of epistemic actions a learner currently tends to deploy — whether they typically create, connect, critique, or maintain — rather than a fixed learner type; the examples are illustrative, non-exhaustive, and task-sensitive. The learner who sharpens any draft put in front of them but originates none is not low in agency; they are operating in a single mode. The triad is deliberately coarse. These are sorting bins for a delegability analysis, not a new psychology of agency; each could be subdivided further, and the subdivisions would matter for other questions. For this question, three suffice, because the components already behave differently under the only test that matters here: what happens when one tries to hand each of them over. The warrant for the triad is not psychological exhaustiveness but intervention divergence: each category directs education toward a different lever under AI assistance.

### 2.3 Two forms of magnitude

Magnitude is not a single quantity. Educators will recognize the state: the learner with substantial energy and no settled object — *I want to do something; I do not yet know what.* We call this *available activation*: the learner's current, context-sensitive capacity to mobilize effort, varying with health, affect, workload, accessibility, and circumstance — not treated here as a fixed trait, nor yet anchored to any particular orientation. If drive were simply a function of direction, this state could not exist. It does, and two further observations confirm the split it implies: learners pursuing the same direction differ persistently in the force they bring to it, and learners who change direction often carry substantial energy into the new field. We therefore distinguish available activation from *motivational drive*: propulsion that exists only as anchored to a specific direction. The two forms respond to different levers. Available activation can be protected, provisioned, and depleted, but not lectured into existence. Motivational drive is derivative: it appears when a direction captures available activation. How that capture happens is the subject of Section 3. What matters for the sorting is that the two forms separate cleanly under delegability.

### 2.4 The sort

Delegability is applied here jointly with its educational companions — trainability (can deliberate practice develop it?) and measurability (can its current state be observed?). These are distinct operations, not values on a single scale; the sort records, for each component, which operations it admits. Mapped this way, the components sort cleanly.

*Available activation is supportable and protectable.* Institutions shape it through workload design, wellbeing and accessibility provision, recovery time, and the removal of depleting friction — the externalization-cost reduction that AI now performs at scale belongs here, on the support side (Tomita, 2026a). Institutions cannot reliably manufacture available activation by exhortation; the defensible levers are protection and provisioning — reducing depleting friction, designing workload and recovery — not production on demand. Nothing here licenses treating low activation as a fixed attribute of the learner, and this analysis is not proposed as a basis for admissions, selection, or deficit classification.

*Mode is trainable.* A learner whose drive habitually critiques can learn to create; repertoires widen with practice and narrow with disuse. AI systems can scaffold the weaker modes directly — drafting so the critic has an object, structuring so the connector has materials — which makes mode supportable as well as trainable, and the least contested entry in the sort.

*Motivational drive is convertible.* It is neither trained directly nor installed from outside; it is converted from available activation when a direction takes hold. The conditions under which this conversion may occur are addressed by the design conjecture in Section 3.

*Direction alone resists.* Here the sort requires precision, because what resists is not the supply of candidate directions. Proposals are cheap: a teacher can suggest ten, an AI can generate fifty on request, and both have a legitimate role in widening what a learner encounters. What cannot be handed over is ownership. A proposed direction becomes the learner's own — or fails to — through a process the proposer does not control, and the difference between an installed direction and an owned one is behaviorally visible: compliance tracks the supervisor's attention; commitment does not. Self-determination theory documented this boundary a generation ago from a different angle: externally proposed goals become integrated, rather than merely complied with, only under conditions that are relational as much as informational (Ryan & Deci, 2000) — a finding whose second-personal undertone Section 5 returns to. Direction is not installed. It crystallizes as the learner's own, or it remains someone else's.

Table 1 summarizes the sort.

**Table 1.** Learner agency under the delegability axis.

| Component | Operational status | Educational lever |
|---|---|---|
| Available activation | Context-sensitive; supportable and protectable | Workload, wellbeing, accessibility, recovery time, and removal of depleting friction |
| Mode | Trainable and supportable | Repertoire widening through practice; conditional AI scaffolding |
| Motivational drive | Hypothesized to emerge when available activation becomes anchored to an endorsed direction | Conditions supporting endorsement and sustained follow-through (Section 3) |
| Direction | Candidate directions can be proposed or co-constructed; endorsement is non-substitutable | Encounter, dialogue, reflection, and autonomy-supportive conditions (Sections 3, 5); never direct installation |

*Note.* Answerability is omitted because it is a relational status rather than a learner component. The delegability question nevertheless applies: its institutional allocation may change, but answering for a judgment cannot be performed by a substitute while the judgment remains the learner's own. Section 4 establishes this standing.

### 2.5 What the sort shows about distribution

Set this result against the distribution account of agency. Reading agency as a property of human–AI systems rather than of individuals (Cukurova, 2026) is right — indispensably right — about most of the list above: planning and execution scaffolds, support structures for available activation, mode-widening tools, even the maintenance architecture around an existing motivational drive all genuinely distribute across hybrid configurations, and the sort specifies exactly where that reading holds. What the sort adds is the location of its silence. A hybrid system can host proposals for direction in any number; what it cannot do is supply an individual learner's endorsement while the resulting judgment is still presented as that learner's own. A hybrid system may participate in forming and sustaining a shared direction; what cannot be substituted is each learner's endorsement of the commitment they claim as their own. Distribution accounts are right about what distributes — and silent about what does not. The present article is therefore not a rejection of distributed agency but a component-level restriction on what distribution can legitimately explain. And the sorted residue hands the next section its question: if direction cannot be installed, where does it come from?

## 3. A design conjecture: encounter, crystallization, conversion

If direction cannot be installed, where does it come from? We propose a design conjecture in three movements: embodied encounter with a problem-holder may contribute to the crystallization of evaluative commitment, and an endorsed direction may then anchor available activation as motivational drive. The model is deliberately spare — each movement names a condition, not a guarantee.

The metaphor is chosen for its precision, not its color. Crystallization needs a supersaturated solution and a nucleation site: the available activation of Section 2 is the supersaturation — energy without an object — and the embodied encounter supplies the site. Read this way, the model makes intelligible the two failure modes educators already know. Exhortation without encounter — telling an unengaged learner to *find their passion* — addresses a solution that has nowhere to crystallize: there is energy, but no site at which a commitment could form. Encounter without protected follow-through — a moving field placement absorbed back into a packed schedule of unrelated demands — dissolves what had begun to form. Neither failure is a motivation deficit, and neither is fixed by more exhortation.

Three heterogeneous illustrative sources display sequences compatible with this conjecture. The innovation cases assembled by Nonaka and Takeuchi (1995) show the pattern repeatedly: developers' commitments formed at sites of direct contact with users and their troubles, not in planning meetings, and the organizational machinery that mattered was the machinery that put people in front of problems and then protected what crystallized there. The publicly documented winner profiles of a recent global AI-assisted development competition show the same pattern from the opposite end of the tooling era: among the top entrants, a lawyer automating building permits, a cardiologist building post-visit care, a musician, a road engineer — practitioners whose commitments predated their tools, for whom AI removed the externalization barrier and changed nothing about where the direction had come from (in a hackathon hosted by an AI developer; Anthropic, 2026). And the single-case trajectory documented in prior work (Tomita, 2026a) shows the sequence at fine grain: a domain commitment formed in the researcher's own usage context steered the tool, not the reverse. The three sources share no method, population, or era; what they share is the shape of the sequence. Jointly, they complicate the two default stories — that direction is installed by instruction, or that it is fixed temperament — since in each case it postdates an encounter and predates the tooling. These sources are illustrative and hypothesis-generating rather than confirmatory — the third, in particular, is the author's own prior work and cannot count as independent convergence.

We present this as a design conjecture motivated by illustrative, hypothesis-generating observations — not a demonstrated mechanism. No controlled study here isolates encounter as the cause of crystallization, and the sources above were not collected to test the model they now illustrate. The model earns its place by what it organizes and by what it identifies as manipulable. Its educational translation is correspondingly modest and probabilistic: if encounter can contribute to direction formation, then education can design the conditions under which such encounters become more likely — it can guarantee exposure, never crystallization. The model should therefore be read as a design hypothesis for educational technology, not as a causal account of motivation formation. What such design looks like in practice, and what it deliberately leaves alone, is the work of Section 5.

## 4. What the decomposition isolates

### 4.1 A different kind of remainder

Direction resisted distribution, but it remained a component — something a learner comes to have. The decomposition's second function is different in kind. Run to completion, the sort yields no further component; what it leaves exposed is a relation that was never on the component list: *answerability* — the standing to have to answer for a judgment, introduced in prior work as the non-transferable relation in which the warrant of a judgment remains anchored in a particular agent (Tomita, 2026b). The grammatical contrast carries the conceptual one: one *has* a direction; one *stands in* answerability (Figure 1). A component is a property of the learner that pedagogy can act on. Answerability is not a property of the learner at all. It is a relation between the learner and those entitled to ask — which is why it could not have appeared as a fourth box however finely the sorting continued, and why treating it as one more trait to be fostered would repeat, at the level of theory, the conflation this paper exists to undo. The term is used here in a specific sense. *Answerability* already circulates in education through a Bakhtinian lineage — the answerability of an utterance or act, an ethics of being implicated (e.g., Ewald, 1993); the present sense is Darwall's, the standing to have to answer to one who can demand, and the two should not be elided.

*Figure 1 (image omitted).* Direction, drive (available activation and motivational drive), and mode are properties the learner *has*, shown as boxes within the dashed component region. Answerability is not a fourth component but a relation of address and response in which the learner *stands*: the standing to answer, to those entitled to ask, for a judgment. The figure marks the categorical contrast between components one has and a relation one stands in.

### 4.2 Not an artifact of the axis

An objection should be met before anything is built on the claim: that the delegability axis was constructed to exclude answerability, so its isolation is trivial — true by definition. Two replies, one procedural and one empirical. Procedurally, the sorting rule was applied only to capacities ordinarily counted as agency — orientation, drive, mode of acting; answerability nowhere figures in the rule, and it surfaces only when the sorted capacities, however completely enumerated, fail to explain who can be called to answer for a judgment. Empirically, the exclusion was not smuggled in by our vocabulary: in one of the most detailed multidimensional treatments of machine agency available, the terms responsibility, accountability, answerability, blame, and delegation do not occur (Dung, 2025) — an absence in that account, not a verdict on the entire field. The axis did not push answerability out of this strand of agency theory. What the absence illustrates is an omission in one detailed capacity-based account, not the absence of answerability across the wider field. The shape of the move repeats the method of prior work: there, scoring what could be scored located what could not be legitimately delegated (Tomita, 2026b); here, sorting what can be delegated exposes what was never up for delegation. The axis is not chosen to exclude answerability; it is chosen because generative AI has made handover the practical question for every component of learning agency.

### 4.3 The second-personal ground

What kind of fact is answerability, if not a capacity? Here the paper borrows, and the borrowing must be marked precisely. From Darwall (2006) we take the structure of second-personal address. Claims and demands are addressed person to person, and valid address presupposes, as its felicity condition, the addressee's second-personal competence: the capacity to recognize the demand's validity, to hold oneself to it, and so to have to answer to the addresser. Being responsible *for* something, in this account, is conceptually tied to being responsible *to* someone. In educational settings this relation is not abstract moral theory but the ordinary structure of being asked to justify one's solution, interpretation, or design choice to another person. What is borrowed is this address structure. What is original here is the extension: that the warrant of a judgment, no less than conduct, requires a bearer who can be addressed and challenged, and who must answer. Darwall theorizes demands on action; the claim that evaluative judgment stands in the same second-personal relation is this paper's move — consonant with his text, but not stated in it. Where Darwall has been brought into education before, it has largely been by way of respect and dignity (Giesinger, 2012); applying his second-personal accountability to the warrant of a learner's judgment, as the concept education must protect under generative AI, is a different route.

One feature of his account, however, transfers with particular force. Darwall freely admits representation on the claiming side: trustees may demand on another's behalf, and third parties may hold reactive attitudes for a victim. The answering side never appears by proxy — guilt's natural expressions are confession, apology, and self-addressed reproach. On the reading developed here, that asymmetry marks the joint: what cannot be done on one's behalf is precisely to answer. This sharpens a distinction prior work had begun to draw: where *accountability* can diffuse across institutional structures, *answerability* names the non-transferable relation in which the warrant of a judgment stays anchored in a particular agent (Tomita, 2026b). This article carries that distinction into education — reserving *answerability* for the non-transferable standing just described, and keeping *accountability* for institutional relations, which can, by design, be delegated, audited, and reassigned. This standing runs in the opposite direction to the *authority* that Xing et al. (2026) find learners conferring on AI teachable agents: authority is conferred by the learner and tracks perceived competence, whereas standing is retained by the one who judges and tracks answerability. The agent can be granted more authority without acquiring any standing.

Recent work offers a complementary route from the AI side: Archer and Wiltsche (2026) argue from systems' cognitive limits — the absence of world-directed, temporal, and anticipatory cognition — through an epistemic answerability to the world, that responsibility lies not in the model but in the system surrounding it, and cannot be offloaded. The two routes divide the labor — that account explains the systems, this one locates the relation — and the division is principled: an argument from present limits must be re-made each time capability moves; an argument from the structure of address does not.

### 4.4 What the relation grounds

Three matters must not be conflated: answerability as a relational standing; answer-giving competence as a developable capacity; and answerable practice as the observable enactment of that standing. Institutions assign or recognize the standing, pedagogy develops the competence to occupy it well, and research can observe its institutional allocation and behavioral enactment.

The second layer is not a decoration on the first; it is what keeps the first from collapsing into capability education. Strong, coherent direction guarantees nothing by itself — a skilled fraud has direction in abundance, and answers to no one until made to. The qualification is the point: a human fraud *can* be made to answer, and that very susceptibility — to being addressed, challenged, and held — is answerable practice: the observable enactment of a standing one occupies. A current AI system cannot be made to answer in this sense: nothing can be taken from it, no commitment of its own is at stake, and self-reproach, were it scripted, would idle. It has no such standing; for an AI-assisted judgment, the answer is institutionally assigned to a human agent. The difference is not one of degree along any of Section 2's dimensions; it is the difference between refusing a relation and being unable to stand in one. The asymmetry has a practical edge the other way as well: uncritical delegation does not leave the learner's side untouched: shifts in the frequency and sequencing of planning, monitoring, and evaluation under heavy AI reliance (Fan et al., 2025) motivate concern that the practices sustaining answerable judgment may weaken, though they do not demonstrate erosion of answerability itself — which is why the prescription that follows treats delegation as something to be shaped, not merely permitted.

The boundary this draws does not turn on a metaphysical verdict about machines. It does not require settling whether future systems may simulate address-like behavior; it concerns the educational institution's present criterion for standing — whether a learner can be called to own, revise, and answer for a judgment as theirs. That learners may experience AI systems as second-personal interlocutors — consulting them, trusting them, calling them partners — is consistent with well-attested general mechanisms of anthropomorphism and mind perception (Epley et al., 2007; Gray et al., 2007); its prevalence in educational settings remains an empirical question, and the experience does not imply that the system stands in the relation; perceiving the system as a partner and its being a legitimate addressee of answerability are distinct, on the same reading that separated conferred authority from retained standing above.

On this extension, Darwall's structural point secures the gap: the second-personal notions — authority, valid claim, second-personal reason, accountability — form an interdefinable circle that cannot be entered from outside it, so no enumeration of first-layer capacities, however long, adds up to entry.

This, in turn, grounds what prior work could only state as a condition. (By stipulation, this article reserves *accountability* for institutionally allocatable duties — reportable, transferable, auditable — and *answerability* for the non-transferable standing; Darwall's own use of the former term is broader.) Tomita (2026b) held that the delegation boundary stands as long as legitimacy over value judgments remains institutionally attributed to humans — a formulation that leaves the attribution looking like convention. It is not. Institutions keep attributing judgment to humans because the standing is relationally and institutionally assigned, and second-personal competence is required to occupy it validly; the condition is backed by structure, and would have to be re-engineered, not merely re-decided, to move. Nor does the argument lean on the inner opacity of present systems, so it is robust to progress in interpretability: however legible a system's internals become, legibility yields evidence about capability, never standing. And nothing here forecloses the question whether some future system could acquire second-personal competence — any movement of the boundary would require both credible second-personal competence and a legitimate assignment of standing; what the argument forecloses is shortcutting that assignment by capability alone.

## 5. The two-layer prescription

The two-layer structure yields a two-layer prescription, and the layers — though pedagogically concurrent — must not be conflated. Layer one addresses everything the decomposition can place — it maps components, designs encounters, and configures AI so that delegation removes barriers without substituting for the learner. Layer two addresses what layer one cannot reach. For each prescription we state a principle and one worked example, and we say explicitly what is left to others (these residues are collected as a research agenda in Section 6); the restraint is not modesty for its own sake but the framework's own discipline — a paper about non-delegable judgment should not deliver judgments that belong to institutions.

### 5.1 Layer one: an analytic compass

*Principle.* The OECD's Learning Compass 2030 placed agency at the center of a framework for how learners navigate an uncertain world, but it is a compass that points a direction to travel, not one that resolves that direction into components an educator can read (OECD, 2019). This layer supplies a complement: an analytic compass that disaggregates the direction the OECD's compass indicates. Read a learner's components separately instead of guessing at aptitude as a single quantity. Direction, available activation, motivational drive, and mode are distinct analytic readings, and several have established instruments adjacent to them — self-regulated-learning measures speak to mode and its trainability (Zimmerman, 2000), engagement and vitality measures to available activation, interest inventories to candidate directions. The compass is a reading frame for existing instruments, organized by the delegability sort rather than summed; the reliability and validity of this mapping require separate construct-validation research. One reservation is constitutive rather than cautionary: the compass reads only what can be externalized. Answerability should not be represented as an individual trait score, and a compass that claimed to score it would re-import the conflation this paper identifies. Its institutional allocation and observable enactment can nevertheless be studied — who is entitled to ask, who is required to respond, who actually gives reasons; what remains inaccessible to direct measurement is sincere endorsement. This is the point at which both the OECD's compass of direction and this compass of components reach their limit. This is also the precise sense in which the present account accepts the demand that agency remain measurable rather than a residual aspiration (Cukurova, 2026) — and then locates, at that demand's edge, the standing itself; the competence to occupy it well is developed, second-personally, in layer two.

*Worked example.* A learner presents as "unmotivated." The compass disaggregates: available activation high — the same student is animated elsewhere; direction absent; mode predominantly critical. The reading is not a motivation deficit but a pre-crystallization state with a strong engine and no object, and the indicated lever is exposure to encounters, not exhortation. One further effect is rhetorical but consequential: the compass replaces *find your purpose* — a binary demand that mostly paralyzes — with *observe your own gradients*, an incremental practice a pre-crystallization learner can actually perform.

*Left to others.* Which instruments, with what weights, against which values: to each institution, whose reading of its own learners is itself a judgment someone must answer for.

### 5.2 Layer one: encounter engineering

*Principle.* If encounter can contribute to direction formation (Section 3), then curricula can be designed for encounter density: structured contact with problem-holders, early and embodied, before competence would conventionally "justify" it. Medicine has long operated a cognate design: clinical clerkship routes students through patients on the premise that direction toward care is formed at the bedside rather than installed in the lecture hall — a premise institutionalized by practice, not causally verified in this article's terms. The model can serve as a design heuristic wherever curricula can create sustained contact with problem-holders.

*Worked example.* For disciplines without wards, the encounter can be miniaturized into what we call a discomfort inventory exercise: the learner delegates a task wholly to an AI system, then inventories every discomfort with the output. The inventory is the learner's first specification profile — the felt difference between fluent output and right output is exactly where tacit commitment surfaces, following the ablation logic documented in Tomita (2026a). The exercise turns the AI's weakness-without-specification into a mirror, and a sequence of such micro-encounters into a curriculum. Independent evidence is consistent with the design: studying EFL learners revising AI-drafted statements of purpose, Jiang et al. (2026) found revision patterns ranging from compliance-oriented acceptance through form-oriented modification to content-oriented innovation — a gradient this article reinterprets as degrees of crystallized direction, a reading the authors themselves do not make — with two factors dividing them: the felt gap between an authentic and a GenAI-constructed voice, and enthusiasm to present one's intentions. Those two map onto components this article decomposed independently — what this article tentatively reads as a precursor of answerable practice (a judgment one will have to own), and the motivational drive of a direction one has taken up — surfacing as empirical dividing factors in a study that did not set out to test the decomposition. Where Jiang et al. document the gradient and prescribe that learners "remain the agents," the present account provides a design conjecture for what their study observed after the fact: the discomfort inventory is designed to elicit conditions hypothesized to support movement along that gradient; the proposition remains untested.

*An ethical boundary.* Encounter engineering must not instrumentalize the people encountered. Problem-holders are not teaching materials: consent, reciprocity of benefit, protection from repeated emotional labor, and structured reflection are design requirements, not optional refinements.

*Left to others.* Which problem-holders, at which sites, with what safeguards: discipline-specific terrain, owned by those who know it. The design guarantees exposure, never crystallization, and an honest program says so.

### 5.3 Layer one: AI guardrails

*A prior distinction.* Performance delegation and developmental delegation are different objects: offloading production can raise artifact quality while leaving knowledge and transfer unchanged (Fan et al., 2025). What guardrails protect, therefore, is not the artifact but the episodes in which the learner answers for judgments. *Principle.* Configure educational AI to distinguish two requests that look alike. When a prompt carries the learner's specification — their constraints, judgments, reasons — completion may primarily reduce externalization cost; whether it is educationally legitimate still depends on the learning objective, the learner's developmental stage, the plan for fading support, and the criterion for unaided transfer. When the prompt is specification-empty, completion would substitute for the very thing education exists to develop; the right behavior is to route the request back into dialogue until the learner's own commitments appear, and only then to draft.

*Worked example.* An essay assistant receives "write my essay on X." Instead of producing text, it asks what the learner finds wrong with the standard view of X, which two sources they would trust and why, and what conclusion they would defend if pressed — and drafts only from the answers. The same model, the same capability, a different default.

*Left to others — with two stated limits.* Detection of specification can be gamed; a determined learner can launder emptiness through borrowed opinions, so the guardrail shapes the default path rather than guaranteeing the outcome. And dialogue with an AI, however well configured, does not cultivate answerability — the system can elicit commitments, but it cannot be the one to whom the learner answers. Guardrails serve layer one. They do not substitute for layer two.

### 5.4 Layer two: the second person

*Principle.* The standing of answerability is conferred by the relation itself; what grows is the learner's competence to answer well, and that competence, however rehearsed, is normatively tested and sustained only in second-personal exchange: being questioned, answering, and owning the answer. The educator's irreplaceable function — the one no configuration of tools absorbs — is to be the other person: to ask the learner *what is your assessment?* and to hold them to what they say. AI can help learners rehearse this competence — drafting reasons, anticipating objections, simulating questions — and can mediate the exchange; what it cannot occupy is the position of final addressee, the person to whom the answer is owed. And the entitlement to ask is not innocent of power: a relation in which only the learner answers degenerates into interrogation. The educator who asks must also be answerable — for the questions posed, the criteria applied, and the decisions taken on the learner's work. Nor does answering privilege one performance format: reasons can be given in writing, multimodally, or with preparation, so that the standing to answer is not confounded with rapid oral fluency in a particular language or neurotype. Clinical supervision often exemplifies this structure: once responsibility for a patient-facing judgment is institutionally assigned, the trainee stands answerable for it; what training builds is the competence to answer well, and it builds it by making the trainee answer, case after case, to someone entitled to ask. The structure generalizes beyond medicine: a learner's standing does not wait for graduation — from the moment work is submitted under their own name, the answer is theirs — and what education builds is not the standing but the competence to occupy it. Assessment forms that stage this exchange — oral defense of one's own work, process accounts the learner must stand behind — are implications worth one sentence each here and a literature of their own elsewhere.

The prescription is structurally grounded, not nostalgic. When AI accelerates the externalization and combination of knowledge, the rate-limiting processes shift to socialization and internalization (Nonaka & Takeuchi, 1995; Tomita, 2026b) — and socialization, where evaluative commitments are contested and revised between persons, is precisely the second-personal site. The relational conditions that self-determination theory found necessary for internalization point the same way (Ryan & Deci, 2000). Nor is this a retreat from human–AI configurations: the hybrid is the right vessel, and layer one fills it. But within any configuration, the answerable party is the human in it, not the configuration — layers that mesh, not a fusion that answers. What layer two restores is older than the lecture hall: apprenticeship's core, with its drudgery finally delegable, returned to the center.

*Left to others.* Teacher development and assessment regimes that institutionalize the exchange: stated here as implications, designed by those who will answer for them.

## 6. Boundary conditions and research agenda

What this article leaves to others is collected here as testable commitments rather than scattered disclaimers. The encounter–crystallization–conversion model is a design conjecture, and the two-layer structure yields propositions that could falsify or refine it. **P1.** AI drafting support may improve assisted artifact quality without comparable gains in unaided knowledge or transfer (cf. Fan et al., 2025); whether adding structured answerability episodes improves subsequent transfer is a separate moderation hypothesis to be tested. **P2.** Encounter-rich curricula will produce stronger observable indicators compatible with endorsed direction — voluntary re-engagement, persistence across changes in supervision, reasoned defense across contexts — than information-rich curricula of equivalent coverage; no single indicator is treated as proof of sincere endorsement. **P3.** Enacted answerability episodes — rather than formal allocation alone — will predict deeper revision, error correction, and justification, after controlling for time-on-task and prior attainment. **P4.** The allocation and enactment of answerability are observable through questioning episodes, reason-giving, revision records, and decision ownership; divergence between recorded and enacted answerability is an analytic indicator, and sincere endorsement is not directly inferable from compliance. The decomposition also reads excess without treating activity level as a diagnosis. In occupational research, work engagement and workaholism both present as high activity while differing in motivational quality (Schaufeli et al., 2006); used here as a boundary-case analogy, that contrast prompts two inquiries — whether available activation is being depleted by ill health or adverse circumstance even while the direction remains endorsed, and whether the direction anchoring the activity is endorsed at all or compulsively held. "Just stop" is no more a component-level intervention than "just start": instruction alone neither restores available activation nor resolves what anchors the direction; and because sincere endorsement cannot be inferred from activity level, slowing a learner down remains a relational act — performed by someone entitled to ask, who in turn owes the learner reasons for the stop. Boundary conditions equally belong here: the framework is developed for formal education with identifiable educators. Its extension to informal, massive, or fully automated settings, the accessibility of reason-giving formats across languages and neurotypes, and the ethics of encounter designs involving real problem-holders are left open — as a research agenda rather than a residue.

## 7. Conclusion

What remains for the learner when AI can do the work? The question dissolves once agency is decomposed along the axis the question itself supplies. Many functions gathered under agency may be supported or partially offloaded when the design preserves development, transfer, error detection, and independent judgment — the sort in Section 2 says where, and layer one of the prescription says how. What cannot be handed over is of two kinds, and keeping them distinct is this article's central discipline: direction, a component whose endorsement cannot be substituted and may be supported by encounter; and answerability, not a component at all but the standing in which a learner answers to someone for a judgment. AI changes the economics of everything around that relation, stripping the externalization burden from teaching and learning alike; what it does not change is the relation itself: who must answer, and to whom. The educator's position is thereby clarified, not diminished: design the encounters, configure the tools, read the compass; and then ensure that the learner remains answerable to a legitimate human addressee — and, often, be that person. Education in the age of AI is not the defense of human tasks against automation. It is the cultivation of what was never a task.

## Practitioner Notes

**What is already known about this topic**
- Generative AI systems now plan, draft, and revise, making learner agency a central contested concept in educational technology.
- Distribution accounts treat agency as a property of human–AI systems; psychological accounts treat it as an individual capacity to be fostered. The two run in parallel.

**What this paper adds**
- A decomposition of learner agency by delegability — direction, two forms of drive, and mode — rather than by psychological function.
- A conjectured sequence of direction formation: embodied encounter may support the crystallization of commitment and the anchoring of available activation as motivational drive.
- Answerability identified as a relation isolated, not contained, by the decomposition: the non-delegable standing to have to answer for a judgment.
- A two-layer educational prescription matching the two layers.

**Implications for practice and/or policy**
- Read a learner's components separately, as an analytic map rather than a high-stakes diagnostic classification, instead of guessing at aptitude as a single quantity.
- Include ethically designed encounters with consequential problems and affected persons rather than relying on exhortation alone.
- Configure educational AI to route specification-empty requests back into dialogue rather than completing them.
- Protect second-personal exchange — being questioned, answering, owning the answer — as the site where answerability is enacted and answer-giving competence develops. (Answerability here means that learners must remain able to say why a judgment is theirs when questioned by another person.)

## Statements

**Conflict of Interest.** The author declares no competing interests.

**Data Availability.** This is a theoretical article. No datasets were generated or analyzed. All sources discussed are publicly available and cited in the references.

**Generative AI Use.** The author used generative AI tools (large language models) as drafting and editing aids during manuscript preparation, and as an object of analysis discussed in the text. All conceptual claims, the framework, the argument, and final wording are the author's own; the author takes full responsibility for the content.

**Funding.** None

## References

Anthropic. (2026, April 20). *Meet the winners of our Built with Opus 4.6 Claude Code hackathon* [Blog post]. https://claude.com/blog/meet-the-winners-of-our-built-with-opus-4-6-claude-code-hackathon

Archer, K., & Wiltsche, H. (2026). *The origins of artificial intelligence in natural intelligence* [Preprint]. PhilArchive. https://philarchive.org/rec/ARCTOO-2

Bandura, A. (2001). Social cognitive theory: An agentic perspective. *Annual Review of Psychology, 52*, 1–26. https://doi.org/10.1146/annurev.psych.52.1.1

Cathcart, S., Priestley, M., Priestley, A., & Rushton, E. A. C. (2026). Unravelling agency: A critical review of conceptualisations of agency for educational research, policy and practice. *Review of Education, 14*(1), e70131. https://doi.org/10.1002/rev3.70131

Cukurova, M. (2026). Agency as a system property in human–AI interaction in education. *British Journal of Educational Technology, 57*(4), 1065–1070. https://doi.org/10.1111/bjet.70060

Darwall, S. (2006). *The second-person standpoint: Morality, respect, and accountability*. Harvard University Press.

Dung, L. (2025). Understanding artificial agency. *The Philosophical Quarterly, 75*(2), 450–472. https://doi.org/10.1093/pq/pqae010

Emirbayer, M., & Mische, A. (1998). What is agency? *American Journal of Sociology, 103*(4), 962–1023. https://doi.org/10.1086/231294

Epley, N., Waytz, A., & Cacioppo, J. T. (2007). On seeing human: A three-factor theory of anthropomorphism. *Psychological Review, 114*(4), 864–886. https://doi.org/10.1037/0033-295X.114.4.864

Ewald, H. R. (1993). Waiting for answerability: Bakhtin and composition studies. *College Composition and Communication, 44*(3), 331–348. https://doi.org/10.2307/358987

Fan, Y., Tang, L., Le, H., Shen, K., Tan, S., Zhao, Y., Shen, Y., Li, X., & Gašević, D. (2025). Beware of metacognitive laziness: Effects of generative artificial intelligence on learning motivation, processes, and performance. *British Journal of Educational Technology, 56*(2), 489–530. https://doi.org/10.1111/bjet.13544

Giesinger, J. (2012). Respect in education. *Journal of Philosophy of Education, 46*(1), 100–112. https://doi.org/10.1111/j.1467-9752.2011.00836.x

Gray, H. M., Gray, K., & Wegner, D. M. (2007). Dimensions of mind perception. *Science, 315*(5812), 619. https://doi.org/10.1126/science.1134475

Hidi, S., & Renninger, K. A. (2006). The four-phase model of interest development. *Educational Psychologist, 41*(2), 111–127. https://doi.org/10.1207/s15326985ep4102_4

Jiang, Y., Wu, Q., Yang, Y., Jian, C., & Zhao, J. (2026). Learner agency in revising GenAI-generated statements of purpose. *British Journal of Educational Technology, 57*(4), 965–983. https://doi.org/10.1111/bjet.70041

Järvelä, S., & Hadwin, A. F. (2013). New frontiers: Regulating learning in CSCL. *Educational Psychologist, 48*(1), 25–39. https://doi.org/10.1080/00461520.2012.748006

Kortemeyer, G., Dittmann-Domenichini, N., Schlienger, C., Spilling, E., Yaroshchuk, A., & Dissertori, G. (2023). Attending lectures in person, hybrid or online—How do students choose, and what about the outcome? *International Journal of Educational Technology in Higher Education, 20*(1), 19. https://doi.org/10.1186/s41239-023-00387-5

Luo, J. (2025). How does GenAI affect trust in teacher–student relationships? Insights from students' assessment experiences. *Teaching in Higher Education, 30*(4), 991–1006. https://doi.org/10.1080/13562517.2024.2341005

Nonaka, I., & Takeuchi, H. (1995). *The knowledge-creating company: How Japanese companies create the dynamics of innovation*. Oxford University Press.

OECD. (2019). *OECD learning compass 2030: A conceptual learning framework* [Concept note]. OECD. https://www.oecd.org/content/dam/oecd/en/about/projects/edu/education-2040/concept-notes/OECD_Learning_Compass_2030_concept_note.pdf

Ryan, R. M., & Deci, E. L. (2000). Self-determination theory and the facilitation of intrinsic motivation, social development, and well-being. *American Psychologist, 55*(1), 68–78. https://doi.org/10.1037/0003-066X.55.1.68

Scardamalia, M. (2002). Collective cognitive responsibility for the advancement of knowledge. In B. Smith (Ed.), *Liberal education in a knowledge society* (pp. 67–98). Open Court.

Schaufeli, W. B., Taris, T. W., & Bakker, A. B. (2006). Dr Jekyll or Mr Hyde? On the differences between work engagement and workaholism. In R. J. Burke (Ed.), *Research companion to working time and work addiction* (pp. 193–217). Edward Elgar.

Tomita, K. (2026a). *Domain-native development: A Mekiki framework for AI-assisted knowledge work* [Preprint]. SocArXiv. https://doi.org/10.31235/osf.io/cwkav_v1

Tomita, K. (2026b). *Philosophy as cognitive assay: Measuring the delegation legitimacy boundary in AI-assisted knowledge work* [Preprint]. SocArXiv. https://doi.org/10.31235/osf.io/e9qw5_v2

Xing, W., Kim, T., Song, Y., Li, H., Li, C., & Kim, J. (2026). Unveiling interaction patterns between students and a generative AI teachable agent: Focusing on students' agency and AI agents' authority. *British Journal of Educational Technology, 57*(4), 896–923. https://doi.org/10.1111/bjet.70038

Zimmerman, B. J. (2002). Becoming a self-regulated learner: An overview. *Theory Into Practice, 41*(2), 64–70. https://doi.org/10.1207/s15430421tip4102_2

Zimmerman, B. J. (2000). Attaining self-regulation: A social cognitive perspective. In M. Boekaerts, P. R. Pintrich, & M. Zeidner (Eds.), *Handbook of self-regulation* (pp. 13–39). Academic Press. https://doi.org/10.1016/B978-012109890-2/50031-7

---

# Paper T4 — 組織における「自分ごと化」のアドヒアランス的再記述：知識労働がAIで加速された時に組織に求められるもの

*(An Adherence-Based Redescription of "Jibungoto-ka" (Treating Matters as One's Own) in Organizations: What AI-Accelerated Knowledge Work Requires of Organizations)*

**Preprint version:** 1  
**Canonical DOI:** https://doi.org/10.31235/osf.io/495wg_v1

**Kengo Tomita**
Institute of Technology, Shimizu Corporation

**Language note:** This paper is written in Japanese. An English abstract is included at the end of this section, following the original paper's structure. Contemporary AI systems read the Japanese full text directly; the English abstract provides orientation.

---

清水建設株式会社　技術研究所　冨田賢吾

**要旨**

日本の組織では「自分ごと化」が領域を問わず要請されるが，概念は未成熟で，失敗に共通するのは，なぜやるのかを渡す説明言語の不在である。医療は同型の問題を，指示への服従（コンプライアンス）から意味を理解した主体的参加（アドヒアランス）への転換として先に経験し，服薬指導はその実装の一つだった。本稿はこの構造を組織へ転用する。自分ごと化を，引き受け（目的の内的承認を，特定の他者へ理由を示す関係の中で保持すること）と身体化（実践への浸透）の複合として再定義する。引き受けの関係的な核は，移転不能な応答可能性（answerability）であり，相互性を要求する。問う側も答える立場に立たなければ，引き受けの場は成立しない。医療と組織の非対称は分野でなく遭遇への接続経路に由来する。ここから，意図を伝達して従業員が引き受ける順方向と，従業員由来の向きを正式な検討の回路に入れ，組織側が採択・保留・停止の理由を返す逆方向からなる二経路モデルを導く。慢性的な失敗は，順方向のみを押し逆方向を欠く帰結である。生成AIが知識の外化と結合を加速するほど，引き受けと身体化は律速段階になる。処方を，遭遇を含む発現条件の設計・停止判断への説明責任・先行指標の観測として与える。

**キーワード**: 自分ごと化，アドヒアランス，応答可能性（answerability），生成AI，組織変革

---

### 1. 問題の所在

#### 1.1 「自分ごと化」という未成熟な要請

日本の組織では，「自分ごと化」という言葉が領域を問わず要請される。防災では住民に水害のリスクを自分の問題として捉えさせる文脈で[^b1]，地方自治体の計画では持続可能性の目標を住民が自分のこととして引き受ける文脈で[^b2]，安全管理では現場が規則を自分のものとして守る文脈で[^b3]，そして組織変革やAI導入の場面でも，従業員に主体的な参加を求める言葉として使われる。心理的な所有や当事者意識の研究もこの語の周辺に積み重なってきた[^b4][^b5]。ただしこれらが測るのは所有の感覚や意識という状態であり，本稿が後に定義する引き受けの関係的な側，すなわち特定の他者に理由を示す立場とは，測る対象が異なる。隣接する分野の蓄積もある。自己決定理論は，外から与えられた目標が自律的な動機へ内在化する条件を扱い[^b25]，発言と沈黙の研究は，提案や懸念が上位へ届くか塞がれるかの条件を扱ってきた[^b26][^b27]。しかしいずれも，目的を自らの判断理由として承認することと，特定の他者に答える立場と，実践への身体化と，従業員に由来する向きへ組織が理由を返す経路とを，同時には扱っていない。少なくとも，これら四つの要素を同時に位置づけ，測定と介入へ接続する統合的な枠組みは，十分な形では示されていない。表記すら「自分ごと化」「自分事化」「自分ゴト化」と揺れていること自体が，概念の未成熟を映している。要請は強いが，要請される当のものが何であるかは，はっきりしていない。

#### 1.2 医療が一度通過した同型の問題

ここで本稿が手がかりとするのは，医療が一度通過した転換である。医療は1990年代以降，指示への受動的な服従（コンプライアンス）から，意味を理解した主体的な参加（アドヒアランス）への概念の転換を進め，2003年の世界保健機関の報告で国際的に定式化した[^b6]。そしてその転換を支えた実装の一つが，服薬指導という説明の実務だった。なぜこの治療が必要かを説明し，理解を経て，主体的な行動につなげる手続きである。組織の「自分ごと化」は，これと同型の転換を暗黙のうちに求めている。従業員に，指示への服従ではなく，意味を理解した主体的な参加を期待している。だが組織では，服薬指導に相当する説明，すなわち，なぜそれをやるのかを構造として渡す言語が，十分な形では体系化・実装されていない。施策の手元にある道具は，多くの場合，決まった方針を一方向に知らせる周知までである。周知に閉じた施策は，転換前の側，すなわち服従を求めるコンプライアンスの道具立てにとどまる。

#### 1.3 説明言語の不在という横断的な構造

説明言語の不在が浸透を妨げるという構造は，個別の領域でそれぞれに指摘されてきた。手続きの公正に関する研究は，説明の量と内容，そしてその伝え方が，人々の公正の感覚と判断の受け入れに影響することを示している[^b8]。安全文化の領域でも，取り組みへの認識や納得感を測り可視化することが政策の事業で進められているが，その方法論はなお整備の途上にある[^b9]。領域はばらばらだが，指摘の形は共通している：なぜやるのかの説明言語が体系化されていないから浸透しない。なお本稿でいう説明言語の不在とは，個々の説明が皆無であることではなく，なぜやるのかを構造として渡す言語が，組織の制度として十分に体系化・実装されていないことを指す。本稿は，この横断的に現れる空白を，一つの枠組みで埋めることを試みる。

#### 1.4 なぜ今この再記述が必要か

自分ごと化の難しさは，昔からあった。ではなぜ今，この再記述が必要なのか。理由は生成AIにある。知識の変換には，外に出す（外化），組み合わせる（結合），人と人のあいだで分かち合う（社会化），個人の身体に染み込ませる（内面化）という四つの過程がある[^b10]。生成AIが直接加速するのは外化と結合である。社会化と内面化は，人間の関係と実践と身体への依存が大きく，同じ仕方では代替も短縮もされにくい。外化と結合が速くなるほど，律速段階（全体の速さを決める最も遅い段階）は，社会化と内面化の側に移る。本稿の語彙でいえば，引き受けと身体化を回せない組織が，まさにその段階で詰まるようになる。アドヒアランスの不良は以前から組織にあったが，AIの時代には，それが組織の速さを決める律速段階として前面に出てくる。これが，古い問題に今あらためて言語を与える理由である。

#### 1.5 本稿の貢献

本稿の貢献は五つである。第一に，分散していた「自分ごと化」の点的な研究を統合する概念枠組みを，医療アドヒアランスの転用として提供する。第二に，自分ごと化を引き受けと身体化の複合として再定義し，引き受けの関係的な核に応答可能性（answerability）を置く。第三に，応答可能性が組織で成立する条件として相互性（問う側が自らも答える立場に立つこと）を特定する。第四に，医療と組織を分かつ非対称が，分野に固有なのではなく遭遇の経路に由来することを示し，組織アドヒアランス（本稿の枠組みに写した自分ごと化の成立過程）の二経路モデルを提示する。第五に，そこから遭遇を含む発現条件の設計・停止判断への説明責任・先行指標による観測という運用原則を導く。

### 2. 概念枠組み：アドヒアランスと引き受けの構造

#### 2.1 医療アドヒアランスの核心：正統性の所在

医療において「コンプライアンス」から「アドヒアランス」への転換が指してきたのは，患者がどれだけ忠実に従うかという服従の度合いの問題ではない。転換の核心は，正統性の所在が動いたことにある。コンプライアンスの語が前提していたのは，何が正しい治療かを決める権限が医師の側にあり，患者はその指示に従う，という配置だった。アドヒアランスはこれを，患者と医療者の合意に正統性を置く配置へと置き換えた。世界保健機関の定義が「合意した推奨に対する行動の一致」と述べるとき，鍵となるのは一致の前にある合意であって，一致の率ではない[^b6]。患者が治療の意味を理解し，自らの判断としてそれに参加すること。ここが転換の中身である。

この転換を精神論でなく実務として支えた実装の一つが，服薬指導という説明の実務だった。服薬指導では，なぜこの薬がこの身体に効くのかという機序，飲まなければどうなるかというリスク，そして飲めばどう変わるかという効果が説明される。これらに共通するのは，いずれも「従え」という命令ではなく「なぜ」を渡す行為だという点である。そして，説明だけでは本人にしか行えない服薬の実行を確保しにくい局面では，医療は直接服薬確認療法（DOTS）のような設計を用いてきた。DOTSの設計からは，三つの特徴を抽象できる。代理が不可能であること，服薬を直接その場で確認すること，単一の介入でなく複数の要素を束ねることである。この三分は世界保健機関の公式の整理ではなく，組織への転用のために本稿が行う抽象化である。これらは後の議論で使う。

あらかじめ転用の範囲を限定しておく。本稿が組織へ移すのは，医療アドヒアランスの全体ではなく，三つの構造，すなわち正統性の所在の移動，なぜを渡す説明の実装，代理不可の過程を守る設計である。患者と従業員では，利害の切実さも，関係を規定する契約も，拒否の自由も同じではない。同型なのは転換の構造であって，当事者の置かれた条件ではない。この差そのものは4.1節と4.2節で正面から扱う。もう一つ限定しておく。本稿が医療を先行例として引くのは，アドヒアランスの達成度においてではない。服薬の不遵守は医療でも今なお解決されない問題であり続けており，説明や情報の提供だけでは服薬の行動が動かないことも実証的に示されている[^b11]。医療が先行しているのは，問題の捉え方を服従から合意へ転換し，それを測る尺度[^b7]と，影響する要因の分析と，介入の検証という研究の回路を先に整えた点にある。本稿が輸入するのは，この転換と回路の側である。

#### 2.2 Mekikiによる翻訳：二つの区別の輸入

医療のアドヒアランス論を組織に持ち込もうとする試みは従来も散発的にあったが，共通の語彙がなかったために，類比は表面的な比喩にとどまってきた。本稿は翻訳層として，Mekikiフレームワーク[^b12]とその測定軸[^b13]から二つの区別を輸入する。

第一は，専門性の基質（specification）と，それを出力に変換する障壁との分離である。ある仕事をこなすには，その分野固有の判断の蓄積（どの手順をどの状況で適用するかを決めるもの）が要る。これが基質であり，文書化された手順そのものではなく，手順をどう使うかを定める当人の判断の側にある。基質を実際の成果物に変えるときには別の障壁がかかる。情報に到達する障壁，それを構造として理解する障壁，そして実践に染み込ませる障壁である。生成AIが劇的に下げたのは主にこの変換側の障壁であって，基質そのものではない[^b12]。第二は，事実認識（Sein）と価値判断（Sollen）の分離である。何がそうであるかの記述と，何をなすべきかの判断は，論理的に別の層にあり，前者から後者は導けない。AIが事実記述で人間を上回ることと，価値判断が人間の側に残ることは，別の問題である[^b13]。

この語彙を使うと，服薬指導が何をしていたのかを構造として書き直せる。機序の説明は，治療という行為の背後にある基質を患者に渡す行為であり，リスクと効果の説明は，飲む・飲まないという判断が患者自身のSollenに関わることを示す行為である。服薬指導とは，基質と判断の所在を言語化して患者に手渡す説明にほかならない。組織における「なぜこの業務が必要か」の説明は，これと同じ構造を持ちうる。持ちうるが，現状ではその説明の言語が，組織の側で十分な形には体系化されていない。

#### 2.3 中核命題：自分ごと化とは何か

ここで本稿の中核命題を述べる。自分ごと化とは，経営の意図を知っている状態でも，それに従っている状態でもない。それは，引き受けと身体化の複合である。

引き受けの内的な側とは，外から降りてきた意図を，自らの価値判断（Sollen），すなわち自らの判断理由として承認することである。本稿では，この価値判断の方向を向きと呼ぶ。経営層が「なぜこの目標か」を伝えたとき，それを聞いて理解した段階では，従業員はまだ「経営層のSollenを知っている」状態にとどまる。それを自分のSollenとして承認したとき，まず内的な更新が起きる。重要なのは，意図の出所と引き受けが別の事柄だという点である。たとえ与えられた目標であっても，引き受ければ，それについて答えるのは自分になる。由来が外にあることと，引き受けによって自分が答える立場になることは，無関係である。身体化とは，その引き受けた向きが実践に染み込み，手順を実行する身体に定着することである。これは説明を聞くことでは起こらず，本人が実際にやることでしか起こらない。前節でいえば，変換障壁のうち最も内側の，実践に染み込ませる障壁を本人が越える過程に当たり，1.4節の語でいえば内面化に相当する。

引き受けと身体化は，どちらか一方では自分ごと化にならない。向きを引き受けても身体が動かなければ言葉だけに終わり，身体が動いても向きを引き受けていなければ言われたから動いているだけになる。両方がそろったとき，経営の意図は従業員の振る舞いの中で生きはじめる。

#### 2.4 引き受けの核：応答可能性（answerability）

引き受けの中心には，能力とは独立の，ある関係が座っている。ある判断について，それを問う資格のある他者に答えねばならない立場，応答可能性（answerability）である。これは判断する人の能力の高低ではなく，その判断について誰が答えるのかという関係の事実であり，能力のように他者へ移すことができない。

この移転不能性は，契約という身近な制度を二層に分けるとよく見える。契約の中身（何を果たすか，違反すればどうなるか）と，その履行について説明する義務は，制度として定められ，第三者が保証し，必要なら別の主体に割り当て直すことができる。この制度の層を，本稿では説明責任（accountability）と呼ぶ。一方，その契約を結び，引き受けるという行為そのものは，本人にしか行えない。引き受けた以上その判断について答えるのは本人であって，これを応答可能性（answerability）と呼ぶ。AIや第三者に委ねられるのは作業と記録の側であり，説明責任は制度上指定された主体に残るか再配賦される。応答可能性は，引き受けた本人から移転できない。本稿が自分ごと化の核に置くのは，この後者，つまり移転できない引き受けの立場である[^n1]。ここで，2.3節で述べた内的な更新（意図を自らの価値判断として承認すること）と，この応答可能性の関係を明確にしておく。両者は分析上区別される。前者は，目的を自らの判断理由として承認する内的な側である。後者は，その判断について特定の他者に理由を示す関係的な立場である。本稿でいう引き受けとは，前者が後者の関係の中で保持されている状態を指す。更新を欠いたまま応答の義務だけがある状態は5.1節で扱う形骸化の入口であり，答える相手を欠いたままの更新は，私的な決意にとどまる。どちらか一方だけでは，組織における引き受けは成立しない。

この立場は，問う資格のある特定の他者へ向かうという意味で二人称的だが，さらに相互的な構造を要求する。Darwallの第二人称的観点[^b14]に基づいて松本[^b15]が論じるように，問う側が相手を対等な判断の主体として遇し，自らも答える側に立つのでなければ，そのかかわりはもはや二人称的ではない。相手にだけ応答を求め，自らは応答しない態度は，関係の形を借りた一方的な要求にすぎない。応答可能性の立つ場は，相互性の上にしか成立しない。組織で引き受けが成り立つ条件を，本稿はここに置く。経営が従業員に引き受けを求めるなら，経営の側もまた，従業員の判断に答える立場へ立たねばならない。この相互性が組織の設計に何を課すかは，第4節と第5節で展開する。

医療と組織の対応を，ここまでの語彙で表1に整理する。

**表1　医療アドヒアランスと組織の「自分ごと化」の対応**

| 観点               | 医療アドヒアランス                                           | 組織の「自分ごと化」                                         |
| ------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 転換前の様式       | コンプライアンス（指示への服従。正統性は医師の側）           | 浸透施策・指示の徹底（正統性は経営の側）                     |
| 転換後の様式       | アドヒアランス（合意にもとづく主体的参加）                   | 引き受け×身体化（本稿の再定義）                              |
| 目的の所在         | 診療開始時点で内在化しやすい（治りたい）                     | 自動的には内在化しない（階層上位から降りる）                 |
| 説明の実装         | 服薬指導（機序・リスク・効果の説明）                         | 説明言語の不在（本稿が供給する対象）                         |
| 代理不可の設計     | DOTS（直接服薬確認）                                         | 手動測定・ピッチなど（身体化の経路として意図化しうる設計）   |
| 制度の層と関係の層 | 服薬・確認・説明義務の制度的配置（accountability）／治療の判断について答える立場（answerability） | 職務・契約・説明義務の制度的配置（accountability）／引き受けた判断について答える立場（answerability） |
| 相互性の条件       | 医師と患者が互いに説明し受け止め合う関係（服薬指導はその実装） | リーダーと従業員が互いに答える立場に立つこと（欠けたときの失敗＝自惚れ・形骸化） |
| 失敗様式           | 病識なき中断・形だけの服薬                                   | 忠誠の信号合戦・形骸化                                       |

*注：表中では制度の層と関係の層を一行にまとめたが，この区別は他の観点と同列の一項目ではなく，表の全体を貫く分析の軸である。応答可能性は引き受けの関係的で移転不能な核にあたり，残りの観点はその成立の条件と現れを整理している。*

### 3. 事例分析

ここまでの枠組みを，一つの事例に当てて深く読む。目的は事例の列挙ではなく，現象を本稿の語彙へ写す手順を示すことにある。検証の経路は第5節の先行指標（表2）が開き，本節が担うのは適用の実演である。なお本例が示すのは，定義の構成要素のうち主に身体化の側であり，引き受けと二経路モデルの全体を実証するものではない。

**事例：アンモニア検知管の手動測定**

筆者が関わった案件である。ある現場で，アンモニア濃度を週に一度，手動の検知管で測る作業を，若い係員に依頼した。当初の目的はデータの収集であり，事実（Sein）の取得にすぎなかった。ところが意図しない副産物が生じた。検知管の色の変化を読み，数値に直し，それを現場の感覚と結びつける。この一連を繰り返すうちに，色と数値と体感の対応が，係員の身体に定着していった。後に工事長が，この作業に教育的な効果があったことを事後に認識した。

これをアドヒアランスの語彙で読むと，こうなる。仮にこの測定を自動センサーに置き換えていたら，データは同じように得られたが，同じ感覚的・身体的な学習は生じにくかった可能性が高い。変換障壁のうち最も内側の，実践に染み込ませる障壁を意図せず残したことが，測定という行為そのものを基質の蓄積の経路に変えた。本稿の枠組みがあれば，これを設計の段階で意図できた。「この測定は，実は身体化を通じた専門性の蓄積が目的です」と説明し，あらかじめその向きの理由を示して，引き受けの前提を整えることができた。

この事例が示すのは，説明言語があれば効果を設計の段階で意図できたという点である。説明言語の不在は，効果が生じないことを意味しない。偶然に生じることはある。だがそれは，効果を再現可能な設計として組織が持てないことを意味する。そして，ここで示したのは事例の網羅ではなく，現象を本稿の語彙へ写す手順である。読者は自らの組織で対応する経験を想起できるはずであり，その経験にこの写像を反復することが，本稿の枠組みの使い方にほかならない[^n2]。

### 4. 考察：非対称の経路依存と二経路モデル

#### 4.1 なぜ医療で成立しやすく組織で難しいのか

前節の事例は，手動の測定の反復と身体的な習得が併存した過程と，説明言語があればその効果を設計段階で意図できたこととを示した。ではなぜ，医療ではアドヒアランスを支える説明と観測の回路が先に整い，組織ではそれが慢性的に欠けるのか。

第一の説明は，診療や職務が始まる時点での，目的の所在の差にある。医療では多くの場合，患者の中に「治りたい」という意図が既に内在化しており，医療者はそこに治療行動を接続する課題として扱える。これに対し企業では，目標は階層の上位から降りてくる。売上やシェアといった数値目標は，それ自体は事実（Sein）の装いをとるが，それを目指すべきだとする選択は価値判断（Sollen）であり，しかもその判断は経営層のものであって，従業員の中に対応する内在的な意図が自動的にあるわけではない。患者の「治りたい」に当たるものが，従業員の側に最初から備わっているとは限らない。自分ごと化が組織で難しいのは，根のところで，目的が外から降りてくるからである。

#### 4.2 非対称の正体は経路にある

しかしこの説明は，まだ医療を特別扱いしている。医療が特別なのは，医療という分野だからなのか。本稿はそうではないと考える。非対称はドメインに固有なのではなく，経路に固有である。

ただし4.1節が述べたのは，診療が始まる時点での配置であって，その目的がどこから来たかという前史ではない。形成の経路をたどれば，見え方は変わる。医療が「目的が内在する分野」に見えるのは，医療という営みの構造が，問題との身体的な遭遇へ，関与する双方を構造的に接続しているからである。患者は，自らの症状と生活の制約とに，身体ごと出会わされている。医師や薬剤師は，書類の上の抽象的な課題にではなく，目の前で苦しんでいる患者に，身体ごと出会わされる。この遭遇が，治療への向きの結晶化を，それぞれの当人の中に促す。つまり目的は最初から内在していたのではなく，遭遇を通じて内在化したのである。ここを取り違えると，組織にできることを見誤る。

人の自己目的は，無から湧くものではない。本稿は，その重要な形成経路の一つとして，身体化された経験からの結晶化を置く。この仮説は思弁にとどまらず，性質の異なる四つの観察源が同じ形に収束している。第一に，野中・竹内が組織的イノベーションの事例として集めた一群では，開発者のコミットメントは計画会議ではなく，顧客や現場の困りごとに直接触れる場で形成されている[^b10]。第二に，近年のAI支援開発コンペで公に記録された入賞者たちは，道具が登場するより前にコミットメントを持っていた実務家（住宅許可の停滞に向き合った弁護士，自分の子に向き合った技術者，診察後のケアに向き合った循環器医，道路への投資評価に向き合った実務家）であり，彼らにとってAIは変換障壁を取り除いただけで，向きがどこから来たかは変えなかった[^b16]。第三に，土木技術者の越境学習の研究では，国の研究所への派遣という組織の外に出る経験の中で，被災地の調査に加わり，同業者が災害対応で働く姿に直接触れたことが，自らの業種の使命の認識につながった過程が記録されている[^b17]。第四に，筆者の先行研究が扱ったAI支援開発の事例でも，現場の経験から形成された向きが，AIという道具を操舵した順序が記録されている[^b12]。四つは方法も対象も時代も共有しないが，遭遇が先にあり向きが後から結晶化するという順序の形を共有している。これらはこの機序の因果的な証明ではなく，仮説と整合する異質な観察である。なお，筆者は，教育の文脈を扱う別稿においても，遭遇から結晶化へ至る同型の構造を設計仮説として定式化している[^b28]。

帰結は，組織設計の作用点を変える。目的そのものを注入することはできない[^b25]。前節までに見たとおり，引き受けは説明や命令で強制できない。しかし，従業員が身体で何に出会うかは設計できる。組織にできるのは目的の注入ではなく，遭遇をはじめとする発現条件の設計である。なお，しばしば仕事の対極に置かれる趣味は，この観点からは敵ではない。それは未だ社内の課題に接続されていない自己目的的なエネルギーの蓄えであり，問題は趣味の存在ではなく，そのエネルギーを走らせる経路が組織の課題に向けて開かれていないことの側にある。

#### 4.3 組織アドヒアランスの二経路モデル

遭遇が向きの結晶化を促しうるという仮説を組織の側から見ると，アドヒアランスには方向の異なる二つの経路があることがわかる。

経路1は順方向である。経営層が意図（なぜこの目標か）を伝達し，従業員がそれを引き受ける。これは2.3節で述べた自分ごと化の標準的な像であり，多くの浸透施策が暗黙に想定している経路でもある。だがこの経路は，目的が従業員に内在しないという4.1節の事情のために，構造的に難しい。経路2は逆方向である。従業員が遭遇から結晶化させた向きを，正式な検討の回路に入れ，権限を持つ特定の主体が，採択・保留・停止のいずれについても理由を返す。組織がここで必ず引き受けるのは，向きそのものではなく，その向きをどう扱うかという自らの判断である。採択されたものについては，組織はその向きを自らの目的として引き受け，資源を配し，社会的な需要との整合を図る。なお，ここで組織が引き受ける，組織が答えると言うとき，それは抽象的な法人が答えるという意味ではなく，制度上指定された特定の役職者や意思決定の場が答えることを指す。この向きは，経路2の検討の回路に入る時点では，すでに当人に内在している（遭遇から結晶化したのだから）ため，経路1が抱える内在化の困難を，構造的に回避できる。ただし経路2は万能の迂回路ではない。結晶化した向きが社会の需要と整合するか，資源を配してよいか，止めるなら誰が答えるかという，経路2に固有の設計課題が残る。この設計は第5節で扱う。

この二経路モデルは，自分ごと化施策がなぜ慢性的に失敗するのかを説明する。失敗する施策の多くは，経路1を強く押している。「もっと自分ごととして捉えよ」と繰り返し要請する。1.2節で述べた周知は，この型の施策が制度としてとる典型の形である。しかし実際の拘束条件は，経路2の不在の側にあることが多い。このうち，表出と応答の回路が塞がれる条件については，発言と沈黙の研究が蓄積してきた[^b26][^b27]。遭遇がそもそも設計されておらず，向きが結晶化する場がなく，結晶化しかけたものを止める阻害因子が残っている。押している経路と，詰まっている経路が違う。だから声を大きくしても通らない。

なお，経路2の起点となる遭遇は，組織の内部に限らない。3Mのポストイットの起源が，開発者が聖歌隊の活動で讃美歌集に挟んだ栞が落ちることに困った，という業務外の遭遇にあったことはよく知られている[^b10]。4.2節の末尾で触れた趣味と同じく，組織の外の遭遇から結晶化した向きもまた，経路2が正式な検討と応答の対象とする資源のうちにある。表2の結晶化の行が，提案の出所を業務の内外で区分するのは，この定義域を観測に写すためである。

この二経路の対は，2.4節で置いた相互性を，組織の規模に写したものでもある。経路1で組織は従業員に引き受けを求め，経路2で組織は従業員の結晶化した向きに応答し，採択の場合にはそれを引き受け返す。経路2を欠いたまま順方向だけを押す施策は，求めるが応答しないという一方的な関係の形をとる。これは，第5節で自惚れとして取り上げる歪みの，組織の規模での現れである。

この二経路には，先行する実装がある。野中らが描いたミドル・アップダウン・マネジメントは，トップの理想と現場の現実との矛盾を，中間管理職が解消していく型である[^b10]。本稿の語彙で読み直せば，ミドルは上位の意図を現場の言葉に翻訳して降ろし（経路1），現場で結晶化した向きを拾い上げて経営へ通す（経路2）。二つの経路を，役職という人が同時に媒介していたことになる。ただし役職による解は，優れたミドルという個人への依存を再び持ち込む。第5節で扱う運用原則は，この媒介を人から設計へ移す試みである。本稿は野中理論の置き換えを試みているのではない。その媒介の機能を二経路に分解し，設計と観測の語彙へ写すことを試みている。

そしてこの二経路は，人が担うことはあっても，明示的な設計の対象ではなかった。経験の豊富な管理者は，向きと勢い，遭遇，そして応答可能性といった本稿の主題を，名前を与えないまま経験知で暗黙のうちに回してきた。だがAIが外化と結合を吸収するほど，暗黙のまま回る余地は狭くなる。1.4節の律速段階の移動を管理の側から言い直せば，経験知だけで運営できていた構造が，意識して設計しなければ回らない対象に変わる，ということである。

さらにこの帰結は，組織の責任をめぐる古典的な診断と逆向きに交差する。多くの手の問題（the problem of many hands）[^b18][^b19]と責任の空隙（responsibility gap）[^b20]をめぐる議論は，組織とAIがともに判断の所在を拡散させる方向に働くと論じてきた。関与する手が増えるほど，また判断が機械へ移るほど，誰が答えるのかは見えにくくなる，という見立てである。本稿の枠組みは，逆向きの可能性を開く。事実認識（Sein）と価値判断（Sollen）の分解を明示した委譲[^b13]は，何を機械に渡し何を人が保持したかの線引きを，そのたびに記録するよう構造の上で要求する。この線引きが実際に引かれるかぎり，AIの導入はむしろ判断の所在を可視化する方向に働きうる。ただし，この逆転はAIの導入一般に成り立つ主張ではない。分解を明示しない導入は，古典的な診断のとおり所在を曖昧にするだろう。逆転が生じるのは，委譲の設計がこの明示を伴う場合に限られる。また，記録が形式に流れ，記録の上の応答者と実際の決定者が乖離する可能性も残る。可視化が実質を持つかどうかは，記録と運用の突き合わせで確かめるほかない。そしてこれは，枠組みからの帰結であると同時に，観測にかけるべき仮説である。表2の「判断所在の明示」の行は，この条件と帰結を観測可能な形で残すために置いてある。

#### 4.4 射程の限定とその反転

ここで一つ，重要な限定を置く。本稿が「自分ごと化の難しさ」と呼んできた問題は，普遍的なものではないかもしれない。職務の範囲を契約で事前に明文化する契約型の雇用（いわゆるジョブ型）は，範囲外の引き受けを明示的には求めない。範囲を超えた引き受けとしての自分ごと化は，この構造の中では要請として立ちにくい。契約という制度が，引き受けの範囲を区切ることで，意図の階層的な分裂を回避している。これに対し日本型の雇用は，職務の範囲が曖昧なまま（メンバーシップ型），範囲を超えた引き受けを要請する[^b21]。本稿の問題設定は，契約で範囲を区切らずに自分ごと化を求める，この日本型の構造において特に顕在化しやすいと考えられる。

ただし，この限定は逆向きにも読める。契約型が引き受けを回避できていたのは，職務を事前に明文化できていたからである。そして生成AIが吸収していくのは，まさにその明文化できる職務の部分である。契約に書ける仕事がAIに移っていくにつれ，契約で範囲を区切るという回避策そのものが効かなくなる。業務の中で，契約に書けない判断と引き受けの占める比重が高まっていく。とすれば，引き受けをどう扱うかという本稿の問題は，契約型の雇用にも，これから合流してくることになる。日本型の組織がこの問題を長く抱えてきた経験は，欠点であると同時に，これから多くの組織が直面する問題の先行指標でもある。この限定にはもう一つの側面がある。価値のある能力を明示的には育てず，仕事の副産物として期待するという同型の失敗は，教育や研究の場でも同時に表面化しつつある[^n3]。本稿の診断は，組織に閉じない可能性がある。

### 5. 失敗と成功の様式：形骸化と3M

引き受けには，対になる失敗の様式と成功の様式がある。順に見る。両者は別々の現象ではなく，引き受けという同じ過程が，条件によって反対の方向に転ぶ姿である。

#### 5.1 失敗の様式：形骸化と自惚れ

自分ごと化の要請が，ある条件下で逆機能に転じることがある。本稿はこれを，自分ごと化の形骸化と呼ぶ。引き受けの中身が抜け落ち，要請の形だけが回り続ける状態である。この形骸化を駆動するのは，判断を支える根拠を欠いたまま，価値判断だけが集団の中で強化されていくスパイラルであり，個体の水準で記述されてきた現象（根拠の伴わない確信が自己強化していく過程）の，集団版として本稿が拡張するものである[^b13]。

転じ方は典型的にこうである。自分ごと化が組織の中で疑ってはならない価値として扱われはじめると，「自分ごと化できていない」という指摘が，業務内容についての指摘ではなく，組織への忠誠度への攻撃として受け取られるようになる。すると人々は，内容の妥当性を競うのではなく，忠誠を表明する形式的な振る舞いを競うようになる。忠誠の信号合戦である。自分ごと化方針への合理的な批判は組織への裏切りと同一視され，価値判断の領域が議論の外に置かれる。これは神聖な価値が挑戦を受けたときに道徳的な怒りが起こり合理的な検討が止まる構造として知られているものに対応する[^b24]。そして批判が裏切りと見なされるために，批判は防衛を強め，防衛がさらに批判を呼ぶ循環に入り，学習が止まる。

ここで決定的なのは，2.4節で置いた区別である。形骸化した組織では，応答可能性の座に，忠誠の表明という代理物が収まっている。答える立場に本当に立つことと，立っているふりをすることが，外から見分けにくくなる。だからこそ，それが個人の能力ではなく関係の事実だという2.4節の規定が，この失敗を見抜く足場になる。

失敗の様式は，もう一つある。松本[^b15]が自惚れ（self-conceit）と呼ぶ態度，すなわち相手には答えることを要求しながら，自らは答える側に立たない関係の歪みである。リーダーが部下に自分ごと化を求めながら，部下の判断を対等な判断として受け止めないとき，2.4節で見た相互性が欠ける。このとき，部下の側で応答可能性が立つための場そのものが消える。自分の判断について問われ，答えを受け止めてもらえる相手がいなければ，答える立場は成立のしようがない。形骸化が集団の力学として引き受けを代理物に置き換えていくのに対し，自惚れは関係の構造として，引き受けが成立する条件を先に壊す。二つの失敗は水準を異にし，補完的に働く。集団の水準で忠誠の信号合戦が回っているとき，関係の水準では，求めながら答えない構えが批判の受け手を消していることが多い。

#### 5.2 成功の様式：3Mの三操作

反対の極に，引き受けを育てることに成功してきた設計がある。広く知られた例として，3Mの一連の制度を，本稿の語彙で読み直す。3Mはボトムアップ経営の典型と呼ばれてきたが，本稿の読みは逆である。ボトムアップの弱点は，結晶化した個人の突破力に成否が懸かるという個人への依存にあり，3Mの制度は，その依存を組織の側に肩代わりさせた設計として読める。4.3節で見た野中のミドルが人格の力で少数の向きを深く増幅する媒介だとすれば，3Mの制度化された運用は人を選ばずに広い口径で結晶化を保護する装置であり，両者は補完する。この読みは，3Mの設計者たちが本稿の語彙で考えていたという歴史の主張ではなく，公に知られてきた制度の機能を枠組みの側から再記述するものである。そのうえで重要なのは，3Mが意図そのものを製造しているのではない，という点である。4.2節で見たとおり，それはできない。3Mがしているのは，意図が発現する条件の側を整える，三つの操作である。

第一は，発現の阻害を除去することである。15%ルール（就業時間の一部を，事前の正当化を要さずに個人が選んだ課題に充ててよいとされる運用）と，それを支える社内の設備が，着手のコストと資源の障壁を取り除く。第二は，説明責任の配置を変えることである。通常の組織は，何かを始めることに正当化を要求する（既定は「やらない」側にある）。3Mの運用は，継続を既定の側に置き，説明の要求を停止の側に移したものとして読める。よく知られた起源の挿話では，ある開発者が中止の指示に背いて開発を続け，後に経営者がこれを，没頭している適切な人物は放っておき自発性を信頼するという方針へと変えた[^b10]。その経営者は，人が犯す誤りは経営が逐一指示するという誤りに比べればはるかに軽い，という趣旨を述べている。この停止側の設計の正体は「止めるな」という放任ではなく，「止める者が答えよ」という配置である。組織が引き受けに介入してそれを止めるなら，その介入の側に説明責任を課す。失敗そのものが個人への答責要求を起動しにくい構造として読める。

この第二の操作は，2.4節の相互性を制度に写した形にあたる。引き受けを求める側の組織が，止めるという自らの判断について答える側に回る。松本[^b15]が示すrespectの語源respicěre，すなわち見返すという動きを借りれば，従業員の引き受けという眼差しを，組織が制度化された運用の水準で見返す設計である。誤解を二つ封じておく。第一に，保護されているのは実績のある個人の特権ではない。ポストイットは，失敗作とされた弱い接着剤と，讃美歌集の栞という私的な困りごとから始まり，着手の時点で示せる実績を持たなかった[^b10]。守られる対象は人ではなく，まだ実績のない結晶化と，その着手から初期の継続までである。第二に，これは免責でもない。誰も答えなくてよいのではなく，答える義務の置き場所が，始める側から止める側へ移されているだけである。なお，ここでいう説明責任は，2.4節の区別でいえば制度の層（accountability）の配置である。制度は移転できない応答可能性を作れないが，その立つ場を用意することはできる。

この設計には，医療の側に先行する同型がある。薬剤師は，処方に疑わしい点があるときは処方した医師に問い合わせて確かめた後でなければ調剤してはならず（薬剤師法24条），問われた医師の側には，これに適切に対応する義務が課されている（保険医療機関及び保険医療養担当規則23条2項）。問う義務と答える義務の両側を条文が固めており，要求する側が自らも答える側に回るという相互性が，医療では法の水準で実装されている。組織を同じ形で縛る法はない。だがこの法令の配置は，問う側と答える側の義務を対にして，相互的な理由の交換を制度化した例である。本稿はここから，制度として反復される義務がやがて構えの形成を支えうる，という仮説を置く。その制度は法である必要がない。社内の制度化された運用でも足りうることを，3Mの例は示唆している。

第三は，インセンティブをそろえることである。直近数年に出た新製品が売上の一定割合を占めることを規律として課し，経営層の側にもそれに整合する利得を置く[^b10]。これにより，途中の試行を許容することが，管理者の徳に依存せず，組織の自己利益と整合する。

三つを束ねると，これは基質を保護し阻害因子を除去するという，一つの設計になっている。遭遇から結晶化した向きを途中で殺さず，その発現を妨げる要因（正当化の要求，資源の欠如，早すぎる打ち切り）を取り除く。ただしこの設計が保証するのは，試行の量と，結晶化した向きが殺されないことまでであって，個々の試行の成功ではない。成功した事例だけを見て設計の万能を語ることのないよう，この限界は明示しておく。なお，遭遇から結晶化した向きが社会的な需要と前もって整合するのは，遭遇の相手がより広い層を代表している度合いにおいてである。患者は他の患者を，顧客は市場を代表しうる。停止側に説明責任を置く配置は，この整合の確認を，答えを伴う形で実行する装置でもある。

最後に，なぜこれらが制度でなければならないのかを言語化しておく。挑戦せよ，自分ごとで捉えよ，勝手にやってよい，といった口頭の奨励は，三つの理由で，原理的に制度の代わりにはならない。第一に，自発性そのものは順方向の伝達に載らない。命じられて始めた自発はすでに自発ではない。順方向で渡せるのは意図の理由までであり，自発性の発現を支えるのは条件の設計である。第二に，口頭の許可だけでは，誰がその許可について答えるかという関係が，制度的に固定されない。失敗したとき，許可した個人は言った覚えがないと降りることができる。若手が着手の前に確認を重ねるのは意欲の不足ではなく，その許可の答責が本物かどうかを検証する合理的な行動である。第三に，許可する側の管理者自身が説明責任の秩序に拘束されており，部下の試行を言葉で守る行為は，管理者個人の徳と勇気を消費する。15%ルールが継続的な運用として置かれているのは，この三つを同時に解くためである。この運用は自発を命じず，着手に許可を要しないという条件だけを定める。制度は個人と違って言った覚えがないとは言えず，降りられない。そしてこの設計は，守る側の徳にも勇気にも依存しない。本稿が供給する説明言語が，この奨励の言葉と別物であることも，ここで区別しておく。説明言語はなぜやるのかの構造を渡し，引き受けの前提を整える。発現を保証するのは条件の設計の側であり，言語と制度は代替ではなく補完の関係にある。

#### 5.3 先行指標による観測

失敗と成功の様式を分けたうえで，組織はイノベーションの管理を，遅れて出てくる指標（売上）から，先行する指標へと移すことができる。観測の対象は，誰の向きがどこで結晶化しているかという状態と，その向きが実際に動いているか・どこで摩擦が起きているかという駆動の状況である。

ただし，何を測ってよいかには一線を引く。測るのは価値の中身ではなく，発現の条件と，行動に現れる相関物である。引き受けの内的な側，すなわち意図の更新が本当に起きたかは，直接には測れない。一方，応答可能性の関係の側，すなわち誰が誰に理由を求め，誰が実際に答えたかという配置は，観測できる。表2の指標は，この関係の配置と発現の条件とに属する。この留保を保ったまま，観測の枠組みを表2に示す。各指標の測定単位，データの取得方法，評定の一致といった測定の設計は本稿の射程の外にあり，枠組みを実装する研究の課題として残る。

もう一つ，観測の偏りを述べておく。表2の指標は，結晶化と挑戦の側に現れる引き受けを捉えるように作られている。だが引き受けは，新しい向きの結晶化に限らない。既存の業務の品質や安全を自らの判断理由として保持し，その判断について日々答える立場に立ち続けること，すなわち維持を担うことも，2.4節の定義を満たす引き受けである。異常に気づいて手を止める判断，手順を守り続けるという判断について誰が答えるのかを問えば，その立場は確認できる。目立つ形をとらず，提案の数のような指標に現れにくいだけである。したがって，表2における指標の不在を，引き受けの不在と読み替えてはならない。

**表2　引き受けの先行指標（候補）**

| 観測の対象     | 先行指標の例                                                 | 確かめていること                                             |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 結晶化の発生   | 自発的な提案の発生数とその出所の分布（業務内の遭遇由来か，業務外・社外由来かを区分） | 遭遇から結晶化への経路が生きているか                         |
| 発現の阻害     | 自由裁量時間・設備の実利用率，着手までの承認段数             | 阻害が除去されているか                                       |
| 保護           | 自発的な活動の継続期間，中断理由の分布                       | 結晶化した向きが殺されていないか                             |
| 停止の質       | 停止判断の文書化率と，その説明の質                           | 「止める者が答えよ」が機能しているか                         |
| 整合           | 遭遇の相手の分布（顧客・現場・社会をどれだけ代表するか）     | 遭遇由来の向きが需要と整合する度合い                         |
| 判断所在の明示 | AIに委ねた事実認識と人が保持した価値判断の記録率，採択・停止判断における最終応答者の明記率 | 委譲が判断の所在を拡散させず，可視化として機能しているか（第4節の逆転仮説の観測点） |

*注：この表に，意図の更新そのもの（引き受けの内的な側）を測る行はない。一方，応答可能性の関係の配置は，停止の質や判断所在の明示の行を通じて観測される。残りの行が捉えるのは，発現の条件と行動に現れる相関物である。*

### 6. 結論

自分ごと化は，命令で直接生み出すことも，研修で直接植え付けることもできない。だが，偶然に委ねるしかないものでもない。それを引き受けと身体化の複合として再定義すると，組織にできることとできないことの境界が引ける。組織は意図そのものを注入できないが，従業員が問題の保持者と身体ごと出会う遭遇を設計できる。結晶化しかけた向きを理由なく途中で止めず，止めるのであれば止める側が答える。そして引き受けの内的な成立は直接には測れないと知ったうえで，応答可能性の関係の配置と，発現の条件を観測する。本稿が示したのは，以上の運用原則と，その背後にある二経路モデルである。

医療が一世代をかけて学んだのは，人は意味を理解し目的を共有しなければ，自分自身の治療にすら主体的には参加しない，ということだった。組織はこの認識を，AIの時代にこそ必要とする。生成AIは知識の外化と結合を加速するが，それを引き受ける主体と，引き受けが育つ場（人と人とが向き合う社会化の場）は，同じ仕方では加速されない。むしろAIが外化と結合を肩代わりするほど，律速段階はそちらへ移り，引き受けと身体化を回せるかどうかが組織の速さを決めるようになる。

最後に，本稿の射程の限定を，もう一度逆向きに置いておく。引き受けの範囲を契約で区切らずに自分ごと化を求める問題は，日本型の雇用において特に顕在化しやすい。だが，契約で区切れていたのは職務を事前に明文化できていたからであり，その明文化できる部分こそ，AIがこれから吸収していくものである。契約に書ける仕事が移っていったあとには，契約に書けない判断と引き受けの占める比重が高まっていく。日本型の組織がこの問題を長く抱えてきたことは，弱みであると同時に，これから多くの組織が向き合う問題を先に経験しているということでもある。

これを知る者はこれを好む者に如かず。これを好む者はこれを楽しむ者に如かず[^n4]。組織の周知が渡せるのは，知るまでである。好む者と楽しむ者は，周知だけでは生まれない。本稿が二経路モデルとして構造化したものは，この言葉と響き合う。渋沢栄一が論語を算盤の傍らに置いて以来[^n5]，日本の組織はこの言葉を手元に持ち続けてきた。欠けていたのは教えではなく，教えを組織の設計に写す語彙である。その経験を，この語彙とともに残すこと。それが本稿の目的である。

---

## 注

[^n1]: 本稿の用語法として，制度の層に置かれ，役割の間で移転や再配賦が可能な履行の責務と，その履行についての説明の義務にaccountability（説明責任）を，引き受けた本人に帰属し移転できない応答の立場にanswerability（応答可能性）を当てて訳し分ける。関連する測定論上の区別は[^b13]に拠る。なお，Darwall[^b14]は同書でaccountabilityの語を二人称的な関係を含む広い意味で用いる。本稿の訳し分けは同書の用語法の再現ではなく，制度の層と関係の層を測定と設計のために分節する，本稿の操作的な区別である。
[^n2]: 教育の場面にも同型の類例がある。筆者が同席した大学研究室への訪問では，研究に向いていないかもしれないと自己判断しかけた学生の問いに，教員が自らの大学院時代の迷いを開示して答えを返していた。求める側が自らも答える側に回るという第5節の構造の，組織の外での観察例である。
[^n3]: 教育の側からは，批判的思考を明示的には教えてこなかった失敗を生成AIが露出させたという指摘があり[^b22]，知識労働の側では，AI使用下での批判的思考の発揮が使用者の自己確信とAIへの信頼に依存することが報告されている[^b23]。
[^n4]: 『論語』雍也第六。訓読は金谷治訳注『論語』（岩波文庫，2001年）に拠る。
[^n5]: 渋沢栄一（守屋淳訳）『現代語訳 論語と算盤』（筑摩書房・ちくま新書，2010年）。渋沢は仕事に対する趣味を説く章（第五章「理想と迷信」）で，雍也のこの言葉を自ら引いている。

## 参考文献

[^b1]: 国土交通省，**「水害リスクを自分事化し，流域治水に取り組む主体を増やす流域治水の自分事化検討会」とりまとめ**（2023），https://www.mlit.go.jp/report/press/mizukokudo03_hh_001203.html
[^b2]: 陣内雄次，ＳＤＧｓと地方自治体計画の自分事化に関する一考察，**共生科学，13**，72-83（2022）
[^b3]: 庄司敬子，清水裕美子，堀下智子，武内寛子，安全行動に影響を与える要素の検討，**あんけん，Vol.18**，JR西日本安全研究所（2025）
[^b4]: 福原康司，**自分事化に関する探索的研究：心理的所有（psychological ownership）概念を拠り所にして**，専修大学経営研究所定例研究会資料（2022）
[^b5]: 神吉直人，就労者の「仕事に対する当事者意識」概念の検討，**追手門経営論集，31**（1），1-18（2025），https://doi.org/10.69274/105250601
[^b6]: World Health Organization，**Adherence to Long-term Therapies: Evidence for Action**，World Health Organization（2003）
[^b7]: 上野治香，山崎喜比古，石川ひろの，日本の慢性疾患患者を対象とした服薬アドヒアランス尺度の信頼性及び妥当性の検討，**日本健康教育学会誌，22**（1），13-29（2014）
[^b8]: 今在慶一朗，手続き的公正要因としての説明責任と鄭重さに対する中心的・周辺的認知処理の影響：裁判での弁護活動を模したコミュニケーション実験，**社会心理学研究，31**（3），184-192（2016），https://doi.org/10.14966/jssp.31.3_184
[^b9]: 特定非営利活動法人保安力向上センター，**令和4年度産業保安等技術基準策定調査研究等事業（産業保安に関連する課題に対する新たな解決アプローチ推進調査）報告書**，経済産業省（2023），https://www.meti.go.jp/meti_lib/report/2022FY/000160.pdf
[^b10]: 野中郁次郎，竹内弘高（梅本勝博訳），**知識創造企業**，東洋経済新報社（1996）
[^b11]: 櫻井秀彦，アドヒアランス研究の意義と現状，**薬局薬学，14**（2），83-90（2022），https://doi.org/10.32160/yakkyoku.ra.2022-3000
[^b12]: K. Tomita，Domain-Native Development: A Mekiki Framework for AI-Assisted Knowledge Work，SocArXiv（2026），https://doi.org/10.31235/osf.io/cwkav_v1
[^b13]: K. Tomita，Philosophy as Cognitive Assay: Measuring the Delegation Legitimacy Boundary in AI-Assisted Knowledge Work，SocArXiv（2026），https://doi.org/10.31235/osf.io/e9qw5_v2
[^b14]: S. Darwall，**The Second-Person Standpoint: Morality, Respect, and Accountability**，Harvard University Press（2006）
[^b15]: 松本大理，ダーウォルの二人称的尊敬と相互的尊敬について，**山形大学紀要（人文科学），21**（1），1-15（2026），https://doi.org/10.15022/0002001699
[^b16]: Anthropic，Meet the Winners of Our Built with Opus 4.6 Claude Code Hackathon（2026），https://claude.com/blog/meet-the-winners-of-our-built-with-opus-4-6-claude-code-hackathon
[^b17]: 宮原史，土木技術者の越境学習：民間企業から国の研究所への派遣に着目して，**土木学会論文集，81**（1），24-00203（2025），https://doi.org/10.2208/jscejj.24-00203
[^b18]: D. F. Thompson，Moral Responsibility of Public Officials: The Problem of Many Hands，**American Political Science Review，74**（4），905-916（1980），https://doi.org/10.2307/1954312
[^b19]: I. van de Poel，L. Royakkers，S. D. Zwart，**Moral Responsibility and the Problem of Many Hands**，Routledge（2015），https://doi.org/10.4324/9781315734217
[^b20]: A. Matthias，The Responsibility Gap: Ascribing Responsibility for the Actions of Learning Automata，**Ethics and Information Technology，6**（3），175-183（2004），https://doi.org/10.1007/s10676-004-3422-1
[^b21]: 八代充史，メンバーシップ型雇用管理とジョブ型雇用管理：ジョブ型雇用管理は日本に定着するか？，**日本労働研究雑誌**，755，34-43（2023）
[^b22]: P. Soundar-Shah，A. Kestigian，We Have Never Taught Critical Thinking，**Inside Higher Ed**（2026）
[^b23]: H.-P. Lee，A. Sarkar，L. Tankelevitch，I. Drosos，S. Rintel，R. Banks，N. Wilson，The Impact of Generative AI on Critical Thinking: Self-Reported Reductions in Cognitive Effort and Confidence Effects From a Survey of Knowledge Workers，**Proceedings of the 2025 CHI Conference on Human Factors in Computing Systems**，Article 1121，1-22（2025），https://doi.org/10.1145/3706598.3713778
[^b24]: P. E. Tetlock，Thinking the Unthinkable: Sacred Values and Taboo Cognitions，**Trends in Cognitive Sciences，7**（7），320-324（2003），https://doi.org/10.1016/S1364-6613(03)00135-9
[^b25]: R. M. Ryan，E. L. Deci，Self-Determination Theory and the Facilitation of Intrinsic Motivation, Social Development, and Well-Being，**American Psychologist，55**（1），68-78（2000），https://doi.org/10.1037/0003-066X.55.1.68
[^b26]: E. W. Morrison，F. J. Milliken，Organizational Silence: A Barrier to Change and Development in a Pluralistic World，**Academy of Management Review，25**（4），706-725（2000），https://doi.org/10.5465/amr.2000.3707697
[^b27]: E. W. Morrison，Employee Voice and Silence，**Annual Review of Organizational Psychology and Organizational Behavior，1**，173-197（2014），https://doi.org/10.1146/annurev-orgpsych-031413-091328
[^b28]: K. Tomita，Decomposing Agency, Isolating Answerability: Cultivating What Cannot Be Delegated in AI-Assisted Learning，EdArXiv（2026），https://doi.org/10.35542/osf.io/hvbfe_v2

---

**Abstract**

In Japanese organizations, *jibungoto-ka* (treating matters as one's own) is demanded across domains, yet the concept remains underdeveloped. Medicine confronted a similar problem in shifting from compliance to adherence; medication counseling was one practical implementation of this shift. This article transfers the structure to organizations, redefining *jibungoto-ka* as undertaking—holding an internally endorsed purpose within a relation of answerability—combined with embodiment, its integration into practice. Answerability is a non-transferable standing to give reasons to specific others and requires reciprocity. The medicine–organization asymmetry derives from pathways of encounter, not from domains. We propose two pathways of organizational adherence: a forward pathway through which employees undertake managerial purposes, and a reverse pathway through which employee-originated orientations enter a formal review process, and decision makers give reasons for adoption, deferral, or termination. Chronic failure results from pressing only the forward pathway. As generative AI accelerates externalization and combination, undertaking and embodiment become the rate-limiting steps. We derive three principles: designing enabling conditions including encounters, assigning accountability for stopping decisions, and observing leading indicators.
