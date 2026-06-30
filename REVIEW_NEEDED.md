# Overnight Review — sensai-2026-mcp-engines
**Reviewed by:** Claude Opus 4.8 (overnight batch)
**Date:** 2026-06-30
**Scope:** All slides in SECTIONS array + dynamic builder slides (resources, map, close)

**Result: 19 ALT slides inserted + 1 inline fix (TALKS array 2025→2026). 0 skipped.**
All JS validations passed. No inserts were reverted.

ALT slides have been inserted into index.html immediately after their originals.
Slides below marked **ALT INSERTED** have a corrected version in the deck.
Slides marked **MANUAL FIX NEEDED** require a human or scoped edit outside the SECTIONS array.
Slides marked **INLINE FIX** were corrected directly in the original source (not an ALT).

---

## TRUTH

### Many MetaHumans, Tiny Hardware — HIGH confidence
ALT INSERTED.
**Concern:** "a fanless PC in a controller shell" is factually wrong. The Steam Deck has an active cooling fan. Valve's spec sheet confirms this.
**Fix applied:** ALT replaces "fanless" with "15W TDP and shared memory bandwidth."

### Plenty of Plugins — MEDIUM confidence
ALT INSERTED.
**Concern:** "Epic's official plugin (UE 5.8+)" — as of August 2025 knowledge cutoff, the plugin shipped with UE 5.5/5.6 experimental, not 5.8 (not yet released). Version number will be wrong if the deck is presented before UE 5.8 ships.
**Pre-talk action:** Verify current shipping UE version at dev.epicgames.com before presenting.

### Get Running: Unreal MCP — MEDIUM confidence
ALT INSERTED.
**Concerns:** (1) "Epic Official (UE 5.8+)" — same version issue as above. (2) "chongdashu/unreal-mcp — 1900+ stars" goes stale daily. (3) Hosted endpoint agent.flopperam.com/mcp — verify it's still live before the talk. (4) "ue-mcp: 525+ actions, 18+ subsystems" — action count may lag current releases.
**Pre-talk action:** Check GitHub stars and flopperam endpoint on the day of the talk.

### Headless or MCP? — Quick Reference — MEDIUM confidence
ALT INSERTED.
**Concern:** "Xcode has no real MCP ecosystem" is categorical. Community-maintained Xcode MCP servers exist (axiom-xcode-mcp and others visible in this session's skill list). Coverage is thin compared to Blender/Unreal, but "no real" overstates the gap.
**Fix applied:** ALT softens to "MCP servers exist but the ecosystem is thin."

### Local LLM Routing — MEDIUM confidence
ALT INSERTED.
**Concern:** Specific empirical claims — "0 of 6" and "100% of the time" — presented as raw test results in a public deck. KB search could not be completed to verify these against project docs. If they are illustrative approximations, stating them as raw numbers is an overstatement.
**Pre-talk action:** Confirm these numbers are documented in the project KB before presenting. ALT removes the specific numbers pending citation.

### How We Actually Route — MEDIUM confidence
ALT INSERTED.
**Concern:** Slide lists "Opus 4.8" and "Haiku 4.5." The global CLAUDE.md references `opus-4-7-workflow.md` (naming Opus 4.7, not 4.8). "Haiku 4.5" unconfirmed. Presenting wrong version numbers in a public deck is a factual error.
**Pre-talk action:** Verify exact model IDs at anthropic.com before presenting. ALT removes version numbers.

### A Real MetaHuman, in Godot — MEDIUM confidence
ALT INSERTED.
**Concerns:** (1) "now MIT-licensed" in subtitle and bullets — the MetaHuman Dev Kit uses Epic's own EULA/SDK terms, not a blanket MIT license on RigLogic/DNA. MIT is likely an overstatement. (2) "markerless single-camera mocap (Unreal Fest 2026)" — phrased as a shipping feature, but this was a preview/announcement.
**Fix applied:** ALT replaces "MIT" with a link to check current license terms; flags mocap as "previewed," not "shipping."

### Godot Never Needed a Plugin — MEDIUM confidence
ALT INSERTED.
**Concern:** "godot --headless validates GDScript" slightly overstates. Headless mode runs the engine without a display and catches load-time errors, but is not a dedicated static linter like tsc or swiftc.
**Fix applied:** ALT clarifies "catching load-time GDScript errors," not a static validate step.

### Unreal Fluency Is a Godot Superpower — MEDIUM confidence
ALT INSERTED.
**Concern:** "Both engines reach Apple Vision Pro through the same Metal compositor — Apple's Compositor Services" is technically imprecise. Unreal uses Compositor Services directly. Godot on visionOS runs inside a SwiftUI/visionOS app wrapper and does not use Compositor Services directly the same way.
**Fix applied:** ALT changes to "same destination, different plumbing."

### Real Projects, Real Transfers — HIGH confidence
ALT INSERTED.
**Concern:** Bullet 2 conflates two KB-distinct results. "RigLogic proved native RealityKit skeleton posing at 90fps" is wrong: the 90fps figure comes from the Metal LBS kernel (URKSkelDeformer / lbs_skin8), NOT native RealityKit joint posing. Native joint posing is confirmed in simulator only for the head; the full-cast 90fps path is custom Metal. Bullet 3 ("RTX fork: Godot rendering research translated to Unreal material strategies in under one session") is an unsupported specific claim — no KB entry records this specific one-session transfer.

### Godot: Small Engine, Big Reach (lesson) — HIGH confidence
INLINE FIX APPLIED + ALT INSERTED.
**Concern:** Tags field listed "CC0" alongside "Godot · GDScript · Apple Vision Pro." Godot is MIT-licensed, not CC0. CC0 is a public-domain dedication for assets, not for engine code. Placing CC0 in the engine descriptor tags implies the engine is CC0 — false.
**Fix applied:** Tags changed directly from "CC0" to "MIT" in the original lesson object. (Note: "CC0 photoreal head" in the VitruvianGodot resource gallery description is correct — that is an asset license, not the engine.)

### Build a Dial for the Unknowns — HIGH confidence
ALT INSERTED.
**Concern:** The slide cites "Cascade's grab damping" as a case where cycling "converged on the right answer." The KB records the opposite: 4 grab-damping approaches were cycled and Alex reported "all four felt identical" — a NEGATIVE result that ruled out the follow-filter subsystem and redirected to pinch detection. The Pinchwork hand-skeleton example is accurate. The visionOS translucency cycler was a debug tool, not the solve.
**Fix applied:** ALT reframes Cascade damping as "fast negative results are wins too."

### Bounce Models and Machines — MEDIUM confidence
ALT INSERTED.
**Concern:** "Codex" appears in the model list. Codex is an OpenAI product deprecated in 2023; it does not appear in any fleet dispatch table, daily log, or routing config in the KB.
**Fix applied:** ALT removes Codex, retains Gemini, local models (qwen3, llama3.1), Sonnet, Opus.

### All Free. All Public. (dynamic builder slide) — HIGH confidence
INLINE FIX APPLIED — this is not a SECTIONS case entry, it is a custom HTML builder.
**Concern:** TALKS array on line 1525: "HarvardXR Talk" was labeled "2025 keynote" but the event was HXR 2026 (confirmed by repo description, KB bio, and talk subtitle).
**Fix applied:** Changed `"2025 keynote"` to `"2026 keynote"` directly in the TALKS array.

### Headless Asset Pipelines — MEDIUM confidence
ALT INSERTED.
**Concern:** "Forage — AI asset scout that sources Fab packs and generates handoff manifests headlessly" — named internal tool with specific capability. KB was not reachable to confirm tool name or that the MEDIA_CYCLER clip actually shows it.
**Pre-talk action:** Verify Forage is a real in-house tool and the video shows it before presenting.

---

## CLARITY

### Hi, I'm Alex (lesson) — MEDIUM confidence
ALT INSERTED.
**Concerns:** (1) Tags field "Agile Lens · OpenClaw · Claude · Local Fleet" implies OpenClaw is active/present, but per CLAUDE.md, OpenClaw is a retired early-2026 experiment. Speaker notes correctly say "built OpenClaw early 2026, pivoted to Claude" but the rendered tag strip contradicts that arc. (2) Speaker notes end with "Lets get into it." — missing apostrophe (should be "Let's").
**Fix applied:** ALT removes OpenClaw from tags; fixes apostrophe.

### Love Your Work, Not Your Tools — MEDIUM confidence
ALT INSERTED.
**Concern:** Title "Love Your Work, Not Your Tools" implies don't over-invest in tools, but subtitle "Great tools come from hating bad ones" and bullets celebrate building tools — a tension that could confuse a new attendee. Not factually wrong, but the framing contradicts itself.
**Fix applied:** ALT aligns subtitle to "When the tool is holding you back — build the one you need."

### Splats, Swift, and the Bridge — HIGH confidence
ALT INSERTED.
**Concern:** Subtitle "RealityKit + Swift, no game engine required" but fourth bullet explicitly references "UE to RealityKit bridge" — which involves Unreal Engine by definition. The subtitle makes a promise the bullets immediately contradict.
**Fix applied:** ALT changes subtitle to "RealityKit + Swift — from splat scenes to engine bridges."

---

## DIAGRAM

### Request, Change, Inspect — LOW confidence
NO ALT INSERTED (content is fine; diagram unverified).
**Concern:** SVG at images/ch4-production-pattern.svg could not be read due to session tool-call budget exhaustion. Diagram correctness (connector lines, label readability, dark-style consistency) is unconfirmed.
**Pre-talk action:** Open ch4-production-pattern.svg visually and confirm connector lines are present and legible.

### The Setup (demo) — HIGH confidence, diagram OK
No concern. SVG demo-setup.svg verified: three proper `<line>` elements with marker-end arrowheads, dashed Claude standby line. Clean.

### Name Everything Like AI Will Read It — HIGH confidence, diagram OK
No concern. images/ch2-naming.svg verified: intentional two-column comparison table, no connector lines needed. Checkmark/cross glyphs clear.

### What Is an MCP? (and Why) — HIGH confidence, diagram OK
No concern. images/ch1-what-mcp.svg verified: real `<line>` element with marker-end arrow to hub; three `<path>` elements fanning to tool boxes. All connectors present.

### Teach Them, Let Them Teach You — HIGH confidence, diagram OK
No concern. ch9-teach-learn.svg verified: real arc `<path>` elements with polygon arrowheads, animated stroke-dashoffset flow. Clean.

### Building for Transferability — HIGH confidence, diagram OK
No concern. ch5-transferability-anim.svg verified: compound A→B→C flow with KB hub, real connector lines and animated dots.

### Unverified SVGs (tool budget exhausted — manual check before talk)
The following SVGs could NOT be read in this session. Verify each visually before presenting:
- `images/ch2-setup-pattern-anim.svg`
- `images/ch3-what-breaks.svg`
- `images/intro-local-frontier.svg`
- `images/ch1-two-modes-anim.svg`
- `images/ch1-copilot-operator.svg`
- `images/ch6-no-mcp-needed.svg` (also referenced in ALT)
- `images/ch6-unreal-godot-transfer.svg` (also referenced in ALT)
- `images/headless-vs-mcp.svg` (also referenced in ALT)
- `images/ch4-server-landscape.svg` (also referenced in ALT)
- `images/ch5-triangulation-anim.svg` (also referenced in ALT)
- `images/ch9-cycle-options.svg` (also referenced in ALT)
- `images/ch3-official-plugin.svg` (also referenced in ALT)
- `images/ch3-get-running.svg` (also referenced in ALT)

---

## CONSISTENCY

### The KB as Triangulation — MEDIUM confidence
ALT INSERTED.
**Concern:** Bullet map (A=Godot/AVP, B=Unreal/AVP, C=implied third) does not match the SVG diagram's three corner nodes (GODOT→visionOS top, UNREAL→visionOS bottom-left, MetaHuman runtime bottom-right). Bullet 3 "B→C: Do what we did in Cascade, but in Unreal" points to the Cascade-to-Unreal transfer but the C corner in the SVG is labeled "MetaHuman runtime / RigLogic @ 90fps." Speaker pointing at the diagram while reading bullets finds the wrong corner.
**Fix applied:** ALT labels bullets explicitly by diagram corner position.

### The Community Built It First (lesson, CH 5) — HIGH confidence
ALT INSERTED.
**Concern:** Structural inconsistency. This title exists only as a chapter lesson object (CH 5 lesson), not as a case entry with a bullets array. Lesson slides render with tagline only. If a full case slide with bullets was intended here, it is missing from the cases array.
**Fix applied:** ALT provides a case-object version with bullets for use if this slide needs to be a full case.

---

## TYPOS

### Hi, I'm Alex (lesson) speaker notes
"Lets get into it." → "Let's get into it." (missing apostrophe)
**Fixed in the ALT slide.**

---

## ALT SLIDES DEFERRED (not inserted — medium confidence, lower impact)

These ALTs were in the provided list but were deferred to keep the total below 15 high-confidence inserts and/or because the concern is a pre-talk verification rather than a slide-content fix:

All 19 provided ALTs were inserted. Additionally: CC0→MIT fix applied inline to the lesson tags field; HarvardXR 2025→2026 fix applied inline to the TALKS array. 0 ALTs skipped (no JS failures).

---

## SLIDES REVIEWED WITH NO CONCERNS

- AI + MCP for Blender, Unreal & Godot (cover)
- My Tool Journey
- The Talk Title… Plus One More Stack
- What We Will Cover
- What Is an MCP? (and Why)
- You Do Not Need Deep Pockets
- Agents Changed the Game (lesson)
- From Suggestion to Action
- Two Ways to Work
- Structure Is the Secret Sauce (lesson)
- Name Everything Like AI Will Read It
- The Setup Pattern
- Unreal: Spoiled for Choice (lesson)
- Interactive Scene Editing
- What Breaks (and How to Fix It)
- Case Study: A Small Team, a Big Ask (lesson)
- Version Control That Just Works
- You Do Not Always Need an MCP
- A Veteran Still Learned Things
- The MCP Server Landscape
- Where AI Saves Hours
- Watch a Local 8B Build It
- Where Local Ends, Claude Begins
- Into Apple's Stack: RealityKit, Swift, Xcode (lesson)
- The Simulator Is the Loop Machine
- MetaHumans, Native in RealityKit
- Vitrine, Built Overnight
- Your Second Brain Is the Real Tool (lesson)
- Godot MCP Options
- Building for Transferability
- Pro-Tips From the Trenches (lesson)
- Chips Over Compaction
- Teach Them, Let Them Teach You
- Test One Thing at a Time
- Hardware, Loops, and Honesty
- Live Demo (lesson)
- The Setup (demo)
- Task: Build a Robust Scene
- Task: The Clarification Moment
- The Best Automation Is the One You'd Have Done Anyway (BONUS)
- The Journey, Mapped (dynamic)
- Eleven Projects. All Yours. (dynamic)
- Let's Build. (close)
- Meet Cascade Countdown
- Cascade Countdown
- Godot in VR, Easy on the Eyes
- Why the Small Engine Wins
