# SuperMODI-Bros 🍄🇮🇳

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![GitHub Pages](https://img.shields.io/badge/Demo-GitHub%20Pages-brightgreen)](https://hexsleuth.github.io/SuperMODI-Bros/)
[![Three.js](https://img.shields.io/badge/3D%20Engine-Three.js-black?logo=three.js)](https://threejs.org/)
[![HTML5 Canvas](https://img.shields.io/badge/Render-HTML5%20Canvas%202D-orange?logo=html5)](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)

> A hybrid retro platformer combining a 2D HTML5 Canvas physics engine with dynamic real-time Three.js 3D extrusion, deterministic procedural level generation, a full-featured level editor, custom sprite mapping, and the **Super Modi Animated FX Runner**.

🎮 **Live Demo:** [https://hexsleuth.github.io/SuperMODI-Bros/](https://hexsleuth.github.io/SuperMODI-Bros/)

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Core Features](#-core-features)
- [Rendering Architecture & 3D Auto-Camera](#-rendering-architecture--3d-auto-camera)
- [Game Mechanics & FX Runner](#-game-mechanics--fx-runner)
- [Controls](#-controls)
- [In-Game Level Editor & Storage](#-in-game-level-editor--storage)
- [Sprite Sheet Customization](#-sprite-sheet-customization)
- [Project Structure](#-project-structure)
- [Local Development Setup](#-local-development-setup)
- [Roadmap & Contributing](#-roadmap--contributing)
- [License](#-license)

---

## 📖 Overview

**SuperMODI-Bros** bridges nostalgic 8-bit platforming with modern browser-based graphics programming. Players can seamlessly swap between standard 2D side-scrolling and full 3D perspectives on the fly. 

The game contains 32 procedural stages spanning 8 distinct worlds, culminating in classic castle finish lines, accompanied by custom sprite animation support, touch input emulation, and an integrated level-authoring sandbox.

---

## ✨ Core Features

- **Dual-Engine Rendering:** Instant toggling between 2D HTML5 Canvas pixel rendering and Three.js 3D scene geometry.
- **Dynamic 3D Camera System:** Real-time auto-panning camera tracking player velocity, jump trajectory, screen aspect ratio, and level bounds.
- **Deterministic Procedural World Generation:** 8 worlds with 4 levels each (32 stages total). Each level derives from a fixed pseudorandom seed, ensuring predictable layouts and shareable seeds.
- **Super Modi Animated FX Runner:** Standalone FX canvas overlay featuring customized animations, score multipliers, double-jump spin moves, and responsive particle effects.
- **Built-in 128×15 Level Editor:** Browser-based tile builder with multi-tile brushes, terrain painting, enemy placement, and local persistence.
- **Universal Custom Sprite Sheets:** Custom grid slicer allowing users to swap Hero, Goomba, Koopa, Mushroom, and Coin art via URL or local file upload.
- **Cross-Platform Input:** Simultaneous support for physical keyboards, virtual touch D-pads, and action buttons.

---

## 📐 Rendering Architecture & 3D Auto-Camera


+-------------------------------------------------------------+
|                     Game State & Physics                    |
|        (Position, Velocity, Collision Boxes, Entities)       |
+------------------------------+------------------------------+
|
+------------------+------------------+
|                                     |
v                                     v
+-----------------------+             +-----------------------+
|    2D Canvas Loop     |             |   Three.js 3D Scene   |
| - 256x240 buffer      |             | - Geometry Extrusion  |
| - Pixel-perfect blit  |             | - Billboard Sprites   |
| - Retro CRT feel      |             | - Dynamic Auto-Camera |
+-----------------------+             +-----------------------+

### 3D Auto-Camera Parameters

In 3D mode (`V`), the world is constructed as real 3D geometry. The camera adapts dynamically to maintain player focus and dramatic framing:

| Parameter | Default Value | Description |
| :--- | :--- | :--- |
| **Pitch / Tilt** | `16°` | Downward angle toward the ground plane |
| **Yaw / Orbit** | `15°` | Horizontal offset producing depth parallax |
| **Field of View (FOV)** | `55°` | View frustum angle; broadens during high speed |
| **Distance** | `11 units` | Base distance behind the character |
| **Height Offset** | `1.5×` | Vertical elevation offset relative to hero height |
| **Aspect Adapt** | Auto | Re-centers frustum based on mobile vs. ultra-wide ratios |

---

## 🕹️ Controls

### Keyboard Navigation

| Action | Primary Key | Secondary / Alternative |
| :--- | :--- | :--- |
| **Move Left / Right** | <kbd>←</kbd> / <kbd>→</kbd> | <kbd>A</kbd> / <kbd>D</kbd> |
| **Crouch** | <kbd>↓</kbd> | <kbd>S</kbd> |
| **Jump** | <kbd>Space</kbd> | <kbd>Z</kbd> / <kbd>↑</kbd> / <kbd>W</kbd> |
| **Double-Jump Spin** | <kbd>Space</kbd> *(in air)* | <kbd>W</kbd> *(in air)* |
| **Run / Dash** | <kbd>X</kbd> | <kbd>Shift</kbd> |
| **Toggle 2D / 3D** | <kbd>V</kbd> | — |
| **Pause Game** | <kbd>P</kbd> | — |
| **Restart Level** | <kbd>R</kbd> | — |
| **Start / Confirm** | <kbd>Enter</kbd> | — |
| **Exit Overlay / FX** | <kbd>Esc</kbd> | — |

### Mobile / Touch Controls
- **Virtual D-Pad:** 8-way directional touch control on the left screen half.
- **Action Buttons:** Dedicated on-screen **A (Jump)**, **B (Run)**, and **3D (View Toggle)** buttons.

---

## 🛠️ In-Game Level Editor & Storage

The integrated editor enables level creation without opening an IDE or modifying code:

- **Grid Resolution:** `128` horizontal tiles by `15` vertical tiles.
- **Painting Tools:**
  - **Single Click:** Place a selected tile or entity.
  - **Click + Drag:** Multi-tile stroke painting for ground, platforms, or pipes.
  - **Eraser:** Clear placed blocks and objects.
- **Supported Tile Elements:**
  - Standard Bricks & Solid Ground
  - Mystery `?` Blocks (Coins & Power-ups)
  - Pipe segments (entry/exit)
  - Goombas, Koopas, and Items
- **Saving & Loading:**
  - Levels can be named and serialized into browser `localStorage`.
  - Levels can be exported, reloaded, and played directly inside the test runner.

---

## 🎨 Sprite Sheet Customization

All characters and objects can be replaced at runtime using the **Sprites / Options** drawer:

1. **Target Characters:**
   - **Hero** (`Supermodi-sprites.png` by default)
   - **Goomba** (Walking / squished states)
   - **Koopa** (Walking / shell states)
   - **Mushroom** & **Coin**
2. **Configuration Settings:**
   - **Columns & Rows:** Defines cell cuts for the sprite atlas grid.
   - **FPS:** Controls animation cycle playback rate.
   - **Scale:** Multiplier (`0.5×` to `3.0×`) applied across both 2D blits and 3D billboards.
   - **Pixel Quality:** Toggle between `1×` (crisp retro nearest-neighbor) and `4×` (anti-aliased supersampling).
   - **360° Movement:** Optional toggle to bypass gravity and test flight mechanics.

> **Note on Remote Assets:** If a remote sprite image fails due to browser CORS headers, use the **Local file** upload option to load images directly from disk.

---

## 📂 Project Structure

``text
SuperMODI-Bros/
│
├── index.html                 # Main markup, canvas viewports & UI controls
├── Supermodi-sprites.png      # Default hero sprite sheet
│
├── css/
│   └── styles.css             # Arcade UI, responsive layout, virtual D-pad
│
└── js/
    ├── main.js                # App lifecycle, state coordinator & input router
    ├── engine2d.js            # 2D canvas renderer, physics & AABB collisions
    ├── engine3d.js            # Three.js scene, geometry generation & camera math
    ├── procedural.js          # Seed-based world/level generator (Worlds 1-8)
    ├── editor.js              # 128x15 tile editor, brush tools & persistence
    └── sprites.js             # Sprite sheet slicing, atlas parser & animations

---
## 🛠️ Tech Stack
- **HTML5 Canvas** – 2D physics loop, collision handling, and tile rendering.
- **Three.js** – Real-time 3D geometry extrusion, billboard sprite rendering, lighting, and camera tracking.
- **Vanilla JavaScript (ES6+)** – Deterministic procedural generation, game loop, sprite sheet slicing, and local state persistence.
- **CSS3** – Responsive retro arcade UI and virtual controls.
---
## 🚀 Getting Started
**🚀 Local Development Setup**
​No build tools, compilation, or package installations are necessary. However, because Three.js texture loaders and web audio enforce CORS restrictions on file:/// URLs, run a lightweight local web server.
No build step or Node.js environment is required—this project runs directly in any modern web browser.
### Clone and Run Locally
1. **Clone the repository:**
   ```bash
   git clone [https://github.com/HexSleuth/SuperMODI-Bros.git](https://github.com/HexSleuth/SuperMODI-Bros.git)
   cd SuperMODI-Bros

2. **Serve the project:**
Because sprite loading and Three.js textures may be subject to browser CORS policies, serve the files with a local HTTP server:
Using Python 3:
``bash
python3 -m http.server 8000

**Or using Node (npx):
``bash
npx serve -l 8080 .

3.**Using PHP:**
php -S localhost:8080

3.**Open in browser:**
Navigate to http://localhost:8000 in your web browser.
---
## 🎨 Custom Sprites
​You can customize character and enemy appearances via the in-game settings panel:
​Upload any sprite sheet via image URL or local file upload.
​Adjust Columns, Rows, and FPS to match your sprite layout.
​In 3D mode, sprites automatically convert into camera-facing 3D billboards.
---
## 🤝 Contributing
​Contributions, bug reports, and level design submissions are welcome!
​Fork the Project
​Create your Feature Branch (git checkout -b feature/NewFeature)
​Commit your Changes (git commit -m 'Add some NewFeature')
​Push to the Branch (git push origin feature/NewFeature)
​Open a Pull Request
---
## Open in Browser
​Visit http://localhost:8080 in Chrome, Firefox, Safari, or Edge.
**​🗺️ Roadmap & Contributing**
​[ ] Add sound effects and chiptune BGM using Web Audio API synthesis.
​[ ] Export custom levels as shareable JSON seeds/strings.
​[ ] Add underground and underwater level themes in Three.js.
​[ ] Support custom gamepad/controller mapping via the Gamepad API.
​Pull requests and issues are welcome! Feel free to fork the repository, create feature branches, and submit PRs.
---
## ​📜 License
​Distributed under the MIT License.
<ElicitationsGroup message="To tailor this README further:">
  <Elicitation label="Add Web Audio API BGM & SFX implementation roadmap" query="Draft a detailed Web Audio API chiptune audio architecture section to include in the SuperMODI-Bros README."/>
  <Elicitation label="Create a GitHub Actions deployment workflow" query="Create a GitHub Actions workflow YAML file to automatically deploy SuperMODI-Bros to GitHub Pages on push."/>
  <Elicitation label="Generate a detailed CONTRIBUTING.md file" query="Generate a complete CONTRIBUTING.md file for the SuperMODI-Bros repository with PR guidelines and coding standards."/>
</ElicitationsGroup>
---
