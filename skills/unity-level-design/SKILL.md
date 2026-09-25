---
name: unity-level-design
description: Level-design principles (pacing, pathing, signposting, blockout methodology) plus practical ProBuilder/justgame mechanics for building Unity levels programmatically. Use whenever building, reviewing, or planning a level/arena/blockout in a Unity project via the justgame MCP server — from a brief, a blueprint image, or a bare request to "build this level."
---

# Unity Level Design — Principles + justgame/ProBuilder Playbook

Two halves: **what makes a level good** (from *Introduction to Level Design in Game Development and in Unity*, Unity's official e-book, 2023/Unity 2022 LTS) and **how to actually build one with justgame** (from hands-on validated experience wiring ProBuilder into justgame and building a level with it). Apply both — geometry that's structurally sloppy defeats good pacing, and good pacing ideas are wasted if the blockout takes forever to iterate on.

## Part 1 — Design principles

### Know who you're building for
Bartle's Taxonomy: **Killers** (competition/rank), **Achievers** (goals/status), **Socialites** (social play), **Explorers** (discovery). Identify which the level serves and build toward that — don't dilute a level trying to please all four. A competitive arena serves Killers/Socialites; an open exploration space serves Explorers/Achievers.

### The 3Cs — tune these together, not in isolation
**Camera** (FOV, framing, what's occluded — first-person limits rear awareness, isometric gives full surround), **Character** (abilities, how gradually they're taught, strength vs. challenge pacing), **Control** (input device — widen corridors or reduce action density for analog-stick precision vs. mouse/keyboard). Lock these — and the character's metrics (height, crouch height, collider size, jump distance) — in a small test **gym/zoo** scene before building real content. Changing metrics after cover/obstacle placement is expensive rework.

### Player pathing — four categories, don't conflate them
- **Critical path**: longest route needed to see/test all shippable content.
- **Golden path**: the *best* route (most rewarding), not necessarily the longest — these are explicitly different things.
- **Secondary/tertiary paths**: side content, ideally one per supported playstyle (stealth/combat/hacking, etc.). Never make a player backtrack through already-drained, non-rewarding space. Reward dead ends and path endpoints, even minimally.

### Teaching mechanics
- Break a mechanic into ordered sub-skills (press → hold → combine → chain) and introduce them easiest-first.
- **Rule of Three**: have the player perform a new mechanic at least 3 times before treating it as learned, then escalate.
- **Subvert, don't break**: once a pattern is trusted, twist the *outcome* without changing the *input* (e.g., the same jump-attack works on an armored enemy, just takes two hits instead of one).

### Directing attention (four tools)
1. **Lighting** — light pulls players toward a path; darkness signals danger/keeps them out.
2. **Physical blockers** — mark boundaries with a visible cue; don't rely on invisible walls alone. (Common containment patterns: instant-death void beneath a suspended space, resource-scarcity soft limits, or a timed shrink/warning boundary.)
3. **Signposting** — landmarks visible from a distance, and consistent color language (red = danger, green = go).
4. **Sound** — reinforces the other three; pair with a visual/UI cue too (accessibility).

### Pacing
Own the tempo deliberately — sketch it as a beat timeline before building. Remove time limits to invite exploration; add them for urgency. Give a low-intensity **respite beat** after a high-intensity one.

### Environmental storytelling
Ground any scene by implicitly answering: **Why is this happening? What happened? Where? When? How?** Prefer implication over exposition text.

### Spawns, saves, checkpoints
- Spawn the player already facing the direction of travel.
- **Checkpoints** (temporary, in-memory) vs. **save points** (explicit/manual, or free-save with an enemy/position reset) are different tools — pick deliberately.
- **Avoid soft-locks**: test every checkpoint for (a) reload-into-collision, (b) a save that leaves the player unequipped to progress *or* retreat, (c) a save that guarantees death.
- Don't place a save immediately before an unskippable cutscene leading into a hard section — repeated failure means repeated cutscene-watching. Put a checkpoint between two chained hard challenges (e.g., platforming right before a boss).

### Blockout methodology (apply this before any art pass)
1. White-box with simple shapes — prioritize layout correctness over looks.
2. Name blocks descriptively (use/location/dimensions) and color-code by function (interactive vs. static, breakable vs. not) so intent survives a handoff.
3. Get design sign-off on the whitebox *before* spending art budget — quote worth internalizing: "you don't want to be [paying for models] until you're sure your level is exactly how you want it to be."
4. Test relentlessly: doorway camera clearance, winding-path readability, slope traversal (including deliberately-impassable slopes), jump distances, trigger placement.

### On hard numbers
This source is deliberately thin on universal numeric standards (no fixed corridor-width or room-size table) — its own position is that **metrics come from your character/camera/input, tested in a gym, not copied from a book**. If the current project already derives its own canon this way (check for a `LEVEL_DESIGN.md` / `GDD.md` / `Appendix A` — e.g. a `Docs/LEVEL_DESIGN.md` that derives every corridor width, cover cap, and ramp gradient from player speed, collider size, and camera geometry, with the derivation shown), **that project's derived numbers are canon — use them, don't substitute generic ones.** Absent that, derive minimums the same way: corridor width ≥ character collider + clearance + dash/roll distance if one exists; cover height in bands relative to character height (kerb / low / chest / full); ramp angle bounded by whatever traversal-speed-vs-camera-shear math applies to your rig.

## Part 2 — Building it with justgame + ProBuilder

### Two build modes — pick based on scale
- **A handful of pieces, interactive/exploratory work**: call justgame's ProBuilder tools directly (`create_probuilder_shape`, `inspect_probuilder_mesh`, `extrude_probuilder_faces`, `bevel_probuilder_edges`, `subdivide_probuilder_faces`, `delete_probuilder_faces`, `weld_probuilder_vertices`, `set_probuilder_material`). Good for prototyping a mechanic, testing a doorway, or one-off adjustments.
- **A whole level from a brief or blueprint (dozens+ of pieces)**: write a persistent C# generator script (`Assets/Scripts/Editor/<LevelName>Generator.cs`, mirroring any existing `*BlockoutGenerator.cs` in the project) that builds the entire level programmatically using ProBuilder's `ShapeGenerator` API directly, then invoke its static `Generate()` method once via justgame's `execute_csharp`. One compile + one execution beats dozens of individual tool round-trips, and the script is a reusable, tweakable asset afterward — not a throwaway. This is how the Logistics Hub level (2026-07-21) was actually built.

### The generator-script recipe
1. **Coordinate plan first.** Fix an origin and axis convention (e.g., +X east, +Z north, Y=0 ground) and write down every room/zone's extent in that frame *before* writing code — most bugs in a first pass are arithmetic slips in this step, not API misuse.
2. **Every solid is a `ShapeGenerator` call**, not `GameObject.CreatePrimitive`: `GenerateCube` for boxes (walls, floors, pillars, crates — set the size vector's components directly per axis, never rotate an axis-aligned box), `GenerateDoor` for a wall panel with a built-in doorway cutout (cheaper than manually flanking a gap with cubes), `GenerateArch` for a walk-through archway frame, `GenerateStair` for real stepped geometry, `GenerateCylinder`/`GenerateIcosahedron`/etc. for anything rounder.
3. **Materials**: create dedicated `.mat` assets for the new level (`Greybox_<LevelName>_<Purpose>`) — **never reuse another level's shared material asset**, even by name-lookup; overwriting its color/shader repaints that other, possibly-shipped level too. Use a `Lit` shader with a real light in-scene if the level needs to be visually reviewable; an `Unlit` near-black palette (seen in some projects) is a deliberate art-direction choice tied to that specific project's contrast rules, not a default to copy blindly.
4. **Wall-with-opening pattern**: decompose a wall run around a door/gate gap into flanking solid cubes plus either a `GenerateDoor` panel (self-contained, has its own header/legs) or open space with a `GenerateArch` frame — see the recipe in any `*Generator.cs` file's `WallRunXDoored`/`WallRunZDoored`-style helpers.
5. **Boolean ops (union/subtract/intersect) are not safely available.** ProBuilder's `CSG` class is internal to its own assembly and gated behind an experimental compile define with no headless entry point — don't attempt them from generator code; use door/arch shapes or manual gap decomposition instead.
6. **Colliders**: `ShapeGenerator.*` shapes don't get one automatically — add explicitly: `go.AddComponent<MeshCollider>().sharedMesh = go.GetComponent<MeshFilter>().sharedMesh;`. Guard against assigning a collider mesh with zero vertices (e.g., after deleting every face) — Unity logs a native error otherwise; check `mesh.vertexCount > 0` first.
7. **`ProBuilderMesh.renderer` / `.mesh` are `internal`** to ProBuilder's own assembly — inaccessible from project code even though they read as public in some docs. Use `go.GetComponent<MeshRenderer>()` / `go.GetComponent<MeshFilter>().sharedMesh` instead.
8. **Some ProBuilder classes are internal despite public-looking methods** — the class itself lacks the `public` modifier (e.g. `Subdivision` in v6.1.2). Grep the actual installed source under `Library/PackageCache/com.unity.probuilder@.../Runtime` for `public static class` rather than trusting API docs, which can be thin or stale for newer versions. Where a convenience wrapper is internal, its public building block usually isn't — e.g. `Subdivide()` is just `ConnectElements.Connect(mesh, faces)` under the hood, and `ConnectElements` itself is public.
9. **`using UnityEditor;` + `using UnityEditor.ProBuilder;` together creates an ambiguous `EditorUtility`** (ProBuilder ships its own class of that name). Fully qualify: `UnityEditor.EditorUtility.SetDirty(...)`.
10. **New scene vs. reuse**: if the level is genuinely new content (not a revision of an existing shipped level), give it its own scene (`EditorSceneManager.NewScene` + a new path) rather than building into whatever scene happens to be open.

### Verifying a generator actually ran correctly
- Unity's own file watcher can auto-recompile a saved edit *before* an explicit `recompile`/`execute_csharp` call resolves — two edits made in quick succession can each trigger their own reload, and a test issued right after "the server is back up" can land on a stale intermediate build. **Confirm `ping`'s `reloadCount` actually advanced past the count from the specific edit you're testing**, not just that the port answers.
- `execute_csharp_result` reports `"status": "compiling"` while its temp script's containing assembly is still building — if a *different* file in the same assembly has a compile error, the temp script will report "compiling" forever (its own cleanup code never runs because the assembly never finishes building). If this happens, read Unity's raw log directly rather than trusting the console-capture tool, which can lag or miss build-pipeline errors entirely: `tail -100 <ProjectPath>/Logs/Editor.log | grep "error CS"`. Fix the real error, then `execute_csharp_result` with `abort: true` to clear the stuck temp script before retrying.
- After a clean run, sanity-check with `scene_hierarchy` (object count, spot-check a few positions) and `screenshot` — an orthographic top-down camera (`orthographic = true`, high `Y`, `rotation = (90,0,0)`) is far more useful than a perspective angle for checking plan proportions against a blueprint.
- If something looks structurally wrong (a room reads as a wedge instead of a rectangle, a zone is narrower than intended), it's almost always a constant reused for the wrong axis/parameter in the coordinate plan — recheck the plan from step 1 before suspecting the ProBuilder API.

### Editor grid & snapping
Unity's Scene-view grid snapping is **off by default** even when the visible grid overlay is showing — check `UnityEditor.EditorSnapSettings.snapEnabled` before assuming manual drags land on-grid. A generator script (see above) doesn't need this — its coordinates are already exact — but any manual nudging of an object in the Scene view (by a human or by an AI dragging via the Move tool) will silently produce off-grid, non-round positions until snapping is turned on. Set `EditorSnapSettings.move` to match the project's actual grid unit (commonly 1m — check `LEVEL_DESIGN.md`/`GDD.md` for a stated "grid unit" rather than assuming) rather than leaving Unity's fussier 0.25m default. This is a project-wide Editor preference, not scene data — set it once, it persists.

### justgame's tool surface for this (as of 2026-07-21)
`create_probuilder_shape` (Cube/Stair/CurvedStair/Prism/Cylinder/Plane/Door/Pipe/Cone/Sprite/Arch/Sphere/Torus, with an optional MeshCollider), `inspect_probuilder_mesh` (face index/center/normal — call before targeting faces by index), `extrude_probuilder_faces`, `bevel_probuilder_edges`, `subdivide_probuilder_faces`, `delete_probuilder_faces` (requires explicit face indexes — refuses if omitted, won't silently wipe a mesh), `weld_probuilder_vertices`, `set_probuilder_material`. All wrap edits in `Undo.RegisterCompleteObjectUndo`. `execute_csharp` / `execute_csharp_result` are the escape hatch for anything bigger, including invoking a generator script's `Generate()` method.

## Sources
- *Introduction to Level Design in Game Development and in Unity*, Unity Technologies (2023, Unity 2022 LTS edition), 112 pages — `~/Downloads/UNITY_Ebook_Introduction_to_level_design_in_game_development_and_in_Unity_V2.pdf`. Read in full for Part 1; the book is light on hard numeric standards by design (see "On hard numbers" above).
- Hands-on justgame + ProBuilder integration work (2026-07): informs all of Part 2.
- See also the `justgame-unity-mcp` memory for the MCP-server-level gotchas (domain reload timing, Undo requirements, optional-package `versionDefines` pattern) that this skill's Part 2 assumes.
