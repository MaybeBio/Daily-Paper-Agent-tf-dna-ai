## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, footnotes)
- **Assessment boundary** Scientific content and technical soundness only. No assessment of editorial fit or journal-specific scope.
- **Shared manuscript claim summary** The authors identify a monomeric DNA-binding domain in the C-terminal region of human CtIP, show that CtIP binds non-specifically to DNA and diffuses processively over long distances, and demonstrate that efficient DNA bridging requires both DNA binding and tetramerization. Disease-associated CtIP variants (Seckel, Jawad, R100W) show impaired DNA binding and/or bridging.
- **Visible evidence base** Figures 1-7 (described in text), Supplementary Figures 1-5 (described), SEC-MALS, native nanoESI-MS, EMSA, fluorescence anisotropy, magnetic tweezers, optical tweezers/confocal microscopy
- **Missing materials affecting confidence** Figures and supplementary figures not directly viewable. Exact numerical values for some binding constants and statistical analyses not fully reported in text. Details of magnetic tweezers data analysis (e.g., number of molecules per condition, statistical tests) partially described. Methods for fluorescence anisotropy fitting not fully detailed.

## Reviewer
- **Overall assessment** This manuscript presents a systematic biochemical and biophysical dissection of CtIP DNA binding and bridging activities. The work is carefully executed, combining bulk and single-molecule approaches to define a minimal C-terminal DNA-binding domain and to demonstrate that tetramerization is required for efficient DNA bridging. The disease variant analysis adds translational relevance. The conclusions are largely supported by the data presented, though several technical details and quantitative analyses require clarification. The study advances our understanding of CtIP function but leaves open questions about the structural basis of DNA binding and the in vivo significance of bridging.
- **Who would be interested in the results, and why** Researchers in DNA repair, particularly homologous recombination and end resection; biophysicists studying protein-DNA interactions and single-molecule approaches; clinical geneticists interested in Seckel and Jawack syndromes; structural biologists studying intrinsically disordered proteins.
- **Major strengths** 1) Systematic construct design allowing clear dissection of functional domains. 2) Combination of bulk and single-molecule assays providing complementary views of DNA binding and bridging. 3) Direct comparison of disease-associated variants with wild-type protein. 4) Quantitative magnetic tweezers assay for DNA bridging that provides kinetic information. 5) Identification of a minimal C-terminal DNA-binding domain that will facilitate future structural studies.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative rigor of binding data), R1-M2 (magnetic tweezers assay validation), R1-M3 (ΔN790 binding specificity)
- **Assessment against Nature-style criteria** Originality: The identification of a monomeric C-terminal DNA-binding domain and the demonstration that tetramerization is specifically required for bridging (not binding) are novel contributions. Scientific importance: Moderate to high. The work clarifies the molecular basis of CtIP function, which is relevant to DNA repair and disease. Interdisciplinary readership: The work bridges biochemistry, biophysics, and human genetics, which could appeal to a broad audience. Technical soundness: Generally sound, but several quantitative aspects require strengthening (see concerns). Readability for nonspecialists: The manuscript is clearly written and the logic is easy to follow, though some single-molecule methodology may be challenging for non-specialists.
- **Recommendation posture** Supportive if technical concerns are resolved.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors report dissociation constants (Kd) for CtIP variants binding to a forked DNA substrate, including wild-type (66 nM and 37 nM in two independent experiments), R100W (115 nM), ΔN500 (45 nM and 33 nM), ΔN541 (210 nM and 960 nM), and ΔN790 (270 nM).
- **Evidence pointer** Results section "The CtIP disease variants tetramerise but cannot bind to DNA efficiently" and "The CtIP ΔN variants bind to DNA but cannot tetramerise"; Figures 2D-E and 3E-F
- **Concern** The manuscript reports Kd values from fluorescence anisotropy experiments but does not provide details on the fitting model, the number of replicates, or the error estimates for these values. The text states that wild-type Kd was 66 nM in one experiment and 37 nM in another (described as an "independent biological repeat"), but it is unclear whether these values are statistically distinguishable. For the ΔN541 variant, two different Kd values (210 nM and 960 nM) are reported for the two SEC peaks, but the text does not explain whether this difference is significant or reproducible. Additionally, the ΔN790 binding was measured using fluorescence quenching rather than anisotropy, which is a different observable and may not be directly comparable to the other measurements.
- **Why it matters** The quantitative comparison of binding affinities across variants is central to the conclusion that the C-terminal domain is the major DNA-binding determinant and that disease mutations impair binding. Without proper error analysis and statistical comparison, the reported differences (e.g., 2-fold reduction for R100W) may not be robust. The use of different assays for different variants (anisotropy vs. quenching) complicates direct comparison.
- **Resolution test** Provide Kd values with standard errors or confidence intervals from at least three independent replicates. Perform and report statistical tests comparing wild-type to each variant. If ΔN790 binding must be measured by quenching, validate that this method reports on the same binding event as anisotropy (e.g., by competition experiments or by measuring a known binding mutant).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "efficient bridging requires both the DNA binding and tetramerization activities of CtIP" based on magnetic tweezers experiments showing that ΔC608, ΔN500, and ΔN790 fail to bridge DNA, while ΔC782 and R100W show impaired but significant bridging.
- **Evidence pointer** Results section "The CtIP disease variants tetramerise but cannot bind to DNA efficiently" and "Only full length CtIP promotes efficient bridging of distant DNA segments"; Figures 4 and 5
- **Concern** The magnetic tweezers assay is described as a "single-molecule DNA bridging assay" but the text does not provide sufficient detail on how the assay distinguishes specific CtIP-mediated bridging from non-specific DNA condensation or aggregation. The classification of events into five classes (I-V) is described, but the criteria for classification appear somewhat subjective and the inter-observer or inter-experiment variability is not reported. The number of molecules analyzed per condition is stated in figure legends (as "N" values) but the statistical comparison between conditions (e.g., wild-type vs. ΔC782 vs. R100W) is not described. The text mentions that ΔC782 and R100W show "impaired but nevertheless significant bridging" but does not provide the statistical test or p-values supporting this claim.
- **Why it matters** The conclusion that tetramerization is specifically required for bridging (as opposed to binding) rests entirely on the magnetic tweezers data. If the assay cannot reliably distinguish specific bridging from non-specific effects, or if the statistical power is insufficient, the central claim of the paper is weakened.
- **Resolution test** Provide a more detailed description of the event classification criteria, including how partial ruptures (Class III) are distinguished from multiple independent events. Report the number of independent experiments and molecules analyzed per condition. Perform and report statistical tests comparing the distribution of event classes or Δz values between conditions. Include a control showing that a DNA-binding-competent but non-bridging protein (e.g., a monomeric DNA-binding domain) does not produce Class II-V events.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors conclude that the ΔN790 construct (residues 790-897) contains a monomeric DNA-binding domain, based on binding assays and the observation that it is monomeric by native mass spectrometry.
- **Evidence pointer** Results section "The CtIP ΔN variants bind to DNA but cannot tetramerise"; Figures 3B-F
- **Concern** The ΔN790 construct binds DNA with a Kd of 270 nM, which is only ~4-fold weaker than wild-type. However, the text notes that ΔN790 binding was measured by fluorescence quenching rather than anisotropy, and that the binding mode appears "qualitatively different" from other variants. The manuscript does not address whether this quenching effect could be due to non-specific aggregation or a different binding mode (e.g., binding to the Cy5 fluorophore rather than the DNA). The authors also do not discuss whether the 63 Da mass excess observed by native MS (consistent with zinc binding) could affect the DNA binding properties.
- **Why it matters** The identification of a minimal C-terminal DNA-binding domain is a key finding of the paper. If the ΔN790 binding measurement is confounded by artifacts (e.g., fluorophore binding, aggregation), the conclusion that this region constitutes a bona fide DNA-binding domain is not secure.
- **Resolution test** Perform additional characterization of ΔN790 binding, such as competition experiments with unlabeled DNA, binding to a substrate lacking the Cy5 label, or a different binding assay (e.g., electrophoretic mobility shift assay with a longer DNA substrate). Address whether zinc coordination is required for DNA binding by testing a zinc-binding mutant.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, "However, we show that binding alone is insufficient for DNA bridging, which also requires tetramerization via the N-terminal domain."
- **Issue** The abstract states that tetramerization is required for bridging, but the results show that ΔC782 (which retains the N-terminal tetramerization domain) has impaired bridging, and R100W (which tetramerizes normally) also has impaired bridging. This suggests that tetramerization is necessary but not sufficient for efficient bridging. The abstract could be more precise.
- **Required correction** Rephrase to indicate that tetramerization is necessary but not sufficient for efficient bridging, or that both DNA binding and tetramerization are required.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Native nanoESI-MS"
- **Evidence pointer** Methods section "Native nanoESI-MS"
- **Issue** The methods state that "Both EcN4 and InN4 were dialysed into 20 mM ammonium acetate solution." These protein names (EcN4 and InN4) are not defined anywhere in the manuscript and do not correspond to any construct described in the text or figures.
- **Required correction** Replace with the correct construct names (likely ΔN790 and possibly another variant) or define the abbreviations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "The CtIP disease variants tetramerise but cannot bind to DNA efficiently"
- **Evidence pointer** Figure 2B and accompanying text
- **Issue** The SEC-MALS data for the disease variants report molecular masses of 338, 262, and 376 kDa for ΔC782, ΔC608, and R100W respectively. The text states these are "close to the expected values of 352, 272 and 404 for tetramers in all cases." The deviation for R100W (376 vs. 404, ~7% error) is not discussed. Is this within the expected accuracy of SEC-MALS?
- **Required correction** Briefly comment on the accuracy of SEC-MALS mass determination and whether the R100W deviation is within experimental error.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Non-specific CtIP-DNA interactions underpin rapid and processive 1D diffusion"
- **Evidence pointer** Figure 6F and accompanying text
- **Issue** The diffusion constant is reported as D = 3.9 ± 0.2 µm² s⁻¹ (mean ± SEM). The number of trajectories (115) is stated, but the distribution of diffusion constants is not shown. It would be helpful to know if the population is homogeneous or if there are subpopulations with different mobilities.
- **Required correction** Show the distribution of diffusion constants (e.g., as a histogram) or state that the population was homogeneous.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion, "A construct with the final 397 amino acids of the protein (ΔN500) has the same DNA binding affinity as wild type"
- **Issue** The text states ΔN500 has "the same DNA binding affinity as wild type" but the Kd values reported are 45 nM and 33 nM for the two SEC peaks, compared to 37-66 nM for wild-type. These are not necessarily "the same" without statistical comparison.
- **Required correction** Soften the language to "comparable affinity" or provide statistical evidence of equivalence.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Optical Tweezers and Confocal Microscopy Assay"
- **Evidence pointer** Methods section "Optical Tweezers and Confocal Microscopy Assay"
- **Issue** The methods state that "DNA molecules were never exposed to intercalating dyes or UV radiation during their production." This is good practice but the rationale is not stated. It would be helpful to note that this avoids DNA damage that could affect CtIP binding.
- **Required correction** Add a brief rationale for this choice.

## Risk / unsupported claims
- The claim that "efficient bridging requires both the DNA binding and tetramerization activities of CtIP" is supported by the data but the statistical basis for comparing bridging efficiency across variants is not fully reported.
- The claim that ΔN790 contains a "monomeric DNA-binding domain" is supported by binding and mass spectrometry data, but the potential for artifacts in the fluorescence quenching assay is not fully addressed.
- The statement that "dephosphorylated CtIP (λ-CtIP) was more effective in bridging DNA molecules than untreated WT-CtIP" is presented without quantitative comparison or statistical analysis in the current manuscript (the authors reference previous work for the tighter binding affinity).
- The discussion of the "RHR motif" and its role in DNA binding is based on previous work and the current data with ΔN790 R839A, but the manuscript does not show direct evidence that R839 is the critical residue within the context of full-length CtIP.
- The claim that disease variants "display impaired DNA binding and bridging activities" is supported for ΔC782 and ΔC608, but the R100W variant shows only a modest (~2-fold) reduction in binding affinity, and the text does not discuss whether this is likely to be physiologically significant.