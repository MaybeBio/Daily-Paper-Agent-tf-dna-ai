## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary information descriptions
- **Assessment boundary** Scientific validity, technical soundness, and significance of the claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors report that the E. coli Rep helicase exists in four conformational states (S1-S4) in solution, with two previously unidentified intermediates between the open (S1) and closed (S4) states. They propose a sequential transition pathway S1→S2→S3→S4 involving distinct subdomain movements, and demonstrate that NaCl concentration tunes the population distribution and transition kinetics between these states. They further propose that the S2 intermediate may prevent premature closure in the absence of DNA.
- **Visible evidence base** Ensemble TC-FCS data (Fig. 1), confocal smFRET with ALEX (Figs. 2-3), ABEL trap single-molecule data (Fig. 4), H2MM kinetic analysis (Fig. 5), MD simulations with FRET accessible volume analysis (Fig. 6), functional assays (Supplementary Fig. 1), and supplementary tables of fitting parameters
- **Missing materials affecting confidence** Actual figures and supplementary figures not viewable; exact numerical values for rate constants and uncertainties not fully provided in text; details of H2MM model selection criteria partially described; MD simulation convergence and force field validation details limited; no information on replicate numbers for smFRET experiments beyond stated collation of multiple acquisitions

## Reviewer
- **Overall assessment** This manuscript presents an ambitious and technically sophisticated integration of multiple single-molecule fluorescence approaches with atomistic MD simulations to address conformational dynamics of the Rep helicase. The identification of four conformational states and the salt-dependent tuning of their interconversion is potentially significant for understanding helicase regulation. However, the manuscript as presented has several critical gaps that prevent full evaluation of the central claims. The most significant concerns relate to the interpretation of the four Gaussian components as discrete conformational states, the assignment of specific structural movements to the S1→S2→S3→S4 pathway, and the functional significance of the proposed intermediates. The comparison with prior UvrD work is useful but the differences between the two systems are not fully explored. The technical quality of the individual methods appears high, but the integration of results from different techniques with different timescales and conditions requires more careful justification.
- **Who would be interested in the results, and why** Researchers studying DNA helicase mechanisms, particularly those interested in conformational dynamics of SF1A helicases. The methodological integration of smFRET, ABEL trapping, and MD simulations will interest single-molecule biophysicists. The proposed salt-dependent tuning of conformational equilibria may be relevant to those studying ionic strength effects on protein-nucleic acid interactions. The broader claim about conformational plasticity in accessory helicases could interest the DNA replication and repair community.
- **Major strengths** The combination of multiple orthogonal single-molecule techniques (confocal smFRET, ABEL trapping, ensemble TCSPC/FCS) provides complementary views of the conformational landscape. The use of photon-by-photon H2MM analysis represents a rigorous approach to extracting kinetics from smFRET data. The integration of MD simulations with FRET accessible volume calculations provides a plausible structural interpretation of the observed FRET states. The functional validation through helicase activity assays strengthens the relevance of the findings. The authors are appropriately cautious in several places about the limitations of their comparisons with prior UvrD work.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data interpretation
- **Claim pointer** The manuscript claims that four Gaussian components in the smFRET efficiency distributions represent four discrete conformational states (S1-S4), with S2 and S3 being "hitherto hidden intermediates."
- **Evidence pointer** Results section "Single-molecule FRET reveals Rep exhibits four states"; Fig. 2d; Supplementary Table 3
- **Concern** The assignment of four Gaussian components to four discrete conformational states requires stronger justification. The BIC improvement from 3 to 4 components is reported, but the text does not provide the actual BIC values or the magnitude of improvement. More critically, the manuscript does not adequately address whether the four components could arise from dye photophysics, incomplete labeling, or conformational heterogeneity within a single structural state. The reported sigma widths (0.02-0.18) are quite broad, and the manuscript does not discuss whether these widths are consistent with a single conformation or could represent multiple unresolved sub-states. The exclusion of a fifth state as an "acceptor-dark state" is plausible but the criteria for this assignment are not fully described.
- **Why it matters** The central claim of the paper rests on the existence of four discrete states. If the four Gaussian components do not represent four distinct conformational states, then the proposed transition pathway and its functional implications are not supported. The distinction between discrete states and a continuous conformational distribution with preferred regions is fundamental to the interpretation.
- **Resolution test** Provide the actual BIC values and the magnitude of improvement for 2, 3, 4, and 5 component fits. Include control experiments with donor-only and acceptor-only labeled protein to rule out dye photophysics contributions. Show that the four components are reproducible across multiple protein preparations and labeling batches. Discuss whether the sigma widths are consistent with static conformational heterogeneity or dynamic averaging within each state.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural interpretation
- **Claim pointer** The manuscript claims that MD simulations combined with FRET accessible volume analysis identify the "most likely transitional pathway" as S1→S2→S3→S4, involving "an initial truncated swing of 2B which then rolls across the 1B surface, following by combined rotations of 1B, 2A and 2B."
- **Evidence pointer** Results section "Rep's transition from open to closed is more complex than a simple swing-arm movement of the 2B subdomain"; Fig. 6; Supplementary Movie 7
- **Concern** The structural interpretation relies on MD simulations in implicit solvent with 50 ns windows. This timescale is likely insufficient to capture the full conformational transition between open and closed states, which involves large domain movements. The manuscript acknowledges this limitation but does not adequately justify why the observed partial transitions in MD should correspond to the experimentally observed S2 and S3 states. The claim that 95% of 60 cluster structures fall within 1 sigma of the experimental FRET states is presented as validation, but this is a weak test given the broad sigma widths. The specific structural assignments (e.g., "truncated swing" vs "roll") are based on visual inspection of morph animations rather than quantitative analysis. The manuscript does not describe how the MD-derived structures were matched to the experimental FRET states, nor how the transition pathway was determined from the simulation data.
- **Why it matters** The structural model of the transition pathway is a major claim of the paper. If the MD simulations do not reliably sample the conformational space or if the assignment of simulated structures to experimental FRET states is not rigorous, then the proposed mechanism is speculative. The distinction between a sequential pathway through defined intermediates versus a more continuous conformational change has implications for understanding the energy landscape.
- **Resolution test** Provide quantitative analysis of the MD trajectories showing the populations of the proposed intermediate states and the transition rates between them. Show that the simulations converge and that the observed partial transitions are reproducible across independent simulations. Describe the criteria for matching simulated structures to experimental FRET states. Consider longer simulations or enhanced sampling methods to more reliably sample the transition pathway.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Kinetic interpretation
- **Claim pointer** The manuscript claims that H2MM analysis reveals "high forward and reverse rates for S1→S2" and that "increasing the NaCl concentration results in significant changes to the S1-S3 transitions" and "the S2-S3 transitions."
- **Evidence pointer** Results section "Rep undergoes dynamic transitions over a timescale range of sub-milliseconds to seconds"; Fig. 5; Supplementary Table 4
- **Concern** The H2MM analysis is performed on confocal smFRET data with burst durations of approximately 1 ms. The manuscript claims to resolve transitions on timescales from sub-milliseconds to seconds, but the confocal burst duration limits the ability to observe transitions slower than the burst duration. The ABEL trap data extends the observation window, but the manuscript does not clearly describe how the H2MM analysis was applied to the ABEL trap data, nor how the rate constants from the two different techniques were reconciled. The reported rate constants span a wide range, and the manuscript does not provide confidence intervals for all reported values. The claim that "five out of the 12 transitions show a strong rate dependence on NaCl concentration" is presented without a clear statistical framework for determining which transitions are significantly affected.
- **Why it matters** The kinetic model and the salt dependence of the transition rates are central to the claim that the conformational landscape "can be tuned by salt." If the rate constants are not reliably determined or if the salt dependence is not statistically robust, then this claim is weakened. The comparison with the prior UvrD study depends on the reliability of the kinetic parameters.
- **Resolution test** Provide a clear description of how H2MM was applied to both confocal and ABEL trap data, including the model selection criteria and the handling of different observation timescales. Report confidence intervals for all rate constants. Describe the statistical test used to determine which transitions show significant salt dependence. Consider whether the limited number of transitions observed in individual bursts could bias the estimated rate constants.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Functional significance
- **Claim pointer** The manuscript claims that "1B may act to sterically hinder 2B movement with a result that the likelihood for premature closing of Rep in the absence of DNA is reduced" and that the observations "support a more general binding model for accessory DNA helicases that utilises conformational plasticity to explore a multiplicity of structures whose landscape can be tuned by salt prior to locking-in upon DNA binding."
- **Evidence pointer** Discussion section; Fig. 6d
- **Concern** The functional significance of the proposed intermediates is largely speculative. The claim that S2 prevents premature closure is based on the observation of high forward and reverse rates for S1→S2, but the manuscript does not provide direct evidence that this intermediate is functionally relevant. The proposed "general binding model" is presented without sufficient comparative analysis with other helicases. The manuscript does not discuss how the salt concentrations used (10-500 mM) relate to physiological conditions in E. coli, nor whether the observed salt effects are specific to NaCl or represent general ionic strength effects. The connection between the in vitro observations and the in vivo function of Rep is not established.
- **Why it matters** The broader significance of the work depends on the functional relevance of the proposed intermediates and the generalizability of the model. If the intermediates are not functionally important or if the salt effects are not physiologically relevant, then the impact of the work is substantially reduced.
- **Resolution test** Provide direct experimental evidence for the functional role of the proposed intermediates, such as mutational analysis of residues predicted to stabilize S2 or S3. Discuss the physiological relevance of the salt concentrations used. Consider whether the proposed model can be tested in other helicase systems.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Comparison with prior work
- **Claim pointer** The manuscript states that "the closest published data that can be compared against our single-molecule findings here is not from Rep itself but from the homologous UvrD DNA helicase" and provides comparisons of rate constants in Supplementary Table 5.
- **Evidence pointer** Discussion section; Supplementary Table 5
- **Concern** The comparison with the prior UvrD study is presented in a way that emphasizes differences between the two systems, but the manuscript does not adequately address whether these differences could arise from methodological differences rather than genuine biological differences. The prior UvrD study used TIRF microscopy with 32 ms time resolution, while the current study uses confocal smFRET with much higher time resolution. The labeling positions, dye pairs, and buffer conditions may also differ. The manuscript acknowledges some of these caveats but does not systematically address how they might affect the comparison. The claim that the current study reveals "transient and salt-dependent transitions" that the prior study could not observe is plausible but not fully established.
- **Why it matters** The comparison with prior work is important for establishing the novelty and significance of the current findings. If the differences between Rep and UvrD are largely methodological, then the claim of a "more general binding model" is weakened.
- **Resolution test** Provide a more systematic comparison of the experimental conditions between the two studies. Discuss whether the differences in time resolution could explain the apparent differences in the number of states and transition rates. Consider whether the prior UvrD data could be reanalyzed with the current analytical approach.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that the authors "detect four states revealing two hitherto hidden intermediates (S2, S3), between the open (S1) and closed (S4) structures." The phrase "hitherto hidden" is somewhat overstated given that the prior UvrD study also reported four states. The abstract could be more precise about what is genuinely novel.
- **Required correction** Revise the abstract to more carefully distinguish between the identification of four states and the specific structural and kinetic characterization of these states.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods section on H2MM
- **Evidence pointer** Methods section "BVA and H2MM of smFRET confocal microscopy data"
- **Issue** The description of the H2MM model selection criteria is brief. The text mentions BIC' and ICL but does not provide the specific values or the range of models tested. The criteria for excluding the fifth state as an "acceptor-dark state" are not fully described.
- **Required correction** Provide more detail on the model selection procedure, including the range of models tested and the specific criteria for selecting the four-state model.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Fig. 5
- **Evidence pointer** Fig. 5
- **Issue** The rate constants in Fig. 5 are presented as a network diagram, but the numerical values are not easily readable in the text description. The manuscript would benefit from a table of all rate constants with confidence intervals.
- **Required correction** Consider adding a table of all rate constants with confidence intervals for each salt condition.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion of MD simulations
- **Evidence pointer** Results section on MD simulations
- **Issue** The manuscript states that "57 (i.e. 95%) lay within 1 sigma of its nearest identified FRET state" for the cluster structures. This is presented as validation, but the statistical significance of this overlap is not assessed. A random distribution of structures might also show a high overlap given the broad sigma widths.
- **Required correction** Provide a statistical test for the significance of the overlap between simulated and experimental FRET values, such as a comparison with a null distribution.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion of salt effects
- **Evidence pointer** Discussion section
- **Issue** The manuscript reports that "five out of the 12 transitions which are in principle possible between any pair of these four Rep states show a strong rate dependence on NaCl concentration." The discussion of which specific transitions are salt-dependent and the potential mechanism of the salt effect is limited.
- **Required correction** Expand the discussion of the salt dependence, including which specific transitions are affected and the potential molecular mechanism (e.g., electrostatic screening, ion binding).

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Fig. 6d
- **Evidence pointer** Fig. 6d
- **Issue** The 2D cartoon schematic in Fig. 6d is described in the text but the specific features of the cartoon are not clearly explained. The relationship between the cartoon and the MD-derived structures is not fully described.
- **Required correction** Provide a more detailed legend for Fig. 6d that explains the features of the cartoon and how it relates to the structural data.

## Risk / unsupported claims
- The claim that S2 and S3 are "hitherto hidden intermediates" is not fully supported given that the prior UvrD study also reported four states; the novelty lies in the specific characterization, not the mere existence of intermediates.
- The specific structural assignments for the S1→S2→S3→S4 pathway (truncated swing, rolling, combined rotations) are based on MD simulations with limited sampling and are not directly validated by experimental data.
- The claim that "1B may act to sterically hinder 2B movement" is speculative and not directly tested experimentally.
- The proposed "more general binding model for accessory DNA helicases" is not supported by comparative data from other helicase systems.
- The functional significance of the salt-dependent tuning of conformational states for Rep's in vivo function is not established.
- The comparison with the prior UvrD study is complicated by methodological differences that are not fully addressed.
- The statistical significance of the overlap between MD-predicted and experimentally observed FRET values is not assessed.
- The manuscript does not provide sufficient detail on the H2MM model selection criteria to fully evaluate the robustness of the four-state model.