## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, supplementary information) as provided in the submission.
- **Assessment boundary** Scientific content, methodological soundness, interpretability claims, and consistency of evidence presented in the provided text. No external data or code was accessed.
- **Shared manuscript claim summary** The authors present InfluenceNet, a compact convolutional neural network that directly encodes motif influence profiles to predict base-resolution TF binding from ChIP-nexus data. They claim performance comparable to BPNet, direct interpretability of motif syntax, discovery of a cooperative Nanog-Nanog grammar with 10.5-bp helical periodicity, and a structural hypothesis for Nanog oligomerization supported by AlphaFold3 and molecular dynamics simulations.
- **Visible evidence base** Main text figures referenced (Fig. 1a-b, 2a-c, 3a-e, 4a-c, 5a-d), supplementary figures (Supplementary Fig. 1, 3a-b, 4a, 5b, 6, 8, 9), supplementary data (Supplementary Data 1), and methods sections 4.1-4.7.
- **Missing materials affecting confidence** Figure panels and actual data values are not visible in the text; only figure captions and descriptions are available. Supplementary figures and data are referenced but not provided. Code repository is mentioned but not accessible. This limits quantitative verification of performance metrics, statistical significance, and structural modeling results.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually appealing architecture that aims to make motif interactions directly interpretable in a predictive model. The idea of encoding influence as explicit parameters is timely and could be valuable to the regulatory genomics community. However, the evidence as presented is insufficient to fully establish the central claims. Key quantitative comparisons to BPNet are described but not shown in detail, the statistical robustness of the 10.5-bp periodicity is asserted but not rigorously demonstrated, and the structural mechanism is speculative without direct experimental validation. The work is promising but requires substantial additional evidence and clarification before the case is convincing.
- **Who would be interested in the results, and why** Researchers in regulatory genomics, computational biology, and machine learning applied to gene regulation would be interested. The model offers a potential alternative to post-hoc interpretability methods, which is a recognized bottleneck in the field. The proposed Nanog oligomerization mechanism may also interest biophysicists and structural biologists studying transcription factor cooperativity.
- **Major strengths** 1) The architecture is genuinely interpretable by design, avoiding the need for expensive perturbation analyses.  2) The model is compact and efficient, making it accessible and scalable.  3) The integration of predictive modeling with structural and simulation approaches is ambitious and interdisciplinary.  4) The finding of helical periodicity in Nanog influence profiles is biologically plausible and aligns with prior work.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (performance comparison not quantitatively shown), R1-M2 (statistical significance of periodicity not established), R1-M3 (structural mechanism not directly supported), R1-M4 (de novo motif validation incomplete).
- **Assessment against Nature-style criteria** Originality: High. The explicit encoding of influence is a novel contribution relative to post-hoc approaches. Scientific importance: Moderate to high. If validated, the model could accelerate mechanistic discovery, but the current evidence does not yet demonstrate broad impact. Interdisciplinary readership: The work bridges deep learning and biophysics, which is attractive, but the structural claims need stronger support to engage biophysicists. Technical soundness: The architecture and training are plausible, but key validations are missing or underreported. Readability for nonspecialists: The text is generally clear, but some sections (e.g., Fourier analysis, MD details) assume familiarity with specialized methods.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is strong, but the manuscript currently does not provide sufficient quantitative and statistical evidence to fully support the claims. Major revisions are required.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Performance comparison
- **Claim pointer** "InfluenceNet achieves performance comparable to state-of-the-art models" (Abstract, Section 2.1).
- **Evidence pointer** Section 2.1, Fig. 1b; location not provided for specific values.
- **Concern** The claim of comparable performance to BPNet is central to the paper's utility, but the text only states that profile correlations "trailed BPNet by only 1.2-2.6%" and that cross-region correlations "matched or exceeded BPNet for all but Oct4." No actual correlation values, confidence intervals, or statistical tests are reported. The reader cannot assess whether these differences are meaningful or within noise.
- **Why it matters** If the performance gap is larger than implied or not statistically robust, the model's practical value as a replacement for BPNet is undermined. The claim of "comparable" performance must be quantified rigorously.
- **Resolution test** Provide a table or figure with mean and standard deviation of profile and cross-region correlations for both models across all folds and TFs. Include statistical tests (e.g., paired Wilcoxon) to demonstrate equivalence or superiority. Report exact numbers in the text.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical significance of periodicity
- **Claim pointer** "Nanog's striking 10.5-bp helical periodicity" and "the 10.5-bp signal persisted up to 84 bp for Oct4-Sox2 and 63 bp for Nanog" (Abstract, Section 2.3).
- **Evidence pointer** Section 2.3, Fig. 3a-e; location not provided for specific values.
- **Concern** The Fourier analysis identifies a peak at 10.5 bp, but no statistical significance is reported. It is unclear whether this peak is significantly stronger than background or could arise from noise. The persistence of the signal up to 84 bp is stated but not supported by any quantitative threshold or error analysis.
- **Why it matters** The helical periodicity is a key biological finding and a major selling point of the interpretability. Without statistical rigor, the claim is not convincing and could be an artifact of the averaging procedure.
- **Resolution test** Perform a permutation test or compare the Fourier amplitude at 10.5 bp to a null distribution (e.g., shuffled influence profiles). Report p-values or confidence intervals for the peak and for the persistence length. Show the full spectra with error bands.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural mechanism support
- **Claim pointer** "We propose that Nanog forms chain-like oligomers on DNA through asymmetric contacts between WRD and DBD that maintain helical phase alignment" (Abstract, Section 2.5).
- **Evidence pointer** Section 2.5, Fig. 5a-d; location not provided for specific values.
- **Concern** The structural hypothesis is based on AlphaFold3 predictions and MD simulations, but the text does not provide quantitative details. For example, what is the confidence of the AlphaFold3 predictions? How stable are the proposed contacts in the MD simulations? Are the contact maps statistically enriched compared to a control? The authors acknowledge the WR domains are unstructured, which raises questions about the reliability of the proposed interactions.
- **Why it matters** The structural model is a major component of the paper's interdisciplinary appeal. If the simulations are not robust or the contacts are transient, the proposed mechanism is speculative and should be framed as such, not as a supported finding.
- **Resolution test** Provide AlphaFold3 confidence scores (e.g., pLDDT) for the DBD and WR regions. Report the occupancy and lifetime of the WR-DBD contacts in the MD simulations, with error bars across replicates. Compare to a control simulation with a non-specific DNA sequence or a mutated WR domain.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** De novo motif validation
- **Claim pointer** "reveal a cooperative Nanog-Nanog grammar supported by de novo motif discovery" (Abstract, Section 2.4).
- **Evidence pointer** Section 2.4, Fig. 4a-c; location not provided for specific values.
- **Concern** The de novo motif clusters are identified, but their biological relevance is not validated. For example, are the "TTA" half-sites enriched in actual Nanog-bound regions beyond what is expected by chance? Is the 10-bp spacing statistically overrepresented? The authors mention overlap with known motifs, but no comparison to existing databases (e.g., JASPAR) is shown.
- **Why it matters** The claim of a cooperative grammar relies on the motifs being functionally meaningful. Without validation, the clusters could be artifacts of the model or the analysis pipeline.
- **Resolution test** Compare the identified motifs to known TF motifs using a tool like TomTom against a comprehensive database. Perform a permutation test to show that the "TTA…TTA" spacing is enriched in Nanog ChIP-nexus peaks relative to random genomic regions. Report enrichment statistics.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Section 4.2
- **Evidence pointer** Location not provided.
- **Issue** The description of the influence layer is brief. It is unclear how the influence kernels are applied multiplicatively and how the linear aggregation works. A more detailed mathematical formulation would help reproducibility.
- **Required correction** Provide a formal equation or pseudocode for the influence layer computation, including tensor dimensions and the role of the linear layer.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Ablation analysis
- **Affected element** Section 2.1
- **Evidence pointer** Location not provided.
- **Issue** The authors compare InfluenceNet to a no-influence variant, but no ablation of the influence layer's width or the number of free kernels is shown. It is unclear how sensitive the results are to these hyperparameters.
- **Required correction** Add a supplementary figure showing performance as a function of influence kernel width and number of free kernels, with a brief discussion of the trade-offs.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Generalizability
- **Affected element** Section 3
- **Evidence pointer** Location not provided.
- **Issue** The model is only tested on pluripotent TFs. The authors claim generalizability, but no evidence is provided for other cell types or TFs.
- **Required correction** Add a statement acknowledging this limitation and, if possible, a preliminary analysis on a different dataset (e.g., a single TF from another cell type) to demonstrate transferability.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Code availability
- **Affected element** Section 3
- **Evidence pointer** Location not provided.
- **Issue** The code repository is mentioned, but no version or DOI is provided. This hinders reproducibility.
- **Required correction** Provide a specific version or commit hash and consider depositing the code in a permanent repository like Zenodo.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Fig. 3d-e
- **Evidence pointer** Location not provided.
- **Issue** The text describes "progressively trimmed central regions" but the figure is not visible. It is unclear how the persistence length is defined and measured.
- **Required correction** Clarify in the figure legend or text how the persistence length is calculated and what threshold is used to define "persistence."

## Risk / unsupported claims
- The claim of "comparable performance" to BPNet is unsupported without quantitative data and statistical tests.
- The "striking" 10.5-bp periodicity is not statistically validated.
- The persistence of helical coherence up to 84 bp is asserted without a clear definition or error analysis.
- The structural model of Nanog oligomerization is presented as a plausible mechanism but is not directly supported by experimental evidence; the simulations are described qualitatively.
- The de novo motif clusters are claimed to be reproducible but no quantitative reproducibility metrics (e.g., fraction of motifs recovered across seeds) are provided.
- The generalizability of InfluenceNet to other TFs or cell types is claimed but not tested.