# COMPAS Fairness Analysis: A Comprehensive Study

A detailed analysis of algorithmic fairness in the COMPAS (Correctional Offender Management Profiling for Alternative Sanctions) recidivism prediction system, examining racial disparities in predictive accuracy, calibration, and feature importance.

## 📋 Project Overview

This project conducts a multi-faceted examination of the COMPAS algorithm's performance across racial groups, specifically comparing outcomes for African-American and Caucasian defendants. The analysis addresses critical questions about algorithmic fairness in criminal justice decision-making.

## 🔍 Research Questions

1. **Does COMPAS exhibit differential predictive accuracy across racial groups?**
2. **What factors (age, prior convictions, race) most strongly influence COMPAS risk scores?**
3. **Is COMPAS well-calibrated for predicting actual recidivism rates across different racial groups?**

## 📊 Analyses Included

### 1. Predictive Accuracy by Race
**Location:** Cells 1-18

**Methods:**
- Confusion matrix analysis for each racial group
- Calculation of key performance metrics:
  - False Positive Rate (FPR)
  - False Negative Rate (FNR)
  - True Positive Rate (TPR/Recall)
  - Accuracy
  - Precision
- Two-proportion z-tests for statistical significance

**Key Findings:**
- Comparison of error rates between African-American and Caucasian defendants
- Statistical testing of differential accuracy
- Visualization of confusion matrices and performance metrics

---

### 2. Multiple Linear Regression Analysis
**Location:** Cells 19-20

**Methods:**
- Multiple regression controlling for:
  - Age
  - Prior conviction count
  - Race (African-American vs. Caucasian)
- Ordinary Least Squares (OLS) regression
- Statistical significance testing of predictors

**Purpose:**
- Isolate the effect of race on COMPAS scores after controlling for legitimate risk factors
- Examine whether racial disparities persist even when accounting for criminal history

**Outputs:**
- Regression coefficients
- P-values and confidence intervals
- Model diagnostics (R², residuals)

---

### 3. Feature Importance Analysis
**Location:** Cells 21-22

**Methods:**
- **Linear Regression**: Coefficient-based feature importance
- **Random Forest**: Tree-based feature importance
- Visualization of top features driving risk scores

**Features Analyzed:**
- Age
- Sex
- Prior conviction count
- Race
- Charge degree

**Purpose:**
- Understand which variables have the strongest predictive power
- Compare linear vs. non-linear feature importance
- Identify potential sources of bias

---

### 4. Calibration Analysis
**Location:** Cell 23

**Methods:**
- Calibration curves (expected vs. observed recidivism rates)
- **Brier Score**: Overall prediction accuracy metric
- **Hosmer-Lemeshow Test**: Goodness-of-fit testing
- Decile-level calibration tables

**Purpose:**
- Assess whether predicted probabilities match actual outcomes
- Examine calibration separately for each racial group
- Test whether COMPAS is equally well-calibrated across demographics

**Outputs:**
- Calibration plots comparing races to perfect calibration
- Statistical tests of calibration quality
- Quantitative calibration metrics

## 🛠️ Technical Stack

### Core Libraries
```python
pandas          # Data manipulation
numpy           # Numerical computing
matplotlib      # Visualization
seaborn         # Statistical visualization
```

### Statistical Analysis
```python
scipy           # Statistical tests
statsmodels     # Regression analysis
```

### Machine Learning
```python
scikit-learn    # Random Forest, preprocessing, metrics
```

## 📦 Installation

1. Clone this repository:
```bash
git clone https://github.com/YOUR_USERNAME/compas-fairness-analysis.git
cd compas-fairness-analysis
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Launch Jupyter:
```bash
jupyter notebook finalProject.ipynb
```

## 📁 Dataset

**Required file:** `compas_final_merged.csv`

**Required columns:**
- `person_id`: Unique identifier
- `age`: Defendant age
- `sex`: Male/Female
- `race`: Racial category
- `decile_score`: COMPAS risk score (1-10)
- `score_text`: Risk category (Low/Medium/High)
- `priors_count`: Number of prior convictions
- `two_year_recid`: Binary recidivism outcome
- `c_charge_degree`: Charge severity
- `screening_date`: Date of assessment
- `date_of_birth`: Defendant DOB
- `raw_score`: Raw COMPAS score
- `is_completed`: Completion status

**Important:** The dataset is not included in this repository. Update the file path in the notebook:
```python
file_path = "/path/to/your/compas_final_merged.csv"
```

**Data Source:** The COMPAS dataset is publicly available from ProPublica's analysis.

## 📈 Results Structure

Each analysis section produces:
1. **Numerical outputs**: Statistical test results, coefficients, metrics
2. **Visualizations**: Plots, charts, and confusion matrices
3. **Interpretations**: What the results mean for algorithmic fairness

## 🔑 Key Concepts

### Fairness Metrics
- **Predictive Parity**: Equal FPR across groups
- **Error Rate Balance**: Equal FNR across groups
- **Calibration**: Predicted probabilities match observed rates
- **Overall Accuracy**: Correct predictions across groups

### Why Multiple Approaches?
Different fairness criteria can conflict. This analysis examines:
- **Individual prediction accuracy** (confusion matrices)
- **Systemic bias** (regression controlling for confounds)
- **Feature influence** (what drives scores)
- **Probability calibration** (reliability of risk estimates)

## 📝 Usage Notes

1. **File Paths**: Update all file paths to match your local setup
2. **Data Filtering**: The analysis focuses on African-American and Caucasian defendants
3. **Missing Data**: NaN values are dropped; ensure sufficient sample size
4. **Reproducibility**: Set random seeds for Random Forest analysis

## 🚀 Future Enhancements

Potential extensions:
- [ ] Add additional racial/ethnic groups
- [ ] Temporal analysis of score consistency
- [ ] Intersectional analysis (race × gender)
- [ ] Alternative fairness metrics (equalized odds)
- [ ] Cross-validation for predictive models
- [ ] Cost-sensitive analysis
- [ ] Comparison with alternative risk assessment tools

## 📚 References

### Key Papers
- **ProPublica's Analysis**: "Machine Bias" (2016)
- **Northpointe's Response**: Practitioner's Guide to COMPAS
- **Academic Research**: Chouldechova (2017), Kleinberg et al. (2017)

### Fairness in ML
- Fairness Definitions Explained (Verma & Rubin, 2018)
- The Impossibility Theorem (Kleinberg, Mullainathan, Raghavan, 2017)

## ⚖️ Ethical Considerations

This project analyzes algorithmic fairness in criminal justice. Key considerations:
- COMPAS scores influence real sentencing and parole decisions
- Algorithmic bias can perpetuate systemic inequalities
- Multiple fairness criteria may be incompatible
- Statistical parity doesn't guarantee individual fairness

## 📄 License

This project is open source and available under the MIT License.

## 🤝 Contributing

Contributions are welcome! Areas for contribution:
- Additional statistical tests
- Improved visualizations
- Documentation improvements
- Bug fixes
- New fairness metrics

## 👤 Author

**Your Name**
- GitHub: [@yourusername](https://github.com/yourusername)
- Email: your.email@example.com

## 🙏 Acknowledgments

- ProPublica for the original COMPAS investigation
- The algorithmic fairness research community
- Open-source Python scientific computing ecosystem

---

**Note:** This analysis is for educational and research purposes. Results should be interpreted carefully in the context of criminal justice policy debates.
