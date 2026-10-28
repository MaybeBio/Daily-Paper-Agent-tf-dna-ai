## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, limitations, methods) as provided.
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and alignment with Nature-style criteria. Editorial or formatting issues are not assessed.
- **Shared manuscript claim summary** The authors present a time-resolved single-cell multi-omic atlas of human iPSC-derived cardiac organoid differentiation, integrate it with deep learning models (ChromBPNet) to predict chromatin accessibility from DNA sequence, and use this framework to discover cell-state-specific regulatory syntax underlying early cardiac development. They validate predictions by perturbing MYOCD, identify distinct regulatory programs for ventricular versus pacemaker cardiomyocytes, and link noncoding variants to CHD-associated genes with cell-state-specific predicted effects.
- **Visible evidence base** Main figures referenced: Fig. 1A-G, Fig. 2A-F, Fig. 3A-H, Fig. 4A-G, Fig. 5A-J, Fig. 6A-G; supplementary figures S1-S11; tables S1-S4, S8-S9; methods sections for cell culture, single-cell processing, data analysis, ChromBPNet training and interpretation.
- **Missing materials affecting confidence** Figure panels and supplementary figures/tables are referenced but not provided in the submitted text. Exact numerical results (e.g., correlation coefficients, p-values, effect sizes) are not reported in the text. Details of the MYOCD perturbation experiment (e.g., guide RNAs, validation of knockdown efficiency, number of replicates) are not described. The in vivo reporter assay comparison (Kosicki et al.) is described qualitatively without quantitative concordance metrics.

## Reviewer
- **Overall assessment** This manuscript presents a substantial and timely integration of single-cell multi-omic data with deep learning to decode regulatory grammar during cardiac organoid differentiation. The conceptual framework is compelling, and the potential to link noncoding variation to developmental gene regulation is of high interest. However, the current text provides limited quantitative evidence for key claims, and several methodological details are insufficiently described to assess robustness. The validation experiments, while promising, are described at a level that does not yet establish the central claims with the rigor expected for a high-impact venue.
- **Who would be interested in the results, and why** Developmental biologists studying cardiac lineage specification and congenital heart disease; computational biologists working on regulatory genomics and deep learning; researchers using organoid models for disease modeling; geneticists interested in interpreting noncoding variation in developmental disorders.
- **Major strengths** 1) The generation of a time-resolved single-cell multi-omic atlas of cardiac organoid differentiation is a valuable resource. 2) The application of ChromBPNet to learn cell-state-specific regulatory syntax at base-pair resolution is methodologically advanced. 3) The framework's ability to resolve context-dependent cis-regulatory elements (cdCREs) and predict cell-state-specific effects of noncoding variants addresses a critical gap in the field. 4) The functional validation of MYOCD as a ventricular specification factor provides a concrete test of the model's predictions. 5) The integration with in vivo reporter data adds external validity.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The claim that the deep learning models accurately predict cell-state-specific chromatin accessibility from DNA sequence.
  - **Evidence pointer** Results section "Deep learning models decipher the regulatory sequence syntax of cardiac lineage commitment"; Fig. S3A-B
  - **Concern** The manuscript reports Pearson correlations ranging from 0.78 to 0.88 and median JSD values from 0.47 to 0.73, but no details are provided on how these metrics were computed, what the baseline or null expectations are, or how they compare to alternative methods. The text states "model correlations ranged from 0.78 to 0.88" without specifying whether these are per-cell-state, per-peak, or aggregated values. The JSD values are presented without context for what constitutes a good or poor profile match. Without this information, the accuracy of the models cannot be adequately assessed.
  - **Why it matters** The entire framework depends on the predictive accuracy of the ChromBPNet models. If the models are not demonstrably accurate, all downstream analyses of regulatory syntax, cdCREs, and variant effects are built on an unvalidated foundation.
  - **Resolution test** Provide a clear description of the evaluation metrics, including how correlations and JSDs were computed, and include comparisons to appropriate baselines (e.g., random sequence, motif-scanning approaches) and, if possible, to other deep learning models. Report the distribution of these metrics across cell states and peaks, and show that the models outperform baselines.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The claim that the framework identifies cell-state-specific regulatory programs and that MYOCD is essential for ventricular specification.
  - **Evidence pointer** Results section "Functional validation reveals MYOCD is essential for ventricular cardiomyocyte specification"; Fig. 5A-G
  - **Concern** The MYOCD perturbation experiment is described in minimal detail. The text states "We used a CRISPR-interference (CRISPRi) system to knock down (KD) MYOCD" and reports "a significant reduction in canonical in vitro vCMs by day 10," but no information is provided on the number of biological replicates, the efficiency of knockdown, the specificity of the guide RNAs, or the statistical methods used to assess significance. The claim that MYOCD is "essential" is strong and requires robust evidence, including demonstration that the effect is specific to MYOCD loss and not an off-target effect.
  - **Why it matters** The functional validation is a key component of the manuscript's claim to have identified a critical regulator. Without adequate experimental detail, the validity of this central conclusion cannot be evaluated.
  - **Resolution test** Provide full details of the CRISPRi experiment, including guide RNA sequences, validation of on-target activity, number of replicates, and statistical analysis. Show that the effect on vCM specification is rescued by MYOCD overexpression or that the phenotype is recapitulated with independent guides. Quantify the reduction in vCMs and demonstrate specificity to the ventricular lineage.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The claim that the framework links noncoding variants to CHD-associated genes with cell-state-specific predicted effects.
  - **Evidence pointer** Results section "Noncoding variants associated with CHD genes have cell-state-specific predicted effects"; Fig. 6A-G
  - **Concern** The analysis of noncoding variants is described at a high level, but the specific methods for variant effect prediction are not fully detailed. The text mentions "quantitatively evaluated the predicted effect on chromatin accessibility of various single-nucleotide polymorphisms" and identifies one variant (rs377307764) that disrupts a GATA motif, but no information is provided on how many variants were tested, how the significance of the predicted effects was determined, or how the cell-state-specificity was established. The connection to CHD is based on gene annotation, but the functional relevance of the predicted regulatory disruption is not experimentally tested.
  - **Why it matters** The claim that the framework can identify disease-relevant noncoding variants is a major translational implication. Without a clear description of the variant effect prediction methodology and its limitations, the strength of this claim is unclear.
  - **Resolution test** Provide a detailed description of the variant effect prediction pipeline, including the number of variants tested, the null model used to assess significance, and the criteria for calling a variant "disruptive." Show that the predicted effects are specific to the cell states where the target gene is expressed and, ideally, validate at least one variant experimentally in an appropriate cellular context.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The claim that the framework "uncovered cell-state-specific rules of cardiogenesis" and that this represents a "dynamic regulatory sequence code."
  - **Evidence pointer** Abstract; Results sections throughout
  - **Concern** While the framework is innovative, the manuscript does not clearly articulate what fundamentally new biological insights are gained beyond what could be obtained with existing approaches. The examples provided (DHRS3 cdCRE, TEAD partner-dependent activity, MYOCD in ventricular specification) are illustrative but do not yet constitute a systematic discovery of a "code." The claim of a "code" implies a predictive, generalizable set of rules, which is not demonstrated.
  - **Why it matters** The framing of the manuscript as decoding a "regulatory sequence code" sets a high bar. If the findings are primarily descriptive or confirmatory of known biology, the impact may be more incremental than implied.
  - **Resolution test** Clearly articulate what specific, novel regulatory rules were discovered and demonstrate their predictive power, e.g., by showing that the model can accurately predict the effects of new perturbations or that the identified syntax rules generalize to other developmental contexts or organoid systems.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, first sentence
  - **Issue** The phrase "dynamic regulatory sequence code" is evocative but not defined. It is unclear whether this refers to the model's learned representations, the identified motifs, or the rules governing their combinatorial activity.
  - **Required correction** Define the term explicitly in the introduction or abstract.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, ChromBPNet training
  - **Evidence pointer** Methods section "ChromBPNet Training"
  - **Issue** The text states "5 individual ChromBPNet models were trained by following the 5-fold cross-validation scheme" but does not specify the hyperparameters used, the number of training epochs, or the computational resources required.
  - **Required correction** Provide full training details or a reference to a prior publication with complete specifications.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Results, Fig. 5H
  - **Evidence pointer** Results section "MYOCD loss perturbs cardiac and ectodermal regulatory programs"
  - **Issue** The enrichment analysis using Fisher's exact test is described, but no multiple testing correction is mentioned. Given the large number of motifs tested, this could lead to false positives.
  - **Required correction** State whether multiple testing correction was applied and, if not, justify its omission.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Methods, Data analysis
  - **Evidence pointer** Methods section "Data analysis"
  - **Issue** The text states "All analysis scripts can be found here https://github.com/GreenleafLab/Cardioid" but does not specify where the raw sequencing data will be deposited.
  - **Required correction** Provide a data availability statement with accession numbers for the raw and processed data.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Results, Fig. 3H
  - **Evidence pointer** Results section "Modeling deciphers the context-dependent grammar of TF cooperativity"
  - **Issue** The claim that "a HAND and TEAD motif pair has the highest chromatin activity when separated by exactly three base pairs" is presented without confidence intervals or a statistical test. It is unclear if this spacing preference is significantly different from other spacings.
  - **Required correction** Provide statistical support for the spacing preference or soften the claim.
- **Technical failings that need to be addressed before the case is established** R1-M1 (model evaluation metrics), R1-M2 (MYOCD perturbation details), R1-M3 (variant effect prediction methodology). These are blocking because the central claims of the manuscript depend on the validity of the deep learning models, the functional validation, and the disease relevance.
- **Assessment against Nature-style criteria**  
  *Originality*: The integration of single-cell multi-omics with deep learning for regulatory syntax discovery is novel and represents a methodological advance. However, the biological insights presented are largely confirmatory of known cardiac developmental regulators.  
  *Scientific importance*: The framework has the potential to significantly impact the field by enabling systematic interpretation of noncoding variation in developmental disorders. The resource itself (the atlas) is valuable. However, the current evidence does not yet demonstrate a major conceptual advance in understanding cardiac development.  
  *Interdisciplinary readership*: The work bridges developmental biology, computational genomics, and disease genetics, and would appeal to a broad audience. The writing is generally accessible, though some methods sections are dense.  
  *Technical soundness*: The deep learning approach is state-of-the-art, but the evaluation metrics and validation experiments are insufficiently described to assess robustness. The lack of quantitative details undermines confidence.  
  *Readability for nonspecialists*: The abstract and introduction are clear and compelling. The results sections are more technical but generally understandable. The manuscript would benefit from a more explicit explanation of what the "regulatory sequence code" means and why it matters.
- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual framework is promising and the resource is valuable, but the current evidence does not fully establish the central claims. The authors must provide a more rigorous evaluation of their models, detailed validation of the MYOCD perturbation, and a clearer description of the variant effect prediction methodology.

## Risk / unsupported claims
- The claim that the models "uncovered cell-state-specific rules of cardiogenesis" is not fully supported by the quantitative evidence presented.
- The claim that MYOCD is "essential" for ventricular specification is not supported by the limited experimental detail provided.
- The claim that the framework can identify disease-relevant noncoding variants is not supported by experimental validation.
- The claim that the identified regulatory syntax represents a "code" is not demonstrated; the findings are illustrative rather than systematic.
- The claim that the cardioid model "recapitulates human organogenesis" is based on projection to a gastrula atlas, but the statistical significance and robustness of this projection are not reported.
- The claim that "85% of these dynamically regulated ZNFs are poorly characterized" relies on a text-mining approach (Note S5) that is not described in sufficient detail to assess its accuracy.