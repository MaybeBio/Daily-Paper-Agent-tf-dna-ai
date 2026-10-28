## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplemental figure legends. No figures or tables were provided for direct inspection.
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency as presented in the text. Statistical analyses and raw data were not independently verifiable from the provided material.
- **Shared manuscript claim summary** The authors propose that the non-catalytic subunit of human DNA polymerase ε (POLE2) is a general receptor for Asn-Pro-Phe (NPF) short linear motifs, expanding the known repertoire of NPF-binding proteins beyond EH domains. They support this with native holdup assays, fluorescence polarization, mutagenesis, AlphaFold predictions, and proximity labeling, and suggest that POLE2 links DNA replication with other nuclear processes through NPF-mediated interactions.
- **Visible evidence base** Text descriptions of results, methods, and supplemental figure legends. No primary figures, tables, or supplementary data files were available for direct examination.
- **Missing materials affecting confidence** All figures, tables, and supplementary data files. Raw mass spectrometry data, statistical analysis outputs, and detailed experimental replicates were not accessible. This limits verification of quantitative claims and the strength of statistical support.

## Reviewer
- **Overall assessment** The manuscript addresses a timely and important question in SLiM biology, namely the identification of novel NPF motif receptors and the determinants of specificity between distinct NPF-binding proteins. The combination of unbiased proteomic screening, quantitative binding assays, and structural prediction is methodologically strong and appropriate for the question. The claim that POLE2 is a general NPF receptor is plausible and supported by multiple lines of evidence, though the lack of direct structural validation and the limited in vivo functional data temper the strength of the conclusions. The work is likely to be of interest to the SLiM, DNA replication, and interactomics communities, but several technical and interpretive issues need to be resolved before the case is fully established.
- **Who would be interested in the results, and why** Researchers studying short linear motifs and their binding partners, particularly those interested in motif degeneracy and cross-reactivity between different receptor families. The DNA replication and replisome assembly fields will also be interested, as the work proposes new protein-protein interactions at the replication fork. Finally, the broader interactomics community may find the native holdup methodology and its application to SLiM-mediated interactions of value.
- **Major strengths** The study combines an unbiased, quantitative screening approach with targeted biochemical validation, which is a robust strategy for identifying novel SLiM receptors. The use of AlphaFold predictions to guide mutagenesis is a modern and appropriate approach. The identification of natural variants that affect NPF binding adds potential translational relevance. The discussion of motif degeneracy and network overlap is conceptually valuable and well contextualized.
- **Major Concerns** The concerns below are listed in detail in the following section.
- **Minor Comments** The minor comments are listed in detail in the following section.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5, R1-M6.
- **Assessment against Nature-style criteria**  
  *Originality*: The finding that POLE2, a non-catalytic polymerase subunit, acts as a general NPF receptor is novel and not predictable from prior literature. The conceptual framing of overlapping SLiM-mediated networks is also original.  
  *Scientific importance*: The work has the potential to reshape understanding of POLE2 function and to expand the known NPF interactome. However, the functional significance of these interactions in cells remains incompletely demonstrated, which limits current importance.  
  *Interdisciplinary readership*: The topic bridges SLiM biology, DNA replication, and interactomics, and should appeal to readers across these fields. The writing is generally accessible.  
  *Technical soundness*: The core methods are appropriate and well described, but several quantitative claims and the interpretation of mutagenesis data require additional support or clarification.  
  *Readability for nonspecialists*: The manuscript is clearly written and the logic is easy to follow, though some sections assume familiarity with SLiM and holdup assay concepts.
- **Recommendation posture** Supportive if technical concerns are resolved. The central claim is plausible and well supported in its broad strokes, but the quantitative rigor, the interpretation of mutagenesis data, and the in vivo relevance need to be strengthened before the case is fully established.

## Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative claim
- **Claim pointer** The authors state that POLE2 binds NPF-containing peptides with micromolar affinities, and that the apparent affinity of the POLE2-POLE interaction is between 0.1 and 0.3 nM.
- **Evidence pointer** Results section, Figure 1I-K, Figure 5B, Table S2; location not provided
- **Concern** The manuscript reports a wide range of binding affinities across different experiments, from 16 μM for the isolated DONSON peptide in fluorescence polarization to 0.28 μM for the same interaction in native holdup with cellular POLE2, and 0.1-0.3 nM for the POLE2-POLE interaction estimated from indirect measurements. The authors attribute the discrepancy between in vitro and cellular affinities to destabilization of POLE2 or the influence of the MBP tag, but this explanation is not directly tested. The estimation of the POLE2-POLE affinity relies on assumptions about the independence of the POLE2-NPF and POLE2-POLE interactions that are not experimentally validated.
- **Why it matters** The quantitative claims are central to the paper's message that POLE2 is a physiologically relevant NPF receptor. If the affinity estimates are unreliable, the biological significance of these interactions is uncertain.
- **Resolution test** Provide direct measurements of POLE2-POLE affinity using purified components, and test whether the MBP tag or POLE2 destabilization quantitatively accounts for the observed differences between in vitro and cellular affinities. Alternatively, temper the quantitative claims to reflect the uncertainty.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural validation
- **Claim pointer** The authors state that NPF motifs interact with a shallow pocket near the POLE2 C-terminus, and that Y513, E520, and S522 are key coordinating residues.
- **Evidence pointer** Results section, Figure 2; location not provided
- **Concern** The structural model is based entirely on AlphaFold 3 predictions. While AlphaFold is a powerful tool, it is not a substitute for experimental structural validation, especially for a claim about a specific binding interface. The mutagenesis data are consistent with the model, but the interpretation of the Y311F mutation as showing that Y311 is not contributing via its hydroxy group is based on a single point mutation and does not exclude a role for the aromatic ring or other interactions.
- **Why it matters** The proposed binding interface is a key mechanistic claim. If the model is incorrect, the interpretation of the mutagenesis data and the design of future experiments would be compromised.
- **Resolution test** Provide experimental structural data, such as X-ray crystallography, NMR, or cryo-EM, or at minimum use cross-linking or hydrogen-deuterium exchange to validate the predicted interface. Alternatively, present the AlphaFold model as a hypothesis and clearly state that it is not experimentally validated.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** In vivo relevance
- **Claim pointer** The authors state that POLE2 can recruit various NPF-bearing partners involved in replication, DNA repair, and transcription regulation, and that these interactions are functionally important.
- **Evidence pointer** Results section, Figure 6; location not provided
- **Concern** The in vivo relevance of the identified interactions is supported only by proximity labeling (BioID) and by the presence of NPF motifs in the identified partners. No functional experiments are presented to show that these interactions are required for replication, repair, or transcription in cells. The BioID data show proximity, not direct binding, and the overlap between BioID and nHoldup hits is limited to three proteins.
- **Why it matters** The claim that POLE2 is a central hub linking replication with other processes is a major conclusion of the paper. Without functional validation, this remains speculative.
- **Resolution test** Perform functional experiments, such as knockdown or mutation of the NPF motifs in the identified partners, and assess the impact on replication, repair, or transcription. Alternatively, temper the conclusions to state that these are potential interactions that require functional validation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Specificity determinants
- **Claim pointer** The authors state that they determined the key specificity determinants of NPF motifs between POLE2 and EPS15, and that the NPF motif of DONSON can be converted into an EPS15 binder by multimerization.
- **Evidence pointer** Results section, Figure 5; location not provided
- **Concern** The chimera experiments are described only in text, and the data are not shown in the provided material. The conclusion that multimerization is sufficient to convert a POLE2-specific motif into an EPS15 binder is based on a single set of experiments with a triple-repeat construct. The authors do not test whether the individual flanking regions of the SYNJ1 NPF motifs contribute to EPS15 binding in a sequence-specific manner.
- **Why it matters** The specificity determinants are a key conceptual contribution of the paper. If the chimera experiments are not robust, the conclusion that specificity is primarily determined by valency rather than sequence may be overstated.
- **Resolution test** Provide the full data for the chimera experiments, including dose-response curves and statistical analysis. Test additional chimeras with different flanking regions to confirm that the effect is general.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors state that 70 proteins showed significant binding to POLE2 in the nHoldup screen, and that 17 of these contain NPF motifs.
- **Evidence pointer** Results section, Figure 3A-B, Table S1; location not provided
- **Concern** The statistical threshold for significance in the nHoldup screen is described as a 2σ threshold, but the details of the statistical model, multiple testing correction, and the false discovery rate are not provided. The enrichment of NPF motifs in the identified partners is stated to be >10-fold, but the calculation is not shown.
- **Why it matters** The identification of 70 partners is a key result. If the statistical threshold is not rigorous, the list of partners may contain false positives, which would affect the downstream analysis and conclusions.
- **Resolution test** Provide the full statistical analysis, including the distribution of depletion values, the threshold selection, and the false discovery rate. Show the calculation of the NPF enrichment and its confidence interval.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Indirect binding estimation
- **Claim pointer** The authors estimate the POLE2-POLE dissociation constant to be 0.1-0.3 nM based on indirect measurements from nHoldup experiments.
- **Evidence pointer** Results section, "Estimating affinities of indirectly captured complexes"; location not provided
- **Concern** The estimation relies on the assumption that the POLE2-POLE interaction is independent of the POLE2-NPF interaction, and that the concentrations of POLE and POLE2 in the extract are known and equal. These assumptions are not tested, and the resulting affinity estimate is likely to be highly uncertain.
- **Why it matters** The claim that POLE2 and POLE form a very high-affinity complex is used to support the idea that POLE2 is stable in the cell. If the estimate is unreliable, this conclusion is weakened.
- **Resolution test** Measure the POLE2-POLE affinity directly using purified proteins and a biophysical method such as surface plasmon resonance or isothermal titration calorimetry.

## Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states that POLE2 "selectively binds diverse NPF-containing peptides," but the term "selectively" is not defined. Given the later discussion of cross-reactivity with EH domains, the selectivity of POLE2 is relative, not absolute.
- **Required correction** Clarify what is meant by "selectively" in the context of the results, or rephrase to avoid ambiguity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Results section, "Identification of POLE/POLE2 as a recurring interaction partner"
- **Evidence pointer** Results section, Figure 1C-H; location not provided
- **Issue** The text states that the SYNJ1 NPF-motif rich region showed significant interaction with EH proteins, but the depletion of SYNJ1 itself is not discussed in the context of POLE2 binding. The relationship between the SYNJ1 peptide and the full-length SYNJ1 protein is not fully clarified.
- **Required correction** Clarify whether the SYNJ1 peptide used in the nHoldup experiments represents the full NPF-rich region and how this relates to the full-length protein binding data.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Methods, "Single-point and titration nHoldup experiments"
- **Evidence pointer** Methods section; location not provided
- **Issue** The description of the nHoldup assay mentions that the bait concentration was measured experimentally for protein baits, but the method for determining the concentration of peptide baits is not described.
- **Required correction** Provide the method for determining peptide bait concentration, or state that it was estimated.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results section, "In vivo proximity interactome of POLE2"
- **Evidence pointer** Results section, Figure 6; location not provided
- **Issue** The BioID data are presented as a list of 26 significant partners, but the full list is not shown in the provided material. The text mentions that only three partners overlap with the nHoldup data, but the significance of this overlap is not discussed.
- **Required correction** Provide the full list of BioID partners and discuss the overlap with nHoldup data in more detail.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, "Motif mediated interactions: distinct networks or coherent interactome"
- **Evidence pointer** Discussion section; location not provided
- **Issue** The discussion of network overlap is conceptually interesting but relies on the assumption that the observed cross-reactivity is biologically relevant. The authors acknowledge this limitation but do not propose specific experiments to test it.
- **Required correction** Suggest specific experiments that could test whether the observed cross-reactivity occurs in cells.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Throughout; location not provided
- **Issue** The term "native holdup" is used throughout, but it is not defined in the text. Readers unfamiliar with the method may be confused.
- **Required correction** Define "native holdup" at first use, or provide a brief description of the method.

## Risk / unsupported claims
- The claim that POLE2 is a "central hub" linking replication with other processes is not supported by functional data and should be considered a hypothesis.
- The estimated POLE2-POLE dissociation constant of 0.1-0.3 nM is based on indirect measurements and unvalidated assumptions; this should be presented as a rough estimate.
- The claim that the NPF motif of DONSON can be converted into an EPS15 binder by multimerization is based on experiments not shown in the provided material.
- The structural model of the POLE2-NPF interaction is based solely on AlphaFold predictions and has not been experimentally validated.
- The statement that NPF motifs are enriched >10-fold in POLE2 partners is not accompanied by the calculation or statistical test.
- The claim that POLE2 exists in a different spatial environment compared to other NPF-binding proteins is based on limited BioID data and requires further validation.