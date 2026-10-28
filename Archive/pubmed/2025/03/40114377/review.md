## Review setup
- **Input scope** Full manuscript text including abstract, introduction, materials and methods, results, discussion, and supplementary material references.
- **Assessment boundary** Scientific content, methodological rigor, validity of claims relative to presented evidence, and technical soundness. Not assessed: language editing, formatting, or journal fit.
- **Shared manuscript claim summary** The authors present a multiscale modeling pipeline that integrates Micro-C contact frequencies, chemical mapping/ChIP-seq protein localization data, and microscopy-derived spatial constraints to build near-atomistic models of the 200 kb Nanog gene locus in mouse embryonic stem cells. They claim the models reveal sequence-guided chromatin organization at cis-regulatory elements, mutually exclusive localization of linker histones and transcription machinery, and a "nucleosomal handshake" mechanism for enhancer-promoter communication.
- **Visible evidence base** Full text of manuscript, including methods descriptions, results narrative, figure references, and supplementary figure/table references. No actual figures, tables, or supplementary files were provided for direct inspection.
- **Missing materials affecting confidence** All figures, tables, and supplementary materials referenced in the text were not available for review. This includes Figure 1-7, Supplementary Figures S1-S18, Supplementary Tables S1-S3, and Supplementary Videos S1-S5. Quantitative validation metrics (e.g., correlation coefficients, error bars, statistical test outputs) could not be independently verified.

## Reviewer
- **Overall assessment** This manuscript describes an ambitious and technically sophisticated multiscale modeling pipeline that integrates diverse experimental datasets to generate near-atomistic models of a 200 kb gene locus. The methodological approach is novel in its combination of Hi-C metainference, nucleosome positioning data, and protein localization data into a single coherent modeling framework. The resulting models offer potentially valuable insights into chromatin organization at cis-regulatory elements. However, the manuscript as presented has several significant weaknesses. The central claims regarding sequence-guided chromatin accessibility and the "nucleosomal handshake" mechanism are presented with limited quantitative support. The validation of the models against experimental data is described qualitatively rather than demonstrated with rigorous metrics. The relationship between the near-atomistic models and the biological conclusions drawn from them requires clearer articulation. The discussion of limitations is honest but reveals substantial simplifications that may affect the biological relevance of the findings. The manuscript would benefit from more rigorous quantitative analysis and clearer presentation of validation evidence.
- **Who would be interested in the results, and why** Computational biologists and biophysicists studying chromatin organization and genome architecture would be the primary audience. Researchers working on enhancer-promoter communication, transcription regulation, and 3D genome organization would find the methodological framework and the proposed "nucleosomal handshake" concept of interest. The multiscale modeling approach may also appeal to researchers developing integrative modeling methods for large biomolecular systems. Experimentalists studying gene regulation at the Nanog locus or similar pluripotency genes might find the models useful as a framework for generating hypotheses, though the models' predictive power remains to be demonstrated.
- **Major strengths** 1) The methodological ambition is commendable; integrating multiple experimental data types into a near-atomistic model of a 200 kb locus represents a significant technical achievement. 2) The use of Hi-C metainference to capture ensemble heterogeneity is methodologically sound and addresses a known limitation of single-structure approaches. 3) The backmapping pipeline with knot-checking and iterative refinement is technically rigorous. 4) The models are made available through a public repository, supporting reproducibility. 5) The authors acknowledge limitations honestly and position the work appropriately as a first step toward more comprehensive models.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** **Originality**: The multiscale integration approach is novel, though individual components (Hi-C metainference, nucleosome positioning modeling, protein-DNA docking) are established methods. The "nucleosomal handshake" concept is a new contribution to the field. **Scientific importance**: The question of how genome organization relates to transcription regulation is of fundamental importance. However, the current manuscript provides a descriptive model rather than a mechanistic understanding, limiting its immediate impact. **Interdisciplinary readership**: The work bridges computational biology, biophysics, and gene regulation, which could attract readers from multiple fields. However, the technical complexity may limit accessibility. **Technical soundness**: The methods are generally sound, but validation is insufficiently rigorous. Key claims lack quantitative support. The short equilibration time and simplified protein models raise questions about the biological relevance of the specific molecular arrangements observed. **Readability for nonspecialists**: The manuscript is clearly written but assumes substantial background knowledge in chromatin biology and computational modeling. The abstract effectively communicates the scope and significance of the work.
- **Recommendation posture** Supportive if technical concerns are resolved. The methodological framework is valuable and the models represent a significant technical achievement. However, the current manuscript does not adequately support several central claims, particularly regarding the "nucleosomal handshake" mechanism and the sequence-guided accessibility model. Substantial revision with more rigorous quantitative validation and clearer articulation of what can and cannot be concluded from the models is required.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The authors claim that "the sequence-regulated chromatin accessibility facilitates the recruitment of transcription regulatory proteins exclusively at CREs, guided by the contrasting nucleosome organization compared to other regions."
- **Evidence pointer** Results section "Mapping nucleosome-associated protein factors", Figures 4 and 5, location not provided
- **Concern** The claim of sequence-regulated chromatin accessibility is based on correlations between nucleosome positioning features, H1 binding, and TF localization. However, the manuscript does not provide a quantitative demonstration that the observed nucleosome organization at CREs is specifically sequence-driven rather than a consequence of other factors (e.g., active transcription, chromatin remodeling, or boundary elements). The comparison between CRE and non-CRE regions is described qualitatively, and no statistical analysis is presented to support the claim of "contrasting nucleosome organization."
- **Why it matters** This claim is central to the manuscript's proposed mechanism linking genome sequence to chromatin structure to transcription regulation. Without quantitative evidence that the nucleosome organization differences are statistically significant and specifically sequence-driven, the mechanistic conclusion is not established.
- **Resolution test** Provide quantitative comparison of nucleosome organization features (positioning strength, linker length distribution, H1 occupancy) between CRE and non-CRE regions, with appropriate statistical tests. Demonstrate that the observed patterns are specifically associated with sequence features (e.g., poly(dA:dT) tracts, TF binding motifs) rather than confounding factors.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validation
- **Claim pointer** The authors claim that their models are "experimentally consistent" and that the near-atomistic models reveal "a robust framework for future studies on nuclear compartmentalization, chromatin organization, and transcription regulation."
- **Evidence pointer** Results sections "3D modeling of the Nanog gene locus" and "Chromatin organization at the near-atomistic resolution", Figures 2 and 6, location not provided
- **Concern** The validation of the models against experimental data is described qualitatively. The manuscript states that the replica-averaged pairwise interaction frequencies match Micro-C data with a Pearson correlation coefficient of r=0.90, but no error analysis, comparison to null models, or assessment of whether this level of agreement is sufficient is provided. The comparison of the near-atomistic models to experimental imaging data (e.g., distances between loci, sizes of transcriptional condensates) is described in general terms without quantitative metrics. The manuscript does not demonstrate that the models reproduce experimental observations better than alternative models or that the specific structural features highlighted in the analysis are robust to modeling choices.
- **Why it matters** The value of the models depends on their ability to faithfully represent the biological system. Without rigorous validation demonstrating that the models capture experimentally observed features with quantitative accuracy, the biological conclusions drawn from the models are not reliable.
- **Resolution test** Provide quantitative validation metrics for each experimental dataset used, including: (1) agreement between model-predicted and experimental contact frequencies with appropriate error analysis; (2) comparison of model-predicted distances between specific genomic loci with imaging data; (3) sensitivity analysis showing that key conclusions are robust to modeling parameters and choices.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic claim
- **Claim pointer** The authors propose a "nucleosomal handshake" mechanism whereby "expanded chromatin segments favor nonlocal interactions preferably with other expanded segments" forming "a roadmap for communication between CREs."
- **Evidence pointer** Results section "Chromatin organization at the near-atomistic resolution", Figure 7, location not provided
- **Concern** The "nucleosomal handshake" is presented as a novel mechanistic insight, but the evidence supporting it is limited. The analysis shows that expanded chromatin segments have a larger radius of gyration and form more nonlocal interactions, but this is almost tautological: larger, more expanded segments will have a larger capture radius for interactions. The manuscript does not demonstrate that these nonlocal interactions are specifically between CREs, that they are functionally relevant for enhancer-promoter communication, or that they represent a distinct mechanism beyond what would be expected from polymer physics. The claim that this forms a "roadmap" for communication is speculative and not supported by direct evidence of functional communication.
- **Why it matters** The "nucleosomal handshake" is presented as a key finding of the manuscript. If the claim is not well-supported, the manuscript's contribution is reduced to a descriptive model rather than a mechanistic insight.
- **Resolution test** Provide evidence that the nonlocal interactions between expanded segments are specifically enriched between CREs compared to what would be expected by chance. Demonstrate that the proposed mechanism has functional implications, for example by showing that perturbations that disrupt these interactions affect transcription or enhancer-promoter communication. Alternatively, temper the claim to be explicitly hypothesis-generating rather than a demonstrated mechanism.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validity
- **Claim pointer** The authors state that "the models are equilibrated by high-performance molecular dynamics simulations" and that the final structures are representative of the biological system.
- **Evidence pointer** Materials and methods section "Backmapping mesoscopic to near-atomistic model", Results section "Backmapping mesoscopic to near-atomistic resolution", location not provided
- **Concern** The equilibration protocol consists of only 100 ns of simulation time for a system of approximately 2.5 million CG particles. For a system of this size, 100 ns is likely insufficient to achieve equilibrium, particularly for chromatin fibers that are known to have slow relaxation times. The manuscript does not demonstrate that the system has reached equilibrium (e.g., through convergence analysis, monitoring of key observables over time). The authors acknowledge that "the lack of large-scale dynamics will make the discussion mostly speculative," but this limitation is not adequately reflected in the strength of the claims made elsewhere in the manuscript.
- **Why it matters** If the models are not properly equilibrated, the specific structural features and interactions described in the results may be artifacts of the initial conditions or the equilibration protocol rather than representative of the biological system.
- **Resolution test** Provide evidence of equilibration, such as convergence of key observables (radius of gyration, contact maps, energy) over the simulation time. If 100 ns is insufficient, extend the simulations or use enhanced sampling methods. Alternatively, clearly state the limitations of the equilibration and temper claims accordingly.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors state that "the generated model is a first step towards understanding the functional role of chromatin organization in facilitating E-P communication" and that the pipeline is "easily transferable to model other genomic segments."
- **Evidence pointer** Data availability section, Materials and methods section, location not provided
- **Concern** While the authors state that code and models are available in a Zenodo repository, the manuscript does not provide sufficient detail for others to reproduce the pipeline. Key parameters for the Hi-C metainference simulations, the Monte Carlo nucleosome positioning, and the backmapping protocol are not fully specified in the main text or referenced supplementary materials. The manuscript does not describe how to handle cases where experimental data is incomplete or inconsistent, which would be essential for transferability to other genomic loci.
- **Why it matters** Reproducibility is a core requirement for scientific claims. Without sufficient methodological detail, other researchers cannot build on this work or verify the findings.
- **Resolution test** Provide a complete description of all parameters and protocols, either in the main text or supplementary materials. Include example input files and outputs. Describe potential failure modes and how to troubleshoot them.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that the models "offer novel insights into chromatin organization and its role in enhancer-promoter communication" but does not specify what these insights are. The abstract would be strengthened by stating one or two specific findings.
- **Required correction** Add one or two specific findings to the abstract, such as the mutually exclusive localization of H1 and transcription machinery, or the proposed "nucleosomal handshake" mechanism.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results section "3D modeling of the Nanog gene locus"
- **Evidence pointer** Figure 2, location not provided
- **Issue** The manuscript reports a Pearson correlation coefficient of r=0.90 between replica-averaged and experimental contact frequencies but does not report confidence intervals or a comparison to a null model. A correlation of 0.90 could be misleading if the range of contact frequencies is narrow or if the model systematically over- or under-predicts certain types of contacts.
- **Required correction** Report confidence intervals for the correlation coefficient and compare the model's performance to a null model (e.g., a polymer model without experimental data constraints).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results section "Mapping nucleosome-associated protein factors"
- **Evidence pointer** Figure 4, location not provided
- **Issue** The authors interpret the exponential decay of BRD4 and H3K9Ac ChIP-seq signal with increasing H1/nucleosome ratio as evidence for mutual exclusivity of H1 and BRD4 binding. However, this correlation could also be explained by other factors, such as differences in chromatin accessibility or nucleosome turnover rates.
- **Required correction** Acknowledge alternative interpretations and, if possible, provide additional evidence supporting the mutual exclusivity interpretation, such as direct competition assays or analysis of nucleosomes with both H1 and acetylation marks.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section, location not provided
- **Issue** The discussion of the "nucleosomal handshake" mechanism would benefit from a more thorough comparison with existing models of enhancer-promoter communication, such as the loop extrusion model or the phase separation model. The authors mention these models only briefly.
- **Required correction** Expand the discussion to explicitly compare the proposed mechanism with existing models and discuss how the "nucleosomal handshake" relates to or differs from them.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Title and throughout
- **Evidence pointer** Title, location not provided
- **Issue** The term "in silico nanoscope" is evocative but may be misleading. A nanoscope implies the ability to observe at nanometer resolution, while the models presented are computational predictions that have not been directly validated at that resolution. The term may overstate the capabilities of the approach.
- **Required correction** Consider using a more precise term such as "computational model" or "integrative modeling approach" in the title, or provide a clear definition of what is meant by "in silico nanoscope" in the introduction.

## Risk / unsupported claims
- The claim that "sequence-regulated chromatin accessibility facilitates the recruitment of transcription regulatory proteins exclusively at CREs" is not quantitatively supported. The manuscript does not demonstrate that the observed accessibility patterns are specifically sequence-driven or that recruitment is exclusive to CREs.
- The "nucleosomal handshake" mechanism is presented as a finding but is more accurately described as a hypothesis. The evidence shows that expanded segments form more nonlocal interactions, but does not demonstrate that this constitutes a specific mechanism for enhancer-promoter communication.
- The claim that the models are "experimentally consistent" is not rigorously demonstrated. While the correlation with Micro-C data is reported, other experimental comparisons are described qualitatively.
- The statement that the models "span a scale of ~350 nm" and provide "a realistic molecular-level picture of chromatin organization" is not fully supported given the simplified protein models and short equilibration time.
- The claim that the pipeline is "easily transferable to model other genomic segments" is not demonstrated. The manuscript does not discuss potential challenges in applying the pipeline to loci with different characteristics or less complete experimental data.