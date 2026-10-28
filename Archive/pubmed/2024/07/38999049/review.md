## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors identify novel GANT61 analogs with inhibitory activity in Hedgehog functional assays and GLI1-dependent cancer cells, with BAS 07019774 emerging as a lead compound predicted to bind the ZF4 region of GLI1.
- **Visible evidence base** Abstract, Introduction, Results (Sections 2.1–2.7), Discussion, Conclusions, Materials and Methods (Sections 4.1–4.8), Figure legends referenced in text, Table 1 and Table 2 referenced in text
- **Missing materials affecting confidence** Figures 1–7 and Supplemental Figures S1–S5, Supplemental Tables S1–S3, raw dose-response data, statistical analysis outputs, compound purity and structural characterization data, full experimental details for docking validation

## Reviewer
- **Overall assessment** The manuscript describes a systematic screen of 52 GANT61 analogs using two orthogonal Hedgehog-responsive cell-based assays, followed by qRT-PCR validation and cancer cell viability studies. The work addresses a relevant problem, namely the need for improved GLI1 inhibitors with better stability and potency than GANT61. The identification of BAS 07019774 as a compound with activity in multiple assays is of interest. However, the evidence presented is incomplete in several critical areas. The claim that BAS 07019774 targets GLI1 directly is supported only by computational docking without experimental validation. The manuscript does not provide sufficient data to establish the mechanism of action, selectivity, or the relationship between GLI1 expression levels and compound sensitivity in the cancer cell lines used. The stability and solubility data that would support the central premise of improved properties over GANT61 are not presented. The statistical analysis section describes methods that are not clearly linked to specific results. The manuscript would benefit from additional experiments and clearer presentation of data.

- **Who would be interested in the results, and why** Researchers in cancer biology and drug discovery, particularly those focused on the Hedgehog signaling pathway, GLI transcription factors, and the development of small-molecule inhibitors. The work may also be of interest to medicinal chemists seeking new scaffolds for GLI inhibition. The identification of a compound with activity in GLI1-dependent cancer cell lines could provide a starting point for further optimization.

- **Major strengths** The study uses two orthogonal cell-based assays to filter initial hits, which reduces the likelihood of assay-specific artifacts. The inclusion of a cytotoxicity assessment strengthens the interpretation that the observed inhibition is not due to general cell killing. The use of qRT-PCR to confirm Gli1 mRNA reduction provides a direct readout of pathway transcriptional activity. The docking analysis, while preliminary, offers a testable hypothesis for the binding mode of BAS 07019774.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for mechanism of action
- **Claim pointer** The manuscript claims that BAS 07019774 inhibits Hedgehog signaling by targeting GLI1, specifically by binding to the ZF4 region and potentially interfering with DNA binding.
- **Evidence pointer** Section 2.7, Figure 6, Section 3
- **Concern** The only evidence for direct GLI1 binding is a computational docking prediction. No biochemical or biophysical experiments (e.g., surface plasmon resonance, isothermal titration calorimetry, electrophoretic mobility shift assay, or cellular thermal shift assay) are presented to support direct binding of BAS 07019774 to GLI1. The docking prediction is not validated by mutagenesis or by testing analogs with modified predicted contact residues. The manuscript acknowledges discrepancies with previous docking studies for GANT61 but does not resolve them experimentally.
- **Why it matters** The central claim of the manuscript is that BAS 07019774 is a GLI1 inhibitor. Without experimental evidence of direct binding, the mechanism of action remains speculative. The observed effects on Gli1 mRNA and cell viability could be mediated by upstream pathway components or off-target effects.
- **Resolution test** Provide experimental evidence of direct GLI1 binding, such as surface plasmon resonance or a cellular thermal shift assay. Alternatively, demonstrate that mutations in the predicted binding residues (e.g., Arg348, His335, Glu334) abolish compound activity in a functional assay.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for selectivity and on-target activity
- **Claim pointer** The manuscript claims that BAS 07019774 reduces viability in GLI1-dependent cancer cell lines (U87MG, T98G, SK-MES-1) but not in a cell line with minimal GLI expression (H1437).
- **Evidence pointer** Section 2.6, Figure 5
- **Concern** The manuscript does not establish that the cancer cell lines used are indeed GLI1-dependent. GLI1 and GLI2 expression is shown, but no functional evidence (e.g., GLI1 knockdown or overexpression) links the observed viability effects to GLI1 dependence. The statement that H1437 has minimal GLI expression is presented, but the manuscript does not demonstrate that BAS 07019774 is inactive in other GLI-independent cell lines. The selectivity of the compound for GLI1 over GLI2 is not addressed experimentally.
- **Why it matters** The conclusion that BAS 07019774 is effective in GLI1-dependent cancer cells requires evidence that the observed effects are specifically due to GLI1 inhibition. Without this, the compound could be acting through other mechanisms, and the proposed link between GLI1 expression and sensitivity is not established.
- **Resolution test** Perform GLI1 knockdown or overexpression experiments in the cancer cell lines to demonstrate that sensitivity to BAS 07019774 correlates with GLI1 dependence. Include additional GLI-independent cell lines as controls.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for improved properties over GANT61
- **Claim pointer** The manuscript states that GANT61 has been hindered by modest activity and aqueous chemical instability, and implies that the identified analogs may have improved properties.
- **Evidence pointer** Abstract, Section 3, Table 2
- **Concern** No experimental data on the stability or solubility of BAS 07019774 or any other analog are presented. Table 2 is referenced for calculated chemical properties, but the actual stability and solubility of the compounds are not measured. The claim that these analogs may overcome GANT61 limitations is therefore unsupported.
- **Why it matters** The rationale for seeking GANT61 analogs is based on the limitations of GANT61. If the new analogs do not demonstrate improved stability or solubility, the significance of the work is substantially reduced.
- **Resolution test** Provide experimental measurements of aqueous stability and solubility for BAS 07019774 and GANT61 under relevant conditions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and data availability
- **Claim pointer** The manuscript reports IC50 values for multiple compounds in multiple assays.
- **Evidence pointer** Sections 2.2, 2.3, 2.6, Table 1
- **Concern** The number of independent experiments and the variability of the IC50 values are not clearly reported. The statistical methods described in Section 4.8 are not explicitly linked to the results in Sections 2.2–2.6. It is unclear which comparisons were tested and what the statistical outcomes were.
- **Why it matters** Reproducibility and clarity of statistical reporting are essential for evaluating the robustness of the findings. Without this information, the reliability of the reported IC50 values and the significance of the observed differences cannot be assessed.
- **Resolution test** Clearly state the number of independent experiments for each assay, report IC50 values with confidence intervals, and specify which statistical tests were applied to which comparisons.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Completeness of compound characterization
- **Claim pointer** The manuscript identifies 52 GANT61 analogs and reports their activities.
- **Evidence pointer** Section 2.1, Supplemental Table S1
- **Concern** The manuscript does not provide structural information for the analogs beyond the chemical names or identifiers. No purity data or structural confirmation (e.g., NMR, mass spectrometry) are presented. The source of the compounds is stated, but the quality control of the purchased compounds is not described.
- **Why it matters** The reproducibility of the findings depends on the availability of well-characterized compounds. Without purity and structural confirmation, the results cannot be reliably interpreted or replicated.
- **Resolution test** Provide structural formulas, purity data, and confirmation of compound identity for all analogs used in the study.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Section 2.5
- **Evidence pointer** Section 2.5, Figure 4
- **Issue** The text states "BAS 0701977" in Section 2.5, which appears to be a typo for "BAS 07019774". This inconsistency could confuse readers.
- **Required correction** Correct the compound identifier to "BAS 07019774" throughout the manuscript.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Section 4.7
- **Evidence pointer** Section 4.7
- **Issue** The docking methods are described briefly. The preparation of the protein structure, the ligand preparation, the search algorithm, and the scoring function are not described in sufficient detail to allow reproduction.
- **Required correction** Provide a more detailed description of the docking protocol, including software parameters, preparation steps, and validation of the docking procedure.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of results
- **Affected element** Section 2.2
- **Evidence pointer** Section 2.2, Table 1
- **Issue** The IC50 values for BAS 07019774 differ between the fluorescence and absorbance readouts of the C3H10T1/2 assay (5.5 μM vs. 3.3 μM). The manuscript does not discuss this discrepancy.
- **Required correction** Address the variability between the two readouts and discuss potential reasons for the observed differences.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Section 3
- **Evidence pointer** Section 3
- **Issue** The discussion of other GLI inhibitors is brief. A more comprehensive comparison with previously reported GLI inhibitors, including their potencies and mechanisms, would strengthen the context.
- **Required correction** Expand the discussion to include a more detailed comparison with other GLI-targeting compounds.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Section 2.6
- **Evidence pointer** Section 2.6, Figure 5
- **Issue** The manuscript reports IC50 values for BAS 07019774 in cancer cell lines but does not show the full dose-response curves or the statistical significance of the effects compared to controls.
- **Required correction** Include representative dose-response curves and statistical analysis for the cancer cell viability data.

## Risk / unsupported claims
- The claim that BAS 07019774 binds to the ZF4 region of GLI1 is unsupported by experimental evidence and relies solely on computational docking.
- The claim that the identified analogs may have improved properties over GANT61 is unsupported, as no stability or solubility data are presented.
- The claim that the cancer cell lines used are GLI1-dependent is not experimentally established.
- The statement that BAS 07019774 is more effective than GANT61 in reducing U87MG cell viability is based on limited data and lacks statistical context.
- The manuscript does not provide evidence that the observed inhibition in the cancer cell lines is specifically due to GLI1 targeting rather than off-target effects.