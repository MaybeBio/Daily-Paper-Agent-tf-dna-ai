## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends not provided)
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided text
- **Shared manuscript claim summary** The authors investigate the molecular basis for divergence in co-transcription factor (Pho2) dependence between two Pho4 orthologs in yeast. They propose and test two non-mutually exclusive models: enhanced activity and autoinhibition. Through chimeric protein analysis, they identify three key differences: DNA binding affinity, presence of two activation enhancer domains (AEDs) in CgPho4, and a dual-functional intrinsically disordered region (P2ID) in ScPho4 that both enables Pho2-dependent activation and restricts activity without Pho2.
- **Visible evidence base** Abstract, Introduction, Results (narrative), Discussion, Methods (partial), Data availability statements
- **Missing materials affecting confidence** Figures and figure legends, supplementary figures, tables (including Table 1 and Table 2), source data files, statistical analysis outputs, full methods details for some assays

## Reviewer
- **Overall assessment** This manuscript addresses an important and underexplored question in eukaryotic gene regulation: how transcription factor interdependence evolves. The authors use a natural comparative system (S. cerevisiae vs C. glabrata Pho4) and a systematic chimeric approach to dissect the molecular determinants of Pho2 dependence. The finding that intrinsically disordered regions, rather than the DNA binding domain, are the primary drivers of divergence in co-TF dependence is novel and significant. The identification of activation enhancer domains (AEDs) that boost AD activity without independent activation capacity is an interesting concept. However, the manuscript as presented has several limitations: key data are not visible (figures, tables), some claims appear to extend beyond what the described experiments can support, and the mechanistic depth for how AEDs function remains speculative. The chimeric approach is powerful but the interpretation of negative results (e.g., DBD swaps) requires more careful consideration of potential confounding factors such as protein stability or folding.
- **Who would be interested in the results, and why** Researchers studying eukaryotic transcription regulation, particularly those interested in combinatorial control, transcription factor evolution, intrinsically disordered regions in transcriptional regulation, and yeast phosphate signaling. The work also has relevance for understanding how transcription factor networks rewire during evolution and potentially in disease contexts where TF interdependence is altered.
- **Major strengths** 1) The study addresses a fundamental and understudied question in gene regulation: how TF interdependence evolves. 2) The use of natural variation between two yeast species provides evolutionary relevance. 3) The systematic chimeric approach (50 constructs) is comprehensive and well-designed. 4) The identification of AEDs as a new functional class of regulatory elements within IDRs is conceptually novel. 5) The dual-functional P2ID in ScPho4 that both enables Pho2-dependent activation and mediates autoinhibition is an elegant finding. 6) The authors test two explicit models and find support for both, providing a nuanced view.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** 
- **Assessment against Nature-style criteria** 
- **Recommendation posture** 

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "CgPho4 binds the same consensus motif with a higher affinity compared to ScPho4" and that this contributes to reduced Pho2 dependence.
- **Evidence pointer** Results section "CgPho4 binds the same consensus motif with a higher affinity compared to ScPho4"; Fig. 2D, E; Supplementary Fig. 4
- **Concern** The manuscript reports a 3-4 fold difference in binding affinity (KD = 5.2 nM vs 1.2 nM for ScPho4 and CgPho4, respectively) measured by BLI and confirmed by EMSA. However, the functional significance of this difference is not established. The authors themselves acknowledge in the Discussion that the impact depends on nuclear Pho4 concentration relative to KD. In the chimeric experiments, swapping the DBD from CgPho4 into ScPho4 reduced rather than increased activity, which contradicts the enhanced activity model prediction. The authors attribute this to potential incompatibility, but this explanation is post hoc. The claim that binding affinity contributes to Pho2 independence is therefore not supported by the functional data presented. The authors need to either provide direct evidence that the affinity difference matters under relevant nuclear concentrations or temper this claim.
- **Why it matters** The binding affinity difference is presented as one of three key findings, but the functional data do not support its role in Pho2 dependence. This weakens the overall model and could mislead readers about the relative importance of the three identified differences.
- **Resolution test** The authors should either (a) measure Pho4 nuclear concentrations under relevant conditions and model whether the affinity difference would be physiologically significant, (b) perform experiments with DBD-swapped chimeras at varying Pho4 concentrations to test for affinity-dependent effects, or (c) explicitly reframe the binding affinity finding as a correlative observation without demonstrated functional significance.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic depth
- **Claim pointer** The authors claim that the two AEDs in CgPho4 "boost its activation domain's activity" and that this contributes to reduced Pho2 dependence.
- **Evidence pointer** Results section "CgPho4 encodes two additional Activation Enhancer Domains (AEDs)"; Fig. 3
- **Concern** The mechanism by which AEDs enhance AD activity is not investigated. The authors speculate that AEDs may be "weaker ADs with the same biochemical activities" or may "affect the conformation of the AD," but no experiments distinguish these possibilities. The Y1H assay demonstrates that AEDs enhance activity when fused to an AD, but the molecular mechanism remains entirely unknown. Given that the AEDs are identified as a novel functional class, the manuscript would be substantially strengthened by at least preliminary mechanistic characterization. For example, do AEDs recruit specific coactivators? Do they affect AD conformation? Do they promote interactions with the basal transcription machinery?
- **Why it matters** The novelty of the AED concept depends on understanding what they do. Without mechanistic insight, the finding remains descriptive and the claim that AEDs are a distinct functional class is not fully justified.
- **Resolution test** The authors should perform at least one experiment to probe AED mechanism, such as (a) testing whether AEDs interact with known coactivators (e.g., SAGA, Mediator components) by co-IP, (b) testing whether AEDs affect AD conformation using limited proteolysis or FRET, or (c) testing whether AEDs function by recruiting general transcription factors using a reconstituted in vitro transcription assay.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design
- **Claim pointer** The authors claim that the P2ID in ScPho4 "both allows for enhanced activity with Pho2 and inhibits activity without Pho2" and that these functions are "encoded by physically separate parts."
- **Evidence pointer** Results section "A double-edged sword"; Fig. 6
- **Concern** The chimeric analysis identifies the P2ID as a key determinant of Pho2 dependence, but the experiments described do not clearly separate the two proposed functions (Pho2 interaction vs. autoinhibition). The authors state that the first half of P2ID interacts with Pho2 and the second half limits activity without Pho2, but the data supporting this separation are not fully described in the text. Specifically, the Y2H assay (Fig. 6D) only tests physical interaction with Pho2, not whether this interaction is required for the activity enhancement. The autoinhibition function is inferred from reduced activity without Pho2, but alternative explanations (e.g., reduced protein stability, altered subcellular localization) are not excluded. The authors should provide direct evidence that the second half of P2ID mediates autoinhibition, for example by showing that deletion of this region increases activity without Pho2 in the absence of any Pho2 interaction.
- **Why it matters** The dual-function P2ID is a central finding of the paper. If the two functions are not cleanly separated, the model becomes less compelling and the evolutionary interpretation (that these functions can evolve independently) is weakened.
- **Resolution test** The authors should perform additional experiments to directly test autoinhibition, such as (a) measuring activity of ScPho4 with the second half of P2ID deleted in the absence of Pho2, (b) testing whether the second half of P2ID can inhibit a heterologous AD when fused in cis, or (c) using NMR or other biophysical methods to detect intramolecular interactions between P2ID and the AD.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors suggest that "IDR divergence drives TF interdependence evolution" and that this may be a general mechanism.
- **Evidence pointer** Discussion section
- **Concern** The study examines only two Pho4 orthologs. While the authors mention preliminary analyses of eight Pho4 orthologs (Supplementary Fig. 8), these data are not shown in the manuscript text and the analysis is described as "preliminary." The claim that IDR divergence is a general mechanism for TF interdependence evolution requires broader comparative analysis. The authors should either present the eight-ortholog analysis in the main text or temper the generalizability claim.
- **Why it matters** The broader significance of the work depends on whether the findings extend beyond the specific Pho4/Pho2 pair. If the mechanism is idiosyncratic to this system, the impact is substantially reduced.
- **Resolution test** The authors should present the eight-ortholog analysis with appropriate statistical tests, or clearly frame the study as a case study with limited generalizability.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that CgPho4 "regulates ∼70 genes" while ScPho4 regulates "∼28 genes," but the basis for these numbers is not explained in the abstract. It is unclear whether these are direct targets, indirect targets, or genes whose expression changes upon Pho4 perturbation.
- **Required correction** Clarify in the abstract what these gene numbers represent (e.g., "direct binding targets" or "differentially expressed genes").

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Fig. 2D, E
- **Evidence pointer** Results section "CgPho4 binds the same consensus motif with a higher affinity compared to ScPho4"
- **Issue** The manuscript reports a Student's t-test on log-transformed KD values with P < 0.01, but the number of replicates and the variance are not reported in the text. The EMSA confirmation is mentioned but the data are not shown in the text.
- **Required correction** Report the number of independent replicates, the mean and standard deviation for each KD measurement, and show the EMSA data in the main text or supplementary.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Fig. 5D
- **Evidence pointer** Results section "The two Activation Enhancer Domains (AEDs) in CgPho4 increased the activity of the chimeric TFs"
- **Issue** The linear model for epistasis analysis is described, but the results are not presented in the text. The reader cannot assess which interaction terms were significant or their magnitudes.
- **Required correction** Report the model coefficients, standard errors, and P-values for the main effects and interaction terms in the text or a table.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Y2H assay
- **Evidence pointer** Results section "A double-edged sword"; Fig. 6D
- **Issue** The Y2H assay is described in a single sentence. The specific regions of Pho4 and Pho2 used, the controls, and the quantification method are not described.
- **Required correction** Provide a more detailed description of the Y2H assay in the Methods section, including the constructs used, the interaction detection method, and the positive/negative controls.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Fig. 6C
- **Evidence pointer** Results section "A double-edged sword"
- **Issue** The rescue experiment (inserting P2ID:Sc between P2ID:Cg and DBD:Sc) is described as supporting the hypothesis that DBD:Sc requires P2ID:Sc and Pho2 to function. However, the interpretation assumes that the inserted P2ID:Sc functions identically in the chimeric context as in the native context. This assumption is not tested.
- **Required correction** Acknowledge this limitation and consider testing whether the inserted P2ID:Sc physically interacts with Pho2 in the chimeric context.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The comparison to the ABL-BCR fusion in chronic myeloid leukemia is interesting but somewhat tangential. The analogy is not developed and may distract from the main findings.
- **Required correction** Either develop the analogy more fully or remove it.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section
- **Issue** The Methods section describes the BLI and EMSA experiments but does not provide sufficient detail for replication. For example, the protein concentrations used, the buffer conditions, and the data analysis parameters are not fully specified.
- **Required correction** Provide complete experimental details for all assays, including concentrations, buffers, temperatures, and analysis parameters.

## Risk / unsupported claims
- The claim that the 3-4 fold difference in DNA binding affinity between CgPho4 and ScPho4 contributes to reduced Pho2 dependence is not supported by the functional data (chimeric DBD swaps showed reduced activity, not increased).
- The claim that the two AEDs in CgPho4 are a novel functional class of regulatory elements is not fully supported without mechanistic characterization.
- The claim that the P2ID in ScPho4 has separable functions (Pho2 interaction vs. autoinhibition) is inferred from chimeric analysis but not directly demonstrated.
- The claim that IDR divergence is a general mechanism for TF interdependence evolution is based on only two orthologs, with preliminary data on eight orthologs not shown.
- The functional significance of the binding affinity difference is acknowledged by the authors to depend on nuclear Pho4 concentration, but this concentration is not measured or estimated.
- The statement that "CgPho4 has reduced Pho2 dependence and regulates ∼70 genes" implies a causal relationship between Pho2 dependence and target gene number, but this correlation is not rigorously established.