## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, supplementary figure/table references) as provided by the user.
- **Assessment boundary** Scientific content, technical soundness, and clarity of claims as presented in the supplied text. No external validation of data, code, or trajectories was performed.
- **Shared manuscript claim summary** The authors present microsecond-timescale, all-atom explicit-solvent MD simulations of a DNA-bound full-length p53 tetramer (wild-type, Y220C, G245S) using the Anton2 supercomputer. They report DNA bending consistent with experiment, compact tetramer formation via N-terminal domain (NTD)–DNA-binding domain (DBD) interactions, a unique WT-only quaternary DBD organization, differential dynamics of inner versus outer DBDs, and identification of a cryptic loop 6 (L6) pocket. They also characterize the L1/S3 pocket opening and cysteine solvent accessibility.
- **Visible evidence base** Abstract, full introduction, results, discussion, methods, and references to supplementary figures (S1–S23) and tables (S1–S7). No actual figures, tables, or trajectory data were provided.
- **Missing materials affecting confidence** All figures, tables, supplementary data, and trajectory files are absent from the supplied material. This severely limits quantitative verification of the reported results.

## Reviewer
- **Overall assessment** This manuscript addresses a significant and timely question: the dynamics of the full-length p53 tetramer bound to DNA, a system of high biomedical relevance. The use of Anton2 for microsecond-scale simulations of a ~500k-atom system is technically ambitious and represents a notable computational achievement. The authors report several potentially interesting observations, including a WT-specific clamped quaternary state and a cryptic L6 pocket. However, the current manuscript, as provided, is not sufficient to establish the central claims. The absence of all figures and tables makes it impossible to evaluate the quality of the data, the validity of the MSM construction, or the robustness of the conclusions. Several methodological details are also under-specified, and some claims appear to extend beyond what the presented evidence can support. The manuscript would benefit from a clearer articulation of the novelty relative to prior work, a more rigorous treatment of sampling convergence, and a more cautious interpretation of the biological implications.
- **Who would be interested in the results, and why** Structural biologists, computational biophysicists, and cancer researchers studying p53 function and reactivation. The work is relevant to those interested in cryptic pocket discovery, allostery in multi-domain transcription factors, and the application of long-timescale MD to large protein–DNA complexes. The potential identification of a new druggable pocket on p53 could attract medicinal chemists working on p53 reactivators.
- **Major strengths**
  - The study tackles a biologically important and technically challenging system: full-length p53 tetramer bound to DNA, which has eluded experimental structure determination.
  - The use of Anton2 for microsecond-scale simulations of a ~500k-atom system is a significant technical achievement and represents a state-of-the-art application of specialized hardware.
  - The integration of multiple analytical methods (PCA, tICA, MSM, FTMap) is appropriate and potentially powerful for characterizing conformational landscapes.
  - The reported agreement between simulated DNA bending angles and experimental measurements provides a useful validation of the model.
  - The observation of a WT-specific clamped quaternary state and a cryptic L6 pocket are potentially novel and interesting findings.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality and reproducibility
- **Claim pointer** The manuscript claims to have "elucidated the conformational landscape" of the DNA-bound fl-p53 tetramer and to have identified specific metastable states and a cryptic L6 pocket.
- **Evidence pointer** All figures and tables (Fig 1–7, Table 1–4, Fig S1–S23, Table S1–S7) are referenced but not provided.
- **Concern** The entire evidentiary basis of the manuscript is missing from the supplied material. Without figures, tables, and supplementary data, it is impossible to assess the quality of the simulations, the validity of the MSM construction, the statistical significance of the reported populations, or the structural basis of the claimed findings. This is a fundamental barrier to evaluation.
- **Why it matters** The central claims of the paper rest entirely on the presented data. Without access to this data, the claims cannot be verified or falsified, and the manuscript cannot be considered scientifically complete.
- **Resolution test** Provide all figures, tables, and supplementary data. Ensure that all claims are directly supported by the displayed data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of MSM analysis
- **Claim pointer** The authors state that MSMs were constructed using k-means clustering with k=150 and validated by implied timescale plots and Chapman-Kolmogorov tests.
- **Evidence pointer** Methods section, "Markov State Model Construction"; Fig 6, Fig 7, Fig S16–S23.
- **Concern** The description of the MSM construction is insufficient to evaluate its rigor. Key details are missing, including: the number of states used in the final MSM, the lag time selection procedure, the statistical uncertainty estimates for state populations and transition probabilities, and the criteria used to judge the Chapman-Kolmogorov tests. The choice of k=150 for k-means clustering is stated but not justified. Without these details, the reliability of the reported metastable states and their populations cannot be assessed.
- **Why it matters** MSM-based conclusions are only as reliable as the underlying model. Inadequate validation or under-specified construction can lead to spurious states and incorrect kinetic or thermodynamic interpretations.
- **Resolution test** Provide a detailed description of the MSM building process, including state count selection, lag time validation, uncertainty quantification (e.g., via Bayesian MSMs or bootstrapping), and clear presentation of the Chapman-Kolmogorov test results.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Sampling convergence and statistical power
- **Claim pointer** The authors claim to have "elucidated the conformational landscape" and to have identified differences in dynamics between WT and mutant systems, as well as between inner and outer DBDs.
- **Evidence pointer** Results sections "p53 Organization around DNA" and "DBD Dynamics"; Fig 3, Fig 5.
- **Concern** The manuscript reports 3 replicas of 7.5 μs per system. While this is a substantial simulation effort, it is unclear whether this sampling is sufficient to converge the conformational distributions of a ~500k-atom system with multiple flexible domains. No convergence analysis is presented (e.g., time-dependent free energy estimates, split-half analyses, or comparison of replica distributions). The claim that the WT tetramer samples a "unique" clamped state not accessed by mutants is particularly strong and requires evidence that the mutants have been sampled sufficiently to rule out such states.
- **Why it matters** Without demonstrated convergence, the reported free energy landscapes and state populations may be biased by insufficient sampling, leading to incorrect conclusions about system-specific behavior.
- **Resolution test** Provide convergence analyses, such as plotting free energy estimates as a function of simulation time, comparing distributions across replicas, and performing statistical tests to support claims of differential sampling between systems.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Novelty and contextualization
- **Claim pointer** The authors state that this is the "first" full-length p53 tetramer model bound to DNA and that the L6 pocket is "underexplored" and "novel."
- **Evidence pointer** Introduction; Results section "DBD Dynamics"; Discussion.
- **Concern** The manuscript does not adequately contextualize its findings against prior computational and experimental work on p53 dynamics. The claim of a "first" model may be overstated given prior integrative models and simulations of p53 tetramers. The novelty of the L6 pocket should be more carefully qualified, as the authors themselves note that a ligand-bound structure (pdbID 8DC6) was recently published. The discussion would benefit from a more explicit comparison of the present findings with those of previous studies, including the authors' own 2017 work.
- **Why it matters** Overstating novelty can mislead readers and undermine the perceived contribution of the work. A clear delineation of what is new versus what confirms prior findings is essential for scientific accuracy.
- **Resolution test** Revise the introduction and discussion to explicitly compare the present results with prior computational and experimental studies, and temper claims of novelty where appropriate.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation and significance
- **Claim pointer** The authors suggest that the observed NTD–DBD interactions and the WT-specific clamped state may have functional relevance, and that the L6 pocket "presents a unique opportunity for structure-based design."
- **Evidence pointer** Results sections "DNA, CTD and NTD Dynamics" and "L1/S3 Pocket"; Discussion.
- **Concern** The functional implications of the observed conformational states are speculative. The manuscript does not provide experimental validation or a clear mechanistic hypothesis linking the observed dynamics to p53 function (e.g., transcriptional activity, DNA binding affinity, or mutant phenotypes). The claim that the G245S mutant may be "concealing phosphorylation sites" is highly speculative and not supported by direct evidence.
- **Why it matters** For a computational study, the biological relevance of the findings is a key part of the impact. Speculative interpretations without experimental support or a clear mechanistic framework weaken the paper's contribution.
- **Resolution test** Either provide experimental validation (e.g., mutagenesis, binding assays) or clearly frame the biological interpretations as hypotheses, with a more rigorous discussion of their plausibility and testability.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and completeness of methods
- **Affected element** Methods section, "MD System Setup"
- **Evidence pointer** Methods section, "MD System Setup"
- **Issue** The description of the system preparation is incomplete. The specific sequence of the p53 construct (residue boundaries for NTD, DBD, TET, CTD) is not stated. The DNA sequence used (beyond "p21 response element") is not fully specified. The method for generating mutant starting structures is described only as "mutated manually," which is insufficient for reproducibility.
- **Required correction** Provide a complete description of the p53 construct, the exact DNA sequence, and a detailed protocol for generating mutant structures (e.g., specific software and rotamer selection criteria).

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results sections reporting quantitative values
- **Evidence pointer** Results sections "DNA, CTD and NTD Dynamics" and "L1/S3 Pocket"; Table 3, Table 4.
- **Issue** Quantitative results (e.g., DNA bending angles, pocket opening frequencies, SASA values) are reported as mean ± standard deviation, but the number of independent samples and the statistical tests used are not stated. It is unclear whether the reported differences between systems or monomers are statistically significant.
- **Required correction** Report the number of independent observations, the statistical tests used, and confidence intervals or p-values for key comparisons.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality and accessibility
- **Affected element** All figures
- **Evidence pointer** Fig 1–7
- **Issue** The figures are not provided, so their quality cannot be assessed. However, based on the text, some figures may be overly complex (e.g., Fig 5 with multiple panels and overlays) and may not be accessible to a broad readership.
- **Required correction** Ensure that all figures are clear, well-labeled, and accompanied by legends that explain the key findings in a way that is accessible to non-specialists.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Language and terminology
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The term "in situ dynamics" is used in the title and abstract but is not clearly defined. It could be confused with in-cell or in-vivo studies. The authors should clarify that they mean "in the context of the full-length tetramer bound to DNA" rather than in a cellular environment.
- **Required correction** Define "in situ" explicitly in the introduction and use consistent terminology throughout.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data Availability section
- **Evidence pointer** Data Availability section
- **Issue** The data availability statement points to a website, but the URL is not provided in the text. It is also unclear whether the data will be permanently archived in a public repository.
- **Required correction** Provide the full URL and consider depositing the data in a permanent public repository (e.g., Zenodo, figshare) to ensure long-term accessibility.

## Risk / unsupported claims
- The claim that the WT tetramer samples a "unique" clamped quaternary state not accessed by mutants is unsupported without evidence of sampling convergence and statistical comparison.
- The claim that the L6 pocket is "novel" is overstated given the recent publication of a ligand-bound structure (pdbID 8DC6).
- The speculation that G245S may conceal phosphorylation sites to evade degradation is not supported by any direct evidence and should be clearly labeled as a hypothesis.
- The claim that the simulations "elucidated the conformational landscape" is too strong given the lack of demonstrated convergence and the absence of experimental validation.
- The statement that the observed NTD–DBD interactions are "in line with" FRET and NMR studies is plausible but not quantitatively compared, so the degree of agreement is unclear.