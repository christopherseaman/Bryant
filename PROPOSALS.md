# AI Research Proposals for Carroll Award

## Inspiration Sketches

Rough ideas that could be a starting point for something:

### AI

1. Digital Twin–Driven Adaptive Treatment Orchestration

    - Creates patient-level digital twins using longitudinal pain, UDS, medication, and housing data
    - Employs reinforcement learning to optimize multi-domain interventions
    - Paradigmatic shift: From point predictions to closed-loop policy systems managing clinical and social variables simultaneously
    - **Outcome Specification:** Optimizes treatment recommendations, predicts optimal intervention timing, and generates personalized dosing strategies for each patient.
    - **Feasibility Notes:**
        - Requires large, high-quality longitudinal datasets per patient (hundreds to thousands of patients with multi-year records).
        - Demands robust computational infrastructure for real-time simulation and policy optimization (GPU-enabled servers, scalable storage).
        - Implementation timeline: 12–24 months for full deployment, including model training and clinical integration.
        - Validation requires prospective simulation and retrospective outcome comparison; external validation on independent cohorts recommended.

2. Temporal Graph Neural Systems of Socio-Clinical Interdependencies

    - Models patients as dynamic graphs with visits, medications, UDS results, and housing as interconnected nodes
    - Uses temporal graph neural networks to discover system-level patterns predicting outcomes
    - Paradigmatic shift: From linear risk scores to graph-structured discovery of interacting subsystems
    - **Outcome Specification:** Discovers predictive subnetworks, enables risk stratification, and provides early warning systems for treatment failure or adverse events.
    - **Feasibility Notes:**
        - Needs sufficient patient volume and event density (ideally >1,000 patients, frequent events per patient).
        - Requires advanced graph analytics frameworks (e.g., PyTorch Geometric, DGL) and high-memory compute nodes.
        - Implementation timeline: 9–18 months, including graph construction and iterative model refinement.
        - Validation through cross-validation, temporal holdout, and subnetwork interpretability assessments.

3. Counterfactual Causal Platform for Policy-Level Simulation

    - Builds structural causal models linking housing, medication adherence, UDS outcomes, and retention
    - Creates "what-if" simulators for policy makers to test resource allocation scenarios
    - Paradigmatic shift: From correlation-based predictions to causal policy simulation across socioeconomic and treatment domains
    - **Outcome Specification:** Simulates policy impacts, generates resource allocation recommendations, and provides quantitative "what-if" scenario results for decision support.
    - **Feasibility Notes:**
        - Requires datasets with policy variation and well-specified structural relationships (hundreds of policy instances or natural experiments).
        - Needs causal inference toolkits (e.g., DoWhy, CausalNex) and moderate computational resources.
        - Implementation timeline: 6–12 months for initial platform, with ongoing refinement as new data/policies emerge.
        - Validation via back-testing on historical policy changes and sensitivity analyses.

4. Hybrid Agent-Based & Generative Synthetic Cohort Engine

    - Combines variational autoencoders with agent-based modeling to simulate clinic ecosystems
    - Tests disruptive interventions (e.g., housing prioritization) at population scale
    - Paradigmatic shift: Integrates bottom-up patient simulation with macro-scale policy testing
    - **Outcome Specification:** Estimates population-level intervention effects, validates synthetic cohorts against real-world data, and reveals emergent system behaviors under novel scenarios.
    - **Feasibility Notes:**
        - Needs both population-level parameters and granular individual-level data for agent calibration (hundreds to thousands of agents).
        - Requires agent-based simulation platforms (e.g., Mesa, AnyLogic) and generative modeling frameworks (e.g., TensorFlow, PyTorch).
        - High computational requirements for large-scale simulations; access to cloud or HPC resources recommended.
        - Implementation timeline: 12–24 months, including iterative calibration and scenario testing.
        - Validation through synthetic-real cohort comparison and scenario-based stress testing.

### ML

1. Dynamic Survival Ensemble for Adaptive Pain-Addiction Trajectories

    - Uses gradient-boosted survival trees with time-dependent risk scoring
    - Paradigm shift: From one-off binary predictions to continuously updated risk landscapes enabling real-time clinical intervention
    - Treats treatment as control inputs in a dynamic system rather than fixed covariates
    - **Data Assumptions:** Requires longitudinal, time-stamped data on pain scores, opioid use, treatment interventions, and outcomes; assumes accurate event timing, minimal informative censoring, and sufficient follow-up duration for survival analysis.
    - **Outcomes:** Predicts individualized time-to-event outcomes such as relapse, treatment discontinuation, or composite endpoints; enables dynamic risk stratification for real-time intervention.
    - **Feasibility Notes:** Needs moderate-to-large sample size (N > 300) with adequate event rates; data must support time-varying covariates and right-censoring; survival analysis methods require careful handling of missingness and censoring.

2. Causal Treatment-Sequence Inference via Targeted Learning

    - Combines IPTW and TMLE with SuperLearner ensembles for causal effect estimation
    - Paradigm shift: Transforms observational data into decision-support for "what-if" treatment sequence planning
    - Moves from "who will relapse?" to "what treatment path optimizes outcomes?"
    - **Data Assumptions:** Requires rich longitudinal data with detailed treatment sequences, covariates, and outcomes; assumes sequential ignorability (no unmeasured confounding at each decision point), positivity, and correct model specification for causal inference.
    - **Outcomes:** Estimates causal effects of alternative treatment sequences on relapse, retention, or pain improvement; supports individualized treatment path recommendations.
    - **Feasibility Notes:** Needs large sample size (N > 500) with diverse treatment trajectories; data must be structured for time-varying exposures and outcomes; robust to moderate missingness if missing at random.

3. Temporal Multi-View Clustering for Phenotype Discovery

    - Multi-view clustering across pain, treatment, and UDS pattern dimensions over time
    - Paradigm shift: Replaces one-size-fits-all guidelines with empirically derived trajectory phenotypes
    - Recognizes pain-addiction as complex multi-component system
    - **Data Assumptions:** Requires multi-modal, longitudinal data with synchronized time points across views (pain, treatment, UDS); assumes sufficient within- and between-patient variability and minimal batch effects.
    - **Outcomes:** Identifies distinct patient trajectory phenotypes based on temporal patterns; clusters are validated for clinical relevance and interpretability.
    - **Feasibility Notes:** Needs moderate sample size (N > 200) with repeated measures per patient; clustering validity depends on data completeness and dimensionality; interpretability requires linkage to clinical outcomes and expert review.

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

**Plan:**

1. Clean & align time-series
2. Train & validate models vs baselines
3. Cross-validate & calibrate
4. Explore development of a prototype dashboard if results support further investigation.

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

**Plan**:

1. Clean & embed text
2. Cluster phenotypes
3. Associate clusters with outcomes
4. Propose phenotype-specific interventions.
