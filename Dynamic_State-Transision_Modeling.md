# Dynamic State-Transition Modeling of Opioid Use Disorder for Predictive Risk Stratification

**A Proposal for the Carroll Award for Innovation**

## 1. Executive Summary

This research will develop and validate a dynamic state-transition model for Opioid Use Disorder (OUD) to enable predictive risk stratification. This framework will model patient journeys as a series of state transitions, moving beyond static archetypes. Using Hidden Markov Models (HMMs) and Gated Recurrent Units (GRUs), we will analyze sparse, longitudinal electronic health record (EHR) data from the OTOP program to identify latent phenotypes of treatment response, engagement, and relapse.

The core technical innovations are:
1.  **Dynamic State-Transition Modeling**: We will use models that learn the probabilistic pathways of patient progression to capture the interdependent nature of OUD.
2.  **Clustering on AI-Derived Features**: We will cluster model outputs (e.g., HMM transition matrices) to generate a robust and clinically relevant taxonomy of patient trajectories.

This research addresses the Carroll Award's call for work on "complex, interdependent systems" by creating a tool to calculate the real-time probability of outcomes like treatment dropout and relapse. The goal is to develop an early-warning system that provides clinicians with data-driven insights for proactive, personalized interventions.

## 2. Alignment with the Carroll Award for Innovation

This research aligns with the Carroll Award's focus on innovative approaches to complex health problems.

*   **Addresses a Complex, Interdependent System**: OUD is a dynamic condition influenced by behavioral, clinical, and social factors. Our state-transition models will capture this complexity by treating the patient journey as an evolving process.
*   **Novel Methodology**: This work introduces a new method for patient stratification. Traditional clustering of cross-sectional data produces static "types" that do not capture the volatility of OUD. Our approach will replace this with a dynamic model that provides probabilistic predictions, moving from description to prediction.
*   **Predictive, Systems-Level Impact**: The research is focused on predicting patient behavior. By modeling the patient system over time, we will generate predictions regarding treatment adherence, dropout risk, and relapse probability.

## 3. Research Plan & Methodology

The research plan consists of two stages: first, discovering dynamic phenotypes in an adult population, and second, laying the groundwork for applying these insights to adolescent risk prediction.

### Stage 1: Dynamic Phenotype Discovery in the Adult OTOP Cohort

The core of the work is the application of sequence modeling to longitudinal patient data.

**A. Core Methodology: Hidden Markov Models (HMMs)**

Hidden Markov Models (HMMs) are the primary tool for this task. They are designed to model systems that transition between unobserved ("hidden") states over time, based on a sequence of observations.

*   **Observed Variables**: `udsresults_*` (Urine Drug Screen results), `enrollmentstatus_*` (e.g., enrolled, discharged), `mat_*` (Medication-Assisted Treatment status), `takehomephase_*`.
*   **Hidden States**: The model will learn a set of latent "dynamic phenotypes," representing states such as 'Stable Engagement,' 'High-Risk Fluctuation,' 'Pre-Dropout,' or 'Successful Tapering.'
*   **Key Advantage**: HMMs are robust to the sparse and irregularly sampled data characteristic of EHRs. They inherently handle missing observations and attrition, which are treated as signals to be modeled.

**B. Advanced Clustering of AI-Derived Features**

A key technical component is a two-step clustering process:
1.  An HMM will be trained for each patient, yielding a unique **state-transition probability matrix**. This matrix is a learned representation of the patient's individual trajectory dynamics.
2.  We will then perform clustering (e.g., using hierarchical clustering) on these *matrices*. This groups patients based on their behavioral dynamics, a more direct approach than clustering on surface-level variables.

**C. Alternative Model: Gated Recurrent Units (GRUs)**

As a secondary approach, we will use Gated Recurrent Units (GRUs), a type of recurrent neural network. GRUs can capture more complex, non-linear dependencies in the data. We will extract patient-level embeddings from the final hidden state of the GRU and cluster these embeddings. This provides a deep learning alternative to validate and potentially enhance the findings from the HMMs.

### Stage 2: Application to Adolescent Risk Prediction (Future Work)

The dynamic phenotypes and transition probabilities discovered in Stage 1 will inform future work on adolescent OUD. The adult-derived models will serve as a prior for developing a predictive engine for early-onset OUD.

## 4. OTOP Data Integration & Risk Mitigation

**A. Primary Data Focus**

The analysis will focus on variables that track treatment progression and substance use to provide a clear signal for our dynamic models:
*   `udsresults_*`
*   `enrollmentstatus_*`
*   `mat_*`
*   `takehomephase_*`

Pain-related variables will be considered secondary modulators to maintain focus on the core dynamics of treatment engagement and relapse.

**B. Risk Assessment and Mitigation Plan**

Challenges of working with clinical data will be addressed with proactive mitigation strategies.

*   **Risk 1: Data Completeness & Sparsity**: Patient data may be sparse with gaps between encounters.
    *   **Mitigation**: The chosen methodology is a core strength. HMMs and GRUs are designed to handle sparse, irregular time-series data. Data attrition will be treated as a signal of disengagement. We will quantify data completeness and perform sensitivity analyses to ensure model robustness.

*   **Risk 2: Model Feasibility & Interpretability**: The learned hidden states may not be clinically interpretable or models may fail to converge.
    *   **Mitigation**: The project will start with simple HMMs (3-5 states) and incrementally increase complexity. State interpretation will be a collaborative effort with clinical experts. The GRU models will serve as a benchmark; if they outperform HMMs, we will use model-agnostic interpretation techniques (e.g., SHAP) to understand their predictions.

## 5. Predictive Outcomes & Clinical Utility

The research will generate the following predictive outcomes:

*   **Primary Predictive Outcomes**:
    1.  **Next-State Probability**: For any patient, the model will calculate the probability of their state at the next timepoint (e.g., 75% chance of remaining 'Enrolled-Stable,' 20% chance of transitioning to 'Enrolled-High-Risk').
    2.  **Relapse/Dropout Risk Score**: A time-varying score will represent the immediate risk of a negative outcome.

*   **Secondary Outcomes**:
    *   **Trajectory Mapping**: The work will visualize and quantify the most common pathways to different treatment outcomes.

*   **Clinical Utility**: The model will function as a **clinical decision support tool**—an early warning system that flags patients whose trajectory is deviating towards high-risk states, allowing for proactive intervention.

## 6. Timeline & Resources

*   **Months 1-3**: Data acquisition, preprocessing, and finalization of the core variable set.
*   **Months 4-8**: HMM and GRU model development, training, and validation. Iterative clustering of model outputs.
*   **Months 9-12**: Clinical interpretation of dynamic phenotypes, development of the predictive risk scoring system, and manuscript preparation.

Resources required are primarily computational (GPU access for GRU models) and personnel with expertise in machine learning and clinical informatics.

## 7. Conclusion

This research proposes a shift from static, descriptive analytics to dynamic, predictive modeling. By representing OUD as a system of state transitions, this work will characterize patient journeys and create a predictive tool to support clinical decision-making. The research is technically focused and aligned with the mission of the Carroll Award for Innovation.