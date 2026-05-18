# RL for Diffusion Awesome Repo Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build the first usable version of a curated awesome list for RL, RLHF, and preference optimization for image and video diffusion models.

**Architecture:** Keep the repository lightweight with one primary `README.md`, one `CONTRIBUTING.md`, and one `LICENSE`. The README is method-first, with compact tables and task/method tags so image and video work remains easy to scan. Verification is documentation-focused: check markdown structure, table consistency, and a sample of public links.

**Tech Stack:** Markdown, Git, shell tools (`rg`, `sed`, `git`), optional network checks with `curl`.

---

## File Structure

- Create `README.md`: main curated list, method-first sections, seed entries, and maintenance notes.
- Create `CONTRIBUTING.md`: scope, entry format, ordering rules, and pull request checklist.
- Create `LICENSE`: Apache-2.0 text to match the most relevant source repos and allow broad reuse.
- Keep `docs/superpowers/specs/2026-05-18-rl-for-diffusion-awesome-design.md`: approved design reference.
- Keep this plan in `docs/superpowers/plans/2026-05-18-rl-for-diffusion-awesome.md`.

## Task 1: Create README

**Files:**
- Create: `README.md`

- [ ] **Step 1: Create the README skeleton**

Use `apply_patch` to create `README.md` with this complete structure:

```markdown
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

## Reward Models & Feedback Signals

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |

## RLHF / Policy Gradient

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |

## DPO / Preference Optimization

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |

## GRPO / RLOO / Policy Optimization

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |

## Reward Guidance / Test-time Optimization

| Year | Paper | Venue | Task | Method | Resources |
| --- | --- | --- | --- | --- | --- |

## Benchmarks & Evaluation

| Year | Resource | Venue | Task | Method | Links |
| --- | --- | --- | --- | --- | --- |

## Toolkits & Codebases

| Name | Scope | Task | Method | Links |
| --- | --- | --- | --- | --- |

## Related Areas

- [awesome-diffusion-model-in-rl](https://github.com/opendilab/awesome-diffusion-model-in-rl): diffusion models for reinforcement learning, a related but different direction.
- [Awesome-RLHF-Video-Diffusion](https://github.com/wangqiang9/Awesome-RLHF-Video-Diffusion): focused list for RLHF in video diffusion.
- [awesome-diffusion-rl](https://github.com/JasperChennn/awesome-diffusion-rl): related list covering RL for diffusion and diffusion-related post-training.

## Contributing

Contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before adding a paper or resource.
```

- [ ] **Step 2: Add seed entries from known image/video RL-for-diffusion work**

Add entries under the correct method-first sections. Use official or stable links where possible. Keep entries newest first inside each section.

Minimum target seed coverage:

- At least 6 video generation entries.
- At least 6 image generation entries.
- At least 3 reward model, benchmark, or evaluation resources.
- At least 2 toolkit/codebase resources.
- At least 1 related survey or overview if a directly relevant public manuscript exists.

Use this entry style exactly:

```markdown
| 2025 | [VideoDPO: Omni-Preference Alignment for Video Diffusion Generation](https://arxiv.org/abs/2504.15230) | arXiv | T2V | DPO | [Paper](https://arxiv.org/abs/2504.15230) |
```

If a paper has no official code, omit `Code` rather than linking to unofficial implementations.

- [ ] **Step 3: Verify README structure**

Run:

```bash
rg -n "^## " README.md
rg -n "TBD|TODO|placeholder|paper-url|code-url|project-url" README.md
```

Expected:

- The section list contains all method-first sections from the design spec.
- The placeholder scan prints no matches.

- [ ] **Step 4: Commit README**

Run:

```bash
git add README.md
git commit -m "docs: add rl for diffusion awesome list"
```

Expected: commit succeeds and mentions `README.md`.

## Task 2: Create Contribution and License Files

**Files:**
- Create: `CONTRIBUTING.md`
- Create: `LICENSE`

- [ ] **Step 1: Create CONTRIBUTING.md**

Use `apply_patch` to create `CONTRIBUTING.md`:

```markdown
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
| 2025 | [VideoDPO: Omni-Preference Alignment for Video Diffusion Generation](https://arxiv.org/abs/2504.15230) | arXiv | T2V | DPO | [Paper](https://arxiv.org/abs/2504.15230) |
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
```

- [ ] **Step 2: Create Apache-2.0 LICENSE**

Use the standard Apache License 2.0 text in `LICENSE`.

Set the copyright line to:

```text
Copyright 2026 Awesome RL for Diffusion Contributors
```

- [ ] **Step 3: Verify contribution files**

Run:

```bash
rg -n "TBD|TODO|placeholder|paper-url|code-url|project-url" CONTRIBUTING.md LICENSE
rg -n "Apache License" LICENSE
```

Expected:

- Placeholder scan prints no matches.
- License scan prints the Apache License heading.

- [ ] **Step 4: Commit contribution and license files**

Run:

```bash
git add CONTRIBUTING.md LICENSE
git commit -m "docs: add contribution guide and license"
```

Expected: commit succeeds and mentions both files.

## Task 3: Final Documentation Verification

**Files:**
- Modify only if verification finds issues: `README.md`, `CONTRIBUTING.md`, `LICENSE`

- [ ] **Step 1: Check markdown tables for obvious malformed rows**

Run:

```bash
rg -n "^\\| " README.md CONTRIBUTING.md
```

Expected:

- README paper tables use six columns.
- README toolkits table uses five columns.
- CONTRIBUTING examples are readable and not accidentally inserted into README tables.

- [ ] **Step 2: Check internal links**

Run:

```bash
rg -n "\\[.*\\]\\(#" README.md
rg -n "^## " README.md
```

Expected:

- Every table-of-contents anchor corresponds to a README heading.

- [ ] **Step 3: Sample public links**

Run a small sample of important links:

```bash
curl -I -L https://github.com/opendilab/awesome-diffusion-model-in-rl
curl -I -L https://github.com/wangqiang9/Awesome-RLHF-Video-Diffusion
curl -I -L https://github.com/JasperChennn/awesome-diffusion-rl
```

Expected:

- Each command returns an HTTP 200 or a redirect chain ending in HTTP 200.

For seed paper links, sample at least five arXiv or project links added in Task 1 and fix any broken URLs before finalizing.

- [ ] **Step 4: Review git status and diff**

Run:

```bash
git status --short
git log --oneline -5
git diff -- README.md CONTRIBUTING.md LICENSE
```

Expected:

- No uncommitted changes after fixes are committed.
- Recent commits include the design spec, README, and contribution/license commits.
- Final diff is empty.

- [ ] **Step 5: Report completion**

Summarize:

- Files created.
- Number of seed entries by broad category.
- Verification commands run.
- Any links that could not be checked due to network issues.
