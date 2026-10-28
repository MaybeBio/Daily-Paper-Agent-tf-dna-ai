## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to methods, results, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose ESM2-BiMamba, a hybrid architecture combining a truncated ESM2 (first 29 of 33 layers) with bidirectional Mamba state-space modules, a length-adaptive dynamic chunking mechanism, a lightweight adapter, and a dual-task prediction head. They claim superior performance over existing methods for DNA-binding protein (DBP) and DNA-binding residue site (DBS) prediction, with particular advantages on long sequences and low-homology targets.
- **Visible evidence base** Abstract text only; no quantitative results, benchmark names, comparison baselines, or statistical measures are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, detailed methods, hyperparameters, training details, benchmark specifications, baseline implementations, and any supplementary data

## Reviewer
- **Overall assessment** The abstract presents a technically plausible hybrid architecture that addresses a real computational bottleneck in protein language model applications. However, the absence of any quantitative results, benchmark details, or comparison baselines in the provided material makes it impossible to evaluate the central claims of superior performance and generalization. The architectural rationale is coherent, but the evidence base is insufficient to establish the case.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein function prediction, particularly those developing scalable deep learning methods for genomic and proteomic sequence analysis. Researchers applying protein language models to long-sequence tasks would also find the length-adaptive and linear-time aspects relevant.
- **Major strengths** The architectural design is well motivated, directly addressing known limitations of Transformer-based protein language models, namely quadratic complexity and inadequate long-range dependency modeling. The hybrid approach of retaining pretrained layers while introducing efficient state-space modules is a sensible strategy for balancing performance and computational cost. The dual-task design for joint protein-level and residue-level prediction is a practical and potentially impactful contribution.
- **Major Concerns**  
  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Evidence sufficiency  
  - **Claim pointer** The abstract claims "superior performance in both DNA-binding protein identification and DNA-binding residue prediction, with notable advantages in processing long sequences and generalizing to low-homology targets."  
  - **Evidence pointer** Abstract, "Extensive experiments" sentence; no specific data provided  
  - **Concern** The abstract provides no quantitative results, no benchmark dataset names, no comparison methods, and no performance metrics. The claim of superiority is entirely unsupported by the visible material.  
  - **Why it matters** Without concrete numbers, statistical significance, or baseline comparisons, the central contribution cannot be assessed. The claim of "notable advantages" is unfalsifiable from the abstract alone.  
  - **Resolution test** Provide in the full manuscript, and ideally in the abstract, specific performance metrics (e.g., AUC, F1, MCC) on named benchmarks, with comparisons to at least two state-of-the-art baselines and measures of variance or significance.  
  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Technical validation  
  - **Claim pointer** The abstract claims the length-adaptive dynamic chunking mechanism "reduces redundant computation and stabilizes long-range dependency modeling."  
  - **Evidence pointer** Abstract, architecture description; no experimental validation provided  
  - **Concern** No evidence is presented that the chunking mechanism achieves its stated goals. The claim of "stabilizing" long-range modeling is vague and unquantified.  
  - **Why it matters** The chunking mechanism is a key novel component. If it does not demonstrably improve efficiency or accuracy, the contribution is weakened.  
  - **Resolution test** Include ablation studies showing performance and computational cost with and without the chunking mechanism, across sequence length ranges, with clear metrics for both accuracy and runtime.  
  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Generalization claim  
  - **Claim pointer** The abstract claims "generalizing to low-homology targets" as a notable advantage.  
  - **Evidence pointer** Abstract, final sentence; no supporting data  
  - **Concern** No definition of "low-homology" is provided, and no results on such targets are shown. The claim is unverifiable.  
  - **Why it matters** Generalization to low-homology sequences is a critical challenge in the field. If the claim is not rigorously demonstrated, it may mislead readers about the method's practical utility.  
  - **Resolution test** Define the homology threshold used, report performance separately on low-homology test subsets, and compare against baselines on the same subsets.  
  - **Concern ID** R1-M4  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Reproducibility  
  - **Claim pointer** The abstract describes a specific architecture, including "first 29 Transformer layers of the pretrained 33-layer ESM2" and "bidirectional Mamba state-space modules."  
  - **Evidence pointer** Abstract, architecture description; no implementation details  
  - **Concern** The abstract lacks any information on training data, hyperparameters, optimization, or computational resources. Reproducibility cannot be assessed.  
  - **Why it matters** For a methods paper, reproducibility is essential. The absence of these details in the abstract is not fatal, but the full manuscript must provide them.  
  - **Resolution test** Ensure the full manuscript includes complete training and implementation details, and ideally release code and pretrained models.

- **Minor Comments**  
  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Clarity  
  - **Affected element** Abstract, architecture description  
  - **Evidence pointer** Abstract, "A sequence-length-adaptive dynamic chunking mechanism"  
  - **Issue** The term "dynamic chunking" is not defined. It is unclear whether chunks are fixed-size, content-based, or variable.  
  - **Required correction** Provide a brief definition or illustrative example of the chunking mechanism in the abstract or full manuscript.  
  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Terminology  
  - **Affected element** Abstract, "lightweight adapter"  
  - **Evidence pointer** Abstract, "a lightweight adapter is incorporated"  
  - **Issue** The type of adapter (e.g., LoRA, prefix tuning, or a custom module) is not specified.  
  - **Required correction** Specify the adapter architecture or cite the relevant method.  
  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Completeness  
  - **Affected element** Abstract, benchmark description  
  - **Evidence pointer** Abstract, "multiple standard benchmark data sets"  
  - **Issue** No benchmark names are given, making it impossible to contextualize the results.  
  - **Required correction** Name the specific benchmark datasets in the abstract or full manuscript.

- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The absence of quantitative results, ablation studies, and low-homology validation means the core claims are not currently supported by the provided material.

- **Assessment against Nature-style criteria**  
  - **Originality** The hybrid ESM2-Mamba architecture is a reasonable incremental contribution, but similar hybrid approaches have been explored in other domains. The specific combination with dynamic chunking and dual-task heads is somewhat novel, though not groundbreaking.  
  - **Scientific importance** The problem of efficient and accurate DBP/DBS prediction is of practical importance, but the abstract does not demonstrate a significant advance over existing methods.  
  - **Interdisciplinary readership** The work is primarily of interest to computational biologists and machine learning researchers. The abstract is accessible to these audiences but may not attract broader readership without stronger results.  
  - **Technical soundness** The architectural rationale is sound, but the lack of evidence prevents assessment of technical execution.  
  - **Readability for nonspecialists** The abstract is reasonably clear but uses jargon (e.g., "Mamba state-space modules") without sufficient explanation for a general scientific audience.

- **Recommendation posture** Currently not established from the provided evidence. The architectural idea is promising, but the abstract alone does not support the performance claims. I would be supportive if the full manuscript provides rigorous quantitative results, ablations, and low-homology validation that substantiate the stated advantages.

## Risk / unsupported claims
- The claim of "superior performance" in DBP and DBS prediction is unsupported by any quantitative data in the provided material.
- The claim of "notable advantages in processing long sequences" is unsupported by any runtime or accuracy comparisons across sequence lengths.
- The claim of "generalizing to low-homology targets" is unsupported by any definition or experimental evidence.
- The claim that the dynamic chunking mechanism "reduces redundant computation and stabilizes long-range dependency modeling" is unverified without ablation studies.
- The overall effectiveness of the hybrid architecture relative to existing methods is not assessable from the abstract alone.