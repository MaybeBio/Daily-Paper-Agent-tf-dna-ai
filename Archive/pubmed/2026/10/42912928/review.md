## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report that micheliolide (MCL) covalently engages Cys367 in the STAT3 DNA-binding domain (DBD), a residue unique to STAT3 among STAT family members, and that this modification disrupts STAT3 phosphorylation at Tyr705, nuclear translocation, and transcriptional activity without upstream JAK inhibition. Using covalent docking, R-group enumeration, and free-energy perturbation (FEP), they designed MCL analogs with improved physicochemical properties. Microscale thermophoresis (MST) confirms C367-dependent binding; molecular dynamics (MD) simulations and pair-interaction energy analyses identify electrostatic interactions with Lys365, Val366, and Ile368 as dominant. Compound 16 is proposed as a next-generation lead.
- **Visible evidence base** Abstract text only; no experimental details, numerical data, structural coordinates, or statistical analyses provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, experimental methods, compound synthesis and characterization data, assay protocols, statistical details, MD simulation parameters, FEP calculation settings, and any supplementary information

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting strategy for targeting a previously challenging site on STAT3, and the combination of covalent docking with FEP-guided optimization is timely. However, the abstract alone provides insufficient evidence to evaluate the rigor of the experimental design, the validity of the computational methods, or the robustness of the biological conclusions. Several claims, particularly those regarding the mechanism of action and the drug-like superiority of compound 16, are stated without supporting quantitative data. The work may be of interest to medicinal chemists and cancer biologists, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Medicinal chemists working on covalent inhibitors and undruggable targets would find the FEP-guided design approach relevant. Cancer biologists studying STAT3 signaling, particularly in pancreatic cancer, would be interested in the proposed C367-dependent mechanism. Computational chemists may value the application of FEP to covalent inhibitor optimization. The potential clinical relevance of ACT001 derivatives may also attract translational researchers.
- **Major strengths** The identification of a STAT3-specific cysteine residue in the DBD as a covalent target is a novel concept that could address selectivity limitations of SH2-domain inhibitors. The combination of experimental and computational approaches, including MST, MD simulations, and FEP, is multidisciplinary and potentially powerful. The focus on physicochemical property optimization alongside potency is commendable for lead development.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Biological mechanism
  - **Claim pointer** The abstract claims that C367 modification disrupts STAT3 phosphorylation at Tyr705, nuclear translocation, and transcriptional activity prior to any detectable inhibition of upstream JAK phosphorylation, suggesting that STAT3 inhibition is not primarily driven by upstream kinase blockade.
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** The temporal ordering of events (C367 modification preceding JAK inhibition) is stated as a key mechanistic finding, but no kinetic data, dose-response curves, or time-course experiments are described. The claim that STAT3 inhibition is not driven by upstream kinase blockade requires direct measurement of JAK activity and STAT3 phosphorylation at matched time points and concentrations. Without these data, the causal sequence is not established.
  - **Why it matters** The central novelty of the paper rests on a STAT3-intrinsic mechanism of inhibition. If JAK inhibition occurs at similar or lower concentrations, the proposed selectivity and mechanism would be undermined. This claim is foundational to the paper's significance.
  - **Resolution test** Provide time-course and dose-response data for JAK phosphorylation, STAT3 Tyr705 phosphorylation, nuclear translocation, and transcriptional activity in the same cell system. Show that C367 modification occurs at earlier time points or lower concentrations than any detectable JAK inhibition, with appropriate statistical comparisons.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Computational methodology
  - **Claim pointer** The abstract states that FEP-guided optimization was used to design MCL analogs with improved properties, and that microsecond-scale MD simulations and pair-interaction energy analyses highlight stable complexes with electrostatic interactions predominating.
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** No details are provided on the FEP protocol, including the force field, simulation length, number of lambda windows, convergence criteria, or the correlation between predicted and experimental binding affinities. Similarly, the MD simulation conditions, system setup, and the method for pair-interaction energy analysis are not described. Without these details, the reliability of the computational predictions cannot be assessed.
  - **Why it matters** The claim that FEP-guided design was successful depends on the accuracy of the calculations. If the FEP predictions were not validated against experimental binding data for a training set, the design rationale is weakened. The MD-based interaction analysis is also central to the proposed binding mode.
  - **Resolution test** Provide full computational methods, including software versions, force field parameters, system preparation, simulation lengths, convergence metrics, and a comparison of FEP-predicted versus experimentally measured binding affinities for the designed analogs. Show that the MD simulations are converged and that the pair-interaction energy analysis is statistically robust.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Compound characterization and selectivity
  - **Claim pointer** The abstract claims that compound 16 is a promising next-generation lead with a superior drug-like profile, and that the derivatives retain comparable antiproliferative potency with improved physicochemical properties.
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** No quantitative data are provided for antiproliferative potency (e.g., IC50 values), solubility, lipophilicity, or selectivity of compound 16 against other STAT family members or off-target proteins. The claim of a superior drug-like profile requires comparison with the parent MCL and with established STAT3 inhibitors. Selectivity for C367 over other cysteines in the proteome is not demonstrated.
  - **Why it matters** The translational potential of compound 16 is a key conclusion. Without quantitative potency, selectivity, and physicochemical data, the claim of superiority is unsupported. Off-target reactivity is a major concern for covalent inhibitors.
  - **Resolution test** Provide IC50 values for MCL and all analogs in relevant pancreatic cancer cell lines, measured solubility and logP values, and selectivity data for compound 16 against STAT1, STAT5, and a panel of cysteine-containing proteins. Include a comparison with a known STAT3 inhibitor as a reference.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract wording
  - **Evidence pointer** Abstract text; location not provided
  - **Issue** The phrase "prior to any detectable inhibition of upstream JAK phosphorylation" is ambiguous. It is unclear whether this refers to a time-course experiment, a concentration-response experiment, or both.
  - **Required correction** Specify the experimental design that supports this temporal claim, or rephrase to describe the actual observations without implying a specific temporal order.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Compound numbering
  - **Evidence pointer** Abstract text; location not provided
  - **Issue** Compound 16 is mentioned as the lead, but no structural information or relationship to other analogs is provided in the abstract.
  - **Required correction** Include a brief structural description or refer to a figure in the full manuscript that shows the structure of compound 16 and its relationship to MCL.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Binding and simulation data
  - **Evidence pointer** Abstract text; location not provided
  - **Issue** No statistical measures (e.g., error bars, confidence intervals, replicate numbers) are mentioned for MST binding data or MD simulation analyses.
  - **Required correction** State the number of replicates and statistical methods used for MST measurements and for the pair-interaction energy analyses in the full manuscript.
- **Technical failings that need to be addressed before the case is established** R1-M1 (mechanistic temporal claim), R1-M2 (computational methodology transparency), R1-M3 (quantitative compound characterization and selectivity)
- **Assessment against Nature-style criteria**  
  Originality: The concept of targeting a STAT3-specific cysteine in the DBD is original and potentially significant. However, the abstract does not provide enough context to determine how this compares with existing covalent STAT3 inhibitors.  
  Scientific importance: If fully validated, the work could address a significant gap in STAT3-targeted therapy for pancreatic cancer. The importance is high, but the evidence presented is insufficient to confirm the claims.  
  Interdisciplinary readership: The work bridges medicinal chemistry, computational chemistry, and cancer biology, which could appeal to a broad audience. However, the abstract is written in a way that assumes familiarity with all three fields.  
  Technical soundness: The technical soundness cannot be assessed from the abstract alone. The lack of methodological detail for FEP, MD, and MST is a major limitation.  
  Readability for nonspecialists: The abstract is dense and uses field-specific jargon without sufficient explanation. A nonspecialist would struggle to understand the significance of the findings.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an interesting hypothesis and a plausible workflow, but the absence of quantitative data and methodological detail prevents a fair assessment of the claims. I would be supportive if the full manuscript addresses the major concerns outlined above.

## Risk / unsupported claims
- The claim that C367 modification occurs prior to JAK inhibition and is therefore not driven by upstream kinase blockade is unsupported without time-course and dose-response data.
- The claim that FEP-guided design successfully optimized the analogs is unsupported without details on the FEP protocol and validation against experimental data.
- The claim that compound 16 has a superior drug-like profile is unsupported without quantitative potency, solubility, lipophilicity, and selectivity data.
- The claim that electrostatic interactions with Lys365, Val366, and Ile368 predominate is unsupported without details on the MD simulation setup and the pair-interaction energy analysis methodology.
- The claim that C367 is unique to STAT3 among STAT family members is plausible but not verifiable from the abstract alone; sequence alignment data are not provided.