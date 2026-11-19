# NFL Big Data Bowl 2027

## Git rules (ELI5 — read this first)

- **Kevin** works on **`kevin_branch1`**. That is the day-to-day branch.
- **Agents never push to `main`.** Never commit, push, or open a PR that targets `main`.
- **Agents** put every change on a new branch named **`kevin_cursor_agent_branch_XXXX`** (example: `kevin_cursor_agent_branch_flipignores`). They push only that branch.

### How Kevin merges an agent branch

1. `git checkout kevin_branch1`
2. `git pull --no-edit`
3. `git merge kevin_cursor_agent_branch_XXXX`  ← use the real branch name the agent gave you
4. If there are conflicts, stop and ask. Else: `git push`

On GitHub: if you open a Pull Request, set **base = `kevin_branch1`** (never `main`).

### Notebook folders (one-liner)

Agents write locally in `notebooks/cursor_dev/` (**git-ignored** + Cursor-ignored); Kevin copies keepers to `notebooks/cursor_user_run/` (**git-tracked**, Cursor-ignored); Kevin-only exploration lives in `notebooks/user_dev/` (**git-tracked**, Cursor-ignored).

---

Scaffold for Kevin Zhang’s BDB 2027 analysis (Combine → in-game get-off / pass-rush).

## Layout

| Path | Purpose |
|------|---------|
| `Data/` | Competition CSVs (local only; **git-ignored** + **Cursor-ignored**) |
| `DerivedData/` | Notebook-built aggregate CSVs (local only; **git-ignored** + **Cursor-ignored**) |
| `notebooks/cursor_dev/` | Agent scratch notebooks (local only; **git-ignored** + **Cursor-ignored**; never run here; clear outputs) |
| `notebooks/cursor_user_run/` | Kevin’s executed copies of agent notebooks (**git-tracked**; **Cursor-ignored** so AI never sees outputs) |
| `notebooks/user_dev/` | Kevin-only exploration (**git-tracked**; **Cursor-ignored**; may contain data in outputs) |
| `src/` | Package code |
| `outputs/` | Non-CSV artifacts |

## Pass-rush aggregates (manual)

Run a copy of `player_play_passrush_aggs.ipynb` from `notebooks/cursor_user_run/` (or copy from `cursor_dev` first) after placing competition files under `Data/` (paths parameterized at top). Schema is **snake_case**. Filters `nfl_position` ∈ {DE, OLB, DT, NT}.

Writes (season only):

- `DerivedData/player_play_passrush_by_season_player.csv`

## Combine + players DL export (manual)

Run a copy of `combine_players_dl_export.ipynb` after placing `Data/players.csv` and `Data/combine_results.csv`. Joins on `nfl_id`, filters `nfl_position` ∈ {DE, OLB, DT, NT}, renames `ngs_college_production_score` → `ngs_production_score`.

Writes:

- `DerivedData/combine_players_dl.csv`

## Forty histogram (manual)

Run a copy of `forty_histogram.ipynb` after `DerivedData/combine_players_dl.csv` exists. Drops NaN `forty`, then plots a histogram.

Do not paste raw competition CSV rows into AI chats. Do not commit `Data/` or `DerivedData/` CSVs.
