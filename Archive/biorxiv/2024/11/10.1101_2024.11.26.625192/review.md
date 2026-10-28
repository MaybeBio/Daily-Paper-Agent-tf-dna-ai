## Review setup

- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, materials and methods, and supplementary figure legends as provided.
- **Assessment boundary** The scientific claims, experimental design, data interpretation, and technical soundness of the presented work, based solely on the provided manuscript text.
- **Shared manuscript claim summary** The authors propose that ubiquitylation of DNA-protein crosslinks (DPCs) allosterically activates the SPRTN protease via a novel ubiquitin-binding interface at the back of its protease domain, thereby confining SPRTN's promiscuous proteolytic activity to crosslinked proteins and maintaining genome stability. This mechanism is reported to be critical for the residual function of Ruijs-Aalfs syndrome patient-derived SPRTN variants.
- **Visible evidence base** In vitro autocleavage assays with recombinant SPRTN variants; in vitro reconstituted DPC ubiquitylation using synthetic and enzymatic systems; ColabFold structure predictions; all-atom molecular dynamics simulations; NMR spectroscopy; cellular assays in HeLa and HAP1 cells; mass spectrometry-based ubiquitin linkage analysis; and complementation assays in conditional Sprtn knockout MEFs.
- **Missing materials affecting confidence** The manuscript text does not include the actual figures, figure legends, or supplementary figures referenced throughout. Quantitative data, statistical analyses, and exact experimental replicates are not fully described. NMR assignment details and MD simulation convergence criteria are only partially provided. The precise nature of the "activating DNA structure" used in NMR experiments is not specified.

## Reviewer

- **Overall assessment** This manuscript addresses a fundamental and long-standing question in the DPC repair field: how SPRTN achieves substrate specificity despite its promiscuous proteolytic activity. The authors present a compelling multi-disciplinary approach combining biochemistry, structural biology, biophysics, and cell biology. The central claim, that ubiquitin allosterically activates SPRTN through a novel interface, is well-supported by the in vitro data presented in the text. The connection to Ruijs-Aalfs syndrome patient variants is clinically relevant and adds significant translational importance. However, the absence of the actual figures and detailed quantitative data in the provided material limits a full assessment of the robustness of the evidence. The mechanistic model, while plausible, relies on computational predictions and NMR data that are described but not fully verifiable from the text alone. The cellular data, particularly regarding genome stability phenotypes, are described but their statistical power and reproducibility cannot be fully evaluated.

- **Who would be interested in the results, and why** Researchers in the fields of DNA repair, genome stability, ubiquitin signaling, and protease biology would find these results of high interest. The work provides a novel paradigm for how a protease can achieve substrate specificity through allosteric activation by a post-translational modification on the substrate itself. This concept could have broader implications for understanding other proteases and enzymes that need to act selectively on modified substrates. Clinically, the findings are relevant to researchers studying Ruijs-Aalfs syndrome and other premature aging disorders, as well as cancer biologists interested in liver cancer predisposition.

- **Major strengths**
  1. The study addresses a critical, unresolved question in the field with a clear and logical experimental strategy.
  2. The multi-disciplinary approach, combining biochemistry, computational biology, NMR, and cell biology, provides converging lines of evidence for the central claim.
  3. The identification of a novel ubiquitin-binding interface (USD) on SPRTN is a significant advance.
  4. The reconstitution of the full DPC repair pathway, including SUMOylation and ubiquitylation, is a technical achievement.
  5. The connection to patient-derived SPRTN variants provides direct clinical relevance and explains a previously enigmatic observation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that ubiquitin binding to the USD interface stabilizes an open, active conformation of SPRTN, based on MD simulations and NMR data.
- **Evidence pointer** Results section "Ubiquitin stimulates SPRTN's DNA-dependent protease activity by promoting an open conformation"; Figures 1F-N, 2A; Supplementary Figures S1H, S2, S3
- **Concern** The central mechanistic claim of an open-to-closed conformational equilibrium is based on computational predictions and NMR data that are described in the text but cannot be fully evaluated without the actual figures and detailed experimental parameters. The MD simulations are only 400 ns long, which may be insufficient to sample large-scale conformational transitions. The NMR data show line-broadening effects, but the text does not provide quantitative CSP values, assignment completeness, or evidence that the observed effects are specific to the USD interface rather than non-specific binding.
- **Why it matters** The conformational selection model is the core mechanistic explanation for how ubiquitin activates SPRTN. If this model is not robustly supported, the entire conceptual framework of the paper is weakened.
- **Resolution test** Provide the actual figures with quantitative CSP data, show that the MD simulations have converged, and demonstrate that the conformational change is specifically dependent on ubiquitin binding to the USD interface, for example through control experiments with ubiquitin mutants or SPRTN variants that disrupt the interface.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional relevance
- **Claim pointer** The authors claim that the USD interface is critical for SPRTN function in cells, particularly for the residual function of Ruijs-Aalfs syndrome patient variants.
- **Evidence pointer** Results section "Ubiquitin-dependent activation of SPRTN maintains genome stability in Ruijs-Aalfs syndrome"; Figures 5A, 6A-E; Supplementary Figures S6, S7
- **Concern** The cellular data are described in the text, but the actual figures are not provided. The text states that SPRTN ΔC -L99S causes growth defects, G2/M arrest, micronuclei, and chromatin bridges, but the magnitude of these effects, the statistical significance, and the number of independent experiments are not reported. Furthermore, the text does not clarify whether the L99S mutation affects SPRTN protein stability or expression levels, which could confound the interpretation of the cellular phenotypes.
- **Why it matters** The cellular data are essential to translate the biochemical findings into a physiological context. Without robust quantitative data, the claim that the USD is critical for genome stability in patients cannot be firmly established.
- **Resolution test** Provide the actual figures with quantitative data, including statistical analyses, and include control experiments showing that the L99S mutation does not affect SPRTN protein stability, localization, or expression levels.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic specificity
- **Claim pointer** The authors claim that ubiquitin chain length and linkage type do not matter for SPRTN activation, and that the effect is independent of SPRTN's known ubiquitin-binding domains.
- **Evidence pointer** Results section "Ubiquitin chains are particularly potent at SPRTN activation"; Figures 3A-F, S4
- **Concern** The text states that all tetra-ubiquitin chains (M1, K48, K63) stimulate SPRTN activity, and that longer chains are more potent. However, the text does not provide a clear mechanistic explanation for why chain length matters if the activation is purely allosteric through the USD. The authors suggest that the USD interaction is too weak to withstand pulldown washing steps, but this is not directly demonstrated. The potential role of avidity effects in chain-length-dependent activation is not discussed.
- **Why it matters** Understanding the quantitative relationship between ubiquitin chain length and SPRTN activation is important for a complete mechanistic model. The current description leaves ambiguity about whether the effect is truly allosteric or whether it involves additional binding events.
- **Resolution test** Provide a more detailed analysis of the chain-length dependence, including dose-response curves and binding affinity measurements, and discuss the potential role of avidity in the activation mechanism.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, "We discover that DPC ubiquitylation strongly activates SPRTN independently of SPRTN's known ubiquitin-binding domains."
- **Issue** The abstract states that DPC ubiquitylation activates SPRTN, but the text later shows that free ubiquitin chains also activate SPRTN. The abstract could be clearer about whether the activation is specific to ubiquitylated DPCs or a general effect of ubiquitin chains.
- **Required correction** Clarify in the abstract that ubiquitin chains, whether free or conjugated to DPCs, activate SPRTN through the USD interface.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods, NMR spectroscopy
- **Evidence pointer** Methods section "NMR spectroscopy"
- **Issue** The text mentions the use of an "activating DNA structure" in NMR experiments but does not specify the exact DNA sequence or structure used. This is important for reproducibility.
- **Required correction** Provide the exact DNA sequence and structure used in the NMR experiments.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results, Figure 4
- **Evidence pointer** Results section "Ubiquitylation of DNA-protein crosslinks promotes their cleavage by SPRTN"; Figure 4A
- **Issue** The text describes the appearance of "additional smaller cleavage products (cleaved DPC*)" in the presence of ubiquitin chains. The nature of these products is not discussed, and it is unclear whether they represent alternative cleavage sites or processive degradation.
- **Required correction** Provide a brief discussion of the nature of the additional cleavage products and whether they are relevant to the physiological function of SPRTN.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, "triple-lock" model
- **Evidence pointer** Discussion section, "triple-lock" model
- **Issue** The "triple-lock" model is described as "partially speculative," which is appropriate, but the text could more clearly delineate which aspects are directly supported by data and which are speculative.
- **Required correction** Clearly distinguish between data-supported conclusions and speculative elements of the model.

## Risk / unsupported claims

- The claim that ubiquitin binding to the USD stabilizes an open conformation of SPRTN is based on computational predictions and NMR data that cannot be fully evaluated from the provided text without the actual figures and quantitative data.
- The claim that the USD is critical for genome stability in Ruijs-Aalfs syndrome patients is supported by cellular data, but the quantitative details and statistical analyses are not provided in the text.
- The statement that "SPRTN activation is coupled to the modification of the crosslinked protein" is a strong conclusion that is supported by the in vitro data but may require further in vivo validation to be fully established.
- The "triple-lock" model is presented as a unifying framework but is acknowledged as partially speculative; the relative contributions of each proposed mechanism are not quantitatively assessed.