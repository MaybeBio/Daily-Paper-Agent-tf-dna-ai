## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods) without figures, tables, videos, or supplementary files
- **Assessment boundary** Scientific claims, experimental logic, methodological adequacy, and interpretation as presented in the text; figure contents and raw data are not directly assessable
- **Shared manuscript claim summary** The authors report that full-length Kid (KIF22) forms a homodimer, moves processively along microtubules, and transports double-stranded DNA in vitro, revising the previous view of Kid as a monomeric, nonprocessive motor
- **Visible evidence base** Text descriptions of size-exclusion chromatography, mass photometry, single-molecule TIRF motility assays, AlphaFold2 and AlphaFold3 structural predictions, and a K605A point mutant
- **Missing materials affecting confidence** All figures, figure supplements, videos, source data files, and supplementary files; exact experimental replicates and statistical details are only partially described in the text

## Reviewer
- **Overall assessment** This manuscript addresses a long-standing question in the chromokinesin field, namely whether Kid is a monomeric, nonprocessive motor or a processive dimer. The authors provide multiple lines of evidence, including biochemical oligomerization analysis, single-molecule motility assays, domain deletion experiments, a chimeric motor construct, and an in vitro DNA transport assay. The central claims are potentially important and would revise the current understanding of Kid mechanochemistry. However, the manuscript as presented has several gaps that prevent full evaluation. The absence of figures and raw data limits verification of the quantitative claims. The mass photometry data showing predominantly monomeric Kid at nanomolar concentrations, combined with processive movement at picomolar concentrations, raises a conceptual tension that the authors acknowledge but do not fully resolve. The DNA transport experiments rely on a single point mutant for validation, and the AlphaFold3 modeling, while suggestive, is not experimentally corroborated beyond this single mutant. The discussion of how dimerization relates to DNA binding is speculative and would benefit from direct binding measurements. Overall, the work is timely and the conclusions are plausible, but the evidence as presented is not yet fully convincing.

- **Who would be interested in the results, and why** Researchers studying kinesin mechanochemistry, mitotic spindle assembly, and chromosome dynamics would be the primary audience. The finding that Kid is a processive dimer challenges the textbook view of this motor and has implications for how polar ejection forces are generated during prometaphase. The demonstration that a kinesin-10 family member can directly transport DNA along microtubules without adaptor proteins is also of interest to those studying cargo transport mechanisms. The chimeric KIF1A experiment provides general insight into the determinants of kinesin processivity and will interest the broader motor protein community.

- **Major strengths** The study addresses a clear and important question with a direct experimental approach using full-length proteins, which is a significant improvement over previous studies that relied on truncated constructs. The combination of biochemical oligomerization analysis and single-molecule motility assays provides complementary evidence. The use of both human and Xenopus orthologs strengthens the generality of the findings. The in vitro DNA transport assay is a novel and valuable addition that directly tests the cargo transport function of Kid. The authors are appropriately cautious in interpreting the trimer species and acknowledge the limitations of their AlphaFold predictions.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Full-length Kid forms a homodimer and moves processively along microtubules"
- **Evidence pointer** Results sections "Kid exhibits processive movement along microtubules" and "Full-length Kid form dimers"; Figures 1 and 2
- **Concern** The manuscript reports that Kid is predominantly monomeric by mass photometry at nanomolar concentrations, yet processive movement is observed at picomolar concentrations in single-molecule assays. The authors propose that dimerization occurs on the microtubule surface, but no direct evidence for this is provided. The two-color colocalization experiment (Figure 4) shows comigration of differently labeled Kid molecules, but the authors state that approximately 20% of motile particles showed comigration, leaving 80% of motile events potentially attributable to monomeric movement. The text does not clarify whether the 20% comigration rate is consistent with stochastic co-occurrence of two independent monomers or whether it represents a specific dimerization event. Without a quantitative model or control experiment, the claim that processive movement requires dimerization is not fully established.
- **Why it matters** The central revision of the field's understanding of Kid depends on demonstrating that the processive motor is a dimer. If monomeric Kid can also move processively, the mechanistic model presented in the Discussion would need substantial revision. The distinction between monomeric and dimeric processivity is fundamental to understanding how this motor generates force.
- **Resolution test** The authors should provide a quantitative analysis of the colocalization frequency relative to the expected random co-occurrence of two independent molecules at the measured surface densities. Alternatively, they could perform single-molecule photobleaching step analysis to directly determine the number of fluorophores per moving complex, or use a fluorescent protein with a known dimerization-deficient mutation to show loss of processivity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "The neck linker and coiled-coil domains of Kid could add processive activity to the motor domain of KIF1A"
- **Evidence pointer** Results section "The stalk domain of XKid adds processivity to the motor domain of KIF1A"; Figure 5
- **Concern** The chimeric KIF1A experiment is presented as evidence that the Kid neck linker and coiled-coil domains are sufficient to confer processivity. However, the text does not provide quantitative comparisons of the motility parameters (velocity, run length, processivity index) between the chimeric construct and the wild-type KIF1A or the full-length Kid. The statement that the chimera "exhibited processive movement" is qualitative. Without knowing whether the chimera's processivity is comparable to that of native processive kinesins, the conclusion that the Kid domains are "functional" is difficult to evaluate. Additionally, the text does not specify whether the KIF1A motor domain used in the chimera was the monomeric or dimeric version, which is critical for interpreting the result.
- **Why it matters** This experiment is intended to demonstrate that the Kid neck linker and coiled-coil domains are not only necessary but sufficient for processivity. If the quantitative parameters are not reported, the reader cannot assess whether the chimera is truly processive in the same sense as native Kid or whether it shows only marginal improvement over monomeric KIF1A.
- **Resolution test** The authors should report the full motility parameters for the chimera, including velocity, run length, and the fraction of processive runs, with appropriate controls. They should also specify the exact KIF1A construct used and compare the chimera's performance to both monomeric KIF1A and a known processive kinesin control.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** "Dimerization of Kid stabilizes the association with DNA"
- **Evidence pointer** Results section "Dimerization would be required for DNA transport"; Figure 7
- **Concern** The claim that dimerization stabilizes DNA binding is based on AlphaFold3 predictions and a single point mutant (K605A). The AlphaFold3 model shows two DNA-binding domains associating with one DNA molecule, but this is a prediction, not an experimental result. The K605A mutant abolishes DNA transport, but the text does not report whether this mutant is still able to dimerize. If K605A disrupts dimerization rather than DNA binding directly, the interpretation would be different. The authors do not provide a direct binding assay (e.g., electrophoretic mobility shift assay or surface plasmon resonance) to measure the affinity of wild-type versus mutant Kid for DNA, nor do they test whether a monomeric but DNA-binding-competent Kid construct can still transport DNA.
- **Why it matters** The proposed model that dimerization is required for stable DNA binding is a key mechanistic claim. If the K605A mutation affects dimerization rather than DNA binding, the conclusion would be that dimerization is required for transport but not necessarily for DNA binding. The distinction matters for understanding how Kid engages chromatin during mitosis.
- **Resolution test** The authors should perform a direct DNA binding assay with wild-type and K605A Kid, and should also test whether K605A affects dimerization (e.g., by size-exclusion chromatography or mass photometry). A complementary experiment using a dimerization-deficient but DNA-binding-competent construct would help separate these two functions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Evidence sufficiency
- **Claim pointer** "The full-length Kid, containing a helix–hairpin–helix domain, can transport double-stranded DNA along microtubules in vitro"
- **Evidence pointer** Results section "Reconstitution of DNA transport in vitro"; Figure 6
- **Concern** The DNA transport assay is a key novel result, but the text provides limited quantitative detail. The authors report that 93.4 ± 10.5% of DNA signals comigrated with Kid, but do not report the number of independent experiments, the number of molecules tracked, or the statistical test used. The velocity of DNA movement is stated to be approximately 100 nm/second, but no error or comparison to Kid-alone velocity is given. The specificity of the interaction is tested with the K605A mutant, but no other negative controls are described (e.g., a DNA-binding domain deletion mutant or a motor-dead mutant). The text also does not clarify whether the DNA is transported as a single molecule or as a DNA-protein complex with multiple Kid molecules.
- **Why it matters** The in vitro DNA transport assay is the most direct demonstration of Kid's cargo transport function. If the quantitative details are not provided, the reader cannot assess the robustness of the result or compare it to other motor-cargo systems.
- **Resolution test** The authors should report the number of independent experiments, the number of molecules analyzed, and the statistical methods used. They should also include additional negative controls, such as a motor-dead mutant or a construct lacking the DNA-binding domain, to demonstrate specificity.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, "AlphaFold3 prediction suggests that the dimerization of Kid stabilizes the association with DNA"
- **Issue** The abstract presents the AlphaFold3 prediction as a finding without clearly distinguishing it from experimental results. This could mislead readers into thinking the DNA-binding stabilization was experimentally demonstrated.
- **Required correction** Rephrase to clearly indicate that this is a computational prediction, for example, "AlphaFold3 prediction suggests..." should be followed by a statement that experimental validation is needed or that the K605A mutant provides preliminary support.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Results section "Full-length Kid form dimers"
- **Evidence pointer** Figure 2 and associated text
- **Issue** The text states that mass photometry revealed "a predominant monomer population, with a smaller fraction corresponding to dimers and trimers," but does not provide the relative proportions or the concentrations at which these measurements were made. The concentration dependence of the monomer-dimer equilibrium is central to the authors' argument, yet the quantitative relationship is not reported.
- **Required correction** Provide the relative fractions of monomer, dimer, and trimer at the measured concentrations, and ideally a concentration series showing the shift in oligomeric state.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section "Biochemical properties of Kid"
- **Evidence pointer** Discussion, paragraph on protein concentration
- **Issue** The authors attribute the discrepancy with previous studies to protein concentration, but they do not directly compare their results with the specific conditions used in the earlier studies. A more direct comparison, or at least a discussion of the concentration ranges used previously, would strengthen this argument.
- **Required correction** Add a brief comparison of the concentrations used in prior studies versus the current work, and discuss whether the differences are sufficient to explain the discrepant results.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Materials and methods, "TIRF single-molecule motility assays"
- **Evidence pointer** Methods section
- **Issue** The methods describe the assay procedure but do not specify how the concentration of Kid was calibrated or how the surface density of microtubules was controlled. These details are important for interpreting the single-molecule data, particularly the colocalization experiment.
- **Required correction** Add details on protein concentration determination, surface preparation, and any controls for nonspecific binding.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results sections and figure legends
- **Evidence pointer** Figures 1, 3, 5, and 6
- **Issue** The text reports means and standard deviations for some measurements but does not consistently report the number of independent experiments or the statistical tests used. The figure legends are not available for review, so the statistical details cannot be verified.
- **Required correction** Ensure that all quantitative claims are accompanied by the number of independent experiments, the number of measurements, and the specific statistical tests used.

## Risk / unsupported claims
- The claim that "dimerization of Kid stabilizes the association with DNA" is based on AlphaFold3 prediction and a single point mutant; direct experimental evidence for the stabilization mechanism is not provided
- The claim that the Kid neck linker and coiled-coil domains "could add processive activity to the motor domain of KIF22" is not quantitatively supported in the text
- The claim that Kid is "predominantly monomeric" at nanomolar concentrations is based on mass photometry, but the quantitative distribution of oligomeric states is not reported
- The claim that "microtubule-dependent association between hKid molecules" occurs is based on a colocalization experiment with a 20% comigration rate, but the expected random co-occurrence rate is not provided
- The in vitro DNA transport assay is described qualitatively; the number of experiments, molecules tracked, and statistical significance are not reported in the text
- The statement that "Kid has an exceptionally long neck linker, approximately four times longer than that of kinesin-1" is not supported by a direct structural or sequence alignment comparison in the text
- The claim that "the elementary force-generating unit of Kid is a single Kid dimer" is an extrapolation from the in vitro data and is not directly tested in the manuscript