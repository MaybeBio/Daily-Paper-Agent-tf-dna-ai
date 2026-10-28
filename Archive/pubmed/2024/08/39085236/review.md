## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and support of claims based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors present a computational framework that integrates molecular dynamics-derived properties of ethidium bromide-intercalated DNA base-pair steps into a finite element model (SNUPI) to predict shape changes, flexibility modulation, and supercoiling instability in structured DNA assemblies, with quantitative validation against prior experimental data
- **Visible evidence base** Main text sections, figure legends for Figures 1-5, supplementary figure and table references, methods descriptions
- **Missing materials affecting confidence** Actual figure images, supplementary figures and tables, source data, experimental raw data, prior experimental references cited for validation, and code availability information

## Reviewer
- **Overall assessment** The manuscript presents a potentially valuable computational framework for predicting chemo-mechanical responses of DNA nanostructures to intercalating ligands. The approach of bridging MD-derived local properties to continuum finite element models is conceptually sound and addresses a real gap in the field. However, the validation strategy relies heavily on comparisons with previously published experimental data, and the manuscript as provided does not include sufficient quantitative detail to fully assess the accuracy and robustness of the predictions. The binding model, while simple, may oversimplify the complex intercalation process. The work is likely of interest to the DNA nanotechnology community, but several technical concerns need to be addressed before the claims are fully established.
- **Who would be interested in the results, and why** Researchers in structural DNA nanotechnology, particularly those working on dynamic DNA origami devices, mechanoresponsive DNA structures, and drug delivery applications using DNA nanostructures. The framework offers a pathway to computationally screen ligand effects on DNA nanostructure shape and mechanics, which could accelerate design of responsive DNA-based materials.
- **Major strengths** 1) Addresses an important and timely problem: predicting ligand-induced deformation of DNA nanostructures at scale. 2) The multiscale approach (MD to finite element) is well-motivated and builds on the authors' established SNUPI platform. 3) The framework is generalizable in principle to other intercalators and binding molecules. 4) The inclusion of a binding model connecting concentration to bound number is a practical step toward experimental relevance. 5) The range of validation cases (straight bundles, twisted structures, rings) demonstrates versatility.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** 
  - Originality: Moderate to high. The specific integration of MD-derived intercalator effects into a finite element framework for DNA origami is novel, though the individual components (MD of DNA-intercalator complexes, SNUPI) are established.
  - Scientific importance: Moderate. The work provides a useful design tool but does not reveal fundamentally new physics or biology. The importance is incremental rather than transformative.
  - Interdisciplinary readership: Moderate. Will appeal to DNA nanotechnologists, computational biophysicists, and potentially drug delivery researchers, but may be too specialized for a broad general audience.
  - Technical soundness: The core methodology is reasonable, but several aspects require clarification and additional validation (see Major Concerns). The reliance on prior experimental data without direct new experimental validation weakens the current evidence base.
  - Readability for nonspecialists: The manuscript is generally well-written and the figures are described clearly, but the methods sections assume significant background in both MD simulation and finite element analysis. The abstract is accessible.
- **Recommendation posture** Supportive if technical concerns are resolved. The framework is promising and likely publishable after addressing the validation, methodological clarity, and robustness issues outlined below.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation
- **Claim pointer** The authors claim quantitative agreement with experiments for shape changes, flexibility modulation, and supercoiling instability, but the manuscript does not provide direct quantitative comparisons with error metrics or statistical significance.
- **Evidence pointer** Figures 3-5, Supplementary Tables 2, 5, 6, 8
- **Concern** The validation of the proposed framework relies entirely on comparisons with previously published experimental data. However, the manuscript does not present quantitative error analyses, correlation coefficients, or statistical tests to support the claim of agreement. For example, in Figure 3c, the persistence length predictions are compared with experimental data, but no numerical values or confidence intervals are provided in the text. Similarly, in Figure 4b, the slopes of the linear fits are stated as -0.14 and -0.17 per 100 EtBr for simulation and experiment, but the uncertainty in these values and the goodness of fit are not reported. The supercoiling results in Figure 5 are compared qualitatively with prior AFM images, but no quantitative metric (e.g., writhe distribution comparison) is given.
- **Why it matters** The central claim of the paper is that the framework can quantitatively predict experimental observations. Without rigorous quantitative validation metrics, the accuracy and reliability of the framework cannot be properly assessed. This is critical for establishing the framework as a predictive design tool.
- **Resolution test** Provide quantitative comparison metrics for each validation case, including but not limited to: root-mean-square deviation between predicted and measured twist angles, confidence intervals for fitted parameters, statistical tests (e.g., chi-squared or Kolmogorov-Smirnov) for distribution comparisons, and error bars on all predicted quantities. For the supercoiling case, provide a quantitative measure of agreement such as the distribution of writhe values or the critical EtBr number compared with theory and experiment.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The authors state that "the same number of regular base-pair steps in random positions was converted into EtBr-binding base-pair steps" and that binding positions were chosen considering "minor steric hindrance that binding probability has similar levels between inner and outer helices."
- **Evidence pointer** Methods section "SNUM simulations", Figure 3d, Supplementary Table 4
- **Concern** The treatment of binding site selection is a critical component of the model, yet the methodology is described only briefly. The authors state that binding positions are random but do not specify the exact algorithm used, the number of random configurations sampled per condition, or how the results depend on the specific choice of binding sites. The assumption of uniform binding probability between inner and outer helices is stated to be supported by prior studies, but the sensitivity of the predictions to this assumption is not explored. Furthermore, the binding model assumes independent, non-cooperative binding with a fixed dissociation constant, which may not hold at high EtBr concentrations or for specific DNA sequences.
- **Why it matters** The spatial distribution of intercalated EtBr molecules directly affects the predicted deformation. If the model is sensitive to binding site selection, the results may not be robust. The lack of sensitivity analysis undermines confidence in the framework's predictive power and generalizability.
- **Resolution test** Provide a detailed description of the binding site selection algorithm, including how randomness is implemented and how many random configurations are averaged. Perform a sensitivity analysis by varying the binding site distribution (e.g., clustered vs. uniform, inner vs. outer helix bias) and report the effect on predicted twist angles, persistence lengths, and supercoiling behavior. Justify the assumption of uniform binding probability with additional data or a more sophisticated binding model.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors claim that the framework can be generalized to other ligands and DNA structures, and that it enables rational design of DNA assemblies with tunable properties.
- **Evidence pointer** Discussion section, Methods section
- **Concern** The manuscript does not provide sufficient information for others to reproduce the work. Key details are missing: (1) the specific MD simulation parameters (force field versions, water model details, ion concentrations, simulation box size, equilibration protocol) are only partially described; (2) the finite element model parameters (element type, mesh density, material properties for regular vs. EtBr-bound steps) are not fully specified; (3) the code for the framework is not mentioned as being available; (4) the methods for calculating persistence length from normal mode analysis are not described in sufficient detail. Without these details, the work cannot be independently replicated or extended.
- **Why it matters** Reproducibility is a cornerstone of scientific progress. For a computational framework that is intended to be a design tool, the lack of detailed methodological information and code availability significantly limits its utility to the community.
- **Resolution test** Provide complete methodological details in the main text or supplementary information, including all simulation parameters, model construction steps, and analysis procedures. Make the code and input files publicly available (e.g., on GitHub or a similar repository) and provide a link in the manuscript. Include a detailed description of the normal mode analysis procedure for persistence length calculation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scope of claims
- **Claim pointer** The authors state that the proposed model "captures various structural changes induced by EtBr-binding such as shape variation, flexibility modulation, and supercoiling instability" and that it "enables a rational design of structured DNA assemblies with tunable shapes and mechanical properties by binding molecules."
- **Evidence pointer** Abstract, Results sections "Shape variation", "Flexibility modulation", "Supercoiling instability", Discussion
- **Concern** The manuscript demonstrates the framework on a limited set of DNA structures (straight bundles, twisted bundles, rings) and only for EtBr. The claim of generalizability to other ligands and structures is not supported by evidence in the current manuscript. The framework's ability to predict the effects of other intercalators or groove binders, which may have different binding modes and local effects, is speculative. Additionally, the framework assumes that the local effects of EtBr on base-pair steps are independent of the surrounding structural context, which may not hold for all DNA nanostructures.
- **Why it matters** Overstating the generalizability of the framework could mislead other researchers into applying it beyond its validated range, potentially leading to incorrect predictions. The scope of the claims should match the evidence provided.
- **Resolution test** Either temper the claims of generalizability in the abstract and discussion, or provide additional validation cases with different ligands and/or a wider range of DNA structures. If the framework is intended to be general, demonstrate its applicability to at least one other intercalator or binding molecule with different binding characteristics.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The schematic in Figure 1 is dense and the flow is not immediately clear. The relationship between the MD simulation box, the base-pair step properties, and the finite element model could be better illustrated with a clearer step-by-step layout.
- **Required correction** Consider revising Figure 1 to have a clearer left-to-right or top-to-bottom flow, with labeled steps (e.g., "Step 1: MD simulation", "Step 2: Property extraction", "Step 3: Finite element integration", "Step 4: Prediction").

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 3c, Supplementary Table 2
- **Evidence pointer** Figure 3c, Supplementary Table 2
- **Issue** The box plots in Figure 3c and the persistence length results in Supplementary Table 2 do not report the number of independent simulations or the statistical significance of differences between regular and EtBr-bound cases.
- **Required correction** Add sample sizes and statistical test results (e.g., p-values) to the figure legends and table captions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract, Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The term "chemo-mechanical" is used throughout but is not explicitly defined. While the meaning is likely clear to specialists, a brief definition would improve accessibility.
- **Required correction** Add a brief definition or explanatory phrase when the term is first used, e.g., "chemo-mechanical (i.e., ligand-binding-induced mechanical)".

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section "SNUM simulations"
- **Evidence pointer** Methods section "SNUM simulations"
- **Issue** The methods state that "the same number of regular base-pair steps in random positions was converted into EtBr-binding base-pair steps" but do not specify how the number of EtBr molecules is determined for a given concentration in the simulations, beyond the binding model equation.
- **Required correction** Clarify the procedure for converting a target EtBr concentration to a specific number of bound EtBr molecules in the simulation, including how the total number of base-pairs in the structure is calculated.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction, Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The introduction and discussion could benefit from a more explicit comparison with other computational approaches for predicting DNA nanostructure mechanics, such as coarse-grained molecular dynamics (e.g., oxDNA) or other finite element methods.
- **Required correction** Add a brief paragraph in the introduction or discussion situating the proposed framework relative to existing computational methods, highlighting the specific advantages and limitations.

## Risk / unsupported claims
- The claim that the framework "enables a rational design of structured DNA assemblies with tunable shapes and mechanical properties by binding molecules" is not directly demonstrated in the manuscript. No design example is shown where the framework was used to predict and then experimentally verify a new structure with desired properties.
- The claim that the binding model is in agreement with reported values (Kd = 3.2 ± 0.6 μM, Ξ = 7.3 ± 0.2 base-pair/EtBr) is stated, but the comparison with specific literature values is not shown in detail. The reader cannot assess the quality of this agreement.
- The statement that "the proposed model successfully predicted EtBr-driven shape changes, flexibility modulation, and supercoiling instability of various DNA origami structures, in agreement with experiments" is a strong claim. While the results sections describe qualitative agreement, the lack of quantitative metrics (as noted in R1-M1) means this claim is not fully supported by the provided evidence.
- The assumption that EtBr binding does not significantly affect single-stranded DNA is stated but not validated in the context of the structures studied, some of which may contain single-stranded regions.
- The generalizability of the framework to other ligands is asserted but not tested. The local effects of different intercalators or groove binders on base-pair step geometry and mechanics may differ significantly from EtBr.