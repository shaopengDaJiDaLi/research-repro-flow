# Workflow

## Checklist

1. Read the user's target task, benchmark, dataset preference, compute budget, and time window.
2. If the user gives only a task family, default to the last two calendar years.
3. Search recent papers, leaderboards, official repos, benchmark repos, and implementation indexes.
4. Build a numbered method table.
5. Recommend exactly three candidates when evidence permits:
   - `popular`: strongest popularity/adoption signal
   - `accurate`: best reported accuracy on the relevant benchmark
   - `fast`: best speed/latency/throughput tradeoff
6. Stop and ask the user to choose a method by ID.
7. After selection, search for official code first, then benchmark-maintained code, then reliable community code.
8. If code exists, clone/adapt it and preserve upstream instructions where practical.
9. If no reliable code exists, implement the method from the paper. State assumptions for missing architectural/training details.
10. Create a minimal conda environment.
11. Download data automatically when allowed. If access requires login, payment, license approval, or manual request, stop with exact steps.
12. Provide and, when feasible, run complete training and testing commands.
13. Report status, blockers, files, commands, artifacts, and next action.

## Research Table Template

| ID | Method | Year | Venue | Paper | Benchmark/metric | Speed | Popularity signal | Code | Datasets | Note |
|---:|---|---:|---|---|---|---|---|---|---|---|

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
