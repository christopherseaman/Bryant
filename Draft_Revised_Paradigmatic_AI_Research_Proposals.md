# Draft Revised Paradigmatic AI Research Proposals

Proposal A: Multi-Modal Temporal Trajectory Modeling  
• Summary: Jointly model demographics, pain profile, UDS, medication dose, housing, and retention across intake and 1/2/3/6/12 months using T-LSTM and mixed-effects models.  
• Strength: Minimal assumptions; leverages complete longitudinal structure.  
• Data Assumptions: Uses only OTOP time-series and intake fields.

Proposal B: Dynamic Causal Network Analysis  
• Summary: Learn time-varying Bayesian networks (PCMCI/PC) among pain, substance use, housing, and retention.  
• Strength: Reveals actionable feedback loops with no external data.  
• Data Assumptions: Only OTOP intake and follow-up panels.

Proposal C: Transfer Learning for Adolescent Risk Prediction  
• Summary: Pretrain sequence autoencoder on adult (≥25 yrs) longitudinal patterns, fine-tune on adolescent (<18 yrs) outcomes.  
• Strength: Strong signal transfer; only requires cohort age labels.  
• Data Assumptions: Uses age fields; no external data.

Proposal D: Causal Treatment Effect Estimation  
• Summary: Use marginal structural models and IPW to estimate causal effects of MAT dose and take-home trajectories on retention/UDS.  
• Strength: Direct clinical policy insights; causal inference within dataset.  
• Data Assumptions: Assumes dose/take-home measures available in follow-ups.

Proposal E: NLP Pain Phenotyping  
• Summary: Apply transformer embeddings and clustering to free-text `currentpainyes`, link to trajectories for phenotypic risk profiles.  
• Strength: Unlocks text insights; high innovation.  
• Data Assumptions: Relies on free-text field only.