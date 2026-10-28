## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, methods, and supplementary figure legends as provided.
- **Assessment boundary** Scientific validity, methodological soundness, clarity of claims, and alignment with Nature-style criteria. No assessment of formatting or editorial fit.
- **Shared manuscript claim summary** The authors present a deep learning-based approach to infer absolute developmental time with 1-minute resolution from nuclear morphology in fixed Drosophila embryos. They apply this to resolve spatiotemporal regulation of Kr by Bicoid and Hunchback, and to uncover unsteady-state bursty kinetics of hunchback transcription using time-resolved single-molecule statistics.
- **Visible evidence base** Abstract, Introduction, Results sections (narrative only, no figures or tables included), Methods, Discussion, Data and Code availability statements.
- **Missing materials affecting confidence** All figures, supplementary figures, supplementary tables, and the supplementary note are referenced but not provided. This significantly limits the ability to evaluate the technical soundness of the deep learning models, the quality of the imaging data, and the validity of the mathematical modeling.

## Reviewer
- **Overall assessment** The manuscript addresses a significant challenge in developmental biology: extracting high-resolution temporal information from fixed embryos to study dynamic gene regulation. The proposed approach, combining multi-scale ensemble deep learning with time-resolved single-molecule statistics, is conceptually novel and potentially impactful. However, the absence of all figures, tables, and the supplementary note prevents a thorough evaluation of the methods and results. The claims are ambitious, and the evidence base as presented is insufficient to fully establish them.
- **Who would be interested in the results, and why** Developmental biologists studying gene regulatory networks, particularly those interested in Drosophila embryogenesis. Researchers using fixed-tissue imaging who need temporal resolution. Computational biologists working on deep learning applications in biology. The method could also interest researchers studying transcriptional dynamics and stochastic gene expression.
- **Major strengths** 1. The problem addressed is important and timely. 2. The conceptual approach of using deep learning on nuclear morphology to infer time is innovative. 3. The combination of time inference with single-molecule statistics to study unsteady-state kinetics is a powerful idea. 4. The authors demonstrate application to endogenous genes without genetic modification, which is a significant advantage.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing validation data), R1-M2 (missing model details), R1-M3 (missing statistical modeling details), R1-M4 (missing validation of biological findings).
- **Assessment against Nature-style criteria** **Originality:** High. The use of deep learning for time inference from fixed embryos is novel. **Scientific importance:** High. The ability to study dynamic gene regulation without live imaging or genetic modification has broad implications. **Interdisciplinary readership:** Moderate to high. The work bridges developmental biology, computational biology, and biophysics. **Technical soundness:** Cannot be fully assessed due to missing figures and supplementary materials. The described methods are plausible but not verifiable from the text alone. **Readability for nonspecialists:** The abstract and introduction are accessible, but the results and methods sections are dense and assume significant background knowledge. The lack of figures makes the narrative difficult to follow.
- **Recommendation posture** Currently not established from the provided evidence. The core claims are interesting and potentially important, but the missing figures, tables, and supplementary note are essential for evaluating the technical soundness and validity of the results. A revised submission with all supporting materials is required for a fair assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that the deep learning approach achieves "1-minute resolution" and "precise" time inference from fixed embryos.
- **Evidence pointer** Results section "Predicting developmental time from nuclear histone images with 1-minute accuracy", Figure 1 (not provided)
- **Concern** The central claim of 1-minute accuracy is not verifiable without the data shown in Figure 1 and Supplementary Figures 1-2. The text describes residuals and percentages of predictions within 1 minute, but the actual distributions, error metrics, and comparisons to ground truth are not visible. Furthermore, the validation strategy for fixed embryos (where ground truth is not known) is not described in sufficient detail. How was the "ground truth" for fixed embryos established? The text mentions using live imaging data for training, but the transfer to fixed tissue involves assumptions about fixation effects that are not fully addressed.
- **Why it matters** The entire premise of the paper rests on the accuracy and reliability of the time inference. Without seeing the validation data, the reader cannot assess whether the method truly achieves the claimed resolution or whether it is robust across different embryos, imaging conditions, and developmental stages.
- **Resolution test** Provide Figure 1 and Supplementary Figures 1-2 showing: (a) scatter plots of predicted vs. true time for live embryos, (b) residual plots, (c) histograms of prediction errors, (d) a clear description and demonstration of the validation method for fixed embryos, including how ground truth was assigned and how fixation-induced shrinkage was corrected.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that the multi-scale ensemble deep learning framework, with three independent CNN models, provides robust and accurate time inference.
- **Evidence pointer** Methods section "Model construction, training, and testing", Supplementary Table 1 (not provided)
- **Concern** The description of the CNN architecture is incomplete. The text mentions a "modified VGGNet architecture" with specific changes, but the exact architecture (number of layers, filter sizes, pooling, etc.) is not fully specified. Supplementary Table 1, which presumably contains this information, is not provided. The training procedure, including hyperparameter selection, data augmentation details, and cross-validation strategy, is described but not in sufficient detail to be reproducible. The ensemble method (median filter) is mentioned, but the rationale for this specific combination and its advantage over other ensemble methods is not discussed.
- **Why it matters** Reproducibility is a cornerstone of scientific research. Without a complete description of the model architecture and training procedure, other researchers cannot replicate or build upon this work. The lack of detail also prevents an assessment of whether the model is overfitting or generalizing well.
- **Resolution test** Provide Supplementary Table 1 with full architectural details for all three CNN models. Expand the Methods section to include a complete description of the training procedure, including hyperparameter values, optimization settings, and data augmentation parameters. Justify the choice of the median filter for ensemble combination.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that the time-resolved theoretical model of single-molecule mRNA statistics reveals "unsteady-state bursty kinetics" of hb transcription.
- **Evidence pointer** Results section "Time-resolved single-molecule mRNA statistics reveal unsteady-state kinetics of hb transcription", Figure 5 (not provided), Supplementary Note 1 (not provided)
- **Concern** The mathematical modeling of unsteady-state transcriptional kinetics is a key part of the paper, but the details are entirely delegated to Supplementary Note 1, which is not provided. The text describes the model conceptually (two-state stochastic kinetics with time-dependent parameters) but does not provide the equations, assumptions, or inference procedure. The claim of "unsteady-state" kinetics is central, but without the model details, it is impossible to evaluate whether the data truly support this conclusion or whether simpler models could explain the observations.
- **Why it matters** The biological conclusions about hb transcription kinetics depend entirely on the validity of the mathematical model. Without seeing the model equations, the assumptions made, and the fitting procedure, the reader cannot assess the robustness of the findings or the interpretation of the data.
- **Resolution test** Provide Supplementary Note 1 in full. The main text should include a summary of the model equations and key assumptions. Show the fits of the model to the data in Figure 5, including a comparison to alternative models (e.g., steady-state models) to demonstrate that the unsteady-state model is necessary.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The claim that the method resolves "spatiotemporal regulation of the endogenous segmentation gene Krüppel (Kr) by multiple transcription factors (TFs) during early development without genetic modification."
- **Evidence pointer** Results section "Time inference of fixed embryos resolves the dynamic regulation of Kr by multiple TFs", Figure 4 (not provided)
- **Concern** The biological findings regarding Kr regulation are presented as a demonstration of the method's utility. However, the results are not visible. The text describes a thermodynamic model with fitted parameters (n_B ~ 4, n_H ~ 6, C_B0 ~ 2.4 nM, C_H0 ~ 7.2 nM), but the quality of the fits, the comparison to experimental data, and the statistical significance of the findings are not shown. The claim that Kr is "dynamically governed by a multiplicative combination of cooperative Bicoid activation and Hunchback repression" is a strong statement that requires visual evidence of the model's agreement with the data.
- **Why it matters** The biological insights are a major part of the paper's significance. Without seeing the data and model fits, the reader cannot judge whether the conclusions are well-supported or whether alternative interpretations are possible.
- **Resolution test** Provide Figure 4 and Supplementary Figures 4 showing: (a) the spatiotemporal profiles of Kr, Bicoid, and Hunchback, (b) the model fits to the data, (c) the parameter estimates with confidence intervals, and (d) a comparison of the multiplicative model to alternative models (e.g., additive or independent effects).

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The abstract and introduction are well-written but could benefit from a clearer statement of the limitations of existing methods. The claim that live imaging is limited to "typically <4" molecular species is made without a citation. The statement that genetic modifications "can disrupt endogenous gene expression" is also general and could be more specific.
- **Required correction** Add citations for the limitations of live imaging and the effects of genetic modifications. Consider providing specific examples to strengthen the motivation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Fly strains"
- **Evidence pointer** Methods section "Fly strains"
- **Concern** The description of the fly strains is brief. The genotype of the 1× bcd strain is given as "+/ CyO-bcd+ ; E1s", but the nature of the E1s element is not explained. The origin of the his2av-mrfp1 strain is given, but the specific stock numbers are listed without further context.
- **Required correction** Provide a brief description of the E1s element and its role in reducing bcd dosage. Clarify the genetic background of the his2av-mrfp1 strain.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Predicting developmental time from nuclear histone images with 1-minute accuracy"
- **Evidence pointer** Results section, Figure 1 (not provided)
- **Concern** The text mentions ">30 transgenic embryos" for training and testing, but the exact numbers per nuclear cycle are not given. The description of the "relayed learning" strategy is clear conceptually, but the details of how the histone-based model was used to train the DNA-based model are not fully explained.
- **Required correction** Provide the exact number of embryos used for training and testing for each nuclear cycle. Expand the description of the relayed learning strategy to clarify the training procedure.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results section "Time inference of fixed embryos resolves the dynamic regulation of Kr by multiple TFs"
- **Evidence pointer** Results section, Figure 4 (not provided)
- **Concern** The text describes the temporal dynamics of Kr, Bicoid, and Hunchback, but the specific time points and the number of embryos analyzed are not stated. The description of the "two distinct expression peaks" in Kr during nc13 is interesting but lacks quantitative detail.
- **Required correction** Provide the number of embryos analyzed and the time points sampled. Quantify the two peaks in Kr expression (e.g., peak heights, durations, and statistical significance of the difference).

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Data and Code availability
- **Evidence pointer** Data and Code availability
- **Concern** The data are available on a "private server" and the code on GitHub. The private server link may not be stable or accessible to all readers. The code repository name is given, but the contents are not described.
- **Required correction** Consider depositing the data in a public repository (e.g., Zenodo, Figshare) to ensure long-term accessibility. Provide a brief description of the code repository contents.

## Risk / unsupported claims
- The claim of "1-minute resolution" is not supported by visible data (Figure 1 not provided).
- The claim of "unsteady-state bursty kinetics" of hb transcription is not supported by visible data or model details (Figure 5 and Supplementary Note 1 not provided).
- The claim of "multiplicative combination of cooperative Bicoid activation and Hunchback repression" for Kr regulation is not supported by visible data (Figure 4 not provided).
- The general applicability of the method to "other developmental stages, other organisms, or even non-developmental processes" is speculative and not demonstrated.
- The statement that the method "offers a versatile framework for investigating dynamic gene regulation in genetically unmodified organisms" is a reasonable inference but is not directly tested beyond the two genes studied.