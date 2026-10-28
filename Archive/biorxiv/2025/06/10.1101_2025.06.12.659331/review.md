## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods, supplementary figure legends referenced but not provided in full)
- **Assessment boundary** Scientific validity, technical soundness, and significance of the claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors present POGO-PANCE, a phage-assisted evolution platform that alternates positive and negative selection to evolve allosteric protein switches, and RAMPhaGE, a retron-based diversification method enabling insertions, deletions, and point mutations. Applied to AraC-LOV fusions, the system yields optogenetic switches with ~1,000-fold dynamic range. Long-read sequencing tracks evolutionary trajectories, and mechanistic analysis identifies linker mutations that enhance conformational coupling.
- **Visible evidence base** Main text figures referenced (Figs. 1-5), supplementary figures referenced (Supplementary Figs. 1-21), methods section, supplementary tables referenced
- **Missing materials affecting confidence** Supplementary figures and tables not provided; raw sequencing data not provided; detailed experimental protocols for selection stringency not fully described; flow cytometry gating strategy referenced but not shown

## Reviewer

- **Overall assessment** This manuscript describes a substantial technical advance in directed evolution of allosteric proteins. The combination of opposing selection pressures with retron-based diversification is conceptually novel and addresses a real gap in existing phage-assisted evolution platforms. The results are impressive, particularly the ~1,000-fold dynamic range achieved in AraC-LOV switches. However, several technical concerns need to be addressed to fully establish the claims, particularly regarding the mechanistic interpretation of linker mutations, the generalizability of the approach, and the robustness of the sequencing-based analyses.

- **Who would be interested in the results, and why** Researchers in protein engineering, synthetic biology, optogenetics, and directed evolution would find this work of high interest. The platform addresses a long-standing challenge in engineering allosteric proteins, which has broad applications in biotechnology, cell biology, and therapeutic protein design. The methodological advance of combining retron-based diversification with phage-assisted selection could also be adopted by groups working on other protein engineering problems.

- **Major strengths**
  1. The conceptual advance of applying opposing selection pressures to evolve switchable proteins is elegant and addresses a clear gap in existing directed evolution approaches.
  2. The development of RAMPhaGE as a retron-based diversification method that can introduce insertions and deletions is a significant technical contribution, as existing mutagenesis plasmids are limited to point mutations.
  3. The integration of long-read sequencing to track evolutionary trajectories provides a powerful analytical framework that goes beyond simple endpoint characterization.
  4. The achievement of ~1,000-fold dynamic range in optogenetic switches is a substantial improvement over existing AraC-LOV hybrids.
  5. The identification of convergent evolutionary solutions across independent pools strengthens the claim that the observed mutations are functionally relevant.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of mechanistic claims
- **Claim pointer** "Mechanistically, we found that linker mutations promoting α-helix extension at the sensor-effector junction enhance conformational coupling between LOV2 and AraC."
- **Evidence pointer** Figure 3, Figure 5, Supplementary Figures 7, 9, 17
- **Concern** The mechanistic claim that linker mutations promote α-helix extension is based primarily on AlphaFold3 structural predictions and mutational enrichment patterns. While the convergent evolution of specific linker mutations is suggestive, the manuscript does not provide direct experimental evidence (e.g., circular dichroism, NMR, or hydrogen-deuterium exchange) that these mutations actually alter secondary structure or conformational dynamics. The AlphaFold3 predictions are computational and may not accurately capture the dynamic behavior of a chimeric protein under selection conditions.
- **Why it matters** The mechanistic interpretation is central to the paper's claim of providing insight into allosteric networks. Without direct structural or biophysical validation, the α-helix extension mechanism remains speculative and could be an artifact of the prediction algorithm or a correlation without causal significance.
- **Resolution test** Provide experimental validation of the proposed mechanism, such as circular dichroism spectroscopy comparing wild-type and mutant linkers, or site-directed mutagenesis of the predicted helix-extension residues to test whether the phenotype is abolished. Alternatively, use hydrogen-deuterium exchange mass spectrometry to demonstrate altered conformational dynamics.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability of the platform
- **Claim pointer** "By coupling dynamic selection with deep mutational scanning and temporal sequencing, it enables both functional optimization and mechanistic insight into allosteric networks."
- **Evidence pointer** Main text, Discussion
- **Concern** The manuscript demonstrates the platform on a single protein system (AraC-LOV). The claim of generalizability to "allosteric networks" broadly is not supported by the data presented. The authors do not discuss potential limitations of the approach for other protein families, such as those with different oligomeric states, different allosteric mechanisms (e.g., conformational selection vs. induced fit), or those where the allosteric site is not amenable to domain insertion. The Discussion mentions future directions but does not critically assess the scope of applicability.
- **Why it matters** The significance of the work depends on its potential to be broadly applicable. If the platform only works for a narrow class of proteins, its impact is substantially reduced. The authors should provide a more balanced and critical assessment of the platform's limitations and the conditions under which it is likely to succeed or fail.
- **Resolution test** Add a section in the Discussion that critically evaluates the generalizability of the approach, including potential challenges for different protein classes. If possible, include preliminary data on a second protein system to demonstrate broader applicability.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor of selection stringency
- **Claim pointer** "POGO-PANCE alternates between temporally separated, mutually exclusive positive and negative selection steps, aligned with the presence or absence of an input signal."
- **Evidence pointer** Methods, Figure 3, Supplementary Tables 3-5
- **Concern** The manuscript describes the selection stringency as a critical parameter but does not provide a systematic analysis of how stringency affects evolutionary outcomes. The choice of IPTG concentration for negative selection (25 µM) and the duration of each selection step appear to be empirically determined, but the authors do not report how these parameters were optimized or whether the results are robust to variations in stringency. The Discussion mentions that "relatively permissive negative selection likely contributed" to suboptimal outcomes in some pools, but this is presented as a post-hoc explanation rather than a systematically explored variable.
- **Why it matters** For a platform to be useful to the community, the key parameters and their influence on outcomes need to be characterized. Without this, users cannot make informed decisions about how to apply the platform to their own systems, and the reproducibility of the results across laboratories may be compromised.
- **Resolution test** Provide a systematic analysis of how selection stringency (e.g., IPTG concentration, duration of negative selection) affects the trade-off between activity and switchability. This could be done through a parameter sweep or by comparing outcomes across different stringency conditions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical robustness of sequencing analyses
- **Claim pointer** "Long-read sequencing across selection cycles enabled high-resolution tracking of evolving variant pools, revealing adaptive trajectories and context-dependent residue interactions."
- **Evidence pointer** Figure 3, Supplementary Figures 8, 9, 20
- **Concern** The manuscript relies heavily on long-read sequencing to track evolutionary trajectories and identify co-occurring mutations. However, the authors do not report the sequencing depth, the number of biological replicates, or the statistical methods used to distinguish true enrichment from noise. The correction for systematic positional biases in Nanopore data is described, but the effectiveness of this correction is not quantitatively assessed. The co-occurrence analysis appears to be based on a limited number of reads, and the threshold for calling co-occurring mutations is not clearly defined.
- **Why it matters** The conclusions about adaptive trajectories and epistatic interactions depend on the reliability of the sequencing data. If the sequencing depth is insufficient or the analysis methods are not statistically robust, the identified "adaptive trajectories" could be artifacts of sampling noise or systematic errors.
- **Resolution test** Report sequencing depth and coverage statistics for each time point and replicate. Provide a statistical framework for identifying significant enrichment and co-occurrence, including false discovery rate control. Validate key findings with an independent method, such as Sanger sequencing of individual clones or targeted amplicon sequencing with higher depth.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Functional characterization of evolved switches
- **Claim pointer** "Through iterative evolution cycles, we obtained light-responsive AraC variants with nearly binary switch-like behavior and dynamic control spanning over three orders of magnitude."
- **Evidence pointer** Figure 4, Supplementary Figures 10, 17, 18
- **Concern** The functional characterization of the evolved switches appears to rely primarily on reporter assays (mRFP fluorescence) and flow cytometry. The manuscript does not report the absolute expression levels of the AraC-LOV variants, the protein stability, or the response kinetics. The "nearly binary" switch-like behavior is described qualitatively, but the quantitative criteria for this classification are not provided. The comparison with the BLADE system is useful but is performed under potentially different conditions.
- **Why it matters** For the evolved switches to be useful as tools, their performance characteristics need to be thoroughly characterized, including response kinetics, reversibility, and stability. The claim of "nearly binary" behavior needs quantitative support, such as Hill coefficients or threshold analysis.
- **Resolution test** Provide dose-response curves with fitted Hill coefficients for the best-performing variants. Report response kinetics (on/off rates) and reversibility over multiple light-dark cycles. Include protein stability data (e.g., half-life) for the evolved variants.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 3D
- **Evidence pointer** Figure 3D
- **Issue** The revision note indicates that Figure 3D was "revised and improved for clarity," but the current description of this panel is insufficient to understand what is being shown. The text refers to "temporal sequencing" and "adaptive trajectories" but does not clearly explain the visualization.
- **Required correction** Provide a more detailed figure legend for Figure 3D that explains the visualization method, the axes, and the interpretation of the data.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Flow cytometry gating strategy
- **Evidence pointer** Methods, Supplementary Figure 2
- **Issue** The gating strategy for flow cytometry is referenced but not described in the methods section. The criteria for identifying single cells and measuring fluorescence are not specified.
- **Required correction** Include a description of the gating strategy in the methods section or provide the gating strategy as a supplementary figure with detailed annotations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of control experiments
- **Affected element** Supplementary Figure 19
- **Evidence pointer** Supplementary Figure 19
- **Issue** The Discussion mentions "coding escape mutation" and "recombination-driven excision of the LOV domain" as failure modes, but the details of these events are not described. It is unclear whether these are common or rare events and whether they could be mitigated by design changes.
- **Required correction** Provide a more detailed analysis of the failure modes, including the frequency of LOV excision and the nature of escape mutations. Discuss potential strategies to mitigate these issues.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility of AlphaFold3 predictions
- **Affected element** Figure 3D, Supplementary Figure 21
- **Evidence pointer** Methods, Supplementary Figure 21
- **Issue** The AlphaFold3 predictions are used to support the mechanistic interpretation, but the specific model parameters, confidence metrics, and the version of AlphaFold3 used are not fully described. The pLDDT and PAE metrics are mentioned but not interpreted in the context of the structural claims.
- **Required correction** Provide the AlphaFold3 version and parameters used, and include a more detailed interpretation of the confidence metrics in the context of the structural predictions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Comparison with existing tools
- **Affected element** Supplementary Figure 10
- **Evidence pointer** Supplementary Figure 10
- **Issue** The comparison with the BLADE system is useful, but the conditions under which the comparison was performed are not fully described. It is unclear whether the comparison is fair in terms of expression levels, induction conditions, and measurement methods.
- **Required correction** Provide a detailed description of the conditions used for the BLADE comparison, including expression levels, light intensity, and measurement methods.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: The mechanistic claim of α-helix extension requires experimental validation beyond computational predictions.
  - R1-M2: The generalizability claim needs to be tempered or supported with additional data on a second protein system.
  - R1-M4: The sequencing analysis needs more rigorous statistical treatment and reporting of depth and replicates.

- **Assessment against Nature-style criteria**
  - **Originality**: High. The combination of opposing selection pressures with retron-based diversification is a novel approach that has not been previously described. The application to allosteric protein switches addresses a challenging and important problem.
  - **Scientific importance**: High. Allosteric regulation is a fundamental biological mechanism, and the ability to engineer allosteric proteins has broad implications for biotechnology and medicine. The platform could enable the creation of new tools for optogenetics and synthetic biology.
  - **Interdisciplinary readership**: Moderate to high. The work bridges protein engineering, directed evolution, synthetic biology, and structural biology. The methods and concepts are likely to be of interest to researchers in these fields, though the technical complexity may limit accessibility to a broader audience.
  - **Technical soundness**: Moderate. The core experimental approach is sound, and the results are impressive. However, the mechanistic interpretation relies heavily on computational predictions, and the sequencing analysis lacks the statistical rigor expected for high-impact publication. The lack of systematic parameter optimization for selection stringency is also a concern.
  - **Readability for nonspecialists**: Moderate. The manuscript is generally well-written, but the technical details of the directed evolution platform and the sequencing analysis may be challenging for readers outside the field. The abstract provides a clear summary, but the main text assumes significant background knowledge.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript describes a significant technical advance with impressive results. However, the mechanistic claims need experimental validation, the sequencing analysis needs more rigorous statistical treatment, and the generalizability claims need to be tempered. If these concerns are addressed, the work would be suitable for publication in a high-impact journal.

## Risk / unsupported claims
- The claim that linker mutations promote α-helix extension is not directly supported by experimental evidence and relies on computational predictions.
- The claim that the platform provides "mechanistic insight into allosteric networks" is overstated given the limited direct evidence for the proposed mechanism.
- The generalizability of the platform to other protein systems is not demonstrated and is presented as an assumption rather than a tested hypothesis.
- The claim of "nearly binary" switch-like behavior is not quantitatively supported.
- The effectiveness of the Nanopore sequencing bias correction is not quantitatively assessed, and the statistical significance of the identified adaptive trajectories is not established.