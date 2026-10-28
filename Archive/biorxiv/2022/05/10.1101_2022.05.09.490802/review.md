## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, experimental procedures, and data availability statements.
- **Assessment boundary** Scientific content, technical soundness, logical coherence, and support of claims by presented data. No assessment of formatting, grammar, or journal fit beyond Nature-style criteria.
- **Shared manuscript claim summary** The authors report that human SDE2 contains a SAP domain with an extended C-terminal tail (CTT) that together form a novel extended SAP domain preferentially binding single-stranded DNA. They present an NMR solution structure of this domain, biochemical binding data, and cell-based assays linking the SAP domain to TIM localization at replication forks and fork progression. They propose that this extended SAP domain is conserved in SF3A3 and represents a specialized DNA binding module important for replication fork integrity.
- **Visible evidence base** Figures 1-7, supplementary figures S1-S7, supplementary tables S1-S4, NMR structure deposited as PDB 7N99 and BMRB 30927.
- **Missing materials affecting confidence** No raw NMR spectra or assignment tables are shown in the manuscript. No quantification of Western blots is provided. No statistical details for the SIRF and DNA combing experiments beyond the methods description. No negative control data for the FLIP experiments. No direct binding affinity comparison between full-length SDE2 and the SAP domain alone for ssDNA versus dsDNA using the same assay.

## Reviewer

### Overall assessment
This manuscript presents a structurally and functionally characterized extended SAP domain in SDE2, with evidence for ssDNA binding and a role in replication fork progression via TIM localization. The NMR structure is a valuable contribution, and the identification of a CTT that augments DNA binding is novel. However, several technical concerns weaken the current support for the central claims. The binding affinity data are limited to a single assay with a modest reported Kd, and the functional assays rely heavily on overexpression and knockdown-rescue approaches without clear demonstration of physiological relevance. The link between the in vitro ssDNA binding preference and the in vivo function at replication forks is correlative rather than causal. The conservation argument for SF3A3 is intriguing but not functionally tested. Overall, the work is promising but requires additional experimental support to fully establish the model proposed.

### Who would be interested in the results, and why
Researchers studying DNA replication stress, fork protection complex biology, and genome stability mechanisms would find this work relevant. The structural characterization of a SAP domain variant with an extended binding interface will interest structural biologists studying DNA-protein interactions. The potential connection to SF3A3 and splicing factors may attract investigators studying the interface between RNA processing and DNA damage responses. The work also has relevance for understanding how DNA binding domains evolve and diversify.

### Major strengths
1. The NMR structure of the SDE2 SAP domain is a solid technical achievement and provides the first structural view of this domain in SDE2.
2. The identification of a CTT that contributes to DNA binding is a novel finding that extends the canonical SAP domain concept.
3. The combination of structural, biochemical, and cell-based approaches is commendable and provides multiple lines of evidence.
4. The demonstration that SAP domain mutations affect TIM localization and fork progression links the DNA binding property to a functional outcome.
5. The evolutionary analysis suggesting conservation of the extended SAP in SF3A3 is interesting and potentially impactful.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of binding data
- **Claim pointer** The authors claim that SDE2 SAP preferentially binds ssDNA with a Kd of approximately 1.77 μM, and that the CTT contributes to this binding.
- **Evidence pointer** Figure 2, Figure 3, Figure 5, "location not provided" for raw binding curves
- **Concern** The binding affinity is determined using fluorescence anisotropy with a single DNA substrate and a single protein construct. The reported Kd of 1.77 μM is relatively weak, and no error bars or replicate measurements are shown. The EMSA data are qualitative and do not provide a rigorous comparison of binding affinities between wild-type and mutant proteins. The claim that the CTT "augments" binding is based on deletion mutants, but the quantitative contribution is not clearly established. Additionally, the GST tag on the SAP domain construct could influence binding, and no tag-free protein was tested.
- **Why it matters** The central claim of the paper is that SDE2 SAP is a bona fide ssDNA binding domain with a specific preference. Without rigorous, quantitative binding data with appropriate controls and replicates, this claim is not firmly established. The weak affinity also raises questions about whether this interaction is physiologically relevant.
- **Resolution test** Provide full binding curves with at least three independent replicates for wild-type and mutant proteins, using both tagged and tag-free constructs. Include competition assays with unlabeled ssDNA and dsDNA to demonstrate specificity. Report Kd values with standard deviations and perform statistical comparisons between constructs.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional relevance of SAP domain in cells
- **Claim pointer** The authors claim that the SAP domain is required for SDE2 localization at replication forks and for TIM localization, and that this is necessary for efficient fork progression.
- **Evidence pointer** Figure 1, Figure 7, "location not provided" for quantification details
- **Concern** The functional assays rely on overexpression of wild-type or mutant SDE2 in cells with endogenous SDE2 knocked down. The level of knockdown and the expression levels of the rescue constructs are not clearly documented. The SIRF assay measures proximity between SDE2 and EdU-labeled DNA, but the specificity of this signal is not fully validated. The DNA combing data show shorter replication tracks in the SAP mutant, but the statistical analysis and the number of fibers analyzed are not reported in sufficient detail. The connection between the in vitro ssDNA binding preference and the in vivo function is not directly tested, as no separation-of-function mutants are presented.
- **Why it matters** The physiological relevance of the SAP domain is a key claim. If the overexpression system masks endogenous regulation or if the observed phenotypes are due to non-specific effects of the mutant protein, the conclusions would be weakened. The lack of direct evidence that DNA binding by the SAP domain is what mediates the functional effects leaves a gap in the causal chain.
- **Resolution test** Provide detailed characterization of knockdown efficiency and rescue expression levels. Include a separation-of-function mutant that disrupts DNA binding but preserves protein folding and SDE2-TIM interaction. Perform the SIRF and DNA combing experiments with at least three biological replicates and report the number of cells/fibers analyzed and the statistical tests used.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Structural evidence for the extended SAP domain
- **Claim pointer** The authors claim that the NMR structure reveals a helix-extended loop-helix motif with a CTT that is positioned to contribute to DNA binding.
- **Evidence pointer** Figure 4, Table 1, PDB 7N99
- **Concern** The NMR structure is presented, but the quality of the structure is not fully assessed in the manuscript. The number of distance restraints per residue, the RMSD of the ensemble, and the validation statistics are not shown in the main text. The structural basis for the claim that the CTT contributes to DNA binding is based on chemical shift perturbations, but no structure of the complex with DNA is presented. The docking model is speculative and not experimentally validated.
- **Why it matters** The structural model is central to the claim of an extended DNA binding interface. Without clear evidence of structure quality and without experimental validation of the proposed binding mode, the structural conclusions remain preliminary.
- **Resolution test** Provide a full table of NMR statistics including restraint counts, RMSD values, and Ramachandran analysis. If possible, obtain a structure of the SAP domain in complex with ssDNA, or provide mutagenesis data that directly test the predicted DNA contacts in the CTT.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Conservation and generality of the extended SAP motif
- **Claim pointer** The authors claim that the extended SAP domain is conserved in SF3A3 and may represent a general DNA binding module.
- **Evidence pointer** Figure 6, "location not provided" for sequence alignment details
- **Concern** The sequence alignment showing conservation between SDE2 and SF3A3 is presented, but the functional significance is only tested for SF3A3 chromatin binding. No direct test of whether the SF3A3 SAP domain binds DNA with similar properties is shown. The claim that this is a "unique" extended SAP domain is based on a limited comparison to other SAP-containing proteins.
- **Why it matters** The broader significance of the finding depends on whether this extended SAP domain is a general feature or specific to SDE2 and SF3A3. Without functional data on SF3A3 DNA binding and a more comprehensive phylogenetic analysis, the generality claim is not supported.
- **Resolution test** Perform direct DNA binding assays with the SF3A3 SAP domain, including mutagenesis of the conserved lysine residues. Expand the sequence analysis to include a broader set of SAP-containing proteins and assess whether the CTT is present in other contexts.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1, "location not provided"
- **Issue** The subcellular fractionation data in Figure 1B-C are not quantified. The difference in chromatin localization between wild-type and SAP mutant is stated but not shown with statistical support.
- **Required correction** Provide quantification of Western blots from at least three independent experiments with statistical analysis.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Experimental detail
- **Affected element** DNA substrates used in binding assays
- **Evidence pointer** Figure 2, "location not provided"
- **Issue** The sequences and lengths of the DNA substrates used in EMSA and anisotropy are not described in the main text or methods. The 16-mer used in NMR titration is mentioned but its sequence is not given.
- **Required correction** Include the sequences of all DNA oligonucleotides used in the supplementary tables.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** SIRF and DNA combing data
- **Evidence pointer** Figure 7, "location not provided"
- **Issue** The number of cells analyzed for SIRF and the number of DNA fibers for combing are not reported. The statistical tests used are mentioned in methods but the results are not shown with p-values in the figures.
- **Required correction** Add the number of biological replicates, the number of cells/fibers analyzed, and the p-values to the figure legends.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of NMR data
- **Affected element** Figure 3
- **Evidence pointer** Figure 3, "location not provided"
- **Issue** The chemical shift perturbation data are shown as a bar graph, but the threshold for significance is not defined. It is unclear which residues are considered significantly perturbed.
- **Required correction** Define the significance threshold for chemical shift perturbations and indicate which residues exceed this threshold.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** "location not provided"
- **Issue** The discussion does not address the relatively weak binding affinity of the SAP domain for ssDNA or the lack of a co-crystal structure with DNA.
- **Required correction** Add a paragraph discussing the limitations of the current study and future directions to address them.

### Technical failings that need to be addressed before the case is established
1. Lack of quantitative binding data with replicates and statistical analysis (R1-M1).
2. Insufficient validation of the overexpression/rescue system in functional assays (R1-M2).
3. Incomplete NMR structure validation statistics (R1-M3).
4. No direct functional test of the SF3A3 extended SAP domain DNA binding (R1-M4).

### Assessment against Nature-style criteria
- **Originality** The identification of an extended SAP domain with a CTT contributing to DNA binding is novel and extends the current understanding of SAP domain function. This is a meaningful contribution to the field.
- **Scientific importance** The work addresses a relevant question in DNA replication stress and fork protection. The potential link between SDE2 DNA binding and TIM regulation is important, but the physiological significance is not fully established.
- **Interdisciplinary readership** The work will appeal to structural biologists, DNA replication researchers, and genome stability investigators. The broader cell biology community may find the functional aspects interesting, but the current data are not sufficiently developed to have wide appeal.
- **Technical soundness** The NMR structure determination appears technically sound, but the binding assays and functional experiments have limitations as noted above. The overall technical quality is good but not exceptional.
- **Readability for nonspecialists** The manuscript is generally well-written and accessible. The figures are clear, but some of the methods and data presentation could be improved for a broader audience.

### Recommendation posture
Supportive if technical concerns are resolved. The core finding of an extended SAP domain is interesting and potentially important, but the current evidence does not fully establish the model. The binding data need to be strengthened, the functional assays need better controls, and the structural claims need more validation. If these issues are addressed, the work could make a solid contribution to the field.