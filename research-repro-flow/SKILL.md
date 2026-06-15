---
name: research-repro-flow
description: Use when the user wants to research an ML task, shortlist strong baselines, inspect open-source code, create conda environments, download data, and reproduce training or evaluation.
---

# Research Repro Flow

## Overview

This skill turns a research request into a reproducible baseline workflow: search recent methods, group them into a shortlist, choose one or more baselines, check code availability, set up conda, obtain data, and run a smoke reproduction.

Use it when the user asks for any of these:

- "Find the best recent baselines for X"
- "Give me a shortlist table and recommend a baseline"
- "Check whether the code is open source"
- "Set up conda and reproduce the method"
- "Download the dataset and run train/eval"

## Workflow

1. Identify the task family, benchmark, and constraints.
2. Search recent papers, official repos, and benchmark repos.
3. Group methods into a shortlist table with:
   - method, year, venue
   - open-source status and repo link
   - dataset coverage
   - a short reproducibility note
   - a recommendation flag
4. Recommend 1 default baseline and, when useful, 1-2 alternates.
5. Prefer official or benchmark-maintained code. If no code exists, state that a reimplementation is needed.
6. Create a minimal conda environment from the repository instructions.
7. Download public data automatically when permitted. If the dataset requires login, payment, or special approval, stop and give step-by-step download instructions.
8. Run the shortest credible smoke train/eval command and save commands, artifacts, and metrics.

## Output Expectations

- Be explicit about what was chosen and why.
- Keep the shortlist small and actionable.
- Separate "research complete" from "execution blocked" when data or code is missing.
- When the task is ambiguous, infer the closest task family and still provide a usable shortlist.

## Reference

See [workflow](references/workflow.md) for the concise checklist and output template.
