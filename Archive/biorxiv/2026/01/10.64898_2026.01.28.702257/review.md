## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present Seq2Pocket, a methodology for protein-ligand binding site (LBS) prediction that combines protein language model (pLM) finetuning, an extended training dataset (sc-PDB enhanced), an embedding-supported smoothing classifier, and a clustering approach selected via a newly defined Pocket Fragmentation Index. They report state-of-the-art performance on the LIGYSIS benchmark for general binding site prediction and on the CryptoBench benchmark for cryptic binding site prediction, with a reported improvement of up to 12% in distance-center-to-center recall on LIGYSIS.
- **Visible evidence base** Abstract text only; no quantitative results beyond the single 12% improvement figure, no benchmark tables, no dataset statistics, no methodological details, no code or data availability statements
- **Missing materials affecting confidence** Full manuscript, all figures and tables, benchmark evaluation protocols, dataset construction details, hyperparameters, baseline comparisons, statistical significance tests, and any supplementary information

## Reviewer
- **Overall assessment** The abstract describes a plausible and potentially useful methodology for pocket-level LBS prediction, addressing a real limitation of residue-centric pLM approaches. However, the evidence provided in the abstract is insufficient to evaluate the core claims. The single quantitative result (12% improvement on one metric) lacks context, baseline specification, and statistical validation. The novelty of the components, particularly the dataset enhancement and the smoothing classifier, cannot be assessed without methodological detail. The claim of state-of-the-art performance across two benchmarks is not supported by the visible evidence.
- **Who would be interested in the results, and why** Computational structural biologists, bioinformaticians, and researchers in drug discovery would be interested if the claims hold. The work addresses a practical problem in translating residue-level predictions to usable binding pockets, which is directly relevant to virtual screening and target identification workflows. The proposed dataset enhancement and evaluation metrics could also interest researchers working on benchmark design in protein function prediction.
- **Major strengths** The problem addressed is well-defined and practically important. The proposed combination of pLM finetuning with structure-aware post-processing is a sensible direction. The introduction of a Pocket Fragmentation Index as a selection criterion for clustering is a potentially useful contribution. The use of two distinct benchmarks, including a cryptic site benchmark, suggests an attempt at broad evaluation.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**  
  Originality: The combination of components appears incremental rather than conceptually novel; the individual elements (pLM finetuning, dataset augmentation, clustering) are established techniques. The Pocket Fragmentation Index is a new metric but its utility is not demonstrated in the abstract.  
  Scientific importance: The problem is important, but the abstract does not provide enough evidence to establish that the proposed method advances the field beyond existing tools.  
  Interdisciplinary readership: The work is primarily of interest to computational biologists and bioinformaticians; the abstract does not clearly articulate broader implications for chemistry or biology.  
  Technical soundness: Cannot be assessed from the abstract; no methodological detail or statistical validation is provided.  
  Readability for nonspecialists: The abstract is reasonably clear but uses field-specific terms (e.g., pLM, LIGYSIS, CryptoBench) without sufficient context for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract alone does not support the claims of state-of-the-art performance or methodological advance. A full manuscript with detailed methods, complete benchmark results, and statistical analysis would be required for a supportive assessment.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "Across both benchmarks, the proposed methodology achieves state-of-the-art performance."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract provides only one quantitative result (up to 12% improvement in distance-center-to-center recall on LIGYSIS) and no data for CryptoBench. No baseline methods are named, no absolute performance numbers are given, and no statistical significance or variance measures are reported.  
- **Why it matters** A claim of state-of-the-art performance requires comparison against current best methods with complete results on all benchmarks. Without this, the claim is unverifiable and potentially misleading.  
- **Resolution test** Provide full benchmark tables with all compared methods, absolute metric values, standard deviations or confidence intervals, and statistical tests (e.g., paired bootstrap or Wilcoxon) for both LIGYSIS and CryptoBench.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological clarity  
- **Claim pointer** "we introduce sc-PDB enhanced , an extended training dataset that augments sc-PDB with additional small-molecule and ion-binding sites"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract does not specify how the dataset was constructed, what sources were used for additional sites, how redundancy with the original sc-PDB was handled, or how the augmentation affects the evaluation benchmarks. Without this information, the contribution of the dataset enhancement cannot be assessed.  
- **Why it matters** Dataset curation is a central claimed contribution. If the augmentation introduces bias or overlaps with test sets, the reported improvements could be artifactual.  
- **Resolution test** Describe dataset construction in detail, including data sources, filtering criteria, redundancy removal, and a demonstration that the test benchmarks are not contaminated by training data.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical detail  
- **Claim pointer** "we employ an embedding-supported smoothing classifier to refine residue-level predictions" and "we define the Pocket Fragmentation Index and use it to select a clustering approach"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract provides no detail on how the smoothing classifier works, what embeddings are used, how the Pocket Fragmentation Index is computed, or which clustering algorithms were compared. The methodological novelty and the basis for the reported improvement cannot be evaluated.  
- **Why it matters** The core methodological contributions are described only at a high level. Reproducibility and assessment of technical soundness require specific algorithmic descriptions.  
- **Resolution test** Provide full method descriptions, including equations, pseudocode, hyperparameter choices, and ablation studies showing the contribution of each component.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Generalizability  
- **Claim pointer** "provide pocket-level prediction tool that are better suited for downstream applications such as drug discovery"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract claims suitability for downstream applications but provides no demonstration of this, such as case studies, docking experiments, or comparison with existing pocket prediction tools in a practical setting.  
- **Why it matters** The stated motivation is downstream utility. Without evidence of practical applicability, the claim remains speculative.  
- **Resolution test** Include a case study or application example showing the predicted pockets are usable in a downstream task, or temper the claim to reflect the current scope of evaluation.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract wording  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The phrase "pocket-level prediction tool that are better suited" contains a grammatical error ("tool" should be "tools" or "tool that is").  
- **Required correction** Revise to "pocket-level prediction tools that are better suited" or "a pocket-level prediction tool that is better suited."

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** "sc-PDB enhanced"  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The naming convention with a space before the comma is inconsistent and the term "enhanced" is vague.  
- **Required correction** Use a consistent notation, e.g., "sc-PDB-enhanced" or "sc-PDB_enhanced," and clarify what "enhanced" means in terms of dataset size and composition.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Benchmark evaluation  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract does not state whether the evaluation used the standard splits of LIGYSIS and CryptoBench or custom splits, which affects comparability with prior work.  
- **Required correction** Specify the evaluation protocol, including data splits and any preprocessing steps applied to the benchmarks.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Availability statement  
- **Evidence pointer** Abstract, location not provided  
- **Issue** No mention of code or data availability, which is important for reproducibility.  
- **Required correction** Include a data and code availability statement in the full manuscript.

## Risk / unsupported claims
- The claim of "state-of-the-art performance" on both benchmarks is unsupported by the visible evidence, as only one metric on one benchmark is reported.
- The claim that the proposed methodology "contribute[s] to more reliable evaluation practices" is not substantiated by any analysis of evaluation methodology.
- The claim of suitability for "downstream applications such as drug discovery" is speculative and not demonstrated.
- The effectiveness of the Pocket Fragmentation Index as a selection criterion is not demonstrated with any comparative data.
- The contribution of the sc-PDB enhanced dataset to the reported improvements is not isolatable from the other methodological components.