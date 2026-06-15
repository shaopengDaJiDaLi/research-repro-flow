<div align="center">

# Research Repro Flow

Research, shortlist, and reproduce machine learning baselines with Codex.

[![Codex Skill](https://img.shields.io/badge/Codex-skill-111827)](research-repro-flow/SKILL.md)
[![Workflow](https://img.shields.io/badge/workflow-research%20to%20repro-2563eb)](research-repro-flow/references/workflow.md)
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

</div>

`research-repro-flow` is a Codex skill for turning an ML research goal into a practical reproduction path. It helps an agent search recent methods, shortlist credible baselines, inspect open-source code, set up the environment, obtain data, and run a smoke train/eval when possible.

## Why Use It

Research reproduction usually fails in the gaps between "this paper looks good" and "this command runs." This skill makes those gaps explicit:

- shortlist recent baselines with repo and dataset coverage
- prefer official or benchmark-maintained implementations
- choose one default baseline plus a small number of alternates
- separate research completion from execution blockers
- stop cleanly when data requires login, payment, or manual approval
- record the commands, artifacts, and metrics needed for a reproducible handoff

## Quick Start

Install the skill from this repository's `research-repro-flow/` directory:

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo <owner>/<repo> \
  --path research-repro-flow
```

Or install from a GitHub URL:

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --url https://github.com/<owner>/<repo>/tree/main/research-repro-flow
```

Restart Codex after installing so the new skill is visible.

## Usage

Trigger the skill directly in Codex:

```text
$research-repro-flow
```

Example prompts:

```text
$research-repro-flow Find the best reproducible baselines for gait recognition, then help me reproduce one of them.
```

```text
$research-repro-flow Compare recent open-source baselines for remote sensing change detection and recommend one to run first.
```

```text
$research-repro-flow Reproduce the strongest practical baseline for my dataset if public code and data are available.
```

## Workflow

1. Identify the task family, benchmark, and user constraints.
2. Search recent papers, official repositories, and benchmark repositories.
3. Build a compact shortlist with method, year, venue, code status, datasets, and reproducibility notes.
4. Recommend one default baseline and, when useful, one or two alternates.
5. Set up a minimal conda environment from the selected repository's instructions.
6. Download public data automatically when allowed.
7. Run the shortest credible smoke train/eval command.
8. Report commands, artifacts, metrics, blockers, and the next action.

## Output Shape

The skill is designed to produce small, decision-ready outputs instead of broad literature surveys:

| Rank | Method | Year | Venue | Open source | Repo | Datasets | Why it matters |
|---|---|---:|---|---|---|---|---|
| 1 | Default baseline | 2026 | Example | Official | Link | Target benchmark | Strong, runnable first choice |
| 2 | Alternate | 2025 | Example | Community | Link | Related benchmark | Useful fallback or comparison |

## Repository Layout

```text
.
├── README.md
├── RELEASE.md
├── LICENSE
└── research-repro-flow/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        └── workflow.md
```

## Project Status

This is a lightweight Codex skill rather than a Python package. The core behavior lives in [`research-repro-flow/SKILL.md`](research-repro-flow/SKILL.md), with the operational checklist in [`research-repro-flow/references/workflow.md`](research-repro-flow/references/workflow.md).

## License

Released under the [MIT License](LICENSE).
