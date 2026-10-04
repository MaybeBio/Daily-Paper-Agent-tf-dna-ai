## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and supplementary material descriptions
- **Assessment boundary** Scientific validity, methodological soundness, interpretability of results, and alignment with claims made in the abstract and discussion
- **Shared manuscript claim summary** The authors propose a supervised clustering workflow using Random Forest models trained on DNA duplex stability (DDS) features and Shapley values to classify and discover subgroups within bacterial promoter sequences from six sigma factor families in E. coli K-12. They report identification of two promoter subgroups (P and V) distinguished by DDS conservation at positions −9 to −7, and five σ70 subclusters differing in the presence and position of a conserved C/G pair near the −10 motif.
- **Visible evidence base** Main text figures (Figs 2–7), Tables 1–2, supplementary materials S1–S19 (described but not fully visible)
- **Missing materials affecting confidence** Supplementary figures and tables S1–S19 are referenced but not provided in the submitted material; exact parameter values for Random Forest and UMAP are only partially described; raw data and code are not available for independent verification

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting application of supervised clustering with Shapley value interpretability to bacterial promoter classification. The core idea of using DDS as a biophysically grounded feature representation and then interrogating model attributions to discover promoter subgroups is timely and potentially useful. However, the current evidence base has several gaps that prevent full evaluation of the claims. The distinction between P and V subgroups rests primarily on visual inspection of sequence logos and DDS plots, with limited quantitative support. The relationship between the discovered clusters and biological function is speculative, and the authors themselves acknowledge that further experimental evidence is needed. The robustness analysis is described but the results are not shown in the visible material. Overall, the work is promising but not yet fully established from the provided evidence.

- **Who would be interested in the results, and why** Researchers working on bacterial promoter structure and function, particularly those interested in sigma factor selectivity and promoter strength prediction. The methodological approach combining supervised ML with Shapley value interpretability for biological sequence analysis will also appeal to bioinformaticians developing interpretable models for regulatory genomics. The finding that DDS-based features can separate promoter subgroups with different conserved positions may inform future promoter prediction tools and experimental design for promoter engineering.

- **Major strengths**  
  1. The use of DDS as a feature representation grounded in biophysical properties of DNA is well justified and mechanistically meaningful.  
  2. The supervised clustering workflow with Shapley values is a thoughtful integration of ML interpretability with unsupervised discovery.  
  3. The authors are transparent about the distinction between the SHAP model (trained on full data for attribution) and the evaluation model (train-test split for performance assessment), which is methodologically important.  
  4. The robustness analysis addressing the dependence on negative set composition is a good practice, though results are not fully visible.  
  5. The identification of distinct σ70 subclusters with different C/G positioning relative to the −10 motif is a concrete and potentially testable finding.

- **Major Concerns**

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical support for subgroup distinction  
- **Claim pointer** The authors claim identification of two promoter subgroups (P and V) differentiated by conservation of positions −9 to −7, and five σ70 subclusters with different C/G positioning.  
- **Evidence pointer** Figures 5 and 6, Results section "Clustering of promoter signals"  
- **Concern** The distinction between P and V subgroups is based on visual inspection of sequence logos and DDS plots. No quantitative metrics are provided to support the claim that these are statistically distinct groups rather than arbitrary divisions of a continuum. For the σ70 subclusters, the authors describe differences in C/G presence and position but do not provide statistical tests comparing the clusters' sequence compositions or DDS profiles. The DBSCAN clustering parameters were determined empirically, and no cluster validity indices (e.g., silhouette score, Davies-Bouldin index) are reported.  
- **Why it matters** Without quantitative support, the central claim of discovering two distinct promoter groups is not established. The biological interpretation and the proposed use of these subgroups in classification frameworks depend on the robustness and statistical validity of the clustering.  
- **Resolution test** Provide quantitative comparisons between clusters, such as position-specific nucleotide frequency differences with appropriate statistical tests (e.g., chi-square or Fisher's exact test per position), cluster validity indices, and bootstrap or cross-validation assessment of cluster stability.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Robustness of Shapley values to negative set composition  
- **Claim pointer** The authors state that "Shapley values are strongly correlated" across different random seeds for negative set generation, and that the same features are used to distinguish clusters.  
- **Evidence pointer** Methods section "Robustness of Shapley values to negative set composition", Supplementary materials S10–S11  
- **Concern** The robustness analysis is described in the methods but the actual results (correlation coefficients, cluster assignment consistency via ARI) are not presented in the visible material. The claim that results are consistent across seeds cannot be verified. Furthermore, the analysis only varies the random seed for generating random negative sequences; it does not test the sensitivity to the choice of negative set composition more broadly (e.g., using genomic background sequences, shuffled promoters, or coding regions with matched GC content).  
- **Why it matters** The supervised clustering results depend critically on the negative set used to train the classifier. If the Shapley values and resulting clusters are sensitive to negative set composition, the biological conclusions may be artifacts of the specific negative set chosen.  
- **Resolution test** Present the full robustness results including Pearson correlation coefficients and ARI values for all seeds. Additionally, test at least one alternative negative set construction (e.g., coding sequences or intergenic regions) and show that the main clustering findings are preserved.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** Biological interpretation and validation  
- **Claim pointer** The authors suggest that the discovered subgroups "could provide more insights into the sigma factor-promoter interaction and the separation of the DNA double-strand" and that P and V subgroups "could suggest different activity."  
- **Evidence pointer** Discussion section, Supplementary material S18  
- **Concern** The biological interpretation is largely speculative. The comparison with experimental promoter activity data (reference 40) is mentioned but the results are only summarized as "20% of the promoters per cluster are active" with no statistical analysis or clear presentation of how activity correlates with cluster membership. The claim that P and V subgroups may have different activities is not directly tested.  
- **Why it matters** The broader significance of the work depends on whether the discovered subgroups have biological relevance. Without direct validation linking cluster membership to measurable promoter activity or sigma factor binding, the findings remain a descriptive clustering exercise.  
- **Resolution test** Provide a clear statistical comparison of promoter activity between clusters using the experimental data from reference 40, including effect sizes and confidence intervals. If possible, validate the P/V distinction on an independent promoter dataset with known activity measurements.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Methodological clarity and reproducibility  
- **Claim pointer** The authors describe a supervised clustering workflow using Random Forest, DDS features, UMAP, and DBSCAN.  
- **Evidence pointer** Methods sections "Model training and evaluation", "Dimensionality reduction and clustering algorithms"  
- **Concern** Several methodological details are missing. The exact hyperparameters for Random Forest (beyond reference to Supplementary S2) and UMAP (n_neighbors selection criteria beyond "empirical") are not fully specified. The DBSCAN parameters (epsilon 1.5, min_samples 10) are stated but the sensitivity of results to these parameters is not explored. The procedure for selecting the number of UMAP dimensions (4) is not justified. The authors state that "the parameters of DBSCAN were determined empirically by visual inspection" which raises concerns about reproducibility and potential overfitting to the specific dataset.  
- **Why it matters** Reproducibility is a core requirement for computational biology studies. Without complete parameter specifications and sensitivity analyses, other researchers cannot reliably apply this workflow to their own promoter datasets.  
- **Resolution test** Provide complete hyperparameter specifications for all algorithms, justify the choice of UMAP dimensions, and include a sensitivity analysis showing that the main clustering conclusions are stable across reasonable parameter ranges for DBSCAN and UMAP.

- **Minor Comments**

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity of figure presentation  
- **Affected element** Figures 5 and 6  
- **Evidence pointer** Results section "Clustering of promoter signals"  
- **Issue** The sequence logos in Figures 5 and 6 are described but not visible in the submitted material. The authors reference "up to 1 bit of information" for the P cluster and "0.1 bits" for the V cluster, but without seeing the logos it is difficult to assess the visual distinction.  
- **Required correction** Ensure figures are clearly legible with appropriate resolution. Consider adding a quantitative comparison of information content between clusters at each position.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Terminology consistency  
- **Affected element** Abstract and Results  
- **Evidence pointer** Abstract, Results section  
- **Issue** The abstract states "two subgroups of sequences differentiated by the conservation of the −9 to −7 positions" while the Results section describes differences "between the −10 and −5 positions." These ranges are not identical and should be reconciled.  
- **Required correction** Clarify the exact positions that differentiate the P and V subgroups and ensure consistency between the abstract and the main text.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Statistical test reporting  
- **Affected element** Methods section "Statistical tests"  
- **Evidence pointer** Methods section "Statistical tests"  
- **Issue** The Kruskal-Wallis and Dunn's tests are described but the specific comparisons and results are not presented in the visible material. It is unclear which groups were compared and what the effect sizes were.  
- **Required correction** Report the specific test statistics, degrees of freedom, p-values, and effect sizes for all statistical comparisons in the main text or supplementary materials.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Data availability  
- **Affected element** Data availability statement  
- **Evidence pointer** Data availability section  
- **Issue** The data availability statement indicates that research data are available as supplementary materials S1–S16, but the supplementary materials are not provided with the manuscript. This prevents verification of the results.  
- **Required correction** Ensure all supplementary materials are submitted and accessible. Consider depositing the promoter sequence dataset and analysis code in a public repository.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Reference to experimental validation  
- **Affected element** Discussion section  
- **Evidence pointer** Discussion section, reference 40  
- **Issue** The comparison with experimental promoter activity data from reference 40 is mentioned but the details of this dataset and the analysis are not described. It is unclear how the activity data were obtained and how the comparison was performed.  
- **Required correction** Provide a brief description of the experimental dataset used for comparison and the analysis method. If this comparison is important for the conclusions, it should be presented in the main text rather than only in the discussion.

## Risk / unsupported claims
- The claim that P and V subgroups represent functionally distinct promoter classes is not supported by direct experimental evidence; the authors acknowledge this but the claim is presented prominently in the abstract.
- The statement that "Shapley values point to features of biological significance" is an interpretation that goes beyond what the analysis can establish; Shapley values indicate feature importance for the trained model, not biological causality.
- The claim that the workflow "could provide more insights into the sigma factor-promoter interaction" is speculative and not directly tested.
- The assertion that the discovered σ70 subclusters have different interaction mechanics with sigma factors is not supported by any experimental or structural evidence.
- The robustness of the clustering to negative set composition is claimed but not demonstrated in the visible material.
- The biological relevance of the P/V distinction is suggested but not validated with independent data or functional assays.