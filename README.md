# VR-Based Virtual Museum

A Unity project for immersive virtual reality museum exploration. It presents a modeled gallery with cultural exhibits, exhibit information, and XR interaction components, using Unity's OpenXR and XR Interaction Toolkit packages.

## Table of Contents

- [Project Introduction](#project-introduction)
- [Project Objectives](#project-objectives)
- [Technologies Used](#technologies-used)
- [Features and Functionalities](#features-and-functionalities)
- [VR Interaction Details](#vr-interaction-details)
- [Project Architecture and Folder Structure](#project-architecture-and-folder-structure)
- [Unity Installation and Setup](#unity-installation-and-setup)
- [How to Run the Project](#how-to-run-the-project)
- [Application Workflow](#application-workflow)
- [Screenshots](#screenshots)
- [Future Enhancements](#future-enhancements)
- [Conclusion](#conclusion)
- [GitHub Repository](#github-repository)

## Project Introduction

A virtual museum presents exhibits in a digital gallery that visitors can explore from a first-person perspective. Virtual reality can add a sense of spatial presence and support direct interaction with objects, making digital museum visits useful for education and cultural exploration.

This project is developed in Unity and includes a museum scene with Ancient and Modern gallery areas, 3D exhibit objects, labels, and information panels. It also includes XR Interaction Toolkit sample scenes and assets that demonstrate XR interaction patterns.

## Project Objectives

- Develop an immersive virtual museum environment.
- Enable interactive exploration of virtual exhibits.
- Provide an engaging educational experience through exhibit labels and information panels.
- Demonstrate practical use of Unity, OpenXR, and XR interaction components.

## Technologies Used

Versions are taken from `Packages/manifest.json` and `ProjectSettings/ProjectVersion.txt`.

| Technology | Version/configuration | Project use |
| --- | --- | --- |
| Unity Editor | 6000.3.21f1 | Project authoring and runtime |
| Universal Render Pipeline (URP) | 17.3.0 | Rendering pipeline |
| XR Interaction Toolkit | 3.5.1 | XR interactors, interactables, and interaction systems |
| OpenXR | 1.17.1 | XR runtime integration |
| XR Plug-in Management | 4.6.0 | XR loader configuration |
| Input System | 1.20.0 | Input actions and device input support |
| XR Hands | 1.8.1 | XR hand package and included sample assets |
| AR Foundation | 6.5.0 | Installed XR/AR framework dependency |
| Meta OpenXR | 2.5.1 | Meta OpenXR features |
| Android XR OpenXR | 1.3.1 | Android XR OpenXR package support |
| XR Core Utilities | 2.6.0 | Shared XR utilities |
| glTFast | 6.20.0 | GLB/glTF model import support |
| TextMesh Pro | Included through Unity packages/assets | Scene text and UI |

The saved OpenXR configuration enables Meta Quest support and the Meta Quest Touch Plus controller profile for Android. Android minimum and target SDK values are both 34. These settings indicate a Quest-oriented Android OpenXR configuration; this repository does not include headset test results or guarantee compatibility with a particular device model.

## Features and Functionalities

| Feature | Evidence in the project |
| --- | --- |
| Museum environment | `Assets/Scenes/MuseumScene.unity` contains a modeled gallery with Ancient and Modern areas, entrance, walls, floor, and lighting. |
| 3D exhibits | Scene objects include an ancient vase/vessel, ancient painting, and modern artwork. The project also includes Egyptian artifact models, a Tutankhamun model, and a lion statue. |
| Exhibit information | The museum scene contains exhibit labels and information-panel text, including panels for the Ancient and Modern galleries. |
| XR scene setup | The museum scene contains an XR Origin Hands rig and an XR Interaction Manager. OpenXR loaders and project-level XR settings are included. |
| Object interaction | The museum scene contains XR Grab Interactable components. XR Interaction Toolkit sample content includes ray and poke interaction examples. |
| User interface | TextMesh Pro, exhibit information panels, and XR Toolkit sample coaching/tutorial UI are present. |
| Teleportation setup | A teleport area is present, but its saved Teleportation Provider reference is unassigned. Functional teleport locomotion is therefore not confirmed. |

There are no project-specific C# files in `Assets/Scripts`. The C# components under `Assets/VRTemplateAssets/Scripts` and `Assets/Samples` belong to included template or sample content.

## VR Interaction Details

- **XR viewpoint and rig:** `MuseumScene.unity` includes an XR Origin Hands rig, which provides the scene's XR origin setup.
- **Interactable exhibits:** XR Grab Interactable components are serialized in the museum scene. Actual controller or hand input behavior depends on the active interactor and input bindings.
- **Sample interactions:** The separate `SampleScene.unity` contains XR Interaction Toolkit tutorial content and ray/poke interaction examples. These are sample functionality and should not be confused with custom museum scripts.
- **Locomotion limitation:** A teleport area exists, but the museum scene's Teleportation Provider field is null. Assign and verify a provider and input bindings before treating teleportation as a working navigation feature.
- **Device configuration:** OpenXR settings include Meta Quest support and a Quest Touch Plus controller profile for Android. The project does not document a tested headset/controller matrix.

## Project Architecture and Folder Structure

```text
VR-Virtual-Museum/
├── Assets/
│   ├── Scenes/                 # MuseumScene, SampleScene, and BasicScene
│   ├── Models/                 # Museum models, including GLB assets
│   ├── Materials/              # Museum and scene materials
│   ├── Textures/               # Model and environment textures
│   ├── VRTemplateAssets/       # XR template scripts, prefabs, materials, and UI
│   ├── Samples/                # Imported XR Hands and XR Interaction Toolkit samples
│   ├── XR/                     # OpenXR settings and loader assets
│   ├── XRI/                    # XR Interaction Toolkit settings assets
│   ├── UI/                     # UI assets
│   └── ...                     # Other imported exhibit and environment assets
├── Packages/
│   ├── manifest.json           # Direct Unity package dependencies
│   └── packages-lock.json      # Resolved package versions
├── ProjectSettings/            # Unity version, build scenes, platform, and XR settings
├── Screenshots/                # Genuine screenshots can be added here
└── README.md
```

The workspace also has top-level `Assets/Scripts`, `Assets/Prefab`, and `Assets/Audio` directories, but those directories are currently empty; Git does not retain empty directories in a clone. Museum prefabs and scripts that are present are organized under `Assets/VRTemplateAssets` and `Assets/Samples`.

### Included scenes

- `Assets/Scenes/MuseumScene.unity` — modeled museum gallery and exhibits.
- `Assets/Scenes/SampleScene.unity` — XR Interaction Toolkit sample/tutorial scene.
- `Assets/Scenes/BasicScene.unity` — basic scene containing an XR Origin and XR Interaction Manager.

`ProjectSettings/EditorBuildSettings.asset` currently enables only `SampleScene.unity`. The museum scene must be added and enabled in the build scene list to launch it from a player build.

## Unity Installation and Setup

### Requirements

- Unity Hub.
- Unity Editor **6000.3.21f1**, matching `ProjectSettings/ProjectVersion.txt`.
- For Android headset builds: Android Build Support, including Android SDK, NDK, and OpenJDK modules.
- A VR headset and OpenXR runtime compatible with the selected build configuration for physical-device use. Device compatibility is not validated in this repository.

### Setup steps

1. Clone the repository:

   ```bash
   git clone https://github.com/jalagam-saineha/VR-Virtual-Museum.git
   ```

2. In Unity Hub, choose **Add project from disk** and select the cloned `VR-Virtual-Museum` folder. It contains `Assets`, `Packages`, and `ProjectSettings` and is the Unity project root.
3. Open it with Unity **6000.3.21f1**. Allow Unity Package Manager to resolve dependencies and Unity to import the assets. The first import may take several minutes.
4. Open `Assets/Scenes/MuseumScene.unity` from the Project window to inspect the museum scene.
5. For an Android OpenXR headset, install Android Build Support and select the Android platform in **File > Build Profiles**. In **Project Settings > XR Plug-in Management**, review the Android OpenXR loader and Meta Quest feature/controller profile settings.
6. Add `Assets/Scenes/MuseumScene.unity` to the Build Profile scene list, enable it, and move it to the first position if it should launch first. The current project build settings launch `SampleScene.unity` instead.
7. Review the XR Origin, interaction bindings, and locomotion setup for the intended device. Configure the unassigned Teleportation Provider if teleportation is required.

The Android project settings specify minimum SDK 34 and target SDK 34. Confirm those platform requirements and the headset's OpenXR runtime against the intended deployment device before building.

## How to Run the Project

### Inspect or run from the Unity Editor

1. Open `Assets/Scenes/MuseumScene.unity`.
2. Connect and enable a compatible XR headset/runtime, and confirm the XR Plug-in Management and input configuration for the active platform.
3. Enter Play mode. For this scene, verify the XR Origin Hands rig and interaction bindings are active. The repository does not document a tested editor/headset configuration.

### Build for an Android OpenXR headset

1. In **File > Build Profiles**, select Android and install any requested build modules.
2. Add and enable `MuseumScene.unity` in the scene list, placing it first. `SampleScene.unity` is the only scene enabled by the checked-in build settings.
3. Confirm the Android OpenXR loader, Meta Quest settings if applicable, controller/input mappings, and any required locomotion provider.
4. Connect the headset with its OpenXR runtime ready, then use the Build Profile's build/deploy option to install and launch the application.

## Application Workflow

1. The user launches the museum scene in the Editor or from a build configured to start with `MuseumScene.unity`.
2. The XR Origin Hands rig supplies the scene's XR viewpoint and interaction context.
3. The user explores the Ancient and Modern gallery areas and views the exhibit models, labels, and information panels.
4. The XR Grab Interactable components can be used through compatible, configured interactors. The precise controls depend on the selected device and input bindings.
5. Teleport navigation requires a Teleportation Provider and input bindings to be configured and verified; those references are not complete in the saved museum scene.

A build using the current checked-in scene list starts in the XR Toolkit sample/tutorial scene rather than the museum. Configure the scene list as described above for a museum-first build.

## Screenshots

No genuine application screenshots were found in the project. The image under `Assets/Images` is a museum reference image, not a screenshot of this application, and is not presented as one.

Capture real views from the running museum scene and save them under `Screenshots/`, for example `Screenshots/museum-gallery.png`. Then add them here using Markdown:

```markdown
![Museum gallery view](Screenshots/museum-gallery.png)
```

Do not use reference art or mockups as application screenshots. The `Screenshots/` folder includes a short capture guide.

## Future Enhancements

- Add more curated exhibits and gallery environments.
- Complete and validate teleport locomotion and device-specific input bindings.
- Add exhibit-specific audio guides.
- Expand information panels with historical context, citations, and accessible text.
- Add guided tours and visitor navigation aids.
- Capture genuine screenshots and document tested headset/runtime combinations.

## Conclusion

The VR-Based Virtual Museum combines a modeled gallery, cultural exhibits, and Unity XR components to demonstrate how virtual reality can support interactive educational exploration. The existing scene and XR configuration provide a foundation for further exhibit development, interaction setup, and device testing.

## GitHub Repository

[https://github.com/jalagam-saineha/VR-Virtual-Museum](https://github.com/jalagam-saineha/VR-Virtual-Museum)
