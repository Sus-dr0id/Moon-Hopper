# Moon Hopper 

**A torch-based group exploration experience for the National Space Centre's Outer Solar System Gallery.**

Built with **Three.js** and designed to simulate the NSC video wall (4:1 aspect ratio), Moon Hopper invites visitors to explore the surface of Jupiter's moon Callisto — discovering hidden scientific phenomena by shining a virtual torch across a dark, cratered landscape.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technologies](#technologies)
- [How to Run](#how-to-run)
- [Game Flow](#game-flow)
- [Controls](#controls)
- [Project Structure](#project-structure)
- [Callisto — Scientific Context](#callisto--scientific-context)
- [Credits](#credits)

---

## Overview

Moon Hopper is a browser-based 3D exploration game developed for the **National Space Centre** as part of the CO2108 Concurrent Design module. The game is set in the Outer Solar System Gallery and focuses on Callisto, one of Jupiter's four Galilean moons.

Players use a mouse-as-torch spotlight mechanic and WASD movement to traverse Callisto's ancient surface, uncovering five scientific discoveries hidden in the terrain. Each discovery triggers a character popup featuring real astronauts and astrobiologists who share educational facts about the moon.

---

## Features

- **Torch-based exploration** — Mouse controls a spotlight that reveals hidden discovery objects on the terrain
- **WASD movement** — Slow, bouncing camera movement simulating an astronaut walking in low gravity
- **Planet hub selection screen** — Hover-to-unlock lock screen with hand-drawn planet illustrations alongside each planet name
- **Jupiter moon hub** — Secondary hub for selecting individual moons to explore
- **Cinematic cutscene** — Fly-through travel sequence from Jupiter to Callisto
- **5 interactive discoveries** — Subsurface Ocean, Ancient Impact Crater, Silicate Rock Deposits, Carbon Dioxide Exosphere, Organic Compounds
- **Astronaut character popups** — Dr. Louisa Preston (Astrobiologist) and Neil Armstrong deliver science facts in speech bubbles
- **Mission Complete celebration** — Summary screen with astronaut cards after all five discoveries are found
- **Procedural terrain** — Crater-pocked landscape generated with noise functions
- **Atmospheric effects** — Floating dust particles, fog, Jupiter in the sky, starfields

---

## Technologies

| Technology | Purpose |
|---|---|
| **Three.js** (r128) | 3D rendering engine — scenes, cameras, lighting, geometry |
| **WebXR** | Extended reality framework (Three.js WebXR compatible) |
| **HTML5 / CSS3** | UI overlays, transitions, popups, responsive layout |
| **JavaScript (ES6)** | Game logic, state management, animation loop |
| **Google Fonts** | Outfit + Space Mono typefaces |

### Three.js Features Used

- `THREE.PerspectiveCamera` — Multiple cameras for hub, cutscene, and exploration scenes
- `THREE.SpotLight` — Torch spotlight mechanic with shadow mapping
- `THREE.Raycaster` — Mouse-to-terrain intersection for torch targeting
- `THREE.PlaneGeometry` — Procedurally deformed terrain with craters
- `THREE.FogExp2` — Atmospheric depth fog
- `THREE.BufferGeometry` — Custom starfields and dust particle systems
- `THREE.MeshStandardMaterial` — PBR materials with emissive properties for discoveries
- `THREE.SphereGeometry` — Planets, moons, Jupiter sky object
- Shadow mapping via `THREE.PCFSoftShadowMap`
- `THREE.ACESFilmicToneMapping` — Cinematic colour grading

---

## How to Run

Moon Hopper is a single self-contained HTML file with no build step required.

### Option 1 — Open directly
```
Open MoonHopper.html in any modern browser (Chrome, Firefox, Edge, Safari)
```

### Option 2 — Local server (recommended for WebXR)
```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx http-server .

# Then open http://localhost:8000/MoonHopper.html
```

### Option 3 — VS Code Live Server
Right-click `MoonHopper.html` → **Open with Live Server**

### Requirements

- Modern browser with WebGL support
- No external dependencies — Three.js is loaded via CDN
- All images (planet illustrations, astronaut portraits) are embedded as base64 data URIs

---

## Game Flow

```
Title Screen
    │
    ▼
Planet Hub (Outer Planets)
    │  Hover to unlock planets, click Jupiter
    ▼
Jupiter Moon Hub
    │  Select Callisto
    ▼
Cutscene (Travel to Callisto)
    │
    ▼
Exploration (Callisto Surface)
    │  Use WASD to move, mouse torch to find 5 discoveries
    │  Click lit discoveries to reveal astronaut popups
    ▼
Mission Complete (Celebration)
    │
    ▼
Return to Moon Hub
```

---

## Controls

| Input | Action |
|---|---|
| **Mouse** | Aim torch / spotlight |
| **W** | Move forward |
| **A** | Move left |
| **S** | Move backward |
| **D** | Move right |
| **Click** | Interact with lit discoveries / dismiss popups |

Movement is deliberately slow with a bouncing animation to simulate an astronaut walking in Callisto's low-gravity environment (0.126 g).

---

## Project Structure

```
MoonHopper.html        — Complete self-contained game (single file)
README.md              — This file
png/                   — Source planet illustration assets
  ├── jupiter.png
  ├── saturn.png
  ├── uranus.png
  ├── neptune.png
  ├── callistio.png
  ├── erpa.png
  └── lo.png
```

### Scenes

| Scene | Description |
|---|---|
| **Hub Scene** | 4 outer planets (Jupiter, Saturn, Uranus, Neptune) with orbital motion |
| **Moon Hub Scene** | Jupiter's moons (Callisto, Ganymede, Europa, Io) with Jupiter backdrop |
| **Cutscene Scene** | Fly-through from deep space towards Jupiter |
| **Exploration Scene** | Callisto surface with terrain, torch, dust, discoveries |

### Game States

`TITLE` → `HUB` → `MOON_HUB` → `CUTSCENE` → `EXPLORATION` → `ASTRONAUT_POPUP` → `CELEBRATION`

---

## Callisto — Scientific Context

Callisto is Jupiter's second largest moon and the third largest moon in our solar system, discovered on 7 January 1610 by Galileo Galilei. Key scientific facts incorporated into the game:

- **Namesake** — Named for a woman turned into a bear by Zeus in Greek mythology
- **Potential for Life** — May harbour a salty subsurface ocean interacting with rock ~155 miles beneath the surface; oxygen detected in the exosphere
- **Size** — Almost as big as Mercury, with a circumference of ~9,410 miles (15,144 km)
- **Orbit** — Takes ~17 Earth days to orbit Jupiter; tidally locked (same side always faces Jupiter); orbits ~1,170,000 miles from Jupiter
- **Surface** — Oldest and most heavily cratered surface in the solar system (~4 billion years old); little to no geologic activity
- **Atmosphere** — Very thin carbon dioxide exosphere detected by the Galileo spacecraft in 1997
- **Structure** — Icy surface with possible interior layers of ice mixed with rock and metal

---

## Credits

- **Game Development** — Three.js, HTML5, CSS3, JavaScript
- **Planet Illustrations** — Hand-drawn artwork (embedded with transparent backgrounds)
- **Astronaut Characters** — Dr. Louisa Preston (Astrobiologist, UCL) and Neil Armstrong (Commander, Apollo 11)
- **Scientific Data** — NASA / JPL Callisto fact sheet
- **Fonts** — [Outfit](https://fonts.google.com/specimen/Outfit) and [Space Mono](https://fonts.google.com/specimen/Space+Mono) via Google Fonts
- **3D Engine** — [Three.js](https://threejs.org/) r128

---

*Prototype — Simulating NSC Video Wall (4:1)*
