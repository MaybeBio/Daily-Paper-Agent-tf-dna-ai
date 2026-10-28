## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The manuscript identifies TagR as a novel MarR family transcriptional regulator encoded within the til pathogenicity island of toxigenic Klebsiella oxytoca. The authors report that TagR directly represses the NRPS operon responsible for tilimycin and tilivalline biosynthesis, based on structural predictions, molecular dynamics simulations, biochemical dimerization assays, gene expression analyses, and cytotoxicity experiments.
- **Visible evidence base** Full text including Introduction, Materials and Methods, Results, Discussion, and Acknowledgments. Figures and tables are referenced but not provided in the submitted material.
- **Missing materials affecting confidence** Figures 1-9 and Tables 1-2 are referenced but not included. Raw data, statistical outputs, and experimental replicates are not available. Primer sequences and strain construction details are partially described but not fully verifiable.

## Reviewer
- **Overall assessment** The manuscript addresses an important and timely question in the field of K. oxytoca pathogenesis, namely the regulation of enterotoxin biosynthesis. The identification of a MarR family regulator directly controlling the NRPS operon is a potentially significant finding. However, the evidence presented has several critical gaps. The most substantial concern is the lack of direct biochemical evidence for TagR-DNA binding, as the EMSA experiments are described but the data are not shown. Additionally, the claim of "direct repression" is not fully supported without demonstrating that TagR binding to the identified region is necessary and sufficient for transcriptional repression. The structural modeling and MD simulations are supportive but not definitive. The gene expression data showing derepression in the ΔtagR mutant are compelling, but the magnitude of the effect (hundreds-fold) warrants additional validation. The cytotoxicity data are consistent with the model but rely on indirect measurements. Overall, the study is well-conceived and the findings are likely of interest to the microbial pathogenesis community, but the current evidence does not fully establish the mechanistic claims.

- **Who would be interested in the results, and why** Researchers studying K. oxytoca pathogenesis, particularly those focused on the regulation of enterotoxin production and the til pathogenicity island. The broader community studying MarR family transcriptional regulators and their roles in virulence gene regulation in Gram-negative pathogens would also find this work relevant. Additionally, investigators interested in the molecular mechanisms of antibiotic-associated hemorrhagic colitis would benefit from understanding how toxin production is controlled.

- **Major strengths** The study addresses a previously uncharacterized aspect of K. oxytoca virulence regulation. The combination of computational structural prediction, molecular dynamics simulations, biochemical assays, genetic approaches, and functional cytotoxicity assays provides a multi-pronged approach. The identification of a local regulator within the til pathogenicity island adds to the understanding of the regulatory network controlling enterotoxin production. The gene expression data showing strong derepression in the ΔtagR mutant are clear and compelling. The complementation experiments provide genetic evidence for specificity.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "EMSAs provided direct experimental evidence that TagR specifically recognizes the upstream regulatory region of the NRPS operon."
- **Evidence pointer** Results section, "Electrophoretic mobility shift assays (EMSAs)" subsection; Figure 6
- **Concern** The manuscript claims direct DNA-binding evidence via EMSA, but the actual gel images are not provided in the submitted material. The description of the experiments is insufficient to evaluate the quality of the data, including whether appropriate controls were included, the purity of the protein, and the specificity of the binding. The negative control using pehX is mentioned, but no data are shown.
- **Why it matters** The claim that TagR is a "direct" repressor hinges on demonstrating physical interaction between TagR and the NRPS regulatory region. Without visible EMSA data, this central claim cannot be verified. Indirect effects on gene expression could also explain the transcriptional changes observed in the ΔtagR mutant.
- **Resolution test** Provide the EMSA gel images with all experimental conditions clearly labeled, including protein concentrations, DNA probe concentrations, and appropriate controls. Include a competition assay with unlabeled specific and non-specific DNA to demonstrate binding specificity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "A combined analysis of the 5′ and 3′ deletion experiments localized the TagR-binding region to a 78-nucleotide segment spanning nucleotides 235-312 of the regulatory fragment."
- **Evidence pointer** Results section, "Identification of the TagR DNA-binding site within the npsA regulatory region" subsection; Figure 7
- **Concern** The deletion mapping experiments are described, but the actual EMSA data for the deletion fragments are not shown. The boundaries of the minimal binding region are defined by the absence of binding to certain fragments, but without seeing the data, it is impossible to assess whether the conclusions are justified. The putative inverted repeat motif is identified by sequence inspection, but no mutational analysis is presented to confirm its functional relevance.
- **Why it matters** The identification of the minimal binding region and the putative recognition motif is critical for understanding the molecular mechanism of TagR-mediated repression. Without visible data and functional validation, the proposed binding site remains speculative.
- **Resolution test** Provide the EMSA data for all deletion fragments. Perform site-directed mutagenesis of the proposed inverted repeat motif and test the effect on TagR binding in EMSA experiments. This would confirm the functional importance of the identified sequence.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "The predicted protein displays the characteristic α-helical and β-sheet architecture conserved among MarR family regulators, whereas the stable inter-chain interaction energy and low RMSD fluctuations observed during molecular dynamics simulations indicate that the TagR homodimer adopts a structurally stable conformation compatible with DNA binding."
- **Evidence pointer** Results section, "Structural and stability prediction of the putative TagR homodimer" subsection; Figure 1
- **Concern** The structural model is generated using AlphaFold 3 and refined with a 40 ns MD simulation. While this is a reasonable approach, the manuscript does not provide details on the quality of the model, such as pLDDT scores per residue, Ramachandran plot statistics, or comparison with known MarR family structures. The MD simulation length is relatively short for drawing strong conclusions about conformational stability. The functional significance of the predicted structure is not experimentally validated.
- **Why it matters** The structural predictions are used to support the classification of TagR as a MarR family regulator. While the sequence homology and conserved motif are suggestive, the structural evidence is computational and should be treated as supportive rather than definitive. Over-interpretation of computational predictions can lead to incorrect conclusions.
- **Resolution test** Provide model quality metrics and a more detailed analysis of the MD simulation, including convergence checks. If possible, compare the predicted structure with experimentally determined structures of related MarR family regulators. Consider experimental validation of the dimer interface, such as through cross-linking or size-exclusion chromatography.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Evidence sufficiency
- **Claim pointer** "Loss of TagR increases cytotoxicity in epithelial cells" and "deletion of tagR increases the production of cytotoxic factors associated with the NRPS operon."
- **Evidence pointer** Results section, "Loss of TagR increases cytotoxicity in epithelial cells" subsection; Figure 9
- **Concern** The cytotoxicity data show that ΔtagR supernatant is more cytotoxic than wild-type, and complementation restores the phenotype. However, the manuscript does not directly measure toxin production (e.g., by LC-MS or ELISA). The claim that increased cytotoxicity is due to increased toxin production is inferred from the gene expression data, but this link is not directly demonstrated. The assay uses HeLa cells, and the specificity of the cytotoxic effect to TM/TV is supported by the ΔnpsA control, but the manuscript acknowledges that TM and TV were not directly quantified.
- **Why it matters** The functional significance of TagR-mediated repression is tied to its effect on toxin production and cytotoxicity. Without direct toxin quantification, the connection between transcriptional derepression and increased toxin output remains correlative.
- **Resolution test** Quantify TM and TV levels in culture supernatants from wild-type, ΔtagR, and complemented strains using LC-MS or a similar method. This would provide direct evidence that the increased cytotoxicity is due to increased toxin production.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "The results indicate that TagR acts as a negative regulator by repressing genes involved in TM/TV biosynthesis within the NRPS operon."
- **Evidence pointer** Results section, "TagR functions as a repressor of the NRPS operon" subsection; Figure 5
- **Concern** The RT-qPCR data show a substantial increase in npsA, thdA, and npsB transcript levels in the ΔtagR mutant. However, the manuscript does not report the statistical analysis in detail, including the number of biological replicates, the specific statistical test used, or the variance within groups. The fold-changes are reported as approximately 473-fold, 467-fold, and 436-fold, which are very large and warrant careful validation. The manuscript also does not report whether the expression of other genes in the til pathogenicity island was affected.
- **Why it matters** The magnitude of the reported fold-changes is unusual and could be influenced by technical artifacts, such as differences in RNA quality or PCR efficiency. A rigorous statistical analysis is essential to support the claim that TagR is a potent repressor of the NRPS operon.
- **Resolution test** Provide detailed statistical analysis, including the number of biological replicates, the statistical test used, and confidence intervals. Consider validating the fold-changes using an independent method, such as Northern blotting or RNA-seq.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction
- **Evidence pointer** Introduction section, paragraph 1
- **Issue** The sentence "Recent studies have focused on identifying the molecular determinants of K. oxytoca virulence, particularly those involved in enterotoxin biosynthesis and regulation (3-8)" is vague and does not provide specific context for the reader.
- **Required correction** Provide a brief summary of what is known about the regulation of enterotoxin biosynthesis in K. oxytoca, including the specific regulators that have been identified and their mechanisms of action.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Materials and Methods, "Bacterial strains and growth conditions"
- **Evidence pointer** Materials and Methods section, "Bacterial strains and growth conditions" subsection; Table 1
- **Issue** The manuscript states that "Table 1 provides a comprehensive list of all bacterial strains and plasmids," but the table is not provided. The description of the growth conditions is brief.
- **Required correction** Provide Table 1 and include more details on the growth conditions, such as the specific antibiotics used for selection and the growth phase at which cells were harvested.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Materials and Methods, "Generation of the tagR isogenic mutant strain"
- **Evidence pointer** Materials and Methods section, "Generation of the tagR isogenic mutant strain" subsection; Table 2
- **Issue** The manuscript describes the generation of the ΔtagR mutant using the λ Red recombination system but does not provide the primer sequences used for the deletion. The details of the deletion (e.g., the extent of the deletion) are not specified.
- **Required correction** Provide the primer sequences in Table 2 and describe the exact region of the tagR gene that was deleted. Include details on how the deletion was confirmed (e.g., by sequencing).

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "Structural and stability prediction of the putative TagR homodimer"
- **Evidence pointer** Results section, "Structural and stability prediction of the putative TagR homodimer" subsection; Figure 1
- **Issue** The description of the structural model is brief and does not provide sufficient detail on the model quality or the specific features of the predicted structure.
- **Required correction** Provide more details on the model, such as the pLDDT scores, the confidence of the predicted dimer interface, and a comparison with known MarR family structures. Consider including a figure showing the predicted structure with key features labeled.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Materials and Methods, "Electrophoretic mobility shift assays (EMSAs)"
- **Evidence pointer** Materials and Methods section, "Electrophoretic mobility shift assays (EMSAs)" subsection
- **Issue** The description of the EMSA experiments is brief and does not provide sufficient detail on the DNA probes used, the binding conditions, or the concentrations of protein and DNA.
- **Required correction** Provide more details on the EMSA protocol, including the sequences of the DNA probes, the binding buffer composition, the incubation time and temperature, and the concentrations of protein and DNA used.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion section, paragraph 5
- **Issue** The sentence "These results support a regulatory model in which NRPS operon expression is governed by multiple transcriptional regulators that integrate nutritional, physiological, environmental, and interspecies signaling cues" is somewhat speculative and not directly supported by the data presented.
- **Required correction** Soften the language to indicate that this is a proposed model that requires further testing, and provide specific examples of how the identified regulators might integrate these signals.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Materials and Methods, "Lactate dehydrogenase (LDH) cytotoxicity assays"
- **Evidence pointer** Materials and Methods section, "Lactate dehydrogenase (LDH) cytotoxicity assays" subsection
- **Issue** The description of the LDH assay is brief and does not provide details on the multiplicity of infection (MOI) used, the duration of exposure, or the number of replicates.
- **Required correction** Provide more details on the LDH assay protocol, including the MOI, the incubation time, and the number of biological and technical replicates.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "Loss of TagR increases cytotoxicity in epithelial cells"
- **Evidence pointer** Results section, "Loss of TagR increases cytotoxicity in epithelial cells" subsection; Figure 9
- **Issue** The description of the cytotoxicity data is brief and does not provide the actual values or the statistical analysis. The figure is not provided.
- **Required correction** Provide the actual cytotoxicity values and the statistical analysis in the text or in the figure legend.

## Risk / unsupported claims
- The claim that TagR "directly" represses the NRPS operon is not fully supported without visible EMSA data and functional validation of the binding site.
- The claim that the predicted structural model is "compatible with DNA binding" is based on computational predictions and requires experimental validation.
- The claim that increased cytotoxicity in the ΔtagR mutant is due to increased toxin production is inferred from gene expression data and requires direct toxin quantification.
- The claim that TagR is a "newly identified member" of the MarR family is supported by sequence analysis, but the functional significance of this classification is not fully established.
- The claim that TagR is the "first MarR family transcriptional regulator demonstrated to directly repress the NRPS operon" in K. oxytoca is not verifiable without a comprehensive literature review.
- The manuscript does not provide evidence for the specificity of TagR binding to the NRPS regulatory region, as no competition experiments or mutational analysis are shown.
- The manuscript does not address whether TagR regulates other genes beyond the NRPS operon, leaving the scope of its regulon undefined.

## Assessment against Nature-style criteria
- **Originality** The identification of a MarR family regulator controlling the NRPS operon in K. oxytoca is a novel finding. While MarR regulators are well-studied in other bacteria, their role in K. oxytoca enterotoxin regulation has not been previously described. The study is original in its specific focus.
- **Scientific importance** The findings have potential importance for understanding the regulation of virulence in K. oxytoca, an emerging pathogen. The identification of a dedicated local repressor adds to the understanding of the regulatory network controlling enterotoxin production. However, the broader significance is somewhat limited by the lack of mechanistic depth and the absence of in vivo validation.
- **Interdisciplinary readership** The study is primarily of interest to microbiologists and microbial pathologists. The use of structural modeling and MD simulations may appeal to computational biologists, but the overall scope is narrow. The clinical relevance to antibiotic-associated hemorrhagic colitis is mentioned but not explored in depth.
- **Technical soundness** The experimental design is generally sound, but the lack of visible data for key experiments (EMSA, deletion mapping) and the absence of direct toxin quantification weaken the technical rigor. The statistical analysis is not reported in sufficient detail. The computational predictions are not experimentally validated.
- **Readability for nonspecialists** The manuscript is written in a clear and accessible style. The introduction provides sufficient background for readers unfamiliar with K. oxytoca or MarR regulators. However, the methods section is dense and may be challenging for nonspecialists.

## Recommendation posture
Supportive if technical concerns are resolved. The study addresses a relevant and timely question, and the findings are potentially significant. However, the current evidence does not fully establish the central claim of direct repression. The authors must provide the missing data, particularly the EMSA results and the deletion mapping data, and directly quantify toxin production to strengthen the link between transcriptional derepression and increased cytotoxicity. The statistical analysis should be reported in detail. With these revisions, the manuscript could make a valuable contribution to the field.