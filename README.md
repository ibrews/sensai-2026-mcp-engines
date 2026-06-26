# AI + MCP for Blender, Unreal & Godot

Talk deck for the **SensAI Hackademy** virtual workshop — prep session for the [Worlds in Action Hack at SIGGRAPH 2026](https://lu.ma/sensai-q6jg).

**Speaker:** Alex Coulombe — [Agile Lens](https://agilelens.com) · UE Gold Authorized Instructor  
**Format:** 30 min lecture · 15 min live demo · 15 min Q&A  
**Live deck:** https://ibrews.github.io/sensai-2026-mcp-engines/

Built with [Spatial Deck](https://github.com/ibrews/spatial-deck) — a single-file HTML presentation framework.

---

## Talk Outline

| Chapter | Topic | Accent |
|---------|-------|--------|
| CH 1 | Agents Changed the Game — from copilot to operator, what MCP is, the two paradigms | Teal |
| CH 2 | Structure Is the Secret Sauce — scene naming, local LLM routing, the setup pattern | Purple |
| CH 3 | Epic's Official Answer — Unreal Engine MCP plugin, interactive editing, headless pipelines | Amber |
| CH 4 | The Community Built It First — Blender MCP servers, high-leverage tasks, a local 8B building a scene live, production patterns | Rose |
| CH 5 | Your Second Brain Is the Real Tool — Godot + cross-engine knowledge transfer + the KB thesis | Teal |
| DEMO | Live Demo — Blender + Claude Code + MCP, live in front of the audience | Amber |

---

## Things to Try

1. **Open the deck** — load `index.html` in any browser. Arrow keys or click to navigate. `?` for keyboard shortcuts.
2. **Speaker notes** — press `N` to open the presenter popup (or load `index.html?notes` on your phone for a mobile speaker view).
3. **Search** — press `/` or `Cmd+F` to search across all slides by keyword.
4. **Edit mode** — open `index.html?edit` to see the full UI with annotation tools, move mode, and the slide grid.
5. **Export** — open `index.html?print` for a static page-per-slide render suitable for PDF export.

---

## Key Concepts Covered

- **Model Context Protocol (MCP):** how AI agents connect to 3D editors as tool operators
- **Interactive vs. headless workflows:** when to use each mode
- **Scene structure for AI:** naming, organization, and context scoping
- **Local LLM routing:** cost, speed, and privacy tradeoffs
- **Cross-engine knowledge transfer:** how a robust second brain (KB) makes every new project faster via triangulation
- **Real projects:** Cascade (Godot + AVP), MetaHuman on visionOS, RTX fork — and how lessons from each informed the others

---

## Live Demo Setup

The demo is **fleet-first**: a **local model (Ollama) drives Blender via typed MCP tools**, with Claude on standby for open-ended asks. Requirements:
- Blender 4.x + [blender-mcp](https://github.com/ahujasid/blender-mcp)
- A local model via Ollama (qwen3:8b) **+ the typed-tool MCP wrapper** (small structured tools instead of one free-form `execute_blender_code`)
- Claude Code (CLI) as the backup driver

The demo pattern: Alex gives a natural-language instruction → the local model emits a clean typed-tool plan → a visible change appears in the viewport. The CH 4 slide *"Watch a Local 8B Build It"* shows a scene a local 8B model built this way.

> **Why typed tools:** with the stock single `execute_blender_code` tool, local models leak the call as text (~0/6 reliable). With typed tools they're 100% reliable — *tool design beats model size.* Full runbook, the typed-tool server, and the video generator: KB `projects/sensai-blender-demo/`.
