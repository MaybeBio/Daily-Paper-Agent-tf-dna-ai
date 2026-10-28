## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, data availability, and code availability statements.
- **Assessment boundary** Scientific and technical evaluation of the DynaVelo model, its application to germinal center B cell multiomic data, and the validity of the perturbation and rescue predictions. The assessment is based solely on the provided manuscript text; no supplementary figures, tables, or external validation data were available for review.
- **Shared manuscript claim summary** The authors present DynaVelo, a generative neural ordinary differential equation (ODE) model that jointly learns the dynamics of gene expression and transcription factor (TF) motif accessibility from single-cell multiomic data. The model is claimed to recover known germinal center B cell dynamics, identify disrupted trajectories in Arid1a and Ctcf heterozygous loss-of-function mutants, infer dynamic gene regulatory networks, and predict both loss-of-function effects and rescue perturbations, with in vivo validation in double heterozygous mutant mice.
- **Visible evidence base** The manuscript text includes descriptions of model architecture, training procedures, and downstream analyses. Results are described qualitatively with references to figures (Fig. 1–6) and supplementary materials, but the actual figures, supplementary figures, and tables are not provided in the submitted material. Data availability statements reference GEO accessions and a private Figshare repository.
- **Missing materials affecting confidence** The following materials were not provided and are critical for a complete assessment: all main figures (Fig. 1–6), all supplementary figures (Fig. S1, S2), the supplementary note, the unpublished manuscript by Debek, Meydan et al. cited for validation of Ctcf rescue, and the actual data files. Without these, quantitative claims regarding model performance, statistical significance, and experimental validation cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting and technically ambitious approach to modeling cellular dynamics from single-cell multiomic data. The integration of RNA expression and TF motif accessibility within a neural ODE framework is a reasonable extension of existing velocity-based methods, and the application to germinal center B cells with mutant genotypes addresses a biologically important question. However, the current submission has several significant limitations. The most critical issue is that the central validation claims, particularly the in vivo rescue experiments, rely on an unpublished manuscript that is not available for review. Additionally, the manuscript lacks quantitative performance metrics, baseline comparisons, and statistical rigor in several key analyses. The model's novelty relative to existing methods such as MultiVelo is not clearly established beyond the ability to perform in silico perturbations. While the potential of the approach is evident, the evidence provided in this manuscript is insufficient to fully support the strong claims made, especially regarding the predictive power and generalizability of the model.
- **Who would be interested in the results, and why** Computational biologists developing methods for single-cell trajectory inference and dynamical modeling would be interested in the methodological contributions. Researchers studying germinal center biology, B cell differentiation, and the role of chromatin regulators such as ARID1A and CTCF would be interested in the biological findings. The demonstration of in silico perturbation and rescue prediction could be of interest to the broader community working on predictive modeling of genetic perturbations, though the validation of this aspect is currently incomplete.
- **Major strengths**
  1. The conceptual framework of jointly modeling RNA and TF motif accessibility dynamics within a generative neural ODE is a novel and potentially powerful approach that goes beyond existing methods that treat these modalities separately.
  2. The model's ability to generate trajectories and perform in silico perturbations is a valuable feature that could enable hypothesis generation and reduce the need for extensive animal experiments.
  3. The application to a well-defined biological system (germinal center B cells) with known biology provides a good testbed for the method, and the recovery of known TF-gene relationships lends some credibility to the approach.
  4. The authors have made their code and data publicly available, which is commendable and will facilitate further evaluation and use by the community.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Experimental validation
  - **Claim pointer** The manuscript claims that "we validated these predictions in vivo using double heterozygous mutant mice, confirming rescue of the Arid1a dark zone phenotype in all cases and quantitatively assessing model predictions using multiome in Arid1aHet;CtcfHet double heterozygous mice."
  - **Evidence pointer** Results section, Figure 6e–g; citation to "Debek, Meydan et al., unpublished manuscript, Related Manuscript File"
  - **Concern** The central validation of the model's rescue predictions relies entirely on an unpublished manuscript that is not provided for review. The authors state that the Ctcf rescue was confirmed in vivo, but the data supporting this claim are not accessible. Furthermore, the validation of Bcl6 and Stat3 as rescue targets is mentioned as a prediction but no experimental validation is described for these candidates. Without access to the primary validation data, the key claim that DynaVelo can predict rescue perturbations is not verifiable.
  - **Why it matters** The ability to predict rescue perturbations is a major selling point of the manuscript and is highlighted in the title and abstract. If this claim cannot be substantiated with accessible, peer-reviewed data, the significance of the work is substantially diminished. The reliance on an unpublished manuscript is a serious concern for a preprint and would be even more problematic for a journal submission.
  - **Resolution test** The authors must provide the full data and analysis from the validation experiments, either by including them in the main manuscript or supplementary materials, or by making the related manuscript available for review. The quantitative assessment of the rescue (e.g., effect sizes, statistical significance) must be presented in a transparent manner.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness and model validation
  - **Claim pointer** The manuscript claims that DynaVelo "recovers the complex and bifurcating in vivo dynamics of wildtype murine germinal center B cells" and that its latent time "better recapitulated GC dynamics than those of scVelo."
  - **Evidence pointer** Results section, Figure 2a–c; Supplementary Figure S2
  - **Concern** The comparison with scVelo and MultiVelo is described qualitatively, with no quantitative metrics provided. The manuscript states that scVelo "had difficulties" and that MultiVelo "failed to identify" certain trajectories, but no numerical comparisons of trajectory accuracy, latent time correlation with known biology, or robustness metrics are given. The evaluation appears to be based on visual inspection of UMAP plots, which is subjective and insufficient to support the claim of superiority.
  - **Why it matters** A central claim of the manuscript is that the joint modeling of RNA and chromatin accessibility improves dynamical inference over existing methods. Without quantitative benchmarks, this claim is not supported. The lack of rigorous comparison undermines the technical contribution of the work.
  - **Resolution test** The authors should provide quantitative comparisons with baseline methods, such as trajectory consistency scores, correlation of latent time with known differentiation markers, or accuracy in recovering known regulatory relationships. These metrics should be reported with appropriate statistical tests and error bars.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical rigor and reproducibility
  - **Claim pointer** The manuscript describes "in silico perturbation analysis" and "rescue rates" as key outputs, and states that "we performed a statistical test to identify RNA and motif delta velocities in each cell type whose mean was significantly different from zero."
  - **Evidence pointer** Methods section, "In silico perturbations" and "Calculating predicted rescue rates of RNA and motif velocities"
  - **Concern** The statistical methods for assessing the significance of delta velocities and rescue rates are described only briefly. The manuscript does not specify the type of t-test used (one-sample vs. two-sample), how multiple testing was corrected, or how the results were aggregated across cell types. The definition of "rescue rate" is given, but the statistical significance of these rates is not addressed. Furthermore, the manuscript does not report confidence intervals or effect sizes for the rescue predictions.
  - **Why it matters** The predictive claims of the model depend on the statistical robustness of the delta velocity and rescue rate calculations. Without clear and rigorous statistical methodology, the results are not reproducible and the conclusions are not reliable.
  - **Resolution test** The authors should provide a detailed description of the statistical tests, including the null hypotheses, multiple testing corrections, and how the results were aggregated. They should also report confidence intervals and effect sizes for the key predictions, and ideally provide a permutation-based or bootstrap-based assessment of the significance of the rescue rates.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Novelty and positioning
  - **Claim pointer** The manuscript states that "DynaVelo exploits single-cell multiome to powerfully model how gene expression and chromatin accessibility, as summarized by TF motif activities, influence each other in cell dynamics, enabling the accurate prediction of loss-of-function and rescue perturbations."
  - **Evidence pointer** Discussion section
  - **Concern** The novelty of the approach relative to existing methods is not clearly articulated. The manuscript mentions MultiVelo as a method that also uses both RNA and chromatin accessibility, but the key differences are stated as (1) the use of a neural ODE and (2) the ability to perform in silico perturbations. However, the manuscript does not discuss whether other neural ODE-based methods for single-cell dynamics (e.g., those based on scDiffEq) could be extended to multiomic data, nor does it compare the performance of DynaVelo against such potential extensions. The claim of "powerful" modeling is not supported by a clear demonstration of superiority.
  - **Why it matters** For a methods paper, establishing clear novelty and advantage over existing approaches is essential. Without a thorough comparison and discussion of the state of the art, the contribution of the work is unclear.
  - **Resolution test** The authors should provide a more detailed comparison with existing methods, including MultiVelo and potentially other neural ODE-based approaches, using quantitative benchmarks. They should also discuss the specific advantages of their architecture and training procedure that lead to improved performance.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and presentation
  - **Affected element** Abstract and Introduction
  - **Evidence pointer** Abstract, Introduction
  - **Issue** The abstract and introduction use terms such as "powerful" and "accurate" without providing specific quantitative evidence. The abstract states that the model "predicts" loss-of-function and rescue perturbations, but the scope of these predictions (e.g., which genes, which cell types) is not specified.
  - **Required correction** The authors should temper the language in the abstract and introduction to reflect the actual evidence presented, and should provide a brief summary of the key quantitative results to support the claims.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, "Model training and inference details"
  - **Evidence pointer** Methods section
  - **Issue** The description of hyperparameter selection is somewhat vague. The manuscript states that different values of κ1 and κ3 were tested, but it does not specify the range of values tested or the criteria used to select the final values.
  - **Required correction** The authors should provide a more detailed description of the hyperparameter search, including the range of values tested and the metric used for selection.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Results, Figure 6
  - **Evidence pointer** Results section, Figure 6
  - **Issue** The description of Figure 6 is dense and difficult to follow. The figure appears to contain multiple panels with different types of information (delta velocity fields, rescue rates, experimental validation), but the text does not clearly guide the reader through each panel.
  - **Required correction** The authors should restructure the description of Figure 6 to clearly explain each panel, the data shown, and the conclusions drawn from each.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Methods, "Calculating predicted rescue rates of RNA and motif velocities"
  - **Evidence pointer** Methods section
  - **Issue** The term "rescue rate" is used to describe the fraction of significant differential velocity genes that match in sign between the perturbed mutant and the wildtype. This is a somewhat unusual use of the term "rescue," which typically implies a functional restoration. The authors should clarify that this is a computational metric, not a direct measure of phenotypic rescue.
  - **Required correction** The authors should define "rescue rate" more precisely and consider using a different term, such as "velocity alignment rate," to avoid confusion.
- **Technical failings that need to be addressed before the case is established**
  1. The validation of the central rescue prediction relies on an unpublished manuscript (R1-M1). This is a blocking issue.
  2. The comparison with existing methods (scVelo, MultiVelo) is qualitative and lacks quantitative metrics (R1-M2). This is a blocking issue for establishing the technical contribution.
  3. The statistical methodology for delta velocity and rescue rate calculations is under-specified (R1-M3). This is a blocking issue for reproducibility.
  4. The manuscript does not provide a clear statement of the model's limitations, such as its sensitivity to the quality of input velocity estimates or its scalability to larger datasets.
- **Assessment against Nature-style criteria**
  - **Originality** The idea of jointly modeling RNA and TF motif accessibility dynamics in a neural ODE framework is original and extends existing velocity-based methods. However, the incremental novelty over MultiVelo and other neural ODE approaches needs to be more clearly articulated and demonstrated.
  - **Scientific importance** The application to germinal center B cells and the prediction of rescue perturbations for ARID1A loss-of-function is of potential importance, given the relevance of these pathways to B cell lymphomas. However, the importance is contingent on the validity of the predictions, which is currently not fully established.
  - **Interdisciplinary readership** The work is likely to appeal to computational biologists, immunologists, and researchers interested in gene regulation. The writing is generally accessible, but the methods section is dense and may be challenging for non-specialists.
  - **Technical soundness** The model architecture is described in detail, but the validation is incomplete. The lack of quantitative benchmarks and the reliance on an unpublished manuscript for key validation are significant technical weaknesses.
  - **Readability for nonspecialists** The abstract and introduction are clear, but the results section is heavily reliant on jargon and references to figures that are not provided. The manuscript would benefit from a more accessible summary of the key findings and their implications.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a promising approach, but the central claims of predictive power and in vivo validation cannot be assessed without the missing data and quantitative analyses. The authors should be encouraged to resubmit a revised version that addresses the blocking concerns, particularly by providing the validation data and a rigorous comparison with existing methods.

## Risk / unsupported claims
- The claim that DynaVelo "predicts" rescue perturbations is not supported by accessible evidence, as the validation relies on an unpublished manuscript.
- The claim that DynaVelo's latent time "better recapitulated GC dynamics" than scVelo is not supported by quantitative metrics.
- The claim that DynaVelo "recovers" known TF-gene relationships is based on a qualitative description and lacks statistical assessment of the recovered edges.
- The claim that the model can "identify TF perturbations to rescue loss-of-function dynamic and immunological phenotypes" is based on in silico predictions, but the experimental validation is only described for Ctcf and is not accessible.
- The generalizability of the model to other biological systems is claimed but not demonstrated.