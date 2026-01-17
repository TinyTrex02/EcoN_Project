# Eco Project - Comprehensive Analysis

## Directory Overview
Location: `/Users/rexy/Desktop/Learn_Git/Eco/`

The Eco directory contains three files:
1. **EcoN_Project.pdf** (260.5 KB) - Project specification document
2. **Goyal_Welch_data.xlsx** (261.994 KB) - Monthly financial and economic data
3. **vulnerability.csv** (100.905 KB) - Climate vulnerability index data

---

## PROJECT OVERVIEW

This is an **Econometrics and Data Analysis project** (MN52080) from the University of Bath, School of Management for AY 2025-2026.

**Due Date:** Friday 12 December 2025, 14:00 (GMT)
**Weight:** 40% of overall assessment
**Unit Convenor:** Dr. Qinye Lu (ql762@bath.ac.uk)

### Project Scope
- **Type:** Individual empirical project work
- **Format:** Word or PDF report (max 1,500 ± 10% words, excluding tables, graphics, references, appendices)
- **Code Submission:** Python (.py or .ipynb file)
- **Research Focus:** US stock market returns and climate vulnerability

---

## PROJECT PURPOSE & RESEARCH QUESTION

The project examines whether **climate vulnerability** (measured by the Notre Dame Global Adaptation Initiative ND-GAIN Index) affects US stock market returns, along with traditional financial/economic variables.

### Central Research Question:
**How does climate vulnerability - measured by the ND-GAIN Vulnerability Score - along with other traditional factors, affect stock market returns and how does this impact vary during periods of heightened economic risk?**

### Key Concepts:
- **Climate Vulnerability:** A country's degree of exposure to climate change effects and ability to cope with them
- **ND-GAIN Vulnerability Score:** Ranges from 0 (low vulnerability) to 1 (high vulnerability)
  - 0.27 = Low vulnerability (strong adaptive capacity)
  - 0.49 = Moderate vulnerability (noticeable risk but some resilience)
  - 0.65 = High vulnerability (more exposed, less able to cope)
- **Focus:** US market only (USA score approximately 0.31, indicating relatively low vulnerability)

### Theoretical Context:
- Research shows higher climate vulnerability can increase economic volatility, reduce productivity, and elevate borrowing costs
- Climate-related shocks influence asset prices and risk premia
- Financial markets increasingly price in climate risks
- May translate to higher risk premia and lower equity valuations

---

## DATA FILES

### 1. Goyal_Welch_data.xlsx
**Structure:** Single sheet named "Monthly"
- **Size:** 1,824 rows × 16 columns
- **Time Coverage:** From January 1871 to recent period (monthly data)
- **Data Quality:** Many historical gaps (NaN values)

#### Available Variables:
| Variable | Description | Non-Null Count | Notes |
|----------|-------------|-----------------|-------|
| yyyymm | Date (year-month format) | 1,824 | Complete |
| Index | S&P 500 index price | 1,824 | Complete |
| D12 | 12-month moving sum of dividends (S&P 500) | 1,824 | Complete |
| E12 | 12-month moving sum of earnings (S&P 500) | 1,824 | Complete |
| b/m | Book-to-Market ratio (Dow Jones Industrial Average) | 1,222 | 66% complete |
| tbl | Treasury Bill rates (3-month) | 1,236 | 68% complete |
| AAA | Corporate Bond Yields (AAA-rated) | 1,248 | 68% complete |
| BAA | Corporate Bond Yields (BAA-rated) | 1,248 | 68% complete |
| lty | Long-term government bond yields | 1,248 | 68% complete |
| ntis | Net Equity Expansion ratio | 1,153 | 63% complete |
| Rfree | Risk-free rate (Treasury-bill) | 1,823 | 99.9% complete |
| infl | Inflation (Consumer Price Index) | 1,319 | 72% complete |
| ltr | Long-term rate of return (govt bonds) | 1,164 | 64% complete |
| corpr | Long-term corporate bond returns | 1,164 | 64% complete |
| CRSP_SPvw | S&P 500 returns (including dividends) | 1,164 | 64% complete |
| CRSP_SPvwx | S&P 500 returns (excluding dividends) | 1,164 | 64% complete |

**Data Sources:**
- Robert Shiller's website (dividends 1871-1987)
- S&P Corporation (dividends 1988+)
- NBER Macrohistory Database
- Federal Reserve Economic Data (FRED)
- Ibbotson's Stocks, Bonds, Bills and Inflation Yearbook
- Center for Research in Security Press (CRSP)
- Bureau of Labor Statistics

### 2. vulnerability.csv
**Structure:** Country-year climate vulnerability index
- **Size:** 192 rows (countries) × 31 columns (years 1995-2023)
- **Data Type:** Float values (vulnerability scores)
- **Time Coverage:** Annual data from 1995 to 2023

#### Key Information:
- Column 1: ISO3 (3-letter country codes)
- Column 2: Name (country names)
- Columns 3-31: Years 1995-2023
- **USA Entry:**
  - ISO3: USA
  - Name: United States
  - Values range from 0.317 (1995) to 0.312 (2023)
  - Indicates relatively low and stable vulnerability

---

## REQUIRED VARIABLES TO CONSTRUCT

Students must create the following derived variables from the raw data:

1. **d/p (Dividend Price Ratio)** = D12 / Index
2. **d/y (Dividend Yield)** = D12 / Index (annualized)
3. **d/e (Dividend Payout Ratio)** = D12 / E12
4. **dfy (Default Yield Spread)** = BAA - AAA (spread between BAA and AAA corporate bond yields)
5. **tms (Term Spread)** = lty - tbl (long-term minus short-term yields)
6. **dfr (Default Return Spread)** = corpr - ltr (corporate minus long-term government returns)

These are traditional equity premium predictors from Goyal & Welch (2008).

---

## PROJECT REQUIREMENTS

### 1. Research Question & Model Specification (5 marks)
- Define research question or study objectives
- Explain relationships and expected variable signs using economic reasoning
- Present econometric model clearly
- Justify variable choices

**Requirement:** Minimum 3 independent variables:
  - ND-GAIN Vulnerability Score (mandatory)
  - At least 2 others from traditional financial/macro indicators

### 2. Economic/Financial Reasoning (12 marks)
- Explain theoretical rationale behind model
- Present econometric specification formally
- Discuss why selected variables matter for predicting excess returns

### 3. Data Formation & Description (12 marks)
- Prepare suitable monthly or quarterly dataset
  - Example: 360 observations (30 years monthly, Jan 1991 - Dec 2020)
  - Can choose different time period
- Integrate ND-GAIN Vulnerability Score with rest of dataset
  - Annual ND-GAIN scores must be extended to monthly/quarterly
  - **Method:** Assign same annual value to all months/quarters of that year
- Check for and handle missing values clearly
- Address outliers (suggested: winsorize at 1% or 5%)
- Define data type (e.g., "pooled cross-sectional" or "time-series")
- Discuss data limitations

### 4. Regression Analysis (15 marks)
- Perform multiple regression to estimate parameters
- Explain significance in "ceteris paribus" and "partial effect" contexts
- Interpret test statistics and implications
- Discuss consequences of omitting key variables
- Explain R² and adjusted R²
- Interpret F-statistic
- **Note:** Out-of-sample regression NOT required

### 5. Diagnostic Tests (32 marks - LARGEST SECTION)

#### 5.1 Multicollinearity
- Test for multicollinearity (e.g., VIF, correlation matrix)
- Interpret results
- Resolve if problematic

#### 5.2 Normality of Error Terms
- Determine if error terms are normally distributed
- Appropriate tests required

#### 5.3 Heteroskedasticity
- Test for presence (e.g., Breusch-Pagan, White test)
- Interpret results
- Discuss test advantages and limitations
- Suggest actions if detected

#### 5.4 Autocorrelation
- Test for autocorrelation (e.g., Durbin-Watson, LM test)
- Interpret results
- Discuss test advantages and limitations
- Suggest actions if detected

### 6. Dummy Variable & Structure Break (18 marks)
- Create dummy variable for recession periods
- Run regression with recession indicator
- Provide interpretation
- List of US recessions available on Wikipedia
- Investigate potential structural breaks
- Provide evidence to support conclusions
- **Note:** Don't re-run all diagnostic tests when adding dummy variable

### 7. Presentation, References, Format (6 marks)
- Professional formatting and presentation
- Proper academic references
- 1,500 ± 10% word count (excluding tables, graphics, references, appendices)
- Student number only (9-digit) at beginning
- File naming: `[StudentNumber].pdf` for report, `[StudentNumber]_code.ipynb/py` for code

---

## MARKING SCHEME

| Item | Marks |
|------|-------|
| 1. Question of interest outline | 5 |
| 2. Economic/financial reasoning & econometric specification | 12 |
| 3. Data formation, description, omitted data | 12 |
| 4. Regression analysis (parameters, R², t-tests, F-stat) | 15 |
| 5. Diagnostic tests (distribution, multicollinearity, heteroskedasticity, autocorrelation) | 32 |
| 6. Dummy variable & structure break | 18 |
| 7. Presentation, references, format | 6 |
| **TOTAL** | **100** |

---

## KEY TASKS & INCOMPLETE SECTIONS

### What Needs to Be Done:

1. **Data Integration**
   - Load Goyal_Welch_data.xlsx (monthly observations)
   - Load vulnerability.csv (annual US data)
   - Extend annual ND-GAIN scores to monthly/quarterly
   - Merge datasets on date
   - Select appropriate time period (suggest: 1991-2020 or similar)

2. **Variable Construction**
   - Create derived financial ratios (d/p, d/y, d/e, dfy, tms, dfr)
   - Calculate excess returns (CRSP_SPvw - Rfree)
   - Handle missing values and outliers
   - Descriptive statistics

3. **Variable Selection**
   - Choose minimum 2 additional variables beyond ND-GAIN
   - Options: dividend yield, book-to-market, interest rate spreads, inflation, etc.
   - Justify selections with economic reasoning

4. **Regression Analysis**
   - Run OLS regression with excess returns as dependent variable
   - Estimate coefficients and significance
   - Interpret R² and adjusted R²
   - Analyze F-statistic for overall model fit
   - Interpret each coefficient in economic terms

5. **Diagnostic Testing (Most Important)**
   - Test for multicollinearity (VIF, correlation)
   - Test normality of residuals (Jarque-Bera, Q-Q plot, Shapiro-Wilk)
   - Test heteroskedasticity (Breusch-Pagan, White test)
   - Test autocorrelation (Durbin-Watson, Breusch-Godfrey test)
   - Interpret all tests thoroughly
   - Suggest remedies (e.g., robust standard errors, transformations)

6. **Recession Analysis**
   - Create recession dummy variable based on NBER/Wikipedia dates
   - Rerun regression with dummy variable
   - Interpret differential effects during recessions
   - Analyze whether relationship between variables and returns changes

7. **Structural Break Analysis**
   - Test for structural breaks (e.g., Chow test)
   - Identify potential break points
   - Discuss implications for model stability

8. **Report Writing**
   - Organize findings in 1,500-word report
   - Include tables and figures (don't count toward word limit)
   - Proper citations and references
   - Professional presentation

---

## REFERENCES PROVIDED

Key papers to consult:
- **Goyal & Welch (2008)** - Comprehensive look at equity premium prediction
- **Goyal, Welch & Zafirov (2024)** - 2022 update on equity premium prediction
- **Campbell & Thompson (2008)** - Predicting excess stock returns
- **Cochrane (2011)** - Discount rates
- **Engle et al. (2020)** - Hedging climate change news
- **Fama & French (1989)** - Business conditions and expected returns
- **Batten, Sowerbutts & Tanaka (2020)** - Climate change macroeconomic impact
- **Kling et al. (2025)** - Climate vulnerability and cost of debt
- **Torres (2024)** - Brazil's climate vulnerability analysis

---

## IMPORTANT NOTES

1. **Data Gaps:** Historical data has many NaN values; students should carefully select analysis period
2. **Time Period Flexibility:** Students can choose different period than 1991-2020 example
3. **No Out-of-Sample Requirement:** Focus on in-sample fit and diagnostics
4. **Extension of Annual Data:** ND-GAIN annual values must be extended to monthly/quarterly frequency consistently
5. **Outlier Treatment:** Consider winsorizing extreme values (1%-5%) for robustness
6. **Recession Definition:** Use NBER official dates (available via Wikipedia link provided)
7. **Extensions:** Consider interaction terms (e.g., vulnerability × recession) to explore differential effects

---

## FILE SUBMISSION REQUIREMENTS

- **Report File:** `[9DigitStudentNumber].pdf` or Word document
- **Code File:** `[9DigitStudentNumber]_code.ipynb` or `[9DigitStudentNumber]_code.py`
- **Deadline:** Moodle submission by Friday 12 December 2025, 14:00 GMT
- **Extensions:** Available through Bath's coursework extension process

---

## SUMMARY OF STATUS

This project is **fully specified but not yet started**. All three data files are present and contain:
- Clean financial/economic time series data (1871-present)
- Climate vulnerability index data (1995-2023)
- Detailed project specification document with clear requirements

**Ready to Begin:** Data collection, cleaning, integration, and analysis phase.

