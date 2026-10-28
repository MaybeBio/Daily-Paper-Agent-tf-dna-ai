## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose EGNA, an empirical graph neural network that incorporates scaffold information to predict protein-ligand binding affinity. The method constructs separate graphs for protein, ligand, and their interactions based on different regions of the bound complex, uses graph convolutional layers to capture interaction patterns, and claims superior performance and good generalization compared to state-of-the-art machine learning-based scoring functions on two benchmark datasets.
- **Visible evidence base** Abstract text only; no quantitative results, benchmark details, or implementation specifics are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, benchmark dataset descriptions, evaluation metrics, baseline method details, statistical significance tests, and supplementary information

## Reviewer
- **Overall assessment** The abstract presents a plausible methodological direction for protein-ligand binding affinity prediction, specifically the incorporation of scaffold information and region-specific graph construction. However, the abstract lacks quantitative results, benchmark specifications, and methodological details necessary to evaluate the validity of the claims. The core assertions of superiority and generalization are unsupported by the visible evidence.
- **Who would be interested in the results, and why** Computational structural biologists, medicinal chemists, and researchers in drug discovery would be interested if the method demonstrates reliable affinity prediction. The emphasis on interpretability of factor contributions may also appeal to those developing explainable AI models for molecular interactions.
- **Major strengths** The proposed approach of using region-specific graphs to model differential atom contributions is conceptually reasonable and addresses a known limitation in existing deep learning scoring functions. The stated availability of a web server and source code supports reproducibility.
- **Major Concerns**  
  - **Concern ID** R1-M1  
    **Severity** Major  
    **Blocking** Yes  
    **Axis** Evidence sufficiency  
    **Claim pointer** "EGNA is compared with the state-of-the-art machine learning-based scoring functions on two widely used benchmark datasets. The results demonstrate the superiority of EGNA and its good generalization capability."  
    **Evidence pointer** Abstract, Results section; location not provided  
    **Concern** The abstract claims superiority and good generalization but provides no numerical results, no specification of which benchmarks were used, no definition of evaluation metrics, and no description of how generalization was assessed.  
    **Why it matters** Without quantitative evidence, the central claim of the paper cannot be evaluated. The term "superiority" is undefined in the absence of performance numbers or statistical comparisons.  
    **Resolution test** Provide performance metrics (e.g., RMSE, Pearson correlation, Spearman correlation) for EGNA and all baselines on both benchmarks, including confidence intervals or significance tests, and describe the generalization protocol (e.g., cross-validation splits, temporal splits, or external test sets).  
  - **Concern ID** R1-M2  
    **Severity** Major  
    **Blocking** Yes  
    **Axis** Methodological clarity  
    **Claim pointer** "Graphs of protein, ligand and their interactions are constructed based on different regions of each bound complex."  
    **Evidence pointer** Abstract, Methods description; location not provided  
    **Concern** The abstract does not explain what "different regions" means, how scaffold information is specifically encoded, or how the interaction graph is constructed. The term "empirical graph neural network" is not defined.  
    **Why it matters** The methodological novelty hinges on these design choices. Without specification, the approach cannot be reproduced or distinguished from existing graph neural network scoring functions.  
    **Resolution test** Describe the graph construction procedure in detail, including how protein regions are defined, how scaffold atoms are identified and represented, and how interaction edges are weighted or typed.  
  - **Concern ID** R1-M3  
    **Severity** Major  
    **Blocking** Yes  
    **Axis** Interpretability claim  
    **Claim pointer** "The contributions of different factors on binding affinity can thus be transparently investigated."  
    **Evidence pointer** Abstract, Results section; location not provided  
    **Concern** The abstract asserts that factor contributions can be transparently investigated but provides no example, analysis, or validation of this interpretability.  
    **Why it matters** Interpretability is presented as a key advantage, but without demonstration, this claim is unsubstantiated.  
    **Resolution test** Include an analysis section showing how specific factors (e.g., scaffold atoms, interaction distance, residue type) contribute to predicted affinity, with validation against known biophysical principles or experimental data.

- **Minor Comments**  
  - **Concern ID** R1-m1  
    **Severity** Minor  
    **Axis** Clarity  
    **Affected element** Abstract, Availability section  
    **Evidence pointer** Abstract, Availability and implementation; location not provided  
    **Issue** The web server and source code URLs are provided, but the abstract does not state the license or the programming language and dependencies for the code.  
    **Required correction** Specify the software license and the primary implementation language and key dependencies.  
  - **Concern ID** R1-m2  
    **Severity** Minor  
    **Axis** Terminology  
    **Affected element** Abstract, Results section  
    **Evidence pointer** Abstract, Results section; location not provided  
    **Issue** The term "empirical graph neural network" is used without definition or contrast to other graph neural network variants.  
    **Required correction** Define the term in the abstract or methods, and clarify how it differs from standard graph neural network scoring functions.  
  - **Concern ID** R1-m3  
    **Severity** Minor  
    **Axis** Completeness  
    **Affected element** Abstract, Results section  
    **Evidence pointer** Abstract, Results section; location not provided  
    **Issue** The abstract does not mention the size of the datasets, the number of complexes, or the range of binding affinities covered.  
    **Required correction** Include basic dataset statistics in the abstract or indicate where they are reported in the full manuscript.

## Risk / unsupported claims
- The claim of "superiority" over state-of-the-art methods is unsupported by any quantitative data in the abstract.
- The claim of "good generalization capability" is unsupported without a description of the evaluation protocol.
- The claim that "contributions of different factors on binding affinity can thus be transparently investigated" is unsupported without any demonstration or analysis.
- The methodological novelty regarding scaffold information and region-specific graphs is not sufficiently described to be assessed.