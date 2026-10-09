# VOX Style Library (bundled reference)

Unified visual / narrative spec distilled from reference samples (FRMWRKD-EXPLAINED, Jackson's AI, AIpreneur). Use this as the single source of truth for style when generating Vox-style videos.

## Unified visual spec

### Palette
- Low-saturation, desaturated neutral-gray base / soft colors; **2.5D layered** (foreground / midground / background planes clearly separated with parallax depth).
- Single accent highlight color (yellow highlighter or theme color) for key data / words.
- No high saturation; flat **2.5D layered** rendering with parallax depth — NOT full volumetric 3D render, and NOT pure flat 2D.

### Typography / captions
- Bold condensed kinetic typography (FRMWRKD lineage) OR restrained documentary typography (Jackson / AIpreneur lineage).
- Text is part of the composition (with drop shadows / typewriter reveal), not a hard-subtitle bar pasted on top.
- On-screen captions reinforce key facts and names from the narration.

### Transitions
- Paper-cut / collage hard cuts, light cuts, simple fades.
- No dramatic transitions, no effect stacking.
- Transition is secondary; each scene carries itself via "one visual anchor per screen".

### Fixed visual motifs (lock these in the reference-image library)
- Magazine-style collage, archival photographs, annotated maps (thin white leader lines + labels).
- Paper texture, film grain, halftone quality.
- Paper-cut layered illustration, flat backgrounds.
- ONE visual anchor per screen: map zoom / an archival photo / a data chart / a typographic moment.

## Unified narrative spec

### Tone
- Calm, curious, documentary narrator; like telling a friend an interesting fact. Conversational, natural.

### Opening hook (first 5s decides retention)
- Counter-intuitive fact / question.
- e.g. "In 1925 Paris, someone sold the Eiffel Tower twice." / "What if Earth suddenly stopped spinning?"

### Pacing
- Narration-driven, NOT picture-driven.
- Single shot 4–8s (FRMWRKD leans 5–6s slow; Jackson 5–8s; AIpreneur 4–8s).
- Script ≈ 130–150 words / 60s; one sentence = one scene; split a sentence with two actions / locations into two shots.

## Reusable prompt framework

### 4.1 Fixed style sentence (MUST appear verbatim in every image prompt)
```
Vox-style 2.5D layered paper-cut collage motion graphic with clear foreground/midground/background plane separation and parallax-ready depth, flat layered illustration, muted desaturated palette with a single accent highlight color, annotated maps and archival photo textures, halftone paper grain, bold condensed kinetic typography, one clear visual anchor per scene, documentary infographic aesthetic --ar 16:9
```
Chinese equivalent: VOX 式 2.5D 分层剪纸拼贴动态图文，前后景明显分层并带视差景深，扁平分层插画，低饱和中性调 + 单一强调色，注释地图与档案照质感，半调纸张颗粒，粗体压缩动态文字，每屏一个视觉锚点，纪录片信息图美学，16:9

> 2.5D layered depth is the default (user-confirmed 2026-08-27: "月球崩塌" 2.5D 效果获赞，要求全片统一大幅 2.5D 纵深). 出图时务必让前景元素离镜头最近、背景最远，制造三层明显纵深，便于视频强视差运镜。

### 4.2 Image prompt template (per beat)
```
[4.1 style sentence] + [specific scene: subject / action / setting] + [shot type: map zoom / archival photo / data chart / typographic moment] + [negative: avoid high saturation, 3D render, flashy effects, text morphing]
```
Example: `[style sentence] A vintage archival photo of a 1920s Paris street transforming into a paper-cut illustration, annotated with a white leader line pointing to the Eiffel Tower, single yellow accent on the tower --ar 16:9`

### 4.3 Video prompt template (image-to-video)

**⚠️ 动效强度准则（关键，避免"看着没动"）**
- 图生视频模型会过度遵从 `gentle / subtle / slight / static / barely / minimal / faint / soft motion` 这类词，结果运动幅度极小、几乎看不出变化。**这些弱化词一律禁用。**
- 每个 prompt **必须写清「动什么 + 怎么动 + 幅度明显可见」**。即使要慢，也写 `slow but clearly visible motion`，明确"可见"。
- 优先用强动词：`flow / stream / pulse / swell / crash / rush / recede dramatically / rotate / spin / slide / zoom in sharply / expand / collapse / assemble energetically / grow visibly`。
- 时长：单镜 5–8s。**1080P 易超时，统一用 720P 更稳**（已实测：1080P 偶发 600s 超时，720P 稳定）。

**模板 A — 动作型镜头（潮汐/引力/旋转等）**
```
[强动词描述明确运动] + [幅度/节奏: energetic / rhythmic / clearly visible] + strong parallax depth (foreground moves faster than midground than background) + camera gently pushes in / orbits to reveal layered depth + keep 2.5D paper-cut layered texture + no text morphing + 5-8s
```
Example: `Energetic flowing arrows stream from the Moon toward Earth's ocean with strong parallax depth, foreground arrows move faster than midground, tidal waves swell and crash rhythmically, the moon pulses with light, camera gently pushes in, keep 2.5D paper-cut layered texture`

**模板 B — 构图/信息图型镜头（也要动起来，不能"static"）**
```
[主体明显运动: zoom in sharply / rotate / slide apart / layers shift] + [辅助动画: arrows fade in, labels draw themselves visibly] + strong parallax depth (foreground elements drift faster than background) + camera slowly orbits / pushes in + keep 2.5D paper-cut layered texture + 5-8s
```
Example: `Camera zooms in sharply on the paper-cut diagram with strong parallax depth, foreground leader lines draw themselves clearly faster than background, arrows glow and pulse, keep 2.5D paper-cut layered texture`

### 4.4 Narration script framework (per minute)
- Hook (1 counter-intuitive sentence / question)
- Background (2–3 setup sentences)
- Body (main, scene-by-scene, one sentence per shot)
- Close (1 twist / uplift sentence)
- Word budget: 130–150 words / minute

### 4.5 Captions & editing spec (user-confirmed 2026-08-27)
- **Captions**: white text + dark stroke/outline (never light text on light paper background); highlight keywords in accent **blue #2E6FB7** to match the on-screen accent.
- **No flashy caption effects** — only a 0.2s fade-in.
- **Transitions**: light cuts / simple fades only; no effect stacking.
- **BGM**: soft, low volume.
- **Assembly**: follow the storyboard timeline exactly; if a clip is short, use 0.4× slow-motion to stretch (e.g. shot 7's 6s clip slowed to ~15s to fill 60s).
- **Use only the 7 clips listed in the project's §6 asset list** for final assembly — the videos/ folder also contains older weak-motion / flat versions; do not use those by mistake.
