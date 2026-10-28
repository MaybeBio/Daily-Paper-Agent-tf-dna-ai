## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, conclusions) as provided by the user. Supplementary Information referenced but not supplied.
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims relative to the evidence presented in the main text. No assessment of editorial fit or journal policy.
- **Shared manuscript claim summary** The authors use homology modeling, molecular docking, and molecular dynamics simulations to characterize the binding of 90 polycyclic aromatic compounds (PACs) to the rat aryl hydrocarbon receptor (rAhR), identifying van der Waals interactions and residues Pro295 and Arg316 as key drivers. They further develop two QSAR models (for non-halogenated and halogenated PACs) with reported good predictive performance, and interpret descriptor contributions mechanistically.
- **Visible evidence base** Main text tables (Tables 1–4), figures (Figures 1–4), equations (1)–(2), and statistical parameters reported in the text. Supplementary tables and figures are referenced but not available for inspection.
- **Missing materials affecting confidence** Supplementary Information (SI Tables S1–S4, SI Figures S1–S7), including the full docking results, MD simulation details, descriptor values, and validation data. The homology model construction details are only partially described. The dataset sources are cited but the raw experimental values are not fully reproduced in the main text.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant toxicological question, namely the molecular basis of rAhR activation by diverse PACs, and combines computational structural biology with QSAR modeling. The structural simulation component is plausible but limited by the absence of experimental validation and the lack of detailed SI inspection. The QSAR models appear statistically reasonable, but the mechanistic interpretation of descriptors is speculative and not fully supported by the simulation data. The link between the two components is underdeveloped. The manuscript is technically sound in parts but the overall case, particularly the claimed mechanistic insight and the generalizability of the models, is not fully established from the provided evidence.
- **Who would be interested in the results, and why** Researchers in environmental toxicology, particularly those studying AhR-mediated effects of polycyclic aromatic compounds; computational chemists working on ligand-receptor interactions; and regulatory scientists interested in predictive models for hazard assessment of PACs. The QSAR models may be of practical use for screening untested PACs.
- **Major strengths** 1. The study combines multiple computational approaches (homology modeling, docking, MD, QSAR) to address a mechanistically important question. 2. The QSAR models are validated using multiple criteria (internal, external, CCC), which is commendable. 3. The identification of specific residues (Pro295, Arg316) and interaction types provides testable hypotheses. 4. The distinction between non-halogenated and halogenated PACs in model development is chemically sensible.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of experimental validation), R1-M2 (incomplete reporting of MD methodology), R1-M3 (overinterpretation of descriptor causality), R1-M4 (unsubstantiated generalizability claim).
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The combination of MD and QSAR for PAC-rAhR is not entirely novel, but the specific focus on rat AhR and the inclusion of halogenated PACs adds some value.  
  *Scientific importance*: Moderate. The findings are of interest to the toxicology community but do not represent a major conceptual advance.  
  *Interdisciplinary readership*: Limited. The work is primarily of interest to computational toxicologists and environmental chemists.  
  *Technical soundness*: Partially sound. The QSAR statistics are reasonable, but the MD component lacks sufficient detail and validation.  
  *Readability for nonspecialists*: Acceptable. The text is generally clear, though some sections assume familiarity with computational methods.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the need for experimental validation, full reporting of MD parameters, and tempering of mechanistic claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "van der Waals forces" are the major driving force in PACs-rAhR binding and that Pro295 and Arg316 are "key residues" governing activity.
- **Evidence pointer** Section 2.1, Table S2 (referenced), Figure 2
- **Concern** The identification of key residues and interaction types is based solely on computational predictions (docking and MD) without any experimental corroboration, such as site-directed mutagenesis or binding assays with modified ligands. The claim that these residues "govern" activity implies a causal role that computational binding energy decomposition alone cannot establish.
- **Why it matters** Without experimental validation, the mechanistic claims remain speculative. Overstating computational predictions as definitive mechanisms could mislead downstream research and risk assessment applications.
- **Resolution test** Provide experimental validation (e.g., mutagenesis of Pro295 and Arg316 followed by activity assays) or substantially temper the language to indicate that these are predicted, not confirmed, key residues.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors state that MD simulations were performed for 15 complexes with varying time scales (70–200 ns) and that binding free energies were calculated using MM/GBSA.
- **Evidence pointer** Section 3.2, Section 2.1, Table S2 (referenced)
- **Concern** The methods section lacks critical details required for reproducibility: force field parameters for ligands (GAFF? AM1-BCC charges?), water model, salt concentration, temperature/pressure coupling algorithms, and the number of snapshots used for MM/GBSA calculations. The variation in simulation time scales (70–200 ns) across complexes is not justified. Convergence criteria are not reported.
- **Why it matters** Reproducibility is a core requirement for computational studies. Without these details, the MD results cannot be independently verified, and the reported ΔGbind values are not fully trustworthy.
- **Resolution test** Provide a complete description of MD simulation parameters, ligand parameterization, and convergence analysis in the main text or SI.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive validity
- **Claim pointer** The authors interpret QSAR descriptors mechanistically, e.g., "molecular polarizability" as enhancing van der Waals interactions, and EHOMO as reflecting nucleophilicity that impedes binding.
- **Evidence pointer** Sections 2.2 and 2.3, Tables 1 and 3
- **Concern** The causal interpretation of QSAR descriptors is speculative. Correlational descriptors do not establish mechanism. For example, the claim that higher EHOMO impedes electrophile-nucleophile interactions is plausible but not directly tested. The link between the MD-derived insight (van der Waals dominance) and the QSAR descriptor interpretation is asserted but not quantitatively demonstrated.
- **Why it matters** Overinterpretation of descriptor causality can lead to incorrect mechanistic conclusions and poor extrapolation to untested compounds.
- **Resolution test** Either provide additional analyses (e.g., correlation between descriptor values and MD-derived interaction energies) or explicitly frame descriptor interpretations as hypotheses rather than conclusions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors state that the models "could be employed to predict the rAhR activity of other reactive PACs" and that they "assist in the assessment of their fate and risk in organisms."
- **Evidence pointer** Abstract, Section 2.3, Section 4
- **Concern** The applicability domain of the QSAR models is not clearly defined. The training sets are limited (62 and 21 compounds, respectively) and cover specific chemical classes. The claim of generalizability to "other reactive PACs" is not supported by external validation on diverse structures. The models are developed for rAhR activity in a specific in vitro assay; extrapolation to in vivo risk is not justified.
- **Why it matters** Overstated generalizability could lead to inappropriate use of the models for regulatory or risk assessment purposes.
- **Resolution test** Define the applicability domain explicitly, test the models on an external set of diverse PACs, and temper claims regarding in vivo risk assessment.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1, statement on RMSD values
- **Evidence pointer** Section 2.1, SI Figure S4 (referenced)
- **Issue** The text states that RMSD values for all ligands are less than 2 Å, while receptor RMSD reaches up to 8 Å. This large receptor flexibility is not discussed in terms of its implications for binding site stability or the validity of the chosen representative structures.
- **Required correction** Add a brief discussion of receptor flexibility and how the selected cluster representative accounts for it.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 2.2, model validation
- **Evidence pointer** Section 2.2, Table 2
- **Issue** The text reports R2 and Q2 values but does not report confidence intervals or standard errors for the regression coefficients. The number of descriptors (6) relative to the sample size (62) is not discussed in terms of overfitting risk.
- **Required correction** Report standard errors or confidence intervals for coefficients and discuss the ratio of samples to descriptors.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Section 3.1, dataset description
- **Evidence pointer** Section 3.1, Table S1 (referenced)
- **Issue** The text states that IEQ values are "relative to 2,3,7,8-tetrachlodizenzo-p-dioxin (TCDD)" but the spelling "tetrachlodizenzo" appears to be a typo. Also, the relationship between IEQ and activity is described as "negative" but the direction is not clearly explained.
- **Required correction** Correct the typo and clarify the direction of the relationship between IEQ values and rAhR activity.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.2, homology modeling
- **Evidence pointer** Section 3.2, SI (referenced)
- **Issue** The template selection process and the criteria for choosing the "lowest Molpdf value" are not described in the main text. The quality of the homology model is only partially validated (Ramachandran, Z-score).
- **Required correction** Briefly describe the template selection and include additional model validation metrics (e.g., QMEAN, ERRAT) in the main text or SI.

## Risk / unsupported claims
- The claim that Pro295 and Arg316 are "key residues" governing rAhR activity is unsupported without experimental validation.
- The claim that the QSAR models can predict activity of "other reactive PACs" is unsupported without a defined applicability domain and external validation on diverse structures.
- The claim that the models "assist in the assessment of their fate and risk in organisms" is unsupported, as the models are based on in vitro data and do not account for toxicokinetics.
- The mechanistic interpretation of QSAR descriptors (e.g., EHOMO as nucleophilicity) is speculative and not directly tested.
- The reported ΔGbind values and their interpretation are not fully assessable without complete MD methodological details and SI data.