---
name: DIRECTOR
description: Creative Video Director skill. Use when directing any motion video from a brief, script, or music track to produce a treatment, 11-block shot blueprint, timeline.json, scene_spec.json, or critic fix cards (bikin video dari brief/naskah/musik, susun treatment/timeline/scene_spec). Targets the standalone samurai engine CLI when rendering Katana motion.
---

# Director — Creative Direction, Timeline & Scene-Spec Authoring

Pure creative director skill (owns treatments, 11-block shot blueprints, pacing dials, and 3-pass Critic QA). Transforms a brief, voiceover script, or music track into **`timeline.json`** and schema-valid **`scene_spec.json`** targeting `SAMURAI` (Katana engine), `STUDIO` (Remotion/Three.js), or `ATELIER` (Blender PBR), paired with `SONIC` for audio.

---

## Hard Rules (Non-Negotiable)

1. **Zero Renderer Code**: NEVER write JavaScript, Canvas2D, Three.js, GLSL shaders, or touch `samurai/engine/`. Your ONLY technical outputs are JSON files (`timeline.json`, `scene_spec.json`, `fix_card.json`) and Markdown creative/critic docs.
2. **Read-Only Contract**: Author `scene_spec.json` strictly against `../samurai/schema/scene_spec.schema.json` and fix cards against `../samurai/schema/fix_card.schema.json`. Do NOT copy or fork the schemas.
3. **CLI-Only Engine Invocation**: Invoke `samurai` strictly via CLI (`validate_spec.py`, `render_samurai_cli.py --validate-only`, `render_samurai_cli.py --ranges`, `qa_video.py`, `transcribe_beats.py`) — NEVER copy engine code.
4. **Renderer Selection Discipline**: Choosing `meta.renderer` (`canvas2d` vs `webgl`) is a creative decision owned by Director. Choose `webgl` ONLY when the brief genuinely requires 3D motion (true depth perspective, multi-plane parallax, camera orbit, PBR 3D geometry, or selective DOF). Otherwise choose `canvas2d`.

---

## Owned Pipeline Phases

- **Phase 1 — Intake & 4 Per-Film Dials**: Lock `clock`, `continuity`, `register`, and `text_policy` (`references/director_protocol.md` §1).
- **Phase 2 — Treatment & 11-Block Shot Blueprint**: Write the 1-sentence core idea, 0–3s muted hook, 11-block shot specs, and pass the 5-point self-review (`references/director_protocol.md` §2).
- **Phase 3 — Single Timeline (`timeline.json`)**: Lock every beat in seconds/frames (invoke `../samurai/scripts/transcribe_beats.py` CLI for voice, or BPM grid for music).
- **Phase 4 — Look-Proof Stills & `scene_spec.json`**: Author `scene_spec.json`, validate via `samurai` Engine CLI (`validate_spec.py` & `render_samurai_cli.py --validate-only`), then render 2–4 contrasting look-proof stills via `--ranges` before approving full render.
- **Phase 8 — Clean-Context Critic Review, 3-Pass Self-Interrogation & Fix Card Loop**: Run all 3 Director Self-Interrogation Passes backed by exact `qa_report.json` numbers + visual inspection of `hook_sheet.jpg` & `phone_sheet.jpg`, emit Fix Cards, and update `scene_spec.json` until all 3 passes pass.

---

## Mandatory Self-Audit & Revise-Before-Delivery Gate

Before approving final delivery:
1. Run all 3 Director Self-Interrogation passes against `qa_report.json` and visually inspect `hook_sheet.jpg` and `phone_sheet.jpg` via `read_file`.
2. Emit Fix Cards for any defect and revise `scene_spec.json` until zero visual/timing issues remain.

---

## Reference Sub-Modules & Templates

- [director_protocol.md](references/director_protocol.md) — 4 Dials, 11-Block Blueprint, Motion/Sound Laws, Critic Rubric, Fix Cards, and 3-Pass Self-Interrogation.
- [katana_presets.md](references/katana_presets.md) — Katana motion visual grammar & reusable design presets.
- [timeline.json](templates/timeline.json) & [scene_spec.json](templates/scene_spec.json) — Schema-valid templates.
