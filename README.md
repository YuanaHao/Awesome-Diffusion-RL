# Awesome RL for Diffusion

A curated list of papers and resources on reinforcement learning, RLHF, and preference optimization for image and video diffusion models.

This repository focuses on **RL for diffusion generation**, especially image and video generation. It does not track the separate line of work on diffusion models used as policies, planners, or dynamics models in reinforcement learning.

This list is maintained with **weekly updates**, with priority given to recent high-impact arXiv papers, papers accepted by top-tier conferences, and influential open-source resources.

## Scope

Included:

- RLHF and policy-gradient optimization for image or video diffusion models.
- DPO and preference optimization for text-to-image, image-to-image, text-to-video, image-to-video, and video-to-video generation.
- GRPO, RLOO, PPO-style, and related policy optimization methods for diffusion post-training.
- Stochastic optimal control, surrogate-objective, and reward-corrected regression methods for diffusion or flow post-training.
- Reward models, feedback signals, and benchmarks used to optimize or evaluate image/video diffusion outputs.
- Reward guidance and test-time optimization methods when they directly target image or video diffusion alignment.

Out of scope:

- Diffusion models used as RL policies, planners, or dynamics models.
- General LLM RLHF papers without a direct image/video diffusion application.
- Audio, 3D, robotics, molecule, or text diffusion work, except as brief related context.

## Contents

- [Surveys & Overviews](#surveys--overviews)
- [Reward Models & Feedback Signals](#reward-models--feedback-signals)
- [RL Post-Training Taxonomy](#rl-post-training-taxonomy)
  - [Policy Gradient / SDE Rollout](#policy-gradient--sde-rollout)
  - [Stochastic Optimal Control / Adjoint](#stochastic-optimal-control--adjoint)
  - [Surrogate Objective / Likelihood Approximation](#surrogate-objective--likelihood-approximation)
  - [Reward-Corrected Regression / Score Matching](#reward-corrected-regression--score-matching)
- [DPO / Preference Optimization](#dpo--preference-optimization)
- [Reward Guidance / Test-time Optimization](#reward-guidance--test-time-optimization)
- [Benchmarks & Evaluation](#benchmarks--evaluation)
- [Toolkits & Codebases](#toolkits--codebases)
- [Related Areas](#related-areas)
- [Contributing](#contributing)

## Tag Guide

Task tags: `T2I`, `I2I`, `T2V`, `I2V`, `V2V`, `Unified`

Method tags: `RLHF`, `Policy Gradient`, `PPO`, `GRPO`, `RLOO`, `SOC`, `Adjoint`, `Surrogate`, `Likelihood Estimation`, `Reward-Corrected Regression`, `Score Matching`, `DPO`, `Reward Model`, `Reward Guidance`, `Benchmark`, `Toolkit`

## Surveys & Overviews

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |
| 2026 | [Advances in GRPO for Generation Models: A Survey](https://arxiv.org/abs/2603.06623) | arXiv | Unified | GRPO | [Paper](https://arxiv.org/abs/2603.06623) |
| 2025 | [Reinforcement Learning for Large Model: A Survey](https://arxiv.org/abs/2508.08189) | arXiv | Unified | RLHF, GRPO | [Paper](https://arxiv.org/abs/2508.08189), [Code](https://github.com/weijiawu/Awesome-Visual-Reinforcement-Learning) |

## Reward Models & Feedback Signals

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |
| 2026 | [VIGOR: VIdeo Geometry-Oriented Reward for Temporal Generative Alignment](https://arxiv.org/abs/2603.16271) | arXiv | T2V | Reward Model, Reward Guidance | [Paper](https://arxiv.org/abs/2603.16271) |
| 2026 | [Beyond VLM-Based Rewards: Diffusion-Native Latent Reward Modeling](https://arxiv.org/abs/2602.11146) | arXiv | T2I | Reward Model | [Paper](https://arxiv.org/abs/2602.11146) |
| 2025 | [VideoScore2: Think before You Score in Generative Video Evaluation](https://arxiv.org/abs/2509.22799) | arXiv | T2V | Reward Model, GRPO | [Paper](https://arxiv.org/abs/2509.22799), [Project](https://tiger-ai-lab.github.io/VideoScore2/) |
| 2025 | [Cycle Consistency as Reward: Learning Image-Text Alignment without Human Preferences](https://arxiv.org/abs/2506.02095) | ICCV | T2I | Reward Model, DPO | [Paper](https://arxiv.org/abs/2506.02095), [CVF](https://openaccess.thecvf.com/content/ICCV2025/html/Bahng_Cycle_Consistency_as_Reward_Learning_Image-Text_Alignment_without_Human_Preferences_ICCV_2025_paper.html), [Project](https://cyclereward.github.io/) |
| 2025 | [Improving Video Generation with Human Feedback](https://arxiv.org/abs/2501.13918) | NeurIPS | T2V | Reward Model, RLHF | [Paper](https://arxiv.org/abs/2501.13918), [Project](https://gongyeliu.github.io/videoalign/), [Code](https://github.com/KwaiVGI/VideoAlign) |
| 2024 | [VisionReward: Fine-Grained Multi-Dimensional Human Preference Learning for Image and Video Generation](https://arxiv.org/abs/2412.21059) | arXiv | Unified | Reward Model | [Paper](https://arxiv.org/abs/2412.21059), [Code](https://github.com/zai-org/VisionReward) |
| 2024 | [VideoScore: Building Automatic Metrics to Simulate Fine-grained Human Feedback for Video Generation](https://arxiv.org/abs/2406.15252) | arXiv | T2V | Reward Model | [Paper](https://arxiv.org/abs/2406.15252) |
| 2023 | [ImageReward: Learning and Evaluating Human Preferences for Text-to-Image Generation](https://arxiv.org/abs/2304.05977) | NeurIPS | T2I | Reward Model, RLHF | [Paper](https://arxiv.org/abs/2304.05977), [Code](https://github.com/zai-org/ImageReward) |
| 2023 | [Pick-a-Pic: An Open Dataset of User Preferences for Text-to-Image Generation](https://arxiv.org/abs/2305.01569) | NeurIPS | T2I | Reward Model | [Paper](https://arxiv.org/abs/2305.01569), [Code](https://github.com/yuvalkirstain/PickScore) |

## RL Post-Training Taxonomy

Following the taxonomy used by Reinforce Adjoint Matching (RAM), this section organizes reward-based diffusion and flow post-training by the optimization estimator used to inject reward into the model: policy-gradient rollouts, stochastic optimal control/adjoint methods, surrogate objectives, and reward-corrected regression. Preference-only objectives are kept in the separate DPO section below.

### Policy Gradient / SDE Rollout

These methods treat the denoising or flow trajectory as an on-policy rollout and optimize reward through PPO, GRPO, RLOO, or related policy-gradient estimators.

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |
| 2026 | [Flow-OPD: On-Policy Distillation for Flow Matching Models](https://arxiv.org/abs/2605.08063) | arXiv | T2I | Policy Gradient, GRPO | [Paper](https://arxiv.org/abs/2605.08063) |
| 2026 | [Embedding-perturbed Exploration Preference Optimization for Flow Models](https://arxiv.org/abs/2605.15803) | ICML | T2I | Policy Gradient, GRPO | [Paper](https://arxiv.org/abs/2605.15803), [ICML](https://icml.cc/Downloads/2026) |
| 2026 | [World-R1: Reinforcing 3D Constraints for Text-to-Video Generation](https://arxiv.org/abs/2604.24764) | ICML | T2V | Policy Gradient, GRPO, Reward Model | [Paper](https://arxiv.org/abs/2604.24764), [ICML](https://icml.cc/Downloads/2026) |
| 2026 | [MAR-GRPO: Stabilized GRPO for AR-diffusion Hybrid Image Generation](https://arxiv.org/abs/2604.06966) | arXiv | T2I | Policy Gradient, GRPO | [Paper](https://arxiv.org/abs/2604.06966), [Code](https://github.com/AMAP-ML/mar-grpo) |
| 2026 | [Manifold-Aware Exploration for Reinforcement Learning in Video Generation](https://arxiv.org/abs/2603.21872) | arXiv | T2V | Policy Gradient, GRPO | [Paper](https://arxiv.org/abs/2603.21872), [Project](https://dungeonmassster.github.io/SAGE-GRPO-Page/), [Code](https://github.com/Tencent-Hunyuan/SAGE-GRPO) |
| 2026 | [From Sparse to Dense: Multi-View GRPO for Flow Models via Augmented Condition Space](https://arxiv.org/abs/2603.12648) | arXiv | T2I | Policy Gradient, GRPO | [Paper](https://arxiv.org/abs/2603.12648) |
| 2026 | [Alleviating Sparse Rewards by Modeling Step-Wise and Long-Term Sampling Effects in Flow-Based GRPO](https://arxiv.org/abs/2602.06422) | ICML | T2I | Policy Gradient, GRPO | [Paper](https://arxiv.org/abs/2602.06422), [ICML](https://icml.cc/Downloads/2026), [Code](https://github.com/YunzeTong/TurningPoint-GRPO) |
| 2026 | [DenseGRPO: From Sparse to Dense Reward for Flow Matching Model Alignment](https://arxiv.org/abs/2601.20218) | ICLR | T2I | Policy Gradient, GRPO, Reward Model | [Paper](https://arxiv.org/abs/2601.20218), [OpenReview](https://openreview.net/pdf?id=nIwFge9nW0) |
| 2026 | [BranchGRPO: Stable and Efficient GRPO with Structured Branching in Diffusion Models](https://arxiv.org/abs/2509.06040) | ICLR | T2I, I2V | Policy Gradient, GRPO | [Paper](https://arxiv.org/abs/2509.06040), [Project](https://fredreic1849.github.io/BranchGRPO-Webpage/) |
| 2026 | [Rethinking the Design Space of Reinforcement Learning for Diffusion Models: On the Importance of Likelihood Estimation Beyond Loss Design](https://arxiv.org/abs/2602.04663) | ICML | T2I | Policy Gradient, Likelihood Estimation | [Paper](https://arxiv.org/abs/2602.04663), [ICML](https://icml.cc/Downloads/2026) |
| 2025 | [Identity-GRPO: Optimizing Multi-Human Identity-preserving Video Generation via Reinforcement Learning](https://arxiv.org/abs/2510.14256) | arXiv | I2V | Policy Gradient, GRPO, Reward Model | [Paper](https://arxiv.org/abs/2510.14256), [Project](https://ali-videoai.github.io/identity_page), [Code](https://github.com/alibaba/identity-grpo) |
| 2025 | [Understanding Sampler Stochasticity in Training Diffusion Models for RLHF](https://arxiv.org/abs/2510.10767) | arXiv | T2I | Policy Gradient, SDE Rollout | [Paper](https://arxiv.org/abs/2510.10767) |
| 2025 | [Adaptive Divergence Regularized Policy Optimization for Fine-tuning Generative Models](https://arxiv.org/abs/2510.18053) | NeurIPS | T2I | Policy Gradient | [Paper](https://arxiv.org/abs/2510.18053), [NeurIPS](https://papers.nips.cc/paper_files/paper/2025/hash/b396d8821d3ac740db8b887b5eda6f18-Abstract-Conference.html) |
| 2025 | [MixGRPO: Unlocking Flow-based GRPO Efficiency with Mixed ODE-SDE](https://arxiv.org/abs/2507.21802) | arXiv | T2I | Policy Gradient, GRPO | [Paper](https://arxiv.org/abs/2507.21802), [Code](https://github.com/Tencent-Hunyuan/MixGRPO) |
| 2025 | [InfLVG: Reinforce Inference-Time Consistent Long Video Generation with GRPO](https://arxiv.org/abs/2505.17574) | arXiv | T2V | Policy Gradient, GRPO | [Paper](https://arxiv.org/abs/2505.17574), [Code](https://github.com/MAPLE-AIGC/InfLVG) |
| 2025 | [DanceGRPO: Unleashing GRPO on Visual Generation](https://arxiv.org/abs/2505.07818) | arXiv | Unified | Policy Gradient, GRPO | [Paper](https://arxiv.org/abs/2505.07818), [Project](https://dancegrpo.github.io/) |
| 2025 | [Flow-GRPO: Training Flow Matching Models via Online RL](https://arxiv.org/abs/2505.05470) | NeurIPS | T2I | Policy Gradient, GRPO | [Paper](https://arxiv.org/abs/2505.05470), [Project](https://gongyeliu.github.io/Flow-GRPO/), [Code](https://github.com/yifan123/flow_grpo) |
| 2025 | [DiffExp: Efficient Exploration in Reward Fine-tuning for Text-to-Image Diffusion Models](https://arxiv.org/abs/2502.14070) | AAAI | T2I | Policy Gradient, Exploration | [Paper](https://arxiv.org/abs/2502.14070), [AAAI](https://ojs.aaai.org/index.php/AAAI/article/view/33723) |
| 2025 | [Human-Feedback Efficient Reinforcement Learning for Online Diffusion Model Finetuning](https://arxiv.org/abs/2410.05116) | arXiv | T2I | Policy Gradient | [Paper](https://arxiv.org/abs/2410.05116) |
| 2023 | [DPOK: Reinforcement Learning for Fine-tuning Text-to-Image Diffusion Models](https://arxiv.org/abs/2305.16381) | NeurIPS | T2I | Policy Gradient, PPO | [Paper](https://arxiv.org/abs/2305.16381), [Code](https://github.com/google-research/google-research/tree/master/dpok) |
| 2023 | [Training Diffusion Models with Reinforcement Learning](https://arxiv.org/abs/2305.13301) | ICLR | T2I | Policy Gradient, PPO | [Paper](https://arxiv.org/abs/2305.13301), [Project](http://rl-diffusion.github.io), [Code](https://github.com/kvablack/ddpo-pytorch) |

### Stochastic Optimal Control / Adjoint

These methods formulate reward maximization as stochastic optimal control or adjoint matching. They are more explicit about the KL-regularized control problem, but often require reward gradients, adjoint equations, or careful continuous-time estimation.

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |
| 2026 | [Efficient Adjoint Matching for Fine-tuning Diffusion Models](https://arxiv.org/abs/2605.11480) | arXiv | T2I | SOC, Adjoint | [Paper](https://arxiv.org/abs/2605.11480) |
| 2026 | [A unified perspective on fine-tuning and sampling with diffusion and flow models](https://arxiv.org/abs/2605.00229) | arXiv | Unified | SOC, Adjoint | [Paper](https://arxiv.org/abs/2605.00229) |
| 2025 | [Score as Action: Fine-Tuning Diffusion Generative Models by Continuous-time Reinforcement Learning](https://arxiv.org/abs/2502.01819) | arXiv | T2I | SOC, Policy Gradient | [Paper](https://arxiv.org/abs/2502.01819) |
| 2025 | [Adjoint Matching: Fine-tuning Flow and Diffusion Generative Models with Memoryless Stochastic Optimal Control](https://arxiv.org/abs/2409.08861) | ICLR | Unified | SOC, Adjoint | [Paper](https://arxiv.org/abs/2409.08861), [OpenReview](https://openreview.net/forum?id=RqjVMnS5Vn) |
| 2024 | [Fine-Tuning of Continuous-Time Diffusion Models as Entropy-Regularized Control](https://arxiv.org/abs/2402.15194) | ICML | T2I | SOC, Reward Guidance | [Paper](https://arxiv.org/abs/2402.15194), [PMLR](https://proceedings.mlr.press/v235/uehara24a.html) |

### Surrogate Objective / Likelihood Approximation

These methods avoid direct likelihood or rollout estimation by optimizing a tractable proxy, such as forward-process contrast, flow-matching ELBOs, variational EM, reward-weighted regression, or density-control surrogates.

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |
| 2026 | [DiffusionNFT: Online Diffusion Reinforcement with Forward Process](https://arxiv.org/abs/2509.16117) | ICLR Oral | T2I | Surrogate, Forward Process | [Paper](https://arxiv.org/abs/2509.16117), [ICLR](https://iclr.cc/virtual/2026/poster/10009149), [Project](https://research.nvidia.com/labs/dir/DiffusionNFT) |
| 2026 | [Diffusion Alignment as Variational Expectation-Maximization](https://arxiv.org/abs/2510.00502) | ICLR | T2I | Surrogate, Reward Guidance | [Paper](https://arxiv.org/abs/2510.00502), [OpenReview](https://openreview.net/forum?id=aBeIFDshvZ), [Code](https://github.com/Jaewoopudding/dav) |
| 2026 | [V-GRPO: Online Reinforcement Learning for Denoising Generative Models Is Easier than You Think](https://arxiv.org/abs/2604.23380) | arXiv | T2I | Surrogate, GRPO, Likelihood Estimation | [Paper](https://arxiv.org/abs/2604.23380) |
| 2025 | [Flow Density Control: Generative Optimization Beyond Entropy-Regularized Fine-Tuning](https://arxiv.org/abs/2511.22640) | NeurIPS | T2I | Surrogate, Density Control | [Paper](https://arxiv.org/abs/2511.22640), [OpenReview](https://openreview.net/pdf?id=JzCjNJlSxI) |
| 2025 | [Reinforcing Diffusion Models by Direct Group Preference Optimization](https://arxiv.org/abs/2510.08425) | arXiv | T2I | Surrogate, Group Preference | [Paper](https://arxiv.org/abs/2510.08425), [Code](https://github.com/Luo-Yihong/DGPO) |
| 2025 | [Advantage Weighted Matching: Aligning RL with Pretraining in Diffusion Models](https://arxiv.org/abs/2509.25050) | arXiv | T2I | Surrogate, Score Matching | [Paper](https://arxiv.org/abs/2509.25050), [Code](https://github.com/scxue/advantage_weighted_matching) |
| 2025 | [ImageReFL: Balancing Quality and Diversity in Human-Aligned Diffusion Models](https://arxiv.org/abs/2505.22569) | arXiv | T2I | Surrogate, Reward Feedback | [Paper](https://arxiv.org/abs/2505.22569), [Code](https://github.com/ControlGenAI/ImageReFL) |
| 2025 | [Online Reward-Weighted Fine-Tuning of Flow Matching with Wasserstein Regularization](https://arxiv.org/abs/2502.06061) | ICLR | T2I | Surrogate, Reward-Weighted Regression | [Paper](https://arxiv.org/abs/2502.06061), [Project](https://gelab-uiuc.github.io/projects/orw/), [OpenReview](https://openreview.net/forum?id=2IoFFexvuw) |
| 2025 | [LiFT: Leveraging Human Feedback for Text-to-Video Model Alignment](https://arxiv.org/abs/2412.04814) | arXiv | T2V | Surrogate, Human Feedback | [Paper](https://arxiv.org/abs/2412.04814), [Project](https://codegoat24.github.io/LiFT), [Code](https://github.com/CodeGoat24/LiFT) |
| 2024 | [PRDP: Proximal Reward Difference Prediction for Large-Scale Reward Finetuning of Diffusion Models](https://arxiv.org/abs/2402.08714) | CVPR | T2I | Surrogate, Reward Model | [Paper](https://arxiv.org/abs/2402.08714), [Project](https://fdeng18.github.io/prdp/) |

### Reward-Corrected Regression / Score Matching

These methods preserve the pretraining-style regression or score-matching structure while modifying the target with reward information. RAM is the clearest example of this fourth category in the RAM taxonomy.

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |
| 2026 | [Reinforce Adjoint Matching: Scaling RL Post-Training of Diffusion and Flow-Matching Models](https://arxiv.org/abs/2605.10759) | arXiv | T2I | Reward-Corrected Regression, SOC | [Paper](https://arxiv.org/abs/2605.10759) |
| 2026 | [Reward Score Matching: Unifying Reward-based Fine-tuning for Flow and Diffusion Models](https://arxiv.org/abs/2604.17415) | arXiv | T2I | Reward-Corrected Regression, Score Matching | [Paper](https://arxiv.org/abs/2604.17415) |

## DPO / Preference Optimization

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |
| 2026 | [ViPO: Visual Preference Optimization at Scale](https://arxiv.org/abs/2604.24953) | ICLR | T2I, T2V | DPO | [Paper](https://arxiv.org/abs/2604.24953), [ICLR](https://iclr.cc/virtual/2026/poster/10006676), [OpenReview](https://openreview.net/pdf?id=x5zP3k64Nl) |
| 2026 | [Towards Better Optimization For Listwise Preference in Diffusion Models](https://arxiv.org/abs/2510.01540) | ICLR | T2I, I2I | DPO | [Paper](https://arxiv.org/abs/2510.01540), [OpenReview](https://openreview.net/forum?id=ippWaS9PG9) |
| 2026 | [Diffusion Negative Preference Optimization Made Simple](https://openreview.net/forum?id=CU5EHe1KUt) | ICLR | T2I | DPO | [OpenReview](https://openreview.net/forum?id=CU5EHe1KUt) |
| 2026 | [alpha-DPO: Robust Preference Alignment for Diffusion Models via alpha Divergence](https://openreview.net/forum?id=wqbnA6PcKr) | ICLR | T2I | DPO | [OpenReview](https://openreview.net/forum?id=wqbnA6PcKr), [ICLR](https://iclr.cc/virtual/2026/poster/10006698) |
| 2026 | [Taming Preference Mode Collapse via Directional Decoupling Alignment in Diffusion Reinforcement Learning](https://arxiv.org/abs/2512.24146) | arXiv | T2I | DPO, RLHF | [Paper](https://arxiv.org/abs/2512.24146) |
| 2025 | [Diffusion-SDPO: Safeguarded Direct Preference Optimization for Diffusion Models](https://arxiv.org/abs/2511.03317) | arXiv | T2I | DPO | [Paper](https://arxiv.org/abs/2511.03317), [Code](https://github.com/AIDC-AI/Diffusion-SDPO) |
| 2025 | [CPO: Condition Preference Optimization for Controllable Image Generation](https://arxiv.org/abs/2511.04753) | NeurIPS | T2I, I2I | DPO | [Paper](https://arxiv.org/abs/2511.04753), [OpenReview](https://openreview.net/forum?id=ToEgGjClB9), [Project](https://zonglinl.github.io/CPO_page) |
| 2025 | [DenseDPO: Fine-Grained Temporal Preference Optimization for Video Diffusion Models](https://arxiv.org/abs/2506.03517) | arXiv | T2V | DPO | [Paper](https://arxiv.org/abs/2506.03517) |
| 2025 | [D-Fusion: Direct Preference Optimization for Aligning Diffusion Models with Visually Consistent Samples](https://arxiv.org/abs/2505.22002) | ICML | T2I, I2I | DPO | [Paper](https://arxiv.org/abs/2505.22002), [Proceedings](https://kunkuang.github.io/papers/ICML25-D-Fusion.pdf) |
| 2025 | [CHATS: Combining Human-Aligned Optimization and Test-Time Sampling for Text-to-Image Generation](https://openreview.net/forum?id=D4Y71nbGRg) | ICML | T2I | DPO, Reward Guidance | [OpenReview](https://openreview.net/forum?id=D4Y71nbGRg), [Code](https://github.com/AIDC-AI/CHATS) |
| 2025 | [Smoothed Preference Optimization via ReNoise Inversion for Aligning Diffusion Models with Varied Human Preferences](https://openreview.net/forum?id=G3grccIXIg) | ICML | T2I | DPO | [OpenReview](https://openreview.net/forum?id=G3grccIXIg) |
| 2025 | [Rethinking DPO-style Diffusion Aligning Frameworks](https://openaccess.thecvf.com/content/ICCV2025/html/Wu_Rethinking_DPO-style_Diffusion_Aligning_Frameworks_ICCV_2025_paper.html) | ICCV Highlight | T2I | DPO | [CVF](https://openaccess.thecvf.com/content/ICCV2025/html/Wu_Rethinking_DPO-style_Diffusion_Aligning_Frameworks_ICCV_2025_paper.html), [Code](https://github.com/yushuiwx/RDPO) |
| 2025 | [Self-Supervised Direct Preference Optimization for Text-to-Image Diffusion Models](https://nips.cc/virtual/2025/poster/119288) | NeurIPS | T2I | DPO | [NeurIPS](https://nips.cc/virtual/2025/poster/119288), [OpenReview](https://openreview.net/forum?id=COifgrjzXR) |
| 2025 | [A Gradient Guidance Perspective on Stepwise Preference Optimization for Diffusion Models](https://papers.nips.cc/paper_files/paper/2025/hash/8a91eb31a82077b18b6004c88a5f53a4-Abstract-Conference.html) | NeurIPS | T2I | DPO, Reward Guidance | [NeurIPS](https://papers.nips.cc/paper_files/paper/2025/hash/8a91eb31a82077b18b6004c88a5f53a4-Abstract-Conference.html), [Code](https://github.com/JoshuaTTJ/GradSPO) |
| 2025 | [Diffusion Model as a Noise-Aware Latent Reward Model for Step-Level Preference Optimization](https://arxiv.org/abs/2502.01051) | NeurIPS | T2I | DPO, Reward Model | [Paper](https://arxiv.org/abs/2502.01051), [Code](https://github.com/casiatao/LPO) |
| 2025 | [Boost Your Human Image Generation Model via Direct Preference Optimization](https://arxiv.org/abs/2405.20216) | CVPR | T2I | DPO | [Paper](https://arxiv.org/abs/2405.20216), [CVF](https://openaccess.thecvf.com/content/CVPR2025/html/Na_Boost_Your_Human_Image_Generation_Model_via_Direct_Preference_Optimization_CVPR_2025_paper.html) |
| 2025 | [Personalized Preference Fine-tuning of Diffusion Models](https://arxiv.org/abs/2501.06655) | CVPR | T2I | DPO | [Paper](https://arxiv.org/abs/2501.06655), [CVF](https://openaccess.thecvf.com/content/CVPR2025/html/Dang_Personalized_Preference_Fine-tuning_of_Diffusion_Models_CVPR_2025_paper.html) |
| 2025 | [Discriminator-Free Direct Preference Optimization for Video Diffusion](https://arxiv.org/abs/2504.08542) | arXiv | T2V | DPO | [Paper](https://arxiv.org/abs/2504.08542) |
| 2025 | [DSPO: Direct Score Preference Optimization for Diffusion Model Alignment](https://openreview.net/forum?id=xyfb9HHvMe) | ICLR | T2I | DPO | [OpenReview](https://openreview.net/forum?id=xyfb9HHvMe), [Proceedings](https://proceedings.iclr.cc/paper_files/paper/2025/file/7f70331dbe58ad59d83941dfa7d975aa-Paper-Conference.pdf), [Code](https://github.com/huaishengzhu/DSPO) |
| 2025 | [Curriculum Direct Preference Optimization for Diffusion and Consistency Models](https://arxiv.org/abs/2405.13637) | CVPR | T2I | DPO | [Paper](https://arxiv.org/abs/2405.13637), [Code](https://github.com/CroitoruAlin/Curriculum-DPO) |
| 2025 | [Refining Alignment Framework for Diffusion Models with Intermediate-Step Preference Ranking](https://arxiv.org/abs/2502.01667) | arXiv | T2I | DPO | [Paper](https://arxiv.org/abs/2502.01667), [OpenReview](https://openreview.net/forum?id=9LZna4ryFH) |
| 2024 | [VideoDPO: Omni-Preference Alignment for Video Diffusion Generation](https://arxiv.org/abs/2412.14167) | arXiv | T2V | DPO | [Paper](https://arxiv.org/abs/2412.14167), [Project](https://videodpo.github.io/) |
| 2024 | [OnlineVPO: Align Video Diffusion Model with Online Video-Centric Preference Optimization](https://arxiv.org/abs/2412.15159) | arXiv | T2V | DPO | [Paper](https://arxiv.org/abs/2412.15159), [Project](https://visual-ai.github.io/onlinevpo/) |
| 2024 | [Margin-aware Preference Optimization for Aligning Diffusion Models without Reference](https://arxiv.org/abs/2406.06424) | arXiv | T2I | DPO | [Paper](https://arxiv.org/abs/2406.06424), [Project](https://mapo-t2i.github.io) |
| 2024 | [Diffusion-RPO: Aligning Diffusion Models through Relative Preference Optimization](https://arxiv.org/abs/2406.06382) | arXiv | T2I | DPO | [Paper](https://arxiv.org/abs/2406.06382), [Code](https://github.com/yigu1008/Diffusion-RPO) |
| 2024 | [A Dense Reward View on Aligning Text-to-Image Diffusion with Preference](https://arxiv.org/abs/2402.08265) | ICML | T2I | DPO, Reward Model | [Paper](https://arxiv.org/abs/2402.08265), [PMLR](https://proceedings.mlr.press/v235/yang24e.html), [Code](https://github.com/Shentao-YANG/Dense_Reward_T2I) |
| 2024 | [Using Human Feedback to Fine-tune Diffusion Models without Any Reward Model](https://arxiv.org/abs/2311.13231) | CVPR | T2I | DPO | [Paper](https://arxiv.org/abs/2311.13231), [Code](https://github.com/yk7333/d3po) |
| 2023 | [Diffusion Model Alignment Using Direct Preference Optimization](https://arxiv.org/abs/2311.12908) | CVPR | T2I | DPO | [Paper](https://arxiv.org/abs/2311.12908), [Code](https://github.com/SalesforceAIResearch/DiffusionDPO) |

## Reward Guidance / Test-time Optimization

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |
| 2026 | [Diffusion-DRF: Free, Rich, and Differentiable Reward for Video Diffusion Fine-Tuning](https://arxiv.org/abs/2601.04153) | arXiv | T2V | Reward Guidance | [Paper](https://arxiv.org/abs/2601.04153) |
| 2026 | [Scaling Group Inference for Diverse and High-Quality Generation](https://arxiv.org/abs/2508.15773) | ICLR | Unified | Reward Guidance | [Paper](https://arxiv.org/abs/2508.15773), [Project](https://www.cs.cmu.edu/~group-inference), [OpenReview](https://openreview.net/pdf?id=IyTNxjTuWT) |
| 2026 | [Asynchronous Denoising Diffusion Models for Aligning Text-to-Image Generation](https://arxiv.org/abs/2510.04504) | ICLR | T2I | Reward Guidance | [Paper](https://arxiv.org/abs/2510.04504), [OpenReview](https://openreview.net/forum?id=ZHb4bduWkM), [Code](https://github.com/hu-zijing/AsynDM) |
| 2025 | [Inference-Time Text-to-Video Alignment with Diffusion Latent Beam Search](https://arxiv.org/abs/2501.19252) | arXiv | T2V | Reward Guidance | [Paper](https://arxiv.org/abs/2501.19252) |
| 2025 | [Directly Aligning the Full Diffusion Trajectory with Fine-Grained Human Preference](https://arxiv.org/abs/2509.06942) | arXiv | T2I | Reward Guidance, DPO | [Paper](https://arxiv.org/abs/2509.06942) |
| 2025 | [T2V-Turbo-v2: Enhancing Video Generation Model Post-Training through Data, Reward, and Conditional Guidance Design](https://arxiv.org/abs/2410.05677) | ICLR | T2V | Reward Guidance | [Paper](https://arxiv.org/abs/2410.05677), [Project](https://t2v-turbo-v2.github.io/), [Code](https://github.com/Ji4chenLi/t2v-turbo) |
| 2024 | [Video Diffusion Alignment via Reward Gradients](https://arxiv.org/abs/2407.08737) | arXiv | T2V | Reward Guidance | [Paper](https://arxiv.org/abs/2407.08737), [Project](https://vader-vid.github.io/) |
| 2024 | [T2V-Turbo: Breaking the Quality Bottleneck of Video Consistency Model with Mixed Reward Feedback](https://arxiv.org/abs/2405.18750) | arXiv | T2V | Reward Guidance | [Paper](https://arxiv.org/abs/2405.18750), [Code](https://github.com/Ji4chenLi/t2v-turbo) |
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
