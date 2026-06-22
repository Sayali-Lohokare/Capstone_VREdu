# Conclusion and Next Steps

## 1. Summary of the Project

Capstone_VREdu is designed as a Unity-based virtual classroom in which learners practise core searching and sorting algorithms via direct interaction with 3D visualisations. The system combines algorithm stations, adaptive feedback, flashcard reinforcement, and an optional LLM-backed support panel into a single environment intended to promote active, step-by-step learning rather than passive observation.

From a software engineering perspective, the project demonstrates a modular architecture built around scene management, station abstraction, feedback pipelines, flashcard decks, session tracking, and optional external integration. The documentation and repository structure show a clear attempt to separate responsibilities between user interface, educational logic, data models, and configuration assets.

## 2. Achievements

Several important achievements are evident from the current state of the project and its documentation:

- A coherent high-level design has been defined, including authentication, classroom, and summary scenes, and a clear flow between them. 
- Eight algorithm stations have been specified with individual rules, level configurations, and mistake taxonomies, covering both sorting and searching algorithms. 
- An adaptive feedback pipeline and Bloom-tagged flashcard system have been designed to respond to specific mistake types and to support progressive cognitive depth. 
- A session data model has been implemented to aggregate algorithm attempts, hint usage, and flashcard results for later summary and reflection. 
- An optional LLM service layer has been introduced to provide contextual natural language support without making the core system dependent on external connectivity.

These achievements confirm that the project has moved beyond a simple prototype and into a structured educational application with a clearly articulated pedagogical rationale.

## 3. Limitations and Unresolved Issues

At the same time, the development log and testing record show that the current implementation does not yet fully realise the intended learner experience. The most significant limitations include:

- **Visual presentation problems**: station boards and text can become cluttered by overlapping objects, and some text appears blurred or difficult to read, reducing the clarity of instructions and feedback.  
- **Incomplete station usability**: although keyboard mappings are carefully defined, their practical value is reduced when the learner cannot reliably see which state the station is in or what the next expected action is.  
- **Flashcard and progression inconsistencies**: the final summary has reported zero algorithms and flashcards attempted even after a session has been completed, suggesting that parts of the progression and data recording pipeline are not yet functioning as intended. 
- **Summary accuracy concerns**: the summary scene currently fails to present the rich analytics and learner profile information described in the design, which undermines the project’s ability to evidence learning outcomes.

These limitations do not invalidate the project, but they do show that further integration and debugging work is required before the application can be considered ready for deployment in a teaching context.

## 4. Reflection on the Development Process

The documentation now present in the repository — including the overview, technical explanation, installation guide, development log, and testing record — reveals that the project has been approached with an emphasis on clarity, modularity, and educational alignment. However, it also shows that the process has involved substantial trial and error, particularly during scene setup, runtime evaluation, and analysis of conflicting outputs.

From a reflective academic standpoint, the most important lesson is that well-specified architecture and detailed text documentation are necessary but not sufficient. For an educational system, reliable end-to-end behaviour, readable interfaces, and trustworthy summary data are equally critical, and these aspects can only be evaluated through systematic testing and iterative debugging.

## 5. Recommended Technical Next Steps

The following technical actions are recommended as priorities for future work:

1. **Stabilise station rendering**  
   - Review the station prefabs, canvas layers, and text components to remove duplicated or misaligned objects.  
   - Simplify the station canvas hierarchy where necessary to ensure that each board renders only one set of text and that overlays such as hints and prompts are correctly z-ordered.

2. **Clarify text and UI styling**  
   - Verify font assignments, TextMesh Pro material settings, and canvas scaling to eliminate blurred or unreadable text.  
   - Ensure that all instructional text, key prompts, and algorithm descriptions are legible at the expected screen resolutions and in both classroom and summary scenes.

3. **Verify the action–feedback–flashcard pipeline**  
   - Test individual stations to confirm that action logging, mistake classification, and hint presentation operate consistently.  
   - Confirm that level completion reliably triggers flashcards and that flashcard results are written back into the session data model.

4. **Repair session recording and summary reporting**  
   - Instrument the `SessionData` and summary controller to ensure that algorithms attempted, levels reached, and flashcard statistics are correctly accumulated and displayed.  
   - Add temporary debug output if needed to trace where information is lost between station interaction and summary rendering.

5. **Retest the full learner journey**  
   - After the above fixes, perform end-to-end tests from login through classroom interaction to summary, using multiple stations and levels.  
   - Compare the observed summary results with the known sequence of learner actions to confirm that the system now provides an accurate reflection of activity.

## 6. Recommended Research and Evaluation Steps

Beyond technical fixes, the project also presents opportunities for future research and evaluation:

- **Pedagogical effectiveness**: once the implementation is stable, the system could be evaluated with students to measure its impact on understanding of searching and sorting algorithms compared to more traditional teaching methods.  
- **Feedback and difficulty tuning**: the adaptive feedback thresholds and level configurations could be adjusted based on empirical data to identify which combinations of hints and difficulty transitions are most beneficial for different learner profiles.  
- **LLM support analysis**: the optional LLM integration provides a natural point for studying whether contextual question-answering improves learner confidence or conceptual understanding, and under what conditions it is most effective.

These lines of investigation would allow the project to evolve from a purely technical artefact into a contribution to educational research.

## 7. Role of the Repository Documentation

The sequence of documentation files in the `docs` folder now tells a coherent story: what the project is intended to do, how it is built, how it is set up, what went wrong during development, and what was observed during testing. This satisfies the requirement for a transparent and evidence-based record of the capstone project’s lifecycle, including both achievements and limitations.

From a dissertation perspective, this set of documents can be referenced directly in the methods, implementation, evaluation, and reflection chapters, demonstrating that the project has been approached with both engineering discipline and critical awareness.

## 8. Final Remarks

In its current form, Capstone_VREdu represents a substantial piece of system design and implementation work that is closely aligned with the learning objectives of teaching algorithms in an interactive environment. While the project still requires technical refinement to fully realise its potential, the underlying architecture, documentation, and reflective analysis provide a strong foundation for continued development and formal academic reporting.[file:92][file:93][file:94]
