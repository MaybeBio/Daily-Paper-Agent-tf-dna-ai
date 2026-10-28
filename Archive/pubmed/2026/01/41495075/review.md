## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure legends
- **Assessment boundary** Scientific content, methodological rigor, validity of claims relative to provided evidence, and alignment with Nature-style criteria
- **Shared manuscript claim summary** The authors use a multiscale computational approach (AlphaFold3 predictions, all-atom MD, and coarse-grained MD) to show that DNA actively regulates the "safety-belt" dynamics of yeast condensin during loop extrusion. They report that DNA binding stabilizes the Ycg1-Brn1 safety belt, that DNA outside the loop promotes opening while DNA inside promotes closure, and that the rate-limiting step of DNA entrapment depends on latch-buckle interaction strength.
- **Visible evidence base** Main text figures 1-5 (described in text), supplementary figures S1-S19 (referenced), supplementary tables S1-S3 (referenced), methods section, and one supplementary movie (referenced)
- **Missing materials affecting confidence** Actual figure images, supplementary figures, supplementary tables, simulation parameter files, force field details, convergence criteria, and the supplementary movie were not provided. Statistical analysis details and raw trajectory data are not accessible.

## Reviewer
- **Overall assessment** This manuscript presents a computationally intensive multiscale study of condensin's safety-belt dynamics, addressing a mechanistically important question in SMC biology. The central claim that DNA actively regulates safety-belt opening and closing is interesting and potentially significant. However, the evidence provided is entirely computational, and the manuscript does not include experimental validation. The link between the computational predictions and the biological process of loop extrusion remains largely inferential. The coarse-grained model involves several parameter choices that are justified primarily by comparison to experimental diffusion coefficients and bending angles, but the sensitivity of the conclusions to these choices is not fully explored. The manuscript is well written and the methodological approach is sophisticated, but the strength of the conclusions relative to the evidence base is a concern.
- **Who would be interested in the results, and why** Researchers studying SMC complexes, chromosome organization, loop extrusion mechanisms, and protein-DNA interactions. The multiscale simulation approach may also interest computational biophysicists developing methods for studying large protein-DNA assemblies. The potential connection to cohesin and Smc5/6 biology broadens the audience to the wider genome-architecture community.
- **Major strengths** The study addresses a mechanistically important and unresolved question in the condensin field. The multiscale approach is ambitious and appropriate for the problem. The authors make a genuine effort to connect their computational results to existing experimental data, including structural, biochemical, and single-molecule measurements. The identification of a non-monotonic dependence of entrapment kinetics on latch-buckle interaction strength is a nontrivial and potentially testable prediction. The manuscript is clearly written and the methods are described in substantial detail.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence strength
  - **Claim pointer** The manuscript claims that DNA "actively regulates" safety-belt dynamics, with DNA outside promoting opening and DNA inside promoting closure, and that this constitutes a mechanism for regulating loop extrusion.
  - **Evidence pointer** Figures 4B, 5B, 5D; Results section "Effect of Latch-buckle Interaction Strength on the Kinetics of DNA Entrapment and Diffusion along DNA"
  - **Concern** The central mechanistic claim rests entirely on coarse-grained simulations with a model that has been parameterized using a limited set of experimental observables. The authors do not provide experimental validation of the predicted bidirectional DNA effect. The claim that DNA "actively regulates" implies a level of biological causality that is not established by simulation alone. The coarse-grained model involves several approximations (e.g., removal of native contacts in the unstructured region, use of a loop-segment library, specific choices for electrostatic scaling) whose impact on the conclusions is not systematically tested. The authors state that conclusions are "robust across parameter ranges" but the evidence for this is not fully presented in the visible text.
  - **Why it matters** The central claim of the paper is that DNA plays an active regulatory role in safety-belt dynamics. If this claim is not supported by sufficiently strong evidence, the paper's main contribution is reduced to a computational prediction that requires experimental confirmation. The lack of experimental validation is particularly concerning given that the authors themselves identify testable predictions (e.g., mutational effects, single-molecule FRET experiments) that are not performed.
  - **Resolution test** The authors should either (a) provide experimental validation of at least one key prediction, (b) substantially strengthen the evidence that the computational results are robust to model parameter choices and independent of initial conditions, or (c) temper the claims to clearly present the results as predictions requiring experimental testing. Specifically, the claim that DNA "actively regulates" should be softened unless direct evidence for a regulatory mechanism is provided.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The manuscript claims that the rate-limiting step of DNA entrapment depends on the tightness of the safety belt, with a loose belt making closure rate-limiting and a tighter belt shifting the barrier to initial DNA entry.
  - **Evidence pointer** Figure 5B; Results section "Effect of Latch-buckle Interaction Strength on the Kinetics of DNA Entrapment and Diffusion along DNA"
  - **Concern** The kinetic analysis is based on mean first passage times extracted from coarse-grained simulations. The authors do not provide sufficient detail on how these times were computed, how convergence was assessed, or how statistical uncertainties were estimated. The claim of a non-monotonic dependence on εLB is based on comparing transition times across different parameter values, but the statistical significance of the differences is not reported. The number of independent simulations (n=50) is stated, but the effective sample size for rare transition events may be much smaller. The authors also do not discuss whether the observed kinetics are affected by the finite simulation time or by the specific choice of order parameter Q for defining states.
  - **Why it matters** The kinetic predictions are a key novel contribution of the paper. If the kinetic analysis is not statistically robust, the conclusions about rate-limiting steps and the proposed trade-off between capture and retention are not reliable. This directly affects the paper's ability to make testable predictions for experimental studies.
  - **Resolution test** The authors should provide a more detailed description of the kinetic analysis, including how transition times were extracted, how convergence was assessed, and what the statistical uncertainties are. They should also demonstrate that the qualitative conclusions (non-monotonic dependence, shift in rate-limiting step) are robust to the choice of analysis parameters and to the number of independent simulations.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility
  - **Claim pointer** The manuscript claims that the multiscale approach provides a "transferable way to quantify effective strain, contact dynamics, and loop flexibility in protein-DNA complex."
  - **Evidence pointer** Methods sections "PAE-Predicted Effective Strain", "All-atom MD Simulations", "CG MD simulations of Ycg1-Brn1 in Complex with DNA"
  - **Concern** The methods section describes the general approach but lacks sufficient detail for reproduction. Specific force field parameters, simulation box sizes, equilibration protocols, and analysis scripts are not provided. The coarse-grained model is described in the supplementary information, which was not provided for review. The authors state that "Complete CG model parameters and Ycg1-Brn1 simulation settings are provided in the Supplementary information" but this material is not accessible. Without access to these details, the reproducibility of the work cannot be assessed.
  - **Why it matters** Reproducibility is a core requirement for computational studies. If the model parameters and simulation protocols are not fully documented, other researchers cannot build on this work or verify the conclusions. This is particularly important given that the paper proposes a "transferable" approach.
  - **Resolution test** The authors should ensure that all model parameters, simulation protocols, and analysis scripts are made available, either in the supplementary information or through a public repository. The review process should include access to these materials.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 1
  - **Evidence pointer** Figure 1A-D
  - **Issue** The description of the effective strain calculation is dense and the figure caption is complex. The relationship between the effective strain and the physical concept of flexibility could be explained more clearly for a general readership.
  - **Required correction** Consider adding a brief intuitive explanation of what effective strain measures and why it is relevant to safety-belt function. Simplify the figure caption where possible.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Discussion of limitations
  - **Evidence pointer** Discussion section
  - **Issue** The discussion does not explicitly address the limitations of the computational approach, such as the approximations inherent in the coarse-grained model, the lack of explicit ATP hydrolysis, and the absence of the full condensin complex.
  - **Required correction** Add a paragraph acknowledging these limitations and discussing how they might affect the conclusions.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Presentation
  - **Affected element** Abstract
  - **Evidence pointer** Abstract
  - **Issue** The abstract states that DNA "actively regulates" safety-belt dynamics, which overstates the strength of the evidence given that the results are entirely computational.
  - **Required correction** Consider softening the language in the abstract to reflect that the results are computational predictions, e.g., "our simulations suggest that DNA actively regulates..."
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical detail
  - **Affected element** Methods, CG model parameterization
  - **Evidence pointer** Methods section "CG MD simulations of Ycg1-Brn1 in Complex with DNA"
  - **Issue** The choice of εHD = 0.6 is justified by comparison to experimental diffusion coefficients and bending angles, but the sensitivity of the conclusions to this specific value is not discussed in the main text.
  - **Required correction** Briefly state in the main text whether the qualitative conclusions hold for a range of εHD values around the chosen value.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Context
  - **Affected element** Introduction
  - **Evidence pointer** Introduction, paragraph 4
  - **Issue** The introduction mentions the "hold-and-feed" model and the distinction between topological and pseudotopological entrapment, but the connection between the safety-belt dynamics studied here and these models could be made more explicit.
  - **Required correction** Add a sentence or two clarifying how the present results relate to the hold-and-feed model and what specific aspect of that model is being addressed.

## Risk / unsupported claims
- The claim that DNA "actively regulates" safety-belt dynamics is not supported by direct experimental evidence and should be presented as a computational prediction.
- The claim that the rate-limiting step of DNA entrapment depends on belt tightness is based on kinetic analyses whose statistical robustness is not fully demonstrated.
- The claim that the coarse-grained model "closely matches experimental data" for diffusion coefficients and bending angles is based on a comparison to a range of published values, and the precision of this match is not quantified.
- The claim that phosphorylation could tune safety-belt dynamics is speculative and is presented as a hypothesis, which is appropriate, but the connection to specific experimental observations is not fully developed.
- The claim that the multiscale approach is "transferable" to other protein-DNA systems is not demonstrated beyond the present case study.
- The relationship between the coarse-grained simulation results and the actual loop extrusion process is not directly established, as the simulations do not include the full condensin complex or ATP hydrolysis.

## Assessment against Nature-style criteria
- **Originality** The study addresses a question that has not been directly tackled by previous computational work, and the bidirectional regulatory role of DNA in safety-belt dynamics is a novel concept. The multiscale approach combining AlphaFold3, all-atom MD, and CG MD is not entirely new but is applied here to a system and question that have not been studied this way. The originality is moderate to high.
- **Scientific importance** The question of how condensin captures and retains DNA during loop extrusion is of central importance to understanding chromosome organization. If the computational predictions are validated experimentally, the work could have significant impact. However, the lack of experimental validation currently limits the importance of the findings to the level of testable predictions.
- **Interdisciplinary readership** The topic is of interest to molecular biologists, biophysicists, and computational biologists. The manuscript is written in a way that is largely accessible to these groups, though some of the computational details may be challenging for experimentalists. The potential relevance to cohesin and Smc5/6 biology broadens the readership.
- **Technical soundness** The computational methods are sophisticated and generally appropriate for the questions addressed. However, the lack of detailed information about the coarse-grained model parameters and the limited statistical analysis of the kinetic results are concerns. The validation of the model against experimental data is reasonable but not exhaustive.
- **Readability for nonspecialists** The manuscript is clearly written and the figures are described in detail. However, the effective strain concept and the coarse-grained model details may be difficult for nonspecialists to follow. The abstract is accessible, but the results section requires substantial background knowledge.

## Recommendation posture
Currently not established from the provided evidence. The manuscript presents an interesting and potentially important computational study, but the central claims are not sufficiently supported by the evidence provided. The lack of experimental validation, the incomplete description of the coarse-grained model, and the limited statistical analysis of the kinetic results prevent the case from being fully established. The authors should either provide experimental validation of key predictions, substantially strengthen the computational evidence, or temper the claims to clearly present the results as predictions requiring experimental testing.