## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, discussion, figure legends not provided, supplementary materials referenced but not provided)
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text. Figures, tables, and supplementary materials are referenced but were not available for direct inspection.
- **Shared manuscript claim summary** The manuscript claims that Agrobacterium tumefaciens employs two redox-responsive LysR-type transcription factors, OxyR and LsrB, to coordinate the oxidative stress response. LsrB is described as a thiol-based redox sensor with four cysteine residues that form two intramolecular disulfide pairs, directly regulating katG along with OxyR. The authors propose a "fail-safe" model wherein OxyR acts as a fast sensor and LsrB as a broader stress regulator.
- **Visible evidence base** Phylogenetic analysis (Fig. 1A), genomic context comparison (Fig. 1B), phenotypic assays including spot tests and inhibition zones (Fig. 2A–C), virulence assay (Fig. 2D), RNA-seq data (Figs. 3–4, Supplementary Table S4), GO enrichment analysis (Fig. 5, Supplementary Fig. S4), qRT-PCR validation (Fig. 6A, Supplementary Fig. S3), EMSA (Fig. 6C, Supplementary Fig. S5), complementation experiments (Fig. 7), AlphaFold 3 modeling (Fig. 8A–B), cryo-EM structure (Fig. 8C–E, Supplementary Fig. S7), site-directed mutagenesis (Fig. 9), and mass spectrometry-based thiol trapping (Fig. 10, Supplementary Fig. S8)
- **Missing materials affecting confidence** Figures and figure legends, supplementary tables (S1–S4), supplementary figures (S1–S8), RNA-seq raw data, mass spectrometry raw data, cryo-EM density maps and validation reports, statistical details for phenotypic assays

## Reviewer

### Overall assessment
This manuscript addresses a significant and timely question in bacterial oxidative stress biology: how two LysR-type transcriptional regulators, OxyR and LsrB, coordinate the response to reactive oxygen species in the plant pathogen Agrobacterium tumefaciens. The study combines genetics, transcriptomics, structural biology, and biochemistry to provide a multi-layered characterization of both regulators. The finding that LsrB functions as a thiol-based redox sensor with four cysteines forming two intramolecular disulfide pairs is novel and potentially important for understanding redox regulation in Rhizobiales. The transcriptomic datasets are comprehensive and will be a valuable community resource. However, several concerns limit the strength of the conclusions as currently presented. The direct evidence for redox-dependent regulation of LsrB activity is indirect, the mechanistic distinction between OxyR and LsrB functions is not fully resolved, and the structural data are presented at moderate resolution without clear functional validation of the proposed disulfide-based mechanism. The manuscript would be strengthened by additional experiments directly linking cysteine oxidation to transcriptional activity and by clarifying the regulatory hierarchy between the two factors.

### Who would be interested in the results, and why
Researchers studying bacterial oxidative stress responses, transcriptional regulation in Alphaproteobacteria, and redox biology will find this work of direct interest. The study is also relevant to those investigating plant-microbe interactions, as Agrobacterium tumefaciens is a major plant pathogen and the virulence phenotype is linked to the regulators studied. The cryo-EM structure of LsrB and the identification of a second redox-sensing LTFR in Rhizobiales will interest structural biologists and evolutionary microbiologists. The transcriptomic dataset provides a resource for the broader Agrobacterium and Rhizobiales research communities.

### Major Strengths
1. The study addresses a clear and important biological question with a multi-technical approach spanning genetics, transcriptomics, structural biology, and biochemistry.
2. The identification of LsrB as a second redox-responsive LTFR in A. tumefaciens, with four cysteines forming two intramolecular disulfide pairs, is a novel contribution.
3. The transcriptomic analysis is comprehensive and provides a valuable dataset for the community.
4. The combination of AlphaFold 3 modeling with cryo-EM validation is a modern and rigorous approach to structural characterization.
5. The phenotypic analyses are well-designed and include relevant controls, such as complementation experiments.
6. The proposed "fail-safe" model is conceptually interesting and provides a framework for future studies.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for redox-sensing mechanism
- **Claim pointer** The manuscript claims that LsrB functions as a thiol-based redox switch, with four cysteine residues forming two intramolecular disulfide bonds in response to oxidative stress, and that this redox sensitivity is functionally important for its regulatory activity.
- **Evidence pointer** Fig. 8, Fig. 9, Fig. 10, Supplementary Fig. S8
- **Concern** The central claim that LsrB is a redox sensor relies on indirect evidence. The cryo-EM structure shows the positions of cysteine residues but does not demonstrate redox-dependent conformational changes. The mutagenesis experiments show that C273 is important for function, but the data do not establish that oxidation of this residue is the activating signal. The mass spectrometry data demonstrate that all four cysteines can be modified after reduction, but this does not prove that they form disulfide bonds under physiological oxidative stress conditions in vivo. The authors do not provide direct evidence that oxidized LsrB has different DNA-binding or transcriptional activity compared to reduced LsrB.
- **Why it matters** The title and central thesis of the manuscript depend on LsrB being a bona fide redox sensor. Without direct biochemical evidence linking cysteine oxidation to changes in LsrB activity, the mechanistic claim is not fully supported. The distinction between a redox-regulated transcription factor and a transcription factor that merely contains cysteines is critical for the paper's significance.
- **Resolution test** The authors should perform in vitro DNA-binding assays (e.g., EMSA or fluorescence anisotropy) with purified LsrB in reduced versus oxidized states, or with wild-type versus cysteine-to-serine mutants, to demonstrate that oxidation directly modulates DNA-binding affinity or specificity. Alternatively, they could use a reporter assay in vivo where the redox state of the cell is manipulated to show that LsrB activity correlates with its oxidation state.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional distinction between OxyR and LsrB
- **Claim pointer** The manuscript claims that OxyR and LsrB co-regulate key antioxidant genes, including katG, and that LsrB has a broader role in stress responses beyond H2O2 detoxification.
- **Evidence pointer** Fig. 3, Fig. 4, Fig. 5, Supplementary Table S4
- **Concern** The transcriptomic data show that deletion of lsrB affects many more genes than deletion of oxyR, and that the double deletion has a distinct transcriptomic profile. However, the manuscript does not clearly delineate which genes are directly regulated by each factor versus indirect effects. The claim that LsrB is a "master stress regulator" is based largely on the number of differentially expressed genes, but this could reflect indirect regulatory cascades. The authors do not perform chromatin immunoprecipitation sequencing (ChIP-seq) or DNA-binding motif analyses to distinguish direct from indirect targets. Furthermore, the relationship between OxyR and LsrB is not clarified: do they act independently, additively, or hierarchically?
- **Why it matters** The proposed "fail-safe" model implies a specific functional relationship between the two regulators. Without knowing the direct regulons of each factor and how they interact, the model remains speculative. The interpretation of the transcriptomic data is central to the paper's conclusions about the division of labor between OxyR and LsrB.
- **Resolution test** The authors should perform ChIP-seq for both OxyR and LsrB under control and H2O2 stress conditions to define their direct regulons. Alternatively, they could use a transcriptomic approach with a short time course and protein synthesis inhibition to distinguish primary from secondary effects. A more targeted approach would be to test whether the promoters of key shared targets (e.g., katG) are directly bound by both factors and whether binding is cooperative or competitive.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Structural evidence and functional relevance of disulfide bonds
- **Claim pointer** The manuscript claims that the cryo-EM structure of LsrB, combined with AlphaFold 3 modeling, reveals two proximal cysteine pairs that likely form intramolecular disulfide bonds upon oxidation, and that this is the structural basis for redox sensing.
- **Evidence pointer** Fig. 8, Supplementary Fig. S6, Supplementary Fig. S7
- **Concern** The cryo-EM structure is reported at 3.9 Å resolution, which is moderate and may not be sufficient to unambiguously resolve side-chain conformations, particularly for cysteine residues. The authors state that the AlphaFold 3 model was fitted into the cryo-EM density, but it is unclear whether the cysteine pairings are supported by the experimental density or primarily derived from the model. The manuscript does not report local resolution estimates, map-to-model cross-validation (e.g., Q-score or half-map FSC), or other validation metrics that would support the assignment of specific disulfide bonds. Additionally, the functional relevance of the proposed disulfide bonds is not directly tested.
- **Why it matters** The structural model is used to support the redox-sensing mechanism. If the cysteine pairings are not robustly supported by the experimental data, the structural argument is weakened. The field of cryo-EM requires rigorous validation, particularly when claims about specific side-chain interactions are made at moderate resolution.
- **Resolution test** The authors should provide additional validation metrics for the cryo-EM structure, including local resolution maps, FSC curves, and model-to-map fit statistics. They could also perform site-directed mutagenesis of the proposed disulfide-forming cysteines and test the effects on protein stability, oligomerization, and DNA-binding activity under oxidizing and reducing conditions. Alternatively, they could use mass spectrometry to directly identify disulfide-linked peptides in oxidized versus reduced LsrB.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Phenotypic data and statistical rigor
- **Claim pointer** The manuscript claims that deletion of lsrB and oxyR leads to increased sensitivity to H2O2, paraquat, and GSSG, and reduced virulence in a plant infection model.
- **Evidence pointer** Fig. 2, Supplementary Fig. S1, Supplementary Fig. S2
- **Concern** The phenotypic assays are described in the results but the statistical details are not provided in the text. It is unclear how many biological replicates were performed, what statistical tests were used, and whether the differences are statistically significant. The inhibition zone assay data are presented as representative images or measurements without clear quantification. The virulence assay is described as showing "drastically reduced" T-DNA transfer, but the quantification method and statistical analysis are not described. The cell length measurements are mentioned as "minor" changes but no statistical analysis is presented.
- **Why it matters** The phenotypic data are foundational to the paper's claims about the functional importance of OxyR and LsrB. Without proper statistical validation, the reader cannot assess the robustness of the observed phenotypes. This is particularly important for the subtle phenotypes, such as the GSSG sensitivity and the cell length changes.
- **Resolution test** The authors should provide full statistical details for all phenotypic assays, including the number of replicates, the statistical test used, and the effect sizes with confidence intervals. For the inhibition zone assays, they should provide quantitative measurements (e.g., zone diameter) with statistical comparisons. For the virulence assay, they should provide a quantitative scoring system with statistical analysis.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the "fail-safe" model
- **Claim pointer** The manuscript proposes that the presence of two redox-responsive LTFRs provides a "fail-safe" mechanism for oxidative stress protection in A. tumefaciens.
- **Evidence pointer** Fig. 11, Discussion
- **Concern** The "fail-safe" model is presented as a conceptual framework, but the evidence supporting it is limited. The authors suggest three possible reasons for having two regulators, but these are presented as hypotheses rather than tested conclusions. The model does not account for the observation that the double deletion mutant has a transcriptomic profile that is not simply the sum of the single deletions, suggesting complex epistatic interactions. The model also does not explain why LsrB is only found in Rhizobiales, whereas OxyR is broadly conserved.
- **Why it matters** The "fail-safe" model is a key conceptual contribution of the paper. If it is presented as a hypothesis, it should be clearly framed as such. If it is presented as a conclusion, it requires more direct experimental support. The evolutionary and ecological context of having two regulators is interesting but not fully developed.
- **Resolution test** The authors should either reframe the "fail-safe" model as a testable hypothesis or provide additional experimental evidence, such as measuring the fitness of single and double mutants under various stress conditions, or examining the expression dynamics of both regulators under different stress regimes. They could also compare the regulatory logic with other bacteria that have only one redox-sensing LTFR.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure references
- **Affected element** Results section
- **Evidence pointer** Fig. 3, Fig. 4, Fig. 5
- **Issue** The results section references figures without clear descriptions of what is shown in each panel. For example, "Fig. 3A" and "Fig. 3B" are mentioned but the reader cannot determine what specific data are presented without the figure legends.
- **Required correction** The authors should ensure that each figure reference in the text is accompanied by a brief description of the data shown, or the figure legends should be included in the manuscript for review.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Consistency of gene nomenclature
- **Affected element** Throughout
- **Evidence pointer** Location not provided
- **Issue** The manuscript uses italicized gene names (e.g., katG, oxyR, lsrB) in some places but not consistently. The nomenclature for A. tumefaciens genes should follow standard bacterial genetic nomenclature conventions.
- **Required correction** The authors should ensure consistent use of italics for gene names and standard nomenclature throughout the manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting in text
- **Affected element** Results section, phenotypic assays
- **Evidence pointer** Fig. 2, Supplementary Fig. S1
- **Issue** The text states that differences were observed but does not report p-values or confidence intervals. For example, "the ΔlsrB and the ΔlsrB/ΔoxyR strains also showed sensitivity to paraquat" does not include statistical support.
- **Required correction** The authors should include statistical details in the text or figure legends for all quantitative comparisons.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion
- **Evidence pointer** Location not provided
- **Issue** The discussion does not address potential limitations of the study, such as the moderate resolution of the cryo-EM structure, the lack of direct biochemical evidence for redox sensing, or the potential for indirect effects in the transcriptomic analysis.
- **Required correction** The authors should include a paragraph acknowledging the limitations of their study and how these might be addressed in future work.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity of the "fail-safe" model
- **Affected element** Discussion, Fig. 11
- **Evidence pointer** Fig. 11
- **Issue** The "fail-safe" model is described in text but the figure (Fig. 11) is not available for review. The model would benefit from a clear schematic showing the proposed regulatory relationships and the points of redundancy.
- **Required correction** The authors should ensure that Fig. 11 clearly illustrates the proposed model, including the distinct and overlapping functions of OxyR and LsrB.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability statement
- **Affected element** Data availability
- **Evidence pointer** Location not provided
- **Issue** The data availability statement mentions deposition of RNA-seq, mass spectrometry, and cryo-EM data but does not provide accession numbers for the cryo-EM structure beyond the PDB ID. The mass spectrometry data are deposited at ProteomeXchange but the accession is given.
- **Required correction** The authors should ensure all relevant accession numbers are provided and that the cryo-EM data include the EMPIAR deposition for the raw micrographs.

### Technical Failings That Need to Be Addressed Before the Case Is Established
1. The direct biochemical evidence for redox-dependent regulation of LsrB activity is missing. The manuscript demonstrates that LsrB contains cysteines that can be modified, but does not show that oxidation changes its function as a transcription factor.
2. The cryo-EM structure at 3.9 Å resolution is used to support specific cysteine pairing, but validation metrics are not provided. The authors should report local resolution, FSC curves, and model-to-map fit statistics.
3. The transcriptomic analysis does not distinguish direct from indirect regulatory targets. ChIP-seq or a comparable approach is needed to define the direct regulons of OxyR and LsrB.
4. The statistical analysis for phenotypic assays is not described. The authors should provide details on replicates, tests used, and effect sizes.

### Assessment Against Nature-Style Criteria
- **Originality** The study is original in its focus on the coexistence of two redox-responsive LTFRs in a single organism and the proposal of a "fail-safe" mechanism. The identification of LsrB as a second redox sensor in A. tumefaciens, with a distinct cysteine architecture compared to OxyR, is a novel contribution. However, the concept of redox-sensing transcription factors is well established, and the novelty lies primarily in the specific system studied.
- **Scientific importance** The work is important for understanding oxidative stress responses in Rhizobiales, a group that includes both plant pathogens and symbionts. The finding that LsrB regulates a broader set of genes than OxyR and is involved in virulence has implications for understanding host-pathogen interactions. The transcriptomic dataset is a valuable resource. However, the importance would be enhanced by clearer mechanistic insights into how the two regulators coordinate their activities.
- **Interdisciplinary readership** The manuscript will appeal to microbiologists, redox biologists, structural biologists, and plant pathologists. The combination of genetics, transcriptomics, structural biology, and biochemistry broadens the potential readership. The use of cryo-EM and AlphaFold will attract structural biologists. The plant infection assays will interest plant-microbe interaction researchers.
- **Technical soundness** The technical approaches are generally sound and appropriate for the questions asked. The RNA-seq analysis appears well-designed, and the cryo-EM workflow is modern. However, the lack of direct biochemical evidence for redox sensing and the missing validation metrics for the cryo-EM structure are technical weaknesses that need to be addressed.
- **Readability for nonspecialists** The manuscript is generally well-written and accessible. The introduction provides sufficient background for readers unfamiliar with bacterial oxidative stress responses. The results are presented logically, and the discussion places the findings in a broader context. However, some sections, particularly the structural biology parts, may be challenging for nonspecialists. The abstract is clear and concise.

### Recommendation Posture
Supportive if technical concerns are resolved. The manuscript addresses an important question and provides a substantial dataset, but the central claim that LsrB is a redox-sensing transcription factor requires direct biochemical evidence. The authors should demonstrate that oxidation of LsrB's cysteines directly modulates its DNA-binding or transcriptional activity. Additionally, the cryo-EM structure should be validated with appropriate metrics, and the transcriptomic analysis should be complemented with ChIP-seq or a similar approach to define direct regulatory targets. If these concerns are addressed, the manuscript would be suitable for publication in a high-impact journal.

## Risk / Unsupported Claims
1. The claim that LsrB functions as a thiol-based redox switch is not directly supported by the data presented. The manuscript shows that LsrB contains cysteines that can be modified, but does not demonstrate that oxidation alters LsrB's activity.
2. The claim that the four cysteine residues form two intramolecular disulfide bonds is inferred from the structure and mass spectrometry data but is not directly demonstrated. The cryo-EM structure at 3.9 Å may not be sufficient to resolve specific disulfide linkages.
3. The claim that OxyR acts as a "fast" sensor and LsrB as a "broader" regulator is speculative and not directly tested. The transcriptomic data show differences in the number of regulated genes, but this does not establish differences in response kinetics or regulatory scope.
4. The claim that the "fail-safe" mechanism provides a selective advantage is presented as a conclusion but is not experimentally tested. This should be framed as a hypothesis.
5. The statement that "LsrB is solely found in Rhizobiales" is based on bioinformatic analysis but the methods for this analysis are not described in the provided text. The reader cannot assess the robustness of this claim.
6. The discrepancy between RNA-seq and qRT-PCR results for ohr regulation is acknowledged but not fully explained. The authors should address this inconsistency more thoroughly.