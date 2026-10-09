# Gamma evaluation criteria and findings (draft)

## Scope and source

Survey files: RY_24.csv, RY25_PreMay10.csv, RY25_PostMay10.csv.
Instances: aggregated response counts for configured four-option questions.
Matching P matrices: exported from the project's P.RData.

**IMPORTANT MODEL LIMITATION:** The original R script samples latent student types.
This provisional Python pipeline instead uses observed response categories as
latent types when simulating retests. These are not proven equivalent. Results
are *exploratory survey-derived proxy diagnostics*, NOT validated evidence of
"genuinely poor Gamma fit in real instances" until the team approves the
conditional simulation model or supplies a faithful real-instance simulator.

## Evaluation protocol

- 10,000 simulated scaled d_hat draws per instance.
- 70% for Gamma MLE (shape/rate), 30% held out for evaluation.
- KS statistic: maximum empirical vs fitted CDF discrepancy on holdout.
- q95 relative error: |fitted q95 - empirical q95| / empirical q95.
- Tail error: absolute fitted vs empirical survival probability at empirical q95.
- Exact zeros, invalid draws, singular covariance: flagged for review, not discarded.
- Failure thresholds: **to be agreed by team**, not asserted automatically.

## Results

Instances attempted: 12. Successfully evaluated: 12.
See `gamma_failure_analysis.csv` and `worst_10_gamma_cases.csv`.
See `gamma_fit_plots/` for plots of the three largest q95 errors.

## Findings (fill in after inspection)

- Which questions/group comparisons have the largest errors?
- Are errors associated with group size imbalance, rare categories, or P structure?
- Which cases remain poor under repeated seeds or more trials?
- Are the simulation assumptions faithful to the original Gemfinder method?

## Notes

KS is descriptive; ordinary KS p-values are not calibrated after fitting parameters.
Group comparisons are not assumed independent if survey respondent overlap exists.
