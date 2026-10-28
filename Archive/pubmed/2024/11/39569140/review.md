## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results and discussion, and materials and methods
- **Assessment boundary** Scientific claims, experimental design, evidence quality, and internal consistency based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors propose that Chlamydia plasmid-encoded protein Pgp2 is a replication initiator, identified via AlphaFold structural prediction and DALI homology search, and that a unique β-hairpin motif (residues 108–118) is conserved across Chlamydia species and essential for plasmid transformation, presumably via iteron binding
- **Visible evidence base** AlphaFold structural predictions, DALI search results, sequence alignments, plasmid construction and transformation experiments, fluorescence microscopy
- **Missing materials affecting confidence** No experimental validation of direct DNA binding (e.g., electrophoretic mobility shift assay, surface plasmon resonance, or chromatin immunoprecipitation); no replication origin binding assays; no complementation or rescue experiments; no quantification of transformation efficiency; no statistical analysis; no raw data or uncropped images; no negative controls for transformation beyond absence of fluorescence

## Reviewer
- **Overall assessment** The manuscript presents a plausible structural hypothesis linking Pgp2 to plasmid replication initiation, supported by computational predictions and a single functional assay (transformation failure upon β-hairpin deletion). However, the evidence falls short of establishing Pgp2 as a bona fide replication initiator or demonstrating that the β-hairpin mediates iteron binding. The central claim of iteron-binding is inferred but never directly tested. The transformation failure could result from multiple causes unrelated to replication initiation, including protein misfolding, plasmid instability, or polar effects on downstream genes. The manuscript would benefit from direct biochemical and genetic evidence.
- **Who would be interested in the results, and why** Researchers studying Chlamydia biology, plasmid replication mechanisms, and obligate intracellular bacterial pathogenesis. The work may also interest structural biologists using AlphaFold for functional annotation of uncharacterized proteins, and those studying iteron-based plasmid replication systems across bacterial species.
- **Major strengths** The use of AlphaFold to generate a testable structural hypothesis for an uncharacterized protein is timely and methodologically sound. The identification of a conserved β-hairpin across all Chlamydia species adds evolutionary significance. The transformation assay, while limited, provides a clear phenotypic readout. The manuscript is clearly written and the figures are logically organized.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (no direct iteron-binding evidence), R1-M2 (transformation failure not definitive for replication initiator function), R1-M3 (inconsistent deletion nomenclature), R1-M4 (no complementation or rescue)
- **Assessment against Nature-style criteria** Originality: moderate. The application of AlphaFold to a previously uncharacterized plasmid protein is novel, but the conceptual framework (plasmid replication initiators with iteron binding) is well established. Scientific importance: moderate. Understanding chlamydial plasmid replication could inform therapeutic strategies, but the current evidence does not yet elevate this to a paradigm-shifting finding. Interdisciplinary readership: limited. The work will primarily interest Chlamydia and plasmid biology specialists. Technical soundness: the computational predictions are sound, but the experimental validation is incomplete and does not yet support the central claims. Readability for nonspecialists: the manuscript is generally accessible, though some structural biology terminology may require background knowledge.
- **Recommendation posture** Currently not established from the provided evidence. The structural predictions are intriguing, but the functional evidence is insufficient to support the claim that Pgp2 is a replication initiator with a β-hairpin necessary for iteron binding. Direct DNA-binding assays and genetic complementation are required.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for central claim
- **Claim pointer** The abstract and conclusion state that the β-hairpin motif plays "a critical role in binding to its cognate iteron sequences in the replication origin of the chlamydial plasmid"
- **Evidence pointer** Results and Discussion, "Requirement of the β-hairpin motif for Pgp2 activity"; Figure 4
- **Concern** The manuscript claims that the β-hairpin is necessary for iteron binding, but no experiment directly tests DNA binding. The only functional assay is transformation failure, which does not demonstrate a binding defect. The authors speculate that positively charged residues in the β-hairpin "likely facilitate interactions with the negatively charged iteron DNA," but this is presented without supporting biochemical data.
- **Why it matters** The central mechanistic claim of the paper is iteron binding. Without direct evidence, the conclusion that Pgp2 is a replication initiator that binds iterons is unsupported. Transformation failure could be due to protein instability, improper folding, or polar effects on other plasmid genes.
- **Resolution test** Perform electrophoretic mobility shift assays or surface plasmon resonance with purified Pgp2 (wild-type and β-hairpin deletion mutant) against predicted iteron sequences from the chlamydial plasmid origin. Alternatively, use chromatin immunoprecipitation to demonstrate in vivo binding. Show that the wild-type protein binds specifically to iteron DNA and that the mutant does not.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional evidence for replication initiator role
- **Claim pointer** The manuscript concludes that "Pgp2 is a DNA replication initiator" based on structural homology and transformation failure of the deletion mutant
- **Evidence pointer** Results and Discussion, "Prediction of Pgp2 as a replication initiator" and "Requirement of the β-hairpin motif for Pgp2 activity"; Figure 4
- **Concern** The structural homology to known replication initiators is suggestive but not definitive. The transformation failure of the β-hairpin deletion mutant is consistent with a role in replication, but it does not establish that Pgp2 initiates replication. The mutant plasmid could fail to transform for reasons unrelated to replication initiation, such as reduced plasmid copy number, segregation defects, or gene expression changes. No complementation experiment with a wild-type copy of pgp2 in trans is shown.
- **Why it matters** Establishing Pgp2 as a replication initiator requires evidence that it acts at the origin to initiate DNA replication. Transformation failure alone is insufficient. Without complementation or rescue, the phenotype cannot be unambiguously attributed to Pgp2 function.
- **Resolution test** Complement the Δ108–118 mutant with a wild-type copy of pgp2 expressed from an inducible promoter and show restoration of transformation. Additionally, perform a replication initiation assay, such as measuring plasmid copy number or origin-specific replication intermediates in the presence and absence of functional Pgp2.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Internal consistency
- **Claim pointer** The abstract and results state the deletion removes "the 11 amino acids constituting the β-hairpin motif," and the mutant is named Pgp2Δ108–118; however, the results section also refers to "Pgp2Δ111–118" in the transformation experiment description
- **Evidence pointer** Abstract; Results and Discussion, "Requirement of the β-hairpin motif for Pgp2 activity"; Figure 4
- **Concern** The manuscript inconsistently refers to the deletion mutant as both Pgp2Δ108–118 and Pgp2Δ111–118. The abstract and conclusion use Δ108–118, while the transformation results section uses Δ111–118. This inconsistency creates confusion about which residues were actually deleted and undermines the precision of the reported experiment.
- **Why it matters** Accurate reporting of mutant constructs is essential for reproducibility. The discrepancy could reflect an error in the manuscript or a genuine difference in the constructs used, which would affect interpretation of the results.
- **Resolution test** Clarify the exact deleted residues and ensure consistent nomenclature throughout the manuscript. Verify the construct sequence and report the correct deletion boundaries in all sections and figures.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Experimental controls
- **Claim pointer** The transformation experiments show that pGFP::SW2 produces transformants by passage 2, while pGFP::SW2-pgp2Δ108–118 produces none by passage 5
- **Evidence pointer** Results and Discussion, "Requirement of the β-hairpin motif for Pgp2 activity"; Figure 4D, E
- **Concern** The transformation assay lacks a positive control for the mutant plasmid's integrity and expression. It is not shown that the mutant plasmid is stably maintained or that Pgp2Δ108–118 protein is expressed at levels comparable to wild-type. The absence of transformants could be due to plasmid degradation, poor transformation efficiency, or failure of the mutant protein to fold properly, rather than a specific defect in replication initiation.
- **Why it matters** Without controls demonstrating that the mutant plasmid and protein are otherwise functional, the transformation failure cannot be attributed specifically to the loss of the β-hairpin's proposed function.
- **Resolution test** Include a control plasmid with a neutral deletion or a point mutation in a non-functional region to show that the transformation system works with modified plasmids. Confirm expression of Pgp2Δ108–118 by western blot. Verify plasmid integrity in transformed E. coli and in Chlamydia by sequencing or PCR.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of structural analysis
- **Affected element** Results and Discussion, "Prediction of Pgp2 as a replication initiator"
- **Evidence pointer** Table 1; Figure 1
- **Issue** The manuscript reports RMSD values and Z-scores for structural matches but does not provide the alignment coverage or the number of aligned residues. This information is important for assessing the significance of the structural similarity.
- **Required correction** Report the percentage of Pgp2 residues aligned and the number of aligned residues for each structural match in Table 1 or the text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Materials and Methods, "Three-dimensional structure prediction"
- **Evidence pointer** Location not provided
- **Issue** The methods state that "the online AlphaFold 3 servers" were used, but no version, parameters, or access date are provided. This limits reproducibility.
- **Required correction** Specify the AlphaFold version, any relevant parameters, and the date of access. If multiple models were generated, describe the selection criteria for the "top-ranked" model.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of structural conservation
- **Affected element** Results and Discussion, "Identification of a conserved β-hairpin motif in Pgp2 of Chlamydia species"
- **Evidence pointer** Figure 3
- **Issue** The sequence alignment shows conservation of the β-hairpin across Chlamydia species, but the manuscript does not discuss whether the flanking regions or the overall fold are also conserved. This would help determine whether the β-hairpin is an isolated conserved element or part of a larger conserved domain.
- **Required correction** Briefly describe the overall conservation of Pgp2 across species and place the β-hairpin conservation in that context.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 4D, E
- **Evidence pointer** Location not provided
- **Issue** The representative microscopy images are described but not shown in the text. The manuscript would benefit from including the images or a more detailed description of the fluorescence signal and cell morphology.
- **Required correction** Include the microscopy images or provide a more detailed description of the observed phenotypes, including the number of fields examined and the proportion of cells showing fluorescence.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Location not provided
- **Issue** The introduction states that Pgp1 is predicted to function as a DnaB helicase, but no citation is provided for this prediction. Similarly, the roles of Pgp5–8 are referenced without citations.
- **Required correction** Add appropriate citations for the predicted functions of Pgp1, Pgp5, Pgp6, Pgp7, and Pgp8.

## Risk / unsupported claims
- The claim that Pgp2 binds to iteron sequences is unsupported by direct experimental evidence; it is inferred from structural homology and transformation failure
- The claim that the β-hairpin motif is "necessary for Pgp2's activity" is only supported by a single transformation assay with no complementation or rescue
- The claim that Pgp2 is a "replication initiator" is based on structural similarity alone and is not functionally validated
- The statement that the β-hairpin deletion "did not alter the overall structure of Pgp2" is based on AlphaFold prediction of the mutant, which is not experimentally verified
- The transformation failure of the mutant plasmid is not quantitatively assessed; no transformation efficiency or statistical comparison is provided
- The manuscript does not demonstrate that the mutant plasmid is stably maintained or that the mutant protein is expressed, leaving alternative explanations for the observed phenotype unexplored