## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, limitations, methods) from bioRxiv preprint
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text; no supplementary figures or raw data were available for inspection
- **Shared manuscript claim summary** The authors use single-molecule tracking (SMT) with machine learning (pEMv2) to identify two distinct low-mobility states for H2B and multiple transcriptional regulators in the nucleus. They report that these states are not spatially separated but dynamically interconvert, that ligand activation increases the population of the lowest mobility state for steroid receptors, and that the lowest mobility state requires intact DNA-binding and oligomerization domains for PPARγ2. They propose a two-state model for chromatin and transcription factor mobility.
- **Visible evidence base** Main text figures referenced (Figs. 1-7), supplementary figures referenced (Figs. S1-S8), methods section describing SMT, pEMv2 classification, and Richardson-Lucy analysis
- **Missing materials affecting confidence** Supplementary figures and tables, raw tracking data, detailed pEMv2 output parameters, statistical test details for transition probabilities, and full figure panels were not available for independent verification

## Reviewer
- **Overall assessment** This manuscript addresses an important question in gene regulation: how transcription factors navigate the nucleus and interact with chromatin. The authors present a technically sophisticated approach combining SMT with machine learning to identify two low-mobility states shared across chromatin and transcriptional regulators. The finding that these states are dynamically interconvertible rather than spatially fixed challenges existing models and is potentially significant. However, several technical concerns regarding the classification methodology, the interpretation of the two states, and the generalizability of the conclusions need to be addressed before the case is fully established.
- **Who would be interested in the results, and why** Researchers in transcription regulation, chromatin biology, and biophysics would be interested. The work provides a framework for classifying protein mobility states in the nucleus and links these states to functional outcomes such as ligand activation and DNA-binding integrity. The methodological approach (pEMv2 combined with SMT) will also appeal to method developers in single-molecule imaging.
- **Major strengths** The study uses a rigorous machine-learning approach (pEMv2) that does not presuppose a fixed number of states, which is an improvement over earlier methods. The inclusion of multiple transcriptional regulators and two cell lines strengthens the generality of the findings. The mutational analysis of PPARγ2 provides functional validation of the mobility states. The observation of dynamic switching between states over long timescales (up to 2 minutes) is novel and important.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (classification robustness), R1-M2 (state identity and biological interpretation), R1-M3 (transition probability statistics), R1-M4 (generalizability of PPARγ2 findings)
- **Assessment against Nature-style criteria** Originality: High. The two-state model with dynamic switching is a novel contribution that challenges existing spatial domain models. Scientific importance: High. The findings have implications for understanding transcription factor search mechanisms and transcriptional regulation. Interdisciplinary readership: Moderate to high. The work bridges biophysics, cell biology, and gene regulation, and should appeal to a broad audience. Technical soundness: Moderate. The methodology is sophisticated but several technical concerns need to be resolved. Readability for nonspecialists: Good. The manuscript is generally well-written and the concepts are explained clearly, though some sections assume familiarity with SMT and machine-learning terminology.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are potentially important, but the current evidence does not fully establish the two-state model as presented.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that pEMv2 identifies two distinct low-mobility states for H2B and all tested transcriptional regulators.
- **Evidence pointer** Results section, Fig. 1C-E, Fig. 2, Fig. 4, Fig. 5A, Methods (pEMv2 classification)
- **Concern** The pEMv2 algorithm is described as exploring between 1 and 15 states, but the authors report that "the bulk of sub-tracks were classified into two states" for H2B. It is unclear how the number of states was selected for each dataset and whether the two low-mobility states are consistently recovered across all proteins and conditions. The authors state that states with population fraction smaller than 5% are removed, but the criteria for determining the final number of states (e.g., BIC score thresholds) are not fully described. Without this information, it is difficult to assess whether the two states are robust biological features or artifacts of the classification procedure.
- **Why it matters** The central claim of the paper rests on the identification of two distinct low-mobility states. If the classification is not robust or if the number of states varies across conditions, the interpretation of the results could change substantially.
- **Resolution test** Provide a detailed description of the model selection procedure, including BIC scores for different numbers of states for each protein and condition. Show that the two low-mobility states are consistently recovered across independent replicates and that the classification is stable to parameter variations (e.g., sub-track length, filtering thresholds).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors claim that the two low-mobility states represent dynamic interactions with chromatin and that state 1 is associated with active transcription.
- **Evidence pointer** Results section, Figs. 1-5, Discussion
- **Concern** The biological identity of the two low-mobility states is not clearly established. The authors infer that state 1 represents a more constrained chromatin interaction based on the effects of ligand activation and PPARγ2 mutations, but they do not directly demonstrate what distinguishes state 1 from state 2 at a molecular level. For example, it is unclear whether state 1 corresponds to specific DNA binding, interaction with nucleosomes, or some other chromatin feature. The claim that state 1 is associated with active transcription is inferred from the PPARγ2 data but is not directly tested for other factors.
- **Why it matters** The interpretation of the two states as functionally distinct is central to the proposed model. Without direct evidence linking the mobility states to specific molecular interactions or transcriptional outcomes, the biological significance of the findings remains speculative.
- **Resolution test** Provide additional evidence linking the mobility states to molecular interactions, such as colocalization with known chromatin marks, correlation with transcriptional activity at specific loci, or experiments with mutants that separate DNA-binding from other functions. Alternatively, use a reporter system to directly correlate state 1 occupancy with transcriptional output.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that transition probabilities between states are statistically significant based on permutation tests.
- **Evidence pointer** Results section, Fig. 1H, Fig. S4, Methods (transition probability calculation)
- **Concern** The permutation test for transition probabilities is described briefly. The authors state that "the statistical significance for a transition probability P t ( i, j ) is reported as the proportion of randomized trials with [condition]." The exact condition is not specified in the text provided. Additionally, the permutation test shuffles sub-track state assignments, which may not preserve the temporal correlations within tracks. This could lead to incorrect significance estimates.
- **Why it matters** The claim that molecules preferentially remain in the same state is based on these transition probabilities. If the statistical test is flawed, the conclusion that state persistence is non-random could be incorrect.
- **Resolution test** Provide a complete description of the permutation test, including the exact condition for significance. Consider using a block-permutation approach that preserves temporal correlations within tracks. Show that the results are robust to the choice of test.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that the lowest mobility state of PPARγ2 requires an intact DNA-binding domain and oligomerization domain, and that this state correlates with transcriptional activity.
- **Evidence pointer** Results section, Fig. 5, Fig. S7
- **Concern** The PPARγ2 mutational analysis is performed in 3T3-L1 cells, while the other factors are studied in 3617 cells. The authors do not discuss whether the two cell lines have different chromatin environments that could affect the mobility states. Additionally, the functional relevance of the PPARγ2 findings is inferred from the known role of PPARγ2 in adipogenesis, but no direct transcriptional readout is provided in the same cells under the same conditions as the SMT experiments.
- **Why it matters** The claim that state 1 is associated with transcriptional activity is a key part of the model. If this is only shown for one factor in one cell line without direct functional validation, the generality of the claim is weakened.
- **Resolution test** Perform SMT and transcriptional assays in the same cell system, or provide evidence that the mobility states are comparable across cell lines. Include a direct measurement of transcriptional activity (e.g., reporter gene assay or RNA FISH) correlated with the mobility states.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Methods section, pEMv2 description
- **Evidence pointer** Methods (pEMv2 classification)
- **Issue** The description of the pEMv2 algorithm is dense and assumes familiarity with the method. A brief intuitive explanation of how the algorithm works and why it is advantageous over previous methods would improve accessibility for non-specialist readers.
- **Required correction** Add a short paragraph in the Methods or Results explaining the key principles of pEMv2 in plain language.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section, Fig. 1E
- **Evidence pointer** Fig. 1E
- **Issue** The authors report that states 1 and 2 each account for approximately 35% of all sub-tracks, with about 30% unbound. It is unclear how the unbound fraction is defined and whether it is consistent across all proteins and conditions. The methods describe using H2B jump distances to set thresholds, but the rationale for this approach is not fully explained.
- **Required correction** Clarify the definition of the unbound fraction and justify the use of H2B as a reference for setting thresholds.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The discussion of the two-state model and its implications is somewhat speculative. The authors propose that state 1 represents a "loading state" for transcription, but this is not directly tested. A more measured discussion of alternative interpretations would strengthen the manuscript.
- **Required correction** Add a paragraph discussing alternative explanations for the two states and the limitations of the current data in distinguishing between them.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section, Richardson-Lucy analysis
- **Evidence pointer** Methods (RL analysis)
- **Issue** The RL analysis is used to classify entire tracks into lower or higher mobility populations, but the threshold values (e.g., MSD at 0.8 s) are not justified. It is unclear how sensitive the results are to the choice of threshold.
- **Required correction** Provide a sensitivity analysis showing that the conclusions are robust to reasonable variations in the threshold values.

## Risk / unsupported claims
- The claim that the two low-mobility states represent "common pathways for transcription activation in mammalian cells" is not directly supported by the data, as only a limited set of factors and two cell lines were tested.
- The claim that state 1 is associated with active transcription is inferred from indirect evidence (ligand activation, PPARγ2 mutations) and is not directly demonstrated.
- The claim that the two states are not spatially separated is based on the observation of switching within individual tracks, but the spatial resolution of the SMT setup may not be sufficient to rule out sub-diffraction-scale spatial organization.
- The generalizability of the PPARγ2 findings to other transcription factors is not established, as the mutational analysis was only performed for PPARγ2.