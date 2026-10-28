## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report that a PfmiR156f-PfSPL regulatory module responds to phytoplasma stress in *Paulownia fortunei*. They claim that PfmiR156 cleaves PfSPL1 and PfSPL10 transcripts at specific sites, that PfSPL1 protein stability is regulated by the 26S proteasome pathway, and that multiple phytoplasma effectors target PfSPL1, potentially via its conserved SBP domain. They conclude that PfSPL1 stability is controlled by both miRNA-mediated cleavage and proteasomal degradation, and that this contributes to understanding phytoplasma pathogenesis.
- **Visible evidence base** Abstract text only; methods and results are summarized without numerical data, statistical details, or experimental controls
- **Missing materials affecting confidence** Full manuscript, all figures and tables, degradome and ceRNA sequencing datasets, RLM-5'RACE results, dual luciferase assay data, proteasome inhibitor experiments, molecular docking parameters, effector localization and interaction validation, statistical analyses, and any negative controls

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting regulatory module involving a microRNA and a transcription factor in a plant pathogen response. However, the evidence as summarized is insufficient to establish the central claims. Several conclusions appear to extend beyond what the described experiments can support, particularly regarding effector targeting and the functional significance of PfSPL1 stability. The work may be of interest to plant pathologists and molecular biologists studying phytoplasma interactions, but the current abstract does not provide enough detail to assess technical rigor or biological significance.
- **Who would be interested in the results, and why** Researchers studying plant-microbe interactions, particularly phytoplasma pathogenesis and effector biology, as well as those interested in miRNA-mediated regulation of transcription factors in plant stress responses. The ceRNA and degradome sequencing approach may also appeal to scientists working on regulatory networks in non-model plants.
- **Major strengths** The study combines multiple complementary approaches, including degradome sequencing, RLM-5'RACE, dual luciferase assays, and proteasome inhibitor treatments, to address both transcriptional and post-translational regulation. The identification of a specific miRNA-target module in a woody plant species under pathogen stress is a useful contribution. The potential link between host protein stability and pathogen effector targeting is conceptually interesting.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that PfmiR156 cleaves PfSPL1 and PfSPL10 at specific nucleotide positions (1104 nt and 1177 nt, respectively), based on RLM-5'RACE and dual luciferase analyses.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract does not report the magnitude of cleavage, the number of biological replicates, the efficiency of cleavage in the dual luciferase assay, or whether the identified cleavage sites were validated by sequencing of the 5' RACE products. Without these details, it is not possible to assess whether the cleavage events are biologically meaningful or merely minor products.
  - **Why it matters** The entire regulatory module hinges on the functional relevance of PfmiR156-mediated cleavage. If cleavage efficiency is low or the sites are not reproducible, the proposed module may not be physiologically significant.
  - **Resolution test** Provide quantitative cleavage data, including the proportion of transcripts cleaved at each site, replicate numbers, and statistical comparison with a non-cleavable mutant control in the dual luciferase assay.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that MG132 and epoxomicin significantly increased PfSPL1 accumulation, implying 26S proteasome-mediated degradation of PfSPL1.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract does not specify the experimental system (e.g., heterologous expression, endogenous protein, or tagged construct), the concentration and duration of inhibitor treatment, the method of protein quantification, or whether the increase was specific to PfSPL1 rather than a general effect on cellular proteins. No data on protein half-life or ubiquitination are provided.
  - **Why it matters** Proteasome inhibitor treatments can have broad effects on cellular physiology. Without evidence of specificity and dose-response, the conclusion that PfSPL1 is a direct substrate of the 26S proteasome is not established.
  - **Resolution test** Provide immunoblot data with loading controls, quantification from at least three independent experiments, a time-course of inhibitor treatment, and ideally a ubiquitination assay or a mutant lacking the degradation signal.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Claim support
  - **Claim pointer** The authors claim that PfSPL1 is an attack target of phytoplasma effectors (Pawb 3/9/16/37/51) and that molecular docking implies interaction with the conserved SBP domain.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract states that PfSPL1 is a target of five effectors, but no experimental validation is described. Molecular docking alone is a predictive tool and cannot establish physical interaction. No co-immunoprecipitation, yeast two-hybrid, pull-down, or in planta interaction data are mentioned. The phrase "attack target" implies functional relevance that is not supported by the described evidence.
  - **Why it matters** The claim that effectors target PfSPL1 is a central and novel aspect of the study. If this is based solely on docking, it is speculative and could mislead readers about the strength of the evidence.
  - **Resolution test** Provide experimental interaction data for at least one effector with PfSPL1, such as co-immunoprecipitation or yeast two-hybrid, and ideally a functional assay showing that effector expression alters PfSPL1 stability or activity in planta.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The authors conclude that PfSPL1 stability is regulated by PfmiR156 cleavage and/or the 26S proteasome pathway, and that this provides a good scope to understand phytoplasma infection mechanisms.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract does not establish a causal link between PfSPL1 stability and phytoplasma disease symptoms or plant susceptibility. No phenotypic data, such as plant growth, symptom severity, or pathogen titer, are presented in relation to PfSPL1 levels or mutations.
  - **Why it matters** Without a functional connection to disease outcome, the biological relevance of the described regulatory module remains unclear. The abstract claims significance for understanding infection mechanisms but does not demonstrate it.
  - **Resolution test** Include data showing that modulation of PfSPL1 expression or stability affects phytoplasma accumulation or symptom development, or at minimum, that PfSPL1 target genes are differentially expressed upon infection.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Abstract structure
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract moves abruptly from sequencing-based identification to inhibitor treatments to effector docking without clear logical transitions. The relationship between the miRNA module and the effector targeting is not explicitly connected.
  - **Required correction** Rewrite the abstract to clearly separate the identification of the regulatory module, the validation of cleavage, the proteasome experiments, and the effector interaction predictions, and state how these pieces fit together.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Terminology
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The phrase "post-translation level" is imprecise. Proteasome-mediated degradation is a post-translational process, but the abstract also describes miRNA-mediated cleavage, which occurs at the RNA level. The sentence conflates these distinct regulatory layers.
  - **Required correction** Use precise terminology, such as "post-transcriptional regulation by miR156" and "post-translational regulation by the 26S proteasome," and describe them as separate mechanisms.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Abstract wording
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The final sentence "This study provides a good scope to understand the paulownia phytoplasma infecting mechanism" is vague and does not specify what new insight was gained.
  - **Required correction** Replace with a specific statement of the proposed mechanism, such as how miR156-mediated regulation and effector targeting of PfSPL1 might modulate host responses to phytoplasma.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The cleavage validation, proteasome-mediated degradation evidence, and effector interaction claims all require additional experimental data beyond what is summarized in the abstract.
- **Assessment against Nature-style criteria**  
  *Originality*: The combination of ceRNA network analysis with effector targeting of a transcription factor in phytoplasma-infected woody plants is somewhat novel, but the individual components (miRNA regulation, proteasome degradation, effector-host interactions) are well-established concepts.  
  *Scientific importance*: The potential to understand phytoplasma effector strategies is relevant, but the abstract does not demonstrate a clear advance in mechanistic understanding or disease relevance.  
  *Interdisciplinary readership*: The work may appeal to plant pathologists, molecular biologists, and possibly computational biologists, but the narrow focus on a single transcription factor in one plant species limits broader appeal.  
  *Technical soundness*: The described methods are appropriate in principle, but the abstract lacks the quantitative and control data needed to assess rigor.  
  *Readability for nonspecialists*: The abstract is accessible but uses jargon without sufficient context, and the logical flow could be improved.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an interesting hypothesis but does not provide sufficient experimental detail to support the central claims. If the full manuscript contains rigorous validation of cleavage efficiency, proteasome specificity, and effector interactions with functional relevance, the work could be considered for publication in a specialized journal. However, based on the abstract alone, the case is not made.

## Risk / unsupported claims
- The claim that PfSPL1 is an "attack target" of five phytoplasma effectors is unsupported by experimental evidence in the abstract; molecular docking is predictive only.
- The claim that PfSPL1 stability is regulated by the 26S proteasome pathway is weakly supported without specificity controls or protein half-life data.
- The functional significance of the PfmiR156f-PfSPL module in phytoplasma disease progression is not established; no phenotypic or pathogen load data are presented.
- The statement that the study "provides a good scope to understand" the infection mechanism is an overreach given the lack of causal evidence.