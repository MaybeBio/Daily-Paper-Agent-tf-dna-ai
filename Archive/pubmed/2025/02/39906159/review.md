## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, and methods sections
- **Assessment boundary** Scientific validity, methodological soundness, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors evaluate whether the standard Gillespie stochastic simulation algorithm (SSA), which assumes spatial homogeneity, can accurately capture gene regulation dynamics when spatial heterogeneity is present. They find that under slow transcription factor diffusion, the SSA fails to capture mRNA variability and mean levels in certain conditions. They then test two quasi-steady-state approximations (stQSSA and slQSSA) as model reduction techniques for the spatial SSA, finding that stQSSA introduces errors while slQSSA remains accurate.
- **Visible evidence base** Main text figures (Figs. 1-4), supplementary figures referenced (S1-S5), tables of propensity functions (Tables 1-4), and mathematical derivations in Methods
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; code or simulation implementation details not provided; parameter sensitivity analyses not shown; no experimental validation data

## Reviewer

### Overall assessment
This manuscript addresses a relevant and timely question in stochastic simulation of gene regulatory networks: whether the common homogeneity assumption in the Gillespie SSA remains valid when spatial heterogeneity is present, and whether existing QSSA reduction techniques can be safely applied to spatial stochastic simulations. The authors demonstrate with clear simulation examples that the SSA fails under slow diffusion conditions, and that stQSSA can produce erroneous results in spatially heterogeneous settings while slQSSA remains accurate. The work is technically sound in its core simulation comparisons, and the message is practically important for the computational biology community. However, the manuscript would benefit from a more systematic characterization of the parameter regimes where the identified failures occur, and from a clearer articulation of the practical guidance for when spatial simulations are necessary.

### Who would be interested in the results, and why
Computational biologists and biophysicists who use stochastic simulation methods to model gene regulation, particularly those studying systems where transcription factor diffusion may be slow relative to binding reactions. Researchers developing or applying model reduction techniques for stochastic simulations will also find the comparison between stQSSA and slQSSA in spatial contexts valuable. The work may also interest experimental biologists who use computational models to interpret single-cell or single-molecule data, as it highlights conditions under which standard modeling assumptions may break down.

### Major strengths
1. The manuscript addresses a genuinely important and underappreciated issue: the homogeneity assumption in the Gillespie SSA is often taken for granted, and the authors provide clear simulation evidence for when this assumption fails.
2. The comparison between stQSSA and slQSSA in the spatial context is novel and practically useful, as stQSSA is widely used for model reduction and the demonstration of its failure in heterogeneous settings is an important cautionary result.
3. The presentation is clear and accessible, with well-designed figures that illustrate the key findings intuitively.
4. The authors provide a mechanistic explanation for the stQSSA failure (local molar ratio approaching 1:1 near DNA), which strengthens the credibility of the result.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "the stQSSA can be inaccurate in reducing the full model for spatial SSA, even under conditions previously predicted to ensure accuracy in reducing the full model for SSA" (Discussion).
- **Evidence pointer** Fig. 3C-D, Supplementary Fig. S3
- **Concern** The demonstration of stQSSA failure is limited to a narrow set of parameter values and initial conditions. The authors show two specific scenarios (Fig. 3C-D) where stQSSA fails, but do not systematically map the parameter space to identify the boundaries of validity. The claim that stQSSA "can be inaccurate" is supported, but the practical guidance for when it is safe to use stQSSA versus when it is not remains unclear. A phase diagram or parameter scan showing regions of accuracy versus failure would substantially strengthen the practical utility of this finding.
- **Why it matters** Without a systematic characterization, readers cannot determine whether their specific parameter regime falls in the safe or unsafe region. The current evidence supports the qualitative conclusion but does not provide quantitative guidance for practitioners.
- **Resolution test** Provide a systematic parameter scan (e.g., varying Kd, DT/PT ratio, diffusion coefficient) showing the regions where stQSSA is accurate versus inaccurate for the spatial SSA, and compare these boundaries with the conditions previously derived for the homogeneous SSA.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that "our study provides guidelines on how to simulate and simplify models describing gene regulation by transcription factors with slow diffusion in spatially heterogeneous environments" (Abstract and Discussion).
- **Evidence pointer** Fig. 2, Fig. 3, Fig. 4
- **Concern** The manuscript demonstrates the failure of SSA and stQSSA in specific test cases, but the "guidelines" are not explicitly articulated. The authors do not provide a clear decision framework for when a practitioner should use spatial SSA versus standard SSA, or when slQSSA is a safe reduction. The practical recommendations are implicit in the results but are not distilled into actionable guidance.
- **Why it matters** The stated contribution is to provide guidelines, but the manuscript currently reads more as a demonstration of failure modes than as a practical guide. Making the guidelines explicit would increase the impact and utility of the work.
- **Resolution test** Add a dedicated section or figure that summarizes the conditions under which (a) standard SSA is adequate, (b) spatial SSA is necessary, and (c) slQSSA can be safely used as a reduction. This could take the form of a decision tree or a summary table of parameter regimes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "the slQSSA always correctly reduced the full model" (Results section, Fig. 3C-D).
- **Evidence pointer** Fig. 3C-D, Supplementary Fig. S3
- **Concern** The claim that slQSSA "always" correctly reduces the full model is too strong given the evidence presented. The authors demonstrate accuracy for the specific test cases shown, but do not provide a proof or exhaustive analysis that slQSSA is universally accurate for spatial SSA. The word "always" is not justified by the evidence.
- **Why it matters** Overstating the generality of the result could lead readers to apply slQSSA in regimes where it may not be valid. The claim should be tempered to reflect the evidence.
- **Resolution test** Either soften the claim to "in the tested cases" or provide a more rigorous argument (analytical or extensive numerical) for why slQSSA should be expected to be accurate across a broad range of conditions in spatial settings.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "when the molar ratio is close to 1:1, the stQSSA overestimates the mRNA production" (Fig. 3C-D).
- **Evidence pointer** Fig. 3C-D
- **Concern** The mechanistic explanation for the stQSSA failure is that the local molar ratio of D and P approaches 1:1 near the DNA, but this explanation is not directly verified. The authors infer this from the simulation results but do not measure or directly demonstrate the local ratio during the simulations. A more direct verification of the proposed mechanism would strengthen the interpretation.
- **Why it matters** The proposed mechanism is plausible and consistent with previous work, but without direct verification, alternative explanations cannot be ruled out. For example, the failure could also be related to the spatial correlation of fluctuations or to the timescale separation assumptions.
- **Resolution test** Directly measure the local D and P concentrations in the spatial simulations at the DNA-containing compartment and show that the ratio approaches 1:1 in the failure regime, or provide additional simulations that manipulate the local ratio to confirm the causal role.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction, paragraph 1
- **Evidence pointer** Introduction, location not provided
- **Issue** The introduction assumes familiarity with the Gillespie algorithm and QSSA methods. A brief intuitive explanation of why the homogeneity assumption might fail would help nonspecialist readers understand the motivation.
- **Required correction** Add one or two sentences explaining in plain terms why spatial localization of DNA and slow diffusion of transcription factors could invalidate the well-mixed assumption.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Stochastic simulation of homogeneous environments"
- **Evidence pointer** Methods section, location not provided
- **Issue** The initial conditions for the SSA simulations are stated somewhat awkwardly with a duplicated phrase: "the number of D and P, D and P, were set to the following initial conditions were used." This appears to be a typographical or editing error.
- **Required correction** Rewrite the sentence to clearly state the initial conditions, e.g., "The initial numbers of D and P were set as follows: [D(0),P(0)] = [1,30] for Fig. 2A and C, ..."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Derivation of two reduction model equations"
- **Evidence pointer** Methods section, location not provided
- **Issue** The derivation of the slQSSA and stQSSA equations is presented without sufficient context for readers who may not be familiar with the previous work. The relationship between the reduced model equations and the full model is not explicitly stated.
- **Required correction** Briefly explain how the reduced models are derived from the full model and what assumptions are made in each approximation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Fig. 3B
- **Evidence pointer** Fig. 3B
- **Issue** The figure panel showing the relative error of stQSSA as a function of sensitivity is not fully explained in the text. The connection between sensitivity and error is not immediately obvious.
- **Required correction** Add a sentence in the text or figure legend explaining why high sensitivity of the QSSA leads to large errors.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion, location not provided
- **Issue** The discussion of future work mentions applying tQSSA in stochastic and spatially heterogeneous contexts, but does not discuss potential alternative approaches (e.g., hybrid methods, moment-based approximations) that could also address the identified limitations.
- **Required correction** Briefly mention alternative approaches and how they compare to the slQSSA approach recommended in this work.

### Technical failings that need to be addressed before the case is established
1. The claim that slQSSA "always" works (R1-M3) needs to be tempered or more rigorously supported.
2. The parameter space exploration is insufficient to establish the general validity boundaries of the findings (R1-M1).
3. The mechanistic explanation for stQSSA failure is inferred but not directly verified (R1-M4).

### Assessment against Nature-style criteria
- **Originality**: The work is original in its specific focus on testing QSSA methods in the context of spatial stochastic simulations. While the general idea that spatial heterogeneity matters is not new, the systematic comparison of stQSSA versus slQSSA in this context provides a novel contribution.
- **Scientific importance**: The findings are important for practitioners using stochastic simulation methods. The demonstration that stQSSA can fail in spatial settings, despite being widely used, is a cautionary result with practical implications. However, the importance is somewhat limited by the narrow parameter exploration.
- **Interdisciplinary readership**: The work is primarily relevant to computational biologists and biophysicists. The potential for broader interdisciplinary interest is limited, as the findings are specific to stochastic simulation methodology rather than to a particular biological system or question.
- **Technical soundness**: The core simulation comparisons appear technically sound, but the limited parameter exploration and the overstatement of the slQSSA claim weaken the overall technical case.
- **Readability for nonspecialists**: The manuscript is generally well-written and the figures are clear. However, some sections assume familiarity with QSSA methods, and the practical implications could be articulated more explicitly for a broader audience.

### Recommendation posture
Supportive if technical concerns are resolved. The core message is valuable and the simulations appear well-executed, but the manuscript would be substantially strengthened by a more systematic parameter exploration, a tempered claim about slQSSA, and explicit practical guidelines for when spatial simulations are necessary.

## Risk / unsupported claims
- The claim that slQSSA "always correctly reduced the full model" is not supported by the evidence, which only demonstrates accuracy for specific test cases.
- The claim that the stQSSA failure is due to the local molar ratio approaching 1:1 is plausible but not directly verified.
- The statement that "the diffusion timescale of transcription factors can be slower than the reaction timescale" in the Discussion is based on literature estimates but is not systematically explored across the full range of biologically relevant parameters.
- The claim that the slQSSA achieves a "40- to 120-fold speedup" is based on supplementary figures not provided in the manuscript, so this cannot be independently assessed.
- The generalizability of the findings to two-dimensional or three-dimensional domains is suggested but only briefly supported by a reference to Supplementary Fig. S4, which is not provided.