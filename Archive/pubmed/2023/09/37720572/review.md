## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, conclusion, and figure legends, as provided.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and internal consistency of the claims as presented. No external data, supplementary files, or raw datasets were accessed.
- **Shared manuscript claim summary** The authors claim that 20(S)-protopanaxadiol (PPD), a ginsenoside metabolite, directly binds the transcription factor PURA in brain tissue, and that this binding upregulates the transcription of PURA target genes implicated in cognitive function, thereby providing a mechanistic basis for PPD's cognitive benefits.
- **Visible evidence base** DARTS with mass spectrometry, biolayer interferometry (BLI) binding and kinetic analyses, molecular docking, site-directed mutagenesis, qRT-PCR of selected target genes in rat brain tissues, and bioinformatics enrichment (GO/KEGG) of a protein interaction network.
- **Missing materials affecting confidence** Supplementary methods, supplementary figures (including mutagenesis validation gels), raw mass spectrometry data, full BLI sensorgrams, statistical details for qRT-PCR (e.g., exact P values, dispersion), and details of the transcription factor library intersection. These are referenced but not provided.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant question, namely the identification of a direct transcription factor target for a bioactive ginsenoside metabolite in the brain. The combination of DARTS, BLI, docking, and mutagenesis is a reasonable workflow for target identification. However, the evidence as presented has several gaps that prevent full support of the central claim. The DARTS data are not shown in sufficient detail to assess specificity, the BLI affinity values are modest and lack appropriate controls, the mutagenesis data are only summarized without validation of protein integrity, and the qRT-PCR results show selective effects that are not fully consistent with a simple model of PURA activation. The bioinformatics analysis is descriptive and does not establish a causal link to cognitive improvement. The manuscript would benefit from additional controls, quantitative rigor, and a more cautious interpretation of the in vivo relevance.
- **Who would be interested in the results, and why** Researchers studying ginsenoside pharmacology, natural product target identification, transcription factor regulation in the CNS, and potential therapeutic targets for cognitive dysfunction. The methodological combination of DARTS with BLI and mutagenesis may also interest investigators working on drug-target interactions for other natural products.
- **Major strengths** The study addresses an important gap in understanding how ginsenoside metabolites exert central effects. The use of orthogonal methods (DARTS, BLI, docking, mutagenesis) to support a direct interaction is commendable. The focus on a transcription factor as a target is novel and potentially impactful. The in vivo qRT-PCR data, while limited, provide some translational relevance.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (DARTS specificity), R1-M2 (BLI affinity and controls), R1-M3 (mutagenesis validation), R1-M4 (qRT-PCR causal link), R1-M5 (bioinformatics overinterpretation).
- **Assessment against Nature-style criteria** Originality is moderate; the target identification is novel but the approach is not unprecedented. Scientific importance is potentially high if the claims are fully substantiated, but the current evidence is insufficient. Interdisciplinary readership is plausible given the intersection of pharmacology, neurobiology, and chemical biology. Technical soundness is currently limited by missing controls and incomplete data presentation. Readability for nonspecialists is acceptable, though some methods are described tersely.
- **Recommendation posture** Currently not established from the provided evidence. Supportive if the technical concerns are resolved with additional data and more cautious interpretation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that DARTS identified three transcription factors, including PURA, as potential targets of ginsenosides in brain tissue.
- **Evidence pointer** Results section, Figure 1
- **Concern** The DARTS results are presented only as a heatmap and Venn diagram. No information is provided on the criteria for selecting the 355 differential proteins, the magnitude of changes, statistical thresholds, or the reproducibility of the mass spectrometry analysis. The specificity of the DARTS signal for ginsenosides versus vehicle is not demonstrated with representative gels or spectra. Without these details, the identification of PURA as a candidate target is not robustly supported.
- **Why it matters** DARTS is prone to false positives and requires careful validation. If the initial screening is not rigorously controlled, all downstream claims about PURA as a target are weakened.
- **Resolution test** Provide representative DARTS gels or proteomic data showing dose-dependent protection of PURA by ginsenosides, along with statistical analysis of differential proteins and a clear description of the filtering criteria.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor
- **Claim pointer** The authors claim that PPD has a high affinity for PURA, with a KD of 6.26 ± 0.25E-6 M, and that this binding is specific.
- **Evidence pointer** Results section, Figure 2
- **Concern** The reported KD of approximately 6 micromolar is modest and may not support the term "high affinity." The BLI experiments lack critical controls, such as a negative control protein (e.g., a non-PURA protein) to demonstrate binding specificity, and a competition assay with an excess of unlabeled PPD or a structurally related compound. The kinetic data are shown for a single experiment, and no information is given on the fitting model or the reproducibility across replicates.
- **Why it matters** A micromolar affinity, without proper controls, could reflect nonspecific binding or artifacts of the assay. The claim of specific targeting of PURA by PPD is central to the manuscript.
- **Resolution test** Include BLI experiments with a negative control protein, show replicate sensorgrams with fitting statistics, and perform a competition assay to confirm specific binding. Discuss the physiological relevance of the measured KD.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors claim that mutations of S102 and M103 in PURA abolish binding to PPD, identifying these as key residues.
- **Evidence pointer** Results section, Figure 4
- **Concern** The mutagenesis data are presented only as KD values or "no concentration dependence" for each mutant. No data are shown to confirm that the mutant proteins are properly folded and expressed at levels comparable to wild-type. The absence of binding for S102A and M103A could be due to protein misfolding or instability rather than specific loss of the interaction. Additionally, the statement that other mutants showed "not particularly significant" differences is vague and lacks statistical analysis.
- **Why it matters** Without validation of mutant protein integrity, the conclusion that S102 and M103 are essential for binding is not justified. This is a key piece of evidence for the specificity of the interaction.
- **Resolution test** Provide SDS-PAGE or circular dichroism data for all purified proteins, and include a positive control (e.g., a known binding partner) to demonstrate that the mutants retain functional activity. Perform statistical comparison of KD values across mutants.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The authors claim that PPD upregulates the transcription of PURA target genes in brain tissue, implying a functional consequence of binding.
- **Evidence pointer** Results section, Figure 5
- **Concern** The qRT-PCR data show that PPD increases the expression of some target genes (e.g., APP, Mbp, Fe65) in a tissue- and dose-dependent manner, but not all genes in all conditions. The authors do not demonstrate that this upregulation is dependent on PURA binding. For example, no experiments are shown where PURA is knocked down or inhibited to test whether the PPD effect is lost. The link between PPD binding to PURA and transcriptional changes is therefore correlative, not causal.
- **Why it matters** The central claim of the manuscript is that PPD acts through PURA to affect cognitive function. Without a loss-of-function experiment, the data do not exclude alternative mechanisms.
- **Resolution test** Perform PURA knockdown or overexpression experiments in relevant cell lines or in vivo models, and show that the PPD-mediated changes in target gene expression are abolished or enhanced accordingly.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The authors claim that bioinformatics analysis shows that PURA target proteins are involved in learning and memory, supporting a role in cognitive function.
- **Evidence pointer** Results section, Figure 6
- **Concern** The GO and KEGG enrichment analyses are based on a small set of proteins (PURA, PURB, five target genes, and 32 interacting proteins). The enrichment of terms such as "learning or memory" and "Alzheimer's disease" is expected given the selected input proteins, and the analysis does not provide independent evidence for a functional role. The authors do not discuss the statistical significance or the background correction of the enrichment.
- **Why it matters** The bioinformatics results are used to strengthen the cognitive relevance of the findings, but as presented, they are circular and do not add substantive support.
- **Resolution test** Provide a more rigorous enrichment analysis with appropriate background sets and multiple testing correction, and discuss the limitations of the approach.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1C
- **Evidence pointer** Results section, Figure 1
- **Issue** The text states that three transcription factors were identified, but Figure 1C lists four transcription factors. This discrepancy is confusing.
- **Required correction** Clarify whether three or four transcription factors were identified, and correct the figure or text accordingly.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** qRT-PCR data
- **Evidence pointer** Results section, Figure 5
- **Issue** The statistical analysis is described as one-way ANOVA, but the figure legend does not specify the post hoc test used or the exact P values for each comparison. The use of asterisks without a clear scale is not sufficient.
- **Required correction** Provide exact P values or a clear description of the significance thresholds, and specify the post hoc test used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract, Discussion
- **Issue** The term "high affinity" is used to describe the PPD-PURA interaction, but the measured KD of approximately 6 micromolar is not typically considered high affinity in the context of drug-target interactions.
- **Required correction** Use a more neutral term such as "moderate affinity" or provide context for why this affinity is considered high in this context.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section
- **Evidence pointer** Methods, DARTS and BLI
- **Issue** The methods for DARTS and BLI are described as "detailed procedures are described in Supplementary Methods," but the supplementary material is not provided. This makes it difficult to assess the technical quality of these experiments.
- **Required correction** Include the supplementary methods or provide sufficient detail in the main text to allow replication.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Figure 4
- **Evidence pointer** Results section, Figure 4
- **Issue** The figure legend states that data are shown as mean ± SEM (n = 3), but the number of independent experiments is not clear. It is also unclear whether the KD values are from independent protein preparations or repeated measurements on the same preparation.
- **Required correction** Clarify the experimental design and the number of independent replicates.

## Risk / unsupported claims
- The claim that PURA is a transcription target of PPD in the brain is not fully supported because the DARTS data are not shown in sufficient detail and the BLI affinity is modest without adequate controls.
- The claim that PPD upregulates PURA target genes through direct binding is not established, as no loss-of-function experiments are provided.
- The claim that the findings have implications for treating cognitive dysfunction is speculative, as no behavioral or functional cognitive data are presented.
- The bioinformatics analysis is used to support cognitive relevance, but the analysis is circular and does not provide independent evidence.
- The statement that "PURA may play a regulatory role in some AD-related genes" is based on cited literature, not on data from this study, and should be clearly distinguished from the authors' own findings.