## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) for a Nature Communications submission.
- **Assessment boundary** Scientific validity of claims, technical soundness of methods, interpretation of results, and alignment with Nature-style criteria. Editorial decisions and author rebuttals are outside scope.
- **Shared manuscript claim summary** The authors report that chromosome folding in zebrafish embryos begins with the formation of "fountains" at enhancers upon zygotic genome activation (ZGA). They propose that fountains arise from facilitated cohesin loading at enhancers followed by two-sided but desynchronized loop extrusion, and that this process is causally linked to pioneer transcription factor activity. They extend observations to mouse cells and propose fountains as a general enhancer-associated chromosome organization feature.
- **Visible evidence base** Hi-C data from zebrafish embryos at multiple developmental stages (wild-type and mutant), ChIP-seq data (Rad21, histone marks, pioneer TFs), ATAC-seq data, Repli-seq data, polymer simulations, and published datasets from other species (medaka, Xenopus, mouse).
- **Missing materials affecting confidence** Supplementary figures, supplementary notes, supplementary datasets, and source data files are referenced but not provided. Detailed methods for Hi-C data processing, fountain calling thresholds, and simulation parameters are only partially described in the main text.

## Reviewer
- **Overall assessment** This manuscript presents a novel and potentially significant observation: the identification of "fountains" as early chromosome organization features emerging at enhancers upon ZGA. The combination of experimental Hi-C data, genetic perturbations, and polymer simulations provides a compelling framework. However, several technical concerns regarding the robustness of fountain detection, the specificity of the enhancer association, and the causal claims from knockout experiments need to be addressed before the central conclusions are fully established.
- **Who would be interested in the results, and why** Researchers in chromosome architecture, developmental biology, gene regulation, and epigenetics. The work bridges a gap between early embryonic chromatin state and the establishment of canonical TAD-based organization, and proposes a mechanistic role for enhancers in initiating chromosome folding. The potential generality across species (fish, frog, mouse) broadens its appeal.
- **Major strengths**
  1. Novel identification and systematic characterization of a distinct chromosome organization feature ("fountains") in a developmental context.
  2. Integration of multiple data types (Hi-C, ChIP-seq, ATAC-seq, Repli-seq) and species to support the findings.
  3. Use of genetic knockouts (pioneer TFs) to establish a causal link between enhancer activity and fountain formation.
  4. Development of a new computational tool (fontanka) for fountain detection, which may be useful to the community.
  5. Polymer simulations that provide a mechanistic model and generate testable predictions.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of fountain detection
- **Claim pointer** The authors claim to have systematically detected 1460 fountains at 5.3 hpf using their fontanka algorithm.
- **Evidence pointer** Results section "Fountains are transient structures emerging after ZGA", Figure 1, Supplementary Figure 1, Methods "Fountain calling with fontanka"
- **Concern** The robustness and specificity of the fontanka algorithm are not fully established. The method relies on a manually defined reference fountain matrix, which introduces potential bias. The thresholding steps (Li's method, Scharr score filtering) are described but their impact on the final call set is not quantified. It is unclear how many candidate peaks are removed at each step and whether the algorithm can distinguish fountains from other features like stripes or loops, especially at later developmental stages when TADs are present.
- **Why it matters** The central claim of the paper rests on the reliable identification of fountains. If the detection method is not robust or is biased toward certain genomic features, the subsequent analyses (enhancer enrichment, knockout effects) could be compromised.
- **Resolution test** Provide a detailed benchmark of fontanka, including precision/recall on simulated data with known fountain positions, comparison to other feature detection methods (e.g., insulation, domain calling), and a sensitivity analysis of the thresholding parameters. Show that the algorithm can distinguish fountains from stripes and loops in controlled settings.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal link between pioneer TFs and fountain formation
- **Claim pointer** The authors state that "Knockouts of pioneer transcription factors driving ZGA enhancers cause a specific loss of fountains, establishing a causal link between enhancer activation and fountain formation."
- **Evidence pointer** Results section "Pioneer factors establish open chromatin platforms for fountain formation", Figure 3
- **Concern** The causal claim is based on the observation that fountains are lost in MZtriple mutants. However, the analysis appears to be largely correlative: fountains that lose accessibility in mutants also lose their Hi-C signal. It is not clear whether the loss of fountains is a direct consequence of losing pioneer TF binding at those specific enhancers, or an indirect effect of global transcriptional shutdown and chromatin state changes. The authors do not show that restoring pioneer TF activity (e.g., by mRNA injection) rescues fountain formation at the same loci.
- **Why it matters** The paper proposes a specific mechanism: pioneer TFs open chromatin, which facilitates cohesin loading, which creates fountains. Without a direct test of this causality, alternative explanations (e.g., global chromatin compaction in mutants) remain plausible.
- **Resolution test** Perform rescue experiments where individual pioneer TFs are re-expressed in the MZtriple background and show that fountains reappear specifically at loci where those TFs bind. Alternatively, use a system where pioneer TF binding can be induced acutely (e.g., hormone-inducible) and monitor fountain formation in real time.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of simulation results
- **Claim pointer** The authors claim that "polymer simulations demonstrate that fountains may arise as sites of facilitated cohesin loading, requiring two-sided but desynchronized loop extrusion."
- **Evidence pointer** Results section "Fountain shape helps elucidate loop extrusion mechanism", Figure 5, Supplementary Figures 5-6
- **Concern** The simulations are used to argue for a specific mechanism, but the parameter space explored is limited. The authors test three desynchronization mechanisms (collisions, random barriers, internal switching) and find they can all produce fountains. This suggests the model is not strongly discriminating between mechanisms. Furthermore, the simulations do not include other known features of the early zebrafish nucleus, such as the absence of CTCF or the presence of active transcription, which could affect extrusion dynamics.
- **Why it matters** The mechanistic conclusion is a key part of the paper's significance. If the simulations cannot distinguish between different desynchronization mechanisms, the claim that fountains "require" desynchronized extrusion is weakened.
- **Resolution test** Design simulations that make distinct, testable predictions for each desynchronization mechanism (e.g., different fountain shapes at varying cohesin densities or barrier distributions). Validate these predictions against the experimental Hi-C data at different developmental stages or in mutant conditions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generality of the phenomenon
- **Claim pointer** The authors state that "fountains represent enhancer-specific elements of chromosome organization" and that "observations in multiple systems further support facilitated loading at enhancers as a widespread phenomenon."
- **Evidence pointer** Results sections "Fountains are enriched at enhancers" and "Cohesin-dependent fountain-like structures emerge at enhancers in mouse cells", Figure 6
- **Concern** The mouse cell data show fountain-like patterns at enhancers in pileups, but individual fountains are not detectable. The authors attribute this to masking by TADs, but this is not directly demonstrated. The claim of generality would be strengthened by showing fountain patterns in additional species or cell types where TADs are absent or weak, or by demonstrating that the pileup signal in mouse cells is specifically due to the same mechanism (facilitated loading) rather than a different process.
- **Why it matters** The paper argues for a general principle of chromosome organization. If the phenomenon is only clearly observed in zebrafish embryos, its broader relevance is less certain.
- **Resolution test** Analyze Hi-C data from additional organisms or conditions where TADs are reduced (e.g., after CTCF depletion in a different cell type, or in early embryos of other species) to see if individual fountains emerge. Alternatively, perform simulations of mouse-like conditions (with CTCF) to show that fountains are present but obscured.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** Introduction, Results
- **Evidence pointer** "Fountains are transient structures emerging after ZGA"
- **Issue** The term "fountain" is used to describe a Hi-C pattern, but its precise definition (e.g., in terms of contact enrichment relative to expected) is only given in the Methods. A reader may struggle to visualize what a fountain looks like from the text alone.
- **Required correction** Provide a clear, concise definition of a fountain in the Results section, possibly with a schematic in Figure 1, and explicitly state how it differs from other features like loops, stripes, and TADs.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results section "Fountains are enriched at enhancers"
- **Evidence pointer** Figure 2c
- **Concern** The enrichment analysis of regulatory elements at fountains uses a randomized control, but the details of the randomization (e.g., how many iterations, how genomic features are matched) are not fully described in the main text.
- **Required correction** Briefly describe the randomization procedure in the Results or Methods, and report the number of randomizations and the variability of the control.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Methods, Data Availability
- **Evidence pointer** "Source data" statement
- **Concern** The manuscript references several supplementary datasets and notes, but these are not provided for review. It is impossible to verify the claims about fountain lists, simulation parameters, and detailed analyses.
- **Required correction** Ensure all supplementary materials are available to reviewers and readers, and that the Data Availability statement clearly indicates where all data and code can be accessed.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure clarity
- **Affected element** Figure 3
- **Evidence pointer** Figure 3c-e
- **Concern** The figure is dense and the distinction between the three approaches (ATAC-seq groups, differential fountains, TF-specific effects) is not immediately clear from the figure alone.
- **Required correction** Consider splitting Figure 3 into multiple panels with clearer subheadings, or adding a schematic overview of the three approaches at the top of the figure.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion
- **Evidence pointer** "Discussion" section
- **Concern** The Discussion does not explicitly address the limitations of the study, such as the inability to detect individual fountains in mouse cells, the correlative nature of some analyses, or the assumptions in the simulations.
- **Required correction** Add a paragraph acknowledging these limitations and discussing how they might be addressed in future work.

## Risk / unsupported claims
- The claim that fountains are "hallmarks of chromosome organization emerging upon zygotic genome activation" is supported for zebrafish but the generality to other species is inferred from pileup analyses in mouse cells where individual fountains are not observed.
- The claim of a "causal link" between pioneer TFs and fountain formation is based on knockout experiments, but the directness of the causality (TF binding -> chromatin opening -> cohesin loading -> fountain) is not fully established.
- The statement that "fountains may arise as sites of facilitated cohesin loading" is presented as a conclusion from simulations, but the simulations cannot distinguish between several possible mechanisms of desynchronization.
- The claim that fountains are "distinct from known features of local chromosome folding" is supported by the data, but the relationship between fountains and other features like "dots" or "stripes" at later stages is not fully explored.
- The assertion that "observations in multiple systems further support facilitated loading at enhancers as a widespread phenomenon" is an extrapolation that goes beyond the direct evidence presented.