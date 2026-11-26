# Samurai Master Prompt & Vector / 3D / Motion Preset Guidelines

## The Official Katana Prompt Blueprint

```
Create a kinetic typography promo using the supplied reference images and brand information. 
Follow the reference’s rapid sequence of oversized condensed headlines, stacked words, isolated punctuation, and small supporting text. 
Alternate near-black backgrounds with warm off-white and vivid red panels. 
Animate lettering through punchy scale changes, lateral sweeps, stretching, rotation, and motion blur. 
Interleave framed interface or reference-image inserts, simple red geometric forms, thin glowing lines, and subtle particles. 
Keep the composition bold and tightly timed, then resolve into a clean centered brand end card.
```

## Visual Grammar & Vector/3D Matrix

| Category | Design Specification | Implementation |
| :--- | :--- | :--- |
| **Headline Fonts** | `Archivo Black` / `Barlow Condensed 900` / `Inter 900` | Upright bold (`150px–680px`, tight tracking `-6px..-26px`) |
| **Editorial Accent** | `Playfair Display Italic` / `JetBrains Mono 700` | Serif italic for editorial phrases; mono for timers, prompts, layer bars |
| **Background Texture** | Subtle Dot-Matrix Grid | `radial-gradient(circle, rgba(..., 0.085) 1.5px, transparent 1.5px)` @ `38px` |
| **Boolean Knockouts** | SVG `<clipPath>` | Starburst / expanding circle color-inversion + diagonal 2-half blade slices |
| **True 3D Geometry** | Perspective Vertex Projector | `Rx * Ry * Rz`, focal `4.4`, backface cull (`nz > 0`), directional face shading (`#F28B56` top, `#EA261B` / `#A4150E` sides) |
| **Motion Trails** | Stepped Sub-Frame Echoes + Directional Blur | `motionEcho(6, dx, dy, fn)` + SVG `<feGaussianBlur stdDeviation="18 0">` |
| **Checkerboard Fill** | SVG `<pattern>` | After Effects alpha checkerboard (`#232325` / `#3B3B3F`) clipped by left-to-right progress bar |

---

## `STUDIO-BENCH` Engineering Documentary Preset Blueprint

- **Studio Stage & Lighting:** Persistent moody `#11151C` walnut/concrete studio workbench set (swapping only the hero prop per episode), focused top-softbox key + rim light + shallow `f/2.8` DoF bokeh.
- **Color & Accent System:** Neutral dark studio canvas with dual-accent highlights (`#38BDF8` cyan for data/electric/autonomy, `#F59E0B` amber for energy/heat/caution).
- **3D Callouts & Data Viz:** 3D-tracked frosted dark callout pins (`rgba(15,20,28,0.85)`) with anchor dot + thin vertical hairline leader, micro gray primary-source citations (`IEA`, `ABB`, official standards), and 2D charts embedded directly on in-world studio screens.
- **Pacing & Sound:** Calm `110–125 WPM` VO with `0.3–0.5s` reading pauses, subtle mechanical/UI SFX, and `-14 LUFS` mastering (`LRA 2–4 LU`).
