# FlyRank ML Internship Project — Content Refresh Opportunity Ranking

An applied machine-learning workflow that ranks existing content pages for review using anonymized search and engagement signals. It is a decision-support queue, not a claim to predict Google's ranking algorithm.

![Status](https://img.shields.io/badge/Status-Documented-yellow)

## 📌 Table of Contents

- [Overview](#-overview)
- [Problem Statement](#-problem-statement)
- [Objectives](#-objectives)
- [Features](#-features)
- [Dataset](#-dataset)
- [Tech Stack](#-tech-stack)
- [Project Workflow](#-project-workflow)
- [Repository Structure](#-repository-structure)
- [Installation](#-installation)
- [Usage](#-usage)
- [Results and Insights](#-results-and-insights)
- [Screenshots](#-screenshots)
- [Challenges and Solutions](#-challenges-and-solutions)
- [Limitations](#-limitations)
- [Future Improvements](#-future-improvements)
- [What I Learned](#-what-i-learned)
- [Author](#-author)
- [License](#-license)

## 📖 Overview

An applied machine-learning workflow that ranks existing content pages for review using anonymized search and engagement signals. It is a decision-support queue, not a claim to predict Google's ranking algorithm.

## 🎯 Problem Statement

This repository presents a portfolio project intended to demonstrate a clear problem, a traceable implementation, and evidence-backed outcomes. Reviewers should be able to find the relevant files and understand which results are verified.

## 🎯 Objectives

- Make the purpose and contents of the repository clear.
- Highlight the real implementation and tools used.
- Preserve verifiable metrics and distinguish saved outputs from independent reproduction.
- Make navigation and reproduction straightforward for reviewers.

## ✨ Features

```text
01_prepare_features.py     prepare fields and target
02_baseline_score.py       create a transparent rule baseline
03_train_model.py          train candidate models using client holdout
04_evaluate_and_export.py  evaluate, rank, and export queue/charts/report
05_build_pdf_report.py     produce PDF summary
run_all.py                 execute the pipeline
```

## 📂 Dataset

The saved model report records **30,000 rows scored**, with 16,262 declining-label rows (a 54.2% label rate). The target is `is_declining_label`; the saved workflow says it uses a client-holdout split. The bundled data is anonymized and excludes client names, domains, URLs, titles, and keywords. Follow `DATA_USE.md` and do not add private client data.

These are recorded output metrics; rerun the scripts to validate them against the current data and dependency versions.

## 🛠️ Tech Stack

See the repository source files and dependency manifests for technologies actually used.

## 🔄 Project Workflow

```text
01_prepare_features.py     prepare fields and target
02_baseline_score.py       create a transparent rule baseline
03_train_model.py          train candidate models using client holdout
04_evaluate_and_export.py  evaluate, rank, and export queue/charts/report
05_build_pdf_report.py     produce PDF summary
run_all.py                 execute the pipeline
```

## 🗂️ Repository Structure

Browse the repository tree for the actual source files and folders.

## ⚙️ Installation

1. Create a Python environment.
2. Install dependencies with `pip install -r requirements.txt`.
3. Review `SETUP.md`, `GUIDE.md`, and `DATA_USE.md`.
4. From the repository root, run:

   ```bash
   python scripts/run_all.py
   ```

5. Compare fresh outputs with `outputs/model_report.md` and check that files were regenerated successfully.

## ▶️ Usage

1. Create a Python environment.
2. Install dependencies with `pip install -r requirements.txt`.
3. Review `SETUP.md`, `GUIDE.md`, and `DATA_USE.md`.
4. From the repository root, run:

   ```bash
   python scripts/run_all.py
   ```

5. Compare fresh outputs with `outputs/model_report.md` and check that files were regenerated successfully.

## 📊 Results and Insights

The following values are from `outputs/model_report.md`:

| Model | ROC-AUC | Average precision | Precision@50 | Recall | F1 |
|---|---:|---:|---:|---:|---:|
| Decision tree | 0.742 | 0.575 | 0.540 | 0.716 | 0.634 |
| Logistic regression | 0.700 | 0.522 | 0.400 | 0.567 | 0.566 |
| Random forest | 0.750 | 0.618 | 0.740 | 0.744 | 0.640 |
| Baseline rules | 0.627 | 0.468 | 0.240 | — | — |

The random forest was selected using Precision@50. Against the rule baseline, Precision@50 improves from 0.240 to 0.740 (an absolute increase of 0.500, or 50 percentage points). Treat these figures as stored report results until the pipeline is rerun; do not imply measured business lift, ranking improvements, or revenue impact.

## 🖼️ Screenshots

Use only screenshots or visual assets that are actually stored in this repository. Verify paths and captions before adding image links.

## 🧩 Challenges and Solutions

| Challenge | Approach |
|---|---|
| Recruiters need fast context | Use a concise overview, clear file map, and direct project links. |
| Metrics can be overstated | Preserve evidence and validation caveats beside each reported result. |
| Reproduction can be unclear | Document setup steps, inputs, entry points, and dependencies. |

## ⚠️ Limitations

- The label is a modeled declining-content target; verify its definition and time window in the data dictionary and feature scripts.
- Model metrics evaluate ranking/classification against the available label. They do not prove that applying recommendations increases traffic or business outcomes.
- Check feature timing for leakage and keep client groups separated as intended by the holdout.
- Use the ranked queue for human review rather than automatic publishing decisions.
- Respect the data-use terms and do not publish private or identifying client information.

## 🚀 Future Improvements

- [ ] Verify all links and execution instructions.
- [ ] Document dependencies and data sources.
- [ ] Add genuine screenshots and reproducible outputs.

## 📚 What I Learned

- Organizing project documentation for technical and nontechnical readers.
- Linking implementation details to evidence-backed results.
- Explaining limitations and next steps clearly.

## 👤 Author

**Sahil Gaikwad**

- GitHub: [sahil2003-ai](https://github.com/sahil2003-ai)
- LinkedIn: [Sahil Gaikwad](https://www.linkedin.com/in/sahil-gaikwad-a76b7224a/)

## 📄 License

Check the repository license and any linked dataset licenses before reuse.