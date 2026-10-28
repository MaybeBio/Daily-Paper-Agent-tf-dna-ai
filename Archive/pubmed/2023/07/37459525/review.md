## Review setup
- **Input scope** Full manuscript text (main text, methods, and supplementary figure legends as provided)
- **Assessment boundary** Scientific claims, experimental design, data analysis, and interpretation as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors propose that after transcribing an operon, bacterial RNA polymerase can remain bound to DNA, slide along it, and reinitiate transcription of nearby operons, thereby coupling their transcriptional activities. They combine a theoretical model with single-molecule experiments to estimate key kinetic parameters and predict that this coupling can be efficient over genomic distances typical of bacterial operon spacing.
- **Visible evidence base** Theoretical derivations (Eqs. 1-11), single-molecule dwell time measurements (Fig. 3), parameter estimates (Table 2), stochastic simulations (Fig. 4A), and genome-wide distance analysis (Fig. 4C)
- **Missing materials affecting confidence** Full supplementary information (SI Appendix sections S1-S4, Figs. S1-S10, Tables S1-S3) is referenced but not provided in the submitted text. Raw data traces and detailed fitting procedures are not fully described. The experimental validation of the coupling mechanism itself (as opposed to parameter measurement) is not directly demonstrated.

## Reviewer

### Overall assessment
This manuscript presents a theoretically grounded and experimentally parameterized model for transcriptional coupling between adjacent bacterial operons via posttermination sliding of RNA polymerase. The combination of single-molecule measurements with analytical theory is appropriate and the parameter estimates are potentially valuable. However, the central claim that this mechanism can couple transcription of nearby operons in vivo rests on extrapolations from in vitro measurements and simplifying assumptions that are not fully tested. The work is likely to be of interest to the bacterial transcription community, but the strength of the conclusions relative to the evidence should be tempered.

### Who would be interested in the results, and why
Researchers studying bacterial transcription regulation, particularly those interested in mechanisms of transcriptional coupling, operon organization, and the role of RNA polymerase recycling. The work may also appeal to biophysicists studying protein-DNA interactions and single-molecule approaches to transcription. The potential implications for synthetic biology and the design of genetic circuits would interest a broader audience in biotechnology.

### Major strengths
1. The theoretical framework is clearly developed and provides testable predictions.
2. The single-molecule experiments are well designed to measure the relevant kinetic parameters.
3. The authors acknowledge and address potential complications (e.g., multiple RNAP binding, surface effects).
4. The genome-wide analysis grounds the predictions in realistic biological distances.
5. The discussion of σ70's dual role (stimulating dissociation yet required for promoter capture) is insightful.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation of the proposed mechanism
- **Claim pointer** The manuscript claims that "reinitiation may provide a mechanism to orchestrate the transcriptional activities of groups of nearby operons" and that the mechanism is "expected to be common and efficient for physiological ranges of terminator-promoter spacings and σ70 concentrations."
- **Evidence pointer** Fig. 4A-B, Discussion section
- **Concern** The central claim of the paper is that posttermination sliding can couple transcription of nearby operons. However, the experiments presented measure dwell times of RNAP on promoterless DNA templates, not actual reinitiation events at a downstream promoter. The model assumes that every encounter of the RNAP-σ70 complex with a promoter is productive, and the authors state that relaxing this assumption to 1% productivity gives "essentially identical" results (SI Appendix, Fig. S9). This is surprising and should be explained more carefully. More importantly, no direct experimental demonstration of reinitiation via sliding is provided. The connection between the measured parameters and the predicted coupling efficiency relies entirely on the theoretical model.
- **Why it matters** Without direct experimental evidence of sliding-mediated reinitiation, the biological significance of the measured parameters remains speculative. The claim that this mechanism can couple operon transcription in vivo requires experimental support or at least a more explicit acknowledgment of the extrapolative nature of the predictions.
- **Resolution test** Provide direct experimental evidence of reinitiation via sliding, for example by using a dual-promoter construct where reinitiation can be distinguished from de novo initiation. Alternatively, clearly frame the predictions as model-based extrapolations requiring in vivo validation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Parameter estimation and model identifiability
- **Claim pointer** The manuscript claims to measure kb, koff, and koff,s from dwell time distributions, with values reported in Table 2.
- **Evidence pointer** Fig. 3C-D, Table 2, SI Appendix S4
- **Concern** The dwell time distributions are described as requiring a sum of three exponentials, suggesting at least three types of RNAP-σ70-DNA complexes. The authors attribute the fastest component to σ70-induced dissociation and use this to extract kb, koff, and koff,s. However, the physical origin of the intermediate and slow components is not fully explained, and the assignment of the fast component to the model in Fig. 1 is based on its hyperbolic dependence on [σ70]. The possibility that the fast component represents a subpopulation of RNAP with different properties (e.g., different conformation or labeling state) is not fully excluded. The global fitting procedure is described but the identifiability of the three parameters from the data is not discussed.
- **Why it matters** If the parameter estimates are not uniquely determined by the data, the subsequent predictions of coupling efficiency and distance inherit this uncertainty. The biological conclusions depend critically on the accuracy of these parameters.
- **Resolution test** Perform a parameter identifiability analysis (e.g., profile likelihood) to demonstrate that kb, koff, and koff,s are uniquely determined by the data. Alternatively, provide independent measurements of at least one parameter to cross-validate the estimates.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Assumption of equal diffusion coefficients
- **Claim pointer** The model assumes that the diffusion coefficient of RNAP-σ70 complex on DNA is the same as that of RNAP alone, since "reliable measurements of the former are not available."
- **Evidence pointer** Model description, Fig. 1
- **Concern** The diffusion coefficient D = (3.9 ± 0.5) × 10^4 bp²/s was measured for posttermination RNAP in a previous study (ref. 16). The authors assume that σ70 binding does not change the diffusion coefficient. This is a significant assumption because σ70 binding could alter the conformation of RNAP and its interaction with DNA, potentially changing its sliding behavior. If the diffusion coefficient of the RNAP-σ70 complex is different, the predicted coupling distances and efficiencies would change accordingly.
- **Why it matters** The predicted coupling distance scales as sqrt(D/koff,s). If the diffusion coefficient of the RNAP-σ70 complex is, for example, 2-fold lower than assumed, the coupling distance would decrease by approximately 30%, potentially changing the biological conclusions.
- **Resolution test** Measure the diffusion coefficient of the RNAP-σ70 complex directly, or perform a sensitivity analysis showing how the conclusions depend on this parameter.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** In vivo relevance of measured parameters
- **Claim pointer** The manuscript states that "the free σ70 concentration in the cell could be either above or below [σ70]c, which we calculate to be 0.4 μM" and that at 5 μM free σ70, coupling is efficient at distances up to 1000 bp.
- **Evidence pointer** Fig. 4B-C, Discussion
- **Concern** The predictions of in vivo coupling efficiency rely on the assumption that the in vitro measured parameters (kb, koff, koff,s, D) are applicable in the cellular context. However, the intracellular environment contains many factors that could affect RNAP sliding and σ70 binding, including nucleoid-associated proteins, other DNA-binding proteins, macromolecular crowding, and the presence of other RNAP molecules. The authors briefly mention that some protein binding sites might obstruct sliding, but this is not quantitatively addressed. Additionally, the free σ70 concentration in vivo is not directly measured but inferred from total σ70 levels and regulation by anti-σ factors.
- **Why it matters** The biological significance of the proposed mechanism depends on whether the predicted coupling actually occurs in cells. If the in vivo parameters differ substantially from the in vitro measurements, the conclusions may not hold.
- **Resolution test** Perform in vivo experiments to test for coupling between adjacent operons, for example by measuring transcriptional correlation between neighboring operons under conditions where σ70 availability is modulated. Alternatively, incorporate known in vivo factors into the model to assess their impact on the predictions.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of model assumptions
- **Affected element** Model description, Fig. 1
- **Evidence pointer** Model section
- **Issue** The model assumes that σ70 binding to sliding RNAP is irreversible. While the authors justify this based on previous measurements, the potential consequences of reversible binding are not discussed. If σ70 unbinding occurs on timescales comparable to sliding, the model predictions could change.
- **Required correction** Briefly discuss the validity of the irreversibility assumption and its potential impact on the conclusions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical treatment of censored data
- **Affected element** Dwell time analysis
- **Evidence pointer** CoSMoS Data Analysis section
- **Issue** The authors state that censored data were jointly fit with uncensored data using maximum likelihood, which is appropriate. However, the fraction of censored events and its potential impact on parameter estimates is not reported.
- **Required correction** Report the fraction of censored events in each experiment and discuss whether this could bias the parameter estimates.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Genome-wide analysis details
- **Affected element** Fig. 4C
- **Evidence pointer** Genome-Wide Analysis section
- **Issue** The genome-wide analysis measures distances from operon-ending terminators to the nearest operon-initial promoter. It is not clear whether this accounts for the direction of transcription (i.e., whether the promoter is downstream of the terminator on the same strand). If promoters on the opposite strand are included, the distances may not be relevant for the proposed mechanism.
- **Required correction** Clarify whether only same-strand, downstream promoters were considered, and if not, discuss the potential impact on the analysis.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Comparison with previous work
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The manuscript cites previous work on RNAP sliding and reinitiation but does not quantitatively compare the present results with previous estimates of sliding parameters or coupling efficiencies.
- **Required correction** Add a brief quantitative comparison with relevant previous studies to contextualize the new measurements.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout
- **Evidence pointer** Various sections
- **Issue** The terms "RNAP-σ70 complex" and "holoenzyme" are used somewhat interchangeably. While the authors note the distinction between RNAP-σ70-DNA (formed by σ70 binding to DNA-bound RNAP) and holoenzyme-DNA (formed by σ70RNAP binding to DNA), the terminology could be confusing.
- **Required correction** Use consistent terminology throughout, or define the terms clearly at first use.

### Technical failings that need to be addressed before the case is established
1. The lack of direct experimental demonstration of sliding-mediated reinitiation (R1-M1) is the most significant gap. The current evidence supports the parameterization of the model but not the central biological claim.
2. The assumption of equal diffusion coefficients for RNAP and RNAP-σ70 (R1-M3) needs to be addressed, either through direct measurement or sensitivity analysis.
3. The identifiability of the kinetic parameters from the dwell time distributions (R1-M2) should be demonstrated.

### Assessment against Nature-style criteria
- **Originality**: The concept of transcriptional coupling via posttermination sliding is not entirely new, but the quantitative framework and the systematic measurement of the relevant kinetic parameters represent a valuable contribution. The idea that σ70 has opposing effects on coupling is a novel insight.
- **Scientific importance**: If the proposed mechanism operates in vivo, it would have significant implications for understanding bacterial gene regulation, particularly the organization of operons and the coordination of transcriptional activity. The work could also inform synthetic biology design. However, the in vivo relevance remains to be demonstrated.
- **Interdisciplinary readership**: The work bridges single-molecule biophysics, theoretical modeling, and bacterial transcription. It would appeal to researchers in these fields, but the presentation is likely too specialized for a broad interdisciplinary audience. The significance statement helps, but the main text assumes substantial background knowledge.
- **Technical soundness**: The experimental design and data analysis are generally sound, with appropriate controls and statistical treatment. The theoretical model is clearly derived. However, the key assumptions (equal diffusion coefficients, irreversible σ70 binding, productive promoter encounters) need further justification or sensitivity analysis.
- **Readability for nonspecialists**: The manuscript is clearly written but technically dense. The significance statement is accessible, but the main text would be challenging for readers without a background in transcription or single-molecule methods. Figures appear well designed, though the full figure content could not be assessed from the text alone.

### Recommendation posture
**Supportive if technical concerns are resolved.** The manuscript presents a well-executed combination of theory and experiment that provides quantitative estimates of parameters relevant to a potentially important mechanism of transcriptional regulation. However, the central claim that this mechanism can couple transcription of nearby operons in vivo is not directly supported by the presented experiments. The authors should either provide direct experimental evidence of sliding-mediated reinitiation or substantially temper their conclusions and clearly frame the predictions as model-based extrapolations requiring in vivo validation. The assumption of equal diffusion coefficients should also be addressed.

## Risk / unsupported claims
1. The claim that "reinitiation is expected to be common and efficient for physiological ranges of terminator-promoter spacings and σ70 concentrations" is a model-based prediction that is not directly validated by experiments. The assumption that every promoter encounter is productive is acknowledged but the robustness of this assumption is only briefly addressed.
2. The claim that the measured rate constants (kb, koff, koff,s) are relevant for the in vivo situation is not directly supported. The experiments use purified components in vitro, and the applicability to the cellular context is assumed.
3. The statement that "the value obtained for koff,s is an order of magnitude smaller than the value obtained for k1D... suggests that the RNAP-σ70-DNA complex and the holoenzyme-DNA complex have different conformations" is speculative. While plausible, this conclusion is not directly supported by structural or other conformational data.
4. The genome-wide analysis (Fig. 4C) shows the distribution of terminator-promoter distances but does not directly demonstrate that coupling occurs at these distances in vivo. The connection between the distance distribution and the predicted coupling efficiency is indirect.
5. The assumption that the diffusion coefficient of RNAP-σ70 is the same as that of RNAP alone is stated without direct evidence and could affect the quantitative predictions.