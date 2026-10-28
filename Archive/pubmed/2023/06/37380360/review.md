## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods, data deposition) as provided.
- **Assessment boundary** Scientific content, methodological soundness, interpretation of results, and support of claims based solely on the supplied material. No external literature or unpublished data were consulted.
- **Shared manuscript claim summary** The authors report the secondary structure of the 110 nt E. coli stress response sRNA OxyS, identify a previously uncharacterized fourth stem-loop (SL4), propose a three-dimensional envelope with a boomerang-like shape, and provide evidence for base-pairing interactions between OxyS and fhlA mRNA at two distinct sites.
- **Visible evidence base** NMR spectroscopy (1D 1H, 2D NOESY, JR-NOESY, 1H-15N SF-HMQC, HNN-COSY, 1H-13C HSQC, 15N-edited HSQC), SAXS with ab initio envelope reconstruction, UV melting, FARFAR2 de novo modeling, unbiased MD simulations, SEC, DLS. Figures referenced: Figures 2-8, Supplemental Figures S1-S22, Supplemental Tables S1-S7.
- **Missing materials affecting confidence** The manuscript text was provided without figures, figure legends, supplemental data files, or the deposited SAXS data (SASDQP8). The absence of these materials limits independent verification of spectral assignments, envelope quality, and model fitting. The authors state that the full-length OxyS contains an additional nucleotide at each terminus due to the cloning strategy, but the exact sequence of the construct used is not fully specified in the text provided.

## Reviewer
- **Overall assessment** This manuscript presents a technically demanding and largely well-executed structural study of a biologically important bacterial sRNA. The combination of NMR, SAXS, and MD simulations is appropriate and the identification of a fourth stem-loop in a region previously predicted to be unstructured is a notable finding. The interaction studies with fhlA mRNA provide useful biochemical validation. However, the manuscript has several weaknesses that need to be addressed. The evidence for the spatial arrangement of the stem-loops is indirect and the authors themselves acknowledge the limitations of the modeling. The claim that the structure is "preorganized for efficient bipartite interaction" is speculative and not directly tested. The presentation of the NMR data is incomplete in the text provided, and the quality of the SAXS envelope and the ensemble analysis needs to be more critically evaluated. The manuscript is of interest to the RNA structure and bacterial gene regulation communities, but the conclusions are not fully established from the evidence presented.
- **Who would be interested in the results, and why** Researchers studying bacterial small noncoding RNAs, particularly those interested in the structure-function relationships of sRNAs and their mechanisms of target recognition. The work is also relevant to the RNA structural biology community, especially those using integrative approaches combining solution-state NMR, SAXS, and molecular dynamics. The finding of a new structural element in a well-studied sRNA will be of interest to those working on OxyS and its regulatory network.
- **Major strengths**
    1.  The study addresses a significant gap in the field by providing the first detailed structural characterization of the full-length OxyS sRNA.
    2.  The combination of multiple biophysical techniques (NMR, SAXS, MD) is a powerful and appropriate strategy for studying a molecule of this size and flexibility.
    3.  The identification of a novel stem-loop (SL4) in a region previously thought to be unstructured is a clear and important finding, supported by NMR evidence.
    4.  The use of site-specific isotopic labeling to overcome spectral overlap is a sophisticated and effective approach.
    5.  The interaction studies with fhlA mRNA, while on model constructs, provide direct biochemical evidence for the proposed base-pairing interactions.
- **Major Concerns**

    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Support for central structural claim
    - **Claim pointer** The authors claim that the 3D models of OxyS, derived from SAXS and MD, demonstrate that OxyS adopts an extended boomerang-like structure with four solvent-exposed stem-loops, and that SL1 and SL2 constitute the long arm while SL3 and SL4 constitute the short arm.
    - **Evidence pointer** Results section "3D structure of OxyS adopts a boomerang-like shape", Figures 6 and 7, Supplemental Figures S13-S16, Supplemental Tables S5-S7.
    - **Concern** The central structural claim of a "boomerang-like" shape with a specific arrangement of stem-loops is based on a low-resolution SAXS envelope and a selected set of models from MD simulations. The Rg of the initial FARFAR2 models (22.54-36.78 Å) was significantly lower than the experimental value (47.6 ± 3.8 Å), indicating that the starting models were not representative of the solution state. While the MD simulations expanded the conformational space, the selection of the final five models was based on fitting to the SAXS data. The text does not provide sufficient detail on the selection criteria, the degree of fit for each model, or the variability within the final ensemble. The authors state that "a certain degree of variability in relative orientations of individual stem-loops is observed," which undermines the confidence in the specific spatial arrangement described. The assignment of SL1/SL2 to the long arm and SL3/SL4 to the short arm appears to be based on the representative model (model 3-1) alone, and the authors note that model 2-1 has a different arrangement. The evidence for a single, dominant "boomerang-like" conformation is therefore weak.
    - **Why it matters** The title and a major conclusion of the paper is the "spatial arrangement of functional domains." If the models are highly variable and the envelope is of low resolution, the specific claim about the arrangement of the four stem-loops is not robustly supported. The biological interpretation, which relies on the distance between SL1 and SL3, is contingent on this structural model.
    - **Resolution test** The authors should provide a more rigorous and quantitative analysis of the ensemble. This should include: (1) a clear description of the selection criteria for the final ensemble; (2) a figure showing the superposition of the final ensemble models with their fit to the SAXS data; (3) a quantitative measure of the variability in the relative positions of the stem-loops across the ensemble (e.g., a distance matrix or principal component analysis); and (4) a discussion of whether the SAXS data can distinguish between the proposed arrangement and other possible arrangements. If the data only support an extended, flexible structure, the claims should be moderated accordingly.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** No
    - **Axis** Support for functional claim
    - **Claim pointer** The authors state that "Spatial positioning of the two regions within OxyS suggests their preorganization for efficient bipartite interaction with fhlA and subsequent regulation of stress response."
    - **Evidence pointer** Discussion section, Results section "fhlA mRNA interacts with stem-loops SL1 and SL3 in OxyS", Figure 8.
    - **Concern** The claim of "preorganization" is a functional interpretation that goes beyond the structural data presented. The authors have shown that SL1 and SL3 can independently base-pair with their respective target sites in fhlA mRNA in vitro. However, they have not demonstrated that the spatial arrangement of these loops in the context of the full-length OxyS enhances the rate or affinity of this interaction. The distance between the two sites on the mRNA and the flexibility of the OxyS structure could mean that the "preorganization" is not functionally relevant. The authors do not test the interaction with a full-length fhlA mRNA or in a competitive binding assay.
    - **Why it matters** This claim is a key part of the biological narrative of the paper. Overstating the functional implications of a static structural model can be misleading. The structural data can suggest a hypothesis, but it does not provide evidence for it.
    - **Resolution test** The authors should either (a) perform experiments to test the functional significance of the spatial arrangement (e.g., by comparing the binding kinetics of full-length OxyS to a variant where the linker is lengthened or the orientation of the stem-loops is altered), or (b) temper the language in the discussion to clearly state that the spatial arrangement is a hypothesis that remains to be tested.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Completeness of evidence for interaction
    - **Claim pointer** The authors claim to provide "evidence of base-pairing between OxyS and fhlA mRNA" and specifically map the interaction to SL1 and SL3.
    - **Evidence pointer** Results section "fhlA mRNA interacts with stem-loops SL1 and SL3 in OxyS", Figure 8, Supplemental Figures S17-S22.
    - **Concern** The interaction studies are performed with truncated model constructs (SL1Δ17, SL3, fhlA1, fhlA41) rather than the full-length OxyS and fhlA mRNA. While this is a reasonable approach for NMR studies, the authors do not demonstrate that the interactions observed with the isolated domains are representative of the interactions in the full-length context. The authors state that the interaction requires 5 mM Mg2+ and that this partially unfolds the constructs. It is not clear if the full-length OxyS would behave in the same way. The number of base pairs formed in the complexes (6 and 4) is less than the number predicted by sequence complementarity (9 and 6), and the authors do not fully explain this discrepancy.
    - **Why it matters** The biological function of OxyS is to regulate fhlA. If the interaction is only demonstrated with isolated domains, the relevance to the full-length system is not fully established. The discrepancy between predicted and observed base pairs could indicate that the interaction is weaker or different in the full-length context.
    - **Resolution test** The authors should provide a more detailed discussion of the limitations of using truncated constructs. Ideally, they would perform a gel-shift or similar assay with the full-length OxyS and a longer fhlA mRNA fragment to confirm the interaction and its stoichiometry. At minimum, they should clearly state that the interaction was mapped using isolated domains and that the full-length interaction has not been directly characterized.

- **Minor Comments**

    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity and completeness of methods
    - **Affected element** Materials and Methods, NMR spectroscopy
    - **Evidence pointer** Materials and Methods section "NMR spectroscopy"
    - **Issue** The methods section describes the NMR experiments but does not provide specific details on the concentrations of the RNA samples, the buffer conditions for each experiment, or the temperature at which the spectra were acquired (beyond stating 5°C for some experiments and 25°C for others). The text mentions "1D 15N-edited HSQC spectra" but does not specify the pulse sequence used.
    - **Required correction** Provide a more detailed description of the NMR experimental parameters, including sample concentrations, buffer compositions, temperatures, and the specific pulse sequences used for each experiment. This is essential for reproducibility.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Data presentation
    - **Affected element** Results section "3D structure of OxyS adopts a boomerang-like shape"
    - **Evidence pointer** Figure 7, Supplemental Figure S15.
    - **Issue** The text refers to the "averaged envelope of the most representative cluster" but does not describe the clustering process or how the "most representative" cluster was chosen. The number of clusters and the population of each cluster are not stated.
    - **Required correction** Add a brief description of the clustering methodology and the criteria used to select the representative cluster. This will allow the reader to assess the robustness of the envelope.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Interpretation of UV melting data
    - **Affected element** Results section "Truncated SL1, SL2, and SL3 form stable stem-loops", Supplemental Figure S5.
    - **Issue** The UV melting experiments are used to support the stability of the isolated stem-loops. However, the text does not report the melting temperatures (T1/2) for SL1 and SL2, only for SL3 (84°C) and SL2 (57°C). The T1/2 for SL1 is not mentioned.
    - **Required correction** Report the T1/2 values for all three stem-loops in the text or in the figure legend. This will allow for a direct comparison of their relative stabilities.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Terminology
    - **Affected element** Discussion section
    - **Evidence pointer** Discussion section, first paragraph
    - **Issue** The authors state that "the models we obtained are in good agreement with experimental data and describe the overall shape of OxyS." The term "good agreement" is vague. The text should provide the specific χ2 values for the final models and a description of what constitutes a "good" fit in this context.
    - **Required correction** Provide the χ2 values for the final ensemble and a brief explanation of how these values are interpreted in the context of SAXS model validation.

## Risk / unsupported claims
- The claim that OxyS adopts a specific "boomerang-like" shape with a defined spatial arrangement of SL1/SL2 and SL3/SL4 is not robustly supported by the data presented. The variability within the final ensemble and the acknowledged limitations of the modeling make this a weak claim.
- The claim that the spatial arrangement of SL1 and SL3 suggests "preorganization for efficient bipartite interaction" is speculative and not directly tested by any experiment.
- The statement that the interaction between OxyS and fhlA is "confirmed" is based on experiments with truncated model constructs. The relevance of these findings to the full-length system is not demonstrated.
- The authors state that the "conformational plasticity may play a key role in the capability of OxyS to interact with multiple targets." This is a reasonable hypothesis but is not supported by any direct experimental evidence in this manuscript.
- The claim that the newly identified SL4 "significantly shortens the nonstructured linker" and that this "could be important for the interaction with fhlA" is a structural observation with a speculative functional interpretation. The functional importance is not tested.

## Assessment against Nature-style criteria
- **Originality**: The work is original in its specific focus on the full-length OxyS sRNA structure. While the individual techniques are established, their combination and application to this specific, biologically important sRNA is novel. The identification of a new structural element (SL4) is a new finding.
- **Scientific importance**: The work is of importance to the RNA biology field, as it provides the first structural model of a key stress-response sRNA. This could have implications for understanding how OxyS recognizes its multiple targets. However, the importance is somewhat limited by the lack of functional validation of the structural model.
- **Interdisciplinary readership**: The work is primarily of interest to structural biologists and RNA biologists. The use of multiple biophysical techniques may appeal to a broader readership, but the biological context is specific to bacterial stress responses. The paper is unlikely to have a broad impact beyond these fields.
- **Technical soundness**: The technical execution of the experiments appears to be sound. The use of site-specific labeling is a strength. However, the analysis and interpretation of the SAXS and MD data, particularly the selection of the final ensemble and the claims made from it, are not presented with sufficient rigor to fully support the conclusions.
- **Readability for nonspecialists**: The manuscript is written in a technical style that assumes a high level of familiarity with NMR, SAXS, and MD methods. The abstract is accessible, but the results and discussion sections would be challenging for a nonspecialist to follow. The key findings could be communicated more clearly.

## Recommendation posture
**Supportive if technical concerns are resolved.** The manuscript presents a potentially valuable structural characterization of an important sRNA. The identification of SL4 is a solid finding. However, the central claim about the "spatial arrangement" of the domains is not sufficiently supported by the analysis presented. The authors need to provide a more rigorous and quantitative analysis of their SAXS and MD data to demonstrate that the proposed arrangement is robust. The functional claims should be moderated or supported by additional experiments. The manuscript is not currently acceptable for publication in its present form.