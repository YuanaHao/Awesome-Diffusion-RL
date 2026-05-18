# RL for Diffusion Awesome Repo Design

## Goal

Create a focused awesome repository for papers and resources on reinforcement learning for image and video diffusion models. The repository should fill the gap left by existing awesome lists that are either focused on diffusion models inside RL, too narrow, or not updated frequently enough.

## Scope

The repository focuses on RL and preference-based post-training for image and video diffusion generation.

Included topics:

- RLHF and policy-gradient optimization for diffusion generators.
- DPO and other preference optimization methods for image or video diffusion.
- GRPO, RLOO, PPO-style, and related policy optimization methods for diffusion models.
- Reward model training, aesthetic or human preference rewards, and vision-language rewards used to optimize diffusion outputs.
- Reward guidance, test-time reward optimization, and inference-time alignment methods when they are directly tied to image or video diffusion.
- Benchmarks, datasets, evaluation protocols, and toolkits for RL-based image or video diffusion alignment.

Out of scope for the main list:

- Diffusion models used as policies, planners, or dynamics models in reinforcement learning.
- General language model RLHF papers unless they introduce a method directly used by image or video diffusion.
- Audio, 3D, robotics, molecule, or text diffusion work unless it is included in a small related-work section as background.

## Repository Structure

The first version should stay lightweight:

- `README.md`: the main curated list.
- `CONTRIBUTING.md`: submission and formatting rules.
- `LICENSE`: repository license.

The README should be the primary artifact. Separate topic files can be added later only if the list becomes too large to navigate comfortably.

## README Organization

The README uses method-first organization:

1. `Surveys & Overviews`
2. `Reward Models & Feedback Signals`
3. `RLHF / Policy Gradient`
4. `DPO / Preference Optimization`
5. `GRPO / RLOO / Policy Optimization`
6. `Reward Guidance / Test-time Optimization`
7. `Benchmarks & Evaluation`
8. `Toolkits & Codebases`
9. `Related Areas`

Within each section, entries should generally be ordered newest first. If a section contains both image and video papers, the `Task` column makes the distinction explicit.

## Entry Format

Paper sections use a compact table:

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |
| 2026 | Paper title | arXiv | T2V | GRPO, Reward | Paper / Code / Project |

Expected tags:

- Task tags: `T2I`, `I2I`, `T2V`, `I2V`, `V2V`, `Unified`
- Method tags: `RLHF`, `PPO`, `DPO`, `GRPO`, `RLOO`, `Reward Model`, `Reward Guidance`, `Benchmark`, `Toolkit`
- Resource links: `Paper`, `Code`, `Project`, `Dataset`, `Benchmark`

Entries should prefer stable, public links: arXiv, official project pages, official code repositories, or conference pages. Blog posts and social media links can be used only as secondary resources.

## Contribution Rules

`CONTRIBUTING.md` should define:

- Accepted scope: RL or preference optimization for image/video diffusion.
- Required metadata: title, year, paper link, task tag, method tag, and at least one public resource.
- Preferred ordering: newest first within each section.
- Duplicate handling: one primary entry per paper, with cross-method notes only when needed.
- Quality bar: papers should have a public manuscript, official project, code, benchmark, or clear technical description.

## Maintenance Principles

- Keep the list curated rather than exhaustive at any cost.
- Prioritize official sources over third-party summaries.
- Avoid mixing "Diffusion for RL" with "RL for Diffusion"; the former belongs only in related links if useful.
- Make image and video coverage explicit through task tags.
- Keep the initial repository simple and expand file structure only when navigation becomes difficult.

## Initial Seed Content

The first README should include seed entries from recent RL-for-diffusion image and video work, especially:

- Video diffusion RLHF and preference optimization papers.
- Image diffusion DPO and reward-alignment papers.
- GRPO-style and policy-gradient post-training papers for diffusion.
- Reward model and benchmark resources used to optimize or evaluate generated images/videos.

Existing repositories can be used as references, but their structure should not be copied directly because this repository has a narrower RL-for-image/video-diffusion scope.
