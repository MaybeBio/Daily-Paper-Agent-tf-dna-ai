## Review setup
- **Input scope** Full manuscript text including Significance, Results, Discussion, Methods, and Data Availability sections
- **Assessment boundary** Scientific validity, technical soundness, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors present PhytoExpr, a deep learning framework trained on approximately 0.6 million genes from 17 plant species, which predicts mRNA abundance from proximal cis-regulatory DNA sequences alone. The model also predicts species identity from sequence. The authors report that a transformer architecture with multitask learning (predicting both expression and species) achieves highest accuracy, generalizes to unseen gene families from unseen species, and that derived nucleotide importance scores correlate with conserved noncoding sequences, TFBSs, and eQTLs. They further present two design algorithms: one for rational design of cis-regulatory variants via guided small deletions, and one for de novo evolution of species-specific regulatory sequences using a genetic algorithm with PhytoExpr as selection operator. Experimental validation includes dual-luciferase assays in maize protoplasts, transient expression in Arabidopsis seedlings, and STARR-Seq in maize protoplasts.
- **Visible evidence base** Main text figures referenced (Fig. 1A–E, Fig. 2, Fig. 3A–F, Fig. 4A–I), SI figures referenced (Fig. S1–S12), Datasets S1–S4, Methods section
- **Missing materials affecting confidence** Supplementary figures and datasets not provided; figure images not available; exact performance metrics (R², MSE values) not stated numerically in text; code repository and model weights deposited but not reviewed

## Reviewer

- **Overall assessment** This manuscript presents a substantial computational resource with promising predictive performance and two potentially useful design tools. The core claim that a sequence-only model can explain over 50% of expression variation across diverse plant species is notable and, if robust, would be of broad interest. However, several technical aspects require clarification and additional validation before the case is fully established. The experimental validations are limited in scope (four maize promoters, one Arabidopsis transient assay, one STARR-Seq experiment) and do not yet demonstrate that the designed sequences function in stable transgenic contexts or that the de novo evolved sequences work as claimed in the intended species. The generalizability claim to unseen species is weakened by the Chlamydomonas exception, which the authors acknowledge but do not fully resolve. The manuscript would benefit from clearer reporting of performance metrics, additional negative controls, and more extensive experimental validation.
- **Who would be interested in the results, and why** Plant molecular biologists and crop geneticists interested in promoter engineering and cis-regulatory element discovery would find the design tools immediately relevant. Computational biologists working on regulatory genomics and deep learning for genomics would be interested in the model architecture and transfer learning findings. Synthetic biologists working on plant systems would value the de novo sequence design approach. The finding that proximal regions dominate expression prediction in plants, contrasting with human systems, is of interest to evolutionary and regulatory genomics researchers broadly.
- **Major strengths** The training dataset scale (0.6 million genes, 17 species, 6,256 RNA-seq samples) is impressive and represents a significant community resource. The gene family-aware cross-validation scheme is methodologically sound and addresses a common pitfall in regulatory genomics. The multitask learning approach (jointly predicting expression and species) is well motivated and empirically shown to improve performance. The association of importance scores with independent functional annotations (CNS, TFBS, eQTL) provides convergent evidence that the model has learned biologically meaningful features. The two design algorithms address real needs in plant biotechnology and are demonstrated with at least preliminary experimental validation.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that PhytoExpr "explained over 50% of the variation in gene expression" using only proximal cis-regulatory sequences.
- **Evidence pointer** Discussion section, first paragraph
- **Concern** The R² value of over 0.5 is stated qualitatively but no exact performance metrics are provided in the main text. It is unclear whether this R² is on the log scale or raw TPM scale, whether it is the average across all 17 species or a pooled value, and what the variance is across species. The claim that proximal regions alone explain this much variance is central to the paper's significance, yet the supporting numbers are not visible in the provided material.
- **Why it matters** Without precise metrics, readers cannot assess the practical utility of the model. A pooled R² of 0.5 could mask poor performance in individual species. The comparison to human models (ExPecto, Basenji, Enformer) that require additional epigenomic features is only meaningful if the plant model's performance is reported on comparable scales and metrics.
- **Resolution test** Provide exact R², MSE, MAE values for each species and the pooled value, with confidence intervals. State clearly the transformation applied to expression values (e.g., log10 TPM). Report performance separately for held-out gene families versus held-out species.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that PhytoExpr "generalizes well to unseen species that share evolutionary relations with the species incorporated during the initial model training."
- **Evidence pointer** Results section, "PhytoExpr Is Generalizable to Unseen Gene Families from Unseen Plant Species"
- **Concern** The Chlamydomonas reinhardtii exception is acknowledged but not resolved. The authors state that models not trained on C. reinhardtii had "no predictive accuracy" for this species, attributing this to its early divergence and unique cis-regulatory logic. However, this is a single-celled alga with fundamentally different regulatory biology, and its failure could indicate that the model has learned species-specific features rather than general cis-regulatory syntax. The claim of generalizability is therefore only supported for land plants, and the boundary of the model's applicability is not well characterized.
- **Why it matters** The paper's significance statement claims the model can make predictions on "unseen species," which is a strong claim. If the model fails on the most diverged species tested, the practical scope of the model is narrower than claimed. Understanding whether the failure is due to phylogenetic distance, genome structure differences, or regulatory grammar differences would help users know when the model can be trusted.
- **Resolution test** Provide a systematic analysis of predictive performance as a function of phylogenetic distance from the training set. Test intermediate divergences (e.g., mosses, lycophytes, ferns) to map the boundary of generalizability. Discuss whether the Chlamydomonas failure reflects fundamental regulatory differences or a limitation of the model architecture.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that importance scores derived from PhytoExpr are "enriched with conserved noncoding sequences, transcription factor binding sites, and eQTLs."
- **Evidence pointer** Results section, "PhytoExpr-Derived Nucleotide Importance Scores Associated with Conserved Noncoding Sequences, TFBSs, and cis-eQTLs"
- **Concern** The enrichment analyses are described qualitatively. No statistical tests, effect sizes, or enrichment fold values are reported in the visible text. The comparison to TFBS data relies on a single maize cistrome dataset, and the eQTL comparison uses one prior study. It is unclear whether the enrichment is specific to importance scores or would also be observed with random genomic regions matched for sequence composition.
- **Why it matters** The biological interpretability of the model depends on these enrichment results. If importance scores do not preferentially mark functional elements, the design algorithms built on them would have limited utility. The lack of quantitative reporting prevents assessment of the strength and specificity of these associations.
- **Resolution test** Report enrichment fold values with confidence intervals and P values for each annotation type. Include appropriate genomic background controls (e.g., matched random regions, shuffled importance scores). Show that enrichment is specific to high-importance nucleotides and not a property of the input regions generally.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the de novo evolved sequences from the genetic algorithm "conferred strong eGFP fluorescence signal comparable to that from the full-length CaMV 35S promoter" in Arabidopsis seedlings.
- **Evidence pointer** Results section, "PhytoExpr Facilitates Rational Design of cis-Acting Variants and De Novo Creation of Species-Specific Regulatory Sequences", Fig. 4F
- **Concern** The experimental validation of de novo designed sequences is limited to a single transient expression experiment in Arabidopsis seedlings with three replicates. The comparison to the full-length CaMV 35S promoter is qualitative (fluorescence imaging). No quantitative fluorescence measurements, statistical comparisons, or dose-response data are provided. The claim of "comparable" strength is therefore not rigorously supported.
- **Why it matters** The de novo design algorithm is a major claimed contribution. If the designed sequences are not reproducibly and quantitatively comparable to natural strong promoters, the practical utility for synthetic biology is uncertain. Transient expression can also differ substantially from stable transformation contexts.
- **Resolution test** Provide quantitative fluorescence measurements (e.g., mean fluorescence intensity, percentage of expressing cells) with statistical comparisons to positive and negative controls. Ideally, test the designed sequences in stable transgenic lines and measure transcript levels by RT-qPCR or RNA-seq.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the rational design algorithm for cis-regulatory variants can design "a single small deletion that can be easily created by the CRISPR/Cas9 system with two gRNA cassettes, or a small replacement that can be achieved by prime editing."
- **Evidence pointer** Results section, "PhytoExpr Facilitates Rational Design of cis-Acting Variants and De Novo Creation of Species-Specific Regulatory Sequences", Fig. 4A–C
- **Concern** The validation of the variant design algorithm is limited to four maize promoters tested in a dual-luciferase assay in protoplasts. The designed deletions are not compared to a comprehensive set of alternative designs (e.g., random deletions, deletions of similar size in low-importance regions). The specificity of the design algorithm is therefore not demonstrated.
- **Why it matters** Without appropriate negative controls, the observed expression changes could be due to general disruption of promoter architecture rather than targeted removal of repressive elements. The claim that the algorithm enables "rational design" requires evidence that the designed variants outperform naive approaches.
- **Resolution test** Include control deletions in regions with low importance scores, scrambled sequences, or random small deletions. Show that the designed variants produce expression changes significantly different from controls. Ideally, test multiple independent designs for the same target gene to assess reproducibility.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that "PhytoExpr has learned general cis-regulatory logic in the plant kingdom" and that it "has learned general syntax rules governing gene expression."
- **Evidence pointer** Discussion section, first paragraph
- **Concern** The claim of learning "general syntax rules" is strong and not directly supported by the presented analyses. The model's ability to predict expression on held-out genes and species demonstrates statistical learning, but it does not establish that the model has extracted interpretable regulatory grammar. The importance score analyses provide correlative evidence but do not reveal the syntax rules themselves.
- **Why it matters** The distinction between predictive accuracy and mechanistic understanding is important for the scientific contribution. If the model is purely predictive without interpretable rules, its value for understanding regulatory biology is limited, even if its practical utility for design is maintained.
- **Resolution test** Provide analyses that extract interpretable features from the model, such as position weight matrices for learned motifs, identification of syntax rules (e.g., spacing constraints between elements), or systematic perturbation analyses that reveal combinatorial logic. Alternatively, temper the claims to focus on predictive capability rather than learned grammar.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, "RNA-seq Data Collection and Processing"
- **Evidence pointer** Methods section
- **Issue** The description of the RNA-seq processing pipeline is brief. It is unclear how TPM values were calculated across samples with different library sizes, whether any batch correction was applied, and how genes with zero expression in some samples were handled.
- **Required correction** Provide additional details on TPM calculation, handling of zero counts, and any normalization steps. State the criteria for including genes in the analysis (e.g., minimum expression threshold).

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Model training and evaluation
- **Evidence pointer** Methods section, "Model Architecture and Hyperparameter Optimization"
- **Issue** The hyperparameter optimization procedure is described but the final hyperparameter values are not listed in the visible text. The random forest-based optimization approach is unusual and its convergence properties are not discussed.
- **Required correction** Provide the final hyperparameter values for both architectures in a table or supplementary file. Briefly justify the random forest optimization approach and discuss potential limitations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Fig. 1D and Fig. 2 comparisons
- **Evidence pointer** Results section, "PhytoExpr Achieved the Highest Accuracy When Employing Multispecies and Multitask Learning with a Transformer Architecture"
- **Issue** The comparisons between architectures and designs are described as "significantly" different but no statistical tests are mentioned. It is unclear whether the reported differences are based on paired tests across folds or simple mean comparisons.
- **Required correction** Report the statistical tests used for architecture and design comparisons, including the number of paired observations and the test statistic.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** STARR-Seq validation
- **Evidence pointer** Results section, "PhytoExpr Facilitates Rational Design of cis-Acting Variants and De Novo Creation of Species-Specific Regulatory Sequences", Fig. S12
- **Issue** The STARR-Seq experiment is described as having high reproducibility among biological replicates, but the correlation values are not reported. The number of evolved sequences tested (20) is stated, but the range of activities relative to controls is not quantified.
- **Required correction** Report the correlation coefficients between replicates and the distribution of activity values for evolved sequences relative to positive and negative controls.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Code and data availability
- **Evidence pointer** Data, Materials, and Software Availability section
- **Issue** The code and model weights are deposited on figshare, but there is no mention of a software package, documentation, or a user-friendly interface for applying PhytoExpr to new species or genes. The input data format and requirements are not described.
- **Required correction** Provide a brief description of how to use the deposited code, including input data format, dependencies, and expected runtime. Consider providing a simple command-line interface or notebook example.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion of Chlamydomonas failure
- **Evidence pointer** Results section, "PhytoExpr Is Generalizable to Unseen Gene Families from Unseen Plant Species"
- **Issue** The authors attribute the Chlamydomonas failure to "very early divergence and unique cis-regulatory logic" but do not provide evidence for this interpretation. Alternative explanations, such as differences in GC content, gene density, or training data quantity, are not discussed.
- **Required correction** Provide a brief analysis of potential causes for the Chlamydomonas failure, such as sequence composition differences or the number of training genes available from related species.

- **Technical failings that need to be addressed before the case is established** R1-M1 (exact performance metrics), R1-M2 (scope of generalizability claim), R1-M3 (quantitative enrichment statistics), R1-M4 (quantitative validation of de novo sequences), R1-M5 (appropriate negative controls for variant design)

- **Assessment against Nature-style criteria** 
  - Originality: The work is original in its scale and in the specific combination of multitask learning with design algorithms for plant cis-regulatory sequences. The application of a genetic algorithm with a deep learning fitness function for de novo regulatory sequence design in plants is novel. However, the underlying approach (deep learning on promoter sequences to predict expression) builds on prior work in human and yeast systems, and the incremental novelty over existing plant models should be clarified.
  - Scientific importance: The potential importance is high. If the model and design tools perform as claimed, they could accelerate promoter engineering for crop improvement and provide insights into plant cis-regulatory logic. The resource of 0.6 million genes across 17 species is valuable. However, the importance is currently tempered by the limited experimental validation and the unresolved Chlamydomonas exception.
  - Interdisciplinary readership: The work bridges computational biology, plant molecular biology, and synthetic biology. The writing is generally accessible, though some sections assume familiarity with deep learning terminology. The significance statement is clear and should attract interest from a broad readership.
  - Technical soundness: The computational methodology is largely sound, with appropriate cross-validation and consideration of gene family structure. The experimental validations are appropriate in design but limited in scope. The main technical concerns are the lack of quantitative performance reporting, the absence of negative controls in the design validations, and the incomplete characterization of the generalizability boundary.
  - Readability for nonspecialists: The manuscript is generally well-written and the logic is clear. The significance statement and figure legends are accessible. Some methods details are dense but appropriate for the target audience. The discussion of limitations is honest but could be more thorough.

- **Recommendation posture** Supportive if technical concerns are resolved. The core computational resource and design tools are potentially valuable, and the preliminary experimental validations are encouraging. However, the manuscript currently does not fully establish the strength of the claims regarding generalizability, the quantitative performance of the model, and the specificity of the design algorithms. Addressing the major concerns outlined above, particularly providing exact performance metrics, appropriate negative controls, and a more thorough characterization of the model's limitations, would substantially strengthen the case. The Chlamydomonas exception needs a more detailed analysis to define the model's scope of applicability.

## Risk / unsupported claims
- The claim that PhytoExpr "explained over 50% of the variation in gene expression" is not quantitatively supported in the visible text; exact R² values and their distribution across species are not provided.
- The claim that PhytoExpr "has learned general syntax rules governing gene expression" is an interpretation not directly demonstrated by the presented analyses.
- The claim that the de novo evolved sequences are "comparable" to the full-length CaMV 35S promoter is based on qualitative fluorescence imaging without quantitative measurements or statistical comparison.
- The claim that the rational design algorithm enables design of variants that "can be easily created by the CRISPR/Cas9 system" is plausible but not experimentally demonstrated with actual CRISPR edits.
- The generalizability to unseen species is not fully established given the Chlamydomonas failure, and the boundary of applicability is not characterized.
- The enrichment of importance scores with functional annotations is described qualitatively without statistical tests or effect sizes.
- The statement that "PhytoExpr implicitly learned the phylogenetic relationship among the species" is an inference from prediction patterns that is not directly tested.