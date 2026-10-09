# VOX Science Video — Workflow Detail

## Tool-chain mapping (original → WorkBuddy)

| Step | Original tool | WorkBuddy substitute |
|------|--------------|----------------------|
| Script / prompt gen | Claude / DeepSeek | WorkBuddy directly |
| Batch image gen | Google Flow / Nano Banana / ZAPI Flow | **ImageGen** |
| Image-to-video | Veo / Gemini Omni | **VideoGen** (or seedance / kling as domestic alternative) |
| Composition editing | CapCut / 剪映 | Local GUI (WorkBuddy supplies storyboard + timeline; user assembles) |

Only the desktop editor click cannot be done by WorkBuddy. All materials (images + motion clips + storyboard + timeline) are prepared.

## Step-by-step procedures

### Step 1 — Knowledge base
- If user has Obsidian vault `VOX-Video-Refs/01-Reference-Videos`, read notes, extract style rules.
- Else use bundled `style-library.md`.
- Collect 5–10 references; extract palette / typography / transitions / motifs / tone / hook / pacing only.

### Step 2 — Script + prompts
- Choose niche.
- Write narration (§4.4), control word count.
- Split into beats (one per sentence).
- Per beat: image prompt = §4.1 + scene + shot + negative (§4.2).
- Per image: video prompt = §4.3.

### Step 3 — Storyboard + timeline
- Storyboard table columns: Time | Narration | Visual Anchor | Image Prompt | Video Prompt.
- Timeline: each beat 4–8s; sum runtime; align words to on-screen time.

### Step 4 — Assets + handoff
- ImageGen per §4.2 prompt.
- VideoGen / seedance / kling per §4.3.
- Deliver table + clips; user edits in CapCut / 剪映 / PR with subtitles + soft BGM + light transitions.

## Output format example (storyboard table)

| # | Time | Narration | Visual Anchor | Image Prompt | Video Prompt |
|---|------|-----------|--------------|-------------|-------------|
| 1 | 0:00–0:06 | Hook sentence... | Annotated map of Earth | [4.1] + spinning earth paper-cut, single red accent | Zoom in sharply + earth rotates visibly, 6s, 720P |
| 2 | 0:06–0:13 | Background sentence... | Archival photo | [4.1] + 1920s street photo → paper-cut | Photo layers slide apart energetically, 7s, 720P |
| 3 | 0:13–0:21 | Body sentence... | Data chart | [4.1] + bar chart of rotation speed | Bars grow visibly upward, 8s, 720P |

## Consistency rule
Reuse §4.1 style sentence verbatim in EVERY image prompt. This is the single most important factor for making 10+ clips look like one film.
