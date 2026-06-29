# HANDOFF — Continue the SensAI deck

> Written 2026-06-29 at the end of an overnight build. The chip/spawn-task MCP tool
> dropped on a process restart, so this doc is the continuation hand-off instead.
> Start a fresh session and follow this. **Route via non-Opus (Sonnet default; local
> fleet / Gemini when useful) to save budget. Commit + push after EVERY step** — the
> process restarted twice tonight and killed long background agents.

Context + status: read `~/knowledge/projects/sensai-2026-mcp-engines.md` and
`~/knowledge/daily/2026-06-29-alex-mbp.md` (§ "SensAI 2026 MCP talk deck") first.
Single-file-deck gotchas: `.claude/CLAUDE.md` + `HANDOFF_PROMPT.md` (Python binary
edits, ASCII notes, media-cycler IIFEs AFTER the gif/video override, never break
existing wiring).

**Public-deck safety (hard):** never show a celebrity likeness, Tailscale IPs
(100.x.x.x), the literal text "ECABridge", or internal/unreleased app names. CH4
case study stays anonymized ("broadcast game-show").

## Remaining work (priority order)

1. **Asset hunt re-run** (the overnight one died on a restart, wrote nothing). Replace
   gradients in CH6 (Godot) + CH7 (Apple stack) with real screenshots; fix any dups.
   - Targets: Cascade in the Godot editor + in the AVP simulator (pull a short clip
     from https://www.youtube.com/watch?v=-2zL1m6rzhU → `media/cascade-avp.mp4`);
     VitruvianGodot CC0 head render; SplatStage splat-on-AVP; a visionOS Simulator
     screenshot; Xcode/TestFlight (ue5-testflight).
   - Sources: `~/dev` clones, `~/Pictures/lore-r1`, public repos via
     `gh api "repos/ibrews/<name>/git/trees/HEAD?recursive=1"`.
   - Gradient slides wanting images: CH6 "A CC0 Human", CH6 "Why the Small Engine Wins",
     CH7 "The Simulator Is the Loop Machine", CH7 "Splats, Swift, and the Bridge".

2. **Images #6/#38/#39:**
   - #6 "You Do Not Need Deep Pockets" (gradient): crop the Claude panel from
     `media/local-vs-claude.png`, or make an on-brand SVG (local ≈ frontier for routine).
   - #39 "Teach Them, Let Them Teach You" (gradient): on-brand SVG of the teach/learn
     loop (Gemini image-gen is 404 right now, so use SVG).
   - #38 "Chips Over Compaction": ✅ DONE — wired `media/cs-chip-spawn.png` (Alex's
     screenshot of the chip-spawn, cropped to just the chip card, no transcript leak).

3. **#2 intro power-up sprite sequence** on the "Hi, I'm Alex" slide — the centerpiece.
   Study the intro of ibrews/harvardxr-keynote (https://ibrews.github.io/harvardxr-keynote/,
   its index.html) for the substep/sprite mechanic. Build an escalating logo-sprite
   barrage: Alex powers up shooting Unreal-logo sprites, then ADD increasingly fast
   Claude → Xcode → Godot → Blender sprites until it's a comedic overload. Use
   `slideSteps` + an isolated JS IIFE. (Skip the harvardxr "going back in time" bit.)

4. **Live Forage "robust scene" demo design** — substantive, not "look, primitives."
   Forage building out a rich scene. Spec it; tie to `~/knowledge/projects/sensai-blender-demo/`.

5. **Verify:** full visual pass on all ~52 slides; CONFIRM the 4 animated SVGs
   (`images/*-anim.svg`) actually animate in `<img>` — if not, revert those slides to the
   static originals; fix any layout breaks.

## Already shipped this session (do NOT redo)
- CH6 Godot chapter + CH7 "Into Apple's Stack" (RealityKit/Swift/Xcode) chapter.
- 4 animated SVG diagrams wired (triangulation, two-modes, setup-pattern, transferability).
- Penultimate Resources slide (12 QR cards + blurbs; capafy-skills in; Understudy/
  holodeck-pocket/aether-companion out). Close repo-list removed.
- Agile Lens logo on cover; wifi/USB analogy on "What is an MCP"; slide-0 shortcuts card.
- Review fixes: Copilot→"From Suggestion to Action"; Epic de-emphasized (Promethean AI
  2018/Neostack); 2025 date removed; "Case Study:" label; Production Pattern→Request/
  Change/Inspect; Lincoln quote attributed; "−time"→"faster"; TOC spinning gif; live-demo
  slide canned-video removed.
