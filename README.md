# lung-cancer-risk-ml

[![Paper](https://img.shields.io/badge/paper-IEEE%20Xplore-00629B.svg)](https://ieeexplore.ieee.org/document/10766818) ![Python](https://img.shields.io/badge/python-3.10%2B-blue.svg) ![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

Predicting lung cancer risk from a lifestyle questionnaire with machine
learning. This is the code behind our conference paper:

> **Prediction of Lung Cancer Risk Through Machine Learning Based on Lifestyle
> Questionnaire Data.**
> S. Chavez-Caceres, A. Hincho-Jove, E. Castro-Gutierrez, A. Soriano-Vargas.
> 2024 IEEE International Conference on Automation / XXVI Congress of the Chilean
> Association of Automatic Control (ICA-ACCA), Santiago, Chile, 2024.
> DOI: [10.1109/ICA-ACCA62622.2024.10766818](https://doi.org/10.1109/ICA-ACCA62622.2024.10766818)
> · [IEEE Xplore](https://ieeexplore.ieee.org/document/10766818)

## What it does

Lung cancer is the leading cause of cancer mortality worldwide. This work tests
a low-cost screening aid: from lifestyle and symptom answers (smoking, anxiety,
chronic disease, wheezing, and so on), classify whether a person is at risk, and
expose why the model decided that way.

Pipeline:

1. **EDA** of the questionnaire data (univariate and multivariate).
2. **SMOTE** to balance the under-represented class.
3. Compare Logistic Regression, SVC, Decision Tree, Random Forest, a Keras
   neural net, and **XGBoost** (the chosen model), tuned with **GridSearchCV**
   on a 70/30 split.
4. **LIME** for per-prediction explanations, so a risk score comes with the
   factors behind it.

## Results (from the paper)

| Dataset | Accuracy | F1 | Precision | Sensitivity |
|---------|---------:|---:|----------:|------------:|
| Dataset 1 | 96.50% | 96.50% | 96.51% | 96.51% |
| Dataset 2 | 95.83% | 95.83% | 96.27% | 95.83% |

## Repository

```
notebooks/
  01_eda_and_models.ipynb        # EDA + model comparison
  02_survey_dataset_models.ipynb # second dataset (Kaggle "survey lung cancer")
data/README.md                   # where to get the datasets (not redistributed)
paper/
  lung-cancer-risk-ml-accepted.pdf  # authors' accepted manuscript
  README.md                         # citation + IEEE notice
```

The notebooks were written on Google Colab (paths like `/content/...`); point
the `read_csv` calls at your local copy of the data (see [`data/`](data/)).

## Reproduce

```bash
pip install -r requirements.txt
# download the dataset (see data/README.md), then run the notebooks
jupyter lab
```

## Citation

```bibtex
@inproceedings{chavezcaceres2024lungcancer,
  title     = {Prediction of Lung Cancer Risk Through Machine Learning Based on Lifestyle Questionnaire Data},
  author    = {Chavez-Caceres, Samir and Hincho-Jove, Angel and Castro-Gutierrez, Eveling and Soriano-Vargas, Aurea},
  booktitle = {2024 IEEE International Conference on Automation/XXVI Congress of the Chilean Association of Automatic Control (ICA-ACCA)},
  year      = {2024},
  doi       = {10.1109/ICA-ACCA62622.2024.10766818},
}
```

## Limitations and next steps

- The datasets are small lifestyle questionnaires, so the results may not
  generalize beyond that population.
- The notebooks were written on Colab; local runs need the `read_csv` paths
  adjusted.
- Next: external validation on an independent cohort, and calibration of the
  predicted probabilities.

## License

Code is under the MIT License (see [LICENSE](LICENSE)). The paper is published by
IEEE; read it on [IEEE Xplore](https://ieeexplore.ieee.org/document/10766818).
