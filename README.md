# 🌈 Neon Kaleidoscope

*Radial symmetry turns particle streams into ever-changing mandala patterns. Watch glowing particles emit from the center and multiply across symmetry axes, creating hypnotic floral and geometric designs. Click to burst particles. Adjust symmetry count, speed, size, trail fade, color cycling. Pure generative art.*

---

## What is this?

A kaleidoscope works by reflecting a scene through multiple mirrors arranged in a circle, producing intricate radial patterns. This digital version simulates that: particles radiate from the center, and each particle is drawn multiple times rotated around the center by the symmetry count. The result is a constantly evolving mandala of glowing neon.

---

## Features

- **Radial symmetry** (2–24 axes) replicates each particle into a symmetric pattern
- **Particle emitter** from center with configurable rate and speed
- **Neon glow** with HSL color cycling
- **Trail fade** effect for motion blur and persistence
- **Slow global rotation** of the symmetry axes adds extra dynamism
- **Interactive burst** — click anywhere to inject a spray of particles
- **Adjustable parameters:**
  - Symmetry count (2–24) — number of rotational copies; even numbers produce balanced mandalas, odd numbers produce star patterns
  - Max particles (50–800) — total particles on screen
  - Emission rate (1–15) — how many new particles per frame
  - Speed (0.2–4) — multiplier for particle velocity
  - Size (1–8) — base particle radius
  - Trail fade (0.01–0.3) — how quickly old frames fade; lower = longer trails, denser patterns
  - Color cycle speed (0–2) — rate of global hue rotation
- **Pause/Resume** and **Randomize** all sliders
- **Stats overlay** — particle count, FPS
- **Single HTML file** — no dependencies

---

## How to Use

1. Open `index.html`
2. Particles stream from the center, each duplicated across the symmetry axes to form radial patterns. Watch the mandala grow and evolve.
3. **Click** anywhere to create a burst of particles at that location.
4. Adjust sliders to change the visual style:
   - **Symmetry** — more axes = more complex, higher CPU; try 6, 8, 12 for classic kaleidoscope looks
   - **Max Particles** — density of the pattern
   - **Emission Rate** — how quickly new particles appear
   - **Speed** — faster particles stretch patterns
   - **Size** — larger particles produce bolder strokes
   - **Trail Fade** — lower values keep trails longer, building up intricate layers; higher values give sharper, fleeting designs
   - **Color Cycle** — how fast colors shift
5. Press **Randomize** to conjure a new random configuration
6. **Pause** to freeze the current artwork

---

## Technical Details

- **Particle system:** Each particle has position, velocity, lifespan, hue, size. Emitted near center with random outward direction.
- **Symmetry rendering:** For each particle, we compute its offset from the center, then rotate that offset by `θ_i = i * (2π / symmetry)` for each axis, drawing a circle at each rotated position. We also add a global `angleOffset` that slowly rotates over time, causing the entire pattern to turn.
- **Trails:** Instead of clearing the canvas each frame, we draw a semi-transparent black rectangle, causing previous frames to gradually fade.
- **Performance:** Draw calls = particles × symmetry. With symmetry=12 and particles=300, that's 3600 arcs/frame, fine for Canvas 2D.
- **Color:** Each particle carries a base hue; a global `hueCycle` adds temporal variation. Final hue = (particle hue + globalCycle) mod 360.

---

## The Real Story

Kaleidoscopes are one of those simple inventions that produce endless beauty. By taking a handful of colored fragments and multiplying them through symmetry, you get infinite patterns. This digital version adds motion and time — the pattern continuously morphs as particles age and new ones are born. The slow rotation of the symmetry axes adds a subtle shift that prevents the design from ever truly repeating. It's like a never-ending firework made of light.

---

*Made with 🌈 and rotation matrices.*

**Repo:** https://github.com/Kiloooai/neon-kaleidoscope
