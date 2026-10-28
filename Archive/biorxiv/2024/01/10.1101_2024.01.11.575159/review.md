## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, limitations, methods, supplementary figure legends, supporting information) as provided
- **Assessment boundary** Scientific content, methodological soundness, validity of claims relative to presented evidence, and clarity of presentation. No assessment of code functionality, data availability beyond stated links, or replication of analyses.
- **Shared manuscript claim summary** The authors present FourierCycle, a framework combining single-cell multiome sequencing (snRNA-seq and snATAC-seq), deep learning (DeepCycle), and biophysical modeling with Fourier series solutions, to quantify gene-specific rates of mRNA transcription, splicing, nuclear export, and degradation across the cell cycle in mouse embryonic stem cells. They report oscillatory waves of these rates at distinct cell cycle phases, with post-transcriptional regulation (degradation and nuclear export) playing a prominent role in shaping mRNA accumulation. They also report dynamic changes in chromatin accessibility and TF binding footprints, identifying known and potentially novel cell cycle regulators.
- **Visible evidence base** Main text figures 1-6 (described in text), supplementary figures S1-S7 (described in text), methods section, supporting information (mathematical derivations)
- **Missing materials affecting confidence** Figure files themselves were not provided; only figure legends and in-text descriptions. No supplementary tables, no detailed parameter estimates, no per-gene fit quality metrics, no code output or validation reports. No information on the number of genes passing filters beyond the 1,800 and 2,000 thresholds mentioned. No details on the 678 TF PWMs beyond the SwissRegulon source. No explicit statement of replicates used for the multiome experiment beyond "around 5,000 cells in each experiment" and two replicates mentioned in text.

## Reviewer
- **Overall assessment** This manuscript presents a technically ambitious and potentially valuable framework for dissecting mRNA metabolism dynamics during the cell cycle. The combination of single-cell multiome data with biophysical modeling and deep learning is conceptually appealing and addresses a genuine gap in the field. The observation that post-transcriptional regulation, particularly mRNA degradation and nuclear export, plays a substantial role in shaping cell cycle-dependent mRNA accumulation is interesting and, if robust, would be a meaningful contribution. However, the manuscript as presented has several significant weaknesses that prevent full confidence in the conclusions. The validation of the model is largely internal (fit quality) rather than external (comparison to independent experimental measurements). The treatment of nuclear export, a key novel claim, rests on assumptions that are acknowledged but not rigorously tested. The chromatin accessibility and TF footprint analyses, while suggestive, are presented at a level of detail that makes it difficult to assess their robustness. The writing is generally clear but contains some imprecise statements and overclaims relative to the evidence shown. The work is likely of interest to researchers in cell cycle biology, RNA biology, and computational genomics, but the current evidence base does not fully establish all the stated conclusions.
- **Who would be interested in the results, and why** Researchers studying cell cycle regulation, particularly those interested in post-transcriptional control of gene expression, would find the framework and the specific predictions about degradation and export waves valuable. Computational biologists developing methods for RNA velocity and dynamical modeling from single-cell data would be interested in the FourierCycle approach. Chromatin biology researchers studying TF dynamics during the cell cycle may find the footprint analysis of interest. The resource itself (processed data, code, web server) could be useful to the broader single-cell community.
- **Major strengths** 1) The conceptual advance of combining multiome data with a biophysical model to separate transcription, splicing, export, and degradation rates genome-wide during the cell cycle is novel and addresses a real limitation of standard RNA velocity approaches. 2) The use of an unsynchronized, unperturbed cell population is a strength, avoiding artifacts from synchronization methods. 3) The validation that DeepCycle works on snRNA-seq data extends its utility. 4) The integration of chromatin accessibility and TF footprint dynamics with the mRNA metabolism modeling is a forward-looking design. 5) The authors are transparent about limitations and provide resources (code, data, web server).
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Validation
- **Claim pointer** The model provides accurate genome-wide estimates of transcription, degradation, and nuclear export rates during the cell cycle.
- **Evidence pointer** Results sections "Kinetic modeling reveals cell cycle-dependent mRNA transcription and degradation rates" and "Waves of transcriptional and post-transcriptional regulation during the cell cycle"; Figures 2, 3, 4
- **Concern** The validation of the fitted rates is almost entirely internal. The authors show that the model can reproduce the observed spliced and unspliced RNA dynamics for genes with r² > 0.2, but this is a goodness-of-fit measure, not a validation of the biological accuracy of the inferred rates. For example, the claim that degradation rates for Wee1 peak at M/G1 transition is compared qualitatively to literature, but no quantitative comparison to independent measurements (e.g., RNA half-life assays, metabolic labeling) is provided. Similarly, the nuclear export rates are inferred from a model that assumes export dominates over degradation in the nucleus, an assumption that is stated but not tested. Without external validation, it is difficult to know whether the inferred rate parameters reflect true biology or are artifacts of the model assumptions and fitting procedure.
- **Why it matters** The central contribution of the paper is the inference of these rates. If the rates are not validated against independent measurements, the conclusions about the relative importance of transcriptional versus post-transcriptional regulation, and the specific waves of degradation and export, remain speculative. This is a fundamental issue that affects the interpretation of all downstream analyses.
- **Resolution test** The authors should provide external validation for at least a subset of genes. This could include: (1) comparison of inferred degradation rates to measurements from transcription inhibition experiments (e.g., actinomycin D) or metabolic labeling (e.g., SLAM-seq) in a comparable cell type; (2) comparison of inferred transcription rates to measurements from approaches like TT-seq or Bru-seq; (3) for nuclear export, a direct test of the assumption that nuclear degradation is negligible, perhaps by comparing model fits with and without a nuclear degradation term. If such experiments are not feasible, the authors should clearly state this as a limitation and temper the strength of their claims accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Model identifiability
- **Claim pointer** The model can distinguish between transcription, splicing, export, and degradation rates for individual genes.
- **Evidence pointer** Methods section "Biophysical model"; Supporting information
- **Concern** The model has four rate parameters (α, β, η, γ) per gene, some of which are allowed to be cell cycle-dependent. The identifiability of these parameters from steady-state or snapshot measurements of unspliced and spliced RNA is a serious concern. The authors do not discuss parameter identifiability, nor do they provide any analysis (e.g., profile likelihoods, practical identifiability analysis, or simulation-based studies) demonstrating that the parameters can be uniquely and reliably estimated from the data. It is possible that different combinations of parameters produce equally good fits, which would undermine the specific claims about which processes are cell cycle-regulated.
- **Why it matters** If the parameters are not identifiable, the specific conclusions about, for example, the relative amplitude of transcription versus degradation waves, or the timing of peak export rates, may not be reliable. This is a technical issue that is central to the validity of the entire approach.
- **Resolution test** The authors should perform and report an identifiability analysis. This could include: (1) profile likelihood analysis for key parameters on a subset of genes; (2) simulation studies where data are generated from known parameters and the fitting procedure is tested for its ability to recover those parameters; (3) a discussion of which parameters are well-constrained and which are not, and how this affects the biological conclusions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance / Interpretation
- **Claim pointer** "Post-transcriptional regulation, including mRNA degradation and nuclear export, plays a prominent role in shaping mRNA accumulation during the cell cycle."
- **Evidence pointer** Results section "Kinetic modeling reveals cell cycle-dependent mRNA transcription and degradation rates"; Figure 2C; Discussion
- **Concern** The claim that post-transcriptional regulation plays a "prominent role" is based on the model selection results (67.5% of genes prefer the full model with both transcription and degradation cell cycle-dependent). However, the interpretation of this result is not straightforward. The full model will almost always fit better than a reduced model, and the BIC comparison, while penalizing complexity, may still favor the full model even if the contribution of degradation is biologically minor. The authors do not quantify the relative contribution of transcription versus degradation to the overall mRNA dynamics. For example, they do not report the fold-changes in transcription rates versus degradation rates for individual genes, or the fraction of variance in mRNA levels explained by each process. Without such a decomposition, the claim of "prominence" is not well-supported.
- **Why it matters** The relative importance of transcriptional versus post-transcriptional regulation is a key biological question. The current analysis does not provide a clear quantitative answer, and the claim of prominence may be overstated.
- **Resolution test** The authors should provide a quantitative decomposition of the contributions of transcription, degradation, and export to the observed mRNA dynamics. This could be done by, for example, computing the fraction of the total variance in mRNA levels explained by each process, or by reporting the distribution of fold-changes in each rate across genes. This would allow the reader to assess the relative importance of each process.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Data processing
- **Claim pointer** The multiome data provides reliable measurements of both nuclear RNA expression and chromatin accessibility from the same cells.
- **Evidence pointer** Results section "DeepCycle sorts single cells and single nuclei according to their cell cycle progression"; Methods section "Data Processing"
- **Concern** The manuscript does not provide sufficient detail on the quality control of the multiome data. For example, what was the fraction of cells passing QC? What was the median number of genes detected per cell for RNA and the median number of fragments per cell for ATAC? How were doublets removed? How was the concordance between the RNA and ATAC modalities assessed at the single-cell level? The authors state that the correlation between replicates was high, but the details of the QC pipeline are not provided. This is important because the multiome protocol is known to have lower sensitivity than separate RNA or ATAC assays, and poor-quality cells could confound the downstream analyses.
- **Why it matters** The reliability of the conclusions depends on the quality of the input data. If the data are noisy or contain artifacts, the model fits and the inferred dynamics could be affected. The lack of detailed QC information makes it difficult to assess the robustness of the results.
- **Resolution test** The authors should provide a detailed description of the QC pipeline, including the number of cells passing each step, the thresholds used, and the metrics for data quality. They should also show that the key results are robust to variations in QC thresholds.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance / Novelty
- **Claim pointer** The approach "uncovered a high-resolution map of RNA metabolism dynamics and chromatin accessibility, offering new insights into the temporal control of gene expression in proliferating cells."
- **Evidence pointer** Abstract; Discussion
- **Concern** The novelty of the biological findings, as opposed to the methodological novelty, is not fully established. The authors identify waves of transcription and degradation, and changes in TF footprints, but it is not clear what specific, new biological insights are gained. For example, are there specific genes or regulatory modules whose cell cycle regulation was previously unknown? Are there new TF candidates identified? The paper would be strengthened by a more detailed biological analysis that goes beyond describing the waves and identifies specific, testable hypotheses about cell cycle control.
- **Why it matters** For a Nature-style publication, the biological insights need to be significant and clearly articulated. The current manuscript is strong on methodology but weaker on the biological discoveries that the method enables.
- **Resolution test** The authors should highlight specific, novel biological findings that emerge from their analysis. This could include, for example, the identification of a new class of cell cycle-regulated genes, a new mechanism of post-transcriptional control, or a specific TF whose cell cycle dynamics were previously unappreciated. These findings should be presented with appropriate validation or at least with clear hypotheses for future testing.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / Presentation
- **Affected element** Figure 1G and 1H description
- **Evidence pointer** Results section "DeepCycle sorts single cells and single nuclei according to their cell cycle progression"
- **Issue** The text states that total mRNA content shows a two-fold change during the cell cycle, but it is not clear whether this is the total RNA content per cell or per nucleus, and whether this is expected based on cell size changes. The statement "This is the expected behavior, assuming that the concentration of mRNA remains constant during the cell cycle" is somewhat vague.
- **Required correction** Clarify whether the two-fold change is in total RNA content and whether this is normalized for cell size or volume. Provide a reference for the expectation of constant mRNA concentration.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity / Terminology
- **Affected element** Use of "trasncriptional" and "posttranscriptional"
- **Evidence pointer** Discussion
- **Issue** There is a typo: "trasncriptional" should be "transcriptional". Also, the term "posttranscriptional" is used to encompass both degradation and export, which is fine, but the distinction between nuclear and cytoplasmic events could be made clearer.
- **Required correction** Fix the typo. Consider using "post-transcriptional" consistently and clarifying that degradation and export are distinct processes occurring in different cellular compartments.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness / Statistical reporting
- **Affected element** Model selection results
- **Evidence pointer** Results section "Kinetic modeling reveals cell cycle-dependent mRNA transcription and degradation rates"; Figure 2C
- **Issue** The percentages of genes preferring each model (67.5%, 19.2%, 12.5%, 1%) are reported, but the total is 100.2%, which is likely due to rounding. More importantly, the text does not report the uncertainty in these percentages or whether they are consistent across replicates.
- **Required correction** Report the percentages with appropriate rounding and state whether the model selection results were consistent between the two replicates.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity / Methods
- **Affected element** Chromatin accessibility analysis
- **Evidence pointer** Methods section "Chromatin accessibility analysis"
- **Issue** The description of the chromatin accessibility analysis is brief. It is not clear how the "accessibility profiles" were smoothed, what window was used, or how the TF footprints were normalized. The statement "Additional smoothing along the relative genomic coordinates with respect to the TF binding sites was performed" is vague.
- **Required correction** Provide more detail on the computational steps for the chromatin accessibility and TF footprint analyses, including parameters and software versions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation / Resources
- **Affected element** Web server and code availability
- **Evidence pointer** Methods section "Data availability" (implied)
- **Issue** The manuscript mentions a web server and GitHub repository, but the URLs are not provided in the text. The processed data link is given, but the code link is not.
- **Required correction** Provide the full URLs for the GitHub repository and the web server in the main text or a data availability statement.

## Risk / unsupported claims
- The claim that the model provides accurate estimates of nuclear export rates is not supported by external validation. The assumption that nuclear degradation is negligible is stated but not tested.
- The claim that post-transcriptional regulation plays a "prominent role" is not quantitatively supported. The relative contributions of transcription versus degradation to mRNA dynamics are not decomposed.
- The claim that the approach identifies "key regulators" of the cell cycle based on TF footprint dynamics is suggestive but not validated. No functional validation or comparison to known regulators beyond a few examples is provided.
- The claim that the model can distinguish between transcription, splicing, export, and degradation rates is not supported by an identifiability analysis.
- The statement that "this is the first time that genome-wide transcriptional and posttranscriptional waves have been reported during the cell cycle using scRNA-seq profiles" is a strong claim that is difficult to verify and may be overstated given prior work on cell cycle gene expression dynamics.
- The biological novelty of the findings, beyond the methodological advance, is not clearly established. The specific new insights into cell cycle control are not articulated in a way that distinguishes them from prior knowledge.