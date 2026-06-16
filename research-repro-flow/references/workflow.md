# Workflow

## Checklist

1. Read the user's target task, modality, benchmark, dataset preference, compute budget, and time window.
2. If the task family is ambiguous, ask for the missing scope before research.
3. For emotion tasks, clarify one of:
   - text sentiment/emotion classification
   - speech emotion recognition
   - facial expression recognition
   - multimodal emotion recognition
   - affective dialogue/emotion cause/emotion recognition in conversation
4. If the user corrects the first-stage scope, restart research under the corrected task and do not continue from the mismatched table.
5. If the user gives only a task family after clarification, default to the last two calendar years.
6. Search recent papers, leaderboards, official repos, benchmark repos, and implementation indexes.
7. Build a numbered method table.
8. Recommend exactly three candidates when evidence permits:
   - `popular`: strongest popularity/adoption signal
   - `accurate`: best reported accuracy on the relevant benchmark
   - `fast`: best speed/latency/throughput tradeoff
9. Stop and ask the user to choose a method by ID.
10. After selection, search for official code first, then benchmark-maintained code, then reliable community code.
11. If code exists, clone/adapt it and preserve upstream instructions where practical.
12. If no reliable code exists, implement the method from the paper. State assumptions for missing architectural/training details.
13. Create a minimal conda environment.
14. Download data automatically when allowed. If access requires login, payment, license approval, or manual request, stop with exact steps.
15. Provide and, when feasible, run complete training and testing commands.
16. Report status, blockers, files, commands, artifacts, and next action.

## Research Table Template

| ID | Method | Year | Task/modality | Venue | Paper | Benchmark/metric | Speed | Popularity signal | Code | Datasets | Note |
|---:|---|---:|---|---|---|---|---|---|---|---|---|

## Recommendation Template

| Choice | ID | Method | Why |
|---|---:|---|---|
| Most popular |  |  |  |
| Highest accuracy |  |  |  |
| Fastest |  |  |  |

End the research phase with:

```text
Please choose the method ID to reproduce. After you send the ID, I will check code availability and either adapt the open-source implementation or reproduce it from the paper.
```

## Execution States

- `clarifying_scope`
- `researching`
- `awaiting_selection`
- `checking_code`
- `implementing_or_adapting`
- `setup_environment`
- `download_data`
- `train_eval_scripts`
- `smoke_train_eval`
- `completed`
- `blocked`

## Rules

- Ask a clarification question before research when task words can map to multiple modalities or benchmarks.
- For emotion classification, do not default to text if the user did not specify text; ask whether they mean text, speech, facial, multimodal, or dialogue emotion recognition.
- If the user says the results do not match their intent, treat it as valid scope feedback and redo the research table.
- Browse for current paper/code/leaderboard information before producing the research table.
- Do not start clone/setup/download/implementation work before the user selects a method ID.
- Prefer official code when available.
- Prefer benchmark-maintained code over random forks.
- Use community code only when it is active enough to be credible.
- Use older methods only as anchors or regression baselines unless the user asks for them.
- When no code exists, reproduce from the paper and identify assumptions.
- Deliver runnable `train` and `test` entry points or scripts for the selected method.
- Stop when data access requires a human step.
- Keep the output concise and reproducible.
