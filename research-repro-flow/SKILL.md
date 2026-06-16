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

1. Identify the task family, modality, benchmark, dataset preference, compute budget, and constraints.
2. If the task family is ambiguous, ask a short clarification before research. Do not silently choose a modality.
   - Emotion tasks must be clarified as text sentiment/emotion, speech emotion recognition, facial expression recognition, multimodal emotion recognition, or affective dialogue unless the user already specifies the modality.
   - Detection tasks must be clarified when needed as 2D object detection, 3D detection, open-vocabulary detection, video detection, etc.
3. If the user says the first-stage result is off target, accept the correction, restate the corrected task, and restart the research phase from that scope.
4. Search recent papers, leaderboards, official repos, benchmark repos, and papers-with-code style indexes. For fast-moving tasks, browse before answering.
5. For broad tasks such as object detection, default to methods from the last two calendar years unless the user requests another window.
6. Build a method table with:
   - method, year, venue
   - task variant and modality
   - paper link
   - reported benchmark and metric
   - speed/FPS/latency when available
   - popularity signal when available, such as citations, GitHub stars, community adoption, or benchmark usage
   - open-source status and repo link when already known
   - dataset coverage
   - reproducibility note
7. Recommend exactly three selectable candidates when evidence permits:
   - most popular
   - highest accuracy
   - fastest
8. Stop after the research table and recommendations. Ask the user to choose by number before checking out code, writing implementation files, downloading data, or starting environment setup.
9. After the user selects a number, inspect whether official or reliable third-party code exists.
10. If code exists, prefer adapting that code. If no reliable code exists, reproduce the method from the paper and state any assumptions.
11. Create a minimal conda environment and dependency install plan.
12. Download public data automatically when permitted. If the dataset requires login, payment, license approval, or manual request, stop and give exact download instructions.
13. Produce runnable training and testing code or scripts, then run the shortest credible smoke train/eval when compute and data allow.

## Output Expectations

- Be explicit about what was chosen and why.
- For the research phase, give a complete enough table for the requested time window, then keep recommendations small and actionable.
- Use stable numeric IDs in the table and ask the user to input the ID of the method to reproduce.
- Do not continue beyond the research/recommendation phase until the user chooses a method, unless the user explicitly asks for autonomous execution.
- For ambiguous task names, first ask for the missing scope instead of producing a table from an arbitrary default.
- If the user corrects the scope, discard the mismatched table and redo first-stage research under the corrected scope.
- Separate "research complete" from "execution blocked" when data or code is missing.
- When the task is ambiguous and the missing scope changes the literature search, ask one clarification question before producing the shortlist.
- If implementing from a paper, mark uncertain details and create the smallest faithful implementation that can train and test end to end.

## Reference

See [workflow](references/workflow.md) for the interactive checklist, table template, and execution contract.
