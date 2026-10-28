## Review setup
- **Input scope** Full manuscript text (including abstract, introduction, methods, results, discussion, conclusions, and supplementary information description) as provided by the user.
- **Assessment boundary** The scientific content, methodology, data interpretation, and claims as presented in the supplied text. No external literature or unpublished data were consulted.
- **Shared manuscript claim summary** The manuscript reports that copper(II) and silver(I) complexes of 1,10-phenanthroline-5,6-dione (phendione) interact with double-stranded DNA via minor groove binding and/or intercalation, with the copper complex showing higher binding affinity, ability to inhibit topoisomerase I, and induce oxidative DNA cleavage. The authors propose that these DNA interactions contribute to the antimicrobial activity of the complexes against Pseudomonas aeruginosa.
- **Visible evidence base** Molecular docking results (Fig. 1B, Tables S1 and S2), competitive ethidium bromide displacement assays (Fig. 2, Table 1), fluorescence quenching with EtBr and Hoechst 33258 (Fig. 2, Table 1), topoisomerase I relaxation assays (Fig. 3), DNA cleavage assays with and without reductant (Figs. 3 and 4), ROS scavenger studies (Fig. 5), ESI-MS stability studies (Fig. 6, Figs. S2 and S3), UV-Vis stability studies (Fig. 6C), PI displacement assays with bacterial cells (Table 2), DNA fragmentation gel (Fig. 7A), and TUNEL assay (Fig. 7B).
- **Missing materials affecting confidence** The full supplementary information file (PDF 528 KB) was not provided, including Tables S1 and S2 and Figures S1-S3. Raw data for statistical analyses, detailed experimental conditions for some assays, and the full gel images were not available for independent verification.

## Reviewer

- **Overall assessment** This manuscript presents a systematic investigation of the DNA-binding and DNA-cleavage properties of two phendione-based metal complexes, with a focus on their potential relevance to antimicrobial activity against P. aeruginosa. The work combines computational, biochemical, and cellular approaches, which is commendable. However, several technical concerns and interpretive gaps limit the strength of the conclusions. The claim that DNA interaction is a primary mechanism of antimicrobial action is not fully established, as the study does not directly link the observed DNA damage to bacterial cell death. Additionally, the quantitative analysis of DNA cleavage and the interpretation of the ESI-MS data require further clarification. The manuscript is of interest to the bioinorganic chemistry and antimicrobial research communities, but the evidence presented does not fully support the broad conclusions drawn.

- **Who would be interested in the results, and why** Researchers in the fields of bioinorganic chemistry, antimicrobial drug discovery, and nucleic acid chemistry would find this work relevant. The study provides comparative data on the DNA-binding modes of Cu(II) and Ag(I) phendione complexes, which is useful for structure-activity relationship studies. The potential link between metallo-nuclease activity and antimicrobial efficacy is a topic of ongoing interest, and the data presented here contribute to that discussion, albeit with limitations.

- **Major strengths**
  1. The study employs a multi-technique approach, combining in silico docking, in vitro biochemical assays, and cellular experiments, which provides a broad perspective on the DNA interactions of the complexes.
  2. The comparative analysis of Cu-phendione and Ag-phendione, along with the parent ligands, allows for insights into the role of the metal center in DNA binding and cleavage.
  3. The inclusion of bacterial genomic DNA fragmentation and TUNEL assays extends the findings to a clinically relevant pathogen, P. aeruginosa, which adds translational relevance.
  4. The ESI-MS stability studies, particularly under reducing conditions, provide valuable information on the speciation of the complexes, which is often overlooked in similar studies.

- **Major Concerns**

  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Experimental design and data interpretation
  - **Claim pointer** The manuscript claims that "Cu-phendione was found to first unwind negatively SC DNA prior to introducing DNA damage at concentrations greater than 50 µM" and that this indicates intercalative activity.
  - **Evidence pointer** Figure 3A and 3B, topoisomerase I relaxation assay section.
  - **Concern** The interpretation of the topoisomerase I relaxation assay is not sufficiently rigorous. The authors state that Cu-phendione unwinds DNA at low concentrations and causes damage at higher concentrations, but the distinction between unwinding and nicking is not clearly quantified. The gel images (Fig. 3) are described qualitatively, and no densitometric analysis is provided for this assay. Furthermore, the claim that Ag-phendione induces positive supercoils at 10 µM is unusual and not adequately explained. The authors do not discuss whether this effect is due to intercalation, which typically unwinds DNA, or another mechanism. The lack of quantitative data and mechanistic discussion weakens the conclusion that these complexes act as intercalators.
  - **Why it matters** The mode of DNA binding (intercalation vs. groove binding) is a central claim of the manuscript. If the topoisomerase assay is not properly quantified and interpreted, the conclusion that the complexes intercalate is not supported. This affects the overall narrative of the mechanism of action.
  - **Resolution test** The authors should provide densitometric quantification of the topoisomerase I relaxation gels, showing the proportion of supercoiled, relaxed, and nicked DNA at each concentration. They should also include a discussion of the expected electrophoretic mobility shifts for intercalators versus groove binders, and provide a control with a known intercalator (e.g., ethidium bromide) under identical conditions.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Data interpretation and claim support
  - **Claim pointer** The manuscript claims that "Cu-phendione promotes oxidative DNA damage" and that this is mediated by reactive oxygen species (ROS), specifically superoxide.
  - **Evidence pointer** Figure 5, DNA cleavage in the presence of ROS scavengers section.
  - **Concern** The ROS scavenger experiments are only shown for Tiron (superoxide scavenger), and the authors state that other scavengers (D-mannitol, KI, D2O) "play only a minor role" and were "not further investigated" with data not shown. This is a significant omission. The conclusion that superoxide is the primary ROS species is based on a single scavenger, and the lack of data for other scavengers prevents a comprehensive assessment. Additionally, the concentration of Tiron (10 mM) is high, and its specificity for superoxide at this concentration should be discussed. The authors also do not address whether the observed DNA cleavage in the presence of reductant is truly ROS-dependent or could be due to direct metal-mediated hydrolysis.
  - **Why it matters** The mechanism of DNA cleavage is a key finding. If the ROS-dependence is not rigorously established, the claim of oxidative damage is weakened. This is important for understanding the potential in vivo mechanism and for comparing with other metallo-nucleases.
  - **Resolution test** The authors should provide data for all ROS scavengers tested, including dose-response curves. They should also include a control with a metal chelator (e.g., EDTA) to confirm the role of the metal ion. Additionally, they should discuss the specificity of Tiron at the concentration used and consider using a more specific superoxide scavenger or a combination of scavengers.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Relevance of findings to antimicrobial activity
  - **Claim pointer** The manuscript concludes that "the antimicrobial activity of Cu-phendione could, in part, be correlated with the artificial metallo-nuclease activity of Cu-phendione."
  - **Evidence pointer** Conclusions section, Figure 7.
  - **Concern** The link between the observed DNA damage in vitro and the antimicrobial activity is not directly established. The study shows that Cu-phendione can fragment bacterial genomic DNA and induce TUNEL positivity, but it does not demonstrate that this DNA damage is the cause of bacterial cell death. The concentrations used in the DNA damage assays (e.g., 15 µM for bacterial treatment) are not directly compared to the MIC values, and no time-course correlation between DNA damage and cell viability is provided. The authors also do not rule out other mechanisms of action, such as membrane disruption or protein damage, which could contribute to the antimicrobial effect.
  - **Why it matters** The manuscript's title and conclusions emphasize the "multi-modal activity" of the complexes. If the DNA damage is not shown to be a primary or contributing mechanism of cell death, the conclusions are overstated. This is critical for the translational relevance of the findings.
  - **Resolution test** The authors should perform a time-course experiment correlating DNA fragmentation (e.g., by gel electrophoresis or TUNEL) with bacterial viability (CFU counts) at various concentrations of Cu-phendione. They should also compare the MIC values with the concentrations required for DNA damage. Additionally, they could use a non-DNA-damaging analog of the complex as a control to assess the contribution of DNA damage to antimicrobial activity.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical rigor of ESI-MS analysis
  - **Claim pointer** The manuscript claims that "the [Cu(phendione)2]2+ cation appears to have greater solution stability and is less easily reduced compared to [Cu(phen)3]2+" based on ESI-MS data.
  - **Evidence pointer** Figure 6A and 6B, ESI-MS stability studies.
  - **Concern** The ESI-MS data are presented qualitatively, with descriptions of ion intensities but no quantitative analysis. The authors do not provide the relative abundances of the species over time, nor do they discuss the potential for in-source reduction or oxidation artifacts. The claim that the phendione complex is "less easily reduced" is not supported by electrochemical data, and the ESI-MS results alone are insufficient to make this conclusion. Additionally, the authors note that the experiments were performed "in situ" without DNA, which limits the relevance to the DNA-binding studies.
  - **Why it matters** The stability and redox behavior of the complexes are important for understanding their mechanism of action. If the ESI-MS data are not rigorously quantified and interpreted, the conclusions about stability are speculative.
  - **Resolution test** The authors should provide quantitative data on the relative ion abundances of the complexes over time, with error bars. They should also consider performing cyclic voltammetry to directly measure the redox potentials of the complexes. Additionally, they should discuss the limitations of ESI-MS for studying redox processes and consider complementary techniques.

- **Minor Comments**

  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of presentation
  - **Affected element** Figure 1B
  - **Evidence pointer** Figure 1B, molecular docking section.
  - **Issue** The figure legend for Figure 1B is not provided in the text, and the figure itself is not described in sufficient detail. The authors state that "the best docking poses for DNA with the test compounds" are shown, but it is unclear which complex is shown in which panel and what the color coding represents.
  - **Required correction** The authors should provide a detailed figure legend for Figure 1B, including the identity of each complex, the DNA atoms or residues involved in interactions, and the type of interaction (e.g., hydrogen bond, hydrophobic) with distances.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Table 2
  - **Evidence pointer** Table 2, PI displacement assay.
  - **Issue** The table reports mean fluorescence intensity and percentage of fluorescent cells, but the number of replicates and the statistical test used are only mentioned in the footnote. The authors state "analysis of variance one-way (ANOVA) (Dunnett’s multiple comparison test)" but do not provide F-values, degrees of freedom, or exact p-values.
  - **Required correction** The authors should provide the number of independent experiments, the exact p-values for each comparison, and the error bars in the table or figure.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Methodological detail
  - **Affected element** Molecular docking
  - **Evidence pointer** Molecular docking section.
  - **Issue** The docking protocol is described briefly, but key parameters are missing, such as the search space dimensions, the number of runs, and the scoring function used. The authors state that "the grid center at the center of mass" was used, but the box size is not given.
  - **Required correction** The authors should provide full details of the docking protocol, including the grid box dimensions, the exhaustiveness or number of runs, and the version of AutoDock Vina used.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretation of binding constants
  - **Affected element** Table 1
  - **Evidence pointer** Table 1, competitive EtBr displacement.
  - **Issue** The Kapp values are reported for the complexes and compared to actinomycin D and netropsin. However, the authors do not discuss the potential limitations of the Kapp calculation, which assumes a simple competitive binding model. The Kapp for Ag-phendione is relatively low, and the authors do not comment on whether this is consistent with the observed biological activity.
  - **Required correction** The authors should briefly discuss the limitations of the Kapp determination and consider whether the binding affinity correlates with the antimicrobial activity.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of quantitative analysis of topoisomerase I relaxation assay.
  - R1-M2: Incomplete ROS scavenger data, with only Tiron shown.
  - R1-M3: No direct correlation between DNA damage and antimicrobial activity.
  - R1-M4: Qualitative ESI-MS data without quantitative support for stability claims.

- **Assessment against Nature-style criteria**
  - **Originality** The work is moderately original, as it applies known concepts of metallo-nuclease activity to phendione complexes and extends them to P. aeruginosa. However, the approach is not conceptually novel, and similar studies on copper-phenanthroline complexes exist.
  - **Scientific importance** The findings are of interest to the bioinorganic and antimicrobial communities, but the importance is limited by the lack of a direct mechanistic link between DNA damage and antimicrobial activity. The study does not provide a significant advance in understanding the fundamental chemistry or biology.
  - **Interdisciplinary readership** The manuscript is likely to appeal to a niche audience of bioinorganic chemists and microbiologists. The relevance to a broader readership, such as clinicians or drug developers, is not clearly demonstrated.
  - **Technical soundness** The technical quality is mixed. The biochemical assays are generally well-executed, but the lack of quantitative analysis in key experiments (topoisomerase assay, ESI-MS) and the incomplete ROS scavenger data undermine the robustness of the conclusions.
  - **Readability for nonspecialists** The manuscript is written in a technical style that assumes familiarity with bioinorganic chemistry and DNA-binding assays. The introduction provides some context, but the results and discussion sections are dense and may be challenging for nonspecialists to follow.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses a relevant topic and provides a reasonable body of data, but the major concerns regarding data quantification, mechanistic interpretation, and the link to antimicrobial activity must be addressed before the conclusions can be considered established. The authors should provide additional experiments and analyses to strengthen the case.

## Risk / unsupported claims
- The claim that Cu-phendione acts as an intercalator is not fully supported by the topoisomerase I assay, which lacks quantitative analysis.
- The claim that superoxide is the primary ROS species responsible for DNA cleavage is based on a single scavenger experiment, with data for other scavengers not shown.
- The conclusion that DNA damage contributes to the antimicrobial activity of Cu-phendione is not directly supported by experiments correlating DNA damage with cell viability.
- The claim that Ag-phendione does not induce DNA damage is based on a single experiment (Fig. 3B) and is not supported by additional assays or discussion.
- The stability of the complexes, as inferred from ESI-MS, is not quantitatively assessed, and the relevance of the in situ conditions to biological environments is unclear.