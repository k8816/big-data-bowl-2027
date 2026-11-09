# NFL Big Data Bowl 2027

Scaffold for Kevin Zhang’s BDB 2027 analysis (Combine → in-game get-off / pass-rush).

## Layout

| Path | Purpose |
|------|---------|
| `Data/` | Competition CSVs (local only; **git-ignored** + **Cursor-ignored**) |
| `DerivedData/` | Notebook-built aggregate CSVs (local only; **git-ignored** + **Cursor-ignored**) |
| `notebooks/cursor_dev/` | Shared, agent-readable notebooks (no raw CSV outputs committed) |
| `notebooks/user_dev/` | Personal exploration (Cursor-ignored; may contain data in outputs) |
| `src/` | Package code |
| `outputs/` | Non-CSV artifacts |

## Pass-rush aggregates (manual)

Run `notebooks/cursor_dev/player_play_passrush_aggs.ipynb` after placing competition files under `Data/` (paths parameterized at top). Schema is **snake_case**. Filters `nfl_position` ∈ {DE, OLB, DT, NT}.

Writes (season only):

- `DerivedData/player_play_passrush_by_season_player.csv`

Do not paste raw competition CSV rows into AI chats. Do not commit `Data/` or `DerivedData/` CSVs.
