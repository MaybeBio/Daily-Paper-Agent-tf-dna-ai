## Review setup
- **Input scope** Full manuscript text (abstract, background, methods, results, discussion, supplementary figure/table legends) as provided
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and alignment with Nature-style criteria. Editorial and minor language issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors present INFLAMeR, a machine learning model integrating transcription factor binding and genomic features to predict functional lncRNAs. They report 85% validation of predicted lncRNAs in K562 cells, and characterize SNHG6 as a regulator of hematopoietic differentiation with in vivo tumor growth attenuation.
- **Visible evidence base** Main text figures 1-5 (described in text), supplementary figures S1-S13 and tables S1-S11 (legends only), methods descriptions, statistical details
- **Missing materials affecting confidence** Actual figure images, raw data files, complete supplementary tables, code repository contents, detailed experimental protocols for differentiation assays, and full statistical outputs were not available for review

## Reviewer
- **Overall assessment** This manuscript presents a potentially useful computational framework for prioritizing functional lncRNAs, with substantial experimental validation. The integration of TF binding data with genomic features to predict lncRNA functionality is a reasonable approach, and the validation rate of 85% is impressive. However, several methodological details and analytical choices require clarification, and the mechanistic characterization of SNHG6, while suggestive, remains incomplete. The clinical relevance claims, particularly regarding leukemia prognosis, are not directly supported by the data presented. The work is of interest to the lncRNA and hematopoiesis communities, but the current evidence does not fully establish the mechanistic model proposed.

- **Who would be interested in the results, and why** Researchers studying lncRNA function, particularly those interested in computational prediction of functional lncRNAs and in hematopoiesis or leukemia biology. The INFLAMeR framework could be of interest to computational biologists developing tools for functional genomics. The SNHG6 findings may interest investigators studying erythroid and megakaryocytic differentiation, as well as those exploring lncRNA roles in leukemia.

- **Major strengths** 
  1. The computational approach is well-reasoned, with careful attention to class imbalance and feature selection
  2. The validation strategy is comprehensive, combining knockdown, overexpression, and in vivo models
  3. The 85% validation rate is notable and suggests the model has genuine predictive power
  4. The identification of SNHG6 as a regulator of hematopoietic differentiation is potentially significant
  5. The authors appropriately used multiple validation methods (CRISPRi, CRISPR knockout, overexpression)

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that INFLAMeR successfully "reconstituted CRISPRi screening data" and that the model has high predictive accuracy
- **Evidence pointer** Methods "Model performance" section, Figure 1b-c, Supplementary Tables S6-S10
- **Concern** The model evaluation relies heavily on cross-validation on the training data derived from the same CRISPRi screens. The authors do not demonstrate external validation on independent datasets or experimental screens. The AUROC of 0.8250, while reasonable, is reported without confidence intervals across the three randomized repeats. More critically, the positive predictive value appears low given the 1:55 class imbalance, and the authors do not report calibration metrics or precision-recall curves, which would be more informative for this imbalanced setting.
- **Why it matters** Without external validation or more robust performance metrics, it is difficult to assess whether INFLAMeR would generalize to other cell types or experimental conditions. The claim of high predictive accuracy may be overstated if the model primarily learns screen-specific artifacts rather than general features of functional lncRNAs.
- **Resolution test** Provide external validation on an independent CRISPRi screen or experimentally validate a larger, pre-registered set of predictions. Report precision-recall curves, calibration plots, and confidence intervals for all performance metrics.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The claim that SNHG6 KD "sensitized them to differentiation" and specifically promotes erythrocyte differentiation while inhibiting megakaryocyte differentiation
- **Evidence pointer** Results section "SNHG6 regulates hematopoietic differentiation in K562 cells", Figure 5b-c, Supplementary Figure S13
- **Concern** The differentiation assays rely on single surface markers (GPA for erythroid, CD41/CD61 for megakaryocytic) measured by flow cytometry. This is a limited assessment of differentiation. The authors do not report morphological assessment, hemoglobin production (benzidine staining), or expression of additional lineage-specific markers. Furthermore, the distinction between "promoting erythroid" and "inhibiting megakaryocytic" differentiation is based on reciprocal marker changes, but the authors do not demonstrate that this represents a true lineage switch versus independent effects on each marker.
- **Why it matters** The central biological claim of the paper rests on the differentiation phenotype. If the effects are limited to surface marker changes without functional or morphological correlates, the conclusion that SNHG6 regulates hematopoietic differentiation is not fully supported.
- **Resolution test** Include additional differentiation markers, morphological analysis, and functional assays (e.g., hemoglobin production, platelet-like particle formation). Consider single-cell RNA-seq or colony-forming assays to demonstrate lineage commitment changes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The claim that SNHG6 acts in trans based on "widespread" genomic changes and cytoplasmic localization
- **Evidence pointer** Results section "SNHG6 regulates hematopoiesis in K562 cells", Figure 4b, Supplementary Figure S11
- **Concern** The trans regulatory claim is inferred from two observations: (1) DEGs are spread across the genome, and (2) SNHG6 is cytoplasmic. However, the authors do not perform RNA immunoprecipitation, chromatin isolation by RNA purification, or other assays to directly test SNHG6 interactions with chromatin, proteins, or other RNAs. The cytoplasmic localization is consistent with trans regulation but does not exclude cis effects on neighboring genes or indirect effects through the host snoRNA.
- **Why it matters** The mechanistic model proposed in Figure 5g depends on understanding how SNHG6 functions. Without direct evidence of SNHG6 molecular interactions, the mechanism remains speculative.
- **Resolution test** Perform RNA pulldown or RIP-seq to identify SNHG6-interacting partners. Alternatively, demonstrate that SNHG6 overexpression in trans rescues the KD phenotype in a manner independent of genomic location.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The claim that SNHG6 KD "attenuated tumor growth in vivo"
- **Evidence pointer** Results section "SNHG6 regulates hematopoietic differentiation in K562 cells", Figure 5d-f
- **Concern** The xenograft experiment uses a single cell line (K562) with n ≥ 11 per group from two independent experiments. While the tumor volume and weight differences are reported as significant, the authors do not provide details on randomization, blinding, or whether the two experiments were pooled appropriately. Additionally, K562 is an established cell line that may not fully recapitulate patient-derived leukemia biology.
- **Why it matters** In vivo efficacy is a key translational claim. Without proper experimental design details and ideally validation in additional models (e.g., patient-derived xenografts or a second cell line), the generalizability of the in vivo finding is uncertain.
- **Resolution test** Provide details on randomization and blinding. Consider validating in an additional leukemia model or using a more clinically relevant system.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, "Developing the ML algorithm"
- **Evidence pointer** Methods section, "ENCODE TF ChIP-seq"
- **Issue** The description of TF ChIP-seq data processing is brief. It is unclear how peak height was normalized across different TF experiments and cell lines, and how the 10% intersection cutoff was applied.
- **Required correction** Provide additional detail on data normalization and the rationale for the 10% cutoff.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Cell culture" and "Stable knockdown"
- **Evidence pointer** Methods section
- **Issue** The methods for cell culture and lentiviral transduction are described, but the specific details of the differentiation assays (concentrations, timing, media) are not fully provided in the main text.
- **Required correction** Include complete protocols for differentiation assays in the methods or supplementary materials.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, "Validation of INFLAMeR's predictions"
- **Evidence pointer** Figure 2b-d
- **Issue** The authors report that 74% of predicted lncRNAs affected proliferation and 44% affected drug response, with 85% affecting at least one. However, the overlap between proliferation and drug response phenotypes is not fully explored. It would be informative to know whether these represent independent functional classes.
- **Required correction** Provide a more detailed analysis of the relationship between proliferation and drug response phenotypes.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of SNHG6's mechanism is largely speculative and does not fully integrate the authors' own transcriptomic data with the known biology of SNHG6 in other cancer types.
- **Required correction** Strengthen the discussion by comparing the authors' findings with previous SNHG6 studies and proposing more specific, testable mechanistic hypotheses.

- **Technical failings that need to be addressed before the case is established** R1-M1 (external validation and performance metrics), R1-M2 (differentiation assay rigor), R1-M3 (direct evidence for trans mechanism), R1-M4 (in vivo experimental details)

- **Assessment against Nature-style criteria**
  - **Originality** The INFLAMeR approach is a novel integration of TF binding and genomic features for lncRNA prioritization, though it builds on existing machine learning methods for functional element prediction. The SNHG6 findings add to a growing literature on this lncRNA in cancer.
  - **Scientific importance** The work addresses the important problem of predicting functional lncRNAs, and the high validation rate suggests practical utility. The SNHG6 findings are potentially relevant to leukemia biology, but the mechanistic depth is currently insufficient for broad significance.
  - **Interdisciplinary readership** The computational approach and experimental validation span bioinformatics, molecular biology, and cancer biology, which could appeal to a broad audience. However, the technical detail may limit accessibility for non-specialists.
  - **Technical soundness** The computational methods are generally sound, but the lack of external validation and limited performance metrics are concerns. The experimental validation is thorough in scope but the differentiation assays lack depth.
  - **Readability for nonspecialists** The manuscript is clearly written and the figures are well-described, but the methods section is dense. The logical flow from computational prediction to experimental validation is easy to follow.

- **Recommendation posture** Supportive if technical concerns are resolved. The computational framework is promising and the validation rate is notable, but the mechanistic characterization of SNHG6 and the robustness of the model evaluation need strengthening. The authors should address the concerns regarding external validation, differentiation assay rigor, and direct evidence for the proposed mechanism before the case is fully established.

## Risk / unsupported claims
- The claim that INFLAMeR can be "readily applied to identify novel targets for precision medicine" is not directly supported by the data, as no clinical or therapeutic applications are demonstrated.
- The statement that SNHG6 "strongly promotes megakaryocyte differentiation" is not fully supported by the data, which show reduced CD41/CD61 levels after KD but do not demonstrate a direct promotion of this lineage.
- The claim that the model "predicted functional lncRNAs that were previously overlooked" is difficult to evaluate without a systematic comparison to existing prediction methods.
- The assertion that SNHG6's role in hematopoiesis is "consistent with its predicted role" is circular, as the prediction was based on features that may not be mechanistically linked to differentiation.
- The clinical relevance of SNHG6 in AML, suggested by the survival analysis, is based on a single dataset and requires validation in independent cohorts.