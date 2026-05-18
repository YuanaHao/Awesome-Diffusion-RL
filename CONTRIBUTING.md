# Contributing

Thanks for helping keep this list useful and current.

## Scope

This repository tracks reinforcement learning, RLHF, reward optimization, and preference optimization for image and video diffusion models.

Good fits:

- Image or video diffusion papers using RLHF, PPO, GRPO, RLOO, DPO, reward-weighted training, preference optimization, or reward guidance.
- Reward models, human preference datasets, aesthetic rewards, vision-language rewards, benchmarks, and evaluation protocols used for image/video diffusion alignment.
- Official codebases, project pages, datasets, and toolkits for RL-based diffusion post-training.

Usually out of scope:

- Diffusion models used as RL policies, planners, or dynamics models.
- General LLM RLHF papers with no direct image/video diffusion use.
- Audio, 3D, robotics, molecule, or text diffusion papers unless they are clearly useful background for image/video diffusion alignment.

## Entry Format

Paper entries should use:

```markdown
| 2025 | [VideoDPO: Omni-Preference Alignment for Video Diffusion Generation](https://arxiv.org/abs/2412.14167) | arXiv | T2V | DPO | [Paper](https://arxiv.org/abs/2412.14167) |
```

Task tags:

- `T2I`: text-to-image
- `I2I`: image-to-image
- `T2V`: text-to-video
- `I2V`: image-to-video
- `V2V`: video-to-video
- `Unified`: multiple image/video generation settings

Method tags:

- `RLHF`
- `PPO`
- `DPO`
- `GRPO`
- `RLOO`
- `Reward Model`
- `Reward Guidance`
- `Benchmark`
- `Toolkit`

## Ordering

- Add papers newest first inside the most relevant method section.
- Put each paper in one primary section.
- If a paper spans multiple methods, choose the method that best describes its main contribution and include the secondary method in the `Method` column.

## Source Quality

Prefer stable, official links:

- arXiv or conference paper pages.
- Official project pages.
- Official GitHub repositories.
- Dataset or benchmark pages.

Avoid adding only social media posts, slide decks, or third-party summaries unless they point to a public technical source.

## Pull Request Checklist

- The entry is in scope for image/video diffusion alignment.
- The paper or resource link is public.
- The task and method tags are filled in.
- The entry is placed newest first in its section.
- The same paper is not duplicated elsewhere in the README.
