## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, discussion, data availability, supplementary notes) as provided.
- **Assessment boundary** Scientific claims, methodological soundness, data interpretation, and presentation quality as inferable from the provided text. No access to raw data, spectra, or supplementary files beyond what is described.
- **Shared manuscript claim summary** The authors propose that chemical crosslinking (using mechlorethamine, diepoxybutane, and formaldehyde) combined with a new search engine (NuXL) extends and complements UV crosslinking for identifying RNA/DNA-protein interaction sites by mass spectrometry, both in vitro and in vivo, and enables integrative structural modelling.
- **Visible evidence base** Descriptions of experimental procedures, results summaries, and references to figures and tables (e.g., Figures 1, 3, 4, 5, 6, 7; Supplementary Figures S1-S17; Supplementary Tables S1-S13). Specific numerical data, spectra, and statistical outputs are not fully visible.
- **Missing materials affecting confidence** Raw mass spectrometry data, detailed search engine parameters and scoring functions, complete statistical analysis outputs, validation metrics (e.g., FDR curves, decoy distributions), and full versions of supplementary figures and tables. The manuscript is a preprint and may lack final formatting and some methodological details.

## Reviewer
- **Overall assessment** This manuscript presents a substantial methodological advance in the field of nucleic acid-protein crosslinking mass spectrometry. The introduction of chemical crosslinkers as a complement to UV, the development of the NuXL search engine, and the large-scale in vivo application in E. coli are potentially significant contributions. The work is technically ambitious and the results, as described, are promising. However, the current manuscript has several areas that require clarification and strengthening, particularly regarding the validation of NuXL, the specificity of chemical crosslinking, and the statistical rigor of the enrichment analyses. The claims of "unprecedented accuracy" for AlphaFold3 models, while interesting, need to be more carefully contextualized and supported. Overall, the manuscript is of high interest to the community but requires revisions to fully establish its conclusions.
- **Who would be interested in the results, and why** Researchers in the fields of structural biology, molecular biology, and proteomics, specifically those studying RNA-protein and DNA-protein interactions, ribonucleoprotein complexes, and the development of crosslinking mass spectrometry methods. The NuXL software will be of direct use to this community. The large E. coli dataset provides a valuable resource. The work is also relevant to computational biologists interested in integrative modelling and the application of AI-based structure prediction.
- **Major strengths**
    1.  The conceptual advance of using chemical crosslinkers to complement UV crosslinking is logical and potentially impactful, addressing a known limitation of UV-based methods.
    2.  The development of NuXL as a dedicated, open-source search engine with FDR control is a significant and necessary contribution to the field.
    3.  The demonstration of the method in vivo in E. coli, resulting in a large dataset of crosslinked proteins and sites, is a major strength and provides a useful resource.
    4.  The application of the method to provide spatial restraints for structural modelling, including the comparison with AlphaFold3 predictions, is forward-looking and demonstrates the utility of the data.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical soundness and validation
    - **Claim pointer** The claim that NuXL provides "robust and fast identification of such crosslinks at amino acid resolution" and that it outperforms previous approaches (e.g., RNPxl) is central to the paper.
    - **Evidence pointer** Results section "NuXL – a nucleic acid–protein XL-MS search engine for automated and sensitive crosslink site identification"; Methods section "XL-MS data analysis using NuXL"; Supplementary Methods.
    - **Concern** The validation of NuXL is not sufficiently detailed in the provided text. The comparison to RNPxl is mentioned, but the specific metrics (e.g., sensitivity, precision, FDR calibration) are not presented. The claim of a 1.2- to 8.1-fold higher identification rate is made, but the basis for this comparison (e.g., on which datasets, with what parameters) is not clear. A rigorous benchmarking against existing tools on a well-defined dataset, including an analysis of false discovery rates and the ability to correctly localize crosslink sites, is essential to support the central claims of the paper.
    - **Why it matters** The entire manuscript rests on the reliability of the NuXL search engine. Without a clear and robust validation, the biological conclusions drawn from the E. coli dataset and the structural modelling are not fully trustworthy.
    - **Resolution test** Provide a detailed benchmarking section in the Results or Supplementary Materials, comparing NuXL against RNPxl and potentially other tools (e.g., MSFragger) on the same datasets. Include precision-recall curves, FDR calibration plots, and a clear description of the datasets and parameters used. Show examples of correctly and incorrectly localized crosslinks.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Specificity and interpretation of chemical crosslinking
    - **Claim pointer** The claim that chemical crosslinking "complements and extends UV crosslinking" and that it identifies different interaction sites.
    - **Evidence pointer** Results sections "UV combined with chemical crosslinking provides spatial constraints in structural modelling of protein-RNA complexes" and "NuXL facilitates identification of UV and chemical crosslinking sites in E. coli"; Figures 1, 3, 4.
    - **Concern** The manuscript does not adequately address the specificity of the chemical crosslinkers. While it is stated that they react with purines, the potential for non-specific or biologically irrelevant crosslinks (e.g., due to the long spacer arms of DEB/NM, or the reactivity of formaldehyde) is a major concern. The authors need to provide more evidence that the identified crosslinks represent genuine, direct contacts within native complexes, rather than artifactual or "crowding" effects. The analysis of the PNPase structure, where chemical crosslinks were not found in the active site cavity, is interesting but raises questions about the accessibility and specificity of the crosslinkers.
    - **Why it matters** The biological interpretation of the data, particularly the claim that crosslinks are found at functionally relevant sites, depends on the specificity of the crosslinking reaction. If the chemical crosslinkers are promiscuous, the conclusions about RNA-binding properties of various proteins would be weakened.
    - **Resolution test** Include control experiments demonstrating the specificity of crosslinking, such as competition experiments with free nucleotides, or a more detailed analysis of the structural context of crosslinked residues. Discuss the potential for non-specific crosslinking and provide evidence that the observed crosslinks are not simply due to protein abundance or random proximity. A more detailed comparison of the crosslinked residues with known or predicted RNA-binding domains would be helpful.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Statistical rigor of enrichment analyses
    - **Claim pointer** The claim that crosslinked sites are enriched in RNA-binding residues, disordered regions, and conserved residues, and that this enrichment is independent of protein abundance.
    - **Evidence pointer** Results section "Properties of crosslinked E. coli proteins"; Figure 5; Supplementary Figures S10, S11, S14; Methods section "Statistical testing for residue feature enrichment".
    - **Concern** The statistical methods for the enrichment analysis are described, but the results are only summarized in the text. The authors mention a "propensity score-based covariate matching" to correct for abundance bias, but the effectiveness of this correction is not fully demonstrated. The choice of background (e.g., "all MS-detectable peptides") and the potential for confounding factors (e.g., peptide detectability, protein size) need to be more thoroughly discussed. The claim that enrichment is "beyond abundance bias" is crucial and needs to be supported with clear data showing the comparison between corrected and uncorrected analyses.
    - **Why it matters** The conclusion that the crosslinking data provides insights into the general principles of RNA-protein interactions depends on the robustness of the statistical analysis. If the enrichment is an artifact of abundance or other biases, the biological conclusions would be invalid.
    - **Resolution test** Provide a more detailed description of the statistical analysis, including the number of samples, the distribution of the test statistics, and the effect of the abundance correction on the enrichment results. Show the enrichment analysis with and without the abundance correction to demonstrate its impact. Consider using additional statistical methods (e.g., permutation tests) to validate the findings.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Interpretation of AlphaFold3 modelling
    - **Claim pointer** The claim that AlphaFold3 models show "unprecedented accuracy" and are validated by the crosslinking data.
    - **Evidence pointer** Results section "UV combined with chemical crosslinking provides spatial constraints in structural modelling of protein-RNA complexes"; Methods section "Generation of spDnmt2-tRNAAsp models with AlphaFold3".
    - **Concern** The comparison between the AlphaFold3 model and the previous model is interesting, but the claim of "unprecedented accuracy" is too strong and not fully supported. The analysis is based on a single protein-RNA complex (Dnmt2-tRNAAsp). The criteria for "compatibility" with crosslinking data (distance thresholds) are described, but the scoring and ranking of models are not fully transparent. The authors should be more cautious in their claims and acknowledge the limitations of using a single example.
    - **Why it matters** Overstating the accuracy of AlphaFold3 could mislead readers and detract from the more solid contributions of the paper, which are the experimental method and the NuXL software.
    - **Resolution test** Soften the claim of "unprecedented accuracy" and provide a more nuanced discussion of the results. Acknowledge that this is a single case study and that more extensive benchmarking is needed. Provide a clearer description of the model scoring and ranking process.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity and presentation
    - **Affected element** Abstract and Introduction
    - **Evidence pointer** Abstract; Introduction
    - **Issue** The abstract is dense and could be more accessible to a broader audience. The introduction could better set the stage for why chemical crosslinking is needed, beyond the general statement that it "complements" UV.
    - **Required correction** Consider revising the abstract to more clearly state the problem, the novel solution, and the key findings. In the introduction, briefly discuss the specific limitations of UV crosslinking (e.g., bias towards certain amino acids, low efficiency for some complexes) that motivate the use of chemical crosslinkers.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Data presentation
    - **Affected element** Results section "NuXL facilitates identification of UV and chemical crosslinking sites in E. coli"
    - **Evidence pointer** Figure 4
    - **Issue** The description of the E. coli dataset is impressive but could be more clearly organized. The relationship between the different panels of Figure 4 (e.g., Venn diagrams, structural mapping) could be better explained in the text.
    - **Required correction** Provide a more structured summary of the E. coli results, perhaps with a table listing the number of crosslinks per category (RNA vs. DNA, UV vs. chemical) and the overlap between methods. Ensure the text guides the reader through the key messages of each figure panel.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Methodology
    - **Affected element** Methods section "XL-MS data analysis using NuXL"
    - **Evidence pointer** Methods; Supplementary Methods
    - **Issue** The description of the NuXL algorithm is high-level. While the Supplementary Methods are referenced, the main text should provide enough detail for a reader to understand the key steps without having to consult the supplement.
    - **Required correction** Briefly describe the main steps of the NuXL algorithm in the main text, including the scoring function, the FDR control method, and the localization score. This will make the method section more self-contained.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Discussion
    - **Affected element** Discussion
    - **Issue** The discussion is somewhat broad and could be more focused on the specific implications of the findings. The comparison with other studies is useful but could be more critical.
    - **Required correction** Consider structuring the discussion around the three main contributions (chemical crosslinking, NuXL, and the E. coli dataset) and their implications for the field. Discuss the limitations of the current study more explicitly and outline future directions.

- **Technical failings that need to be addressed before the case is established**
    - R1-M1 (NuXL validation) and R1-M2 (specificity of chemical crosslinking) are the most critical technical issues. Without a robust validation of NuXL and a clear demonstration of the specificity of the chemical crosslinkers, the central claims of the manuscript are not fully established. The statistical rigor of the enrichment analysis (R1-M3) also needs to be strengthened.

- **Assessment against Nature-style criteria**
    - **Originality** High. The combination of chemical crosslinkers with a dedicated search engine for nucleic acid-protein interactions is a novel and logical extension of existing UV-based methods. The large-scale in vivo dataset is also a significant original contribution.
    - **Scientific importance** High. The work addresses a key challenge in the field of RNA/DNA-protein interactomics and provides a new tool and resource that will be of broad use. The potential to expand the scope of crosslinkable interactions is important.
    - **Interdisciplinary readership** Moderate to High. The topic is of primary interest to molecular biologists, biochemists, and proteomics specialists. The methodological focus may limit its appeal to a wider audience, but the biological findings (e.g., on metabolic enzymes) could attract broader interest.
    - **Technical soundness** Currently Moderate. The overall approach is sound, but the lack of detailed validation for NuXL and the insufficient discussion of crosslinking specificity are significant weaknesses that need to be addressed.
    - **Readability for nonspecialists** Moderate. The manuscript is well-written but uses specialized terminology that may be challenging for non-experts. The abstract and introduction could be made more accessible.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a potentially important methodological advance and a valuable dataset. However, the central claims regarding the performance of NuXL and the specificity of chemical crosslinking need to be more rigorously supported. The statistical analyses also need to be more transparent. If these concerns are adequately addressed in a revised manuscript, it would be a strong candidate for publication.