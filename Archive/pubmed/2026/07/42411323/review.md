## Review setup
- **Input scope** Full manuscript text (abstract, main text, materials and methods, case examples, validation, conclusion, outlook)
- **Assessment boundary** Scientific and technical evaluation of the described update to the FABIAN-variant tool, based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors present FABIAN-variant 2026, a major update to their existing web application for predicting the effects of DNA variants on transcription factor binding. The update expands the model library from ~5000 to over 40,000 models for human TFs, adds mouse genome support, introduces an optional deep learning (BPNet) scorer, expands known TF binding site sources, adds heterodimer TF complex predictions, and rewrites the backend with improved performance and programmatic access.
- **Visible evidence base** Abstract, main text sections (expanded model library, mouse support, deep learning, TFBS sources, heterodimers, technical improvements, comparison with related tools), materials and methods (model database, PWM/TFFM scoring, BPNet scoring, combined score against SNP-SELEX, BPNet against SNP-SELEX, combined score versus BPNet, runtime comparison), case examples, validation against SNP-SELEX, conclusion, outlook
- **Missing materials affecting confidence** Figures (Fig. 1, Fig. 2, Fig. 3) and tables (Table 1, Table 2, Table 3) are referenced but not provided. The full mathematical formulation of the per-model score S is not shown (equation appears truncated). Details of the SNP-SELEX benchmark methodology and the specific case example results are not fully described. No information is provided on statistical significance testing for the reported performance metrics.

## Reviewer
- **Overall assessment** This manuscript describes a substantial technical update to an existing and already-used bioinformatics tool. The expansion of the model library, addition of mouse support, and inclusion of a deep learning-based scorer are meaningful improvements that address clear limitations of the previous version. The validation against SNP-SELEX data is a reasonable approach, and the reported directional agreement rates are encouraging. However, the manuscript as presented has several significant gaps. The most critical issue is the lack of a rigorous, quantitative comparison against existing tools. The authors mention other tools (PERFECTOS-APE, motifbreakR, RSAT, atSNP, SNP2TFBS, sTRAP, DeepSEA, deltaSVM, ChromBPNet, AlphaGenome, Evo 2, GPN-Star) but provide no head-to-head benchmarking. The claim that FABIAN-variant 2026 is "the only tool" combining multiple features is strong and requires more careful substantiation. Additionally, the validation is limited to directional agreement on a subset of SNP-SELEX data; there is no assessment of calibration, precision-recall, or comparison with alternative scoring approaches on the same benchmark. The case examples are illustrative but not systematic. The technical details of the BPNet integration, particularly how the 2114 bp sequence is handled and how predictions are normalized across cell types, are insufficiently described. The runtime improvement claim is based on a limited benchmark with no statistical analysis. Overall, the update is likely useful to the community, but the manuscript needs substantial revision to establish the scientific case for improved prediction performance.

- **Who would be interested in the results, and why** Researchers and clinicians working on noncoding variant interpretation, particularly those studying regulatory regions, promoters, and enhancers. This includes human geneticists interpreting whole-genome or whole-exome sequencing data, functional genomicists studying TF binding, and clinical diagnostic laboratories. The tool's free availability, web interface, API, and standalone version make it accessible to a broad user base. The mouse genome support will be of particular interest to the mouse genetics community.

- **Major strengths** The update addresses clear limitations of the previous version, particularly the limited model library and human-only support. The inclusion of multiple PWM databases and TFFMs from original sources is a methodological improvement over aggregated collections. The optional BPNet deep learning scorer represents a meaningful addition that can capture binding effects beyond simple motifs. The rewritten backend with reduced runtime and the provision of API and standalone versions are practical improvements that will facilitate broader use. The validation against SNP-SELEX data, while limited, provides some evidence of predictive utility.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance / technical soundness
- **Claim pointer** The manuscript claims that FABIAN-variant 2026 provides "improved prediction" of DNA variant effects on TF binding, and that it is "the only tool" combining PWM, TFFM, and deep learning-derived models with the described feature set.
- **Evidence pointer** Abstract; Comparison with related tools section; Validation against SNP-SELEX section
- **Concern** The central claim of "improved prediction" is not substantiated by a rigorous, quantitative comparison against existing tools. The validation against SNP-SELEX shows directional agreement rates but does not compare FABIAN-variant's performance with that of other available tools (e.g., motifbreakR, atSNP, DeepSEA, deltaSVM) on the same benchmark. The claim of being "the only tool" with the described combination of features is a strong assertion that requires a systematic survey of the field, which is not provided.
- **Why it matters** The scientific contribution of this manuscript rests on demonstrating that the update provides tangible improvements over existing approaches. Without a head-to-head comparison, the reader cannot assess whether the expanded model library, BPNet integration, or other features translate into better prediction accuracy. The "only tool" claim, if inaccurate, would mislead users.
- **Resolution test** Provide a systematic benchmark comparing FABIAN-variant 2026 with at least 2-3 representative existing tools (e.g., motifbreakR, atSNP, DeepSEA) on the SNP-SELEX dataset or another appropriate benchmark, reporting standard metrics such as AUROC, AUPRC, and calibration. Alternatively, provide a comprehensive literature survey to substantiate the "only tool" claim.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that the BPNet deep learning scorer provides "neural network-based binding predictions for 240 human TFs" and that it is integrated into the scoring pipeline.
- **Evidence pointer** Deep learning predictions section; Materials and methods, BPNet deep learning scoring section
- **Concern** The technical details of the BPNet integration are insufficiently described. The manuscript states that a 2114 bp sequence is used and that log2 fold change and Jensen-Shannon distance are computed, but it does not explain how the BPNet models are loaded, how predictions are normalized across different cell types, how the models are applied to indels (which change sequence length), or how the per-cell-type predictions are meant to be interpreted by users. The relationship between the BPNet-derived metrics and the existing PWM/TFFM-based combined score is unclear.
- **Why it matters** Reproducibility and proper interpretation of the deep learning predictions require a clear description of the methodology. Users need to understand what the BPNet scores mean, how they should be combined with or compared to the motif-based scores, and what the limitations of the deep learning approach are.
- **Resolution test** Provide a detailed description of the BPNet integration, including model architecture, input preprocessing, handling of indels, normalization procedures, and guidance on interpretation of the output metrics. Clarify how the BPNet scores relate to the combined PWM/TFFM score.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The manuscript states that the prediction model library has been expanded to "40,315 models for 1530 human TFs and 35,990 models for 1123 mouse TFs" and that models are sourced from "nine PWM databases."
- **Evidence pointer** Expanded prediction model library section; Table 1 (not provided)
- **Concern** The manuscript does not provide a breakdown of how many models come from each database, how redundancy between databases is handled, or how model quality is assessed. The previous version used MotifDb as an aggregated collection; the new version retrieves from original sources, but the implications of this change for prediction performance are not discussed. The potential for conflicting predictions from different models for the same TF is not addressed.
- **Why it matters** Users need to understand the composition and potential biases of the model library. The presence of redundant or conflicting models could affect the reliability of predictions. The manuscript should clarify how the diversity of models is managed and whether any quality filtering is applied.
- **Resolution test** Provide a supplementary table detailing the number of models per database, the overlap between databases, and any quality control measures applied. Discuss how predictions from multiple models for the same TF are aggregated or presented to users.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims a "~70%" runtime reduction compared to the 2022 version.
- **Evidence pointer** Technical improvements section; Table 2 (not provided)
- **Concern** The runtime comparison is based on only three representative workloads with three runs each. No statistical analysis is provided, and the specific hardware and software environment are not described. The comparison is made against the 2022 version with a restricted model set, which may not be representative of typical usage.
- **Why it matters** The runtime improvement is a claimed advantage of the update. Without a more rigorous benchmark, the reader cannot assess the reliability of this claim.
- **Resolution test** Provide a more detailed benchmark with additional workloads, more runs, and a description of the test environment. Report mean and standard deviation of runtimes and perform a statistical test (e.g., t-test or Wilcoxon test) to support the claim.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that "Predictions for over 1400 heterodimer TF complexes have been added" and that these are displayed in three modes.
- **Evidence pointer** Heterodimer TF complexes section
- **Concern** The source of the heterodimer models is not clearly described. The manuscript mentions contributions from JASPAR 2026, CAP-SELEX studies, HOMER, and UniPROBE, but the total number of models (1420 human, 1355 mouse) does not match the sum of the listed contributions (628+1959+3+2 = 2592 for human). This discrepancy needs clarification. Additionally, the methodology for scoring heterodimer complexes, particularly how the two component TFs are handled, is not described.
- **Why it matters** The heterodimer predictions are a new feature, and users need to understand their basis and limitations. The numerical discrepancy raises questions about the accuracy of the reported counts.
- **Resolution test** Clarify the source and counting of heterodimer models. Provide a detailed description of how heterodimer scoring is performed and how it differs from monomer scoring.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is dense and lists many technical details (e.g., "40,315 models for 1530 human TFs") without providing context for why these numbers matter. The abstract could better highlight the practical benefits for users.
- **Required correction** Consider restructuring the abstract to emphasize the key user-facing improvements (e.g., broader coverage, mouse support, faster results) before presenting the technical details.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Materials and methods, PWM and TFFM scoring
- **Evidence pointer** Materials and methods, PWM and TFFM scoring section
- **Issue** The equation for the per-model score S is not fully shown in the provided text. The description of the scoring function is incomplete.
- **Required correction** Provide the complete equation and a clear explanation of all variables and parameters.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Validation against SNP-SELEX
- **Evidence pointer** Validation against SNP-SELEX section
- **Issue** The manuscript reports directional agreement rates but does not provide confidence intervals for the BPNet results or a statistical comparison between the combined score and BPNet performance.
- **Required correction** Add confidence intervals for all reported agreement rates and perform a statistical test to compare the performance of the combined score and BPNet.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Case examples
- **Evidence pointer** Case examples section
- **Issue** The case examples are described in a single paragraph without a table or figure summarizing the results. This makes it difficult for readers to quickly grasp the outcomes.
- **Required correction** Consider presenting the case examples in a table format with columns for variant, gene, TF, predicted effect, and experimental result.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Materials and methods, Model database
- **Evidence pointer** Materials and methods, Model database section
- **Issue** The description of how TF names are mapped to canonical gene symbols and how species assignment is performed is brief. The potential for mapping errors or ambiguous assignments is not discussed.
- **Required correction** Provide more detail on the mapping procedure and any manual curation steps. Discuss potential sources of error and how they are mitigated.

## Risk / unsupported claims
- The claim that FABIAN-variant 2026 provides "improved prediction" is not supported by a quantitative comparison with existing tools.
- The claim that FABIAN-variant 2026 is "the only tool" combining the described features is not substantiated by a systematic survey.
- The reported runtime reduction of ~70% is based on a limited benchmark without statistical analysis.
- The numerical discrepancy in heterodimer model counts (1420 vs. the sum of listed sources) is unexplained.
- The performance of the BPNet scorer is reported only in terms of directional agreement; no other metrics (e.g., AUROC, AUPRC) are provided for the BPNet results.
- The case examples are illustrative and do not constitute a systematic validation.
- The manuscript does not address potential limitations of the approach, such as the inability of PWM/TFFM models to capture cooperative binding or chromatin context, beyond the addition of BPNet.