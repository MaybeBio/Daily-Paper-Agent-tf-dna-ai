## Review setup
- **Input scope** Full manuscript text, including abstract, results, discussion, experimental procedures, and supporting information references
- **Assessment boundary** Scientific validity of the claims as presented in the provided manuscript; no assessment of editorial fit or journal policy
- **Shared manuscript claim summary** The authors propose that two positively charged surface loops (α1-α2 and β1-β2 K-rich loops) unique to human NAMPT mediate its interaction with TLR4, and that mutations in these loops impair TLR4 binding and downstream NF-κB signaling, with docking simulations supporting the interaction model
- **Visible evidence base** Bioinformatic sequence analysis (Fig. 1), electrostatic surface comparisons (Fig. 2), structural models (Fig. 3), kinetic characterization (Table 1, Figs. S1–S5), surface plasmon resonance binding studies (Fig. 4, Table 2), cellular NF-κB signaling assays (Fig. 5, Figs. S6–S8), and molecular docking (Fig. 6, Table S1)
- **Missing materials affecting confidence** Raw SPR sensorgrams for individual mutants, full Western blot images, statistical details for docking scores, and the complete multiple sequence alignment (only a section shown in Fig. 1)

## Reviewer
- **Overall assessment** This manuscript presents a systematic and largely well-executed investigation into the molecular determinants of the NAMPT-TLR4 interaction. The combination of bioinformatic analysis, site-directed mutagenesis, kinetic characterization, SPR binding studies, cellular assays, and docking simulations provides a multi-pronged approach that is commendable. However, several technical concerns regarding the interpretation of SPR data, the statistical treatment of cellular assays, and the robustness of the docking conclusions need to be addressed before the central claims can be fully established. The work is of interest to the inflammation and innate immunity communities, and the identification of specific loop regions as interaction hotspots has translational potential. Nevertheless, the current evidence base, while suggestive, does not yet conclusively demonstrate that these loops are the sole or primary determinants of the NAMPT-TLR4 interaction in a physiological context.

- **Who would be interested in the results, and why** Researchers studying eNAMPT biology, TLR4 signaling, damage-associated molecular patterns (DAMPs), and inflammatory disorders would find this work relevant. The identification of specific structural elements mediating the NAMPT-TLR4 interaction offers potential targets for therapeutic intervention in inflammatory diseases where eNAMPT has been implicated. Additionally, the methodological approach combining computational and experimental techniques may interest structural biologists and those studying protein-protein interactions.

- **Major strengths**
  1. The study addresses a significant gap in understanding the molecular basis of eNAMPT's cytokine-like activity, which has been a subject of considerable interest in the field.
  2. The integrated approach using multiple complementary techniques (bioinformatics, mutagenesis, SPR, cellular assays, docking) strengthens the overall conclusions.
  3. The identification of evolutionarily acquired loops in human NAMPT provides a compelling evolutionary perspective on the acquisition of signaling function.
  4. The careful characterization of mutant proteins (oligomeric state, kinetic properties) before functional assays demonstrates methodological rigor.
  5. The inclusion of endotoxin contamination controls (HEK-Blue hTLR4 cells, ε-poly-L-lysine treatment) addresses a common pitfall in studies involving recombinant proteins and TLR4.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of binding data interpretation
- **Claim pointer** The authors claim that mutations in the α1-α2 loop "strongly decreased the association rate, increasing the KD value from 18 nM, as determined for the wildtype, to 1.3 μM" and that mutations in the β1-β2 loop "increased the dissociation rate, yielding KD values of 0.63 and 0.22 μM, respectively."
- **Evidence pointer** Table 2, Figure 4
- **Concern** The SPR experiments were performed with NAMPT concentrations in the range of 1 to 3 nM, yet the reported KD values for the wildtype (18 nM) and several mutants (20.8 nM, 37 nM) are substantially higher than the highest analyte concentration tested. This is a fundamental problem in SPR analysis. Reliable KD determination requires that analyte concentrations bracket the KD value, ideally spanning from approximately 0.1x to 10x the expected KD. With a maximum concentration of 3 nM, the sensor surface would be far from saturation at equilibrium for a KD of 18 nM, making the kinetic and affinity parameters poorly constrained. The authors do not report the maximum response units (Rmax) achieved or the fraction of surface saturation, which would help assess the reliability of the fits. Furthermore, the monoexponential fitting model is mentioned, but no details are provided on the goodness of fit, residuals, or whether a mass transport limitation model was considered. The lack of these critical details undermines confidence in the quantitative KD values reported.
- **Why it matters** The quantitative KD values are central to the claim that specific mutations differentially affect association versus dissociation rates, which in turn supports the mechanistic interpretation that distinct loops mediate different aspects of the binding interaction. If the KD values are unreliable due to experimental design limitations, the differential effects attributed to the α1-α2 versus β1-β2 loops may not be robust. This would weaken the central conclusion of the paper.
- **Resolution test** The authors should repeat SPR experiments with a wider concentration range (e.g., 1 nM to 5 μM) that brackets the reported KD values. Alternatively, they should provide a detailed justification for the concentration range used, including the expected surface capacity, achieved Rmax values, and a demonstration that the kinetic parameters are well-constrained. Global fitting with appropriate models (including mass transport) and reporting of residuals and confidence intervals would also strengthen the analysis.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Sufficiency of evidence for physiological relevance
- **Claim pointer** The authors state that "mutations impairing TLR4 binding in vitro also affect the NAMPT ability to prime signaling in human macrophages" and conclude that the identified loops are involved in the signaling function of the enzyme.
- **Evidence pointer** Figure 5, Figures S6–S7
- **Concern** The cellular assays were performed with only two mutants (α-loop triple mutant and β-loop full mutant) at a single concentration (100 ng/ml) and a single time point (20 min for p65 phosphorylation, 6 h for IL-8 expression). The dose-response experiment (Fig. S6) was used to select the optimal concentration for the wildtype protein, but it is not clear whether the same concentration is optimal for the mutants, which have different binding affinities. Moreover, the statistical analysis is described as a paired t-test, but the number of biological replicates is not explicitly stated (n = 5 is mentioned in the figure legend, but it is unclear if these are independent donors or technical replicates). The claim that mutations "impair" signaling would be strengthened by demonstrating a dose-dependent effect and by testing additional mutants, particularly the α-loop double mutant which showed minimal change in KD but might still affect signaling. Furthermore, the observation that mutant-treated cells showed decreased p65 phosphorylation compared to untreated cells is intriguing but not discussed; this could indicate residual agonist activity or experimental artifact.
- **Why it matters** The connection between in vitro binding affinity and cellular signaling is the key translational claim of the paper. If the cellular assays are not sufficiently robust or comprehensive, the conclusion that the identified loops are functionally relevant for eNAMPT's pro-inflammatory activity is not fully supported. This is particularly important given that the authors propose these loops as therapeutic targets.
- **Resolution test** The authors should provide dose-response curves for the mutants, include additional time points, and clearly state the number of independent biological replicates. Testing additional mutants (including the α-loop double mutant) would help establish a correlation between binding affinity and signaling potency. Ideally, a rescue experiment (e.g., using a chimeric protein with the loops grafted onto a non-signaling scaffold) would provide more definitive evidence for the causal role of these loops.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Robustness of docking conclusions
- **Claim pointer** The authors state that "the involvement of the two loops in receptor binding was supported by NAMPT-TLR4 docking simulations" and present a model showing the interaction interface.
- **Evidence pointer** Figure 6, Table S1
- **Concern** The docking methodology is described very briefly. The authors used ZDOCK for rigid-body docking, followed by minimization with the DISCOVER module. However, no details are provided on the number of docking poses generated, the scoring function used for pose selection, the criteria for selecting the "best pose," or the results of any clustering analysis. The binding affinity calculation is described as using "interfacial contacts and noninteracting surfaces," but the specific method is not referenced. More critically, the docking was performed between the NAMPT homodimer and a homology model of the TLR4 homodimer, and the quality of the TLR4 model is not assessed. The authors do not discuss whether the docking results are consistent with the mutagenesis data in a quantitative manner, nor do they address the possibility of alternative binding modes. The statement that the docking "confirms" the role of the loops is an overstatement given the limitations of the approach.
- **Why it matters** The docking simulations are presented as independent support for the experimental findings. If the docking methodology is not robust or the results are not critically evaluated, this support is weakened. Moreover, the proposed model of the NAMPT-TLR4 complex could be misleading if the docking was not performed and validated rigorously, potentially leading to incorrect hypotheses about the interaction interface for future therapeutic design.
- **Resolution test** The authors should provide more details on the docking protocol, including the number of poses generated, the scoring function, and the selection criteria. They should also perform cross-validation by docking the mutant NAMPT models and showing that the mutations disrupt the predicted interface. Ideally, the docking results should be compared with experimental data from other TLR4-ligand complexes to validate the approach. If the docking is intended to be illustrative rather than definitive, this should be stated explicitly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of kinetic data for the deleted mutant
- **Claim pointer** The authors describe the kinetic behavior of the β-loop deleted mutant as showing "biphasic Michaelis–Menten kinetics" and hypothesize that "the deleted mutant exists in two different assembled states with distinct kinetic properties."
- **Evidence pointer** Table 1, Figures S4–S5
- **Concern** The biphasic kinetics observed for the Δ(42>51) mutant is intriguing but the interpretation is speculative. The authors suggest multiple assembled states, but they did not perform any direct biophysical characterization (e.g., analytical ultracentrifugation, dynamic light scattering, or native mass spectrometry) to confirm this hypothesis. The concentration-dependent activity (Fig. S5) is consistent with a monomer-dimer equilibrium, but alternative explanations such as substrate-dependent conformational changes or aggregation effects are not excluded. The authors also do not discuss whether the biphasic kinetics could be an artifact of the assay system at high substrate concentrations. The lack of direct evidence for the proposed mechanism weakens this aspect of the study.
- **Why it matters** The biphasic kinetics of the deleted mutant is presented as evidence for the importance of the β1-β2 loop in maintaining proper protein assembly. If this interpretation is incorrect, the conclusion that the loop is required for structural integrity would be weakened. Moreover, the unusual kinetic behavior of this mutant could confound the interpretation of its reduced TLR4 binding, as the binding defects might be due to protein misfolding rather than loss of specific contact residues.
- **Resolution test** The authors should perform direct biophysical characterization of the deleted mutant to confirm the proposed assembly states. This could include size-exclusion chromatography coupled with multi-angle light scattering (SEC-MALS), analytical ultracentrifugation, or native mass spectrometry. Alternatively, they could perform the kinetic assays at different protein concentrations to determine if the biphasic behavior is concentration-dependent, which would support the assembly-state hypothesis.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The multiple sequence alignment shown in Figure 1 is described as a "section" of the full alignment, but the criteria for selecting this section are not stated. The shading and highlighting are described in the legend, but it is unclear which residues are highlighted in green (the "possible regions implicated in signaling") and how these were identified.
- **Required correction** The authors should clarify the selection criteria for the alignment section shown and provide a more detailed legend explaining the shading scheme. If the full alignment is available as a supplementary file, this should be indicated.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 5
- **Evidence pointer** Figure 5
- **Issue** The statistical analysis for the cellular assays is described as a paired t-test, but the exact p-values are not reported in the figure or legend. Only asterisks are shown. Additionally, it is unclear whether the data were tested for normality and whether multiple comparison corrections were applied.
- **Required correction** The authors should report exact p-values and describe the statistical tests used more fully, including any assumptions and corrections applied.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Experimental procedures, "Biosensor binding studies"
- **Evidence pointer** Experimental procedures
- **Issue** The SPR methods section does not specify the temperature at which binding experiments were performed (the text mentions the sensing chamber was thermostatted at 37 °C, but this is in the results section), the flow rate, the regeneration conditions, or whether the data were double-referenced. The concentration range tested is also not explicitly stated in the methods.
- **Required correction** The authors should provide a more complete description of the SPR experimental conditions, including the concentration range tested, flow rate, regeneration protocol, and data processing methods.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of docking
- **Affected element** Figure 6
- **Evidence pointer** Figure 6
- **Issue** The docking figure shows the NAMPT dimer interacting with TLR4, but the orientation and the specific residues involved are difficult to discern from the figure as described. The authors mention that the α1-α2 and β1-β2 loops are highlighted, but it is not clear from the figure legend how these are distinguished.
- **Required correction** The authors should provide a more detailed figure legend that clearly identifies the NAMPT loops involved in the interaction and the TLR4 residues they contact. A zoomed-in view of the interface would be helpful.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of the physiological relevance of the NAMPT-TLR4 interaction would benefit from a more thorough comparison with other reported TLR4-DAMP interactions. The authors mention fibronectin, hyaluronan, and tenascin C, but do not discuss whether the proposed binding mode for NAMPT is consistent with what is known about these other interactions.
- **Required correction** The authors should expand the discussion to place their findings in the broader context of TLR4-DAMP interactions, noting similarities and differences in binding modes and signaling mechanisms.

## Risk / unsupported claims
1. The claim that the α1-α2 and β1-β2 loops are "unique to the human enzyme" is not fully supported. The sequence alignment shows these loops are present in vertebrate NAMPTs, but the authors do not demonstrate that they are absent from all bacterial NAMPTs beyond the single example of AbNadV. The statement "unique to the human enzyme" in the Discussion overstates the evidence.
2. The claim that "mutations impairing TLR4 binding in vitro also affect the NAMPT ability to prime signaling" is only tested for two mutants at a single concentration. The correlation between binding affinity and signaling potency is not systematically established.
3. The statement that the docking simulations "confirm" the role of the loops in receptor binding is not supported by the level of detail provided. Docking results are hypothesis-generating, not confirmatory, without experimental validation.
4. The interpretation of the biphasic kinetics of the deleted mutant as evidence for "two different assembled states" is speculative without direct biophysical characterization.
5. The claim that the identified loops "might represent a promising therapeutic strategy" is presented without any discussion of the potential challenges or limitations of targeting these regions, such as the structural flexibility of the loops or potential off-target effects.