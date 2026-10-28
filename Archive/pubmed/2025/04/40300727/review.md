## Review setup
- **Input scope** Full manuscript text (abstract, results, discussion, experimental procedures, data availability, supporting information list)
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text. No external validation or replication of methods was performed.
- **Shared manuscript claim summary** The authors report that the highly divergent TBP homolog from *Giardia intestinalis* (gTBP) preferentially binds single-stranded DNA (ssDNA) over double-stranded DNA, and does so via two distinct modes: a sequence-dependent "A mode" targeting poly(G) tracts (potentially involving G-quadruplex structures) and a structure-dependent "B mode" targeting flexible ssDNA regions characterized by low base stacking energy. The authors propose that these unconventional properties may reflect novel roles for TBP in *Giardia* transcription.
- **Visible evidence base** EMSA binding assays (Figures 3, 4, 6–10), PBM data (Figure 5), AlphaFold2 structural prediction (Figure 1), AlphaFold3 docking (Figure S3), subcellular fractionation and immunofluorescence (Figure 2), native PAGE (Figure S6), base stacking energy calculations (Table 1), and a polynomial regression model (Figure S7).
- **Missing materials affecting confidence** Raw PBM data (File S3), full EMSA gel images for all replicates, detailed AlphaFold3 input parameters and output metrics, the complete list of 36 sequences used for regression training (File S2), and the polynomial regression model code and hyperparameters. The manuscript states n=2 or n=4 for key experiments, but individual data points are not shown.

## Reviewer
- **Overall assessment** This manuscript presents a potentially interesting and novel observation: a TBP homolog that preferentially binds ssDNA in two distinct modes. The work combines biochemical, biophysical, and computational approaches. However, the evidence for the two binding modes is largely indirect, and several key claims—particularly regarding the biological relevance and the mechanistic distinction between the A and B modes—are not fully supported by the data presented. The manuscript would benefit from more direct biophysical characterization (e.g., ITC, SPR, or NMR) and from experiments that more clearly separate sequence-dependent from structure-dependent binding.
- **Who would be interested in the results, and why** Researchers studying TBP biology, transcription initiation mechanisms, and the evolution of transcription factors. The work may also interest scientists studying ssDNA-binding proteins and the role of DNA structure in protein–DNA recognition. The potential link to *Giardia* biology and the unusual promoter architecture of this parasite could attract parasitologists.
- **Major strengths**
  1. The identification of a TBP homolog with a clear preference for ssDNA over dsDNA is unexpected and challenges conventional views of TBP function.
  2. The use of base stacking energy as a predictive tool for ssDNA binding is a creative and potentially useful approach.
  3. The combination of PBM, EMSA, and computational modeling provides a multi-pronged approach to the problem.
  4. The nuclear localization data (Figure 2) help establish a plausible cellular context for the observed biochemical activity.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence for A mode (poly(G) binding)
  - **Claim pointer** "gTBP binds as an oligomer to ssDNA that contains four or more consecutive guanine bases" (A mode)
  - **Evidence pointer** Figures 5–8, PBM data (File S3)
  - **Concern** The evidence for the A mode is largely based on PBM data and EMSA competition experiments. However, the PBM data are not shown in the main text (only motifs are presented), and the EMSA experiments (Figures 7, 8) rely on competition assays that are indirect. The claim that gTBP binds as an "oligomer" to poly(G) tracts is not directly demonstrated. The authors do not show a stoichiometric analysis or a clear molecular weight determination of the gTBP–poly(G) complex. Furthermore, the possibility that the observed binding to poly(G) is due to non-specific electrostatic interactions or to the formation of G-quadruplex structures in the DNA (which the authors themselves suggest) is not rigorously excluded.
  - **Why it matters** The A mode is one of the two central claims of the manuscript. Without direct evidence for oligomeric binding and without a clear distinction between sequence-specific recognition and structure-specific recognition (e.g., G-quadruplex), the mechanistic basis of the A mode remains speculative.
  - **Resolution test** Provide direct binding assays (e.g., ITC or SPR) with defined poly(G) oligonucleotides of varying lengths and with mutant sequences that disrupt G-quadruplex formation. Perform analytical ultracentrifugation or size-exclusion chromatography coupled with multi-angle light scattering to determine the stoichiometry of the gTBP–poly(G) complex. Show the raw PBM data and demonstrate that the A mode is dependent on the number of consecutive Gs in a controlled sequence context.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence for B mode (structure-dependent binding)
  - **Claim pointer** "gTBP binds as a monomer to ssDNA in a manner that is dependent on DNA structural properties" (B mode)
  - **Evidence pointer** Figures 9–11, Table 1
  - **Concern** The B mode is defined by a correlation between low base stacking energy and binding, but the evidence is correlative. The authors generate de novo sequences with similar base stacking energy profiles and show they compete for binding, but this does not prove that base stacking energy is the causal determinant. Other sequence features (e.g., nucleotide composition, propensity for secondary structure) may correlate with the observed binding. The claim that gTBP binds as a "monomer" in the B mode is not directly tested. The regression model (Figure S7) has an R² of 0.80 on training data but performs poorly on test data (R² = 0.15), which the authors acknowledge but do not fully address. This suggests the model is overfit and that the identified features may not be generalizable.
  - **Why it matters** The B mode is the second central claim. If the structural basis of this mode is not clearly established, the manuscript's main thesis is weakened. The poor predictive performance of the model on test data raises questions about whether the identified "rules" for B-mode binding are robust.
  - **Resolution test** Perform direct binding assays with a panel of designed sequences that systematically vary base stacking energy while controlling for other features (e.g., nucleotide composition, GC content). Use mutagenesis to disrupt predicted low-base-stacking regions and show a corresponding loss of binding. Provide a more rigorous validation of the regression model, including cross-validation and testing on an independent set of sequences not used in training.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Biological relevance
  - **Claim pointer** "we present a potential new perspective on eukaryotic transcription regulation based on our findings around unconventional gTBP-ssDNA binding"
  - **Evidence pointer** Discussion section
  - **Concern** The manuscript does not provide any direct evidence that the observed ssDNA binding activity of gTBP is relevant to transcription in *Giardia*. The nuclear localization (Figure 2) is consistent with a role in transcription, but no functional experiments (e.g., knockdown, overexpression, or reporter assays) are presented. The link between the in vitro binding modes and in vivo function is entirely speculative.
  - **Why it matters** The title and abstract imply a significance for transcription regulation. Without functional data, the biological relevance of the findings remains unsubstantiated, and the manuscript's impact is diminished.
  - **Resolution test** Perform experiments to link gTBP binding to transcriptional activity, such as chromatin immunoprecipitation (ChIP) to identify gTBP binding sites in the *Giardia* genome, or reporter assays with promoters containing or lacking the identified binding motifs. Alternatively, knockdown or knockout of gTBP could be used to assess effects on gene expression.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Figure 3
  - **Evidence pointer** Figure 3B
  - **Issue** The EMSA gels in Figure 3B are representative (n=2), but individual data points are not shown. The quantification in Figure 3D is based on only two replicates, which is insufficient to support the statistical claims.
  - **Required correction** Provide individual data points and error bars for all replicates. Increase the number of replicates or provide a statistical test to support the claims.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Methodology
  - **Affected element** AlphaFold3 modeling
  - **Evidence pointer** Figure S3, File S5
  - **Issue** The AlphaFold3 modeling is used to support the claim that gTBP binds ssDNA, but the details of the modeling (e.g., input sequences, number of models, selection criteria) are not fully described. The ipTM and pTM scores are mentioned, but the interpretation of these scores in the context of ssDNA binding is not discussed.
  - **Required correction** Provide a more detailed description of the AlphaFold3 modeling, including the input sequences, the number of models generated, and the criteria for selecting the best model. Discuss the limitations of AlphaFold3 for modeling protein–ssDNA interactions.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** "A mode" and "B mode"
  - **Evidence pointer** Throughout
  - **Issue** The terms "A mode" and "B mode" are introduced without a clear definition of what distinguishes them at a molecular level. The A mode is described as sequence-dependent (poly(G)) and the B mode as structure-dependent (flexibility), but the distinction is not always clear in the data.
  - **Required correction** Provide a clear operational definition of the two modes, perhaps with a schematic figure, and ensure that the data are consistently interpreted in terms of these definitions.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Statistical analysis
  - **Affected element** Figure 6C
  - **Evidence pointer** Figure 6C
  - **Issue** The Hill coefficients and KD values are reported with standard errors, but the number of replicates and the fitting procedure are not fully described. The claim of positive cooperativity (Hill coefficient ~2) is based on a single experiment.
  - **Required correction** Provide details on the number of replicates, the fitting procedure, and the statistical significance of the Hill coefficients. Consider performing independent replicates to confirm the cooperativity.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Discussion
  - **Evidence pointer** Discussion section
  - **Issue** The discussion of the potential biological roles of gTBP-ssDNA binding is brief and does not fully engage with the existing literature on TBP-ssDNA interactions or on the unusual transcription machinery of *Giardia*.
  - **Required correction** Expand the discussion to more thoroughly consider alternative interpretations and to place the findings in the context of what is known about TBP-ssDNA binding in other organisms and about *Giardia* transcription.
- **Technical failings that need to be addressed before the case is established**
  1. The stoichiometry of gTBP binding to poly(G) (A mode) is not determined.
  2. The distinction between sequence-specific and structure-specific binding in the A mode is not clearly established.
  3. The regression model for B-mode binding is overfit and does not generalize to test data.
  4. The claim of positive cooperativity in B-mode binding is based on limited data.
  5. The biological relevance of the observed ssDNA binding is not tested experimentally.
- **Assessment against Nature-style criteria**
  - **Originality** The finding that a TBP homolog preferentially binds ssDNA in two distinct modes is original and unexpected. However, the conceptual framework (ssDNA binding by transcription factors) is not entirely new.
  - **Scientific importance** The work has the potential to inform our understanding of TBP evolution and the diversity of transcription mechanisms. However, the lack of functional data limits the immediate importance.
  - **Interdisciplinary readership** The work will primarily appeal to biochemists and molecular biologists. The computational aspects (base stacking energy modeling) may attract biophysicists, but the overall impact is likely to be within a specialized niche.
  - **Technical soundness** The experimental design is generally sound, but several key claims are not fully supported by the data. The reliance on indirect assays (competition EMSA) and the poor performance of the predictive model are significant weaknesses.
  - **Readability for nonspecialists** The manuscript is clearly written and the concepts are accessible. However, the extensive use of specialized terminology (e.g., "base stacking energy," "LBSR") may be challenging for readers outside the field.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents an interesting observation, but the central claims regarding the two binding modes are not sufficiently supported. Major revisions and additional experiments are required before the case is established.