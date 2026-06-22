# Testing and Observed Results

## 1. Introduction

This document records the practical testing activities carried out on the Capstone_VREdu project and compares the intended behaviour of the system with the outputs observed during execution. It should be read alongside the project overview, technical explanation, installation guide, and development log in order to present a complete account of both the designed functionality and the issues encountered during implementation and runtime evaluation.

The purpose of this document is not only to describe what the system is supposed to do, but also to show how it behaved when tested through actual user interaction. In an academic context, this is important because software quality cannot be judged solely from architecture or intended design; it must also be assessed through direct execution and observation.

## 2. Testing Context

The application is documented as a Windows-targeted Unity 2022.3 LTS project using keyboard and mouse input. Its intended flow begins in the authentication scene, continues to the classroom scene with eight interactive algorithm stations, and ends in a summary scene that reports learner progress and reflection prompts.

Testing was therefore carried out with this expected flow in mind. The practical goal was to verify whether a user could enter the project, reach the classroom, begin interacting with algorithm stations, follow the displayed keyboard instructions, complete algorithm tasks, trigger flashcards, and finally obtain a valid end-of-session summary.

## 3. Intended Testable Behaviour

The supplied documentation defines several behaviours that can be tested directly during runtime:

- The learner should be able to move in first-person mode within the classroom using keyboard and mouse controls.
- When near a station, the learner should see a prompt and press `E` to enter the station.
- Each station should display a readable algorithm panel, a visual array, and the current instruction state.
- Keyboard shortcuts should allow the learner to perform algorithm-specific actions such as swapping, shifting, marking minima, selecting search directions, or declaring a target found.
- Correct completion should trigger flashcard interaction and later contribute to the session summary.
- The summary scene should report attempted algorithms, levels reached, flashcard performance, and learner profile information.

These expectations formed the basis for the observed-results analysis below.

## 4. Input and Interaction Coverage

The project includes a well-defined input scheme for both classroom movement and station interaction. Free-roam movement is assigned to `W`, `A`, `S`, `D`, arrow keys, mouse look, and sprint input, while station entry and pause behaviour are mapped to `E` and `Escape` respectively.

Inside stations, the application uses a shared set of action keys such as `S`, `K`, `D`, `M`, `F`, `N`, `H`, and `R`, with their meanings changing depending on the currently active algorithm. Flashcard interaction is also documented through dedicated keys such as `V`, `C`, `I`, and `X`.

From a testing perspective, this means the system is highly dependent on readable instructions and correct input-state handling. If the interface is not visually clear, then even a correct key mapping does not guarantee a usable learning experience.

## 5. Station-Level Test Expectations

The internal explanation file provides a structured description of what each station should do when tested. Sorting stations are intended to guide the learner through adjacent comparisons, minimum selection, insertion shifts, partition placement, or merge decisions, depending on the algorithm. Searching stations are intended to guide the learner through sequential scanning, binary halving, or ternary third-selection.

Each algorithm also includes three levels with increasing complexity, and the testing expectation is that successful completion of one stage leads to a flashcard phase and eventually level progression. This creates a testable loop of action, feedback, reinforcement, and progression.

## 6. Observed Runtime Results

During practical execution, the project did not consistently achieve the intended station presentation or flow. Instead of a stable and clearly readable algorithm-learning interface, testing revealed that visual output in the classroom and at specific stations could become disrupted by overlapping text objects and cluttered display elements, making the intended station instructions difficult to read.

A further observed issue was that some text appeared blurred or unclear during use. Since the project relies heavily on text to communicate algorithm instructions, key mappings, level context, and feedback, this had a direct impact on usability. In practical terms, even where interaction logic may have been partially active, the readability problem prevented confident and reliable user testing.

## 7. Observed Results by Functional Area

### 7.1 Authentication and scene loading

The documented scene sequence implies that authentication should lead into the classroom and eventually into the session summary.[file:92][file:93] At a high level, the project could be launched and run far enough to reach classroom and completion-related states, indicating that scene transitions were not universally failing.

However, successful scene entry alone did not confirm that the educational functionality was working correctly. The more significant problems appeared once the user attempted to interact with station content and later review the resulting session output.

### 7.2 Station interaction

The expected station interaction model is clear in the internal explanation: approach station, press `E`, begin Level 1, act using keyboard shortcuts, receive hints, and move forward after correct completion.[file:93] In observed testing, however, the station interface did not remain sufficiently clear and stable to confirm that this cycle was functioning properly end to end.

The presence of overlapping text and obstructive visual elements reduced the reliability of station testing. Because the learner must read station instructions in order to apply the correct keys, this visual breakdown affected not only presentation quality but also the ability to validate the algorithm-learning workflow itself.

### 7.3 Feedback and hinting

The documented system includes an adaptive feedback pipeline in which actions are logged, evaluated against mistake rules, and translated into escalating hints.This is one of the most important functional claims of the project because it underpins the pedagogical argument for adaptive learning support.

During the observed tests, the main difficulty was not proving the internal concept wrong, but confirming its behaviour in practice under visually broken station conditions. Since station readability was compromised, it became difficult to verify whether feedback was appearing in a pedagogically meaningful way or whether learners could interpret it correctly in context.

### 7.4 Flashcards

Flashcards are intended to appear after level completion and to influence both progression and summary statistics. The documentation also states that flashcard answers should be recorded and reused later in the session summary.

In the observed test outcomes, the final summary displayed zero attempted flashcards, which suggests that the flashcard stage either did not trigger correctly, did not register user activity, or failed to store the results in the expected session data structure. This weakens the evidence that the reinforcement mechanism currently operates correctly across the full learner journey.

### 7.5 Session summary

According to the project overview, the summary screen should display algorithms attempted, levels reached, steps taken, mistakes made, hints used, flashcard scores, learner strengths and weaknesses, and reflection questions. The technical explanation similarly describes `SessionData` as a persistent in-memory object that accumulates records throughout the user’s activity and is then interpreted by the summary controller.

The observed result, however, was a summary screen that reported no attempted algorithms and zero flashcard activity despite the fact that the session had entered a completion state. This indicates a breakdown either in session recording, event timing, or summary rendering logic, and it represents one of the clearest mismatches between intended design and observed behaviour.

## 8. Comparison of Intended and Observed Outcomes

| Functional area | Intended behaviour | Observed result |
|---|---|---|
| Scene flow | Login should lead to classroom and then to a meaningful session summary. | Scene access occurred, but later outputs did not reliably reflect meaningful recorded activity. |
| Station display | Stations should show readable instructional text, array elements, and current level information. | Visual overlap and blurred text reduced readability and obstructed interaction. |
| Keyboard interaction | Learners should use documented keys to carry out algorithm-specific steps. | Input mappings existed in documentation, but practical use was weakened by poor station readability. |
| Flashcards | Level completion should trigger flashcard interaction and contribute to progression and summary statistics. | Final summary suggested that flashcard attempts were not being captured correctly. |
| Session summary | End-of-session report should show algorithms attempted, performance indicators, and reflection prompts. | Summary displayed a largely empty or contradictory result state, including no attempted algorithms. |

## 9. Testing Interpretation

The testing outcomes suggest that the project currently demonstrates partial operational success at the level of structure and scene access, but not full functional success at the level of educational interaction flow. In other words, the application can be opened and navigated to some extent, yet this does not automatically mean that its core pedagogical loop is working correctly in practice.

The most important interpretation is that usability and data integrity issues are closely linked in this project. Visual overlap and blurred instructional content prevent confident use of the algorithm stations, while missing or contradictory summary data prevents the project from proving that user activity has been captured and interpreted correctly.

## 10. Limitations of the Current Test Evidence

The current evidence is based on observed runtime behaviour during hands-on testing rather than automated test suites. This means the findings are especially useful for usability, integration, and workflow evaluation, but less precise for isolating the exact internal source of each defect.

Even so, the observed results are academically valuable because they reveal the practical gap between specification and execution. In educational software, such gaps are highly significant because the success of the system depends not only on underlying code structure but on whether the learner can actually read, interpret, and complete the intended tasks.

## 11. Priority Areas for Retesting

Based on the observed results, future retesting should focus on the following priorities:

1. **Station rendering clarity** – verify that boards, prompts, and array labels render once only and remain readable.
2. **Text quality** – verify that instructional and interface text remains sharp and legible in the classroom and summary scenes.
3. **End-to-end progression** – confirm that station completion truly triggers flashcards, level advancement, and session recording.
4. **Summary integrity** – confirm that attempted algorithms, flashcard activity, and mistake data are preserved and displayed correctly.
5. **Interaction consistency** – confirm that documented key mappings behave correctly for each algorithm station.

## 12. Conclusion of Testing Record

This testing record shows that the project contains a well-documented intended interaction model, but the observed results indicate unresolved issues in rendering, workflow completion, and session reporting. The project therefore demonstrates clear progress in system design and implementation, but it also requires further integration testing before it can fully support the learning experience described in the earlier documentation.
