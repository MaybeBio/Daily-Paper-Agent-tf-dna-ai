## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors define the binding architecture of HP1043, an essential orphan response regulator of Helicobacter pylori, to a target promoter (Php1227). Through scanning mutagenesis of both the DNA consensus sequence and the protein DNA-binding domain, combined with data-driven protein-DNA docking, they propose a head-to-head binding conformation distinct from the canonical head-to-tail mode of other OmpR/PhoB family members. They further validate the model through site-directed mutagenesis, binding assays, and molecular dynamics simulations, and demonstrate that HP1043 acts as a transcriptional activator on this promoter.
- **Visible evidence base** Abstract, full text including Introduction, Results (Sections 2.1-2.5), Discussion, Materials and Methods (Sections 4.1-4.10), figure legends referenced in text
- **Missing materials affecting confidence** Figures 1-6 and Supplementary Figures S1-S3, Tables S1-S3, and raw experimental data (footprinting gels, EMSA images, MD trajectories) were not provided. Statistical details and replicate numbers for quantitative assays are not fully described.

## Reviewer

- **Overall assessment** This manuscript presents a comprehensive and methodologically rigorous investigation into the DNA-binding architecture of HP1043, an essential regulator in H. pylori. The combination of experimental mutagenesis, biochemical binding assays, and computational modeling is well conceived and largely well executed. The central claim of a head-to-head binding conformation, distinct from the canonical head-to-tail mode of related response regulators, is interesting and potentially significant. However, the strength of this conclusion rests heavily on the computational docking model, and the experimental validation, while supportive, does not fully resolve the architecture at high resolution. The transcriptional activation data are convincing but limited to a single promoter. Overall, the work is solid and of interest to the bacterial gene regulation community, but the novelty of the architectural claim and the depth of validation warrant careful scrutiny.

- **Who would be interested in the results, and why** Researchers studying bacterial two-component signal transduction systems, particularly the OmpR/PhoB family of response regulators, will find the proposed non-canonical binding mode of interest. The Helicobacter pylori research community will value the functional characterization of this essential regulator and its role in transcriptional activation. Additionally, those interested in computational approaches to protein-DNA docking and the integration of experimental restraints with modeling will find the methodology relevant. The potential translational angle regarding HP1043 as a drug target for novel antimicrobial strategies may attract interest from applied microbiology groups.

- **Major strengths** 1) The study combines multiple complementary approaches (DNase I footprinting, EMSA, in vitro transcription, computational docking, MD simulations) to address the binding mechanism, providing a multi-layered evidence base. 2) The identification of specific residues in both the DNA and protein that are critical for binding is systematic and well controlled. 3) The use of experimental data as restraints for docking is a sound approach that increases confidence in the resulting model. 4) The demonstration of transcriptional activation by HP1043 on Php1227 connects the binding studies to functional output. 5) The discussion of the asymmetry in hemi-site recognition and its structural rationale is thoughtful and adds depth to the interpretation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for central architectural claim
- **Claim pointer** The manuscript claims that HP1043 binds to the Php1227 promoter in a head-to-head conformation, differing from the canonical head-to-tail mode of other OmpR/PhoB family regulators.
- **Evidence pointer** Section 2.3, Section 2.4, Figure 3
- **Concern** The head-to-head binding model is derived from a computational docking procedure (HADDOCK) guided by experimental restraints. While the docking approach is reasonable, the final model is a prediction, not a direct experimental determination. The validation experiments (site-directed mutagenesis of K194, R210, Q190, R209) provide indirect support by showing that some predicted interface residues affect binding, but they do not definitively establish the overall architecture. The authors do not present high-resolution structural data (e.g., co-crystal structure, NMR structure of the complex, or cross-linking experiments) that would directly confirm the head-to-head arrangement. The claim of a novel binding mode, which is a central conclusion of the paper, therefore rests on a computational model with limited direct experimental verification.
- **Why it matters** The head-to-head conformation is presented as a significant departure from the established paradigm for OmpR/PhoB family members. If this claim is not robustly supported, the novelty and impact of the study are substantially diminished. The distinction between head-to-head and head-to-tail binding has implications for understanding DNA recognition mechanisms, cooperativity, and the evolution of binding modes within this important protein family.
- **Resolution test** The authors should provide additional experimental evidence that directly tests the head-to-head architecture. This could include: (1) Förster resonance energy transfer (FRET) experiments with labeled protein termini to measure relative orientations; (2) hydroxyl radical footprinting or other high-resolution footprinting methods that can distinguish between different binding geometries; (3) cross-linking mass spectrometry to identify inter-subunit contacts; or (4) a co-crystal or cryo-EM structure of the HP1043-DNA complex. Alternatively, the authors could temper the claim and present the head-to-head model as one plausible architecture consistent with current data, rather than a definitive conclusion.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Functional relevance and generalizability
- **Claim pointer** The manuscript claims that HP1043 acts as a transcriptional activator on the Php1227 promoter and that the identified binding determinants are relevant for target recognition.
- **Evidence pointer** Section 2.1, Section 2.5, Figure 1E-F
- **Concern** The transcriptional activation assay is performed only on a single promoter (Php1227) using an E. coli RNA polymerase system. While this is a reasonable heterologous approach, it does not fully recapitulate the native H. pylori context, where additional factors (e.g., other regulatory proteins, DNA supercoiling, chromatin structure) may influence transcriptional output. Furthermore, the manuscript does not address whether the binding determinants identified for Php1227 are conserved across other known HP1043 target promoters. The ChIP-seq data referenced from previous work identified 37 binding sites, but the current study does not examine whether the same residues and DNA elements are important across this broader set of targets.
- **Why it matters** The claim that HP1043 is a master regulator implies that it coordinately controls multiple promoters. If the binding mechanism described here is specific to Php1227 and not generalizable, the broader significance of the architectural findings is reduced. Understanding whether the head-to-head mode is a general feature of HP1043 binding across its regulon is important for assessing the physiological relevance of the model.
- **Resolution test** The authors should extend the analysis to at least one or two additional HP1043 target promoters to demonstrate that the binding determinants and the proposed architecture are general. Alternatively, they could perform a comparative analysis of the consensus sequences across all ChIP-seq-identified binding sites to show that the key nucleotides identified in this study are conserved. If such experiments are not feasible, the authors should explicitly acknowledge the limitation that the findings are based on a single promoter.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor and reproducibility of binding data
- **Claim pointer** The manuscript reports differential binding affinities of HP1043 for wild-type and mutant DNA probes, and differential binding of mutant proteins to wild-type DNA, based on DNase I footprinting and EMSA.
- **Evidence pointer** Section 2.1, Section 2.2, Section 2.4, Figures 1-3
- **Concern** The binding assays are described qualitatively (e.g., "protection appeared at higher protein concentration," "completely abolished protection") without quantitative binding constants (Kd values) or statistical analysis. The manuscript does not report replicate numbers, error bars, or statistical tests for the footprinting and EMSA data. This makes it difficult to assess the significance of observed differences between mutants and wild-type, and whether the "complete" versus "partial" loss of binding is robust and reproducible.
- **Why it matters** Quantitative binding data are essential for ranking the importance of individual residues and nucleotides. Without such data, the conclusions about which residues are "fundamental" versus "minor" contributors to binding are not well supported. The field of protein-DNA interactions increasingly expects quantitative measurements, and the lack of these weakens the manuscript's impact.
- **Resolution test** The authors should provide quantitative binding data, such as Kd values from EMSA titration experiments or fluorescence anisotropy measurements, for at least the key mutants and DNA probes. At minimum, they should report the number of independent replicates and include representative data with appropriate statistical analysis (e.g., mean ± SD, significance testing) for the footprinting and EMSA results.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of consensus sequence definition
- **Affected element** Section 2.1, Figure 1
- **Evidence pointer** Section 2.1
- **Issue** The manuscript states that the consensus sequence can be interpreted as either a direct or an inverted repeat, but the implications of this ambiguity for the binding model are not fully discussed. The authors note that the head-to-head model would explain the asymmetry in recognition, but the relationship between the repeat orientation and the proposed architecture could be made more explicit.
- **Required correction** The authors should clarify how the direct versus inverted repeat interpretation relates to the head-to-head binding model. A schematic figure showing the proposed orientation of the two HP1043 monomers relative to the DNA sequence elements would help readers understand the architectural model.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail for MD simulations
- **Affected element** Section 4.10
- **Evidence pointer** Section 4.10
- **Issue** The description of the molecular dynamics simulations is brief. The manuscript states that ten simulations of 10 ns each were performed, but does not specify the temperature coupling scheme, pressure coupling, or the criteria for equilibration. The box size is given as "about 1000-650 nm3" which appears to be a typographical error or unclear notation.
- **Required correction** The authors should provide a more complete description of the MD simulation parameters, including the ensemble (NPT or NVT), thermostat and barostat algorithms, and the total simulation time. The box size notation should be corrected to a clear volume (e.g., nm3) or dimensions (e.g., nm x nm x nm).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation of supplementary data
- **Affected element** Section 2.4, Figure S1
- **Evidence pointer** Section 2.4
- **Issue** The manuscript refers to Supplementary Figure S1 for the Methyl green competition experiment but does not describe the results in the main text. The reader is left to infer the outcome from the figure alone.
- **Required correction** The authors should briefly describe the Methyl green competition result in the main text, even if the full data are shown in the supplementary material. This will help readers follow the logic of the argument without needing to consult the supplementary information.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of alternative models
- **Affected element** Section 3
- **Evidence pointer** Section 3
- **Issue** The Discussion does not consider alternative binding architectures that could also explain the experimental data. For example, a head-to-tail binding mode with a different register or a monomeric binding mode with extended contacts could potentially produce similar footprinting patterns.
- **Required correction** The authors should acknowledge alternative models and explain why the head-to-head model is preferred over these alternatives based on the available data. This would strengthen the argument for the proposed architecture.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Consistency of residue numbering
- **Affected element** Section 2.2, Section 2.3, Figure 2
- **Evidence pointer** Section 2.2
- **Issue** The manuscript refers to residues in the DNA-binding domain using the full-length protein numbering (e.g., R192, K197, T206, R208). However, the docking was performed using only the DNA-binding domain (residues 120-223). It would be helpful to clarify whether the numbering corresponds to the full-length protein throughout.
- **Required correction** The authors should explicitly state that residue numbering corresponds to the full-length HP1043 protein, and if the DNA-binding domain construct has a different numbering, this should be clarified to avoid confusion.

## Risk / unsupported claims
1. The head-to-head binding conformation of HP1043 on Php1227 is a computational prediction that lacks direct experimental validation (e.g., high-resolution structure, FRET, cross-linking). This is the central architectural claim and should be treated as a model rather than an established fact.
2. The claim that HP1043 positively stimulates RNA polymerase activity is supported by in vitro transcription data, but the magnitude of activation and its physiological relevance in the native H. pylori context are not fully established.
3. The statement that the identified residues (R192, K197, T206, R208) could serve as "hot spots" for drug development is speculative and not directly supported by the data presented.
4. The generalizability of the binding architecture to other HP1043 target promoters is not demonstrated; the study focuses exclusively on Php1227.
5. The quantitative significance of differences in binding between wild-type and mutant proteins or DNA probes cannot be assessed from the qualitative descriptions provided; no statistical analysis or binding constants are reported.
6. The claim that the model could be used for virtual screening of specific inhibitors is forward-looking but not validated by any screening data in this manuscript.