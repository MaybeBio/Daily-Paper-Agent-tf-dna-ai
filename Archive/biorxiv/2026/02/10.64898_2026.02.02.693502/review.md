## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors introduce AtomPaint, a full-atom diffusion-based method for designing protein interactions with non-protein partners (DNA, RNA, small molecules). The method uses a fully atomic 3D image representation, masks regions to be redesigned, inpaints with a diffusion model, and classifies amino acids with an SE(3)-equivariant ResNet. Trained on PDB structures emphasizing protein/non-protein interactions, the method reportedly outperforms random guessing in a sequence recovery benchmark.
- **Visible evidence base** Abstract text only; no quantitative results, benchmark details, or model architecture specifics beyond those stated
- **Missing materials affecting confidence** Full manuscript, methods section, benchmark definitions, training data curation details, model hyperparameters, evaluation metrics, baseline comparisons, and any figures or tables

## Reviewer
- **Overall assessment** The abstract presents a conceptually interesting approach to a genuine gap in computational protein design, namely the handling of non-protein binding partners. The fully atomic representation is a plausible innovation. However, the evidence provided is minimal and largely qualitative. The single benchmark result, described only as "better than random guessing," is insufficient to establish the method's utility or superiority over existing approaches. The abstract reads as a preliminary report rather than a completed study, and the claims made are not adequately supported by the visible evidence.
- **Who would be interested in the results, and why** Researchers in computational protein design, machine learning for structural biology, and synthetic biology would be interested. The method addresses a recognized limitation in current ML-based design tools, and the image-based approach could offer a new direction for modeling mixed biomolecular systems. Those working on DNA-binding protein design, RNA-binding protein design, or small-molecule sensor engineering would find the potential applications relevant.
- **Major strengths** The problem addressed is important and clearly articulated. The fully atomic representation is a conceptually clean solution to the heterogeneity of molecular partners. The use of SE(3)-equivariant networks on a 3D image representation is technically sound in principle. The authors are transparent about the preliminary nature of the results and discuss avenues for improvement.
- **Major Concerns** The evidence base is too thin to support the central claims. The benchmark result is described without any quantitative detail, making it impossible to assess significance or practical relevance. The abstract does not specify how the method compares to existing approaches, nor does it provide any measure of design success beyond sequence recovery. The training data curation is mentioned but not described, leaving questions about generalizability and bias. The lack of any negative results or failure cases weakens the credibility of the claims.
- **Minor Comments** The abstract would benefit from a clearer statement of the method's limitations. The phrase "better than random guessing" is vague and should be replaced with specific metrics. The discussion of future improvements is useful but should be grounded in identified weaknesses rather than generic suggestions.
- **Technical failings that need to be addressed before the case is established** The absence of quantitative benchmark results, lack of comparison to existing methods, and insufficient description of the training data and evaluation protocol are critical gaps. Without these, the claim that AtomPaint "understands some aspects of molecular structure" is not established.
- **Assessment against Nature-style criteria** Originality: The fully atomic image-based approach is novel and addresses a real gap. Scientific importance: The problem is significant, but the demonstrated impact is not yet shown. Interdisciplinary readership: The topic would appeal to structural biologists, ML researchers, and bioengineers, but the abstract does not provide enough detail to engage nonspecialists. Technical soundness: The architecture choices are reasonable, but the lack of validation data prevents assessment of robustness. Readability for nonspecialists: The abstract is clear but assumes familiarity with diffusion models and equivariant networks; a brief explanation of these would improve accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The concept is promising, but the abstract alone does not provide sufficient support for the claims. A revised version with quantitative results, baseline comparisons, and methodological detail would be needed to assess the method's validity.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "In a sequence recovery benchmark, AtomPaint performed better than random guessing, suggesting that it understands some aspects of molecular structure."
- **Evidence pointer** Abstract, location not provided
- **Concern** The only quantitative claim in the abstract is that the method outperforms random guessing in a sequence recovery benchmark. No numerical results, confidence intervals, or statistical tests are provided. The phrase "better than random guessing" is a very low bar and does not demonstrate practical utility. It is unclear what the benchmark entails, how many targets were tested, or what the baseline performance was.
- **Why it matters** Without quantitative evidence, the central claim that AtomPaint "understands" molecular structure is unsupported. Sequence recovery is a weak proxy for design success, and outperforming random guessing does not indicate that the method can produce functional binders. The reader cannot assess whether the method is competitive with existing tools or even minimally useful.
- **Resolution test** Provide the full benchmark results, including recovery rates, standard deviations, and a comparison to at least one existing method (e.g., a sequence-based or structure-based design tool). Include a description of the benchmark dataset and the evaluation protocol.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** "Both models are SE(3)-equivariant ResNets, and were trained on a dataset of structures from the Protein Data Bank (PDB) curated to emphasize protein/non-protein interactions."
- **Evidence pointer** Abstract, location not provided
- **Concern** The training data curation is described only in vague terms. It is not stated how the dataset was filtered, what fraction of the PDB was used, how non-protein partners were selected, or how the train/test split was constructed. The risk of data leakage or bias is not addressed.
- **Why it matters** The method's generalizability depends entirely on the training data. If the dataset is small or biased toward certain types of interactions, the method may not work on novel targets. Without details on curation and splitting, the results cannot be reproduced or trusted.
- **Resolution test** Describe the dataset curation process in detail, including inclusion and exclusion criteria, the number of structures, the types of non-protein partners, and the train/test split. Provide statistics on the diversity of the dataset.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative evaluation
- **Claim pointer** "Most machine learning (ML) algorithms for protein design can only work with systems composed entirely of amino acids, and therefore cannot be directly applied to this task."
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract implies that existing methods are inadequate for non-protein partners, but no comparison to any existing method is provided. It is unclear whether AtomPaint offers any advantage over current state-of-the-art approaches that do accommodate non-protein molecules, such as those using graph-based representations or equivariant diffusion on mixed systems.
- **Why it matters** The novelty of the approach is only meaningful if it leads to improved performance. Without a head-to-head comparison, the reader cannot judge whether the fully atomic representation provides a real benefit or is merely an alternative implementation.
- **Resolution test** Include a benchmark comparison against at least one existing method that can handle non-protein partners, using the same evaluation protocol. Report performance on a common set of design tasks.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Method description
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that the method "proceeds by (i) converting that model to a 3D image, (ii) masking out the parts of that image that need to be redesigned, (iii) using a diffusion model to inpaint the masked voxels, then (iv) using a classification model to identify the amino acids in the inpainted image." The step of converting a model to a 3D image is not explained. It is unclear how atomic coordinates are rasterized, what resolution is used, or how the image is represented.
- **Required correction** Provide a brief description of the image representation, including voxel resolution and how atomic identities and bonds are encoded.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Benchmark description
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "sequence recovery benchmark" is used without definition. It is not clear whether this refers to native sequence recovery, where the method must predict the original amino acid identities from a masked structure, or something else.
- **Required correction** Define the benchmark explicitly and state the metric used (e.g., per-residue accuracy, fraction of fully recovered sequences).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scope
- **Affected element** Discussion of limitations
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract mentions "possible avenues of improvement" but does not identify specific weaknesses of the current method. This makes the discussion generic and less informative.
- **Required correction** List concrete limitations, such as computational cost, resolution limits, or failure modes observed in the benchmark, and tie the proposed improvements to these issues.

## Risk / unsupported claims
- The claim that AtomPaint "understands some aspects of molecular structure" is unsupported by the visible evidence, as the only benchmark result is described qualitatively and without statistical context.
- The claim that existing ML algorithms "cannot be directly applied" to non-protein binding design is presented without citation or comparison, making it unverifiable from the abstract.
- The assertion that the training dataset is "curated to emphasize protein/non-protein interactions" is unverifiable without details on the curation process.
- The overall utility of the method for designing functional binders is not established, as no design experiments or experimental validation are reported.