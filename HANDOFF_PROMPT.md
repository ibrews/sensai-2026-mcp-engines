# SensAI Deck — Handoff

Repo: /Users/alex/sensai-2026-mcp-engines · main · GitHub ibrews/sensai-2026-mcp-engines.
Builds **73 slides, 0 console errors** (HEAD d8e9fd4, pushed). Single-file index.html.
EDIT index.html JS via a Python exact-string-replace script (NOT the Edit tool — corrupts JS quotes); curly apostrophes inside single-quoted strings. One editor at a time; gate every edit on a clean headless build + a #N screenshot before commit.

## Done this session (committed + pushed)
- **Grid swap:** VitruvianGodot → `ue-openxr-passthrough` (AgileLens PCVR passthrough plugin); RES entry carries the full AgileLens URL; new OG-style card. Grid stays 12.
- **Reorder:** "Godot MCP Options" moved CH8 → CH6 (between "Why the Small Engine Wins" and "Godot Never Needed a Plugin").
- **UE logo fix:** the intro power-up barrage's "unreal" sprite was a placeholder open-U; swapped for the authentic Unreal Engine spiral-U glyph (`LOGOS.unreal`).
- **Pulsing Agile Lens monocle restored** on the orbit slide (presenter #3 / "Agile Lens"): draws the real `media/monocle-white.png` onto the orbit canvas, ring aligned to the client orbit, breathing alpha pulse. (NOT the Three.js bonus-slide torus — that's unrelated.)
- **OpenClaw slide** "From Jarvis to Dummy" (CH9, before the DEMO): honest arc — built it to be Jarvis, hit reliability+friction, demoted to a glorified "Dummy" (Iron Man). Two images (Iron-Man-Dummy + the renamed Slack "Dummy" bot) via a title-keyed IIFE.
- **Cascade Countdown:** the two consecutive slides merged into one (kept the on-device AVP clip + best bullets). `media/cascade-intro.mp4` now unused but left in place.
- **"You Do Not Need Deep Pockets"** moved INTRO → CH5 (right before "Watch a Local 8B Build It"); auto-picks up the CH5 chapter eyebrow.

## NEXT
- **Forage cyberpunk showcase → delegated to FORT** (RTX 5090). Forage is set up on Fort (per Alex). TODO filed in the KB: `inbox/fort.md` + `triggers/forage-cyberpunk-showcase-sensai-deck-2026-06-30.md`. It builds a cyberpunk Megascans showcase, captures stills + a flythrough, and wires them into the **"Headless Asset Pipelines"** slide (currently `img:'MEDIA_CYCLER'`). ⚠️ "Cyberpunk Environment Vol.1" is **Vault-only** (not on Fab); Fort has **ECABridge** installed → keep it + any internal names OUT of every frame. The rough `media/forage-scene-*.png` are stale grey-box test renders (not wired in).
- Possible polish: tune the monocle pulse alpha (0.12–0.25) if Alex wants it brighter/dimmer; the OpenClaw Slack screenshot shows Agile Lens product names ("Blueprint Immersive", "Holodeck Anywhere") — swap the image if those shouldn't be projected.

## Verify / gotchas (build gate that works)
- **Headless Chrome `--dump-dom` / `--screenshot` do NOT self-exit** — wrap in `perl -e 'alarm 30; exec @ARGV' <chrome> …` (the DOM/PNG is written before SIGALRM kills it; exit 142 is expected/harmless). Without the alarm the gate hangs forever.
- **Slide count:** `python3 -m http.server` + full Chrome `--headless=new --virtual-time-budget=7000 --dump-dom`; strip `<script>` blocks; count `class="slide[ "]` (i.e. class STARTS with the `slide` token — excludes spurious `sg-thumb slide-hidden` / `na-slide-num`). Expect **73**. Console check: second pass with `--enable-logging=stderr --v=1`, grep `Uncaught|TypeError|ReferenceError|SyntaxError`.
- **Screenshot a slide:** nav hash is **0-based** (`#0` = cover, `#1` = "Hi, I'm Alex", `#2` = "Agile Lens" … presenter "slide N" = `#N`). `--screenshot --screenshot-delay=5000 …index.html#N` (canvas cyclers + SVG/video need full Chrome + the real 5s delay, never virtual-time). Reusable scripts this session: `scratchpad/gate.sh [N]` and `scratchpad/shot.sh N out.png`.
- An SVG used as a slide `<img>` must be valid XML (no tag-literals in CSS comments) + all content visible by default (CSS animations don't run in the `<img>` context).
- Card thumbnails (`media/cards/<repo>.jpg`) are GitHub OG images: `curl -sL "https://opengraph.githubassets.com/<cachebuster>/<Owner>/<repo>"` (rate-limited — use a random path segment), then `sips` resize/crop to **800×420**.
