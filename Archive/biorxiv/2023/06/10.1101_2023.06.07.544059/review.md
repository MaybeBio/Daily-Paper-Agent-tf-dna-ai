## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and supplementary figure legends
- **Assessment boundary** Scientific validity, methodological soundness, claims vs. evidence, and clarity of the presented work
- **Shared manuscript claim summary** The authors extend AlphaLink, a deep learning method that integrates crosslinking mass spectrometry (MS) distance restraints into AlphaFold, to protein complexes. They report substantial improvements in modelling challenging heteromeric targets (CASP15 and antibody-antigen) with simulated crosslinks, and demonstrate utility with sparse in-cell crosslinking data from Bacillus subtilis, including a biological application revealing the structural basis of iron homeostasis via the Fur-Fpa interaction. They also apply the method to a multi-subunit Cullin4-RING ubiquitin ligase complex.
- **Visible evidence base** Main text figures (Fig 1a-d, 2a-c, 3a-e, 4a-f), Extended Data Figures 1-10, Supplementary Tables S1, Supplementary Information SI1, Supplementary Movie MS1, and Methods section
- **Missing materials affecting confidence** The manuscript does not include the actual Extended Data Figures, Supplementary Tables, or Supplementary Movie content, only their legends. No code or model weights are provided for direct inspection. The full CASP15 target list and per-target results are not shown. The SAbDab target list is not provided. The exact training hyperparameters and loss function details are not fully specified.

## Reviewer

- **Overall assessment** This manuscript presents a timely and potentially impactful extension of AlphaLink to protein complexes, addressing a critical bottleneck in structural biology. The core idea of integrating experimental crosslinking MS restraints into AlphaFold-Multimer is sound and the reported improvements on challenging targets are encouraging. The biological application to the Fur-Fpa system is a compelling demonstration of the method's practical value. However, several technical aspects require clarification and additional validation before the claims are fully established. The reliance on simulated crosslinks for the primary benchmark, the limited analysis of failure cases, and the lack of detailed comparison with alternative approaches temper the strength of the conclusions. The biological story, while interesting, is presented with limited experimental validation of the proposed structural mechanism.
- **Who would be interested in the results, and why** Structural biologists, computational biologists, and proteomics researchers interested in protein complex prediction, integrative modelling, and the application of crosslinking mass spectrometry. The work is also relevant to the broader AlphaFold user community seeking to incorporate experimental data into predictions. The Fur-Fpa biological finding will be of interest to microbiologists studying iron homeostasis and bacterial gene regulation.
- **Major strengths**
  - Addresses a significant and timely problem: improving deep learning-based protein complex prediction with experimental data.
  - The extension of AlphaLink to multimers is a logical and valuable step, with the potential for broad applicability.
  - The demonstration that a single in-cell crosslink can dramatically improve model quality is a powerful and practically important result.
  - The biological application to the Fur-Fpa system provides a compelling, real-world example of the method's utility, moving beyond purely computational benchmarks.
  - The method shows robustness to crosslinker chemistry (SDA vs DSSO) and noise, suggesting practical utility.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Claims vs. Evidence
- **Claim pointer** The claim that "Integrating crosslinking MS data substantially improves modelling performance on challenging targets" is primarily based on benchmarks using simulated crosslinks.
- **Evidence pointer** Main text Fig. 1a, Methods section "We simulate SDA crosslinks with XWalk..."
- **Concern** The primary benchmark for the central claim of the paper uses simulated crosslinks. While this is a common practice for initial validation, the simulation process may not fully capture the noise, bias, and non-uniform distribution of real crosslinking data. The authors acknowledge some limitations (e.g., uniform subsampling of crosslink candidates), but the impact of these simplifications on the reported performance gains is not systematically assessed. The results on real data (B. subtilis, CRL4) are presented as case studies, but the number of targets is small and the evaluation metrics (model confidence) are less definitive than the DockQ scores used for simulated data.
- **Why it matters** The central promise of the method is its utility with real experimental data. If the performance gains observed with simulated data do not translate to real-world scenarios, the practical impact of the work is significantly diminished. A more rigorous evaluation on a larger set of real crosslinking data, or a detailed analysis of how simulation parameters affect performance, is needed to substantiate the main claim.
- **Resolution test** The authors should either (a) validate their method on a larger, publicly available dataset of protein complexes with real crosslinking MS data and known structures, or (b) provide a detailed sensitivity analysis showing how the performance gain varies with simulation parameters (e.g., noise level, coverage, crosslinker specificity) and argue convincingly that the simulated conditions are representative of real experiments.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Reproducibility
- **Claim pointer** The method's performance is compared against "the best performing algorithms that participated in CASP15, which used up to 120x more sampling."
- **Evidence pointer** Main text Fig. 1a, Methods section "For the comparison, we use the official predictions from CASP15."
- **Concern** The comparison with CASP15 participants is not a controlled experiment. The CASP15 groups used different sampling strategies, MSA generation pipelines, and post-processing, making it difficult to attribute performance differences solely to the integration of crosslinks. The claim that AlphaLink achieves similar or better results with "up to 120x less sampling" is potentially misleading, as the baseline AlphaFold-Multimer used for comparison (NBIS-AF2-multimer) may not be the same as the versions used by other top-performing groups. A more controlled comparison, where the only variable is the presence or absence of crosslink data, is necessary to isolate the contribution of the method.
- **Why it matters** The performance comparison is a key selling point of the paper. If the comparison is not fair or controlled, the conclusion that crosslinks provide a significant advantage over brute-force sampling is weakened. The reader needs to be confident that the observed improvements are due to the crosslink information and not other confounding factors.
- **Resolution test** The authors should provide a direct, controlled comparison where AlphaLink and AlphaFold-Multimer are run under identical conditions (same MSAs, same sampling, same recycling) with and without crosslinks, for all targets. This would isolate the effect of the crosslink data. The comparison with CASP15 groups should be presented as contextual, not as a direct head-to-head benchmark.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance / Biological validation
- **Claim pointer** The claim that AlphaLink "reveals the long-enigmatic molecular basis of iron homeostasis in B. subtilis" and that the predicted Fur-Fpa complex structure explains the mechanism.
- **Evidence pointer** Main text Fig. 3a-e, Methods section "To analyze the binding of Fur to the dhbA promoter region, we performed EMSA assays..."
- **Concern** The biological story is presented as a key outcome, but the experimental validation is limited. The EMSA and beta-galactosidase assays confirm the interaction and its functional consequence (Fpa prevents Fur binding to DNA), but they do not directly validate the specific structural model proposed by AlphaLink. The claim that the structure "clearly shows why Fur bound by Fpa is incapable of binding DNA" is based on the model, but no mutagenesis or other structural validation (e.g., crosslinking validation of the specific interface, SAXS, or co-crystal structure) is provided to confirm the predicted interface and conformational changes.
- **Why it matters** The biological application is a major strength of the paper, but the strength of the claim is not matched by the experimental evidence. If the structural model is incorrect, the biological interpretation would be misleading. The paper would be significantly strengthened by additional experimental validation of the predicted Fur-Fpa interface.
- **Resolution test** The authors should provide additional experimental evidence to support the predicted structure. This could include targeted mutagenesis of the predicted interface residues followed by interaction assays, or validation of the model against additional crosslinking data (e.g., from a different crosslinker or a different laboratory). If such validation is not possible, the claims about the structural mechanism should be tempered.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Generalizability
- **Claim pointer** The claim that "our results suggest a broad applicability of AlphaLink to varying crosslinker chemistry and the typically low data densities achieved in large-scale and whole-cell crosslinking MS experiments."
- **Evidence pointer** Main text Fig. 2a-c, Methods section "For the Bacillus subtilis predictions, we use the same MSAs as O'Reilly et al."
- **Concern** The generalizability claim is based on a single dataset (B. subtilis) with a different crosslinker (DSSO) and a single multi-protein complex (CRL4). While the results are promising, the number of examples is small. The performance on the B. subtilis dataset is evaluated using model confidence, which is a proxy for accuracy and may not always correlate perfectly with structural correctness, especially for complexes with low sequence coverage or few crosslinks. The authors do not provide a clear analysis of cases where the method fails or where the crosslinks are insufficient to guide the prediction.
- **Why it matters** The claim of broad applicability is important for the impact of the work. If the method only works well under specific conditions (e.g., with a certain number of crosslinks, or for certain types of complexes), its utility is more limited. A more thorough analysis of the limits of the method is needed.
- **Resolution test** The authors should provide a more systematic analysis of the relationship between the number/quality of crosslinks and the improvement in model quality. They could also test the method on additional publicly available datasets with real crosslinking data to demonstrate generalizability.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / Readability
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The abstract and introduction are dense and assume significant prior knowledge of both AlphaFold and crosslinking mass spectrometry. The specific challenges of protein complex prediction (e.g., the "search space that grows exponentially") could be explained more clearly for a non-specialist reader.
- **Required correction** Briefly explain what AlphaFold-Multimer does and why it struggles with complexes, and what a "crosslink" is in this context, in a way that is accessible to a broad scientific audience.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness / Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section "We train on 4 A100 GPUs for 10 days."
- **Issue** The training details are sparse. The loss function, optimizer, learning rate schedule, and data augmentation strategies are not described. The exact architecture modifications to AlphaFold-Multimer (beyond adding the crosslink embedding layer) are not fully specified.
- **Required correction** Provide a more detailed description of the training procedure, including the loss function, optimizer, hyperparameters, and any changes to the model architecture. This is essential for reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity / Readability
- **Affected element** Figure 1
- **Evidence pointer** Main text Fig. 1a-d
- **Issue** The figure is complex and the caption is not fully self-explanatory. The distinction between the different panels (a, b, c, d) and the meaning of the different symbols/colors could be clearer.
- **Required correction** Improve the figure caption to clearly explain each panel, the metrics shown, and the statistical significance of the comparisons.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness / Claims vs. Evidence
- **Affected element** Main text, "A single crosslink obtained in cells can dramatically improve model quality"
- **Evidence pointer** Main text Fig. 2a-c
- **Issue** The claim that "a single crosslink can dramatically improve the results" is based on a specific example (CodY-YppF). It is unclear how general this phenomenon is. The authors show a distribution of improvements, but the specific example is highlighted.
- **Required correction** Clarify whether the dramatic improvement from a single crosslink is a common occurrence or a best-case scenario. Provide statistics on how often a single crosslink leads to a significant improvement.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness / Reproducibility
- **Affected element** Data Availability
- **Evidence pointer** Data and materials availability section
- **Issue** The statement "AlphaLink models based on experimental crosslinks have been deposited as integrative/hybrid models in PDB-Dev" is good, but the code and model weights are on GitHub and Zenodo. It is not clear if the exact training scripts and configuration files used to produce the results in this paper are included.
- **Required correction** Ensure that the code repository includes the exact training scripts, configuration files, and a README with instructions for reproducing the main results.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: The primary benchmark relies on simulated crosslinks, and the translation of these results to real-world performance is not rigorously demonstrated.
  - R1-M2: The comparison with CASP15 groups is not a controlled experiment, making it difficult to isolate the contribution of the crosslink data.
  - R1-M3: The biological mechanism proposed for Fur-Fpa is not directly validated by experiments.
  - R1-M4: The generalizability claim is based on a small number of examples with real data.

- **Assessment against Nature-style criteria**
  - **Originality:** The work is original in its specific combination of crosslinking MS data with AlphaFold-Multimer for protein complexes. While the concept of integrating experimental restraints into deep learning models is not entirely new, the extension to multimers and the demonstration on challenging targets and a biological system is a novel contribution.
  - **Scientific importance:** The problem of protein complex prediction is of high importance. The potential to use sparse, readily obtainable experimental data to guide predictions could have a significant impact on the field. The biological application to iron homeostasis is also of interest.
  - **Interdisciplinary readership:** The work is likely to appeal to a broad readership, including structural biologists, computational biologists, proteomics researchers, and microbiologists. The methods and concepts are relevant across these disciplines.
  - **Technical soundness:** The technical approach is generally sound, but the validation is incomplete. The reliance on simulated data for the main benchmark and the lack of controlled comparisons are significant weaknesses. The biological validation is also limited.
  - **Readability for nonspecialists:** The manuscript is written for a specialist audience. The abstract and introduction are dense and may be challenging for readers outside the immediate field. The main text is generally clear, but the methods are highly technical.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the potential impact is high. However, the current evidence base is insufficient to fully support the central claims. The authors must address the concerns regarding the use of simulated data, the controlled comparison, and the biological validation before the case is fully established.