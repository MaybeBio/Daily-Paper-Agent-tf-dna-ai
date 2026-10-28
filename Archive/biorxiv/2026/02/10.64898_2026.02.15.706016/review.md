## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) without figures, tables, or supplementary data
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency based solely on the provided text
- **Shared manuscript claim summary** The authors propose that the MECP2 MBD and ID function as a single integrated nucleic acid binding module, that this module binds both methylated DNA and structured RNA with high affinity, that RNA competitively displaces DNA binding, and that Rett syndrome-associated ID mutations selectively impair RNA and non-methylated DNA binding while preserving methyl-DNA binding, providing a potential molecular etiology for Rett syndrome
- **Visible evidence base** Methods descriptions for protein expression, purification, fluorescent anisotropy binding assays, EMSA, and competition experiments; results narrative with quantitative KD,app values; sequence alignment methods; ClinVar variant identification
- **Missing materials affecting confidence** All figures and tables (including Fig. 1-5, Fig. S3, Tables S2-S3), supplementary data, raw binding curves, statistical analysis details, and the multiple sequence alignment visualization are not provided

## Reviewer
- **Overall assessment** The manuscript presents a compelling and potentially important redefinition of MECP2 nucleic acid binding architecture, proposing that the MBD and ID function as a single integrated module rather than as independent domains. The central claims are internally consistent and the experimental approach is logical. However, the absence of all figures, tables, and supplementary data prevents independent verification of the quantitative results, the quality of the binding data, and the statistical analyses. The claim that ID mutations selectively impair RNA and non-methylated DNA binding while preserving methyl-DNA binding is particularly interesting but requires careful scrutiny of the actual binding data. The therapeutic implications regarding the MiniGene construct are clinically relevant but the biochemical characterization appears incomplete. The manuscript would benefit from additional structural or biophysical evidence to support the proposed competitive interface model.

- **Who would be interested in the results, and why** Researchers studying MECP2 function and Rett syndrome pathogenesis will find this work directly relevant. The proposed integrated MBD-ID model challenges the existing domain segregation paradigm and may influence how the field interprets MECP2 mutations. Investigators interested in nucleic acid binding proteins with dual DNA/RNA specificity, particularly those studying intrinsically disordered regions in nucleic acid recognition, will also find the results relevant. The potential therapeutic implications for the MiniGene construct currently in clinical trials make this work of interest to translational researchers and clinicians involved in Rett syndrome gene therapy development.

- **Major Strengths**
  - The manuscript addresses a genuine and important contradiction in the MECP2 literature: the proposed segregation of DNA and RNA binding functions versus evidence for competitive displacement
  - The experimental design is systematic and logical, progressing from domain-level dissection to full-length protein characterization to disease-associated mutations
  - The inclusion of a therapeutic construct (MiniGene) in the analysis adds translational relevance
  - The proposed model of an integrated nucleic acid binding module with competitive DNA/RNA interactions provides a testable framework for future studies
  - The selection of patient-derived mutations with documented clinical significance strengthens the disease relevance of the findings

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality and verification
- **Claim pointer** The authors claim that the ID enhances MBD affinity for methylated DNA by approximately 35-fold and that the MBD-ID construct recapitulates full-length MECP2 binding behavior
- **Evidence pointer** Results section "Synergy Between the ID and MBD Drives High-Affinity DNA Binding by MECP2"; Fig. 3B (not provided)
- **Concern** The central quantitative claim of 35-fold affinity enhancement cannot be verified without the actual binding curves, fitted parameters, and statistical comparisons. The text states that MBD-ID closely recapitulates full-length protein behavior, but no quantitative comparison between MBD-ID and full-length MECP2 is provided in the text. The Hill coefficient of 2.4 for full-length MECP2 suggests cooperativity, but it is unclear whether the MBD-ID construct also exhibits cooperativity and whether the comparison is appropriate.
- **Why it matters** The 35-fold enhancement is a cornerstone of the integrated module model. If the enhancement is smaller or the MBD-ID does not truly recapitulate full-length behavior, the central thesis is weakened. The claim that MBD-ID is "necessary and sufficient" for DNA binding requires direct quantitative comparison with full-length MECP2.
- **Resolution test** Provide the actual binding isotherms, fitted KD,app values with errors, and statistical comparisons between MBD, MBD-ID, and full-length MECP2 for both methylated and non-methylated DNA. Report the number of independent replicates and the statistical test used.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality and verification
- **Claim pointer** The authors claim that the MBD-ID module binds structured RNAs with high affinity (KD,app approximately 2-10 nM) and that this binding is competitive with DNA binding
- **Evidence pointer** Results section "The MECP2 MBD-ID is a High-Affinity, Promiscuous RNA-Binding Module"; Fig. 4A-C and Fig. 5A-C (not provided)
- **Concern** The RNA binding data are presented as a series of KD,app values for different RNA ligands, but the text does not provide information on the RNA structural characterization, the basis for selecting these particular RNA sequences, or the quality of the binding fits. The claim of "promiscuous" RNA binding is based on testing only a limited set of structured RNAs. The competition experiments demonstrating RNA-mediated displacement of MECP2 from DNA are described but the actual displacement curves, IC50 values, and the stoichiometry of the competition are not provided. The text states that RNA binding "precludes" DNA binding, but the mechanism (steric versus allosteric) is not experimentally distinguished.
- **Why it matters** The competitive binding model is central to the proposed biological function of the MBD-ID module. Without the actual competition data and RNA binding characterization, the claim that RNA can displace MECP2 from chromatin cannot be properly evaluated. The limited RNA ligand set may not adequately support the "promiscuous" RNA binding claim.
- **Resolution test** Provide the RNA binding isotherms for all tested RNA ligands, the competition displacement curves with IC50 values, and a clear demonstration of whether the competition is mutually exclusive binding or allosteric. Include structural characterization of the RNA ligands (e.g., predicted or experimentally determined secondary structures).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support and interpretation
- **Claim pointer** The authors claim that Rett syndrome-associated ID mutations (R167W, K174Q, R190H) selectively weaken RNA and non-methylated DNA binding while preserving methyl-DNA binding, and that this "decoupling" provides a potential molecular etiology for Rett syndrome
- **Evidence pointer** Results section "Rett-associated Mutations in the Intervening Domain Affect Nucleic Acid Interactions"; Table 1 (not provided)
- **Concern** The text states that all three patient variants and the K(171-174)A control bound methylated DNA with "nearly identical" affinity to wild-type, but the actual KD,app values and statistical comparisons are not provided. The claim of a "common molecular phenotype" is based on only three mutations, and the text does not discuss whether these mutations are representative of the broader spectrum of ID mutations. The mechanistic link between reduced RNA/non-methylated DNA binding and Rett syndrome pathogenesis is speculative. The text does not address how a 2-4 fold reduction in RNA binding affinity translates to a disease phenotype, particularly given the high abundance of MECP2 in neurons.
- **Why it matters** The disease relevance of the findings depends on establishing a clear link between the biochemical phenotype of the mutations and the clinical phenotype. Without quantitative data and a discussion of the physiological threshold for MECP2 function, the claim that this decoupling provides a molecular etiology for Rett syndrome is not fully supported.
- **Resolution test** Provide the complete Table 1 with KD,app values, errors, and statistical comparisons for all constructs and ligands. Discuss the relationship between the magnitude of the binding defects and the clinical severity of the mutations. Consider whether additional ID mutations should be tested to establish a generalizable phenotype.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Experimental design and controls
- **Claim pointer** The authors claim that the isolated ID shows weak micromolar affinity to both methylated and non-methylated DNA with little preference for methylation, and that the MBP tag does not interact with nucleic acids
- **Evidence pointer** Results section "Synergy Between the ID and MBD Drives High-Affinity DNA Binding by MECP2"; Fig. S3 (not provided)
- **Concern** The isolated ID was expressed as an MBP fusion to overcome solubility issues. The text states that MBP alone does not interact with nucleic acids, but the control data are only referenced as Fig. S3. The text does not describe how the MBP-ID fusion was used in binding assays, whether the MBP tag was cleaved for any experiments, or whether the MBP tag could influence the binding properties of the ID. The micromolar affinity of the isolated ID is presented without discussion of whether this represents a specific or non-specific interaction.
- **Why it matters** The interpretation of the ID's contribution to the integrated module depends on accurate characterization of the isolated domain. If the MBP tag influences ID behavior, the conclusions about the ID's intrinsic binding properties could be compromised.
- **Resolution test** Provide the MBP control binding data, describe whether any experiments were performed with cleaved ID, and discuss the potential influence of the MBP tag on ID structure and binding.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and completeness
- **Affected element** Methods section
- **Evidence pointer** Methods section "Fluorescent Anisotropy Binding Assay for KD,app Determination"
- **Issue** The methods describe the binding assay but do not specify the concentration range of protein used, the number of replicates, or the statistical methods for comparing KD,app values. The fitting equations are referenced but not shown.
- **Required correction** Provide the full details of the binding assay including protein concentration ranges, replicate numbers, and the specific statistical tests used for comparisons.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Interpretation and speculation
- **Affected element** Discussion section
- **Evidence pointer** Discussion section, final paragraph
- **Issue** The discussion speculates that ID mutations and disrupted RNA interaction may cause "hyperstability of MECP2 on chromatin" and affect "neural cell fate transitions." This is presented without supporting data or a clear mechanistic model connecting the biochemical findings to chromatin dynamics.
- **Required correction** Either provide supporting evidence or clearly label this as speculation and suggest specific experiments that could test this hypothesis.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "Molecular Dissection of the MECP2 Intervening Domain (ID)"
- **Evidence pointer** Results section, first paragraph; Fig. 1A-B (not provided)
- **Issue** The text references ClinVar mutations and evolutionary conservation but does not provide the actual alignment data or a comprehensive list of ID mutations. The statement that many mutations are "classified as variants of unknown significance" is not quantified.
- **Required correction** Provide the sequence alignment figure and a table of ID mutations with their ClinVar classifications to support the claims about conservation and disease association.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods section "Oligonucleotide preparation"
- **Evidence pointer** Methods section, oligonucleotide preparation
- **Issue** The methods describe RNA folding by snap cooling but do not specify how the RNA secondary structures were verified or predicted. The text mentions UNAfold predictions for Rncr3_2 and Rncr3_3 but does not provide the predicted structures.
- **Required correction** Provide the predicted secondary structures for all RNA ligands or reference a figure showing these structures.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: The 35-fold affinity enhancement claim requires the actual binding data and statistical comparisons
  - R1-M2: The competitive binding model requires the competition curves and IC50 values
  - R1-M3: The mutation phenotype claims require the complete Table 1 with statistical analysis
  - R1-M4: The MBP control data and the characterization of the isolated ID require verification

- **Assessment against Nature-style criteria**
  - **Originality**: The proposed integrated MBD-ID model challenges the established domain segregation paradigm for MECP2 and offers a new framework for understanding how a single protein achieves dual nucleic acid specificity. This represents a conceptual advance, though the idea of integrated nucleic acid binding modules is not entirely novel in the field of RNA-binding proteins.
  - **Scientific importance**: The work has significant implications for understanding MECP2 function and Rett syndrome pathogenesis. The potential link between ID mutations and altered RNA binding could provide a new mechanistic explanation for disease. The findings may also inform therapeutic development, particularly for the MiniGene construct in clinical trials.
  - **Interdisciplinary readership**: The work bridges structural biology, biophysics, and neurogenetics. The findings would be of interest to researchers in chromatin biology, RNA biology, and neurodevelopmental disorders. The clinical relevance to Rett syndrome broadens the potential audience.
  - **Technical soundness**: The experimental approach is logical and the methods are generally appropriate. However, the absence of the actual data prevents full assessment of technical quality. The reliance on a single biophysical technique (fluorescent anisotropy) for most binding measurements, with EMSA used for only one RNA ligand, is a limitation. The lack of structural data to support the proposed competitive interface is a gap.
  - **Readability for nonspecialists**: The manuscript is generally well-written and accessible. The key concepts are explained clearly, and the progression from domain dissection to disease mutations is logical. However, some sections assume familiarity with biophysical binding assays and the significance of specific KD,app values may not be immediately clear to nonspecialists.

- **Recommendation posture** Supportive if technical concerns are resolved. The central hypothesis is interesting and potentially important, but the current manuscript does not provide sufficient data for independent verification of the key claims. The authors should provide the complete binding data, statistical analyses, and competition experiments. The manuscript would be strengthened by additional structural or biophysical evidence supporting the proposed competitive interface and by a more thorough discussion of the physiological relevance of the observed binding affinities.

## Risk / unsupported claims
- The claim that the MBD-ID module is "necessary and sufficient" for nucleic acid binding of full-length MECP2 is not fully supported without direct quantitative comparison of all constructs
- The claim that RNA binding "precludes" DNA binding is not supported by mechanistic evidence distinguishing steric from allosteric competition
- The claim that the identified mutations provide "a potential molecular etiology of Rett syndrome" is speculative and not directly tested in any cellular or in vivo system
- The claim that the MiniGene exhibits "diminished RNA binding" is presented without the actual binding data for this construct
- The physiological relevance of the observed binding affinities and the 2-4 fold reductions in mutant binding is not established
- The statement that the ID is "intrinsically disordered" is referenced but not experimentally demonstrated in this study
- The claim of "promiscuous" RNA binding is based on a limited set of RNA ligands and may not be generalizable