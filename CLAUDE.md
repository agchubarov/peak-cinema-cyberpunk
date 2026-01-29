# Cyberpunk Interactive Particle System

## Project Overview
Single-file HTML application featuring a 12,000 particle system controlled by hand gestures using Three.js and MediaPipe Hands.

## Technology Stack
- **Three.js r128** - 3D rendering and particle system
- **MediaPipe Hands** - Hand tracking and gesture recognition
- **Canvas 2D API** - Text-to-particle coordinate generation
- **Pure HTML/CSS/JS** - Single file, no build tools

## File Structure
```
/peak-cinema/
├── index.html    # Main application (single file)
├── README.md     # Project documentation
└── CLAUDE.md     # Development notes
```

## Configuration Constants
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

## Features

### Visual Effects
- [x] Deep black background
- [x] Animated scanlines overlay
- [x] Moving grid animation
- [x] Vignette effect (radial gradient)
- [x] HUD displays (4 corners) with Orbitron font
- [x] Neon cyan color scheme with glow effects
- [x] Full-screen webcam as background layer

### Particle System
- [x] 12,000 particles with BufferGeometry
- [x] AdditiveBlending for neon glow
- [x] Particle size 2.4 with attenuation
- [x] Fast lerp (0.16) for snappy movement
- [x] Velocity-based physics with damping

### Hand Tracking
- [x] MediaPipe Hands integration (max 2 hands)
- [x] Finger counting algorithm
- [x] Hand chirality detection (left/right)
- [x] Gesture debouncing (150ms)

### Idle Mode (No Hands)
- [x] Particles spread across entire screen when no hands detected
- [x] Dim cyan color (40% brightness)
- [x] New random positions generated each time idle activates
- [x] HUD shows "IDLE" status on both corners

### Left Hand - Shape Controller
| Fingers | Shape                                          | Color                 |
|---------|------------------------------------------------|-----------------------|
| 1       | "Hello"                                        | Neon Blue (0x00FFFF)  |
| 2       | "生き甲斐"                                      | Neon Yellow (0xFFFF00)|
| 3       | "Вукојѐбина"                                   | Neon Pink (0xFF00FF)  |
| 4       | "Schützengrabenvernichtungspanzerkraftwagen"   | Neon Green (0x00FF88) |
| 5       | Catch Mode                                     | (context dependent)   |

### Right Hand - Physics Interactor
- [x] Index finger tip tracking (Landmark 8)
- [x] State A (< 5 fingers): XY-only repulsion (no Z distortion)
- [x] State B (5 fingers): Nebula mode with water ripple effect

### Dual Hand Combo - Basketball
- [x] Trigger: Both hands open (5 fingers each)
- [x] Fibonacci sphere distribution
- [x] Orange color with black seam lines
- [x] Bouncing particle trajectory
- [x] Continuous Y-axis rotation

## Architecture

### Z-Index Layers (bottom to top)
1. Webcam video - z:0 (full-screen background, mirrored, dimmed 40% opacity, desaturated)
2. Three.js canvas - z:1 (transparent background, particles only)
3. Scanlines overlay - z:2
4. Grid overlay - z:2
5. Vignette overlay - z:3
6. HUD elements - z:10

### Animation Loop
1. Process hand tracking results
2. Update particle targets based on gesture state
3. Apply physics (lerp + velocity)
4. Apply interaction forces (repulsion/ripple/attraction)
5. Update BufferGeometry attributes
6. Update HUD (FPS, hand status)
7. Render scene

## TODO (perhaps)
- [ ] Add particle trail effects
- [ ] Implement sound effects for interactions
- [ ] Add more gesture-based shapes
- [ ] Optimize for mobile devices
- [ ] Add particle color transitions/gradients

## Usage
1. Open `index.html` in Chrome/Firefox
2. Allow camera access
3. Use hand gestures to interact:
   - Left hand 1-4 fingers: Change text shape
   - Right hand pointing: Scatter particles
   - Right hand open: Nebula mode
   - Both hands open: Basketball combo
