## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Results and Discussion, Materials and Methods, Conclusions)
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims relative to presented evidence, and alignment with Nature-style criteria
- **Shared manuscript claim summary** The authors report a structure-based virtual screening workflow targeting the ERCC1–XPF protein-protein interaction, identifying 106 putative inhibitors from NCI, ChemBridge, and DrugBank databases. Of 102 compounds experimentally tested in H1299 NSCLC cells, 22 were reported to enhance cisplatin-induced cytotoxicity. The authors propose Phe293 of ERCC1 as a key binding site and Lys860 of XPF as a docking anchor.
- **Visible evidence base** Computational docking validation against 84 ChEMML compounds, virtual screening of 1,292,927 compounds, qRT-PCR expression profiling of six NSCLC cell lines, cisplatin dose-response assays (CV and MTS), combination screening at 50 µM and 10 µM, interaction analysis of selected compounds
- **Missing materials affecting confidence** Compound identities and chemical structures of the 22 "best" inhibitors (only in Supplementary Figure S1, not provided); dose-response data for the 22 selected compounds; statistical details for combination index or synergy analysis; raw data for Figure 10 and Figure 12; docking scores for individual selected compounds; positive/negative control data for the combination assays; information on whether the 22 compounds were tested at multiple concentrations in the confirmatory step

## Reviewer

- **Overall assessment** This manuscript presents a systematic computational-experimental pipeline for identifying putative ERCC1-XPF interaction inhibitors. The computational workflow is described in reasonable detail and the experimental design is logical. However, the central claim that 22 compounds "enhance cisplatin-induced cytotoxicity" rests on a single-concentration screening assay with a modest threshold (15% enhancement), and the manuscript lacks dose-response validation, synergy analysis, and mechanistic evidence that the compounds act through ERCC1-XPF inhibition rather than off-target effects. The work is a useful screening study but does not yet establish a validated set of ERCC1-XPF inhibitors.

- **Who would be interested in the results, and why** Researchers in cancer pharmacology, DNA repair-targeted therapy, and structure-based drug design would find this work relevant. The identification of new chemotypes for ERCC1-XPF disruption could inform medicinal chemistry programs aimed at sensitizing tumors to platinum-based chemotherapy. The computational protocol may also be of interest to computational chemists working on protein-protein interaction targets.

- **Major strengths** The study addresses a clinically relevant target with a clear therapeutic rationale. The computational workflow is well-structured, with validation against known actives and attention to physicochemical properties. The experimental design includes a rational cell line selection step based on ERCC1 expression. The decision tree for compound prioritization is transparent and systematic.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for central claim
- **Claim pointer** "22 compounds emerged as promising enhancers of cisplatin efficacy" and "22 compounds that demonstrated positive results in enhancing cisplatin-induced cytotoxicity"
- **Evidence pointer** Section 2.3.1, Figure 10, Figure 11
- **Concern** The identification of the 22 "best" inhibitors is based on a single screening concentration (50 µM) with a threshold of 15% enhancement of cisplatin cytotoxicity. No dose-response data are presented for these compounds, and no combination index or isobologram analysis is provided to establish whether the effect is synergistic, additive, or merely additive toxicity. The subtraction method used to calculate "inhibitor effect" is not a validated approach for assessing synergy.
- **Why it matters** The central claim of the manuscript is that these compounds enhance cisplatin efficacy. Without dose-response relationships and formal synergy analysis, the claim that these are genuine enhancers of cisplatin activity is not established. The observed effects could be due to simple additive cytotoxicity or off-target effects unrelated to ERCC1-XPF inhibition.
- **Resolution test** Provide dose-response curves for the 22 compounds alone and in combination with cisplatin at multiple concentrations, with formal combination index analysis (e.g., Chou-Talalay method). Demonstrate that the combination effect exceeds additivity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Target engagement and mechanism of action
- **Claim pointer** "Novel ERCC1-XPF Complex Inhibitors" and "potential inhibitors" with implied mechanism of disrupting ERCC1-XPF interaction
- **Evidence pointer** Section 2.4, Figure 13, Figure 14, Figure 15
- **Concern** No experimental evidence is provided that the 22 compounds actually bind to ERCC1-XPF or disrupt the protein-protein interaction. The interaction analysis is purely computational (docking poses and PLIP analysis). No biophysical assays (e.g., SPR, ITC, MST) or cellular assays demonstrating target engagement (e.g., NER activity assays, ERCC1-XPF complex formation assays) are presented.
- **Why it matters** The title and framing of the manuscript claim these are ERCC1-XPF complex inhibitors. Without experimental validation of target engagement, the compounds could be acting through any number of mechanisms to enhance cisplatin cytotoxicity. The computational predictions are hypothesis-generating, not confirmatory.
- **Resolution test** Perform biophysical binding assays (SPR, ITC, or MST) for representative compounds against the ERCC1-XPF complex, and/or cellular assays demonstrating inhibition of NER activity or disruption of ERCC1-XPF interaction.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Selectivity and specificity
- **Claim pointer** "more than one hundred potential inhibitors" and "22 compounds emerged as promising enhancers"
- **Evidence pointer** Section 2.1.3, Section 2.3.1
- **Concern** No selectivity data are presented. The compounds were selected based on docking scores and in vitro cytotoxicity enhancement, but there is no assessment of whether these compounds are selective for ERCC1-XPF over other protein-protein interaction targets or DNA repair proteins. Given that many of the compounds are known drugs (e.g., terfenadine, bisoprolol, betaxolol), their primary pharmacological targets are well known and unrelated to ERCC1-XPF.
- **Why it matters** For a compound to be useful as a research tool or therapeutic lead, selectivity is essential. The inclusion of known drugs with well-characterized primary targets raises questions about whether the observed effects are due to ERCC1-XPF inhibition or to their known pharmacological activities.
- **Resolution test** Provide selectivity data against related DNA repair proteins or a panel of unrelated targets. For the known drugs, discuss how their primary pharmacological activities might confound the interpretation of results.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor and experimental design
- **Claim pointer** "H1299 cells presented the highest ERCC1 expression" and "There was no statistical significance between all cell lines regarding ERCC4 expression"
- **Evidence pointer** Section 2.2.1, Figure 8
- **Concern** The statistical analysis is incompletely described. For the qRT-PCR data, it is unclear how many biological replicates were performed, what statistical test was used, and whether multiple comparison corrections were applied. For the combination screening data, the number of independent experiments (2-3) is low, and the variability is not shown in the text.
- **Why it matters** The selection of H1299 as the model cell line is a key decision in the experimental design. If the statistical basis for this selection is weak, the rationale for the entire experimental pipeline is weakened. Similarly, the screening results need adequate statistical power to support the identification of 22 hits.
- **Resolution test** Provide complete statistical details including number of replicates, tests used, and dispersion measures. Consider increasing the number of independent experiments for the screening assay.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and data availability
- **Claim pointer** "The chemical structures of the 22 best inhibitors are present in Supplementary Materials, Figure S1"
- **Evidence pointer** Section 2.3.1, Supplementary Figure S1
- **Concern** The identities of the 22 selected compounds are not provided in the main text. The reader cannot evaluate whether these compounds are chemically reasonable, whether they are known pan-assay interference compounds (PAINS) that passed the filter, or whether they represent diverse chemotypes as claimed.
- **Why it matters** Reproducibility is a core scientific principle. Without compound identities in the main text or accessible supplementary material, the study cannot be replicated or built upon by other researchers.
- **Resolution test** Provide a table of the 22 compounds with their structures, docking scores, and key physicochemical properties in the main text or a readily accessible supplementary file.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Section 2.1.3, virtual screening workflow
- **Evidence pointer** Section 2.1.3, Figure 5
- **Issue** The description of the virtual screening workflow is somewhat fragmented, with details of filtering criteria (score thresholds, PAINS filters) presented in different parts of the text. The schematic in Figure 5 is helpful but the text could be more streamlined.
- **Required correction** Consolidate the description of the virtual screening pipeline into a single, clearly numbered sequence of steps with explicit thresholds for each filter.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Interpretation of computational results
- **Affected element** Section 2.1.1, structural analysis
- **Evidence pointer** Section 2.1.1, Figure 1, Table 1
- **Issue** The RMSD values (1.30-1.60 Å) are presented as evidence of structural similarity, but the significance of these values for the specific region of interest is not discussed. The statement that the pocket is "highly conserved" is based on visual inspection and RMSD alone.
- **Required correction** Provide a quantitative measure of pocket conservation (e.g., residue identity across structures) and discuss the RMSD values in the context of the specific binding site.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Experimental details
- **Affected element** Section 3.2.6, combination screening
- **Evidence pointer** Section 3.2.6
- **Issue** The concentration of 50 µM for the putative inhibitors is described as a "balanced compromise," but no justification is provided for why this concentration is appropriate for the screening. The solubility of the compounds at this concentration is not discussed.
- **Required correction** Provide a rationale for the 50 µM screening concentration, including any preliminary solubility or toxicity data.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction, Section 1
- **Evidence pointer** Section 1
- **Issue** The introduction mentions previous computational studies on ERCC1-XPF inhibitors but does not clearly differentiate the present approach from prior work in terms of methodology or findings.
- **Required correction** Add a brief comparison with prior computational studies on ERCC1-XPF, highlighting the specific methodological advances or novel findings of this work.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 10
- **Evidence pointer** Figure 10
- **Issue** The figure showing combination screening results for 102 compounds is likely to be dense and difficult to interpret. The text does not describe how the data are presented (e.g., individual data points, means, error bars).
- **Required correction** Clarify the presentation of data in Figure 10 and consider whether a heatmap or other visualization would be more effective for 102 compounds.

## Risk / unsupported claims
- The claim that 22 compounds are "promising enhancers of cisplatin efficacy" is not supported by dose-response or synergy analysis; the evidence is limited to a single-concentration screening assay.
- The claim that these are "ERCC1-XPF complex inhibitors" is not supported by experimental target engagement data; the mechanism is inferred from computational docking only.
- The statement that "Phe293 (ERCC1) plays a pivotal role in maintaining complex stability" is based on literature and structural analysis but is not experimentally validated in this study.
- The claim that the virtual screening protocol was "validated" using the ChEMBL set is weakened by the lack of quantitative metrics (e.g., enrichment factors, AUC values) for the validation.
- The selection of H1299 as the model cell line is based on ERCC1 expression, but the functional relevance of this expression level to NER activity or cisplatin sensitivity is not demonstrated.
- The manuscript does not provide evidence that the 22 compounds are cell-permeable or stable under assay conditions, which is a prerequisite for their proposed intracellular activity.