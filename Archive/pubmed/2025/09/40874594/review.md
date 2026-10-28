## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, supplementary figure legends referenced but not provided in full)
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility of claims, and significance of the presented results based solely on the supplied manuscript text
- **Shared manuscript claim summary** The authors present a family-level machine learning framework ("FamilyCode") that uses a reference-free tetrahedral representation of DNA base preferences to predict shifts in transcription factor (TF) DNA binding specificity caused by missense mutations. The method is validated on the bHLH and homeodomain (HD) families using both existing and newly generated high-throughput binding data, and is benchmarked against sequence-similarity and structure-based approaches.
- **Visible evidence base** Abstract; full introduction; full methods section; full results section; full discussion; data availability statement; funding and author contribution statements. Supplementary figures and tables are referenced but their content is not provided.
- **Missing materials affecting confidence** Supplementary figures S1–S11, supplementary data SD1–SD7, and the full set of figures (main text figures 1–6 are described but not shown). Without these, quantitative claims about prediction accuracy, statistical significance, and comparisons to other methods cannot be independently verified.

## Reviewer

- **Overall assessment** This manuscript describes a conceptually interesting and potentially useful framework for predicting how missense mutations alter TF DNA binding specificity. The tetrahedron representation of base preferences is a thoughtful solution to a real technical problem, and the authors demonstrate its application across two TF families with reasonable success. However, the manuscript as presented has several gaps that prevent full evaluation: the key figures and supplementary materials are not available, some methodological details are underspecified, and the comparison to existing methods is incomplete. The core idea has merit, but the strength of the claims currently exceeds what can be verified from the provided text alone.

- **Who would be interested in the results, and why** Researchers studying transcription factor DNA binding specificity, particularly those interested in the functional consequences of disease-associated TF mutations. The work is also relevant to computational biologists developing interpretable machine learning methods for protein-DNA recognition, and to experimentalists who need to prioritize TF variants for functional testing. The FamilyCode framework could be of practical use in variant interpretation pipelines for developmental disorders and cancer.

- **Major strengths**
  1. The tetrahedron representation is an elegant and well-motivated solution to the problem of comparing base preferences across TFs with different preferred bases, and it naturally handles the numerical instability of strongly disfavored bases.
  2. The authors validate their approach on two structurally distinct TF families (bHLH and HD), which strengthens the claim of generalizability.
  3. The inclusion of newly generated SELEX-seq data for mutant bHLH factors, alongside reanalysis of published PBM data, provides a multi-platform assessment.
  4. The comparison to rCLAMPS and DeepPBS, while limited, is a useful benchmark against existing prediction tools.
  5. The manuscript is generally well-written and the logic of the approach is clearly explained for a specialist audience.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that FamilyCode achieves high prediction accuracy for mutant TF binding specificity, with R² values of 0.94 (ASCL2) and 0.61 (HES2) for ΔΔΔG/RT predictions, and R² = 0.98 for HLH-1 mutants.
- **Evidence pointer** Results section, Figures 3F, 3G, 4C, 4D; location not provided for figure content
- **Concern** The central quantitative claims of this manuscript rest entirely on figures that are not included in the provided text. Without seeing the actual scatter plots, correlation values, and the distribution of data points, it is impossible to assess whether the reported R² values are meaningful, whether they are driven by a few outliers, or whether the predictions are uniformly accurate across the motif positions. The same applies to the comparison with rCLAMPS and DeepPBS shown in Figure 6D.
- **Why it matters** The predictive accuracy of FamilyCode is the core contribution of the paper. If the figures do not support the reported metrics, or if the accuracy is heterogeneous across positions or mutation types, the conclusions would need to be substantially revised.
- **Resolution test** Provide the actual figures with clear axis labels, per-position breakdowns of prediction accuracy, and confidence intervals on the reported R² values. Show the full distribution of predicted versus empirical ΔΔΔG/RT values, not just summary statistics.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The authors state that "we used the same tetrahedral transformation to compute ΔΔΔG/RT values in all cases" to ensure a fair comparison with rCLAMPS and DeepPBS.
- **Evidence pointer** Results section, "Comparison with DeepPBS" and "Comparison with rCLAMPS" paragraphs; location not provided
- **Concern** The comparison to rCLAMPS and DeepPBS is described only in the briefest terms. It is unclear whether these methods were applied exactly as intended by their developers, whether hyperparameters were tuned, whether the same training data were used, and whether the output formats were directly comparable. The statement that DeepPBS "performed only modestly" is not quantified. A fair benchmark requires careful attention to these details, and the current description is insufficient to rule out inadvertent disadvantages to the comparison methods.
- **Why it matters** The claim that FamilyCode outperforms existing methods is a key selling point. If the comparison is not rigorously fair, the conclusion is not established.
- **Resolution test** Provide a detailed description of how rCLAMPS and DeepPBS were run, including input formats, any preprocessing steps, and whether the developers' recommended protocols were followed. Report the full distribution of performance metrics, not just a single R² value, and discuss any known limitations of the comparison methods in this context.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors use MANOVA to identify associations between amino acid identity at protein positions and base preference at DNA positions, and report "P < 0.001 after Bonferroni correction" for 9 bHLH positions.
- **Evidence pointer** Results section, "Mapping of DNA binding specificity determinants for bHLH factors"; Methods section, "Multivariate analysis of variance (MANOVA)"
- **Concern** The MANOVA analysis is described as testing the association between amino acid identity and tetrahedral coordinates, but the details of the multiple testing correction are vague. The manuscript states "P < 0.001 after Bonferroni correction" but does not specify the total number of tests performed, which is essential for assessing whether the correction was adequate. Additionally, the use of MANOVA with a categorical independent variable (amino acid identity) and three correlated dependent variables (tetrahedral coordinates) may violate assumptions of the test if the data are not multivariate normal, and this is not discussed.
- **Why it matters** The identification of key protein positions that determine DNA binding specificity is a central result. If the statistical analysis is not properly described or is flawed, the biological conclusions drawn from it may not be reliable.
- **Resolution test** Specify the total number of MANOVA tests performed, the exact correction method used, and whether assumptions of the test were checked. Consider reporting effect sizes or variance explained in addition to p-values.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Validation completeness
- **Claim pointer** The authors state that "the lower prediction accuracy for HES2 mutants (R² = 0.61) is consistent with the lower reproducibility of the wild-type HES2 model noted above."
- **Evidence pointer** Results section, "Experimental validation of specificity shift predictions for mutant bHLH factors"; Methods section, "SELEX assays"
- **Concern** The manuscript attributes the lower prediction accuracy for HES2 to lower reproducibility of the wild-type model, but the evidence for this is not presented. The RMSD between wild-type replicates for HES2 is mentioned as 0.61, but no comparison is made to the replicate reproducibility for ASCL2 or for the HD factors. Without a direct quantification of replicate variability for each TF, the explanation for the lower accuracy remains speculative.
- **Why it matters** Understanding why predictions are less accurate for some TFs is important for assessing the generalizability of the method and for guiding future improvements.
- **Resolution test** Provide a direct comparison of replicate reproducibility across all TFs used in the study, and discuss whether the observed prediction accuracy for each mutant correlates with the quality of the wild-type model.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors claim that "the approach is general, and could also be applied to other TF families that have a sufficiently larger number of members for which high-throughput DNA binding data are available."
- **Evidence pointer** Discussion section, first paragraph
- **Concern** The manuscript demonstrates the approach on only two TF families, both of which are relatively well-characterized and have clear consensus binding motifs. The claim of generalizability is plausible but not tested. It is unclear how the method would perform for TF families with more diverse binding modes, such as zinc finger proteins with variable spacing between fingers, or for TFs that bind as heterodimers with complex cooperative interactions.
- **Why it matters** The broader impact of the work depends on its applicability beyond the two families tested. Without evidence of generalizability, the claim remains speculative.
- **Resolution test** Either temper the claim of generalizability or provide at least one additional example of a TF family with different structural characteristics to demonstrate the method's breadth.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, "Mapping of DNA binding free energy (ΔΔG/RT) parameters to tetrahedral coordinates"
- **Evidence pointer** Methods section, paragraph 3
- **Issue** The description of the tetrahedral transformation is mathematically dense and would benefit from a more intuitive explanation. The relationship between the tetrahedral coordinates and the original ΔΔG/RT values is not immediately obvious to a reader who is not already familiar with this type of embedding.
- **Required correction** Add a brief intuitive explanation of why the tetrahedron representation is useful, perhaps with a simple example showing how a change in base preference maps to a movement within the tetrahedron.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section, "Collecting HT-SELEX data for training bHLH binding models"
- **Evidence pointer** Methods section, paragraph 1
- **Issue** The manuscript states that data from three publications were used, but does not specify the exact accession numbers or database identifiers for the raw data. The statement "we only used the unmethylated library" for the Yin et al. data is clear, but the specific filtering criteria for the other datasets are not described.
- **Required correction** Provide a table listing all datasets used, their sources, and any filtering steps applied. Include accession numbers or URLs where the raw data can be accessed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results section, "Mapping the protein sequence determinants of DNA binding specificity for bHLH factors"
- **Evidence pointer** Results section, paragraph 3
- **Issue** The discussion of positions 20 and 50 as "not previously associated with bHLF binding specificity" is interesting, but the mechanistic explanations offered are speculative. The manuscript states that position 20 "mediates a contact at the homodimerization interface" and that position 50 may "form an electrostatic and hydrogen bond with Glu, Gln, or Asp at residue position 22," but no direct experimental evidence is provided to support these claims.
- **Required correction** Clearly distinguish between statistically significant associations and mechanistically validated interactions. Consider adding a caveat that the proposed mechanisms are hypotheses that require experimental testing.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section, "Extension of our approach to wild-type and mutant bHLH data from the PBM platform"
- **Evidence pointer** Results section, paragraph 5
- **Issue** The manuscript mentions that most of the PBM data for bHLH factors in CisBP are for C. elegans factors, but does not discuss whether the conclusions drawn from this cross-species analysis are consistent with the human data. This is a potential confound that should be addressed.
- **Required correction** Add a brief discussion of whether the C. elegans bHLH factors behave similarly to their human counterparts, and whether any species-specific differences were observed.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Discussion section, final paragraph
- **Evidence pointer** Discussion section, paragraph 4
- **Issue** The discussion of future directions is brief and does not address some obvious limitations of the approach, such as the assumption of a fixed backbone geometry or the potential for non-additive effects of multiple mutations.
- **Required correction** Expand the discussion of limitations and future directions, particularly regarding the applicability of the method to TFs with more complex binding mechanisms.

## Risk / unsupported claims
- The claim that FamilyCode "outperforms" rCLAMPS and DeepPBS is not fully supported by the provided text, as the comparison details are insufficient and the actual performance data are in figures not provided.
- The claim that the approach is "general" and applicable to other TF families is plausible but untested and therefore not established.
- The mechanistic explanations for the effects of positions 20 and 50 in bHLH factors are speculative and not directly supported by experimental evidence.
- The statement that lower prediction accuracy for HES2 is due to lower wild-type model reproducibility is not directly evidenced.
- The claim that the tetrahedron representation "naturally alleviates the numerical issues" associated with strongly disfavored bases is plausible but not quantitatively demonstrated in the provided text.
- The overall predictive performance of FamilyCode for held-out wild-type TFs (R² = 0.69) is presented without confidence intervals or a clear statement of how this compares to the theoretical upper bound given the noise in the underlying data.