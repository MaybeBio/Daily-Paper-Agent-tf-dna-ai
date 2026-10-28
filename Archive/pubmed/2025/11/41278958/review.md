## Review setup
- **Input scope** Full manuscript text (abstract, results, discussion, methods) as provided
- **Assessment boundary** Scientific claims, methodological soundness, and evidence quality based solely on the supplied text
- **Shared manuscript claim summary** The authors present SEAM, a computational framework combining deep learning with explainable AI to map mechanistic impacts of genetic mutations in regulatory DNA. Applied to human and Drosophila loci, SEAM identifies functional binding sites, distinguishes mutation-sensitive (foreground) from mutation-insensitive (background) signals, and reveals that regulatory sequences exhibit high evolvability, with single mutations capable of reprogramming transcriptional logic.
- **Visible evidence base** Main text figures referenced (Figs. 1–5), supplementary figures referenced (Supplementary Figs. 1–21), methods descriptions, and code/data availability statements
- **Missing materials affecting confidence** Figure panels and actual data plots not visible; quantitative performance metrics absent; benchmark comparisons not shown; details of clustering validation incomplete; no ablation studies for key design choices

## Reviewer

### Overall assessment
This manuscript introduces SEAM, a framework for dissecting cis-regulatory mechanisms by clustering attribution maps from locally mutagenized sequence libraries. The conceptual advance of separating foreground and background attribution signals is potentially valuable, and the application across multiple DNNs and assay types demonstrates versatility. However, the evidence presented in the text is largely qualitative, with no quantitative benchmarks, statistical validations, or comparisons to existing methods. The central claims of mechanistic discovery and evolvability rest on visual inspection of figures that are not available in the provided material. The manuscript would benefit from rigorous quantitative evaluation of clustering stability, foreground-background separation accuracy, and biological validation of predicted mechanisms.

### Who would be interested in the results, and why
Computational biologists and genomics researchers working on regulatory genomics, interpretable deep learning, and noncoding variant interpretation would find this framework relevant. The foreground-background decomposition addresses a recognized limitation of attribution methods, and the evolvability analysis connects to evolutionary genomics. Researchers developing synthetic regulatory sequences or studying disease-associated noncoding variants may also find the approach applicable.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "SEAM uncovers functional binding sites at sequences of interest and identifies which mutations preserve, disrupt, or create novel binding sites"
- **Evidence pointer** Results section "SEAM dissects complex cis-regulatory mechanisms"; Fig. 2
- **Concern** The claim that SEAM uncovers functional binding sites is supported only by qualitative descriptions of figure panels. No quantitative metrics are provided for binding site recovery accuracy, precision, or recall relative to known motifs or experimental validation. The text states "clear correspondence between CSM-entropy patterns and the presence or absence of motifs" but provides no statistical measure of this correspondence.
- **Why it matters** Without quantitative evaluation, it is impossible to assess whether SEAM reliably identifies functional elements or whether the clustering approach introduces systematic biases. The framework's utility for variant interpretation depends on demonstrated accuracy.
- **Resolution test** Provide quantitative benchmarks on datasets with known ground truth (e.g., ChIP-seq validated motifs, STARR-seq validated enhancers), including precision-recall curves, motif recovery rates, and comparison to existing methods such as TF-MoDISco.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "SEAM also reveals that two qualitatively distinct classes of regulatory signal are operative at many loci: signals that are robust to mutation and signals that are readily reprogrammable"
- **Evidence pointer** Results section "SEAM disentangles motif syntax from sequence context"; Fig. 3
- **Concern** The foreground-background decomposition is a central methodological contribution, yet the validation of this decomposition is not described. The text states that background signals "remained largely constant across clusters" and "correlate with GC content," but no statistical test is shown to demonstrate that the background is truly mutation-insensitive or that the decomposition is stable across parameter choices. The scaling factor applied before subtraction is described but its derivation and impact on results are not evaluated.
- **Why it matters** The foreground-background distinction underpins the claim of disentangling motif syntax from sequence context. If the decomposition is not robust or the background subtraction introduces artifacts, the biological interpretations drawn from this analysis would be compromised.
- **Resolution test** Demonstrate that the background signal is invariant across mutation rates, library sizes, and attribution methods with quantitative similarity measures. Validate the decomposition on synthetic sequences with known foreground and background components. Show that background subtraction improves motif identification accuracy compared to raw attribution maps.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** "SEAM uncovered a striking diversity of transcriptional activities and associated mechanisms... with many novel regulatory programs driven predominantly by single nucleotide mutations"
- **Evidence pointer** Results section "Regulatory sequences exhibit high mechanistic evolvability"; Fig. 4
- **Concern** The claim of high evolvability is based on analysis of a single locus (PIK3R3) with a single model (CLIPNET). The text states that "oncogene promoters such as MYC and NOTCH1 displayed greater mechanistic evolvability than other promoters" but provides no statistical framework for comparing evolvability across loci, no confidence intervals, and no correction for multiple comparisons. The biological significance of "evolvability" as measured here is not established.
- **Why it matters** The evolutionary implications are a major stated contribution of the work. Without rigorous comparative analysis and statistical validation, the claim that some promoters are more evolvable than others is not supported. The connection to population genetics concepts (e.g., "portal mutations") is speculative without quantitative evidence.
- **Resolution test** Provide a formal definition of evolvability with appropriate statistical tests across multiple loci. Include confidence intervals and multiple testing corrections. Validate predicted evolvability differences with independent experimental data or evolutionary conservation analysis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "SEAM is not universally applicable, but when applied to assays that generate libraries amenable to clustering, it can reveal distinct facets of regulatory logic"
- **Evidence pointer** Results section "SEAM generalizes across diverse sequence libraries"; Fig. 5
- **Concern** The generalization claims are based on three different library types (exhaustive, design, global), but the analysis for each is described only briefly. For the PBM application, the text states SEAM "recovered both primary and secondary binding motifs" but does not quantify recovery accuracy. For the REVO libraries, no comparison to standard ISE is shown in terms of diversity or quality of solutions beyond qualitative statements. The "global" library analysis is explicitly described as exploratory.
- **Why it matters** The claim of versatility across library types is important for establishing SEAM as a general framework. Without quantitative comparisons and clear success criteria for each library type, the generalizability remains anecdotal.
- **Resolution test** Provide quantitative metrics for each library type: motif recovery rates for PBM data, diversity and activity distributions for REVO versus ISE, and clear success criteria for global libraries. Include comparisons to appropriate baselines.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Methods section "SEAM-based background separation"
- **Evidence pointer** Methods, equation for background entropy
- **Issue** The equation for background entropy is presented without derivation or intuitive explanation. The relationship between the entropy threshold and the mutation rate is not immediately clear.
- **Required correction** Provide a brief derivation or intuitive explanation of why this particular entropy threshold is appropriate, and clarify the relationship between the threshold and the mutation rate.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Deep learning models"
- **Evidence pointer** Methods, list of seven DNNs
- **Issue** The text states that seven DNNs were employed but does not specify which DNN was used for which analysis. This makes it difficult to assess the appropriateness of model choices for each application.
- **Required correction** Add a table or explicit mapping of DNNs to the specific analyses in which they were used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section "SEAM dissects complex cis-regulatory mechanisms"
- **Evidence pointer** Supplementary Fig. 4
- **Issue** The text mentions robustness to "number of clusters" but does not describe the range of values tested or the criteria for selecting the final number of clusters.
- **Required correction** Specify the range of cluster numbers tested and the metric used to select the optimal number.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion section
- **Evidence pointer** Discussion, paragraph on foreground-background decomposition
- **Issue** The discussion of background signals as potentially reflecting "intrinsic DNA properties such as shape or flexibility" is speculative and not tied to any specific evidence presented in the results.
- **Required correction** Either provide supporting evidence from the results or clearly label this as a hypothesis requiring further investigation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "SEAM framework"
- **Evidence pointer** Methods, description of clustering
- **Issue** The clustering strategy is described as "hierarchical clustering" but no details are given on distance metric, linkage criterion, or how the number of clusters is determined.
- **Required correction** Provide full details of the clustering algorithm, including distance metric, linkage method, and cluster number selection procedure.

### Technical failings that need to be addressed before the case is established
R1-M1, R1-M2, R1-M3

### Assessment against Nature-style criteria
**Originality**: The concept of clustering attribution maps from locally mutagenized libraries to dissect regulatory mechanisms is a novel contribution. The foreground-background decomposition is an interesting idea that addresses a recognized limitation of attribution methods. However, the originality is somewhat tempered by the incremental nature of combining existing techniques (mutagenesis, attribution, clustering) in a new way.

**Scientific importance**: The potential to systematically map the mechanistic landscape of regulatory DNA and assess evolvability is scientifically important. If validated, this framework could advance understanding of how regulatory logic is encoded and how it evolves. However, the current evidence is insufficient to establish this importance.

**Interdisciplinary readership**: The work bridges deep learning, genomics, and evolutionary biology, which could attract a broad readership. The framework's potential for variant interpretation and synthetic design extends relevance to clinical genetics and bioengineering.

**Technical soundness**: The methodological description is incomplete in several critical areas, including quantitative validation of binding site recovery, statistical assessment of foreground-background separation, and formal comparison to existing methods. The robustness analyses are mentioned but not described in sufficient detail to assess their adequacy.

**Readability for nonspecialists**: The manuscript is written in a style accessible to computational biologists but may be challenging for experimental biologists or nonspecialists. Key concepts such as attribution maps and foreground-background decomposition are introduced but could benefit from more intuitive explanations and illustrative examples.

### Recommendation posture
Currently not established from the provided evidence. The conceptual framework is promising, but the manuscript lacks quantitative validation of its central claims. The authors should provide rigorous benchmarks, statistical analyses, and comparisons to existing methods before the case for SEAM's utility is established. The work has potential to be a valuable contribution to regulatory genomics, but the current evidence is insufficient to support the strong claims made.

## Risk / unsupported claims
- The claim that SEAM "uncovers functional binding sites" is unsupported without quantitative validation against known binding sites or experimental data.
- The claim of "high mechanistic evolvability" of regulatory DNA is based on a single locus analysis without statistical framework.
- The assertion that background signals "reflect underlying biological sequence properties" is not directly tested; alternative explanations (e.g., model artifacts) are acknowledged but not ruled out.
- The claim that SEAM "provides a framework for dissecting complex cis-regulatory mechanisms" is a reasonable aspiration but not demonstrated with quantitative evidence.
- The statement that oncogene promoters "displayed greater mechanistic evolvability than other promoters" is not supported by statistical comparison across loci.
- The generalizability claims across library types are not quantitatively validated for each type.