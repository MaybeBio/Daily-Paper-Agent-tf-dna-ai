## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends, supplementary legends) as provided in the submission
- **Assessment boundary** Scientific content, experimental logic, evidence quality, and internal consistency of the claims as presented. No assessment of editorial fit or journal policy.
- **Shared manuscript claim summary** The authors report that the KER region of the CAF-1 Cac1 subunit forms a single alpha helix (SAH) that binds DNA, confers length selectivity for tetrasome-length DNA, and cooperates with the WHD to support DNA damage survival and gene silencing in budding yeast. They propose the KER acts as a DNA-binding spacer element during chromatin assembly.
- **Visible evidence base** Results sections for Figures 1–6, methods descriptions, figure legends, supplementary figure legends, and source data legends. No raw data files, no uncropped gel images, no crystallographic validation reports, no flow cytometry gating details beyond a brief description.
- **Missing materials affecting confidence** Raw EMSA gel images, uncropped Western blots, crystallographic refinement statistics beyond the summary table, flow cytometry raw data and gating strategy, strain validation data (e.g., PCR verification of CRISPR edits), and any statistical analysis details for the in vivo assays.

## Reviewer
- **Overall assessment** This manuscript presents a potentially interesting finding: a SAH domain in CAF-1 that binds DNA and contributes to length-dependent DNA recognition. The structural and biophysical characterization is a reasonable starting point. However, the evidence linking the in vitro DNA-binding properties to the proposed in vivo mechanism is incomplete. Several key experiments lack appropriate controls, and some conclusions are drawn from data that do not directly support them. The claim that this is a "first-in-class" DNA-binding SAH requires more careful comparison to existing literature. The manuscript would benefit from additional experiments to directly test the proposed spacer function and to rule out alternative explanations for the observed in vivo phenotypes.
- **Who would be interested in the results, and why** Researchers studying histone chaperones, chromatin assembly, DNA repair, and the biophysics of protein-DNA interactions. The identification of a new DNA-binding motif in a well-studied chaperone could be of interest to those working on CAF-1 function across species. The proposed SAH-DBD concept may also attract interest from structural biologists studying intrinsically disordered or extended helical domains.
- **Major strengths** The study combines structural, biophysical, and genetic approaches. The identification of a SAH in the KER region is a clear advance. The use of a competitive DNA-length assay is a useful approach to quantify length selectivity. The in vivo experiments are performed in a relevant organism (budding yeast) with endogenous-level CRISPR-generated mutations. The authors also test a human KER substitution, which adds a comparative dimension.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (crystallographic evidence), R1-M2 (in vivo phenotype interpretation), R1-M3 (length selectivity assay interpretation), R1-M4 (SAH-DBD novelty claim).
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The finding of a SAH in CAF-1 is new, but the concept of extended helical domains binding DNA is not unprecedented. The "first-in-class" claim needs stronger support.  
  *Scientific importance*: Potentially significant if the spacer function is validated, as it would provide a mechanism for how CAF-1 measures DNA length. However, the current evidence does not fully establish this.  
  *Interdisciplinary readership*: The topic is relevant to chromatin biology, DNA repair, and structural biology. The biophysical approach may appeal to a broader audience, but the current presentation is somewhat specialized.  
  *Technical soundness*: Mixed. The in vitro assays are generally well-executed, but the crystallographic data are under-validated, and the in vivo experiments lack key controls.  
  *Readability for nonspecialists*: The manuscript is reasonably well-written but assumes significant background knowledge. The figures are dense and may be difficult for nonspecialists to follow.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is interesting, but the evidence as presented does not fully support the conclusions. Additional experiments and clarifications are needed.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim to have determined the crystal structure of the KER at 2.81 Å resolution and describe it as a continuous alpha helix of 128 Å.
- **Evidence pointer** Results section "The KER is a first-in-class single alpha helix (SAH) DNA-binding domain", Figure 2, Supplementary Table 4
- **Concern** The crystallographic analysis is presented with minimal detail. The resolution is modest (2.81 Å), and the authors do not report key validation metrics such as R-free/R-work, Ramachandran statistics, or B-factor distributions. The statement that the helix is "almost entirely solvent exposed" is not supported by any quantitative analysis of solvent accessibility. The authors also do not discuss how the crystal packing might influence the observed conformation. Without these details, the structural claims cannot be properly evaluated.
- **Why it matters** The structural model is central to the claim that the KER forms a SAH. If the model is not reliable, the entire premise of the manuscript is weakened. The authors also use the structure to make claims about the arrangement of charged residues, which is important for their DNA-binding model.
- **Resolution test** Provide full refinement statistics, including R-free, Ramachandran plot statistics, and B-factor analysis. Show electron density maps for the KER region, particularly for the charged side chains. Discuss crystal packing and whether the extended conformation is likely to be maintained in solution. If possible, provide additional evidence for the SAH in solution, such as SAXS or analytical ultracentrifugation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The authors claim that the KER cooperates with the WHD to overcome DNA damage sensitivity and maintain gene silencing, based on the observation that the double mutant (ΔKER+mWHD) shows a phenotype similar to cac1Δ.
- **Evidence pointer** Results section "The KER is a major DNA binding domain in CAF-1 that cooperates with the WHD in vivo", Figure 1n, Figure 1-figure supplement 2d, Table 1
- **Concern** The interpretation of the double-mutant phenotype as evidence for cooperation is not fully justified. The authors do not measure protein levels of the mutant Cac1 variants. If the ΔKER+mWHD mutant protein is unstable or expressed at lower levels, the phenotype could be due to reduced protein levels rather than loss of DNA-binding function. The authors also do not test whether the double mutant is properly incorporated into the CAF-1 complex. Without these controls, the conclusion that the two domains cooperate is not established.
- **Why it matters** The in vivo cooperation claim is a key part of the manuscript's central thesis. If the phenotype is due to protein instability, the interpretation changes substantially. The authors need to rule out this trivial explanation.
- **Resolution test** Perform Western blots to confirm equal expression of all mutant Cac1 proteins. Test whether the mutant proteins still form the CAF-1 complex (e.g., by co-immunoprecipitation or size-exclusion chromatography). If possible, perform a rescue experiment with a version of the double mutant that is targeted to chromatin independently of DNA binding.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The authors claim that the KER confers length selectivity for tetrasome-length DNA, based on the Cy5-DNA ladder competition assay.
- **Evidence pointer** Results section "The KER confers the selectivity of CAF-1 for tetrasome-length DNA", Figure 4
- **Concern** The Cy5-DNA ladder assay is a novel approach, but the interpretation is not straightforward. The authors measure depletion of free DNA as a function of protein concentration, but they do not account for the possibility that the protein binds to the ends of the DNA fragments or that the binding stoichiometry varies with DNA length. The assay also does not distinguish between specific length recognition and a general preference for longer DNA due to more binding sites. The authors should provide a more quantitative analysis, such as determining the stoichiometry of protein-DNA complexes for each length.
- **Why it matters** The length-selectivity claim is central to the proposed function of the KER. If the assay does not accurately measure length preference, the conclusion is not supported. The authors need to demonstrate that the observed preference is due to the KER specifically recognizing a particular DNA length, rather than a non-specific avidity effect.
- **Resolution test** Perform the assay with a fixed DNA length and varying protein concentrations to determine binding stoichiometry. Use a competition assay with unlabeled DNA of different lengths to confirm the preference. Consider using a more quantitative method, such as fluorescence anisotropy or surface plasmon resonance, to measure binding affinities for different DNA lengths.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Originality
- **Claim pointer** The authors claim the KER is a "first-in-class" DNA-binding SAH domain.
- **Evidence pointer** Discussion section "The KER SAH is a novel DNA binding motif"
- **Concern** The claim of "first-in-class" is not adequately supported. The authors do not perform a comprehensive search of the literature for other SAH domains that bind DNA. There are examples of extended helical domains that interact with nucleic acids, and the authors should discuss these in more detail. The classification of the KER as a new type of DNA-binding domain requires a more thorough comparison to known DNA-binding motifs.
- **Why it matters** The novelty claim is important for the perceived impact of the work. If similar domains have been described, the claim needs to be moderated. The authors should provide a more rigorous analysis of the uniqueness of the KER.
- **Resolution test** Perform a systematic search of the literature and structural databases for SAH domains with DNA-binding activity. Discuss any similar domains and explain how the KER differs. If no such domains exist, provide a clear definition of what makes the KER unique.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1
- **Evidence pointer** Figure 1a, Figure 1-figure supplement 1a
- **Issue** The domain diagram in Figure 1a is not clearly labeled. It is difficult to determine the exact boundaries of the KER, WHD, and other domains. The supplementary figure shows the purified proteins, but the labels are small and hard to read.
- **Required correction** Provide a larger, clearer domain diagram with residue numbers indicated. Increase the font size of labels in the supplementary figure.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section "Electrophoretic mobility shift assays (EMSA)"
- **Issue** The methods for the Cy5-DNA ladder assay are not described in sufficient detail. It is unclear how the "normalized free DNA" was calculated and how the 50% depletion point was determined. The description of the fitting procedure is also vague.
- **Required correction** Provide a more detailed description of the data analysis, including the exact equations used and how the error range of the 95% confidence limit was calculated. Consider including a representative example of the fitting procedure.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Figure 1o, Figure 3j, Figure 5c
- **Evidence pointer** Results sections describing flow cytometry experiments
- **Issue** The flow cytometry data are presented as mean ± standard deviation, but the number of independent experiments is not always clear. The statistical significance of the differences between strains is not reported.
- **Required correction** Clearly state the number of independent experiments for each flow cytometry analysis. Perform appropriate statistical tests (e.g., ANOVA with post-hoc comparisons) and report p-values.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section "Function of the KER SAH-DBD in CAF-1 and implications for nucleosome assembly"
- **Issue** The discussion of the proposed spacer function is speculative and does not fully consider alternative models. For example, the KER could also affect the kinetics of DNA binding or the stability of the CAF-1 complex, rather than acting purely as a spacer.
- **Required correction** Acknowledge alternative models and discuss how the current data distinguish between them. If the data do not distinguish, state this explicitly and suggest experiments that could.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is dense and uses specialized terminology without definition. The phrase "tetrasome-length DNA selectivity" is not immediately clear to a general reader.
- **Required correction** Briefly define what is meant by "tetrasome-length DNA" in the abstract. Consider simplifying the language to improve accessibility.

## Risk / unsupported claims
- The claim that the KER is a "first-in-class" DNA-binding SAH domain is not fully supported by the evidence presented. A more thorough literature comparison is needed.
- The claim that the KER acts as a "spacer function" during chromatin assembly is speculative and not directly tested. The data are consistent with this model, but alternative explanations are not ruled out.
- The claim that the KER and WHD "cooperate" in vivo is not fully established, as the authors do not rule out the possibility that the double-mutant phenotype is due to protein instability or complex misassembly.
- The crystallographic model is not sufficiently validated to support the detailed structural claims made in the manuscript.
- The length-selectivity assay is novel but not fully validated. The interpretation of the results depends on assumptions about binding stoichiometry and mode of binding that are not tested.