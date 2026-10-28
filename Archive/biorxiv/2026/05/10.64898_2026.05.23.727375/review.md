## Review setup
- **Input scope** Full manuscript text (abstract, main text, results sections, discussion, author contributions, declarations)
- **Assessment boundary** Scientific content, experimental logic, claims versus evidence, technical soundness, and presentation quality. No assessment of editorial fit or publication venue.
- **Shared manuscript claim summary** The authors claim that DNA superhelical polarity is the primary determinant of H-NS binding mode: positive supercoiling induces nucleoprotein filament formation at AT-rich loci, while negative supercoiling induces bridging. They further claim that H-NS dynamically switches between these modes in response to topological changes on a timescale of seconds, that the two modes are mechanistically distinct and genetically separable, and that this helicity-sensing mechanism drives self-organized chromosomal domain architecture with implications for gene silencing and stochastic regulation.
- **Visible evidence base** Main text figures referenced (Fig. 1a-1i, Fig. 2a-2i, Fig. 3a-3i, Fig. 4a-4e, Fig. 5a-5k), supplementary figures referenced (Fig. S1-S11), supplementary movies referenced (Movie S1-S9), and text descriptions of experimental procedures and results.
- **Missing materials affecting confidence** Figure panels and supplementary figures/movies were not provided for direct inspection. Quantitative details of image analysis, statistical methods, and control experiments are referenced but not fully described. Raw data and detailed experimental protocols are not available in the provided material.

## Reviewer
- **Overall assessment** This manuscript presents a compelling and potentially significant advance in understanding how H-NS, a paradigmatic bacterial nucleoid-associated protein, selects between its two known DNA-binding modes. The single-molecule approach is well conceived, and the central claim that DNA superhelical polarity acts as a switch between filament and bridging modes is novel and mechanistically plausible. The experiments are logically ordered, and the use of a genetically defined mutant to separate the two modes strengthens the argument. However, the provided text lacks sufficient experimental detail and direct figure inspection to fully verify the quantitative claims, particularly regarding plectoneme diffusion coefficients, the kinetics of mode switching, and the stochasticity of bridging site selection. The discussion is appropriately cautious in some areas but overreaches in others, particularly in extrapolating to in vivo transcriptional regulation without direct supporting data. Overall, the core finding is likely to be of broad interest to the bacterial chromosome biology and gene regulation communities, but the case would be substantially strengthened by additional methodological transparency and, ideally, complementary experiments addressing the structural basis of the proposed helicity sensing.

- **Who would be interested in the results, and why** Researchers studying bacterial chromosome organization, nucleoid-associated proteins, DNA supercoiling dynamics, and transcriptional regulation will find these results directly relevant. The work also speaks to the broader biophysics community interested in protein-DNA interactions and single-molecule approaches. The proposed mechanism, whereby a single protein reads torsional state to produce distinct architectural outcomes, offers a conceptual framework that could extend to other DNA-binding proteins, making the paper of interest to those studying chromatin biology in other organisms. The stochastic domain formation aspect will interest researchers working on phenotypic heterogeneity and gene expression noise in bacterial populations.

- **Major strengths** The single-molecule fluorescence approach with unlabeled H-NS is a methodological strength, avoiding artifacts from fluorescent protein tags. The use of topologically constrained DNA with defined sequence elements is well designed. The genetic separation of the two modes using the Y61D/M64D mutant is a powerful control. The demonstration of bidirectional switching in real time is convincing. The multi-locus experiment provides a compelling illustration of the proposed self-organizing principle.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors report mean plectoneme diffusion coefficients of D=12.88 ± 7.0 kbp²/s (Template-1) and 15.86 ± 7.6 kbp²/s (Template-2) on bare positively supercoiled DNA, and D=3.72 ± 1.41 kbp²/s on H-NS-bound Template-1.
- **Evidence pointer** Results section "H-NS filament acts as a topological barrier on positively supercoiled DNA", Fig. S2
- **Concern** The diffusion coefficients are reported with large standard deviations, and the method of calculation is not described. It is unclear whether these values represent ensemble averages over many molecules, time-averaged single-molecule trajectories, or a combination. The reduction from approximately 13-16 kbp²/s to 3.72 kbp²/s upon H-NS binding is interpreted as reflecting reduced accessible contour length, but without a detailed description of the tracking algorithm, the uncertainty in these values, and the statistical comparison between conditions, this quantitative claim cannot be fully evaluated. Additionally, the large spread in the bare DNA values (standard deviation approximately 50% of the mean) raises questions about the precision of the measurement and whether the reported difference is statistically robust.
- **Why it matters** The quantitative comparison of plectoneme dynamics before and after H-NS binding is central to the claim that filaments act as topological barriers. If the measurement uncertainty is as large as the reported standard deviations suggest, the conclusion that H-NS binding reduces diffusion by approximately 4-fold may not be statistically secure.
- **Resolution test** Provide a detailed description of the particle tracking and diffusion coefficient calculation methods, including the number of molecules analyzed, the number of trajectories, the time window used for MSD analysis, and the statistical test used to compare conditions. Report confidence intervals or effect sizes. Ideally, show representative individual trajectories and the distribution of diffusion coefficients across molecules.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that on negatively supercoiled DNA, H-NS "entirely switches into bridging mode" and that this is evidenced by "predominantly single static plectonemes as persistent, high-intensity puncta precisely at the AT-rich locus."
- **Evidence pointer** Results section "H-NS entirely switches into bridging mode on negatively supercoiled DNA", Fig. 3d-3i, Fig. S3
- **Concern** The claim of an "entire" switch to bridging mode is strong, but the evidence presented in the text is primarily qualitative. The authors report a "clear preference" for AT-rich regions in plectoneme density profiles and a "near-complete immobilization" with D=0.23 ± 0.3 kbp²/s. However, the text does not describe how the authors distinguished between a plectoneme stabilized by H-NS bridging versus a plectoneme that is simply trapped or kinetically slowed by the presence of bound protein. The possibility that H-NS binding alters plectoneme dynamics through non-specific friction or altered DNA flexibility, rather than through specific bridging interactions, is not addressed. The claim that bridging is the exclusive mode on negatively supercoiled DNA requires direct evidence that the observed puncta correspond to H-NS cross-links between two duplexes.
- **Why it matters** The central thesis of the paper is that superhelical polarity selects between two distinct binding modes. If the "bridging" observed on negatively supercoiled DNA could be explained by alternative mechanisms, the specificity of the proposed switch is weakened.
- **Resolution test** Provide additional evidence for bridging, such as: (1) direct visualization of H-NS localization at the plectoneme tip or junction using a minimally perturbing label; (2) experiments with a mutant that specifically disrupts the bridging interface but not DNA binding; (3) force or stiffness measurements that distinguish cross-linked from non-cross-linked plectonemes; or (4) a quantitative analysis showing that the fraction of plectonemes immobilized by H-NS is consistent with a specific bridging model.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that "helicity-driven mode selection produces self-organized 'chromosomal' architecture" and that "in a clonal bacterial population, this mechanism predicts that different cells will silence different genes despite identical DNA sequence and identical H-NS levels, a physical topology-driven source of cell-to-cell heterogeneity in gene silencing."
- **Evidence pointer** Results section "Helicity-driven mode selection drives self-organized chromosomal domain formation", Fig. 5f-5k, Fig. S9
- **Concern** The multi-locus experiment is intriguing, but the claim of "self-organized chromosomal architecture" and the extrapolation to population-level heterogeneity in gene silencing extends beyond the presented data. The experiment demonstrates that on a single 21 kb DNA molecule with multiple AT-rich loci, some sites form bridges and others form filaments, and that the choice is stochastic. However, the text does not describe how the authors quantified the stochasticity, how many molecules were observed, or whether the distribution of bridging sites matched a random expectation. The leap from a single-molecule in vitro observation to predictions about clonal bacterial populations is substantial and not supported by direct experimental evidence in this manuscript.
- **Why it matters** The claim of stochastic domain formation with functional consequences for population heterogeneity is a significant and exciting extension of the work. However, if this claim is not rigorously supported, it risks overstating the implications of the findings.
- **Resolution test** Provide a quantitative analysis of the stochasticity of bridging site selection across many molecules, including a statistical test against a null model. If possible, perform experiments with different numbers or arrangements of AT-rich loci to test the predictions of the self-organization model. Alternatively, temper the claims about population-level consequences and present them as speculative implications rather than direct findings.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "H-NS can sense and switch between modes within seconds responding to topology changes" and that "the kinetics of the intensity transition is slower than the rate of supercoiled DNA relaxation, indicating that the topological change itself drives the mode switch and that H-NS reorganization is rate-limiting."
- **Evidence pointer** Results section "H-NS senses changes in DNA helicity and switches binding modes in real-time", Fig. 4a-4e, Fig. S8
- **Concern** The switching experiments are conceptually important, but the text provides limited quantitative detail. The authors report that the transition occurs over "seconds" and that it is "slower than the rate of supercoiled DNA relaxation," but no quantitative comparison is provided. The washing experiments (Fig. S8g-S8j) are described as showing that switching does not require free protein, but the text does not describe how the authors confirmed that all free H-NS was removed, nor how they distinguished between H-NS that remained bound versus H-NS that dissociated and rebinding was prevented.
- **Why it matters** The claim that H-NS can dynamically switch modes in response to topological changes is a key finding. If the kinetics are not rigorously characterized, or if the washing experiments are not convincingly controlled, the strength of this claim is diminished.
- **Resolution test** Provide quantitative kinetic data, including the time constant of the intensity transition and a direct comparison to the relaxation rate. Describe the washing protocol in detail, including how wash efficiency was verified. Consider performing a control experiment with a fluorescently labeled H-NS to directly track protein localization during the switch.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction
- **Evidence pointer** Main text, first paragraph
- **Issue** The terms "stiffening mode" and "bridging mode" are introduced without a brief physical description of what these modes look like at the molecular level. A nonspecialist reader may struggle to visualize the difference.
- **Required correction** Add one or two sentences describing the structural arrangement of H-NS on DNA in each mode (e.g., "in stiffening mode, H-NS polymerizes along the DNA minor groove, forming a rigid filament; in bridging mode, H-NS cross-links two separate DNA duplexes").

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, "H-NS forms nucleoprotein filaments at AT-rich loci on relaxed DNA"
- **Evidence pointer** Fig. 1e-1g
- **Issue** The text states that "A distinct decrease in fluorescence intensity was observed precisely at the AT-rich region" but does not describe how the authors controlled for potential sequence-dependent differences in SxO staining intensity in the absence of H-NS.
- **Required correction** State explicitly whether the fluorescence intensity of bare DNA was uniform across the AT-rich and non-AT-rich regions, or describe a normalization procedure used to account for any intrinsic intensity differences.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, "H-NS filament acts as a topological barrier on positively supercoiled DNA"
- **Evidence pointer** Fig. 2d-2i
- **Issue** The text reports that plectonemes are "fully excluded" from the H-NS filament zone, but the resolution of the imaging system and the criteria for "exclusion" are not defined. It is unclear whether the authors mean that no plectoneme signal was detected above background, or that the signal was reduced below a threshold.
- **Required correction** Define the detection threshold for plectoneme occupancy and describe how the exclusion zone was determined relative to the filament position.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Discussion
- **Evidence pointer** Main text, Discussion, paragraph 3
- **Issue** The discussion of the twin-supercoiling domain model and the prediction that H-NS "immediately downstream of an elongating polymerase would adopt filament mode" is presented without a clear explanation of why this matters for gene regulation.
- **Required correction** Briefly explain the functional consequence of filament versus bridging mode for transcription (e.g., "filament mode may act as a roadblock to RNA polymerase, while bridging mode may sequester promoter regions").

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, "H-NS senses changes in DNA helicity and switches binding modes in real-time"
- **Evidence pointer** Fig. 4a-4e
- **Issue** The text states that "the same H-NS molecules that were bridging on underwound DNA can reorganize into a stiffening filament within seconds as the DNA becomes relaxed." This implies that the same protein molecules remain bound throughout the transition, but the imaging approach (SxO exclusion) does not directly track individual H-NS molecules.
- **Required correction** Soften the language to "H-NS molecules that were bridging" or "the population of H-NS molecules" to avoid implying single-molecule tracking that was not performed.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Main text, Discussion, paragraph 4
- **Issue** The comparison to GapR is interesting but brief. The statement that GapR shows "the opposite topology preference" could be expanded to clarify whether this is a direct experimental observation or an inference from the literature.
- **Required correction** Add a citation or a brief description of the GapR experiment that demonstrates its preference for positively supercoiled DNA.

- **Technical failings that need to be addressed before the case is established** The quantitative analysis of plectoneme diffusion coefficients (R1-M1) and the evidence for exclusive bridging on negatively supercoiled DNA (R1-M2) are the most significant technical gaps. The lack of detailed methods for image analysis, particle tracking, and statistical comparisons undermines the ability to fully evaluate the central claims. The washing experiments (R1-M4) also require more rigorous controls.

- **Assessment against Nature-style criteria**
  - Originality: High. The idea that DNA superhelical polarity, rather than ionic conditions or sequence alone, is the primary switch for H-NS binding mode is novel and not previously demonstrated. The single-molecule approach to directly visualize this switch is innovative.
  - Scientific importance: High. H-NS is a central regulator of bacterial gene silencing and chromosome organization. Resolving the long-standing question of what controls its binding mode has broad implications for understanding bacterial physiology, virulence, and chromosome dynamics. The proposed mechanism could also inform studies of other nucleoid-associated proteins.
  - Interdisciplinary readership: Moderate to high. The work bridges single-molecule biophysics, bacterial molecular biology, and gene regulation. The conceptual framework of a protein reading DNA superhelicity to switch functions will appeal to biophysicists and molecular biologists alike. The implications for stochastic gene expression may attract interest from systems biologists.
  - Technical soundness: Moderate. The experimental design is sound, and the use of unlabeled protein and a genetic mutant is commendable. However, the lack of detailed quantitative methods and the absence of direct structural evidence for the proposed mode-switching mechanism limit the current technical rigor. The large uncertainties in the reported diffusion coefficients are a concern.
  - Readability for nonspecialists: Moderate. The text is generally clear, but the introduction of specialized terms and the density of single-molecule methodology may pose challenges for readers outside the biophysics community. The discussion of in vivo implications is accessible but could be better connected to the experimental findings.

- **Recommendation posture** Supportive if technical concerns are resolved. The core finding is novel and likely correct, but the manuscript in its current form does not provide sufficient quantitative detail to fully establish the case. The authors should address the concerns regarding diffusion coefficient analysis, provide more rigorous evidence for the exclusivity of bridging on negatively supercoiled DNA, and clarify the kinetics of the mode switch. If these issues are resolved, the paper would be a strong candidate for publication in a high-impact journal.

## Risk / unsupported claims
- The claim that H-NS "entirely switches into bridging mode" on negatively supercoiled DNA is not fully supported by the provided evidence, as the text does not rule out alternative explanations for plectoneme immobilization.
- The extrapolation from the multi-locus experiment to "self-organized chromosomal architecture" and predictions about population-level heterogeneity in gene silencing extends beyond the direct experimental evidence.
- The statement that "the topological change itself drives the mode switch" is inferred from the observation that the transition is slower than DNA relaxation, but no direct causal evidence is provided.
- The claim that the observed effects are independent of ionic conditions is stated but not quantitatively supported in the provided text.
- The comparison to GapR and the broader claim that "supercoiling polarity sensing may be a broader organizing principle among DNA-binding proteins" is speculative and not directly tested in this work.