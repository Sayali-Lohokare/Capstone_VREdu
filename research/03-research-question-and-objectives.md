# Research Question and Objectives

## 1. Main Research Question

The main research question for the project is:

> Is it possible to create a general, rule-based mistake-detection architecture that can be used with multiple algorithms and embedded in a first-person virtual learning environment to provide measurable and extensible support for learner comprehension of sorting and searching algorithms without modifying the underlying feedback engine for each algorithm?

## 2. Secondary Research Questions

The main question leads to the following secondary questions:

1. Can algorithm-specific mistake taxonomies be represented using independent C# rule classes while preserving real-time responsiveness in the Unity environment?
2. Can a locally persisted learner profile derived from session telemetry identify the learner’s strongest and weakest algorithms across repeated sessions?
3. Can adaptive hints and flashcard assessment be integrated without making the core learning workflow dependent on the optional LLM service?
4. Can the architecture be extended to additional algorithms without changing the shared feedback pipeline?

## 3. Research Aim

The aim is to design, implement, and critically evaluate VREdu as an interactive algorithm-learning environment that combines:

- active algorithm visualisation,
- rule-based mistake detection,
- escalating feedback,
- flashcard assessment,
- local learner profiling,
- and optional LLM tutoring.

## 4. Project Objectives

### Objective 1: Shared feedback architecture

Develop a shared feedback pipeline that can process learner actions independently of the algorithm-specific correctness rules.

**Primary components:**

- `InteractionHandler`
- `ActionLogger`
- `FeedbackManager`
- `HintPanelController`
- `AudioManager`

### Objective 2: Multiple algorithm stations

Implement eight algorithm stations under a common interaction contract.

**Algorithms:**

- Bubble Sort.
- Selection Sort.
- Insertion Sort.
- Quick Sort.
- Merge Sort.
- Linear Search.
- Binary Search.
- Ternary Search.

### Objective 3: Adaptive hint severity

Implement a hint model that increases guidance when the learner repeatedly makes the same type of mistake and reduces support after correct actions.

### Objective 4: Flashcard assessment

Implement a flashcard gate aligned with Bloom’s Taxonomy and biased towards the learner’s observed weaknesses.

### Objective 5: Session and learner persistence

Implement local persistence for users, session information, and learner profiles without requiring a networked backend.

### Objective 6: Evaluation

Evaluate the structural correctness, extensibility, and observed behaviour of the implemented system through scenario-based verification, runtime testing, and documented reflection.

## 5. Objective-to-Evidence Mapping

| Objective | Evidence source |
|---|---|
| Shared feedback architecture | Technical explanation and source architecture |
| Eight algorithm stations | Station implementations and runtime screenshots |
| Adaptive hint severity | Feedback rules and level configuration |
| Flashcard assessment | Flashcard assets, controller logic, and session records |
| Learner persistence | Session and user-data structures |
| Evaluation | Testing document, issue log, and final resolution record |

## 6. Scope

The project is limited to a single-player educational application designed for Windows PC. The current interaction model uses keyboard and mouse input. The architecture may support future XR controllers, but this project does not claim to provide a completed headset-based implementation unless that has been separately tested.

The project covers eight algorithms and focuses on procedural understanding, learner feedback, and session-level reflection. It does not claim to provide a statistically validated measure of long-term learning improvement without a controlled study involving participants.

## 7. Research Claims to Review

Before finalising the paper, check every claim against available evidence.

Claims that can be supported by the implementation include:

- The system contains multiple algorithm stations.
- The system uses algorithm-specific rule classes.
- The system includes adaptive hint logic.
- The system includes session tracking and flashcard components.
- The system includes an optional LLM integration layer.
- The architecture is designed to support extension.

Claims requiring additional empirical evidence include:

- The system improves learner comprehension.
- The system increases retention.
- The system is more effective than traditional teaching.
- The system improves engagement for all learners.
- The LLM improves learning outcomes.

These stronger claims should either be supported by a suitable evaluation study or rewritten as proposed benefits and future evaluation objectives.
