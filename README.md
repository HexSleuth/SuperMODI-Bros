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


---
## 🎮 Controls
### Desktop Keyboard

| Action | Primary Key | Alternate Keys |
| :--- | :--- | :--- |
| **Move Left / Right** | <kbd>←</kbd> / <kbd>→</kbd> | <kbd>A</kbd> / <kbd>D</kbd> |
| **Crouch** | <kbd>↓</kbd> | <kbd>S</kbd> |
| **Jump / Double-Jump Spin** | <kbd>Space</kbd> | <kbd>Z</kbd> / <kbd>↑</kbd> / <kbd>W</kbd> |
| **Run / Dash** | <kbd>X</kbd> | <kbd>Shift</kbd> |
| **Toggle 2D / 3D** | <kbd>V</kbd> | — |
| **Pause** | <kbd>P</kbd> | — |
| **Restart Level** | <kbd>R</kbd> | — |
| **Start / Confirm** | <kbd>Enter</kbd> | — |
| **Exit Overlay / FX** | <kbd>Esc</kbd> | — |

---
## 🛠️ Tech Stack
- **HTML5 Canvas** – 2D physics loop, collision handling, and tile rendering.
- **Three.js** – Real-time 3D geometry extrusion, billboard sprite rendering, lighting, and camera tracking.
- **Vanilla JavaScript (ES6+)** – Deterministic procedural generation, game loop, sprite sheet slicing, and local state persistence.
- **CSS3** – Responsive retro arcade UI and virtual controls.
---
## 🚀 Getting Started
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
npx serve .
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
## ​📜 License
​Distributed under the MIT License.
---
