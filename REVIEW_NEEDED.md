# Deck Review — Resolved (sensai-2026-mcp-engines)

**Reviewed:** 2026-06-30 — overnight automated pass + KB validation + Alex's calls.
**Status:** All findings triaged and resolved. The automated ALT-insert pass corrupted
`index.html` (a case object lost its `bullets` → build halted at 4 slides); the deck was
rebuilt clean from the last good commit and re-verified (71 slides, 0 errors). See commit `95603f6`.

## Applied — fact-fixes now live in the deck
- **Many MetaHumans, Tiny Hardware** — "fanless PC in a controller shell" → "15W-TDP shared-memory PC in a controller shell" (the Steam Deck has an active fan).
- **Real Projects, Real Transfers** — "RigLogic proved native RealityKit skeleton posing at 90fps" → "RigLogic + a custom Metal skinning kernel drove the full cast at 90fps on device" (KB: the 90fps figure is the custom Metal LBS kernel, not native RealityKit `jointTransforms`).
- **Real Projects, Real Transfers** — dropped "in under one session" from the RTX-fork bullet (not KB-documented; Alex's call).
- **Godot: Small Engine, Big Reach** — tags `CC0` → `MIT` (Godot is MIT-licensed).
- **Hi, I'm Alex** — speaker notes "Lets" → "Let's".
- **Splats, Swift, and the Bridge** — subtitle → "RealityKit + Swift — from splat scenes to engine bridges" (resolves the "no game engine required" vs. UE-bridge contradiction).
- **All Free. All Public.** — HarvardXR "2025 keynote" → "2026 keynote" (event was April 2026).

## Verified correct — no change (automated-review false positives)
- **How We Actually Route** — "Opus 4.8 / Haiku 4.5" are correct current model names.
- **Local routing numbers** — "0 of 6" and "100%" are KB-documented (`blender-mcp-local-model-driver.md`).
- **Unreal Fluency Is a Godot Superpower** — "both reach AVP through Apple's Compositor Services (Metal)" is ACCURATE: shipping Cascade renders via the CompositorServices immersive path at 90fps (`godot-avp-cascade.md`). The RealityKit/Swift path is a documented-but-unexecuted future eval.
- **A Real MetaHuman, in Godot** — "RigLogic + DNA under an MIT license" kept (OpenRigLogic code is MIT; Alex's call).
- **Bounce Models and Machines** — "Codex" kept (listed as an ecosystem model others can use, not fleet-deployed).
- **Build a Dial for the Unknowns** — Cascade grab-damping example is correct (the cycler helped pick the best pinch/drag feel — a positive result).
- **Hi, I'm Alex** — "OpenClaw" tag kept (part of the tool-journey arc; the notes frame the pivot to Claude).
- **Godot Never Needed a Plugin**, **Love Your Work** — no factual error.

## ALT slides
The automated pass inserted 5 ALT duplicate slides; they caused the build break and were
low-value per validation. Removed from the live deck. Their full content is preserved in git
(commit `4a9bb48`) should any ever be wanted.

## Pre-talk checklist — day-of verification (can't be fixed in-slide)
1. Confirm the shipping Unreal version vs the deck's "UE 5.8+" (Plenty of Plugins, Get Running).
2. Check `chongdashu/unreal-mcp` star count, and that `agent.flopperam.com/mcp` is live.
3. Confirm the Headless-Asset-Pipelines cycler video actually shows Forage.
4. (Optional) Visually verify the SVG diagrams flagged in the diagram review.
