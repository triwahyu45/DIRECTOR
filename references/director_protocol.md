# Samurai Director v8 — Cinematic & Code-as-Camera Protocol

Reference sub-module distilled from `video-director` (11-Block Cinematic Architecture + 8-Phase Gated Code-as-Camera QA). Load this whenever directing a new video or performing an independent critic review.

---

## 1. The 4 Per-Film Dials (Decide Before Treatment)

1. **Clock** (what each reveal is cued to):
   - **Music grid**: cuts on beats, chapter changes on bars, drop lands on hero moment.
   - **Voice**: reveals land on measured word timestamps (`transcribe_beats.py`), music ducked under speech, payoff hit placed in the pause *before* the payoff line.
   - **Reads**: silent storytelling; reading time sets shot length.
2. **Continuity Mode**:
   - `One shape` (persistent object morphs, no cuts) | `Journey` (continuous follow-camera) | `Morph chain` (transitions morph into next, 1 payoff slam) | `Cut on beat` (lists/montages) | `Chaptered` (continuity inside chapter, hard cut + impact between chapters).
3. **Register** (look & physics):
   - `Clean/premium` (60fps, spring `ζ=0.72–1.0`, no grain/particles)
   - `Handmade/playful` (24fps on twos, `ζ=0.4–0.7`, squash & stretch, grain)
   - `Editorial/documentary` (30fps, restrained moves, strict `FACTS.md`)
   - `Kinetic` (30 or 60fps, fast-in hold next, cut-clamped `4x/12x` shutter blur, 3-layer fireflies, optical bloom)
4. **Text Policy**:
   - `Type as hero` | `In-world captions` | `No text` (exception: hook in first 3s unless waived).

---

## 2. The 11-Block Cinematic Shot Blueprint (Mandatory Order)

Every major shot or scene beat MUST specify these 11 blocks in exact order before writing code:

1. **SCENE**: Setting, palette regime (`BLACK` / `OFF_WHITE` / `RED`), atmosphere, grid/stage.
2. **CHARACTER / BRAND LOCK**: Exact verbatim tokens (`SkillField`, `SAMURAI`, `Antigravity Motion`, logo SVG/Canvas paths) — never paraphrase or improvise brand marks.
3. **ACTION**: Explicit `Anticipation → Action → Reaction` beats with frame counts (never vague adjectives like "moves dynamically").
4. **CAMERA**: Position, height, distance, move (`lock-off`, `dolly`, `whip-pan`, `handheld`, `push`, `pull`, `off-axis`).
5. **LENS**: Focal length equivalent (`24mm wide` / `35mm` / `50mm` / `85mm` / `200mm telephoto`) + DOF (`deep` / `shallow`).
6. **LIGHTING**: Key, fill, rim/back, practical sources + explicit angle (e.g., `warm directional top-left -1.0, 5.0, 2.5`).
7. **ENVIRONMENT MOTION**: Background world motion (3-layer fireflies, 35mm sprocket scroll, embers, radar ring) & which beat it drives.
8. **SECONDARY MOTION**: Reactive layer (`2–4` frame child lag, shockwave rings, sparks, camera recoil).
9. **MOOD**: Single emotional read (no compound moods).
10. **DURATION**: Exact seconds & frame range (`startF..endF`).
11. **NEGATIVE CONSTRAINTS**: Load-bearing bans on top (e.g., `no 1-frame pop-ins`, `no static slideshow holds > 1s`, `no flat centered title on gradient`, `no cross-cut shutter bleed`, `no clipped typography`).

### 5-Point Pre-Code Self-Review Gate
1. Lens focal length & camera move explicitly named?
2. Lighting direction/angle named?
3. `ACTION` names `Anticipation → Action → Reaction` beats in frames, not adjectives?
4. `NEGATIVE CONSTRAINTS` has >= 4 load-bearing entries?
5. Brand/character tokens copied verbatim?

### Visual 3×4 Storyboard Pre-Vis & 4:5 Feed Cover Spec
- For 45–60s vertical 9:16 explainers/stories, optionally generate a **10–12 panel 3×4 visual storyboard grid** (via `image-generator` subagent) alongside the 11-block blueprint to lock visual metaphors and framing before invoking `SAMURAI`.
- For Instagram Reels / TikTok deliverables, specify a dedicated **`cover.png` (4:5 center-crop safe zone, max 2-line title)** in the shot plan.

---

## 3. Motion, Sound & Craft Laws

- **Avoid the 2 Named Failures**:
  - **Slideshow**: everything arrives, then freezes.
  - **Screensaver**: everything drifts forever on a loop and nothing resolves.
- **Easing by Role**: Entrances = strong `expoOut`; Exits = `easeIn` at ~half entrance duration; State moves = `easeInOut`; Mass = `spring()`; Continuous drift = linear.
- **Pixel-Scale Anticipation**: Compute anticipation in pixels (`>= 18px` at 1080p; `4px` is invisible on mobile).
- **Hook in First 3s (Muted Test)**: By `t = 3.0s`, core promise + subject must be readable at `>= 84px` hook / `>= 48px` CTA (`1080p` short side) with `>= 7:1` contrast.
- **Sound on Same Clock**: Silence before payoff, loudest non-voice hit on payoff, `-14 LUFS ±1`, true peak `<= -1 dBTP`.
- **Canonical Script Ground-Truth & Dry VO Pacing**: When clock = `Voice`, align `transcribe_beats.py` / Whisper timestamps against the **canonical original script** (never ship raw ASR mishearings), use **Dry VO** trimmed of `> 0.3s` silences at `1.1x–1.2x` pace for lip-sync/beat accuracy, and validate `qa_sheet.jpg` + `cover.png` before full `60fps` render.

---

## 4. Independent Clean-Context Critic Rubric & Fix Card

Before final delivery on major projects, spawn a fresh subagent (`research` or `self`) with **ONLY** the rendered QA sheets (`hook_sheet.jpg`, `phone_sheet.jpg`, `director_*.jpg`, `qa_report.json`) and the brief:
- Critic defaults to **REJECT**, cites exact frame/timestamp numbers, and must restate the film's 1-sentence message from frames alone (muted).
- For every defect found, write a **Fix Card**:
  - **Timecode Scope**: `f=X..Y (t=A..B)`
  - **Must Not Change**: untouched scenes/frames
  - **Observed Failure**: exact visual/timing defect
  - **Target Mechanism**: exact primitive/curve/mask fix
  - **Banned Shortcuts**: e.g. no fake enlarging, no style swap, no hiding behind heavy blur.

---

## 5. Autonomous 3-Pass Director Self-Interrogation Protocol (Never Wait for the User to Direct You)

Before EVER presenting a rendered video as "done", the Director MUST run ALL 3 self-interrogation passes against `qa/hook_sheet.jpg`, `qa/phone_sheet.jpg`, `qa/qa_report.json`, and HD side-by-side forensic sheets (`REF` vs `SAM`), and automatically execute selective `--ranges` fix loops until all 3 passes are clean:

### Pass 1 — Macro Composition, Background & Brand Parity ("Ada yg kurang gak?")
- **Frame 0 & Continuity**: Frame 0 is a finished visual (`std > 3`, never pitch-black); `frozen_stretches == 0`; zero blank black gaps (`flat_stretches`).
- **Studio Backgrounds**: Light studio panels use crisp warm cream (`drawPanelBg(..., 'light', t, { dots: false })`, no muddy `#C4C0B6` corner vignette); dark panels have depth, radial glow, and embers.
- **Signature Visual Layers**: Echo shapes (`drawEchoShapes`), watermark echo walls (`drawEchoTextWall`), optical flares (`drawAnamorphicFlare`), and ink bursts (`drawInkBurst`) are present wherever the beat calls for impact.
- **Brand Parity**: Logos match true identity (e.g., Antigravity 4-stop rainbow spectral gradient `#4285F4 → #EA4335 → #FBBC05 → #34A853`).
- **360px Phone Readability**: Every UI card, radar, prompt box, and ETA/label in `phone_sheet.jpg` is legible on mobile.

### Pass 2 — Forensic Micro-Detail, Edge Clipping & Cut-Boundary Audit ("Detail kecil lainnya?")
- **Zero Viewport Clipping**: Inspect every tile of `hook_sheet.jpg` & `phone_sheet.jpg` so wide display words (`ANIMATION`, `FUCKING`, `OKAY.`, `RENDER.`) never clip against left/right margins.
- **Contrast & Stroke Clarity**: Catch dark text colliding with dark halftone/starburst lines, and dim wireframe strokes (`< 0.4` alpha) on dark backgrounds.
- **Strict Mask / Split Containment**: Verify X-splits and masks clip strictly to their target bounds (never crossing over header text or bleeding onto incoming scenes).
- **Cut-Boundary Sync**: Verify `audit_all_frames.py` achieves `>= 99.5%` panel accuracy and fix 1–2 frame transition offsets.

### Pass 3 — Animation Physics & Craft Audit ("Detail Animasinya?")
- **Smooth Directional Smear (No Ghost-Stepping)**: Extreme-speed whips/streaks use smooth weighted directional smear (`12–18` micro-steps or directional blur), not sparse `4–5` discrete copies.
- **Anticipation & Squash-and-Stretch**: Never hard-swap morphing shapes or slam cuts without a `2–3f` `anticipate()` pull + spin-pop or elastic rebound (`scale 0.65 → 1.18 → 1.0`).
- **Living Holds (Secondary Motion)**: Zero dead holds after entrance — landed text keeps subtle micro tracking/scale breathing; typing prompts use organic burst rhythm + keyword scale-pop; UI playheads use non-linear easing.
- **Match-Cut Whip Continuity**: Every scene's exit momentum (`outDir` / `zoomOut`) MUST connect to the next scene's entrance (`inDir` / `zoomIn`) so the film flows as one continuous camera.
- **Per-Character Choreography**: Prefer per-character stagger, wave, or stretch (`drawProportionalChars`, `drawFloorMaskStagger`, `drawSlitWaveText`) over flat single-block text slams.
