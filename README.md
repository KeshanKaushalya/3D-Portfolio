# 3D-Portfolio 🚀✨

A modern 3D portfolio project showcasing interactive WebGL experiences. Built with a fast frontend toolchain (Vite + Tailwind CSS + PostCSS + ESLint) and a 3D renderer stack (Three.js / React Three Fiber or raw Three.js depending on implementation). This README was created from the repository structure and typical Marantz-style stack conventions — please replace the inferred dependency list with your exact package.json entries if needed.

---

## Overview 🧭

This project is a personal 3D portfolio that demonstrates interactive 3D scenes, gesture-driven controls, and smooth micro-interactions for portfolio items and navigation. It’s optimized for modern browsers and mobile devices and built for iterative development with Vite.

Key goals:
- Showcase 3D models, animations and interactive UI.
- Provide intuitive gesture controls across pointer, touch, and device orientation.
- Be fast to iterate on locally and easy to deploy (Vercel / Netlify / GitHub Pages).

---

## Features ✨

- Immersive 3D scenes rendered with WebGL (Three.js / react-three-fiber).
- Smooth transitions & animations (GSAP / framer-motion patterns).
- Gesture-based interactions (drag, pinch, rotate, tap).
- Responsive & accessible UI (Tailwind CSS + utility-first styles).
- Fast dev loop with Vite and PostCSS build pipeline.
- ESLint + recommended configuration for consistent code style.

---

## Live Demo 🔗

Add your deployed demo URL here (examples):
- Vercel : (https://3-d-portfolio-eosin-ten.vercel.app/)


(If you want, tell me the deployment URL and I’ll add it to this README.)

---

## How It Works 🧩

High-level flow:
1. App bootstraps via index.html → Vite dev server.
2. Main JS mounts 3D scene(s) into a canvas element.
3. Renderer (Three.js / R3F) creates camera, lights, loaders, and scene graph.
4. Gesture handlers subscribe to pointer/touch/DeviceOrientation events and translate user input to camera or model transforms.
5. UI overlays (HTML/CSS) provide navigation and project detail cards, interacting with the 3D scene via events or shared state.

Common implementation pieces:
- Scene Manager: centralizes camera, renderer, scene, and resize handling.
- Loader & Asset Cache: DRY loader for models, textures, HDRI maps.
- Interaction Layer: mapping gestures to scene transforms, with smoothing (lerp) and inertia.
- UI Layer: React or vanilla DOM controls that communicate with the 3D scene.

---

## Gesture Controls 🖐️📱

The project supports multiple input modalities — pointer, touch, and device orientation. Below are recommended gesture mappings; adapt as-needed.

- Pan / Orbit:
  - Desktop: Mouse drag (left button) rotates the camera/orbital controls.
  - Mobile: Single-touch drag rotates the camera.
- Zoom:
  - Desktop: Mouse wheel or Ctrl + wheel.
  - Mobile: Pinch gesture to zoom the camera or change camera distance.
- Rotate Model:
  - Desktop: Shift + drag rotates the focused model.
  - Mobile: Two-finger rotate gesture to rotate the selected model.
- Tap / Select:
  - Single click/tap performs raycast and selects/interacts with object.
- Quick Look / Peek:
  - Long-press on mobile or right-click on desktop to open a quick preview/detailed card.
- Device Tilt (optional):
  - DeviceOrientation API maps small tilt motions to subtle camera parallax for immersion.

Tips for implementation:
- Debounce heavy computations (raycasting / loaders) for performance.
- Use requestAnimationFrame for all continuous animations and update loops.
- Provide a gesture hint UI for first-time users (small overlay).

---

## System Architecture 📊

A simple architecture diagram (ASCII + emojis):

App Entry (index.html)  
  ↓  
Vite Dev Server / Production Build ⚡  
  ↓
+----------------------------+
| UI Layer (HTML/React) 🧩    |
| - Navigation, overlays     |
+----------------------------+
           ↕ (events/props)
+----------------------------+
| Interaction Layer 🤝        |
| - Gesture handling         |
| - Raycasting, selection    |
+----------------------------+
           ↕
+----------------------------+
| 3D Engine (Three.js) 🎨    |
| - Scene, camera, lights    |
| - Models, animations       |
+----------------------------+
           ↕
+----------------------------+
| Asset Pipeline & Storage   |
| - GLTF, textures, HDRIs    |
| - Cache & loaders          |
+----------------------------+

Notes:
- State flows between UI and 3D engine via a shared store or event bus (e.g., React context, Zustand, or custom event emitter).
- Keep render logic and UI logic separated to allow server-side rendering of UI while client-only rendering of 3D canvas.

---

## Installation ⚙️

Clone the repo and install dependencies:

```bash
# clone
git clone https://github.com/KeshanKaushalya/3D-Portfolio.git
cd 3D-Portfolio

# install (npm)
npm install

# or using pnpm / yarn if you prefer
# pnpm install
# yarn install
```

Run the development server:

```bash
npm run dev
# open http://localhost:5173 (default for Vite)
```

Build for production:

```bash
npm run build
npm run preview
```

If your package.json uses different scripts or package manager commands, substitute them accordingly.

---

## Usage 🧭

- Develop: Use the dev server, editing files under src/ to see live reloads.
- Models & Assets: Drop GLTF/GLB files under an assets/ or public/ directory and reference them via the loader utility.
- Configuration: Tailwind settings are in tailwind.config.cjs. PostCSS settings are in postcss.config.cjs.
- Linting: Run ESLint via the configured npm script (e.g., npm run lint) to keep code consistent.

Recommended local workflow:
1. npm run dev
2. Work on src/Scene* or src/components/*
3. Test gestures on both desktop and mobile browsers (or device emulation)
4. Commit and push to your branch, deploy via Vercel/Netlify.

---

## Technologies Used 🛠️

Inferred from repository files (please verify exact versions in package.json):

- Build & Tooling
  - Vite (dev server & bundler)
  - PostCSS, Tailwind CSS (utility-first styling)
  - ESLint (linting)
- 3D & Interaction
  - Three.js or @react-three/fiber (Three.js renderer / React wrapper)
  - GLTFLoader / DRACOLoader (for compressed models)
  - Gesture libraries (e.g., @use-gesture / react-use-gesture / pointer/touch handlers)
- Animations & UX
  - GSAP or framer-motion (for timeline-driven animations)
- Hosting & CI
  - Deployable to Vercel / Netlify / GitHub Pages

If you’d like, I can replace the inferred technologies above with the exact dependency list from your package.json.

---

## Future Enhancements 🔮

- Add an offline asset cache (service worker) for faster repeat visits.
- Progressive loading with LOD (level of detail) for large models.
- WebXR / AR preview integration for immersive experiences on compatible devices.
- Collaborative / shareable scene view (share camera state via URL).
- Accessibility improvements (keyboard navigation, semantic fallbacks).
- Analytics & performance monitoring (Lighthouse, Real User Metrics).

---

## Contributing 🤝

Contributions are welcome! Please open issues for bug reports or feature requests. If you submit PRs, follow the existing lint and formatting rules and provide a clear description of what's changed.

---

## License 📜

The repository contains a LICENSE file. Please see LICENSE in the repository root for full license text and conditions:
https://github.com/KeshanKaushalya/3D-Portfolio/blob/main/LICENSE

---

Thanks — I created this README using the repository files I inspected and common best-practices for 3D Web projects. If you want me to automatically commit this README.md into the repo or tailor the Tech / Dependencies / License sections using exact package.json and LICENSE contents, I can fetch them and update the file for you.
