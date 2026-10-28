## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods, supplementary figure/table legends as provided)
- **Assessment boundary** Scientific content, methodological rigor, and logical coherence of the claims as presented in the provided text. No external data or unpublished materials were consulted.
- **Shared manuscript claim summary** The authors propose that epidermal stem cells (EpdSCs) in mice retain lifelong epigenetic memory of a psoriasis-like inflammatory episode, and that this memory is encoded by CpG dinucleotide density within specific chromatin domains. They argue that CpG-rich sequences, once opened by inflammation-induced transcription factors, sustain accessibility through DNA demethylation, methylation-sensitive TF binding, nucleosome disfavor, and H2A.Z incorporation, thereby conferring enhanced stress responsiveness for the animal's lifetime.
- **Visible evidence base** Bulk ATAC-seq across timepoints (D6, D30, Y1, Y2); scATAC-seq and scRNA-seq at D30 and Y1; WGBS across timepoints; MINT-ChIP for histone marks; Cut-and-Run for TFs; two deep-learning models (ChromBPNet for establishment, PersistNet for persistence); in silico CpG perturbation experiments; reanalysis of published datasets (wounding, pancreatitis, LPS); functional wound-healing assays at Y1.
- **Missing materials affecting confidence** No figures, tables, or supplementary data files were provided for direct inspection. Statistical details, exact effect sizes, and quality control metrics for genomics datasets are not fully assessable. The description of the logistic regression model for predicting memory longevity lacks key performance metrics. Details on the H2A.Z BPNet model training and evaluation are incomplete.

## Reviewer
- **Overall assessment** This manuscript presents a conceptually important and technically ambitious investigation into the molecular basis of epigenetic memory longevity. The central claim, that CpG density acts as a sequence-intrinsic determinant of memory persistence, is novel and potentially transformative. The combination of longitudinal epigenomic profiling, deep learning, and functional validation is commendable. However, the strength of the conclusions is not fully matched by the evidence presented in the text. Several key claims rely on correlative analyses or model predictions that lack direct experimental validation. The manuscript would be substantially strengthened by addressing the concerns below, particularly regarding causal evidence for the CpG-H2A.Z axis and the generalizability of the findings.
- **Who would be interested in the results, and why** This work will appeal to a broad audience in epigenetics, chromatin biology, immunology, and skin biology. Specifically, researchers studying epigenetic memory, trained immunity, stem cell biology, and the role of DNA sequence in chromatin regulation will find the findings highly relevant. The use of deep learning to uncover sequence determinants of epigenetic stability offers a methodological template applicable to other systems. Clinically, the work has implications for understanding the long-term consequences of inflammatory diseases such as psoriasis and for designing therapies that modulate epigenetic states.
- **Major strengths**
  1. The longitudinal design (D6 to Y2) is a major strength, allowing the authors to distinguish between memory establishment and maintenance.
  2. The development of PersistNet, a deep-learning model trained specifically on a persistence metric, is an innovative approach that directly addresses the question of longevity.
  3. The multi-omics integration (ATAC, WGBS, histone marks, TF binding) provides a comprehensive view of the epigenetic state.
  4. The functional validation via wound healing at Y1 demonstrates the biological relevance of the long-term memory.
  5. The cross-tissue reanalysis (pancreatitis, LPS) suggests a potentially generalizable principle, which is exciting.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal evidence
- **Claim pointer** "CpG-enriched sequences thereafter become essential, reinforcing accessibility across cellular generations by integrating DNA demethylation, methylation-sensitive transcription factors, sequence-intrinsic nucleosome disaffinity, and the nucleosome-destabilizing histone variant H2A.Z."
- **Evidence pointer** Figures 5 and 6 (described in text); methods sections on PersistNet, WGBS, and H2A.Z BPNet
- **Concern** The manuscript proposes a mechanistic model where CpG density drives H2A.Z incorporation, which in turn stabilizes the open chromatin state. However, the evidence presented is largely correlative. The H2A.Z BPNet model identifies CpG as a predictive feature, and H2A.Z ChIP shows enrichment at long-term domains, but there is no direct experimental manipulation to demonstrate that CpG density is causally required for H2A.Z deposition or memory persistence. The in silico CpG perturbation experiments (Fig. 5E-G) alter predicted longevity but do not test the actual biological mechanism. The claim that H2A.Z "integrates" these features is an interpretation that requires direct testing, such as H2A.Z depletion or overexpression experiments.
- **Why it matters** Without causal evidence, the central mechanistic claim of the paper remains a hypothesis. The distinction between correlation and causation is critical for establishing the proposed model and for guiding future therapeutic interventions.
- **Resolution test** Provide experimental evidence, such as: (1) knockdown or overexpression of H2A.Z in EpdSCs followed by assessment of memory domain accessibility and persistence; (2) targeted demethylation or methylation of CpG sites within a specific long-term memory domain to test whether this alters H2A.Z incorporation and memory retention; (3) mutation of CpG dinucleotides within a reporter construct to test the effect on H2A.Z deposition and chromatin stability.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability
- **Claim pointer** "in mining publicly available datasets, we found that CpG was enriched in the long-lasting epigenetic memories formed upon response of EpdSCs to wounding, acinar cells to pancreatitis, and hematopoietic stem cells to lipopolysaccharide exposure"
- **Evidence pointer** Methods section "Analysis of published ATAC-seq datasets"; Figure S11 (described in text)
- **Concern** The claim of generalizability across tissues and stimuli is based on a single metric (CpG enrichment) in reanalyzed datasets. It is unclear whether the same mechanistic pathway (demethylation, H2A.Z, methylation-sensitive TFs) operates in these other contexts. The analysis appears to be purely correlative and does not test whether the identified CpG-rich domains in these other systems are functionally relevant for memory persistence. The criteria for defining "long-lasting" memories in these published datasets may differ from the authors' own definitions, and the statistical power of these reanalyses is not described.
- **Why it matters** The generalizability claim significantly elevates the impact of the work. If the mechanism is not conserved, the title and abstract overstate the findings. If it is conserved, the evidence needs to be more robust.
- **Resolution test** Provide a more detailed analysis of the reanalyzed datasets, including the number of domains, effect sizes, and statistical significance. Ideally, validate the mechanism in at least one other system by showing that H2A.Z is enriched at these CpG-rich memory domains and that its depletion affects memory persistence.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Model validation and interpretability
- **Claim pointer** "The model accurately predicted experimentally observed accessibility persistence (Spearman's correlation, r = 0.62)"
- **Evidence pointer** Methods section "PersistNet: BP-based model to predict persistence score from DNA sequence"; Figure 5A (described in text)
- **Concern** While the reported correlation of 0.62 is reasonable, the manuscript does not provide sufficient detail on how the model was validated. It is unclear whether this correlation is on held-out chromosomes or on the training set. The text mentions cross-validation but does not report the variance across folds. Furthermore, the model's interpretability is limited to motif discovery; it is not shown whether the model's predictions are robust to perturbations in the input sequence beyond the CpG removal experiments. The choice of the persistence score metric (arctan-transformed ratio) is somewhat arbitrary and its biological meaning is not fully discussed.
- **Why it matters** The deep-learning model is a central pillar of the paper. If the model is overfit or not properly validated, the subsequent conclusions drawn from it (e.g., the importance of CpG) are weakened.
- **Resolution test** Report the mean and standard deviation of the Spearman correlation across cross-validation folds. Provide a more detailed description of the model architecture and training procedure. Show that the model's performance is significantly better than a baseline model (e.g., a model trained on shuffled sequences or a model using only GC content). Discuss the biological interpretation of the persistence score.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Functional significance of individual genes
- **Claim pointer** "Among the 62 transcripts displaying heightened wound sensitivity was the inflammasome effector Aim2... Other stress-responsive transcripts included long-term memory-associated genes encoding the inflammatory cytokine IL-18 and antimicrobial and antiviral ribonuclease and chemoattractant RNase2b"
- **Evidence pointer** Figure 2 (described in text); data S8
- **Concern** The functional validation focuses on wound healing and identifies a set of genes with heightened responsiveness. However, the manuscript does not demonstrate that the long-term memory domains are required for the enhanced wound healing phenotype. It is possible that the enhanced healing is due to other factors, such as changes in cell number or composition, rather than the specific epigenetic memory at these loci. The link between the identified genes (Aim2, Il18, Rnase2b) and the wound healing phenotype is not directly tested.
- **Why it matters** The claim that epigenetic memory "profoundly affects tissue fitness upon recall" requires a direct demonstration that the memory domains are functionally responsible for the improved outcome.
- **Resolution test** Perform experiments where the memory domains are disrupted (e.g., by CRISPR-mediated deletion or epigenetic editing) and assess the impact on wound healing and gene induction. Alternatively, show that the enhanced healing is dependent on one of the identified genes (e.g., Aim2) using knockout mice.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of definitions
- **Affected element** Definition of "long-term" vs "short-term" memory domains
- **Evidence pointer** Methods section "Selection of short- and long-term memory domains from ATAC-seq"
- **Issue** The criteria for classifying domains as "long-term" (117 domains) vs "short-term" (117 domains) are described, but the rationale for these specific thresholds is not fully justified. It is unclear how sensitive the downstream analyses are to these choices.
- **Required correction** Provide a sensitivity analysis or a more detailed justification for the chosen thresholds. Show that the main conclusions are robust to reasonable variations in these parameters.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Multiple comparisons
- **Evidence pointer** Throughout results section
- **Issue** The manuscript reports many comparisons (e.g., motif enrichment, methylation differences, gene expression). It is not always clear whether multiple testing corrections were applied and what the corrected significance thresholds were.
- **Required correction** Clearly state the multiple testing correction method used for each analysis (e.g., Benjamini-Hochberg, Bonferroni) and report adjusted p-values.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Code and data availability statement
- **Evidence pointer** "Data, code, and materials availability" section
- **Issue** The statement says "All data needed to evaluate the conclusions in the paper are present in the paper or the supplementary materials" and mentions deposition in GEO. However, the code is only available on Zenodo, and the specific version/DOI is not provided in the text.
- **Required correction** Provide the specific Zenodo DOI for the code and ensure that all custom scripts are included and documented.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** All figures
- **Evidence pointer** Not applicable
- **Issue** The figures were not provided for review. It is impossible to assess the quality of the data visualization, the appropriateness of the statistical tests, or the clarity of the figure legends.
- **Required correction** Ensure that all figures are of high quality, with clear labels, and that the legends contain all necessary statistical details (e.g., n, test used, p-values).

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Epigenetic longevity"
- **Evidence pointer** Title and abstract
- **Issue** The term "epigenetic longevity" is not standard and could be misinterpreted. It may be clearer to use "epigenetic memory persistence" or "long-term epigenetic memory."
- **Required correction** Consider revising the terminology for clarity and consistency with the field.

## Risk / unsupported claims
- The claim that CpG density is "essential" for memory persistence is not supported by direct causal evidence; it is inferred from correlative and in silico analyses.
- The claim that the mechanism is generalizable across tissues and stimuli (wounding, pancreatitis, LPS) is based on limited reanalysis and lacks functional validation in those systems.
- The claim that H2A.Z "integrates" the various features is an interpretation that is not directly tested.
- The functional significance of the memory domains for wound healing is not directly demonstrated; the link between specific genes and the phenotype is correlative.
- The statement that "the remaining degree of openness persisting through life" is based on data up to Y2, which may not be the full lifespan of a mouse. The extrapolation to "life" is an overstatement.