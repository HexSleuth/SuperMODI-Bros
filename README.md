# SuperMODI-Bros 🍄🇮🇳
A retro side-scrolling platformer blending classic 2D HTML5 Canvas physics with full real-time 3D Three.js rendering, procedural level generation, a built-in tile editor, and custom sprite support.
🎮 **[Play Live Demo](https://hexsleuth.github.io/SuperMODI-Bros/)**
---
## 🌟 Highlights & Features
- **Dual Render Modes (2D Canvas & 3D Three.js):** Switch instantly between classic retro 2D pixel-art and dynamic 3D geometric views at the press of a key (`V`).
- **Dynamic 3D Camera System:** Responsive camera tracks player speed, jump height, viewport aspect ratio, and level boundaries with real-time pitch, yaw, and FOV adjustments.
- **32 Seeded Procedural Stages:** Play across 8 worlds (4 levels each), ending at the castle. Every stage is deterministically generated from fixed seeds—ensuring consistent, shareable gameplay.
- **Super Modi Animated FX Runner:** Special effect overlay featuring custom animations, particle effects, score multipliers, and dynamic sprite detection.
- **In-Browser Level Editor:**
  - Full-featured 128×15 grid canvas.
  - Paint and erase blocks, mystery boxes, coins, and enemies.
  - Save and load custom stages locally.
- **Custom Sprite Sheet Loader:** Load your own character, enemy (Goomba, Koopa), and item sprites with configurable column/row grids and FPS playback.
- **Mobile & Touch Support:** On-screen virtual D-pad and action buttons for touchscreen play.
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
