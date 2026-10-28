## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific content, methodological rigor, data interpretation, and claims as presented in the manuscript
- **Shared manuscript claim summary** The authors generated multi-omics epigenetic profiles (ATAC-seq, ChIP-seq, BS-seq, HiChIP, NET-CAGE) across four developmental stages in barley to annotate candidate cis-regulatory elements (cCREs), characterize chromatin interactions, and demonstrate the utility of their dataset for predicting distal regulatory elements, using the LEA gene family and Vrn3 as case studies
- **Visible evidence base** Main text figures (Figures 1-7), supplementary figure descriptions, methods section, data availability statements
- **Missing materials affecting confidence** Raw data files, supplementary tables (Tables S1-S6), detailed quality control metrics, complete analysis parameters, and the interactive genome browser content could not be directly examined

## Reviewer
- **Overall assessment** This manuscript presents a substantial multi-omics resource for the barley research community, integrating epigenetic profiling, chromatin conformation capture, and machine learning to annotate putative cis-regulatory elements. The dataset generation is comprehensive and the integration approach is methodologically sound. However, several concerns regarding the functional validation of predicted elements, the interpretation of promoter-promoter interactions, and the generalizability of the Vrn3 case study require clarification. The resource value is clear, but the biological insights derived from the data are somewhat limited and would benefit from deeper mechanistic exploration.

- **Who would be interested in the results, and why** Plant molecular biologists, particularly those working on cereal genomics and gene regulation. Researchers studying cis-regulatory element annotation, chromatin architecture, and epigenetic regulation in large plant genomes would find the dataset valuable. The barley breeding community may also be interested given the potential applications for trait engineering through regulatory element manipulation. The methodological framework could be of interest to computational biologists developing integrative approaches for regulatory element prediction.

- **Major strengths** 
  1. Comprehensive multi-omics dataset generation across four developmental stages, providing a valuable community resource
  2. Integration of multiple epigenetic marks with chromatin conformation data using machine learning approaches
  3. The interactive genome browser platform enhances accessibility and utility of the data
  4. The LEA gene family analysis provides a concrete example of how the data can be used to study developmentally regulated gene clusters
  5. The Vrn3 case study demonstrates the potential for cross-species transferability of regulatory element predictions

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation
- **Claim pointer** The manuscript claims that predicted cCREs are functional regulatory elements, but no experimental validation (e.g., reporter assays, CRISPR editing, or transgenic approaches) is provided to confirm enhancer or silencer activity
- **Evidence pointer** Results sections "Profiles of epigenetic features enable the annotation of cis-regulatory elements" and "Characterization of candidate cis-regulatory elements"; Discussion section
- **Concern** The central premise of the manuscript is the identification of functional cis-regulatory elements, yet none of the predicted cCREs are experimentally validated. The authors acknowledge this limitation in the Discussion, but the lack of any functional validation weakens the claim that these are bona fide regulatory elements. The LEA gene cluster analysis is purely correlative, and the Vrn3 case study relies on sequence similarity to previously identified wheat enhancers rather than direct functional testing.
- **Why it matters** Without experimental validation, the biological significance of the predicted cCREs remains uncertain. Epigenetic marks and chromatin accessibility are imperfect predictors of regulatory activity, and the field has moved toward requiring at least some functional confirmation of predicted elements. The manuscript would be substantially strengthened by even a small-scale validation experiment.
- **Resolution test** Provide experimental evidence for at least a subset of predicted cCREs, such as reporter assays in transient expression systems, CRISPR-based deletion or perturbation of selected elements, or comparison with validated regulatory elements from other cereal species.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Data interpretation
- **Claim pointer** The manuscript claims that promoter-promoter interactions are frequent and potentially functional, but the analysis does not adequately distinguish between technical artifacts, structural constraints, and regulatory interactions
- **Evidence pointer** Results section "Annotation of genomic interactions determines the composition of the primary interaction classes"; Figure 5
- **Concern** The high proportion of promoter-promoter interactions (25.8-31.7% of all interactions) is interpreted as evidence of co-regulation and regulatory hubs. However, HiChIP at 5-kb resolution may not adequately resolve whether these represent true promoter-promoter contacts or are influenced by the high density of genes and regulatory elements in the barley genome. The authors do not compare their observed interaction frequencies to what would be expected by genomic proximity alone.
- **Why it matters** Overinterpretation of promoter-promoter interactions could lead to incorrect conclusions about regulatory mechanisms. The field has debated whether such interactions are functionally significant or largely reflect the three-dimensional organization of the genome and the high gene density in plant genomes.
- **Resolution test** Include appropriate background models or permutation tests that account for genomic distance and gene density when assessing the significance of promoter-promoter interactions. Compare observed interaction frequencies to expectations from random genomic organization.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical rigor
- **Claim pointer** The manuscript claims that NET-CAGE data demonstrate that eRNA transcription is not a typical attribute of barley cCREs, but the sensitivity and specificity of the NET-CAGE approach for detecting unstable transcripts is not adequately established
- **Evidence pointer** Results section "Barley bidirectional and unidirectional unstable transcripts are an infrequent feature associated with cCREs"; Figure 3
- **Concern** The conclusion that eRNA transcription plays a minor role in barley is based on a single NET-CAGE experiment in one developmental stage (4DAG embryo). The authors do not provide adequate controls to demonstrate that their NET-CAGE protocol can detect unstable transcripts, nor do they compare their results with other methods (e.g., PRO-seq, GRO-seq) that have been used successfully in wheat. The low detection rate could reflect technical limitations rather than biological reality.
- **Why it matters** The conclusion about eRNA prevalence in barley has implications for understanding regulatory mechanisms in cereals. If the NET-CAGE method is insufficiently sensitive, the conclusion could be misleading and may not reflect the true extent of eRNA transcription in barley.
- **Resolution test** Validate the NET-CAGE approach using known eRNA loci or spike-in controls. Compare results with alternative methods for detecting nascent transcription. Consider analyzing additional developmental stages or conditions where eRNA transcription may be more prevalent.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The Vrn3 case study claims to demonstrate the power of the dataset to predict regulatory elements for other developmental stages, but the analysis is limited to a single gene and does not provide experimental validation
- **Evidence pointer** Results section "Regulatory elements of Vrn3 are detectable in non-expressing tissues and without vernalization treatment"; Figure 7
- **Concern** The Vrn3 analysis identifies cCREs based on sequence conservation and epigenetic features, and shows that one cCRE (cCRE3) interacts with the Vrn3 promoter via H3K27me3 HiChIP. However, the functional significance of this interaction is not tested. The claim that this demonstrates the predictive power of the dataset for other developmental stages is overstated, as no functional validation is provided and the analysis is limited to a single locus.
- **Why it matters** The Vrn3 example is presented as a key demonstration of the utility of the dataset, but without functional validation, it remains a correlative observation. The claim that the dataset can predict regulatory elements for other developmental stages requires more extensive validation across multiple loci.
- **Resolution test** Provide functional validation of the predicted Vrn3 cCREs, such as testing enhancer activity in reporter assays or examining the effect of perturbation on Vrn3 expression. Extend the analysis to additional developmentally regulated genes to demonstrate generalizability.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1C and chromatin state definitions
- **Evidence pointer** Figure 1C; Results section "Profiles of epigenetic features enable the annotation of cis-regulatory elements"
- **Issue** The chromatin state emission values heatmap is difficult to interpret without a clear description of what each state represents biologically. The seven states are named E1-E7, but the functional annotations are only briefly described in the text.
- **Required correction** Provide a clear table or annotation for each chromatin state with its predicted functional role, and consider adding state-specific genomic feature enrichment profiles to aid interpretation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Motif enrichment analysis
- **Evidence pointer** Figure 2D; Results section "Characterization of candidate cis-regulatory elements"
- **Issue** The motif enrichment analysis identifies transcription factor binding sites enriched in cCREs, but the statistical methods and multiple testing corrections are not fully described. The significance thresholds and background models used are unclear.
- **Required correction** Provide detailed description of the statistical methods used for motif enrichment, including background model selection, multiple testing corrections, and significance thresholds.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** HiChIP interaction visualization
- **Evidence pointer** Figure 4; Results section "High-resolution analysis of the interactome in the 24DAP embryo"
- **Issue** The HiChIP interaction data are presented as examples (Figures 4A and 4B), but the criteria for selecting these examples and the representation of interaction strength are not clearly explained.
- **Required correction** Clarify how representative examples were selected and provide a clear legend explaining the visual representation of interaction strength and significance.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Resource accessibility
- **Affected element** Data availability
- **Evidence pointer** Data and code availability section
- **Issue** While the data are deposited in public repositories, the interactive genome browser is hosted on a custom platform that may not be maintained long-term. The GitHub repository is mentioned but the completeness of code documentation is unclear.
- **Required correction** Consider depositing the genome browser tracks in established platforms (e.g., Ensembl Plants, JBrowse instances maintained by major databases) and ensure all code is fully documented and versioned.

- **Technical failings that need to be addressed before the case is established**
  1. Lack of experimental validation for any predicted cCREs (R1-M1)
  2. Inadequate controls for NET-CAGE sensitivity in detecting unstable transcripts (R1-M3)
  3. No comparison of promoter-promoter interaction frequencies to genomic background expectations (R1-M2)
  4. Limited validation of the Vrn3 case study claims (R1-M4)

- **Assessment against Nature-style criteria**
  - **Originality**: The manuscript offers a novel integration of multiple epigenetic datasets in barley, particularly the combination of HiChIP with chromatin state analysis. However, similar approaches have been applied in other cereals (wheat, maize, rice), and the conceptual framework is not entirely new. The LEA gene cluster analysis and Vrn3 case study provide some novel biological context.
  - **Scientific importance**: The dataset represents a valuable resource for the barley research community and potentially for cereal genomics more broadly. The identification of cCREs and their putative targets could inform future functional studies and breeding applications. However, the biological insights derived are somewhat limited without functional validation.
  - **Interdisciplinary readership**: The work will primarily appeal to plant molecular biologists, epigenomics researchers, and computational biologists. The broader plant science community may find the resource useful, but the appeal beyond plant biology is limited.
  - **Technical soundness**: The experimental and computational methods are generally sound and well-described. The integration of multiple data types is thoughtful. However, the lack of functional validation and some statistical concerns (e.g., background models for interaction analysis) reduce confidence in the conclusions.
  - **Readability for nonspecialists**: The manuscript is clearly written and the figures are generally well-designed. However, the complexity of the multi-omics integration may be challenging for readers without specialized knowledge in epigenomics or chromatin biology. The abstract and introduction are accessible, but the results section assumes significant background knowledge.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a valuable resource and a reasonable analytical framework, but the lack of functional validation and some interpretive concerns prevent the biological claims from being fully established. The authors should address the major concerns regarding validation and statistical rigor before the case is fully made.