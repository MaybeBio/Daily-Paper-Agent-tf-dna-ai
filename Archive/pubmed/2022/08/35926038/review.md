## Review setup
- **Input scope** Full manuscript text (abstract, results, discussion, methods summary)
- **Assessment boundary** Scientific claims, methodological soundness, and data interpretation as presented in the provided text
- **Shared manuscript claim summary** The authors present a single-cell atlas of Drosophila melanogaster embryogenesis spanning 0 to 20 hours, profiling chromatin accessibility in ~1 million nuclei and gene expression in ~0.5 million nuclei. They use neural network-based models to predict the absolute developmental age of individual nuclei, enabling continuous temporal resolution. They identify 171 cell states in ATAC data and 268 in RNA data, construct developmental trajectories, and nominate transcription factors driving germ layer-specific differentiation programs.
- **Visible evidence base** Main text figures referenced (Fig. 1A-G, 2A-I, 3A-H, 4A-H, 5A-G), supplementary figures (fig. S1-S11), supplementary tables (S1-S10), and methods summary
- **Missing materials affecting confidence** Full methods details, supplementary figures and tables, quality control metrics, model architecture specifics, and validation statistics are not fully visible in the provided text

## Reviewer
- **Overall assessment** This manuscript presents a substantial and technically ambitious resource for the Drosophila developmental biology community. The scale of data generation is impressive, and the concept of using neural network-based age prediction to create a continuous temporal atlas is conceptually novel and potentially transformative. The authors demonstrate careful attention to potential confounders such as batch effects and embryo contamination. However, several technical concerns need to be addressed to fully establish the validity of the age prediction approach and the biological conclusions drawn from it. The validation of predicted ages, the handling of edge effects, and the robustness of trajectory inference require further scrutiny. The resource itself is likely to be highly valuable, but the strength of the biological claims should be calibrated to the limitations of the inference methods.
- **Who would be interested in the results, and why** Developmental biologists studying Drosophila embryogenesis, particularly those interested in gene regulatory networks, cell fate specification, and chromatin dynamics. The resource will also be valuable to computational biologists developing methods for temporal inference in single-cell data, and to researchers studying ZGA and pioneer transcription factors. The atlas format and the age prediction framework could serve as a template for similar efforts in other model organisms.
- **Major strengths** 1) Unprecedented temporal density of sampling across the entirety of Drosophila embryogenesis, addressing a clear gap in existing atlases. 2) The neural network-based age prediction framework is conceptually novel and represents a methodological advance over discrete time point analyses. 3) The integration of ATAC and RNA modalities provides complementary views of regulatory and transcriptional dynamics. 4) The authors demonstrate the utility of the resource through multiple analyses, including ZGA dynamics, trajectory inference, and TF nomination. 5) The validation of novel findings (e.g., elav expression in visceral muscle) through orthogonal methods strengthens confidence in the data quality.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (age prediction validation), R1-M2 (edge effect handling), R1-M3 (trajectory inference robustness), R1-M4 (TF nomination validation)
- **Assessment against Nature-style criteria** **Originality**: High. The continuous temporal atlas concept and the application of neural network-based age prediction to single-cell developmental data represent a novel contribution. **Scientific importance**: High. The resource addresses a fundamental limitation in developmental atlases and provides a framework applicable to other systems. **Interdisciplinary readership**: Moderate to high. The work bridges developmental biology, genomics, and computational biology, and will appeal to researchers across these fields. **Technical soundness**: Moderate. The data generation appears rigorous, but the validation of the age prediction model and the robustness of downstream inferences require additional evidence. **Readability for nonspecialists**: Good. The manuscript is clearly written, with a logical structure and accessible explanations of complex concepts, though some sections assume familiarity with single-cell genomics terminology.
- **Recommendation posture** Supportive if technical concerns are resolved. The resource is valuable and the conceptual framework is promising, but the validity of the age prediction approach and the robustness of the biological inferences must be more rigorously established before the claims can be fully accepted.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that neural network-based models can predict the absolute developmental age of individual nuclei with high accuracy, enabling continuous temporal resolution at the scale of minutes.
- **Evidence pointer** Results section "Predicting the absolute age of individual nuclei", Fig. 2
- **Concern** The validation of the age prediction model is insufficient. The authors report MSE and proportion correct for held-out data, but these metrics are computed against the center of the collection window, which is a coarse label. The claim of minute-scale resolution is not directly validated. The authors apply the model to bulk RNA-seq and DNase-seq time courses, but these are also discrete time points. There is no direct validation against an independent, continuous ground truth. The authors acknowledge that scRNA and scATAC models produce slightly different age predictions, but the implications of this discrepancy for downstream analyses are not discussed.
- **Why it matters** The entire framework of a "continuum" of development rests on the accuracy of the age predictions. If the model is only accurate to within the 2-4 hour collection window, then the claimed minute-scale resolution is not achieved, and the downstream analyses (e.g., ZGA dynamics, trajectory inference) may be built on unreliable temporal ordering.
- **Resolution test** Provide direct validation of predicted ages against an independent continuous measure, such as time-lapse imaging of individual embryos or a carefully staged series with finer temporal resolution. Alternatively, demonstrate that the model's predictions are robust to perturbations in the training data and that the discrepancy between scRNA and scATAC predictions does not materially affect the conclusions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that cells with predicted ages >18 hours were excluded due to edge effects, and that reduced cell numbers are observed at the beginning and end of the time course.
- **Evidence pointer** Results section "Predicting the absolute age of individual nuclei", fig. S6A
- **Concern** The exclusion of cells with predicted ages >18 hours is a significant fraction of the data (61% fewer cells than expected under uniform sampling). The authors attribute this to edge effects but do not provide a detailed characterization of the problem. It is unclear whether the model systematically misassigns ages for late-stage cells, and whether the exclusion of these cells biases the trajectory inference or the identification of late-stage cell types. The reduced cell numbers at early time points are also not fully explained.
- **Why it matters** If the age prediction model has systematic biases at the edges of the temporal range, then the atlas is incomplete at the very stages where important developmental transitions occur (e.g., terminal differentiation). The exclusion of these cells could lead to missing cell states or incorrect trajectory topologies.
- **Resolution test** Provide a detailed analysis of the edge effects, including the distribution of predicted ages for cells from each collection window, and demonstrate that the exclusion of late-stage cells does not alter the conclusions. Consider alternative approaches, such as training the model on a more balanced dataset or using a different loss function that is less sensitive to edge effects.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors construct developmental trajectories by linking cell clusters across adjacent time windows based on the proportion of nearest neighbors from the parent window.
- **Evidence pointer** Results section "Annotation and inference of diversifying developmental trajectories", Fig. 3C-D, fig. S6B-C
- **Concern** The trajectory inference method is relatively simple and may not be robust to the choice of parameters, such as the number of nearest neighbors or the edge weight threshold (0.2). The authors note that some paths terminate prematurely, which they attribute to sampling or technical factors, but this could also reflect limitations of the inference method. The method does not appear to account for the possibility of cell state convergence or divergence in a principled way.
- **Why it matters** The trajectories are a central output of the atlas and are used to support claims about the emergence and diversification of cell lineages. If the inference method is not robust, the trajectories may be misleading, and the biological conclusions drawn from them (e.g., the timing of lineage specification) may be incorrect.
- **Resolution test** Perform sensitivity analyses to demonstrate that the trajectories are robust to the choice of parameters. Consider using more sophisticated trajectory inference methods that can handle branching and convergence, and validate the inferred trajectories against known lineage relationships from genetic studies.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors nominate transcription factors as regulators of specific cell types based on the correlation between motif accessibility and gene expression.
- **Evidence pointer** Results section "Nominating stage- and cell type-specific TF regulators", Fig. 5, table S10
- **Concern** The TF nomination approach is correlative and may produce false positives. The authors validate a few examples (e.g., Sage, GATAe, Awh) against known functions, but the overall list of 1258 TF-to-tissue relationships is not systematically validated. The method may miss TFs that act through indirect mechanisms or that are regulated post-transcriptionally.
- **Why it matters** The TF nominations are presented as a resource for future studies, but if the false positive rate is high, the resource may mislead researchers. The claims about specific TFs (e.g., the potential role of Fru in neuroectoderm) should be tempered until experimentally validated.
- **Resolution test** Provide additional validation of the TF nominations, such as comparing against known regulatory interactions from curated databases or performing targeted experiments on a subset of predictions. Discuss the expected false positive rate and provide guidance on how to prioritize candidates for validation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Fig. 1A
- **Evidence pointer** Fig. 1A
- **Issue** The schematic of the experimental design is not fully described in the text. It is unclear how the 11 overlapping time windows were chosen and whether the overlap was designed to ensure uniform coverage.
- **Required correction** Add a brief description of the time window design in the main text or figure legend.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Fig. 2E-F
- **Evidence pointer** Fig. 2E-F
- **Issue** The ZGA analysis is presented as a demonstration of minute-scale resolution, but the figure only shows a few genes. It is unclear how representative these examples are and whether the analysis was performed on all ZGA genes.
- **Required correction** Clarify the scope of the ZGA analysis and consider showing aggregate statistics across all ZGA genes.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods summary
- **Evidence pointer** Materials and methods summary
- **Issue** The methods summary is brief and does not provide sufficient detail for replication. Key parameters for the neural network model, such as architecture, training procedure, and hyperparameter selection, are not described.
- **Required correction** Provide a more detailed methods section, either in the main text or as a supplement, with full model specifications and code availability.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of limitations is brief and does not address the potential impact of the age prediction errors on the biological conclusions.
- **Required correction** Expand the discussion of limitations, including a quantitative assessment of how age prediction uncertainty propagates to downstream analyses.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and materials availability
- **Evidence pointer** Data and materials availability section
- **Issue** The data availability statement mentions a custom web app, but it is unclear whether the underlying code for the analysis is also available.
- **Required correction** Clarify the availability of analysis code and provide a persistent repository link.

## Risk / unsupported claims
- The claim of "minute-scale" temporal resolution is not directly validated and may be overstated given the coarse training labels.
- The claim that the atlas provides a "continuum" of development is conceptually appealing but depends on the accuracy of the age predictions, which is not fully established.
- The TF nominations are correlative and not systematically validated; the claim that they represent "regulators" should be considered as hypotheses rather than established findings.
- The trajectory inference method is simple and may not capture the full complexity of developmental lineage relationships; the claim that the trajectories are "systematic" is not fully supported.
- The statement that the data "did not appear to be confounded by batch effects" is based on a figure reference but the specific analysis is not described in the text, making it difficult to assess.