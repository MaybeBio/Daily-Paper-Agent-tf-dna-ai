## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods) as provided on bioRxiv
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical soundness based solely on the provided text. No supplementary figures or tables were available for direct inspection beyond those referenced in the text.
- **Shared manuscript claim summary** The authors propose a deep learning framework (COP) to predict C2H2-ZFP genomic occupancy, apply it to the mouse clustered protocadherin (cPcdh) locus, identify Wiz as a candidate regulator, and provide experimental evidence that Wiz restricts CTCF/cohesin loop extrusion in a genomic-distance biased manner to repress cPcdh gene expression.
- **Visible evidence base** Abstract, Introduction, Results (six subsections), Discussion, Materials and Methods (including animal work, cell culture, CRISPR editing, RNA-seq, ChIP-seq, QHR-4C, and AI model details), Author contributions, Declarations
- **Missing materials affecting confidence** Supplementary figures (S1-S6), supplementary tables (S1-S4), all figure panels (Figs 1-6), raw sequencing data, statistical analysis details, and code availability. These are referenced but not provided in the submitted text.

## Reviewer
- **Overall assessment** This manuscript presents a potentially interesting application of deep learning to predict ZFP occupancy and identifies Wiz as a regulator of cPcdh gene expression. The experimental work is extensive, combining computational prediction with genetic knockout, transcriptomic, epigenomic, and chromatin conformation analyses. However, the central mechanistic claim that Wiz restricts CTCF/cohesin loop extrusion in a genomic-distance biased manner is not fully established from the provided evidence. Key quantitative details, statistical rigor, and direct mechanistic tests are lacking. The manuscript would benefit from clearer presentation of the computational model's validation and more direct evidence linking Wiz to loop extrusion dynamics.
- **Who would be interested in the results, and why** Researchers studying zinc finger proteins, 3D genome organization, CTCF/cohesin biology, and the regulation of clustered protocadherin genes. The COP framework may interest computational biologists developing protein-DNA interaction predictors. The potential therapeutic relevance of Wiz in sickle cell disease adds translational interest.
- **Major strengths** 1) The COP framework integrates multiple feature types (sequence, structure) in a novel way for ZFP occupancy prediction. 2) The combination of computational prediction with experimental validation (CRISPR tagging, knockout, multi-omics) is comprehensive. 3) The identification of Wiz as a regulator of cPcdh genes with a proposed distance-dependent mechanism is conceptually interesting. 4) The use of both in vitro and in vivo models strengthens the biological relevance.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (COP validation), R1-M2 (Wiz occupancy evidence), R1-M3 (mechanistic claim), R1-M4 (statistical rigor), R1-M5 (distance-bias quantification)
- **Assessment against Nature-style criteria** **Originality**: Moderate. The application of deep learning to ZFP occupancy prediction is not entirely novel, though the specific integration of secondary structure is a useful contribution. The Wiz-cPcdh connection is new. **Scientific importance**: Potentially high if the mechanism is fully established, as it could reveal general principles of ZFP-mediated regulation of 3D genome architecture. **Interdisciplinary readership**: The topic bridges computational biology, epigenomics, and neuroscience, which could attract broad interest. **Technical soundness**: Currently insufficient. The computational model's performance metrics are incomplete, and the mechanistic experiments do not directly test loop extrusion. **Readability for nonspecialists**: The manuscript is generally well-written but assumes familiarity with 3D genome concepts. Some sections (e.g., COP architecture) are dense and could be simplified.
- **Recommendation posture** Supportive if technical concerns are resolved. The core hypothesis is interesting and the experimental system is appropriate, but the current evidence does not fully establish the proposed mechanism.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational model validation
- **Claim pointer** "COP achieved higher accuracy (63.6%) compared to LightGBM (59.4%), AdaBoost (59.2%), and other known models"
- **Evidence pointer** Results section "Prediction of C2H2-ZFPs localized at promoter CBS elements of cPcdh by COP"; Figure 1C
- **Concern** The reported accuracy of 63.6% is modest and the comparison to baseline models is incomplete. The manuscript does not report precision, recall, F1-score, or area under the ROC curve, which are critical for imbalanced classification problems. The negative sampling strategy (11,346,000 negatives vs 186,000 positives) creates a highly imbalanced dataset, and accuracy alone is misleading. Furthermore, the benchmark against DeepZF appears to use a different evaluation protocol (motif scoring with FIMO) than the direct classification task, making the comparison unfair. The manuscript also does not describe how the model generalizes to unseen ZFPs or whether the 62 ZFPs with ChIP-seq data are representative of the broader family.
- **Why it matters** The entire premise of identifying Wiz as a candidate regulator depends on the reliability of COP predictions. If the model has poor precision or recall, the prioritization of Wiz may be spurious. The lack of proper evaluation metrics undermines confidence in the computational findings.
- **Resolution test** Provide precision-recall curves, F1-scores, and ROC-AUC for COP and all baselines. Report performance on a held-out set of ZFPs not used in training. Describe the cross-validation scheme. For DeepZF comparison, use the same evaluation protocol (e.g., direct classification of binding sites) or clearly justify the different approach.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation of Wiz occupancy
- **Claim pointer** "We confirmed Wiz enrichments at all of the CBS elements across the Pcdh clusters by Myc-tagging the endogenous Wiz gene"
- **Evidence pointer** Results section "Wiz colocalizes with CTCF at CBS elements of cPcdh promoters and enhancers"; Figure 2
- **Concern** The manuscript states that Wiz is enriched at CBS elements but does not provide quantitative ChIP-seq data (e.g., enrichment scores, peak calling statistics, reproducibility between replicates). The text lists specific elements (e.g., Pcdh α1, α8, α9, α12, αc1) but does not show whether Wiz occupancy is comparable to CTCF occupancy in magnitude. Critically, the authors do not demonstrate that Wiz binding is sequence-specific or dependent on its zinc fingers. A control experiment with a Wiz mutant lacking DNA-binding activity would be necessary to confirm that the observed ChIP-seq signal reflects direct DNA binding rather than indirect tethering via CTCF or other proteins.
- **Why it matters** The claim that Wiz directly occupies CBS elements is foundational to the proposed mechanism. Without evidence for direct, sequence-specific binding, the model of Wiz restricting loop extrusion at these sites is speculative.
- **Resolution test** Provide ChIP-seq enrichment values (e.g., IP/input ratios) for Wiz at CBS elements compared to negative control regions. Include a Wiz mutant lacking zinc fingers as a negative control. Show that Wiz binding is lost or reduced at CBS elements upon mutation of the core motif.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic claim of loop extrusion restriction
- **Claim pointer** "Wiz regulates CTCF/cohesin occupancy and long-range enhancer-promoter contacts in a genomic-distance biased manner" and "Wiz may stall cohesin loop extrusion"
- **Evidence pointer** Results sections "Wiz ablation leads to increased cPcdh gene expressions in vitro", "Wiz deletion in the brain leads to increased cPcdh gene expressions in vivo", "Wiz regulates cPcdh gene expression in a genomic-distance biased manner"; Figures 5 and 6
- **Concern** The manuscript proposes that Wiz restricts loop extrusion but does not provide direct evidence for this mechanism. The ChIP-seq data show increased CTCF/cohesin occupancy upon Wiz deletion, but this could result from indirect effects (e.g., changes in gene expression, chromatin state) rather than direct restriction of loop extrusion. The 4C-seq experiments show increased long-range interactions, but the interpretation that this reflects altered loop extrusion dynamics is one of several possible explanations. The authors do not perform time-course experiments, single-molecule imaging, or other assays that would directly measure loop extrusion processivity. Furthermore, the claim of "genomic-distance biased" regulation is based on correlative analysis without a clear quantitative model or statistical test for the distance dependence.
- **Why it matters** The central mechanistic claim of the paper is that Wiz restricts loop extrusion in a distance-dependent manner. If this is not directly demonstrated, the paper's main conclusion is not established. Alternative explanations (e.g., Wiz affecting CTCF chromatin loading, histone modifications, or transcriptional feedback) remain plausible.
- **Resolution test** Perform experiments that directly test loop extrusion, such as auxin-inducible degron of Wiz followed by time-resolved Hi-C or Micro-C. Alternatively, use an in vitro single-molecule loop extrusion assay with purified Wiz, CTCF, cohesin, and DNA. Provide a quantitative model for the distance-dependent effect with statistical support.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and reproducibility
- **Claim pointer** "significant increases of expression levels of the cPcdh genes upon Wiz deletion" and "significant increases of both CTCF and cohesin enrichments"
- **Evidence pointer** Results sections on in vitro and in vivo experiments; Figures 3, 4, 5
- **Concern** The manuscript repeatedly uses the term "significant" but does not report effect sizes, confidence intervals, or exact p-values for most comparisons. The number of biological replicates is stated as "at least two" in the methods, which is insufficient for robust statistical inference in genomics experiments. The differential expression analysis uses DESeq2, but the thresholds (log2 fold change > 0.5, adjusted p < 0.05) are not justified. For the ChIP-seq and 4C-seq analyses, no details on peak calling reproducibility, normalization methods, or statistical tests for differential occupancy are provided. The Poisson test for enrichment is described, but the methodology for the sliding window analysis is not fully specified.
- **Why it matters** The conclusions depend on the statistical significance of the observed changes. Without proper statistical reporting, the reader cannot assess the reliability of the findings. The use of only two replicates is a particular concern for ChIP-seq and 4C-seq, which are known to have high technical variability.
- **Resolution test** Provide exact p-values, effect sizes, and confidence intervals for all key comparisons. Increase the number of biological replicates to at least three, ideally four or more. Describe the statistical methods for ChIP-seq and 4C-seq analyses in detail, including normalization, peak calling, and differential analysis procedures.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantification of genomic-distance bias
- **Claim pointer** "Wiz regulates cPcdh gene expression in a genomic-distance biased manner"
- **Evidence pointer** Results section "Wiz regulates cPcdh gene expression in a genomic-distance biased manner"; Figure 6
- **Concern** The claim of a genomic-distance biased effect is central to the paper's title and conclusions, but the quantitative analysis supporting this claim is not described in sufficient detail. The manuscript does not define how "distance" is measured (e.g., linear genomic distance from the super-enhancer to each promoter), how the bias is quantified (e.g., correlation coefficient, slope of a fitted model), or what statistical test was used to establish that the effect is distance-dependent rather than simply reflecting the overall upregulation of all cPcdh genes. The 4C-seq data are described qualitatively, and no quantitative comparison of interaction frequencies across different distances is provided.
- **Why it matters** The title and abstract emphasize the distance-biased nature of the regulation. If this claim is not rigorously quantified, the paper's main message is weakened. A reviewer cannot evaluate whether the observed pattern is statistically robust or could arise from other factors (e.g., promoter strength, chromatin state).
- **Resolution test** Provide a clear definition of distance and a quantitative analysis showing that the magnitude of expression changes or interaction frequency changes correlates with distance from the super-enhancer. Include a statistical test for the distance dependence (e.g., linear regression with confidence intervals, permutation test). Show that the effect is specific to the cPcdh locus and not a general property of Wiz deletion.

## Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Model interpretability
- **Affected element** COP architecture description
- **Evidence pointer** Methods section "COP architecture"
- **Issue** The description of the attention mechanisms is dense and lacks intuition. It is unclear what biological features the model learns (e.g., specific amino acid-DNA contacts, structural motifs).
- **Required correction** Add a paragraph explaining the biological interpretability of the model, possibly with examples of learned features or attention weights.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Code and data availability
- **Evidence pointer** Methods section "Processing of public ChIP-seq data"
- **Issue** No statement on code availability or data deposition is provided. For a deep learning paper, this is essential for reproducibility.
- **Required correction** Add a "Data and code availability" section with links to the model code, training scripts, and processed data.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Control experiments
- **Affected element** Wiz knockout validation
- **Evidence pointer** Methods section "Generation of ΔWiz single-cell clones"
- **Issue** The manuscript does not describe how Wiz knockout was validated at the protein level (e.g., Western blot) or whether the two clones showed similar phenotypes.
- **Required correction** Include Western blot or mass spectrometry validation of Wiz loss, and show that the two independent clones have consistent phenotypes.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of alternative mechanisms
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The discussion does not adequately address alternative explanations for the observed effects, such as Wiz affecting CTCF chromatin loading, histone modifications, or transcriptional feedback.
- **Required correction** Add a paragraph discussing alternative mechanisms and how the current data distinguish (or fail to distinguish) between them.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 2, 5, 6
- **Evidence pointer** Results sections referencing these figures
- **Issue** The text describes complex multi-panel figures, but the actual figure content is not available for review. The authors should ensure that all key data are clearly presented with appropriate scales and annotations.
- **Required correction** Ensure all figures are self-contained with clear axis labels, legends, and statistical annotations.

## Risk / unsupported claims
- The claim that COP "systematically predict[s] ZFP genomic enrichments" is not fully supported by the provided evaluation metrics, which are limited to accuracy on a single benchmark.
- The claim that Wiz "regulates clustered protocadherin genes by restricting CTCF/cohesin loop extrusion" is not directly demonstrated. The evidence shows correlations (increased CTCF/cohesin occupancy and interactions upon Wiz deletion) but not a causal mechanism involving loop extrusion.
- The claim of a "genomic-distance biased manner" is not quantitatively established with appropriate statistical tests.
- The statement that "Wiz has the potential to bind all of the pCBS elements" is based on computational prediction and ChIP-seq at endogenous loci, but direct DNA-binding assays (e.g., electrophoretic mobility shift assay, surface plasmon resonance) are not provided.
- The inconsistency between the authors' previous finding that Wiz haploinsufficiency reduces Pcdhβ expression (cited as reference 66) and the current finding that Wiz deletion increases Pcdhβ expression is acknowledged but not fully resolved. The authors attribute this to different deletion sizes, but this explanation requires experimental validation.
- The claim that "Wiz may stall cohesin loop extrusion" is speculative and not supported by direct experimental evidence.