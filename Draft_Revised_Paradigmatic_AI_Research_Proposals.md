# Draft Revisions: Paradigmatic AI Research Proposals

**To:** Principal Investigator
**From:** Roo, AI Planning Lead
**Date:** June 6, 2025
**Re:** Revisions to ML Proposals based on Feedback

This document contains the revised drafts for the three machine learning proposals, updated according to your feedback.

The core changes are:
1.  **Reframing for Adolescent Prediction:** All proposals are now framed within a two-stage model. **Stage 1 (This Grant)** focuses on using the adult OTOP dataset to discover risk factors, trajectories, and archetypes of established Opioid Use Disorder (OUD). **Stage 2 (Future Work)** will leverage these findings to develop a predictive model for opioid initiation in adolescents.
2.  **De-emphasis on Pain:** Pain-related variables have been removed from the primary analyses to broaden the scope and align with the observation that OUD is not always tied to pain.
3.  **Focus on Opioid Use & Relapse:** The analyses are now centered on substance use patterns, treatment history, socio-clinical factors, and relapse events.

---

## 1. Revised Proposal: Identifying Adolescent Risk Profiles by Clustering Adult OUD Trajectories

**(Formerly: Temporal Multi-View Clustering for Phenotype Discovery)**

### Summary
This project will apply temporal multi-view clustering to a rich longitudinal dataset of adults with Opioid Use Disorder (OUD) to identify distinct "OUD Archetypes." By analyzing trajectories across substance use, treatment history, and socio-clinical factors, we aim to uncover the dominant pathways that characterize established OUD. We hypothesize that these data-driven archetypes, discovered in an adult population, represent the long-term outcomes of risk profiles that begin in adolescence. The findings will form the empirical foundation for a future predictive screening tool designed to identify at-risk youth and guide early prevention strategies, shifting the paradigm from reactive treatment to proactive, targeted prevention.

### Variables & Views
The analysis will construct three temporal views, removing the previous focus on pain:

- **Substance Use View:** `intakeuds`, `udsresults` (and their time-varying follow-up counterparts, e.g., `udsresults_2mo`, `udsresults_3mo`) to model substance use patterns.
- **Treatment Trajectory View:** `medicationreceived`, `doseamount`, `recentdose`, `takehomephase`, `mat` (and follow-up equivalents) to form a view of the treatment journey.
- **Socio-Clinical View:** `intakedate`, `dob` (to calculate age at intake), `gender`, `race`, `housingstatus`, `referral_source` to provide crucial context.

### Hypothesis
Temporal multi-view clustering of adult OUD data will reveal 3-5 clinically distinct patient trajectory archetypes. We hypothesize that these archetypes are significantly associated with differential treatment outcomes (e.g., retention, relapse) and that their defining characteristics can be translated into a risk-factor model for predicting opioid initiation in adolescents.

### Expected Outcomes
- **Primary Outcome:** A validated set of 3-5 empirically derived "OUD Archetypes" based on temporal patterns in the adult dataset.
- **Secondary Outcomes:**
    - A comprehensive report detailing the clinical, demographic, and substance use characteristics of each archetype.
    - Prototype "risk profiles" based on these archetypes, designed to inform the development of an adolescent screening tool.
    - A foundational methodology for linking adult treatment data to adolescent prevention strategies.

---

## 2. Revised Proposal: Inferring Causal Pathways to Severe OUD to Guide Adolescent Prevention

**(Formerly: Causal Treatment-Sequence Inference via Targeted Learning)**

### Summary
This project will leverage advanced causal inference methods to transform rich, longitudinal observational data from adults with OUD into a map of causal pathways. By moving beyond simple prediction, we will answer "what-if" questions to determine which early-stage factors are causally linked to long-term, severe OUD outcomes like treatment failure and chronic relapse. The goal is to identify critical intervention points that, if addressed early, could alter a trajectory away from severe OUD. These findings will provide an evidence-based framework for designing effective prevention strategies for adolescents, targeting the specific factors that initiate the causal chain of dependency.

### Hypothesis
Causal inference using targeted learning will reveal that specific, modifiable early-stage factors (e.g., initial polysubstance use, housing instability, specific referral sources) have a significant causal effect on long-term treatment outcomes in adults. We hypothesize that these identified causal levers are critical targets for adolescent prevention programs.

### Expected Outcomes
- Quantitative estimates of the causal effects of key early-stage variables on long-term outcomes like relapse and treatment retention.
- Identification of optimal intervention points that can be targeted in adolescent prevention programs.
- A prototype decision-support framework for clinicians and public health officials to understand the downstream consequences of early-risk factors.

---

## 3. Revised Proposal: Dynamic Survival Ensemble to Model Relapse as a Proxy for Initiation Risk

**(Formerly: Dynamic Survival Ensemble for Adaptive Pain-Addiction Trajectories)**

### Summary
This project will develop a dynamic survival ensemble model to continuously update individualized risk predictions for **relapse** in adults undergoing opioid treatment. By treating clinical and social factors as time-varying covariates, we can identify the most potent predictors of treatment failure. We posit that the factors driving relapse in a treatment-seeking adult population are powerful proxies for the factors that drive initial opioid use in adolescents. The resulting model will not only provide a tool for adaptive treatment in adults but will also generate a validated set of risk factors that can be directly translated into a predictive model for adolescent opioid initiation.

### Data Assumptions & Variables
- The analysis will focus on time-to-event data, where the "event" is the first documented relapse (e.g., via `udsresults`) or treatment dropout (`discharge_reason_*`).
- The model will exclude pain-related variables (`painfrequency`, `painduration`, `currentpainyes`) and instead focus on `intakeuds`, `doseamount`, `takehomephase`, `housingstatus`, and other demographic and clinical variables as time-varying predictors.

### Hypothesis
A dynamic, time-dependent survival ensemble will accurately predict relapse and treatment discontinuation in adults with OUD. We further hypothesize that the most significant predictors from this model (e.g., early polysubstance use, housing status changes) will form a robust feature set for a future model aimed at predicting opioid initiation in adolescents.

### Expected Outcomes
- A validated, dynamic survival model for predicting relapse risk in adults with OUD.
- A ranked list of the most significant predictors of relapse, providing an evidence-based feature set for future adolescent-focused research.
- A prototype dashboard for visualizing how risk evolves over time, demonstrating the model's utility for both adult treatment and adolescent prevention planning.