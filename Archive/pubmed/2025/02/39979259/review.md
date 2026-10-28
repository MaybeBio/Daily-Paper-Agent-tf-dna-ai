## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary figure/table references.
- **Assessment boundary** Scientific content, experimental design, data analysis, interpretation, and claims as presented. No assessment of editorial fit or publication decision.
- **Shared manuscript claim summary** The authors use single-molecule imaging in live zebrafish embryos to measure binding kinetics of cohesin and CTCF during early embryogenesis. They report increased chromatin-bound fractions of both proteins between 1000-cell and shield stages, explain this through changes in association and dissociation rates, show that long-bound cohesin restricts chromatin motion, and use polymer simulations with experimentally derived parameters to recapitulate the gradual emergence of chromatin architecture.
- **Visible evidence base** Main text figures 1-4, supplementary figures 1-28, supplementary tables 1-16, methods section, and references to published datasets (GSE130944, GSE133437).
- **Missing materials affecting confidence** Raw single-molecule tracking data, full statistical output tables beyond p-values, detailed simulation parameter sweeps, and complete Western blot images are not fully visible in the provided text. Supplementary tables are referenced but not fully reproduced.

## Reviewer
- **Overall assessment** This manuscript presents a technically sophisticated application of single-molecule imaging to address a fundamental question in developmental biology: how chromatin architecture emerges during embryogenesis. The combination of multiple imaging modalities (continuous, ITM, TACO) with polymer simulations is commendable and provides a framework for linking molecular kinetics to chromosome organization. The central finding that chromatin-bound fractions of cohesin and CTCF increase during development, driven by changes in both association and dissociation rates, is potentially important. However, several concerns regarding the interpretation of binding classes, the quantitative rigor of the kinetic model, and the directness of the link between measured parameters and architectural outcomes need to be addressed before the case is fully established.

- **Who would be interested in the results, and why** Researchers in chromatin biology, developmental biology, and biophysics would find these results of interest. The work provides in vivo measurements of architectural protein dynamics during a critical developmental window, which is rare and valuable. The methodological framework combining single-molecule tracking with simulations could be adopted by others studying protein-DNA interactions in living organisms. The findings also have implications for understanding how chromatin structure is established during development, relevant to those studying gene regulation and nuclear organization.

- **Major strengths**
  1. The use of multiple complementary imaging approaches (continuous, ITM, TACO) to dissect binding kinetics is rigorous and well-designed.
  2. The inclusion of mutant controls (Rad21-3x, CTCF-ΔZF4-7) strengthens the assignment of binding classes to specific molecular interactions.
  3. The integration of experimentally derived parameters into polymer simulations provides a quantitative link between molecular kinetics and architectural outcomes.
  4. The developmental time course spanning pre-ZGA to shield stage captures a biologically meaningful transition.
  5. The work addresses a significant gap in the field, as most cohesin/CTCF dynamics studies have been performed in cultured cells rather than in developing embryos.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of binding classes
- **Claim pointer** The authors state that "long-bound fractions of both cohesin and CTCF are predominantly associated with chromatin binding, while short-bound fractions are presumably associated with unspecific transient modes of binding."
- **Evidence pointer** Figure 1g, h; Supplementary Figures 10-13
- **Concern** The assignment of long-bound (>8.2 s) events to specific chromatin binding and short-bound (<10 s) events to unspecific interactions is a critical interpretive step. While the mutant controls support this assignment, the threshold of 10 s used to separate "short" from "long" binding in the GRID analysis appears somewhat arbitrary. The authors should justify this cutoff more rigorously, perhaps by showing that the binding class distribution is bimodal or by demonstrating that the chosen threshold does not materially affect the conclusions. Additionally, the possibility that some long-bound events represent cohesin engaged in sister chromatid cohesion rather than loop extrusion is not fully addressed, which could confound the interpretation of the architectural role.
- **Why it matters** The central claims of the paper depend on the correct assignment of binding classes to functional states. If the threshold is mis-calibrated or if long binding includes a substantial fraction of cohesion-specific events, the conclusions about loop extrusion and chromatin architecture formation would be weakened.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor of kinetic model
- **Claim pointer** The authors state that "increasing binding of cohesin restricted chromatin motion, potentially via loop extrusion" and that "changes in both association and dissociation rates" explain the increased bound fractions.
- **Evidence pointer** Figure 3d-j; Methods section on GRID analysis
- **Concern** The GRID method is used to extract dissociation rate spectra from fluorescence survival time distributions. While this is a valid approach, the interpretation of the resulting spectra as representing distinct molecular states requires careful validation. The authors should provide more detail on how the number of rate clusters was determined, how the threshold of 0.1 s⁻¹ was chosen to separate short from long binding, and whether the results are robust to changes in these parameters. Furthermore, the calculation of search times relies on assumptions about the number of binding sites and nuclear volume that are only approximately estimated. The authors should provide a sensitivity analysis to show that their conclusions are not overly dependent on these assumptions.
- **Why it matters** The quantitative claims about association and dissociation rates, and the derived search times, are central to the mechanistic interpretation. If the kinetic model is not robust, the conclusions about how binding kinetics change during development would be unreliable.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Link between measured parameters and architectural outcomes
- **Claim pointer** The authors claim that "polymer simulations with experimentally derived parameters recapitulated the experimentally observed gradual emergence of chromatin architecture."
- **Evidence pointer** Figure 4a-g; Methods section on polymer simulations
- **Concern** The polymer simulations are used to argue that the measured changes in binding kinetics are sufficient to explain the emergence of chromatin architecture. However, the simulations omit several factors that could be important, including CTCF directionality, loop extrusion blocking by other complexes, and the presence of multiple cohesin complexes on the same fiber. The authors acknowledge some of these limitations but do not test whether their conclusions are robust to their inclusion. Additionally, the comparison between simulated and experimental contact maps is qualitative. A more quantitative comparison, such as calculating a correlation coefficient or using a statistical test, would strengthen the claim.
- **Why it matters** The claim that the measured kinetic changes are sufficient to explain architectural emergence is a strong one. If the simulations are not robust to model assumptions or if the comparison to experimental data is only qualitative, this claim would be overstated.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of findings
- **Claim pointer** The authors state that "our findings reveal molecular kinetics underlying chromatin architecture formation during zebrafish embryogenesis."
- **Evidence pointer** Throughout the manuscript
- **Concern** The study is performed exclusively in zebrafish embryos. While this is a valid model system, the authors do not discuss the extent to which their findings might generalize to other organisms. Given that the timing and mechanisms of chromatin architecture establishment vary across species, the authors should temper their conclusions or provide a more detailed discussion of the potential for species-specific differences. This is particularly relevant given that the simulation parameters were calibrated using data from mouse embryonic stem cells.
- **Why it matters** The broader significance of the work depends on its generalizability. If the findings are zebrafish-specific, the impact would be more limited.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure presentation
- **Affected element** Figure 1c-e
- **Evidence pointer** Figure 1c-e
- **Issue** The example tracks in Figure 1c are described as being from the 64-cell and shield stages, but the color coding is not clearly explained in the figure legend. Additionally, the inset zooms in Figures 1g and 1h are difficult to read.
- **Required correction** Please clarify the color coding in the figure legend and consider enlarging the inset panels or providing separate enlarged versions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 1d, e
- **Evidence pointer** Figure 1d, e; Supplementary Tables 1-9
- **Issue** The authors report p-values in supplementary tables but do not consistently report effect sizes or confidence intervals. This makes it difficult to assess the magnitude of the reported differences.
- **Required correction** Please include effect sizes and confidence intervals for the key comparisons, or at least for the main claims.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of limitations is relatively brief. The authors acknowledge that photobleaching and nuclear movement may affect measurements but do not discuss the potential impact of ectopic protein expression on the measured kinetics.
- **Required correction** Please add a more detailed discussion of the potential limitations, including the effects of overexpression and the extent to which the measured kinetics might differ from endogenous protein behavior.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement
- **Evidence pointer** Not explicitly stated in the provided text
- **Issue** The manuscript does not include an explicit data availability statement in the provided text. Given the importance of the single-molecule tracking data and simulation code, it would be helpful to state where these are deposited.
- **Required correction** Please add a data availability statement indicating where the raw data and analysis code can be accessed.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Justification of the 10 s threshold for separating short and long binding events.
  - R1-M2: Sensitivity analysis for the GRID analysis parameters and search time calculations.
  - R1-M3: Quantitative comparison between simulated and experimental contact maps, and testing robustness to model assumptions.

- **Assessment against Nature-style criteria**
  - **Originality** The work is original in its application of single-molecule imaging to study architectural protein dynamics in a developing embryo. While similar approaches have been used in cultured cells, the extension to a whole organism is novel.
  - **Scientific importance** The findings address a fundamental question about how chromatin architecture is established during development. The results are likely to be of interest to a broad audience in chromatin biology and developmental biology.
  - **Interdisciplinary readership** The work bridges biophysics, molecular biology, and developmental biology. The methods and concepts are accessible to researchers in these fields, though some background in single-molecule imaging would be helpful.
  - **Technical soundness** The experimental design is generally sound, with appropriate controls and multiple complementary approaches. However, the concerns raised above about the kinetic model and simulation robustness need to be addressed.
  - **Readability for nonspecialists** The manuscript is generally well-written and the main findings are clearly presented. However, some sections, particularly the methods, may be challenging for nonspecialists. The authors could improve accessibility by providing more context for the single-molecule imaging techniques.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a valuable and novel contribution to the field, but the concerns about the interpretation of binding classes, the robustness of the kinetic model, and the quantitative link to architectural outcomes need to be addressed before the case is fully established.

## Risk / unsupported claims
- The claim that long-bound cohesin "potentially via loop extrusion" restricts chromatin motion is not directly tested. The authors infer this from the correlation between long binding and reduced mobility, but alternative explanations (e.g., cohesion) are not excluded.
- The claim that the polymer simulations "recapitulated the experimentally observed gradual emergence of chromatin architecture" is based on qualitative comparison. A quantitative assessment is needed.
- The search time calculations rely on estimates of protein concentration and binding site numbers that are only approximately known. The resulting values should be treated as order-of-magnitude estimates.
- The generalizability of the findings to other organisms is not established and should not be assumed.