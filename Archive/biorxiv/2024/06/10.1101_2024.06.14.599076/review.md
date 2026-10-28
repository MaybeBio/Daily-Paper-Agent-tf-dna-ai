## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary figure/table legends.
- **Assessment boundary** Scientific validity, technical soundness, clarity of claims, and alignment with the stated evidence. No assessment of formatting or editorial fit.
- **Shared manuscript claim summary** The authors present an iterative deep learning-based design pipeline for synthetic human enhancers with cell type-specific activity in HepG2 and K562 cells. They train models on published MPRA and chromatin accessibility data, design and experimentally validate enhancers, retrain with new data, and demonstrate improved specificity across rounds. They report that designed enhancers exhibit condensed TFBS motif grammar, that enhancer activity correlates with TF expression at single-cell level, and that enhancers as short as 50 bp retain specificity.
- **Visible evidence base** Main text figures (Fig. 1-5), supplementary figures (S1-S11), supplementary tables (S1-S5), and detailed methods sections for model training, design, and experimental validation.
- **Missing materials affecting confidence** Raw sequencing data and code are referenced but not directly inspected. Supplementary figures and tables are described but not fully provided in the submitted material. No detailed statistical analysis tables or full model architecture diagrams were available for independent verification.

## Reviewer
- **Overall assessment** This manuscript presents a substantial and well-executed contribution to the field of synthetic enhancer design. The iterative design-build-test cycle is a clear strength, and the demonstration that small amounts of new data can dramatically improve model performance is both practically important and intellectually interesting. The combination of MPRA-based and chromatin accessibility-based approaches is thoughtful, and the single-cell MPRA adds a valuable layer of validation. The motif analyses are informative, though some claims about "condensed sequence grammar" would benefit from more formal statistical treatment. The work is technically sound overall, with a few areas where additional analysis or clarification would strengthen the conclusions.
- **Who would be interested in the results, and why** Researchers in synthetic biology, gene therapy, and regulatory genomics would find this work directly relevant. The demonstration of a practical pipeline for designing cell type-specific enhancers with limited experimental data is of immediate use to those seeking to control gene expression in specific tissues or cell types. The finding that models trained on chromatin accessibility alone can generate functional enhancers is particularly interesting for applications in cell types where MPRA data are unavailable. The single-cell MPRA approach and the analysis of TF expression correlation with enhancer activity will also appeal to those studying the cis-regulatory code and cell-to-cell variability in gene expression.
- **Major strengths**
  1. The iterative design-build-test cycle is a rigorous and compelling demonstration of how small, targeted datasets can improve deep learning models for enhancer design.
  2. The use of two independent training data types (MPRA and chromatin accessibility) and the comparison of their performance is a thoughtful and informative experimental design.
  3. The single-cell MPRA provides a unique and powerful validation layer, connecting enhancer activity to TF expression at the cellular level.
  4. The motif analyses, including ablation studies and dose-response relationships, provide mechanistic insight into the sequence features driving specificity.
  5. The demonstration that 50 bp enhancers retain specificity has practical implications for gene therapy vector design.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** No
  - **Axis** Statistical rigor
  - **Claim pointer** The claim that "condensed sequence grammar" and "higher density syntax" evolve across design rounds is central to the paper's narrative.
  - **Evidence pointer** Fig. 2A-E, motif analysis section
  - **Concern** The comparison of motif density and motif vocabulary across libraries (R0, R1, R2) is presented descriptively, but no formal statistical tests are reported for these comparisons. The claim of "condensed" grammar implies a quantitative reduction in motif diversity or an increase in density that should be tested for significance, accounting for library size and sequence length differences.
  - **Why it matters** Without statistical support, the "condensed grammar" claim remains an observation rather than a demonstrated property of the designed enhancers. This weakens the mechanistic interpretation and the generalizability of the finding.
  - **Resolution test** Provide statistical tests (e.g., permutation tests, bootstrapped confidence intervals) comparing motif density and vocabulary size between libraries, controlling for sequence length and GC content. Report effect sizes and confidence intervals.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** No
  - **Axis** Experimental validation scope
  - **Claim pointer** The claim that designed enhancers achieve "strong differential activity" and "cell type-specificity" is based on measurements in two cell lines.
  - **Evidence pointer** Fig. 1C-E, Fig. 4
  - **Concern** The study demonstrates specificity between HepG2 and K562 cells, but the broader claim of "cell type-specificity" is limited by the use of only two cell lines. It is unclear whether the designed enhancers would show similar specificity in other cell types, or whether the design process would generalize to other cell type pairs. The authors acknowledge this in the discussion, but the title and abstract may overstate the generality.
  - **Why it matters** The practical utility of these enhancers depends on their specificity in relevant therapeutic or experimental contexts, which may involve different cell types. Overstating the generality of the findings could mislead readers.
  - **Resolution test** Either temper the language in the title and abstract to reflect the two-cell-line scope, or add a small validation experiment in a third cell type to demonstrate broader specificity.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical reproducibility
  - **Claim pointer** The iterative improvement in enhancer specificity is attributed to model retraining with new data.
  - **Evidence pointer** Fig. 1F, Fig. S3, methods section on R2 design
  - **Concern** The comparison between R1 and R2 designs involves changes in both the training data and the design algorithm (e.g., addition of L2 regularization, modified loss functions). It is therefore not possible to attribute the observed improvement specifically to the iterative retraining, as opposed to the algorithmic changes. The authors note this confound in the discussion, but the main text presents the improvement as a direct result of the iterative cycle.
  - **Why it matters** The claim that "iterative retraining results in dramatic performance improvements" is a key finding, but the confounded design makes it difficult to know which component of the pipeline is responsible. This limits the actionable insight for others seeking to replicate or extend the approach.
  - **Resolution test** Perform an ablation study where R2 designs are generated with the R1 algorithm but retrained on R1 data, or with the R2 algorithm but trained only on R0 data, to isolate the contribution of retraining versus algorithmic changes.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Data quality and normalization
  - **Claim pointer** The scMPRA data are used to show correlation between enhancer activity and TF expression at single-cell level.
  - **Evidence pointer** Fig. 5, methods section on scMPRA
  - **Concern** The authors note that random barcodes were not an effective proxy for DNA copy number and therefore used pseudobulk quantifications. This is a reasonable decision, but it limits the single-cell resolution of the analysis. The correlation between enhancer activity and TF expression is computed across pseudobulk bins, not at the level of individual cells. This weakens the claim of a "single-cell level" correlation.
  - **Why it matters** The single-cell analysis is presented as a key validation of the mechanistic link between TF expression and enhancer activity. If the analysis is effectively bulk, the claim should be adjusted to avoid overstating the resolution.
  - **Resolution test** Clarify in the text that the correlation is computed on pseudobulk bins, not individual cells. If possible, perform a subset analysis on cells with high-confidence barcode assignments to demonstrate the correlation holds at higher resolution.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Fig. 1F
  - **Evidence pointer** Fig. 1F, bootstrap analysis
  - **Issue** The bootstrap analysis for small library sizes is described in the text but the figure legend is not fully clear on how the "best enhancer" is defined and how the percentages are computed.
  - **Required correction** Expand the figure legend to define "best enhancer" and describe the bootstrap procedure more explicitly.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Methods section on R1-DHS
  - **Evidence pointer** Methods, R1-DHS design
  - **Issue** The description of the GAN training and tuning process is brief. Details on the architecture, training epochs, and convergence criteria are not fully specified.
  - **Required correction** Provide additional details on the GAN architecture and training procedure, or reference a prior publication where the full details are available.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion of TP53 motif
  - **Evidence pointer** Fig. 2E, Fig. 3C
  - **Issue** The finding that TP53 motifs are enriched in HepG2-specific enhancers is interesting, but the discussion does not address the potential mechanism. TP53 is a tumor suppressor with complex regulatory roles; its role in HepG2-specific enhancer activity is not intuitive.
  - **Required correction** Add a brief discussion of potential biological explanations for TP53 motif enrichment, or acknowledge the lack of a clear mechanistic link.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Fig. 1C-E
  - **Evidence pointer** Fig. 1C-E
  - **Issue** The number of replicates and the statistical significance of the differences between designed and control enhancers are not consistently reported in the figure legends.
  - **Required correction** Add replicate numbers and significance tests to the figure legends for all panels showing enhancer activity comparisons.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Generalizability
  - **Affected element** Discussion
  - **Evidence pointer** Discussion section
  - **Issue** The discussion of future applications in gene therapy is reasonable, but it does not address potential off-target effects or the challenges of delivering these enhancers in vivo.
  - **Required correction** Add a brief note on the limitations and challenges of translating these findings to in vivo applications.

## Risk / unsupported claims
- The claim of "condensed sequence grammar" is not statistically supported as currently presented.
- The claim of "single-cell level" correlation between enhancer activity and TF expression is overstated given the pseudobulk analysis.
- The attribution of improved performance specifically to iterative retraining is confounded by simultaneous algorithmic changes.
- The generalizability of the design approach to cell types beyond HepG2 and K562 is not demonstrated and should not be implied.
- The claim that 50 bp enhancers "maintain specificity" is based on a limited number of examples and should be interpreted with caution.