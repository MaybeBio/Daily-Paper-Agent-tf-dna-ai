## Review setup
- **Input scope** Full manuscript text (abstract, results, discussion, methods) as provided
- **Assessment boundary** Scientific content, technical soundness, and claims as presented in the provided text; no supplementary figures, tables, or data files were available for inspection
- **Shared manuscript claim summary** The authors characterize DNA-binding specificities of mammalian BEN domain proteins, including NACC1, NACC2, and BEND3, using protein-binding microarrays and HT-SELEX; determine a crystal structure of the BEND3-BD4 domain bound to DNA; and propose a classification of BEN domains into type I, type II, and type 0 based on structural and functional differences
- **Visible evidence base** Main text figures referenced (Figures 1–7), Table 1 (crystallographic statistics), Supplemental Figures S1–S9, Supplemental Tables S1–S2, Supplemental Data Sets S1–S4 (all referenced but not provided)
- **Missing materials affecting confidence** All supplementary figures, tables, and data sets; crystallographic coordinates (PDB 7W27); raw HT-SELEX data; ChIP-seq data details; methodological parameters for motif discovery; statistical details for reporter assays

## Reviewer
- **Overall assessment** This manuscript presents a substantial body of work characterizing DNA-binding specificities of mammalian BEN domain proteins, with a high-resolution crystal structure of BEND3-BD4 bound to DNA. The combination of in vitro binding assays, structural biology, and genomic analysis is commendable and the findings are likely to be of interest to the transcription factor and chromatin biology communities. However, the provided text lacks sufficient detail in several critical areas, particularly regarding the quantitative validation of binding specificities, the statistical robustness of the reporter assays, and the rigor of the structural comparisons. The claim that BEND3-BD4 motifs underlie known genomic occupancy is supported by correlative evidence but the causal link is not fully established. The manuscript is technically sound in its core structural work but the functional conclusions require additional experimental support or more cautious interpretation.

- **Who would be interested in the results, and why** Researchers studying transcription factor DNA-binding specificity, particularly those interested in novel DNA-binding domain families; chromatin biologists studying heterochromatin organization and gene repression; structural biologists interested in protein-DNA recognition mechanisms; and investigators studying the BEN domain family across metazoans and viruses. The proposed type I/type II/type 0 classification provides a framework that could be broadly useful.

- **Major strengths** 1) The combination of multiple complementary approaches (PBM, HT-SELEX, crystallography, reporter assays, ChIP-seq analysis) provides a multi-layered view of BEN domain function. 2) The high-resolution (1.5 Å) crystal structure of BEND3-BD4 bound to DNA is a significant technical achievement. 3) The identification of a specific DNA-binding motif for BEND3-BD4 and its validation at known genomic targets (rDNA, CALR) provides a concrete link between in vitro specificity and in vivo occupancy. 4) The proposed classification of BEN domains into functional subtypes is a useful conceptual contribution. 5) The use of AlphaFold2 and RoseTTAFold predictions to extend structural insights beyond experimentally determined structures is forward-looking.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of binding specificity determination
- **Claim pointer** The authors claim that PBM and HT-SELEX "yielded mutually supportive data" and that NACC1 and NACC2 BEN domains "bind to very similar, partially palindromic, monomeric sites with an ACATGY core consensus sequence."
- **Evidence pointer** Results section "Modes of sequence-specific DNA binding by NACC family BEN domain proteins"; Figure 2; Supplemental Figure S1; Supplemental Table S2
- **Concern** The text states that motifs were "constructed semimanually with parameters shown on headers of the motifs in Supplemental Table S2." This is a non-standard and potentially subjective approach to motif construction. The manuscript does not provide quantitative measures of motif enrichment significance (e.g., E-values), nor does it describe how the semimanual construction was validated. The claim that PBM and HT-SELEX are "mutually supportive" is presented without showing the actual comparison metrics. The previous report of NACC1 binding to a different motif (Nakayama et al. 2020) is mentioned but the discrepancy is not quantitatively reconciled.
- **Why it matters** The central claim of the manuscript is that specific BEN domains recognize specific DNA sequences. If the motif determination methodology is not rigorously quantitative and reproducible, the downstream structural and functional interpretations are built on an uncertain foundation. The field standard for transcription factor motif determination requires statistical enrichment metrics and independent validation.
- **Resolution test** Provide E-values or similar significance metrics for all reported motifs; show quantitative comparison of PBM and HT-SELEX derived motifs (e.g., correlation coefficients of position weight matrices); demonstrate that the semimanual motif construction does not introduce bias by comparing to fully automated methods; include a quantitative comparison of the NACC1 motif reported here versus that reported by Nakayama et al. 2020.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal link between BD4 motif and genomic occupancy
- **Claim pointer** The authors claim that "both of the known BEND3 genomic targets are directly explained by the presence of perfect matches to the preferred binding sites determined from in vitro assays" and that BEND3 can repress newly identified targets via BD4 sites.
- **Evidence pointer** Results sections "The BEND3-BD4 motif underlies known examples of BEND3 genomic occupancy" and "Genome-wide enrichment of the BD4 motif in BEND3 ChIP-seq data"; Figures 3C–H, 4A–E; Supplemental Figures S2, S3
- **Concern** The evidence presented is largely correlative. For the rDNA and CALR loci, the presence of a BD4 motif match is shown to coincide with BEND3 occupancy, but no direct test (e.g., mutation of the motif in the endogenous locus, or a reporter assay with the motif as the sole variable) is described for these loci. The reporter assays for newly identified targets (Tdrd7, Cdrcn1a, Actg1, Znf316) are mentioned but the data are not shown in the provided text. The claim that BEND3 represses these targets is based on overexpression experiments, which may not reflect endogenous function. The ChIP-seq analysis shows enrichment of BD4-like motifs in BEND3 peaks, but the text does not report the fraction of peaks containing the motif, the statistical significance of the enrichment, or a control analysis using random genomic regions.
- **Why it matters** The manuscript aims to establish that BEND3-BD4 sequence-specific DNA binding is functionally relevant for genomic targeting. Without direct causal evidence, the conclusion that BD4 motifs "underlie" BEND3 genomic occupancy is overstated. The distinction between correlation and causation is critical for the manuscript's contribution to understanding BEND3 function.
- **Resolution test** Show that mutation of BD4 motifs in the rDNA or CALR reporters abolishes BEND3-mediated repression. Provide statistical analysis of BD4 motif enrichment in BEND3 ChIP-seq peaks versus matched genomic controls. For the newly identified targets, show that the reporter assays are dependent on intact BD4 motifs and that the effect is specific to BEND3 (e.g., using a BD4-mutant BEND3).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Structural basis for specificity
- **Claim pointer** The authors state that the crystal structure reveals "the specific binding pattern of the BEND3-BD4 domain with its 5′-ACCCACGCAG-3′/3′-TGGGTGCGTC-5′ binding site" and that base-specific interactions are formed by residues clustered in the C-terminal 807–815 segment.
- **Evidence pointer** Results section "Structural basis for sequence-specific DNA binding by the BEND3-BD4 domain"; Figure 5; Table 1; Supplemental Figures S5–S7
- **Concern** The text describes the structure but does not provide a detailed analysis of the base-specific contacts. It is not clear which amino acid residues contact which DNA bases, nor is there a discussion of how these contacts confer sequence specificity. The validation of the structure via mutagenesis is limited to a triple mutant (E807V, R810L, R814L) in reporter assays, but the text does not show whether these mutations affect DNA binding directly (e.g., by electrophoretic mobility shift assay or isothermal titration calorimetry). The comparison with the Insv-BEN-DNA complex is descriptive but does not provide a quantitative structural comparison (e.g., root-mean-square deviation of the DNA-binding regions).
- **Why it matters** A structural study should provide mechanistic insight into how sequence specificity is achieved. Without a detailed analysis of base-specific contacts and experimental validation of the key residues' roles in DNA binding, the structural contribution is incomplete. The claim that the structure explains specificity requires demonstration that the identified contacts are both necessary and sufficient for sequence discrimination.
- **Resolution test** Provide a detailed figure or table listing all base-specific contacts (hydrogen bonds, van der Waals contacts) between protein residues and DNA bases. Show that the triple mutant (or individual mutants) abolishes or reduces DNA binding in a direct binding assay. Provide a quantitative structural comparison with the Insv-BEN-DNA complex, including RMSD calculations for the DNA-binding regions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the type I/type II classification
- **Claim pointer** The authors propose "two subclasses of DNA-binding BEN domains (Insv-BEN, Bsg25A-BEN, and NACC-BEN as representatives of type I, and BEND3-BD4 as a prototype of type II)" and distinguish them from "type 0" non-DNA-binding domains.
- **Evidence pointer** Results section "BEN domains interact with DNA through distinct strategies"; Figure 7; Supplemental Figure S9
- **Concern** The classification is based on a limited number of experimentally characterized BEN domains. The text states that "many human BEN domains" bear similarities to type I based on AlphaFold2 predictions, but the criteria for this classification are not clearly defined. It is unclear whether the structural differences between type I and type II are consistently observed across all members of each proposed class. The functional significance of the classification is not tested; for example, it is not shown whether type I domains all bind DNA with similar specificity or whether type II domains share functional properties beyond structural similarity.
- **Why it matters** The proposed classification is a conceptual contribution that could guide future studies. However, if the classification is based on limited data and unclear criteria, it may not be robust or useful. The manuscript should provide clear, testable criteria for the classification and acknowledge the limitations of the current dataset.
- **Resolution test** Define explicit structural and/or sequence criteria for type I, type II, and type 0 classification. Apply these criteria systematically to all human and Drosophila BEN domains. Test whether the classification predicts functional properties (e.g., DNA-binding specificity, subcellular localization) in a systematic manner.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** HT-SELEX methodology
- **Evidence pointer** Methods section "High-throughput (HT-SELEX) analysis"
- **Issue** The description of the HT-SELEX procedure is brief and lacks key parameters such as the number of selection rounds, the complexity of the randomized library, the sequencing depth, and the number of biological replicates.
- **Required correction** Provide a more detailed description of the HT-SELEX protocol, including all relevant parameters, or cite a detailed protocol paper.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Reporter assays
- **Evidence pointer** Results sections "The BEND3-BD4 motif underlies known examples of BEND3 genomic occupancy" and "Structural basis for sequence-specific DNA binding by the BEND3-BD4 domain"; Figure 5E
- **Issue** The text states that reporter assays were performed with "three biological replicates" but does not report the statistical test used, the error bars shown, or the significance thresholds.
- **Required correction** Report the statistical methods used for reporter assays, including the test, the number of replicates, and the significance criteria. Add error bars and significance indicators to the figures.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** ChIP-seq analysis
- **Evidence pointer** Methods section "ChIP-seq data analysis"
- **Issue** The ChIP-seq data are referenced as being from a previous study (Kurniawan et al. 2022), but the analysis parameters (e.g., peak calling thresholds, motif search parameters) are not described in sufficient detail to be reproducible.
- **Required correction** Provide the specific parameters used for peak calling, motif discovery, and motif enrichment analysis, or clearly reference the relevant methods from the original study.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of structural comparison
- **Affected element** Comparison with Insv-BEN-DNA complex
- **Evidence pointer** Results section "Comparison of the BEND3-BD4/DNA complex with other solved BEN domain complexes"; Figure 6
- **Issue** The comparison between BEND3-BD4 and Insv-BEN is descriptive and does not include a quantitative measure of structural similarity or difference. The statement that the "helical segments align well" is vague.
- **Required correction** Provide RMSD values for the structural alignment and clearly state the criteria used to define "well aligned."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Issue** The discussion does not acknowledge the limitations of the study, such as the in vitro nature of the binding assays, the potential for other BEND3 domains (BD1, BD2, BD3) to contribute to DNA binding, or the lack of in vivo validation for most newly identified targets.
- **Required correction** Add a paragraph discussing the limitations of the study and the questions that remain to be addressed.

## Risk / unsupported claims
- The claim that PBM and HT-SELEX yielded "mutually supportive data" is not quantitatively demonstrated in the provided text.
- The claim that BEND3-BD4 motifs "underlie" known BEND3 genomic occupancy at rDNA and CALR is correlative; no causal test is described.
- The claim that BEND3 represses newly identified targets (Tdrd7, Cdrcn1a, Actn1, Znf316) is based on overexpression experiments whose data are not shown in the provided text.
- The classification of BEN domains into type I, type II, and type 0 is based on limited experimental data and the criteria for classification are not clearly defined.
- The statement that "BEND3-BD4 protein only forms base-specific interactions with the DNA duplex in the major groove" is a strong claim that requires the full list of contacts to be verified.
- The use of AlphaFold2 and RoseTTAFold predictions to infer functional properties of BEN domains is reasonable but should be clearly labeled as predictions, not experimental determinations.
- The claim that "BEND3 can directly and specifically repress a target gene via BD4 motif matches" is supported by reporter assays but the text does not show that the repression is direct (i.e., no evidence that BEND3 is bound to the reporter in cells).

## Assessment against Nature-style criteria
- **Originality** The manuscript addresses a gap in knowledge regarding DNA-binding specificities of mammalian BEN domain proteins. The identification of a specific motif for BEND3-BD4 and the structural characterization of this interaction are novel contributions. The proposed type I/type II/type 0 classification is a new conceptual framework. However, the finding that BEN domains bind DNA is not entirely new, given prior work on Drosophila BEN factors and the recent NACC1 study.
- **Scientific importance** The work is important for understanding how BEN domain proteins, particularly BEND3, are recruited to specific genomic loci. The link between in vitro specificity and known genomic targets (rDNA, CALR) provides a concrete example of how this protein family functions. The potential connection to methylation-sensitive DNA binding and heterochromatin regulation is of broad interest.
- **Interdisciplinary readership** The manuscript is likely to appeal to transcription factor biologists, chromatin researchers, structural biologists, and those interested in gene regulation. The combination of biochemistry, structural biology, and genomics broadens its potential audience. However, the specialized nature of the topic may limit its appeal to a very broad readership.
- **Technical soundness** The structural determination at 1.5 Å resolution appears technically sound based on the reported R-factors. The use of multiple complementary binding assays is appropriate. However, the lack of quantitative detail in the motif discovery and the limited validation of the functional claims reduce the overall technical rigor. The statistical reporting in the reporter assays is insufficient.
- **Readability for nonspecialists** The manuscript is generally well-written and the logic is clear. However, the text assumes familiarity with transcription factor motif discovery, structural biology, and ChIP-seq analysis. The abstract provides a good summary but the results section is dense and may be challenging for nonspecialists. The figures are referenced appropriately but cannot be evaluated from the text alone.

## Recommendation posture
Supportive if technical concerns are resolved. The core structural work and the identification of BEND3-BD4 DNA-binding specificity are valuable contributions. However, the manuscript currently overstates the causal link between the identified motif and BEND3 genomic occupancy, and the quantitative rigor of the binding specificity determination needs to be strengthened. The authors should provide additional experimental evidence (e.g., direct binding assays with mutant proteins, motif mutation in reporter assays) and more detailed statistical reporting to fully support their claims. The proposed classification scheme is interesting but requires clearer criteria and broader validation.