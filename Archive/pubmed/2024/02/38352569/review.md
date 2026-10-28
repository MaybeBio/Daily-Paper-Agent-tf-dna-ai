## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv 2024.01.28.577658)
- **Assessment boundary** Scientific content, methodological soundness, claims vs. evidence, and presentation quality as presented in the provided text. No external validation or replication performed.
- **Shared manuscript claim summary** The authors present a computational pipeline that simulates single-cell expression data from thermodynamic and non-equilibrium models of transcriptional regulation, generates synthetic MPRA datasets, and evaluates how experimental and biological parameters (mutation rate, library size, transcription factor copy number, binding energy, regulatory logic, non-specific binding, overlapping sites, inducer concentration, and broken detailed balance) affect the interpretability of information footprints and expression shift matrices. They argue this framework aids in designing MPRA experiments and interpreting their outputs for regulatory architecture inference.
- **Visible evidence base** Main text figures referenced (Figs 1–15), equations (Eqs 1–17, 40–47), supplementary appendices (S1–S15) described but not provided in full. No raw data, code output, or experimental validation included in the reviewed text.
- **Missing materials affecting confidence** Supplementary appendices (S1–S15) are cited but not available in the reviewed scope. Figure contents are described but not visually inspectable. No code execution or reproducibility check possible. No comparison to experimental MPRA datasets beyond literature references.

## Reviewer
- **Overall assessment** This manuscript provides a conceptually valuable and timely contribution: a systematic, theory-driven simulation platform for MPRA data generation and interpretation. The authors address important gaps in the field, particularly the lack of a "theory of the experiment" for high-throughput regulatory assays. The work is clearly motivated, well-structured, and demonstrates technical competence in statistical mechanics and computational modeling. However, the manuscript's central claims—that the pipeline can optimize experimental design and reveal limits of MPRA interpretation—are supported primarily through illustrative simulations rather than rigorous quantitative validation or benchmarking against experimental data. Several key results are presented qualitatively, and the non-equilibrium extension, while promising, is preliminary. The paper would be strengthened by more systematic parameter sweeps, quantitative metrics for signal detection, and direct comparison to experimental MPRA datasets.
- **Who would be interested in the results, and why** Researchers in gene regulation, quantitative biology, and systems biology, particularly those using or developing MPRA, Sort-Seq, Reg-Seq, or similar high-throughput reporter assays. The work will also appeal to theorists interested in statistical mechanics models of transcription and to experimentalists seeking guidance on library design and data interpretation. The discussion of non-equilibrium effects and broken detailed balance broadens relevance to those studying energy-consuming regulatory processes.
- **Major strengths**
  1. Addresses a significant and underappreciated problem: the need for a quantitative, predictive framework to interpret MPRA data.
  2. The use of energy matrices to generate sequence-specific binding energies is a principled and powerful approach.
  3. Systematic exploration of multiple parameters (mutation rate, library size, copy number, binding energy, regulatory logic, inducer concentration) provides a broad and useful map of factors affecting information footprints.
  4. The analytical derivation of optimal mutation rate (κ = 1 condition) is elegant and practically useful.
  5. The extension to non-equilibrium models via graph-theoretic methods is forward-looking and demonstrates intellectual ambition.
  6. Clear writing and logical organization; equations are well-motivated and explained.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim the pipeline "demonstrates our ability to optimize MPRA experimental designs with the goal of generating thermodynamic models of the transcriptome with base-pair specificity" (Abstract) and that it "establishes a systematic way of testing how well high-throughput methods such as the MPRAs can be used to recover the ground truth" (Discussion).
  - **Evidence pointer** Results sections 1–4; Figures 3–15; location not provided for specific figure panels
  - **Concern** The central claim of optimizing experimental design and recovering ground truth is not rigorously demonstrated. The simulations show qualitative trends (e.g., signal decreases with higher mutation rate, disappears with high repressor copy number), but no quantitative metrics are provided for detection accuracy, false positive/negative rates, or statistical power as a function of parameters. The "ground truth" is known by construction in simulations, but the authors do not systematically evaluate how often their inference pipeline correctly identifies binding sites across a range of conditions. Without such benchmarks, the claim of optimization is not established.
  - **Why it matters** The stated purpose of the pipeline is to guide experimental design and interpretation. If the authors cannot quantify how parameter choices affect inference accuracy, the practical utility of the framework is unclear. A reader cannot determine, for example, what mutation rate or library size to choose for a given transcription factor and desired detection sensitivity.
  - **Resolution test** Provide quantitative benchmarks: e.g., for each parameter regime, compute the area under the ROC curve or precision-recall for binding site identification, and show how this varies with mutation rate, library size, copy number, etc. Alternatively, demonstrate that the pipeline can recover known regulatory architectures from experimental MPRA datasets (e.g., from Ireland et al. 2020) with high accuracy.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The authors state that "the use of κ lays the groundwork for finding the optimal rate of mutation in a mutant library" and derive κ = 1 as the condition for balanced signals (Section 2.1, Eq 16).
  - **Evidence pointer** Section 2.1, Eqs 12–16; Figure 4; location not provided
  - **Concern** The derivation of optimal mutation rate relies on several simplifying assumptions: (i) the average effect of mutations per base pair is uniform across binding sites (Eq 14), (ii) mutations are independent, and (iii) the signal at a binding site is directly proportional to the change in binding energy. These assumptions are not tested. Real energy matrices have position-dependent effects, and mutation effects can be highly non-additive (as the authors acknowledge for epistasis). The claim that κ = 1 is "optimal" is therefore not robustly established.
  - **Why it matters** The optimal mutation rate is a key practical output of the paper. If the derivation is based on assumptions that do not hold in real systems, the recommended mutation rate may be suboptimal or misleading for experimental design.
  - **Resolution test** Test the robustness of the κ = 1 prediction by: (1) using energy matrices with varying degrees of position-dependent effects, (2) incorporating epistatic interactions, and (3) simulating non-uniform mutation effects. Show that the optimal mutation rate remains near the predicted value, or provide a revised formula that accounts for these complexities.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scope and generalizability
  - **Claim pointer** The authors claim the pipeline can be used to "decipher regulatory architectures" and "explore regulatory evolution" (Abstract, Discussion).
  - **Evidence pointer** Sections 2–4; Figures 7–15; location not provided
  - **Concern** The manuscript focuses almost exclusively on simple repression and simple activation architectures, with brief extensions to double repression (AND/OR logic) and non-equilibrium cases. The claim of deciphering "regulatory architectures" broadly is not supported by the limited set of architectures considered. Real regulatory regions often involve complex combinations of activators, repressors, cooperative interactions, and chromatin state, none of which are systematically addressed. The non-equilibrium treatment is explicitly preliminary and only considers a single broken edge.
  - **Why it matters** The stated goal is to provide a general framework for understanding regulatory architecture. If the pipeline cannot handle the complexity of real regulatory regions, its utility is limited to simple synthetic cases, and the broader claims are overstated.
  - **Resolution test** Expand the analysis to include more complex architectures (e.g., activator-repressor combinations, cooperative binding, multiple transcription factor binding sites with overlapping and competitive interactions). Demonstrate that the pipeline scales and remains interpretable for these cases, or clearly delineate the scope of applicability.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility and transparency
  - **Claim pointer** The authors state "All code used in this work and the presented figures are available open source" (Data Availability).
  - **Evidence pointer** Data Availability section; location not provided
  - **Concern** While code availability is commendable, the manuscript does not provide sufficient detail on simulation parameters, random seeds, or the specific procedures used to generate each figure. The supplementary appendices are cited but not available in the reviewed scope. Without these details, independent replication of the results is not possible.
  - **Why it matters** Reproducibility is a core requirement for computational work. If the simulation procedures are not fully documented, the results cannot be verified, and the scientific claims are weakened.
  - **Resolution test** Provide a complete description of simulation parameters, initialization, and analysis procedures in the main text or appendices. Include version numbers for all software dependencies. Ideally, provide a containerized environment or workflow that reproduces all figures from raw simulation output.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 1 description
  - **Evidence pointer** Section 1.1, Figure 1; location not provided
  - **Issue** The description of Figure 1 is brief and does not clearly explain the workflow. It is unclear what each panel represents and how the reader should interpret the flow from sequence to information footprint.
  - **Required correction** Expand the figure legend and add a step-by-step description in the text, clearly labeling each stage of the pipeline (e.g., sequence generation, energy calculation, expression prediction, MPRA simulation, summary statistic computation).
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Use of "single-cell" in title and abstract
  - **Evidence pointer** Title, Abstract; location not provided
  - **Issue** The term "single-cell" is used in the title and abstract, but the simulations produce bulk expression levels (mean mRNA counts) for each promoter variant, not single-cell distributions. This is potentially misleading.
  - **Required correction** Clarify that the simulations produce population-averaged expression levels, or explicitly state that single-cell variability is not modeled. If single-cell distributions are intended, the model must incorporate stochastic gene expression (e.g., via the chemical master equation or Langevin dynamics).
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Non-equilibrium section
  - **Evidence pointer** Section 4, Figure 15; location not provided
  - **Issue** The non-equilibrium treatment is described as preliminary, but the authors do not discuss the biological relevance of the specific edge where detailed balance is broken (AP→A). It is unclear what biological process this corresponds to and why this choice is meaningful.
  - **Required correction** Provide biological context for the choice of broken edge and discuss what experimental systems or conditions might exhibit such non-equilibrium behavior. If the choice is arbitrary, state this explicitly and discuss the range of possible non-equilibrium scenarios.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Presentation
  - **Affected element** Discussion of limitations
  - **Evidence pointer** Discussion; location not provided
  - **Issue** The limitations section is brief and focuses on combinatorial explosion. Other important limitations are not discussed, such as the neglect of chromatin state, nucleosome positioning, and post-transcriptional regulation.
  - **Required correction** Expand the limitations discussion to acknowledge these additional simplifications and their potential impact on the applicability of the pipeline to real regulatory regions.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Consistency
  - **Affected element** Terminology for "signal"
  - **Evidence pointer** Section 1.3, Eq 11; location not provided
  - **Issue** The term "signal" is used to mean average mutual information at binding sites, but this is not explicitly defined in the main text. The reader must infer this from context.
  - **Required correction** Define "signal" explicitly when first introduced, and consider using a more descriptive term such as "mean binding-site mutual information" to avoid ambiguity.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of quantitative benchmarks for binding site detection accuracy across parameter regimes.
  - R1-M2: Optimal mutation rate derivation relies on untested simplifying assumptions.
  - R1-M3: Limited scope of regulatory architectures considered relative to the broad claims made.
  - R1-M4: Insufficient detail for reproducibility of simulations.
- **Assessment against Nature-style criteria**
  - **Originality** High. The concept of a "theory of the experiment" for MPRA is novel and addresses a real gap. The use of energy matrices to generate sequence-specific predictions is a creative and principled approach. The non-equilibrium extension, while preliminary, is original.
  - **Scientific importance** Moderate to high. The work has clear practical implications for the design and interpretation of MPRA experiments, which are widely used. However, the importance is tempered by the lack of quantitative validation and the limited scope of architectures considered. The paper is more of a proof-of-concept than a definitive framework.
  - **Interdisciplinary readership** Moderate. The work bridges statistical mechanics, computational biology, and experimental genomics. It will appeal to quantitative biologists and theorists, but may be less accessible to purely experimental or genomics-focused readers without a strong physics background.
  - **Technical soundness** Moderate. The thermodynamic models are well-established and correctly applied. The computational pipeline is logically constructed. However, the lack of quantitative benchmarks, the untested assumptions in the optimal mutation rate derivation, and the preliminary nature of the non-equilibrium section weaken the technical case.
  - **Readability for nonspecialists** Moderate. The writing is clear and the equations are well-motivated. However, the manuscript assumes familiarity with statistical mechanics, information theory, and MPRA methodology. The abstract is accessible, but the main text would be challenging for a general scientific audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important problem with a novel and promising approach. However, the central claims of optimization and general applicability are not currently established from the provided evidence. The authors should provide quantitative benchmarks, test the robustness of their key derivations, and either expand the scope or temper the claims. With these revisions, the paper could make a significant contribution to the field.

## Risk / unsupported claims
- The claim that the pipeline can "optimize MPRA experimental designs" is not supported by quantitative benchmarks or comparison to alternative design strategies.
- The claim that the pipeline can "decipher regulatory architectures" broadly is not supported by the limited set of architectures (simple repression, simple activation, double repression with AND/OR logic) considered.
- The claim that information footprints are "robust to extrinsic noise" is based on simulations with log-normal distributions but lacks comparison to experimentally measured noise levels or alternative noise models.
- The non-equilibrium extension is described as preliminary, but the biological relevance and generalizability of the specific broken edge (AP→A) are not discussed.
- The optimal mutation rate derivation (κ = 1) is presented as a general result but relies on assumptions (uniform mutation effects, independence) that are not tested against realistic energy landscapes.
- The statement that "over 80% of promoters in E. coli fall under the six regulatory architectures" is cited to RegulonDB but not verified in the provided text; the basis for this claim is not shown.