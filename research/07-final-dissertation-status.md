# Final Dissertation Status

## 1. Dissertation Title

**VREdu: An Adaptive, Rule-Based Virtual Reality Environment for Teaching Sorting and Searching Algorithms**

## 2. Final Report Status

The VREdu dissertation has reached its final report stage. The completed report contains approximately 13,990 words and is structured as a five-chapter MSc Software Engineering dissertation.

The dissertation documents the design, implementation, evaluation, and reflection associated with VREdu, a Unity-based first-person virtual learning environment for teaching sorting and searching algorithms.

## 3. Research Focus

The dissertation investigates whether a reusable rule-based mistake-detection architecture can support multiple sorting and searching algorithms within a shared Unity learning environment without placing algorithm-specific logic inside the common feedback pipeline.

The project covers eight algorithms:

### Sorting algorithms

- Bubble Sort
- Selection Sort
- Insertion Sort
- Quick Sort
- Merge Sort

### Searching algorithms

- Linear Search
- Binary Search
- Ternary Search

The current evaluated implementation uses keyboard and mouse interaction on Windows. The architecture is designed with future XR and headset support in mind, but the current report does not claim that a completed headset-based implementation was evaluated.

## 4. Main Contributions

The dissertation identifies the following contributions:

- A reusable rule-based mistake-detection architecture.
- A shared feedback pipeline separated from algorithm-specific rules.
- Eight algorithm stations using a common interaction contract.
- Adaptive hint escalation based on repeated learner mistakes.
- A mistake taxonomy shared across algorithms.
- Bloom’s-Taxonomy-aligned flashcard progression.
- Session-level learner profiling and summary generation.
- Optional LLM tutoring through an abstract service interface.
- A null-service fallback that allows the application to operate without an API key.
- Editor utilities supporting repeatable scene construction and setup.
- A documented development, testing, and issue-resolution process.

## 5. Dissertation Structure

The final dissertation contains the following sections:

- Abstract.
- Research Overview.
- Chapter 1: Introduction.
- Chapter 2: Related Work.
- Chapter 3: Solution.
- Chapter 4: Evaluation.
- Chapter 5: Conclusions and Future Work.
- References.

### Chapter 1: Introduction

Introduces the educational problem, research question, motivation, aims, objectives, scope, deliverables, and report structure.

### Chapter 2: Related Work

Discusses:

- active algorithm visualisation;
- virtual learning environments;
- station-based interaction;
- rule-based adaptive tutoring;
- learner modelling;
- formative assessment;
- Bloom’s Taxonomy;
- and optional LLM tutoring.

The chapter connects findings from previous research to the design decisions implemented in VREdu.

### Chapter 3: Solution

Describes:

- the overall architecture;
- the mistake-detection and feedback pipeline;
- the mistake taxonomy;
- learner profiling;
- level progression;
- flashcard assessment;
- station implementation;
- navigation and scene flow;
- session data;
- user-interface design;
- optional LLM tutoring;
- learner dashboards;
- and software-engineering practices.

### Chapter 4: Evaluation

Evaluates:

- architecture separation;
- algorithm-specific rule behaviour;
- adaptive hints;
- flashcard gating;
- session-to-profile persistence;
- dashboard behaviour;
- usability checks;
- LLM integration;
- input-conflict diagnosis;
- runtime issue resolution;
- and reproducibility.

The evaluation is based on architecture inspection, scenario-based verification, runtime testing, documented issues, screenshots, and repository evidence.

### Chapter 5: Conclusions and Future Work

Summarises the results, identifies the technical contributions, reflects on engineering decisions, discusses limitations, and proposes future work including automated regression testing, CI/CD, XR support, accessibility evaluation, larger learner studies, and advanced adaptive feedback.

## 6. Evaluation Scope and Limitations

The evaluation provides evidence for the technical architecture, algorithm-rule behaviour, adaptive feedback design, flashcard gating, persistence model, dashboard, runtime interaction, and final issue resolution.

The report does not claim that VREdu has definitively improved learner comprehension, retention, or engagement unless such claims are supported by appropriate empirical evidence. Educational effectiveness beyond the evaluated technical behaviour remains an area for future investigation.

The report also recognises the following limitations:

- The current implementation uses desktop keyboard and mouse interaction.
- The evaluation is not equivalent to a headset-based VR study.
- Runtime results can be affected by Unity scene setup and hardware configuration.
- The optional LLM component depends on API configuration and network availability.
- Screenshots provide qualitative evidence rather than performance metrics.
- Manual testing may be affected by tester bias.
- Automated EditMode regression testing and continuous integration remain future improvements.

## 7. Repository Reproducibility

The source code, setup instructions, development documentation, test records, screenshots, and final issue-resolution material are available in the project repository:

```text
https://github.com/Sayali-Lohokare/Capstone_VREdu
```

The repository provides the following supporting documents:

| Purpose | Repository document |
|---|---|
| Main project overview | [`README.md`](../README.md) |
| Technical architecture | [`docs/02-technical-explanation.md`](../docs/02-technical-explanation.md) |
| Installation and build process | [`docs/03-installation-and-setup.md`](../docs/03-installation-and-setup.md) |
| Development issues and fixes | [`docs/04-development-log-and-issues.md`](../docs/04-development-log-and-issues.md) |
| Testing and observed results | [`docs/05-testing-and-observed-results.md`](../docs/05-testing-and-observed-results.md) |
| Conclusion and next steps | [`docs/06-conclusion-and-next-steps.md`](../docs/06-conclusion-and-next-steps.md) |
| Final issue resolution | [`docs/08-final-issue-resolution-and-project-completion.md`](../docs/07-final-issue-resolution-and-project-completion.md) |

## 8. Evidence Available in the Repository

The repository contains supporting evidence including:

- Unity classroom screenshots.
- Algorithm-station screenshots.
- Linear Search runtime evidence.
- Learner dashboard and summary evidence.
- LLM tutor evidence.
- Unity hierarchy screenshots.
- Console warnings recorded during diagnosis.
- Input-conflict investigation evidence.
- Final issue-resolution documentation.
- Installation and build procedures.
- Incremental version-control history.

The screenshots and issue records document both early failures and later corrections, preserving the development process rather than presenting only the final intended behaviour.

## 9. Final Project Position

The completed work demonstrates that a shared rule-based mistake-detection architecture can be implemented across eight sorting and searching algorithms without placing algorithm-specific evaluation logic inside the common feedback pipeline.

This conclusion is supported by the implemented architecture, scenario-based verification, runtime testing, persistence checks, repository evidence, and documented issue-resolution process.

The project is best understood as a technically structured educational software prototype. Its contribution is architectural and engineering-focused, while larger-scale evaluation of learning gain, retention, and long-term learner impact remains appropriate future work.

## 10. Final Status

**Status: Final dissertation report completed and supporting repository documentation available.**
