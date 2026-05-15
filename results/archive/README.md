# Archive Folder

Historical artifacts only. Do not use this folder as the current source of truth.

## Current Sources

| Source | Purpose |
|---|---|
| `../CANONICAL_v2/` | Canonical result JSON files. |
| `../CANONICAL_v2/RESULTS_LOCKED.md` | Short verified lookup for headline numbers and source files. |
| `../../RESULTS.md` | Human-readable result narrative. |
| `../../all_results.md` | Auto-generated inventory across `results/**/*.json`. |

## Archive Policy

| File Type | Policy |
|---|---|
| Legacy API v1 outputs | Keep here for audit only. |
| Failed auth/provider debug outputs | Keep here only when useful for provenance. |
| Superseded result JSONs | Keep here if referenced by an issue or diagnostic. |
| Canonical v2 outputs | Keep under `results/CANONICAL_v2/`, not here. |

Simple rule: use `results/CANONICAL_v2/` for numbers that may appear in slides, reports, or writeups. Use this archive only for old, failed, debug, or superseded outputs.

## Historical Notes

- `medhallu_detector_legacy_results.json`: legacy detector-style MedHallu output, comparison only.
- `medhallu_results_snapshot_n50.json`: snapshot copy of MedHallu MC n=50 output.

If an archived file is used in a paper or poster, label it as historical or diagnostic and cite the exact filename.
