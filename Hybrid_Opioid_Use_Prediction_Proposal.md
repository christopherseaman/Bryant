# Carroll Award Proposal: A Hybrid Machine Learning Framework for Predicting Opioid Use

**Project Title:** An Early Warning System for Opioid Use Recurrence: A Hybrid Modeling Approach

---

## 1. Background and Rationale

Research in opioid use disorder (OUD) has traditionally focused on static, baseline risk factors. This approach, while informative, fails to capture the dynamic nature of treatment response and relapse risk. While complex machine learning (ML) models have been explored, their practical application is often limited by implementation challenges and a lack of interpretability, creating a gap between theoretical models and clinically actionable tools.

### A Paradigm Shift in Clinical Prediction

This proposal outlines a project to develop a proactive **early warning system**, shifting the clinical focus from reactive to proactive care. The objective is to build a **novel hybrid ensemble framework** using baseline and early-treatment data (first 1-3 months) to predict high-risk individuals for future opioid use or treatment dropout (at 6-12 months). The goal is to generate timely, accurate warnings that enable proactive clinical intervention.

---

## 2. Primary Research Question & Specific Aims

**Primary Research Question:** Can baseline patient characteristics and early treatment engagement data (from the first 1-3 months) be used to build an effective early warning system for long-term (6-12 months) opioid use recurrence and treatment dropout?

**Specific Aims:**

*   **Aim 1: Develop an Early Warning Model for Opioid Recurrence.** Build and validate competing models using baseline and 1-3 month data to predict opioid use (fentanyl/heroin) at the 6-month mark.
*   **Aim 2: Forecast Long-Term Treatment Retention.** Develop and compare models to predict which patients are at high risk of discontinuing treatment by 12 months.
*   **Aim 3: Identify Critical Windows for Intervention.** Use survival analysis to model the timing of treatment dropout to identify key risk periods and predictive factors.

---

## 3. Approach and Methodology

The methodological approach is a hybrid modeling framework designed to identify the most effective **early warning system** for three clinical prediction tasks.

### 3.1. Prediction Task Definitions

| Task # | Prediction Goal | Outcome Variable(s) | Key Predictor Variables (Features) |
| :--- | :--- | :--- | :--- |
| **1** | **Early ID of 6-Month Opioid Recurrence** | `udsresults_6mo` (Binary: Positive for Fentanyl/6-AM vs. Negative) | **Baseline:** `intakeuds`, Demographics. <br> **Early Treatment (1-3 mo):** `udsresults`, `udsresults_2mo`, `udsresults_3mo`. |
| **2** | **Early ID of 12-Month Dropout Risk** | `enrollmentstatus_12mo` (Binary: Enrolled vs. Not Enrolled) | **Baseline:** `intakeuds`, `medicationreceived`, Demographics (`age`*, `gender`, `race`, `housingstatus`). <br> **Early Treatment (1-3 mo):** `mat_*`, `takehomephase_*`, summary of `udsresults_*`. |
| **3** | **Predicting Time to Treatment Dropout** | Time from `intakedate` to `dischargedate_*`. Censored at 12 months. | **Baseline:** `intakeuds`, Demographics. <br> **Early Treatment (Time-Varying):** `takehomephase_*`, positive `udsresults_*`. |

*Note: All variables are drawn from the OTOP Pain Tracking Intake Data Dictionary (2024-02-26). The `age` variable will be calculated from `dob`.*

### 3.2. Hybrid Modeling Framework

The following models will be implemented for each relevant aim. This selection provides a balance between traditional, interpretable statistical models and more advanced, non-linear machine learning methods. The core of this "AI" approach is not simply applying complex algorithms, but using a methodologically rigorous process to find the *best* predictive tool for this specific clinical problem.

*   **Interpretable Baselines:**
    *   **Logistic Regression (Aims 1 & 2):** Establishes a strong, interpretable baseline, yielding odds ratios for each predictor.
    *   **Cox Proportional Hazards (Aim 3):** The standard for survival analysis, modeling the hazard of an event (dropout) over time.

*   **Non-Linear Machine Learning Models:**
    *   **Random Forest / Random Survival Forest (Aims 1, 2, 3):** An ensemble method robust to non-linear relationships and interactions. Feature importance scores will be used for interpretation.
    *   **XGBoost (Aims 1 & 2):** A high-performance gradient boosting algorithm. Model interpretability will be ensured through the use of SHAP (SHapley Additive exPlanations) analysis.

### 3.3. Evaluation

All models will be trained and evaluated using 10-fold cross-validation to ensure robustness and prevent overfitting.
*   **Classification (Aims 1 & 2):** Performance will be compared using Area Under the Receiver Operating Characteristic Curve (AUC-ROC), F1-score, and Brier score to assess discrimination and calibration.
*   **Survival (Aim 3):** Performance will be measured using the Concordance Index (C-index).

---

## 4. Innovation

The innovation of this proposal lies in its **novel hybrid ensemble approach** for managing complex, interdependent patient systems. Rather than merely predicting a discrete outcome, this framework provides a systems-level management tool that accounts for the dynamic nature of OUD treatment.

1.  **Novel Hybrid Ensemble Approach:** The primary technical contribution is the development of a hybrid framework that integrates interpretable statistical models (Logistic Regression, Cox Proportional Hazards) with advanced machine learning ensembles (Random Forest, XGBoost). This approach moves beyond a simple "model competition" to leverage the strengths of each method, creating a more robust and reliable predictive system for managing patient risk over time.
2.  **Systems-Level Management:** The project reframes the problem from discrete prediction to systems-level management. By identifying critical intervention windows and modeling patient trajectories, the framework provides a holistic view of patient risk. This enables a more strategic, preventative clinical approach focused on managing the entire patient system rather than reacting to isolated events.
3.  **Foundation for Clinical Decision Support:** This project will produce a validated, data-driven framework that serves as **Stage 1** in the development of a **Stage 2** clinical decision support tool. The findings will establish the predictive horizons and feature importance necessary for a tool that can be integrated directly into clinical workflows to support proactive care.

---

## 5. Feasibility and Mitigation

This project is highly feasible due to several factors:

*   **Data Availability:** The research plan is designed around an existing, structured, wide-format dataset (OTOP). It does not depend on unavailable data types like free-text notes.
*   **Sample Size:** ==**PI Callout:** Final sample size is pending confirmation, with an estimated feasible range of **N=200-400** patients. This estimate is based on several assumptions: 1) Typical OUD clinic enrollment rates and patient volume over a 12-24 month recruitment period. 2) Anticipated attrition rates of 20-30%, consistent with similar longitudinal OUD studies. 3) Sufficient statistical power for planned logistic regression and survival analyses. 4) Minimum sample size needed for robust 10-fold cross-validation of machine learning models. This must be confirmed before analysis begins.==
*   **Variable Confirmation:** All proposed outcome and predictor variables have been confirmed to exist in the OTOP data dictionary.
*   **Missing Data Handling:** Standard imputation techniques (e.g., Multiple Imputation by Chained Equations - MICE) will be used for missing predictor data. The selected tree-based models (Random Forest, XGBoost) are also inherently robust to missingness.
*   **Computational Requirements:** The proposed models are computationally efficient and can be executed on standard research computing environments.

---

## 6. Resources and Environment

*   **Personnel:** The project will be led by a Principal Investigator (PI) who will oversee data analysis and interpretation. A graduate research assistant will be responsible for data preparation and model execution.
*   **Timeline:**
    *   Months 1-2: Data acquisition, cleaning, and feature engineering.
    *   Months 3-6: Execution of Aim 1 & 2 model competitions.
    *   Months 7-9: Execution of Aim 3 survival analysis.
    *   Months 10-12: Synthesis of results, interpretation, and manuscript preparation.
*   **Computational Needs:** Analysis will be performed in R and/or Python on existing university high-performance computing resources. No specialized hardware is required.