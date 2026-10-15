# FlyRank ML Internship Project — Content Refresh Opportunity Ranking

An applied machine-learning workflow that ranks existing content pages for review using anonymized search and engagement signals. It is a decision-support queue, not a claim to predict Google's ranking algorithm.

## Project structure

| Path | Purpose |
|---|---|
| `data/raw/content_refresh_anonymized.csv` | Anonymized starter dataset |
| `notebooks/` | Data exploration and introductory model workflows |
| `scripts/01_prepare_features.py`–`scripts/05_build_pdf_report.py` | Feature preparation, baseline, training, evaluation/export, and PDF report |
| `scripts/run_all.py` | Pipeline runner |
| `outputs/model_report.md` | Saved model comparison and summary |
| `outputs/charts/` | Feature importance, action, confidence, trend, and reason-code charts |
| `docs/data-dictionary.md`, `DATA_USE.md` | Field definitions and safe data-use rules |
| `work/` | Assignment/capstone workspace |

## Dataset and target

The saved model report records **30,000 rows scored**, with 16,262 declining-label rows (a 54.2% label rate). The target is `is_declining_label`; the saved workflow says it uses a client-holdout split. The bundled data is anonymized and excludes client names, domains, URLs, titles, and keywords. Follow `DATA_USE.md` and do not add private client data.

These are recorded output metrics; rerun the scripts to validate them against the current data and dependency versions.

## Saved model comparison

The following values are from `outputs/model_report.md`:

| Model | ROC-AUC | Average precision | Precision@50 | Recall | F1 |
|---|---:|---:|---:|---:|---:|
| Decision tree | 0.742 | 0.575 | 0.540 | 0.716 | 0.634 |
| Logistic regression | 0.700 | 0.522 | 0.400 | 0.567 | 0.566 |
| Random forest | 0.750 | 0.618 | 0.740 | 0.744 | 0.640 |
| Baseline rules | 0.627 | 0.468 | 0.240 | — | — |

The random forest was selected using Precision@50. Against the rule baseline, Precision@50 improves from 0.240 to 0.740 (an absolute increase of 0.500, or 50 percentage points). Treat these figures as stored report results until the pipeline is rerun; do not imply measured business lift, ranking improvements, or revenue impact.

## Saved queue distribution

| Output bucket | Items |
|---|---:|
| High confidence | 3,605 |
| Medium confidence | 11,395 |
| Low confidence | 15,000 |
| Action: monitor | 13,093 |
| Action: refresh | 8,178 |
| Action: refresh and review CTR | 6,657 |
| Action: refresh and review engagement | 1,990 |
| Action: expand and refresh | 82 |

The action/confidence counts come from the saved report; confirm that categories are mutually exclusive before adding them together.

## Pipeline

```text
01_prepare_features.py     prepare fields and target
02_baseline_score.py       create a transparent rule baseline
03_train_model.py          train candidate models using client holdout
04_evaluate_and_export.py  evaluate, rank, and export queue/charts/report
05_build_pdf_report.py     produce PDF summary
run_all.py                 execute the pipeline
```

## Run locally

1. Create a Python environment.
2. Install dependencies with `pip install -r requirements.txt`.
3. Review `SETUP.md`, `GUIDE.md`, and `DATA_USE.md`.
4. From the repository root, run:

   ```bash
   python scripts/run_all.py
   ```

5. Compare fresh outputs with `outputs/model_report.md` and check that files were regenerated successfully.

## Interpretation and limitations

- The label is a modeled declining-content target; verify its definition and time window in the data dictionary and feature scripts.
- Model metrics evaluate ranking/classification against the available label. They do not prove that applying recommendations increases traffic or business outcomes.
- Check feature timing for leakage and keep client groups separated as intended by the holdout.
- Use the ranked queue for human review rather than automatic publishing decisions.
- Respect the data-use terms and do not publish private or identifying client information.

## Skills demonstrated

Python, pandas, feature engineering, baseline design, classification, client-holdout validation, ranking evaluation, model interpretation, reporting automation, and data governance.

## Author

Sahil Gaikwad · [GitHub](https://github.com/sahil2003-ai) · [LinkedIn](https://www.linkedin.com/in/sahil-gaikwad-a76b7224a/)
