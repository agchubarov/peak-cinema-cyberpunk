# A Very Simple Cyberpunk-Style Particle Interface

> **An interactive Web-based Augmented Reality experience, controlled by hand gestures and rendered with ~12,000 high-performance particles.**

## About the Project

This project is a **Single-File** application that combines **Computer Vision** and **WebGL**. It uses the webcam to track the user's hands in real-time and enables physical and visual manipulation of a neon particle swarm.

The visual style is inspired by **some niche cyberpunk** aesthetics, featuring scanlines, vignettes, futuristic fonts, and a functional HUD (Heads-Up Display).

## Features

* **Real-Time Hand Tracking:** Uses MediaPipe Hands to detect up to 2 hands simultaneously.
* **Particle Physics:** 12,000 particles reacting to attraction, repulsion, and turbulence forces.
* **Gesture Recognition:** Different finger counts trigger different shapes, colors, and behaviors.
* **Mirror Mode:** The camera feed is displayed in the background with stylized filters, functioning as an augmented reality mirror.
* **Simple Architecture:** All code (HTML, CSS, JS) resides in a single `index.html` file.

## How to Run

### Prerequisites

* A modern browser (Chrome, Edge, Firefox) with WebGL support.
* A connected webcam.

### Step by Step

1. **Download the file:** Save the code as `index.html`.
2. **Open in Browser:**
   * **Recommended Option (VS Code):** Install the "Live Server" extension, right-click the file and choose "Open with Live Server".
   * **Simple Option:** Just drag the `index.html` file into a Chrome tab or double-click it.

3. **Permissions:** When opening, the browser will request permission to use the camera. Click **Allow**.

## Command Guide (Gestures)

The system differentiates between the **Left Hand** (Content Commands) and the **Right Hand** (Physical Interaction).

### Left Hand (Shape Controller)

The number of raised fingers changes the text and color of the particles:

| Gesture | Visual Result | Color (Neon) |
| --- | --- | --- |
| **1 Finger** | Text: "Hello" | Cyan |
| **2 Fingers** | Text: "生き甲斐" (Ikigai - The Japanese Secret to a Long and Happy Life) | Yellow |
| **3 Fingers** | Text: "Вукојѐбина" (place in the mid of nowhere) | Pink |
| **4 Fingers** | Text: "Schützengrabenvernichtungspanzerkraftwagen" (well, some historical transport) | Green |
| **Open Palm** | **Catch Mode:** Prepares attraction | --- |

### Right Hand (Physics Interactor)

Controls the physics and environment behavior:

| Gesture | Effect |
| --- | --- |
| **Pointing / Fist** | **Repulsion:** Particles flee from your index fingertip (2D plane only). |
| **Open Palm (5 Fingers)** | **Nebula Mode:** Particles spread across the entire screen in 3D. Moving your hand creates waves (water ripple effect). |

### ULTIMATE COMBO

When both hands have an **Open Palm (5 fingers)** simultaneously:

* **Effect:** Particles form a rotating **3D Basketball** above the left hand.
* **Behavior:** Particles gain an energetic "bounce" trajectory.

## Technologies Used

* **[Three.js](https://threejs.org/) r128:** 3D rendering and particle system.
* **[MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands.html):** Computer vision and hand skeleton tracking.
* **HTML5 / CSS3:** Interface structure and styling (HUD).

## Configuration

The system uses the following default parameters (editable in the `CONFIG` object):

```javascript
PARTICLE_COUNT: 12000
PARTICLE_SIZE: 2.4
LERP_FACTOR: 0.16          // Fast return speed
REPULSION_RADIUS: 150
REPULSION_STRENGTH: 1200   // Strong and snappy
NEBULA_SPREAD: 500
RIPPLE_FREQUENCY: 0.08
RIPPLE_AMPLITUDE: 40
BOUNCE_FREQUENCY: 15
BOUNCE_AMPLITUDE: 60
```

## Visual Effects

- Deep black background
- Animated scanlines overlay
- Moving grid animation
- Vignette effect (radial gradient)
- HUD displays (4 corners) with Orbitron font
- Neon cyan color scheme with glow effects
- Full-screen mirrored webcam as background layer

## Troubleshooting

* **Black Screen (No video):** Check if you allowed camera access at the top of the browser. Reload the page (F5) if necessary.
* **Slowdown (Low FPS):** The system is graphically intensive. Close other tabs or programs using the GPU. If on a laptop, make sure it's plugged in.
* **Hands Swapped:** The system works like a mirror. Your real left hand controls the left side of the screen (HUD "L.HAND").

## File Structure

```
/peak-cinema/
├── index.html    # Main application (single file)
├── CLAUDE.md     # Development documentation
└── README.md     # This file
```

---

**Made with Three.js + MediaPipe Hands**
