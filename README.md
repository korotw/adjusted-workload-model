# adjusted-workload-model

Adjusted Workload Model: Technical Specifications
Supplemental material for "Beyond Unit Hour Utilization: Toward a Fatigue-Informed Workload Measure for the Fire Service" — Korotkin, W. & Stephenson, A.

Data Source
Dataset: Tiered_Response_GCProject_Update10.csv
Period: September 14, 2024 to October 19, 2026 (182,776 raw records)
Scope: Filtered to 38 career-staffed operational units, resulting in 105,787 records. Units included ALS Transports, BLS Transports, ALS Engines, Trucks, and Rescues.

Exclusions: Designated flex units are excluded from workload calculations. Calls with negative dispatch-to-clear durations are removed as invalid data.

Structure Fire Criteria
Incident description must equal "STRUCTURE FIRE" and all comments columns must contain "5D," the radio channel assigned to working structure fires. The multiplier applies to each unit and call. Units at the same fire may receive different multipliers based on time on scene.

CPR/Cardiac Arrest Criteria
Triggered when an ePCR has a primary impression of cardiac arrest, or when procedures include CPR, defibrillation, or mechanical chest compression. Once triggered, all responding units receive the multiplier. Age is parsed from free-text narrative; years, months, days, and minutes are all handled. Null values default to adults. Ambiguous entries are excluded.

Regression Interaction Terms
All 15 possible two-way combinations were evaluated. Forward stepwise selection was used with AIC and BIC comparisons to assess model fit and penalize unnecessary complexity. Retained interaction terms:
Volume × CPR
Severity Weighted Minutes × CPR
Burst × Volume
Nighttime × Structure Fire
Burst × Structure Fire
Volume × Structure Fire
Nighttime × CPR
Structure Fire × CPR
Volume × Severity Weighted Minutes
Validation Diagnostics

Residual normality was supported by Shapiro-Wilk and Jarque-Bera tests. Homoscedasticity was supported by the Breusch-Pagan test, indicating consistent variance across units. Variance Inflation Factor (VIF) analysis suggested generally acceptable separation among predictors, though nighttime and high-volume multipliers showed elevated collinearity consistent with overlapping workload dimensions. Cook's Distance identified several influential units with distinct workload profiles. This collinearity reflects real-world coupling of workload conditions where high-volume shifts frequently coincide with increased nighttime activity. Other predictors demonstrated low VIF values. Multicollinearity does not compromise interpretation of the findings.
Sensitivity Analysis

A sensitivity analysis assessed whether changes in multiplier magnitudes affected unit rankings. Across all tested scenarios, rankings remained highly stable (Spearman ρ ≥ 0.999). Minimal changes in top-ranked units confirmed that findings are robust and the model is not driven by specific parameter choices.

For questions contact: korotkinw@bouldercolorado.gov
