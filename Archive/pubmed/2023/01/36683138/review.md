## Review setup
- **Input scope** Full manuscript text (abstract, introduction, experimental procedures, results and discussion, conclusion, and supporting information references)
- **Assessment boundary** Scientific claims, experimental design, data interpretation, structural modeling rationale, and alignment with stated conclusions
- **Shared manuscript claim summary** The manuscript reports that water potential (matric stress) modulates the effector specificity of the transcriptional regulator XylR in Pseudomonas putida, with low water potential narrowing specificity toward cognate substrates and high water availability broadening promiscuity, and that this effect is mediated by water-dependent conformational changes in the A domain binding pocket, as supported by in vivo reporter assays and AlphaFold structural predictions.
- **Visible evidence base** Reporter-based transcriptional assays (luxCDEAB) under PEG8000-induced matric stress; comparative analysis of wild-type XylR and variants (Va, V18, V101); glycine betaine osmoprotection experiments; AlphaFold structural models with CAVER pocket/tunnel calculations; statistical analyses (Student's t-test)
- **Missing materials affecting confidence** Raw numerical data for luminescence measurements; full growth curves under PEG8000 conditions; detailed statistical outputs (exact p-values, effect sizes); AlphaFold confidence metrics (pLDDT scores) and validation of predicted structures; original I-TASSER model comparison data; strain construction verification details (PCR results); supplementary figures (Figure S1, S2, S3) not provided in the submitted text

## Reviewer
- **Overall assessment** This manuscript addresses an interesting and underexplored question: how water availability affects the effector specificity of a key transcriptional regulator in catabolic pathways. The experimental system is well chosen, and the use of a non-disruptive lux reporter in strains lacking the TOL plasmid is a sound approach to isolate regulatory effects from metabolic consumption. The observation that matric stress alters the response of XylR to suboptimal inducers, and that this can be reversed by glycine betaine, is potentially significant. However, the manuscript has several weaknesses that currently limit the strength of the conclusions. The quantitative data are presented in a way that makes it difficult to assess the magnitude and reproducibility of the reported effects. The structural interpretation relies heavily on AlphaFold predictions without adequate validation or discussion of limitations. The reinterpretation of previously isolated XylR variants as "water-unresponsive" rather than "effector-specificity variants" is intriguing but not fully supported by the data presented. The link between in vitro structural predictions and in vivo regulatory behavior remains speculative. Overall, the core observation is novel and worthy of publication, but the current evidence base does not fully establish the mechanistic claims.

- **Who would be interested in the results, and why** Researchers in environmental microbiology, biodegradation, and bioremediation would be interested because the work addresses a fundamental environmental parameter (water availability) that is often overlooked in laboratory studies but is critical in soil and rhizosphere settings. Those studying prokaryotic enhancer-binding proteins and σ54-dependent regulation would find the potential environmental modulation of effector specificity relevant to understanding regulatory evolution. The work also speaks to the broader field of protein promiscuity and its role in the evolution of new functions, which would interest evolutionary biologists and protein engineers. Finally, the use of AlphaFold to generate testable hypotheses about environmental sensing could interest structural biologists.

- **Major strengths**
  1. The experimental system is well designed: using a pWW0-free host with a chromosomal lux reporter avoids confounding effects of substrate metabolism and allows direct measurement of transcriptional output.
  2. The inclusion of a constitutive XylR∆A control (MAD3) is a thoughtful approach to separate effects on the general transcription machinery from effects on the regulator itself.
  3. The observation that glycine betaine reverses the effect of matric stress on TCB responsiveness provides a clear link to osmotic physiology.
  4. The reinterpretation of previously isolated "effector-specificity" variants as potentially "water-unresponsive" variants is a conceptually interesting and testable hypothesis.
  5. The use of AlphaFold to generate structural hypotheses about water-dependent conformational changes is timely and forward-looking.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that "water potential governs the effector specificity" of XylR, with a specific effect at −0.25 MPa versus −0.75 MPa, and that this is due to water-dependent conformational changes in the A domain.
- **Evidence pointer** Figure 1C, Figure 2A, Figure 2B, Figure 3, Figure 5; Results and Discussion sections "Effect of matric stress on the transcriptional activity of the XylR/Pu regulatory node" and "Water access determines inducer specificity"
- **Concern** The quantitative data supporting the central claim are not presented with sufficient detail. The manuscript reports luminescence values normalized by OD600 but does not provide raw data, exact fold-changes, or confidence intervals for the key comparisons. The "intriguing peak" at −0.25 MPa in Figure 1C is described qualitatively, and it is unclear whether this peak is reproducible across biological replicates. The claim that XylR becomes "more effector-specific" under matric stress is based on a comparison of only a few inducers, and the statistical significance of the differences between −0.25 and −0.75 MPa conditions is not fully reported. Without these data, it is difficult to assess the robustness of the central phenomenon.
- **Why it matters** The entire manuscript hinges on the claim that water potential quantitatively and reproducibly alters effector specificity. If the effect is small, variable, or dependent on specific batch conditions, the conclusions would be substantially weakened. The current presentation does not allow the reader to evaluate this.
- **Resolution test** Provide raw luminescence data (or normalized values with error bars) for all conditions tested, including biological replicates. Report exact p-values and effect sizes for the key comparisons (e.g., −0.25 vs −0.75 MPa for each inducer). Show that the peak at −0.25 MPa is reproducible across independent experiments. If possible, include a dose-response curve across a wider range of water potentials.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural interpretation validity
- **Claim pointer** The manuscript claims that "the effector-binding pocket of the XylR A domain is prone to water-dependent changes" and that the variants studied "seem to bring about a more expanded volume of the A domain tunnel and binding pocket," which is used to explain the observed in vivo phenotypes.
- **Evidence pointer** Figure 6, Figure S2, Figure S3; Results and Discussion section "The effector-binding pocket of the XylR A domain is prone to water-dependent changes"; Experimental Procedures section "Structural models"
- **Concern** The structural interpretation is based entirely on AlphaFold predictions without experimental validation. The manuscript does not report pLDDT confidence scores, which are critical for assessing the reliability of the predicted structures, particularly for loop regions and the binding pocket. The comparison between the I-TASSER and AlphaFold models is mentioned but not shown in detail. The claim that the variants have "more expanded" binding pockets is based on CAVER calculations, but the manuscript does not report the variability of these calculations or whether the differences are statistically significant. Furthermore, the link between pocket volume and water-dependent conformational changes is speculative; no molecular dynamics simulations or experimental biophysical data are provided to support the claim that water availability directly alters the conformation of the A domain.
- **Why it matters** The structural model is used to provide a mechanistic explanation for the observed in vivo phenomena. If the structural predictions are unreliable or the interpretation is overextended, the mechanistic claim is not supported. The manuscript would be strengthened by a more cautious interpretation or by additional validation.
- **Resolution test** Report pLDDT scores for the AlphaFold models and discuss regions of low confidence. Provide a quantitative comparison of pocket volumes with measures of variability (e.g., standard deviation across multiple calculations). If possible, perform molecular dynamics simulations at different water activities to test whether the pocket volume changes. Alternatively, temper the structural claims and present them as hypotheses rather than conclusions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive framing
- **Claim pointer** The manuscript claims that previously isolated XylR variants (Va, V18, V101), which were selected for responsiveness to TCB, "can be reinterpreted instead as proteins that have lost water control of XylR activity."
- **Evidence pointer** Figure 4, Figure 5; Results and Discussion section "Revisiting XylR effector specificity variants responsive to TCB"
- **Concern** The reinterpretation of the variants is interesting but not fully supported. The data show that these variants have higher basal activity and reduced sensitivity to water potential, but this does not necessarily mean they have "lost water control." It could also mean that the mutations have increased the intrinsic activity of the regulator, making it less dependent on environmental modulation. The manuscript does not directly test whether the variants have lost water sensing or whether they have simply become more active. The claim that the variants "keep a native ability to respond to this compound which could now emerge by eliminating osmotic control" is speculative and not directly tested.
- **Why it matters** The reinterpretation of the variants is a key conceptual contribution of the manuscript. If the interpretation is not well supported, the novelty of the work is diminished. A more careful framing would acknowledge alternative explanations.
- **Resolution test** Perform additional experiments to distinguish between loss of water sensing and increased intrinsic activity. For example, measure the response of the variants to a range of water potentials and inducers, and compare their maximal activity levels. Alternatively, frame the interpretation more cautiously as one possible explanation among several.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The manuscript concludes that "the effector profile of XylR is tuned by environmental water availability" and discusses implications for the evolution of catabolic pathways.
- **Evidence pointer** Conclusion section; Discussion throughout
- **Concern** The manuscript studies only one regulator (XylR) and one set of conditions (PEG8000-induced matric stress in LB medium). The claim that this phenomenon is general, with implications for the evolution of catabolic pathways, is an extrapolation. The manuscript does not discuss whether other regulators in the same family might behave similarly, nor does it address whether the effect is specific to the A domain of XylR or a more general property of such regulators. The evolutionary implications are speculative and not grounded in comparative data.
- **Why it matters** The broader significance of the work depends on the generalizability of the findings. If the effect is specific to XylR or to the particular conditions tested, the impact is more limited.
- **Resolution test** Discuss the generalizability of the findings more carefully, acknowledging the limitations of studying a single system. If possible, include preliminary data on a related regulator or discuss how the findings might be tested in other systems.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1C description
- **Evidence pointer** Results and Discussion section "Effect of matric stress on the transcriptional activity of the XylR/Pu regulatory node"
- **Issue** The description of the "intriguing peak" at −0.25 MPa is vague. It is unclear whether this peak is consistently observed and what its biological significance might be.
- **Required correction** Clarify whether the peak is reproducible and provide a more detailed description of its magnitude and potential significance.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Matric stress assay description
- **Evidence pointer** Experimental Procedures section "Matric stress"
- **Issue** The manuscript states that PEG8000 was added to cultures at OD600 1.0 and incubated for 30 min prior to inducer addition. It is unclear whether the cells were in exponential growth at this point and whether the 30-min pre-incubation was sufficient for the cells to experience the full effect of the osmotic stress.
- **Required correction** Provide more detail on the growth phase of the cells and justify the 30-min pre-incubation period.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Statistical analyses
- **Evidence pointer** Experimental Procedures section "Statistical analyses"; figure legends
- **Issue** The manuscript states that "data were treated with a two-tailed unpaired Student's t-test" but does not report exact p-values or effect sizes in the text or figure legends.
- **Required correction** Report exact p-values and, where appropriate, effect sizes for all statistical comparisons.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Structural modeling
- **Affected element** AlphaFold methodology
- **Evidence pointer** Experimental Procedures section "Structural models"
- **Issue** The manuscript does not report the version of AlphaFold used or the confidence metrics (pLDDT) for the predicted structures. This limits the reader's ability to assess the reliability of the models.
- **Required correction** Report the AlphaFold version and pLDDT scores, and discuss any regions of low confidence.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Use of "water potential" vs "osmotic stress"
- **Evidence pointer** Throughout
- **Issue** The manuscript uses "water potential," "matric stress," and "osmotic stress" somewhat interchangeably. While related, these terms have distinct meanings in soil physics and microbial physiology.
- **Required correction** Define the terms clearly and use them consistently throughout the manuscript.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction; Discussion
- **Issue** The manuscript cites relevant literature but does not fully contextualize the findings within the broader field of osmoregulation and its effects on gene regulation. A more thorough discussion of how water potential affects other regulatory systems would strengthen the manuscript.
- **Required correction** Expand the discussion to include relevant examples of osmoregulation affecting gene expression in other bacteria.

## Risk / unsupported claims
- The claim that water potential directly causes conformational changes in the XylR A domain is not supported by direct experimental evidence; it is inferred from AlphaFold predictions and in vivo reporter data.
- The reinterpretation of the Va, V18, and V101 variants as "water-unresponsive" rather than "effector-specificity" variants is plausible but not definitively established.
- The claim that the effect of water potential on XylR effector specificity has implications for the evolution of catabolic pathways is speculative and not supported by comparative or evolutionary data.
- The statement that "the only way to reach the active centre of the A domain is by having a very plastic conformation" is an overstatement; alternative mechanisms (e.g., ligand-gated channel opening) are not discussed.
- The manuscript claims that the strains used are "not rigorously isogenic" but that pair-wise comparisons substantiate the claims; this caveat is acknowledged but the potential impact on the conclusions is not fully discussed.