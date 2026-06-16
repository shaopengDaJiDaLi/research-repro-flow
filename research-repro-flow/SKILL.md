---
name: research-repro-flow
description: Use when the user wants an interactive ML research-to-reproduction workflow: survey recent methods for a task, present a table, recommend popularity/accuracy/speed choices, wait for the user's numeric selection, inspect or implement code, configure environments, download data, and produce runnable train/test scripts.
---

# Research Repro Flow

## Overview

This skill turns a research request into an interactive reproducible baseline workflow: search recent methods, present a decision table, recommend candidates, wait for the user's selection, check code availability, set up or implement the method, obtain data, and produce runnable train/test commands.

Use it when the user asks for any of these:

- "Find the best recent baselines for X"
- "List recent methods and let me choose one"
- "Recommend the most popular, most accurate, and fastest work"
- "Check whether the selected method has open-source code"
- "If no code exists, reproduce the method from the paper"
- "Download the dataset and provide train/test scripts"

## Workflow

1. Identify the task family, benchmark, and constraints.
2. Search recent papers, leaderboards, official repos, benchmark repos, and papers-with-code style indexes. For fast-moving tasks, browse before answering.
3. For broad tasks such as object detection, default to methods from the last two calendar years unless the user requests another window.
4. Build a method table with:
   - method, year, venue
   - paper link
   - reported benchmark and metric
   - speed/FPS/latency when available
   - popularity signal when available, such as citations, GitHub stars, community adoption, or benchmark usage
   - open-source status and repo link when already known
   - dataset coverage
   - reproducibility note
5. Recommend exactly three selectable candidates when evidence permits:
   - most popular
   - highest accuracy
   - fastest
6. Stop after the research table and recommendations. Ask the user to choose by number before checking out code, writing implementation files, downloading data, or starting environment setup.
7. After the user selects a number, inspect whether official or reliable third-party code exists.
8. If code exists, prefer adapting that code. If no reliable code exists, reproduce the method from the paper and state any assumptions.
9. Create a minimal conda environment and dependency install plan.
10. Download public data automatically when permitted. If the dataset requires login, payment, license approval, or manual request, stop and give exact download instructions.
11. Produce runnable training and testing code or scripts, then run the shortest credible smoke train/eval when compute and data allow.

## Output Expectations

- Be explicit about what was chosen and why.
- For the research phase, give a complete enough table for the requested time window, then keep recommendations small and actionable.
- Use stable numeric IDs in the table and ask the user to input the ID of the method to reproduce.
- Do not continue beyond the research/recommendation phase until the user chooses a method, unless the user explicitly asks for autonomous execution.
- Separate "research complete" from "execution blocked" when data or code is missing.
- When the task is ambiguous, infer the closest task family and still provide a usable shortlist.
- If implementing from a paper, mark uncertain details and create the smallest faithful implementation that can train and test end to end.

## Reference

See [workflow](references/workflow.md) for the interactive checklist, table template, and execution contract.
