## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided.
- **Assessment boundary** Scientific validity, methodological soundness, clarity, and support of claims based solely on the supplied text. No external data, code, or supplementary materials were accessed.
- **Shared manuscript claim summary** The authors introduce PocketCFDM, a generative diffusion model for molecular docking, trained on a dataset augmented with artificially generated binding pockets that mimic statistical patterns of non-bond interactions from real protein-ligand complexes. They report improved performance over DiffDock in terms of non-bond interaction quality, steric clashes, and inference speed.
- **Visible evidence base** Text descriptions of methods and results, including references to Figures 2-9, Tables 1-5, and Figure S1/S2 in the Supporting Information. No actual data values, figures, or tables are visible in the provided material.
- **Missing materials affecting confidence** All figures, tables, and supplementary materials are referenced but not provided. Specific numerical results, statistical analyses, and model architecture details are absent. The scoring function equation is mentioned but not shown. No code or data availability verification was possible.

## Reviewer
- **Overall assessment** The manuscript presents a potentially interesting data augmentation strategy for training diffusion models in molecular docking, addressing a recognized limitation of limited experimental training data. The core idea, generating artificial binding pockets that statistically mimic real non-bond interactions, is conceptually sound and could be of value to the computational drug discovery community. However, the current manuscript, as provided, lacks the necessary detail and evidence to fully evaluate the claims. The methods are described at a high level, and the results are presented qualitatively without numerical data or statistical support. The comparison with DiffDock, while promising, is not substantiated with concrete metrics. The manuscript would benefit from a more rigorous presentation of the methodology, including algorithmic details, and a comprehensive quantitative evaluation.
- **Who would be interested in the results, and why** Researchers in computational drug discovery, specifically those working on molecular docking, structure-based virtual screening, and the application of generative models (e.g., diffusion models, GNNs) to protein-ligand interactions. The data augmentation approach could be of interest to machine learning practitioners seeking to address data scarcity in geometric deep learning for chemistry. The focus on improving non-bond interaction quality and reducing steric clashes is directly relevant to practical docking applications.
- **Major strengths** 1. The manuscript addresses a significant and well-recognized problem in the field: the limited amount of experimental training data for ML-based docking models. 2. The proposed data augmentation strategy is novel and conceptually well-motivated, based on the idea of sampling combinations of known favorable interactions. 3. The work includes a practical comparison with a state-of-the-art model (DiffDock), which is valuable. 4. The authors have made the inference code and model weights publicly available, which is commendable for reproducibility.
- **Major Concerns**
- **Minor Comments**
- **Technical failings that need to be addressed before the case is established** The primary technical failing is the lack of quantitative evidence. The manuscript describes results but does not provide the actual data (e.g., RMSD values, percentages, statistical significance) that would support the claims of improved performance. The methods section is insufficiently detailed to allow replication, particularly the artificial pocket generation algorithm and the scoring function. The comparison with DiffDock is presented without the necessary metrics to be convincing.
- **Assessment against Nature-style criteria** **Originality:** The concept of generating artificial binding pockets for data augmentation is original and addresses a key bottleneck. **Scientific importance:** If validated, the approach could improve the training of docking models, which is of high importance to drug discovery. However, the current evidence is insufficient to establish this importance. **Interdisciplinary readership:** The topic is relevant to chemistry, biology, and computer science, but the presentation is likely too specialized for a broad Nature readership. **Technical soundness:** The technical soundness cannot be fully assessed due to missing methodological details and quantitative results. The described approach is plausible but not rigorously demonstrated. **Readability for nonspecialists:** The manuscript is written for a specialist audience and would be challenging for nonspecialists to follow without more context and clearer explanations of the methods and significance.
- **Recommendation posture** Currently not established from the provided evidence. The core idea is promising, but the manuscript requires substantial revision to provide the necessary quantitative data, methodological detail, and a more rigorous comparison to support its claims. I would be supportive if these technical concerns are resolved.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence
- **Claim pointer** The authors claim that PocketCFDM outperforms DiffDock in terms of non-bond interaction quality, number of steric clashes, and inference speed.
- **Evidence pointer** Results section, Table 5, location not provided.
- **Concern** The claim of superiority over DiffDock is a central finding, but the provided text does not include the actual numerical results from Table 5 or any statistical analysis. Without specific values (e.g., median RMSD, percentage of clashes, time measurements) and an indication of variance or significance, this claim is unsupported.
- **Why it matters** The primary conclusion of the manuscript rests on this comparative performance. Without quantitative evidence, the reader cannot assess the magnitude of the improvement or its practical relevance.
- **Resolution test** Provide the full data from Table 5, including all metrics for both models, with appropriate measures of central tendency and dispersion. Include a statistical test (e.g., paired t-test, Wilcoxon) to demonstrate the significance of any differences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The authors describe an algorithm for generating artificial binding pockets that mimic statistical patterns of non-bond interactions from real protein-ligand complexes.
- **Evidence pointer** Methods section, "Artificial pockets generation", location not provided.
- **Concern** The description of the algorithm is too high-level to be replicable. Key details are missing, such as: the exact definition of "features" for each interaction type, the specific probability distributions used and how they were estimated, the criteria for "compatible" building blocks, the procedure for sampling distances and angles, and the exact rules for avoiding steric clashes and unfavorable interactions. The statement that "no further tuning of the algorithm was required" is not supported by any quantitative comparison.
- **Why it matters** A central contribution of the paper is the data augmentation method. If the method cannot be understood or replicated from the description, its validity and utility cannot be assessed.
- **Resolution test** Provide a detailed, step-by-step algorithmic description, including pseudocode or a formal specification. Include the exact statistical distributions used and how they were derived from the PDBbind data. Show a quantitative comparison of the distributions of interactions in artificial vs. real pockets, with appropriate statistical tests.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The authors state that a "non-covalent interaction score" is used for scoring and ranking generated poses, and that this score is computed using a formula involving F_unfav-atoms and D_clash.
- **Evidence pointer** Methods section, "Model training and inference", location not provided.
- **Concern** The scoring function is a critical component of the model's performance, as it determines which poses are selected. However, the equation is not shown, and the description is incomplete. The coefficients are said to be "adjusted empirically by visual inspection," which is not a rigorous or reproducible method.
- **Why it matters** The choice of scoring function directly impacts the reported results, particularly the comparison with DiffDock, which uses a different scoring mechanism. Without a clear definition, the results cannot be interpreted or compared fairly.
- **Resolution test** Provide the full equation for the scoring function. Describe the process for setting the coefficients, including the range of values tested and the criteria used for selection. Ideally, use a more objective method, such as cross-validation on a validation set.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Evidence
- **Claim pointer** The authors report that training with artificial data led to enhancements in RMSD and Centroid Distance metrics compared to training on experimental data only.
- **Evidence pointer** Results section, Table 2, location not provided.
- **Concern** The text states that improvements were observed, but the actual values are not provided. It is also unclear if the differences are statistically significant. The observation that "training of the artificial dataset is superior to the combined dataset in certain metrics" is vague and not quantified.
- **Why it matters** This is a key result supporting the value of the data augmentation approach. Without specific numbers and significance testing, the reader cannot determine the reliability or magnitude of the effect.
- **Resolution test** Present the full data from Table 2, including all metrics for all three training conditions. Include statistical tests to compare the conditions and report effect sizes.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided.
- **Issue** The abstract states that the model "surpassed DiffDock in terms of non-bond interaction quality, number of steric clashes, and inference speed." This is a strong claim that is not qualified in the abstract.
- **Required correction** Consider softening the claim in the abstract, e.g., "showed improved performance in our evaluation" or "demonstrated potential to outperform," to better reflect the preliminary nature of the results.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction
- **Evidence pointer** Introduction, location not provided.
- **Issue** The statement "there are only 10.270 high-quality complexes" uses a period instead of a comma as a thousands separator, which is inconsistent with standard English usage.
- **Required correction** Change "10.270" to "10,270".

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Methods, "Protein and ligand preprocessing"
- **Evidence pointer** Methods section, location not provided.
- **Issue** The text mentions "The source code of the preprocessing module is available: https://github.com/vtarasv/rai-chem.git". It is unclear if this is the same repository as the main code or a separate one.
- **Required correction** Clarify the relationship between the two repositories, or if they are separate, explain why.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "Statistics of non-bond interactions"
- **Evidence pointer** Results section, location not provided.
- **Issue** The text refers to "Figure 6" for hydrogen bonds, but the preceding text refers to "Figure 2" for hydrophobic interactions, "Figure 3" for pi stacking, and "Figure 4" for amide-pi. The figure numbering appears to skip Figure 5.
- **Required correction** Check the figure numbering and ensure all figures are referenced in order.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "Comparison with DiffDock"
- **Evidence pointer** Results section, location not provided.
- **Issue** The text mentions "the diversity observed within anticipated poses" and reports a median RMSD value of 2.59 for PocketCFDM and 1.29 for DiffDock. It is unclear what this metric represents (e.g., diversity among top-5 poses?).
- **Required correction** Define the diversity metric clearly and explain how it was calculated.

## Risk / unsupported claims
- The claim that PocketCFDM "surpassed DiffDock" is unsupported without the actual numerical data from Table 5.
- The claim that artificial pockets "mimic" real pockets is not quantitatively demonstrated; the text only states a "good match" without providing data.
- The claim that the model's performance is "significantly enhanced" by artificial data is not supported by statistical evidence.
- The description of the scoring function is incomplete, making its role in the reported results unverifiable.
- The generalizability of the approach to other targets or ligand types is not discussed or tested, so any broader claims are unsupported.