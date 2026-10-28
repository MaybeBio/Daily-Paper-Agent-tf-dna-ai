## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors investigate the multistate B- to A- conformational transition in protein-DNA complexes using AMBER force fields (OL15, bsc1, and an experimental combination OL15chi(OL3)). They report that A-like intermediate geometries match native X-ray structures but their populations are underestimated by all tested force fields, with the order of propensity OL15 < bsc1 < OL15chi(OL3). They further claim that force fields predict correct sequence-dependent A-form propensity and that the instability of A-like geometries destabilizes simulated protein-DNA complexes, implying a need for force field refinement.
- **Visible evidence base** Abstract text only; no numerical data, simulation protocols, statistical analyses, or structural comparisons are provided
- **Missing materials affecting confidence** Full manuscript, simulation details, force field parameters, definitions of A/B states and intermediate states, population quantification methods, error bars or convergence criteria, structural figures, and any comparison with experimental data beyond the abstract statement

## Reviewer
- **Overall assessment** The abstract addresses a relevant and timely question in computational biophysics, namely the accuracy of AMBER force fields in capturing the multistate B- to A- transition at protein-DNA interfaces. The conceptual framing of intermediate states as combinations of sugar pucker and glycosidic torsion is sound and useful. However, the abstract alone provides insufficient detail to evaluate the robustness of the claims. The central conclusion that all force fields underestimate A-like populations is stated without quantitative support, and the claim regarding sequence-dependent propensity is presented without statistical evidence. The work is potentially valuable, but the case is not fully established from the supplied material.
- **Who would be interested in the results, and why** Computational biophysicists and force field developers studying nucleic acid conformational dynamics; researchers in protein-DNA recognition and structural biology who rely on molecular dynamics simulations; methodologists interested in the accuracy of AMBER force fields for nucleic acids. The results could inform future force field parameterization and guide simulation protocol choices for protein-DNA systems.
- **Major strengths** The study addresses a biologically important and mechanistically nuanced phenomenon, the multistate nature of the B- to A- transition, rather than treating it as a simple two-state process. The use of multiple force fields and an experimental combination allows comparative assessment. The finding that A-like intermediate geometries are well reproduced while their populations are not is a potentially useful diagnostic distinction. The observation of sequence-dependent propensity in unbound DNA that correlates with protein-bound conformations is an interesting and potentially testable claim.
- **Major Concerns**  
  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Evidence sufficiency  
  - **Claim pointer** The authors claim that "populations (stabilities) are significantly underestimated" for A-like intermediate states across all tested force fields.  
  - **Evidence pointer** Abstract only; location not provided  
  - **Concern** The abstract provides no quantitative data, such as population percentages, free energy differences, or statistical uncertainties, to support the claim of significant underestimation. No comparison with experimental populations or benchmarks is described.  
  - **Why it matters** The central conclusion of the paper rests on this claim. Without quantitative evidence and appropriate statistical treatment, the reader cannot assess the magnitude of the discrepancy or whether it is within expected force field error.  
  - **Resolution test** Provide population values for each force field and experimental reference, with error estimates and convergence checks, in the full manuscript.  
  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Methodological transparency  
  - **Claim pointer** The authors state that "different force fields predict different propensities for A-like states growing in the order OL15 < bsc1 < OL15chi(OL3)".  
  - **Evidence pointer** Abstract only; location not provided  
  - **Concern** The abstract does not describe how A-like states were defined, how populations were computed, what simulation lengths and replica strategies were used, or how the order of propensities was determined. Without this information, the ordering claim cannot be evaluated.  
  - **Why it matters** The comparative ranking of force fields is a key result. If the definition of A-like states or the population estimation method is flawed, the ranking could be artefactual.  
  - **Resolution test** Specify the structural criteria for A-like states, the simulation protocol, and the method for population estimation, including any free energy calculations or enhanced sampling approaches.  
  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Claim support  
  - **Claim pointer** The authors claim that "force fields seem to predict the correct sequence-dependent A-form propensity, as they predict larger populations of the A-like form in unbound DNA in those steps that acquire A-like conformations in protein-DNA complexes".  
  - **Evidence pointer** Abstract only; location not provided  
  - **Concern** This claim is presented as a correlation between unbound DNA populations and protein-bound conformations, but no statistical measure, such as correlation coefficients or significance tests, is reported. The word "seem" indicates uncertainty, yet the claim is used to support the overall conclusion.  
  - **Why it matters** If the sequence-dependent propensity is not robustly demonstrated, the claim that force fields are qualitatively correct in this aspect is weakened, which affects the interpretation of the population underestimation.  
  - **Resolution test** Provide a quantitative correlation analysis with significance testing between unbound A-like populations and the propensity of steps to adopt A-like conformations in protein-DNA complexes.  
  - **Concern ID** R1-M4  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Outcome interpretation  
  - **Claim pointer** The authors state that "the instability of A-like geometries in current force fields significantly alters the geometry of simulated protein-DNA complexes and destabilizes the binding motif".  
  - **Evidence pointer** Abstract only; location not provided  
  - **Concern** The abstract does not specify which geometric parameters were altered, by what magnitude, or how binding motif destabilization was quantified. The link between A-like population underestimation and overall complex destabilization is asserted but not demonstrated.  
  - **Why it matters** This claim extends the findings from conformational populations to functional consequences for protein-DNA binding. Without supporting data, the practical significance of the force field limitation remains unclear.  
  - **Resolution test** Report specific geometric deviations (e.g., RMSD, base pair parameters) and binding stability metrics (e.g., interaction energies, hydrogen bond occupancy) with comparisons to experimental structures.
- **Minor Comments**  
  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Clarity  
  - **Affected element** Definition of intermediate states  
  - **Evidence pointer** Abstract; location not provided  
  - **Issue** The abstract describes intermediate states as combinations of A-like pucker and B-like chi, and vice versa, but does not clarify how these combinations were classified or whether all possible combinations were observed.  
  - **Required correction** Define the classification scheme for intermediate states and state whether all four combinations were populated in simulations.  
  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Completeness  
  - **Affected element** Force field rationale  
  - **Evidence pointer** Abstract; location not provided  
  - **Issue** The choice of OL15, bsc1, and OL15chi(OL3) is stated but not justified. The reader is not told why these specific force fields were selected or what the experimental combination represents.  
  - **Required correction** Briefly explain the rationale for selecting these force fields and the origin of the OL15chi(OL3) combination.  
  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Generalizability  
  - **Affected element** System selection  
  - **Evidence pointer** Abstract; location not provided  
  - **Issue** The abstract mentions eight diverse protein-DNA complexes but does not describe their nature, sequence diversity, or structural features.  
  - **Required correction** Provide a brief description of the systems studied, including their biological relevance and structural diversity.  
  - **Concern ID** R1-m4  
  - **Severity** Minor  
  - **Axis** Terminology  
  - **Affected element** Use of "experimental combination"  
  - **Evidence pointer** Abstract; location not provided  
  - **Issue** The term "experimental combination OL15chi(OL3)" is ambiguous. It is unclear whether this is a hybrid parameter set or a modified version of OL15.  
  - **Required correction** Clarify the nature of OL15chi(OL3) and how it was constructed.

## Risk / unsupported claims
- The claim that A-like intermediate geometries "agree well" with native X-ray geometries is unsupported in the abstract, as no quantitative comparison metric is provided.
- The claim that all force fields underestimate A-like populations is unsupported without numerical values and statistical analysis.
- The claim of correct sequence-dependent A-form propensity is presented with the qualifier "seem" and lacks statistical evidence.
- The claim that force field instability "significantly alters" complex geometry and "destabilizes" the binding motif is unsupported without specific data.
- The generalizability of the findings beyond the eight studied complexes is not assessable from the abstract.

## Assessment against Nature-style criteria
- **Originality** The conceptual treatment of the B- to A- transition as multistate with mixed pucker/chi combinations is a useful framing, though not entirely novel in the field. The comparative force field assessment adds a practical dimension.
- **Scientific importance** The question of force field accuracy for protein-DNA interfaces is important for the reliability of molecular dynamics simulations in structural biology. The potential finding of systematic underestimation of A-like states could have broad implications.
- **Interdisciplinary readership** The topic bridges computational chemistry, biophysics, and structural biology. The abstract is written in a way that is accessible to nonspecialists, though technical terms such as "sugar pucker" and "glycosidic torsion" are used without definition.
- **Technical soundness** Not assessable from the abstract alone. The lack of methodological detail and quantitative results prevents evaluation of the technical rigor.
- **Readability for nonspecialists** The abstract is concise and generally clear, but assumes familiarity with DNA conformational states and force field terminology. The main findings are stated in accessible language.

## Recommendation posture
Currently not established from the provided evidence. The abstract presents a plausible and potentially important study, but the absence of quantitative data, methodological detail, and statistical support means the central claims cannot be verified. The manuscript may become publishable if the full text provides the necessary evidence and addresses the major concerns raised.