## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods, figure legends where present)
- **Assessment boundary** Scientific and technical evaluation of the ProBound method, its validation, and the claims made regarding prediction of protein-ligand binding affinity from sequencing data
- **Shared manuscript claim summary** The authors present ProBound, a machine learning framework that models sequence recognition in terms of biophysical parameters (equilibrium binding constants, kinetic rates) from high-throughput sequencing data. They claim it outperforms existing resources across multiple benchmarks, captures cooperative binding and DNA modification effects, enables absolute KD measurement via a new assay (KD-seq), profiles kinase kinetics (Kinase-seq), and can infer TF binding models directly from ChIP-seq data without peak calling.
- **Visible evidence base** Main text figures referenced (Figs. 1-6), Extended Data Figures 1-10 referenced, Supplementary Tables 1-5 referenced, methods section with mathematical formulations
- **Missing materials affecting confidence** Actual figure images, supplementary tables with data, software implementation details, full parameter settings, detailed benchmark results per TF, code availability

## Reviewer

### **Overall assessment**
This manuscript introduces ProBound, a flexible maximum-likelihood framework for inferring biophysically interpretable models of protein-ligand interactions from sequencing data. The core idea is strong: modeling the full data generation process rather than relying on enrichment heuristics. The authors demonstrate applications across TF-DNA binding, methylation-aware models, absolute KD measurement, kinase-substrate kinetics, and ChIP-seq analysis. The breadth is impressive, but the depth of validation varies across applications. The central claims regarding improved predictive performance over existing resources are supported by benchmark comparisons, though some comparisons show modest gains. The KD-seq and Kinase-seq applications are conceptually novel but require closer scrutiny of the experimental validation. The ChIP-seq application is intriguing but raises questions about identifiability and model assumptions. Overall, this is a potentially important contribution to quantitative analysis of molecular recognition, but several technical concerns need to be addressed before the case is fully established.

### **Who would be interested in the results, and why**
Computational biologists studying transcription factor binding specificity, experimentalists using SELEX or similar assays, researchers developing biophysical models of protein-DNA/RNA/peptide interactions, and those interested in quantitative frameworks for interpreting high-throughput sequencing data. The method's ability to extract absolute biophysical parameters from sequencing data could be of broad interest to the molecular recognition community.

### **Major strengths**
1. The multi-layer probabilistic framework is principled and general, explicitly modeling the assay process rather than using ad hoc enrichment metrics.
2. The scale of the benchmark (1,632 TF models from diverse sources) is substantial and provides a valuable community resource.
3. The extension to methylation-aware models and multi-protein complexes addresses important biological complexity.
4. The KD-seq concept of using input/bound/free fractions to extract absolute affinities is clever and addresses a real limitation of relative-only measurements.
5. The Kinase-seq application demonstrates the framework's generality beyond DNA-binding proteins.
6. The peak-free ChIP-seq analysis is a novel approach that could change how such data are analyzed.

### **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of KD-seq absolute calibration
- **Claim pointer** The manuscript claims that KD-seq "determines the absolute affinity of protein-ligand interactions" and that the method produces accurate KD values validated by EMSA.
- **Evidence pointer** Figure 4, Extended Data Figures 6-8, "KD-seq" methods section
- **Concern** The KD-seq method relies on estimating the absolute fraction of bound protein p(B) from the input, bound, and free libraries. The authors acknowledge that this requires the free protein concentration [P]F to be estimated, which depends on knowing the total protein concentration [P]T and the fraction bound. However, the manuscript does not clearly explain how [P]T is determined or calibrated in the experimental setup. The validation against EMSA uses only four probes, which is a very small sample size. The simulations show recovery of ground truth parameters, but these simulations assume the model is correct. The practical guidelines section mentions that the method becomes unreliable when [DNA]I >> [P]T, but the quantitative limits of applicability are not established.
- **Why it matters** The central novelty of KD-seq is the claim of absolute, not just relative, affinity measurement. If the calibration of [P]T is not robust or the method has narrow applicability windows, the absolute KD values could be systematically biased. The small validation set (4 probes) is insufficient to establish general accuracy.
- **Resolution test** Provide a more extensive validation of KD-seq against an independent method (e.g., ITC, SPR, or a larger EMSA panel) across a wider range of affinities. Clearly document how [P]T is measured or estimated, and provide error analysis on the KD estimates. Demonstrate the method's accuracy across a range of [P]T/[DNA] ratios and show where the method breaks down.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Benchmark comparison fairness and completeness
- **Claim pointer** The manuscript claims that "On average, ProBound outperformed these resources across all metrics" when compared to JASPAR, DeepBind, HOCOMOCO, Jolma et al., and DeepSELEX.
- **Evidence pointer** Figure 2b, "Benchmarking ProBound" methods section
- **Concern** The benchmark comparison methodology needs more detail. Specifically: (1) How were matched TF-resource pairs determined? Were all TFs in each resource compared, or only those with sufficient testing data? (2) The comparison to DeepBind uses a different underlying model class (deep learning vs. interpretable energy models), and it is unclear if the comparison is apples-to-apples in terms of training data. (3) The manuscript states that two comparisons showed no significant difference, but the overall claim of "outperformed" is based on averages. The distribution of performance differences across TFs should be shown. (4) The MAFR metric is defined in the manuscript but its statistical properties and sensitivity to noise are not fully characterized.
- **Why it matters** The claim of superior performance is a key selling point. If the benchmark is biased or incomplete, the conclusion may not hold broadly. The modest gains in some metrics suggest the advantage may be specific to certain TF families or data types.
- **Resolution test** Provide a more detailed breakdown of benchmark results, including per-TF performance differences, statistical significance testing across the full distribution, and clarification of how matched comparisons were constructed. Show performance stratified by TF family, data source, and model complexity.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** ChIP-seq peak-free analysis identifiability
- **Claim pointer** The manuscript claims that ProBound can "infer specificity directly from in vivo data such as ChIP-seq without peak calling" and that the resulting models agree with those from SELEX data.
- **Evidence pointer** Figure 5, "Peak-free motif discovery from ChIP-seq data" methods section
- **Concern** The ChIP-seq analysis models the relationship between input and ChIP libraries directly. However, ChIP-seq data are influenced by many factors beyond binding affinity, including chromatin accessibility, antibody efficiency, cross-linking artifacts, and local sequence biases in fragmentation. The model assumes that the ChIP signal is proportional to binding probability, but this proportionality is not validated. The comparison to SELEX-derived models shows good correlation (r2 = 0.97 and 0.92), but this is for one TF (GR) in two datasets. The identifiability of the model when jointly estimating binding energy, accessibility, and other nuisance parameters is not discussed.
- **Why it matters** If the ChIP-seq model is misspecified, the inferred "binding models" could reflect confounding factors rather than true specificity. The claim of peak-free analysis is strong and needs robust validation across multiple TFs and cell types.
- **Resolution test** Apply the peak-free ChIP-seq analysis to multiple TFs with known binding specificities and compare to orthogonal measurements. Perform simulations with known ground truth to assess identifiability. Discuss and test the sensitivity of results to model assumptions (e.g., proportionality of ChIP signal to occupancy).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of Kinase-seq
- **Claim pointer** The manuscript claims that Kinase-seq "profiles the sequence specificity of the tyrosine kinase c-Src" and that the model predicts catalytic efficiency keff.
- **Evidence pointer** Figure 6, "Kinase-seq" methods section
- **Concern** The Kinase-seq application is demonstrated for a single kinase (c-Src). The manuscript does not discuss how the framework would handle kinases with different mechanisms (e.g., processive kinases, kinases requiring co-factors, or those with non-Michaelis-Menten kinetics). The validation uses only 11 peptides, and the correlation between predicted and measured rates, while significant, is based on a small sample. The manuscript does not report the dynamic range of keff values tested or whether the model can distinguish between changes in kcat vs. KM.
- **Why it matters** The generality of the framework is a stated advantage, but the Kinase-seq demonstration is limited. If the method only works for simple Michaelis-Menten kinases, its utility is narrower than implied.
- **Resolution test** Apply Kinase-seq to additional kinases with distinct substrate preferences and kinetic mechanisms. Expand the validation set to include more peptides spanning a wider range of keff values. Discuss the model's ability to separate kcat and KM contributions.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Model interpretability and parameter identifiability
- **Claim pointer** The manuscript emphasizes that ProBound produces "biophysically interpretable models" and that the framework is "flexible."
- **Evidence pointer** Methods sections on model architecture and regularization
- **Concern** The manuscript describes the model as using position-specific affinity matrices with optional pairwise interactions, but the details of how the model complexity is selected (e.g., number of binding modes, inclusion of interactions) are not fully specified. The regularization procedure is described, but the sensitivity of results to regularization strength is not explored. The manuscript does not discuss how to determine whether the inferred parameters are uniquely identifiable given the data.
- **Why it matters** If the model is over-parameterized or under-constrained, the "interpretable" parameters could be misleading. The flexibility of the framework is a strength, but it also raises the risk of overfitting.
- **Resolution test** Provide a more detailed description of model selection procedures, including how the number of binding modes and interaction terms are chosen. Show sensitivity analyses for key results across a range of regularization strengths. Discuss identifiability of model parameters, possibly with simulation studies.

### **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure legends
- **Affected element** Figures 1-6
- **Evidence pointer** Figure legends in main text
- **Issue** The figure legends are relatively brief and do not fully explain all panels, especially for Extended Data Figures. For example, the exact definition of "energy logo" and how it differs from standard sequence logos is not explicitly stated in the main text.
- **Required correction** Expand figure legends to clearly describe each panel, define all abbreviations, and explain the visual encoding used.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Software availability
- **Affected element** Code and implementation
- **Evidence pointer** "Supplementary Information" section
- **Issue** The manuscript mentions a "Software Manual and Description of Configuration Files" in the Supplementary Information, but the main text does not state where the software can be downloaded or whether it is open-source.
- **Required correction** Add a clear statement about software availability, including a repository URL or distribution mechanism, in the main text or Data Availability section.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical testing details
- **Affected element** Benchmark comparisons
- **Evidence pointer** Figure 2b
- **Issue** The manuscript states significance was computed using the two-sided Wilcoxon signed-rank test, but the number of paired comparisons and the handling of multiple testing corrections are not reported.
- **Required correction** Report the number of paired comparisons, whether multiple testing corrections were applied, and provide effect sizes in addition to p-values.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Definition of MAFR
- **Affected element** Methods, "Evaluation of model performance"
- **Evidence pointer** Methods section
- **Issue** The MAFR metric is defined but its interpretation and the choice of the 5% threshold for the bound set are not fully justified.
- **Required correction** Provide a more detailed explanation of MAFR, including its relationship to other dynamic range metrics and the rationale for the 5% threshold.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Comparison to other biophysical models
- **Affected element** Discussion
- **Evidence pointer** Main text, Discussion section
- **Issue** The manuscript does not discuss how ProBound compares to other biophysically motivated models such as BEESEM or GEMSTAT, beyond the benchmark comparisons.
- **Required correction** Add a brief discussion of the relationship between ProBound and existing biophysical modeling approaches, highlighting conceptual similarities and differences.

### **Technical failings that need to be addressed before the case is established**
1. KD-seq absolute calibration requires more extensive validation and clearer documentation of experimental parameters (R1-M1).
2. Benchmark comparison methodology needs more detail and per-TF breakdown to support the claim of consistent superiority (R1-M2).
3. ChIP-seq peak-free analysis needs validation across multiple TFs and discussion of identifiability (R1-M3).
4. Kinase-seq demonstration is limited to one kinase and needs broader validation (R1-M4).
5. Model selection and regularization details are insufficiently described (R1-M5).

### **Assessment against Nature-style criteria**

**Originality:** The framework's explicit modeling of the full data generation process, from molecular binding to sequencing counts, is a conceptually novel contribution. The extension to absolute KD measurement via KD-seq and the peak-free ChIP-seq analysis are original ideas. However, the underlying energy model (position-specific affinity matrices) is not new, and the novelty lies primarily in the inference framework.

**Scientific importance:** The ability to extract quantitative biophysical parameters from high-throughput sequencing data at scale has the potential to significantly advance our understanding of molecular recognition. The resource of 1,632 TF models is valuable. The KD-seq approach could enable absolute affinity measurements for many interactions that are currently only characterized relatively.

**Interdisciplinary readership:** The work bridges machine learning, biophysics, and molecular biology. The framework is general and could be applied to various protein-ligand systems. The potential applications in understanding gene regulation, signal transduction, and protein engineering are broad.

**Technical soundness:** The mathematical framework is well-constructed, and the simulations provide evidence of theoretical consistency. However, the experimental validations are limited in scope (small numbers of probes for KD-seq and kinase validation), and the benchmark comparisons need more detailed analysis. The ChIP-seq application raises identifiability concerns that are not fully addressed.

**Readability for nonspecialists:** The main text is generally well-written and accessible, with clear explanations of the key concepts. The methods section is dense but appropriate for the target audience. The figures are informative, though some figure legends could be more detailed.

### **Recommendation posture**
**Supportive if technical concerns are resolved.** The core framework is promising and the potential impact is high. However, the current evidence does not fully establish the accuracy and generalizability of the absolute KD measurements, the robustness of the benchmark claims, or the validity of the ChIP-seq peak-free approach. These concerns need to be addressed with additional validation and analysis before the manuscript is suitable for publication in a high-impact journal.

## Risk / unsupported claims
- The claim that KD-seq "determines the absolute affinity" is not fully supported by the limited validation (4 probes by EMSA) and the lack of clear documentation on how [P]T is calibrated.
- The claim that ProBound "outperformed these resources across all metrics" is based on average performance and may not hold for all TFs or all comparison pairs.
- The claim that ChIP-seq analysis can infer binding models "without peak calling" is intriguing but the identifiability of the model and the potential confounding by chromatin state are not adequately addressed.
- The generalizability of Kinase-seq to other kinases with different mechanisms is not demonstrated.
- The manuscript does not provide a full description of the model selection procedure, making it difficult to assess the risk of overfitting.