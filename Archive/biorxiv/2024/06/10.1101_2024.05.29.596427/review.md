## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods) from bioRxiv preprint
- **Assessment boundary** Scientific content, methodological soundness, claims versus evidence, and presentation quality as presented in the supplied material
- **Shared manuscript claim summary** The authors use atomistic MD simulations (over 100 microseconds total) and enhanced sampling to characterize the full-length FXR-RXR heterodimer bound to DNA. They report that the complex is conformationally dynamic, that the FXR hinge is more flexible than the RXR hinge, that the FXR hinge mediates interdomain communication without direct LBD-DBD contact, and that a positively charged "KR patch" in the FXR hinge interacts with DNA in a ligand-dependent manner. Cell-based luciferase assays with KR patch mutants show no significant effect on transactivation.
- **Visible evidence base** Abstract, Introduction, Results sections (three subsections), Discussion, Materials and Methods, figure legends referenced (Figs 1-5, S1-S5), acknowledgment and footnotes
- **Missing materials affecting confidence** Figures and supplementary figures themselves are not provided; specific numerical data (RMSD values, path counts, statistical outputs) are only partially reported; no coordinates or trajectory data; no detailed parameters for aMD simulations; no information on convergence checks beyond RMSD

## Reviewer

### Overall assessment
This manuscript presents a computational study of the full-length FXR-RXR heterodimer bound to DNA, addressing a genuinely important gap in nuclear receptor structural biology. The use of long-timescale MD simulations on Anton 2 is appropriate and ambitious. The central claims regarding conformational dynamics, hinge flexibility differences, and the absence of direct FXR LBD-DBD contacts in the dimer context are reasonably supported by the described analyses. However, several concerns limit the strength of the conclusions. The claim that the hinge mediates interdomain communication relies on suboptimal path analysis, which is a correlative and method-dependent inference. The functional relevance of the KR patch is tested experimentally, but the negative result is interpreted in a way that leaves the physiological significance unclear. The manuscript would benefit from clearer presentation of quantitative results, additional validation of the simulation models, and a more cautious framing of the communication claim.

### Who would be interested in the results, and why
Structural biologists and biophysicists studying nuclear receptor architecture and dynamics, computational biologists interested in full-length multidomain protein simulations, and researchers in the nuclear receptor signaling field who seek mechanistic understanding of how DNA binding, ligand binding, and domain organization coordinate transcriptional regulation. The work also has relevance for drug discovery efforts targeting FXR, as understanding the dynamic architecture of the heterodimer could inform pharmacological modulation.

### Major strengths
1. Addresses a significant gap: full-length nuclear receptor heterodimer architecture is poorly characterized experimentally, and this study provides a computational framework for studying it.
2. Uses state-of-the-art methodology: long-timescale Anton 2 simulations (10-15 microseconds per trajectory) are appropriate for capturing large-scale conformational dynamics.
3. Systematic variation of conditions: eight complexes varying ligand identity, DNA sequence, and ligand occupancy allow comparative analysis.
4. Integration of computational predictions with experimental validation: the KR patch mutagenesis and luciferase assays represent a good-faith effort to test a computational prediction.
5. Honest reporting of negative results: the absence of FXR LBD-DBD contacts in the dimer context is clearly stated, contrasting with the monomeric case.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "The FXR hinge is predicted as the mediator of interdomain communication, with 1583 and 197 paths traveling from LBD to DBD in OCA-IR1 and CDCA-PLTP complexes, respectively."
- **Evidence pointer** Results section "The FXR hinge facilitates communication between FXR LBD and DBD"; Methods "Network analysis and suboptimal paths were performed as previously described"
- **Concern** The suboptimal path analysis is presented as evidence for interdomain communication mediated by the hinge, but the methodology is described only by reference to a previous publication. The choice of source and sink residues (K148 in DBD, M332 in LBD) is not justified. The path counts (1583 vs 197) differ substantially between complexes, but no statistical framework is provided to determine whether these differences are meaningful. More fundamentally, suboptimal path analysis identifies correlated motions in the simulation, which does not necessarily demonstrate causal communication or allostery. The claim that the hinge "mediates" communication is an interpretation that goes beyond what this analysis can establish.
- **Why it matters** The communication claim is a central finding of the paper, stated in the abstract and discussion. If the evidence is only correlative and method-dependent, the conclusion is overstated. Readers may take this as established allosteric mechanism when it is a computational inference with unvalidated assumptions.
- **Resolution test** Provide a more detailed description of the network analysis methodology, including how nodes and edges were defined, how path significance was assessed, and whether results are robust to parameter choices. Ideally, validate the communication prediction with a perturbation experiment (e.g., mutating predicted key hinge residues and testing effects on LBD-DBD coupling in simulations or in vitro).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Model validation
- **Claim pointer** "To assess the stability of the models, we performed RMSD calculations (Fig. S1). Within the first microsecond, all complexes achieve a stable RMSD that persists until the end of the simulation. However, RMSD values reach anywhere between 2 and 20 Å before stabilizing."
- **Evidence pointer** Results section "The FXR-RXR dimer is conformationally dynamic"; Figure S1
- **Concern** The RMSD values reaching 20 Å before stabilization are very large for a protein-DNA complex of this size and raise questions about the quality of the initial models. The authors state that the complexes "shift out of their initial conformation to adopt a range of stable states," but this could also indicate that the initial models were poorly constructed or that the simulations are sampling non-physiological states. The comparison to crystal structures (Fig. 2A-E) shows good superposition for DBD and LBD dimers, but the hinge regions are not assessed in this manner. Without a clear demonstration that the final states are physically reasonable (e.g., via comparison to experimental SAXS or FRET data, or at least a detailed analysis of specific interactions), the reader cannot fully trust the conformational ensemble.
- **Why it matters** The entire study rests on the validity of the simulation models. If the initial models are flawed or the simulations drift into unrealistic states, all downstream analyses (hinge flexibility, communication paths, KR patch interactions) are compromised.
- **Resolution test** Provide per-residue RMSF analysis to show which regions contribute to the large RMSD. Show that the final conformations maintain known structural features (e.g., DBD-DNA contacts, LBD dimer interface) throughout the trajectory. If possible, compare simulated ensembles to available experimental data (e.g., small-angle X-ray scattering, Förster resonance energy transfer) for full-length nuclear receptor dimers.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Functional interpretation
- **Claim pointer** "To determine whether there is physiological relevance of the KR patch, we created two mutants: KR-Ala and KR-Swap, and tested their activity in luciferase reporter assays (Fig. 4E). The assay was performed with two distinct FXR response elements, neither of which showed a significant reduction in the fold change compared to wild-type FXR."
- **Evidence pointer** Results section "Ligands drive conformational dynamics and function of the FXR hinge"; Figure 4E-G
- **Concern** The experimental result is negative: mutating the KR patch does not affect transcriptional activity. The authors interpret this as "support[ing] the notion that the non-specific interactions observed between the KR patch and DNA are not crucial for transcriptional activity." However, this interpretation is problematic. The KR patch is predicted to interact with DNA in the simulations, but the functional assay measures a downstream outcome (transcription) that could be insensitive to changes in DNA binding affinity or dynamics. The KR patch could affect other aspects of FXR function (e.g., nuclear localization, chromatin association, interaction with co-regulators) that are not captured by the luciferase assay. The authors acknowledge this possibility but do not test it. The negative result therefore neither confirms nor refutes the functional relevance of the KR patch.
- **Why it matters** The paper claims to provide "cell-based experiments to test predictions from computational data" (footnote), but the experiment as designed cannot distinguish between the KR patch being functionally irrelevant versus the assay being insensitive to its role. This weakens the overall impact of the study.
- **Resolution test** Perform additional experiments to probe KR patch function, such as electrophoretic mobility shift assays to test DNA binding affinity of the mutants, or chromatin immunoprecipitation to assess DNA occupancy in cells. Alternatively, test the KR patch mutants in a different functional readout (e.g., target gene expression by qPCR) or in a different cell line.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** "Triplicate 500-ns trajectories for each complex were combined and contacts were analyzed (Fig. 3B)."
- **Evidence pointer** Results section "The FXR hinge facilitates communication between FXR LBD and DBD"; Methods "Molecular dynamics simulations"
- **Concern** The manuscript reports triplicate trajectories for several analyses, which is commendable, but the statistical treatment of these replicates is not described. For the suboptimal path analysis, path counts are reported as single numbers (1583 and 197) without error estimates or tests of significance. For the contact analysis (Fig. 3B), it is unclear whether the triplicates were pooled or averaged, and whether variability between replicates was assessed. The luciferase assays are described as having three biological replicates with four technical replicates each, and a one-way ANOVA was used, but the results are only shown as fold change without error bars or significance indicators in the text description.
- **Why it matters** Without proper statistical treatment, the reader cannot assess the reliability of the quantitative claims. This is particularly important for the path count differences between complexes, which are used to support ligand-specific effects.
- **Resolution test** Report mean and standard deviation or standard error for path counts and contact frequencies across replicates. Provide statistical tests for differences between conditions. Include error bars and significance markers in all figures showing quantitative data.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1
- **Evidence pointer** Results section "The FXR-RXR dimer is conformationally dynamic"
- **Issue** The description of the initial model construction is brief. The authors state that Modeller was used to generate hinge regions, but do not describe how the DBD and LBD dimers were positioned relative to each other and to the DNA. The comparison to EcR-USP (PDB 4UMM) is mentioned but not shown in detail.
- **Required correction** Provide a more detailed description of the modeling procedure, including how the DBD-DNA and LBD-LBD coordinates were combined, what constraints were applied, and how the initial DBD-LBD separation was determined. Consider showing a superposition of the initial model with the EcR-USP structure.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section
- **Evidence pointer** Materials and Methods "Molecular dynamics simulations"
- **Issue** The methods for accelerated MD are described only by reference to previous work. The specific parameters (boost potential settings, frequency of boost application, etc.) are not provided.
- **Required correction** Include the key parameters for aMD simulations in the methods, or provide them in the supplementary information.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion states that "simulation-based methods retain a powerful advantage by circumventing the challenges of sample preparation and handling," but this is somewhat overstated. Simulations have their own limitations (force field accuracy, sampling limitations, system size), which are not discussed.
- **Required correction** Add a paragraph acknowledging the limitations of the computational approach and how they might affect the conclusions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 4
- **Evidence pointer** Results section "Ligands drive conformational dynamics and function of the FXR hinge"
- **Issue** The description of the luciferase assay results is incomplete. The authors state that "neither of which showed a significant reduction in the fold change compared to wild-type FXR," but do not report the actual fold change values or the statistical test results.
- **Required correction** Report the mean fold change values with error bars for each condition, and indicate the statistical significance (or lack thereof) in the figure and text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section
- **Evidence pointer** Materials and Methods "Model development"
- **Issue** The UniProt identifiers and residue numbering are provided, which is good, but the specific PDB structures used for the DBD and LBD templates are not all clearly identified. PDB 1R0N and 6A60 are mentioned, but the source of the RXR DBD structure is not specified.
- **Required correction** Clearly list all PDB structures used as templates, including the specific chains and residue ranges used for each domain.

### Technical failings that need to be addressed before the case is established
1. The suboptimal path analysis methodology is insufficiently described and the interpretation of path counts as evidence for communication is not adequately justified (R1-M1).
2. The large RMSD values (up to 20 Å) before stabilization raise concerns about model quality that are not fully addressed (R1-M2).
3. The negative result of the KR patch mutagenesis experiments does not provide clear support for or against the computational predictions (R1-M3).
4. Statistical treatment of replicate simulations is not described, limiting confidence in quantitative claims (R1-M4).

### Assessment against Nature-style criteria
- **Originality**: The work is original in its application of long-timescale MD simulations to a full-length nuclear receptor heterodimer bound to DNA. While previous studies have examined individual domains or used shorter simulations, the systematic approach here is novel.
- **Scientific importance**: Understanding full-length nuclear receptor architecture is important for the field, and this study provides a framework that could be applied to other receptors. However, the lack of experimental validation for the central communication claim limits the immediate impact.
- **Interdisciplinary readership**: The work bridges structural biology, computational biophysics, and nuclear receptor signaling. The writing is generally accessible, though some computational details may be challenging for experimental readers.
- **Technical soundness**: The simulation methodology is appropriate and state-of-the-art, but the analysis methods (particularly suboptimal paths) need more rigorous treatment. The experimental component is well-designed but the negative result is not fully informative.
- **Readability for nonspecialists**: The manuscript is clearly written and the main findings are presented in an accessible manner. However, the significance of the KR patch finding is not clearly contextualized for readers outside the nuclear receptor field.

### Recommendation posture
Supportive if technical concerns are resolved. The manuscript addresses an important question with appropriate methodology, and the core observations regarding conformational dynamics and hinge flexibility are likely robust. However, the communication claim needs stronger support, the model validation needs to be more thorough, and the statistical treatment needs improvement. The negative experimental result should be either supplemented with additional experiments or interpreted more cautiously. With these revisions, the work could make a valuable contribution to the field.

## Risk / unsupported claims
1. The claim that the FXR hinge "mediates" interdomain communication is not fully supported by the suboptimal path analysis, which is correlative and method-dependent.
2. The statement that "the hinge is also predicted to mediate DNA interactions via the KR patch" is supported by simulation data, but the functional relevance is not established by the experimental results.
3. The claim that "all structures conserve the dimerization interface between LBDs and DBD-DNA contacts reported in crystal structures" is based on visual comparison (Fig. 2A-E) but quantitative measures of interface preservation are not provided.
4. The assertion that "the FXR hinge displays much higher flexibility than the RXR hinge" is stated without quantitative flexibility measures (e.g., RMSF values) in the text.
5. The statement that "these studies provide a much-needed framework that will enable the field to obtain a complete understanding of nuclear receptor quaternary architectures" is an overstatement given the limitations acknowledged in the discussion.