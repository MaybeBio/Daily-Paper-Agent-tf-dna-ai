## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors report the synthesis of a set of arylazo sulfones and their evaluation for DNA binding, DNA cleavage, photocleavage, molecular docking, and activity against A375 melanoma and non-cancer cell lines. They report significant DNA affinity (Kb in the 10⁵–10⁶ M⁻¹ range), enhanced DNA photocleavage under UV-A irradiation for most compounds, and phototoxic effects on melanoma cells for compounds 1, 14, and 17, with IC50 values of approximately 13, 100, and 100 μM, respectively.
- **Visible evidence base** Abstract; Introduction; Results and Discussion sections 2.1–2.6; Materials and Methods sections 3.1–3.4; Conclusions; Figures 2–11 referenced; Tables 1–3 referenced; Supporting Information referenced but not provided
- **Missing materials affecting confidence** Supporting Information (S.1–S.10) not provided; raw gel electrophoresis images not shown; full UV-vis and fluorescence spectra not shown; viscosity data plots not shown; molecular docking figures and detailed interaction data not fully visible; statistical analysis details not provided; cell viability raw data not shown

## Reviewer
- **Overall assessment** The manuscript presents a systematic study of arylazo sulfones as potential DNA-targeting phototoxic agents. The work combines synthetic chemistry, biophysical DNA binding studies, plasmid DNA cleavage assays, molecular docking, and cellular assays. The topic is of interest to the photochemistry and medicinal chemistry communities. However, several technical concerns limit the strength of the conclusions as currently presented. The DNA binding mode is not definitively established, the correlation between in vitro DNA damage and cellular phototoxicity is not rigorously demonstrated, and the selectivity claims for cancer versus non-cancer cells are based on preliminary data. The manuscript would benefit from additional mechanistic experiments, quantitative comparisons, and clearer presentation of raw data.

- **Who would be interested in the results, and why** Researchers in photodynamic therapy, photochemotherapy, DNA-targeting drug design, and medicinal chemistry would be interested. The arylazo sulfone scaffold is relatively underexplored in biological contexts, and the demonstration of light-triggered DNA damage and cellular phototoxicity could inform the design of new photosensitizers. The comparative analysis of substituent effects on DNA binding and photocleavage may also be of interest to structure-activity relationship studies.

- **Major strengths**
  1. The study addresses a novel application of arylazo sulfones, which have been previously studied for synthetic photochemistry but not for biological activity. This is a clear conceptual advance.
  2. The experimental design is multi-faceted, combining biophysical, biochemical, computational, and cellular approaches, which provides a broad initial characterization.
  3. The inclusion of non-cancer cell lines as controls is commendable and addresses the selectivity question, albeit in a preliminary manner.
  4. The identification of compound 1 with an IC50 of approximately 13 μM under UV-A irradiation is a promising finding that warrants further investigation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the compounds interact with CT DNA via intercalation, based on UV-vis spectroscopy, viscosity measurements, and EB displacement assays.
- **Evidence pointer** Section 2.2; Figures 3–5; Tables 1–2; Supporting Information S.2–S.4
- **Concern** The evidence for intercalation is not conclusive. The UV-vis spectral changes are described as "slight hyperchromism or even hypochromism accompanied by a slight red-shift," which is not the classic hypochromism and red-shift pattern expected for strong intercalators. The viscosity data are described as showing an initial plateau followed by an increase only at higher r values, which is not the monotonic increase expected for classical intercalation. The EB displacement assay shows significant displacement for some compounds, but the correlation with the other two methods is not clearly established. The authors themselves note that "the interaction mode may not be safely interpreted" from UV-vis data alone, yet the conclusion of intercalation is still presented.
- **Why it matters** The proposed mechanism of DNA binding underpins the interpretation of the cleavage and photocleavage data. If the binding mode is not intercalation but groove binding or electrostatic interaction, the mechanistic interpretation of DNA damage and the design of improved derivatives would be affected. The claim of intercalation is central to the manuscript's narrative.
- **Resolution test** Provide a more rigorous analysis of the viscosity data, including a plot of (L/L0)³ versus r for multiple compounds, and compare with a known intercalator (e.g., ethidium bromide) under identical conditions. If the viscosity increase is modest, temper the intercalation claim and discuss alternative binding modes. Additionally, perform thermal denaturation (melting temperature) studies, which are a standard and more definitive test for intercalation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that UV-A irradiation considerably improves DNA damage for most compounds, and that compound 5 is very active even at 25 μM, leading to 50% cleavage between 10 and 25 μM.
- **Evidence pointer** Section 2.3; Figures 6–7; Supporting Information S.6
- **Concern** The quantification of DNA cleavage is described only in qualitative terms ("considerable," "very effective," "slightly lower"). No numerical data, error bars, or statistical analysis are provided for the gel electrophoresis quantification. The claim that compound 5 leads to 50% cleavage between 10 and 25 μM is presented without a clear dose-response curve or replicate data. The comparison between UV-A and visible light effects is not quantified.
- **Why it matters** The photocleavage efficiency is a key claim of the manuscript and is used to support the potential of these compounds as photosensitizers. Without quantitative data, the relative potency of the compounds cannot be assessed, and the structure-activity relationships discussed in the text are not supported by rigorous evidence.
- **Resolution test** Provide quantified cleavage data (e.g., percentage of nicked or linear DNA) with standard deviations from at least three independent experiments. Present dose-response curves for key compounds (1, 5, 14, 17) under dark, UV-A, and visible light conditions. Perform statistical comparisons (e.g., ANOVA) to support claims of significant differences between conditions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that compound 1 shows a photo-disruptive effect on A375 melanoma cells with IC50 of approximately 13 μM under UV-A irradiation, and that compounds 1, 14, and 17 are equally toxic to non-cancer cell lines only upon irradiation and not in the dark.
- **Evidence pointer** Sections 2.5–2.6; Figures 9–11; Supporting Information S.10
- **Concern** The cell viability data are presented as single representative experiments without error bars, replicate numbers, or statistical analysis. The IC50 value for compound 1 is stated as 13.34 μM, but the dose-response curve is not shown with confidence intervals. The comparison between cancer and non-cancer cell lines is based on a single concentration point for the non-cancer lines (13.4 μM for compound 1 and 100 μM for compounds 14 and 17), which is insufficient to establish selective toxicity or lack thereof. The statement that compounds are "equally toxic" to non-cancer cells is not supported by dose-response data.
- **Why it matters** The cellular phototoxicity data are the most translationally relevant findings. The claim of light-controlled activity is promising, but the lack of rigorous quantification and statistical analysis prevents assessment of the therapeutic window and selectivity. The preliminary nature of the non-cancer cell data is acknowledged in the text, but the conclusions still overreach.
- **Resolution test** Provide full dose-response curves for compounds 1, 14, and 17 in A375, HFL1, and HaCaT cells, both in the dark and under UV-A irradiation, with at least three independent replicates. Report IC50 values with 95% confidence intervals. Perform statistical comparisons between cancer and non-cancer cell lines to support any claims of differential sensitivity.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that molecular docking calculations "pointed out polar contacts, mainly via the sulfonyl moiety" and provide binding energy values in Table 3.
- **Evidence pointer** Section 2.4; Table 3; Figure 8; Supporting Information S.9
- **Concern** The docking methodology is described briefly, and the validation of the docking protocol is not discussed. The correlation between the calculated binding energies and the experimentally determined Kb values is not systematically analyzed. For example, compound 6 has the highest experimental Kb (2.87 × 10⁷ M⁻¹), but it is unclear whether the docking score for compound 6 is correspondingly the best. The docking results are presented as supportive but are not integrated with the experimental data in a quantitative manner.
- **Why it matters** Docking studies are often used to rationalize experimental binding data. Without a clear correlation or discussion of discrepancies, the docking results add limited value and may be seen as decorative rather than informative.
- **Resolution test** Provide a scatter plot of experimental Kb versus calculated binding energy for all compounds, with a correlation coefficient. Discuss outliers and discrepancies. If the correlation is poor, temper the claims about the predictive value of the docking and focus on the qualitative insights (e.g., polar contacts).

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Section 2.2
- **Evidence pointer** Figure 3; Table 1
- **Issue** The description of UV-vis spectral changes is vague ("slight hyperchromism or even hypochromism accompanied by a slight red-shift"). The reader cannot discern the magnitude of these changes or which compounds show which behavior.
- **Required correction** Provide a supplementary table listing the wavelength of maximum absorbance, the magnitude of hyper/hypochromism, and the shift for each compound. Alternatively, show representative spectra for each group in the Supporting Information.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 2.3.2
- **Evidence pointer** Figure 7
- **Issue** The figure legend mentions "each set of three same-colored plots indicates the average number of the % ss and % ds (photo)cleavage," but the figure itself is not provided in the manuscript text. The reader cannot verify the data.
- **Required correction** Ensure the figure is included with clear labels for dark, UV-A, and visible light conditions, and with error bars if averages are shown.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 3.3
- **Evidence pointer** Methods text
- **Issue** The docking methods state that "100 runs of the Lamarckian genetic algorithm" were performed, but the text also mentions AutoDock Vina, which uses a different search algorithm. This is confusing.
- **Required correction** Clarify which software was used for the final docking calculations. If AutoDock Vina was used, the Lamarckian genetic algorithm description is incorrect. If AutoDock 4.2 was used, specify this clearly.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Section 2.5
- **Evidence pointer** Figure 9
- **Issue** The text states that "compound 1 induced satisfactory photodamage, causing death in about 80% of the cells," but after normalization for DMSO toxicity, the effect is ~60%. This distinction is important but is presented in a confusing manner.
- **Required correction** Present both raw and normalized data clearly, and explain the normalization procedure in the methods or figure legend.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 2.6
- **Evidence pointer** Figure 11
- **Issue** The non-cancer cell experiments were performed at a single concentration for each compound (13.4 μM for compound 1 and 100 μM for compounds 14 and 17). This is acknowledged as preliminary, but the conclusion that the compounds are "equally toxic" to non-cancer cells is not supported by dose-response data.
- **Required correction** Temper the conclusion and state explicitly that full dose-response studies in non-cancer cell lines are required to assess selectivity.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Section 2.5
- **Evidence pointer** Figure 10
- **Issue** The IC50 for compound 1 is reported as 13.34 μM, but the concentration range tested and the number of replicates are not stated in the text.
- **Required correction** Provide the concentration range tested, the number of independent experiments, and the method used to calculate the IC50 (e.g., nonlinear regression).

## Risk / unsupported claims
- The claim that the compounds bind to DNA via intercalation is not fully supported by the presented data; the viscosity and UV-vis data are suggestive but not definitive.
- The claim that UV-A irradiation "considerably improved" DNA damage is not quantified, and the comparison between UV-A and visible light is not statistically supported.
- The claim that compound 1 has an IC50 of approximately 13 μM in A375 cells under UV-A is based on a single described experiment without error analysis.
- The claim that compounds 1, 14, and 17 are "equally toxic" to non-cancer cell lines is based on single-concentration experiments and is not supported by dose-response data.
- The molecular docking results are presented as supportive but are not quantitatively correlated with experimental binding data, limiting their interpretative value.
- The statement that "the azosulfone moiety is important for showing the examined biological activities" is based on a single comparison (compound 15 vs. the sulfones) and requires additional analogs to be conclusive.

## Assessment against Nature-style criteria
- **Originality** The application of arylazo sulfones to biological contexts is novel. Previous work on these compounds has focused on synthetic photochemistry. The concept of using the N–S bond lability for DNA photocleavage is a reasonable extension, but the mechanistic novelty is incremental. The study is original in its specific compound class but does not introduce a fundamentally new concept.
- **Scientific importance** The findings are of moderate importance. The identification of a new scaffold for phototoxic compounds is useful, but the potency (IC50 ~13 μM for the best compound) is modest compared to established photosensitizers. The lack of in vivo data and the preliminary selectivity assessment limit the translational significance.
- **Interdisciplinary readership** The work spans synthetic chemistry, biophysical chemistry, computational chemistry, and cell biology. It would appeal to researchers in photodynamic therapy, DNA-targeting drug design, and medicinal chemistry. However, the depth in each area is limited, and the manuscript may not fully engage specialists in any single discipline.
- **Technical soundness** The synthetic chemistry appears sound, and the biophysical methods are standard. However, the lack of quantitative data and statistical analysis in the cleavage and cell viability experiments is a significant weakness. The docking studies are not validated or correlated with experimental data. These issues need to be addressed.
- **Readability for nonspecialists** The manuscript is generally well-written and organized. The introduction provides adequate context. However, some sections (e.g., the description of UV-vis changes) are vague, and the figures are not all self-explanatory. The conclusions could be more carefully qualified given the preliminary nature of some data.

## Recommendation posture
**Supportive if technical concerns are resolved.** The manuscript addresses a novel application of arylazo sulfones and presents a broad initial characterization. However, the major concerns regarding the definitiveness of the intercalation claim, the lack of quantitative cleavage data, and the preliminary nature of the cell viability experiments must be addressed. Specifically, the authors should provide quantified and statistically analyzed data for DNA cleavage and cell viability, perform additional experiments to confirm the binding mode, and temper their conclusions where the evidence is not yet sufficient. If these revisions are made, the manuscript would be a valuable contribution to the field of phototoxic compound development.