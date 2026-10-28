## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) as provided
- **Assessment boundary** Scientific and technical soundness of the claims as supported by the supplied material
- **Shared manuscript claim summary** The authors propose PccGEO, a conditional generative adversarial network with a "fill-in-the-flank" strategy, to design functional genetic elements by optimizing flanking regions around known functional sequences. They report high success rates for constitutive and inducible E. coli promoters, and large expression increases with limited nucleotide modifications.
- **Visible evidence base** Abstract, Introduction, Methods, Results, Discussion sections. No figures, tables, or supplementary materials were provided.
- **Missing materials affecting confidence** All figures and tables are absent. Experimental data underlying the in silico and in vivo results are not visible. Code availability is stated but not assessed.

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful approach to promoter design that combines prior knowledge with generative deep learning. The core idea of preserving known functional motifs while optimizing flanking regions is reasonable and could be of interest to the synthetic biology community. However, the provided material lacks the experimental evidence needed to evaluate the central claims. The results section describes outcomes without presenting the actual data, and the methods section contains incomplete formulations and missing details. The claims of high success rates and large expression increases cannot be verified from the supplied text alone.
- **Who would be interested in the results, and why** Researchers in synthetic biology, promoter engineering, and computational biology would be interested. The approach addresses a practical problem in genetic element design, and the combination of knowledge constraints with generative models could be relevant to those working on sequence design beyond promoters.
- **Major strengths** The conceptual framing of preserving known functional regions while optimizing flanking sequences is sensible and addresses a real limitation of purely data-driven approaches. The use of a conditional GAN with attention mechanisms is technically appropriate for capturing long-range dependencies. The inclusion of in vivo validation is commendable, and the exploration of limited nucleotide modification is practically relevant.
- **Major Concerns** The absence of all figures and data makes the results impossible to evaluate. The methods section has incomplete formulations and missing details. The relationship between in silico predictions and in vivo outcomes is not clearly established. The claim that DNA shape is a learned implicit pattern is not substantiated with quantitative evidence.
- **Minor Comments** Several typographical and formatting issues are present. The discussion of limitations is brief and does not address potential failure modes. The generalizability claims extend beyond the demonstrated scope.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: the "fill-in-the-flank" strategy is a reasonable incremental contribution, but similar ideas exist in the literature. Scientific importance: promoter design is a relevant problem, but the significance of the reported improvements is unclear without data. Interdisciplinary readership: the work bridges machine learning and synthetic biology, which could attract a broad audience, but the presentation is not sufficiently accessible. Technical soundness: the methods are described at a level that prevents full assessment. Readability for nonspecialists: the manuscript assumes familiarity with both deep learning and promoter biology, and the incomplete methods reduce clarity.
- **Recommendation posture** Currently not established from the provided evidence

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence integrity
- **Claim pointer** The manuscript claims high success rates for constitutive and inducible promoter design, and large expression increases with limited nucleotide modifications.
- **Evidence pointer** Results section, Figures 2, 4, 5, 6 (not provided)
- **Concern** All figures and tables are absent from the supplied material. The results section describes outcomes such as "100% model-designed promoters showed high expression levels" and "159.3-fold increase" without presenting the underlying data, statistical details, or experimental replicates. The reader cannot assess the magnitude of effects, variability, or the validity of the statistical tests mentioned.
- **Why it matters** The central claims of the manuscript rest entirely on these experimental results. Without the data, the claims are unverifiable and the scientific contribution cannot be evaluated.
- **Resolution test** Provide all figures and tables with clear axis labels, error bars, sample sizes, and statistical test details. Ensure that the data visibly support each stated claim.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The methods section describes the loss functions and optimization objectives for the cGAN and the genetic algorithm.
- **Evidence pointer** Methods section, "Implicit patterns learning through 'fill-in-the-flank' cGANs model" and "Accurate prediction offers guidance for properties optimization"
- **Concern** The loss function equations are incomplete. The first loss function is presented without its full expression, and the L1 loss and final optimization objective are described in text but the equations are not fully written out. The genetic algorithm formulation is also incomplete. The description of the DenseLSTM architecture lacks key hyperparameters such as learning rate, batch size, training epochs, and regularization. The "fill-in-the-flank" strategy is described conceptually but the exact input-output structure of the cGAN is not specified.
- **Why it matters** Reproducibility is a core requirement for computational methods. Incomplete method descriptions prevent other researchers from implementing or building upon the approach, and they prevent reviewers from assessing the technical validity of the design choices.
- **Resolution test** Provide complete formulations of all loss functions and optimization objectives. Specify all architectural hyperparameters, training procedures, and the genetic algorithm configuration. Clarify the exact input and output formats for the cGAN.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim substantiation
- **Claim pointer** The manuscript claims that PccGEO can learn implicit patterns such as DNA shape, and that these patterns matter for gene expression.
- **Evidence pointer** Results section, "Implicit patterns matter to the gene expression could be learned by PccGEO", Figure 3 (not provided)
- **Concern** The claim that DNA shape is a learned implicit pattern is based on a UMAP visualization of predicted DNA shape features. The text states that "half of them were directly moved from the right to the left" but does not provide quantitative metrics, statistical tests, or a clear definition of what "moved" means in this context. The relationship between the UMAP clustering and the actual expression improvements is not established.
- **Why it matters** The manuscript positions the learning of implicit patterns as a key contribution. If this claim is not rigorously supported, the conceptual novelty of the work is weakened.
- **Resolution test** Provide quantitative analysis showing that the designed promoters differ from controls in DNA shape features, and that these differences correlate with expression improvements. Include statistical tests and effect sizes.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design
- **Claim pointer** The manuscript claims that inducible promoters designed by PccGEO retain LacI-DNA interaction and show higher induced expression levels compared with non-optimized controls.
- **Evidence pointer** Results section, "Strong knowledge driven inducible promoters design with implicit patterns", Figure 5 (not provided)
- **Concern** The description of the inducible promoter experiments is incomplete. The text states that the lacO motif was inserted at a specific position and that the flanking regions were optimized, but the control conditions are not fully described. It is unclear whether the controls had the same lacO insertion or only the original promoter. The induction conditions, the concentration of IPTG, and the timing of measurements are not specified. The claim of "91.6% success" needs clarification on how success was defined.
- **Why it matters** Inducible promoter function depends critically on the position and context of the operator sequence. Without clear controls and experimental details, the claim that the flanking region optimization improves inducible promoter performance cannot be evaluated.
- **Resolution test** Provide full experimental details including control constructs, induction protocols, measurement times, and a clear definition of success. Show that the improved performance is specifically due to flanking region optimization rather than other factors.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The abstract states "more than 91.6% chance of success" while the introduction states "up to 91.6%". These numbers are inconsistent and should be reconciled.
- **Required correction** Use consistent numbers throughout the manuscript.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Readability
- **Affected element** Methods section
- **Evidence pointer** Methods section, "Problem definition"
- **Issue** The problem definition section contains incomplete sentences and unclear notation. The equation for the optimization objective is not fully presented, and the notation for the prior regions is not clearly defined.
- **Required correction** Rewrite the problem definition section with complete sentences and clearly defined notation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical clarity
- **Affected element** Methods section
- **Evidence pointer** Methods section, "Accurate prediction offers guidance for properties optimization"
- **Issue** The description of the DenseLSTM architecture is brief. The number of LSTM layers, the hidden state size, and the dropout rates are not specified.
- **Required correction** Provide a complete architectural description.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Generalization
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion claims the method could be generalized to eukaryotic elements, but no evidence or reasoning is provided for this claim.
- **Required correction** Either provide supporting evidence or temper the claim.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Availability statement
- **Evidence pointer** Abstract
- **Issue** The code repository is listed, but it is not clear whether the trained models and the experimental datasets are also available.
- **Required correction** Clarify what is included in the repository.

## Risk / unsupported claims
- The claim that PccGEO achieves "100% model-designed promoters showed high expression levels" is unsupported without the underlying data.
- The claim of "159.3-fold increase with 10-bp modification" is unsupported without the underlying data.
- The claim that DNA shape is a learned implicit pattern is not quantitatively substantiated.
- The claim that the method could generalize to eukaryotic elements is speculative and unsupported.
- The claim that "implicit patterns are important in the design of functional gene elements" is a broad conclusion drawn from a single promoter system and limited experiments.
- The statistical significance of the reported improvements cannot be assessed without the data.