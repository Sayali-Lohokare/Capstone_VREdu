# Methodology and Evaluation Plan

## 1. Purpose

This document records the planned methodology for evaluating VREdu. It separates architectural verification, functional testing, runtime observation, and learner-outcome evaluation so that the dissertation does not treat these different forms of evidence as interchangeable.

## 2. Evaluation Areas

The project should be evaluated across four areas:

1. Architectural correctness.
2. Functional correctness.
3. Runtime usability and reliability.
4. Educational effectiveness.

The current project provides stronger evidence for the first three areas than for the fourth.

## 3. Architectural Evaluation

The architectural evaluation examines whether the shared feedback pipeline is independent from algorithm-specific rules.

The evaluation should verify that:

- `IMistakeRule` implementations can be instantiated independently.
- Algorithm-specific rule classes do not depend unnecessarily on Unity rendering.
- The shared feedback pipeline does not contain excessive algorithm-specific branching.
- New algorithm stations can be added through the shared interaction contract.
- Level configuration and flashcard content are represented as data rather than hard-coded into the common pipeline.

## 4. Functional Evaluation

Functional evaluation should use scenario-based tests for each algorithm.

Each algorithm should include:

- at least one valid-action scenario,
- one scenario for each major mistake type,
- and one boundary or completion scenario.

Examples include:

- Bubble Sort: correct swap, correct skip, unnecessary swap, missing swap, and premature completion.
- Selection Sort: correct minimum selection, incorrect minimum, and incorrect placement.
- Insertion Sort: valid shift, missing shift, and incorrect insertion.
- Quick Sort: valid pivot placement, incorrect pivot decision, and incorrect partition boundary.
- Merge Sort: correct left/right selection and out-of-order merge selection.
- Linear Search: correct next action, found target, skipped element, and incorrect not-found declaration.
- Binary Search: correct left/right decision and incorrect half selection.
- Ternary Search: correct third selection and incorrect third selection.

## 5. Adaptive Feedback Evaluation

The feedback system should be tested using repeated actions of the same mistake type.

The expected behaviour is:

1. The first mistake produces a lower-severity hint.
2. Repeated mistakes of the same type increase hint severity.
3. Severity does not exceed the maximum configured in `LevelConfig`.
4. A correct action resets the consecutive-mistake state.
5. Different mistake types are tracked separately.
6. Hint cooldown behaviour follows the active level configuration.

## 6. Progression and Flashcard Evaluation

The evaluation should confirm that:

- Level completion does not immediately bypass the flashcard stage.
- The flashcard panel appears after a valid level completion.
- Flashcard answers are recorded in session data.
- Correct and incorrect responses are distinguished.
- Level progression occurs only after the flashcard result is resolved.
- Flashcards can be selected according to algorithm level and learner mistake history.

## 7. Persistence Evaluation

The persistence loop should be checked from session start to later login.

The evaluation should confirm that:

- a user can be registered,
- the user can log in,
- session activity is recorded,
- summary statistics are generated,
- learner profile information is updated,
- the profile is stored locally,
- and the stored profile can be read during a later session.

The evaluation should also document any differences between intended persistence and observed runtime behaviour.

## 8. Runtime and Usability Evaluation

Runtime testing should record:

- whether the application opens successfully,
- whether scenes transition correctly,
- whether the classroom is readable,
- whether station prompts appear,
- whether keyboard input is captured correctly,
- whether text remains readable,
- whether visual elements overlap,
- whether flashcards appear,
- whether the summary contains valid data,
- and whether the optional LLM tutor responds when configured.

Issues should be documented with:

- date,
- build or project version,
- scene,
- action performed,
- expected outcome,
- observed outcome,
- severity,
- attempted fix,
- final status,
- and evidence screenshot where available.

## 9. Educational Evaluation

A future learner study could compare the adaptive VREdu feedback model against a static-feedback condition.

A controlled study could measure:

- pre-test and post-test performance,
- algorithm step accuracy,
- time to complete tasks,
- number of repeated mistakes,
- hint requests,
- flashcard performance,
- learner confidence,
- perceived usability,
- and delayed retention.

The current project should not claim statistically validated learning improvement unless such a study has been completed and ethically approved where required.

## 10. Evidence Limitations

The current evaluation is primarily based on implementation inspection, scenario-based reasoning, runtime testing, screenshots, and development records. This provides useful evidence of software behaviour and engineering process but does not substitute for a controlled educational study.

This limitation should be stated clearly in the dissertation.

## 11. Reproducibility

A reviewer should be able to reproduce the technical evaluation by:

1. Installing the documented Unity version.
2. Importing the repository project.
3. Applying the scene setup process.
4. Running the relevant scene.
5. Following the documented keyboard actions.
6. Comparing the result against the expected outcome.
7. Reviewing the corresponding repository evidence.

The repository should preserve the relevant documentation, screenshots, and commit history to support this process.
