## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose an integrated molecular dynamics and machine learning (MD-ML) workflow to study structural changes in TDP-43 RRM1 domain induced by three disease-associated mutations (I168A, D169G, I168A-D169G). They report that the double mutant shows the highest inner core packing, suggesting greater stability and pathogenic potential, and identify biological descriptors (interacting residue pairs and individual residues) that influence protein stability and could inform therapeutic strategies.
- **Visible evidence base** Abstract text only; no quantitative results, methodological details, or validation metrics provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, simulation parameters, force field choices, convergence criteria, machine learning model architecture and training details, statistical analyses, and any experimental validation

## Reviewer

- **Overall assessment** The abstract presents a potentially interesting computational approach to a clinically relevant problem, but the evidence provided is insufficient to evaluate the validity, novelty, or significance of the findings. The claims are stated without quantitative support, and the methodological framework is described only at a high level. The abstract does not establish a clear case for the conclusions drawn.
- **Who would be interested in the results, and why** Researchers in computational biophysics and structural biology studying protein aggregation in neurodegeneration, particularly those focused on TDP-43 proteinopathies such as ALS and FTD. The proposed MD-ML workflow may also interest method developers seeking integrated approaches for mutation effect prediction.
- **Major strengths** The study addresses a clinically important problem with potential translational relevance. The combination of molecular dynamics and machine learning is a contemporary and potentially powerful approach. The focus on specific disease-associated mutations in a conserved functional domain is well targeted.
- **Major Concerns** The abstract lacks quantitative results, such as RMSD, RMSF, packing density values, or machine learning performance metrics. The claim that higher inner core packing indicates "more stability and higher chances of pathogenesis" is not mechanistically justified. The biological descriptors are mentioned but not specified or validated. No comparison to wild-type or known experimental data is presented.
- **Minor Comments** The abstract would benefit from clearer articulation of the novelty relative to existing computational studies on TDP-43 mutations. The phrase "formulized" is awkward and should be revised. The significance of the double mutant over single mutants is stated but not contextualized with respect to known clinical phenotypes.
- **Technical failings that need to be addressed before the case is established** The absence of any quantitative data or methodological detail in the abstract prevents assessment of technical soundness. The causal link between packing, stability, and pathogenesis is asserted without supporting evidence or literature context.
- **Assessment against Nature-style criteria**  
  - Originality: Not assessable from the abstract; the MD-ML combination is not inherently novel, and no comparison to prior work is provided.  
  - Scientific importance: The topic is important, but the abstract does not demonstrate a significant advance over existing knowledge.  
  - Interdisciplinary readership: The abstract is accessible to a broad structural biology audience, but the lack of quantitative detail limits appeal to method-focused readers.  
  - Technical soundness: Not assessable due to missing methodological and validation details.  
  - Readability for nonspecialists: The abstract is generally readable, though some terms (e.g., "packing of the protein inner core") could be clarified.
- **Recommendation posture** Currently not established from the provided evidence. The abstract alone does not provide sufficient support for the central claims, and a full manuscript review would be required to determine whether the technical concerns can be resolved.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The authors claim that the I168A-D169G double mutant "delineates the highest packing of the protein inner core" and that this "may indicate more stability and higher chances of pathogenesis."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** No quantitative data are presented to support the packing comparison. No values, error bars, statistical tests, or comparisons to wild-type or other mutants are shown.  
- **Why it matters** Without quantitative evidence, the central finding cannot be evaluated or reproduced. The inference from packing to stability and pathogenesis is also not mechanistically justified.  
- **Resolution test** Provide numerical packing metrics (e.g., packing density, void volumes) with statistical significance, and discuss the structural or biophysical basis linking packing to pathogenic propensity.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological transparency  
- **Claim pointer** The authors state they "formulized an integrated workflow of molecular dynamic simulation and machine learning models (MD-ML)."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** No details are given on simulation parameters, force fields, system setup, simulation length, convergence, or the machine learning model type, features, training, and validation.  
- **Why it matters** The reproducibility and validity of the workflow cannot be assessed. Machine learning results are particularly prone to overfitting without proper validation.  
- **Resolution test** Describe the full methodology in the manuscript, including software, parameters, and validation metrics (e.g., cross-validation, test set performance).

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Claim support  
- **Claim pointer** The authors claim to have "identified the biological descriptors of TDP-43 which includes the interacting residue pairs and individual protein residues that influence the stability of the protein."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The specific descriptors are not named, and no evidence is provided that they influence stability in a meaningful or experimentally testable way.  
- **Why it matters** This is presented as a key outcome with therapeutic implications, but without specificity or validation, the claim is unsubstantiated.  
- **Resolution test** List the identified residues and pairs, provide stability-related metrics (e.g., free energy changes, contact maps), and discuss how they could be experimentally targeted.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract wording  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The phrase "formulized" is nonstandard and unclear.  
- **Required correction** Replace with "developed" or "implemented."

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Contextualization  
- **Affected element** Novelty statement  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract does not state how this work differs from prior computational studies on TDP-43 mutations.  
- **Required correction** Add a sentence contrasting the approach or findings with existing literature.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** "packing of the protein inner core"  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The term is vague and could be misinterpreted.  
- **Required correction** Define the metric used (e.g., atomic packing density, cavity volume) in the abstract or methods.

## Risk / unsupported claims

- The claim that higher inner core packing indicates greater stability and higher pathogenic potential is unsupported without quantitative data and mechanistic reasoning.
- The identification of biological descriptors influencing stability is unsubstantiated as no specific residues or pairs are named.
- The overall conclusion that the MD-ML workflow can inform therapeutic strategies is speculative without experimental validation or clear mechanistic links.
- The novelty and technical validity of the MD-ML approach cannot be assessed from the abstract alone.