# Project Overview

## 1. Introduction

Capstone_VREdu is a Unity-based educational software project developed to support the teaching and learning of searching and sorting algorithms through an interactive three-dimensional classroom environment. The system is designed as a first-person desktop application for Windows PC and allows learners to engage with algorithms through active, step-by-step interaction rather than passive observation alone.

The project has been developed as part of a software engineering capstone and is documented through this repository not only as a codebase, but also as an academic record of design decisions, implementation stages, testing activities, and technical issues encountered during development.

## 2. Project Aim

The primary aim of the project is to improve algorithm learning by providing an environment in which students can practise core algorithmic operations inside a virtual classroom. Instead of only reading pseudocode or lecture slides, learners are expected to interact directly with visual representations of arrays, perform algorithm steps through keyboard input, and receive immediate feedback when they make mistakes.

A secondary aim is to explore how a structured digital environment can combine procedural learning, adaptive feedback, reflection, and contextual learner support within a single educational application.

## 3. Educational Context

Traditional algorithm teaching often relies on static diagrams, theoretical explanation, and written examples. While these remain important, students frequently struggle to translate conceptual understanding into procedural execution. This project addresses that challenge by embedding algorithm learning into a navigable 3D environment where action, feedback, and repetition are central parts of the learning process.

The project therefore sits at the intersection of software engineering, human-computer interaction, and educational technology.

## 4. Scope of the System

The system is designed around a virtual classroom containing eight independent algorithm stations. These stations are grouped into sorting and searching categories.

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

Each station is designed to present an algorithm in an interactive way through a combination of instructional text, coloured array blocks, keyboard actions, and rule-based feedback.

## 5. Intended User Experience

The intended user flow of the system is as follows:

1. The application opens in an authentication scene where the learner can register or log in.
2. After successful authentication, the learner enters the main classroom scene.
3. The learner moves around the classroom using first-person controls and approaches any algorithm station.
4. When close to a station, a prompt appears inviting the learner to begin interaction.
5. The learner performs the algorithm step by step using keyboard controls specific to that station.
6. The system evaluates each action and provides feedback or hints where necessary.
7. After successful completion of a level, the learner completes flashcard-based reinforcement questions.
8. At the end of the session, the learner exits to a summary scene showing performance statistics and reflective prompts.

This flow is intended to support both guided practice and learner self-reflection.

## 6. Core Features

### 6.1 Interactive algorithm stations
Each algorithm station presents a live 3D array representation and requires the learner to perform algorithm-specific actions such as swapping, selecting, shifting, or choosing search directions. These interactions are mapped to keyboard controls and are visually reflected through animations and highlighting.

### 6.2 Adaptive feedback
The project includes a rule-based feedback system that monitors learner actions and identifies mistake types. Hints are intended to escalate in severity from light prompts to more explicit guidance depending on repeated errors, allowing the system to support learners at different levels of difficulty.

### 6.3 Three-level progression model
Each algorithm is designed to contain three levels of increasing difficulty. Lower levels use smaller arrays and more frequent assistance, while higher levels reduce support and increase challenge. Progression depends on successful performance and flashcard outcomes.

### 6.4 Flashcard reinforcement
After completing a level, the learner is expected to answer flashcard questions linked to the algorithm and informed by recent mistakes. These cards are structured to support reinforcement across multiple cognitive levels, from basic recall to deeper conceptual reasoning.

### 6.5 Session summary and reflection
The final summary scene is intended to provide a record of attempted algorithms, levels reached, hints used, mistakes made, and flashcard performance. The design also includes short reflective prompts so that learners can think about their difficulties and progress.

### 6.6 LLM integration for contextual learner support
The system design includes an LLM-based question-answering component implemented through a dedicated panel. This module is intended to allow the learner to submit free-form questions and receive context-aware responses based on the current algorithm and recent mistakes. The project documentation indicates that this feature is implemented through an `LLMPanelController` and an OpenAI service layer, while the rest of the system remains usable even when no API key is configured.

## 7. Technical Context

The project is built in Unity 2022.3 LTS and targets Windows PC. It uses keyboard and mouse input rather than requiring a VR headset, although the broader architecture leaves room for future expansion into more immersive formats.

The documented project structure includes the following major components:

- Authentication systems for login and registration
- Classroom systems for movement and station access
- Core systems for feedback, input, levels, audio, and session tracking
- Flashcard systems for post-level reinforcement
- LLM-related scripts for contextual question-answering support
- Scene setup utilities for configuring the project after import

This structure reflects an attempt to separate concerns across educational logic, interaction logic, and supporting infrastructure.

## 8. Current Development Position

At the present stage, the project should be understood as an actively documented capstone build rather than a fully polished final product. The repository is being maintained to show progress incrementally, including intended system design, setup procedures, testing activity, and observed implementation issues.

This means the repository records both successful development work and unresolved problems. Such transparency is important in an academic context because it shows process, reflection, and evidence-based debugging rather than presenting the project as unrealistically flawless.

## 9. Role of this Repository

This repository functions as a structured development record for supervisor review. It is intended to show:

- what the system is designed to do,
- how it is structured,
- how it is configured and run,
- what has been tested,
- what issues have emerged,
- and how those issues are being documented over time.

For that reason, the repository is organised not only around implementation files, but also around documentation files placed in the `docs/` directory.

## 10. Linked Documentation

This project overview serves as the first formal document in the repository documentation sequence. It is intended to be followed by additional documents covering:

- technical explanation,
- installation and setup,
- development logs,
- testing and debugging records,
- screenshot-based issue analysis,
- and supervisor-facing progress summaries.

Together, these documents provide an auditable account of the project’s development lifecycle.
