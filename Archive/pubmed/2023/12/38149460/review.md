## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, materials and methods, and supplementary material references.
- **Assessment boundary** Scientific validity, methodological soundness, interpretation of results, and clarity of the presented evidence. No assessment of editorial fit or publication policy.
- **Shared manuscript claim summary** The authors argue that a recently developed genomic test for positive selection on transcription factor binding sites (TFBSs), based on machine learning-predicted binding affinities, suffers from an ascertainment bias. They claim that because TFBSs are identified from ChIP-seq data in a focal species, binding sites with higher derived affinities are preferentially included, inflating false positive rates for detecting positive selection. They propose two correction methods and report that previously identified positive selection signals largely disappear after correction.
- **Visible evidence base** Simulation results (Table 1, supplementary tables S1–S3), reanalysis of human TFBS data (Table 2), mathematical derivation of conditional probability (Results section), and supplementary figure S1.
- **Missing materials affecting confidence** The original TFBS datasets and deltaSVM values from Liu and Robinson-Rechavi (2020) are referenced via GitHub but not included in the manuscript. The exact code for simulations is not provided in the text. The ancestral sequence reconstruction method is not described in detail. The relationship between SVM score and actual binding affinity is not empirically validated here.

## Reviewer
- **Overall assessment** The manuscript identifies a plausible and important ascertainment bias in a recently published method for detecting positive selection on regulatory sequences. The mathematical argument is clear, and the simulation results support the claim that the bias inflates false positive rates. However, the proposed correction methods rely on assumptions that are not fully validated, and the reanalysis of real data depends on external datasets and P-values that are not fully described. The conclusion that previously reported signals disappear is only partially supported, as the results for CEBPA remain ambiguous. The manuscript is technically sound in its core demonstration but would benefit from stronger validation of the correction methods and a more transparent presentation of the reanalysis.
- **Who would be interested in the results, and why** Evolutionary biologists studying regulatory evolution, researchers developing or applying tests for positive selection on noncoding sequences, and computational biologists interested in ascertainment biases in genomic analyses. The findings are also relevant to anyone using ChIP-seq-derived functional annotations in evolutionary analyses.
- **Major strengths** The manuscript addresses a timely and important methodological issue. The mathematical derivation of the bias is elegant and convincing. The simulation study is well designed and clearly demonstrates the inflation of false positive rates. The authors propose practical correction methods and apply them to real data, providing a concrete path forward for the field.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Validity of correction methods
- **Claim pointer** The authors claim that methods 1 and 2 mitigate the ascertainment bias and that "almost all previously reported positive selection signals disappear" when these methods are applied.
- **Evidence pointer** Results section "Most Positive Selection Signals Disappear Upon Ascertainment Bias Mitigations", Table 2
- **Concern** The two correction methods are based on assumptions that are not empirically validated. Method 1 assumes that the number of TFBSs with negative deltaSVMs equals the number with positive deltaSVMs in the absence of bias, but this is only shown for simulated data and for a "conserved" subset of real TFBSs. Method 2 assumes that all genomic regions have equal potential to become TFBSs, which the authors themselves acknowledge is a simplification. The manuscript does not provide sensitivity analyses to show how robust the conclusions are to violations of these assumptions.
- **Why it matters** If the correction methods are not reliable, the conclusion that positive selection signals disappear may be an artifact of overcorrection. The authors need to demonstrate that their methods are not overly conservative and that the absence of signal is not simply due to an inflated number of tests.
- **Resolution test** Provide sensitivity analyses that vary the assumptions of methods 1 and 2 (e.g., different ratios of positive to negative deltaSVMs, different estimates of P(n≥2), different genome sizes). Show that the qualitative conclusions remain unchanged across a reasonable range of parameter values. Alternatively, validate the methods on simulated data with known positive selection to demonstrate that true signals are retained.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and transparency of reanalysis
- **Claim pointer** The authors reanalyze TFBS data from Liu and Robinson-Rechavi (2020) and report adjusted P-values for three TFs.
- **Evidence pointer** Results section "Most Positive Selection Signals Disappear Upon Ascertainment Bias Mitigations", Table 2, Materials and Methods section "Reanalysis of Human TFBSs"
- **Concern** The reanalysis relies on P-values and deltaSVM values from a previous study, but the manuscript does not provide the full data or a clear description of how the original P-values were computed. The authors state that they used the P-values reported by Liu and Robinson-Rechavi (2020), but the exact number of TFBSs per TF, the distribution of P-values, and the details of the ancestral sequence reconstruction are not given. This makes it difficult to independently verify the results.
- **Why it matters** The central conclusion of the manuscript depends on the reanalysis of real data. Without full transparency on the data and methods, readers cannot assess whether the analysis was performed correctly or whether the results are robust.
- **Resolution test** Provide the full dataset of TFBSs, deltaSVM values, and P-values as supplementary material or in a public repository. Describe the ancestral sequence reconstruction method and the exact procedure for computing P-values. Include a detailed workflow that allows readers to reproduce the reanalysis from raw data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of simulation results
- **Claim pointer** The authors state that "the false positive rate increased with the proportion of TFBSs removed" and that this demonstrates the impact of ascertainment bias.
- **Evidence pointer** Results section "False Positive Rates Under Various Levels of the Ascertainment Bias", Table 1
- **Concern** The simulation uses 10-nucleotide ancestral sequences and only 2 substitutions per sequence. Real TFBSs are longer (the authors report mean lengths of 269–537 bp for the real data), and the number of substitutions can vary. It is unclear whether the simulation results generalize to more realistic sequence lengths and substitution patterns.
- **Why it matters** If the bias is less severe for longer sequences or for different substitution patterns, the conclusions about the impact on real data may be overstated.
- **Resolution test** Repeat the simulations with longer ancestral sequences (e.g., 50–500 bp) and with variable numbers of substitutions. Show that the qualitative relationship between ascertainment bias and false positive rate holds across these conditions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of CEBPA results
- **Claim pointer** The authors state that "there are no positively selected binding sites for any of the 3 TFs" at the 1% adjusted P-value cutoff, but at the 5% cutoff, 87 CEBPA sites remain significant under method 1.
- **Evidence pointer** Results section "Most Positive Selection Signals Disappear Upon Ascertainment Bias Mitigations", Table 2
- **Concern** The manuscript does not discuss the biological implications of the remaining CEBPA signals under method 1. The authors conclude that "no to weak signals" of positive selection exist for CEBPA, but this is a vague characterization. The reader is left uncertain whether the remaining signals are considered real or artifacts.
- **Why it matters** The interpretation of the CEBPA results affects the overall conclusion about whether positive selection on regulatory sequences is rare or absent. A clearer discussion of the remaining signals is needed.
- **Resolution test** Provide a more detailed analysis of the CEBPA sites that remain significant under method 1, including their genomic locations, nearby genes, and potential functional relevance. Discuss whether these sites share any features that might distinguish them from the sites that are no longer significant.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Validation of the SVM score as a proxy for binding affinity
- **Claim pointer** The authors use deltaSVM as a measure of binding affinity change and assume that it is a reliable proxy for actual binding affinity.
- **Evidence pointer** Materials and Methods section "Analysis of Simulated TFBSs", Discussion section
- **Concern** The manuscript acknowledges that the summed SVM score is not a reliable measure of overall binding affinity for long sequences, but the simulation and reanalysis rely on deltaSVM as the sole metric. The authors do not provide any validation that deltaSVM correlates with experimentally measured binding affinity changes for the specific TFs studied.
- **Why it matters** If deltaSVM is not a good proxy for binding affinity, the entire test for positive selection is built on an unreliable foundation, and the ascertainment bias may be a secondary issue.
- **Resolution test** Provide a comparison of deltaSVM predictions with experimentally measured binding affinities for a subset of the TFBSs studied, or cite published validation studies that demonstrate the reliability of deltaSVM for the specific TFs and sequence contexts used here.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of mathematical derivation
- **Affected element** Results section "Interpretation of P-values in the Selection Test"
- **Evidence pointer** Results section, first paragraph
- **Issue** The derivation of the inequality P′ < P is correct but could be presented more clearly. The notation is dense, and the logical steps are not fully spelled out.
- **Required correction** Expand the derivation with additional intermediate steps and a brief verbal explanation of why the conditioning on inclusion in the dataset biases the P-value downward.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Presentation of simulation parameters
- **Affected element** Materials and Methods section "Analysis of Simulated TFBSs"
- **Evidence pointer** Materials and Methods section, first paragraph
- **Issue** The simulation parameters are described briefly, but the number of replicates, the random seed, and the exact procedure for generating the 1,000 control mutants are not specified.
- **Required correction** Provide complete simulation details, including the number of replicates, the random seed, and the algorithm for generating control mutants, to ensure reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Discussion of alternative explanations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section, first paragraph
- **Issue** The manuscript does not discuss alternative explanations for the observed excess of positive deltaSVMs in ChIP-seq-derived TFBSs, such as biased gene conversion or mutation rate variation.
- **Required correction** Add a brief discussion of alternative explanations and why the ascertainment bias is the most parsimonious explanation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** Figure 1 is described in the text but not included in the manuscript. The figure is essential for understanding the ascertainment bias.
- **Required correction** Ensure that Figure 1 is included in the final version and that it clearly illustrates the bias mechanism.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout
- **Evidence pointer** Abstract, Results, Discussion
- **Issue** The terms "ascertainment bias" and "ascertainment bias" are used interchangeably. The term "ascertainment bias" is more standard.
- **Required correction** Use "ascertainment bias" consistently throughout the manuscript.

- **Technical failings that need to be addressed before the case is established** The correction methods need sensitivity analysis. The reanalysis needs full data transparency. The simulation needs to be extended to more realistic sequence lengths. The SVM score needs validation as a proxy for binding affinity.
- **Assessment against Nature-style criteria** Originality: The manuscript identifies a novel and important bias in a recently published method. Scientific importance: The findings have implications for the interpretation of positive selection on regulatory sequences, a topic of broad interest. Interdisciplinary readership: The work is relevant to evolutionary biology, genomics, and computational biology. Technical soundness: The core mathematical and simulation results are sound, but the correction methods and reanalysis need further validation. Readability for nonspecialists: The manuscript is generally well written, but the mathematical derivation could be more accessible.
- **Recommendation posture** Supportive if technical concerns are resolved. The core demonstration of the ascertainment bias is convincing, but the proposed corrections and the reanalysis of real data need to be strengthened before the conclusions can be fully accepted.