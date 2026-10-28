## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided by the user. No supplementary files, figures, or tables were available for inspection.
- **Assessment boundary** The review is based solely on the manuscript text provided. Claims are assessed for internal consistency, logical coherence, and alignment with the presented evidence. No independent verification of computational results was possible.
- **Shared manuscript claim summary** The authors propose that the Pasteurellaceae Uptake Signal Sequence (USS) receptor is the type IV minor pilin PpdA, previously designated ComN in Haemophilus influenzae. This claim is supported by in silico analyses: functional gene ontology filtering, cellular localization prediction, AlphaFold3 (AF3) protein-DNA complex modeling, DeepPBS DNA-binding specificity prediction, coevolution analyses (Cramér's Φ and mutual information), and molecular dynamics simulations. The authors propose the name ComN for PpdA orthologs in Pasteurellaceae.
- **Visible evidence base** The manuscript text includes descriptions of methods and results, references to supplementary tables (S1–S8), figures (1–12), supplementary figures (S1–S13), and code outputs (S1). Statistical results are described qualitatively (e.g., "strong significance (***)") but no exact p-values, effect sizes, or confidence intervals are reported in the text.
- **Missing materials affecting confidence** Supplementary tables, figures, code outputs, and videos were not provided. Exact statistical values, model confidence scores (ipTM, pLDDT, PAE, CPPM) distributions, and the full list of 73 orthogroups are not accessible. The GitHub repository and Frontiers supplementary material were not consulted. This limits the ability to independently assess the robustness of the reported results.

## Reviewer
- **Overall assessment** The manuscript presents a comprehensive in silico pipeline to identify the USS receptor in Pasteurellaceae, converging on PpdA/ComN as the strongest candidate. The integration of multiple computational approaches is commendable and the authors are appropriately cautious in framing their conclusions as predictions requiring experimental validation. However, the central claim rests entirely on computational predictions, and the manuscript would benefit from clearer presentation of statistical results, explicit handling of potential AF3 biases, and a more critical discussion of the limitations of the methods employed. The proposal to rename PpdA as ComN is reasonable but should be justified more explicitly in the context of existing nomenclature.
- **Who would be interested in the results, and why** Researchers studying natural transformation, bacterial competence, type IV pili biology, and horizontal gene transfer in Pasteurellaceae and related gamma-proteobacteria. The work also has relevance for those interested in applying deep learning tools (AF3, DeepPBS) to protein-DNA interaction prediction, and for the broader community studying the evolution of DNA uptake specificity.
- **Major strengths** The study addresses a long-standing open question in the field. The multi-pronged computational approach is thorough and well-structured. The authors demonstrate awareness of potential pitfalls (e.g., AF3 bias, coevolution confounders) and include negative controls. The evolutionary perspective, linking PpdA to both USS dialects and proposing a divergence scenario, adds conceptual depth. The connection to prior experimental data (comN knockout phenotype) strengthens the overall argument.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (AF3 specificity), R1-M2 (statistical reporting), R1-M3 (coevolution confounders), R1-M4 (experimental validation gap).
- **Assessment against Nature-style criteria**  
  *Originality*: High. The identification of a specific USS receptor candidate in Pasteurellaceae is a novel contribution, and the application of AF3 to this problem is timely.  
  *Scientific importance*: Moderate to high. If validated, this finding would resolve a key gap in understanding natural transformation in a clinically relevant bacterial family. However, the purely computational nature limits immediate impact.  
  *Interdisciplinary readership*: Moderate. The work will appeal primarily to microbiologists and evolutionary biologists. The computational methods section may be of interest to structural biologists, but the specialized topic may limit broader appeal.  
  *Technical soundness*: The pipeline is logically constructed, but the lack of accessible statistical details and the inherent limitations of the computational methods (as acknowledged by the authors) mean the technical case is not fully established.  
  *Readability for nonspecialists*: The manuscript is generally well-written, but the methods section is dense and assumes familiarity with multiple specialized tools. A brief primer on key concepts (e.g., ipTM, Cramér's Φ) would improve accessibility.
- **Recommendation posture** Supportive if technical concerns are resolved. The core hypothesis is plausible and the computational evidence is suggestive, but the current manuscript does not fully establish the case from the provided evidence. The authors should address the concerns below, particularly the need for clearer statistical reporting and a more critical discussion of AF3 limitations.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that AF3 models of PpdA with USS are significantly better than with scrambled USS, and that this identifies PpdA as the USS receptor.
- **Evidence pointer** Results section "Assessment of protein-DNA complexes modeled in AF3"; Figure 2; Table 2; Code Output S1 (not provided)
- **Concern** The central claim relies on the ability of AF3 to distinguish specific from non-specific protein-DNA interactions. AF3 is trained on known protein complexes and may have inherent biases toward certain protein folds or DNA conformations. The authors do not report the distribution of ipTM scores for all 73 orthogroups, nor do they provide a baseline comparison (e.g., a known non-DNA-binding protein). The threshold of ipTM ≥ 0.6 is cited but not justified. Furthermore, the comparison to scrambled USS sequences is a useful control, but it does not rule out the possibility that AF3 predicts binding to any GC-rich DNA, rather than the specific USS motif.
- **Why it matters** If AF3 has a systematic bias, the conclusion that PpdA is uniquely capable of USS-specific binding would be weakened. The manuscript's central claim depends on the specificity of the AF3 predictions.
- **Resolution test** The authors should provide a full distribution of ipTM scores for all 73 orthogroups, including those that did not meet the threshold. They should also include a negative control protein (e.g., a cytoplasmic protein not involved in DNA binding) modeled with USS and scrambled USS. Additionally, they should report the ipTM scores for PpdA with a non-USS DNA sequence of similar GC content to demonstrate specificity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors report "strong significance (***)" for DeepPBS predictions and describe coevolution analyses with "considerable overlap" and "strong coevolutionary signals."
- **Evidence pointer** Results sections "PpdAUSS DeepPBS DNA-binding specificity predictions" and "Ortholog-eUSS coevolution analyses by Cramér's Φ and miBIO"; Figures 3–6; Supplementary Tables S4–S8
- **Concern** The manuscript does not report exact p-values, test statistics, or effect sizes for any of the statistical tests. The use of asterisks (***) is not accompanied by a definition of the significance threshold. For the coevolution analyses, the "considerable overlap" between methods is described qualitatively, but no quantitative measure of agreement (e.g., correlation between ΦC and MI rankings) is provided. This makes it impossible to assess the strength of the evidence.
- **Why it matters** The claim that PpdA is the USS receptor rests on the statistical significance of the computational predictions. Without precise reporting, the reader cannot evaluate whether the results are robust or marginal.
- **Resolution test** The authors should report exact p-values, test statistics, and effect sizes for all comparisons. For the coevolution analyses, they should provide a quantitative measure of agreement between ΦC and MI results (e.g., Spearman's rank correlation) and specify the criteria for identifying "strong" coevolution.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors state that coevolution analyses support PpdA as the USS receptor and that the signal is specific to PpdA relative to other orthogroups.
- **Evidence pointer** Results section "Ortholog-eUSS coevolution analyses by Cramér's Φ and miBIO"; Supplementary Figures S7, S8; Supplementary Tables S6–S8
- **Concern** Coevolution analyses are prone to false positives due to phylogenetic confounding. The authors acknowledge this but do not demonstrate that their results are robust to such effects. They do not report whether the coevolutionary signal is concentrated in specific functional domains of PpdA or whether it is distributed across the entire protein. The identification of 47 positions with strong coevolutionary signals is interesting, but the authors state that these are "distributed across all domains," which complicates the interpretation that a specific DNA-binding interface is under selection.
- **Why it matters** If the coevolutionary signal is not specifically localized to the putative DNA-binding interface, it may reflect broader evolutionary constraints unrelated to USS recognition, weakening the claim that PpdA is the USS receptor.
- **Resolution test** The authors should perform a phylogenetic independent contrast analysis or a similar method to control for phylogenetic non-independence. They should also map the coevolving positions onto the PpdA structure and assess whether they cluster in the DNA-binding interface identified by AF3.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors conclude that PpdA is the USS receptor and propose renaming it ComN.
- **Evidence pointer** Discussion and Conclusion sections
- **Concern** The manuscript is entirely computational. While the authors cite prior experimental work showing that comN is essential for transformation, they do not present any new experimental data directly demonstrating that PpdA binds USS with the predicted specificity. The claim that PpdA is the USS receptor is therefore a prediction, not a demonstrated fact. The authors acknowledge this in the abstract ("predicted") and discussion, but the conclusion is phrased strongly ("make a strong case").
- **Why it matters** The scientific importance of the claim depends on its experimental validation. Without direct biochemical or genetic evidence, the manuscript's contribution is a well-formulated hypothesis, not a definitive identification.
- **Resolution test** The authors should either (a) include experimental validation (e.g., electrophoretic mobility shift assays, surface plasmon resonance, or in vivo USS uptake assays with PpdA mutants) or (b) temper the conclusion to clearly state that PpdA is a strong candidate requiring experimental confirmation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract states the USS receptor "remains unknown" but does not mention that a previous study (Molnar, 2004) had already proposed ComN as a candidate. This omission may mislead readers into thinking this is the first proposal.
- **Required correction** Add a brief mention of prior candidate proposals and how this study differs (e.g., "While ComN has been previously proposed as a candidate, its role as the USS receptor has not been established. Here, we provide comprehensive in silico evidence...").

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Molecular dynamics simulation—GROMACS"
- **Evidence pointer** Methods, GROMACS section
- **Issue** The methods state that simulations ran for "a minimum of 300 ns" but do not report the number of replicates, the system size, or the convergence criteria. This limits reproducibility.
- **Required correction** Provide details on the number of simulation replicates, system composition, and how convergence was assessed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, paragraph on coevolution
- **Evidence pointer** Discussion, "Coevolutionary support of PpdA" section
- **Issue** The authors suggest that coevolutionary signals may be inflated by linkage disequilibrium but do not discuss how this might specifically affect the interpretation of PpdA as the USS receptor. A more explicit discussion of how this confounder could impact the conclusions would strengthen the manuscript.
- **Required correction** Add a sentence explicitly stating how linkage disequilibrium could lead to false positives and why the authors still consider the coevolutionary signal meaningful.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Nomenclature
- **Affected element** Title and Abstract
- **Evidence pointer** Title; Abstract
- **Issue** The title states "ComN predicted the USS-receptor" which is grammatically awkward. The abstract proposes renaming PpdA to ComN, but the title uses ComN as if it is already established.
- **Required correction** Revise the title for clarity, e.g., "Type IV minor pilin PpdA/ComN is predicted to be the USS receptor in Pasteurellaceae."

## Risk / unsupported claims
- The claim that PpdA is the USS receptor is a prediction based on computational modeling and is not experimentally validated. This is acknowledged by the authors but should be more prominently framed as a hypothesis.
- The claim that AF3 models are "significantly better" for PpdA with USS compared to scrambled USS is not fully supported by the data presented in the text, as exact statistics are not reported.
- The proposal to rename PpdA as ComN is based on the authors' findings and prior gene designations, but the rationale for this nomenclature change is not fully articulated.
- The claim that coevolutionary signals support PpdA as the USS receptor is weakened by the acknowledged potential for phylogenetic confounding and the lack of domain-specific localization of the signal.
- The statement that "PpdA was the only orthogroup that consistently yielded AF3 models of high quality" is not verifiable without access to the full dataset of 73 orthogroups and their model quality metrics.