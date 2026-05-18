# Contributing

Thanks for helping keep this awesome list useful, focused, and easy to scan.

## Scope

This list tracks reinforcement learning, RLHF, reward optimization, and preference optimization for image and video diffusion models.

## Good Fits

- Image or video diffusion papers using RLHF, PPO, GRPO, RLOO, DPO, reward-weighted training, preference optimization, or reward guidance.
- Reward models, human preference datasets, aesthetic rewards, vision-language rewards, benchmarks, and evaluation protocols used for image/video diffusion alignment.
- Official codebases, project pages, datasets, and toolkits for RL-based diffusion post-training.

## Usually Out of Scope

- Diffusion models used as RL policies, planners, or dynamics models.
- General LLM RLHF papers with no direct image/video diffusion use.
- Audio, 3D, robotics, molecule, or text diffusion papers unless clearly useful background for image/video diffusion alignment.

## Entry Format

Use this table format:

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |
| 2025 | [VideoDPO: Omni-Preference Alignment for Video Diffusion Generation](https://arxiv.org/abs/2412.14167) | arXiv | T2V | DPO | [Paper](https://arxiv.org/abs/2412.14167) |

## Task Tags

- `T2I`: Text-to-image generation.
- `I2I`: Image-to-image generation or editing.
- `T2V`: Text-to-video generation.
- `I2V`: Image-to-video generation.
- `V2V`: Video-to-video generation or editing.
- `Unified`: Covers multiple image/video diffusion tasks in one system, benchmark, dataset, or method.

## Method Tags

Use one or more of these method tags:

- `RLHF`
- `PPO`
- `DPO`
- `GRPO`
- `RLOO`
- `Reward Model`
- `Reward Guidance`
- `Benchmark`
- `Toolkit`

## Ordering Rules

- Add new entries newest first in the most relevant section.
- Put each paper in one primary section.
- Include secondary methods in the Method column.

## Source Quality

Prefer arXiv or conference pages, official project pages, official GitHub repos, and dataset or benchmark pages. Avoid entries supported only by social posts, slides, or third-party summaries without a public technical source.

## Pull Request Checklist

- The entry is in scope for image/video diffusion alignment.
- At least one public technical link is included.
- Task and method tags are filled in.
- The entry is placed newest first in the relevant section.
- The entry does not duplicate an existing item.
