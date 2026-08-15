# Dissertation Draft Status

## 1. Current Status

The dissertation is currently in draft form. The main research narrative has been prepared, but further revision is required before the document can be treated as a final submission.

The current draft contains:

- an abstract,
- five main chapters,
- a research question,
- aims and objectives,
- a literature review,
- a solution and architecture chapter,
- an evaluation chapter,
- conclusions and future work,
- and a reference list.

## 2. Current Chapter Structure

### Abstract

Introduces the educational problem, the VREdu environment, the eight algorithms, the adaptive rule-based feedback layer, the flashcard assessment model, and the optional LLM tutoring channel.

### Chapter 1: Introduction

Introduces the research context, motivation, research question, objectives, scope, deliverables, and report structure.

### Chapter 2: Related Work

Discusses:

- algorithm visualisation,
- active learner engagement,
- virtual reality in education,
- intelligent tutoring systems,
- rule-based learner modelling,
- gamified formative assessment,
- Bloom’s Taxonomy,
- and large language models in tutoring.

### Chapter 3: Solution

Explains:

- the system architecture,
- the mistake-detection pipeline,
- the mistake taxonomy,
- learner profiles,
- level progression,
- flashcards,
- station implementation,
- navigation,
- session data,
- user interface,
- optional LLM tutoring,
- and software engineering practices.

### Chapter 4: Evaluation

Describes:

- the evaluation scope,
- scenario-based verification,
- reproducibility,
- results,
- session-to-profile persistence,
- extensibility,
- hint escalation,
- and comparative positioning.

### Chapter 5: Conclusions and Future Work

Summarises the research contribution, reflects on the engineering process, discusses alignment with the project standard, and identifies future development opportunities.

## 3. Areas Requiring Revision

The following areas should be reviewed before final submission:

- Grammar and sentence structure.
- Consistency of terminology.
- Consistency of tense.
- Accuracy of claims about implementation.
- Accuracy of claims about educational impact.
- Citation completeness.
- Reference formatting.
- Figure numbering.
- Table numbering.
- Cross-references between sections.
- Consistency between the dissertation and the final software build.
- Clear distinction between implemented, tested, partially implemented, and proposed features.

## 4. Draft Claims Requiring Care

The dissertation describes the system as a virtual reality environment, while the current documented interaction model is a keyboard-and-mouse first-person desktop experience. The final paper should describe this distinction accurately.

A suitable formulation is:

> VREdu is a Unity-based first-person virtual learning environment designed with future XR extensibility in mind. The current implementation is evaluated primarily as a desktop keyboard-and-mouse application.

The optional LLM component should also be described carefully. It is a supplementary service and should not be presented as the source of the core mistake detection, progression, or assessment logic.

## 5. Implementation Evidence

The following repository documents support the dissertation:

- `docs/02-technical-explanation.md`
- `docs/03-installation-and-setup.md`
- `docs/04-development-log-and-issues.md`
- `docs/05-testing-and-observed-results.md`
- `docs/06-conclusion-and-next-steps.md`
- `docs/08-final-issue-resolution-and-project-completion.md`

These documents provide evidence of architecture, setup, debugging, testing, final issue resolution, and completion status.

## 6. Evidence Still Required

Before final submission, the following evidence should be checked or added where available:

- final runtime screenshots,
- station interaction evidence,
- summary-screen evidence,
- flashcard evidence,
- LLM tutor evidence,
- test-case results,
- build information,
- final repository commit,
- and a reproducible installation process.

## 7. Draft Completion Criteria

The dissertation draft should be considered ready for final proofreading when:

- the research question is answered directly,
- each objective is linked to evidence,
- the literature review supports design decisions,
- evaluation results are distinguished from intended behaviour,
- known limitations are acknowledged,
- all references are checked,
- and the conclusion does not claim more than the evidence demonstrates.
