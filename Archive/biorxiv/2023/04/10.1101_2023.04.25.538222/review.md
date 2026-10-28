## Review setup
- **Input scope** Full manuscript text (summary, introduction, results, discussion, methods, figure legends not provided)
- **Assessment boundary** Scientific content, methodological rigor, logical coherence, and support of claims by presented evidence; limited to material supplied
- **Shared manuscript claim summary** The authors combine live imaging of tagged Sox2 promoter and enhancer loci with molecular dynamics simulations to show that chromatin mobility, rather than promoter-enhancer distance, correlates with transcriptional status; that active elements are more constrained; that loop extrusion and transcription factor-mediated clustering have antagonistic effects on chromatin dynamics; and that this competition is necessary to recapitulate experimental observations in simulations.
- **Visible evidence base** Results sections describing live imaging, perturbation experiments (triptolide, CTCF deletions, SRR107/111 deletions), 3D DNA FISH, 4C-seq, single-molecule RNA FISH, ChIP-qPCR, and molecular dynamics simulations; references to Figures 1-7 and Supplementary Figures S1-S9 and Tables S1-S7; methods section
- **Missing materials affecting confidence** Figure panels and legends, supplementary figures and tables, numerical data underlying statistical tests, simulation parameter details, and code availability; these omissions limit full verification of statistical claims and model behavior

## Reviewer

- **Overall assessment** This manuscript addresses a fundamental question in gene regulation: how promoter-enhancer communication and chromatin dynamics are coordinated. The combination of high-resolution live imaging with perturbation experiments and simulations is ambitious and timely. The central finding that chromatin mobility, not physical distance, tracks transcriptional status, and that loop extrusion and transcription-associated clustering have opposing effects on dynamics, is potentially important. However, the evidence as presented has several gaps that prevent full confidence in the conclusions. Key issues include the reliance on a single locus, the indirect nature of some perturbation effects, the limited statistical detail, and the need for clearer demonstration that the simulation model captures the essential biology rather than being tuned to match observations. The manuscript is well written and will interest a broad readership, but the case is not fully established from the provided material.

- **Who would be interested in the results, and why** Researchers in gene regulation, chromatin biology, and nuclear organization will find this relevant. The work speaks to ongoing debates about the role of looping versus dynamic hubs in enhancer function, and the use of live imaging to dissect these processes is of broad interest. The methodological framework for analyzing chromatin mobility and the simulation approach may also appeal to biophysicists and computational biologists studying polymer dynamics.

- **Major strengths** 
  1. The use of small ANCHOR tags placed close to the Sox2 promoter and within the enhancer is a technical advance that allows direct visualization of regulatory elements with minimal perturbation.
  2. The combination of experimental perturbations with molecular dynamics simulations provides a framework for interpreting complex dynamic data.
  3. The finding that enhancer mobility specifically decreases upon transcriptional activation, while promoter mobility is unaffected, is a novel and potentially significant observation.
  4. The demonstration that CTCF and transcription factor binding site deletions have opposing effects on local mobility is intriguing and may help reconcile conflicting literature.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The claim that "alterations in chromatin mobility, not promoter-enhancer distance, is more informative about transcriptional status" is central to the paper.
- **Evidence pointer** Results sections "Enhancer-promoter proximity is frequently maintained at the Sox2 locus independent of transcription" and "The SCR has reduced chromatin dynamics on transcriptional firing"; Figures 2, 5
- **Concern** The evidence for this claim rests on comparisons of median distances and mobility parameters across conditions, but the statistical framework is not fully described. For example, the comparison of Sox2-SCR distances between transcribing and non-transcribing alleles (Figure 5c) reports a non-significant difference, but the power to detect meaningful differences is unclear given the sample sizes. More critically, the claim that mobility is "more informative" requires a direct statistical comparison of the predictive power of distance versus mobility, which is not presented. The authors should provide effect sizes, confidence intervals, and ideally a model comparison to support this strong claim.
- **Why it matters** This is the central conclusion of the paper. If the statistical support is weak, the entire narrative is undermined.
- **Resolution test** Provide a formal statistical analysis comparing the ability of distance versus mobility parameters to predict transcriptional status, including effect sizes and confidence intervals. Alternatively, soften the claim to match the evidence.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validity
- **Claim pointer** The claim that simulations "recapitulate these experimental findings only when competition between loop extrusion and transcription-linked enhancer-promoter communication was reinforced" is used to support the biological interpretation.
- **Evidence pointer** Results section "Opposing effects of loop extrusion and promoter-enhancer communication on local chromatin mobility"; Figures 7, S8
- **Concern** The simulation model is described as being adjusted (e.g., "reinforced competition") to match experimental results. This raises concerns about circularity. The authors need to demonstrate that the model makes testable predictions that are not simply fitted to the data. Specifically, the claim that the original model failed and the revised model succeeded needs quantitative comparison, and the parameter changes should be justified on biological grounds rather than as a fitting exercise. Additionally, the model's ability to reproduce the specific experimental observations (e.g., the differential mobility of enhancer vs. promoter) should be shown with uncertainty estimates.
- **Why it matters** The simulations are used to infer mechanistic antagonism. If the model is overfitted, the inference is not reliable.
- **Resolution test** Provide a clear description of the model parameters that were changed, justify them with independent evidence, and show that the revised model's success is not simply a result of increased flexibility. Ideally, perform a sensitivity analysis and test a priori predictions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors generalize from the Sox2 locus to broader principles of "promoter and enhancer dynamics."
- **Evidence pointer** Discussion section
- **Concern** The study is performed at a single locus (Sox2) in a single cell type (mouse ESCs). While the Sox2 locus is a good model, the authors should be cautious in generalizing. The discussion does acknowledge this, but the abstract and summary make broad claims. The authors should either provide evidence from additional loci or temper the general claims.
- **Why it matters** Overgeneralization could mislead the field if the observed phenomena are locus-specific.
- **Resolution test** Add a clear statement of limitations in the discussion, or provide preliminary data from a second locus to support generalizability.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical validation
- **Claim pointer** The claim that the ANCHOR system has "negligible observable effects on transcription, nuclear organization and cell state" is used to validate the imaging approach.
- **Evidence pointer** Results section "Enhancer-promoter proximity is frequently maintained at the Sox2 locus independent of transcription"; Figure 1c,d; Figure S1
- **Concern** The validation of the ANCHOR system relies on a limited set of assays (qRT-PCR, 4C-seq, cell cycle analysis). The authors should provide more comprehensive validation, such as RNA-seq or ChIP-seq to ensure that the insertion of ANCHOR tags does not alter the local chromatin state or enhancer activity. Additionally, the effect of ParB binding on chromatin dynamics is not directly assessed.
- **Why it matters** If the tags alter the very properties being measured, the conclusions are invalid.
- **Resolution test** Provide additional validation data, such as RNA-seq or ATAC-seq, comparing tagged and untagged cells, and assess whether ParB binding itself affects mobility.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 3c
- **Evidence pointer** Results section "Promoters and enhancers have more constrained chromatin motion than control sequences"
- **Issue** The distribution of alpha_app values is shown, but the text does not clearly explain how the "apparent" alpha differs from the true alpha and what the biological interpretation of the difference is.
- **Required correction** Add a brief explanation of the apparent alpha and its interpretation in the text or figure legend.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Molecular dynamics simulations"
- **Evidence pointer** Methods section
- **Issue** The simulation parameters are described, but the code and input files are not provided. This limits reproducibility.
- **Required correction** Provide a link to a repository with the simulation code and parameters, or include them as supplementary material.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Multiple results sections
- **Evidence pointer** Results sections; Tables S1, S2
- **Issue** The number of biological replicates and the total number of cells analyzed for each condition are not consistently reported in the text.
- **Required correction** Add a summary table of sample sizes for each experiment, or state them clearly in the text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The discussion of "hit and run" mechanisms is speculative and not directly tested. This is fine, but it should be clearly labeled as speculation.
- **Required correction** Add a sentence clarifying that this is a hypothesis that requires further testing.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Figure 7d
- **Evidence pointer** Results section "Opposing effects of loop extrusion and promoter-enhancer communication on local chromatin mobility"
- **Issue** The schematic model in Figure 7d is mentioned, but the figure itself is not provided in the text. The model is important for understanding the conclusions.
- **Required correction** Ensure the figure is included and described in sufficient detail in the legend.

## Risk / unsupported claims
- The claim that "alterations in chromatin mobility, not promoter-enhancer distance, is more informative about transcriptional status" is not fully supported by the statistical analysis presented.
- The claim that simulations "recapitulate these experimental findings only when competition between loop extrusion and transcription-linked enhancer-promoter communication was reinforced" is at risk of circularity without a clear demonstration that the model is not overfitted.
- The generalization from the Sox2 locus to general principles of promoter-enhancer dynamics is not fully supported by evidence from a single locus.
- The claim that the ANCHOR system has "negligible observable effects" is based on limited validation assays.
- The specific molecular mechanism of "competition" between loop extrusion and transcription is inferred from simulations and indirect perturbations, not directly demonstrated.