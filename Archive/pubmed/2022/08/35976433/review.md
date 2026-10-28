## Review setup
- **Input scope** Full manuscript text including abstract, introduction, materials and methods, results, discussion, and figure legends
- **Assessment boundary** Scientific validity, technical soundness, interpretation of results, and support of conclusions based on the provided manuscript content
- **Shared manuscript claim summary** The authors present single-nucleus ATAC-seq data from frontal cortex of PSP, CBD, and control cases, identifying astrocyte-specific chromatin accessibility changes, transcription factor motif enrichment signatures, and integration with GWAS risk variants and external transcriptomic data to propose disease-specific astrocyte regulon signatures, validated by immunofluorescence for selected target genes
- **Visible evidence base** Main text, figure legends for Figures 1-7, supplementary figure references, Table 1, and methods descriptions
- **Missing materials affecting confidence** Supplementary figures and data files referenced but not provided; detailed bioinformatic methods in Supplementary Methods not available; raw sequencing data not assessable; full statistical outputs and code not provided

## Reviewer
- **Overall assessment** This manuscript addresses an important gap in the field by providing the first single-nucleus chromatin accessibility profiling of PSP and CBD, two primary 4R tauopathies with overlapping but distinct neuropathology. The focus on astrocyte signatures is well justified given the neuropathological distinction between tufted astrocytes in PSP and astrocytic plaques in CBD. The study design is logical and the integration of multiple analytical approaches is ambitious. However, several technical and interpretational concerns limit the strength of the conclusions as currently presented. The small sample size (4 PSP, 4 CBD, 5 controls) is a major limitation that is not adequately addressed. The reliance on a single frontal cortex region, the lack of validation in independent cohorts, and the absence of key quality control metrics for the snATAC-seq data reduce confidence in the robustness of the findings. The immunofluorescence validation is limited to two target genes and does not directly validate the transcription factor activities inferred from motif analysis. The manuscript would benefit from clearer presentation of statistical methods, effect sizes, and the biological relevance of the identified signatures.

- **Who would be interested in the results, and why** Researchers in neurodegenerative disease biology, particularly those studying tauopathies, astrocyte biology, and epigenetic regulation in the CNS. The study provides a resource for understanding cell type-specific chromatin changes in PSP and CBD, which could inform future studies on disease mechanisms, biomarker development, and therapeutic targeting. The methodological framework combining snATAC-seq with GWAS integration and machine learning may also interest computational biologists working on single-cell epigenomics.

- **Major strengths** The study addresses a novel question with an appropriate technology, provides a multi-layered analytical approach, and identifies potentially important astrocyte-specific signatures. The integration of GWAS risk variants with cell type-specific chromatin accessibility is a valuable contribution. The authors are transparent about limitations such as the CBD3 outlier and perform a sensitivity analysis.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim reliable cell type identification and clustering from snATAC-seq data, and report specific cell type proportions and differences between disease groups.
- **Evidence pointer** Results section "Characterization of PSP and CBD frontal lobe brain nuclei via snATAC-seq", Figure 2, Supplementary Figures 1-4
- **Concern** The manuscript does not provide sufficient quality control metrics for the snATAC-seq data. Key parameters such as the number of unique fragments per nucleus, fraction of fragments in peaks, transcription start site enrichment scores, and the number of nuclei passing QC per sample are not reported. The clustering approach and the criteria for assigning cell type identity are described only briefly, and the resolution to distinguish closely related cell types (e.g., astrocyte subtypes, distinct neuronal populations) is not demonstrated. The authors report 45,205 nuclei total across 13 samples, but the per-sample distribution and whether this is sufficient for robust downstream analyses is unclear. The sensitivity analysis excluding CBD3 is mentioned but the impact on all major results is not fully shown.
- **Why it matters** Without adequate QC metrics and clear demonstration of cell type resolution, the validity of all downstream analyses, including cell type proportion comparisons, differential accessibility, and TF motif analyses, is uncertain. The small sample size amplifies the impact of any technical variability or misclassification.
- **Resolution test** Provide comprehensive QC metrics per sample, including the number of nuclei, median fragments per nucleus, fraction of fragments in peaks, and TSS enrichment. Demonstrate cluster stability and marker gene specificity. Show that the reported cell type proportions and differences are robust to QC thresholds and clustering parameters. Provide a more detailed description of the sensitivity analysis excluding CBD3, including whether all major conclusions hold.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors report statistically significant differences in cell type proportions, differential accessibility, and TF motif enrichment between PSP, CBD, and control groups.
- **Evidence pointer** Results sections throughout, Figure 2c, Figure 3, Figure 4, Figure 5, Figure 6
- **Concern** The statistical methods for comparing cell type proportions and for differential accessibility analysis are not described in sufficient detail. For cell type proportion comparisons, it is unclear whether the analysis accounts for the nested structure of the data (multiple nuclei per individual) and the small number of biological replicates. For differential accessibility and TF motif enrichment, the authors mention Wilcoxon rank-sum tests and BH correction, but the unit of analysis (nuclei vs. individual) is not clearly stated. Pseudobulk approaches are standard for such analyses to avoid pseudoreplication, and it is unclear if this was done. The machine learning model's performance metrics are reported, but the potential for overfitting given the small sample size is not adequately discussed.
- **Why it matters** Inflated statistical significance due to pseudoreplication or inappropriate unit of analysis could lead to false positive findings. The small number of biological replicates (4 per group) limits statistical power, and the manuscript does not address how this affects the reliability of the reported differences.
- **Resolution test** Clearly state the unit of analysis for all statistical tests. Use pseudobulk approaches for differential accessibility and TF motif analyses, aggregating reads per individual. Report effect sizes and confidence intervals. Discuss the statistical power given the sample size. For the machine learning model, provide cross-validation details and discuss the risk of overfitting.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation and support of conclusions
- **Claim pointer** The authors conclude that "astrocyte-relevant epigenetic alterations" and specific TF signatures distinguish PSP and CBD, and that these signatures are "meaningful biologically as the representation of a pathogenetically relevant gene expression program."
- **Evidence pointer** Discussion section, Figure 6, Figure 7
- **Concern** The causal or mechanistic link between the identified TF motif accessibility changes and disease pathogenesis is not established. The authors infer TF activity from motif enrichment in open chromatin regions, but this does not directly demonstrate TF binding or functional consequences on gene expression. The validation is limited to two target genes (MAP3K8 and CTSD) at the protein level, and the connection between these targets and the broader TF signatures is not fully explored. The statement that the signatures are "pathogenetically relevant" is an overinterpretation given the descriptive nature of the data. The authors acknowledge that accessibility changes could be secondary, but this caveat is not sufficiently integrated into the conclusions.
- **Why it matters** The central claim of the paper is that distinct astrocyte signatures are biologically meaningful. Without functional validation or a clear mechanistic link, the significance of the findings remains correlative. Overinterpretation could mislead the field.
- **Resolution test** Soften the conclusions to reflect the descriptive and correlative nature of the findings. Provide additional evidence linking TF motif accessibility to actual TF activity, such as integration with gene expression data (e.g., snRNA-seq) or chromatin immunoprecipitation experiments. Expand the validation to include more target genes and demonstrate that the protein changes are specific to the predicted TF regulatory networks.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and data availability
- **Claim pointer** The authors state that the analysis is based on a detailed bioinformatic workflow described in Supplementary Methods, and that data are available.
- **Evidence pointer** Methods section, Supplementary Information
- **Concern** The Supplementary Methods, which contain the detailed bioinformatic analysis, are not provided for review. Key parameters for the Cicero analysis, tradeSeq modeling, RTN network reconstruction, and the machine learning approach are not described in the main text. The availability of the raw sequencing data and processed data matrices is not stated. The custom code is mentioned to be on GitHub, but the repository is not referenced in the provided text.
- **Why it matters** Reproducibility is a core requirement for scientific publication. Without access to the detailed methods and data, other researchers cannot replicate or build upon this work.
- **Resolution test** Provide the Supplementary Methods for review. State data availability clearly, including accession numbers for raw and processed data. Provide the GitHub repository link and ensure the code is documented and accessible.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Sample size and generalizability
- **Claim pointer** The authors generalize their findings to PSP and CBD based on 4 cases per disease group.
- **Evidence pointer** Table 1, Methods section
- **Concern** The sample size is very small (n=4 per disease group, n=5 controls). The manuscript does not discuss the potential impact of this small sample size on the robustness and generalizability of the findings. The cases are not fully characterized in terms of disease duration, severity, or regional distribution of pathology, which could influence chromatin accessibility profiles. The selection of frontal cortex as the sole region of interest is not justified, given that PSP and CBD have distinct regional patterns of pathology.
- **Why it matters** Small sample sizes increase the risk of false positives and limit the ability to detect true differences. The findings may not be representative of the broader PSP and CBD populations.
- **Resolution test** Acknowledge the small sample size as a major limitation. Provide a power analysis or discussion of the detectable effect sizes. Consider validating key findings in an independent cohort or in additional brain regions. Provide more detailed clinical and neuropathological characterization of the cases.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1 legend
- **Issue** The figure legend is very long and contains a large amount of methodological detail that would be better placed in the Methods section. The legend is difficult to follow.
- **Required correction** Shorten the figure legend to focus on the key elements of the figure. Move detailed methodological descriptions to the Methods or Supplementary Methods.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 2c
- **Evidence pointer** Figure 2c legend
- **Issue** The statistical test used for cell type proportion comparisons is mentioned as Welch t-test, but the multiple testing correction across the many cell types compared is not described.
- **Required correction** State whether multiple testing correction was applied and, if so, which method. If not, justify the approach.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, paragraph 2
- **Evidence pointer** Discussion section
- **Issue** The statement "To our surprise, we did neither find microglia-associated accessibility changes" is presented as a key negative finding, but the power to detect such changes is limited by the small sample size and the analysis approach.
- **Required correction** Soften this statement and acknowledge the limitations in detecting microglial changes.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods, "Analysis of snATAC-seq data"
- **Evidence pointer** Methods section
- **Issue** The description of the machine learning model is brief. The hyperparameters, feature selection, and evaluation metrics are not fully described.
- **Required correction** Provide more detail on the machine learning model, including hyperparameters, feature selection, and evaluation procedures.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 7
- **Evidence pointer** Figure 7 legend
- **Issue** The figure legend for Figure 7 is complex and the boxplots are not clearly described. The statistical test used is mentioned as paired t-test, but the pairing structure is not clear.
- **Required correction** Clarify the boxplot statistics and the pairing structure. Consider simplifying the figure.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction, paragraph 1
- **Evidence pointer** Introduction section
- **Issue** The introduction is brief and does not fully contextualize the study within the broader field of tauopathy epigenetics and astrocyte biology.
- **Required correction** Expand the introduction to provide more background on prior epigenetic studies in tauopathies and the role of astrocytes in these diseases.

## Risk / unsupported claims
- The claim that the identified TF signatures are "pathogenetically relevant" is not supported by the data, which are descriptive and correlative.
- The claim that microglia are not involved in PSP and CBD based on the lack of accessibility changes is not supported given the small sample size and potential power limitations.
- The generalization of findings from 4 cases per disease group to the broader PSP and CBD populations is not supported.
- The inference of TF activity from motif enrichment alone, without validation of TF binding or functional consequences, is not fully supported.
- The statement that the proposed signatures could "aid future TF-based studies with latent or missing phenotype data in a priori trait mapping" is speculative and not directly supported by the data.