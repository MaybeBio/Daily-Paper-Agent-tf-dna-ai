## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific and technical evaluation of the proposed hybrid pipeline, benchmark dataset, and reported performance metrics; no assessment of code functionality or dataset contents beyond what is described
- **Shared manuscript claim summary** The authors propose a hybrid pipeline combining Fpocket geometric pocket detection with GPT-4o-mini-based literature extraction to identify and prioritize biologically relevant protein binding pockets. They report the creation of a curated benchmark dataset of ten proteins and 35 papers, and present metrics including Pocket Number Accuracy, Pocket Recall, Pocket Specificity, and amino acid-level F1 scores. They claim the method offers an efficient, accurate, and automated alternative to manual literature analysis for pocket prioritization in drug discovery workflows.
- **Visible evidence base** Abstract; Sections 1, 2, 3, 4, 5, 6, 7, 8; references cited within text; one figure reference (Fig. 1) and multiple figure references (Figs. 2, 4, 5, 7, 8, 9, 10) described in text but not visible; Supplementary Information referenced but not provided
- **Missing materials affecting confidence** Figures 1-10 (not visible); Supplementary Information (prompts, baseline configurations); benchmark dataset contents (JSON files); exact prompt templates; per-protein results; statistical significance tests; comparison against baseline methods beyond Fpocket; details of manual curation of papers; computational cost measurements

## Reviewer
- **Overall assessment** The manuscript addresses a real and practical bottleneck in structure-based drug discovery: the labor-intensive and error-prone process of translating literature-reported binding site information into usable geometric definitions for docking and screening. The idea of using LLMs to automate literature extraction and validation of geometric pocket predictions is timely and potentially useful. However, the current manuscript provides insufficient evidence to establish the reliability, generalizability, or practical utility of the proposed pipeline. The reported metrics are based on a small, self-created dataset without external validation, the evaluation methodology is incompletely described, and several claims in the abstract and discussion are not fully supported by the data presented. The manuscript would benefit from a more rigorous evaluation framework, including comparison against simpler baselines, per-protein breakdowns, and error analysis.

- **Who would be interested in the results, and why** Computational chemists and structural biologists working in drug discovery, particularly those involved in virtual screening, pocket detection, and target validation. Researchers developing automated literature-mining tools for biomedical applications would also find the benchmark dataset and prompt engineering strategies relevant. The work may also interest developers of LLM-based scientific information extraction systems, as it presents a domain-specific application with structured output requirements.

- **Major Strengths**
  - Addresses a genuine and underappreciated bottleneck in computational drug discovery workflows
  - The idea of using LLMs to filter geometric pocket predictions against literature evidence is novel and practical
  - The benchmark dataset is made publicly available, which is a valuable community resource
  - The pipeline design is modular and could accommodate alternative geometric detectors or LLMs
  - The authors acknowledge limitations honestly, including Fpocket's inability to separate adjacent sites and the dependence on input text quality

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Our method leverages Fpocket to generate candidate pockets, which are then validated against published experimental data extracted from research articles using LLM with a series of prompts fine-tuned to identify and extract residue-level information associated with experimentally confirmed binding sites."
- **Evidence pointer** Section 2.2, Section 3.1; location not provided for specific prompt details
- **Concern** The manuscript does not provide the actual prompts used, nor a systematic description of how they were optimized. The authors state that "significant prompt optimization efforts were focused on this step" but provide no details on the optimization process, the number of iterations, the criteria for accepting or rejecting prompt changes, or the final prompt templates. Without this information, the results cannot be reproduced, and the claim that the prompts are "fine-tuned" is not verifiable. The Supplementary Information is referenced but not provided for review.
- **Why it matters** Prompt design is the core methodological contribution of this work. If the prompts are not described, other researchers cannot apply the method, evaluate its robustness, or understand which aspects of the prompt design contribute to performance. This is a fundamental reproducibility issue.
- **Resolution test** Provide the full prompt templates in the main text or supplementary materials, along with a description of the optimization procedure, including the number of iterations, the validation set used, and the specific changes made at each step.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evaluation rigor
- **Claim pointer** "The dataset was initially evaluated by the baseline set of prompts... This yielded a Pocket Number Accuracy of 0.484, Pocket Recall of 0.958, and Pocket Specificity of 0.46. Optimization of the extraction step... resulted in a Pocket Number Accuracy of 0.581, perfect Pocket Recall (1.0), and Pocket Specificity of 0.558. Addition of the Refinement step... further improving Pocket Number Accuracy to 0.71 and Pocket Specificity to 0.657 and maintaining perfect Pocket Recall."
- **Evidence pointer** Section 3.1; location not provided for per-protein results
- **Concern** The evaluation is based on a single dataset of ten proteins and 35 papers, all curated by the authors themselves. There is no external validation, no cross-validation, no confidence intervals, and no statistical testing. The reported improvements from prompt optimization are presented as point estimates without any measure of variability. Furthermore, the dataset is small and may not be representative of the diversity of protein families, binding site types, or literature styles encountered in practice. The authors do not report per-protein results, so it is impossible to assess whether performance is consistent across targets or driven by a few easy cases.
- **Why it matters** Without a rigorous evaluation framework, the claimed performance improvements cannot be distinguished from noise or overfitting to the specific dataset. The practical utility of the method depends on its reliability across diverse targets and literature sources, which is not demonstrated.
- **Resolution test** Provide per-protein results, confidence intervals or error bars, and a discussion of failure cases. Ideally, validate on an independent set of proteins and papers not used in prompt development. Report results for each of the three complexity tiers separately.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparison against baselines
- **Claim pointer** "This hybrid pipeline offers an efficient, accurate and automated method for identifying functional binding pockets, addressing a significant bottleneck in the high-throughput drug discovery workflows."
- **Evidence pointer** Section 3, Section 4; location not provided
- **Concern** The manuscript does not compare the proposed method against any alternative approaches for the same task. For example, how does the LLM-based extraction compare to a simple keyword search, a rule-based information extraction system, or a human annotator (in terms of time and accuracy)? How does the final pocket definition compare to using Fpocket's top-ranked pocket directly, or to using all Fpocket pockets without filtering? The claim of "efficient, accurate and automated" requires a baseline comparison to be meaningful.
- **Why it matters** The value proposition of the method is that it improves upon existing practice. Without a comparison to simpler or alternative approaches, the reader cannot judge whether the added complexity of an LLM-based pipeline is justified.
- **Resolution test** Add a comparison against at least one simple baseline (e.g., using Fpocket's ranking alone, or a keyword-based residue search) and, if possible, against human expert annotation on a subset of papers. Report time and cost metrics for the LLM pipeline.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and limitations
- **Claim pointer** "Our results indicate that the LLM pipeline, particularly after prompt optimization and the inclusion of a refinement step, can effectively identify relevant papers and extract pocket information with high accuracy."
- **Evidence pointer** Section 3.1, Section 4; location not provided
- **Concern** The authors acknowledge several limitations, including the reliance on GPT-4o-mini and the small dataset, but do not discuss how the method might perform with other LLMs, with older or newer model versions, or with papers that are not available in clean digital text form. The authors also note that they "prepared manually curated markdown representations of the articles for this study," which is a significant caveat: the method is not tested on raw PDF parsing, which is a major practical challenge. The claim of "high accuracy" is therefore conditional on a level of input quality that may not be achievable in practice.
- **Why it matters** The practical applicability of the method depends on its robustness to real-world input conditions. If the method requires manually curated text, its utility in high-throughput settings is substantially reduced.
- **Resolution test** Discuss the impact of input text quality on performance, and ideally test the pipeline on at least a few papers processed through an automated PDF-to-text conversion pipeline. Report performance with at least one alternative LLM to assess model dependence.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Validation of biological relevance
- **Claim pointer** "The extracted information is then mapped onto protein structures and used to filter and merge the geometry-based predictions, generating a refined volumetric representation of biologically relevant pockets."
- **Evidence pointer** Section 2.5, Section 3.2; location not provided for quantitative validation
- **Concern** The manuscript describes visual assessment of the final pocket representations by a human expert but provides no quantitative validation that the refined pockets are indeed biologically relevant. For example, are the refined pockets closer to known ligand binding sites (e.g., from co-crystallized ligands in the PDB) than the unfiltered Fpocket predictions? Is there any docking or enrichment analysis to demonstrate that the refined pockets are more useful for virtual screening? The examples shown (GABAA receptor, Nav1.7 chimera) are qualitative.
- **Why it matters** The central claim is that the pipeline produces "biologically relevant" pockets. This claim requires quantitative evidence, not just visual inspection of a few examples.
- **Resolution test** Add a quantitative comparison between the refined pockets and the original Fpocket predictions, using metrics such as overlap with known ligand binding sites, volume accuracy, or docking performance.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.3, metric definitions
- **Evidence pointer** Section 2.3; location not provided
- **Issue** The definitions of Pocket Number Accuracy, Pocket Recall, and Pocket Specificity are described in text but the equations appear to be missing or incomplete. The text states "for each paper, if the number of annotated and extracted pockets match, then prediction is correct (1), otherwise it is incorrect (0). Based on these values for each pocket the final accuracy per parer is calculated." This is unclear. How is accuracy aggregated across papers? What is the denominator for Pocket Recall and Pocket Specificity?
- **Required correction** Provide clear, formal definitions of all metrics, including the exact formulas and how they are aggregated across the dataset. Correct the typo "parer" to "paper."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.1, dataset description
- **Evidence pointer** Section 2.1; location not provided
- **Issue** The dataset description lists ten proteins but does not provide a table summarizing the proteins, their PDB IDs, the number of papers per protein, or the complexity tier assignment. The criteria for assigning papers to complexity tiers are not described.
- **Required correction** Add a table summarizing the dataset composition, including protein names, PDB IDs, number of papers, and tier assignments. Describe the criteria for tier assignment.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.4, threshold selection
- **Evidence pointer** Section 2.4; location not provided
- **Issue** The manuscript states that thresholds of 0.6 for chain matching and 0.7 for cluster matching were "empirically set." No details are provided on how these values were chosen, what range of values was tested, or how sensitive the results are to these choices.
- **Required correction** Describe the threshold selection process, including the range of values tested and the criterion used for selection. Report sensitivity of results to threshold variation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.5, grid representation
- **Evidence pointer** Section 2.5; location not provided
- **Issue** The description of the grid representation states that "only grid points located inside the alpha spheres are retained" and that a convex hull is constructed on the pocket heavy atoms. It is unclear how the pocket heavy atoms are defined at this stage, since the pocket is being constructed from the LLM-extracted residues. Are these the atoms of the residues identified by the LLM?
- **Required correction** Clarify the definition of "pocket heavy atoms" in the context of the grid construction.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.1, model version
- **Evidence pointer** Section 3.1; location not provided
- **Concern** The manuscript states that "all steps of the LLM pipeline are performed by the GPT-4o-mini model" but does not specify the exact model version or snapshot date. Given the rapid evolution of LLMs, this information is important for reproducibility.
- **Required correction** Specify the exact model version and any relevant parameters (e.g., temperature, max tokens) used in the experiments.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figures
- **Evidence pointer** Figures 1-10 referenced in text; not visible in provided material
- **Issue** The figures are referenced but not visible in the provided manuscript text. Based on the text descriptions, it is unclear whether Figure 3 and Figure 6 exist, as they are not referenced in the text provided.
- **Required correction** Ensure all figures are present and referenced in the text. Verify figure numbering is consistent.

## Risk / unsupported claims
- The claim that the method is "efficient, accurate and automated" is not supported by comparison against baselines or by quantitative validation of biological relevance.
- The claim that the prompts are "fine-tuned" is not verifiable without the actual prompts and optimization details.
- The claim of "high accuracy" in pocket extraction is based on a small, self-curated dataset without external validation or statistical analysis.
- The claim that the pipeline "addresses a significant bottleneck" is plausible but not quantitatively demonstrated.
- The performance of the method with raw, uncurated article text is not assessed, despite the authors noting that they used manually curated markdown representations.
- The generalizability of the method to proteins outside the ten selected targets is not demonstrated.
- The impact of the convex hull truncation on pocket volume accuracy is described qualitatively but not quantitatively evaluated.