## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, and materials and methods. Supplementary figure and movie titles are referenced but their contents are not provided.
- **Assessment boundary** The assessment is limited to the scientific claims, methodology, and logical coherence as presented in the supplied text. The quality of the underlying experimental data (e.g., microscopy images, simulation trajectories) cannot be independently verified as the raw data files are not provided.
- **Shared manuscript claim summary** The manuscript claims that active, myosin-driven transport of ARF7/ARF19 condensates along the actin cytoskeleton enhances their condensation in plant cells. This is supported by experimental observations of condensate movement and size, and by coarse-grained simulations showing that applied forces lower the saturation concentration for phase separation and lead to aspherical dense phases that preferentially accumulate active molecules.
- **Visible evidence base** The evidence base consists of the manuscript text, including descriptions of experimental results (Figures 1, 2, and supplementary figures S1, S3, S4), simulation results (Figures 3, 4, and supplementary figure S2), and methodological details. The actual figures, supplementary movies, and raw data are not available for direct inspection.
- **Missing materials affecting confidence** The actual figures and supplementary movies are not provided, preventing direct verification of the reported microscopy data, image analysis, and simulation snapshots. The specific details of the image analysis algorithm (e.g., thresholding, tracking parameters) are described but the code is only referenced via a GitHub link. The statistical analysis of the experimental data (e.g., number of biological replicates, error bars) is not fully described in the provided text.

## Reviewer
- **Overall assessment** The manuscript presents a compelling and novel hypothesis that active transport, rather than purely passive diffusion, can drive and enhance biomolecular condensation. The combination of in vivo plant cell biology with coarse-grained simulations is a strong approach. The experimental data on condensate motility and the effect of myosin knockout are convincing in their description. The simulation results provide a plausible physical mechanism. However, the manuscript's central claim that active transport "enables" condensation is a strong one, and the evidence, while suggestive, may not fully exclude alternative explanations (e.g., changes in local concentration due to transport, or the actin network acting as a scaffold). The link between the simulation parameter (Fact) and the biological reality of myosin pulling on a condensate is not quantitatively established. The manuscript is well-written and will be of interest to a broad audience, but the strength of the conclusions should be tempered to match the evidence.
- **Who would be interested in the results, and why** This work will be of significant interest to researchers in the fields of cell biology, biophysics, and plant biology. Specifically, those studying biomolecular condensates, phase separation, cytoskeletal dynamics, and auxin signaling will find the results relevant. The demonstration that mechanical forces can modulate phase behavior is a conceptual advance that could have implications for understanding condensate formation in various contexts, including in animal cells. The work bridges a gap between cell biology and theoretical biophysics.
- **Major strengths**
    1.  The study addresses a fundamental and open question about the drivers of biomolecular condensation, moving beyond purely passive mechanisms.
    2.  The combination of in vivo experimental data (ARF condensate movement, myosin mutants) with in silico simulations (active polymer model) is powerful and provides a multi-scale perspective.
    3.  The simulation model is elegant and makes specific, testable predictions (e.g., lowering of csat, aspherical dense phases, partitioning of active molecules).
    4.  The manuscript is clearly written and the logical flow from observation to hypothesis to model is easy to follow.
- **Major Concerns**
    - **R1-M1**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Experimental evidence vs. claim
        - **Claim pointer** The manuscript claims that active transport "enables" protein condensation, implying it is a necessary or primary driver. The experimental evidence shows a correlation between movement and condensate size, but does not directly demonstrate that the force of movement is the cause of enhanced condensation.
        - **Evidence pointer** Results section, Figures 2E and 2H.
        - **Concern** The conclusion that active transport enhances condensation is primarily based on the observation that condensates are smaller when actin is disrupted (LatB) or myosin is knocked out (myo3KO). However, this could be an indirect effect. For example, the actin cytoskeleton could act as a scaffold that promotes condensate nucleation or stabilization, independent of active transport. Disrupting the actin network would then lead to smaller condensates without directly implicating the force of movement. The manuscript does not provide a control to distinguish between the physical force of transport and the passive scaffolding role of actin.
        - **Why it matters** The central thesis of the paper rests on the specific role of active force. If the effect is due to a passive scaffold, the conclusion that "motility enables condensation" is not supported. The distinction is crucial for the paper's conceptual contribution.
        - **Resolution test** The authors could perform experiments where the actin network is intact but myosin is inhibited (e.g., with 2,3-butanedione monoxime or a more specific inhibitor) and compare condensate size to the myo3KO and LatB treatments. If condensates are smaller with myosin inhibition but the actin network is intact, it would more directly implicate the force of transport. Alternatively, they could tether condensates to the actin network without allowing movement to see if size is affected.
    - **R1-M2**
        - **Severity** Major
        - **Blocking** No
        - **Axis** Model-to-biology translation
        - **Claim pointer** The manuscript states that the simulations show "applied forces drive the associations of macromolecules to enhance phase separation" and directly links this to the experimental observations.
        - **Evidence pointer** Results section, "Simulations show how motility enables phase separation", Figures 3D and 3E.
        - **Concern** The simulation applies a constant, directional force (Fact) to one bead of each polymer. The manuscript does not provide a quantitative link between this model parameter and the biological reality of a myosin motor pulling on a condensate. The magnitude of Fact is given in units of kBT/σ, but the equivalent force in picoNewtons, or how it relates to the force exerted by a myosin XI motor, is not discussed. Furthermore, the simulation models individual polymers, not pre-formed condensates being moved. The mechanism of force application (on a single bead vs. the whole condensate) may lead to different physical outcomes.
        - **Why it matters** Without a quantitative or conceptual link between the simulation's Fact and the biological system, the simulation remains a generic demonstration that force can enhance phase separation, rather than a model for the specific ARF system. This weakens the claim that the simulations explain the experimental observations.
        - **Resolution test** The authors should provide a more detailed discussion of the biological relevance of Fact. They could estimate the force exerted by myosin XI on a condensate and compare it to the simulation values. They could also perform simulations where the force is applied to a pre-formed condensate (a cluster of polymers) to better mimic the biological scenario.
    - **R1-M3**
        - **Severity** Major
        - **Blocking** No
        - **Axis** Alternative explanations
        - **Claim pointer** The manuscript proposes that the higher concentration of ARF19 in the nucleoplasm compared to the cytoplasm, despite the absence of nuclear condensates, is evidence for active cytoplasmic drivers.
        - **Evidence pointer** Results section, Figure 1C.
        - **Concern** The manuscript lists four possible explanations for the observed nucleocytoplasmic difference and chooses to pursue the one involving active cytoplasmic drivers. However, the other possibilities, particularly (iii) differential ligand binding and (iv) different solution conditions, are not experimentally addressed or ruled out. The discussion mentions these but does not provide any data to exclude them.
        - **Why it matters** The initial observation is a key motivation for the study. If the difference in condensate formation is due to, for example, a nuclear inhibitor or a cytoplasmic promoter that is not related to active transport, the focus on motility might be misplaced. The manuscript's narrative would be stronger if it could provide at least preliminary evidence against these alternatives.
        - **Resolution test** The authors could perform a simple experiment such as isolating nuclei and cytoplasm and measuring the saturation concentration of ARF19 in diluted extracts from each compartment. If the csat is similar, it would argue against (iv). They could also test the effect of adding nuclear or cytoplasmic extracts on the phase separation of purified ARF19 in vitro.
- **Minor Comments**
    - **R1-m1**
        - **Severity** Minor
        - **Axis** Clarity
        - **Affected element** Results section, Figure 2A
        - **Evidence pointer** "We observed a combination of trajectories, with a substantial fraction being defined by values of α greater than unity."
        - **Issue** The term "substantial fraction" is vague. The manuscript would be strengthened by providing the exact percentage of trajectories with α > 1 in wild-type cells.
        - **Required correction** Provide the specific percentage of active trajectories (e.g., "approximately 32% of trajectories were superdiffusive (α > 1) in wild-type cells").
    - **R1-m2**
        - **Severity** Minor
        - **Axis** Statistical reporting
        - **Affected element** Results section, Figures 2E and 2H
        - **Evidence pointer** "We find that short-term LatB treatment leads to condensates that are smaller in size when compared to the mock treatment."
        - **Issue** The text does not report the statistical significance of the size differences. It is unclear if the differences are significant and what test was used.
        - **Required correction** Add statistical details, such as p-values and the statistical test used, for the comparisons of condensate size between treatments.
    - **R1-m3**
        - **Severity** Minor
        - **Axis** Methodology
        - **Affected element** Materials and Methods, "Local MSD analysis"
        - **Evidence pointer** "We used the local MSD analysis to distinguish active versus passive condensate motions."
        - **Issue** The choice of a 12-time-step window for the local MSD analysis is not justified. The sensitivity of the results to this parameter is not discussed.
        - **Required correction** Provide a justification for the chosen time window or show that the results are robust to changes in this parameter.
    - **R1-m4**
        - **Severity** Minor
        - **Axis** Interpretation
        - **Affected element** Discussion section
        - **Evidence pointer** "The current thinking is that nonequilibrium considerations in live cells will have an impact on the material properties, aging, and compositions of condensates."
        - **Issue** This statement is a general reference to the literature. The manuscript could be strengthened by discussing how its specific findings on active transport might relate to these known nonequilibrium effects.
        - **Required correction** Briefly elaborate on how active transport might contribute to the aging or material properties of condensates, connecting the findings to the cited concepts.
- **Technical failings that need to be addressed before the case is established**
    - The lack of a direct experimental test to distinguish between the force of active transport and the passive scaffolding role of the actin cytoskeleton (R1-M1).
    - The absence of a quantitative link between the simulation's active force (Fact) and the biological forces exerted by myosin motors (R1-M2).
- **Assessment against Nature-style criteria**
    - **Originality** High. The concept of active transport as a direct driver of phase separation is a novel and significant departure from the standard view of passive, concentration-dependent condensation.
    - **Scientific importance** High. If the claims are fully substantiated, this work would have broad implications for understanding the physical principles governing condensate formation and function in all cells, not just plants.
    - **Interdisciplinary readership** High. The work bridges cell biology, biophysics, and plant biology, and the core concept will be of interest to a wide audience.
    - **Technical soundness** The experimental and simulation methodologies are, in principle, sound. However, the major concerns regarding the interpretation of the experimental data and the biological relevance of the simulation parameters need to be addressed to ensure the technical conclusions are robust.
    - **Readability for nonspecialists** The manuscript is well-written and the concepts are explained clearly. The abstract and introduction are accessible. The results and discussion sections are more technical but remain understandable for a scientifically literate reader.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is novel and important, and the combination of approaches is powerful. However, the central claim that active transport "enables" condensation is not fully established from the provided evidence. The authors must address the alternative explanation of a passive actin scaffold and provide a stronger link between their simulations and the biological system.

## Risk / unsupported claims
- The claim that active transport is the specific mechanism that "enables" condensation is not fully supported, as the experimental data cannot rule out a passive scaffolding role for the actin cytoskeleton.
- The quantitative relationship between the simulation's active force (Fact) and the force exerted by myosin motors in cells is not established, making the direct applicability of the simulation results to the biological system uncertain.
- The claim that the simulations show "applied forces drive the associations of macromolecules to enhance phase separation" is supported by the simulation data, but the extrapolation to the in vivo situation is not fully justified.
- The statement that the findings "might be directly relevant for a range of phase-separating systems in cells" is speculative and not directly supported by the data presented.