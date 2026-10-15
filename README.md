# FlyRank ML Internship Project — Content Refresh Opportunity Ranking

An applied machine-learning workflow that ranks existing content pages for review using anonymized search and engagement signals. It produces a decision-support queue; it does not claim to predict Google's ranking algorithm.

![Python](https://img.shields.io/badge/Python-ML-blue) ![Workflow](https://img.shields.io/badge/Workflow-Reproducible-green)

## Contents
- [Overview](#overview)
- [Objective](#objective)
- [Dataset and Data Use](#dataset-and-data-use)
- [Workflow](#workflow)
- [Results and Metrics](#results-and-metrics)
- [Technology Stack](#technology-stack)
- [Repository Structure](#repository-structure)
- [Run the Pipeline](#run-the-pipeline)
- [Limitations and Next Steps](#limitations-and-next-steps)

## Overview
The project prepares anonymized content-level features, compares baseline rules with machine-learning models, and ranks pages for human review. The score is intended to prioritize a review queue, not to make automated editorial decisions.

## Objective
- Frame a practical ranking task using anonymized search/engagement signals.
- Build a transparent baseline and compare candidate models.
- Evaluate ranking usefulness at a fixed review budget.
- Export a review queue and a report with documented limitations.

## Dataset and Data Use
The saved model report records **30,000 rows scored**, with **16,262 declining-label rows (54.2%)**. The target is `is_declining_label`; the saved workflow describes a client-holdout split.

The bundled dataset is anonymized and excludes client names, domains, URLs, titles, and keywords. Follow `DATA_USE.md` and do not add private client data.

## Workflow
```text
Prepare features → Score baseline → Train models → Evaluate and export → Build report
```

- `01_prepare_features.py`: prepare fields and target.
- `02_baseline_score.py`: create a transparent rule baseline.
- `03_train_model.py`: train candidate models with client-holdout evaluation.
- `04_evaluate_and_export.py`: evaluate models and export queue, charts, and report.
- `05_build_pdf_report.py`: produce the PDF summary.
- `run_all.py`: execute the pipeline.

## Results and Metrics
Values recorded in `outputs/model_report.md`:

| Model | ROC-AUC | Average precision | Precision@50 | Recall | F1 |
|---|---:|---:|---:|---:|---:|
| Decision tree | 0.742 | 0.575 | 0.540 | 0.716 | 0.634 |
| Logistic regression | 0.700 | 0.522 | 0.400 | 0.567 | 0.566 |
| Random forest | 0.750 | 0.618 | 0.740 | 0.744 | 0.640 |
| Baseline rules | 0.627 | 0.468 | 0.240 | — | — |

The random forest was selected using Precision@50. Precision@50 rises from 0.240 for the rule baseline to 0.740 for the random forest in the saved report. These values should be reconfirmed by running the pipeline against the current data and dependencies.

## Technology Stack
See `requirements.txt` and the `scripts/` directory for the concrete packages and implementation. The workflow uses Python scripts, ML evaluation, CSV exports, and report generation.

## Repository Structure
- `data/raw/content_refresh_anonymized.csv`: anonymized data
- `docs/`: data dictionary and project guidance
- `notebooks/`: learning and capstone notebooks
- `scripts/`: feature preparation, training, evaluation, and report generation
- `outputs/`: model report and ranked queue
- `DATA_USE.md`, `SETUP.md`, `GUIDE.md`: data policy and setup documentation

## Run the Pipeline
1. Create a Python environment.
2. Install dependencies with `pip install -r requirements.txt`.
3. Review `SETUP.md`, `GUIDE.md`, and `DATA_USE.md`.
4. From the repository root, run:
   ```bash
   python scripts/run_all.py
   ```
5. Compare newly generated outputs with `outputs/model_report.md`.

## Limitations and Next Steps
- Treat the score as a prioritization aid for human review, not a search-ranking prediction.
- Recheck data splits, leakage, label construction, and client holdout boundaries.
- Compare models with the baseline on the same evaluation set.
- Preserve anonymization and follow the repository data-use policy.
- Document dependency versions and rerun outputs before citing results externally.

## Skills Demonstrated
ML task framing, feature preparation, baseline design, model comparison, ranking metrics, data-use discipline, and report generation.

## Author
**Sahil Gaikwad** · [GitHub](https://github.com/sahil2003-ai) · [LinkedIn](https://www.linkedin.com/in/sahil-gaikwad-a76b7224a/)
