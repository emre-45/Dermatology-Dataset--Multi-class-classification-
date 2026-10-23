# Dermatology Dataset – Multi-class Classification

Classifying six erythemato-squamous skin diseases from 34 clinical and histopathological features using tree-based models.

## Dataset

`dermatology_database_1.csv`: 366 patients, 34 features, 6 classes.

- 32 features are graded 0–3, `family_history` is 0/1, and `age` is an integer (8 values missing)
- Classes: 1 psoriasis, 2 seborrheic dermatitis, 3 lichen planus, 4 pityriasis rosea, 5 chronic dermatitis, 6 pityriasis rubra pilaris

## Approach

1. Exploratory analysis of feature distributions per class (see `dermatology_eda.html`)
2. Stratified 80/20 train/test split
3. Preprocessing: median imputation and 4-bin discretization of `age`
4. Decision Tree, Random Forest and Gradient Boosting, tuned with `RandomizedSearchCV` (60 iterations, 5-fold stratified CV, refit on macro F1)
5. Final evaluation of the best model on the held-out test set

## Results

| Model | CV macro F1 |
|---|---|
| **Random Forest** | **0.985 ± 0.008** |
| Gradient Boosting | 0.971 ± 0.029 |
| Decision Tree | 0.953 ± 0.016 |

Random Forest on the test set: accuracy 0.959, macro F1 0.943, weighted ROC AUC 0.998.

## Files

- `dermatology_final.ipynb`: full notebook (EDA, tuning, evaluation)
- `dermatology_eda.html`: exported EDA report
- `dermatology_database_1.csv`: dataset

## Requirements

Python 3 with `numpy`, `pandas`, `matplotlib`, `scipy` and `scikit-learn`.
