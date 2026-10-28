## Review setup
- **Input scope** Full manuscript text (abstract, significance, introduction, methods, results, discussion, data availability, acknowledgments, author contributions, declarations)
- **Assessment boundary** Scientific and technical evaluation of the S3CS method as presented, including simulation validation, live-cell experimental evidence, and biological applications
- **Shared manuscript claim summary** The authors introduce spatial triple-correlation spectroscopy (S3CS), a fluorescence fluctuation method combining three-channel line scan microscopy with a spatial triple-correlation function, to detect and track heterotrimeric protein complexes in live cells. They claim S3CS quantitatively captures heterotrimer formation, local diffusion, and long-range transport, and demonstrate its utility on importin-α/importin-β/NLS cargo nuclear import and NF-Y transcription factor assembly.
- **Visible evidence base** Abstract, significance statement, introduction, full methods section, results section with figure descriptions (Figures 1–6, Figures S1–S12 referenced), discussion, data availability statement
- **Missing materials affecting confidence** Actual figures and figure panels are not provided; supplementary figures S1–S12 are referenced but not available; no raw data or statistical analysis details beyond mean ± SE and t-test p-values; no detailed derivation of the triple-correlation function or its noise properties; no comparison with existing methods on the same datasets

## Reviewer

### Overall assessment
This manuscript presents a methodological advance in fluorescence fluctuation spectroscopy, extending triple-correlation analysis to include spatial information. The concept is timely and addresses a genuine gap in the field, as heterotrimer dynamics in live cells have indeed remained difficult to resolve. The simulation framework appears thoughtfully designed, and the two biological applications are well chosen to demonstrate the method's capabilities. However, the manuscript as presented has several significant technical concerns that must be addressed before the claims are fully established. The lack of actual figure data makes it impossible to fully assess the quality of the results, and several methodological details require clarification. The biological conclusions, while plausible, rest on assumptions about the correlation function's specificity that need stronger validation.

### Who would be interested in the results, and why
Biophysicists and cell biologists studying protein complex dynamics, particularly those working on nucleocytoplasmic transport, transcription factor assembly, and signaling complexes. Method developers in fluorescence fluctuation spectroscopy and advanced microscopy will also find this work relevant. The method addresses a real need for tools that can resolve higher-order protein complexes in living cells with spatial information, and the two demonstrated applications (importin and NF-Y systems) are of broad interest to cell biology.

### Major Strengths
1. The conceptual advance of adding a spatial dimension to triple-correlation analysis is novel and addresses a clear methodological gap.
2. The simulation framework is comprehensive, testing specificity, quantitation, and performance under heterogeneous conditions.
3. The two biological applications are well chosen and demonstrate the method's versatility.
4. The authors are transparent about the limitations of their approach, including the low-expression requirement and the focus on the τ1 = τ2 diagonal.
5. The method is presented with sufficient detail in the methods section to be reproducible, and code is made available.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that S3CS "quantitatively captures heterotrimer formation, local diffusion, and long-range transport" based on simulation results.
- **Evidence pointer** Results section, Figures 2 and 3; Methods section, Simulations
- **Concern** The simulation validation is described in text but the actual figures are not available for review. More critically, the manuscript does not report any quantitative metrics of fit quality, accuracy, or precision for the extracted parameters (N, D, τ). The text states that "comparison of the fitted parameters confirmed that both G123(τ1 = τ2) and G123(τ1 = τ2, δr) provide quantitative readouts," but no error analysis, bias assessment, or comparison between true and recovered values is presented. Without these metrics, the claim of quantitative accuracy is not established.
- **Why it matters** The central claim of the paper is that S3CS provides quantitative information about heterotrimer dynamics. If the accuracy and precision of the recovered parameters are not demonstrated, the method's utility for biological applications is uncertain.
- **Resolution test** Provide quantitative comparisons between simulated ground truth and recovered parameters across the full range of tested conditions, including bias, variance, and limits of detection. Report fit quality metrics (e.g., reduced chi-squared, residuals) and demonstrate that the fitting procedure is unbiased.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that S3CS "selectively detects heterotrimers while excluding monomeric or heterodimeric species" in live cells.
- **Evidence pointer** Results section, Figure 4; Methods section, Live-cell line scan data preprocessing
- **Concern** The negative controls (monomers and heterodimers) are described as producing no positive triple-correlation amplitude, but the statistical framework for this conclusion is not described. How many cells were examined? What was the distribution of Q123 values in negative controls? What threshold was used to define a "positive" signal? The manuscript reports Q123 = 4.78 ± 1.71 for the triple construct but does not report the corresponding values for negative controls. Without this information, the specificity claim is not quantitatively supported.
- **Why it matters** Specificity is the foundation of the method's utility. If the false-positive rate is not characterized, users cannot interpret Q123 values in new systems.
- **Resolution test** Report Q123 values for all negative control conditions with sample sizes, distributions, and the statistical threshold used to distinguish positive from negative signals. Provide receiver-operating characteristic analysis or equivalent.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that S3CS can "resolve directional, irreversible nuclear import" for the importin-α/importin-β/NLS cargo complex.
- **Evidence pointer** Results section, Figure 5
- **Concern** The interpretation of direction-dependent transport relies on comparing G123 and G321 correlation functions. However, the manuscript does not provide a theoretical framework or control experiments establishing that the asymmetry between G123 and G321 is specifically attributable to directional transport rather than to other factors such as differences in fluorophore brightness, spectral cross-talk, or the spatial arrangement of the three detection channels. The biological conclusion of "irreversible nuclear import" is significant and would benefit from orthogonal validation.
- **Why it matters** The directionality claim is a key biological finding. If the G123/G321 asymmetry has alternative explanations, the conclusion about irreversible import is not secure.
- **Resolution test** Provide control experiments with known bidirectional or symmetric transport systems to validate the directionality readout. Alternatively, provide a theoretical derivation showing that G123/G321 asymmetry is uniquely determined by transport directionality under the stated assumptions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The claim that S3CS "provides a versatile platform to dissect how heterotrimeric signaling complexes employ molecular interactions to navigate the dynamic structural framework of the living cell."
- **Evidence pointer** Discussion section
- **Concern** The NF-Y application demonstrates that the method can detect heterotrimer formation and differences in mobility between wild-type and mutant complexes. However, the biological insight gained is limited: the finding that a DNA-binding mutant shows faster mobility is consistent with expectations but does not reveal new biology. The authors should articulate more specifically what new biological questions S3CS can answer that existing methods cannot.
- **Why it matters** The broader impact of the method depends on its ability to generate new biological insights, not just confirm known behavior.
- **Resolution test** Provide a more detailed discussion of specific open questions in heterotrimer biology that S3CS is uniquely positioned to address, or include a third biological application that demonstrates a novel finding.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction, first paragraph
- **Evidence pointer** Introduction section
- **Issue** The introduction assumes familiarity with FCS terminology and does not provide sufficient context for readers outside the immediate field. Terms such as "triple correlation function," "pair correlation function," and "spatial offset" are used without intuitive explanations.
- **Required correction** Add brief explanations of these concepts for nonspecialist readers, perhaps with a simple schematic or analogy.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Equation 3
- **Evidence pointer** Methods section, Extracting heterotrimer fraction from S3CS carpets
- **Issue** The definition of Q123 in Equation 3 uses a max() function over three pairwise ratios, but the rationale for this specific normalization is not explained. Why is the maximum used rather than the mean or a specific ratio?
- **Required correction** Provide a brief justification for this choice and discuss its implications for the interpretation of Q123.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Live-cell line scan data preprocessing
- **Evidence pointer** Methods section
- **Issue** The threshold for excluding segments (three times the mean standard deviation) is described as "user-defined," but no sensitivity analysis is provided. The results could depend on this choice.
- **Required correction** Report the sensitivity of the main conclusions to this threshold or justify the specific value chosen.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Results, Figures 4 and 5
- **Evidence pointer** Results section
- **Issue** The biological significance of the transit time values (e.g., τCY = 0.18 ± 0.07 ms) is not contextualized. Are these times consistent with known nuclear transport kinetics?
- **Required correction** Add a brief comparison with published values for nuclear transport times to help readers assess the biological relevance.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Simulations
- **Evidence pointer** Methods section
- **Issue** The simulation parameters (e.g., 200 particles per channel, D = 10 μm2 s−1) are stated but the rationale for these choices is not given. How sensitive are the conclusions to these parameters?
- **Required correction** Provide justification for the parameter choices or include a sensitivity analysis.

### Technical failings that need to be addressed before the case is established
R1-M1 (quantitative validation metrics), R1-M2 (statistical framework for specificity), R1-M3 (directionality interpretation)

### Assessment against Nature-style criteria
- **Originality** The concept of spatial triple-correlation spectroscopy is genuinely novel. While triple-correlation FCS exists, integrating spatial information through line scanning represents a creative extension that addresses a real limitation. The originality is comparable to what would be expected for a strong methods paper.
- **Scientific importance** The ability to track heterotrimer dynamics with spatial resolution in live cells addresses a significant gap. Heterotrimeric complexes are central to many signaling pathways, and the two demonstrated applications are biologically relevant. However, the biological insights demonstrated here are somewhat incremental, and the broader impact will depend on future applications.
- **Interdisciplinary readership** The work bridges biophysics, cell biology, and method development. The potential audience is broad, but the presentation is currently too specialized for nonspecialists to fully appreciate. The significance statement helps but is not sufficient.
- **Technical soundness** The simulation framework is well conceived, but the lack of quantitative validation metrics and the incomplete statistical framework for specificity are significant concerns. The directionality interpretation requires stronger support. These issues must be resolved before the technical case is fully established.
- **Readability for nonspecialists** The manuscript is clearly written for specialists in fluorescence fluctuation spectroscopy. The introduction and methods assume significant prior knowledge. For a Nature-style audience, additional context and explanation would be needed.

### Recommendation posture
Supportive if technical concerns are resolved. The core concept is promising and the work addresses a real need, but the quantitative validation, statistical framework, and directionality interpretation require strengthening before the claims are fully established. The authors should also consider whether the biological applications demonstrate sufficient new insight to justify the broad interest claim.

## Risk / unsupported claims
1. The claim that S3CS "quantitatively captures heterotrimer formation, local diffusion, and long-range transport" is not fully supported without quantitative validation metrics comparing simulated ground truth to recovered parameters.
2. The claim that S3CS "selectively detects heterotrimers while excluding monomeric or heterodimeric species" in live cells is not quantitatively supported without reporting negative control Q123 values and statistical thresholds.
3. The interpretation of "directional, irreversible nuclear import" based on G123/G321 asymmetry is not fully supported without control experiments or theoretical justification.
4. The claim that S3CS "provides a versatile platform" for studying heterotrimer signaling complexes is somewhat overstated given the limited biological insight demonstrated in the two applications.
5. The statement that S3CS "resolves heterotrimer assembly and disassembly events" is not directly demonstrated in the results; the method appears to detect steady-state heterotrimer populations rather than dynamic assembly/disassembly events.