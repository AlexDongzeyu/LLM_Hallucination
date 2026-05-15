# CURED / ALTAS Locked Results

This file is the short, verified lookup for the main result numbers. The full narrative remains in `../../RESULTS.md`; raw source JSON files remain in this directory.

## Source Of Truth

- Canonical result directory: `results/CANONICAL_v2/`
- Full human-readable results: `RESULTS.md`
- Generated full ledger: `all_results.md`
- Paired statistical tests: `statistics_table.json`

If slides, notes, or generated reports disagree, use the JSON files named below.

## Main TruthfulQA Results

Headline greedy baselines use the full `n=817` TruthfulQA greedy files. CURED/ALTAS headline runs use `n=500`.

| Model | Greedy | CURED/ALTAS | Delta | Greedy source | CURED/ALTAS source |
|---|---:|---:|---:|---|---|
| Llama 3.2 3B | 50.1% | 60.6% | +10.5 pp | `main_greedy_3b_truthfulqa_n817.json` | `main_cured_3b_truthfulqa_n500_v2.json` |
| Llama 3.1 8B | 49.6% | 60.2% | +10.6 pp | `main_greedy_8b_truthfulqa_n817.json` | `main_cured_8b_truthfulqa_n500_v2.json` |
| Qwen 2.5 14B | 62.2% | 64.0% | +1.8 pp | `main_greedy_14b_truthfulqa_n817.json` | `main_cured_14b_truthfulqa_n500.json` |
| Qwen 2.5 32B | 58.8% | 60.1% | +1.3 pp | `main_greedy_32b_truthfulqa_n817.json` | `main_cured_32b_truthfulqa_n500.json` |

## Paired McNemar Statistics

These rows use matched first-500 question subsets for pairing, so the greedy percentages are not the same denominator as the full `n=817` headline greedy baselines above.

| Comparison | Greedy | CURED/ALTAS | Delta | b | c | Discordant | p_exact | Significant |
|---|---:|---:|---:|---:|---:|---:|---:|---|
| 3B TruthfulQA | 51.8% | 60.2% | +8.4 pp | 16 | 58 | 74/500 | 0.000001 | yes |
| 8B TruthfulQA | 48.2% | 60.0% | +11.8 pp | 15 | 74 | 89/500 | 0.000000 | yes |
| 14B TruthfulQA | 63.6% | 64.0% | +0.4 pp | 15 | 17 | 32/500 | 0.860050 | no |
| 32B TruthfulQA | 59.8% | 59.6% | -0.2 pp | 1 | 0 | 1/500 | 1.000000 | no |
| 3B StrategyQA | 65.0% | 62.4% | -2.6 pp | 33 | 20 | 53/500 | 0.098371 | no |

## Protocol Ablations

TruthfulQA ablations use cosine scoring with `n=200`.

| Model | Greedy | ALTA | CoVe | ITI |
|---|---:|---:|---:|---:|
| 3B | 56.5% | 59.0% | 46.0% | 56.5% |
| 8B | 48.0% | 60.6% | 39.2% | 57.5% |
| 14B | 64.5% | 57.9% | 45.5% | 67.0% |
| 32B | 57.6% | 58.0% | 49.8% | 64.3% |

MedHallu ablations use cosine scoring with `n=200`.

| Model | Greedy | ALTA | CoVe | ITI |
|---|---:|---:|---:|---:|
| 3B | 55.0% | 58.0% | 47.7% | 53.0% |
| 8B | 45.5% | 59.8% | 42.4% | 61.1% |
| 14B | 54.0% | 57.5% | 60.0% | 63.0% |
| 32B | 53.0% | 60.0% | 53.0% | 61.3% |

## Mechanistic Profiles

Source files: `profile_3b.json`, `profile_8b.json`, `profile_14b.json`, and `profile_32b.json`.

| Model | R2 | Kappa | ECR | H_final | H_peak |
|---|---:|---:|---:|---:|---:|
| 3B | 0.501 | 0.455 | 0.076 | 0.837 | 11.00 |
| 8B | 0.582 | 0.597 | 0.066 | 0.669 | 10.14 |
| 14B | 0.444 | 0.360 | 0.031 | 0.306 | 9.73 |
| 32B | 0.473 | 0.322 | 0.051 | 0.529 | 10.32 |

R2 correlation source: `r2_scale_correlation.json`.

- Scale-level R2 vs ALTA gain: r=0.9859, p=0.0141.
- Per-question R2 vs per-question gain: r=0.0393, p=0.5803.

## FACTOR Diagnostics

| Benchmark | Greedy | ALTA | CURED/ALTAS | Source |
|---|---:|---:|---:|---|
| FACTOR-News | 59.0% | 69.0% | 61.5% | `results_8b_factor_news_n200.json` |
| FACTOR-Wiki original | 29.0% | 64.0% | 43.0% | `results_8b_factor_wiki_n200.json` |
| FACTOR-Wiki fixed | 29.5% | 65.0% | 65.0% | `results_8b_factor_wiki_n200_fixed.json` |

## Separate Protocol Results

Ben's ALTA results use a separate log-prob MC1 / Alpaca-style protocol and should not be compared directly with the CURED/ALTAS tables above.

| Benchmark | ALTA |
|---|---:|
| TruthfulQA | 65.1% |
| MedQA | 73.8% |
| PubMedQA | 77.4% |
