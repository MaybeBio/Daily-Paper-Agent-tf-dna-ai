## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, competing interests, data availability)
- **Assessment boundary** Scientific content, methodological soundness, claims versus evidence, resource utility, and alignment with Nature-style criteria. Not a line-by-line editorial review.
- **Shared manuscript claim summary** The authors present CellRegulon, a large-scale atlas of transcription factor (TF) regulons derived from ~5 million single-cell RNA-seq cells across 15 organ systems and ~550 cell types. They demonstrate applications in B cell differentiation, disease gene signature mapping (adult and childhood asthma), and extension to enhancer-gene regulatory networks (eGRNs) using a new adult lung multiome dataset. They further integrate GWAS data for asthma, COPD, and IPF to identify cell-type-specific disease associations and provide an interactive web resource and Python package.
- **Visible evidence base** Abstract, full introduction, full results sections (with figure references), discussion, methods (partial), data availability statement, competing interests. Figure panels are referenced but not directly viewable.
- **Missing materials affecting confidence** Figure images and legends are not provided. Supplementary figures and tables are referenced but not available. The full methods for regulon computation, snp2cell analysis, and multiome processing are only partially described. No code repository link is provided in the visible text. The web resource (cellregulondb.org) is not accessible for verification.

## Reviewer
- **Overall assessment** This manuscript describes a substantial and potentially valuable community resource: a cell-type-resolved atlas of TF regulons spanning a wide range of human tissues. The scale of data integration (~5 million cells, 15 organ systems) is impressive, and the demonstrated applications, particularly the extension to eGRNs with GWAS integration, are timely and relevant. However, the manuscript as presented has several significant gaps. The validation of regulon predictions is largely indirect, relying on known biology rather than quantitative benchmarking. The disease association analyses, while suggestive, lack formal statistical rigor in places and would benefit from clearer null models. The comparison between CellRegulon and the multiome-derived eGRN is interesting but the claimed superiority of the larger dataset is based on a single metric (precision at recall) for a single cell type. The manuscript would be strengthened by more systematic benchmarking, clearer presentation of the statistical methods, and a more critical discussion of limitations. The resource itself is likely to be of high interest to the community, but the scientific claims need to be more firmly established.
- **Who would be interested in the results, and why** This resource will be of direct interest to researchers in gene regulation, developmental biology, and computational biology. Those studying cell-type-specific transcription factor function, cellular differentiation, and disease mechanisms, particularly in the lung, will find the atlas and the eGRN extension useful for hypothesis generation. The integration with GWAS data provides a bridge for human geneticists and those studying complex disease. The interactive database and Python package lower the barrier for non-specialists to explore TF programs in their cell types of interest.
- **Major strengths**
  1. The scale and scope of the CellRegulon atlas is a major achievement, integrating a large body of single-cell data to provide a comprehensive view of TF programs.
  2. The demonstration of the utility of the atlas in multiple contexts (B cell differentiation, disease signatures, GWAS integration) is compelling and shows its broad applicability.
  3. The creation of a new adult lung multiome dataset and its integration into an eGRN is a valuable contribution in itself, providing a resource for lung biology.
  4. The provision of an interactive web interface and a Python package is commendable and will facilitate community adoption.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Validation
- **Claim pointer** The manuscript claims that CellRegulon provides accurate cell-type-specific TF-target gene predictions, validated by recapitulating known B cell biology.
- **Evidence pointer** Results section "Regulatory map of cell type transitions in the B cell lineage", Figure 2
- **Concern** The validation of the regulon predictions is largely qualitative and based on known biology. The authors state that the atlas recapitulates known B cell differentiation, but no quantitative benchmarking is provided. For example, how does the precision and recall of CellRegulon compare to other methods (e.g., SCENIC, ARACNe) on a gold-standard set of TF-target interactions? The comparison between crReg and eReg for B cells (Figure 4g) is a step in this direction, but it is limited to a single cell type and a single metric. A more systematic and quantitative validation is needed to establish the reliability of the atlas.
- **Why it matters** Without quantitative benchmarking, it is difficult for users to assess the confidence they should place in the regulon predictions. The claim that the atlas is a reliable resource for hypothesis generation is weakened if its accuracy is not rigorously demonstrated.
- **Resolution test** Provide a quantitative comparison of CellRegulon predictions against a curated gold standard of TF-target interactions (e.g., from ChIP-seq, literature-curated databases) across multiple cell types. Report precision-recall curves or similar metrics and compare against at least one other state-of-the-art method.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor / Disease relevance
- **Claim pointer** The manuscript claims that snp2cell analysis identifies cell-type-specific disease associations for asthma, COPD, and IPF, and that the eGRN improves cell-type associations with genetic risk loci.
- **Evidence pointer** Results section "Gene regulatory networks in lung disease", Figure 5
- **Concern** The statistical framework for the disease association analysis is not fully described. The authors state that snp2cell propagates association scores over the network and computes "significant enrichments," but the details of the null model, multiple testing correction, and how significance is defined are not provided in the visible text. The claim that the eGRN "improves" cell-type associations is based on a comparison that is not clearly described. What is the baseline? Is it a comparison to using only promoter-based regulons? The lack of statistical detail makes it impossible to evaluate the robustness of these findings.
- **Why it matters** The disease association results are a key selling point of the manuscript. If the statistical methods are not transparent and rigorous, the conclusions about disease-relevant cell types and TFs are not trustworthy.
- **Resolution test** Provide a detailed description of the snp2cell analysis, including the null model, the definition of significance, and the multiple testing correction. Clearly state the baseline for the "improvement" claim and provide a statistical test for the difference.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Data integration
- **Claim pointer** The manuscript claims that the multiomic eGRN, built from a new dataset of ~37,000 cells, is less comprehensive than CellRegulon, which was built from ~5 million cells, and that this is due to the larger data volume.
- **Evidence pointer** Results section "Extension into a multi-omic regulon atlas of adult lung", Figure 4
- **Concern** The comparison between the eGRN and CellRegulon is confounded by more than just data volume. The two networks are built using different pipelines (SCENIC+ vs. pySCENIC), different input data modalities (RNA+ATAC vs. RNA only), and different cell type annotations. The claim that the difference in performance is due to "increased data volume" is an over-simplification and is not directly supported by the presented analysis. A controlled experiment, where the same pipeline is run on datasets of different sizes, would be needed to make this claim.
- **Why it matters** The manuscript makes a general claim about the benefits of large-scale data integration. If this claim is not rigorously supported, it could mislead the field about the relative importance of data volume versus algorithmic improvements.
- **Resolution test** Perform a controlled down-sampling experiment where the CellRegulon pipeline is run on a subset of the data to match the size of the multiome dataset, and compare the performance. Alternatively, run SCENIC+ on a larger RNA-only dataset to isolate the effect of data modality.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Originality / Scientific importance
- **Claim pointer** The manuscript claims that CellRegulon is a novel resource that provides a "detailed census of TF dependent transcriptional states."
- **Evidence pointer** Abstract, Introduction, Discussion
- **Concern** While the scale of the atlas is impressive, the conceptual approach of using co-expression and motif analysis to predict TF regulons is well-established (e.g., SCENIC). The novelty appears to lie primarily in the scale of data integration and the specific applications. The authors should more clearly articulate what is conceptually new about their approach or findings, beyond the sheer size of the resource. The claim of a "census" is strong; how complete is the coverage of known human TFs and cell types?
- **Why it matters** For a Nature-style publication, the conceptual advance needs to be clear. If the contribution is primarily a larger database, the scientific importance may be seen as incremental rather than transformative.
- **Resolution test** Clearly state the conceptual novelty in the discussion. Provide a quantitative assessment of the coverage of the atlas (e.g., what fraction of all known human TFs are represented, what fraction of expected cell types are covered).

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Readability for nonspecialists
- **Claim pointer** The manuscript claims to provide a resource that is accessible for "cell type engineering" and other applications.
- **Evidence pointer** Abstract, Discussion
- **Concern** The manuscript is dense and assumes a high level of familiarity with computational genomics. The description of the methods and results is likely to be challenging for a non-specialist reader. The potential applications, such as "cell type engineering," are mentioned but not explained in a way that a broader audience would understand. The figures are referenced but not visible, making it hard to assess their clarity.
- **Why it matters** Nature-style papers aim to reach a broad audience. If the key findings and the utility of the resource are not accessible to non-specialists, the impact will be limited.
- **Resolution test** Revise the text to include a clearer, more accessible summary of the key findings and the potential applications. Ensure that the figures are self-explanatory and that the main messages are clear from the figures alone.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1
- **Evidence pointer** Results section "Census of transcription factors across single cell datasets"
- **Issue** The text refers to "Fig. 1a, right top" and "Fig. 1a, right bottom" but the figure is not visible. The description of the "spherical shape" of the regulon space is intriguing but not fully explained.
- **Required correction** Ensure the figure legend clearly explains the different panels and the meaning of the "spherical shape" of the regulon space.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods
- **Evidence pointer** Methods section "Computation of regulons"
- **Issue** The methods for computing regulons are described briefly. The specific parameters used for pySCENIC (e.g., the motif databases, the thresholds for co-expression and motif enrichment) are not provided.
- **Required correction** Provide a more detailed description of the parameters and thresholds used in the pySCENIC pipeline to ensure reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 4e
- **Evidence pointer** Results section "Extension into a multi-omic regulon atlas of adult lung"
- **Issue** The text reports a p-value of 0.0036 for the comparison of regulon specificity scores (RSS) but does not state the effect size or the number of cell types compared.
- **Required correction** Report the effect size and the number of cell types included in the Wilcoxon rank-sum test.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the "limitation" of the approach is brief and does not address potential sources of false positives in the regulon predictions (e.g., indirect effects, co-expression due to shared cell type composition).
- **Required correction** Expand the discussion of limitations to include a more critical assessment of the potential for false discoveries and the interpretability of the regulons.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Resource availability
- **Affected element** Data Availability
- **Evidence pointer** Data Availability section
- **Issue** The data availability statement says data "will be released upon publication." This is a barrier for reviewers and for the community if the publication process is delayed.
- **Required correction** Consider making the data available at the time of preprint submission to maximize the utility of the resource.

## Risk / unsupported claims
- The claim that the multiomic eGRN is less comprehensive than CellRegulon due to "increased data volume" is not directly supported by the presented analysis, as the two networks are built with different pipelines and data modalities.
- The claim that the atlas "can be used to predict cell-type specific TF activity from bulk RNAseq data" is mentioned in the introduction but not demonstrated in the results.
- The claim that the atlas is valuable for "cell type engineering" is not substantiated with any examples or discussion.
- The statistical significance of the disease association results (Figure 5) cannot be fully evaluated without a detailed description of the null model and multiple testing correction.
- The completeness of the "census" of TF programs is not quantified; the claim of a "detailed census" is not supported by a clear definition of coverage.