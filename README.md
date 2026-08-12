# lung-cancer-risk-ml

Predicting lung cancer risk from a lifestyle questionnaire with machine
learning - the code and materials behind our paper:

> **Prediction of Lung Cancer Risk through Machine Learning based on Lifestyle
> Questionnaire Data.**
> Samir Diego Chávez Cáceres, Angel Eduardo Hincho Jove, Maribel Molina
> (Universidad Nacional de San Agustín, UNSA), Aurea Soriano-Vargas
> (Universidade Estadual de Campinas, UNICAMP). Published in IEEE Xplore.
>
> 📄 IEEE Xplore: `<add DOI / link>` · see [`paper/`](paper/) for the manuscript and poster.

## What it does

Lung cancer is the leading cause of cancer mortality worldwide. This work
explores a low-cost, questionnaire-based screening aid: given lifestyle and
symptom answers (smoking, anxiety, chronic disease, wheezing, ...), classify
whether a person is at risk, with the model's reasoning made inspectable.

Pipeline:

1. **EDA** - univariate and multivariate analysis of the questionnaire data.
2. **Imbalance handling** - the positive class is over-represented, so the
   minority class is balanced with **SMOTE**.
3. **Models** - Logistic Regression, SVC, Decision Tree, Random Forest, a Keras
   neural net, and **XGBoost** (the proposed model), tuned with
   **GridSearchCV** on a 70/30 split.
4. **Explainability** - **LIME** for local, per-prediction interpretability, so
   a risk score comes with the factors that drove it.

## Results (from the paper)

| Dataset | Accuracy | F1 | Precision | Sensitivity |
|---------|---------:|---:|----------:|------------:|
| Dataset 1 | 96.50% | 96.50% | 96.51% | 96.51% |
| Dataset 2 | 95.83% | 95.83% | 96.27% | 95.83% |

Model: XGBoost, after SMOTE balancing and GridSearchCV tuning.

## Repository

```
notebooks/
  01_eda_and_models.ipynb        # EDA + model comparison
  02_survey_dataset_models.ipynb # second dataset (Kaggle "survey lung cancer")
paper/
  lung-cancer-risk-ml-paper.pdf  # authors' manuscript
  poster.pdf                     # conference poster
data/README.md                   # how to get the datasets (not redistributed)
```

The notebooks were authored on Google Colab (paths like `/content/...`); point
the `read_csv` calls at your local copy of the data (see [`data/`](data/)).

## Reproduce

```bash
pip install -r requirements.txt
# download the dataset (see data/README.md), then run the notebooks
jupyter lab
```

## Citation

```bibtex
@inproceedings{chavez_lung_cancer_ml,
  title     = {Prediction of Lung Cancer Risk through Machine Learning based on Lifestyle Questionnaire Data},
  author    = {Ch\'avez C\'aceres, Samir Diego and Hincho Jove, Angel Eduardo and Molina, Maribel and Soriano-Vargas, Aurea},
  booktitle = {IEEE Xplore},
  year      = {<add year>},
  note      = {DOI: <add>}
}
```

## License

Code is released under the MIT License (see [LICENSE](LICENSE)). The paper and
poster in [`paper/`](paper/) are the authors' work; see [`paper/README.md`](paper/README.md)
for reuse and the IEEE copyright note.
