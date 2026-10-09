---
name: vox-science-video
description: This skill should be used when the user wants to create VOX-style science/explainer videos with AI. It codifies a narration-driven pipeline — build a reference knowledge base, generate script + style/image/video prompts, produce a storyboard with precise timeline, and prepare assets for local editing. Triggers include phrases like "Vox 视频", "VOX 科普视频", "跑 VOX 工作流", "生成 Vox 风格视频", "做解说类动画", "VOX style video".
agent_created: true
---

# Vox Science Video

## Overview
Codify the zero-to-publish workflow for VOX-style explainer/science videos. VOX style is NOT a single "generate Vox animation" command — it is four coordinated components: narration-driven storyboard, consistent style reference images, precise timeline, and post-production composition. This skill turns a topic into a full production package (script, image prompts, video prompts, storyboard table, timeline) that the user composes locally in CapCut / 剪映 / PR.

## When to use
- The user requests a Vox-style / paper-cut collage explainer video.
- The user mentions "VOX 视频", "科普动画", "解说类动画", "旁白驱动分镜".
- The user wants a reusable pipeline rather than a one-off generation.

## Workflow
Execute the four steps in order. Read `references/style-library.md` for the unified visual/narrative spec and reusable prompt templates; read `references/workflow-detail.md` for tool mapping and output formats.

### Step 1 — Build / use the reference knowledge base
- If the user has an Obsidian vault of reference clips (e.g. `VOX-Video-Refs/01-Reference-Videos`), read those notes to absorb style samples.
- Otherwise, work from the bundled style library in `references/style-library.md`.
- Key principle: collect 5–10 reference videos; extract only style rules (palette, typography, transitions, motifs, narration tone, hook, pacing), not full transcripts.

### Step 2 — Generate script + prompts
- Pick a niche (科普 / history / money&power / tech / disaster / sports).
- Produce a narration script using the framework in `references/style-library.md` §4.4 (hook → background → body → close; 130–150 words/min).
- Derive a list of visual beats (one scene per sentence).
- For each beat, write an image prompt by concatenating the fixed style sentence (§4.1) + specific scene description + shot type + negative constraints (§4.2).
- Write a video prompt per image using the §4.3 template (subtle parallax / piece-by-piece assembly, 5–8s).

### Step 3 — Generate storyboard + timeline
- Output a storyboard table: row per beat with [Time | Narration | Visual Anchor | Image Prompt | Video Prompt].
- Compute a precise timeline: assign each beat a 4–8s duration, sum to total runtime, align narration words to on-screen time.
- Deliver as a Markdown table the user can paste into a spreadsheet or editing software.

### Step 4 — Prepare assets + hand off to editing
- Generate images via ImageGen using the §4.2 prompts (flat paper-cut / collage, consistent palette).
- Convert images to motion clips via VideoGen (or seedance / kling) using §4.3 prompts.
- Hand the storyboard table + timeline + generated clips to the user for local composition in CapCut / 剪映 / PR (add subtitles, soft BGM, light transitions).
- Note: WorkBuddy cannot click the desktop editor GUI; provide all materials so local assembly is mechanical.

## Consistency rule (critical)
Reuse the exact same style sentence (§4.1) verbatim in every image prompt. Consistency across 10+ clips comes from repetition, not from a single magic prompt.

## Resources
- `references/style-library.md` — unified VOX visual/narrative spec + reusable prompt framework (style sentence, image/video prompt templates, narration framework).
- `references/workflow-detail.md` — detailed step procedures, tool-chain mapping (Claude / Google Flow / Veo / CapCut → WorkBuddy ImageGen / VideoGen / local edit), and output format examples.
