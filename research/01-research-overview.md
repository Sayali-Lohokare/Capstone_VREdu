# Research Overview

## 1. Research Project

The research project is titled:

**VREdu: An Adaptive, Rule-Based Virtual Reality Environment for Teaching Sorting and Searching Algorithms**

The project investigates the design and implementation of an interactive educational environment built in Unity. The system presents sorting and searching algorithms through a first-person virtual classroom in which learners interact directly with algorithm stations.

The current research paper is maintained as a draft while the implementation, evaluation evidence, written analysis, and presentation of findings continue to be refined.

## 2. Research Context

Understanding algorithms can be difficult when dynamic and stateful processes are presented only through static text or passive diagrams. Sorting and searching algorithms require learners to understand how values, indices, pointers, boundaries, pivots, and comparisons change over time.

VREdu addresses this challenge through an interactive learning environment in which the learner performs algorithmic actions directly. The system combines three-dimensional visualisation, rule-based mistake detection, adaptive hints, flashcard assessment, learner profiling, and optional large language model support.

## 3. Research Aim

The aim of the project is to design, implement, and critically evaluate a virtual learning environment that supports the learning of sorting and searching algorithms through active interaction and adaptive feedback.

The project focuses on whether algorithm-specific mistake rules can be separated from a shared feedback pipeline so that multiple algorithms can be supported without redesigning the underlying tutoring architecture.

## 4. Algorithms Covered

The application covers eight algorithms.

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

The algorithms were selected because they represent different procedural structures, including adjacent comparison, minimum selection, shifting, pivot-based partitioning, merging, sequential search, binary division, and ternary division.

## 5. Main System Features

The research prototype contains the following main features:

- Interactive 3D algorithm stations.
- First-person navigation through a virtual classroom.
- Step-by-step learner interaction.
- Algorithm-specific mistake detection.
- Escalating hints based on repeated mistakes.
- Three difficulty levels per algorithm.
- Flashcard assessment linked to algorithm progress.
- Bloom’s Taxonomy alignment for flashcard difficulty.
- Session-level mistake and performance tracking.
- Learner profile generation.
- Optional LLM-based tutoring support.
- Local user and session persistence.

## 6. Research Contribution

The main contribution of the project is the design of a reusable rule-based mistake-detection and feedback architecture. Algorithm-specific rules are separated from the shared application pipeline through a common interface.

This architecture is intended to support:

- explainable feedback,
- independent rule testing,
- consistent interaction across algorithms,
- extension to additional algorithms,
- and learner profiling based on recorded mistake patterns.

A second contribution is the integration of procedural interaction, adaptive feedback, flashcard assessment, and optional LLM support within one educational environment.

## 7. Current Research Status

The research paper is currently in draft form. The core chapters have been prepared, including:

- Abstract.
- Introduction.
- Related Work.
- Solution and Architecture.
- Evaluation.
- Conclusions and Future Work.
- References.

Further work is required to improve academic clarity, verify all claims against evidence, refine the evaluation discussion, check references, and ensure that the final paper accurately distinguishes implemented features from intended or future features.

## 8. Related Repository Documents

The software-development history is documented separately in the `docs/` folder:

- `docs/02-technical-explanation.md`
- `docs/03-installation-and-setup.md`
- `docs/04-development-log-and-issues.md`
- `docs/05-testing-and-observed-results.md`
- `docs/06-conclusion-and-next-steps.md`
- `docs/07-readme-for-markers.md`
- `docs/08-final-issue-resolution-and-project-completion.md`

The `research/` folder records the preparation and refinement of the dissertation itself.
