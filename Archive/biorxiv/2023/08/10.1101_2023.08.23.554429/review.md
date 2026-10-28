## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods, acknowledgements, footnotes)
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text. No external data or unpublished materials were consulted.
- **Shared manuscript claim summary** The authors investigate structural and functional differences between the transcription factors MAFA and MAFB, focusing on how mutations in conserved DNA-contact residues affect Insulin enhancer-driven activity. They use AlphaFold 2 to predict structural differences in disordered regions and test functional consequences via reporter assays and chimeric proteins, concluding that unique C-terminal structural features influence cooperative activity with other islet-enriched transcription factors.
- **Visible evidence base** Abstract, Introduction, Results sections 1-4, Discussion, Materials and Methods (AlphaFold 2 modeling, DNA constructs, cell culture and assays), Figure legends referenced (Figures 1-5, Supplemental Figures 1-6), Acknowledgements, Footnotes
- **Missing materials affecting confidence** Actual figures and supplemental figures (images, data plots, gels, EMSA results) are not provided. Statistical details (error bars, n numbers, significance tests) are not described in the text. Full methods for mutagenesis, cloning, and reporter assays are only partially described. No raw data or quantitative values for reporter activity, EMSA, or AlphaFold 2 distance measurements are given.

## Reviewer
- **Overall assessment** The manuscript addresses an important question in islet biology: how two closely related transcription factors, MAFA and MAFB, achieve distinct functional outcomes despite high sequence similarity. The combination of mutagenesis, AlphaFold 2 structural prediction, and functional reporter assays is a reasonable approach. However, the evidence presented is largely qualitative and descriptive. The central claims about structural differences driving functional divergence rest heavily on AlphaFold 2 predictions that are not experimentally validated (e.g., by mutagenesis of predicted structural elements or biophysical characterization). The chimeric protein experiments are informative but limited in scope, and the mechanistic link between predicted structural features and observed functional differences remains speculative. The manuscript would benefit from more quantitative data, additional controls, and direct testing of the proposed structural determinants.
- **Who would be interested in the results, and why** Researchers studying transcription factor structure-function relationships, pancreatic islet development and function, insulin gene regulation, and the molecular basis of monogenic diabetes. The use of AlphaFold 2 to generate hypotheses about disordered regions may also interest computational biologists and structural biologists. Clinically oriented readers may be interested in the pathogenic MAFA S64F and MAFB S70A variants.
- **Major strengths** 1. The study addresses a significant biological question with potential clinical relevance. 2. The combination of structural prediction and functional assays is a modern and potentially powerful approach. 3. The identification of a differential effect of the R272A/R256A mutation between MAFA and MAFB is a clear and interesting finding. 4. The use of chimeric proteins to map functional domains is a logical strategy. 5. The manuscript is generally clearly written and logically organized.
- **Major Concerns** 1. The AlphaFold 2 predictions are presented as central evidence but are not experimentally validated. 2. The functional assays rely on a single reporter system (HeLa cells, -238 WT Insulin luciferase) without validation in a more physiologically relevant context. 3. The quantitative data (reporter activity, EMSA) are not shown in the text, making it impossible to assess the magnitude of effects or statistical significance. 4. The mechanistic interpretation of chimeric protein results is underdeveloped; the authors do not identify which specific residues or structural features are responsible for the observed functional differences. 5. The claim that "structural differences impart unique functional properties" is not directly tested; the authors do not show that altering the predicted structural features changes function in a predictable way.
- **Minor Comments** 1. The abstract states that "regions outside of the contact areas also contributed to activity," but this is only demonstrated for one mutant (R272A). 2. The description of AlphaFold 2 modeling is brief; more details on model confidence (e.g., pLDDT scores) would strengthen the analysis. 3. The choice of phosphomimetics (D/E substitutions) is not justified in detail. 4. The Discussion speculates about in vivo relevance without direct experimental support. 5. The manuscript would benefit from a figure showing the AlphaFold 2 predicted structures with the key regions highlighted.
- **Technical failings that need to be addressed before the case is established** 1. Lack of quantitative data for reporter assays and EMSA (no values, error bars, or statistics). 2. No experimental validation of AlphaFold 2 predicted structural differences (e.g., by mutagenesis of predicted structural elements or by biophysical methods). 3. The chimeric protein experiments do not include reciprocal controls (e.g., MAFA with MAFB C-terminus and vice versa) in a systematic way. 4. The functional significance of the predicted C-terminal differences is not directly tested; the authors do not show that swapping the C-terminal regions between MAFA and MAFB transfers the functional phenotype.
- **Assessment against Nature-style criteria** Originality: The study is original in its application of AlphaFold 2 to this specific question, but the overall concept of structure-function analysis of transcription factors is not novel. Scientific importance: The question of how MAFA and MAFB achieve distinct functions is important for islet biology and diabetes, but the current evidence does not fully establish the proposed mechanism. Interdisciplinary readership: The topic may appeal to molecular biologists, structural biologists, and diabetes researchers, but the lack of quantitative data and mechanistic depth may limit broader appeal. Technical soundness: The methods are generally sound but the lack of quantitative data and validation of structural predictions weakens the technical case. Readability for nonspecialists: The manuscript is readable but assumes familiarity with transcription factor biology and structural prediction methods.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents interesting observations and a plausible hypothesis, but the evidence is insufficient to support the central claims. Major revisions with additional quantitative data, experimental validation of structural predictions, and more direct tests of the proposed mechanism would be required.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that "structural differences between MAFA and MAFB impart their unique functional properties under physiologic and disease conditions" (Introduction) and that "unique C-terminal region structural differences predicted by AlphaFold 2" influence cooperative activity (Abstract).
- **Evidence pointer** Results section 4, Figure 5, Supplemental Figure 5
- **Concern** The central claim that predicted structural differences in the C-terminal region are functionally significant is not directly tested. The chimeric protein experiments show that swapping N- and C-terminal regions affects activity, but the authors do not identify which specific structural features are responsible. The AlphaFold 2 predictions are not validated experimentally, and no mutagenesis of the predicted structural elements is performed to confirm their functional importance.
- **Why it matters** Without direct testing of the predicted structural determinants, the causal link between structure and function remains speculative. The manuscript would be substantially strengthened by experiments that alter the predicted structural features (e.g., by targeted mutagenesis) and show a corresponding change in function.
- **Resolution test** The authors should perform mutagenesis of the specific residues or regions predicted by AlphaFold 2 to be structurally unique in MAFA versus MAFB, and test whether these mutations alter the functional interactions with PDX1, ISL1, or GLIS3. Alternatively, they could swap the specific predicted structural elements between MAFA and MAFB and show that the functional phenotype transfers.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative data
- **Claim pointer** The authors state that "MAFA R272A had WT-like activity whereas the comparable MAFB R256A mutant was inactive" (Results section 1) and describe various differences in cooperative activity (Results sections 3-4).
- **Evidence pointer** Results sections 1, 3, 4; Figures 2, 4, 5
- **Concern** The manuscript does not provide any quantitative data for the reporter assays or EMSA experiments. No values, error bars, or statistical tests are reported. It is impossible to assess the magnitude of the effects described or whether the differences are statistically significant.
- **Why it matters** Quantitative data are essential for evaluating the robustness and significance of the findings. Without them, the reader cannot determine whether the observed differences are meaningful or within experimental noise.
- **Resolution test** The authors should provide quantitative data for all reporter assays (e.g., mean ± SEM, n values, statistical tests) and for EMSA experiments (e.g., densitometry or binding affinity measurements). This would allow the reader to assess the strength of the evidence.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors use AlphaFold 2 to predict structural differences between MAFA and MAFB, including in the C-terminal region, and state that these differences are "functionally significant" (Abstract, Discussion).
- **Evidence pointer** Results section 2, Figure 3, Supplemental Figure 3
- **Concern** The AlphaFold 2 predictions are presented as a key finding, but they are not validated by any experimental method. The authors do not provide confidence scores (e.g., pLDDT) or compare the predictions to any experimental structural data. The functional relevance of the predicted differences is inferred but not directly demonstrated.
- **Why it matters** AlphaFold 2 predictions, especially for disordered regions, can be unreliable. Without experimental validation, the structural claims remain speculative and cannot support the functional conclusions drawn.
- **Resolution test** The authors should provide pLDDT scores or other confidence metrics for the AlphaFold 2 models. They could also validate the predictions using biophysical methods (e.g., circular dichroism, NMR, or small-angle X-ray scattering) or by testing the functional consequences of mutations in the predicted structural elements.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Physiological relevance
- **Claim pointer** The authors state that their results "have revealed features of these closely related proteins that are functionally significant in islet biology" (Abstract) and discuss implications for diabetes (Discussion).
- **Evidence pointer** Results sections 3-4, Discussion
- **Concern** All functional assays were performed in HeLa cells using an overexpressed reporter system. The physiological relevance of these findings to pancreatic islet cells is not demonstrated. The authors do not test the effects of the mutations or chimeras in islet cell lines, primary cells, or in vivo models.
- **Why it matters** Transcription factor function is highly context-dependent. Results obtained in HeLa cells may not reflect the behavior of MAFA and MAFB in pancreatic islet cells, where chromatin context, cofactor availability, and post-translational modifications differ.
- **Resolution test** The authors should validate key findings in a more physiologically relevant system, such as a β-cell line (e.g., INS-1, MIN6) or human stem cell-derived β-like cells. Alternatively, they could use primary islet cells or in vivo models to confirm the functional significance of the identified structural features.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that "regions outside of the contact areas also contributed to activity," but this is only demonstrated for one mutant (R272A). This overgeneralizes the finding.
- **Required correction** The abstract should be more precise, e.g., "a region outside of the contact area contributed to activity in the case of MAFA R272A."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Materials and Methods, AlphaFold 2 modeling
- **Evidence pointer** Materials and Methods, "Modeling by AlphaFold 2"
- **Issue** The description of the AlphaFold 2 modeling is brief. The authors do not specify which version of AlphaFold 2 was used, how model confidence was assessed, or how the "highest predicted interface" was determined.
- **Required correction** Provide more details on the modeling parameters, confidence metrics (e.g., pLDDT, PAE), and the criteria for selecting the representative models shown.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results section 4, Figure 5
- **Evidence pointer** Results section 4, Figure 5
- **Issue** The chimeric protein experiments are described, but the interpretation is not fully developed. The authors do not explain why the N-terminal region of MAFA is sufficient to abolish ISL1 stimulation in the MAFA/B chimera, or why the C-terminal region of MAFB is necessary for PDX1 stimulation.
- **Required correction** Provide a more detailed interpretation of the chimeric results, including possible mechanisms (e.g., direct protein-protein interactions, conformational changes, or altered post-translational modifications).

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The Discussion does not adequately contextualize the findings with respect to previous structural and functional studies of MAFA and MAFB. For example, the authors do not discuss how their AlphaFold 2 predictions compare to the existing X-ray crystal structures of the basic-leucine-zipper domains.
- **Required correction** Add a paragraph comparing the AlphaFold 2 predictions to existing experimental structures and discussing how the new predictions extend or challenge previous understanding.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figures
- **Evidence pointer** Figures 1-5, Supplemental Figures 1-6
- **Issue** The figure legends are not provided in the text, so it is unclear what exactly is shown in each panel. The text references specific panels (e.g., Figure 2A, Figure 5B), but without legends, the reader cannot fully interpret the data.
- **Required correction** Include figure legends in the manuscript text or ensure that the figures are self-explanatory with clear labels and annotations.

## Risk / unsupported claims
- The claim that "structural differences between MAFA and MAFB impart their unique functional properties under physiologic and disease conditions" is not directly supported by the data, as the functional assays were performed in HeLa cells and the structural predictions were not experimentally validated.
- The claim that "unique C-terminal region structural differences predicted by AlphaFold 2" are responsible for the observed functional differences is speculative, as the chimeric experiments do not isolate the specific structural features responsible.
- The statement that "MAFA R272A had WT-like activity" is not supported by quantitative data, so the magnitude of the effect and its statistical significance are unknown.
- The claim that "MAFB, but not MAFA, provided additional enhanced activation in the presence of PDX1 and ISL1" is based on a single reporter assay in HeLa cells and may not be generalizable to other cell types or conditions.
- The relevance of the findings to diabetes and islet biology is inferred but not directly tested, as no experiments were performed in islet cells or in vivo models.