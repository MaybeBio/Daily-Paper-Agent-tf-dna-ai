## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific claims, methodology, and interpretation as presented in the provided manuscript
- **Shared manuscript claim summary** The authors propose that the shelterin protein TRF2 can drive both single-chain DNA compaction and multi-chain phase separation through multivalent interactions, and that the binding partner hRap1 modulates these processes, acting as a specificity switch. They support this with single-molecule force spectroscopy, turbidity assays, microscopy, and coarse-grained simulations.
- **Visible evidence base** Abstract, full results section, discussion, materials and methods, figure legends referenced in text
- **Missing materials affecting confidence** Figures and supplementary figures not provided; detailed numerical data (e.g., force-extension curves, turbidity values, FRAP recovery curves) not available; simulation parameter table (Table S8) not provided; statistical analysis details not provided

## Reviewer
- **Overall assessment** This manuscript addresses a timely and important question in telomere biology and biomolecular condensate research: whether the shelterin component TRF2 can drive nucleic acid condensation and phase separation, and how binding partners modulate this behavior. The combination of single-molecule force spectroscopy, turbidity assays, microscopy, and simulations is ambitious and potentially powerful. However, the manuscript as presented has several significant gaps that prevent full evaluation of the claims. The absence of actual figures and quantitative data makes it impossible to assess the robustness of the experimental results. The conceptual framework linking single-chain compaction to phase separation is interesting and well-motivated, but the evidence presented in the text alone is insufficient to establish the central claims. The authors should be commended for addressing a question of broad significance, but the current presentation does not yet provide a convincing case.

- **Who would be interested in the results, and why** Researchers in telomere biology, biomolecular condensates/phase separation, chromatin organization, and biophysics of protein-nucleic acid interactions would find these results of interest. The potential link between shelterin components and phase separation at telomeres has implications for understanding telomere organization, telomere dysfunction-induced foci, and ALT-associated PML bodies. The methodological approach combining single-molecule and bulk assays could also interest biophysicists studying protein-mediated nucleic acid condensation.

- **Major strengths** The manuscript addresses a significant and timely question with a multi-pronged experimental approach. The conceptual framework linking single-chain compaction and multi-chain phase separation as two outcomes of the same molecular interactions is well-articulated and theoretically motivated. The inclusion of hRap1 as a modulator adds biological relevance and provides a potential mechanism for specificity control. The use of coarse-grained simulations to complement experiments is a strength, as it allows for testing of mechanistic hypotheses.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that TRF2 promotes single-chain dsDNA condensation based on optical tweezer and magnetic tweezer experiments.
- **Evidence pointer** Results section "TRF2 promotes single-chain dsDNA condensation"; Figures 2A–G
- **Concern** The text describes dramatic compaction of λDNA in the presence of TRF2, but no quantitative data are provided. The force-extension curves, compaction rates, and the fraction of molecules showing compaction are not reported. The claim that compaction is "rapid and complete" is not supported by any numerical threshold or statistical comparison. The magnetic tweezer data are described as showing "a wide range of behaviors," which suggests heterogeneity that is not quantified or explained. The hysteresis between relaxation and pulling is mentioned but no quantitative measure (e.g., area of hysteresis loop, fraction of irreversible compaction) is given.
- **Why it matters** The central claim of the paper rests on the demonstration that TRF2 compacts individual DNA molecules. Without quantitative data, it is impossible to assess the magnitude, reproducibility, or force-dependence of this effect. The heterogeneity observed in magnetic tweezer experiments could indicate multiple mechanisms or artifacts, and this needs to be addressed.
- **Resolution test** Provide quantitative analysis of compaction: fraction of molecules compacted, degree of compaction (e.g., change in extension at a given force), kinetics of compaction, and statistical comparison between conditions. For magnetic tweezer data, provide histograms or distributions of compaction behavior and quantify the hysteresis.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that TRF2 drives phase separation with DNA, forming liquid-like droplets, based on turbidity assays and microscopy.
- **Evidence pointer** Results section "Interaction of TRF2 with multiple dsDNA molecules leads to phase separation"; Figures 4A–I, S3, S4, S5
- **Concern** The turbidity data are described as showing "classical re-entrant behavior," but no actual absorbance values, concentration ranges, or replicate numbers are provided. The microscopy images are described but not shown. The FRAP data are mentioned as indicating mobility, but no recovery curves, mobile fractions, or diffusion coefficients are given. The claim that droplets are "liquid-like" is based on qualitative observations of fusion and FRAP, but no quantitative criteria are provided. The distinction between phase separation and aggregation is not rigorously established.
- **Why it matters** The claim that TRF2 and DNA undergo bona fide liquid-liquid phase separation is a key finding. Without quantitative turbidity data, FRAP recovery curves, and clear evidence of liquid-like behavior (e.g., fusion events, spherical morphology, viscosity measurements), the interpretation remains speculative. The re-entrant phase behavior is an important observation that needs to be documented with actual data.
- **Resolution test** Provide turbidity titration curves with replicates and error bars, representative microscopy images with scale bars, FRAP recovery curves with fitted parameters (mobile fraction, half-time), and quantitative criteria for distinguishing liquid-like droplets from aggregates (e.g., fusion events, circularity, viscosity).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that hRap1 modulates TRF2-induced compaction and phase separation, acting as a specificity switch.
- **Evidence pointer** Results section "hRap1 modulates single DNA chain condensation and the phase-separation propensity of TRF2"; Figures 6A–G, 7B
- **Concern** The text states that hRap1 reduces compaction and shifts phase boundaries, but no quantitative data are provided. The claim that hRap1 abolishes phase separation with single-stranded nucleic acids is not supported by any numerical threshold or statistical test. The mechanism by which hRap1 exerts this effect (e.g., by reducing DNA binding affinity, by altering TRF2 conformation) is not directly tested. The statement that hRap1 has no effect on TRF2ΔC is mentioned but not shown with data.
- **Why it matters** The modulatory role of hRap1 is a central claim of the paper and has potential biological significance. Without quantitative data, it is impossible to assess the magnitude of the effect or the specificity of the modulation. The proposed mechanism of hRap1 as a "specificity switch" requires direct evidence that hRap1 differentially affects specific versus non-specific nucleic acid interactions.
- **Resolution test** Provide quantitative comparison of compaction and phase separation in the presence and absence of hRap1, with statistical analysis. Show that the effect is specific to hRap1-TRF2 interaction (e.g., using a mutant that cannot bind hRap1). Provide direct evidence for the mechanism, such as binding affinity measurements or structural studies.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors use coarse-grained simulations to support their experimental findings and to make predictions about the role of multivalency.
- **Evidence pointer** Results section "Coarse-grained simulations"; Figures 2H, 3B–D, 7C, S7, S10; Table S8
- **Concern** The simulation model is described only briefly. The mapping between simulation parameters and experimental conditions is not clearly established. The conversion from lattice units to nanometers and molar concentrations is presented as an estimate, but the sensitivity of the conclusions to this conversion is not discussed. The interaction parameters in Table S8 are not provided, making it impossible to evaluate the model. The claim that simulations recapitulate experimental observations is not supported by direct comparison of simulation and experimental data.
- **Why it matters** The simulations are used to support the interpretation of experimental results and to make mechanistic claims. Without a clear description of the model, parameter choices, and validation against experimental data, the simulation results cannot be evaluated. The conversion from simulation units to physical units is critical for comparing with experiments and needs to be justified.
- **Resolution test** Provide a detailed description of the simulation model, including interaction potentials, parameter values, and the rationale for parameter choices. Show direct comparison between simulation and experimental results (e.g., force-extension curves, phase boundaries). Discuss the sensitivity of conclusions to the unit conversion and parameter choices.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Biological relevance
- **Claim pointer** The authors suggest that their findings have implications for telomere organization and function in cells, including the formation of telomere-associated condensates.
- **Evidence pointer** Discussion section
- **Concern** The discussion extrapolates from in vitro experiments to cellular contexts without direct evidence. The concentrations used in the experiments (e.g., 10 μM TRF2) may not reflect cellular concentrations. The relevance of the findings to telomere biology, such as the formation of APBs or telomere clustering, is speculative. The authors do not discuss potential alternative explanations for their observations or address the limitations of the in vitro system.
- **Why it matters** The broader significance of the work depends on the relevance to cellular telomere biology. Without addressing the concentration regimes and potential cellular factors that could modulate the observed behavior, the claims about biological relevance are not well-supported.
- **Resolution test** Discuss the concentration regimes in the context of cellular concentrations of TRF2 and telomeric DNA. Consider potential regulatory mechanisms in cells that could modulate the observed interactions. If possible, provide preliminary evidence from cellular systems or discuss how the findings could be tested in cells.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that TRF2 "can condense individual DNA chains and drives coalescence of multiple DNA molecules, leading to phase separation and the formation of liquid-like droplets." This is a strong claim that is not fully supported by the data presented in the text, as quantitative evidence is lacking.
- **Required correction** Soften the language in the abstract to reflect the preliminary nature of the findings, or ensure that the main text provides sufficient quantitative support for these claims.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Materials and Methods
- **Evidence pointer** Materials and Methods, "Turbidity experiments"
- **Issue** The turbidity experiments are described as measuring absorbance at 340 nm, but no details are provided on the instrument settings, path length, or how the absorbance was converted to a measure of phase separation. The "re-entrant behavior" is described qualitatively.
- **Required correction** Provide detailed experimental conditions for turbidity measurements, including cuvette path length, wavelength verification, and the range of concentrations tested. Describe how the phase boundary was determined from the absorbance data.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "TRF2 promotes single-chain dsDNA condensation"
- **Evidence pointer** Results section, Figure 2
- **Issue** The description of the optical tweezer experiments is unclear regarding the experimental protocol. It is not clear how the "drag force" was varied and how the compaction was measured. The statement that "the free bead was eventually brought all the way into the active trap, thus ending the experiment" suggests that the compaction was so strong that the bead was pulled into the trap, but this is not explained.
- **Required correction** Clarify the experimental protocol for optical tweezer experiments, including how the drag force was controlled, how the DNA extension was measured, and what happened when the bead was pulled into the trap. Provide a schematic or detailed description of the setup.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, "Coarse-grained simulations"
- **Evidence pointer** Results section, Figure 3
- **Issue** The description of the simulations is brief and lacks important details. The "hyper coarse-grained model" is not described in sufficient detail to understand what is being simulated. The statement that "simulations sample from the underlying Boltzmann-weighted conformational ensemble" is vague.
- **Required correction** Provide a more detailed description of the simulation model, including the representation of DNA and protein, the interaction potentials, and the simulation protocol. Clarify what is meant by "Boltzmann-weighted conformational ensemble" in this context.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion introduces the concept of "pre-wetting demixing" and references a figure (Figure S9) without explaining this concept in the main text. This may be confusing for readers not familiar with this phenomenon.
- **Required correction** Provide a brief explanation of "pre-wetting demixing" in the main text or refer the reader to the supplementary information for a more detailed discussion.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Materials and Methods, "Fluorescence and Differential Interference Contrast (DIC) microscopy"
- **Evidence pointer** Materials and Methods
- **Issue** The FRAP analysis is described as being presented in the Supporting Information, but the details of the analysis (e.g., how the mobile fraction was calculated, how diffusion times were determined) are not provided in the main text.
- **Required correction** Provide a summary of the FRAP analysis method in the main text or ensure that the Supporting Information contains sufficient detail for reproducibility.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "Specificity and multi-valency of telomeric repeats"
- **Evidence pointer** Results section, Figure 4E
- **Issue** The text states that "phase separation occurs only in the presence of telomeric repeats" for the 24 bp DNA substrate, but the data are not shown. It is unclear what concentration of protein was used and whether the control (mix sequence) was tested at the same concentrations.
- **Required correction** Provide the actual data for this experiment, including the protein concentration used and the results for both telomeric and control DNA.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, "hRap1 modulates single DNA chain condensation and the phase-separation propensity of TRF2"
- **Evidence pointer** Results section, Figure 6
- **Issue** The text states that hRap1 "abolishes" phase separation with single-stranded nucleic acids, but the data are not shown. The term "abolishes" is strong and should be supported by quantitative evidence.
- **Required correction** Provide the data showing the effect of hRap1 on phase separation with single-stranded nucleic acids, including the concentration range tested and the threshold for "abolishment."

## Risk / unsupported claims
- The claim that TRF2 promotes single-chain dsDNA condensation is not quantitatively supported in the provided text.
- The claim that TRF2 and DNA form liquid-like droplets through phase separation is not quantitatively supported.
- The claim that hRap1 acts as a "specificity switch" is not directly tested or quantitatively supported.
- The claim that simulations recapitulate experimental observations is not supported by direct comparison.
- The extrapolation of in vitro findings to cellular telomere biology is speculative and not supported by direct evidence.
- The statement that "individual telomeres form distinct globules of finite size" in the introduction is presented as fact but is not directly addressed by the experiments.
- The claim that "binding partners, such as other telomere components, can alter those interactions to promote single-chain DNA compaction over multiple-chain phase separation" is not directly tested for components other than hRap1.

## Assessment against Nature-style criteria
- **Originality** The manuscript addresses a question that has not been directly explored before: whether shelterin components can drive phase separation of telomeric DNA. The conceptual framework linking single-chain compaction and multi-chain phase separation is not entirely novel, as it is rooted in polymer physics theory, but its application to telomere biology is original.
- **Scientific importance** The findings have potential importance for understanding telomere organization and function, particularly in the context of telomere clustering and APB formation. However, the significance is diminished by the lack of quantitative evidence and the speculative nature of the cellular implications.
- **Interdisciplinary readership** The topic is of interest to researchers in telomere biology, phase separation, biophysics, and chromatin biology. The multi-method approach could attract readers from different disciplines.
- **Technical soundness** The combination of single-molecule force spectroscopy, turbidity, microscopy, and simulations is technically ambitious. However, the lack of quantitative data and detailed methods makes it impossible to assess the technical soundness of the experiments. The simulation model is not described in sufficient detail.
- **Readability for nonspecialists** The manuscript is generally well-written and accessible, but the lack of figures and quantitative data makes it difficult for nonspecialists to follow the arguments. The discussion of polymer physics concepts may be challenging for some readers.

## Recommendation posture
Currently not established from the provided evidence. The manuscript addresses an important question with a promising approach, but the lack of quantitative data and figures prevents evaluation of the central claims. The authors should provide the actual experimental data, including force-extension curves, turbidity titrations, microscopy images, and FRAP recovery curves, along with statistical analysis. The simulation model needs to be described in more detail and validated against experimental data. If these concerns are addressed, the manuscript could become a valuable contribution to the field.