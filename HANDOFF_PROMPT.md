# SensAI 2026 MCP Deck — Handoff Prompt

## Repo
`/Users/alex/sensai-2026-mcp-engines/index.html` — single-file HTML deck, no build process.
GitHub: https://github.com/ibrews/sensai-2026-mcp-engines

## Current Task
Two items to fix:

### 1. Slide 21: Missing image
**Slide 21** (0-indexed allSlides[21]) is the case slide "Get Running: Unreal MCP" under CH3.
It currently has `img: ''` → renders a gradient placeholder.
This slide lists 6 Unreal MCP options with their URLs. It needs a visual.

**Recommended fix**: Create `images/ch3-get-running.svg` — a clean options-card grid showing the 6 plugins:
- Epic Official (amber, built-in UE 5.8+)
- NeoStack / Betide Studio (purple)
- chongdashu/unreal-mcp (teal, open source)
- flopperam/unreal-engine-mcp (rose)
- ue-mcp.com (purple, 525+ actions)
- CLI snippet row at bottom: `claude mcp add --transport http unreal http://127.0.0.1:PORT/mcp`

Then change `img:''` on line 194 to `img:'images/ch3-get-running.svg'`.

**JS edits must be done via Python binary replacement** to avoid the Edit tool's curly-quote corruption. Example:
```python
with open('/Users/alex/sensai-2026-mcp-engines/index.html', 'rb') as f: data = f.read()
old = b"img:'',"   # be precise about context
new = b"img:'images/ch3-get-running.svg',"
data = data.replace(old, new, 1)
with open('/Users/alex/sensai-2026-mcp-engines/index.html', 'wb') as f: f.write(data)
```
Use context from surrounding lines to make the replacement unique (e.g. include the subtitle line).

### 2. Links throughout the deck — many URLs in bullets are plain text, not clickable

**CSS** — add link styles in the deck's CSS block (around line 768):
```css
.case-bl li a,.lesson-tagline a{color:var(--teal);text-decoration:none;border-bottom:1px solid rgba(0,212,255,.35);transition:color .15s,border-color .15s}
.case-bl li a:hover,.lesson-tagline a:hover{color:#7be8ff;border-color:rgba(123,232,255,.6)}
.accent-amber .case-bl li a{color:var(--amber);border-color:rgba(245,158,11,.35)}
.accent-amber .case-bl li a:hover{color:#ffd27a;border-color:rgba(245,158,11,.6)}
.accent-purple .case-bl li a{color:var(--purple);border-color:rgba(167,139,250,.35)}
.accent-rose .case-bl li a{color:var(--rose);border-color:rgba(244,63,94,.35)}
```

**Bullets to linkify** (all in SECTIONS array, lines 47–477+):

| Slide | Line | Current text | Link to add |
|-------|------|--------------|-------------|
| INTRO "Love Your Work" | ~82 | `github.com/ibrews/spatial-deck` | `https://github.com/ibrews/spatial-deck` |
| CH3 "Get Running" | ~195 | `betide.studio/neostack` | `https://betide.studio/neostack` |
| CH3 "Get Running" | ~196 | `github.com/chongdashu/unreal-mcp` | `https://github.com/chongdashu/unreal-mcp` |
| CH3 "Get Running" | ~197 | `github.com/flopperam/unreal-engine-mcp` | `https://github.com/flopperam/unreal-engine-mcp` |
| CH3 "Get Running" | ~197 | `agent.flopperam.com/mcp` | `https://agent.flopperam.com/mcp` |
| CH3 "Get Running" | ~198 | `ue-mcp.com` | `https://ue-mcp.com` |
| CH5 "MCP Server Landscape" | ~257 | `github.com/ahujasid/blender-mcp` | `https://github.com/ahujasid/blender-mcp` |
| CH8 "Godot MCP Options" | ~369 | `godotengine.org/asset-library/asset/4961` | `https://godotengine.org/asset-library/asset/4961` |
| CH8 "Godot MCP Options" | ~371 | `github.com/Coding-Solo/godot-mcp` | `https://github.com/Coding-Solo/godot-mcp` |

Also check for any other plain-text URLs in bullets after line 400 (Pro Tips, Demo sections).

**Also: resources slide link audit** — the resources slide (around line 1400+) has a repos grid with GitHub repo names displayed as text; those cards should be clickable `<a>` elements wrapping the whole card.

**Approach**: Since the Edit tool corrupts curly quotes in JS, use Python binary replacement for all SECTIONS bullet changes. For the CSS block (pure CSS, no JS), the Edit tool is safe.

## What's Been Done This Session
All previous items (1–3, 7, 9, 10, 15, 16) landed in commit `69d89e0`:
- Cover logo strip ✅
- Bearded sprite on "Hi, I'm Alex" ✅  
- "One more thing" RealityKit span ✅
- Clickable "What We Will Cover" bullets ✅
- Resources QR codes for 4 talks ✅
- SVG fixes (autocomplete, loop-up direction, return arrows) ✅
- CH3 Promethean AI reveal: `media/promethean/clip3x_final.mp4` (2.6MB, 30.7s) embedded with slideStep badge "⚡ 2018. Promethean AI." ✅

## Slide Index (0-based allSlides[])
0=Settings, 1=Cover, 2=INTRO lesson, 3–7=INTRO cases, 8=CH1 lesson, 9–10=CH1 cases,
11=CH2 lesson, 12–15=CH2 cases, 16=CH3 lesson, 17–21=CH3 cases (21=Get Running, MISSING IMAGE),
22=CH4 lesson, 23–26=CH4 cases, 27=CH5 lesson, 28–32=CH5 cases, 33=CH6 lesson, 34–36=CH6 cases,
37=CH7 lesson, 38–40=CH7 cases, 41=CH8 lesson, 42–45=CH8 cases, 46=CH9 lesson...

## Validation
- The PostToolUse hook at `.claude/hooks/validate-js.sh` checks for JS syntax errors after edits.
- The importmap block (`<script type="importmap">`) causes a false-positive "Unexpected token ':'" — this is pre-existing and not a regression.
- After edits: `cd /Users/alex/sensai-2026-mcp-engines && git add index.html images/ && git commit && git push`

## Safety Rules (permanent)
- Never show a celebrity likeness
- Never show Tailscale IPs (100.x.x.x)  
- "ECABridge" must NEVER appear in the deck
- No internal/unreleased app names
- CH4 case study stays anonymized ("broadcast game-show")
