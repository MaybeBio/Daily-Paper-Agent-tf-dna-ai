## Review setup
- **Input scope** Full manuscript text, including summary, introduction, methods, results, discussion, and supplementary figure legends
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors report that human ATAC and SAGA histone acetyltransferase (HAT) modules bind nucleosomes with high affinity independent of post-translational modifications and transcription factors, directly interact with the VP16 activator domain, enhance acetylation activity in the presence of a TF containing this domain, and increase TF binding to its DNA target site within nucleosomes by an order of magnitude in an acetylation-independent manner
- **Visible evidence base** In vitro biochemical assays (fluorescence anisotropy, FRET, GST pull-down, western blot-based acetylation assays) using recombinant human HAT modules, recombinant nucleosomes, and Gal4-VP16/Gal4-DBD constructs
- **Missing materials affecting confidence** Raw data files, full uncropped western blots, replicate numbers for each experiment, statistical details for all comparisons, supplementary figures S1-S7 and tables S1-S4 referenced but not fully described in the text, and detailed methods for the GST pull-down assay

## Reviewer
- **Overall assessment** This manuscript presents a systematic in vitro characterization of the interactions between human ATAC and SAGA HAT modules, nucleosomes, and the model transcription factor Gal4-VP16. The work addresses an important question in gene regulation, namely how coactivator complexes and transcription factors coordinate their activities on chromatin. The finding that HAT modules facilitate TF binding to nucleosomal DNA in an acetylation-independent manner is potentially novel and of broad interest. However, the manuscript has several technical and interpretive issues that need to be addressed before the central claims can be fully supported. The distinction between the HAT modules and the full complexes, the mechanistic basis for the acetylation-independent TF facilitation, and the physiological relevance of the observed effects require further clarification and experimental support.

- **Who would be interested in the results, and why** Researchers in the fields of chromatin biology, transcription regulation, and epigenetics would be the primary audience. The work is also relevant to those studying coactivator complexes, histone acetyltransferases, and the mechanisms of transcription factor access to nucleosomal DNA. The potential acetylation-independent function of HAT modules could have implications for understanding how chromatin-modifying complexes contribute to gene activation beyond their enzymatic activities.

- **Major strengths** The study uses well-controlled in vitro reconstitution systems with purified recombinant components, which allows for direct mechanistic interrogation. The combination of fluorescence anisotropy, FRET, and biochemical acetylation assays provides complementary approaches to characterize protein-protein and protein-nucleosome interactions. The inclusion of both Gal4-VP16 and Gal4-DBD allows the authors to partially separate the contributions of the DNA-binding domain and the activation domain. The finding that HAT modules enhance TF binding in an acetylation-independent manner is a potentially significant observation that could shift thinking about how these complexes function.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design and controls
- **Claim pointer** The authors claim that ATAC and SAGA HAT modules bind nucleosomes with high affinity independent of post-translational modifications and TFs, and that this binding does not significantly alter DNA wrapping.
- **Evidence pointer** Figure 1D-E, Supplementary Figure S5A-B, Supplementary Table S1
- **Concern** The fluorescence anisotropy binding experiments are performed with unmodified recombinant nucleosomes, which is appropriate for testing PTM independence. However, the claim that binding is independent of TFs is based on experiments where TFs are absent, which does not directly test whether TFs influence HAT module-nucleosome binding. The FRET experiments showing minimal unwrapping are performed over the concentration range where HAT modules bind, but the sensitivity of the FRET assay to detect partial unwrapping events is not calibrated or validated. The authors do not provide a positive control demonstrating that the FRET assay can detect partial unwrapping, such as with a known nucleosome-binding protein that induces unwrapping.
- **Why it matters** The conclusion that HAT modules bind nucleosomes with high affinity and do not induce unwrapping is foundational for the subsequent claims in the paper. If the binding affinity is overestimated or if the FRET assay is not sensitive enough to detect partial unwrapping, the interpretation of the later experiments could be affected. The claim of TF independence is not directly tested and requires an experiment where TF and HAT module are both present.
- **Resolution test** The authors should include a positive control for the FRET assay, such as a known chromatin remodeler or histone chaperone that induces partial unwrapping, to demonstrate the assay can detect such events. They should also perform competition or ternary complex experiments to directly test whether TF presence influences HAT module-nucleosome binding affinity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data interpretation and mechanistic claims
- **Claim pointer** The authors claim that ATAC and SAGA HAT modules increase TF binding to its DNA target site within the nucleosome by an order of magnitude independent of histone acetylation.
- **Evidence pointer** Figure 5A-F, Supplementary Figure S7, Supplementary Table S4
- **Concern** The FRET-based TF binding experiments show that the presence of HAT modules lowers the S1/2 for Gal4-VP16 binding from 55 ± 2 nM to 5.3 ± 0.7 nM (ATAC) and 7 ± 1 nM (SAGA). However, the mechanism for this enhancement is not established. The authors suggest that HAT modules may stabilize the partially unwrapped state, but they do not provide direct evidence for this. Alternative explanations include non-specific stabilization of the nucleosome, direct protein-protein interactions that alter the conformational landscape, or the HAT modules acting as molecular crowding agents. The claim that this is acetylation-independent is supported by experiments without Ac-CoA, but the authors do not test whether catalytically dead HAT module mutants would have the same effect, which would strengthen this conclusion.
- **Why it matters** The central novel claim of the paper is that HAT modules facilitate TF binding in an acetylation-independent manner. Without a mechanistic explanation or experiments with catalytically inactive mutants, the claim remains phenomenological. The distinction between the HAT module acting as a passive binding partner versus an active facilitator is important for understanding the biological function.
- **Resolution test** The authors should perform experiments with catalytically dead mutants of the HAT modules (e.g., KAT2A catalytic site mutations) to confirm that the TF binding enhancement is truly independent of acetyltransferase activity. They should also consider experiments that directly test whether the HAT modules stabilize the unwrapped state, such as measuring unwrapping kinetics or using single-molecule approaches.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and physiological relevance
- **Claim pointer** The authors suggest that their findings reveal synergistic coordination between HAT modules and a TF, where HAT modules both acetylate histones to open chromatin and facilitate TF targeting within nucleosomes.
- **Evidence pointer** Discussion section, Figure 6
- **Concern** The study uses a single model TF (Gal4-VP16) and a single nucleosome positioning sequence (Widom 601) with a Gal4 binding site at a specific position. The generalizability of the findings to other TFs, other binding site positions, and other nucleosome sequences is not tested. The physiological relevance of the observed effects is also unclear, as the experiments are performed with purified components at concentrations that may not reflect cellular conditions. The proposed models in Figure 6 are speculative and not directly tested.
- **Why it matters** The authors make broad claims about the coordination between HAT modules and TFs in gene regulation. Without testing additional TFs or nucleosome contexts, it is difficult to assess whether the observed effects are specific to this experimental system or represent a general mechanism. The physiological relevance of the acetylation-independent TF facilitation is important for the broader significance of the work.
- **Resolution test** The authors should test at least one additional TF and/or vary the position of the binding site within the nucleosome to assess generalizability. They should also discuss the concentrations used in their assays relative to estimated cellular concentrations and acknowledge the limitations of the in vitro system.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative analysis and statistics
- **Claim pointer** The authors report S1/2 values with standard errors for various binding interactions and acetylation fold-changes with statistical significance.
- **Evidence pointer** Figure 3D, Figure 4B-C, E, Figure 5C, F, Supplementary Tables S1-S4
- **Concern** The statistical analysis is described as using two-tailed, unpaired t-tests with Welch's correction, but the number of independent replicates for each experiment is not clearly stated in the text. The fold-changes in acetylation are reported with error bars representing standard error of the mean, but the number of biological replicates is not specified. For the binding isotherm fits, the S1/2 values are reported with standard errors from the fits, but it is unclear how many independent titration experiments were performed and whether the reported errors reflect inter-experiment variability or just the fitting uncertainty.
- **Why it matters** The quantitative claims in the paper, particularly the fold-changes in acetylation and the changes in S1/2 values, depend on the reliability of the statistical analysis. Without clear information on replicate numbers and the nature of the errors, it is difficult to assess the robustness of the conclusions.
- **Resolution test** The authors should clearly state the number of independent replicates for each experiment in the figure legends or methods, and clarify whether the reported errors represent inter-experiment variability. They should also consider reporting confidence intervals for the S1/2 values.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Figure 1A
- **Evidence pointer** Figure 1A
- **Issue** The schematic in Figure 1A is described in the text but the actual content of the figure is not visible in the provided manuscript. The description mentions that ATAC and SAGA HAT modules share three subunits (KAT2A/KAT2B, TADA3, SGF29) and differ in the fourth subunit (TADA2A vs TADA2B), but this is not clearly illustrated.
- **Required correction** Ensure the figure clearly shows the subunit composition of both HAT modules and highlights the shared and distinct subunits.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methods detail
- **Affected element** GST pull-down assay
- **Evidence pointer** Methods section, Supplementary Figure S4
- **Issue** The GST pull-down assay is mentioned in the results and contributions but the detailed method is not fully described in the methods section. The text states that the assay was "previously described" but does not provide sufficient detail for replication.
- **Required correction** Provide a more detailed description of the GST pull-down assay conditions, including buffer composition, incubation times, and washing steps.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Western blot quantification
- **Evidence pointer** Figure 4, Supplementary Figure S6
- **Issue** The western blot quantification is described as using densitometry analysis in ImageJ, but the normalization strategy is not clearly described. It is unclear whether the acetylation signals are normalized to total histone levels or to loading controls.
- **Required correction** Clearly describe the normalization strategy for the western blot quantification in the methods or figure legends.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion of differential acetylation targets
- **Evidence pointer** Introduction, Discussion
- **Issue** The authors mention that ATAC and SAGA have different histone acetylation targets in vivo, but the relevance of this difference to the current findings is not fully discussed. The observation that Gal4-VP16 enhances ATAC HAT acetylation more than SAGA HAT is noted but not mechanistically explored.
- **Required correction** Add a brief discussion of how the differential acetylation targets of ATAC and SAGA might relate to the observed differences in TF-mediated acetylation enhancement.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of acetylation-independent functions of histone-modifying enzymes is brief and could benefit from more specific references to recent studies that have demonstrated such functions.
- **Required correction** Expand the discussion with specific examples of other histone-modifying enzymes that have non-catalytic functions, to better contextualize the novelty of the current findings.

## Risk / unsupported claims
- The claim that ATAC and SAGA HAT modules increase TF binding by an order of magnitude independent of acetylation is supported by the data, but the mechanistic basis is not established and the claim that this is a general mechanism is not supported.
- The claim that the HAT modules do not directly induce nucleosome unwrapping is based on FRET experiments that lack a positive control demonstrating the assay can detect unwrapping.
- The claim that KAT2A is likely to contribute to TF binding in both HAT modules is based on the observation that KAT2A alone binds VP16 AD, but this does not establish that KAT2A is the relevant subunit in the context of the full HAT modules.
- The proposed models in Figure 6 are speculative and not directly tested by the experiments presented.
- The physiological relevance of the findings is not established, as the experiments are performed with purified components in vitro.
- The generalizability of the findings to other TFs, nucleosome sequences, and binding site positions is not tested.

## Assessment against Nature-style criteria
- **Originality** The finding that HAT modules can facilitate TF binding to nucleosomal DNA in an acetylation-independent manner is potentially original and could represent a new function for these complexes. However, the concept of non-catalytic functions for chromatin-modifying enzymes is not entirely new, and the novelty of this specific finding needs to be more clearly articulated in the context of existing literature.
- **Scientific importance** The work addresses a fundamental question in gene regulation, namely how coactivator complexes and TFs coordinate their activities on chromatin. If the findings are robust and generalizable, they could have significant implications for understanding transcriptional activation mechanisms. However, the current study is limited to in vitro experiments with a single model system, which limits the immediate importance.
- **Interdisciplinary readership** The topic is of interest to researchers in chromatin biology, transcription, and epigenetics, but the specialized nature of the in vitro biochemical approach may limit broader appeal. The findings could be of interest to a wider audience if the physiological relevance were more clearly demonstrated.
- **Technical soundness** The experimental approaches are generally appropriate and well-controlled, but there are several technical concerns that need to be addressed, including the lack of a positive control for the FRET unwrapping assay, unclear replicate numbers, and the absence of experiments with catalytically dead mutants to confirm acetylation independence.
- **Readability for nonspecialists** The manuscript is generally well-written and the logic is clear, but the specialized terminology and detailed biochemical methods may be challenging for nonspecialists. The summary and introduction provide good context, but the results section assumes significant background knowledge.

## Recommendation posture
Supportive if technical concerns are resolved. The central finding is potentially interesting and novel, but the manuscript requires additional experiments and clarifications to fully support the claims. Specifically, the authors should provide a positive control for the FRET unwrapping assay, perform experiments with catalytically dead HAT module mutants to confirm acetylation independence, clearly state replicate numbers and statistical details, and address the generalizability of the findings. The mechanistic basis for the acetylation-independent TF facilitation also needs to be explored or at least discussed more thoroughly.