## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and data availability statements.
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and alignment with the stated scope of the journal. No assessment of editorial fit or publication policy.
- **Shared manuscript claim summary** The authors present an unsupervised, interpretable representation learning approach (RHIEPA) that infers fungal cis-regulatory networks from genome sequences alone, using reverse homology to learn TF motif-based embeddings of orthologous promoter sets. They demonstrate that these representations predict gene expression, recover known regulatory motifs, and generate novel hypotheses for diverse fungi including Candida albicans, Neurospora crassa, and Fusarium graminearum.
- **Visible evidence base** Full text of results, methods, figure legends (figures themselves not provided), supplementary figure references, and supplementary file references.
- **Missing materials affecting confidence** Figures and supplementary files (including Supplementary Files 1 and 2, Supplementary Figures 1–4) were not provided. These are essential for evaluating the validity of clustering, enrichment analyses, and motif comparisons. The manuscript also references external databases and tools without providing full parameter details for all analyses.

## Reviewer
- **Overall assessment** This manuscript presents a conceptually interesting and potentially valuable approach for inferring cis-regulatory networks from sequence data alone, with promising validation in yeast and intriguing applications to less-characterized fungi. The core idea of using reverse homology with an interpretable encoder is well-motivated and the results are generally consistent with the claims. However, the manuscript has several technical and presentational issues that need to be addressed before the case is fully established. The lack of access to figures and supplementary materials limits a complete evaluation, but based on the text, the approach appears sound with some caveats regarding statistical rigor, comparison to baselines, and interpretation of novel predictions.
- **Who would be interested in the results, and why** Researchers in fungal genomics, regulatory genomics, and computational biology would be interested. The approach offers a sequence-only method for regulatory network inference that could be applied to non-model organisms, which is of broad interest. The interpretable nature of the learned representations and the specific predictions for Candida, Neurospora, and Fusarium would also appeal to fungal biologists studying these organisms.
- **Major strengths** The approach is novel in combining reverse homology with an interpretable encoder for regulatory network inference. The validation against known motifs and gene expression data is thoughtful. The application to multiple fungal species with varying levels of characterization demonstrates generalizability. The authors are appropriately cautious about limitations such as regulatory turnover and ortholog assignment.
- **Major Concerns** Several concerns are detailed below. The most significant are the lack of a rigorous comparison to existing sequence-based methods, the potential for circularity in the validation using known motifs, and the need for clearer statistical reporting in enrichment analyses.
- **Minor Comments** Several minor issues are listed below, including clarity of some methodological descriptions and presentation of results.
- **Technical failings that need to be addressed before the case is established** R1-M1 (baseline comparison), R1-M2 (statistical rigor of enrichment), R1-M3 (circularity in motif validation), R1-M4 (interpretation of novel predictions).
- **Assessment against Nature-style criteria**  
  - **Originality** High. The combination of reverse homology with an interpretable encoder for regulatory network inference is a novel contribution.  
  - **Scientific importance** Moderate to high. The ability to infer regulatory networks from sequence alone has broad implications, particularly for non-model organisms.  
  - **Interdisciplinary readership** Moderate. The work is primarily of interest to computational biologists and fungal geneticists, but the general approach could appeal to a wider genomics audience.  
  - **Technical soundness** Moderate. The core methodology appears sound, but several technical concerns (baselines, statistics, circularity) need to be addressed.  
  - **Readability for nonspecialists** Good. The manuscript is generally well-written and the concepts are explained clearly, though some methodological details are dense.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the results are suggestive, but the current evidence does not fully establish the superiority or reliability of the approach over existing methods.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that RHIEPA predicts gene expression and regulation better than experimental data and existing methods (e.g., "predict gene expression and regulation better than using experimental data" in the abstract and results).
- **Evidence pointer** Results section, Table 1, Figure 2c
- **Concern** The comparison to NetProphet3 and BLAST is useful, but the manuscript lacks a comparison to other sequence-based regulatory network inference methods, such as motif scanning with known position weight matrices (PWMs) from databases, or simpler conservation-based approaches. The claim of superiority over experimental data is also based on a specific metric (1-NN regression) and may not hold for other evaluation criteria. A more comprehensive baseline comparison is needed to establish the added value of the RHIEPA approach.
- **Why it matters** Without a fair and comprehensive baseline comparison, it is unclear whether the improvements are due to the specific methodological innovations or simply to the use of phylogenetic conservation, which is a known signal. This is critical for establishing the scientific contribution.
- **Resolution test** The authors should compare RHIEPA against at least one or two additional sequence-based baselines, such as (a) scanning promoters with known PWMs from JASPAR and using the best match score, and (b) a simple conservation score based on sequence alignment. The comparison should be done on the same prediction tasks (expression prediction, co-expression classification) and reported with appropriate statistical tests.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors report strong enrichments for Gene Ontology (GO) terms and known target genes in clusters (e.g., "9.6 × enrichment, P = 5.45 × 10−133" for ribosome biogenesis).
- **Evidence pointer** Results section, Figures 3–5, Supplementary File 1
- **Concern** The enrichment analyses use Fisher's exact test and report corrected P-values, but the method for multiple testing correction is not specified. More importantly, the background set for enrichment is not clearly defined. For example, is the background all genes in the genome, or only genes with orthologs and representations? The choice of background can dramatically affect enrichment statistics. Additionally, the clusters are defined by the authors' own clustering of the representation space, and it is unclear how robust these clusters are to parameter choices.
- **Why it matters** Enrichment statistics are a key piece of evidence that the representations capture biological function. If the statistical methodology is flawed or the background is inappropriate, the reported enrichments may be inflated or misleading.
- **Resolution test** The authors should specify the multiple testing correction method (e.g., Benjamini-Hochberg) and clearly define the background gene set. They should also perform a sensitivity analysis, e.g., by varying the clustering parameters or the number of clusters, to show that the enrichments are robust.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors validate learned motifs by matching them to known motifs in JASPAR and cis-BP (e.g., "63 of the 256 learned PWMs match known motifs").
- **Evidence pointer** Results section, Figure 2a, 2b
- **Concern** The validation of learned motifs against known motifs is potentially circular, as the known motifs in JASPAR and cis-BP are often derived from the same or similar species (e.g., S. cerevisiae). The fact that the model recovers known motifs in S. cerevisiae is encouraging, but it does not strongly validate the approach for species where no known motifs exist. The authors should clarify how many of the matched motifs are from S. cerevisiae itself, and whether the model can recover motifs in species where the databases are less complete.
- **Why it matters** The claim that the approach can be applied to poorly characterized species rests on the assumption that the learned motifs are biologically meaningful. If the validation is primarily in well-characterized species, this assumption is weaker.
- **Resolution test** The authors should report the species distribution of the matched known motifs. They could also perform a cross-validation analysis where motifs learned from one species are used to predict regulation in another, or where the model is trained on a subset of species and validated on held-out species.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors make novel predictions for C. albicans (meiosis/parasex pathway), N. crassa (mating and RNAi response), and F. graminearum (effector regulation).
- **Evidence pointer** Results sections on C. albicans, N. crassa, and F. graminearum, Figures 4–6
- **Concern** These predictions are presented as hypotheses, which is appropriate. However, the evidence supporting them is largely based on clustering and motif enrichment, and the authors do not provide any experimental validation or strong orthogonal support. For example, the prediction of a meiosis/parasex pathway in C. albicans is based on a cluster of genes with unknown function and motif matches. The authors should be clearer about the strength of the evidence and avoid overstating the novelty or confidence of these predictions.
- **Why it matters** The manuscript's impact partly depends on the credibility of these novel predictions. If they are presented too strongly without sufficient evidence, it could mislead readers and reduce the overall credibility of the work.
- **Resolution test** The authors should temper the language used to describe these predictions and explicitly state that they are hypotheses requiring experimental validation. They could also provide additional computational evidence, such as comparison to known regulatory networks in related species or analysis of conserved synteny.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, "A motif-based encoder"
- **Evidence pointer** Methods section
- **Issue** The description of the encoder architecture is somewhat brief. The authors mention "trainable scaling, pooling and attention layers" but do not provide sufficient detail on the exact architecture, hyperparameters, or how the attention mechanism is implemented. This makes it difficult to reproduce the method.
- **Required correction** Provide a more detailed description of the encoder architecture, including layer sizes, activation functions, and the specific implementation of the attention mechanism. Consider including a schematic diagram or pseudocode.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "Learning motif-based representations..."
- **Evidence pointer** Figure 1
- **Issue** The example of PHO84 in Figure 1a is described in the text, but the figure itself is not provided. It is unclear how the "many matches to the Pho4 consensus site" are visualized and how the conservation is assessed.
- **Required correction** Ensure the figure clearly shows the motif matches and the conservation across species. Add a clear legend explaining the visualization.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, "Reading the cis-regulatory code..."
- **Evidence pointer** Figure 3, Supplementary File 1
- **Issue** The authors report enrichment P-values but do not consistently report the number of genes in each cluster or the total number of clusters. This makes it difficult to assess the scale of the analysis.
- **Required correction** Report the number of clusters, the number of genes per cluster, and the number of genes with annotations for each cluster discussed in the text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Comparison of learned motifs to databases using TomTom"
- **Evidence pointer** Methods section
- **Issue** The authors state that TomTom outputs are available as supplementary data, but the specific version of TomTom and the parameters used (e.g., database version, scoring method) are not specified.
- **Required correction** Specify the version of TomTom and the parameters used for the database searches.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The authors discuss the potential of their approach for poorly characterized species, but they do not address potential limitations related to the quality of genome assemblies and annotations in such species. This is an important practical consideration.
- **Required correction** Add a brief discussion of how the approach might be affected by genome assembly quality, annotation completeness, and ortholog assignment accuracy in non-model organisms.

## Risk / unsupported claims
- The claim that RHIEPA predicts gene expression "better than using experimental data" is not fully supported by the presented comparisons, which are limited to NetProphet3 and BLAST. The comparison metric (1-NN regression) is also narrow.
- The novel predictions for C. albicans, N. crassa, and F. graminearum are presented as hypotheses, but the strength of the evidence is not fully quantified. The authors should avoid overstating the confidence of these predictions.
- The claim that the approach is "interpretable" is partially supported by the motif-based nature of the representation, but the interpretability of the attention-based interactions is not demonstrated or discussed.
- The generalizability of the approach to non-fungal organisms is not tested and should not be implied.