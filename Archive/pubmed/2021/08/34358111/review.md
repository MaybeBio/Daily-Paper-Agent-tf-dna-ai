## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, conclusions) without figures, tables, or supplementary materials
- **Assessment boundary** Scientific content, experimental design, data interpretation, and internal consistency of the reported findings
- **Shared manuscript claim summary** The authors report that four half-sandwich Ir(III) complexes with phosphine ligands derived from fluoroquinolones interact with DNA via moderate intercalation and predominant minor groove binding, without double-strand cleavage, and bind to HSA and apo-transferrin at specific sites, supporting a mechanism of action distinct from Pt(II) drugs and involving ROS generation.
- **Visible evidence base** Text descriptions of fluorescence spectroscopy, circular dichroism, gel electrophoresis, and molecular docking results; numerical values for Stern-Volmer constants and binding distances are partially reported
- **Missing materials affecting confidence** All figures, tables, and supplementary materials are absent, preventing verification of spectral data, gel images, CD spectra, and docking poses

## Reviewer
- **Overall assessment** The manuscript addresses a relevant topic in medicinal inorganic chemistry, namely the interaction of Ir(III) complexes with biomacromolecules to rationalize their anticancer activity. The experimental approach is multi-technique and generally appropriate. However, the absence of figures and tables in the provided material severely limits the ability to assess data quality and support for the claims. Several quantitative claims lack sufficient detail, and some interpretations appear to overreach the presented evidence. The manuscript would benefit from clearer presentation of control experiments and more rigorous analysis of binding parameters.
- **Who would be interested in the results, and why** Researchers in the fields of bioinorganic chemistry, anticancer drug design, and metallodrug mechanism of action studies would find these results relevant. The comparative analysis of DNA versus protein binding for a series of structurally related Ir(III) complexes provides useful structure-activity information that could guide further development of half-sandwich iridium anticancer agents.
- **Major strengths** The study employs a complementary set of experimental and computational techniques to characterize biomolecular interactions. The comparison across four structurally related complexes allows for structure-activity correlations. The inclusion of both DNA and protein targets provides a more complete picture of potential biological interactions. The molecular docking studies are used to rationalize experimental observations rather than as standalone evidence.
- **Major Concerns** The manuscript lacks quantitative binding constants for DNA interactions, which are standard for such studies. The claim of "moderate intercalation" is not supported by quantitative data. The relationship between the docking results and experimental binding affinities is not rigorously established. The biological relevance of the observed interactions is not discussed in sufficient depth. The absence of figures and tables makes it impossible to verify the quality of spectral data and the validity of the interpretations.
- **Minor Comments** The manuscript contains some typographical errors and inconsistent notation. The methods section would benefit from more detail on data analysis procedures. The discussion of the relationship between ROS generation and DNA damage could be more nuanced.
- **Technical failings that need to be addressed before the case is established** The lack of quantitative binding constants for DNA and protein interactions; the absence of control experiments for the fluorescence quenching studies; the insufficient description of the molecular docking validation; the lack of statistical analysis for replicate measurements
- **Assessment against Nature-style criteria** Originality: The work is incremental, building on the authors' prior publications on similar complexes. Scientific importance: Moderate, as it provides mechanistic insight but does not establish a fundamentally new concept. Interdisciplinary readership: Limited, as the content is primarily of interest to specialists in metallodrug chemistry. Technical soundness: Cannot be fully assessed without figures and tables, but the described methods are generally appropriate. Readability for nonspecialists: The manuscript is written in a technical style that would be challenging for nonspecialists to follow.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires major revisions, including the provision of quantitative binding data, clearer presentation of results, and more rigorous data analysis, before the claims can be adequately evaluated.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative evidence
- **Claim pointer** The authors claim that the complexes interact with DNA by "moderate intercalation and predominance of minor groove binding" based on fluorescence quenching and docking studies.
- **Evidence pointer** Section 2.2.1, Table 1 (not visible)
- **Concern** The manuscript does not report quantitative binding constants (e.g., Kb) for the DNA interaction, which are essential to support the claim of "moderate intercalation." The Stern-Volmer constants (Ksv) are reported, but these are not equivalent to binding constants and do not distinguish between intercalation and groove binding. The claim of intercalation appears to be inferred primarily from the docking results, which is insufficient without corroborating experimental evidence such as viscosity measurements, DNA melting studies, or competitive binding assays with a known intercalator.
- **Why it matters** The mode of DNA binding is a central claim of the manuscript and is used to differentiate these complexes from Pt(II) drugs. Without quantitative binding data and appropriate control experiments, the claim is not adequately supported.
- **Resolution test** Provide binding constants (Kb) from fluorescence or UV-vis titration data, and include additional experiments that can distinguish intercalation from groove binding (e.g., viscosity, DNA melting temperature, or competitive displacement assays with Hoechst 33258 and ethidium bromide).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data presentation and verification
- **Claim pointer** The manuscript reports results from fluorescence spectroscopy, circular dichroism, gel electrophoresis, and molecular docking, and draws conclusions about binding modes and affinities.
- **Evidence pointer** All figures and tables are listed but not provided
- **Concern** The provided material does not include any figures, tables, or supplementary data. This makes it impossible to verify the quality of the spectral data, the gel images, the CD spectra, or the docking poses. Several claims, such as the "slight changes" in CD spectra or the "distinct binding mode" of IrPSf, cannot be evaluated without the actual data.
- **Why it matters** The conclusions of the manuscript rest entirely on the presented data. Without access to the figures and tables, the validity of the interpretations cannot be assessed, and the manuscript cannot be properly reviewed.
- **Resolution test** Provide all figures, tables, and supplementary materials for review. Ensure that all data presented in the text are clearly shown in the corresponding figures or tables.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of docking results
- **Claim pointer** The authors state that the docking results confirm the experimental findings and support the binding modes, including the claim that all complexes bind within 5 Å of Trp214 in HSA and within the apo-Tf binding sites.
- **Evidence pointer** Sections 2.2.2, 2.3.2, 2.3.4, Table 2 (not visible)
- **Concern** The docking results are presented as supporting evidence, but the manuscript does not provide details on the scoring function validation, the treatment of the metal center, or the flexibility of the protein side chains. The claim that the docking results "confirm" the experimental findings is an overstatement, as docking is a predictive tool and not a direct measurement. The difference in binding energy between the apo-Tf pockets (approximately 3 kcal/mol) is presented as significant, but the error of the scoring function is not discussed.
- **Why it matters** Overinterpretation of docking results can lead to misleading conclusions about binding modes and affinities. The manuscript should present docking as a hypothesis-generating tool rather than as confirmation of experimental data.
- **Resolution test** Provide a more cautious interpretation of the docking results, including a discussion of the limitations of the method. Include validation of the docking protocol, such as redocking of a co-crystallized ligand, and discuss the uncertainty in the energy estimates.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological relevance
- **Claim pointer** The authors suggest that the interaction of the complexes with HSA and apo-Tf is relevant for drug delivery and that the mechanism of action is different from Pt(II) drugs.
- **Evidence pointer** Sections 1, 2.3, 4
- **Concern** The manuscript does not discuss the biological relevance of the observed protein binding in sufficient depth. For example, the concentration range used in the protein binding studies is not compared to the concentrations that are cytotoxic in cell-based assays. The potential impact of protein binding on drug efficacy or toxicity is not addressed. The claim that the mechanism of action is "different from DNA targeting typical of Pt(II) drugs" is not fully supported, as the manuscript does not directly compare the activity of these complexes with Pt(II) drugs in the same experimental system.
- **Why it matters** The biological relevance of the findings is a key aspect of the manuscript's significance. Without a discussion of the relationship between the observed binding and the cytotoxic activity, the relevance of the study is unclear.
- **Resolution test** Include a discussion of the relationship between the binding affinities and the cytotoxic concentrations. Compare the mechanism of action with that of a Pt(II) drug in the same experimental system, or clearly state the limitations of the comparison.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and consistency
- **Affected element** Section 2.2.1, text
- **Evidence pointer** Section 2.2.1
- **Issue** The text states that the complexes exhibit "multimodal DNA interaction" but the description of the different modes is not systematic. The order of presentation of the results for the different complexes is not consistent throughout the section.
- **Required correction** Organize the presentation of results for each complex in a consistent manner, and clearly distinguish between the evidence for intercalation, groove binding, and electrostatic interactions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Section 3.2.3, fluorescence quenching analysis
- **Evidence pointer** Section 3.2.3
- **Issue** The manuscript mentions that the Inner Filter Effect was considered and corrected, but the equation provided appears incomplete or incorrectly formatted. The description of the Stern-Volmer analysis is brief and does not mention how the data were fitted or how the constants were calculated.
- **Required correction** Provide the complete and correct equation for the Inner Filter Effect correction, and describe the fitting procedure used to obtain the Stern-Volmer constants.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data interpretation
- **Affected element** Section 2.3.3, apo-transferrin interaction
- **Evidence pointer** Section 2.3.3, Table 4 (not visible)
- **Issue** The manuscript states that the interaction between the complexes and apo-Tf follows a static quenching mechanism, but the evidence for this is not clearly presented. The Ksv values are reported, but the bimolecular quenching rate constants (kq) are not calculated or discussed.
- **Required correction** Calculate and report the bimolecular quenching rate constants (kq) to support the claim of static quenching, and discuss the implications of the values.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Language and style
- **Affected element** Throughout the manuscript
- **Evidence pointer** Location not provided
- **Issue** The manuscript contains several instances of awkward phrasing and grammatical errors that impede readability. For example, "the complexes' luminescence spectra showed that IrPCp, IrPNr and IrPLm are characterized by a red luminescence" could be more concisely stated.
- **Required correction** Perform a thorough language edit to improve clarity and conciseness.

## Risk / unsupported claims
- The claim of "moderate intercalation" is not supported by quantitative binding data or appropriate control experiments.
- The claim that the complexes "can bind to the proteins in order to be transferred" is speculative and not directly supported by the data.
- The statement that the complexes "will not exhibit high genotoxicity" is an extrapolation from the absence of double-strand cleavage and is not directly tested.
- The claim that the docking results "confirmed" the experimental findings is an overstatement, as docking is a predictive tool with inherent limitations.
- The biological relevance of the protein binding studies is not established, as the concentrations used are not compared to cytotoxic concentrations.