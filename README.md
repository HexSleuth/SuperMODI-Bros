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
- [Controls](#-controls)
- [In-Game Level Editor & Storage](#-in-game-level-editor--storage)
- [Sprite Sheet Customization](#-sprite-sheet-customization)
- [Tech Stack](#-tech-stack)
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

```text
+-------------------------------------------------------------+
|                     Game State & Physics                    |
|        (Position, Velocity, Collision Boxes, Entities)       |
+------------------------------+------------------------------+
                               |
       +-----------------------+-----------------------+
       |                                               |
       v                                               v
+-----------------------+             +-----------------------+
|    2D Canvas Loop     |             |   Three.js 3D Scene   |
| - 256x240 buffer      |             | - Geometry Extrusion  |
| - Pixel-perfect blit  |             | - Billboard Sprites   |
| - Retro CRT feel      |             | - Dynamic Auto-Camera |
+-----------------------+             +-----------------------+
```

### 3D Auto-Camera Parameters

In 3D mode (<kbd>V</kbd>), the world is constructed as real 3D geometry. The camera adapts dynamically to maintain player focus and dramatic framing:

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

- **Virtual D-Pad:** 8-way directional touch control on the left half of the screen.
- **Action Buttons:** Dedicated on-screen **A (Jump)**, **B (Run)**, and **3D (View Toggle)** touch buttons.

---

## 🛠️ In-Game Level Editor & Storage

The integrated editor enables custom level creation without opening an IDE:

- **Grid Resolution:** `128` horizontal tiles by `15` vertical tiles.
- **Painting Tools:**
  - **Single Click:** Place individual tiles or entities.
  - **Click + Drag:** Multi-tile stroke painting for ground, platforms, or pipes.
  - **Eraser:** Clear placed blocks and objects.
- **Supported Tile Elements:**
  - Standard Bricks & Solid Ground
  - Mystery `?` Blocks (Coins & Power-ups)
  - Pipe segments (entry/exit)
  - Goombas, Koopas, and Items
- **Saving & Loading:**
  - Levels serialize directly into browser `localStorage`.
  - Levels can be tested and played instantly inside the editor preview runner.

---

## 🎨 Sprite Sheet Customization

All characters and objects can be replaced at runtime using the **Sprites / Options** drawer:

1. **Target Characters & Objects:**
   - **Hero** (`Supermodi-sprites.png` default)
   - **Goomba** (Walking / squished states)
   - **Koopa** (Walking / shell states)
   - **Mushroom** & **Coin**
2. **Configuration Settings:**
   - **Columns & Rows:** Slice cell cuts for any sprite atlas.
   - **FPS:** Adjust animation cycle speed.
   - **Scale:** Multiplier (`0.5×` to `3.0×`) applied across 2D blits and 3D billboards.
   - **Pixel Quality:** Toggle between `1×` (crisp nearest-neighbor) and `4×` (anti-aliased supersampling).
   - **360° Movement:** Debug toggle to bypass gravity and test omnidirectional flight.

> **Note on Remote Assets:** If an external sprite fails to load due to browser CORS restrictions, use the **Local file** upload option to select the image directly from your disk.

---

## 💻 Tech Stack

- **HTML5 Canvas:** 2D physics loop, AABB collision handling, and tile rendering.
- **Three.js:** Real-time 3D geometry extrusion, billboard sprite rendering, lighting, and camera math.
- **Vanilla JavaScript (ES6+):** Game loops, deterministic PRNG procedural generator, and atlas parser.
- **CSS3:** Arcade styling, responsive layouts, and virtual mobile controls.

---

## 📂 Project Structure

```text
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
```

---

## 🚀 Local Development Setup

No complex build tools, bundlers, or package installations are required. However, because Three.js texture loaders and web audio enforce browser CORS restrictions on `file:///` URLs, run a lightweight local HTTP server.

### 1. Clone the Repository

```bash
git clone https://github.com/HexSleuth/SuperMODI-Bros.git
cd SuperMODI-Bros
```

### 2. Start a Local Server

Choose any tool available on your machine:

**Python 3:**
```bash
python3 -m http.server 8000
```

**Node.js (npx):**
```bash
npx serve -l 8000 .
```

**PHP:**
```bash
php -S localhost:8000
```

### 3. Open in Browser

Visit **`http://localhost:8000`** in Chrome, Firefox, Safari, or Edge.

---

## 🗺️ Roadmap & Contributing

- [ ] Add sound effects and chiptune BGM using Web Audio API synthesis.
- [ ] Export custom levels as shareable JSON seeds/strings.
- [ ] Add underground and underwater level themes in Three.js.
- [ ] Support physical gamepads via the browser Gamepad API.

Pull requests and issues are welcome!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/NewFeature`)
3. Commit your Changes (`git commit -m 'Add NewFeature'`)
4. Push to the Branch (`git push origin feature/NewFeature`)
5. Open a Pull Request

---

## 📜 License

Distributed under the **MIT License**. See [LICENSE](LICENSE) for more information.
