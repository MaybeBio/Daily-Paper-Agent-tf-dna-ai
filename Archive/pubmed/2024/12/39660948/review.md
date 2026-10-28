## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, materials and methods, and author contributions. Supplementary figure and table titles are referenced but their content is not provided.
- **Assessment boundary** The scientific claims, experimental design, data interpretation, and conclusions as presented in the manuscript. The review is based solely on the provided text; no external data, supplementary files, or raw data were accessed.
- **Shared manuscript claim summary** The authors propose that the N-terminal helix of MarA, a transcriptional activator of the AcrAB-TolC efflux pump in *E. coli*, plays a critical role in DNA binding. They engineered two double-cysteine MarA variants (I13C/M47C and I16C/M47C) designed to form disulfide bonds that immobilize the N-terminal helix. Using EMSA, in vivo reporter assays, and MD simulations, they report that immobilization of the N-terminal helix via the I16C/M47C disulfide bond prevents DNA binding, while the I13C/M47C variant retains binding. They further suggest this inhibited conformation may be generalizable to other AraC/XylS family members, proposing the N-terminal helix as a target for inhibitor development.
- **Visible evidence base** Main text figures (Figures 1-7), supplementary figure and table titles (Figures S1-S19, Tables S1-S7), methods section, and references cited within the text.
- **Missing materials affecting confidence** The actual content of all supplementary figures and tables, raw EMSA gel images, full Western blot images, detailed MD simulation parameters and convergence criteria, and the complete dataset deposited on Zenodo. The absence of these materials limits the ability to fully assess the robustness of the experimental data and the statistical significance of the findings.

## Reviewer
- **Overall assessment** This manuscript presents a well-structured and hypothesis-driven investigation into the role of N-terminal helix dynamics in MarA function. The combination of experimental biochemistry (EMSA, in vivo reporter assays) with computational simulations (cMD, GaMD) is a strength, and the central finding that a specific disulfide bond (I16C/M47C) can lock MarA in a non-DNA-binding conformation is potentially interesting. However, the study has several significant limitations. The in vivo reporter data are confounded by the use of a strain with a highly modified genetic background and by the redundancy of MarA with SoxA and Rob. The mechanistic interpretation of the MD simulations, while plausible, is not fully supported by the presented analysis, and the claim of universality across the AraC/XylS family is based on a single additional simulation of Rob. The manuscript would be strengthened by a more direct demonstration of the proposed conformational lock, a clearer link between the in vitro and in vivo data, and a more cautious interpretation of the simulation results.
- **Who would be interested in the results, and why** Researchers in the fields of antimicrobial resistance, bacterial transcriptional regulation, and protein dynamics. Specifically, those studying efflux pump regulation, the AraC/XylS family of transcription factors, and the application of disulfide trapping or similar approaches to modulate protein function. The potential for targeting MarA dynamics as a novel anti-resistance strategy would be of interest to drug discovery groups.
- **Major strengths**
    1.  The study addresses a relevant and timely problem (antimicrobial resistance) with a clear and testable hypothesis.
    2.  The use of complementary experimental and computational approaches (EMSA, in vivo reporter, cMD, GaMD) is commendable and provides multiple lines of evidence.
    3.  The design of the two double-cysteine variants (I13C/M47C and I16C/M47C) is a clever approach to test the specific role of N-terminal helix dynamics, with the I13C/M47C acting as a potentially important control.
    4.  The inclusion of a negative control variant (S62C/L121C) that forms a disulfide bond elsewhere in the protein strengthens the specificity of the observed effects.
    5.  The manuscript is generally well-written and the logic of the experimental design is easy to follow.
- **Major Concerns**

    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Experimental support for central claim
    - **Claim pointer** The central claim is that "the immobilization of the N-terminal helix of MarA prevents binding to DNA" (Abstract, Results).
    - **Evidence pointer** Figure 2, Figures S1, S2, Table S1
    - **Concern** The primary evidence for the central claim is the EMSA data showing that the I16C/M47C variant cannot bind DNA in the absence of DTT. However, the authors also state that this variant is "even more unstable that the WT (shown by the protein precipitation after overnight storage at 4°C)". This raises a critical question: is the lack of DNA binding in the EMSA due to the specific conformational constraint of the N-terminal helix, or is it due to the protein being misfolded, aggregated, or otherwise non-functional? The authors do not provide sufficient data to rule out this alternative explanation. The fact that the I13C/M47C variant, which also forms a disulfide bond, is able to bind DNA suggests some specificity, but it does not fully address the stability issue for I16C/M47C. The ESI-MS data confirm disulfide bond formation but do not assess protein folding or stability.
    - **Why it matters** If the I16C/M47C variant is simply unstable or misfolded, the conclusion that immobilizing the N-terminal helix *specifically* prevents DNA binding is not valid. The paper's central mechanistic claim hinges on this distinction.
    - **Resolution test** The authors should provide direct evidence that the I16C/M47C variant is properly folded and stable under the conditions of the EMSA. This could be achieved through techniques such as circular dichroism (CD) spectroscopy, size-exclusion chromatography (SEC) coupled with multi-angle light scattering (MALS), or a thermal stability assay (e.g., differential scanning fluorimetry). If the protein is unstable, the claim must be revised to state that the mutation/disulfide bond leads to a loss of function, potentially through destabilization, rather than a specific conformational lock.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** No
    - **Axis** Interpretation of in vivo data
    - **Claim pointer** The claim that the I16C/M47C variant "cannot induce the transcription of the GFP protein in the reporter system as the WT MarA does" (Results, "The N-terminal helix of MarA is a crucial structural element...").
    - **Evidence pointer** Figure 3a, Figure 3c
    - **Concern** The in vivo reporter assay is performed in two different *E. coli* strains: Shuffle T7 Express (which allows disulfide bond formation) and T7 Express (which does not). The results show that in Shuffle T7 Express, the I16C/M47C variant does not activate transcription, while in T7 Express, it does. This is a key piece of evidence. However, the authors also note that the WT MarA protein is poorly expressed in Shuffle T7 Express cells, possibly due to degradation. This makes the comparison between WT and the variants in this strain difficult to interpret. The Western blot (Figure 3b) shows that the variants are expressed at higher levels than WT, yet they do not activate transcription. This is a strong result, but the low WT expression is a confounding factor. The authors should address this by, for example, normalizing the transcriptional output to the amount of MarA protein present, or by using a strain that allows disulfide bond formation but does not have the same protein degradation issues.
    - **Why it matters** The in vivo data are crucial for demonstrating the biological relevance of the in vitro findings. If the results are confounded by differential protein stability or expression, the conclusion that the disulfide bond inhibits function in a cellular context is weakened.
    - **Resolution test** The authors should provide a more quantitative analysis of the in vivo data, ideally normalizing GFP fluorescence to the level of MarA protein expression (e.g., from the Western blot). They could also consider using a different *E. coli* strain that is more amenable to expressing WT MarA while still allowing cytoplasmic disulfide bond formation.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Generalizability of the proposed mechanism
    - **Claim pointer** The claim that "This inhibited conformation seems to be universal for the monomeric members of the AraC/XylS family" (Abstract, Discussion).
    - **Evidence pointer** Figure 7, Figure S19
    - **Concern** The claim of universality is based on a single set of GaMD simulations of the two-domain protein Rob, where a homologous disulfide bond (L10C/M41C) was introduced. The simulations show that in one out of five replicas, the A-box interaction is lost. This is a very weak basis for a claim of universality. The authors have not tested this hypothesis experimentally in Rob or any other AraC/XylS family member. Furthermore, the simulation result is not robust, with only one of five replicas showing the effect.
    - **Why it matters** The title and abstract suggest a broad applicability of the findings to the entire AraC/XylS family. Overstating the generalizability of results based on limited evidence can mislead the field and is a significant overreach.
    - **Resolution test** The authors should either (a) temper the claim of universality to a hypothesis or suggestion, or (b) provide additional experimental or computational evidence supporting the generalizability, such as simulations of additional family members or, ideally, experimental validation in Rob or another family member.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Mechanistic interpretation of simulations
    - **Claim pointer** The claim that the disulfide bond in I16C/M47C "prevents the N-terminal HTH motif of MarA to properly bend to bind the mar promoter" (Results, "Impact of the I16C/M47C double cysteine mutations...").
    - **Evidence pointer** Figures 4, 5, S9-S11
    - **Concern** The MD simulations are used to provide a mechanistic rationale for the experimental observations. However, the analysis presented is largely descriptive (e.g., PCA, RMSF, secondary structure). The authors do not provide a clear, quantitative metric that directly links the dynamics of the N-terminal helix to the ability to bind DNA. For example, they do not calculate the free energy of binding, nor do they show a clear correlation between the conformational states sampled and the ability to form specific contacts with the DNA. The statement that the I16C/M47C variant samples "unproductive conformations" is vague and not supported by a specific analysis.
    - **Why it matters** A key part of the paper's contribution is the proposed mechanism. If the simulation analysis is not rigorous enough to support the mechanistic claim, the paper's impact is diminished.
    - **Resolution test** The authors should perform a more quantitative analysis of their simulations. This could include calculating the potential of mean force (PMF) along a relevant reaction coordinate (e.g., the distance between the N-terminal helix and the DNA), or performing a detailed analysis of the contacts between MarA and the DNA in the different conformational states. This would provide a more solid foundation for their mechanistic conclusions.

- **Minor Comments**

    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity of experimental details
    - **Affected element** EMSA methodology
    - **Evidence pointer** Section 4, "Electrophoretic mobility shift assay"
    - **Issue** The methods section for the EMSA is brief. It does not specify the concentration of the DNA probe, the protein concentration range, or the buffer conditions in detail. It also does not state how the binding was quantified (e.g., densitometry) or how many independent replicates were performed.
    - **Required correction** Please provide more detailed methods for the EMSA, including the exact concentrations of all components, the binding buffer composition, the incubation time and temperature, and the method of quantification. State the number of independent experimental replicates.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Statistical analysis
    - **Affected element** In vivo reporter assay
    - **Evidence pointer** Figure 3a, 3c
    - **Issue** The in vivo reporter data are presented as the "mean of two biological replicates" (Section 4, "Reporter system"). With only two replicates, it is impossible to assess the statistical significance of the observed differences. No error bars or statistical tests are shown.
    - **Required correction** Please provide the data from individual replicates, or better, increase the number of biological replicates to at least three and present the data with appropriate error bars and statistical analysis (e.g., t-test or ANOVA).

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Data availability
    - **Affected element** MD simulation data
    - **Evidence pointer** Section 4, "System preparation for conventional and Gaussian accelerated molecular dynamics simulations"
    - **Issue** The authors state that the simulation data are available on Zenodo, but the link is not provided in the manuscript text. This makes it difficult for readers to access the data.
    - **Required correction** Please include the full Zenodo DOI or URL in the Data Availability Statement or in the main text.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Figure clarity
    - **Affected element** Figure 2
    - **Evidence pointer** Figure 2
    - **Issue** The EMSA gels in Figure 2 are not clearly labeled. It is difficult to distinguish between the different conditions (e.g., +DTT, -DTT) and the different protein variants. The figure legend is also somewhat brief.
    - **Required correction** Please improve the labeling of the gels in Figure 2 and expand the figure legend to clearly describe each panel and the conditions tested.

    - **Concern ID** R1-m5
    - **Severity** Minor
    - **Axis** Terminology
    - **Affected element** Abstract and Discussion
    - **Evidence pointer** Abstract, Discussion
    - **Issue** The term "immobilization" is used to describe the effect of the disulfide bond on the N-terminal helix. This is a strong statement that implies a complete loss of motion. The simulations show a reduction in mobility, not a complete immobilization. A more accurate term might be "restriction of dynamics" or "conformational constraint."
    - **Required correction** Consider using a more nuanced term such as "restricting the dynamics" or "conformational locking" instead of "immobilization" to more accurately reflect the simulation data.

- **Technical failings that need to be addressed before the case is established**
    - R1-M1: The lack of evidence that the I16C/M47C variant is properly folded and stable, which is essential to distinguish between a specific conformational effect and non-specific protein instability.
    - R1-M2: The confounding factor of low WT MarA expression in the Shuffle T7 Express strain, which complicates the interpretation of the in vivo reporter data.
    - R1-M3: The overstatement of the generalizability of the mechanism based on a single, non-robust simulation of Rob.
    - R1-M4: The lack of a quantitative link between the observed dynamic changes in the simulations and the functional outcome of DNA binding.

- **Assessment against Nature-style criteria**
    - **Originality:** The concept of targeting the dynamics of a transcription factor's N-terminal helix as a means to inhibit DNA binding is a novel and interesting idea. The use of disulfide trapping to test this hypothesis is a creative approach. However, the concept of altering protein dynamics to modulate function is not entirely new.
    - **Scientific importance:** The problem of antimicrobial resistance is of paramount importance. Identifying new targets for inhibitor development, such as the MarA N-terminal helix, has potential translational value. However, the study is primarily a mechanistic investigation, and the direct therapeutic implications are not yet demonstrated.
    - **Interdisciplinary readership:** The work bridges structural biology, computational biophysics, and microbiology. It would be of interest to researchers in these fields. The potential clinical relevance would broaden its appeal, but this is not the primary focus.
    - **Technical soundness:** The experimental design is logical, and the combination of techniques is appropriate. However, the technical soundness is undermined by the concerns raised above, particularly the lack of protein stability data for the key variant and the weak basis for the claim of universality. The simulation methodology is state-of-the-art, but the analysis is not sufficiently quantitative.
    - **Readability for nonspecialists:** The manuscript is generally well-written and the logic is clear. The abstract is accessible. However, the results section is dense and may be challenging for readers without a strong background in molecular dynamics simulations or protein biochemistry. The authors do a good job of explaining the significance of their findings in the discussion.

- **Recommendation posture** Supportive if technical concerns are resolved. The central hypothesis is interesting and the experimental approach is creative. However, the current evidence does not fully establish the mechanistic claim due to the concerns about protein stability and the interpretation of the in vivo data. The claim of generalizability to the AraC/XylS family is not supported by the presented evidence. The authors should be encouraged to address these issues with additional experiments and a more cautious interpretation of their data.

## Risk / unsupported claims
- The claim that the inhibited conformation is "universal for the monomeric members of the AraC/XylS family" is unsupported. It is based on a single simulation of Rob and no experimental validation in any other family member.
- The claim that the I16C/M47C disulfide bond "immobilizes" the N-terminal helix is not fully supported by the data, which show a reduction in mobility, not a complete loss of motion.
- The suggestion that the N-terminal helix is a "promising target for the development of inhibitors" is a reasonable hypothesis but is not directly supported by any inhibitor development data in this manuscript.
- The statement that the multiband pattern of WT MarA in EMSA "could not be related to non-specific binding" is not fully proven. The competitive EMSA experiments are a good start, but the authors themselves state that "further research must be done to clarify this."