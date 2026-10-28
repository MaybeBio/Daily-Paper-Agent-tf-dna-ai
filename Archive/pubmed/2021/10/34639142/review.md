## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Evaluation of the manuscript's claims, methods, results, and conclusions as presented in the provided text
- **Shared manuscript claim summary** The authors present the first systematic evaluation of four molecular docking programs (AutoDock Vina, DOCK 6, Glide, RxDock) for predicting small molecule binding poses to G-quadruplex (G4) DNA, using eight experimentally determined NMR structures of MycG4-ligand complexes. They report that DOCK 6 with GB/SA rescoring performs best, that docking accuracy is primarily limited by scoring functions rather than sampling, and that current docking programs should be used with caution for G4 DNA targets.
- **Visible evidence base** Abstract, Introduction, Results and Discussion sections 2.1-2.3, Materials and Methods sections 3.1-3.5, Conclusions, Tables 1-5, Figures 1-7 (referenced but not visible)
- **Missing materials affecting confidence** Tables 1-5 and Figures 1-7 are referenced but not provided in the supplied text. Specific numerical data (RMSD values, success rates per complex) are partially described in text but full tabulated results are unavailable. The PDB structure files and docking parameters are described but not independently verifiable from the text alone.

## Reviewer
- **Overall assessment** This manuscript addresses a relevant and under-explored question: how well do current docking programs perform for G4 DNA-ligand pose prediction? The study design is straightforward and the choice of MycG4 as a model system is justified. The authors provide a comparative analysis of four programs and offer practical recommendations. However, the manuscript has several weaknesses that limit the strength of its conclusions. The dataset is very small (eight complexes from four ligands), the analysis relies heavily on RMSD thresholds without statistical rigor, and the claim that scoring rather than sampling limits accuracy is not fully supported by the presented evidence. The manuscript would benefit from more detailed quantitative reporting, additional validation metrics, and a more cautious interpretation of the results.
- **Who would be interested in the results, and why** Researchers in computational drug discovery, particularly those working on nucleic acid targets, would find this study useful. The comparative benchmarking of docking programs for G4 DNA is novel and provides practical guidance for selecting tools and interpreting results. The study also highlights the need for G4-specific scoring function development, which could interest method developers in the computational chemistry community.
- **Major strengths** The study addresses a genuine gap in the literature, as no prior systematic evaluation of docking programs for G4 DNA exists. The use of experimentally determined NMR structures as a benchmark is appropriate. The comparison of four widely used programs (including both academic and commercial options) increases the practical relevance. The authors' recommendation to use chemical reasoning and knowledge of G4-ligand interactions as a filter is sensible and actionable.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim that "docking accuracy is mainly limited by the scoring functions" and that sampling is not the primary bottleneck.
  - **Evidence pointer** Section 2.3, Tables 1-5 (not visible)
  - **Concern** The claim that scoring rather than sampling limits accuracy is inferred from the observation that correct poses were sampled but not ranked at the top. However, the manuscript does not provide a systematic analysis of sampling completeness (e.g., whether the correct pose was ever generated across all runs, how many independent runs were performed, or whether sampling parameters were sufficiently exhaustive). Without this information, it is not possible to distinguish between scoring failures and sampling failures.
  - **Why it matters** This claim is central to the authors' conclusion and has implications for how users should approach G4 docking. If sampling is also inadequate, then simply improving scoring functions would not be sufficient. The distinction between scoring and sampling limitations is critical for guiding future method development.
  - **Resolution test** The authors should provide a detailed analysis of sampling performance, such as the number of runs that generated the correct pose, the distribution of RMSD values across all generated poses, and a comparison of sampling efficiency across programs. Alternatively, they could soften the claim to state that scoring appears to be a major limiting factor based on the observed pattern, without asserting that sampling is not also limiting.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical robustness
  - **Claim pointer** The authors report success rates (e.g., 12.5%, 25%, 37.5%, 50%) for the four programs based on eight complexes.
  - **Evidence pointer** Section 2.2, Tables 1-5 (not visible)
  - **Concern** The dataset consists of only eight complexes from four ligands, and the success rates are based on very small numbers. For example, a single correct ranking out of eight corresponds to 12.5%, and the difference between 37.5% (3/8) and 50% (4/8) is one complex. The manuscript does not report confidence intervals, statistical tests, or any measure of variability (e.g., across multiple docking runs). The conclusions about relative program performance are therefore fragile.
  - **Why it matters** The study's primary contribution is a comparative evaluation, but the small sample size and lack of statistical treatment undermine the reliability of the rankings. Readers may over-interpret differences that are not statistically meaningful.
  - **Resolution test** The authors should either (a) increase the dataset size (e.g., include more G4-ligand complexes from the literature or other G4 types), (b) perform multiple independent docking runs and report variability, or (c) explicitly acknowledge the limitations of the small sample size and avoid making strong comparative claims. At minimum, they should report per-complex results in full so readers can assess the pattern.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Methodological transparency
  - **Claim pointer** The authors state that "the docking pose is considered experimental-like if the ligand RMSD between the docked pose and the experimental NMR structure is less than 2.5 Å."
  - **Evidence pointer** Section 2.2, Materials and Methods 3.2-3.5
  - **Concern** The RMSD threshold of 2.5 Å is presented without justification. It is unclear whether this threshold is standard in the field, whether it was chosen a priori, or whether results would differ substantially with a different threshold (e.g., 2.0 Å or 3.0 Å). Additionally, the manuscript does not specify how RMSD was calculated (e.g., heavy atoms only, including hydrogens, symmetry-corrected) for all programs except DOCK 6, where symmetry correction is mentioned for BMVC.
  - **Why it matters** The choice of threshold directly affects all reported success rates. Without justification or sensitivity analysis, the results may be perceived as arbitrary. Inconsistent RMSD calculation methods across programs could also introduce bias.
  - **Resolution test** The authors should justify the 2.5 Å threshold with reference to prior literature or provide a sensitivity analysis showing how success rates change with different thresholds. They should also clearly state the RMSD calculation method used for each program and ensure consistency.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability
  - **Claim pointer** The authors conclude that "current docking programs should be used with caution to predict G4 DNA-small molecule binding modes" and that "virtual screening of a large library might not be feasible for G4 DNA at this time."
  - **Evidence pointer** Section 2.3, Conclusions
  - **Concern** The study only evaluates parallel G4 structures with short loops (MycG4). The authors acknowledge this in the Introduction but do not discuss how their findings might extend to other G4 topologies (e.g., antiparallel, hybrid) or to G4s with longer loops. The conclusion that virtual screening is not feasible is based on a single G4 system and may not be generalizable.
  - **Why it matters** The conclusions are framed broadly, but the evidence base is narrow. Readers working on other G4 types may not be able to extrapolate the findings. The manuscript would be stronger if it explicitly scoped its conclusions to parallel G4s with short loops and discussed potential differences for other topologies.
  - **Resolution test** The authors should either (a) include additional G4 structures of different topologies in the evaluation, (b) clearly limit their conclusions to the tested system and discuss why results might differ for other G4 types, or (c) frame the study as a case study rather than a general evaluation.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 2.2.1
  - **Evidence pointer** Section 2.2.1, Table 1 (not visible)
  - **Issue** The description of AutoDock Vina results states that "the experimental binding poses were only successfully sampled in four cases" but does not specify which complexes failed or whether the failures were consistent across binding sites.
  - **Required correction** Provide a per-complex breakdown of sampling success and failure for AutoDock Vina, either in the text or in a supplementary table.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section 2.2.2
  - **Evidence pointer** Section 2.2.2, Table 2 (not visible)
  - **Issue** The discussion of DOCK 6 results mentions that GB/SA rescoring improved ranking for specific complexes but does not explain why the rescoring failed for other complexes.
  - **Required correction** Add a brief discussion of potential reasons for rescoring failures (e.g., limitations of the GB/SA model for G4 systems) to provide a more complete interpretation.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Section 3.2
  - **Evidence pointer** Section 3.2
  - **Issue** The AutoDock Vina parameters (exhaustiveness=10, energy range=5) are stated, but the number of independent runs and the method for selecting the final pose are not described.
  - **Required correction** Specify the number of independent docking runs performed and how the final pose was selected (e.g., lowest energy, most populated cluster).
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Presentation
  - **Affected element** Section 2.3
  - **Evidence pointer** Section 2.3, Table 5 (not visible)
  - **Issue** The comparison table (Table 5) is described as summarizing results, but the text does not provide a clear narrative of which program performed best overall and under what conditions.
  - **Required correction** Add a summary paragraph in Section 2.3 that explicitly states the overall ranking of programs and highlights key differences in performance.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Section 2.2.3
  - **Evidence pointer** Section 2.2.3
  - **Issue** The term "Glide SP" is used without defining SP (standard precision) in the main text; it is only defined in the Methods section.
  - **Required correction** Define SP at first use in the Results section or move the definition to the Introduction.
  - **Concern ID** R1-m6
  - **Severity** Minor
  - **Axis** Consistency
  - **Affected element** Section 2.2.4
  - **Evidence pointer** Section 2.2.4
  - **Issue** The text states that RxDock "showed the same good sampling power as DOCK 6" but does not provide a quantitative comparison of sampling performance.
  - **Required correction** Provide a quantitative measure of sampling success (e.g., number of complexes where the correct pose was generated) for each program to support this comparison.

## Technical failings that need to be addressed before the case is established
- R1-M1: The claim that scoring rather than sampling limits accuracy is not adequately supported without a systematic analysis of sampling completeness.
- R1-M2: The small dataset and lack of statistical treatment undermine the reliability of comparative success rates.
- R1-M3: The RMSD threshold of 2.5 Å is not justified, and RMSD calculation methods are not fully specified for all programs.

## Risk / unsupported claims
- The claim that "docking accuracy is mainly limited by the scoring functions" is not fully supported by the evidence presented, as sampling completeness is not systematically analyzed.
- The conclusion that "virtual screening of a large library might not be feasible for G4 DNA at this time" is based on a single G4 system and may not be generalizable to other G4 topologies.
- The relative performance rankings of the four programs are based on a very small dataset and should be interpreted with caution.
- The statement that "most programs sampled the search space efficiently" is not quantitatively supported for all programs.

## Assessment against Nature-style criteria
- **Originality** The study addresses a question that has not been systematically examined before, namely the performance of docking programs for G4 DNA targets. This is a novel contribution to the field.
- **Scientific importance** The findings are of practical importance for researchers using docking in G4-targeted drug discovery. The study highlights limitations of current tools and provides guidance for their use. However, the narrow scope (one G4 topology, eight complexes) limits the broader impact.
- **Interdisciplinary readership** The topic sits at the intersection of computational chemistry, structural biology, and drug discovery. The manuscript is likely to appeal to a specialized audience rather than a broad interdisciplinary readership.
- **Technical soundness** The study design is reasonable, but the technical execution has weaknesses, including the lack of statistical analysis, incomplete reporting of sampling performance, and insufficient justification of the RMSD threshold. These issues need to be addressed to strengthen the technical foundation.
- **Readability for nonspecialists** The manuscript is generally well-written and accessible, with clear explanations of the docking programs and the G4 system. However, some sections assume familiarity with docking terminology and would benefit from brief definitions for nonspecialist readers.

## Recommendation posture
Supportive if technical concerns are resolved. The manuscript addresses a relevant and under-explored question, and the authors' practical recommendations are sensible. However, the current evidence does not fully support the central claim about scoring versus sampling limitations, and the small dataset requires more careful statistical treatment. If the authors can address these concerns, the manuscript would make a useful contribution to the field.