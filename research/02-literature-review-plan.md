# Literature Review Plan

## 1. Purpose

This document records the structure and preparation plan for the literature review in the VREdu dissertation.

The literature review positions the project within four main research areas:

1. Algorithm visualisation.
2. Virtual reality in education.
3. Intelligent and adaptive tutoring systems.
4. Gamified and formative assessment.

A fifth area concerns the use of large language models in educational tutoring.

## 2. Algorithm Visualisation

The literature review examines the difference between passive viewing and active learner interaction. The central design principle adopted by VREdu is that learners should construct algorithm states through their own decisions rather than only watching a pre-scripted animation.

The project applies this principle by requiring learners to perform actions such as:

- comparing adjacent values,
- choosing whether to swap,
- marking a minimum,
- shifting an insertion-sort key,
- selecting a pivot partition action,
- taking values during merge operations,
- moving through a linear search,
- choosing a binary-search half,
- and choosing a ternary-search region.

The research preparation task is to ensure that these claims are supported by accurate and relevant sources and that the literature is connected directly to the interaction model implemented in VREdu.

## 3. Virtual Reality in Education

The literature review considers when virtual reality is educationally useful rather than treating immersion as automatically beneficial. The project adopts a walkable classroom with separate stations because the station structure provides spatial separation between learning activities.

The research preparation should explain:

- why a first-person classroom was selected,
- why the project uses spatially separated algorithm stations,
- how direct manipulation supports the learning objective,
- and why the project currently targets keyboard and mouse input while retaining the possibility of future XR support.

The discussion should avoid claiming that the project proves virtual reality improves learning unless a controlled human-subject study has been conducted.

## 4. Intelligent and Adaptive Tutoring Systems

The literature review examines rule-based feedback, learner modelling, hint timing, hint specificity, and adaptive content sequencing.

VREdu applies these concepts through:

- the `IMistakeRule` interface,
- algorithm-specific mistake rules,
- the `FeedbackManager`,
- escalating hint severity,
- `LevelConfig`,
- `SessionData`,
- `LearnerProfile`,
- and mistake-biased flashcard selection.

The literature review should distinguish between:

- an adaptive architecture that has been implemented,
- architectural verification,
- and demonstrated learning effectiveness.

The system can be described as adaptive in its feedback and sequencing behaviour, but learning gains should not be claimed without appropriate user evaluation.

## 5. Rule-Based Systems

The research paper positions rule-based feedback as a deliberate choice because algorithmic correctness can be formally described.

The research preparation should explain that a rule-based approach provides:

- predictable behaviour,
- explainable feedback,
- deterministic testing,
- easier debugging,
- and independence from statistical model training.

The limitations should also be acknowledged. Rule-based systems require algorithm-specific knowledge to be explicitly encoded, and the quality of feedback depends on the completeness of the mistake taxonomy.

## 6. Gamified and Formative Assessment

The flashcard system is linked to formative assessment and Bloom’s Taxonomy. Flashcards are intended to appear after algorithm-level completion and to support conceptual reinforcement before progression.

The research discussion should explain:

- why assessment occurs after procedural activity,
- how flashcards are linked to recent mistake patterns,
- how Bloom levels are used to vary cognitive demand,
- and how the flashcard gate contributes to progression.

The written paper should clearly state whether these behaviours were tested structurally, manually, or through learner evaluation.

## 7. Large Language Models in Tutoring

The LLM feature is an optional supplementary channel. It is not intended to replace the core mistake-detection or feedback pipeline.

The research preparation should document:

- how the LLM receives the current algorithm context,
- how recent mistake information can be included,
- why the system can operate without an API key,
- how the null-service fallback works,
- and the risks of relying on external network services.

The LLM should be presented as an optional support feature rather than the primary source of algorithm correctness or assessment.

## 8. Literature Review Completion Tasks

Before final submission, complete the following tasks:

- Check that every in-text citation appears in the reference list.
- Check that every reference is cited in the main paper.
- Confirm publication details and author names.
- Use one consistent referencing style.
- Remove duplicated or incomplete entries.
- Connect each literature source to a specific design decision.
- Avoid presenting literature claims without explaining their relevance to VREdu.
- Distinguish project evidence from claims made by external researchers.

## 9. Expected Outcome

The completed literature review should do more than list sources. It should establish the theoretical and engineering rationale for the project and show how VREdu responds to limitations or opportunities identified in previous work.
