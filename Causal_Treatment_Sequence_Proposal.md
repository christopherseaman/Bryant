# Inferring Causal Pathways to Severe OUD to Guide Adolescent Prevention

This project will use causal inference methods to analyze longitudinal data from adults with Opioid Use Disorder (OUD) to identify causal pathways. We will determine which early-stage factors are causally linked to long-term OUD outcomes, such as treatment failure and relapse. The goal is to identify intervention points to inform the design of prevention strategies for adolescents.

---

**Strength:**

This project aligns with the Carroll Award’s mission by shifting from optimizing treatment for existing patients to understanding the causal origins of severe OUD to inform prevention. The project uses AI to move beyond prediction and toward causal understanding, enabling the design of targeted prevention strategies. It uses observational data to create a roadmap for public health intervention.

---

**Data Assumptions:**

- Requires rich, longitudinal data with detailed, time-stamped treatment sequences, covariates, and outcomes.
- Assumes sequential ignorability (no unmeasured confounding at each decision point), positivity (all treatment options are possible for all covariate strata), and correct model specification for causal inference.
- Data must support time-varying exposures and outcomes, with moderate robustness to missingness if missing at random.
- Large, diverse sample size (N > 500) with sufficient variation in treatment trajectories.

---

**Data Sources:**

- OTOP Pain Tracking Intake and Follow-Up Data

---

**Variables from OTOP Pain Tracking Intake and Follow-Up Data:**

- **Treatment Sequence Variables:**  
  - `medicationreceived`, `doseamount`, `recentdose`, `takehomes`, `takehomephase`, `mat`, `mat_2mo`, `mat_3mo`, `mat_6mo`, `mat_12mo`
- **Outcome Variables:**  
  - `enrollmentstatus`, `discharge_reason_1mo`, `discharge_reason_mo2`, `discharge_reason_3mo`, `discharge_reason_6mo`, `discharge_reason_12mo`, `udsresults`, `udsresults_2mo`, `udsresults_3mo`, `udsresults_6mo`, `udsresults_12mo`
- **Confounders/Covariates:**  
  - `intakedate`, `dob`, `gender`, `race`, `housingstatus`, `intakeuds`, `referral_source`, `episode_number`

---

**Summary:**

This project will implement a targeted learning pipeline to estimate the causal effects of key early-stage factors on long-term outcomes in adults with OUD. By integrating IPTW and TMLE with SuperLearner ensembles, the approach will identify intervention points that can be targeted in future adolescent prevention programs.

---

**Hypothesis:**

Causal inference using targeted learning will reveal that specific, modifiable early-stage factors have a significant causal effect on long-term treatment outcomes in adults. We hypothesize that these identified causal levers are critical targets for adolescent prevention programs.

---

**Data Required:**

- Longitudinal intake and follow-up data capturing treatment exposures, outcomes, and confounders (excluding pain variables) as listed above.
- Sufficient sample size (N > 500) with diverse treatment trajectories and follow-up points (1, 2, 3, 6, 12 months).

---

**Plan:**

1. **Data Preparation:**  
   - Clean and align longitudinal data; structure for time-varying exposures, covariates, and outcomes.
2. **Variable Selection & Encoding:**  
   - Identify and encode treatment, outcome, and confounder variables for sequential modeling.
3. **Causal Model Specification:**  
   - Define dynamic treatment regimes and specify models for treatment assignment and outcome processes.
4. **Estimation:**  
   - Apply IPTW and TMLE with SuperLearner ensembles to estimate causal effects of alternative treatment sequences.
5. **Validation & Sensitivity Analysis:**  
   - Perform cross-validation, assess model robustness, and conduct sensitivity analyses for unmeasured confounding and positivity violations.
6. **Interpretation & Visualization:**  
   - Generate individualized treatment recommendations and visualize causal effects for clinical decision support.
7. **Prototype Tool Development:**  
   - Develop a prototype dashboard or tool for clinicians to explore "what-if" scenarios and optimal treatment paths.

---

### Methodology Details

- **Causal Estimators:**  
  - Inverse Probability of Treatment Weighting (IPTW) and Targeted Maximum Likelihood Estimation (TMLE) for time-varying exposures.
- **SuperLearner Ensemble:**  
  - Combines multiple machine learning algorithms (e.g., random forests, gradient boosting, neural nets) for robust estimation of propensity scores and outcome regressions.
- **Dynamic Treatment Regimes:**  
  - Models sequences of treatment decisions over time, accounting for evolving patient characteristics and prior treatments.
- **Validation:**  
  - Cross-validation, temporal holdout, and sensitivity analyses for key assumptions (sequential ignorability, positivity).
- **Interpretability:**  
  - Visualization of estimated causal effects and individualized recommendations for clinical translation.

---

### Expected Outcomes

- Quantitative estimates of the causal effects of key early-stage variables on long-term outcomes like relapse and treatment retention.
- Identification of optimal intervention points that can be targeted in adolescent prevention programs.
- A prototype decision-support framework for clinicians and public health officials to understand the downstream consequences of early-risk factors.
- Publications and presentations demonstrating the feasibility and impact of using causal inference to inform prevention strategies.

---

### Implementation Timeline

- **Phase 1 (Months 1–3):** Data preparation, cleaning, and alignment.
- **Phase 2 (Months 4–8):** Model specification, variable encoding, and initial causal estimation.
- **Phase 3 (Months 9–15):** Validation, sensitivity analysis, and refinement of causal models.
- **Phase 4 (Months 16–20):** Development of prototype decision-support tool and visualization.
- **Phase 5 (Months 21–24):** Manuscript preparation, dissemination, and planning for clinical translation.

---

### Resources Required

- **Personnel:**  
  - Data scientist(s) with expertise in causal inference and machine learning  
  - Statistician/biostatistician  
  - Clinical collaborator(s) for domain expertise and tool validation  
  - Software engineer (for dashboard/tool development)
- **Computational Resources:**  
  - Access to secure servers with sufficient memory/CPU for ensemble modeling  
  - Statistical software (R, Python, SuperLearner, TMLE packages)
- **Regulatory/Ethical:**  
  - IRB approval, data governance, and privacy protocols