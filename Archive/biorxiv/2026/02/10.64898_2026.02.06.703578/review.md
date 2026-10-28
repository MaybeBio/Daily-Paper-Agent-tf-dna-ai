## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, materials and methods, and figure legends (figures themselves not provided)
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency based solely on the provided text
- **Shared manuscript claim summary** The authors propose that pioneer-factor activity of Grainy head (Grh) requires stable chromatin occupancy mediated by both sequence-specific DNA binding and disordered protein domains, and that mitotic retention depends solely on sequence-specific DNA binding
- **Visible evidence base** In vitro EMSA binding assays, ChIP-seq, ATAC-seq, FRAP, single-particle tracking, luciferase reporter assays, and transgenic Drosophila salivary gland imaging
- **Missing materials affecting confidence** Actual figures and supplementary figures, quantitative data values, statistical details, ChIP-seq and ATAC-seq quality metrics, replicate numbers for imaging experiments, and full analysis parameters

## Reviewer
- **Overall assessment** This manuscript addresses an important question in the pioneer transcription factor field: how different protein domains collectively contribute to pioneering activity. The authors use a multi-pronged approach combining biochemistry, genomics, and live imaging to dissect the contributions of the DNA-binding domain and the disordered N-terminus of Grh. The central claim that stable chromatin occupancy requires both sequence-specific binding and disordered domain contributions is well-supported by the combination of assays presented. The separation of mitotic retention from interphase pioneering requirements is a notable conceptual advance. However, several technical concerns regarding quantification, statistical rigor, and the interpretation of imaging data need to be addressed before the conclusions are fully established.
- **Who would be interested in the results, and why** Researchers studying pioneer transcription factors, chromatin biology, gene regulation, and developmental biology. The findings have implications for understanding how transcription factors navigate chromatin barriers and how disordered regions contribute to chromatin interactions. Given the involvement of GRHL proteins in epithelial cancers, the work may also interest cancer biologists studying transcriptional dysregulation.
- **Major strengths** The combination of in vitro and in vivo approaches provides complementary evidence for the role of the N-terminus in stable chromatin occupancy. The use of quantitative live imaging (FRAP and single-particle tracking) adds dynamic information that static assays cannot provide. The cross-species comparison with human GRHL2 strengthens the generalizability of the findings. The clear separation of mitotic retention from interphase pioneering activity is conceptually important.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantification of EMSA data), R1-M2 (ChIP-seq normalization and comparison), R1-M3 (FRAP analysis and immobile fraction interpretation), R1-M4 (SPT statistical analysis)
- **Assessment against Nature-style criteria** Originality: The work provides a systematic dissection of domain contributions to pioneer activity, which is a relatively underexplored area. The finding that disordered regions contribute to stable occupancy through composition-dependent rather than sequence-specific mechanisms is novel. Scientific importance: The results have broad implications for understanding how pioneer factors function and how disordered regions contribute to transcription factor activity. The separation of mitotic retention from interphase pioneering is conceptually significant. Interdisciplinary readership: The work bridges biochemistry, genomics, and imaging, making it relevant to multiple subdisciplines. Technical soundness: The experimental approaches are generally appropriate, but several quantification and statistical issues need resolution. Readability for nonspecialists: The manuscript is generally well-written and accessible, though some sections assume familiarity with specialized techniques.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantification and statistical rigor
- **Claim pointer** The authors state that full-length Grh binds to both free and nucleosomal DNA, and that Grh R806A shows a stronger decrease in binding than Grh C800A,K807A
- **Evidence pointer** Figure 1A-C, Figure 2A-D, Figure S1C, Figure S3A
- **Concern** The EMSA quantification methodology is not described in sufficient detail. The authors state that "the fraction of bound protein was quantified by dividing the shifted band of each respective reaction by the unshifted band from the no protein reaction" but do not specify how many independent experiments were performed for each condition, whether binding curves were generated, or how dissociation constants were calculated. The statement that Grh R806A shows a "stronger decrease" than Grh C800A,K807A appears to be based on visual inspection of gels rather than quantitative comparison with statistical testing.
- **Why it matters** The relative binding affinities of the mutant proteins are central to interpreting whether reduced pioneering activity in cells is due to reduced DNA binding or to loss of other functions. Without rigorous quantification, the distinction between "modest" and "strong" effects cannot be evaluated.
- **Resolution test** Provide quantification from at least three independent EMSA experiments with error bars and statistical tests comparing wild-type and mutant binding affinities. Report dissociation constants or apparent Kd values for each protein on both free and nucleosomal DNA.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data analysis and interpretation
- **Claim pointer** The authors claim that Grh ΔN and Grh R806A have "markedly decreased binding to closed chromatin" and that Grh Scr can open chromatin "albeit not to the degree of wild-type Grh"
- **Evidence pointer** Figure 2E-F, Figure 4C-D, Figure 5B-C
- **Concern** The ChIP-seq and ATAC-seq comparisons between wild-type and mutant proteins are complicated by differences in expression levels. The authors state that mutants were expressed at "levels higher than wild type" but do not describe how ChIP-seq signals were normalized to account for these differences. Without spike-in normalization or other appropriate controls, it is unclear whether reduced ChIP signals at closed chromatin reflect true binding differences or differences in nuclear localization, protein stability, or chromatin accessibility during fixation.
- **Why it matters** The central claim that the N-terminus is required for stable chromatin occupancy in cells depends on the interpretation that reduced ChIP signals at closed chromatin reflect reduced binding rather than reduced protein levels or other artifacts.
- **Resolution test** Describe the normalization strategy for ChIP-seq data in detail. If spike-in normalization was not used, provide evidence that differences in expression levels do not confound the comparison. Consider performing ChIP-seq with normalization to an exogenous spike-in control or using a titration experiment to show that binding differences are not simply due to expression level differences.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Imaging data interpretation
- **Claim pointer** The authors claim that wild-type Grh has a substantial immobile fraction in FRAP experiments, while Grh ΔN recovers faster and more completely, indicating that the N-terminus is required for stable chromatin binding
- **Evidence pointer** Figure 3A-B
- **Concern** The FRAP methodology is not described in sufficient detail. The authors state that "effective bleaching was achieved by point bleaching" but do not specify the size of the bleached region relative to the nucleus, the number of cells analyzed, or how the immobile fraction was calculated. The statement that wild-type Grh "never achieved full recovery within the imaging window, plateauing at 50%" suggests that the immobile fraction is substantial, but it is unclear whether this plateau represents true immobility or simply very slow exchange that would eventually recover on longer timescales.
- **Why it matters** The interpretation that the N-terminus mediates stable chromatin occupancy depends on the FRAP data showing different recovery kinetics between wild-type and mutant proteins. If the immobile fraction is an artifact of the bleaching protocol or imaging window, the conclusion would be weakened.
- **Resolution test** Provide details on the number of cells analyzed, the size of the bleached region, and the method for calculating the immobile fraction. Consider extending the imaging window or performing fluorescence loss in photobleaching (FLIP) experiments to distinguish between true immobility and very slow exchange.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical analysis
- **Claim pointer** The authors claim that Grh ΔN and Grh R806A show "reduced anisotropy" in single-particle tracking, indicating less constrained movement and decreased searching behavior
- **Evidence pointer** Figure 3E
- **Concern** The single-particle tracking analysis uses a three-state hidden Markov model, but the statistical comparison between wild-type and mutant proteins is not described. The authors do not report the number of cells, the number of trajectories analyzed, or the statistical test used to compare the proportions of molecules in each state. The anisotropy analysis is described as being done "as previously described" but the specific parameters and statistical approach are not provided.
- **Why it matters** The claim that the N-terminus supports localized searching behavior depends on the statistical comparison of trajectory properties between wild-type and mutant proteins. Without appropriate statistical analysis, the differences could be due to sampling variation or differences in expression levels.
- **Resolution test** Provide details on the number of cells and trajectories analyzed for each condition, the statistical tests used to compare state proportions and anisotropy values, and the criteria for assigning molecules to each state.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Experimental design
- **Affected element** Luciferase reporter assays
- **Evidence pointer** Figure 4B, Figure S4B
- **Issue** The luciferase reporter assays use the hgo promoter, but the authors do not specify whether this promoter contains a single Grh binding site or multiple sites, and whether the context of the binding site (e.g., nucleosome positioning) is relevant to the interpretation.
- **Required correction** Provide details on the hgo promoter construct, including the number and position of Grh binding sites, and discuss whether the reporter assay reflects pioneering activity or simply transcriptional activation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure S5A
- **Evidence pointer** Figure S5A
- **Issue** The authors state that the mammalian GRHL family has a "truncated and less disordered" N-terminus compared to Drosophila Grh, but the quantitative comparison of disorder predictions is not shown.
- **Required correction** Provide the disorder prediction scores or a quantitative comparison of predicted disorder between Drosophila Grh and human GRHL2 to support this claim.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion of GRHL2 function
- **Evidence pointer** Figure 5A-E
- **Issue** The authors show that human GRHL2 can bind closed chromatin and promote accessibility in Drosophila cells but cannot activate transcription from the hgo promoter. The interpretation that this reflects a lack of cofactor recruitment is plausible but not directly tested.
- **Required correction** Consider discussing alternative explanations, such as differences in DNA binding specificity or the inability of GRHL2 to interact with Drosophila-specific cofactors, and suggest experiments to distinguish between these possibilities.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Protein purification
- **Evidence pointer** Materials and Methods
- **Issue** The purification of full-length Grh and mutants using baculovirus expression is described, but the purity and integrity of the proteins are not documented.
- **Required correction** Provide representative Coomassie-stained gels or Western blots showing the purified proteins and their integrity.

## Risk / unsupported claims
- The claim that "both the conserved DNA-binding domain and the extended, intrinsically disordered N-terminus are required for the stable chromatin occupancy that supports access to closed chromatin" is supported by the combination of in vitro and in vivo data, but the quantitative rigor of the EMSA and ChIP-seq comparisons needs to be established.
- The claim that "mitotic retention depends solely on sequence-specific DNA binding" is supported by the observation that Grh ΔN is retained on mitotic chromosomes, but the authors do not test whether the N-terminus contributes to the kinetics or stability of mitotic retention.
- The claim that the scrambled N-terminus "partially restored transcriptional activation activity" is based on luciferase reporter data, but the statistical significance of this partial restoration is not reported.
- The claim that human GRHL2 "can function as a pioneer factor in Drosophila cells" is supported by ChIP-seq and ATAC-seq data, but the lack of transcriptional activation from the hgo promoter raises questions about the functional significance of this pioneering activity.
- The claim that "pioneering activity depends on the combinatorial contributions of structured and disordered domains" is a reasonable interpretation of the data, but the mechanistic basis for how the disordered N-terminus stabilizes chromatin occupancy is not directly addressed.