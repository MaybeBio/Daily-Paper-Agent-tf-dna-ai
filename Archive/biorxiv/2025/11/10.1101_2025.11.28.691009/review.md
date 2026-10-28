## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Scientific content, experimental logic, evidence quality, and claims as presented in the provided text; no external data or supplementary figures were available for verification
- **Shared manuscript claim summary** The authors propose that ERCC6L2, in complex with MRI and KU, coordinates classical non-homologous end joining (NHEJ) specifically at staggered DNA double-strand breaks (DSBs). They report that Ercc6l2-deficient mice show resilient haematopoiesis, mild immunodeficiency with selective defects in class switch recombination (CSR) but not V(D)J recombination, genetic epistasis placing ERCC6L2 downstream of 53BP1 and parallel to shieldin, and a physical complex of ERCC6L2-MRI-KU defined by proteomics and AlphaFold modelling. They conclude that staggered-end DSBs are the pathological substrates in ERCC6L2 disease.
- **Visible evidence base** Results sections describing mouse models, haematopoietic analyses, CSR assays, telomere fusion assays, proteomics, and AlphaFold modelling; methods sections for mice, transplantation, flow cytometry, cell culture, CRISPR editing, proteomics, and structural modelling
- **Missing materials affecting confidence** Figures and Extended Data figures referenced but not provided; statistical details and exact values for many experiments; raw proteomics data; AlphaFold confidence metrics beyond summary statements; details of the telomere fusion assay quantification; information on sample sizes for several experiments

## Reviewer
- **Overall assessment** This manuscript addresses an important question in DNA repair and haematopoietic biology, with potential relevance to understanding bone marrow failure syndromes. The authors present a substantial body of work combining mouse genetics, cellular assays, proteomics, and structural modelling. The central claim that ERCC6L2 functions in a complex with MRI and KU to coordinate NHEJ at staggered DSBs is plausible and mechanistically interesting. However, several key claims are not fully supported by the evidence as presented, and important experimental details are missing. The haematopoietic resilience data are convincing but somewhat negative in nature, while the mechanistic claims rely heavily on AlphaFold predictions and in vitro assays that require further validation. The distinction between staggered and blunt end joining is a potentially significant finding but needs stronger experimental support. Overall, the work is promising but requires substantial revision to fully establish the proposed model.
- **Who would be interested in the results, and why** Researchers in the fields of DNA repair, particularly NHEJ and DSB repair pathway choice; haematologists and those studying bone marrow failure syndromes; cancer biologists interested in genome stability and therapeutic targeting of DNA repair; structural biologists studying protein-DNA repair complexes. The work also has relevance to understanding the molecular basis of inherited bone marrow failure and could inform future therapeutic strategies for ERCC6L2 disease.
- **Major strengths** The study addresses a clinically relevant question with potential translational implications. The combination of in vivo mouse models with biochemical and structural approaches is comprehensive. The genetic epistasis experiments are well designed to position ERCC6L2 within the NHEJ pathway. The identification of a specific ERCC6L2-MRI-KU complex is novel and provides a mechanistic framework. The use of telomere fusion assays to distinguish staggered versus blunt end joining is an elegant approach.
- **Major Concerns** 
  - R1-M1: The claim that ERCC6L2 is dispensable for haematopoiesis is based on limited analyses and may not fully exclude subtle defects.
  - R1-M2: The mechanistic model relies heavily on AlphaFold predictions without sufficient biochemical validation.
  - R1-M3: The distinction between staggered and blunt end joining is based on telomere fusion assays that may not fully recapitulate the in vivo context of CSR.
  - R1-M4: The genetic epistasis experiments with shieldin are interpreted as parallel pathways, but the data may also be consistent with other models.
  - R1-M5: The relevance of the findings to human ERCC6L2 disease is speculative and not directly tested.
- **Minor Comments** 
  - R1-m1: The manuscript contains several typographical errors and inconsistencies in terminology.
  - R1-m2: The methods section lacks detail on certain experimental procedures.
  - R1-m3: The presentation of proteomics data is incomplete.
  - R1-m4: The statistical analysis section is brief and lacks detail on multiple testing corrections.
  - R1-m5: The discussion is overly speculative in places.
- **Technical failings that need to be addressed before the case is established** The AlphaFold-derived structural model requires experimental validation through mutagenesis or crosslinking; the telomere fusion assay needs additional controls to confirm the specificity of the staggered-end phenotype; the proteomics data need to be presented with full statistical analysis and validation of key interactions; the in vivo relevance of the proposed mechanism to human disease needs to be tested or at least discussed with appropriate caveats.
- **Assessment against Nature-style criteria** 
  - Originality: The identification of an ERCC6L2-MRI-KU complex and its proposed role in staggered-end NHEJ is novel and represents a significant conceptual advance. However, the overall framework of ERCC6L2 in NHEJ is not entirely new, and the specific mechanistic details require further validation.
  - Scientific importance: The work has clear importance for understanding DNA repair mechanisms and their role in haematopoietic maintenance. The potential link to bone marrow failure syndromes adds clinical significance. However, the importance is somewhat tempered by the negative haematopoietic findings in mice and the speculative nature of the disease relevance.
  - Interdisciplinary readership: The work bridges DNA repair, haematology, and structural biology, and should appeal to a broad readership. The clinical relevance to bone marrow failure syndromes increases its potential impact.
  - Technical soundness: The experimental approaches are generally sound, but several key claims rely on computational predictions and assays that need additional validation. The lack of key experimental details and the absence of figures for verification reduce confidence in the technical execution.
  - Readability for nonspecialists: The manuscript is generally well written and accessible, with clear explanations of complex concepts. However, some sections, particularly the structural modelling, may be challenging for nonspecialists. The abstract and introduction are clear and engaging.
- **Recommendation posture** Supportive if technical concerns are resolved. The core hypothesis is interesting and the work has potential, but the current evidence does not fully establish the proposed model. The authors need to provide additional experimental validation of the structural predictions, strengthen the biochemical evidence for the complex, and address the concerns about the telomere fusion assay and the relevance to human disease.

## Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** No
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "Ercc6l2-deficient haematopoietic stem and progenitor cell (HSPC) compartment in mice is unexpectedly resilient" and that ERCC6L2 is "largely dispensable for HSC self-renewal and long-term reconstitution of haematopoiesis."
- **Evidence point** Results section "Resilient haematopoiesis characterises a mouse model of ERCC6L2 disease"; Figures 1b-e and Extended Data Figures 1c-i
- **Concern** The conclusion of haematopoietic resilience is based on a small cohort of mice aged to 2 years and on competitive transplantation experiments. The sample sizes are not stated, and the analyses appear to focus on steady-state frequencies and transplantation reconstitution. This may not be sufficient to exclude subtle defects in HSC function, particularly under stress conditions. The authors do not report serial transplantation beyond secondary transplants, and no stress-induced haematopoiesis assays (e.g., 5-fluorouracil treatment, serial bleeding) are described. The claim of resilience is therefore based on a limited set of conditions.
- **Why it matters** The haematopoietic phenotype is central to the manuscript's relevance to ERCC6L2 disease. If the mouse model does not faithfully recapitulate the human condition, the translational implications are weakened. A more thorough characterization of HSC function under stress would strengthen the conclusion that ERCC6L2 is dispensable for steady-state haematopoiesis.
- **Resolution test** Provide sample sizes and statistical power calculations for all haematopoietic analyses. Include stress-induced haematopoiesis assays (e.g., 5-FU treatment, serial transplantation beyond secondary, competitive repopulation with limiting dilution analysis). If possible, include analysis of HSC self-renewal in vitro (e.g., colony-forming unit assays, LTC-IC).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "AF3 generated high-confidence models in which ERCC6L2 formed a complex with DNA bound KU70-KU80, linked by bridging interactions provided by ERCC6L2- and KU- binding interfaces in MRI" and that specific residues (T52, V53, Y54 on MRI; T1213, F1214, I1215 on ERCC6L2) form the interface.
- **Evidence point** Results section "Proteomic elucidation of the endogenous interactome and AlphaFold structural modelling"; Figures 4b-d and Extended Data Figure 9d-e
- **Concern** The structural model is based entirely on AlphaFold3 predictions. While AlphaFold3 has shown impressive performance, the specific claims about interface residues and the functional significance of the predicted interactions require experimental validation. The authors do not provide mutagenesis data to test the predicted interface, nor do they provide crosslinking or other biochemical evidence to confirm the complex architecture. The claim that the model is "high-confidence" is based on pLDDT and PAE scores, but these metrics do not guarantee functional relevance.
- **Why it matters** The structural model is a key part of the proposed mechanism. If the predicted interactions are incorrect or functionally irrelevant, the entire model of ERCC6L2-MRI-KU complex function is called into question. Experimental validation of the interface is essential to support the central claim.
- **Resolution test** Provide mutagenesis of the predicted interface residues (e.g., T52A, V53A, Y54A on MRI; T1213A, F1214A, I1215A on ERCC6L2) and test the effects on complex formation (co-immunoprecipitation) and NHEJ function (CSR assays or telomere fusion assays). Alternatively, provide crosslinking mass spectrometry or hydrogen-deuterium exchange data to confirm the complex architecture.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Experimental design
- **Claim pointer** The authors claim that "ERCC6L2 stimulates the fusion of dysfunctional telomeres when they have G-strand ssDNA tailed, but not blunt telomeric ends," supporting a specific role in staggered-end NHEJ.
- **Evidence point** Results section "ERCC6L2 stimulates NHEJ at staggered DNA ends" (implied); Figures 3b-g and Extended Data Figure 8
- **Concern** The telomere fusion assay is used as a model for staggered-end NHEJ, but the physiological relevance of this assay to CSR is not fully established. The authors do not provide a detailed characterization of the telomere end structures in their experimental system, and the distinction between "staggered" and "blunt" ends is based on the deletion of Trf2 versus Rap1/Apollo, which may have additional effects beyond altering end structure. The assay may not fully recapitulate the complexity of AID-induced DSBs during CSR, which involve clustered lesions and specific chromatin context.
- **Why it matters** The specificity of ERCC6L2 for staggered ends is a key claim of the manuscript. If the telomere fusion assay does not accurately model the relevant DSB substrates, the conclusion that ERCC6L2 is specifically required for staggered-end NHEJ is weakened.
- **Resolution test** Provide additional characterization of the telomere end structures in the experimental system (e.g., electron microscopy, native gel analysis). Include a more direct assay for staggered-end NHEJ, such as a plasmid-based repair assay with defined overhangs. If possible, test ERCC6L2 function in a system that more closely mimics AID-induced DSBs.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The authors claim that "ERCC6L2 and the shieldin complex mediate independent, non-redundant joining activities at AID-dependent DSBs" based on the synergistic effect of Ercc6l2 and Shld2 co-deletion on CSR.
- **Evidence point** Results section "ERCC6L2 and shieldin act in parallel pathways during CSR" (implied); Figures 2g-h and Extended Data Figure 7
- **Concern** The interpretation of synergy as evidence for parallel pathways is reasonable but not definitive. The authors do not provide a mechanistic explanation for how ERCC6L2 and shieldin could act on different substrates or at different steps of the same pathway. The data are also consistent with a model where ERCC6L2 and shieldin act in the same pathway but at different steps, with the combined loss having a more severe phenotype due to the loss of two rate-limiting steps. The authors should provide additional evidence to distinguish between these models.
- **Why it matters** The proposed parallel pathway model is important for understanding the division of labor in NHEJ at staggered ends. If the interpretation is incorrect, the mechanistic model of ERCC6L2 function is less clear.
- **Resolution test** Provide additional experiments to distinguish between parallel and sequential models. For example, examine the kinetics of DSB repair in single and double mutants, or analyze the recruitment of ERCC6L2 and shieldin to DSBs in real time. Alternatively, identify specific substrates or intermediates that are differentially affected by loss of ERCC6L2 versus shieldin.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Translational relevance
- **Claim pointer** The authors speculate that "staggered-end breaks represent the pathological substrates driving haematopoietic failure in ERCC6L2 disease" and suggest that telomere dysfunction may be involved.
- **Evidence point** Discussion section
- **Concern** The link between the proposed mechanism and the human disease is entirely speculative. The authors do not provide any data from patient samples or patient-derived cells to support the claim that staggered-end DSBs are the relevant pathological substrates. The mouse model does not show haematopoietic failure, which limits its utility for understanding the human disease. The suggestion that telomere dysfunction may be involved is not tested.
- **Why it matters** The clinical relevance of the work is a major selling point. If the link to human disease is not established, the impact of the work is reduced.
- **Resolution test** Provide data from patient-derived cells or samples, such as analysis of DSB repair in ERCC6L2-mutant patient fibroblasts or HSCs. If patient samples are not available, provide a more detailed discussion of the limitations of the mouse model and the speculative nature of the disease relevance.

## Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Introduction
- **Evidence point** Abstract, Introduction
- **Issue** The manuscript contains several typographical errors and inconsistencies. For example, "ERRC6L2" in the abstract should be "ERCC6L2". The term "interacters" in the Results section should be "interactors". The Introduction states "ERCC6L2-deficency" which should be "ERCC6L2-deficiency".
- **Required correction** Proofread the manuscript carefully and correct all typographical and grammatical errors.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence point** Methods sections for flow cytometry, CSR assay, and telomere FISH
- **Concern** The methods section lacks detail on several experimental procedures. For example, the flow cytometry gating strategy is not described, the CSR assay does not specify the concentration of LPS used, and the telomere FISH analysis does not describe the number of metaphases scored per experiment beyond "at least ten".
- **Required correction** Provide complete details for all experimental procedures, including gating strategies, reagent concentrations, and sample sizes.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Proteomics results
- **Evidence point** Results section "Proteomic elucidation of the endogenous interactome"
- **Concern** The proteomics data are presented in a summarized form without full statistical analysis. The authors state that ERCC6L2, KU70, KU80, and MRI were identified, but do not provide enrichment scores, p-values, or a full list of identified proteins. The two biological replicates are mentioned, but the variability between replicates is not shown.
- **Required correction** Provide a full table of identified proteins with enrichment scores and statistical significance, and show the variability between replicates.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Statistics section
- **Evidence point** Methods section "Statistics"
- **Concern** The statistics section is very brief and does not describe the statistical tests used for each experiment, whether multiple testing corrections were applied, or how normality was assessed. The figure legends are stated to contain the relevant methods, but these are not provided.
- **Required correction** Provide a detailed statistics section describing the tests used for each experiment, including corrections for multiple testing where applicable.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence point** Discussion section
- **Concern** The discussion is overly speculative in places, particularly regarding the potential role of ERCC6L2 at telomeres and the relevance to human disease. While speculation is appropriate in a discussion, the authors should more clearly distinguish between conclusions supported by their data and hypotheses that require further testing.
- **Required correction** Revise the discussion to more clearly separate data-supported conclusions from speculative hypotheses.

## Risk / unsupported claims
- The claim that ERCC6L2 is "largely dispensable for HSC self-renewal and long-term reconstitution" is not fully supported due to limited experimental conditions and missing sample sizes.
- The specific structural model of the ERCC6L2-MRI-KU complex, including the identified interface residues, is based solely on AlphaFold predictions and is not experimentally validated.
- The claim that ERCC6L2 specifically functions at staggered-end DSBs is based on telomere fusion assays that may not fully recapitulate the in vivo context of CSR.
- The interpretation of synergy between ERCC6L2 and shieldin as evidence for parallel pathways is not definitive and could be consistent with other models.
- The speculation that staggered-end breaks are the pathological substrates in ERCC6L2 disease is not tested with patient samples or patient-derived cells.
- The suggestion that telomere dysfunction may be involved in ERCC6L2 disease is entirely speculative and not supported by direct evidence.