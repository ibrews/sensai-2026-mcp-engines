# SensAI Deck — Handoff

Repo: /Users/alex/sensai-2026-mcp-engines · main · GitHub ibrews/sensai-2026-mcp-engines.
Builds 73 slides, 0 console errors (HEAD 5283fd9, pushed). Single-file index.html.
EDIT index.html JS via a Python exact-string-replace script (NOT the Edit tool — corrupts JS quotes); curly apostrophes inside single-quoted strings. One editor at a time; gate every edit on a clean headless build + a #N screenshot before commit.

## Done this session (committed + pushed)
- Recovered deck from the overnight ALT-insert breakage -> clean 73-slide build.
- Review fact-fixes + REVIEW_NEEDED.md rewritten. Live Blender demo verified + flourished (reproduce prompt delivered).
- Agile Lens orbit slide; "Headless Does the Heavy Lifting" (CH1); "Fleet-First Routing" (CH2); "Build the AI Out" (CH2, cost-down ladder 3rd rung — Blueprint Auto-Layout/Forage/UnReality Kit; SVG images/beyond-ai-ladder-anim.svg).
- Build-a-Dial interactive click-the-options diagram. Grid -> 12 (dropped hyperframes; added crystal-caper + UE5_AndroidXR w/ media/cards thumbnails; RES entries take optional 3rd elem = full URL for AgileLens repos). Media split. Presenter sync = press N.

## NEXT — new asks from Alex (do these in a fresh session / chip)
1. GRID SWAP: replace VitruvianGodot with ue-openxr-passthrough (AgileLens/ue-openxr-passthrough — UE5 PCVR passthrough plugin). Needs a media/cards/ue-openxr-passthrough.jpg thumbnail (match existing card style) + RES entry with the AgileLens full URL as 3rd element. (RES render already supports 3rd-elem URLs.)
2. FORAGE DEMO ON FORT (not alex-mbp): Fort has better internet + an RTX 5090 — crank quality. SSH `fort`. Alex OK'd enabling Forage's experimental AUTOMATED (zero-click) Fab install mode. FIRST verify the Forage UE plugin is installed in the UE project on Fort (Alex asked). Then: Forage installs Megascans Cyberpunk Env Vol.1 -> build cyberpunk environment showcase -> cinematic light + hero camera -> capture stills + flythrough -> wire into the Forage/Headless-Asset-Pipelines slide (keep ECABridge/internal names out of frames).
3. NEW SLIDE — OpenClaw: the problem was RELIABILITY + FRICTION, so Alex has relegated it to a glorified "dummy robot" (like Dummy in Iron Man). Use BOTH images: /Users/alex/Desktop/Iron-Man-Dummy.jpg + /Users/alex/Desktop/slack-dummy.png (copy into media/, transcode/resize as needed). Build a slide (likely CH9 pro-tips, or near the bio/OpenClaw mention).
4. REORDER (clear win, was teed up): move "Godot MCP Options" from CH8 (its opener) -> CH6, between "Why the Small Engine Wins" and "Godot Never Needed a Plugin." LEAVE "Headless Does the Heavy Lifting" in CH1 ("Build the AI Out" is CH2's capstone).
5. OPTIONAL reorders (Alex's call): merge the two "Cascade Countdown" slides (CH6) -> 1; move "You Do Not Need Deep Pockets" INTRO -> CH5 (before "Watch a Local 8B Build It").

## Verify / gotchas
- Build gate: python3 -m http.server + full Chrome --headless=new --dump-dom; strip <script> blocks; confirm 73 (or +N) .slide divs + zero Uncaught/TypeError (--enable-logging=stderr).
- Screenshot a slide: compute index N among slide divs; full Chrome --screenshot --screenshot-delay=5000 ...#N (canvas + SVG <img> need full Chrome + real delay, NOT virtual-time).
- An SVG used as a slide <img> must be valid XML (no tag-literals in CSS comments) + all content visible by default (CSS animations do NOT run in the <img> context).
- Engines: UE 5.8 was open on alex-mbp (PID 92969) with Fab working; Blender 4.2.1 idle on :9876. The Forage demo moves to FORT per Alex.
