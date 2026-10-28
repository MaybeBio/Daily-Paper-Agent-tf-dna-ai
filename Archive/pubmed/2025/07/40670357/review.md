## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, methods, and figure legends
- **Assessment boundary** Scientific validity, methodological rigor, reproducibility, and significance of claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors present a multi-scale ensemble deep learning approach to infer absolute developmental time with 1-minute resolution from nuclear morphology in fixed Drosophila embryos. They apply this to resolve spatiotemporal regulation of Krüppel by Bicoid and Hunchback, and uncover unsteady-state bursty kinetics of hunchback transcription using time-resolved single-molecule mRNA statistics.
- **Visible evidence base** Main text figures 1-5 with legends, methods section, statistical descriptions, supplementary figure references
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; Supplementary Note 1 (mathematical modeling details) not provided; source data files not provided; code availability not stated

## Reviewer
- **Overall assessment** This manuscript presents a technically sophisticated deep learning framework for temporal inference from fixed embryo images, with potentially broad applicability. The core methodological advance, achieving 1-minute temporal resolution from fixed samples, is significant and well-motivated. However, several concerns regarding validation rigor, model generalizability, and the strength of biological conclusions need to be addressed. The biological findings, while interesting, are presented with limited statistical depth in the visible text, and the theoretical modeling sections are not fully assessable without the supplementary materials.

- **Who would be interested in the results, and why** Developmental biologists studying gene regulatory networks, particularly those working on Drosophila embryogenesis, would be the primary audience. Researchers using fixed-tissue imaging across model systems would also find the temporal inference framework valuable. The methodological approach may interest computational biologists developing deep learning tools for biological image analysis. The demonstration of unsteady-state transcriptional kinetics could interest biophysicists and systems biologists studying stochastic gene expression.

- **Major strengths**
  1. The methodological innovation of achieving 1-minute temporal resolution from fixed embryos is a substantial advance over existing approaches, which typically achieve only 2-4 minute resolution or coarse developmental staging.
  2. The multi-scale ensemble architecture with three independent CNN models is well-designed, and the use of relayed learning to bridge histone and DNA signals is clever and practical.
  3. The validation against live imaging data and the demonstration of cross-strain generalizability through size rescaling are commendable.
  4. The application to resolve Kr regulation by multiple TFs and the extension to single-molecule transcriptional kinetics demonstrates the broad utility of the approach.
  5. The observation of temporal asynchrony along the AP axis, consistent with mitotic wave dynamics, provides an internal validation of the method's sensitivity.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Validation
- **Claim pointer** The claim that the method achieves "1-minute accuracy" across nc11-14, with reported mean residuals of 0.01-0.05 min and standard deviations of 0.34-0.68 min.
- **Evidence pointer** Figure 1e, Results section "Predicting developmental time from nuclear histone images with 1-minute accuracy"
- **Concern** The reported standard deviations (0.34-0.68 min) are substantial relative to the claimed 1-minute resolution. For nc14, the standard deviation is 0.68 min, and only 87% of predictions fall within 1 minute. The manuscript does not report confidence intervals for these metrics, nor does it show how accuracy varies across the temporal extent of each nuclear cycle. The temporal alignment procedure, which rescales cycle durations to compensate for "variation in developmental tempo," could introduce systematic biases that are not fully characterized. Additionally, the exclusion of mitotic frames from training and prediction is mentioned but the potential impact on temporal coverage near mitotic boundaries is not discussed.
- **Why it matters** The central claim of the manuscript rests on the precision of temporal inference. If accuracy degrades at cycle boundaries or varies systematically across the cycle, downstream biological conclusions about gene regulation dynamics could be affected. The reported 87% accuracy for nc14 suggests the method may not be uniformly reliable across all stages.
- **Resolution test** Provide per-minute accuracy metrics across the full temporal extent of each nuclear cycle, including near mitotic boundaries. Report confidence intervals for all accuracy metrics. Describe the temporal alignment procedure in more detail, including how many embryos were used to establish the standard cycle durations and how sensitive the results are to this normalization.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Model generalizability
- **Claim pointer** The claim that the method works "regardless of strain" after size rescaling, and the application to WT embryos without additional training.
- **Evidence pointer** Figure 3d-f, Results section "Relayed learning enables time inference from the nuclear DNA signal of WT embryos"
- **Concern** The validation of cross-strain generalizability relies on a single comparison between his2av-mrfp1 and WT embryos, with size rescaling based on total embryo area. The manuscript does not report how many WT embryos were used for validation, the distribution of inferred times, or whether the rescaling factor was validated independently. The Cyclin B validation (Supplementary Fig. 3e) is mentioned but not shown in the visible text. The potential for other strain-specific differences beyond size, such as nuclear density or chromatin organization, is not addressed.
- **Why it matters** The claim of generalizability across strains is important for the method's broad applicability. If the rescaling procedure only partially corrects for strain differences, the temporal inference could be biased in ways that affect downstream biological conclusions.
- **Resolution test** Report the number of WT embryos used for validation, the distribution of inference errors, and a sensitivity analysis of the rescaling factor. Validate the rescaling approach on additional strains if possible. Show the Cyclin B validation data explicitly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance / Biological conclusions
- **Claim pointer** The claim that Kr transcription is "dynamically governed by a multiplicative combination of cooperative Bcd activation and Hb repression" and that hb transcription follows "unsteady-state bursty kinetics driven by dynamic Bcd binding."
- **Evidence pointer** Figure 4e-h, Figure 5, Results sections on Kr and hb regulation
- **Concern** The biological conclusions are presented with limited statistical detail in the visible text. For the Kr model, the fitting procedure, parameter uncertainties, and model comparison (e.g., additive vs. multiplicative) are not described. The claim that maternal Bcd and Hb are "sufficient" for early Kr patterning is strong and would require demonstration that no other factors are needed. For the hb analysis, the unsteady-state model is described only in Supplementary Note 1, which is not provided. The key finding of a temporal lag between Bcd peaking and continued kON increase is interesting but the statistical significance of this lag is not reported.
- **Why it matters** The biological findings are the ultimate demonstration of the method's utility. If the statistical support for these conclusions is weak, the impact of the work is diminished. The claim of sufficiency for Bcd and Hb in Kr patterning is particularly strong and needs robust support.
- **Resolution test** Provide parameter estimates with confidence intervals for the Kr model. Perform and report model comparison tests (e.g., multiplicative vs. additive). For the hb analysis, provide the full model description and report the statistical significance of the temporal lag between Bcd peak and kON peak.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Reproducibility
- **Claim pointer** The overall reproducibility of the deep learning framework.
- **Evidence pointer** Methods section "Model construction, training, and testing"
- **Concern** The manuscript does not state whether the code and trained models will be made publicly available. The training procedure is described but key hyperparameters, such as the exact number of layers for each model, learning rate schedules, and early stopping criteria, are not fully specified. The data splitting procedure for training and testing is described but the potential for data leakage between embryos from the same batch is not addressed.
- **Why it matters** Reproducibility is a core requirement for methodological papers. Without access to code and detailed training procedures, other groups cannot apply or build upon this method.
- **Resolution test** State code availability and provide detailed hyperparameters and training procedures. Describe the data splitting procedure in more detail, including how embryos were assigned to training and test sets.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1c
- **Evidence pointer** Figure 1c legend
- **Issue** The Grad-CAM visualization is described but the color scale and the meaning of the attention maps are not explained in the legend.
- **Required correction** Add a brief explanation of the Grad-CAM color scale and what the attention maps represent.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 2a
- **Evidence pointer** Figure 2a legend
- **Issue** The p-values are reported for the size comparisons, but the effect sizes are not stated.
- **Required correction** Report effect sizes (e.g., mean difference with confidence intervals) alongside p-values.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section on Kr regulation
- **Evidence pointer** Results section "Time inference of fixed embryos resolves the dynamic regulation of Kr by multiple TFs"
- **Issue** The description of the "two distinct expression peaks" in nc13 is brief and the biological interpretation is not fully developed.
- **Required correction** Expand the description of the two peaks and their potential biological significance.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods section on image rescaling
- **Evidence pointer** Methods section "Image rescaling for time inference from fixed embryos"
- **Issue** The recursion procedure for determining the rescaling magnitude is described but the convergence criteria are not stated.
- **Required correction** State the convergence criteria used for the recursion.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion does not address potential limitations of the approach, such as applicability to other developmental stages or organisms with different nuclear morphologies.
- **Required correction** Add a paragraph discussing limitations and potential challenges for broader application.

## Risk / unsupported claims
- The claim of "1-minute accuracy" is supported for nc11-13 but is weaker for nc14 (87% within 1 minute), and the manuscript does not fully characterize accuracy across the temporal extent of each cycle.
- The claim that the method works "regardless of strain" is based on limited validation and may be overstated.
- The claim that maternal Bcd and Hb are "sufficient" for early Kr patterning is strong and not fully supported by the visible evidence.
- The unsteady-state bursty kinetics model for hb is not assessable without Supplementary Note 1.
- The claim of "high-resolution reconstruction of dynamic gene regulation from fixed WT embryos, capturing dynamic details comparable to live imaging" is not directly demonstrated with a quantitative comparison to live imaging for the same biological process.
- The statistical significance of the temporal lag between Bcd peak and kON peak in hb regulation is not reported.