# Technical Explanation

## 1. Overview of System Architecture

Capstone_VREdu is implemented as a scene-based Unity application with clearly separated responsibilities for authentication, classroom interaction, and session summarisation. The high-level architecture consists of:

- **Scene management and session control**, implemented through a central `GameManager` and a persistent `SessionData` object.  
- **Classroom interaction systems**, including the first-person controller, station navigation, and algorithm-specific logic.  
- **Feedback and adaptation systems**, which monitor learner actions, classify mistakes, and generate hints.  
- **Reinforcement and reflection systems**, including flashcards and summary reporting.  
- **Optional LLM integration**, which provides contextual natural language support without being required for the core application to function.[file:92][file:93]

The intention is that each subsystem can be reasoned about independently, while still contributing to a coherent end-to-end learning experience.

## 2. Scene Flow and Control Logic

### 2.1 Scene roles

The project uses three primary Unity scenes, each with a distinct responsibility:[file:92][file:93]

- `01_Auth.unity` – authentication and account management.  
- `02_Classroom.unity` – main virtual classroom with all algorithm stations.  
- `03_Summary.unity` – session summary and learner reflection screen.  

The `GameManager` singleton is responsible for loading these scenes in the correct order and maintaining continuity between them via `SessionData`.[file:93]

### 2.2 Startup and authentication flow

When the application starts, the `GameManager` loads `01_Auth`. Learners can either register a new account or log in using existing details. Credentials are stored as hashed JSON in `users.json` in the application’s persistent data path, and a “remember me” preference can be stored in `PlayerPrefs` for convenience.[file:93]

On successful login, the `GameManager` instructs Unity to load `02_Classroom`, and the current user is stored in `SessionData` so that subsequent activity can be associated with the correct profile.[file:93]

### 2.3 Classroom flow

In `02_Classroom`, the learner controls a first-person character using the Input System. When approaching an algorithm station, a world-space prompt appears inviting the learner to press the interaction key (for example, `E`) to begin.[file:93]

Pressing the interaction key locks movement, activates the chosen station, and initialises the first level for the corresponding algorithm. From this point onward, station-specific scripts govern input handling, array visualisation, feedback, and progression logic.[file:93]

### 2.4 Ending the session

At any point, the learner can exit via the pause menu. When the session is ended, `GameManager` triggers loading of `03_Summary`, where the accumulated `SessionData` is read and displayed. After reviewing the summary, the learner can close the application or return to the authentication stage.[file:93]

## 3. Algorithm Station Design

### 3.1 Station structure

Each algorithm station is implemented as a specialised concrete class derived from a common `AlgorithmStation` base. The base class provides shared functionality such as level initialisation, array construction, input routing, event wiring, and integration with the feedback pipeline.[file:93]

Concrete station implementations encapsulate algorithm-specific logic, including:

- Definition of valid actions for each algorithm step.  
- Mapping from keyboard input to those actions.  
- Algorithm-specific mistake rules.  
- Customised messages for hint and instruction text.[file:93]

### 3.2 Array visualisation

The `ArrayVisualizer` component owns the 3D representation of the array for a station. It supports the following operations:[file:93]

- `BuildArray(values[])` to create or reuse `ArrayElement` instances.  
- `AnimateSwap(i, j)` for swap animations.  
- `AnimateShift(i, j)` for insertion-style shifts.  
- `HighlightElement(i, state)` to set element visual states such as Default, Selected, Comparing, Sorted, Found, Pivot, or Minimum.  

These functions provide a consistent visual language across all stations, meaning that the same visual cues apply to multiple algorithms.

### 3.3 Input handling

Input handling is abstracted through an interaction layer that maps key presses to high-level actions such as “swap elements”, “select minimum”, or “move search boundary”. This abstraction ensures that the station logic does not depend directly on physical keys and can be updated or remapped without rewriting algorithm rules.[file:93]

## 4. Feedback and Adaptive Difficulty

### 4.1 Action logging

Every learner action within a station is passed to an `ActionLogger`, which records the indices involved, the values of the elements affected, and the time step at which the action occurred. Each logged action triggers an event that the feedback system listens to.[file:93]

### 4.2 Mistake classification

The `FeedbackManager` subscribes to the `ActionLogger` events and acts as the central component for evaluating correctness. For each logged action, the `FeedbackManager` calls the algorithm-specific mistake rules through the `IMistakeRule` interface.[file:93]

If the action is correct, the manager updates internal counters and may reset hint severity. If the action is incorrect, the manager identifies a particular mistake type based on a taxonomy of more than twenty-five mistake codes, each prefixed by an algorithm identifier (for example, `BS_` for Bubble Sort or `BNS_` for Binary Search).[file:93]

### 4.3 Hint generation

Mistake counts are tracked per type. Hints have three severity levels:

1. **Level 1 – Nudge**: a light reminder that explains the rule conceptually.  
2. **Level 2 – Worked example**: a more concrete explanation often including example values.  
3. **Level 3 – Direct lesson**: a detailed, step-by-step explanation of what should have been done.[file:93]

The `FeedbackManager` escalates from Level 1 to Level 3 when repeated mistakes occur without correction, and it resets to Level 1 once the learner performs a correct step. Cooldown parameters, maximum severity, and allowed mistake counts are controlled by the level configuration for each algorithm.[file:93]

The `HintPanelController` listens to feedback events and displays the current hint as a world-space UI element near the station, ensuring that guidance is visible without leaving the algorithm context.[file:93]

### 4.4 Adaptive difficulty settings

Adaptive behaviour is configured through fields in the `LevelConfig` assets:[file:93]

- `hintCooldown`: time before another automatic hint is allowed.  
- `maxHintSeverity`: highest hint level available at that stage.  
- `mistakeFailThreshold`: threshold beyond which the level is repeated.  
- `adaptiveDifficulty`: flag indicating whether hint intervals shrink as mistakes increase.  

By tuning these parameters, the system can make lower levels supportive and forgiving while higher levels are more demanding and require greater independence from the learner.

## 5. Level System and Progression

Each algorithm is associated with three `LevelConfig` scriptable objects, representing levels 1, 2, and 3.[file:93]

### 5.1 Level parameters

The main parameters include:

- Minimum and maximum array size.  
- Value ranges used for array elements.  
- Hint and mistake thresholds.  
- Flags controlling whether adaptive difficulty is enabled.[file:93]

### 5.2 Level events

The `LevelManager` component emits events such as `OnLevelAdvanced` and `OnAllLevelsComplete`. Stations respond to these events by animating transitions, resetting arrays, or closing the station and returning the learner to free movement in the classroom.[file:93]

### 5.3 Progression criteria

Progression from one level to the next depends on two broad criteria:

- The learner completes the algorithm with an acceptable number of mistakes as determined by the level configuration.  
- The learner achieves a satisfactory score on the subsequent flashcard quiz, typically exceeding a specified pass rate.[file:93]

If the flashcard performance falls below the threshold, the level is repeated even if the algorithm steps were technically correct. This arrangement encourages both procedural correctness and conceptual understanding.

## 6. Flashcard System

### 6.1 Flashcard decks

Each algorithm has an associated `FlashcardDeck` with multiple `FlashcardData` entries. Cards are annotated with Bloom’s Taxonomy levels, ranging from Remember to Create, so that the cognitive difficulty of questions can be controlled and varied.[file:93]

### 6.2 Card selection logic

When a level is completed, the `FlashcardController` selects a small number of cards, biasing the selection towards topics associated with the mistake types observed most frequently for that learner. For example, repeated errors in Bubble Sort swap conditions trigger cards that specifically target that concept.[file:93]

### 6.3 Interaction pattern

During the quiz, the learner can:

- View the question on a card.  
- Choose to reveal the answer.  
- Mark their response as correct or incorrect (for example, using dedicated keys such as `C` and `I`).[file:93]

These responses are recorded in `SessionData`, enabling later analysis of which concepts remain difficult for a given learner.

## 7. Session Tracking and Summary

### 7.1 SessionData structure

`SessionData` is a `DontDestroyOnLoad` singleton that persists across scenes. For each algorithm station the learner visits, an `AlgorithmAttempt` record is created. Each record typically includes:[file:93]

- Algorithm identifier and levels attempted.  
- Number and type of mistakes.  
- Hint counts and peak severity levels.  
- Flashcard performance per level.  
- Timing and step counts.  

These records are appended throughout the learner’s session.

### 7.2 Persistence and lifetime

`SessionData` exists only in memory during a single run of the application. It is used to populate the summary screen and is discarded once the application is closed. Long-term storage of user accounts relies on JSON files, while preferences such as API keys or volume levels are stored via `PlayerPrefs`.[file:93]

### 7.3 Summary scene behaviour

In `03_Summary`, the `SessionSummaryController` reads `SessionData` and:

- Aggregates statistics across algorithms and levels.  
- Generates textual descriptions of learner strengths and weaknesses based on mistake patterns.  
- Displays flashcard performance and hint usage.  
- Provides short reflection prompts for the learner to complete.[file:92][file:93]

The summary is intended to support both self-reflection and tutor-led discussion.

## 8. LLM Integration

### 8.1 LLM panel design

The project design includes an LLM-based support panel managed by `LLMPanelController`. This controller provides a world-space input field where the learner can type free-form questions while working at a station.[file:93]

### 8.2 Service abstraction

The LLM integration is abstracted behind an `ILLMService` interface. There are currently two implementations:[file:93]

- `OpenAIService`, which sends the learner’s question, the current algorithm name, and recent mistake type to an OpenAI model via `UnityWebRequest`.  
- `NullLLMService`, which returns a default message asking the learner to configure an API key when no external service is available.[file:93][file:94]

This design ensures that the rest of the application does not depend directly on the availability of an external LLM.

### 8.3 Configuration and dependency

The LLM feature is configured at runtime through a settings panel where an API key can be entered and stored. The application is designed to be fully usable without this component; if no key is provided, the panel is still present but only returns the default explanatory response.[file:94]

## 9. Data and Preference Management

The system uses a combination of JSON and `PlayerPrefs` for persistence:[file:93]

- **`users.json`** – stores registered accounts with hashed passwords, located in the platform’s persistent data directory.  
- **`auth_remember_user`** – PlayerPrefs key storing the last logged-in username for convenience.  
- **`llm_api_key`** – PlayerPrefs key storing the LLM API key if provided.  
- **`sfx_volume`** – PlayerPrefs key storing the master sound effects volume.  

Session-level analytics are kept in memory and used only for generating the summary.

## 10. Technical Rationale

The chosen architecture reflects several software engineering considerations:

- **Modularity** – algorithms, feedback rules, flashcard content, and LLM integration are separated into distinct components and scriptable assets.  
- **Extensibility** – new algorithms or additional stations can be added by implementing new station classes and associated configuration without changing the core pipeline.  
- **Testability** – the separation of scene flow, station logic, and data models supports targeted testing of each layer.  
- **Pedagogical alignment** – technical design decisions (such as action logging and Bloom-tagged flashcards) are directly motivated by educational goals.[file:92][file:93]

This technical explanation should be read together with the project overview and subsequent documentation (installation instructions, development logs, and issue analyses) to provide a complete picture of how the system is intended to operate.
