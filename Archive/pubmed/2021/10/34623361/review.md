## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract, with reference to the cited crystallographic structures and computational method
- **Shared manuscript claim summary** The authors report DFT/MFCC interaction energy calculations for four EthR2 inhibitors and conclude that BDM76060 and BDM76150 bind more strongly than BDM72201 and BDM72719, consistent with experimental potency data, and propose the results can guide clinical development of ethionamide boosters.
- **Visible evidence base** Abstract text; PDB IDs 6HS1, 6HRX, 6HS2, 6HRY; method named as DFT with MFCC; no numerical data, figures, tables, or methodological details provided
- **Missing materials affecting confidence** Full manuscript, computational details, energy values, error estimates, structural validation, experimental potency data, and any comparison with alternative methods

## Reviewer
- **Overall assessment** The abstract presents a plausible computational study with a clear hypothesis and a conclusion that aligns with prior experimental findings. However, the evidence provided in the abstract is insufficient to evaluate the technical soundness of the calculations, the statistical or systematic uncertainties, or the robustness of the energetic ranking. The claim that the results can guide clinical trials is overstated given the limited scope of the computational analysis.
- **Who would be interested in the results, and why** Researchers in tuberculosis drug development, computational chemists working on protein-ligand interactions, and medicinal chemists interested in EthR/EthR2 inhibitors as ethionamide boosters. The work may also interest those applying DFT-based fragment methods to biological systems.
- **Major strengths** The study addresses a clinically relevant problem, namely improving ethionamide efficacy against multidrug-resistant tuberculosis. The use of crystallographic structures and a quantum mechanical method (DFT/MFCC) is appropriate for estimating interaction energies. The conclusion is consistent with experimental potency data, which provides a useful cross-validation.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not report any numerical energy values, error bars, or convergence criteria. Without these, the claimed ranking of binding strengths cannot be assessed. The method of comparing computed energies to experimental potency is not described, and no statistical or sensitivity analysis is mentioned. The structural basis for the 10.0 A radius claim is not substantiated.
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The application of DFT/MFCC to EthR2 inhibitors is a specific extension of existing approaches, but the abstract does not demonstrate a novel methodological advance.
  - Scientific importance: Moderate. The topic is relevant to tuberculosis treatment, but the findings are incremental and do not establish a new mechanism or therapeutic principle.
  - Interdisciplinary readership: Limited. The abstract is written for a specialist computational chemistry audience and does not frame the results for a broader biomedical readership.
  - Technical soundness: Not assessable from the abstract. No computational details, validation, or uncertainty quantification are provided.
  - Readability for nonspecialists: Acceptable but technical. The abstract assumes familiarity with EthA, EthR, EthR2, and MFCC.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a potentially useful computational study, but the absence of quantitative results and methodological detail prevents a supportive recommendation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that BDM76060 and BDM76150 produce stronger bonds than BDM72201 and BDM72719, based on calculated interaction binding energies.
- **Evidence pointer** Abstract, no specific section or figure; location not provided
- **Concern** The abstract reports no numerical energy values, no units, no error estimates, and no comparison with experimental binding affinities or inhibition data. The ranking of ligands is stated without any quantitative support.
- **Why it matters** Without numerical data and uncertainty quantification, the reader cannot verify the magnitude of the energy differences, whether they are statistically or physically meaningful, or whether the ranking is robust to methodological choices.
- **Resolution test** Provide a table of computed interaction energies with standard deviations or error bars, and a clear description of how the energies were derived and compared to experimental potency.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors state that calculations were performed using DFT within the MFCC approach, using crystallographic data.
- **Evidence pointer** Abstract, method description; location not provided
- **Concern** No computational details are given, such as the DFT functional, basis set, treatment of solvation, protonation states, truncation criteria for MFCC, or convergence thresholds. The PDB structures are cited, but no preparation steps are described.
- **Why it matters** Reproducibility is a core requirement for computational studies. Without these details, the results cannot be independently replicated or assessed for methodological adequacy.
- **Resolution test** Include a methods section or supplementary information with full computational parameters, software versions, and structure preparation protocols.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Claim scope
- **Claim pointer** The authors propose that the obtained data can be used to guide clinical trials of these inhibitors and other inhibitors acting on the EthR2 pathway.
- **Evidence pointer** Abstract, final sentence; location not provided
- **Concern** The study is a computational analysis of four inhibitors. Extrapolating to clinical trial guidance is a significant leap, as the abstract provides no pharmacokinetic, toxicological, or in vivo efficacy data.
- **Why it matters** Overstating the translational relevance of computational findings can mislead readers and overstate the maturity of the work.
- **Resolution test** Reframe the conclusion to state that the results may inform further preclinical evaluation or rational design, rather than directly guiding clinical trials.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Binding site description
- **Evidence pointer** Abstract, "same binding site within a 10.0 A radius"
- **Issue** The phrase "within a 10.0 A radius of the EthR2 protein" is ambiguous. It is unclear whether this refers to a sphere around a specific residue, the ligand center, or the entire protein.
- **Required correction** Specify the reference point for the 10.0 A radius, such as the ligand centroid or a defined binding pocket residue.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Weakly attached" and "stronger bonds"
- **Evidence pointer** Abstract, results description
- **Issue** The terms "weakly attached" and "stronger bonds" are vague and not defined in energetic or structural terms.
- **Required correction** Use quantitative descriptors, such as interaction energy ranges or contact surface areas, to define weak versus strong binding.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Context
- **Affected element** Comparison with experimental studies
- **Evidence pointer** Abstract, "corroborating with experimental studies"
- **Issue** The abstract does not cite or describe the experimental studies being referenced, so the reader cannot assess the strength of the corroboration.
- **Required correction** Provide citations and a brief description of the experimental potency data used for comparison.

## Risk / unsupported claims
- The ranking of BDM76060 and BDM76150 as stronger binders is unsupported in the abstract due to the absence of numerical energy data.
- The claim that the results can guide clinical trials is unsupported and overreaches the scope of the computational study.
- The statement that the ligands share a binding site within a 10.0 A radius is not verifiable without structural figures or residue-level details.
- The consistency with experimental studies is asserted but not documented with specific data or references.