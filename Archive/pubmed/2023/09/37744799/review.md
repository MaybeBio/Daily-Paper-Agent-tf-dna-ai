## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, acknowledgments) as provided by the user. No supplementary information, figures, or tables were included in the supplied material.
- **Assessment boundary** The review is limited to the content of the provided manuscript text. Claims, methods, and results are assessed based solely on what is written. No external validation, replication, or access to raw data was performed.
- **Shared manuscript claim summary** The authors present a computational design workflow combining molecular dynamics simulations, continuum electrostatics, and charge optimization to predict arginine substitutions in the antimicrobial peptide buforin II that would increase its DNA-binding affinity. They predict and experimentally validate that the T1R variant substantially increases DNA binding and antimicrobial potency, while the L8R variant modestly increases DNA binding with inconsistent antimicrobial effects. The study claims that DNA-binding affinity depends on charge distribution, not just overall monopole, and that this electrostatics-based design strategy can improve AMP potency.
- **Visible evidence base** The manuscript text includes descriptions of methods, results summaries, and references to figures and tables (Figures 1-11, Tables 1-2). However, none of the actual figures, tables, or numerical data are provided in the supplied material. Experimental details for binding assays and antimicrobial tests are described but raw values are not given.
- **Missing materials affecting confidence** All figures and tables are absent, including the key data in Table 2 (binding free energies) and Figures 4-7 (computational predictions and experimental results). Supplementary information is not available. The manuscript text alone does not allow independent verification of the quantitative claims or statistical analyses.

## Reviewer
- **Overall assessment** The manuscript presents a well-structured and logically coherent computational design workflow with experimental validation. The central hypothesis, that electrostatic interactions can be rationally tuned to increase DNA binding of an AMP in a position-dependent manner, is clearly articulated and supported by the described results. However, the absence of all figures and tables in the supplied material severely limits the ability to assess the robustness of the data, the statistical analyses, and the strength of the conclusions. The methodological approach is sound and the work addresses a relevant question in AMP engineering, but the evidence base as provided is insufficient for a full evaluation.
- **Who would be interested in the results, and why** Researchers in antimicrobial peptide engineering, computational protein design, and biophysics of protein-nucleic acid interactions would find this work relevant. The demonstration that a simplified electrostatics-based approach can guide AMP design offers a practical strategy for developing more potent peptides, which is of interest to those working on antibiotic alternatives. The finding that charge position matters beyond total charge is also relevant to the broader field of molecular recognition.
- **Major strengths** The manuscript is clearly written and the workflow is logically organized. The combination of computational predictions with experimental validation is a strength. The authors explicitly address a key hypothesis, namely that charge distribution, not just monopole, affects DNA binding, and they design variants to test this. The inclusion of histidine protonation effects and structural analyses adds depth to the study. The discussion is balanced and acknowledges limitations, such as the simplified electrostatic model and the variability in antimicrobial assays.
- **Major Concerns** The primary concern is the lack of access to the actual data. All quantitative results, including binding free energies, statistical significance values, and experimental measurements, are referenced but not shown. This makes it impossible to evaluate the magnitude of the reported effects, the validity of the statistical claims, or the consistency between computational predictions and experimental outcomes. A secondary concern is the limited scope of experimental validation, with only two variants tested and antimicrobial activity assessed against a single E. coli strain. The generalizability of the design workflow to other AMPs or targets is asserted but not demonstrated.
- **Minor Comments** The manuscript would benefit from a more detailed description of the charge optimization procedure, particularly the constraints applied and the sensitivity of the results to parameter choices. The discussion of the differences between the radial diffusion and microbroth dilution results for L8R is speculative and could be strengthened by additional experimental data, such as membrane permeabilization or translocation measurements. The statement that the design framework is not specific to DNA and could be applied to any peptide/target pair is overly broad and not supported by the data presented.
- **Technical failings that need to be addressed before the case is established** The absence of all figures and tables is a critical technical failing in the supplied material. Without these, the core claims of differential binding affinities and antimicrobial activities cannot be verified. Additionally, the statistical methods used to compare binding free energies and antimicrobial activities are not described in sufficient detail. The manuscript states significance to p ≤ 0.05 but does not specify the tests used or the number of replicates for each comparison.
- **Assessment against Nature-style criteria** Originality: The work is original in its specific application of charge optimization to AMP design for DNA binding, though the general concept of electrostatics-based design is established. Scientific importance: The findings are of moderate importance, providing a proof-of-concept for a design strategy but not yet demonstrating broad applicability or clinical relevance. Interdisciplinary readership: The work bridges computational biophysics and antimicrobial peptide biology, which could appeal to a niche but not broad interdisciplinary audience. Technical soundness: The computational methods are appropriate and the experimental assays are standard, but the lack of data prevents a full assessment of technical rigor. Readability for nonspecialists: The manuscript is generally readable, but the methods section assumes familiarity with continuum electrostatics and MD simulations, which may limit accessibility.
- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual framework and experimental design are promising, and the conclusions are plausible based on the text. However, the case is not fully established from the provided evidence because the key data are missing. Access to the figures, tables, and detailed statistical analyses is essential to confirm the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that T1R and L8R variants show significantly increased DNA binding relative to wild-type BF2, with T1R showing a greater increase than L8R, and that T1R shows increased antimicrobial activity.
- **Evidence pointer** Table 2, Figures 5-7 (location not provided in the supplied material)
- **Concern** All quantitative data supporting the central claims are contained in figures and tables that were not included in the supplied material. The text describes the results but does not provide the actual values, error bars, or statistical test outcomes. Without these data, it is impossible to assess the magnitude of the reported effects, the variability across replicates, or whether the differences are robust and meaningful.
- **Why it matters** The core conclusion of the paper, that the computational design successfully predicts variants with differential DNA-binding affinities and antimicrobial activities, rests entirely on these data. If the effects are small or highly variable, the conclusions would be significantly weakened. The reader cannot evaluate the strength of the evidence.
- **Resolution test** Provide the full figures and tables with numerical values, error bars, and statistical annotations. Include a description of the statistical tests used and the number of independent replicates for each measurement.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Experimental scope
- **Claim pointer** The manuscript states that the design strategy is a novel way to increase the potency of other membrane-translocating AMPs that target nucleic acids.
- **Evidence pointer** Discussion section (location not provided)
- **Concern** The experimental validation is limited to two variants of a single AMP (BF2) and antimicrobial activity is tested against only one E. coli strain. The claim of generalizability to other AMPs is an extrapolation that is not supported by the data presented. The authors do not test whether the workflow would work for other peptides or other bacterial strains.
- **Why it matters** The broader significance of the work depends on its applicability beyond the specific system studied. Without additional examples, the claim of a general design strategy remains speculative and the impact of the work is reduced.
- **Resolution test** Either temper the claim to reflect the specific system studied or provide additional examples of the workflow applied to other AMPs or targets. Alternatively, clearly state the limitations of the current study in the discussion.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological detail
- **Claim pointer** The charge optimization procedure is described as a coarse filter to estimate the effect of arginine substitutions on DNA-binding affinity.
- **Evidence pointer** Methods, Step 2 (location not provided)
- **Concern** The description of the charge optimization is brief and lacks detail on the constraints applied to the optimization, the treatment of side chain conformations, and the sensitivity of the results to the choice of dielectric constants and other parameters. The authors state that the method is coarse but do not provide a thorough analysis of its limitations or how robust the predictions are to parameter variations.
- **Why it matters** The reliability of the computational predictions is central to the study. If the charge optimization results are highly sensitive to parameter choices, the predictions may not be robust. A more detailed description and sensitivity analysis would increase confidence in the methodology.
- **Resolution test** Expand the methods section to include a detailed description of the optimization constraints, parameter choices, and a sensitivity analysis. Alternatively, provide supplementary information with this information.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, Step 5
- **Evidence pointer** Location not provided
- **Issue** The description of the fluorescence intercalator displacement assay is brief and does not specify the DNA concentration, the stoichiometry of TO to DNA, or the buffer conditions in detail.
- **Required correction** Provide more experimental details for the FID assay, including concentrations, buffer composition, and the calculation of C50 values.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, Step 5
- **Evidence pointer** Location not provided
- **Issue** The manuscript reports that L8R shows increased activity in the radial diffusion assay but no significant change in the microbroth assay. The authors attribute this to differences in assay conditions but do not provide a detailed explanation or supporting data.
- **Required correction** Expand the discussion of the discrepancy between the two antimicrobial assays and consider additional experiments, such as membrane permeabilization assays, to clarify the mechanism.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Discussion
- **Evidence pointer** Location not provided
- **Issue** The discussion of histidine protonation effects is interesting but somewhat speculative, particularly the claim that protonation affects the contribution of ARG20 in a mutant-specific manner, which is based on preliminary data not shown.
- **Required correction** Either include the preliminary data or clearly label this as a hypothesis that requires further investigation.

## Risk / unsupported claims
- The claim that T1R and L8R variants show significantly increased DNA binding relative to wild-type BF2 is unsupported in the provided material because the relevant data are in missing figures and tables.
- The claim that T1R shows increased antimicrobial activity is unsupported for the same reason.
- The claim that the design strategy is generalizable to other membrane-translocating AMPs is unsupported, as only one AMP was tested.
- The claim that histidine protonation affects ARG20 contributions in a mutant-specific manner is unsupported, as it is based on preliminary data not shown.
- The claim that the computational workflow is effective for designing tighter DNA-binding peptides is only partially supported by the text, as the quantitative evidence is not available.