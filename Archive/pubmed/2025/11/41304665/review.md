## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, conclusions, and materials and methods
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical soundness as presented in the provided text
- **Shared manuscript claim summary** The authors propose that a chromatin-associated pea apyrase, psNTP9 (PS), and a double-mutant variant (DM), function as DNA-binding regulatory proteins in both yeast and Arabidopsis, based on ChIP-seq, EMSA, and AlphaFold3 modeling data
- **Visible evidence base** ChIP-seq peak identification, EMSA binding assays, co-immunoprecipitation with mass spectrometry, AlphaFold3 structural predictions, qRT-PCR validation, and previously reported RNA-seq data
- **Missing materials affecting confidence** Raw ChIP-seq data files, complete EMSA gel images, mass spectrometry data tables, statistical analysis details, and full supplementary tables referenced but not provided

## Reviewer
- **Overall assessment** The manuscript presents an interesting extension of apyrase function beyond enzymatic nucleotide hydrolysis, proposing a nuclear role in transcriptional regulation. The combination of ChIP-seq, EMSA, and structural modeling is appropriate for the claims made. However, several technical limitations, particularly the low purity of recombinant proteins used in EMSA and the reliance on computational modeling without direct binding affinity measurements, weaken the strength of the conclusions. The study is exploratory and hypothesis-generating rather than definitive, and the authors appropriately acknowledge some of these limitations. The work will be of interest to plant molecular biologists and researchers studying non-canonical functions of metabolic enzymes, but the evidence does not yet fully establish PS as a bona fide transcription factor or DNA-binding regulatory protein.

- **Who would be interested in the results, and why** Plant molecular biologists studying apyrase functions, researchers investigating nuclear-localized metabolic enzymes with potential transcriptional regulatory roles, and scientists working on phosphate homeostasis and drought tolerance mechanisms in crops. The potential link between apyrase overexpression and cuticle formation genes may interest researchers studying plant stress responses.

- **Major strengths** The study addresses a novel question regarding nuclear functions of plant apyrases. The integration of ChIP-seq with transcriptomic data provides a genome-wide perspective. The use of both yeast and Arabidopsis systems strengthens the cross-kingdom relevance. The EMSA experiments include appropriate controls such as mutant probes and competition assays. The AlphaFold3 modeling provides testable structural hypotheses.

- **Major Concerns** The following concerns are detailed below.

- **Minor Comments** The following comments are detailed below.

- **Technical failings that need to be addressed before the case is established** R1-M1 (protein purity), R1-M2 (binding affinity quantification), R1-M3 (ChIP-seq validation), R1-M4 (statistical rigor)

- **Assessment against Nature-style criteria** Originality is moderate to high, as the proposed nuclear regulatory function for a plant apyrase is novel. Scientific importance is moderate, as the findings could have implications for understanding apyrase functions and plant stress responses, but the physiological relevance remains unclear. Interdisciplinary readership is limited, as the work primarily targets plant molecular biology and biochemistry audiences. Technical soundness is adequate but with notable limitations in protein purity and binding quantification. Readability for nonspecialists is acceptable, though some sections assume familiarity with ChIP-seq and EMSA methodologies.

- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding protein purity in EMSA experiments and quantitative binding measurements.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that PS specifically binds to promoter sequences based on EMSA results, and that DM shows minimal binding
- **Evidence pointer** Section 2.5, Figures 3-5, Section 5.5
- **Concern** The EMSA experiments were performed with protein preparations that were only approximately 1% pure, as stated in Section 5.5. This means that the observed band shifts could potentially be attributed to contaminating proteins rather than PS itself. The authors acknowledge this possibility for some bands but still attribute the primary shifts to PS. With such low purity, it is difficult to definitively conclude that PS is the protein responsible for the observed DNA-binding activity.
- **Why it matters** The central claim of the manuscript is that PS functions as a DNA-binding protein. If the binding observed in EMSA is due to contaminants, the entire premise of the study is undermined. The low purity also affects the interpretation of the differential binding between PS and DM, as differences in contaminant profiles between the two preparations could explain the observed differences.
- **Resolution test** The authors should repeat key EMSA experiments with highly purified recombinant PS and DM proteins (e.g., >90% purity) and demonstrate that the binding is retained. Alternatively, they could perform supershift assays with anti-PS antibodies to confirm that PS is indeed part of the DNA-protein complex.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that PS binds to specific promoter sequences with a consensus motif 5'-(G/T)GG(G/T)A-3', and that DM has reduced binding affinity
- **Evidence pointer** Section 2.5, Figures 3-5, Section 2.7, Figure 6
- **Concern** The manuscript does not provide quantitative binding affinity measurements (e.g., Kd values) for PS or DM binding to the identified DNA sequences. The EMSA results are presented qualitatively, and the claim of "minimal" DM binding is not supported by quantitative data. Additionally, the consensus motif is derived solely from AlphaFold3 modeling of three sequences, which is a limited sample size for deriving a binding motif.
- **Why it matters** Without quantitative binding data, it is not possible to assess the strength or specificity of PS-DNA interactions. The claim that DM has reduced binding affinity is central to the interpretation that the PCBD1 mutations affect DNA binding, but this is not rigorously demonstrated. The consensus motif prediction from only three sequences is statistically weak.
- **Resolution test** The authors should perform quantitative EMSA or surface plasmon resonance (SPR) experiments to determine binding affinities of PS and DM for the identified sequences and mutant controls. They should also validate the proposed consensus motif using a larger set of binding sites, such as from the ChIP-seq data, and test additional sequences.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that ChIP-seq identified PS- and DM-specific binding sites in Arabidopsis promoters, with largely non-overlapping distributions
- **Evidence pointer** Section 2.3, Table S1, Figure S1
- **Concern** The ChIP-seq experiments were performed using 4Myc-tagged PS and DM proteins overexpressed under the 35S promoter. Overexpression can lead to non-physiological binding patterns. Additionally, the manuscript does not describe validation of the ChIP-seq results by independent methods such as ChIP-qPCR. The peak calling criteria and the statistical significance thresholds are not fully described. The integration with RNA-seq data is presented in a simplified manner, and the causal relationship between binding and gene expression changes is not established.
- **Why it matters** ChIP-seq with overexpressed proteins can produce artifacts. Without independent validation and clear statistical criteria, the reliability of the identified binding sites is uncertain. The claim that PS and DM regulate different transcriptional networks depends on the accuracy of these binding site identifications.
- **Resolution test** The authors should validate a subset of ChIP-seq peaks by ChIP-qPCR. They should also provide more detailed information on peak calling parameters and statistical thresholds. Ideally, they would perform ChIP-seq with antibodies against endogenous PS protein, though this may not be feasible if no suitable antibody exists.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors claim that PS and DM overexpression leads to different gene expression profiles and phenotypes
- **Evidence pointer** Section 2.3, Section 2.6, Table S1, Table S5
- **Concern** The manuscript relies heavily on previously reported RNA-seq data and phenotypic observations. The statistical analysis of the gene expression data is not described in detail, and the criteria for defining differentially expressed genes are not stated. The co-immunoprecipitation experiments identified interacting proteins, but the significance of these interactions is not validated by reciprocal co-IP or functional assays.
- **Why it matters** The link between PS/DM binding and gene expression changes is correlative. Without clear statistical criteria and validation, the claim that PS and DM regulate different transcriptional programs is not firmly established. The co-IP data are presented as a list of potential interactors without functional validation.
- **Resolution test** The authors should provide detailed statistical methods for the RNA-seq analysis, including thresholds for significance and effect size. They should validate at least a few key co-IP interactions by reciprocal co-IP or in vitro pull-down assays.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1, Figure 1
- **Evidence pointer** Section 2.1, Figure 1
- **Issue** The description of the NLS_BP sequence and the rationale for the DM mutations is somewhat confusing. The text states that the P216R mutation may interfere with nuclear targeting, but the data in Figure 1 are not clearly explained.
- **Required correction** Clarify the relationship between the NLS_BP sequence, the PCBD1 domain, and the specific mutations introduced. Provide a clearer figure legend explaining the sequence alignment and the positions of the mutations.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.3
- **Evidence pointer** Section 2.3, Table S1
- **Issue** The manuscript states that 16,667 PS-specific, 23,207 DM-specific, and 28,889 overlapping sites were identified, but the criteria for defining "specific" versus "overlapping" are not described.
- **Required correction** Provide a clear definition of how binding sites were classified as PS-specific, DM-specific, or overlapping, including the thresholds used for peak overlap.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.5.2, Figures 4-5
- **Evidence pointer** Section 2.5.2, Figures 4-5
- **Issue** The EMSA figures are described in the text but the specific bands corresponding to PS-DNA complexes are not clearly labeled in the figure descriptions.
- **Required correction** Ensure that figure legends clearly indicate which bands represent PS-DNA complexes, free probe, and any non-specific complexes.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 5.3.3
- **Evidence pointer** Section 5.3.3
- **Issue** The ChIP-seq data processing section mentions the use of "fastpXpress" and CLC Genomics Workbench but does not provide version numbers for all software or the specific parameters used for peak calling.
- **Required correction** Provide complete software versions and analysis parameters to ensure reproducibility.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.7, Figure 6
- **Evidence pointer** Section 2.7, Figure 6
- **Issue** The AlphaFold3 modeling results are presented as supporting evidence for direct DNA binding, but the confidence metrics for the predicted structures are not reported.
- **Required correction** Report AlphaFold3 confidence scores (e.g., pLDDT, PAE) for the predicted protein-DNA complexes to allow readers to assess the reliability of the models.

## Risk / unsupported claims
- The claim that PS functions as a DNA-binding regulatory protein is not fully supported due to the low purity of protein preparations used in EMSA experiments
- The proposed consensus binding motif 5'-(G/T)GG(G/T)A-3' is derived from only three modeled sequences and lacks experimental validation
- The causal relationship between PS/DM binding to promoters and changes in gene expression is not established
- The physiological relevance of PS binding to the identified promoter sequences in Arabidopsis is speculative, as the endogenous targets and conditions under which PS regulates these genes are unknown
- The claim that DM has reduced DNA-binding affinity is not quantitatively supported
- The co-immunoprecipitation data are presented without functional validation of the identified interactions