# Paradigmatic AI Research Proposals for Carroll Award

## Proposal 1: Multi-Modal Temporal Modeling  

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
**Plan**: (1) Clean & align time-series; (2) Train & validate models vs baselines; (3) Cross-validate & calibrate; (4) Prototype dashboard.

## Proposal 2: Dynamic Causal Network Analysis  

• Strength: Weak

Provides incremental advance in temporal causal inference but does not fully meet Carroll Award criteria for paradigmatic shift or cross-scale integration.

- Learns time-varying Bayesian networks to map feedback loops among pain, substance use, housing, and retention.
- Focuses on identifying intervention points within discrete clinical domains, not on managing complex, interdependent systems.
- Does not incorporate data across biological or socioeconomic scales.
- Methodologically robust but lacks disruptive or high-risk elements prioritized by the award.

**Data Sources:**
- OTOP Pain Tracking Intake and Follow-Up Data

**Variables from OTOP Pain Tracking Intake and Follow-Up Data:**

- Required: `painfrequency`, `painduration`, `currentpainyes`, `intakeuds`, `recentdose`, `takehomes`, `takehomephase`, `housingstatus`, `enrollmentstatus`, `udsresults`, `discharge_reason_1mo`, `discharge_reason_mo2`, `discharge_reason_3mo`, `discharge_reason_6mo`, `discharge_reason_12mo`
- Optional: `doseamount`, `mat`, `mat_2mo`, `mat_3mo`, `mat_6mo`, `mat_12mo`
**Summary**: Learn time-varying Bayesian network (PCMCI) among painfrequency, polysubstance use, housing transitions, and retention.  
**Hypothesis**: Temporal causal loops identify intervention points missed by static models.  
**Data Required**: painfrequency, painduration, currentpainyes, intakeuds/udsresults, recentdose, takehomephase, housingstatus, enrollmentstatus, discharge_reason across timepoints.  
**Plan**: (1) Aggregate & align variables; (2) Structure learning & parameter estimation; (3) Simulate interventions & map leverage points.

## Proposal 3: Causal Treatment Effect Estimation  

• Strength: Very Weak
Offers practical, incremental improvements to clinical policy but does not align with Carroll Award criteria for bold, disruptive, or cross-scale innovation.

- Applies marginal structural models to estimate causal effects of dosing and take-home policies on retention and UDS outcomes.
- Focuses on optimizing existing clinical practices within a single domain, without integrating multiple clinical, biological, or socioeconomic factors.
- Lacks elements of paradigmatic shift, cross-scale integration, or high-risk innovation.
  
**Data Sources:**
- OTOP Pain Tracking Intake and Follow-Up Data

**Variables from OTOP Pain Tracking Intake and Follow-Up Data:**

- Required: `doseamount`, `recentdose`, `takehomes`, `takehomephase`, `enrollmentstatus`, `udsresults`
- Optional: `mat`, `mat_2mo`, `mat_3mo`, `mat_6mo`, `mat_12mo`, `discharge_reason_1mo`, `discharge_reason_mo2`, `discharge_reason_3mo`, `discharge_reason_6mo`, `discharge_reason_12mo`
**Summary**: Apply marginal structural models with IPW to estimate causal effects of MAT dose and take-home policies on retention & UDS outcomes.  
**Hypothesis**: Optimal dosing and take-home strategies improve retention by ≥10%.  
**Data Required**: doseamount, recentdose, takehomes, takehomephase, enrollmentstatus, udsresults across intake and follow-ups.  
**Plan**: (1) Define exposures/outcomes/confounders; (2) Compute IP weights & fit MSM; (3) Perform sensitivity analyses; (4) Recommend policy adjustments.

## Proposal 4: Transfer Learning for Adolescent Risk Prediction  

• Strength: Weak
Partially aligns with Carroll Award criteria by attempting cross-population transfer learning, but remains focused on discrete risk prediction rather than complex systems management.

- Pretrains sequence autoencoder on adult trajectories and fine-tunes on adolescent data to improve opioid initiation risk prediction.
- Demonstrates technical innovation in transfer learning across age-defined cohorts, but does not integrate data across biological or socioeconomic scales.
- Does not model interdependent clinical systems or address multi-domain integration.
- Moderate risk; potential for impact is limited by focus on single-outcome prediction.

• Data Assumptions: Cohorts defined solely by DOB and intake date; no external labels.  
**Summary**: Pretrain sequence autoencoder on adult (≥25 yrs) trajectories; fine-tune on adolescents (<18 yrs) for opioid initiation risk.  
**Hypothesis**: Transferred latent representations yield ≥10% uplift vs youth-only baselines.  
**Data Required**: Age labels from DOB, intake date, and intake & follow-up panels.  
**Plan**: (1) Pretrain on adult sequences; (2) Freeze encoder & fine-tune on adolescent outcomes; (3) Evaluate vs baselines.

## Proposal 5: NLP Pain Phenotyping  

• Strength: Very Strong
Strongly meets Carroll Award criteria by leveraging AI to extract complex, emergent phenotypes from unstructured clinical text, moving beyond discrete variable modeling.

- Applies transformer-based embeddings and clustering to free-text pain descriptions, enabling discovery of novel patient subgroups.
- Moves toward managing complex, interdependent systems by linking text-derived phenotypes to clinical trajectories and outcomes.
- Does not integrate data across biological or socioeconomic scales; focus is on clinical and behavioral text data.
- High-risk, disruptive approach with potential for near-term transformative change in patient stratification and intervention.

• Data Assumptions: Relies solely on `currentpainyes`; no external lexicons or annotations.  
**Summary**: Apply transformer embeddings and clustering to intake pain descriptions to derive phenotypes linked to clinical trajectories.  
**Hypothesis**: Text-derived phenotypes stratify patients by treatment response and risk profiles.  
**Data Required**: Free-text `currentpainyes` field at intake.  
**Plan**: (1) Clean & embed text; (2) Cluster phenotypes; (3) Associate clusters with outcomes; (4) Propose phenotype-specific interventions.
