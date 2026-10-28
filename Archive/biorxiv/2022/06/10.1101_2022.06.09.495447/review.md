## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors use computer simulations based on biophysical principles of genome organisation to simultaneously predict 3D chromatin structure and transcriptional output across the human genome. They validate the model against Hi-C, FISH, GRO-seq, and single-cell RNA-seq data, and introduce a resource called 3DGene. They report that transcription correlates with protein-mediated microphase separated clusters of promoters and enhancers, that gene noise arises from structural heterogeneity, and that cohesin-mediated loop extrusion does not affect average transcription but modulates transcriptional noise.
- **Visible evidence base** Abstract text only; no quantitative results, model details, validation statistics, or resource description are visible
- **Missing materials affecting confidence** Full manuscript, all figures and tables, model equations and parameters, validation datasets and statistical comparisons, description of the 3DGene resource, and any supplementary information

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting computational framework linking 3D genome structure to transcriptional output and noise. However, the claims are broad and the evidence base is entirely inaccessible from the supplied material. The central assertions regarding microphase separation, structural heterogeneity as the cause of gene noise, and the specific role of loop extrusion are not quantitatively supported in the abstract. The work may be of interest to the genome biology and biophysics communities, but the current evidence does not establish the case.
- **Who would be interested in the results, and why** Researchers in genome architecture, transcriptional regulation, and computational biophysics would be interested because the work proposes a mechanistic link between chromatin structure and transcriptional noise. Those studying cohesin function and CTCF-mediated loop extrusion may also find the predicted role in noise modulation relevant. The 3DGene resource could appeal to experimentalists seeking predicted structural ensembles for active genes.
- **Major strengths** The abstract describes a multi-scale validation strategy against diverse experimental datasets, which suggests an effort to ground simulations in empirical data. The proposal that structural heterogeneity underlies transcriptional noise is a testable and conceptually interesting hypothesis. The potential resource for visualising gene structures could be a useful community tool.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  Originality: The idea of linking structural heterogeneity to transcriptional noise is not entirely new, but the specific computational approach may offer a fresh angle. However, the abstract does not clearly differentiate this work from prior simulation studies of genome organisation.  
  Scientific importance: If the claims are fully supported, the work could have broad implications for understanding gene expression variability and the evolutionary role of CTCF sites. The importance is potentially high but not yet demonstrated.  
  Interdisciplinary readership: The topic bridges biophysics, genomics, and molecular biology, which could attract a wide audience. The abstract is written in a way that is largely accessible to nonspecialists, though some terms such as "microphase separated clusters" may require background.  
  Technical soundness: Not assessable from the abstract alone. The validation strategy is mentioned but no statistics, error bars, or model performance metrics are provided.  
  Readability for nonspecialists: The abstract is concise and generally clear, but the mechanistic claims are stated without sufficient context or evidence, which may confuse readers unfamiliar with the field.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a promising direction, but the core claims require full manuscript evaluation. I would be supportive if the technical concerns are resolved with quantitative validation and clear model descriptions.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The abstract claims that simulations "simultaneously predict 3D structure and transcriptional output of human chromatin genome wide" and that the model is validated by quantitative comparison with Hi-C, FISH, GRO-seq, and single-cell RNA-seq data.  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** The abstract provides no quantitative details of the validation. No correlation coefficients, error metrics, or statistical significance values are given for any of the four data types. The claim of "quantitative comparison" is therefore unsubstantiated.  
- **Why it matters** Without quantitative validation metrics, the reader cannot assess whether the model predictions are accurate enough to support the subsequent mechanistic claims. The entire edifice of the paper rests on the model's ability to reproduce experimental data.  
- **Resolution test** Provide in the full manuscript explicit statistical comparisons for each validation dataset, including appropriate metrics and error bars, and show that the model outperforms reasonable null models.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Causal inference  
- **Claim pointer** The abstract states that "gene noise is a consequence of structural heterogeneity" and that "transcription strongly correlates with the formation of protein-mediated microphase separated clusters of promoters and enhancers."  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** The abstract uses correlative language ("correlates") but then asserts a causal relationship ("is a consequence"). No evidence is presented to distinguish correlation from causation, such as perturbation experiments or causal inference analyses.  
- **Why it matters** The central novelty of the paper appears to be the causal claim that structural heterogeneity drives noise. If only correlation is shown, the claim is overstated and the mechanistic interpretation is not justified.  
- **Resolution test** Demonstrate causality through targeted perturbations in the simulations, such as disrupting microphase separation or altering structural heterogeneity, and show corresponding changes in transcriptional noise. Alternatively, reframe the claim as correlative.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Model assumptions  
- **Claim pointer** The abstract states that simulations are "based on the known biophysical principles of genome organisation" and that "loop extrusion by cohesin does not affect average transcriptional patterns, but instead impacts transcriptional noise."  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** The abstract does not describe the model's assumptions regarding cohesin dynamics, loop extrusion parameters, or how transcription is coupled to structure. The claim about loop extrusion affecting noise but not average transcription is presented without any supporting simulation results or parameter sensitivity analysis.  
- **Why it matters** The conclusion about loop extrusion is a specific and potentially controversial claim. Without details on how loop extrusion is modelled and how the result was obtained, the claim cannot be evaluated or reproduced.  
- **Resolution test** Provide a full description of the model, including equations and parameters, and show simulation results with and without loop extrusion, including statistical comparisons of both mean transcription and noise.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Resource accessibility  
- **Claim pointer** The abstract states that the authors "provide the 3DGene resource to visualise the panoply of structures adopted by any active human gene in a population of cells."  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** The abstract does not describe the scope, accessibility, or usability of the 3DGene resource. No URL, data format, or example output is provided. The claim that it covers "any active human gene" is broad and unverified.  
- **Why it matters** A resource claim is a significant part of the paper's contribution. If the resource is not publicly available, documented, or comprehensive, the claim is misleading and the utility to the community is diminished.  
- **Resolution test** Provide a clear description of the resource, including its URL, data coverage, and a demonstration of its functionality for a representative set of genes.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Terminology  
- **Evidence pointer** Abstract text; location not provided  
- **Issue** The term "microphase separated clusters" is used without definition or context. Nonspecialist readers may not understand what this means physically or biologically.  
- **Required correction** Provide a brief explanation of microphase separation in the context of chromatin organisation, or use more accessible language.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Scope  
- **Affected element** Generalisability  
- **Evidence pointer** Abstract text; location not provided  
- **Issue** The abstract claims findings for "human chromosomes" and "human chromatin genome wide," but it is unclear whether the simulations cover all chromosomes or a subset, and whether the conclusions generalise across cell types.  
- **Required correction** Specify the genomic coverage and cell type used in the simulations, and discuss potential limitations in generalisability.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Model availability  
- **Evidence pointer** Abstract text; location not provided  
- **Issue** The abstract does not state whether the simulation code is publicly available, which is important for reproducibility in computational biology.  
- **Required correction** State the availability of the simulation code and any relevant software dependencies.

## Risk / unsupported claims
- The claim that the model "simultaneously predict[s] 3D structure and transcriptional output" is unsupported without quantitative validation metrics.
- The causal claim that "gene noise is a consequence of structural heterogeneity" is unsupported; only correlation is mentioned.
- The claim that "loop extrusion by cohesin does not affect average transcriptional patterns, but instead impacts transcriptional noise" is unsupported without simulation details and results.
- The claim that the 3DGene resource covers "any active human gene" is unverifiable from the abstract.
- The overall validation against four experimental data types is not assessable without statistical details.