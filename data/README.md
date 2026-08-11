# Data

The datasets are **not redistributed here**; download them from their sources.

## Survey Lung Cancer (Kaggle)

The main dataset is the public "Lung Cancer" survey dataset (~300 responses,
binary target `LUNG_CANCER`, lifestyle/symptom features):

- Kaggle: search for **"survey lung cancer"** (dataset by *mysarahmadbhat*).
- Download `survey lung cancer.csv` into this folder.

Then update the `read_csv` path in the notebooks (they were authored on Google
Colab, so they reference `/content/...`):

```python
df = pd.read_csv("data/survey lung cancer.csv")
```

The data is an anonymous questionnaire (no personal identifiers). Please follow
the dataset's own license terms on Kaggle.
