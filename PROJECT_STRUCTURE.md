# Project Structure

## File Organization

```
compas-fairness-analysis/
│
├── README.md                    # Main project documentation
├── requirements.txt             # Python dependencies
├── .gitignore                   # Files to exclude from Git
├── finalProject.ipynb          # Main analysis notebook
├── GITHUB_GUIDE.md             # Step-by-step GitHub setup guide
├── COMMANDS.md                  # Quick Git command reference
└── LICENSE                      # (Optional) Project license
```

## Notebook Structure

### finalProject.ipynb

The notebook is organized into 4 main analysis sections:

#### Section 1: Data Audit & Predictive Accuracy (Cells 0-18)
- **Cell 0**: Quick Data Audit header
- **Cells 1-6**: Data loading, cleaning, and preparation
- **Cell 7**: Confusion matrix setup
- **Cell 8-9**: Confusion matrix calculation and visualization
- **Cell 10-11**: Performance metrics (FPR, FNR, TPR, Accuracy)
- **Cells 12-15**: Statistical hypothesis testing (z-tests)
- **Cells 16-18**: Summary tables and visualizations

**Outputs:**
- Confusion matrices for each racial group
- Bar charts comparing error rates
- Statistical significance tests

---

#### Section 2: Multiple Linear Regression (Cells 19-20)
- **Cell 19**: Section header
- **Cell 20**: Full regression analysis

**Predictors:**
- Age
- Prior conviction count
- Race (binary: African-American vs. Caucasian)

**Target Variable:**
- COMPAS decile score

**Outputs:**
- OLS regression summary
- Coefficient estimates
- Statistical significance (p-values)
- Model fit statistics (R², adjusted R²)

---

#### Section 3: Feature Importance Analysis (Cells 21-22)
- **Cell 21**: Section header
- **Cell 22**: Dual model comparison

**Models:**
1. **Linear Regression**: Feature coefficients
2. **Random Forest**: Gini importance scores

**Features:**
- Age
- Sex
- Prior count
- Race
- Charge degree

**Outputs:**
- Side-by-side bar charts
- Ranked feature importance
- Model comparison insights

---

#### Section 4: Calibration Analysis (Cell 23)
- **Cell 23**: Complete calibration study

**Methods:**
- Calibration curves (observed vs. expected)
- Brier score calculation
- Hosmer-Lemeshow goodness-of-fit test

**Outputs:**
- Calibration plots for each race
- Numerical calibration metrics
- Statistical test results
- Calibration tables by decile

---

## Data Flow

```
Raw Data (compas_final_merged.csv)
    ↓
Data Cleaning & Filtering
    ↓
Four Parallel Analyses:
    ├── Predictive Accuracy → Confusion matrices, metrics
    ├── Regression Analysis → Coefficients, p-values
    ├── Feature Importance → Linear + RF models
    └── Calibration → Curves, Brier scores, H-L tests
```

## Key Variables

### Input Variables
- `race`: African-American, Caucasian (other races excluded)
- `age`: Defendant age at screening
- `sex`: Male/Female
- `priors_count`: Number of prior convictions
- `decile_score`: COMPAS risk score (1-10)
- `score_text`: Low/Medium/High risk category
- `c_charge_degree`: Felony/Misdemeanor
- `two_year_recid`: Binary recidivism outcome (0/1)

### Derived Variables
- `predicted_high`: Binary prediction (Medium/High = 1, Low = 0)
- `Expected_Risk`: decile_score / 10 (for calibration)
- Race dummy variables (for regression)

## Analysis Dependencies

### Section 1 Dependencies
```python
pandas, numpy, matplotlib, seaborn, statsmodels.stats.proportion
```

### Section 2 Dependencies
```python
pandas, statsmodels.api (OLS), seaborn, matplotlib
```

### Section 3 Dependencies
```python
sklearn.preprocessing (LabelEncoder)
sklearn.linear_model (LinearRegression)
sklearn.ensemble (RandomForestRegressor)
matplotlib, numpy
```

### Section 4 Dependencies
```python
pandas, numpy, matplotlib
sklearn.metrics (brier_score_loss)
scipy.stats (chi2)
```

## Common Modifications

### Change File Path
Update in cells: 1, 20, 22, 23
```python
file_path = "/Users/akanksha/Downloads/compas_final_merged.csv"
# Change to:
file_path = "/your/path/to/compas_final_merged.csv"
```

### Add More Racial Groups
Currently filters to African-American and Caucasian:
```python
data = data[data['race'].isin(['African-American', 'Caucasian'])]
# Modify to include others:
data = data[data['race'].isin(['African-American', 'Caucasian', 'Hispanic'])]
```

### Adjust Random Forest Parameters
Cell 22:
```python
rf = RandomForestRegressor(n_estimators=100, random_state=42)
# Adjust:
rf = RandomForestRegressor(n_estimators=500, max_depth=10, random_state=42)
```

## Running the Analysis

### Full Run
Execute all cells sequentially:
```
Kernel → Restart & Run All
```

### Individual Sections
- **Predictive Accuracy**: Run cells 0-18
- **Regression**: Run cells 1-6, then 19-20
- **Feature Importance**: Run cells 1-6, then 21-22
- **Calibration**: Run cells 1-6, then 23

### Prerequisites
Each section requires the data loading and cleaning from cells 1-6.

## Output Files

The notebook generates visualizations but doesn't save files by default.

To save outputs, add after plotting:
```python
plt.savefig('confusion_matrix.png', dpi=300, bbox_inches='tight')
```

## Troubleshooting

### Common Issues

**1. File not found**
- Update `file_path` variable
- Ensure CSV is in correct location

**2. Missing columns**
- Verify CSV has required columns
- Check column name spelling/capitalization

**3. FutureWarnings**
- Pandas groupby warnings (cells with Hosmer-Lemeshow)
- Add `observed=True` to groupby calls:
```python
obs = df_hl.groupby('group', observed=True)['y'].agg(['sum','count'])
```

**4. Import errors**
- Install missing packages: `pip install package-name`
- Check requirements.txt

## Next Steps After Upload

1. Create a `data/` folder for datasets (add to .gitignore)
2. Create a `results/` folder for saved plots
3. Add example outputs to README
4. Create a separate analysis script (.py) for production use
5. Add unit tests for key functions
