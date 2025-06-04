# Paradigmatic AI Research Proposals for Carroll Award

## Proposal 1: Multi-Modal Temporal Modeling  

• Strength: Fully self-contained; highest predictive accuracy.

- Boldly targets the Carroll Award's paradigm shift by modeling complex, interdependent patient systems rather than isolated clinical events; strong alignment with the award's disruptive vision.
- Approach is ambitious and high-risk, but stands out as transformative compared to conventional predictive models focused on discrete outcomes.
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

• Strength: Reveals actionable feedback loops; explainable insights.

- Methodologically strong but primarily extends existing causal inference to time-varying settings; does not fully embody the bold, disruptive paradigm shift sought by the Carroll Award.
- Focus remains closer to mapping discrete relationships than managing complex, multi-scale systems, limiting transformative impact.
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

• Strength: Direct clinical policy guidance from dose & take-home analyses.

- Relies on established causal inference techniques for incremental policy improvement; lacks the boldness and high-risk innovation prioritized by the Carroll Award.
- Does not advance the field toward managing complex, interdependent systems or cross-scale integration; too conventional for this award's focus.
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

• Strength: Enhances youth risk detection via adult cohort latent dynamics.

- Represents a bold attempt to transfer knowledge across populations, aligning with the Carroll Award's call for disruptive, cross-paradigm AI approaches.
- While innovative, the focus is still on risk prediction for discrete outcomes rather than fundamentally shifting to complex systems management.
• Data Assumptions: Cohorts defined solely by DOB and intake date; no external labels.  
**Summary**: Pretrain sequence autoencoder on adult (≥25 yrs) trajectories; fine-tune on adolescents (<18 yrs) for opioid initiation risk.  
**Hypothesis**: Transferred latent representations yield ≥10% uplift vs youth-only baselines.  
**Data Required**: Age labels from DOB, intake date, and intake & follow-up panels.  
**Plan**: (1) Pretrain on adult sequences; (2) Freeze encoder & fine-tune on adolescent outcomes; (3) Evaluate vs baselines.

## Proposal 5: NLP Pain Phenotyping  

• Strength: Uncovers novel patient subgroups via free-text phenotypes.

- Strongly embodies the Carroll Award's vision by using AI to uncover hidden, complex patient phenotypes from unstructured data—moving beyond discrete clinical variables.
- Approach is disruptive and has high transformative potential for shifting clinical paradigms, though feasibility risks remain.
• Data Assumptions: Relies solely on `currentpainyes`; no external lexicons or annotations.  
**Summary**: Apply transformer embeddings and clustering to intake pain descriptions to derive phenotypes linked to clinical trajectories.  
**Hypothesis**: Text-derived phenotypes stratify patients by treatment response and risk profiles.  
**Data Required**: Free-text `currentpainyes` field at intake.  
**Plan**: (1) Clean & embed text; (2) Cluster phenotypes; (3) Associate clusters with outcomes; (4) Propose phenotype-specific interventions.
