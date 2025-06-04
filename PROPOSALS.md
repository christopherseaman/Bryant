# Paradigmatic AI Research Proposals for Carroll Award

## Sketches

Rough ideas that could be a starting point for something:

1. Digital Twin–Driven Adaptive Treatment Orchestration

    - Creates patient-level digital twins using longitudinal pain, UDS, medication, and housing data
    - Employs reinforcement learning to optimize multi-domain interventions
    - Paradigmatic shift: From point predictions to closed-loop policy systems managing clinical and social variables simultaneously
    - **Data Assumptions:** Requires a validation dataset with comparable demographics, environment, and known outcomes for digital twin training and evaluation; assumes sufficient longitudinal data per patient.
  
2. Temporal Graph Neural Systems of Socio-Clinical Interdependencies

    - Models patients as dynamic graphs with visits, medications, UDS results, and housing as interconnected nodes
    - Uses temporal graph neural networks to discover system-level patterns predicting outcomes
    - Paradigmatic shift: From linear risk scores to graph-structured discovery of interacting subsystems
    - **Data Assumptions:** Assumes adequate patient volume and graph connectivity; requires longitudinal, multi-domain data and sufficient event density for meaningful temporal graph pattern discovery.

3. Counterfactual Causal Platform for Policy-Level Simulation

    - Builds structural causal models linking housing, medication adherence, UDS outcomes, and retention
    - Creates "what-if" simulators for policy makers to test resource allocation scenarios
    - Paradigmatic shift: From correlation-based predictions to causal policy simulation across socioeconomic and treatment domains
    - **Data Assumptions:** Requires data on policy variation and structural relationships; assumes minimal unmeasured confounding and that causal structure can be reasonably specified from available variables.

4. Hybrid Agent-Based & Generative Synthetic Cohort Engine

    - Combines variational autoencoders with agent-based modeling to simulate clinic ecosystems
    - Tests disruptive interventions (e.g., housing prioritization) at population scale
    - Paradigmatic shift: Integrates bottom-up patient simulation with macro-scale policy testing
    - **Data Assumptions:** Needs population-level parameters and individual-level data to calibrate agent behaviors; assumes agent actions and interactions can be meaningfully modeled and validated.

## Multi-Modal Temporal Modeling  

Develop an integrated time-series framework to explore joint modeling of pain, substance use, housing status, and treatment retention across six follow-up points using a combination of joint T-LSTM and mixed-effects models. By leveraging interdependent clinical and behavioral streams, this project will investigate whether multi-domain modeling can provide meaningful insights beyond single-domain baselines and will assess the feasibility of translational applications such as clinical decision support tools.

**Strength:**

Directly addresses Carroll Award criteria by shifting from discrete outcome prediction to integrated, multi-domain temporal system modeling.

- Simultaneously models pain, substance use, housing, and treatment retention as interdependent time-series, rather than isolated variables.
- Employs joint T-LSTM and mixed-effects models to integrate data across multiple clinical domains and timepoints.
- Lacks explicit integration of genetic/proteomic or socioeconomic data; focus remains on clinical and behavioral scales.
- High-risk, high-reward approach with potential for transformative impact on multi-domain clinical management within 3-5 years.

**Data Assumptions:**

- The dataset includes multiple visits and follow-up timepoints per patient, specifically at 1, 2, 3, 6, and 12-month periods.
- It is assumed that the `currentpainyes` field contains substantial free-text pain descriptions, not just simple "yes" responses.

**Data Sources:**

- OTOP Pain Tracking Intake and Follow-Up Data

**Variables from OTOP Pain Tracking Intake and Follow-Up Data:**

- Required: `intakedate`, `dob`, `gender`, `race`, `housingstatus`, `painfrequency`, `painduration`, `currentpainyes`, `intakeuds`, `doseamount`, `recentdose`, `takehomes`, `takehomephase`, `enrollmentstatus`, `udsresults`, `discharge_reason_1mo`, `discharge_reason_mo2`, `discharge_reason_3mo`, `discharge_reason_6mo`, `discharge_reason_12mo`
- Optional: `referral_source`, `medicationreceived`, `housingother`, `staffinitials`, `episode_number`, `research_consent`

**Summary**: Joint T-LSTM and mixed-effects modeling of intake & 1/2/3/6/12-month streams to investigate factors associated with relapse and retention.

**Hypothesis**: Integrating all modalities may yield improved performance over single-domain models; we will assess whether multi-modal integration provides measurable benefits.

**Data Required**: Intake & follow-up fields (demographics, painfrequency, painduration, currentpainyes, intakeuds/udsresults, doseamount/recentdose, takehomephase, housingstatus, enrollmentstatus, discharge_reason).

**Plan**: (1) Clean & align time-series; (2) Train & validate models vs baselines; (3) Cross-validate & calibrate; (4) Explore development of a prototype dashboard if results support further investigation.

### Methodology Details

- Baseline models for comparison (random forest, logistic regression)
- Evaluation metrics (AUC, calibration curves, silhouette scores for clustering)
- Cross-validation strategy (k-fold, temporal splits)
- Hyperparameter tuning approach

### Expected Outcomes

- Exploratory evaluation of model performance (AUC, effect sizes) relative to baselines
- Assessment of statistical power and limitations
- Consideration of potential clinical validation strategies (e.g., prospective cohort evaluation) if warranted by initial findings

### Implementation Timeline

- Phase 1: Data preparation and cleaning (anticipated initial phase)
- Phase 2: Model development and validation (subsequent phase, timing dependent on data readiness)
- Phase 3: Exploratory clinical testing and dashboard development (if supported by prior results; timing to be determined)

### Resources Required

- Personnel needs (data engineers, clinicians, statisticians)
- IRB approval and ethical considerations
- Data governance and privacy protocols

## NLP Pain Phenotyping

Apply transformer-based embeddings (e.g., BioBERT/ClinicalBERT) and unsupervised clustering to free-text intake pain descriptions (`currentpainyes`) to uncover novel patient phenotypes linked to treatment response. Stratify patients by risk profiles and guide phenotype-specific interventions, targeting near-term translational impact in patient stratification.

• Strength: Strongly meets Carroll Award criteria by leveraging AI to extract complex, emergent phenotypes from unstructured clinical text, moving beyond discrete variable modeling.

- Applies transformer-based embeddings and clustering to free-text pain descriptions, enabling discovery of novel patient subgroups.
- Moves toward managing complex, interdependent systems by linking text-derived phenotypes to clinical trajectories and outcomes.
- Does not integrate data across biological or socioeconomic scales; focus is on clinical and behavioral text data.
- High-risk, disruptive approach with potential for near-term transformative change in patient stratification and intervention.

**Data Assumptions:**

- Relies on `currentpainyes` containing substantial free-text pain descriptions rather than simple "yes"/"no" responses.

**Summary**: Apply transformer embeddings and clustering to intake pain descriptions to derive phenotypes linked to clinical trajectories.  

**Hypothesis**: Text-derived phenotypes stratify patients by treatment response and risk profiles.  

**Data Required**: Free-text `currentpainyes` field at intake.  

**Plan**: (1) Clean & embed text; (2) Cluster phenotypes; (3) Associate clusters with outcomes; (4) Propose phenotype-specific interventions.
