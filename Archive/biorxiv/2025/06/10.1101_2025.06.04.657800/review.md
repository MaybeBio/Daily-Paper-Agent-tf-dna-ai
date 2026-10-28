## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, data availability) as provided
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and reproducibility as presented in the provided text
- **Shared manuscript claim summary** The authors present PBCNet2.0, a cartesian tensor-based Siamese neural network for protein-ligand relative binding affinity prediction. They claim zero-shot performance comparable to physics-based simulations, a 718% speedup in binding affinity optimization with 41% resource reduction, intrinsic understanding of protein-ligand interactions, emergent capability to predict mutation-induced affinity changes, and prospective validation on ENPP1 and ALDH1B1 with 83% hit rate for critical binding residues.
- **Visible evidence base** Results sections 2.1-2.5, figures referenced (Fig. 1-5), supplementary figures and data referenced, methods sections 4.1-4.5
- **Missing materials affecting confidence** Actual figure content, supplementary data files, training details (hyperparameters, loss curves), baseline model configurations, statistical significance tests, code implementation details, and full experimental protocols

## Reviewer
- **Overall assessment** The manuscript presents a technically sophisticated deep learning architecture for relative binding affinity prediction with an impressively large training dataset. The core methodological advance, the use of cartesian tensor-based equivariant graph neural networks in a Siamese architecture, is well motivated and represents a meaningful step beyond the authors' prior PBCNet work. The zero-shot performance claims, if substantiated by the data, would be of considerable interest to the computational drug discovery community. However, the manuscript as presented has several significant gaps in evidence quality and reporting that prevent full assessment of the claims. The prospective validation studies are compelling but limited in scope, and the emergent mutation prediction capability, while intriguing, requires more rigorous statistical treatment and comparison to established methods. The writing is generally clear but some technical details are underspecified.

- **Who would be interested in the results, and why** Computational chemists and structural biologists working on ligand binding affinity prediction, drug discovery researchers interested in lead optimization and resistance mutation prediction, and machine learning researchers developing equivariant neural networks for molecular applications. The demonstrated capability to predict mutation-induced affinity changes without explicit training on such data would be of particular interest to those studying drug resistance mechanisms.

- **Major strengths** 1) The scale of the training dataset (8.6 million pairs) is a substantial advance over prior work and enables meaningful evaluation of scaling laws in this domain. 2) The architectural choice of cartesian tensor-based equivariant networks is well justified and represents a principled approach to encoding 3D structural information. 3) The prospective experimental validation on ENPP1 and ALDH1B1 provides real-world evidence beyond retrospective benchmarks. 4) The interpretability analyses, particularly for fluorine interactions and mutation effects, offer mechanistic insight into model behavior. 5) The comparison to physics-based methods like FEP+ in zero-shot settings addresses a practically important question.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** "PBCNet2.0 achieves zero-shot performance comparable to computationally intensive physics-based simulations"
- **Evidence pointer** Section 2.2, Figure 2a, Supplementary Figure 1
- **Concern** The claim of parity with FEP+ is based on correlation coefficients (rho = 0.67 vs 0.70) and the statement that the difference is not statistically significant (p = 0.39). However, the manuscript does not report confidence intervals for these correlations, the number of compounds per series, or the statistical power of the comparison. More critically, the comparison to FEP+ appears to use published results rather than running FEP+ on the same systems with identical protocols. The authors should provide a more rigorous statistical framework, including per-series breakdowns, error bars, and a clear statement of what "comparable" means in practical terms. Additionally, the conversion of FEP+ free energies to pIC50 values involves assumptions (non-competitive binding) that should be validated.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "PBCNet2.0 speeds up binding affinity optimization by 718% while reducing resource use by 41%"
- **Evidence pointer** Section 2.2, Figure 2c, Supplementary Data 3
- **Concern** The prioritization experiment metrics (advantage order, advantage ratio, efficiency improvement ratio) are not standard in the field and are insufficiently defined. The manuscript states these "matched our previous work" but does not provide the formulas or explain how they should be interpreted. The 718% speedup figure is striking and requires careful explanation of the baseline, the computational environment, and whether this is a fair comparison. The resource reduction of 41% is also unclear in what resources are being measured (GPU hours, CPU time, wall clock time, cost). Without transparent definitions and raw data, these claims cannot be independently verified.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** "PBCNet2.0 exhibits an emergent capability to predict affinity changes induced by binding residue variations"
- **Evidence pointer** Section 2.4, Figure 4, Supplementary Data 6
- **Concern** The mutation prediction results show an average Spearman correlation of 0.53 across 8 targets, but the range of performance is wide (from 0.26 for PfDFHR-TS to 0.76 for tACE). The manuscript does not provide confidence intervals, per-target sample sizes, or an analysis of why performance varies so substantially across targets. The comparison to other methods is incomplete: while several methods show negative correlations, the authors do not report whether these differences are statistically significant. The claim of "emergent" capability is also problematic, as the model was trained on pairs of ligands binding to the same protein, and the generalization to mutations may reflect learning of general interaction patterns rather than a truly emergent property. The authors should provide a more nuanced discussion of what this capability means mechanistically.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "PBCNet2.0 intrinsically comprehends protein-ligand interactions, showing high sensitivity to intermolecular interactions and exceptional perception of spatial geometric information"
- **Evidence pointer** Section 2.3, Figure 3, Supplementary Figures 4-7
- **Concern** The ablation study and geometric perturbation experiments are described qualitatively but the quantitative results are not fully reported in the main text. The manuscript states that removing interaction edges leads to performance decline and that angular perturbations reduce weights, but does not provide the magnitude of these effects, statistical significance, or comparison across different interaction types. The F-Opt benchmark of 10 compound pairs is very small, and the claim of "exceptional perception" based on this limited set is not well supported. The interpretability analysis showing high weights for fluorine interactions is suggestive but does not establish that the model has learned the underlying physics rather than correlational patterns.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** "Trained on 8.6 million protein-ligand complex structure pairs"
- **Evidence pointer** Section 4.1, Supplementary Figure 12
- **Concern** The data processing pipeline is described at a high level but lacks critical details for reproducibility. The manuscript states that docking was performed with Glide but does not specify the exact protocol, scoring function settings, or quality control thresholds. The clustering approach for defining chemical series (Tanimoto similarity of 0.5) is mentioned but the implementation details are not provided. The balance between different protein targets, the distribution of affinity values, and the train/validation/test splits are not described. Given that the dataset is a key contribution, the authors should provide a more detailed data card or refer to a separate publication with full details.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract claims "transformative tool for developing pharmacological probes for all human proteins" which is an overstatement given the limited prospective validation on two targets and the known challenges of generalization across the human proteome.
- **Required correction** Soften the claim to reflect the demonstrated scope, such as "a promising tool for accelerating pharmacological probe development."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 2.1, model architecture
- **Evidence pointer** Section 2.1, Figure 1b
- **Issue** The description of the anti-symmetry enforcement (f(delta x) = -f(-delta x)) is unclear. The manuscript states that -delta x is incorporated during training, but does not explain whether this is a hard constraint on the architecture or a data augmentation strategy, and how this affects the model's capacity.
- **Required correction** Clarify whether anti-symmetry is architecturally enforced or learned, and discuss any trade-offs.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Evidence quality
- **Affected element** Section 2.5, prospective validation
- **Evidence pointer** Section 2.5, Figure 5
- **Issue** The prospective validation on ENPP1 and ALDH1B1 is described with limited quantitative detail. For the ALDH1B1 alanine scanning, the manuscript reports a 5/6 success rate but does not provide the predicted versus experimental values for each mutation, nor the criteria for defining "significant impairment."
- **Required correction** Provide a table with per-mutation predicted and experimental values, and define the threshold for functional significance.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 4.2, model implementation
- **Evidence pointer** Section 4.2
- **Issue** The manuscript references equations (Equation 1-5) but the actual equations are not included in the provided text. This makes it impossible to assess the mathematical correctness of the architecture.
- **Required correction** Ensure all equations are included in the final manuscript and are properly numbered and referenced.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2, baseline comparisons
- **Evidence pointer** Section 2.2, Figure 2a
- **Issue** The manuscript states that PBCNet2.0 was compared against twelve baseline methods but does not provide a summary table of all methods' performance across all metrics in the main text. The reader is referred to supplementary data, which is not available for review.
- **Required correction** Include a summary table of all baseline comparisons in the main text or a clearly accessible supplementary table.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 4.1, data processing
- **Evidence pointer** Section 4.1
- **Issue** The manuscript mentions that water molecules forming more than three hydrogen bonds with ligand or receptor atoms were preserved during protein preparation. This is an unusual criterion and the rationale is not explained.
- **Required correction** Justify this choice or cite precedent for this water retention criterion.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3, Discussion
- **Evidence pointer** Section 3
- **Issue** The discussion of limitations focuses primarily on static structure dependence but does not address potential issues with the training data distribution, such as bias toward certain protein families or ligand chemotypes, which could affect generalization claims.
- **Required correction** Add a discussion of potential dataset biases and their implications for the stated goal of covering all human proteins.

- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical rigor of FEP+ comparison), R1-M2 (undefined prioritization metrics), R1-M3 (incomplete mutation prediction analysis), R1-M4 (insufficient quantitative reporting of ablation and perturbation studies), R1-M5 (incomplete data pipeline description)

- **Assessment against Nature-style criteria** 
  - Originality: The cartesian tensor-based equivariant architecture applied to relative binding affinity prediction in a Siamese framework represents a novel combination, though it builds directly on prior work by the same group and on established equivariant network literature. The emergent mutation prediction capability is a distinctive finding.
  - Scientific importance: If the claims are fully substantiated, the work would be important for computational drug discovery, particularly the demonstration of zero-shot performance approaching FEP+ and the potential for rapid resistance mutation identification. The scale of the training dataset is itself a contribution.
  - Interdisciplinary readership: The work bridges machine learning, structural biology, and medicinal chemistry. The writing is generally accessible, but the methods section assumes significant expertise in equivariant neural networks. The prospective validation studies help make the work tangible for experimentalists.
  - Technical soundness: The architectural choices are well motivated and the evaluation framework is thoughtful, but the manuscript has significant gaps in statistical reporting, metric definitions, and reproducibility details that currently prevent full assessment.
  - Readability for nonspecialists: The introduction and results are reasonably accessible, but the methods section is dense and would benefit from additional context for readers without deep expertise in geometric deep learning.

- **Recommendation posture** Supportive if technical concerns are resolved. The core ideas are promising and the prospective validation is a strength, but the manuscript requires substantial revision to address the statistical rigor, metric transparency, and reproducibility gaps identified above. The claims of parity with FEP+ and emergent mutation prediction need stronger evidence before the case is fully established.

## Risk / unsupported claims
- The claim of "transformative tool for developing pharmacological probes for all human proteins" is not supported by the evidence presented, which covers only two prospective targets.
- The claim of "comparable" performance to FEP+ is not fully supported without confidence intervals and per-series analysis.
- The "emergent" nature of the mutation prediction capability is asserted but not rigorously demonstrated as distinct from learned interaction patterns.
- The 718% speedup and 41% resource reduction figures cannot be evaluated without clear definitions of the metrics and experimental setup.
- The claim that PBCNet2.0 "intrinsically comprehends" protein-ligand interactions is an interpretive overreach based on the limited interpretability analyses presented.
- The assertion that the model has "exceptional perception of spatial geometric information" is based on a small benchmark (10 compound pairs) and limited perturbation experiments.