## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, and figure legends
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors use massively parallel reporter assays (MPRAs) covering >100x the sequence space of the human genome to measure transcriptional activity of DNA sequences, and report that transcription factors act largely additively with weak positional grammar, that enhancers can be classified into three types, and that enhancer-promoter interactions are nonspecific and additive.
- **Visible evidence base** Main text figures 1-7, extended data figures 1-9, supplementary figures 1-4, supplementary tables 1-12, methods section
- **Missing materials affecting confidence** Raw sequencing data, complete statistical analysis details, model hyperparameters for all machine learning analyses, full supplementary methods text, and code availability details are not fully visible in the provided material

## Reviewer

- **Overall assessment** This manuscript presents a large-scale, systematic effort to characterize sequence determinants of human gene regulatory elements using an impressive MPRA design spanning over 100 times the human genome sequence space. The work is ambitious and the data resource is potentially valuable. However, several key claims, particularly regarding the classification of enhancer types and the additivity of enhancer-promoter interactions, require stronger statistical support and clearer presentation of the underlying evidence. The machine learning analyses are described but key details of model interpretation and validation are deferred to supplementary materials, limiting the ability to fully assess the robustness of the conclusions.

- **Who would be interested in the results, and why** Researchers in gene regulation, transcriptional control, and regulatory genomics would be the primary audience. The large-scale MPRA dataset and the proposed classification of enhancers into three types could be of interest to those studying enhancer biology and chromatin structure. The finding that TF interactions are largely additive has implications for computational models of gene expression. The machine learning approaches for predicting regulatory activity from sequence may interest computational biologists.

- **Major strengths** 
  1. The scale of the experimental design is impressive, covering a sequence space 100 times larger than the human genome, which allows for unbiased discovery of regulatory determinants.
  2. The combination of designed motif libraries, random sequences, and genomic fragments provides complementary approaches to dissect regulatory element activity.
  3. The integration of multiple machine learning methods (logistic regression, CNN) with traditional motif analysis is a modern and appropriate approach.
  4. The identification of three enhancer types and the distinction between classical and chromatin-dependent enhancers is a potentially important conceptual contribution.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and evidence for enhancer classification
- **Claim pointer** The manuscript claims that enhancers can be classified into three types: classical, closed chromatin, and chromatin dependent, based on their chromatin features and activity patterns.
- **Evidence pointer** Figure 4a-c, Extended Data Figure 6a-b, location not provided for specific statistical tests
- **Concern** The classification of enhancers into three distinct types appears to be based on qualitative assessment of chromatin features and STARR-seq activity. The manuscript does not provide a clear quantitative framework or statistical test demonstrating that these three categories are statistically distinct from each other or from a continuous distribution of enhancer properties. The overlap analysis with ATAC-seq, histone marks, and TF binding is descriptive, but no formal clustering or classification analysis is presented to justify the discrete categorization.
- **Why it matters** The three-type classification is a central conceptual claim of the paper. If the underlying data actually represent a continuum of enhancer properties, the proposed taxonomy would be an oversimplification that could mislead subsequent research. A rigorous statistical demonstration of distinct categories is essential to support this claim.
- **Resolution test** The authors should provide a formal statistical analysis (e.g., clustering with appropriate validation, mixture modeling, or classification with cross-validation) demonstrating that the three proposed enhancer types are statistically separable based on their chromatin and activity features. Alternatively, they should present the data as a continuum and temper the classification claim accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence for additivity of enhancer-promoter interactions
- **Claim pointer** The manuscript claims that enhancer-promoter interactions are additive and nonspecific, based on the observation that all motif pairs are independently enriched and that permuting promoter-enhancer pairings does not reduce CNN performance.
- **Evidence pointer** Figure 7a-c, location not provided for the permutation test details
- **Concern** The conclusion that enhancer-promoter interactions are additive and nonspecific is based on two analyses: (1) the observation that motif pairs are independently enriched, and (2) the CNN permutation experiment. For the first analysis, the manuscript states that "almost all pairs of TF motifs enriched independently of each other" but does not provide the full distribution of interaction effects or the criteria for calling a pair "independent." For the CNN permutation experiment, the claim that permuted pairings perform similarly to true pairings is stated but the actual performance metrics and statistical comparison are not shown in the main text. The power of this test to detect specific interactions depends on the complexity of the model and the diversity of the sequence library, which is not discussed.
- **Why it matters** The additivity claim has major implications for understanding the mechanisms of enhancer-promoter communication and for building predictive models of gene expression. If the test lacks statistical power to detect specific interactions, the conclusion of additivity would be premature and potentially incorrect.
- **Resolution test** The authors should provide the full distribution of interaction effects for all motif pairs, including a clear definition of "independence." For the CNN permutation test, they should report the performance metrics (e.g., AUPRC) for both the true and permuted pairings, with confidence intervals and a formal statistical test demonstrating equivalence or non-inferiority. They should also discuss the statistical power of their test to detect specific interactions given the sequence library complexity.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of findings across cell types
- **Claim pointer** The manuscript claims that most TF activities are similar between cell types, with only a few lineage-specific TFs showing differential activity.
- **Evidence pointer** Figure 2f, Figure 3a, Extended Data Figure 1a-c
- **Concern** The comparison of TF activities between GP5d and HepG2 cells is based on only two cell types, both of which are cancer cell lines. The claim that "most activities being similar between cell types" is a strong generalization from a limited sample. Additionally, the manuscript does not address how the transformed nature of these cell lines might affect the generalizability of the findings to primary cells or in vivo contexts. The correlation of 0.78 between motif activities in the two cell lines, while substantial, still leaves considerable room for cell-type-specific effects that are not captured by the current analysis.
- **Why it matters** The generalizability of the findings is important for the broader relevance of the work. If the conclusions are largely based on cancer cell lines, they may not accurately reflect regulatory mechanisms in normal tissues. The claim of similarity across cell types needs to be qualified by the limited number and transformed nature of the cell types examined.
- **Resolution test** The authors should either (1) include additional cell types, particularly non-transformed or primary cells, to strengthen the generalizability claim, or (2) temper their conclusions to reflect the limited cell type sampling and explicitly discuss the potential limitations of using cancer cell lines.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Validation of machine learning model interpretations
- **Claim pointer** The manuscript claims that CNN analysis reveals that individual TFs contribute to enhancer function mostly without specific interactions, and that the CNN learned biologically meaningful features.
- **Evidence pointer** Figure 2e, Extended Data Figures 3-4, Supplementary Figure 2
- **Concern** The interpretation of the CNN models relies heavily on post-hoc analysis methods (e.g., TF-MoDISco, DeepLIFT) that are described only in supplementary materials. The manuscript does not provide sufficient detail in the main text about how these interpretations were validated. For example, it is unclear whether the motifs identified by the CNN match known TF binding preferences beyond qualitative visual comparison, and whether the attribution scores from DeepLIFT were validated against independent experimental perturbations. The claim that the CNN learned features similar to those from logistic regression is stated but the quantitative comparison is not shown.
- **Why it matters** The machine learning analysis is a key component of the paper's methodology and supports several central claims. If the model interpretation methods are not rigorously validated, the biological conclusions drawn from them may be unreliable. The reproducibility of these analyses depends on clear documentation of the interpretation pipeline.
- **Resolution test** The authors should provide quantitative validation of the CNN-interpreted motifs (e.g., comparison to known motifs using established metrics like Tomtom similarity scores) and demonstrate that the attribution analysis is robust to model initialization and hyperparameter choices. They should also show a direct quantitative comparison between CNN and logistic regression feature importance.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Evidence for the G-rich element interacting with TSS
- **Claim pointer** The manuscript claims discovery of a G-rich element that interacts with the TSS, potentially positioning RNA polymerase II independently of the TATA box.
- **Evidence pointer** Figure 6b-c, location not provided for the mutual information analysis details
- **Concern** The mutual information analysis identifies a G-rich region downstream of the TSS, but the functional significance of this element is not directly tested. The claim that this element "interacts with the TSS" implies a functional interaction, but the evidence presented is correlative (sequence co-occurrence patterns). No perturbation experiments (e.g., mutating the G-rich element and measuring promoter activity) are presented to demonstrate a causal role. The mechanistic interpretation involving RNA polymerase II positioning is speculative.
- **Why it matters** The discovery of a new promoter element would be a significant contribution, but the current evidence is insufficient to establish its functional importance. Overinterpretation of correlative sequence patterns as functional elements could mislead subsequent research.
- **Resolution test** The authors should either (1) provide direct experimental evidence for the functional role of the G-rich element (e.g., mutagenesis in the MPRA system), or (2) clearly frame this as a preliminary observation requiring further validation, and temper the mechanistic claims accordingly.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure presentation
- **Affected element** Figure 1c
- **Evidence pointer** Figure 1c
- **Issue** The figure shows median fold change for a large number of motifs, but the labeling is dense and difficult to read. The distinction between the most active motifs and the rest is not visually clear.
- **Required correction** Consider using a ranked plot or highlighting the top motifs to improve readability. Provide a clear legend explaining the color scheme and the significance of the red line.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Correlation coefficients
- **Evidence pointer** Figure 2a, 2f, 5a
- **Issue** Pearson correlation coefficients are reported without confidence intervals or p-values in several places. Given the large number of data points, even small correlations may be statistically significant, and the practical significance is unclear.
- **Required correction** Report confidence intervals and p-values for all correlation coefficients, and discuss the practical significance of the observed correlations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** MPRA library construction
- **Evidence pointer** Methods section, "STARR-seq reporter library construction and cloning"
- **Issue** The description of the library construction is brief and refers to supplementary methods for details. The number of biological replicates for each library type is not clearly stated in the main text.
- **Required correction** Provide a summary of the number of replicates and the key quality control metrics in the main text or a supplementary table.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** "Classical enhancer" vs "chromatin-dependent enhancer"
- **Evidence pointer** Figure 4a-c, Discussion
- **Issue** The distinction between "classical" and "chromatin-dependent" enhancers is introduced in the results but the operational definition is not fully clear. It appears to be based on STARR-seq activity and chromatin features, but the exact criteria for classification are not stated.
- **Required correction** Provide a clear operational definition of each enhancer type, including the specific thresholds or criteria used for classification.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** External validation
- **Affected element** Comparison to existing datasets
- **Evidence pointer** Discussion
- **Issue** The manuscript does not compare the identified enhancer types or TF activity patterns to existing large-scale datasets (e.g., ENCODE, FANTOM) beyond brief mentions. Such comparisons would strengthen the validity of the findings.
- **Required correction** Add a section comparing the identified enhancer types and TF activities to existing annotations and datasets, and discuss any discrepancies.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Code and data availability
- **Evidence pointer** Online content section
- **Issue** The data and code availability statement is not visible in the provided text. Given the computational nature of the analyses, clear availability of code and processed data is essential for reproducibility.
- **Required correction** Ensure a clear data and code availability statement is included, with specific accession numbers and repository links.

## Risk / unsupported claims
- The claim that enhancers can be classified into three distinct types (classical, closed chromatin, chromatin dependent) is not supported by formal statistical analysis demonstrating discrete categories.
- The claim that enhancer-promoter interactions are "additive and nonspecific" is based on analyses whose statistical power and full results are not presented in the main text.
- The claim that a G-rich element "interacts with the TSS" and positions RNA polymerase II is speculative and not supported by direct functional evidence.
- The generalization that "most TF activities are similar between cell types" is based on only two cancer cell lines and may not be representative of primary cells or in vivo contexts.
- The claim that the CNN learned features similar to those from logistic regression is stated without quantitative comparison.
- The overall conclusion that "transcriptional activity can be predicted from sequence" is supported, but the specific mechanisms proposed (additivity, weak grammar) require stronger evidence.

## Assessment against Nature-style criteria
- **Originality** The work is original in its scale and systematic approach. The use of MPRA libraries covering >100x the human genome sequence space is novel and provides a unique resource. The proposed classification of enhancers into three types, while potentially oversimplified, is a new conceptual framework.
- **Scientific importance** The findings have significant implications for understanding gene regulation. The large-scale dataset and the proposed additivity of TF interactions could inform future models of gene expression. However, the importance is somewhat tempered by the limited cell type sampling and the need for stronger statistical support for key claims.
- **Interdisciplinary readership** The work is primarily of interest to molecular biologists, genomicists, and computational biologists. The methods and findings may not be immediately accessible to a broader scientific audience without additional context. The machine learning components may be of interest to computational scientists but the presentation assumes familiarity with the field.
- **Technical soundness** The experimental design is generally sound, with appropriate controls and replicates. However, the statistical support for several key claims (enhancer classification, additivity of interactions) is insufficient as presented. The machine learning analyses are described but key validation details are deferred to supplementary materials.
- **Readability for nonspecialists** The manuscript is clearly written but assumes significant background knowledge in gene regulation and genomics. The main findings are summarized well in the abstract and discussion, but the results section is dense and may be challenging for nonspecialists to follow.

## Recommendation posture
**Supportive if technical concerns are resolved.** The manuscript presents a valuable and large-scale dataset with potentially important conceptual contributions. However, the central claims regarding enhancer classification and the additivity of enhancer-promoter interactions require stronger statistical support and clearer presentation of the evidence. The machine learning analyses need more rigorous validation and documentation. If these concerns are adequately addressed, the work would be a significant contribution to the field.