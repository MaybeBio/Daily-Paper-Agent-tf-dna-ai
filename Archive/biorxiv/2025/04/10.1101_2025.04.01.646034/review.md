## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, code/data availability) as provided
- **Assessment boundary** Scientific claims, methodological soundness, interpretability analyses, and evidence alignment as presented in the supplied text
- **Shared manuscript claim summary** The authors present DeepShape, a deep convolutional neural network that augments one-hot encoded DNA sequence with five DNA shape features (MGW, HelT, ProT, Roll, EP) to predict TF binding and other chromatin features. They report comparable or slightly improved predictive performance relative to a sequence-only DeeperDeepSEA baseline, and argue that explicit shape modeling enhances interpretability, revealing regulatory patterns not apparent from sequence alone. They support this with permutation analyses, DeepLIFT attributions, TF-MoDISco motif discovery, and a case study on Myc-Max and MafK.
- **Visible evidence base** Main text figures referenced (Fig. 1a–c, Fig. 2a–b, Fig. 3, Fig. 4a–f, Fig. 5a–c), supplementary figures (Supp. fig. 1, 2, 3), supplementary tables (Supp. table 1, 2), methods descriptions, and code/data availability statements
- **Missing materials affecting confidence** Actual figure images, supplementary figures and tables, hyperparameter search details, full model architecture specifications, training hyperparameters, exact dataset splits, TF-MoDISco parameters, statistical test details, and code implementation were not provided in the supplied text

## Reviewer

- **Overall assessment** The manuscript addresses a relevant and timely question in genomic deep learning, namely whether explicit incorporation of DNA shape features can improve both predictive performance and interpretability of TF binding models. The authors present a reasonable architectural extension of an established model and provide a range of interpretability analyses. However, the central claims of improved interpretability and biological insight are supported by descriptive observations rather than rigorous quantitative validation. The predictive performance gains over the sequence-only baseline are marginal, and the manuscript does not establish that the shape branch captures information that could not be learned implicitly by a sequence-only model. The Myc-Max and MafK case studies are illustrative but lack statistical rigor and comparison against appropriate controls. The manuscript would benefit from clearer hypothesis testing, quantitative comparisons of interpretability outputs, and validation of the biological claims against independent experimental data.

- **Who would be interested in the results, and why** Researchers working on interpretable deep learning for genomics, particularly those studying TF-DNA binding mechanisms, cis-regulatory code modeling, and the role of DNA shape in protein-DNA recognition. The manuscript may also be of interest to method developers seeking to incorporate biophysical features into neural network architectures for regulatory genomics, and to experimental biologists studying shape-readout mechanisms in TF binding.

- **Major strengths** The manuscript addresses an important gap in genomic deep learning, namely the limited interpretability of sequence-only models. The architectural design of separate sequence and shape branches is conceptually clean and allows for independent attribution analysis. The use of established interpretability tools (DeepLIFT, TF-MoDISco) is appropriate. The inclusion of a broad benchmark across 919 targets and multiple cell types provides a solid foundation for evaluating predictive performance. The Myc-Max case study is a thoughtful choice given prior literature on shape-mediated binding specificity. The authors are transparent about limitations, including the static nature of shape features and the diffuse attribution patterns.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The manuscript claims that incorporating DNA shape features "can improve the identification of regulatory elements" and that DeepShape provides "a more nuanced understanding of genomic function and regulation."
- **Evidence pointer** Results section, Fig. 1b
- **Concern** The reported predictive performance improvement of DeepShape over the sequence-only DeeperDeepSEA baseline is marginal (average AUROC 0.929 vs 0.925; average AUPRC 0.379 vs 0.367). The manuscript does not report whether these differences are statistically significant across the six chromosome splits, nor does it provide per-target or per-category breakdowns. The claim of "improved identification of regulatory elements" is therefore not quantitatively established. Furthermore, the authors note that modifying DeeperDeepSEA's hyperparameters to match DeepShape also improved the sequence-only baseline, confounding the attribution of any performance gain to the shape features themselves.
- **Why it matters** The central premise of the manuscript is that shape features add value beyond sequence. Without statistical testing and appropriate ablations, the observed performance differences could be due to noise, hyperparameter changes, or architectural differences rather than the shape inputs.
- **Resolution test** Provide statistical significance testing (e.g., paired tests across splits) for the performance differences, report per-target and per-category results, and include an ablation where the shape branch is removed but all other hyperparameters are held constant. If the performance gain is not significant, the claim should be revised to focus on interpretability rather than predictive improvement.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretability validation
- **Claim pointer** The manuscript claims that DeepLIFT attributions and TF-MoDISco shape motifs "enhance the interpretability of the model and provide additional insights into regulatory patterns not captured by sequence alone."
- **Evidence pointer** Results section, Fig. 2, Fig. 3, Fig. 4, Supp. table 1
- **Concern** The interpretability analyses are largely descriptive. The KS statistics in Fig. 2b show variation in shape feature distributions between motif and background, but no statistical testing is reported. The Myc-Max activation analysis (Fig. 3) shows qualitative differences between sequence and shape branch activations, but no quantitative comparison or null model is provided. The MafK ProT motif analysis (Fig. 4) reports a correlation between ProT motif co-occurrence and ChIP-seq signal, but the effect size, statistical significance, and confounding factors (e.g., sequence motif strength, genomic context) are not addressed. The claim that shape features provide "additional insights" requires validation that these insights are not redundant with sequence information and that they correspond to real biological mechanisms.
- **Why it matters** Interpretability claims are only meaningful if the attributions are reliable and the discovered patterns are biologically validated. Without statistical rigor and appropriate controls, the observed patterns could be artifacts of the attribution method or the model's architecture.
- **Resolution test** Add statistical testing for the KS statistics and the ChIP-seq signal comparison (e.g., permutation tests or bootstrapping). Include a null model where shape features are permuted or replaced with random values to demonstrate that the interpretability outputs are specific to real shape information. Validate the MafK ProT motif finding against independent experimental data (e.g., binding assays with mutated flanking regions) or at least against a larger set of TF targets.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of shape feature integration
- **Claim pointer** The manuscript states that "whole genome shape features were generated for five structural attributes of DNA" using DNAShapeR, and that these were input to the model alongside sequence.
- **Evidence pointer** Methods section, Shape inputs
- **Concern** The methods description for shape feature generation and integration is incomplete. It is unclear how the five shape features were aligned with the one-hot encoded sequence, how gaps were filled (beyond stating mean imputation), whether the shape features were normalized or scaled, and how the shape branch of the network processed these continuous values. The manuscript also does not specify whether the shape features were treated as fixed inputs or learned representations. The choice of DNAShapeR, which provides predicted rather than experimentally measured shape values, introduces a potential circularity if the model is learning to predict binding from predicted structural features that are themselves derived from sequence.
- **Why it matters** Reproducibility and the validity of the interpretability analyses depend on a complete and precise description of how shape features were computed, preprocessed, and integrated. If the shape features are largely redundant with sequence, the interpretability claims are weakened.
- **Resolution test** Provide a detailed description of the shape feature pipeline, including alignment, normalization, imputation, and the exact architecture of the shape branch. Include an analysis of the correlation between shape features and sequence features to assess redundancy. Consider using experimentally derived shape data (e.g., from molecular dynamics simulations) for a subset of targets to validate the predicted shape features.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and scope of claims
- **Claim pointer** The manuscript claims that DeepShape "can improve the identification of regulatory elements" and that the approach is applicable to "TF binding and other molecular phenotypes."
- **Evidence pointer** Results section, Fig. 1b, Discussion
- **Concern** The benchmark includes 919 targets, but the manuscript focuses on TF binding. The performance for open chromatin and histone mark targets is not discussed in detail, and it is unclear whether the shape features provide any benefit for these target types. The claim of general applicability to "other molecular phenotypes" is therefore not supported by the presented evidence. Additionally, the manuscript does not address whether the shape features are useful across diverse TF families with different DNA binding domains, which would be important for generalizability.
- **Why it matters** The scope of the claims should match the evidence. If the shape features only benefit a subset of targets, the manuscript should specify this and discuss the implications.
- **Resolution test** Report performance separately for TF, open chromatin, and histone mark targets. Analyze whether the benefit of shape features varies by TF family or DNA binding domain. Revise the claims to reflect the actual scope of the findings.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that the model "provides an additional axis for model interpretability" but does not specify what this axis is or how it is accessed by users.
- **Required correction** Briefly describe the interpretability outputs (e.g., shape feature attributions, shape motifs) in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, Model design
- **Evidence pointer** Methods section, Model design
- **Issue** The hyperparameter search is referenced but not described. The criteria for selecting the final hyperparameters (filter size, number of kernels) are not stated.
- **Required correction** Provide a brief description of the hyperparameter search space, optimization criterion, and the selected values.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, Model interpretability
- **Evidence pointer** Fig. 2b
- **Issue** The KS statistics are described as showing "variation" across targets, but no measure of uncertainty or significance is provided.
- **Required correction** Report p-values or confidence intervals for the KS statistics, or state that these are descriptive only.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Biological interpretation
- **Affected element** Results, MafK analysis
- **Evidence pointer** Fig. 4e, Supp. table 2
- **Issue** The claim that the ProT motif "modulates binding affinity" is based on ChIP-seq signal differences, which are an indirect measure of affinity. The manuscript does not discuss potential confounding factors such as chromatin accessibility or co-factor binding.
- **Required correction** Acknowledge the indirect nature of ChIP-seq signal as a proxy for affinity and discuss potential confounders.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction, Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The manuscript cites prior work on shape motifs and shape-readout but does not discuss how DeepShape's interpretability outputs compare to those from existing shape-aware models or sequence-only models with attribution methods.
- **Required correction** Add a brief comparison to prior interpretability approaches in genomic deep learning.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Code and data availability
- **Evidence pointer** Code and data availability
- **Issue** The statement that model weights are available on Hugging Face is useful, but it is unclear whether the trained models for all 919 targets are included or only a subset.
- **Required correction** Clarify the scope of the released model weights.

## Risk / unsupported claims
- The claim that DeepShape "can improve the identification of regulatory elements" is not statistically supported given the marginal performance differences and lack of significance testing.
- The claim that shape features provide "additional insights into regulatory patterns not captured by sequence alone" is not rigorously validated; the interpretability analyses are descriptive and lack appropriate controls.
- The claim that the ProT motif "modulates binding affinity" for MafK is based on indirect evidence (ChIP-seq signal) without addressing confounders or providing independent validation.
- The generalizability claim to "other molecular phenotypes" is not supported by the presented evidence, as the manuscript focuses on TF binding and does not analyze open chromatin or histone mark targets in detail.
- The biological interpretation of the Myc-Max activation analysis is speculative and not quantitatively compared against a null model or alternative explanations.