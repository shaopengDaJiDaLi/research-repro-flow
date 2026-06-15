# Workflow

## Checklist

1. Read the user's target task and constraints.
2. Search recent methods and official/benchmark repos.
3. Build a shortlist table.
4. Recommend the best default baseline and alternates.
5. Check code availability.
6. Create conda environment from repo docs.
7. Download data automatically when allowed.
8. Otherwise, provide exact download steps.
9. Run a smoke train/eval.
10. Report status, blockers, files, and next action.

## Shortlist Template

| Rank | Method | Year | Venue | Open source | Repo | Datasets | Why it matters |
|---|---|---:|---|---|---|---|---|

## Execution States

- `researching`
- `awaiting_selection`
- `setup_environment`
- `download_data`
- `smoke_train_eval`
- `completed`
- `blocked`

## Rules

- Prefer official code when available.
- Prefer one strong default baseline over a long list.
- Use older methods only as anchors or regression baselines.
- Stop when data access requires a human step.
- Keep the output concise and reproducible.
