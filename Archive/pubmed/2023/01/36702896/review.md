## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and supplementary figure legends.
- **Assessment boundary** Scientific validity, technical soundness, novelty, and significance of the claims as presented in the provided manuscript. No assessment of editorial fit or publication decision.
- **Shared manuscript claim summary** The authors present ZFDesign, a deep-learning model trained on 49 billion protein–DNA interactions from bacterial one-hybrid (B1H) selections, to design zinc finger (ZF) arrays for any genomic target. The model uses a hierarchical transformer architecture to account for inter-finger compatibility. The authors demonstrate that ZFDesign-designed arrays can reprogram human transcription factors for activation and repression, including endogenous gene regulation, and show improved specificity prediction over existing tools.
- **Visible evidence base** Abstract, full main text, methods section, and descriptions of supplementary figures and tables. No raw data, code, or supplementary files were provided for independent verification.
- **Missing materials affecting confidence** Raw sequencing data, B1H selection datasets, model code and weights, detailed hyperparameters, source data for all figures, and full supplementary figures and tables. These are essential for verifying the training data quality, model architecture, and reproducibility of the reported results.

## Reviewer
- **Overall assessment** The manuscript presents a potentially significant advance in ZF design, addressing a long-standing challenge in the field. The scale of the screening data (49 billion interactions) is impressive, and the hierarchical transformer architecture is a logical and novel approach to modeling neighbor effects. The demonstration of transcription factor reprogramming for both activation and repression, including endogenous targets, is compelling. However, the manuscript has several technical and evidentiary gaps that must be addressed before the central claims are fully established. The lack of access to the model, code, and raw data prevents independent validation, and some experimental details are insufficiently described. The off-target activity observed in ChIP–seq, while discussed, raises questions about the specificity of the designed arrays that are not fully resolved.
- **Who would be interested in the results, and why** Researchers in genome engineering, synthetic biology, gene therapy, and transcription factor biology. The ability to design ZF arrays for any target with high efficacy has direct applications in creating programmable transcription factors, base editors, and other chromatin-modifying tools. The model's potential to reduce the need for laborious experimental selection would be of broad interest to the molecular biology community.
- **Major strengths**
    1.  The scale and design of the screening approach, using multiple libraries with different interface environments, is a significant methodological advance.
    2.  The hierarchical transformer architecture is a novel and appropriate approach to model the hierarchical nature of ZF-DNA interactions.
    3.  The demonstration of functional reprogramming of human transcription factors for both activation and repression, including endogenous gene regulation, is a strong validation of the approach.
    4.  The comparison with ZFPred shows a clear improvement in prediction accuracy, suggesting the model captures important inter-finger interactions.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Reproducibility and Data Availability
    - **Claim pointer** The manuscript claims that ZFDesign is a "universal deep-learning model" that "solves ZF design for any genomic target."
    - **Evidence pointer** Methods: "Computational analysis", "Neural network architecture", "Training datasets". Location not provided for model code or data.
    - **Concern** The manuscript does not provide access to the model architecture code, trained weights, or the raw B1H selection data. The methods describe the architecture but lack critical hyperparameters, training details, and data preprocessing steps. Without these, the model cannot be independently reproduced or tested by the community, which is a core requirement for a tool presented as a general solution.
    - **Why it matters** The central claim of the paper is the creation of a universal design tool. If the tool is not accessible or reproducible, its utility and the validity of the claims are severely undermined. The scientific community cannot build upon or verify the results without access to the underlying resources.
    - **Resolution test** The authors must provide a public repository with the model code, trained weights, and a clear description of the training data and hyperparameters. The raw and processed B1H selection data should also be deposited in a public database.
    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical Soundness of Specificity Analysis
    - **Claim pointer** The manuscript claims that ZFDesign can predict the specificity of designed arrays with "relatively high accuracy" and better than existing tools.
    - **Evidence pointer** Results: "Specificity and genome-wide regulatory activity of RTFs", Figure 6f, Supplementary Figures 19 and 20.
    - **Concern** The specificity analysis relies on B1H selections for individual ZF pairs, which are then concatenated to predict the specificity of the full array. The ChIP–seq data, which is the most direct measure of genome-wide binding, shows a large number of off-target peaks. The manuscript does not provide a quantitative comparison between the predicted specificity (from B1H) and the observed binding (from ChIP–seq) for the same arrays. The claim of "relatively high accuracy" is therefore not directly supported by the presented data.
    - **Why it matters** The utility of ZFDesign for therapeutic applications depends on its ability to design highly specific ZF arrays. If the model's specificity predictions do not correlate with actual genome-wide binding, the tool's practical value is limited. The discrepancy between B1H-predicted and ChIP–seq-observed specificity needs to be reconciled.
    - **Resolution test** The authors should provide a direct, quantitative comparison of predicted binding sites (from B1H and ZFDesign) with ChIP–seq peaks for the same ZF arrays. This could include a Venn diagram, a rank-order correlation, or a receiver operating characteristic (ROC) analysis. The analysis should also address the source of the off-target binding, e.g., whether it is driven by individual high-affinity fingers or by the array as a whole.
    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Experimental Validation and Statistical Power
    - **Claim pointer** The manuscript claims that ZFDesign-designed arrays can "seamlessly reprogram" transcription factors and regulate endogenous genes.
    - **Evidence pointer** Results: "Seamless reprogramming of human transcription factors", Figure 5d and 5e.
    - **Concern** The endogenous gene regulation experiments (CDKN2A activation and DPH1 repression) are presented for a limited number of designed arrays. The manuscript does not report the number of independent biological replicates, the statistical significance of the observed changes, or a comparison to a larger panel of designed arrays to demonstrate the robustness of the design process. The claim of "seamless" reprogramming is strong and requires more extensive validation.
    - **Why it matters** The therapeutic potential of this technology relies on the consistent and predictable function of designed ZF arrays. Demonstrating efficacy on a small number of targets does not establish the generality of the approach. A more comprehensive validation, including multiple targets and replicates, is needed to support the claim of a universal design method.
    - **Resolution test** The authors should provide data from a larger panel of designed ZF arrays targeting multiple genes, with appropriate statistical analysis (e.g., mean ± s.d., number of replicates, p-values). The data should show a high success rate and consistent levels of activation/repression across different targets.
- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity of Methods
    - **Affected element** Methods: "Neural network architecture"
    - **Evidence pointer** Methods section, location not provided.
    - **Issue** The description of the model architecture is high-level. The exact input representation (e.g., one-hot encoding of DNA and amino acids), the masking strategy, and the loss function are described, but the details of the attention mechanisms and the flow of information between the three modules are not fully specified.
    - **Required correction** Provide a more detailed description of the model, including a diagram of the tensor dimensions and the flow of data. Include specific hyperparameters (e.g., number of layers, learning rate schedule, batch size) in the methods or a supplementary table.
    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Data Presentation
    - **Affected element** Figure 6
    - **Evidence pointer** Results: "Specificity and genome-wide regulatory activity of RTFs", Figure 6.
    - **Issue** The ChIP–seq data is presented as a summary of peak counts and a representative genome browser track. The manuscript does not show the full distribution of peak intensities or a comparison of binding strength between on- and off-target sites.
    - **Required correction** Include a plot showing the distribution of ChIP–seq read densities at on-target vs. off-target sites. This would provide a more quantitative view of the specificity of the designed arrays.
    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Discussion of Limitations
    - **Affected element** Discussion section
    - **Evidence pointer** Discussion, location not provided.
    - **Issue** The discussion of off-target binding is brief. The authors attribute it to the modular design and the use of base-skipping linkers, but they do not discuss potential strategies to mitigate this, such as using the model to design arrays with reduced off-target propensity.
    - **Required correction** Expand the discussion to include a more thorough analysis of the causes of off-target binding and potential future directions to improve specificity, such as incorporating negative selection data into the model training.
- **Technical failings that need to be addressed before the case is established**
    - R1-M1: Lack of access to model code, weights, and data.
    - R1-M2: Lack of direct quantitative comparison between predicted and observed genome-wide specificity.
    - R1-M3: Insufficient experimental validation to support the claim of "seamless" and universal reprogramming.
- **Assessment against Nature-style criteria**
    - **Originality** High. The hierarchical transformer architecture applied to ZF design is novel, and the scale of the screening data is unprecedented. The approach of modeling neighbor effects explicitly is a significant conceptual advance over previous methods.
    - **Scientific importance** High. If validated, this work could transform the field of ZF engineering, making it accessible to a wide range of researchers and enabling new therapeutic strategies. The potential to reprogram endogenous transcription factors is of great biological and clinical significance.
    - **Interdisciplinary readership** High. The work bridges computational biology, structural biology, molecular biology, and genomics. The results are relevant to researchers in genome engineering, gene therapy, and synthetic biology.
    - **Technical soundness** Moderate. The experimental design is generally sound, but the lack of data availability and the incomplete validation of specificity claims are significant weaknesses. The statistical power of the endogenous gene regulation experiments is not clearly established.
    - **Readability for nonspecialists** Good. The manuscript is well-written and the concepts are explained clearly. The figures are informative, although some (e.g., Figure 6) could be more quantitative. The abstract is accessible and accurately summarizes the main findings.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea and initial results are highly promising and of significant interest. However, the manuscript is currently not fully established from the provided evidence due to the lack of reproducibility and the incomplete validation of the specificity and generality claims. The authors must provide the model and data, and strengthen the experimental validation, to fully support their claims.

## Risk / unsupported claims
- The claim that ZFDesign "solves ZF design for any genomic target" is not fully supported, as the model was trained on a limited set of 6-bp targets and its performance on all possible genomic sequences is not demonstrated.
- The claim of "seamless" reprogramming is not quantitatively supported by the limited number of endogenous gene targets tested.
- The claim that ZFDesign predicts specificity with "relatively high accuracy" is not directly supported by a quantitative comparison with ChIP–seq data.
- The statement that the model captures "global and target-specific differences" is supported by the data, but the biological interpretation of these differences is not fully explored.
- The performance of ZFDesign compared to other state-of-the-art ZF design tools, beyond ZFpred, is not assessed.