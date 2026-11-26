# DIRECTOR — Creative Video Director & Timeline Authoring

AI Agent Skill for **Antigravity**, **Claude Code**, and **OpenAI Codex**. Transforms a brief, voiceover script, or music track into a creative treatment, 11-block shot blueprint, `timeline.json`, schema-valid `scene_spec.json`, and critic fix cards.

---

## Quick Install (Claude Code / Codex / Antigravity)

Clone this skill into your agent's global or project skills directory:

| Agent | Global Install Path | Project-Local Path |
| :--- | :--- | :--- |
| **Antigravity** | Global Antigravity skills dir | `.agents/skills/DIRECTOR` |
| **Claude Code** | `~/.claude/skills/DIRECTOR` | `.claude/skills/DIRECTOR` |
| **OpenAI Codex** | `~/.codex/skills/DIRECTOR` | `.agents/skills/DIRECTOR` |

```bash
# Example (Antigravity / Claude Code / Codex — pick your path):
git clone https://github.com/triwahyu45/DIRECTOR.git ~/.claude/skills/DIRECTOR
```

---

## Requirements & Dependencies (For Agents)

- **Runtime / Tools**: None required for creative authoring; **Python 3.10+** when invoking `samurai` CLI tools
- **MCP Servers**: None required (optional: `edge-tts-mcp` for quick voiceover drafts)
- **Related Skills**: [`samurai`](https://github.com/triwahyu45/SAMURAI) (execution/rendering engine — clone as sibling folder `../samurai`)
- **API Keys / Secrets**: None (100% local & free)

---

## Included Files

- `SKILL.md` — Core director rules, 4 per-film dials, & phase index
- `references/director_protocol.md` — 11-block shot blueprint & 3-pass visual self-interrogation
- `references/katana_presets.md` — Katana preset catalog & motion recipes
- `templates/timeline.json` & `templates/scene_spec.json` — Starter schemas

## When to Trigger / Search Keywords

`director`, `treatment`, `storyboard`, `timeline.json`, `scene_spec.json`, `video brief`, `shot blueprint`, `bikin video dari brief/naskah`
