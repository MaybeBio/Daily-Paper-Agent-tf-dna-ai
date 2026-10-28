## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the supplied abstract; no figures, tables, methods, or supplementary materials were provided
- **Shared manuscript claim summary** The authors report a computational workflow combining lanmodulin binding-site engineering with multireference quantum chemistry (CASSCF/CASPT2) to prioritize dysprosium over other rare-earth and competing metal ions. The workflow reduces 66 candidate positions to 3 finalist pockets, all retaining rare-earth binding. The top pocket shows favorable local confidence and stability metrics but does not suppress aluminum or iron binding. A compact Dy(III)/Nd(III) cluster is characterized with multireference methods, confirming a valid 4f manifold.
- **Visible evidence base** Abstract text only; no quantitative results, structural coordinates, scoring data, or methodological details are visible
- **Missing materials affecting confidence** Full methods, all figures and tables, sequence alignments, scoring distributions, structural validation metrics, CASSCF/CASPT2 convergence data, active-space details, and any experimental validation

## Reviewer
- **Overall assessment** The abstract presents a plausible computational pipeline with a clear design rationale and an honest acknowledgment of the key limitation (competitor suppression). However, the evidence base is insufficient to evaluate the central claims. No quantitative data are provided for pocket ranking, binding stability, or quantum-chemical convergence. The claim of a "deterministic" workflow is not supported by the described use of stochastic sequence-design tools. The scientific premise is interesting and the target problem is relevant, but the current abstract does not establish the case.
- **Who would be interested in the results, and why** Researchers in rare-earth separations, metalloprotein engineering, computational enzyme design, and quantum chemistry applied to f-element systems. The work addresses a pressing sustainability problem in critical-element supply chains and could inform future design strategies for selective lanthanide-binding proteins.
- **Major strengths** The problem is well-motivated and practically important. The workflow integrates multiple computational tools in a staged manner, which is a sensible strategy. The authors explicitly acknowledge that aluminum and iron capture persists, which is an honest and useful negative result. The use of multireference methods for f-element systems is appropriate and technically demanding.
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
- **Technical failings that need to be addressed before the case is established** The absence of any quantitative evidence for the ranking, the lack of convergence metrics for the quantum calculations, the unsupported use of the term "deterministic," and the absence of any experimental or orthogonal validation for the predicted selectivity.
- **Assessment against Nature-style criteria** 
  - Originality: The combination of lanmodulin engineering with multireference quantum characterization is not entirely novel but is a reasonable integration of existing methods. The specific application to dysprosium prioritization is timely.
  - Scientific importance: The problem is important, but the abstract does not demonstrate a breakthrough or a clear advance over existing approaches.
  - Interdisciplinary readership: The work spans protein engineering, computational chemistry, and separations science, which could attract a broad audience if the results are compelling.
  - Technical soundness: Cannot be assessed from the abstract alone. The described methods are appropriate in principle, but no validation data are shown.
  - Readability for nonspecialists: The abstract is reasonably clear but uses field-specific terms without sufficient context for a general audience.
- **Recommendation posture** Currently not established from the provided evidence. The authors should provide quantitative results, convergence data, and a clearer demonstration of the claimed selectivity before the case can be considered.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "The workflow reduced 66 evaluated mask positions to 3 finalists while retaining rare-earth binding in all cases."
- **Evidence pointer** Abstract only; location not provided
- **Concern** No quantitative data are provided to support the reduction from 66 to 3 positions. There are no scores, thresholds, or ranking criteria shown. The claim that rare-earth binding is retained "in all cases" is presented without any supporting metrics.
- **Why it matters** The central contribution of the workflow is the selection of a small number of candidate pockets. Without evidence of the scoring distributions, the selection criteria, or the validation of binding retention, the reader cannot assess whether the reduction is meaningful or arbitrary.
- **Resolution test** Provide the full ranking table with scores for all 66 positions, the thresholds used at each filtering stage, and quantitative measures of binding retention (for example, interaction energies or structural metrics) for the 3 finalists.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "The top-ranked Hans-derived pocket showed the strongest local confidence signal, the lowest pocket free-energy proxy, and stable rare-earth coordination."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The terms "local confidence signal," "pocket free-energy proxy," and "stable rare-earth coordination" are not defined, and no numerical values are given. It is impossible to evaluate whether the differences between the top pocket and the other two finalists are significant or within noise.
- **Why it matters** The selection of the top pocket is the key decision in the workflow. Without quantitative comparisons, the reader cannot determine whether the choice is robust or whether the differences are marginal.
- **Resolution test** Provide the numerical values for each metric for all 3 finalists, including error estimates or confidence intervals, and define the metrics precisely in the methods.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Compact Dy(III) and Nd(III) coordination clusters were extracted and characterized with CASSCF and CASPT2 using a 4f active space, confirming a physically valid 4f manifold for each metal and a well-converged multireference description."
- **Evidence pointer** Abstract only; location not provided
- **Concern** No convergence data, active-space details, or validation metrics are provided for the quantum-chemical calculations. The claim of a "well-converged multireference description" is unsupported without showing, for example, the weight of the leading configurations, the size of the active space, or the basis-set dependence.
- **Why it matters** Multireference calculations on f-element systems are notoriously sensitive to active-space choice and convergence. The claim of a valid 4f manifold is central to the quantum-characterization aspect of the work and must be backed by rigorous evidence.
- **Resolution test** Provide the active-space composition, the leading configuration weights, the CASPT2 weights, and convergence checks with respect to active-space size and basis set.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim validity
- **Claim pointer** "We report a deterministic computational workflow"
- **Evidence pointer** Abstract only; location not provided
- **Concern** The workflow uses ProteinMPNN, LigandMPNN, and Rosetta, all of which are stochastic or heuristic methods. The term "deterministic" is therefore misleading unless the authors have taken specific steps to ensure reproducibility, such as fixing random seeds and reporting them.
- **Why it matters** The claim of determinism is a strong statement about reproducibility. If the workflow is not actually deterministic, the claim is inaccurate and could mislead readers about the reliability of the results.
- **Resolution test** Clarify the meaning of "deterministic" in this context, report the random seeds used, and demonstrate that repeated runs produce identical results.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "harmonized" in "Four experimentally solved lanmodulin structures were harmonized" is vague. It is unclear whether this refers to structural alignment, sequence alignment, or some other preprocessing step.
- **Required correction** Specify the exact procedure used to harmonize the structures, such as structural superposition or sequence-based alignment.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Experimental validation
- **Evidence pointer** Abstract; location not provided
- **Issue** No experimental validation is mentioned. The abstract describes only computational results.
- **Required correction** State explicitly whether experimental validation was performed, and if not, acknowledge this as a limitation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract; location not provided
- **Issue** The phrase "dysprosium prioritization" is used but not defined. It is unclear whether this means preferential binding, selective extraction, or something else.
- **Required correction** Define the term clearly in the introduction or results.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Comparison to prior work
- **Evidence pointer** Abstract; location not provided
- **Issue** No comparison is made to existing lanmodulin engineering efforts or other computational approaches for rare-earth selectivity.
- **Required correction** Add a brief comparison to prior work to contextualize the novelty of the approach.

## Risk / unsupported claims
- The claim of a "deterministic" workflow is unsupported and likely inaccurate given the stochastic nature of the tools used.
- The claim of "well-converged multireference description" is unsupported without convergence data.
- The claim that rare-earth binding is retained "in all cases" is unsupported without quantitative metrics.
- The relative performance of the top pocket versus the other two finalists is not assessable without numerical values.
- The overall selectivity of the designed pocket for dysprosium over neodymium, yttrium, aluminum, and iron is not demonstrated with any quantitative data.