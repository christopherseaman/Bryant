# Identifying Adolescent Risk Profiles by Clustering Adult OUD Trajectories

This proposal outlines a method to identify risk profiles for adolescent opioid initiation by studying the trajectories of adults with established Opioid Use Disorder (OUD). Using temporal multi-view clustering across substance use, treatment, and socio-clinical data, this project will identify "OUD Archetypes"—distinct pathways characterizing long-term dependency. We hypothesize these archetypes represent the adult manifestation of risk profiles originating in adolescence. The project's goal is to use insights from adult data to inform a future screening tool for at-risk youth.

---

**Strength:**

This project aligns with the Carroll Award’s focus on new paradigms by using adult OUD data to inform adolescent prevention strategies. It proposes that analyzing adult trajectories can identify risk factors relevant to youth. By using AI to discover "OUD Archetypes" from longitudinal data, this work will provide an empirical foundation for future screening tools, linking adult treatment data to adolescent public health strategy.

- **Paradigmatic Shift:** Replaces one-size-fits-all guidelines with empirically derived, data-driven trajectory phenotypes, enabling a move from reactive to proactive care.
- **Systems-Based Approach:** Integrates pain, treatment, and UDS data as interdependent temporal streams, modeling the complex interplay of factors influencing patient outcomes.
- **Personalized Medicine:** Enables personalized care pathways and risk stratification based on a patient's specific trajectory phenotype.
- **Direct Alignment:** Directly aligns with the Carroll Award’s focus on managing complex, interdependent systems and applying AI to drive transformative change in healthcare.

---

**Data Assumptions:**

- Multi-modal, longitudinal data with synchronized time points across substance use, treatment, and socio-clinical views are available.
- Sufficient within- and between-patient variability exists to support the discovery of meaningful clusters.
- Data collection protocols are consistent, and batch effects are minimal.
- A moderate sample size (N > 200) with multiple repeated measures per patient is available.
- Data completeness and dimensionality are sufficient for robust clustering and clinical interpretability.

---

**Data Sources:**

- OTOP Pain Tracking Intake and Follow-Up Data

---

**Variables from OTOP Pain Tracking Intake and Follow-Up Data:**

- **Substance Use View:** `intakeuds`, `udsresults` (and their time-varying follow-up counterparts, e.g., `udsresults_2mo`, `udsresults_3mo`, etc.) will create a view of substance use patterns.
- **Treatment Trajectory View:** `medicationreceived`, `doseamount`, `recentdose`, `takehomephase`, `mat` (and follow-up equivalents) will form a view of the treatment journey.
- **Socio-Clinical View:** `intakedate`, `dob` (to calculate age at intake), `gender`, `race`, `housingstatus`, `referral_source` will provide crucial contextual data.
- **Outcomes:** `enrollmentstatus`, `discharge_reason_1mo`, `discharge_reason_mo2`, `discharge_reason_3mo`, `discharge_reason_6mo`, `discharge_reason_12mo` will be used for archetype validation.

---

**Summary:**

This project will apply temporal multi-view clustering to a longitudinal dataset of adults with Opioid Use Disorder (OUD) to identify distinct "OUD Archetypes." By analyzing trajectories across substance use, treatment history, and socio-clinical factors, we will identify pathways that characterize established OUD. The findings will form the empirical basis for a future screening tool designed to identify at-risk youth.

---

**Hypothesis:**

Temporal multi-view clustering of adult OUD data will reveal 3-5 clinically distinct patient trajectory archetypes. We hypothesize that these archetypes are significantly associated with differential treatment outcomes (e.g., retention, relapse) and that their defining characteristics can be translated into a risk-factor model for predicting opioid initiation in adolescents.

---

**Data Required:**

- Longitudinal intake and follow-up data for substance use, treatment, and socio-clinical variables, synchronized at common time points (e.g., intake, 1, 2, 3, 6, 12 months).
- Demographic and contextual variables for covariate adjustment and phenotype interpretation.
- A sufficient sample size (N > 200) with at least 3-4 repeated measures per patient to robustly model trajectories.

---

**Plan:**

1.  **Data Preprocessing & View Construction:** Clean and align longitudinal data streams for the substance use, treatment, and socio-clinical views at synchronized time points (intake, 1, 2, 3, 6, 12 months). Handle missing data using appropriate imputation techniques (e.g., multiple imputation).
2.  **Temporal Feature Engineering:** For each view, extract and summarize temporal features that capture the dynamics of each patient's trajectory. This will include calculating slopes, volatility, time-to-change, and state transition frequencies.
3.  **Multi-View Clustering:** Apply and compare late fusion (e.g., consensus clustering on single-view results) and joint multi-view clustering algorithms (e.g., multi-view spectral clustering, co-regularized k-means, or tensor factorization) to identify patient trajectory phenotypes.
4.  **Phenotype Validation & Interpretation:** Assess cluster stability using resampling methods. Evaluate clinical interpretability by examining the defining characteristics of each cluster. Statistically test the association of phenotypes with key outcomes (e.g., treatment retention via survival analysis, relapse rates).
5.  **Clinical Translation & Dissemination:** Develop phenotype-based risk profiles and create visualizations to communicate findings. Explore the development of a prototype dashboard for integration into clinical decision support workflows.

---

### Methodology Details

- **Clustering Algorithms:** We will start with a late-fusion approach by clustering each view separately (e.g., using k-means on temporal features) and then combining the cluster assignments. We will then move to more sophisticated joint clustering methods like Multi-View Spectral Clustering, which can capture inter-view dependencies more effectively.
- **Temporal Feature Engineering:** We will compute summary statistics (mean, slope, variance) and use methods like Dynamic Time Warping (DTW) to create patient similarity matrices as input for clustering algorithms.
- **Validation Metrics:** Internal validation will use silhouette scores and the Calinski-Harabasz index. Stability will be assessed with the Jaccard index across bootstrap samples. External validation will involve assessing the association between clusters and clinical outcomes using chi-squared tests, ANOVA, and Cox proportional-hazards models.
- **Cross-Validation:** A k-fold cross-validation strategy will be used to tune hyperparameters of the clustering algorithms and assess the generalizability of the phenotype structure.
- **Interpretability:** We will work closely with clinical experts to review the defining features of each phenotype to ensure they are clinically meaningful and actionable.

---

### Expected Outcomes

- **Primary Outcome:** A validated set of 3-5 empirically derived "OUD Archetypes" based on temporal patterns in the adult dataset.
- **Secondary Outcomes:**
    - A comprehensive report detailing the clinical, demographic, and substance use characteristics of each archetype.
    - Prototype "risk profiles" based on these archetypes, designed to inform the development of an adolescent screening tool.
    - A foundational methodology for linking adult treatment data to adolescent prevention strategies.
    - At least two peer-reviewed publications and presentations at national conferences.

---

### Implementation Timeline

- **Phase 1 (Months 1–4):** Data acquisition, preparation, cleaning, and alignment. IRB protocol finalization.
- **Phase 2 (Months 5–10):** Temporal feature engineering and exploratory single-view clustering analysis.
- **Phase 3 (Months 11–16):** Application and evaluation of advanced multi-view clustering algorithms. Cluster validation and outcome association analysis.
- **Phase 4 (Months 17–20):** In-depth clinical interpretation of phenotypes with clinical expert panel. Development of risk profiles.
- **Phase 5 (Months 21–24):** Manuscript preparation, dissemination of findings, and development of a prototype dashboard for clinical translation.

---

### Resources Required

- **Personnel:** Principal Investigator (0.5 FTE), Data Scientist/Statistician (1.0 FTE), Clinical Expert Panel (consultant basis), Project Coordinator (0.25 FTE).
- **Computational Resources:** Access to a secure, high-performance computing environment with sufficient memory (>64GB RAM) and processing power for iterative clustering and validation on longitudinal data.
- **Ethics & Governance:** IRB approval for secondary data analysis. Adherence to all data governance and privacy protocols established by the institution.
- **Clinical Engagement:** Dedicated time from clinicians with expertise in pain-addiction to participate in phenotype interpretation, validation, and translation workshops.