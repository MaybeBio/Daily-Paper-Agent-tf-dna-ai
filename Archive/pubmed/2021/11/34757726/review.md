## Review setup
- **Input scope** Full manuscript text including abstract, methods, results, discussion, and conclusions. Supplementary material referenced but not provided.
- **Assessment boundary** Evaluation is limited to the content presented in the supplied manuscript text. Claims are assessed for internal consistency, logical coherence, and alignment with the presented data and analyses. No external validation or replication of methods was performed.
- **Shared manuscript claim summary** The authors propose a parallel sequential kinetic model to analyze SpyCas9 cleavage of supercoiled plasmid DNA, yielding four rate constants that describe HNH- and RuvC-initiated pathways. They report that proline substitutions in the bridge helix (SpyCas92Pro) and DNA mismatches alter these rate constants, shifting pathway usage and producing distinct conformational energy landscapes in molecular dynamics simulations. The central claim is that the bridge helix coordinates HNH and RuvC activities to enable target DNA discrimination.
- **Visible evidence base** Kinetic time-course data for plasmid cleavage (Figures 2–4, Table 1), derived commitment fractions and nicked-to-linear efficacies (Table 2), primer extension assay results (SI Section S.9, Figures S13–S15, Table S4), MD simulation analyses including dynamic cross-correlation matrices (Figure 6, Figures S17–S19, Table S5), free-energy landscapes (Figure 7), and RMSD analyses (Figures S20–S21). Supplementary sections S.1–S.9 are referenced but not included in the provided material.
- **Missing materials affecting confidence** The full Supporting Information (SI Sections S.1–S.9, Figures S1–S21, Tables S1–S6) is not provided. This includes derivations of the kinetic model, statistical justification for model selection, details of the primer extension assay, MD simulation parameters, and additional validation data. Without these, the robustness of the model fitting, the statistical comparison between models, and the reproducibility of the MD results cannot be fully assessed.

## Reviewer

- **Overall assessment** This manuscript presents a valuable kinetic framework for dissecting the coordinated activities of Cas9 nuclease domains using a straightforward plasmid cleavage assay. The parallel sequential model is a logical extension of prior work and offers a practical tool for the community. The integration of kinetic measurements with MD simulations is commendable and provides mechanistic hypotheses. However, the manuscript has several weaknesses that temper enthusiasm. The kinetic model, while useful, relies on assumptions that are not fully validated, and the assignment of rate constants to specific pathways is not unequivocally resolved. The MD simulations, while suggestive, are limited in scope and timescale, and the connection between simulated conformational states and the measured rate constants remains largely qualitative. The writing is generally clear but could be tightened in places. Overall, the work is a solid contribution to the Cas9 enzymology field, but the strength of the conclusions is not fully matched by the evidence presented.
- **Who would be interested in the results, and why** Researchers studying CRISPR-Cas9 mechanism, particularly those interested in the enzymology of HNH and RuvC nuclease domains, the role of the bridge helix in catalytic coordination, and the molecular basis of off-target discrimination. The kinetic model may also be of interest to biochemists developing assays for engineered Cas9 variants with altered specificity. The MD simulation approach could appeal to computational biologists studying conformational dynamics of multi-domain nucleases.
- **Major strengths** The development of a parallel sequential kinetic model that leverages supercoiled plasmid substrates to independently track nicked and linear products is a practical and accessible approach. The model provides a quantitative framework for comparing pathway usage across protein variants and DNA substrates. The combination of kinetic assays with MD simulations is a strength, as it attempts to bridge macroscopic activity with microscopic conformational dynamics. The identification of a specific condition (SpyCas92Pro-MM5) where the TS pathway is completely shut down is a striking finding that highlights the interplay between the bridge helix and mismatch position.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The parallel sequential model yields four distinct rate constants (k1,HNH, k1,RuvC, k2,HNH, k2,RuvC) that describe the two pathways for DNA linearization.
- **Evidence pointer** Methods section "Determination of Rate Constants for the Parallel Sequential Reaction Model"; Results section "A Parallel Sequential Model Explicitly Delineates Coordination between SpyCas9 HNH and RuvC Nuclease Domains"; Table 1.
- **Concern** The model fitting relies on the assumption that the two pathways are independent and that the nicked intermediate is a homogeneous population. However, the authors acknowledge that the model cannot distinguish between TS-nicked and NTS-nicked species without additional assays. The primer extension assay (SI Section S.9) is introduced to address this, but the details and results of this assay are not provided in the main text. The assignment of the four rate constants to specific molecular events (HNH first vs RuvC first) is therefore not directly validated by the kinetic data alone. The authors state that the assignment is supported by single-nuclease experiments and the primer extension assay, but the latter is only described in the SI, which is not available for review. Without a clear demonstration that the model uniquely identifies the pathway-specific rate constants, the quantitative conclusions in Table 1 and Table 2 are not fully supported.
- **Why it matters** The central quantitative claims of the paper, including the relative usage of TS vs NTS pathways and the effects of mutations and mismatches on individual rate constants, depend on the correct assignment of the fitted parameters. If the model cannot distinguish the pathways, the biological conclusions about HNH/RuvC coordination are weakened.
- **Resolution test** Provide the full details and results of the primer extension assay in the main text or a clearly accessible SI. Show that the measured ratioTS/ratioNTS values are consistent with the model predictions for each condition. Additionally, perform a sensitivity analysis to demonstrate that the fitted rate constants are uniquely determined by the data and do not suffer from parameter correlation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The MD simulations reveal that the bridge helix and DNA mismatches modulate the conformational energy landscapes, with SpyCas92Pro-MM5 uniquely lacking a favorable HNH precatalytic state.
- **Evidence pointer** Results section "BH Substitutions Impact the Free-Energy Landscape and Conformational Shifts Based on the Type of DNA Substrate"; Figure 7; Figure 6; Table S5.
- **Concern** The MD simulations are based on a starting model (model-B) that was derived from a 1000 ns simulation of model-A, which itself was constructed from a previous simulation study and a crystal structure (5F9R) with missing regions manually added. The authors acknowledge the limitations of this approach, but the reliability of the resulting conformational landscapes is unclear. The free-energy landscapes are computed from only 400 ns of simulation per system, which may be insufficient to sample the relevant conformational space for a large multi-domain complex like Cas9. The claim that SpyCas92Pro-MM5 uniquely lacks a favorable HNH precatalytic state is based on a single simulation condition and may be sensitive to the initial model construction. The connection between the simulated conformational states and the experimentally measured rate constants is qualitative, and no quantitative correlation is established.
- **Why it matters** The MD simulations are used to provide a mechanistic explanation for the kinetic differences observed experimentally. If the simulations are not sufficiently converged or are biased by the starting model, the proposed mechanism may be unreliable.
- **Resolution test** Provide convergence checks for the MD simulations, such as block averaging or multiple independent runs. Validate the starting model against additional experimental structures if available. Consider enhanced sampling methods to more thoroughly explore the conformational landscape. Establish a quantitative link between the simulated populations of precatalytic states and the measured rate constants, or temper the claims accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The results indicate that the bridge helix enables target DNA discrimination through differential use of parallel pathways, with implications for engineering Cas9 variants with improved specificity.
- **Evidence pointer** Discussion section "BH Modulations in SpyCas9 Imparts Target DNA Selectivity by Impairing Both HNH and RuvC Activities"; Conclusions.
- **Concern** The claim that modulating the bridge helix is a promising strategy for enhancing Cas9 specificity is intriguing but is not directly tested in this study. The authors do not measure off-target cleavage or specificity ratios; they only measure cleavage of matched and mismatched plasmid substrates. The connection between the observed kinetic changes and actual editing specificity in cells is speculative. The study demonstrates that the bridge helix and mismatch position affect pathway usage, but whether this translates to improved discrimination in a biological context is not established.
- **Why it matters** The broader significance of the work, particularly for gene editing applications, rests on the claim that the bridge helix can be engineered to improve specificity. Without direct evidence of specificity changes, this claim remains a hypothesis.
- **Resolution test** Perform additional experiments measuring cleavage of a panel of off-target substrates or use a cellular assay to assess editing specificity of SpyCas92Pro compared to wild-type. Alternatively, clearly frame the specificity claim as a hypothesis for future work rather than a conclusion of this study.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract; Introduction, paragraphs 1–2.
- **Issue** The abstract and introduction assume familiarity with Cas9 domain nomenclature and the details of the cleavage mechanism. Terms such as "HNH," "RuvC," "bridge helix," and "R-loop" are used without brief definitions, which may limit accessibility for readers outside the CRISPR field.
- **Required correction** Provide brief definitions or context for these terms when first introduced, or add a short primer on Cas9 architecture in the introduction.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "Time Course Plasmid Cleavage Assay"
- **Evidence pointer** Methods, equations 1–3.
- **Issue** The equations for calculating cleavage activities are presented without clear definitions of the variables (e.g., what is "I" in the equations?). The text states "the '0' subscript represents values for the no enzyme control lane," but the meaning of the terms in the equations is not fully explained.
- **Required correction** Define all variables in the equations explicitly and provide a brief explanation of how the cleavage activities are derived from the measured intensities.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section "Determining the Physical Nature of the Rate Constants"
- **Evidence pointer** Results, paragraph 2; SI Sections S.5 and S.6.
- **Issue** The authors state that the kobs values from single-nuclease experiments support the k1,HNH > k1,RuvC assignment, but the logic is not fully explained in the main text. The reader is directed to the SI for details, which is not available.
- **Required correction** Summarize the key reasoning in the main text, even if the full derivation is in the SI. For example, explain how the kobs values for the D10A and H840A variants relate to the individual pathway rate constants.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Results section "BH Substitutions Impact the Free-Energy Landscape and Conformational Shifts Based on the Type of DNA Substrate"
- **Evidence pointer** Figure 7.
- **Issue** The description of the free-energy landscapes is dense and relies on the reader's familiarity with PCA-based analysis. The biological interpretation of the different energy basins is not immediately clear from the text alone.
- **Required correction** Add a brief explanation of what PCA and free-energy landscapes represent in this context, and clearly state what the differences between the landscapes imply for the cleavage mechanism.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "MD Simulation Software and Setup"
- **Evidence pointer** Methods, paragraph 2.
- **Issue** The description of the MD simulation protocol is brief. Key parameters such as the thermostat and barostat settings, the equilibration time, and the criteria for determining convergence are not specified.
- **Required correction** Provide additional details on the simulation protocol, including the specific algorithms and parameters used, to ensure reproducibility.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion section "The Parallel Sequential Model Provides a Facile Framework to Obtain Mechanistic Insights into the Disruption of SpyCas9 Cleavage Activity"
- **Evidence pointer** Discussion, paragraph 1.
- **Issue** The authors compare their model to prior studies by Gong et al. and Raper et al., but the discussion of how their model differs from or extends these prior works is brief. A more detailed comparison would help position the contribution.
- **Required correction** Expand the comparison to prior models, highlighting the specific advantages and limitations of the current approach.

## Risk / unsupported claims
- The claim that the bridge helix "enables target DNA discrimination" is not directly supported by the data, as no specificity measurements were performed. This is a reasonable hypothesis but is not established.
- The claim that the MD simulations reveal "distinct conformational energy landscapes" that explain the kinetic differences is based on limited sampling and a manually constructed starting model. The connection between the simulated states and the measured rate constants is qualitative and not quantitatively validated.
- The assignment of the four rate constants to specific molecular pathways (TS vs NTS) is not fully validated without the primer extension assay details, which are only in the SI.
- The statement that "RuvC is not completely dependent on HNH to initiate the first cut" is supported by the data, but the broader implication that this is a general feature of Cas9 mechanism is not tested beyond the specific conditions studied.
- The suggestion that "modulating the BH can be a promising strategy for the enhancement of specificity" is speculative and not tested in this work.