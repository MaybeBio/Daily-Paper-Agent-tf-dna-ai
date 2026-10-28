## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report the design of novel dimeric molecular tweezers with functional linkers that bind the DNA-binding fragment of histone H4 with nanomolar affinity, show selectivity over other lysine-containing H4 regions, disrupt histone-DNA interactions, and impair histone acetyltransferase (HAT) activity in a competitive assay, thereby acting as a supramolecular posttranslational modification on a histone H4 peptide.
- **Visible evidence base** Fluorescence titrations, isothermal titration calorimetry (ITC), molecular dynamics (MD) simulations, fluorescence anisotropy assay, competitive enzymatic HAT experiment
- **Missing materials affecting confidence** Full manuscript text, experimental methods, all figures and tables, compound synthesis and characterization data, statistical analyses, raw titration and ITC data, MD simulation parameters and convergence criteria, assay conditions and controls, and any supplementary information

## Reviewer

- **Overall assessment** The abstract presents a conceptually interesting approach to modulating epigenetic control through supramolecular chemistry. The idea of replacing enzymatic acetylation with noncovalent lysine inclusion by molecular tweezers is creative and potentially impactful. However, the evidence as summarized is insufficient to fully evaluate the robustness of the claims. Key quantitative details, control experiments, and methodological rigor are not visible from the abstract alone. The work may be of interest to the supramolecular chemistry and epigenetics communities, but the case for a broad interdisciplinary advance is not yet established from the provided material.
- **Who would be interested in the results, and why** Researchers in supramolecular chemistry, chemical biology, and epigenetics would be interested. The concept of using designed molecular tweezers to mimic or interfere with posttranslational modifications offers a new tool for studying histone-DNA interactions and potentially for modulating epigenetic processes. The design principles for dimeric tweezers with functional linkers may also appeal to those working on molecular recognition of protein surfaces.
- **Major strengths** The conceptual novelty of using supramolecular tweezers as a synthetic surrogate for enzymatic acetylation is a clear strength. The combination of experimental binding assays (fluorescence titrations, ITC) with MD simulations provides a multi-pronged approach to characterize the interaction. The demonstration of functional outcomes, namely disruption of histone-DNA interaction and impairment of HAT activity, moves beyond simple binding measurements and strengthens the potential biological relevance.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The tweezers exhibit nanomolar affinity to the DNA-binding fragment of histone H4 and high selectivity over other lysine-containing H4 areas.
  - **Evidence pointer** Fluorescence titrations and ITC measurements, location not provided
  - **Concern** The abstract states nanomolar affinity and high selectivity but provides no numerical values, no comparison of affinities across different H4 fragments, and no details on the number of replicates or error margins. Selectivity is a relative claim that requires a defined panel of competing lysine-containing peptides or protein regions, and the abstract does not specify how many or which regions were tested.
  - **Why it matters** Affinity and selectivity are the foundational claims on which all downstream functional results depend. Without quantitative data and a clear selectivity panel, the reader cannot assess whether the tweezers are genuinely selective or whether the observed functional effects could arise from promiscuous binding.
  - **Resolution test** Provide dissociation constants (Kd) with standard errors for the target H4 fragment and for each tested competitor. Specify the number and identity of competitor peptides or regions, and show a selectivity ratio or similar metric.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The most powerful tweezers with high H4 affinity successfully competed for lysine binding sites and impaired HAT function.
  - **Evidence pointer** Competitive enzymatic HAT experiment, location not provided
  - **Concern** The abstract reports that the tweezers impaired HAT function but does not provide the magnitude of inhibition, the concentration range tested, the specific HAT enzyme used, or whether the effect was dose-dependent. It is also unclear whether the impairment was due to direct competition for the lysine substrate or to non-specific enzyme inhibition or aggregation effects.
  - **Why it matters** The claim of functional interference with an epigenetic enzyme is central to the paper's significance. Without dose-response data and appropriate controls (e.g., a negative control tweezer with no H4 affinity, or a control peptide), the mechanism of HAT impairment cannot be distinguished from non-specific effects.
  - **Resolution test** Show a dose-response curve for HAT activity versus tweezer concentration, include a negative control compound, and report the IC50 or percentage inhibition with statistical significance. Also confirm that the tweezers do not inhibit HAT in the absence of the H4 substrate.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** MD simulations identified new binding motifs involving attractive interactions between H4 residues and linker functionalities.
  - **Evidence pointer** MD simulations, location not provided
  - **Concern** The abstract does not describe the simulation protocol, force field, simulation length, or how convergence was assessed. The claim of "new binding motifs" is qualitative and cannot be evaluated without structural details or free energy calculations.
  - **Why it matters** The MD simulations are used to rationalize the experimental binding preferences and to propose a structural basis for the linker effects. If the simulations are not robustly converged or if the binding motifs are not validated by experimental mutagenesis or structural data, the mechanistic interpretation remains speculative.
  - **Resolution test** Provide simulation details in the full text, including force field, water model, simulation time, and convergence criteria. If possible, validate the proposed binding motifs with mutagenesis experiments or compare with experimental binding data for linker variants.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Terminology
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The phrase "supramolecular PTM" is used to describe the action of the tweezers. This is an evocative term but may be misleading, as a PTM typically involves a covalent modification. The tweezers act noncovalently, so the term should be clearly defined or qualified.
  - **Required correction** Define "supramolecular PTM" explicitly in the introduction or results, and clarify that it refers to a noncovalent mimicry of a PTM rather than a covalent modification.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Experimental scope
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The abstract focuses on a histone H4 peptide, not on full-length histone H4 or nucleosome context. The claim of relevance to "nucleosome-DNA interactions" is extrapolated from a peptide-based assay.
  - **Required correction** Acknowledge the peptide-based nature of the study in the abstract and discuss the potential limitations and next steps toward nucleosome-level experiments in the full text.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Compound characterization
  - **Evidence pointer** Location not provided
  - **Issue** The abstract does not mention the purity or characterization of the novel dimeric tweezers. For supramolecular systems, purity and aggregation state are critical for interpreting binding data.
  - **Required correction** Include characterization data (e.g., NMR, mass spectrometry, HPLC purity) and any evidence of monomeric behavior in solution in the full text.
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking because the core claims of selective high-affinity binding and functional HAT impairment are not quantitatively supported in the abstract. R1-M3 is non-blocking but requires additional detail to support the mechanistic interpretation.
- **Assessment against Nature-style criteria** Originality is high, as the concept of using molecular tweezers as a supramolecular mimic of histone acetylation is novel. Scientific importance is potentially significant for chemical biology and epigenetics, but the current evidence is preliminary and peptide-based. Interdisciplinary readership is plausible, but the abstract may not be accessible to non-specialists without clearer definitions of the tweezer design and the biological context. Technical soundness cannot be fully assessed from the abstract; the lack of quantitative data and controls is a concern. Readability for nonspecialists is moderate, but the abstract assumes familiarity with both supramolecular chemistry and epigenetics terminology.
- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual advance is promising, but the abstract does not provide sufficient evidence to establish the claims of selective nanomolar binding and functional HAT impairment. Full experimental details, quantitative data, and appropriate controls are required before the case can be considered established.

## Risk / unsupported claims

- The claim of "nanomolar affinity" is unsupported without numerical Kd values and error estimates.
- The claim of "high selectivity over other lysine-containing H4 areas" is unsupported without a defined selectivity panel and quantitative comparison.
- The claim that the tweezers "impaired HAT function" is unsupported without dose-response data, a specified HAT enzyme, and negative controls.
- The claim of "new binding motifs" from MD simulations is unsupported without simulation details or experimental validation.
- The relevance to "nucleosome-DNA interactions" is extrapolated from peptide-based assays and is not directly demonstrated.