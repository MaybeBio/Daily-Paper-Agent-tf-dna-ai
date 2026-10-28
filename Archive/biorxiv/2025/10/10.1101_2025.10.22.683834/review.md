## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, supplementary information descriptions) as provided.
- **Assessment boundary** Scientific soundness, methodological clarity, validity of claims relative to the evidence presented, and suitability for a high-impact general audience. The review is based solely on the provided text; figures, tables, and supplementary materials are referenced but not directly examined.
- **Shared manuscript claim summary** The authors present ProSiteHunter, a unified sequence-based framework for predicting protein-DNA, protein-RNA, protein-protein, and antibody-antigen binding sites. The framework integrates a fine-tuned protein language model (SiteT5) with a multi-source feature-fusion network combining evolutionary, geometric, and statistical features. The authors claim significant performance improvements over state-of-the-art methods, including a 39.1% average PRAUC improvement for protein-DNA/RNA/protein tasks and a 7.4% PRAUC improvement on antibody-antigen tasks. They also claim the method can identify local flexible sites complementing AlphaFold3 predictions and improve antibody-antigen interaction prediction.
- **Missing materials affecting confidence** Figures (Fig. 1-6), all Supplementary Figures, all Supplementary Tables, and the referenced GitHub repository were not provided. The evaluation protocols, exact dataset splits, and statistical significance tests are not fully described. The downstream application section lacks methodological detail for the MultisAAI integration.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational biology: the lack of a unified sequence-based predictor for multiple types of protein binding sites. The proposed framework is architecturally reasonable, combining a fine-tuned protein language model with multiple feature sources. However, the evidence presented is insufficient to fully support the strong claims made. The reported performance improvements are substantial, but the lack of access to figures, detailed statistical analysis, and a clear description of the evaluation protocol limits the ability to verify these claims. The case studies are anecdotal and the downstream application is under-described. The manuscript has potential but requires significant additional detail and analysis to establish the case for a broad, high-impact claim.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein function prediction, specifically those developing or using sequence-based methods for binding site annotation. Researchers in structural biology who use tools like AlphaFold3 and seek complementary functional annotations would also be interested. The potential application to antibody design and vaccine development could attract a broader immunology audience, but this would require stronger validation.
- **Major strengths**
    1.  The problem is well-motivated: a unified framework for multiple binding site types is a genuine gap in the field.
    2.  The architectural design is thoughtful, with a clear rationale for the three-track feature fusion (local, bidirectional, global).
    3.  The development of SiteT5, a task-specific fine-tuned language model, is a logical and potentially valuable contribution.
    4.  The inclusion of a downstream application (improving antibody-antigen interaction prediction) is a good demonstration of practical utility, though under-described.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence for performance claims
    - **Claim pointer** The abstract and results sections claim a 39.1% average improvement in PRAUC for protein-DNA/RNA/protein tasks and a 7.4% PRAUC enhancement on the antibody-antigen task over state-of-the-art methods.
    - **Evidence pointer** Results section, Figures 2 and 3, Supplementary Tables 4-7.
    - **Concern** The performance claims are the central pillar of the paper, but the evidence is not fully verifiable from the provided text. The figures are not available for inspection. The description of the evaluation protocol is incomplete. It is unclear if the reported improvements are statistically significant, what the variance across different test sets is, and whether the same train/test split was used for all methods. The choice of baseline methods is mentioned but the specific versions and hyperparameters are not detailed. The claim of a 39.1% average improvement is particularly strong and requires a robust statistical demonstration, not just a single point estimate.
    - **Why it matters** Without a rigorous and transparent evaluation, the primary claim of the paper cannot be accepted. The magnitude of the reported improvement is unusual and warrants careful scrutiny. If the evaluation is not robust, the conclusions are not reliable.
    - **Resolution test** Provide the actual figures and tables. Detail the exact evaluation protocol, including the number of runs, standard deviations, and statistical significance tests (e.g., paired t-test or Wilcoxon signed-rank test) comparing ProSiteHunter to each baseline. Clarify the data splits and ensure all methods are evaluated on identical test sets. Show the per-dataset performance to demonstrate consistency of the improvement.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Methodological clarity and reproducibility
    - **Claim pointer** The methods section describes the network architecture and training, but key details are missing.
    - **Evidence pointer** Methods section, "Network architecture", "Training", "Sequence features".
    - **Concern** The description of the model architecture is high-level and lacks specific details necessary for reproduction. For example, the exact dimensions of the hidden layers in the MLP, the number of heads in the gated attention, the specific implementation of the cross-attention layer, and the precise nature of the "gating parameters" are not fully specified. The training procedure is described, but the learning rate decay schedule is only referenced as "exponential decay policy outlined" without the specific parameters. The process for generating the MSA inputs for SiteT5 is described, but the computational cost and time for this step are not mentioned. The "protein composite features (pcf)" are mentioned but their exact composition (43-dimensional) is not fully broken down in the main text.
    - **Why it matters** For a methods-driven paper, reproducibility is paramount. The current level of detail is insufficient for another research group to implement and validate the method. This undermines the scientific contribution.
    - **Resolution test** Provide a complete and precise description of the architecture, including all layer dimensions, activation functions, and the exact formulation of the gating and cross-attention mechanisms. Provide the full learning rate schedule. Provide a detailed breakdown of all 43 features in the pcf. Consider releasing the training code and configuration files.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Validation of downstream application and case studies
    - **Claim pointer** The results section claims that ProSiteHunter improves antibody-antigen interaction prediction when integrated into MultisAAI and that it can identify local flexible sites complementing AlphaFold3.
    - **Evidence pointer** Results section, "Downstream application of ProSiteHunter", Figures 6 and 5e.
    - **Concern** The downstream application is a key part of the paper's impact, but the description is superficial. The integration of ProSiteHunter's epitope predictions into MultisAAI is not described. How are the predicted scores used? Is it a feature, a filter, or a prior? The baseline for comparison is not clear. The case study on flexible sites (Fig. 5e) is presented as a single anecdotal example. The claim that the method is "highly complementary to structure-based methods" is a strong statement based on limited evidence.
    - **Why it matters** The practical utility of the method is a major selling point. A poorly described and weakly validated downstream application does not support the claim of broad utility. The complementarity to AlphaFold3 is an interesting claim but needs a more systematic demonstration.
    - **Resolution test** Provide a detailed description of how ProSiteHunter is integrated into MultisAAI. Clearly define the baseline and the experimental setup for the comparison. For the flexible sites claim, provide a more systematic analysis, perhaps on a set of proteins with known conformational changes, rather than a single example.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity of writing
    - **Affected element** Results section, "Performance of protein-nucleic acid binding sites prediction"
    - **Evidence pointer** "It is worth noting that in order to avoid the bias caused by the imbalance of positive and negative sample data in the test set (see Supplementary Table 2 ), we introduced the area under the precision-recall curve (PRAUC) to further evaluate ProSiteHunter performance."
    - **Issue** The sentence is grammatically awkward and the logic is slightly unclear. PRAUC is a standard metric for imbalanced data, and its introduction is not a novel methodological point.
    - **Required correction** Rewrite for clarity, e.g., "Given the class imbalance in the test set (see Supplementary Table 2), we also evaluated performance using the area under the precision-recall curve (PRAUC)."

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Technical detail
    - **Affected element** Methods section, "Sequence features"
    - **Evidence pointer** "We searched for the corresponding MSAs using the protein sequences in their respective training sets for four different binding sites prediction tasks, and input these MSAs as important information into the model for 30 epochs..."
    - **Issue** The sentence is confusing. It implies the MSA is input for 30 epochs, which is not a standard way to describe training. It should be clarified that the model was trained for 30 epochs using the MSA-derived features as input.
    - **Required correction** Rephrase to: "For each of the four binding site prediction tasks, we generated MSAs from the respective training set sequences. The model was then trained for 30 epochs using these MSAs as input."

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Completeness of reporting
    - **Affected element** Methods section, "Training"
    - **Evidence pointer** "Using an NVIDIA GeForce RTX 3090 GPU to train, it takes about 1 hours to train the network."
    - **Issue** The training time is reported, but the inference time or computational cost per sequence is not mentioned. This is relevant for a tool intended for high-throughput screening.
    - **Required correction** Add a statement about inference speed, e.g., "Inference on a typical protein sequence takes X seconds on the same GPU."

- **Technical failings that need to be addressed before the case is established**
    1.  Lack of statistical significance testing for the main performance comparisons (R1-M1).
    2.  Insufficient detail in the architecture description to allow for reproduction (R1-M2).
    3.  The downstream application is not described with enough methodological detail to be evaluated (R1-M3).

## Risk / unsupported claims
- The claim of a "39.1% average improvement in PRAUC" is unsupported without access to the figures and a detailed statistical analysis.
- The claim that ProSiteHunter "is capable of identifying local flexible sites that complement AlphaFold3 predictions" is based on a single case study and is therefore not a generalizable claim from the provided evidence.
- The claim that the method "improving the accuracy of antibody-antigen interaction prediction" is not fully supported as the integration method and baseline are not described.
- The statement that the model is "highly complementary to structure-based methods" is an overstatement based on the limited evidence presented.