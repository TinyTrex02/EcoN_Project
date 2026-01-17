# Eco Project - Task Checklist

## Project Information
- Course: MN52080 Econometrics and Data Analysis for Accounting and Finance
- University: University of Bath, School of Management
- Due Date: Friday 12 December 2025, 14:00 (GMT)
- Instructor: Dr. Qinye Lu (ql762@bath.ac.uk)
- Weight: 40% of overall assessment

---

## PHASE 1: DATA PREPARATION & EXPLORATION

### Data Loading
- [ ] Load `Goyal_Welch_data.xlsx` (1,824 monthly observations from 1871+)
- [ ] Load `vulnerability.csv` (192 countries, 1995-2023)
- [ ] Extract US data from vulnerability.csv
- [ ] Understand date format (yyyymm in Excel file)

### Data Cleaning & Merging
- [ ] Select appropriate time period (suggest: Jan 1991 - Dec 2020)
- [ ] Extend annual ND-GAIN scores to monthly frequency
  - Assign same value to all 12 months of each year
- [ ] Merge datasets on date
- [ ] Check for missing values
- [ ] Document data gaps and exclusions
- [ ] Handle outliers (consider winsorization at 1% or 5%)

### Descriptive Statistics
- [ ] Calculate summary statistics (mean, std, min, max)
- [ ] Create correlation matrix
- [ ] Generate time series plots
- [ ] Document data limitations

---

## PHASE 2: VARIABLE CONSTRUCTION & SELECTION

### Dependent Variable
- [ ] Calculate Excess Returns = CRSP_SPvw - Rfree
- [ ] Verify units and scaling

### Independent Variables - MANDATORY
- [ ] ND-GAIN Vulnerability Score (climate vulnerability)

### Independent Variables - CONSTRUCT (Choose from):
- [ ] Dividend Price Ratio (d/p) = D12 / Index
- [ ] Dividend Yield (d/y) = D12 / Index
- [ ] Dividend Payout Ratio (d/e) = D12 / E12
- [ ] Default Yield Spread (dfy) = BAA - AAA
- [ ] Term Spread (tms) = lty - tbl
- [ ] Default Return Spread (dfr) = corpr - ltr
- [ ] Book-to-Market Ratio (b/m)
- [ ] Net Equity Expansion (ntis)
- [ ] Inflation (infl)

### Model Specification
- [ ] Select minimum 3 total independent variables (including ND-GAIN)
- [ ] Write out econometric model: y = β0 + β1*X1 + β2*X2 + β3*X3 + ε
- [ ] Document expected signs and reasoning for each variable
- [ ] Justify variable selection based on financial/economic theory

---

## PHASE 3: REGRESSION ANALYSIS

### Main Regression
- [ ] Run OLS regression
- [ ] Estimate coefficients (β values)
- [ ] Calculate standard errors
- [ ] Report t-statistics and p-values
- [ ] Calculate R-squared (R²)
- [ ] Calculate adjusted R-squared (Adj R²)
- [ ] Calculate F-statistic and p-value
- [ ] Interpret each coefficient in economic terms
- [ ] Discuss significance using "ceteris paribus" language

### Output & Interpretation
- [ ] Create regression output table
- [ ] Interpret model fit (R² and F-stat)
- [ ] Discuss economic meaning of each coefficient
- [ ] Analyze statistical significance (α = 0.05 level)
- [ ] Discuss omitted variable bias for key excluded variables

---

## PHASE 4: DIAGNOSTIC TESTS (Most Important - 32 marks)

### Test 1: Multicollinearity
- [ ] Calculate Variance Inflation Factors (VIF) for all variables
  - Identify VIF > 5 or 10 as problematic
- [ ] Create correlation matrix
  - Flag correlations > 0.8 as potentially problematic
- [ ] Interpret results
- [ ] If problematic: 
  - [ ] Remove or combine variables
  - [ ] Re-run regression
- [ ] Document actions taken

### Test 2: Normality of Residuals
- [ ] Extract residuals from regression
- [ ] Jarque-Bera (JB) test
  - H0: Residuals are normally distributed
  - Calculate JB statistic
  - Report p-value
- [ ] Shapiro-Wilk test (alternative)
- [ ] Visual inspection: Q-Q plot
- [ ] Visual inspection: Histogram of residuals
- [ ] Interpret findings
- [ ] Document implications if non-normal

### Test 3: Heteroskedasticity
- [ ] Breusch-Pagan test
  - H0: Homoskedastic (constant variance)
  - Calculate LM statistic
  - Report p-value
- [ ] White test (robust alternative)
  - Calculate test statistic
  - Report p-value
- [ ] Plot residuals vs. fitted values
- [ ] Interpret advantages/limitations of each test
- [ ] If detected:
  - [ ] Calculate robust standard errors (Heteroskedasticity-Robust)
  - [ ] Compare with original standard errors
  - [ ] Update t-statistics and p-values

### Test 4: Autocorrelation
- [ ] Durbin-Watson (DW) test
  - Calculate DW statistic
  - Interpret value (2 = no autocorrelation)
  - Check against critical values
- [ ] Breusch-Godfrey test (LM test)
  - Test for AR(1) or higher orders
  - Report test statistic and p-value
  - H0: No autocorrelation
- [ ] Plot residuals over time
- [ ] Discuss advantages/limitations of each test
- [ ] If detected:
  - [ ] Consider using Newey-West standard errors
  - [ ] Discuss alternative models if needed
  - [ ] Update inference based on corrected standard errors

### Diagnostic Summary
- [ ] Create summary table of all test results
- [ ] Document any violations and corrective actions
- [ ] Discuss implications for model reliability

---

## PHASE 5: STRUCTURAL ANALYSIS

### Recession Dummy Variable
- [ ] Research US recession dates (NBER/Wikipedia list)
- [ ] Create binary recession indicator (1 = recession, 0 = normal)
- [ ] Run new regression with recession dummy
- [ ] Interpret recession coefficient
  - Does it change returns during recessions?
  - Is it statistically significant?
- [ ] Analyze interaction effects if relevant
  - Does vulnerability affect returns differently in recessions?

### Structural Break Analysis
- [ ] Identify potential break points (e.g., 2008 financial crisis)
- [ ] Use Chow test to formally test for structural break
  - Split sample at suspected break point
  - Compare RSS of restricted vs. unrestricted models
  - Report test statistic and p-value
- [ ] If break exists:
  - [ ] Estimate separate models for each period
  - [ ] Compare coefficients across periods
  - [ ] Discuss economic meaning of the break
- [ ] Document conclusions about model stability

---

## PHASE 6: REPORT WRITING & PRESENTATION

### Report Structure (1,500 ± 10% words, excluding tables/figures)
- [ ] Cover page with 9-digit student number only (no name)
- [ ] Introduction
  - [ ] Outline research question
  - [ ] State objective
  - [ ] Discuss climate vulnerability relevance
- [ ] Literature & Motivation (5 marks)
  - [ ] Economic/financial reasoning (12 marks)
  - [ ] Model specification and variable justification
- [ ] Data Description (12 marks)
  - [ ] Data sources and coverage
  - [ ] Time period selection
  - [ ] Missing values and treatments
  - [ ] Descriptive statistics table
  - [ ] Data limitations
- [ ] Regression Results (15 marks)
  - [ ] Present main regression table
  - [ ] Interpret R² and F-statistic
  - [ ] Discuss each coefficient
- [ ] Diagnostic Tests (32 marks)
  - [ ] Multicollinearity results and interpretation
  - [ ] Normality test results
  - [ ] Heteroskedasticity test results
  - [ ] Autocorrelation test results
  - [ ] Summary table of diagnostics
  - [ ] Corrective actions taken
- [ ] Recession & Structural Break (18 marks)
  - [ ] Recession analysis results
  - [ ] Structural break test results
  - [ ] Interpretation and implications
- [ ] Conclusion
  - [ ] Summary of findings
  - [ ] Limitations and future work
- [ ] References (minimum from provided list)
- [ ] Appendices (code, detailed tables, plots)

### Formatting
- [ ] 1,500 ± 10% word count (verified)
- [ ] Proper academic style (no casual language)
- [ ] Professional tables (clear headers, proper formatting)
- [ ] Professional figures (labeled axes, legends)
- [ ] Proper citations (in-text and reference list)
- [ ] File naming: `[9DigitStudentNumber].pdf`

### Code Submission
- [ ] Python code (.ipynb or .py)
- [ ] Well-commented and organized
- [ ] File naming: `[9DigitStudentNumber]_code.ipynb` or `.py`
- [ ] Includes all analysis steps
- [ ] Can be run to reproduce results

---

## PHASE 7: FINAL REVIEW & SUBMISSION

### Quality Checks
- [ ] Word count verified (1,500 ± 10%)
- [ ] All marks criteria addressed (100 total)
- [ ] References properly formatted
- [ ] Tables and figures professional
- [ ] Economic reasoning clear and sound
- [ ] Diagnostic tests thoroughly interpreted
- [ ] Spelling and grammar checked
- [ ] Citations accurate and complete

### File Preparation
- [ ] Report file: `[StudentNumber].pdf`
- [ ] Code file: `[StudentNumber]_code.ipynb` or `.py`
- [ ] Both files ready for Moodle submission
- [ ] Verified file names are correct

### Submission
- [ ] Submit to Moodle before Friday 12 December 2025, 14:00 GMT
- [ ] Confirm receipt of submission
- [ ] Keep copies of submitted files

---

## MARKS ALLOCATION CHECKLIST

| Criterion | Expected Marks | Status |
|-----------|---|---|
| Research question outline | 5 | [ ] |
| Economic reasoning & model specification | 12 | [ ] |
| Data formation & description | 12 | [ ] |
| Regression analysis | 15 | [ ] |
| Diagnostic tests | 32 | [ ] |
| Recession & structure break | 18 | [ ] |
| Presentation, references, format | 6 | [ ] |
| **TOTAL** | **100** | [ ] |

---

## KEY DATES & DEADLINES

- **Analysis Period:** Choose a 30-year window (e.g., Jan 1991 - Dec 2020)
  - Data covers 1871-2023, so flexibility exists
- **Code Development:** Ongoing throughout project
- **Report Draft:** Should be completed 2-3 weeks before deadline
- **Final Submission:** Friday 12 December 2025, 14:00 GMT

---

## QUICK REFERENCE: KEY FORMULAS & TESTS

### Variables
```
Excess_Return = CRSP_SPvw - Rfree
d/p = D12 / Index
d/y = D12 / Index
d/e = D12 / E12
dfy = BAA - AAA
tms = lty - tbl
dfr = corpr - ltr
```

### Regression Model
```
Excess_Return = β0 + β1*ND_GAIN + β2*Var2 + β3*Var3 + ε
```

### Key Tests
- **Multicollinearity:** VIF, Correlation matrix
- **Normality:** Jarque-Bera, Shapiro-Wilk, Q-Q plot
- **Heteroskedasticity:** Breusch-Pagan, White test, Robust SE
- **Autocorrelation:** Durbin-Watson, Breusch-Godfrey, Newey-West SE
- **Structural Break:** Chow test

---

## COMMON MISTAKES TO AVOID

1. Not extending annual ND-GAIN data to monthly/quarterly
2. Using the wrong stock return variable (use CRSP_SPvw with dividends)
3. Forgetting to calculate excess returns (must subtract Rfree)
4. Not addressing missing values explicitly
5. Running diagnostics but not interpreting them properly
6. Ignoring econometric issues (heteroskedasticity, autocorrelation)
7. Not using recession dates properly (must use NBER official dates)
8. Exceeding word count or not excluding tables/figures properly
9. Weak economic reasoning for variable selection
10. Not providing corrective actions for diagnostic test failures

---

## RESOURCES & HELPFUL LINKS

- **ND-GAIN Data:** https://gain.nd.edu/our-work/country-index/download-data/
- **US Recession Dates:** https://en.wikipedia.org/wiki/List_of_recessions_in_the_United_States
- **Key References:** See PROJECT_README.md for full citation list
- **Contact:** Dr. Qinye Lu (ql762@bath.ac.uk)

---

## NOTES SECTION (For Your Comments)

```
Add your notes here as you progress:

Week 1 - Data Preparation:
[Your notes here]

Week 2-3 - Analysis & Testing:
[Your notes here]

Week 4 - Report Writing:
[Your notes here]

Final Review:
[Your notes here]
```

---

**Status:** Ready to Begin
**Last Updated:** 2025-11-13

