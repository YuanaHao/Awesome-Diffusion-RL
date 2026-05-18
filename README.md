# Awesome RL for Diffusion

A curated list of papers and resources on reinforcement learning, RLHF, and preference optimization for image and video diffusion models.

This repository focuses on **RL for diffusion generation**, especially image and video generation. It does not track the separate line of work on diffusion models used as policies, planners, or dynamics models in reinforcement learning.

## Scope

Included:

- RLHF and policy-gradient optimization for image or video diffusion models.
- DPO and preference optimization for text-to-image, image-to-image, text-to-video, image-to-video, and video-to-video generation.
- GRPO, RLOO, PPO-style, and related policy optimization methods for diffusion post-training.
- Reward models, feedback signals, and benchmarks used to optimize or evaluate image/video diffusion outputs.
- Reward guidance and test-time optimization methods when they directly target image or video diffusion alignment.

Out of scope:

- Diffusion models used as RL policies, planners, or dynamics models.
- General LLM RLHF papers without a direct image/video diffusion application.
- Audio, 3D, robotics, molecule, or text diffusion work, except as brief related context.

## Contents

- [Surveys & Overviews](#surveys--overviews)
- [Reward Models & Feedback Signals](#reward-models--feedback-signals)
- [RLHF / Policy Gradient](#rlhf--policy-gradient)
- [DPO / Preference Optimization](#dpo--preference-optimization)
- [GRPO / RLOO / Policy Optimization](#grpo--rloo--policy-optimization)
- [Reward Guidance / Test-time Optimization](#reward-guidance--test-time-optimization)
- [Benchmarks & Evaluation](#benchmarks--evaluation)
- [Toolkits & Codebases](#toolkits--codebases)
- [Related Areas](#related-areas)
- [Contributing](#contributing)

## Tag Guide

Task tags: `T2I`, `I2I`, `T2V`, `I2V`, `V2V`, `Unified`

Method tags: `RLHF`, `PPO`, `DPO`, `GRPO`, `RLOO`, `Reward Model`, `Reward Guidance`, `Benchmark`, `Toolkit`

## Surveys & Overviews

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |
| 2026 | [Advances in GRPO for Generation Models: A Survey](https://arxiv.org/abs/2603.06623) | arXiv | Unified | GRPO | [Paper](https://arxiv.org/abs/2603.06623) |
| 2025 | [Reinforcement Learning for Large Model: A Survey](https://arxiv.org/abs/2508.08189) | arXiv | Unified | RLHF, GRPO | [Paper](https://arxiv.org/abs/2508.08189), [Code](https://github.com/weijiawu/Awesome-Visual-Reinforcement-Learning) |

## Reward Models & Feedback Signals

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |
| 2025 | [VideoScore2: Think before You Score in Generative Video Evaluation](https://arxiv.org/abs/2509.22799) | arXiv | T2V | Reward Model, GRPO | [Paper](https://arxiv.org/abs/2509.22799), [Project](https://tiger-ai-lab.github.io/VideoScore2/) |
| 2024 | [VisionReward: Fine-Grained Multi-Dimensional Human Preference Learning for Image and Video Generation](https://arxiv.org/abs/2412.21059) | arXiv | Unified | Reward Model | [Paper](https://arxiv.org/abs/2412.21059), [Code](https://github.com/zai-org/VisionReward) |
| 2024 | [VideoScore: Building Automatic Metrics to Simulate Fine-grained Human Feedback for Video Generation](https://arxiv.org/abs/2406.15252) | arXiv | T2V | Reward Model | [Paper](https://arxiv.org/abs/2406.15252) |
| 2023 | [ImageReward: Learning and Evaluating Human Preferences for Text-to-Image Generation](https://arxiv.org/abs/2304.05977) | NeurIPS | T2I | Reward Model, RLHF | [Paper](https://arxiv.org/abs/2304.05977), [Code](https://github.com/zai-org/ImageReward) |
| 2023 | [Pick-a-Pic: An Open Dataset of User Preferences for Text-to-Image Generation](https://arxiv.org/abs/2305.01569) | NeurIPS | T2I | Reward Model | [Paper](https://arxiv.org/abs/2305.01569), [Code](https://github.com/yuvalkirstain/PickScore) |

## RLHF / Policy Gradient

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |
| 2025 | [Advantage Weighted Matching: Aligning RL with Pretraining in Diffusion Models](https://arxiv.org/abs/2509.25050) | arXiv | T2I | RLHF | [Paper](https://arxiv.org/abs/2509.25050), [Code](https://github.com/scxue/advantage_weighted_matching) |
| 2023 | [DPOK: Reinforcement Learning for Fine-tuning Text-to-Image Diffusion Models](https://arxiv.org/abs/2305.16381) | NeurIPS | T2I | RLHF, PPO | [Paper](https://arxiv.org/abs/2305.16381), [Code](https://github.com/google-research/google-research/tree/master/dpok) |
| 2023 | [Training Diffusion Models with Reinforcement Learning](https://arxiv.org/abs/2305.13301) | ICLR | T2I | RLHF, PPO | [Paper](https://arxiv.org/abs/2305.13301), [Project](http://rl-diffusion.github.io), [Code](https://github.com/kvablack/ddpo-pytorch) |

## DPO / Preference Optimization

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |
| 2025 | [Diffusion-SDPO: Safeguarded Direct Preference Optimization for Diffusion Models](https://arxiv.org/abs/2511.03317) | arXiv | T2I | DPO | [Paper](https://arxiv.org/abs/2511.03317), [Code](https://github.com/AIDC-AI/Diffusion-SDPO) |
| 2025 | [DenseDPO: Fine-Grained Temporal Preference Optimization for Video Diffusion Models](https://arxiv.org/abs/2506.03517) | arXiv | T2V | DPO | [Paper](https://arxiv.org/abs/2506.03517) |
| 2025 | [Discriminator-Free Direct Preference Optimization for Video Diffusion](https://arxiv.org/abs/2504.08542) | arXiv | T2V | DPO | [Paper](https://arxiv.org/abs/2504.08542) |
| 2024 | [VideoDPO: Omni-Preference Alignment for Video Diffusion Generation](https://arxiv.org/abs/2412.14167) | arXiv | T2V | DPO | [Paper](https://arxiv.org/abs/2412.14167), [Project](https://videodpo.github.io/) |
| 2023 | [Diffusion Model Alignment Using Direct Preference Optimization](https://arxiv.org/abs/2311.12908) | CVPR | T2I | DPO | [Paper](https://arxiv.org/abs/2311.12908), [Code](https://github.com/SalesforceAIResearch/DiffusionDPO) |

## GRPO / RLOO / Policy Optimization

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |
| 2026 | [Flow-OPD: On-Policy Distillation for Flow Matching Models](https://arxiv.org/abs/2605.08063) | arXiv | T2I | GRPO | [Paper](https://arxiv.org/abs/2605.08063) |
| 2025 | [DanceGRPO: Unleashing GRPO on Visual Generation](https://arxiv.org/abs/2505.07818) | arXiv | Unified | GRPO | [Paper](https://arxiv.org/abs/2505.07818), [Project](https://dancegrpo.github.io/) |
| 2025 | [Flow-GRPO: Training Flow Matching Models via Online RL](https://arxiv.org/abs/2505.05470) | NeurIPS | T2I | GRPO | [Paper](https://arxiv.org/abs/2505.05470), [Project](https://gongyeliu.github.io/Flow-GRPO/), [Code](https://github.com/yifan123/flow_grpo) |

## Reward Guidance / Test-time Optimization

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |
| 2026 | [Diffusion-DRF: Free, Rich, and Differentiable Reward for Video Diffusion Fine-Tuning](https://arxiv.org/abs/2601.04153) | arXiv | T2V | Reward Guidance | [Paper](https://arxiv.org/abs/2601.04153) |
| 2024 | [Video Diffusion Alignment via Reward Gradients](https://arxiv.org/abs/2407.08737) | arXiv | T2V | Reward Guidance | [Paper](https://arxiv.org/abs/2407.08737), [Project](https://vader-vid.github.io/) |
| 2023 | [Aligning Text-to-Image Diffusion Models with Reward Backpropagation](https://arxiv.org/abs/2310.03739) | arXiv | T2I | Reward Guidance | [Paper](https://arxiv.org/abs/2310.03739), [Project](https://align-prop.github.io/) |
| 2023 | [Directly Fine-Tuning Diffusion Models on Differentiable Rewards](https://arxiv.org/abs/2309.17400) | ICLR | T2I | Reward Guidance | [Paper](https://arxiv.org/abs/2309.17400) |

## Benchmarks & Evaluation

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |
| 2024 | [VBench: Comprehensive Benchmark Suite for Video Generative Models](https://arxiv.org/abs/2311.17982) | CVPR | T2V, I2V | Benchmark | [Paper](https://arxiv.org/abs/2311.17982), [Project](https://vchitect.github.io/VBench-project/), [Code](https://github.com/Vchitect/VBench) |
| 2023 | [GenEval: An Object-Focused Framework for Evaluating Text-to-Image Alignment](https://arxiv.org/abs/2310.11513) | NeurIPS | T2I | Benchmark | [Paper](https://arxiv.org/abs/2310.11513), [Code](https://github.com/djghosh13/geneval) |
| 2023 | [Human Preference Score v2: A Solid Benchmark for Evaluating Human Preferences of Text-to-Image Synthesis](https://arxiv.org/abs/2306.09341) | arXiv | T2I | Benchmark, Reward Model | [Paper](https://arxiv.org/abs/2306.09341), [Code](https://github.com/tgxs002/HPSv2) |
| 2023 | [Pick-a-Pic: An Open Dataset of User Preferences for Text-to-Image Generation](https://arxiv.org/abs/2305.01569) | NeurIPS | T2I | Benchmark, Reward Model | [Paper](https://arxiv.org/abs/2305.01569), [Code](https://github.com/yuvalkirstain/PickScore) |

## Toolkits & Codebases

| Name | Scope | Task | Method | Links |
| --- | --- | --- | --- | --- |
| Flow-Factory | Unified framework for reinforcement learning in flow-matching models | Unified | DPO, GRPO, Toolkit | [Code](https://github.com/X-GenGroup/Flow-Factory) |
| Flow-GRPO | Official implementation for training flow-matching image generators with online RL | T2I | GRPO, Toolkit | [Project](https://gongyeliu.github.io/Flow-GRPO/), [Code](https://github.com/yifan123/flow_grpo) |
| DDPO | Official PyTorch implementation of denoising diffusion policy optimization | T2I | RLHF, PPO, Toolkit | [Project](http://rl-diffusion.github.io), [Code](https://github.com/kvablack/ddpo-pytorch) |
| ImageReward | Reward model, dataset, and reward-feedback learning code for text-to-image alignment | T2I | Reward Model, RLHF, Toolkit | [Code](https://github.com/zai-org/ImageReward) |

## Related Areas

- [awesome-diffusion-model-in-rl](https://github.com/opendilab/awesome-diffusion-model-in-rl): diffusion models for reinforcement learning, a related but different direction.
- [Awesome-RLHF-Video-Diffusion](https://github.com/wangqiang9/Awesome-RLHF-Video-Diffusion): focused list for RLHF in video diffusion.
- [awesome-diffusion-rl](https://github.com/JasperChennn/awesome-diffusion-rl): related list covering RL for diffusion and diffusion-related post-training.

## Contributing

Contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before adding a paper or resource.
