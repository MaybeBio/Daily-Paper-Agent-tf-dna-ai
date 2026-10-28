## Review setup
- **Input scope** Full manuscript text (main text, methods, and supplementary figure/table references as provided)
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and suitability for a high-impact general journal
- **Shared manuscript claim summary** The authors present two deep learning models, CAPSIF2 and PiCAP, for predicting protein–carbohydrate interactions at residue and protein levels, respectively. They introduce a new nonbinder dataset (NoCAP), validate their models against existing tools, and apply them to proteome-scale predictions across multiple species, proposing that a substantial fraction of proteins engage in carbohydrate binding.
- **Visible evidence base** Main text figures (Figs. 1–4), tables (Tables 1–3), methods section, and references to SI Appendix figures and tables
- **Missing materials affecting confidence** SI Appendix figures and tables referenced but not provided; specific training/test split details for some subsets; details on the computational nonbinder dataset construction from Luo et al.; full benchmark comparisons on all test sets

## Reviewer
- **Overall assessment** This manuscript addresses an important gap in glycobiology by attempting proteome-scale prediction of protein–carbohydrate interactions. The development of a nonbinder dataset and two complementary deep learning models is a valuable contribution. However, several concerns regarding dataset construction, model validation, and the interpretation of proteome-scale predictions need to be addressed before the central claims are fully supported. The work is technically sound in its core methodology but requires additional experimental or orthogonal validation to substantiate the broad conclusions about the extent of protein–carbohydrate interplay.
- **Who would be interested in the results, and why** Glycobiologists, computational biologists, and researchers studying protein–ligand interactions would find this work relevant. The proteome-scale predictions could inform experimental prioritization for studying carbohydrate-binding proteins, and the open-source availability of the models would facilitate broader adoption. The approach may also interest those developing deep learning methods for biomolecular interaction prediction.
- **Major strengths** 1) The creation of a large nonbinder dataset (NoCAP) addresses a critical gap in the field, as most existing datasets focus only on positive interactions. 2) The two-model approach (residue-level CAPSIF2 and protein-level PiCAP) provides complementary information. 3) The validation against existing tools and datasets, including agreement with LectomeXplore, strengthens confidence in the predictions. 4) The proteome-scale analysis across multiple species offers a broad perspective on the potential extent of protein–carbohydrate interactions.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** 
  - **Originality** The work is original in its combination of a new nonbinder dataset with two deep learning models for proteome-scale prediction. The concept of predicting carbohydrate binding at a proteome scale is novel, though individual components build on prior work.
  - **Scientific importance** The potential to expand the known protein–carbohydrate interactome substantially is scientifically important, as carbohydrate interactions are understudied relative to protein–protein interactions. However, the importance hinges on the reliability of the predictions, which requires further validation.
  - **Interdisciplinary readership** The work bridges glycobiology, computational biology, and deep learning, and would appeal to researchers in these fields. The proteome-scale findings may also interest cell biologists and systems biologists.
  - **Technical soundness** The core methodology is technically sound, with appropriate use of equivariant graph neural networks and careful dataset curation. However, concerns about dataset contamination, validation on computationally predicted structures, and the interpretation of proteome-scale predictions need to be resolved.
  - **Readability for nonspecialists** The manuscript is generally well-written and accessible, with clear explanations of the methods and significance. The figures are informative, though some details in the methods may be dense for nonspecialists.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding dataset construction, validation on predicted structures, and the interpretation of proteome-scale predictions.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Dataset construction and potential bias
- **Claim pointer** The NoCAP dataset is described as containing proteins that "likely do not bind carbohydrates based on biophysical intuition," and the authors acknowledge potential contamination with unknown carbohydrate-binding proteins.
- **Evidence pointer** Results section "NoCAP: A Nonbinder Dataset"; Table 1
- **Concern** The construction of the nonbinder dataset relies heavily on biophysical intuition and selection of proteins with specific functions or localizations. The authors acknowledge potential contamination, but the extent of this contamination is not quantified. The nonbinder set includes a large proportion of small molecule-binding proteins from PDB-Bind, which may include proteins that also bind carbohydrates or carbohydrate-like moieties. The criteria for selecting "likely nonbinders" are not fully specified, and the potential for systematic bias in the negative set could affect model training and evaluation.
- **Why it matters** If the negative set is contaminated with true carbohydrate binders, the model's performance metrics (e.g., 89.6% BACC) may be underestimated, but more critically, the model may learn to distinguish based on protein function or localization rather than actual carbohydrate-binding propensity. This would undermine the validity of proteome-scale predictions.
- **Resolution test** Provide a detailed description of the criteria used to select nonbinders, including specific biophysical properties considered. Quantify the potential contamination by, for example, running sequence or structural similarity searches against known carbohydrate-binding proteins. Perform sensitivity analyses by training the model on subsets of the nonbinder set with varying confidence levels and reporting performance stability.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation on computationally predicted structures
- **Claim pointer** The authors apply PiCAP to AF2-predicted proteomes and report that 35–40% of proteins in model species are predicted as carbohydrate binders.
- **Evidence pointer** Results section "PiCAP and CAPSIF2 Can Predict Putative Proteome Scale Interactomes"; Figure 4
- **Concern** The model is trained and tested on experimentally determined structures, but applied to AF2-predicted structures. The authors do not assess how prediction accuracy transfers to predicted structures, which may have different geometric properties, especially in low-confidence regions. The authors state they only use regions with pLDDT > 70, but this threshold is not validated for this specific task. The high proportion of predicted binders (35–40%) is striking and may reflect systematic differences between experimental and predicted structures.
- **Why it matters** If the model performs differently on predicted structures, the proteome-scale predictions could be substantially biased. The claim that a large fraction of proteins bind carbohydrates depends critically on the reliability of predictions on AF2 structures.
- **Resolution test** Validate the model on a set of AF2-predicted structures for proteins with known carbohydrate-binding status (e.g., from the test set). Report performance metrics on this subset. Additionally, assess the sensitivity of predictions to pLDDT thresholds and compare predictions on experimental versus predicted structures for the same proteins where both are available.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of proteome-scale predictions
- **Claim pointer** The authors state that "predictions from deep learning propose substantial protein-carbohydrate interplay" and suggest that most extracellular and cell surface proteins bind carbohydrates.
- **Evidence pointer** Discussion section; Figure 4
- **Concern** The proteome-scale predictions are presented as evidence of widespread protein–carbohydrate interactions, but the authors do not provide experimental validation for any of the newly predicted interactions. The agreement with LectomeXplore is noted, but this is a computational comparison. The authors acknowledge that most predicted interactions lack experimental evidence, yet the framing of the results implies a biological conclusion. The claim that 35–40% of all proteins bind carbohydrates is a strong statement that requires more than computational predictions.
- **Why it matters** The central message of the manuscript is that protein–carbohydrate interactions are more widespread than previously appreciated. Without experimental validation, this conclusion is speculative and could mislead the field.
- **Resolution test** Provide experimental validation for a subset of newly predicted interactions, such as binding assays for a few representative proteins. Alternatively, clearly frame the proteome-scale predictions as hypotheses to be tested, and temper the language in the title and abstract accordingly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Benchmarking and comparison with existing methods
- **Claim pointer** The authors state that CAPSIF2 "outcompetes all previous models" on the DR test set, while acknowledging that PesTo-Carbs performs better on the TS-90 test set.
- **Evidence pointer** Results section "CAPSIF2 Outcompetes All Previous Models Identifying Carbohydrate-Binding Residues"; Table 2; Figure 1
- **Concern** The comparison with existing methods is incomplete. The authors compare CAPSIF2 with PesTo-Carbs and their previous CAPSIF models, but do not compare with other available tools for carbohydrate-binding site prediction, such as DeepGlycanSite, which is mentioned in the discussion but not benchmarked. The choice of evaluation metrics and test sets may favor one method over another, and the authors do not provide a comprehensive analysis of performance across different types of carbohydrate-binding proteins.
- **Why it matters** A fair and comprehensive benchmark is essential to support the claim that CAPSIF2 is the best-performing model. Incomplete comparisons could lead to incorrect conclusions about the state of the art.
- **Resolution test** Include comparisons with additional state-of-the-art methods on the same test sets. Provide a more detailed analysis of performance stratified by protein type, carbohydrate type, and binding site characteristics. Discuss potential reasons for performance differences between methods.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of dataset statistics
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** The table lists the number of structures in each dataset category, but the criteria for inclusion in each category are not fully described in the main text. For example, the distinction between "binder" and "nonbinder" within the NoCAP dataset is not clear from the table alone.
- **Required correction** Provide a more detailed description of the dataset composition in the main text or table legend, including how proteins were assigned to each category and the overlap between datasets.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Model interpretability
- **Affected element** Figure 1A and model description
- **Evidence pointer** Figure 1A; Materials and Methods "Architectures"
- **Issue** The manuscript does not provide any analysis of what features the models learn or which structural or sequence properties are most important for predictions. This limits the biological insight that can be gained from the models.
- **Required correction** Include an interpretability analysis, such as attention weights or feature importance, to identify key determinants of carbohydrate binding predictions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical significance
- **Affected element** Figure 3A
- **Evidence pointer** Figure 3A
- **Issue** The authors show a positive relationship between the number of experiments identifying a protein and the fraction predicted as binders, but no statistical test is reported.
- **Required correction** Add a statistical analysis, such as a correlation test or trend test, to support the claim of a significant relationship.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Availability of supplementary data
- **Affected element** SI Appendix
- **Evidence pointer** Multiple references to SI Appendix figures and tables
- **Issue** The SI Appendix is not provided for review, making it impossible to assess the full results, including the analysis for additional species and the detailed GO enrichment results.
- **Required correction** Ensure the SI Appendix is available for review and contains all referenced figures and tables.

## Risk / unsupported claims
- The claim that "35–40% of all proteins in model species bind carbohydrates" is not supported by experimental evidence and relies entirely on computational predictions.
- The statement that "most extracellular and cell surface proteins bind carbohydrates" is an extrapolation from GO enrichment analysis and lacks direct experimental validation.
- The assertion that the nonbinder dataset is "generally representative of proteins that do not bind carbohydrates" is not quantitatively supported, and the potential contamination rate is unknown.
- The claim that CAPSIF2 "outcompetes all previous models" is only supported on the DR test set, not on the TS-90 test set where PesTo-Carbs performs better.
- The agreement with LectomeXplore is presented as validation, but both methods are computational and may share similar biases.