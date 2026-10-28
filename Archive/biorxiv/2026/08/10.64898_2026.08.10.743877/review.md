## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) without figures or supplementary materials
- **Assessment boundary** Scientific claims, methodological soundness, and evidence quality as presented in the text; figure content assessed only through textual descriptions
- **Shared manuscript claim summary** The authors present CALFP-MHC, a deep learning framework using cheminformatics fingerprints (MACCS, ECFP4, ECFP6, RDKit) for amino acid encoding, combined with positional encoding and supervised contrastive learning, to predict peptide-MHC binding across HLA class I and class II. They claim superior performance over existing tools under class imbalance, for rare alleles, and on unseen peptides, alongside interpretability via attention and integrated gradients analyses.
- **Visible evidence base** Textual descriptions of results across five result sections; methods section; data availability and code availability statements
- **Missing materials affecting confidence** All figures and supplementary tables (S1-S6) are referenced but not provided; training/validation data construction details are partially described; no quantitative results are reported in the text itself

## Reviewer

### Overall assessment
The manuscript addresses a relevant problem in computational immunology and proposes a technically interesting combination of established components: cheminformatics fingerprints for amino acid encoding, supervised contrastive learning, and a hybrid convolutional-transformer architecture. The interpretability analyses are a valuable addition. However, the evidence as presented in the text is insufficient to evaluate the core claims. All quantitative results are contained in figures and supplementary tables that were not provided for review. The training data construction using predictions from other tools as surrogate labels raises significant concerns about circularity and what the model actually learns. The claim of robustness under class imbalance is partially attributed to the balanced training strategy, which weakens the novelty of this finding. The interpretability claims, while plausible, are presented without quantitative validation against structural data. The manuscript would benefit from clearer reporting of experimental design, particularly regarding data splits and the distinction between agreement with existing tools and true predictive performance.

### Who would be interested in the results, and why
Computational immunologists and bioinformaticians working on peptide-MHC binding prediction, neoantigen prioritization, and vaccine design would be the primary audience. The interpretability component may also interest researchers developing explainable AI methods for biological sequence data. The potential for improved performance on rare alleles and under class imbalance is clinically relevant for personalized immunotherapy applications.

### Major strengths
1. The combination of cheminformatics fingerprints with contrastive learning is a reasonable and potentially novel integration of existing ideas.
2. The explicit focus on interpretability through multiple complementary analyses (attention, integrated gradients, structural mapping) is commendable.
3. The evaluation across both class I and class II, and across multiple challenging scenarios, is comprehensive in scope.
4. The authors acknowledge limitations of their approach, including the surrogate label issue and the small TESLA dataset.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The manuscript claims superior performance over existing tools across multiple benchmarks, including AUC values of 0.93-0.97 and PPVs of 0.66-0.94, and robustness at 200:1 negative-to-positive ratios.
- **Evidence pointer** Results sections "CALFP-MHCI outperformed existing tools..." and "CALFP-MHCII outperformed existing tools..."; figures 2 and 3; location not provided
- **Concern** All quantitative performance claims are presented exclusively through figures and supplementary tables that were not included in the materials provided for review. The text describes trends and comparisons but contains no numerical results, confidence intervals, or statistical test outcomes that could be independently assessed. Without access to the actual data, the magnitude of the claimed improvements, the variability across alleles, and the statistical significance of the comparisons cannot be verified.
- **Why it matters** The central claim of the manuscript is that CALFP-MHC outperforms existing state-of-the-art tools. This claim cannot be evaluated without the underlying performance data. The absence of any quantitative results in the text makes it impossible to assess whether the observed differences are meaningful or within expected variability.
- **Resolution test** Provide the full figures and supplementary tables, or include key quantitative results (AUC, PPV, confidence intervals, p-values) directly in the text. The performance comparisons should be presented in a format that allows independent verification.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design
- **Claim pointer** The training data for CALFP-MHC were constructed using predictions from NetMHCpan-4.1, MHCflurry-2.0, NetMHCIIpan-4.1, and DeepMHCII as surrogate labels, and the model is then benchmarked against these same tools.
- **Evidence pointer** Methods section "Data collection and preprocessing"; location not provided
- **Concern** The model is trained on labels generated by the very tools it is later compared against. This creates a fundamental circularity problem. The model can at best learn to approximate the consensus of existing predictors, and its "superior" performance may simply reflect better distillation of the training labels rather than improved biological understanding. The authors acknowledge this in the methods but do not adequately address the implications for their claims of outperformance. The independent validation on MS/MS and TESLA datasets partially mitigates this concern, but the primary benchmark results are compromised.
- **Why it matters** The claim of outperforming state-of-the-art tools is the primary contribution of the manuscript. If the training data are derived from those same tools, the comparison is not fair and the results are difficult to interpret. The manuscript needs to clearly separate what the model learned from the surrogate labels versus what it learned from actual biological signal.
- **Resolution test** Provide a clear analysis of how performance differs when trained on experimentally validated data versus surrogate labels. Alternatively, demonstrate that the model's performance on the independent MS/MS and TESLA datasets is not simply a reflection of the training label distribution. The discussion should more thoroughly address the implications of surrogate label training for the validity of the benchmark comparisons.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability validation
- **Claim pointer** The manuscript claims that attention and integrated gradients analyses recovered known anchor positions and highlighted chemically interpretable functional groups, supporting the interpretability of the model.
- **Evidence pointer** Results section "Fingerprint-based contrastive learning enables interpretable prediction"; figure 4; location not provided
- **Concern** The interpretability analyses are described qualitatively. The text states that recovered motifs were "consistent with" known anchors and that attribution maps "highlighted" certain functional groups, but no quantitative comparison against structural data or known binding motifs is provided. The authors themselves note that attention weights are not guaranteed to reflect feature importance, yet the interpretability claims rest heavily on these analyses. The co-localization of attention and attribution signals is presented as evidence of reliability, but this could also reflect shared biases in the model rather than true biological signal.
- **Why it matters** Interpretability is presented as a key advantage of the framework over black-box models. If the interpretability claims are not rigorously validated, this advantage is not established. The clinical and mechanistic utility of the model depends on the reliability of these attributions.
- **Resolution test** Provide quantitative comparisons between model-derived motifs and known binding motifs (e.g., from structural databases or position weight matrices). Include metrics such as motif similarity scores or enrichment analyses. Validate attribution maps against experimentally determined contact residues where available.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The manuscript reports statistically significant differences between CALFP-MHC and competing tools, including p-values on the TESLA dataset.
- **Evidence pointer** Methods section "Statistical analysis"; results sections; location not provided
- **Concern** The statistical methods are described but the results are not presented in the text. The manuscript mentions DeLong's method for pairwise AUC comparisons and Mann-Whitney U tests, but no effect sizes, confidence intervals, or multiple testing considerations are reported. The TESLA dataset contains only 36 positive examples after preprocessing, which severely limits statistical power, and the authors acknowledge this but do not provide power calculations or discuss the implications for their conclusions.
- **Why it matters** The claims of significant outperformance rest on statistical comparisons that cannot be evaluated. Small sample sizes in key validation datasets mean that even large observed effects may not be reliable. The manuscript needs to demonstrate that the reported differences are statistically robust and not artifacts of small sample sizes or multiple comparisons.
- **Resolution test** Report all statistical results in the text or tables, including effect sizes, confidence intervals, and exact p-values. Provide power calculations for the TESTA dataset analysis. Address whether the study is adequately powered to detect the claimed differences.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states "performance remained above AUC 0.90 even at a 200:1 negative-to-positive ratio" but does not specify which dataset or allele this refers to, nor how this compares to the specific competing tools mentioned.
- **Required correction** Specify the dataset and comparison context for this claim, or refer to the relevant figure/table.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, hyperparameters
- **Evidence pointer** Methods section "CALFP-MHC training"; location not provided
- **Issue** The weight decay is reported as "1×10□□" with the exponent missing. Learning rate for Stage 1 is not reported. These are essential hyperparameters for reproducibility.
- **Required correction** Provide the complete hyperparameter values, including weight decay exponent and Stage 1 learning rate.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, class II evaluation
- **Evidence pointer** Results section "CALFP-MHCII outperformed existing tools..."; location not provided
- **Issue** The text mentions "consistentl strong performance" and "Th performance gap" with apparent typos. More substantively, the class II evaluation appears to use a composite dataset mixing MS/MS and IC50 data, but the text does not clarify how these different assay types were harmonized.
- **Required correction** Fix typos and clarify how MS/MS and IC50 data were combined and whether results were consistent across assay types.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, comparison to prior work
- **Evidence pointer** Discussion section; location not provided
- **Issue** The discussion of prior work on fingerprint-based amino acid encoding (refs 9, 10) and contrastive learning (ref 11) is brief and does not clearly articulate what is genuinely novel about the combination presented here beyond the specific architecture.
- **Required correction** Expand the discussion to more clearly delineate the specific novel contributions relative to prior work.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement
- **Evidence pointer** Data availability section; location not provided
- **Issue** The data availability statement lists only the sources of the original datasets but does not state whether the processed training/validation datasets used in this study are available for download.
- **Required correction** Clarify whether the processed datasets are available and where they can be accessed.

### Technical failings that need to be addressed before the case is established
R1-M1 (missing quantitative evidence), R1-M2 (circularity in training data construction), R1-M3 (unvalidated interpretability claims)

### Assessment against Nature-style criteria
**Originality:** Moderate. The combination of fingerprint-based encoding with contrastive learning is a reasonable integration of existing ideas, but each component has been explored separately in prior work. The specific architecture and its application to both class I and class II is a useful contribution, though not conceptually transformative.

**Scientific importance:** Potentially relevant. Improved peptide-MHC binding prediction with interpretability would be valuable for vaccine design and neoantigen prioritization. However, the importance of the specific contribution over existing tools is not established from the provided evidence.

**Interdisciplinary readership:** Limited. The manuscript is primarily of interest to computational immunologists and bioinformaticians. The interpretability angle may attract some interest from the explainable AI community, but the biological focus limits broader appeal.

**Technical soundness:** Cannot be fully assessed. The methodological description is detailed, but the absence of quantitative results and the circularity concern in training data construction prevent a thorough evaluation of technical soundness.

**Readability for nonspecialists:** Adequate. The manuscript is generally well-written and explains concepts clearly, though some sections assume familiarity with immunology and deep learning terminology. The abstract is accessible.

### Recommendation posture
Currently not established from the provided evidence. The manuscript addresses a relevant problem with a plausible technical approach, but the core performance claims cannot be evaluated without the figures and supplementary tables. The training data construction using surrogate labels from the same tools used for comparison is a fundamental concern that must be addressed. The interpretability claims require quantitative validation. The authors should be encouraged to resubmit with the full evidence base and a revised experimental design that addresses the circularity issue.

## Risk / unsupported claims
- All quantitative performance claims (AUC, PPV, comparisons to baselines) are unsupported in the provided text, as they rely entirely on figures and supplementary tables not included in the review materials.
- The claim of robustness under class imbalance is partially attributed to the balanced training strategy, which is acknowledged but not fully explored as a confound.
- The claim that interpretability analyses "recovered" known anchor positions and "highlighted" chemically relevant functional groups is unsupported without quantitative comparison to structural or experimental data.
- The claim that CALFP-MHC "captures predictive features of T cell recognition beyond MHC presentation alone" is not established, as the TESLA dataset is small and the analysis is described only qualitatively.
- The generalizability claims to rare alleles and unseen peptides cannot be evaluated without the underlying data distributions and performance metrics.