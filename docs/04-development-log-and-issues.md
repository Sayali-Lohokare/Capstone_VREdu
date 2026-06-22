# Development Log and Issue Analysis

## 1. Introduction

This document records the practical development and testing issues encountered while building and running the Capstone_VREdu project. It is intended to complement the project overview, technical explanation, and installation guide by documenting the actual trial-and-error process rather than only the intended system design.

In an academic context, this form of reflective documentation is important because it demonstrates that the project was not developed as a perfectly linear process. Instead, implementation required repeated setup attempts, execution tests, observation of runtime failures, interpretation of symptoms, and revision of assumptions. Recording these issues provides evidence of engineering practice, debugging activity, and critical reflection.

## 2. Intended Behaviour

According to the internal project documentation, the expected system flow is structured around three scenes: an authentication scene, a classroom scene, and a session summary scene. After login, the learner should enter the classroom, approach any of the eight algorithm stations, press the interaction key to begin at Level 1, perform algorithm actions through keyboard input, receive adaptive feedback, complete flashcard tasks after level completion, and later view an accurate summary of the session.[file:92][file:93]

The same documentation states that the classroom stations should display coloured 3D array blocks together with clear instructional text, world-space prompts, and algorithm-specific keyboard controls. It also states that session statistics should only appear after meaningful interaction has been recorded in `SessionData`.[file:92][file:93]

## 3. Development Context

During the practical build and run process, the system did not always behave in accordance with its intended architecture. Although the setup utilities, scene order, and runtime flow were documented, the testing process revealed several failures that affected scene preparation, runtime usability, visual presentation, and the final summary output.[file:93][file:94]

These issues emerged not only during initial setup, but also after the project had already been imported and partially configured. As a result, the development process involved repeated attempts to run the scenes, test station behaviour, inspect what was appearing on screen, and determine whether faults were caused by setup configuration, scene state, UI placement, or logic errors.

## 4. Trial-and-Error Process

The project was approached by following the documented setup path: importing the Unity project, allowing packages to resolve, opening the required scenes, and running the provided one-shot editor setup utilities for authentication, classroom stations, flashcards, repositioning, and summary preparation.[file:94]

After setup, the project was run in Play mode to test the full intended user flow. The testing then shifted into a trial-and-error cycle in which the scene was entered, stations were approached, keyboard interaction was attempted, and the resulting runtime behaviour was compared against the expected flow described in the documentation.[file:93][file:94]

Where the observed behaviour did not match the intended design, the process involved repeating setup actions, re-running scenes, checking whether stations had been positioned correctly, observing whether interaction prompts appeared, and determining whether the visible issues were local to one station or system-wide.

## 5. Setup-Related Difficulties

One of the main challenges during development was that successful import and scene preparation did not automatically guarantee correct runtime behaviour. The project includes many setup actions for the classroom scene, including station creation, UI generation, flashcard linking, repositioning, and content creation. This means that if any setup step is incomplete, misapplied, or visually inconsistent, the resulting runtime scene can appear partially broken even when the project technically opens.[file:94]

A related challenge is that the project documentation assumes that the one-shot setup utilities will configure the classroom correctly and idempotently. In practice, the visual and interaction results observed during testing suggest that the classroom scene could still enter a broken or unstable state even after setup had apparently completed, which made it necessary to verify the results through repeated execution rather than relying on configuration alone.[file:94]

## 6. Runtime Visual Failures

The most visible runtime issue was the appearance of severe overlapping text and object rendering around algorithm stations. Instead of displaying a clean instructional board and a readable arrangement of array blocks, multiple large blue letterforms and overlay elements appeared stacked over one another, obscuring the algorithm instructions and interfering with the readability of the station interface.

This problem appears to indicate that the scene was rendering repeated or misplaced text-related objects in front of the station boards. In practical terms, this broke the clarity of the learning interface because the learner could no longer easily interpret the station instructions, identify the relevant array values, or understand the current state of the algorithm interaction.

A further visual issue was that text in several areas appeared blurred, unclear, or difficult to read. This was especially important because the system depends heavily on on-screen instructional text, keyboard guidance, and algorithm state descriptions. When text becomes visually blurred or unreadable, the educational purpose of the station is weakened because the learner cannot reliably follow the step-by-step guidance.

## 7. Station Interaction Problems

The internal documentation explains that each station should begin at Level 1 when the learner approaches and presses the interaction key. It also describes a structured station process in which the learner performs algorithm actions, receives feedback, and progresses after successful completion.[file:93]

However, practical testing showed that the visible station state was not always coherent enough to support this process correctly. In the observed runtime condition, the station interface could appear visually corrupted, making it difficult to determine whether the current interaction state, highlighted elements, or instruction prompts were functioning as intended. This means that even when the core logic might still have been active, the usability of the station was significantly reduced by the rendering faults.

## 8. Problems at the End of a Session

Another major issue was the behaviour of the session completion screen. According to the intended design, the summary scene should present a meaningful record of the learner’s activity, including algorithms attempted, levels reached, mistakes made, hints used, flashcard results, and reflection prompts generated from the session data.[file:92][file:93]

During testing, however, the summary interface displayed a contradictory or incomplete state. The session completion screen indicated that no algorithms had been attempted and that flashcard performance was zero across zero attempted items, even though the session had already moved into a completion state. This suggests that the transition into the summary phase was not correctly aligned with the actual learner activity or that `SessionData` was not being populated, preserved, or interpreted correctly before the summary screen was shown.[file:92][file:93]

## 9. Flashcard and Completion Concerns

The technical explanation states that completing a station should trigger flashcard activity, and that progression through algorithm levels depends partly on the flashcard outcome. Flashcard results are also expected to contribute to the final session summary.[file:93]

The observed summary output showing zero attempted flashcards raises concern that this expected sequence did not complete correctly during testing. In practical terms, either the flashcard stage failed to appear, failed to register learner activity, or failed to write results into the data model before the application moved to its completion screen. This is an important issue because it affects both learner reinforcement and the credibility of the final statistics.

## 10. Interpretation of the Observed Failures

Taken together, the issues observed during testing point to a mismatch between intended scene logic and the actual runtime state of the project. The documented architecture presents a coherent sequence of login, classroom interaction, algorithm progression, flashcards, and summary reporting.[file:92][file:93]

The runtime evidence, however, suggests that the project currently experiences at least four practical categories of failure:

- setup may complete without guaranteeing a stable classroom scene,
- text and visual elements may overlap or render incorrectly,
- educational content may become blurred or unreadable during play,
- and the summary stage may be reached without valid learner activity being captured.

This does not mean the entire project concept is invalid. Rather, it indicates that integration between setup, visual presentation, interaction flow, and end-of-session reporting still requires refinement.

## 11. Academic Reflection

From a software engineering perspective, these failures are valuable to document because they demonstrate that the project has progressed beyond pure design and into meaningful implementation testing. The observed faults were not hypothetical concerns; they were practical problems encountered while attempting to execute the system as a learner would.

Including such evidence in the documentation strengthens the academic credibility of the project because it shows reflective development practice. Instead of presenting only intended features, the documentation acknowledges where setup broke, where runtime behaviour broke, where the visual layer reduced usability, and where the final reporting logic failed to match the expected educational workflow.

## 12. Implications for Further Work

The immediate priority for further development should be improving runtime stability and verifying the connection between scene setup, station interaction, flashcard completion, and summary generation. In particular, the rendering of station text and visual overlays should be reviewed first, because unreadable instructional content directly prevents meaningful educational use.

A second priority is validating the session pipeline end to end: station entry, learner action logging, flashcard triggering, `SessionData` persistence, and summary display. Until those links are reliable, the system cannot fully demonstrate the reflective learning cycle described in the design documents.[file:93]

## 13. Role of this Document

This development log should be read as a formal record of the project’s trial-and-error phase. It captures the difference between intended design and observed behaviour and therefore serves as evidence of testing, debugging, and reflective analysis within the wider dissertation or capstone report.

For supervisor review, this document is particularly useful because it shows that the repository is not only storing the final concept, but also preserving the engineering reality of building, running, observing, and diagnosing the system through iterative development.[file:146][file:148]
