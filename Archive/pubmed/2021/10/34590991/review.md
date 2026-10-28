## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose a novel variant of the artificial bee colony optimization algorithm for mining common structural motifs in DNA binding proteins, specifically the Helix Turn Helix pattern. They report faster convergence on benchmark functions, superior motif feature quality, 92% agreement with existing motif detection tools, high sensitivity/specificity/AUC values, and a docking-based druggability strategy targeting motif locations.
- **Visible evidence base** Abstract text only; no methodological details, quantitative results, or experimental protocols are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, benchmark function definitions, dataset descriptions, comparison method details, statistical analysis, docking protocol, and code availability

## Reviewer

- **Overall assessment** The abstract presents a potentially useful application of swarm intelligence to protein motif discovery, but the claims are broad and largely unsupported by the evidence visible in the abstract. The core novelty of the algorithm variant is not described with sufficient specificity, and the reported performance metrics lack the contextual detail needed to assess their validity. The druggability component is mentioned only as a discussion point, which limits its contribution to the stated aims. The work may be of interest to computational biologists working on motif prediction, but the current evidence base is insufficient to establish the case.

- **Who would be interested in the results, and why** Researchers in computational biology and bioinformatics, particularly those working on protein structure analysis, motif discovery, and swarm intelligence applications. The proposed optimization framework could appeal to groups developing new algorithms for sequence or structure pattern mining. The druggability angle may attract investigators in structural pharmacology, though the abstract provides only a preliminary indication of this direction.

- **Major strengths** The abstract identifies a clear problem, namely the extraction of structural motifs from DNA binding proteins, and proposes a specific algorithmic solution. The use of a well-known optimization paradigm, artificial bee colony, provides a familiar foundation. The reported comparison with existing motif detection tools and the inclusion of multiple performance measures suggest an intention to validate the approach empirically. The mention of a druggability strategy indicates potential translational relevance.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The proposed algorithm variant improves the exploitation process and shows speedier convergence on four benchmark objective functions.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract does not describe the specific modification to the artificial bee colony algorithm that constitutes the claimed novelty. No details are given on how exploitation is enhanced, what parameters are adjusted, or how the variant differs from existing ABC implementations. The benchmark functions are named only as "four benchmark objective functions" without identification, and the dimensions tested are not specified.
- **Why it matters** Without a clear description of the algorithmic innovation, the contribution cannot be distinguished from prior ABC variants. The convergence claim is unverifiable without knowing the benchmark functions, the comparison baselines, and the experimental setup. This is the central technical claim of the work.
- **Resolution test** The full manuscript must provide a precise algorithmic description, identify the benchmark functions and dimensions, and present convergence curves or numerical comparisons against at least one standard ABC variant and one other optimization method.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The algorithm generated optimum features of the Helix Turn Helix structural pattern based on an objective function defined with occurrence count on secondary structure.
- **Evidence pointer** Abstract, location not provided
- **Concern** The objective function is mentioned but not defined. The term "optimum features" is vague and does not specify what constitutes optimality in this context. The relationship between the optimization framework and the biological validity of the resulting motif features is not established.
- **Why it matters** The quality of the generated motif features is a core outcome of the work. Without a clear definition of the objective function and the feature set, the reader cannot assess whether the optimization is biologically meaningful or merely computationally convenient.
- **Resolution test** The manuscript must define the objective function mathematically, list the feature set, and provide evidence that the optimized features correspond to known structural properties of Helix Turn Helix motifs.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** 92% of tested proteins produced matching locations with the results of the compared methods, and the approach showed higher sensitivity, specificity, and area under the curve values.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract reports a single percentage for location matching and claims higher sensitivity, specificity, and AUC without providing the actual values, the number of proteins tested, the identity of the compared methods, or any statistical significance testing. The phrase "higher" is relative and requires a defined comparator.
- **Why it matters** These metrics are the primary quantitative evidence for the method's utility. Without the underlying numbers, the comparison context, and error estimates, the claims cannot be evaluated or reproduced.
- **Resolution test** The full manuscript must report the number of test proteins, the specific compared tools, the exact sensitivity, specificity, and AUC values with confidence intervals, and appropriate statistical tests for differences.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scope and relevance
- **Claim pointer** A novel strategy for druggability finding by docking studies, targeting the motif locations, is also discussed.
- **Evidence pointer** Abstract, location not provided
- **Concern** The druggability component is presented as a discussion point only, with no results, no docking targets, no ligand information, and no validation. This claim is not supported by any visible evidence.
- **Why it matters** The title and abstract imply that druggability is a significant contribution, but the abstract provides no substantive content on this aspect. This creates a mismatch between the stated scope and the actual content.
- **Resolution test** The manuscript must either provide docking results with defined targets and ligands, or the abstract and title should be revised to reflect that druggability is only a proposed future direction.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Title and abstract alignment
- **Evidence pointer** Abstract, location not provided
- **Issue** The title emphasizes druggability, but the abstract focuses primarily on motif mining and algorithm performance. The druggability discussion appears only at the end.
- **Required correction** Ensure the abstract reflects the actual balance of content, or adjust the title to better represent the primary contribution.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Benchmark and dataset description
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not identify the benchmark functions, the protein dataset, or the source of the DNA binding proteins used.
- **Required correction** The full manuscript must provide complete details on benchmark functions, dataset composition, and data availability.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Use of "optimum features"
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "optimum features" is ambiguous and could refer to feature selection, feature generation, or parameter optimization.
- **Required correction** Define precisely what is meant by "optimum features" in the context of the objective function and the motif model.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Comparison completeness
- **Affected element** Comparison with other motif detection tools
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that motif locations were compared with two other tools but does not name them or describe the comparison criteria.
- **Required correction** Name the comparison tools and describe the matching criteria used to determine agreement.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Performance measures
- **Evidence pointer** Abstract, location not provided
- **Issue** Sensitivity, specificity, and AUC are mentioned without numerical values or the context of the classification task.
- **Required correction** Report the actual values and define the positive and negative classes used in the evaluation.

## Risk / unsupported claims

- The claim of "speedier convergence" is unsupported without benchmark function identities, dimensions, and comparison baselines.
- The claim of "optimum features" is unsupported without a definition of the objective function and the feature set.
- The 92% matching rate is unsupported without the number of proteins, the identity of comparison tools, and the matching criteria.
- The claim of "higher sensitivity, specificity and area under the curve values" is unsupported without actual values and statistical context.
- The druggability strategy is unsupported as it is presented only as a discussion point with no results.
- The novelty of the algorithm variant is unassessable from the abstract alone.