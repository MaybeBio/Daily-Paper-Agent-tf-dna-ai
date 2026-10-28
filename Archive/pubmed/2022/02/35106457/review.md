## Review setup
- **Input scope** Full manuscript text, including summary, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific validity, technical soundness, reproducibility, and support of claims based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors identify a single amino acid substitution (L507A) in the KLF4 zinc-finger DNA-binding domain that enhances the speed and efficiency of somatic cell reprogramming to pluripotency in both mouse and human cells. They propose that this variant achieves its effect through altered DNA-binding specificity, particularly increased binding to pluripotency gene promoters/enhancers such as KLF5, and through a predicted conformational change that creates additional protein-DNA interactions.
- **Visible evidence base** Results sections describing alanine-scanning mutagenesis, reprogramming assays in mouse and human cells, ChIP-seq and RNA-seq analyses, co-immunoprecipitation experiments, and molecular dynamics simulations. Figure legends for Figures 1-8 and supplementary figure legends are provided.
- **Missing materials affecting confidence** Actual figures and supplementary figures are not viewable. Numerical data underlying graphs are not provided. Statistical details beyond p-values are incomplete. ChIP-seq and RNA-seq quality metrics are not described. MD simulation convergence and validation details are limited. No information on biological replicates for key experiments beyond n values.

## Reviewer
- **Overall assessment** This manuscript presents a potentially interesting structure-function approach to improving reprogramming factor activity. The identification of a single point mutation in KLF4 that enhances reprogramming is conceptually appealing and could have practical utility. However, the evidence provided is insufficient to fully establish the mechanistic claims. The central assertion that L507A acts through altered DNA-binding specificity and enhanced binding to pluripotency loci is supported by correlative ChIP-seq data but lacks functional validation. The MD simulation results are suggestive but not experimentally confirmed. The manuscript would benefit from additional experiments linking the proposed mechanism to the phenotype, as well as more rigorous quantitative analysis of the reprogramming data.

- **Who would be interested in the results, and why** Researchers in the fields of cellular reprogramming, pluripotency, and regenerative medicine would be interested in the potential for engineered transcription factors to improve reprogramming efficiency. The structural insights into KLF4 DNA-binding may also interest investigators studying Kruppel-like factor family biology and zinc-finger protein-DNA interactions. The broader concept of rational engineering of pioneer transcription factors could appeal to synthetic biologists and protein engineers.

- **Major strengths**
  1. The structure-function approach is logical and addresses an underexplored area: engineering reprogramming factors themselves rather than only optimizing culture conditions or factor combinations.
  2. The alanine-scanning mutagenesis of DNA-interacting residues is systematic and provides a useful map of functionally important residues in the KLF4 zinc-finger domain.
  3. The demonstration of improved reprogramming in both mouse and human cells suggests potential cross-species relevance.
  4. The combination of ChIP-seq, RNA-seq, and MD simulation provides a multi-pronged approach to understanding the mechanism.
  5. The identification of a negative correlation between amino acid side-chain volume at position 507 and reprogramming efficiency is an interesting structure-activity relationship.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic support
- **Claim pointer** The authors claim that "L507A bound more to promoters or enhancers of pluripotency genes, such as KLF5, and drove gene expression of these genes during reprogramming."
- **Evidence pointer** Results section "Distinctive features of DNA binding patterns of KLF4 L507A in reprogramming", Figure 6
- **Concern** The ChIP-seq data show quantitative differences in peak numbers between WT and L507A conditions, but the manuscript does not demonstrate that these differences are functionally causal. The claim that L507A "drove gene expression" of target genes is based on correlative RNA-seq data. No experiments are shown that directly test whether the increased binding to KLF5 or other loci is necessary for the enhanced reprogramming phenotype. For example, knockdown or mutation of the putative L507A-specific target sites, or rescue experiments, would strengthen the causal link.
- **Why it matters** The central mechanistic claim of the paper is that altered DNA binding by L507A leads to enhanced reprogramming. Without functional validation, the ChIP-seq data remain descriptive and the mechanism is not established.
- **Resolution test** Provide loss-of-function experiments: e.g., mutate the L507A-specific binding sites in KLF5 promoter/enhancer and test whether the enhanced reprogramming phenotype is abolished. Alternatively, demonstrate that overexpression of KLF5 alone can phenocopy the L507A effect, or that KLF5 knockdown specifically impairs L507A-mediated reprogramming.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor
- **Claim pointer** The authors claim that L507A "accelerated and stabilized reprogramming to pluripotency" based on colony counts and flow cytometry.
- **Evidence pointer** Results sections "iPSC generation from Nanog-GFP MEF using KLF4 ZnF mutants" and "L507A mutant accelerated and stabilized human iPSC generation", Figures 1, 2, 3
- **Concern** The quantitative data are presented as mean ± SE with p-values, but the effect sizes, exact n values for each experiment, and the variability between independent experiments are not fully described. For the human iPSC experiments, the manuscript reports colony counts and NANOG-positive ratios, but the criteria for colony selection and the reproducibility across independent differentiations are not detailed. The claim of "stabilized" reprogramming is based on reduced heterogeneity in NANOG expression, but the statistical comparison of variances is not provided.
- **Why it matters** The practical utility of the L507A variant depends on the robustness and reproducibility of the enhanced reprogramming phenotype. Without clear quantitative rigor, it is difficult to assess the magnitude of the effect and its reliability.
- **Resolution test** Provide complete statistical reporting including effect sizes, confidence intervals, exact n values for all experiments, and variance comparison tests. Show representative data from multiple independent experiments. For the human experiments, provide details on the number of independent differentiations, the criteria for colony counting, and the reproducibility of the NANOG expression distribution.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Structural validation
- **Claim pointer** The authors claim that "MD simulation analysis predicted that this mutant may additionally acquire a unique structural conformation in the protein-DNA complex by forming additional hydrogen bonds between several other amino acid residues and DNA."
- **Evidence pointer** Results section "L507A mutant was predicted to acquire a unique conformation of protein-DNA complex with additional DNA interaction", Figure 8
- **Concern** The MD simulation results are presented as predictions without experimental validation. The manuscript does not provide experimental evidence (e.g., binding affinity measurements, structural studies, or mutagenesis of the predicted additional interaction residues) to confirm that the predicted conformational change and additional hydrogen bonds actually occur and are functionally relevant.
- **Why it matters** The structural mechanism proposed is a key part of the paper's novelty. Without experimental validation, the MD predictions remain speculative and do not fully support the mechanistic model.
- **Resolution test** Perform experimental validation: e.g., surface plasmon resonance or isothermal titration calorimetry to compare WT and L507A binding affinity to target DNA sequences; mutate the predicted additional interaction residues (Y430, R452, R467, S472) and test whether the enhanced reprogramming phenotype is lost; or solve a crystal structure of the L507A-DNA complex.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Specificity of effect
- **Claim pointer** The authors claim that "variants with smaller amino acid residues in the KLF4 L507 position showed higher reprogramming efficiency" and that this correlates with side-chain volume.
- **Evidence pointer** Results section "Screening all the natural amino acid residue variants at L507 position in reprogramming", Figure 4
- **Concern** The correlation between side-chain volume and reprogramming efficiency is based on a limited set of variants and the R² value of 0.5912 indicates a moderate correlation. The manuscript does not discuss potential confounding factors, such as differences in protein expression levels, stability, or nuclear localization among the variants. The reduced expression of L507R is noted, but the potential impact of expression differences on the observed efficiency for other variants is not systematically addressed.
- **Why it matters** The claim that smaller residues at position 507 confer higher activity is a specific structure-activity relationship. If this is confounded by expression or stability differences, the conclusion may not be valid.
- **Resolution test** Normalize reprogramming efficiency to protein expression levels for each variant. Include additional variants with similar volumes but different chemical properties to test whether the effect is truly volume-dependent. Provide data on protein stability and nuclear localization for all variants.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Experimental design
- **Affected element** Reprogramming efficiency assays
- **Evidence pointer** Figure 1, Methods section "Retrovirus-based generation of iPSCs from Nanog-GFP mouse embryonic fibroblasts"
- **Issue** The manuscript does not specify whether the colony counting was performed in a blinded manner. Given the subjective nature of colony morphology assessment, blinding would reduce potential bias.
- **Required correction** State whether colony counting was performed blinded to the experimental condition. If not, acknowledge this limitation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** ChIP-seq peak numbers
- **Evidence pointer** Figure 6A, Results section "Distinctive features of DNA binding patterns of KLF4 L507A in reprogramming"
- **Concern** The manuscript reports total peak numbers but does not provide information on peak quality, reproducibility between replicates, or whether the differences in peak numbers are statistically significant across biological replicates.
- **Required correction** Provide information on the number of ChIP-seq replicates, peak calling consistency, and statistical significance of peak number differences.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Epistasis analysis
- **Evidence pointer** Figure 5, Results section "iPSCs generation with pro-reprogramming factors dissects independent or shared functions with KLF4 L507A"
- **Concern** The interpretation that L507A is "epistatic to GLF1 and Klf5" is based on the absence of an additive effect. However, this could also be explained by a ceiling effect in the assay. The manuscript does not discuss this alternative interpretation.
- **Required correction** Acknowledge the possibility of a ceiling effect and discuss how the data distinguish between epistasis and saturation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** MD simulation
- **Evidence pointer** Methods section "Molecular dynamics (MD) simulation"
- **Issue** The manuscript states that three independent MD simulations were performed with different initial velocities, but does not provide information on the convergence of the simulations or the statistical uncertainty of the predicted interactions.
- **Required correction** Provide convergence metrics (e.g., RMSD over time) and error estimates for the predicted hydrogen bond occupancies.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 3I and 3J
- **Evidence pointer** Figure 3I, 3J, Results section "L507A mutant accelerated and stabilized human iPSC generation"
- **Issue** The scatter plots showing NANOG expression and residual SeVdp RNA are described in the text, but the axes and units are not fully defined in the figure legend. The Z-score normalization is mentioned but the reference population is not specified.
- **Required correction** Clarify the axes, units, and the reference population used for Z-score calculation in the figure legend.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of engineered transcription factors for reprogramming is brief and does not fully contextualize the findings relative to other recent efforts to improve reprogramming factors through protein engineering.
- **Required correction** Expand the discussion to include recent work on engineered transcription factors and how the present approach differs or advances the field.

## Risk / unsupported claims
1. The claim that L507A "drove gene expression" of pluripotency genes is not fully supported. The RNA-seq data show gene expression differences, but causality is not established.
2. The claim that the MD simulation predicts a "unique structural conformation" is not experimentally validated and should be presented as a hypothesis.
3. The claim that L507A "stabilized" reprogramming is based on reduced heterogeneity in NANOX expression, but the statistical comparison of variances is not provided.
4. The claim that smaller amino acid residues at position 507 confer higher reprogramming efficiency is based on a moderate correlation and may be confounded by expression differences.
5. The statement that L507A "bound more to promoters or enhancers" is based on ChIP-seq peak numbers, but quantitative binding affinity differences are not measured.
6. The claim that the effect of L507A is "epistatic to GLIS1 and Klf5" may be confounded by ceiling effects in the assay.
7. The generalizability of the findings to other cell types and reprogramming contexts is not demonstrated and should not be assumed.