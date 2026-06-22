# Installation and Setup

## 1. Introduction

This document explains how to configure, open, run, and build the Capstone_VREdu project in Unity. It is based on the project’s internal setup documentation and is intended to provide a clear academic record of the environment requirements, first-time import process, scene preparation steps, runtime workflow, and known setup-related issues.[file:94]

The setup process is an important part of the project documentation because the system depends on a specific Unity version, automatic package resolution, and a set of one-time editor utilities that prepare the scenes before the project can be tested consistently.[file:94]

## 2. Prerequisites

Before opening the project, the following software should be installed on the development machine:[file:94]

- **Unity Hub** (latest available version).  
- **Unity Editor 2022.3 LTS**, preferably version `2022.3.62f1` or another compatible `2022.3.x` patch release.  
- **Windows Build Support (IL2CPP)**, required for producing a Windows build.  
- **Visual Studio 2022** or **Visual Studio Code** for inspecting and editing C# scripts.[file:94]

The project is designed for Windows PC and uses keyboard and mouse input rather than requiring a dedicated VR headset.[file:92][file:94]

## 3. Importing the Project

The project should be imported through Unity Hub by selecting the repository root folder rather than a subfolder. The selected folder must contain the `Assets`, `Packages`, and `ProjectSettings` directories, because these define the Unity project structure.[file:94]

When the project is opened for the first time, Unity may take several minutes to import assets, compile scripts, and generate the local `Library` cache. If the editor displays compile warnings or prompts such as Safe Mode during this first import, the recommended approach is to allow package resolution and resource import to complete before assuming that the project is broken.[file:94]

## 4. Package Resolution

Package installation is handled automatically through the Unity package manifest. According to the supplied setup documentation, the main dependencies include the New Input System, TextMesh Pro, and Visual Studio integration packages, which Unity resolves from `Packages/manifest.json` without requiring manual installation.[file:94]

If package retrieval fails, the recommended recovery step is to verify internet connectivity and refresh the package list through the Unity Package Manager. This ensures that editor-side dependencies are aligned with the version expected by the project.[file:94]

## 5. Scene Preparation

A first-time import requires the scenes to be wired using the project’s editor setup utilities. The internal documentation states that these utilities should be run in sequence for the authentication scene, the classroom scene, and the summary scene.[file:94]

The expected order is as follows:[file:94]

1. Open `01_Auth.unity` and run `VREdu → Setup → Auth Scene`.  
2. Open `02_Classroom.unity` and run the setup commands for all eight stations, classroom UI, station repositioning, flashcard linking, and flashcard content creation.  
3. Open `03_Summary.unity` and run `VREdu → Setup → Summary Scene`.  
4. Run `VREdu → Utility → Remove Missing Scripts`.  
5. Save all scenes after setup changes are applied.[file:94]

The provided notes state that these utilities are idempotent, meaning that re-running them should update existing objects rather than duplicate them. This is significant because it reduces the risk of accidental duplication during repeated setup attempts.[file:94]

## 6. Running the Project in Unity

The recommended way to run the project is to start from the authentication scene so that the full user flow can be tested from login through to the classroom. In this path, the user opens `01_Auth.unity`, enters Play mode, authenticates, and is then taken automatically to the classroom scene.[file:94][file:93]

An alternative approach is to begin directly from `02_Classroom.unity`, although the documentation notes that the `GameManager` may redirect the user back to authentication if no current user session has been established. This means the full-flow route is generally better when testing the intended learner journey.[file:94]

During Play mode, the cursor is locked for first-person navigation. Pressing `Escape` opens the pause menu and unlocks the cursor for UI interaction.[file:94]

## 7. Optional LLM Configuration

The project includes an optional LLM-backed support component. To use it, the user is expected to obtain an OpenAI API key, start the project, open the in-game Settings panel, paste the key into the provided field, and save it before asking questions through the world-space learner support panel near a station.[file:94]

This feature is optional rather than mandatory. The internal documentation explicitly states that the rest of the application should remain operational even when no API key has been configured, in which case the support panel returns a default message instead of a contextual response.[file:92][file:93][file:94]

## 8. Building for Windows

To produce a Windows executable, the project must be configured in Unity’s Build Settings. The documented build sequence requires the three scenes to be included in the build in the following order: `01_Auth.unity`, `02_Classroom.unity`, and `03_Summary.unity`.[file:94]

The platform should be set to **Windows, Mac, Linux**, the architecture should be `x86_64`, and the user can optionally enable **Development Build** if debug information and profiling support are required. Once the build is created, the output `.exe` can be launched as a standalone version of the application.[file:94]

## 9. Known Setup Issues

The setup documentation records several recurring issues that may occur during import, configuration, or early execution. These are important to preserve in academic documentation because they show practical constraints encountered during project deployment rather than only ideal intended behaviour.[file:94]

The reported setup-side issues include:[file:94]

- Compile errors during the first import while packages are still resolving.  
- Missing TextMesh Pro essentials, which can cause UI text to render incorrectly.  
- Input System conflicts if the project is not configured to use the new Input System.  
- Missing script references in scenes or prefabs.  
- Apparent keyboard failure when the Game view does not have focus.  
- Build failures caused by missing IL2CPP support in Unity Hub.[file:94]

## 10. Common Fixes

The internal setup notes provide direct remedies for the most common issues:[file:94]

- Wait for package import to finish fully before responding to early compile errors.  
- Import TMP Essential Resources if TextMesh Pro requests them or if text materials appear incorrect.  
- Set **Active Input Handling** to **Input System Package (New)** when Unity reports an input conflict.  
- Use `VREdu → Utility → Remove Missing Scripts` when missing script references appear in the Inspector.  
- Click inside the Game view before testing station keyboard input.  
- Ensure Windows Build Support (IL2CPP) is installed if the Windows build process fails.[file:94]

These remedies are important because they indicate that some observed failures may arise from editor configuration rather than from faults in the application logic itself.[file:94]

## 11. Project Folder Reference

The internal installation guide also identifies the main project-level folders, which is useful for orienting developers and supervisors reviewing the repository:[file:94]

- `Assets/` – game content and source code.  
- `Packages/` – Unity package manifest and resolved package references.  
- `ProjectSettings/` – Unity editor and project configuration.  
- `Library/` – auto-generated cache, not intended for manual editing or version control.  
- `Logs/` – Unity editor logs.  
- `UserSettings/` – local editor preferences not intended for commit.[file:94]

The same guide also recognises the three original internal documentation files: `readme.txt`, `explanation.txt`, and `installation-steps.txt`, which together form the source basis for the formal markdown documentation now being added to the repository.[file:94]

## 12. Documentation Role

This installation and setup guide should be read together with the project overview and technical explanation documents. While the overview explains the purpose of the system and the technical explanation describes how the internal architecture is intended to work, the present document records how the project is actually opened, configured, and run in practice.[file:92][file:93][file:94]

For dissertation and supervisor review purposes, this is important because it demonstrates not only what the project is intended to do, but also what is required to reproduce the environment in which development and testing took place.[file:147][file:148]
