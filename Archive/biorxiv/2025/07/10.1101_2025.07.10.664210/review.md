## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, discussion, conclusions) provided as a single document. No figures, tables, or supplementary materials were included in the submission.
- **Assessment boundary** The review is limited to the scientific content, methodology, data interpretation, and internal consistency of the provided text. Claims referring to figures, tables, or statistical analyses are assessed based on their textual description only.
- **Shared manuscript claim summary** The authors propose that six unclassified BRCA1 DBD variants (T374I, K408E, N417S, N909I, M1008I, R1028H) can be assigned pathogenicity status by comparing their DNA binding affinities (ssDNA, dsDNA, G4 DNA) and cellular phenotypes (menadione and bleomycin sensitivity) to six known pathogenic variants (Q356H, F461L, R496H, D940Y, S1027N, E1038G) and wild-type BRCA1 DBD constructs.
- **Visible evidence base** Text descriptions of biolayer interferometry (BLI) binding affinity measurements, neutral comet assay results, cell survival data, and AlphaFold 2 structural predictions. Reference is made to Figures 1-11 and Tables 1-5, none of which were provided.
- **Missing materials affecting confidence** All figures, tables, raw binding affinity values, statistical test details, replicate numbers, and full experimental datasets. The absence of these materials prevents independent verification of the reported quantitative results and statistical claims.

## Reviewer
- **Overall assessment** The manuscript addresses a clinically relevant question, namely the functional classification of BRCA1 variants of unknown significance. The experimental design, combining in vitro DNA binding measurements with cellular assays, is conceptually sound. However, the presented text contains several critical gaps that prevent the conclusions from being established. The binding affinity data are reported as association constants (K) rather than dissociation constants (Kd), which is inconsistent with the stated methodology. The statistical analysis is incomplete, with only one p-value reported across the entire results section. Most importantly, the authors' central claim, that altered DNA binding affinity correlates with pathogenicity, is not supported by the data as presented. For example, the pathogenic variant F461L shows comparable dsDNA binding to wild-type, while the putatively neutral variant K408E shows a diminished dsDNA affinity, yet both are assigned their respective classifications. The cellular data are incomplete for several key variants, including two of the three pathogenic DBD1 variants, making direct comparison impossible. The structural predictions from AlphaFold 2 are presented descriptively without quantitative metrics or validation. The manuscript requires substantial additional data and analysis before the claims can be considered established.

- **Who would be interested in the results, and why** Clinical geneticists and genetic counselors would be interested in the potential reclassification of BRCA1 VUSs, as this has direct implications for patient risk assessment and management. Cancer biologists studying DNA repair pathways, particularly homologous recombination and the role of BRCA1 in replication fork stability, would find the functional characterization of DBD variants relevant. Researchers investigating the biophysical basis of BRCA1-DNA interactions would be interested in the binding affinity measurements. However, the current incomplete state of the data limits the immediate utility for these audiences.

- **Major strengths** The manuscript addresses a clinically important problem with a clear hypothesis. The experimental approach combines biophysical binding measurements with cellular functional assays, which is appropriate for the research question. The inclusion of both known pathogenic variants and VUSs provides a framework for comparison. The authors acknowledge the limitations of computational predictions and suggest orthogonal validation. The writing is generally clear and the background is well contextualized.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data integrity and reporting
- **Claim pointer** The authors report binding affinities as K values (e.g., "K = 2.92 ± 0.66 × 10^7") throughout the results section, while the methodology describes measuring equilibrium dissociation constants (Kd) via biolayer interferometry.
- **Evidence pointer** Results section, "BRCA1 DBD variants were expressed and purified..." paragraph; Materials and Methods, "Biolayer interferometry (BLI)" section.
- **Concern** The manuscript uses the symbol K without a subscript to denote the measured binding affinity. In the biophysical literature, K typically denotes an association constant (Ka) with units of M^-1, while Kd denotes a dissociation constant with units of M. The reported values (e.g., 10^7) are consistent with association constants, but the text refers to "affinities" without specifying which constant is being reported. This ambiguity is fundamental. If these are association constants, the corresponding Kd values would be in the 10-100 nM range, which is plausible for BRCA1 DBD-DNA interactions. If they are dissociation constants, the values would be implausibly high (10^7 M). The authors must clarify which constant is reported, provide the correct units, and ensure consistency between the methodology and the results.
- **Why it matters** The quantitative binding data are the core experimental output of this manuscript. Without unambiguous reporting of the constant type and units, the data cannot be interpreted, compared to literature values, or used by other researchers. This is a fundamental flaw that affects all subsequent conclusions.
- **Resolution test** The authors must state explicitly whether the reported values are Ka or Kd, provide the appropriate units for each value, and correct the text accordingly. If the values are Ka, the corresponding Kd values should be calculated and reported for clarity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that "cells overexpressed with the R496H variant demonstrated susceptibility to menadione compared to WT BRCA1 (Figure 7B, p < 0.05 in a T-test conducted using comet moment values from comet assaying under treatment conditions of 0, 1, and 100 μM menadione)."
- **Evidence pointer** Results section, "BRCA1 DBD variants were expressed and purified..." paragraph; Figure 7B (not provided).
- **Concern** This is the only statistical test reported in the entire results section. No p-values are provided for any other comparison, including the binding affinity differences between variants and wild-type, the cell survival data for T374I, or the comet assay results for the DBD2 variants. The authors state that T374I showed "significantly decreased cell survival" but provide no statistical support. The DBD2 variants are described as showing "significant DNA damage" without any reported test statistics. The statistical methods section is absent, so the reader cannot determine which tests were used, how multiple comparisons were handled, or what the sample sizes were.
- **Why it matters** The central claim of the manuscript is that certain VUSs are pathogenic based on their functional profiles. This claim rests entirely on the statistical significance of differences between variants and wild-type. Without proper statistical reporting, the conclusions are unsupported. The single p-value reported appears to be from a t-test, which may not be appropriate for multiple treatment conditions or multiple variants.
- **Resolution test** The authors must provide a complete statistical analysis for all reported comparisons, including the specific test used, the sample size (number of independent experiments), the p-values or confidence intervals, and the method for correcting for multiple comparisons. The statistical methods should be described in a dedicated section.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Logical consistency of conclusions
- **Claim pointer** The authors conclude that "the binding patterns, cell phenotypes, and computationally-predicted structures of the variants can also give insight to the functional roles of DBD1 and DBD2 in DNA repair pathways" and assign pathogenicity to VUSs based on these data.
- **Evidence pointer** Discussion section, entire text.
- **Concern** The data presented do not consistently support the pathogenicity assignments. The pathogenic variant F461L shows comparable dsDNA binding to wild-type (K = 1.93 ± 0.55 × 10^7 vs. 2.92 ± 0.66 × 10^7), yet is classified as pathogenic. The VUS K408E shows diminished dsDNA binding (K = 7.09 ± 1.09 × 10^6) but is classified as likely neutral. The authors explain F461L pathogenicity through loss of base stacking, but this explanation is post hoc and not tested. For K408E, the authors state that "the binding characteristics of K408E likely do not affect its DSB repair function," but this is speculative. The cellular data are missing for Q356H, F461L, and N417S, meaning that for three of the six variants, no functional validation is provided. The authors claim that "response to DSBs does not adequately predict pathogenicity" based on the observation that only T374I shows bleomycin sensitivity, but this is a negative conclusion drawn from incomplete data.
- **Why it matters** The manuscript's stated purpose is to classify VUSs. If the classification criteria are applied inconsistently, or if the data do not discriminate between pathogenic and neutral variants, then the classifications are not reliable. The authors must either demonstrate a consistent relationship between the measured parameters and pathogenicity, or acknowledge that the data are insufficient for classification.
- **Resolution test** The authors should provide a clear decision matrix showing how each variant was classified based on the combination of binding affinity, cellular phenotype, and structural prediction. They should also complete the cellular assays for the three variants with missing data, or explicitly state the limitations of the current dataset for those variants.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Structural prediction validation
- **Claim pointer** The authors state that "Predicted structures of the BRCA1 DBD proteins were virtually generated in Alphafold 2" and use these predictions to interpret the effects of mutations on protein structure and function.
- **Evidence pointer** Materials and Methods, "Structural analyses" section; Results, "Predicted structural models of WT DBD1..." paragraph; Figures 8 and 11 (not provided).
- **Concern** The structural analysis relies entirely on AlphaFold 2 predictions without any experimental validation. The authors note in the Conclusions that "AlphaFold models are predicted models and cryo-EM should be used to verify structures," which is appropriate, but this caveat is not reflected in the interpretation of the results. The descriptions of structural changes (e.g., "rotated positioning," "shifted loop") are qualitative and not supported by quantitative metrics such as root-mean-square deviation (RMSD) or per-residue confidence scores (pLDDT). The authors also state that WT DBD2 is "entirely unstructured with no secondary structures present," which is a strong claim that should be supported by the AlphaFold confidence metrics or by experimental evidence.
- **Why it matters** The structural interpretations are used to explain the functional effects of the mutations. If the structural predictions are unreliable, or if the described changes are within the error of the prediction method, then the explanations are not valid. The authors should provide confidence metrics for the predictions and should temper their structural interpretations accordingly.
- **Resolution test** The authors should report the pLDDT confidence scores for the predicted structures, particularly for the regions containing the mutations. They should also provide quantitative measures of structural change (e.g., RMSD) between wild-type and variant structures, and should discuss the limitations of the predictions in the interpretation of the results.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Incomplete data presentation
- **Claim pointer** The authors state that "Data for DBD1 Q356H and F461L remains to be gathered" and "cellular data has not yet been collected" for N417S.
- **Evidence pointer** Results section, "BRCA1 DBD variants were expressed and purified..." paragraph; Discussion section, "DBD1 T374I shows clear similarities..." paragraph.
- **Concern** The manuscript presents binding affinity data for all twelve variants, but cellular phenotype data are missing for three of the six DBD1 variants (Q356H, F461L, N417S). This means that for half of the DBD1 variants, the pathogenicity assessment relies solely on binding affinity and structural prediction, without functional validation. The authors acknowledge this in the text, but the conclusions are presented with confidence that is not warranted by the incomplete dataset.
- **Why it matters** The manuscript's purpose is to classify VUSs. A classification based on a single assay type, without functional validation, is not robust. The missing data should either be collected and presented, or the conclusions should be explicitly limited to the variants with complete datasets.
- **Resolution test** The authors should either complete the cellular assays for the three variants with missing data, or restructure the conclusions to clearly distinguish between variants with complete and incomplete functional characterization.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Abstract, last sentence
- **Evidence pointer** Abstract, "Altogether, these results provide insight into how missense mutations affect the ability of BRCA1 DBDs to facilitate the DNA damage response."
- **Issue** The abstract states that the results "provide insight" but does not state what the insight is. The abstract should summarize the key findings, not just state that findings exist.
- **Required correction** Revise the abstract to include a concise summary of the main findings, such as which variants showed altered binding affinities and which showed cellular phenotypes consistent with pathogenicity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Results section, binding affinity values
- **Evidence pointer** Results, "BRCA1 DBD variants were expressed and purified..." paragraph.
- **Issue** The text uses "K" to denote binding affinity without specifying whether this is Ka or Kd. This is inconsistent with standard biophysical nomenclature and creates ambiguity.
- **Required correction** Define the constant being reported (Ka or Kd) at first use and use the appropriate symbol (Ka or Kd) consistently throughout the text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section, cell survival data
- **Evidence pointer** Results, "DBD1 T374I had significantly decreased cell survival under both menadione and bleomycin treatment (Figures 7C and 7F)."
- **Issue** The claim of significance is made without reporting the statistical test or p-value.
- **Required correction** Provide the statistical test used, the p-value, and the number of independent experiments for this comparison.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure referencing
- **Affected element** Results section, Figure 4
- **Evidence pointer** Results, "BRCA1 DBD variants were expressed and purified from E. coli as discussed in the Materials and Methods (Figure 4)."
- **Issue** Figure 4 is referenced but not described. The reader cannot determine what the figure shows (e.g., SDS-PAGE gel, chromatogram, etc.).
- **Required correction** Add a brief description of what Figure 4 shows, such as "Figure 4 shows a representative SDS-PAGE gel of the purified DBD proteins."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section, overall
- **Evidence pointer** Discussion, entire text.
- **Issue** The discussion does not address the limitations of the study, such as the use of isolated DBD domains rather than full-length BRCA1, the potential effects of the GFP tag on protein function in cellular assays, or the lack of experimental validation of the AlphaFold predictions.
- **Required correction** Add a paragraph discussing the limitations of the study and how they might affect the interpretation of the results.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reference to previous work
- **Affected element** Materials and Methods, "Biolayer interferometry (BLI)" section
- **Evidence pointer** Materials and Methods, "For a detailed explanation of the methodology, please refer to our previous publication (41)."
- **Issue** The manuscript relies on a previous publication for methodological details, but the reference is not provided in the text. The reader cannot access the referenced methodology.
- **Required correction** Provide the full citation for reference 41, or include sufficient methodological detail in the current manuscript to allow replication.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Entire manuscript
- **Evidence pointer** No data availability statement is present.
- **Issue** The manuscript does not include a statement about data availability, which is standard practice for journals and is required by many funding agencies.
- **Required correction** Add a data availability statement indicating where the raw data (BLI traces, comet assay images, etc.) can be accessed.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 8 and 11
- **Evidence pointer** Results, "Predicted structural models of WT DBD1..." paragraph; "DBD2 variant AlphaFold models were generated..." paragraph.
- **Issue** The structural figures are described as showing "rotated positioning" and "shifted loops," but without seeing the figures, it is impossible to assess whether these changes are visually apparent or meaningful. The authors should ensure that the figures clearly highlight the mutated residues and the described structural changes.
- **Required correction** Ensure that the figures include clear labels for the mutated residues and that the described structural changes are visually evident.

## Risk / unsupported claims
- The claim that "excessively strong binding to DNA may impede the ability of BRCA1 to accurately repair DNA" for Q356H is speculative and not directly tested in this study.
- The claim that F461L pathogenicity is due to "loss of base stacking ability" is a post hoc explanation not supported by experimental evidence.
- The claim that K408E is "likely to be neutral" is based on the absence of a significant cellular phenotype, which is a weak basis for classification given the incomplete statistical reporting.
- The claim that N417S "likely causes DBD1 to target BRCA1 to non-canonical structures of DNA" is based solely on binding affinity data and structural prediction, with no cellular validation.
- The claim that "response to DSBs does not adequately predict pathogenicity of BRCA1 DBD variants" is a negative conclusion drawn from incomplete data, as only one variant (T374I) showed a DSB response phenotype.
- The structural interpretations for all variants are based on unvalidated AlphaFold 2 predictions and should be considered preliminary.
- The binding affinity values cannot be interpreted without clarification of whether they represent Ka or Kd values.