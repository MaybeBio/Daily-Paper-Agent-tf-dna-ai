## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results and discussion, conclusion, and methods.
- **Assessment boundary** Scientific validity of the claims, methodological soundness, and consistency with the presented evidence. No assessment of editorial fit or journal-specific policy.
- **Shared manuscript claim summary** The authors use all-atom discrete molecular dynamics (DMD) simulations to propose that TDP-43 directly interacts with Aβ, promoting Aβ toxicity by stabilizing oligomeric states and kinetically delaying fibril maturation. They identify binding sites on the TDP-43 NTD (near the nuclear localization sequence), RRM1–2 (via electrostatic interactions), and the CTD (within the amyloidogenic core), and propose a steric capping mechanism for fibril growth inhibition.
- **Visible evidence base** Simulation data from DMD, including contact frequencies, secondary structure analyses, 2D PMFs, and trajectory classifications. Figures referenced: 1, 2, 3, 4, 5, 6, 7; supplementary figures S1–S13.
- **Missing materials affecting confidence** No experimental validation data (e.g., biophysical or cellular assays) are provided. The manuscript relies entirely on computational predictions. No raw simulation trajectories or force field parameters are provided for independent verification. The methods section lacks details on convergence criteria and error estimation for the PMFs.

## Reviewer
- **Overall assessment** The manuscript presents a comprehensive computational study of the Aβ–TDP-43 interaction, addressing a clinically relevant question with a systematic approach. The use of DMD to cover all TDP-43 domains is commendable, and the identification of specific binding interfaces provides testable hypotheses. However, the central claim that TDP-43 promotes Aβ toxicity by delaying fibril maturation is not directly supported by the simulation data, which only show binding and structural effects on monomers and a short fibril seed. The extrapolation from in silico observations to in vivo toxicity is speculative and requires experimental corroboration. The manuscript would benefit from a clearer distinction between simulation-derived findings and inferred biological consequences.
- **Who would be interested in the results, and why** Researchers studying protein–protein interactions in neurodegeneration, particularly those focused on Aβ aggregation, TDP-43 biology, and cross-seeding phenomena. Computational biophysicists interested in DMD methodology and its application to amyloid systems would also find the work relevant. The proposed mechanism of steric capping by TDP-43 on Aβ fibril ends could inform future experimental designs.
- **Major strengths** Systematic coverage of all TDP-43 domains; use of a clinically relevant Aβ40 fibril structure; identification of specific binding interfaces with residue-level detail; agreement with prior experimental observations regarding NTD importance and Aβ40 vs. Aβ42 differences; clear presentation of simulation methodology.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of direct toxicity evidence), R1-M2 (static constraints limiting mechanistic conclusions), R1-M3 (insufficient validation of the peptide array method).
- **Assessment against Nature-style criteria**  
  - **Originality** Moderate. The study is the first to computationally map Aβ–TDP-43 interactions across all domains, but the overall concept of TDP-43 influencing Aβ aggregation is not new.  
  - **Scientific importance** Moderate. The topic is clinically relevant, but the lack of experimental validation limits the impact.  
  - **Interdisciplinary readership** Limited. The work is primarily of interest to computational biophysicists and neurodegeneration researchers; the methods and results may not be accessible to a broader biological audience.  
  - **Technical soundness** Generally sound within the DMD framework, but several methodological choices (static constraints, implicit solvent) reduce confidence in the biological relevance of the findings.  
  - **Readability for nonspecialists** The manuscript is well-written but assumes familiarity with simulation techniques and amyloid biology; some sections may be dense for a general scientific audience.
- **Recommendation posture** Supportive if technical concerns are resolved and the authors temper the claims regarding toxicity. The computational findings are valuable as a hypothesis-generating study, but the current evidence does not establish the proposed mechanism of toxicity.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Claim-evidence alignment  
- **Claim pointer** The abstract and conclusion state that TDP-43 "promotes Aβ toxicity" and that the mechanism is "stabilizing the oligomeric state and kinetically delaying fibril maturation."  
- **Evidence pointer** Abstract; Conclusion; Results and Discussion sections on NTD and fibril seed simulations  
- **Concern** The simulations demonstrate binding and structural effects on Aβ monomers and a short fibril seed, but no direct measurement of toxicity is presented. The link between delayed fibril maturation and increased toxicity is inferred from literature, not from the data. The authors do not simulate or measure oligomer populations, membrane disruption, or any cellular readout.  
- **Why it matters** The central claim of the manuscript is that TDP-43 promotes toxicity. Without experimental or simulation-based evidence directly linking the observed binding to toxic outcomes, this claim is unsupported. The manuscript would be strengthened by either including toxicity-related simulations (e.g., oligomer stability or membrane interaction) or by explicitly framing the findings as a hypothesis for future experimental testing.  
- **Resolution test** The authors should either (a) provide simulation data on oligomeric species or membrane interactions that directly support a toxicity mechanism, or (b) revise the claims to state that the simulations suggest a potential mechanism that requires experimental validation.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological validity  
- **Claim pointer** The authors claim that the NTD "caps" the fibril elongation surface and thereby blocks monomer addition, based on simulations where the fibril seed was held static.  
- **Evidence pointer** Results and Discussion section "TDP-43 NTD strongly interacted with a short Aβ40 fibril seed"; Methods section "NTD & Aβ fibril seed Molecular System"  
- **Concern** The fibril seed was held static in the simulations, which prevents any conformational rearrangement of the fibril upon TDP-43 binding. This constraint may artificially stabilize the bound state and does not allow for the possibility that the fibril could accommodate or displace the bound protein. The claim of steric capping is therefore based on a restricted model that may not reflect the dynamic nature of fibril ends.  
- **Why it matters** The proposed mechanism of inhibition relies on the steric block being effective under physiological conditions. A static fibril model cannot capture the dynamic fluctuations of fibril ends, which are known to be important for monomer addition. The conclusion may be an artifact of the simulation setup.  
- **Resolution test** The authors should either (a) perform simulations with a flexible fibril seed to test whether the capping interaction is maintained, or (b) acknowledge this limitation and temper the claim to state that the capping is possible under the simulated conditions.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** Methodological validation  
- **Claim pointer** The computational peptide array method identifies the CTD amyloidogenic core as a hotspot for Aβ interaction.  
- **Evidence pointer** Results and Discussion section "TDP-43 domains distinctly influenced Aβ secondary structure"; Methods section "Computational Peptide Array Method"  
- **Concern** The peptide array method uses 15-residue fragments of the CTD, which may not capture the full structural context of the disordered CTD. The authors do not validate this method against known interactions or provide a benchmark for its accuracy. The identification of the amyloidogenic core as a hotspot is based solely on this unvalidated approach.  
- **Why it matters** The CTD interaction is presented as a significant finding, but the method used to identify it has not been shown to be reliable. If the method overestimates or underestimates binding affinities, the conclusions about the CTD hotspot could be incorrect.  
- **Resolution test** The authors should either (a) validate the peptide array method against a known interaction or experimental data, or (b) acknowledge the limitations and suggest experimental validation of the CTD hotspot.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Figure 1b  
- **Evidence pointer** Results and Discussion section "TDP-43 interacted strongly with Aβ in silico"  
- **Issue** The contact frequency for the NTD–fibril seed system is reported as 1.0 with zero standard error, which is unusual and may be an artifact of the analysis window.  
- **Required correction** Clarify whether this value is due to the analysis window or the static nature of the fibril seed, and discuss the implications for the interpretation.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Methods section  
- **Evidence pointer** Methods section "Discrete Molecular Dynamics Simulations"  
- **Issue** The methods do not specify the number of simulation steps or the total simulation time per trajectory beyond the 1200 ns duration. Convergence of the PMFs is not discussed.  
- **Required correction** Add details on simulation length, equilibration time, and convergence criteria for the PMFs.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** Discussion of Aβ42 vs. Aβ40  
- **Evidence pointer** Results and Discussion section "TDP-43 interacted strongly with Aβ in silico"  
- **Issue** The authors attribute the weaker interaction with Aβ42 to intramolecular contacts, but do not quantify the energetic contribution of these contacts.  
- **Required correction** Provide a quantitative analysis of the intramolecular contacts or acknowledge that this is a qualitative observation.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Presentation  
- **Affected element** Figure 5  
- **Evidence pointer** Results and Discussion section "TDP-43 domains distinctly influenced Aβ secondary structure"  
- **Issue** The figure shows secondary structure changes but does not include error bars or statistical significance tests.  
- **Required correction** Add error bars or statistical analysis to support the claims of significant structural changes.

## Risk / unsupported claims
- The claim that TDP-43 "promotes Aβ toxicity" is unsupported by the simulation data, which do not include any toxicity measurements.
- The claim that the NTD "caps" the fibril elongation surface is based on simulations with a static fibril seed and may not be generalizable.
- The identification of the CTD amyloidogenic core as a hotspot relies on an unvalidated computational method.
- The extrapolation from in silico binding to in vivo pathological consequences (e.g., "worsened toxicity" in the conclusion) is speculative and not directly supported by the evidence presented.