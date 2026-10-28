## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific claims, methodology, and interpretation as presented in the provided manuscript
- **Shared manuscript claim summary** The authors apply AlphaFold to predict protein-protein interactions (PPIs) for 360 human proteins with Asp/Glu-ADP-ribosylation (D/E-PARylation) sites, identify 260 confident PPIs, map D/E-PARylation sites onto predicted interfaces, and propose functional implications for PARylation in regulating RNA processing, DNA repair, and chromatin remodeling, including a specific cross-talk mechanism between PARylation and SUMOylation via SUMO2-CHAF1A.
- **Visible evidence base** Abstract, Introduction, Materials and methods, Results and discussion, Concluding remarks, Data availability statement. No figures, tables, or supplementary materials were provided.
- **Missing materials affecting confidence** All figures (Figures 1–7), supplementary tables (S1, S2), supplementary Figure S1, and the structural model repository link could not be accessed. These are essential for evaluating the validity of AlphaFold predictions, interface mapping, and statistical analyses.

## Reviewer
- **Overall assessment** The manuscript presents a potentially interesting application of AlphaFold to study the structural context of D/E-PARylation sites in human proteins. The central idea, that mapping PTM sites onto predicted PPI interfaces can generate mechanistic hypotheses, is timely and relevant. However, the current manuscript has significant limitations. The evidence base is heavily dependent on computational predictions without experimental validation, the description of the AlphaFold methodology lacks critical details for reproducibility, and the statistical framework for assessing interface enrichment is not described. The biological conclusions, while plausible, are largely speculative and not quantitatively supported by the data as presented. The manuscript would benefit from a more rigorous treatment of prediction confidence, a clearer distinction between established and predicted interactions, and a more cautious interpretation of functional consequences.
- **Who would be interested in the results, and why** Researchers in the fields of posttranslational modification biology, particularly those studying ADP-ribosylation, and computational biologists interested in applying deep learning-based structure prediction to functional genomics. The work may also appeal to scientists studying DNA damage response, RNA processing, and chromatin remodeling, as it offers a resource of predicted PPIs and structural models that could guide experimental design.
- **Major strengths** 1. The application of AlphaFold to a biologically relevant PTM dataset is novel and demonstrates a creative use of a powerful tool. 2. The focus on D/E-PARylation, a less-studied PTM type, addresses a gap in the literature. 3. The identification of recurring interaction motifs (e.g., beta-strand complementation) provides a potentially generalizable insight. 4. The authors provide a public resource for structural models, which is commendable for community use.
- **Major Concerns** 
  - **Concern ID** R1-M1
  - **Severity** Major
  umber- **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that AlphaFold predicted 260 confident PPIs involving PARylated proteins, and that D/E-PARylation sites are enriched in PPI interfaces.
  - **Evidence pointer** Results and discussion, section "Prediction of protein-protein interactions of D/E-PARylated proteins"; location not provided
  - **Concern** The manuscript does not provide a clear definition of "confident" PPIs beyond a contact probability threshold of 0.9. The choice of this threshold is not justified, and no information is given about the distribution of scores, the false positive rate, or how this threshold compares to established benchmarks for AlphaFold-based PPI prediction. Furthermore, the claim of enrichment of D/E-PARylation sites in interfaces is not supported by a statistical test comparing observed versus expected frequencies, nor is it clear what the appropriate null model would be.
  - **Why it matters** Without a rigorous and transparent definition of prediction confidence and a statistical framework for enrichment analysis, the core quantitative claims of the manuscript cannot be evaluated. The threshold of 0.9 may be arbitrary, and the enrichment claim could be a result of the inherent properties of the proteins studied rather than a specific feature of PARylation sites.
  - **Resolution test** The authors should provide a detailed description of the score distribution, justify the chosen threshold with reference to benchmarks or independent validation, and perform a statistical test for interface enrichment (e.g., permutation test or comparison to a control set of non-PARylated proteins) with appropriate multiple testing correction.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors state that AlphaFold models of protein complexes were generated by splitting proteins into domains based on predicted aligned error (PAE) and modeling all pairs of domains.
  - **Evidence pointer** Materials and methods, section "Modeling protein complexes with AlphaFold"; location not provided
  - **Concern** The description of the domain-splitting procedure is insufficient for reproducibility. The criteria for splitting (Dintra/Dinter ratio thresholds of 10 or 20) are stated, but the algorithm for finding the split site is not described in detail. More critically, the manuscript does not address how the domain-level predictions were combined to assess full-length protein interactions, nor does it discuss potential artifacts introduced by this approach, such as missing interactions that occur across domain boundaries or false positives due to domain-level truncation.
  - **Why it matters** The domain-splitting approach is a non-standard use of AlphaFold, and its validity is central to the reliability of all predicted PPIs. If the method introduces systematic biases, the subsequent biological interpretations would be compromised. The lack of detail prevents other researchers from replicating the work or assessing its robustness.
  - **Resolution test** The authors should provide a step-by-step description of the splitting algorithm, including pseudocode or a reference to an available implementation. They should also validate the domain-level approach against full-length complex predictions for a subset of cases, and discuss any discrepancies. Additionally, an analysis of how many of the 260 predicted PPIs rely on domain-level versus full-length modeling would be informative.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Scientific importance
  - **Claim pointer** The authors propose that D/E-PARylation at specific sites (e.g., SUMO2 E13) could modulate protein interactions and represent a mechanism of cross-talk between PARylation and SUMOylation.
  - **Evidence pointer** Results and discussion, sections "PCNA - a hub of PPIs with PARylation sites in the interaction interfaces" and "D/E-PARylation sites in other PPI interfaces"; location not provided
  - **Concern** The functional claims are based solely on the presence of D/E-PARylation sites in predicted interfaces. No experimental evidence is provided to show that PARylation at these sites actually occurs in a physiological context, that it affects the predicted interactions, or that it has functional consequences. The authors acknowledge this in some cases (e.g., "warrants future studies"), but the overall tone of the discussion implies a level of confidence that is not supported by the data.
  - **Why it matters** The manuscript's contribution to understanding PARylation function is limited if the predictions are not validated. The claims about cross-talk between PARylation and SUMOylation, while interesting, are speculative and could mislead readers if not clearly framed as hypotheses. The scientific importance of the work depends on the reliability of the predictions and the strength of the functional inferences.
  - **Resolution test** The authors should clearly distinguish between validated and predicted interactions throughout the text. For key claims (e.g., SUMO2-CHAF1A), they should either provide experimental validation (e.g., mutagenesis, pull-down assays) or explicitly state that these are testable predictions. A more conservative interpretation of the functional implications would strengthen the manuscript.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Readability for nonspecialists
  - **Claim pointer** The manuscript describes the use of AlphaFold and its outputs without sufficient context for readers unfamiliar with the tool.
  - **Evidence pointer** Introduction and Materials and methods; location not provided
  - **Concern** The manuscript assumes a high level of familiarity with AlphaFold, its capabilities, and its limitations. Terms such as "contact probability," "pLDDT," and "PAE" are used without adequate explanation of what they mean for a general biology audience. The distinction between predicted and experimentally determined structures is not always clear.
  - **Why it matters** The target audience for a journal like Proteomics includes many experimental biologists who may not be experts in computational structure prediction. If the methods and results are not accessible, the impact of the work will be diminished, and readers may not be able to critically evaluate the claims.
  - **Resolution test** The authors should add a brief primer on AlphaFold and its outputs in the Introduction or Materials and methods, explaining key concepts in plain language. They should also ensure that all figures and tables are self-explanatory with clear legends that do not require prior knowledge of structural bioinformatics.
- **Minor Comments** 
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods, PPI filtering criteria
  - **Evidence pointer** Materials and methods, section "Identification of D/E-PARylated proteins and their potential interactions partners"; location not provided
  - **Issue** The criteria for selecting 5,859 "more confident" PPIs from the initial 72,431 are described, but the rationale for the specific thresholds (summed support score >= 0.1 for single-paper support, >= 0.01 for multi-paper support) is not explained.
  - **Required correction** Provide a justification for these thresholds, perhaps by referencing previous work or showing a sensitivity analysis. Alternatively, state that these are arbitrary and discuss the potential impact on the results.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods, AlphaFold confidence metrics
  - **Evidence pointer** Materials and methods, section "Modeling protein complexes with AlphaFold"; location not provided
  - **Issue** The manuscript uses "contact probability" as the primary confidence metric but does not specify how this is calculated from the AlphaFold output (e.g., from the predicted distance distribution or the predicted aligned error).
  - **Required correction** Clarify the exact definition of contact probability used, including the distance threshold and how it is derived from AlphaFold's output.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Scientific importance
  - **Affected element** Discussion of PARylation site conservation
  - **Evidence pointer** Results and discussion, section "Prediction of protein-protein interactions of D/E-PARylated proteins"; location not provided
  - **Issue** The statement that D/E-PARylation sites in interfaces have a higher fraction in the high conservation category is made without statistical support or a clear comparison to the overall conservation distribution.
  - **Required correction** Provide a statistical test for this comparison and show the full distribution of conservation scores for interface versus non-interface sites.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Figure legends
  - **Evidence pointer** Figures 1–7; location not provided
  - **Issue** The figure legends are not provided in the manuscript text, making it impossible to assess whether they are clear and self-contained.
  - **Required correction** Ensure that all figure legends are included in the manuscript and provide sufficient context for readers to understand the data without referring to the main text.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Data availability
  - **Evidence pointer** Data availability section; location not provided
  - **Issue** The data availability statement provides a link to download structural models but does not specify the format, the number of models, or any associated metadata.
  - **Required correction** Provide a more detailed description of the data repository, including file formats, naming conventions, and any relevant documentation.

## Risk / unsupported claims
- The claim that D/E-PARylation sites are enriched in PPI interfaces is unsupported without a statistical test.
- The functional implications for PARylation in regulating RNA processing, DNA repair, and chromatin remodeling are speculative and not directly tested.
- The proposed cross-talk mechanism between PARylation and SUMOylation via SUMO2-CHAF1A is a hypothesis without experimental support.
- The claim that AlphaFold predictions offer "novel insights" into PARylation regulation is not fully substantiated without comparison to existing structural or interaction data.
- The statement that PARylation could "negatively affect" transcription and RNA processing during genotoxic stress is presented as a conclusion rather than a hypothesis.
- The generalizability of the recurring beta-strand interaction motif is claimed without a systematic analysis of how often this pattern occurs in the full set of predicted interfaces versus a control set.

## Assessment against Nature-style criteria
- **Originality** The application of AlphaFold to map PTM sites onto PPI interfaces is a creative and relatively novel approach. However, the concept of using structural predictions to understand PTM function is not entirely new, and the manuscript does not clearly position itself relative to prior computational studies of PTM sites in structural contexts.
- **Scientific importance** The work addresses a relevant question about the functional impact of a less-studied PTM. If the predictions are reliable, the resource could be valuable. However, the lack of experimental validation and the speculative nature of the functional claims limit the immediate importance. The potential impact is moderate and depends on future validation.
- **Interdisciplinary readership** The work bridges structural biology, bioinformatics, and PTM biology, which could appeal to a broad audience. However, the technical details of the AlphaFold methodology may be challenging for experimental biologists, and the biological implications may not be sufficiently developed to engage computational specialists.
- **Technical soundness** The methodology has several gaps, including unclear thresholds for PPI confidence, insufficient detail on domain splitting, and a lack of statistical rigor in enrichment analyses. These issues undermine the technical soundness of the work as presented.
- **Readability for nonspecialists** The manuscript is generally well-written but assumes familiarity with AlphaFold and structural prediction concepts. The abstract and introduction are accessible, but the methods and results sections would benefit from additional context and explanation for a broader audience.

## Recommendation posture
Currently not established from the provided evidence. The manuscript presents an interesting computational approach and a potentially useful resource, but the core claims are not sufficiently supported due to methodological gaps and lack of validation. The authors should address the major concerns, particularly around PPI confidence thresholds, domain-splitting methodology, and statistical analysis of interface enrichment, before the case for the manuscript's conclusions can be established. If these issues are resolved and the claims are appropriately tempered, the work could be considered for publication.