# Climate Vulnerability and US Stock Market Returns

An empirical investigation examining whether climate vulnerability predicts US excess stock market returns.

## Research Question

Does climate vulnerability (ND-GAIN Vulnerability Score) significantly predict US excess stock market returns after controlling for valuation and credit risk factors?

## Data

- **Period**: January 1995 - December 2020 (312 monthly observations)
- **Sources**: ND-GAIN (climate vulnerability), Goyal-Welch dataset (financial variables)
- **Variables**:
  - Dependent: S&P 500 excess returns (market return minus risk-free rate)
  - Predictors: ND-GAIN Vulnerability Score, Dividend-Price Ratio (dp), Default Return Spread (dfr)

## Model

```
R_excess = β₀ + β₁(Vulnerability) + β₂(dp) + β₃(dfr) + ε
```

## Key Findings

| Variable | Coefficient | p-value | Significant? |
|----------|-------------|---------|--------------|
| Vulnerability | -1.1618 | 0.110 | No |
| Dividend-Price Ratio | -1.0713 | 0.329 | No |
| Default Return Spread | 1.1500 | <0.001 | Yes |

- **R² = 0.252** (model explains 25.2% of variance)
- Climate vulnerability does **not** significantly predict monthly US stock returns
- Default return spread is the dominant predictor
- Results robust to winsorization (1% and 5%)
- Structural breaks detected at March 2000 (dot-com) and September 2008 (financial crisis)

## Diagnostic Tests

- **Multicollinearity**: None detected (all VIF < 1.2)
- **Heteroskedasticity**: Present; corrected with HC3 robust standard errors
- **Autocorrelation**: None detected (Durbin-Watson = 2.09)
- **Normality**: Rejected, but CLT applies with n=312

## Conclusion

Climate vulnerability does not predict short-term US stock returns. Possible explanations include: efficient market pricing, low US vulnerability variation (0.307-0.317), annual data frequency limitations, or climate effects manifesting over longer horizons.

## References

- Goyal & Welch (2008) - Equity premium prediction
- Fama & French (1989) - Business conditions and expected returns
- Campbell & Shiller (1988) - Dividend-price ratio framework
