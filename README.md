# footalytics-data

Public mirror of Footalytics' settled AI football predictions — the same free CSV served at
https://footalytics.farvor.com/api/public/accuracy/settled.csv, refreshed daily by a GitHub Action.

Every prediction was published **before kickoff** and is graded **automatically after the match**.
Nothing is filtered, nothing is retro-edited: misses stay in the file. The live grading board is at
https://footalytics.farvor.com/accuracy.

## File

`data/settled-predictions.csv` — one row per graded official prediction:

| column | meaning |
| --- | --- |
| `kickoff_utc` | scheduled kickoff time (ISO 8601, UTC) |
| `league` | competition code (`eng.1`, `esp.1`, `ita.1`, `ger.1`, `fra.1`, `uefa.champions`, …) |
| `home`, `away` | team names |
| `p_home`, `p_draw`, `p_away` | model probabilities for the three 1X2 outcomes |
| `pick` | the official pick: `home`, `draw` or `away` |
| `home_goals`, `away_goals` | official final score |
| `hit_1x2` | `true` if the pick matched the actual outcome |
| `brier` | Brier score, multiclass sum over the three outcomes (0 = perfect, ≈0.667 = uniform guess) |

## Notes for analysis

- The model currently **never picks draws**; treat draw probabilities as calibration data, not picks.
- Coverage began 2026-10-17 and grows match by match; early sample sizes are small.
- If you use the data, cite it — and if you find an error in the grading, open an issue; grading is
  mechanical (final score in → row settled) but we want errors on the record.

## License

Data: [CC BY 4.0](LICENSE). Credit "Footalytics (footalytics.farvor.com)". Not betting advice — no
odds, no tips; this is a transparency dataset.
