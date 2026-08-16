---
name: seven-layer-visual-director
description: Use when creating, editing, reconstructing, or iterating image or video generation prompts, especially when reference roles, identity consistency, scene locks, shot timing, motion continuity, or conflicting visual requirements need structured control.
---

# Seven-Layer Visual Director

Use an original seven-layer structure to turn visual intent into controllable image or video prompts.

## Workflow

1. Determine whether the request is for an image or video. If unclear, ask only: “这次做图片还是视频？” Then stop.
2. For a new task, read and return the complete blank template for the chosen mode, then stop:
   - Image: [references/image-template.md](references/image-template.md)
   - Video: [references/video-template.md](references/video-template.md)
3. If the user already supplied sufficiently complete information, map it into the seven layers without making them re-copy the template. Separate safe conservative defaults from omissions that materially change the result; ask the latter together.
4. Before compiling a final prompt, read [references/method-notes.md](references/method-notes.md) and [references/output-contract.md](references/output-contract.md). Follow the output order exactly.
5. Register each reference independently as identity, pose, composition, style, first-frame, or last-frame reference. Never let one reference silently control another role.
6. For revisions, state the affected layer first. Rewrite only that layer and the final prompt; preserve all other confirmed locks.
7. This Skill structures prompt work only. Do not call an image or video generator. If the user explicitly asks to generate, the current task decides separately which available tool to use.
8. Do not trigger for tasks unrelated to visual image or video generation prompts.

## Stop Conditions

- Do not output a final copyable prompt while result-changing information or conflicts remain unresolved.
- If “保持结构不变” conflicts with a new aspect ratio, ask the user to prioritize cropping, outpainting, or recomposition.
- Treat “只换脸” as a local edit, not a full redesign.
- Do not promise zero rerolls, fixed success, pixel-perfect replication, or absolute identity locking.
- Do not invent platform parameters, buttons, model names, or value ranges.
