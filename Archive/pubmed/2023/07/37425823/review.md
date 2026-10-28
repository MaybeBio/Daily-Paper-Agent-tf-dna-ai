## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Results, Discussion, Methods) as provided
- **Assessment boundary** Scientific content, methodology, evidence quality, and claims as presented in the provided text; no external data or supplementary materials were available for verification
- **Shared manuscript claim summary** The authors present Puffin, a deep learning-inspired explainable model that predicts transcription initiation at basepair resolution from DNA sequence. They claim that a small set of simple sequence rules (10 motifs, 10 initiators, trinucleotides) can explain the majority of human promoter activity, that position-specific effect curves for these motifs are novel and validated by experimental perturbations and evolutionary conservation, and that these rules are conserved across mammalian species.
- **Visible evidence base** Main text figures referenced (Fig. 1–6), supplementary figures and tables referenced (Fig. S1–S20, Tables S1–S4, Data S1–S3), methods descriptions
- **Missing materials affecting confidence** Supplementary figures, tables, and data files; detailed model architecture and training hyperparameters; specific statistical test results and effect sizes; experimental data processing details for NFYA knockdown, YY1 AID depletion, and STAP-seq datasets; code availability statement

## Reviewer
- **Overall assessment** This manuscript addresses a fundamental question in gene regulation: how DNA sequence determines transcription initiation. The authors develop a novel interpretable modeling approach that achieves high predictive accuracy while providing mechanistic insight through position-specific effect curves. The work is ambitious, technically sophisticated, and the validation strategy combining experimental perturbation data with evolutionary conservation is commendable. However, several technical aspects require clarification and additional evidence to fully support the claims, particularly regarding model interpretability, statistical rigor of validations, and the generalizability of the proposed rules.
- **Who would be interested in the results, and why** Researchers in transcriptional regulation, computational genomics, and machine learning for biology. The work provides a unified framework for understanding promoter sequence-function relationships, with practical implications for promoter engineering and interpretation of disease-associated variants. The interpretable modeling approach may also interest method developers seeking to move beyond black-box deep learning models.
- **Major strengths** 1) Addresses a long-standing problem with a novel approach that balances predictive power and interpretability. 2) The position-specific effect curves provide mechanistic hypotheses that are testable and validated with independent experimental data. 3) The multi-faceted validation strategy (experimental perturbations, cross-species conservation, cross-technique consistency) is rigorous. 4) The model's simplicity (10 motifs + 10 initiators + trinucleotides) is striking and suggests that complex regulatory phenomena may have tractable sequence determinants. 5) The web server resource increases accessibility and utility for the broader community.
- **Major Concerns** 
- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Puffin achieves higher basepair-level correlation with experimental measurement than the most correlated pair of experimental techniques, when evaluated on test chromosomes"
- **Evidence pointer** Fig. 1C–D, Fig. S3
- **Concern** The claim that Puffin outperforms experimental reproducibility is central to establishing the model's utility. However, the comparison methodology is not fully described. Specifically, it is unclear how the "most correlated pair of experimental techniques" was determined, whether this comparison was performed on the same set of TSS, and what statistical test was used to establish significance of the difference. The correlation values themselves are not reported in the text.
- **Why it matters** This claim positions Puffin as effectively capturing the "true" regulatory code at a level beyond experimental noise. If this is not rigorously established, the subsequent interpretability claims are weakened. The comparison must be apples-to-apples and statistically sound.
- **Resolution test** Provide the correlation values for Puffin and for each pair of experimental techniques, describe the exact TSS set used for comparison, and report a statistical test (e.g., bootstrap or permutation test) demonstrating that Puffin's correlation is significantly higher.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "All ten motifs included in the Puffin model are robustly discovered with >0.95 correlation across training replicates"
- **Evidence pointer** Fig. 2D–E, Supplementary Data 2
- **Concern** The criterion for "robustly discovered" is based on correlation of effect curves across training replicates. However, it is unclear whether this correlation is computed on the full effect curve or on the motif position weight matrix. More importantly, the threshold of 0.95 seems arbitrary, and the number of replicates (12) may not be sufficient to establish stability, especially for motifs with weaker effects. The authors should also report how many of the 40 initial motifs were discarded and whether the final 10 were selected based on reproducibility alone or also on functional criteria.
- **Why it matters** The reproducibility of motif discovery is foundational to all subsequent analyses. If the motif set is not stable, the contribution scores and downstream conclusions are unreliable. The selection process must be transparent to allow assessment of potential circularity.
- **Resolution test** Clarify the exact metric used for reproducibility, report the distribution of correlation values across all 40 motifs, justify the 0.95 threshold, and describe the complete selection pipeline from initial motifs to final 10.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "The Puffin prediction not only recapitulated effects on expression level caused by sequence alterations (TSS-level correlation 0.88, Fig. S13A), but also displayed close to 0.9 basepair-level correlation with experimental data for TSS with strong expression"
- **Evidence pointer** Fig. 3E, Fig. S13A–B
- **Concern** The validation using STAP-seq data is compelling, but the analysis appears to be limited to a small number of examples (one LTR12 promoter and one neutral insertion site are shown). The reported correlations of 0.88 and ~0.9 are based on how many independent sequence perturbations? If only a handful of constructs were tested, the correlations may not be robust. Additionally, the selection of "TSS with strong expression" for basepair-level comparison introduces potential selection bias.
- **Why it matters** The experimental validation is the strongest evidence for the model's predictive power. If the sample size is small or the analysis is selective, the generalizability of the model's predictions is not established.
- **Resolution test** Report the total number of sequence perturbations analyzed, the number of TSS with strong expression used for basepair-level comparison, and provide a scatter plot or table showing all data points, not just representative examples.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "We revealed the sequence basis of bidirectional transcription at promoters and links between promoter selectivity and gene expression variation across cell types."
- **Evidence pointer** Fig. 4, Fig. 5
- **Concern** The link between motif composition and cell-type specificity is based on correlative analysis across cell types. The proposed mechanism that "motif composition determines the response curve of a promoter to external transcriptional activation signals" is a hypothesis that is not directly tested. The in silico insertion screen provides indirect evidence, but the connection to endogenous regulatory mechanisms remains speculative.
- **Why it matters** The claim of revealing the "sequence basis" of bidirectional transcription and cell-type specificity is strong. If the evidence is primarily correlative, the conclusions should be tempered. Direct experimental manipulation of motif composition in a controlled context would substantially strengthen the causal claims.
- **Resolution test** Provide additional evidence, such as CRISPR-based perturbation of specific motifs in a reporter assay, or clearly reframe the claims as correlative and hypothesis-generating rather than causal.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "We showed that the sequence determinants are conserved across mammalian species."
- **Evidence pointer** Fig. 6
- **Concern** The cross-species analysis uses PhyloP conservation scores and comparisons between human and mouse models. However, the analysis of 241 mammalian genomes appears to be based on conservation of motif sequences rather than conservation of the position-specific effect curves. The claim of conservation of "sequence determinants" is ambiguous. If only motif presence is conserved, this does not demonstrate that the regulatory logic (position-specific effects) is conserved.
- **Why it matters** The claim of conservation across mammals is a key part of the paper's significance. If the analysis only shows sequence conservation of motifs, this is a weaker claim than conservation of the regulatory model. The distinction matters for understanding whether the model captures universal regulatory principles.
- **Resolution test** Clarify whether the position-specific effect curves are compared across species, or only motif sequence conservation. If only sequence conservation, temper the claim accordingly.

- **Minor Comments** 
- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "simple rules can explain the vast majority of human promoters" but does not quantify "vast majority." A specific percentage or metric would strengthen the claim.
- **Required correction** Provide a quantitative measure of the fraction of promoters explained by the model.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section
- **Issue** The description of the Puffin model architecture is incomplete. The number of parameters, training epochs, learning rate, and other hyperparameters are not specified. The three-stage training procedure is described but the criteria for moving between stages are vague.
- **Required correction** Provide a complete description of the model architecture and training details, or reference a separate methods paper or code repository.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Fig. 4
- **Evidence pointer** Fig. 4H–J
- **Issue** The correlation between motif contribution and selectivity is reported, but confidence intervals or p-values are not provided in the text.
- **Required correction** Report statistical significance for the correlations shown in Fig. 4H–J.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section
- **Evidence pointer** "Bidirectional transcription initiation" section
- **Issue** The definition of "bidirectional TSS pairs" and the criteria for selecting the 8,216 TSS for analysis are not fully described.
- **Required correction** Clarify the selection criteria and provide the exact thresholds used.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section
- **Issue** The web server is mentioned but no URL is provided in the text (only in the abstract).
- **Required correction** Include the URL in the main text or a data availability statement.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The statement "we expect that sequence dependencies of transcription initiation captured by Puffin will be widely applicable across mammalian species" is speculative and not directly supported by the data presented.
- **Required correction** Either provide additional evidence for this claim or soften the language to reflect it as a prediction.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods
- **Evidence pointer** Methods section
- **Issue** The description of the "pseudo-Poisson loss" is unclear. The formula is not provided, and the relationship to a standard Poisson loss is not explained.
- **Required correction** Provide the exact loss function formula and explain why this loss was chosen.

## Risk / unsupported claims
- The claim that Puffin outperforms experimental reproducibility (R1-M1) is not fully supported without detailed comparison methodology and statistics.
- The claim of "conservation across 241 mammalian species" (R1-M5) is ambiguous; if only motif sequence conservation is shown, this does not support conservation of the regulatory model.
- The proposed mechanism linking motif composition to cell-type specificity (R1-M4) is correlative and not causally tested.
- The statement in the Discussion that the model "will be widely applicable across mammalian species" is a prediction, not a demonstrated result.
- The claim that "simple rules can explain the vast majority of human promoters" is not quantified in the abstract.
- The novelty of "position-specific effect curves" is asserted but not compared to previous attempts at characterizing motif positional preferences in a systematic way.

## Assessment against Nature-style criteria
- **Originality** High. The interpretable modeling approach and the systematic characterization of position-specific effect curves represent a novel contribution. The integration of multiple validation strategies is also original.
- **Scientific importance** High. Understanding the sequence basis of transcription initiation is a fundamental question with broad implications. The potential for promoter engineering and variant interpretation adds practical significance.
- **Interdisciplinary readership** Moderate to high. The work bridges computational biology, genomics, and molecular biology. The interpretable model may appeal to a broader audience, but the technical depth may limit accessibility.
- **Technical soundness** Moderate. The core modeling approach appears sound, but several technical details require clarification (R1-M1, R1-M2, R1-M3). The validation strategy is thoughtful but the statistical rigor needs strengthening.
- **Readability for nonspecialists** Moderate. The abstract and introduction are accessible, but the methods and results sections assume significant background in deep learning and genomics. The key findings are clearly stated, but the technical details may be challenging for a general audience.

## Recommendation posture
Supportive if technical concerns are resolved. The manuscript addresses an important problem with a novel approach and provides compelling validation. However, the central claims regarding model performance, reproducibility, and conservation require additional evidence and clarification. If the authors can address the major concerns regarding comparison methodology, motif discovery stability, and the scope of experimental validation, this work would be a strong candidate for publication. The current version, as provided, does not fully establish all claims from the visible evidence.