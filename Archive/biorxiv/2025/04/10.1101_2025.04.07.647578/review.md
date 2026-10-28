## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, funding, acknowledgements) as provided
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text. Figures, tables, and supplementary materials are referenced but not directly examined.
- **Shared manuscript claim summary** The authors propose that transcription factor (TF) hub formation at enhancers is an emergent property of TF–DNA binding kinetics rather than a distinct regulatory layer. Using live imaging of Dorsal in Drosophila embryos, they show that hub enrichment and persistence scale with binding-site number and nuclear concentration but do not predict transcriptional burst parameters. A computational model parameterized with single-molecule tracking data recapitulates experimental observations.
- **Visible evidence base** Text descriptions of results, methods, and figure references. No actual figures, tables, or supplementary data were provided for direct inspection.
- **Missing materials affecting confidence** All figures, tables, supplementary figures, movies, and detailed numerical data. The results section is presented only as section headings without substantive results text. Statistical details, sample sizes, and quantitative values are not directly verifiable.

## Reviewer
- **Overall assessment** This manuscript addresses a timely and important question in gene regulation: whether TF hubs are causal regulatory structures or emergent consequences of binding kinetics. The experimental approach combining lattice light-sheet imaging, MS2 reporters, and computational modeling is sophisticated and well-suited to the question. The central claim that binding kinetics alone can explain hub formation is plausible and potentially significant. However, the provided text lacks the actual results section content, making it impossible to evaluate the strength of the evidence. The methods are described in considerable detail, suggesting careful experimental design, but the absence of quantitative results and figure data prevents full assessment. The discussion is thoughtful and appropriately cautious in several places, though some claims extend beyond what can be verified from the provided material.

- **Who would be interested in the results, and why** Researchers in transcriptional regulation, developmental biology, biophysics of gene expression, and chromatin biology would find these results relevant. The work addresses the ongoing debate about transcriptional condensates and hubs, which has broad implications for understanding how enhancers function. The methodological framework for quantifying hub properties in living embryos will be of interest to the live-imaging community. The finding that binding kinetics alone can explain hub formation challenges prevailing models of phase-separated transcriptional condensates and will interest those studying the physical basis of gene regulation.

- **Major strengths** The study combines multiple advanced techniques: lattice light-sheet microscopy, MS2-based transcription reporters, single-molecule tracking, and computational modeling. The use of the Drosophila Dorsal gradient system provides a natural context to study concentration-dependent effects. The inclusion of synthetic enhancer constructs with defined binding-site composition allows systematic manipulation of the key variable. The modeling approach is grounded in experimentally measured kinetic parameters rather than purely theoretical constructs. The authors address detection limits and background noise as confounding factors, showing awareness of technical limitations.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims to demonstrate that Dorsal hub enrichment and persistence scale with binding-site number and that these properties do not predict transcriptional burst parameters.
- **Evidence pointer** Results section (location not provided); Figures 1–7 referenced but not provided
- **Concern** The results section is entirely absent from the provided text. Only section headings are listed without any accompanying results, quantitative data, or statistical analyses. It is impossible to evaluate whether the data support the claims made in the abstract and discussion. The figures that would contain the primary evidence are referenced but not available for inspection.
- **Why it matters** The central conclusions of the paper rest entirely on the experimental results, which cannot be assessed. Without seeing the actual measurements, statistical tests, and control experiments, the validity of the claims cannot be established.
- **Resolution test** Provide the full results section with all quantitative data, statistical analyses, and figure panels. The reviewer must be able to verify that the described trends are real, statistically significant, and properly controlled.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validation
- **Claim pointer** The authors state that a computational model incorporating binding kinetics alone can recapitulate experimental hub enrichment and persistence, and that removing cooperativity fails to scale persistence with site number.
- **Evidence pointer** Results section, Figure 6, Figure S9, Figure S10 (location not provided)
- **Concern** The model description in the methods is detailed, but the validation against experimental data cannot be assessed. The claim that the model recapitulates experimental results requires quantitative comparison between simulated and measured values. The sensitivity analyses mentioned in the footnotes (testing additional cooperativity parameters) are not described in the provided text. The choice of Hill-like coefficient values (n = 100 versus 2 and 4) and their justification require scrutiny.
- **Why it matters** The conclusion that binding kinetics alone explain hub formation depends entirely on the model faithfully reproducing experimental observations. Without seeing the quantitative agreement between model and experiment, this central claim is unsupported.
- **Resolution test** Provide quantitative comparisons between model predictions and experimental measurements, including appropriate error metrics. Show that the model captures the key features of the data across all enhancer constructs tested. Justify the choice of cooperativity parameters and demonstrate that conclusions are robust to reasonable parameter variation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Correlation versus causation
- **Claim pointer** The manuscript concludes that hub properties do not predict transcriptional burst parameters, suggesting hubs are not a regulatory layer that determines transcriptional output.
- **Evidence pointer** Results section, Figure 3 (location not provided)
- **Concern** The analysis correlating hub properties with burst parameters is restricted to periods of active transcription, as the authors acknowledge. The authors state that hub dynamics prior to or between bursts could be key drivers of burst parameters, but this possibility is not tested. The conclusion that hubs do not determine transcriptional output is therefore incomplete and potentially premature.
- **Why it matters** The interpretation that hubs are emergent rather than causal depends on demonstrating that hub properties do not influence transcription. If the analysis only captures hub behavior during active transcription, it may miss the relevant regulatory events that occur before burst initiation.
- **Resolution test** Provide analysis of hub dynamics during transcriptional off-periods, or clearly state the limitations of the current analysis and temper the conclusions accordingly. If off-period analysis is technically infeasible, this should be explicitly acknowledged and the conclusions adjusted.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors suggest that their findings support a general model in which TF hubs emerge from enhancer-encoded TF–DNA interactions rather than higher-order regulatory assemblies.
- **Evidence pointer** Discussion section (location not provided)
- **Concern** The study examines a single TF (Dorsal) in a single developmental context. While the authors discuss generalizability, the claim that this represents a general model for TF hub formation extends beyond the evidence presented. Other TFs with different DNA-binding domains, interaction partners, or nuclear concentrations may behave differently.
- **Why it matters** The broader significance of the work depends on whether the findings generalize beyond Dorsal. Overstating generalizability could mislead the field.
- **Resolution test** Either provide additional evidence from other TFs or systems, or explicitly frame the conclusions as specific to Dorsal and note that generalizability remains to be tested.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract (location not provided)
- **Issue** The abstract states that hub enrichment and persistence "do not predict transcriptional bursts for a given enhancer" but the basis for this conclusion is not visible in the provided text.
- **Required correction** Ensure the results section clearly presents the correlation analyses and their statistical significance to support this claim.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Burst analysis
- **Evidence pointer** Methods, Burst Analysis section (location not provided)
- **Issue** The burst segmentation algorithm uses a minimum prominence of 0.03 and minimum height of 0.05 in normalized MCP units. The sensitivity of results to these thresholds is not discussed.
- **Required correction** Add a sensitivity analysis for burst detection parameters, or justify the chosen thresholds with reference to the data distribution.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Simulation
- **Evidence pointer** Methods, Simulations section (location not provided)
- **Issue** The simulation uses a Hill-like coefficient with n = 100 as the default, described as "extreme switch-like filtering." The choice of this extreme value and its biological justification require clarification.
- **Required correction** Provide biological rationale for n = 100 and show results across a range of n values to demonstrate robustness.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and code availability statement
- **Evidence pointer** Data, code, and materials availability section (location not provided)
- **Issue** The statement says all data needed to evaluate conclusions are present in the paper or supplementary materials, but the provided text does not include the results or figures.
- **Required correction** Ensure the full manuscript includes all results and figures, and verify that the Zenodo and Gitlab links are functional and contain the described materials.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section (location not provided)
- **Issue** The discussion mentions that prior work on Bicoid clustering did not account for differences in binding site number or hub persistence, but this comparison is not developed in the provided text.
- **Required correction** Expand this comparison to clarify how the current findings differ from or extend prior work on other TFs.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Imaging
- **Evidence pointer** Methods, Imaging Conditions section (location not provided)
- **Issue** The manuscript states that the 488 nm laser was used to excite mNeonGreen and 589 nm for mCherry, but the single-molecule imaging section mentions a 560 laser and 561 excitation. The relationship between these wavelengths is unclear.
- **Required correction** Clarify the laser lines used for each imaging modality and ensure consistency throughout the methods.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results
- **Evidence pointer** Results section (location not provided)
- **Issue** The text references correlations and comparisons but does not provide effect sizes, confidence intervals, or exact p-values in the provided material.
- **Required correction** Ensure all statistical claims include appropriate measures of effect size and uncertainty.

## Risk / unsupported claims
- The claim that hub properties do not predict transcriptional burst parameters is unsupported because the results section is not provided and the analysis is restricted to active transcription periods.
- The claim that binding kinetics alone can explain hub formation is unsupported without quantitative model-experiment comparisons.
- The claim that the findings support a general model for TF hub formation extends beyond the evidence, which examines only Dorsal.
- The statement that "phase separation-like mechanisms are not necessary to explain these observations" is a strong negative claim that cannot be fully established by the provided evidence.
- The suggestion that hub properties are "encoded within DNA sequence" is partially supported by the binding-site manipulation experiments but requires the actual results to verify.
- The claim that detection thresholds and nuclear background can influence conclusions about condensate formation is plausible but requires the sensitivity analyses referenced in the footnotes to be fully evaluated.