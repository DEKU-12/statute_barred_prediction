# Statute-Barred Debt Collection Prediction

Machine learning project to predict whether a debt is **statute-barred** using account/customer and collections-related features.

## Problem
In debt collection, statute-barred accounts have legal/time limitations that can affect collectability.  
This project builds a classification model to predict **IsStatBarred** and evaluates performance using standard ML metrics.

## What I did (from the notebook)
### 1) Data loading
- Loaded the dataset from Excel: `Company_x.xlsx`

### 2) Data cleaning + preprocessing
- Handled missing values (examples):
  - Filled `PurchasePrice` and `NumLiableParties` using mode
  - Filled `CustomerAge` using median
- Removed columns not needed for modeling (e.g., insolvency types, last payment details, closure reason, contact counts, product/status fields, identifiers, etc.)
- Encoded categorical variables using `LabelEncoder`
- Scaled numeric features using `StandardScaler` (applied column-wise)

### 3) Modeling + evaluation
Trained and evaluated multiple classifiers:

**XGBoost (XGBClassifier)**
- K-Fold cross-validation
- Metrics: Accuracy + Classification Report
- ROC-AUC score + ROC curve
- Confusion matrix

**Random Forest (RandomForestClassifier)**
- K-Fold cross-validation
- Hyperparameter tuning using `GridSearchCV`:
  - `n_estimators`: [100, 200, 300]
  - `max_depth`: [None, 2, 4, 8]
  - `min_samples_split`: [2, 3, 5, 10]
  - `min_samples_leaf`: [2, 3, 4]
  - `max_features`: ['auto', 'sqrt', 'log2']

## Files
- `statute-barred prediction.ipynb` — main notebook (cleaning → preprocessing → models → evaluation)
- `Company_x.xlsx` — dataset (add to repo or provide download instructions)


## Tech stack
- Python
- Pandas, NumPy
- scikit-learn (train/test split, scaling, metrics, Random Forest, GridSearchCV)
- XGBoost (XGBClassifier)
- Matplotlib / Seaborn (plots)
- Jupyter Notebook

## How to run
```bash
python -m venv .venv
# mac/linux
source .venv/bin/activate
# windows
# .venv\Scripts\activate

pip install pandas numpy scikit-learn xgboost matplotlib seaborn openpyxl jupyter

jupyter notebook
