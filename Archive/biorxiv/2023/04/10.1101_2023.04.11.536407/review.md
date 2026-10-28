## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text; no external data or supplementary materials were available for verification
- **Shared manuscript claim summary** The authors present a systematic screen of domain insertion tolerance across four unrelated effector proteins, use machine learning to identify sequence conservation statistics as key predictors of insertion permissibility, and demonstrate the discovery of light-switchable AraC variants functioning as Boolean logic gates
- **Visible evidence base** Abstract, Introduction, Results sections (descriptive), Discussion, Methods; figure and table references are cited but their actual content was not provided
- **Missing materials affecting confidence** All figures, extended data figures, supplementary figures, supplementary tables, and supplementary notes; raw sequencing data; detailed machine learning performance metrics beyond those stated; structural models and alignments

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question in protein engineering: what determines whether a protein domain can tolerate insertion of another domain at a given position, and can such insertions generate allosteric switches. The authors present a comprehensive experimental pipeline combining saturated insertion libraries, FACS-based functional screening, and machine learning to dissect determinants of insertion tolerance. The finding that sequence conservation statistics, rather than simple structural features, are the strongest predictors of insertion permissibility is potentially valuable for the field. The demonstration of light-switchable AraC variants functioning as Boolean logic gates is a compelling proof-of-principle. However, the manuscript as provided lacks the actual data presentation (figures, quantitative results), making it impossible to fully evaluate the strength of the claims. The machine learning approach, while reasonable, requires more rigorous validation and comparison to existing methods. The mechanistic interpretation of why conservation statistics predict insertion tolerance is underdeveloped. Overall, the work is promising and of interest to the protein engineering and synthetic biology communities, but the current evidence base is insufficient to fully establish the central claims.

- **Who would be interested in the results, and why** Protein engineers and synthetic biologists interested in domain insertion strategies, allosteric switch design, and optogenetics would find this work directly relevant. The machine learning approach for predicting insertion-tolerant sites could be broadly applicable to protein design efforts. The AraC-based Boolean logic gates have potential applications in biocomputing and gene circuit design. Additionally, researchers studying protein evolution and the constraints on domain recombination would be interested in the finding that conservation statistics are predictive of insertion tolerance.

- **Major strengths** The systematic and unbiased approach to assessing insertion tolerance across multiple unrelated proteins is a significant methodological advance. The use of functional readouts rather than expression or localization is appropriate for identifying sites that preserve protein function. The machine learning framework, particularly the feature reduction to six key predictors, provides a practical tool for future engineering efforts. The identification of light-switchable AraC variants with Boolean logic functionality demonstrates the practical utility of the screening pipeline. The comparison of multiple insert domains of varying size and structure adds generality to the findings.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim that "sequence conservation statistics as the strongest indicators of suitable insertion sites" and that the reduced model with six features performs as well as the full model.
  - **Evidence pointer** Results section "Machine learning reveals statistical features predicting domain insertion tolerance"; Figure 3; Extended Data Figure 5; Supplementary Figures 11 and 12
  - **Concern** The manuscript text describes the machine learning results but the actual performance metrics, feature importance values, and model comparison data are not visible in the provided material. The claim that the reduced model performs "as good as the original one" requires quantitative comparison (e.g., confidence intervals, statistical significance testing). Additionally, the generalizability of the model to proteins beyond the four tested is not demonstrated. The authors should provide external validation on held-out proteins or at least discuss the limitations of training on a small set of structurally and functionally diverse proteins.
  - **Why it matters** The central claim of the paper rests on the predictive power of the machine learning model. Without visible performance data and validation, the reader cannot assess whether the model is genuinely useful for predicting insertion tolerance in new proteins. Overclaiming model performance could mislead the field.
  - **Resolution test** Provide the actual AUROC/AP values with confidence intervals for all models, show feature importance plots, and include a validation experiment on at least one or two additional proteins not used in training. Alternatively, provide a clear discussion of why the current validation is sufficient.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Mechanistic interpretation
  - **Claim pointer** The authors state that "KLD, insertion frequency and deletion frequency, i.e. evolutionary and statistical features derived from MSAs, were detected as most important parameters explaining domain insertion tolerance."
  - **Evidence pointer** Results section "Machine learning reveals statistical features predicting domain insertion tolerance"; Figure 3d; Supplementary Figure 12
  - **Concern** The manuscript does not provide a mechanistic explanation for why conservation statistics should predict insertion tolerance. The authors draw parallels to statistical coupling analysis but do not develop this connection. Why would evolutionarily conserved positions be more or less tolerant to domain insertion? The authors should discuss potential structural or functional reasons, such as conserved positions being in regions critical for folding or function, or conversely, variable regions being more adaptable. Without a mechanistic hypothesis, the finding remains descriptive.
  - **Why it matters** A purely correlative finding, even with strong predictive power, is less useful for guiding engineering efforts than one with a mechanistic basis. Understanding why certain positions tolerate insertion would allow researchers to make rational choices beyond what the model predicts.
  - **Resolution test** Add a discussion section that proposes and tests a mechanistic hypothesis, or at least clearly articulates possible explanations and how they could be distinguished experimentally.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Experimental validation depth
  - **Claim pointer** The authors claim that "extending our experimental pipeline towards the identification of switchable hybrids resulted in opto-chemogenetic derivatives of the transcription factor AraC that function as single-protein Boolean logic gates."
  - **Evidence pointer** Results section "Identification of potent light-switchable AraC variants"; Figure 4; Extended Data Figures 6-8
  - **Concern** While the identification of light-switchable AraC variants is exciting, the characterization appears limited to two variants (I113 and S170). The manuscript does not describe the dynamic range, response kinetics, or reversibility of the switches in detail beyond what is mentioned. The claim of Boolean logic gate functionality is based on the co-dependence on light and arabinose, but the full truth table and the robustness of the logic operations are not presented in the visible text. Additionally, the point mutation analysis is mentioned but the results are not described in the text.
  - **Why it matters** The practical utility of the identified switches depends on their performance characteristics. If the switches are slow, leaky, or have limited dynamic range, their utility for applications is diminished. The Boolean logic claim requires demonstration of all four input combinations and clear separation between ON and OFF states.
  - **Resolution test** Provide detailed characterization data for the switches, including dose-response curves, kinetics, reversibility, and the full logic truth table. Describe the point mutation results and their implications for understanding the allosteric mechanism.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Comparison to existing methods
  - **Claim pointer** The authors state that "our data showcases the absence of any simplistic explanations for domain insertion permissibility" and that their machine learning approach outperforms individual features.
  - **Evidence pointer** Results section "Domain insertion permissibility is sequentially and structurally clustered"; Figure 2; Figure 3c
  - **Concern** The manuscript does not compare the machine learning approach to existing computational tools for predicting domain insertion sites or protein permissiveness to mutation. Several tools exist for predicting protein stability upon mutation, and some studies have used machine learning for similar purposes. The authors should benchmark their model against existing approaches to demonstrate added value.
  - **Why it matters** If existing tools perform comparably, the novelty of the approach is diminished. Demonstrating superiority or complementarity to existing methods strengthens the case for the utility of the presented pipeline.
  - **Resolution test** Include a comparison to at least one or two existing prediction tools or baseline methods on the same datasets, and discuss the relative performance.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of methods
  - **Affected element** Machine learning feature description
  - **Evidence pointer** Methods section "Gradient boosting models"
  - **Issue** The description of features is incomplete. The authors mention "biophysical properties and linker propensity indices fetched from the AAindex database" but do not specify which properties or how many features were used. The feature engineering process is not fully described.
  - **Required correction** Provide a complete list of features used, including the specific AAindex properties, and describe how they were calculated and normalized.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Correlation analysis
  - **Evidence pointer** Results section "Domain insertion permissibility is sequentially and structurally clustered"; Figure 2g
  - **Issue** The authors state that correlations between enrichment scores and individual features were "overall weak trends, with the majority of the correlation coefficients lying in the range between −0.2 and 0.2." No statistical significance testing is mentioned, and the specific correlation values are not provided.
  - **Required correction** Report the actual correlation coefficients with p-values or confidence intervals, and specify which features showed statistically significant correlations, even if weak.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Data availability
  - **Evidence pointer** Data availability section
  - **Issue** The Addgene IDs for the plasmids are listed as "xxxx", which is not useful for readers who wish to obtain the materials.
  - **Required correction** Provide the actual Addgene IDs or state that the plasmids will be deposited upon publication.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretation of structural data
  - **Affected element** Structural analysis
  - **Evidence pointer** Results section "Domain insertion permissibility is sequentially and structurally clustered"; Figure 2; Extended Data Figures 3 and 4
  - **Issue** The manuscript states that "no clear enrichment at surface-exposed unstructured loops could be identified for any of the candidates," which contradicts common assumptions. However, the structural analysis is not described in detail, and the criteria for classifying surface-exposed loops are not provided.
  - **Required correction** Describe the structural analysis methodology, including how surface exposure and secondary structure were defined, and how the mapping of enrichment scores onto structures was performed.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Discussion of limitations
  - **Affected element** Discussion section
  - **Evidence pointer** Discussion section
  - **Issue** The discussion does not address potential limitations of the study, such as the limited number of effector proteins tested, the use of E. coli as the sole expression host, or the potential bias introduced by the choice of insert domains.
  - **Required correction** Add a paragraph discussing the limitations of the study and how they might affect the generalizability of the findings.

## Risk / unsupported claims
- The claim that "sequence conservation statistics as the strongest indicators of suitable insertion sites" is not fully supported by visible data; the actual feature importance values and model performance metrics are not provided in the text.
- The claim that the reduced model with six features performs "as good as the original one" is unsupported without quantitative comparison data.
- The claim that "most parameters were dispensable" for model performance is not supported by visible feature importance analysis.
- The claim that the identified AraC variants function as Boolean logic gates is not fully supported without the complete truth table and characterization data.
- The claim that "no clear enrichment at surface-exposed unstructured loops could be identified" is not supported by visible structural analysis data.
- The generalizability of the machine learning model to proteins beyond the four tested is not demonstrated and cannot be assessed from the provided material.
- The mechanistic interpretation linking conservation statistics to insertion tolerance is speculative and not supported by experimental evidence in the visible text.