## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, limitations, materials and methods, and supplementary materials description.
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text. No external data or unpublished materials were consulted.
- **Shared manuscript claim summary** The authors use single-molecule tracking (SMT) with a machine learning classifier (pEMv2) to identify two distinct low-mobility chromatin states for histone H2B and multiple transcriptional regulators. They report that ligand activation increases the proportion of steroid receptors in the lowest-mobility state, that individual molecules can switch between states on second timescales, and that intact DNA-binding and oligomerization domains are required for engagement with the lowest-mobility state. They propose a two-state model of chromatin mobility relevant to transcriptional activation.
- **Visible evidence base** Figures 1–6 and supplementary figures S1–S11 are referenced but not provided in the submitted text. Methods descriptions for SMT, pEMv2, RL analysis, Spot-On fitting, and photobleaching correction are present. Quantitative results are described in text but numerical values for many key comparisons are not fully reported.
- **Missing materials affecting confidence** All figures, tables, and supplementary materials are referenced but not included. This prevents independent verification of the primary data, statistical analyses, and the quality of the single-molecule tracks. Specific numerical values for population fractions, transition probabilities, and statistical tests are largely absent from the text.

## Reviewer
- **Overall assessment** This manuscript addresses a fundamental question in gene regulation: how chromatin dynamics relate to transcriptional activity. The use of long-timescale SMT combined with machine learning to identify two low-mobility chromatin states is a valuable methodological contribution. The observation that steroid receptors shift toward the lowest-mobility state upon activation, and that this requires intact DNA-binding and oligomerization domains, is potentially important. However, the absence of the actual figures and quantitative data in the provided material limits the ability to fully assess the robustness of the claims. The conceptual model proposed is interesting but would benefit from clearer distinction between correlation and causation, particularly regarding whether TF binding actively remodels chromatin or simply selects a pre-existing state.
- **Who would be interested in the results, and why** Researchers in transcription regulation, chromatin biology, and single-molecule biophysics. The work provides a framework for classifying chromatin-bound factor mobility that could be broadly applicable. The finding that activation shifts steroid receptors into a specific low-mobility state has implications for understanding nuclear receptor function and could interest those studying hormone-responsive gene networks.
- **Major strengths** The study addresses a long-standing question with a technically challenging approach. The use of long imaging times (up to 2 minutes) to capture slow dynamics is a strength compared to faster SMT studies. The combination of pEMv2 with RL analysis and Spot-On provides cross-validation of the identified states. The inclusion of multiple transcriptional regulators and two cell lines strengthens the generality of the observations. The mutational analysis of PPARγ2 provides mechanistic insight into the determinants of state occupancy.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of quantitative data), R1-M2 (causality), R1-M3 (2D imaging limitations), R1-M4 (photobleaching correction).
- **Assessment against Nature-style criteria**  
  *Originality*: The identification of two distinct low-mobility states that are dynamically interconverted is a novel contribution, though related two-state models for chromatin have been proposed. The specific application to steroid receptor activation is new.  
  *Scientific importance*: The findings have the potential to influence how the field thinks about TF-chromatin interactions and transcriptional activation. If the model is correct, it provides a unifying framework for understanding how diverse TFs engage with chromatin.  
  *Interdisciplinary readership*: The work will appeal to molecular biologists, biophysicists, and computational biologists. The methodological aspects (pEMv2, RL analysis) may interest method developers. The conceptual model is accessible.  
  *Technical soundness*: The methods are generally well described, but the absence of figures and quantitative data prevents full assessment. The controls for tracking errors are thoughtful. The use of multiple analysis methods is a strength.  
  *Readability for nonspecialists*: The manuscript is clearly written and the logic is easy to follow. The limitations section is honest and helpful. Some terminology (e.g., "low-mobility states") is introduced clearly.
- **Recommendation posture** Supportive if technical concerns are resolved. The core observations are potentially significant, but the manuscript as provided (without figures and full quantitative reporting) does not yet establish the case. The authors should provide the missing data and address the concerns about causality and 2D imaging limitations.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The manuscript claims that "histone H2B and multiple chromatin-bound transcriptional regulators display two distinct low-mobility states" and that "ligand activation results in a marked increase in the propensity of steroid receptors to bind in the lowest-mobility state."
- **Evidence pointer** Figures 1–6 and supplementary figures S1–S11, location not provided
- **Concern** The manuscript text describes the results qualitatively but does not provide the actual figures or tables. Key quantitative information is missing, including: the exact population fractions of states 1 and 2 for each protein and condition; the statistical significance of differences between conditions; the number of cells, tracks, and sub-tracks analyzed; and the parameters of the pEMv2 fits. Without these data, the central claims cannot be independently evaluated.
- **Why it matters** The conclusions rest entirely on the identification and quantification of the two states. If the population fractions or the differences between conditions are not robustly quantified and statistically tested, the main claims are not supported.
- **Resolution test** Provide all figures and supplementary figures with full axis labels, error bars, and statistical annotations. Report the number of biological replicates, cells, tracks, and sub-tracks for each condition. Include a table with the population fractions, diffusion coefficients, and transition probabilities for all proteins and conditions, with confidence intervals and p-values.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation
- **Claim pointer** The manuscript states that "the mobility of TFs is intimately coupled with their binding dynamics" and proposes that "binding of activated SR to chromatin constrains its mobility and/or activated SRs are more capable of interacting with chromatin in state 1."
- **Evidence pointer** Results sections "SRs exhibit the same two low-mobility states as H2B" and "PPARγ2 requires an intact DNA binding and oligomerization domain to bind to state 1 chromatin", location not provided
- **Concern** The manuscript presents correlative evidence that activation increases the proportion of receptors in state 1, but does not establish causality. The authors acknowledge this in the discussion, but the abstract and results sections present the relationship more definitively. The mutational analysis shows that DBD and HET are required for state 1 occupancy, but this does not distinguish between the possibilities that (a) the receptor actively remodels chromatin to a lower-mobility state, or (b) the receptor preferentially binds to pre-existing low-mobility chromatin. The authors mention this ambiguity but do not design experiments to address it.
- **Why it matters** The proposed model has different implications depending on the direction of causality. If the receptor actively remodels chromatin, this would be a novel mechanism. If the receptor simply selects a pre-existing state, the finding is less mechanistically surprising.
- **Resolution test** Perform experiments that can distinguish between these possibilities, such as measuring chromatin mobility at specific loci before and after receptor activation, or using mutants that separate DNA binding from chromatin remodeling activities. Alternatively, temper the language in the abstract and results to clearly state that the relationship is correlative.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical limitation
- **Claim pointer** The manuscript claims that "individual H2B and bound-TF molecules can dynamically switch between them on time scales of seconds" and that "single bound-TF molecules with different mobilities exhibit different dwell time distributions."
- **Evidence pointer** Results sections "Chromatin mobility is characterized by dynamic switching between two distinct low-mobility states" and "Tracks with different exploration radii exhibit different switching characteristics and dwell times", location not provided
- **Concern** The imaging is performed in 2D (HILO microscopy), and the authors acknowledge in the limitations that 2D projection can make diffusing molecules appear confined. This is a significant concern for the interpretation of the two low-mobility states. A molecule diffusing in 3D could appear to be in a low-mobility state when its motion is projected onto the 2D imaging plane. The authors argue that the probability of a freely diffusing molecule remaining in the focal volume is very low, but this does not fully address the issue of molecules that are partially confined or moving along the z-axis.
- **Why it matters** If the two states are artifacts of 2D projection, the entire model collapses. The authors need to provide stronger evidence that the two states represent genuine differences in chromatin mobility rather than projection effects.
- **Resolution test** Perform 3D tracking experiments (e.g., using astigmatism-based or multiplane imaging) to confirm that the two states are observed in 3D. Alternatively, provide simulations showing that 2D projection of 3D diffusion cannot produce the observed bimodal distribution of mobilities.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodology
- **Claim pointer** The manuscript claims that "photobleaching prevents rapid imaging for long times" and that the authors "estimated the probability of a freely diffusing molecule to remain within our focal volume within our sampling interval of 200 ms to be <10−9."
- **Evidence pointer** Materials and Methods, "Defocalization probability" section, location not provided
- **Concern** The photobleaching correction is described, but the details of how the correction was applied to the survival distributions and how it affects the interpretation of the dwell times are not fully explained. The authors state that the photobleaching rate was estimated from the slowest exponential component of the H2B survival distribution, but it is not clear how this was validated or whether it is appropriate for all proteins and conditions.
- **Why it matters** If the photobleaching correction is inaccurate, the dwell time distributions and the conclusions about binding dynamics could be wrong.
- **Resolution test** Provide a more detailed description of the photobleaching correction, including validation experiments (e.g., comparing corrected and uncorrected survival distributions). Show that the correction does not qualitatively change the conclusions.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that "these states are not spatially separated as previously believed." This is a strong claim that is not fully supported by the data, given the 2D imaging limitations. The authors themselves acknowledge in the limitations that they cannot rule out smaller-scale spatial separation in 3D.
- **Required correction** Soften the language to "these states do not appear to be spatially separated on the length scales probed in this study" or similar.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, "PPARγ2 requires an intact DNA binding and oligomerization domain" section
- **Evidence pointer** Results, location not provided
- **Issue** The authors state that the DBD and HET mutants "abrogate transcriptional responses" but do not provide the data or a reference for this claim. It is important to know whether the mutants are truly transcriptionally inactive in the same cell type and conditions used for the SMT experiments.
- **Required correction** Provide the transcriptional activity data for the mutants, either in the main text or as a supplementary figure, or cite the relevant reference.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, "SRs exhibit the same two low-mobility states as H2B" section
- **Evidence pointer** Results, location not provided
- **Issue** The text reports fold changes in population fractions (e.g., "10-fold for GR") but does not report the absolute values or the variability across replicates. This makes it difficult to assess the robustness of the effect.
- **Required correction** Report the absolute population fractions with standard errors or confidence intervals for each condition, and state the number of independent experiments.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Discussion
- **Evidence pointer** Discussion, location not provided
- **Issue** The term "chromatin exploration domain" (CED) is introduced in the discussion but is not defined precisely. It is unclear whether this is a physical domain or a statistical construct.
- **Required correction** Define CED clearly, including how it is calculated from the data and what physical interpretation is intended.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Materials and Methods, "Tracking" section
- **Evidence pointer** Materials and Methods, location not provided
- **Issue** The tracking algorithm (TrackRecord v6) is described as custom and publicly available, but the specific parameters used for tracking (e.g., maximum gap, minimum track length) are not stated in the text.
- **Required correction** Provide the specific tracking parameters used for the analyses reported in the paper.

## Risk / unsupported claims
- The claim that "these states are not spatially separated as previously believed" is not fully supported given the 2D imaging limitations and the lack of 3D control experiments.
- The claim that "the mobility of TFs is intimately coupled with their binding dynamics" is presented as a conclusion but is only correlative.
- The claim that "binding in state 1 requires an intact DNA binding domain and oligomerization domains" is supported by the mutational analysis, but the mechanism (whether the receptor actively remodels chromatin or selects a pre-existing state) is not established.
- The quantitative values for population fractions, transition probabilities, and dwell times are not provided in the text, making these claims unverifiable from the submitted material.
- The photobleaching correction method is described but not validated in the provided text.