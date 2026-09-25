---
description: Build/reproduce something to exactly match reference image(s), then verify by comparing the result against the reference before declaring done.
argument-hint: [reference image path(s)] [what to build / target]
---

# Replica workflow

Goal: reproduce **exactly** what the reference image(s) show — not "inspired by," not "close enough." Treat the image as the spec. This applies regardless of domain: frontend/UI code, a 3D asset (Blender via `justthreed`), a Unity level/prop (via `justgame`), a Figma design, an icon, a document layout, or any multi-step workflow that chains MCP tools to produce a visual artifact.

Arguments: $ARGUMENTS — one or more reference image paths/attachments, plus a description of what to create and where (which project, which tool/pipeline). If the target or scope is ambiguous, ask before building.

## Steps

1. **Read every reference image closely first.** Use the Read tool (or the relevant MCP viewer) on each reference image before writing any code or calling any creation tool. Note concretely, in your own head, not just vibes:
   - Layout/composition, proportions, spacing, alignment
   - Exact colors (name them or estimate hex if it matters), materials/finish for 3D
   - Typography, iconography, and any text content verbatim
   - Small details that are easy to skip (shadows, borders, corner radii, bevels, prop counts, states)
   - If multiple reference images show different states/angles, treat them as one combined spec.

2. **Identify the right domain and tools before building:**
   - Frontend/UI clone → existing project's component/icon library and styling conventions (check for a `frontend-style` skill or similar project convention) first; don't invent new patterns.
   - 3D asset → `justthreed` MCP (Blender). Call `get_scene_info` first, build, then `get_viewport_screenshot` to check.
   - Unity level/prop → `justgame` MCP, following the `unity-level-design` skill if relevant.
   - Figma → the `claude_ai_Figma` tools, loading `/figma-use` first per its own instructions.
   - Web page/app UI → build it, then use `claude-in-chrome` to screenshot the rendered result.
   - If none of these fit, just build it with the normal tools for that file type.

3. **Build to match the reference exactly.** Don't add scope, don't restyle to "improve" it, don't substitute a similar-but-different asset/icon/component unless the reference is genuinely ambiguous — in that case, ask rather than guess.

4. **Verify against the reference — this step is mandatory, not optional:**
   - Produce a visual artifact of the actual result: a browser screenshot (`claude-in-chrome`), a Blender viewport screenshot (`justthreed`/`blender` MCP), a Unity/game screenshot (`justgame`), a Figma screenshot (`Figma` MCP), or a rendered export — whichever fits the domain.
   - Put the reference image and the result side by side (or view them back to back) and do an explicit comparison pass: layout, colors, proportions, text, missing/extra elements.
   - List concrete mismatches found, even minor ones.

5. **Iterate.** Fix each mismatch and re-verify (repeat step 4) until the result matches the reference, or until remaining gaps are genuinely unachievable (e.g. platform limitation) — in which case say so explicitly and explain why, rather than silently shipping a divergence.

6. **Report tersely**: what was built, where, and a one-line confirmation that it was checked against the reference (plus any accepted/explained deviations). Don't narrate the whole comparison process — just the outcome.

## Notes

- Icon sourcing: if a UI needs an icon not in the project's existing icon library, follow the standing iconscout fallback rule (search/preview freely; download needs explicit permission).
- Never claim "matches the reference" without having actually produced and looked at a screenshot/render of the result. Type-checking or tests passing is not visual verification.
- Downloading/publishing anything externally (uploading screenshots to third-party tools, pushing code, etc.) still follows the normal action-permission rules — this workflow doesn't grant extra authority, only structures the build+verify loop.
