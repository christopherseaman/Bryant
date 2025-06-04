# Paradigmatic AI Research Proposals for Carroll Award

## Multi-Modal Temporal Modeling  

Develop an integrated time-series framework that jointly models pain, substance use, housing status, and treatment retention across six follow-up points using a combination of joint T-LSTM and mixed-effects models. The analysis assumes that the dataset contains multiple visits and follow-up timepoints per patient, with structured longitudinal data aligning these repeated measures. By leveraging interdependent clinical and behavioral streams, it aims for at least a 15% performance gain over single-domain baselines and plans to deliver a prototype dashboard for clinical decision support within 3–5 years.

• Strength: Very Strong
Directly addresses Carroll Award criteria by shifting from discrete outcome prediction to integrated, multi-domain temporal system modeling.

- Simultaneously models pain, substance use, housing, and treatment retention as interdependent time-series, rather than isolated variables.
- Employs joint T-LSTM and mixed-effects models to integrate data across multiple clinical domains and timepoints.
- Lacks explicit integration of genetic/proteomic or socioeconomic data; focus remains on clinical and behavioral scales.
- High-risk, high-reward approach with potential for transformative impact on multi-domain clinical management within 3-5 years.

**Data Sources:**

- OTOP Pain Tracking Intake and Follow-Up Data

**Variables from OTOP Pain Tracking Intake and Follow-Up Data:**

- Required: `intakedate`, `dob`, `gender`, `race`, `housingstatus`, `painfrequency`, `painduration`, `currentpainyes`, `intakeuds`, `doseamount`, `recentdose`, `takehomes`, `takehomephase`, `enrollmentstatus`, `udsresults`, `discharge_reason_1mo`, `discharge_reason_mo2`, `discharge_reason_3mo`, `discharge_reason_6mo`, `discharge_reason_12mo`
- Optional: `referral_source`, `medicationreceived`, `housingother`, `staffinitials`, `episode_number`, `research_consent`

**Summary**: Joint T-LSTM and mixed-effects modeling of intake & 1/2/3/6/12-month streams to predict relapse and retention.  

**Hypothesis**: Integrating all modalities yields ≥15% boost over single-domain models.  

**Data Required**: Intake & follow-up fields (demographics, painfrequency, painduration, currentpainyes, intakeuds/udsresults, doseamount/recentdose, takehomephase, housingstatus, enrollmentstatus, discharge_reason).

**Data Assumptions**: The dataset includes multiple visits and follow-up timepoints per patient. The `currentpainyes` field is expected to contain actual free-text pain descriptions, not just simple "yes" responses.

**Plan**: (1) Clean & align time-series; (2) Train & validate models vs baselines; (3) Cross-validate & calibrate; (4) Prototype dashboard.

### Methodology Details

- Baseline models for comparison (random forest, logistic regression)
- Evaluation metrics (AUC, calibration curves, silhouette scores for clustering)
- Cross-validation strategy (k-fold, temporal splits)
- Hyperparameter tuning approach

### Expected Outcomes

- Concrete success criteria (target AUC thresholds, effect sizes)
- Statistical power calculations
- Clinical validation plans (prospective cohort evaluation)

### Implementation Timeline

- Phase 1: Data preparation and cleaning (Months 1-3)
- Phase 2: Model development and validation (Months 4-9)
- Phase 3: Clinical testing and dashboard development (Months 10-12)

### Resources Required

- Personnel needs (data engineers, clinicians, statisticians)
- IRB approval and ethical considerations
- Data governance and privacy protocols

## NLP Pain Phenotyping

Apply transformer-based embeddings (e.g., BioBERT/ClinicalBERT) and unsupervised clustering to free-text intake pain descriptions (`currentpainyes`) to uncover novel patient phenotypes linked to treatment response. Stratify patients by risk profiles and guide phenotype-specific interventions, targeting near-term translational impact in patient stratification.

• Strength: Very Strong
Strongly meets Carroll Award criteria by leveraging AI to extract complex, emergent phenotypes from unstructured clinical text, moving beyond discrete variable modeling.

- Applies transformer-based embeddings and clustering to free-text pain descriptions, enabling discovery of novel patient subgroups.
- Moves toward managing complex, interdependent systems by linking text-derived phenotypes to clinical trajectories and outcomes.
- Does not integrate data across biological or socioeconomic scales; focus is on clinical and behavioral text data.
- High-risk, disruptive approach with potential for near-term transformative change in patient stratification and intervention.

• Data Assumptions: Relies solely on `currentpainyes`, which is assumed to contain substantial free-text pain descriptions rather than simple "yes"/"no" responses; no external lexicons or annotations.

**Summary**: Apply transformer embeddings and clustering to intake pain descriptions to derive phenotypes linked to clinical trajectories.  

**Hypothesis**: Text-derived phenotypes stratify patients by treatment response and risk profiles.  

**Data Required**: Free-text `currentpainyes` field at intake.  

**Plan**: (1) Clean & embed text; (2) Cluster phenotypes; (3) Associate clusters with outcomes; (4) Propose phenotype-specific interventions.
