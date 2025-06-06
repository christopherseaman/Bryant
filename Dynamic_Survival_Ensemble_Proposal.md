# Dynamic Survival Ensemble to Model Relapse as a Proxy for Initiation Risk

This project will develop a dynamic survival ensemble to predict relapse in adults with Opioid Use Disorder (OUD). The model will continuously update individualized risk landscapes over time to identify factors that predict treatment failure. We posit that the drivers of relapse in adults are proxies for the factors that drive initial opioid use in adolescents. The model will produce a validated set of risk factors for a future predictive model of adolescent opioid initiation.

**Strength:**

This proposal aligns with the Carroll Award’s mission by linking adult treatment outcomes and adolescent prevention. By analyzing relapse, we can inform preventative care. This project uses AI to translate data from adults with OUD into actionable insights for at-risk adolescents.

**Data Assumptions:**

- Requires longitudinal, time-stamped data on substance use, treatment interventions, and relapse/retention outcomes.
- Assumes accurate event timing, minimal informative censoring, and sufficient follow-up duration for survival analysis.
- Data must support time-varying covariates and right-censoring.
- Moderate-to-large sample size (N > 300) with adequate event rates.
- Survival analysis methods require careful handling of missingness and censoring.

**Data Sources:**

- OTOP Pain Tracking Intake and Follow-Up Data

**Variables from OTOP Pain Tracking Intake and Follow-Up Data:**

*Required:*
- `intakedate`, `dob`, `gender`, `race`, `housingstatus`
- `intakeuds`, `doseamount`, `recentdose`
- `takehomes`, `takehomephase`
- `enrollmentstatus`, `udsresults`
- `discharge_reason_1mo`, `discharge_reason_mo2`, `discharge_reason_3mo`, `discharge_reason_6mo`, `discharge_reason_12mo`

*Optional:*
- `referral_source`, `medicationreceived`, `housingother`, `staffinitials`, `episode_number`, `research_consent`

**Summary:**

We will develop and validate a dynamic survival ensemble model to predict relapse and treatment discontinuation in adults with OUD. The model will identify the most significant predictors of these events, providing a feature set for a future model to predict opioid initiation in adolescents.

**Hypothesis:**

A dynamic, time-dependent survival ensemble will accurately predict relapse and treatment discontinuation in adults with OUD. We further hypothesize that the most significant predictors from this model (e.g., early polysubstance use, housing status changes) will form a robust feature set for a future model aimed at predicting opioid initiation in adolescents.

**Data Required:**

- Intake and follow-up fields: demographics, intakeuds/udsresults, doseamount/recentdose, takehomephase, housingstatus, enrollmentstatus, discharge_reason, and all time-stamped intervention and outcome events.

**Plan:**

1. Data cleaning, harmonization, and alignment of longitudinal records.
2. Feature engineering for time-varying covariates and treatment/control inputs.
3. Development and training of gradient-boosted survival tree ensembles.
4. Validation against baseline models (e.g., Cox proportional hazards, static classifiers).
5. Cross-validation, calibration, and assessment of model robustness.
6. Development of a prototype dashboard for real-time risk visualization and clinical decision support.

### Methodology Details

- **Modeling Approach:** Use gradient-boosted survival trees (e.g., XGBoost, LightGBM with survival extensions) to model time-to-event outcomes with time-varying covariates.
- **Dynamic Inputs:** Encode treatment actions (medication changes, take-home status, etc.) as control inputs that can change over time, rather than as static baseline covariates.
- **Baselines:** Compare performance to Cox proportional hazards models and static risk classifiers.
- **Evaluation Metrics:** Concordance index (C-index), time-dependent AUC, Brier score, calibration plots, and clinical utility metrics.
- **Handling Missingness:** Employ multiple imputation and robust survival analysis techniques to address missing or censored data.
- **Visualization:** Develop interactive risk landscape visualizations to support real-time clinical interpretation.
- **Software:** Python (scikit-survival, XGBoost/LightGBM, pandas), R (for validation), and dashboard frameworks (e.g., Dash, Streamlit).

### Expected Outcomes

- A validated, dynamic survival model for predicting relapse risk in adults with OUD.
- A ranked list of the most significant predictors of relapse, providing an evidence-based feature set for future adolescent-focused research.
- A prototype dashboard for visualizing how risk evolves over time, demonstrating the model's utility for both adult treatment and adolescent prevention planning.
- Foundation for prospective clinical validation and broader translational applications.

### Implementation Timeline

- **Months 1–3:** Data acquisition, cleaning, and harmonization.
- **Months 4–6:** Feature engineering and exploratory analysis.
- **Months 7–12:** Model development, training, and baseline comparisons.
- **Months 13–15:** Validation, calibration, and robustness checks.
- **Months 16–18:** Dashboard development and user testing.
- **Months 19–24:** Manuscript preparation, dissemination, and planning for prospective validation.

### Resources Required

- **Personnel:** Data scientist(s), clinician(s), statistician(s), software engineer for dashboard development.
- **Computational:** Access to secure servers with GPU support for model training and dashboard hosting.
- **Administrative:** IRB approval, data governance, and privacy protocols.
- **Other:** Stakeholder engagement for dashboard design and clinical integration.