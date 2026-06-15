# Research Repro Flow

`research-repro-flow` is a Codex skill for research-to-reproduction workflows.

It helps turn an ML task into a practical baseline pipeline:

1. search recent methods
2. shortlist baseline candidates
3. pick one or more defaults
4. check open-source code
5. set up conda
6. download data
7. run a smoke train/eval

## When to use

Use this skill when you want to:

- compare recent baselines for a specific ML task
- ask for a shortlist table and recommendation
- verify whether code is open source
- reproduce a paper or benchmark with conda
- automate dataset download when possible

## Recommended name

`research-repro-flow`

Why this name:

- short
- action-oriented
- describes the exact workflow
- easy to trigger with `$research-repro-flow`

## Install

If you publish this repo on GitHub, install the skill from the `research-repro-flow/` subdirectory:

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

Trigger it directly in Codex:

```text
$research-repro-flow
```

Example prompt:

```text
$research-repro-flow Find the best reproducible baselines for gait recognition, then help me reproduce one of them.
```

## Repo layout

```text
repo-root/
├── README.md
├── LICENSE
└── research-repro-flow/
    ├── SKILL.md
    ├── agents/openai.yaml
    └── references/workflow.md
```

## Notes

- The skill body is intentionally short.
- The workflow details live in `research-repro-flow/references/workflow.md`.
- The skill is designed for research tasks that end in baseline selection and reproduction.
