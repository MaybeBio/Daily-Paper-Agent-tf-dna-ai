## Review setup
- **Input scope** Full manuscript text including Introduction, Materials and methods, Results, Discussion, and figure legends. Supplementary information referenced but not provided.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text. No access to raw data, supplementary figures, or original images.
- **Shared manuscript claim summary** The authors report that MERS-CoV-nsp5 expression in BEAS 2b cells attenuates type I IFN production by inhibiting IRF3 nuclear translocation, and that this effect depends on nsp5 enzymatic activity. They also present computational docking and molecular dynamics data suggesting potential binding interfaces between nsp5 and IRF3 or KPNA4.
- **Visible evidence base** Figures 1-8 as described in the text, including luciferase reporter assays, Western blots, RT-qPCR, immunofluorescence microscopy, and computational modeling. Supplementary Figures 1 and Tables 1-3 are referenced but not available for review.
- **Missing materials affecting confidence** Supplementary figures and tables, raw Western blot images, statistical analysis details, plasmid validation data, and full experimental replicates. The absence of these materials limits verification of several key claims.

## Reviewer
- **Overall assessment** This manuscript addresses a relevant question regarding MERS-CoV immune evasion, specifically the role of nsp5 in suppressing type I IFN responses. The experimental approach is logical and the data generally support the conclusion that nsp5 inhibits IRF3 nuclear translocation. However, several technical concerns, particularly regarding the computational modeling section and the lack of mechanistic depth, prevent full endorsement. The study is incremental in nature, building on prior work with SARS-CoV nsp5, and the novelty is limited to the MERS-CoV context. The manuscript would benefit from additional experiments to strengthen the mechanistic claims and from a more rigorous presentation of the computational data.

- **Who would be interested in the results, and why** Researchers studying coronavirus-host interactions, innate immune evasion mechanisms, and antiviral drug development would find this work relevant. The identification of nsp5 as an IFN antagonist in MERS-CoV adds to the growing body of literature on coronavirus immune evasion strategies. Those working on 3CL protease inhibitors may also be interested in the potential dual role of these compounds in blocking both viral replication and immune evasion.

- **Major strengths**
  1. The study addresses a gap in the literature regarding MERS-CoV nsp5 and IFN antagonism, which is a relevant and timely topic.
  2. The experimental design includes multiple complementary approaches (reporter assays, Western blot, immunofluorescence, cell fractionation) to support the main conclusion.
  3. The use of BEAS 2b cells, a respiratory epithelial cell line, provides physiological relevance for studying respiratory virus infections.
  4. The inclusion of computational modeling to explore potential binding interfaces adds a structural perspective to the functional data.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that MERS-CoV-nsp5 interacts with IRF3 based on co-immunoprecipitation data (Figure 5A).
- **Evidence pointer** Figure 5A, Immunoprecipitation section
- **Concern** The co-immunoprecipitation experiment is described but the figure legend does not provide sufficient detail on the experimental conditions, including the lysis buffer stringency, washing steps, and whether the interaction was detected under endogenous or overexpressed conditions. The IP was performed using FLAG antibody, but it is unclear whether the interaction is direct or mediated by other proteins. Additionally, the authors do not show a reverse co-IP (pulling down nsp5 and probing for IRF3) to confirm the interaction.
- **Why it matters** The claim of a physical interaction between nsp5 and IRF3 is central to the proposed mechanism. Without robust co-IP data, including appropriate controls and confirmation in both directions, the interaction claim is not fully supported.
- **Resolution test** Provide detailed co-IP conditions, include a reverse co-IP, and show that the interaction is specific (e.g., using a non-specific antibody control or a mutant nsp5). Ideally, confirm the interaction under endogenous conditions or with purified proteins.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors conclude that the inhibitory effect of nsp5 on IFN-β production is dependent on its enzymatic activity, based on experiments with protease inhibitors (Figure 6).
- **Evidence pointer** Figure 6, Treatment section
- **Concern** The use of pharmacological inhibitors (Calpain inhibitor II and Rupintrivir) to infer enzymatic dependence is problematic. These inhibitors are not specific to MERS-CoV nsp5 and may have off-target effects on cellular proteases or other pathways. The authors do not demonstrate that the inhibitors actually inhibit nsp5 enzymatic activity in their experimental system. Furthermore, the concentrations used (10 μM) may be cytotoxic or affect cell viability, which is not assessed. A more rigorous approach would involve using a catalytically dead nsp5 mutant (e.g., C148A) to directly test the requirement for protease activity.
- **Why it matters** The claim that nsp5 enzymatic activity is required for IFN suppression is a key mechanistic finding. The current evidence is indirect and confounded by the use of non-specific inhibitors. Without genetic evidence (e.g., mutant nsp5), the conclusion is not firmly established.
- **Resolution test** Repeat key experiments (IFN-β reporter assay, IRF3 nuclear translocation) using a catalytically inactive nsp5 mutant alongside wild-type nsp5. If the mutant fails to suppress IFN-β, the enzymatic dependence claim would be strongly supported.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that computational modeling identified protein conformations involving masking of the NLS region of IRF3 and KPNA4 with MERS-CoV-nsp5.
- **Evidence pointer** Figures 7 and 8, 3D protein-protein modelling section
- **Concern** The computational modeling section lacks critical details. The authors do not specify the docking scoring function used, the number of poses generated, or the criteria for selecting the "most stable" poses. The MD simulation parameters are only briefly mentioned (CHARMM36m force field, 100 ns), but no convergence analysis or validation of the simulations is provided. The claim that pose 6 masks the NLS region is based on visual inspection, but no quantitative measure of interface burial or binding free energy is given. Additionally, the authors state that AlphaFold3 was used but produced unsuitable structures, yet no details on why they were unsuitable are provided.
- **Why it matters** The computational predictions are presented as supporting evidence for the proposed mechanism. However, without rigorous methodology and quantitative analysis, these predictions remain speculative and do not add strong support to the experimental findings.
- **Resolution test** Provide detailed docking and MD parameters, including convergence criteria, and quantify the interface interactions (e.g., buried surface area, binding free energy). Validate the predictions with mutagenesis experiments targeting the predicted interface residues.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that this study provides "the first evidence" that MERS-CoV-nsp5 can antagonize type I IFN responses.
- **Evidence pointer** Introduction, Discussion
- **Concern** The novelty claim is overstated. While the authors note that no prior studies have identified MERS-CoV-nsp5 as an IFN antagonist, the mechanism described (inhibition of IRF3 nuclear translocation) is similar to that reported for SARS-CoV-2 nsp5. The study is largely confirmatory in a different viral context rather than providing fundamentally new mechanistic insights. The computational predictions of nsp5-IRF3 and nsp5-KPNA4 interactions are interesting but not experimentally validated.
- **Why it matters** The novelty of the findings is a key factor in assessing the significance of the work. If the mechanism is largely analogous to previously described coronavirus nsp5 functions, the incremental advance may not justify publication in a high-impact venue.
- **Resolution test** The authors should temper the novelty claim and more clearly articulate what is genuinely new about their findings, such as the specific interaction interfaces or the relevance to MERS-CoV pathogenesis.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and reproducibility
- **Affected element** Methods, Transfection section
- **Evidence pointer** Materials and methods, Transfection
- **Issue** The transfection protocol states that cells were transfected with 200 or 400 ng/ml plasmid DNA, but the well size and total volume are not specified. This makes it difficult to calculate the actual amount of DNA per well.
- **Required correction** Specify the total amount of DNA per well and the well format (e.g., 6-well, 12-well) used for each experiment.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Statistical analysis
- **Evidence pointer** Materials and methods, Statistical analysis
- **Issue** The statistical methods are described only as using GraphPad Prism, with tests specified in figure legends. However, the number of independent experiments and the exact statistical test used for each comparison are not consistently reported in the text.
- **Required correction** Provide a clear description of the statistical tests used, the number of independent replicates, and whether data met assumptions for parametric testing.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 4E
- **Evidence pointer** Figure 4E legend
- **Issue** The legend notes that there was a mean total of 36 cells in the EV control group and 6 cells in the MERS-CoV-nsp5 group analyzed. This is a very small sample size for the nsp5 group, which may not be representative.
- **Required correction** Increase the number of cells analyzed in the nsp5 group or acknowledge this limitation and provide justification for the sample size.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of potential mechanisms by which nsp5 inhibits IRF3 nuclear translocation is speculative and does not fully integrate the computational predictions with the experimental data. The authors mention several possibilities but do not prioritize or design experiments to distinguish between them.
- **Required correction** Provide a more focused discussion of the most likely mechanism based on the data and outline specific experiments to test the proposed hypotheses.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The introduction cites several studies on SARS-CoV-2 nsp5 and IFN antagonism but does not discuss the specific differences between SARS-CoV-2 and MERS-CoV nsp5 that might explain the observed effects. This would help contextualize the findings.
- **Required correction** Add a brief comparison of the sequence and functional differences between MERS-CoV and SARS-CoV-2 nsp5 that are relevant to the observed IFN antagonism.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Co-IP interaction claim requires more rigorous validation.
  - R1-M2: Enzymatic dependence claim relies on non-specific inhibitors; genetic evidence is needed.
  - R1-M3: Computational modeling lacks methodological detail and quantitative validation.

- **Assessment against Nature-style criteria**
  - **Originality**: Moderate. The study applies known mechanisms of coronavirus nsp5 IFN antagonism to MERS-CoV, which has not been previously reported. However, the fundamental mechanism (inhibition of IRF3 nuclear translocation) is not novel.
  - **Scientific importance**: Moderate. Understanding MERS-CoV immune evasion is relevant, but the findings do not fundamentally change our understanding of coronavirus-host interactions. The clinical significance is limited given the lower prevalence of MERS-CoV compared to SARS-CoV-2.
  - **Interdisciplinary readership**: Limited. The work is primarily of interest to virologists and immunologists. The computational component may attract structural biologists, but the overall scope is narrow.
  - **Technical soundness**: The experimental data are generally sound but have notable gaps, particularly in the co-IP validation, inhibitor specificity, and computational modeling rigor. The lack of mechanistic depth (e.g., no mutagenesis or direct binding assays) weakens the overall case.
  - **Readability for nonspecialists**: The manuscript is clearly written and accessible to a broad scientific audience. The figures are well-organized, though some legends lack sufficient detail.

- **Recommendation posture** Supportive if technical concerns are resolved. The core finding that MERS-CoV-nsp5 inhibits IRF3 nuclear translocation is interesting and potentially publishable, but the current evidence is insufficient to fully establish the mechanistic claims. The authors should address the major concerns, particularly the interaction validation and enzymatic dependence, before the manuscript can be considered for publication.

## Risk / unsupported claims
- The claim that nsp5 "specifically" interacts with IRF3 is not fully supported without a reverse co-IP and appropriate controls.
- The conclusion that nsp5 enzymatic activity is required for IFN suppression is not established due to the use of non-specific inhibitors.
- The computational predictions of nsp5-IRF3 and nsp5-KPNA4 interactions are presented as supportive evidence but are not experimentally validated and lack sufficient methodological detail.
- The statement that this is "the first evidence" of MERS-CoV-nsp5 IFN antagonism is difficult to verify without a comprehensive literature search, and the claim should be tempered.
- The observation that high concentrations of EV enhance IFN-β induction is attributed to cGAS-STING activation, but this is speculative and not experimentally tested.