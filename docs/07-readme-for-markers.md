# Readme for Markers and Supervisors

## 1. Purpose of this Repository

This repository contains the code and documentation for the Capstone_VREdu project, a Unity-based educational application designed to teach searching and sorting algorithms in an interactive 3D classroom environment. The code base is accompanied by a structured set of markdown documents that explain the system’s design, setup, development process, testing activities, and conclusions.

The aim of this document is to orient markers and supervisors so that they can quickly find the most relevant information for assessment without needing to navigate the full project tree manually.

## 2. Recommended Reading Order

The documentation in the `docs/` folder is organised as a numbered sequence. The intended reading order is:

1. **02-technical-explanation.md** – Detailed description of how the system is designed to work internally, including scene flow, algorithm stations, feedback pipeline, flashcards, session data, and LLM integration.
2. **03-installation-and-setup.md** – Practical steps for importing the Unity project, configuring required packages, running editor setup utilities, building the application, and resolving common setup issues.  
3. **04-development-log-and-issues.md** – Narrative of the development process with particular emphasis on setup problems, visual failures (such as overlapping text and blurred UI), and inconsistencies between intended and observed behaviour.  
4. **05-testing-and-observed-results.md** – Summary of the testing activities carried out, comparing expected functionality with actual outputs and highlighting the impact of current defects on the learner experience.  
5. **06-conclusion-and-next-steps.md** – Overall reflection on achievements, limitations, and priority areas for future work, including both technical and pedagogical recommendations.

The root-level `README.md` provides a concise public overview of the project; the numbered documents in `docs/` provide the more detailed academic narrative that supports the dissertation.

## 3. How to Run the Project

Markers who wish to run the application are advised to consult **03-installation-and-setup.md** before opening the Unity project.[file:94] That document explains:

- The required Unity version and modules.  
- How to add the project in Unity Hub and open it correctly.  
- The one-shot setup menu items that must be run for each scene.  
- How to run the project in Play mode from the authentication scene.  
- How to build a Windows executable.  
- Common issues (for example, TextMesh Pro resource import, input system configuration, missing scripts) and their documented fixes.[file:94]

Because the project depends on these setup steps, running the editor without reference to this guide may lead to misleading errors or partially configured scenes.

## 4. How to Interpret the Current State

The internal documents present two complementary perspectives:

- **Intended architecture and behaviour** – as described in the overview, technical explanation, and installation guide.[file:92][file:93][file:94]  
- **Observed runtime behaviour** – as described in the development log and testing record, including evidence that some aspects of the implementation (notably visual clarity, flashcard flow, and summary statistics) do not yet fully match the intended design.

This distinction is deliberate. The repository is meant to show both the conceptual design of the system and the practical difficulties encountered when implementing and testing it within the constraints of the project timeframe.

## 5. Key Files and Folders

For quick reference:

- **Root level**  
  - `README.md` – Short summary of Capstone_VREdu.  
  - `overlap.png` – Example screenshot showing overlapping station text.

- **docs/**  
  - `02-technical-explanation.md`  
  - `03-installation-and-setup.md`  
  - `04-development-log-and-issues.md`  
  - `05-testing-and-observed-results.md`  
  - `06-conclusion-and-next-steps.md`  
  - `07-readme-for-markers.md` (this document)

- **Assets/_Project/** (in the Unity project)  
  - `Scenes/` – Contains `01_Auth.unity`, `02_Classroom.unity`, and `03_Summary.unity`.  
  - `Scripts/` – Contains code for core systems, stations, flashcards, LLM services, and session management.

## 6. Assessment Notes

When assessing this project, it may be helpful to consider:

- The **breadth and coherence of the system design**, including the combination of algorithms, feedback mechanisms, flashcards, and optional LLM support.
- The **documentation quality**, which aims to provide a transparent account of the system’s architecture, setup, development challenges, and testing outcomes.  
- The distinction between **conceptual completeness** and **implementation completeness**: certain features are fully specified and partially implemented, but known defects currently prevent the application from functioning exactly as intended in all scenarios.

The documentation is deliberately explicit about these limitations so that the project can be evaluated fairly in terms of both what has been achieved and what remains to be done.

## 7. Contact and Support

Any questions about how to navigate the repository, run the project, or interpret the documentation can be directed to the student during supervision or viva. The documents in `docs/` are intended to act as a self-contained guide for markers, but they can also be used as supporting material for more detailed discussion during assessment.
