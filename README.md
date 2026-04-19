# AR Navigation for RGIPT: CampusAR_BrowserPath
> Developed by Tishya Jha

An Augmented Reality (AR) pathfinding and navigation application designed specifically for the Rajiv Gandhi Institute of Petroleum Technology (RGIPT) campus. This application bridges 3D spatial mapping with real-time AR camera feeds to provide users with an intuitive, glowing path to their destination directly on their smartphone screens.

## ✨ Features
* **Real-Time AR Pathfinding:** Utilizes Unity's NavMesh system combined with ARCore to calculate and draw optimal routes on the physical ground.
* **Dynamic Indicator Path:** An emission-based Line Renderer dynamically updates as the user moves, providing a clear visual guide.
* **Top-Down Minimap:** Features an "eye-in-the-sky" render texture UI that tracks the player's real-time position within the 3D campus model.
* **Intuitive UI:** Simple destination selection menu to seamlessly trigger coordinate routing.

## 📍 Current Campus Coverage
*Note: This project is in active development. The 3D geometry scaling, occlusion mapping, and NavMesh baking have currently been updated and implemented exclusively for:*
* **Academic Block 1**
* **Academic Block 2**

*(Further buildings, roads, and hostel blocks will be integrated into the NavMesh in future updates).*

---

## 🛠️ Tech Stack
* **Game Engine:** Unity 3D (Core Built-In Render Pipeline)
* **AR Framework:** AR Foundation & Google ARCore
* **Language:** C#
* **Pathfinding:** Unity AI Navigation (NavMesh Surface)

---

## 🚀 Getting Started: How to Run Locally

If you are pulling this repository to test or contribute, please follow this strict workflow to ensure the AR packages and materials compile correctly.

### 1. Clone the Repository
Open your terminal or command prompt and run:
```bash
git clone https://github.com/TishyaJ/AR_Navigation_RGIPT.git
```

### 2. Match the Unity Version (Crucial)
To prevent the AR scripts from breaking or materials rendering as bright pink, you must use the exact Unity version this project was built on.
* Navigate inside the cloned folder to `ProjectSettings > ProjectVersion.txt`.
* Check the `m_EditorVersion` (e.g., `2022.3.15f1`).
* Open **Unity Hub**. If you do not have that exact version, go to **Installs > Install Editor** and download it before proceeding.

### 3. Open in Unity Hub
* In Unity Hub, navigate to the **Projects** tab.
* Click **Add** (or **Open**) in the top right.
* Select the root folder of the cloned repository (make sure it contains the `Assets` and `ProjectSettings` folders).
* *Note: Unity will take several minutes to open as it resolves the AR Foundation dependencies and re-bakes the NavMesh cache.*

### 4. Load the Main Scene
When the editor loads, it may display a blank grid.
* Navigate to the **Project** window at the bottom: `Assets > Scenes`.
* Double-click the primary scene file (e.g., `RGIPT_AR_Map`).
* The campus geometry, AR Origin, and UI Canvas will now populate your Hierarchy.

---

## 🧠 System Architecture & Logic

If you are reviewing the codebase, here is how the core systems interact:

* **The Brain (Pathfinding):** The RGIPT campus model acts as the environment. It utilizes a `NavMesh Surface` component to bake the walkable areas around Academic Blocks 1 and 2, ensuring paths don't route through solid walls or steep drops.
* **The Path (Visuals):** The `Indicator` object sits at the user's origin point. It utilizes a `Line Renderer` component mapped to a custom C# script. Unity's `NavMesh.CalculatePath()` computes the corners of the route, which are then passed to the Line Renderer to draw the glowing trail.
* **The Targets (Nodes):** Invisible Empty GameObjects serve as coordinate waypoints across the blocks. The UI Canvas buttons utilize `On Click()` events to pass these specific target coordinates into the navigation script, instantly updating the user's destination.

---

## 📱 Build and Deployment (Android)

Because this is an AR application, it cannot be tested directly in the Unity Editor play mode without a simulator. To test the navigation:

1. Connect your Android device to your PC via USB.
2. Ensure **Developer Options** and **USB Debugging** are enabled on your phone.
3. In Unity, go to **File > Build Settings**.
4. Verify the platform is set to **Android** (click "Switch Platform" if not).
5. Click **Build and Run**.
6. Unity will compile the project and install the `.apk` directly onto your device. Stand at the designated origin point on campus to test the AR overlay!
