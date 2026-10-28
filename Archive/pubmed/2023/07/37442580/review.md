## Review setup
- **Input scope** Full manuscript text (abstract, results, discussion, materials and methods) without figures or supplementary material
- **Assessment boundary** Structural and biochemical characterization of the Rec114-Mei4 trimer interface, including computational modeling, NMR validation, DNA-binding assays, and single-molecule experiments
- **Shared manuscript claim summary** The authors present a structural model of the Rec114-Mei4 trimer interface, validate it experimentally, and demonstrate that the minimal RM-TDB domain can bind and bridge DNA molecules to form nucleoprotein condensates
- **Visible evidence base** Text descriptions of AlphaFold2 predictions, CD spectroscopy, NMR chemical shift assignments, EMSA data, AFM imaging, confocal microscopy, and optical trap experiments
- **Missing materials affecting confidence** All figures, supplemental figures, supplemental tables, movies, and raw data files are not accessible; NMR chemical shift assignments referenced as BMRB IDs 51786 and 51787 cannot be verified

## Reviewer
- **Overall assessment** This manuscript presents a structurally detailed analysis of the Rec114-Mei4 complex, a key component of the meiotic DNA double-strand break machinery. The combination of computational prediction with experimental validation is commendable, and the discovery of DNA-bridging activity in the minimal domain is potentially significant. However, the manuscript would benefit from clearer presentation of quantitative data and more explicit discussion of limitations. The work is solid but incremental in nature, building substantially on prior studies from the same group.
- **Who would be interested in the results, and why** Researchers studying meiotic recombination, particularly those focused on the Spo11 catalytic complex and its accessory factors. The structural information will also interest those studying protein-protein interactions in DNA repair pathways. The DNA-bridging and condensate formation findings may attract researchers interested in phase separation in genome biology.
- **Major strengths** The study combines multiple complementary techniques (computational prediction, NMR, biochemistry, single-molecule imaging) to characterize a biologically important complex. The experimental validation of the AlphaFold2 model is rigorous, and the identification of a minimal domain sufficient for DNA binding and condensation provides a useful tool for future studies. The cross-species structural comparisons add evolutionary perspective.
- **Major Concerns** The manuscript lacks quantitative rigor in several areas. The C50 values are acknowledged as rough approximations, but the text does not provide error estimates or replicate numbers. The claim that the Rec114-4KR mutant phenotype is due to DNA binding defects is not fully supported, as the authors acknowledge. The relationship between the in vitro DNA-bridging activity and in vivo function remains speculative. The evolutionary analysis is limited to a small number of species, and the functional significance of the variable DNA-binding surface is not experimentally tested.
- **Minor Comments** The manuscript is generally well-written but some methodological details are unclear. The optical trap experiments are described in text but the analysis pipeline is not fully detailed. The authors should clarify how the "average number of RM-TDB bound" was calculated and what assumptions were made. The discussion of condensate substructure would benefit from more quantitative characterization.
- **Technical failings that need to be addressed before the case is established** The manuscript does not provide sufficient evidence that the DNA-bridging activity observed in vitro is relevant to the in vivo function of the RM complex. The connection between the structural data and the functional implications for meiotic DSB formation is not experimentally tested. The authors should either provide direct evidence linking the identified residues to in vivo function or temper their conclusions.
- **Assessment against Nature-style criteria** Originality: Moderate. The structural model is novel but builds on extensive prior work from the same group. Scientific importance: Moderate to high. The Rec114-Mei4 complex is essential for meiosis, and understanding its structure and DNA-binding properties is valuable. Interdisciplinary readership: Limited. The work is primarily of interest to meiosis and DNA repair specialists. Technical soundness: Generally strong, with rigorous experimental validation of the computational model. Readability for nonspecialists: The manuscript is accessible but assumes familiarity with meiotic recombination and biophysical techniques.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding the quantitative analysis and the functional relevance of the DNA-bridging activity.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The authors claim that the RM-TDB domain has DNA-bridging activity that can bundle DNA molecules together reversibly, and that this activity is relevant to the in vivo function of the RM complex.
- **Evidence pointer** Results section, Figure 5, Supplemental Figures S10-S12
- **Concern** The DNA-bridging activity is demonstrated in an artificial in vitro system with stretched DNA tethers. The authors do not provide direct evidence that this activity occurs in vivo or that it is required for meiotic DSB formation. The connection between the in vitro observations and the proposed functional role is speculative.
- **Why it matters** The central claim of the manuscript is that the DNA-bridging activity is functionally important. Without direct evidence linking this activity to in vivo function, the significance of the finding is diminished.
- **Resolution test** The authors should either provide experimental evidence that the DNA-bridging activity is required for DSB formation in vivo (e.g., by testing mutants that specifically disrupt bridging but not other functions) or clearly state that the in vivo relevance is speculative.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor
- **Claim pointer** The authors report C50 values for DNA binding by various constructs and mutants, and use these to compare relative affinities.
- **Evidence pointer** Results section, Figure 4, Figure 6, Supplemental Figure S8
- **Concern** The C50 values are described as "rough approximations" because the stoichiometry of protein-DNA complexes is unknown. However, the text does not provide error estimates, replicate numbers, or statistical analysis. This makes it difficult to assess whether the reported differences between constructs are significant.
- **Why it matters** The conclusions about the relative importance of different residues for DNA binding depend on the reliability of these measurements. Without error estimates, the reader cannot evaluate the strength of the evidence.
- **Resolution test** The authors should provide replicate measurements with error bars and statistical analysis for the C50 values, or clearly state the limitations of the measurements.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Functional significance
- **Claim pointer** The authors state that the Rec114-4KR mutant, which reduces DNA binding, "almost completely eliminated DSB formation during meiosis" and that "it is likely that the DNA binding defect is the main cause of defective DSB formation in vivo."
- **Evidence pointer** Results section, Discussion section
- **Concern** The authors acknowledge that they "cannot rule out the possibility that the mutation also affects other protein-protein interactions important for Rec114 function." This caveat is important because the 4KR mutant may have pleiotropic effects beyond DNA binding.
- **Why it matters** The conclusion that DNA binding is critical for DSB formation depends on the specificity of the 4KR mutant phenotype. If the mutation affects other functions, the interpretation is weakened.
- **Resolution test** The authors should test whether the 4KR mutant specifically affects DNA binding without disrupting other protein-protein interactions, or provide additional evidence linking DNA binding to DSB formation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, optical trap experiments
- **Evidence pointer** Materials and Methods, "Single-molecule optical trap experiments: data acquisition"
- **Issue** The description of the optical trap experiments is brief and lacks detail on how DNA tethers were formed, how the number of DNA molecules per tether was determined, and how the force-extension curves were analyzed.
- **Required correction** Provide more detail on the experimental setup and analysis pipeline, including how the number of DNA molecules in each tether was verified.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results section, DNA binding by RM-TDB
- **Evidence pointer** Results section, "The RM-TDB domain is sufficient to form condensates with DNA"
- **Issue** The authors state that "the critical concentration needed is considerably lower for the full-length proteins" but do not provide quantitative comparison or discuss the implications of this difference.
- **Required correction** Provide quantitative comparison of the critical concentrations and discuss what this difference might mean for the in vivo function.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of the evolutionary variability of the DNA-binding surface is brief and does not address the functional implications of this variability in detail.
- **Required correction** Expand the discussion of how the variable DNA-binding surface might affect the function of the RM complex in different species.

## Risk / unsupported claims
- The claim that the RM-TDB domain's DNA-bridging activity is relevant to in vivo condensate formation is not directly supported by the data presented.
- The statement that "the minimal folded RM-TDB domain by itself is capable of assembling cooperatively with DNA to form large structures reminiscent of the nucleoprotein condensates formed by full-length RM complexes" is based on in vitro observations and the in vivo relevance is inferred rather than demonstrated.
- The conclusion that the 4KR mutant phenotype is due to DNA binding defects is not fully supported, as the authors acknowledge the possibility of other effects.
- The quantitative comparison of DNA binding affinities between different constructs is limited by the lack of error estimates and statistical analysis.
- The evolutionary analysis is based on a limited number of species, and the functional significance of the observed variability is not experimentally tested.