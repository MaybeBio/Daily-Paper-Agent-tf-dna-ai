## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors report a physical interaction between transcription factor EhPC4 and polyadenylation factor EhCFIm25 in *Entamoeba histolytica*, characterized via Far-Western blotting, 500 ns molecular dynamics simulations, and protein-protein docking. They propose a structural model where EhCFIm25 acts as a molecular scaffold coupling transcription and polyadenylation, with a conserved hotspot at residues 249–255, and suggest this interface as a therapeutic target.
- **Visible evidence base** Abstract, Introduction, Materials and Methods, Results, Discussion, Conclusions; Figures 1–7 referenced but not provided
- **Missing materials affecting confidence** Figures 1–7, supplementary data, raw MD trajectories, docking scores, statistical analyses, antibody validation details, and sequence alignments

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and understudied question in parasite molecular biology, namely the physical and structural coupling between transcription and mRNA polyadenylation factors in *E. histolytica*. The combination of in vitro Far-Western assays with computational approaches is appropriate and potentially informative. However, the evidence as presented is insufficient to fully support the central claims. The Far-Western data are described but not shown, and the computational pipeline relies on a homology model of EhPC4 without experimental validation of the predicted interface. The functional implications, particularly the co-transcriptional coupling model and therapeutic targeting, are speculative and not directly tested. The manuscript would benefit from additional experimental validation, including mutagenesis of the proposed hotspot residues, co-immunoprecipitation from parasite lysates, and functional assays linking the interaction to virulence gene expression.
- **Who would be interested in the results, and why** Researchers studying gene expression regulation in protozoan parasites, particularly those focused on transcriptional and post-transcriptional mechanisms in *Entamoeba histolytica*. The work may also interest investigators examining the evolution of transcription-polyadenylation coupling across eukaryotes, and those pursuing novel drug targets for amoebiasis. The structural predictions could inform future studies on CFIm25 interactions in other organisms.
- **Major strengths** The study addresses a novel and biologically important question, namely the molecular link between transcription and polyadenylation in a medically relevant parasite. The use of multiple complementary approaches (in vitro binding, MD simulations, docking) is commendable. The identification of a specific hotspot region in EhCFIm25 provides a testable hypothesis. The authors appropriately acknowledge limitations of the computational models and suggest future directions.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
  - R1-m5
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing figure evidence), R1-M2 (unvalidated model), R1-M3 (no functional validation), R1-M4 (overstated conclusions)
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The specific interaction is novel, but the concept of transcription-polyadenylation coupling is established in other systems.
  - Scientific importance: Moderate. Relevant to parasite biology and potential drug development, but the impact is limited by lack of functional data.
  - Interdisciplinary readership: Limited. Primarily of interest to parasitologists and molecular biologists; computational aspects may attract structural biologists.
  - Technical soundness: Partially adequate. The Far-Western approach is standard, but the computational pipeline lacks experimental validation of the model and predicted interface.
  - Readability for nonspecialists: Acceptable. The manuscript is generally clear, though some computational details may be dense for non-experts.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires major revisions, including presentation of the actual experimental data, validation of the structural model, and functional experiments to support the proposed coupling mechanism.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence integrity
- **Claim pointer** "Far-Western assays confirmed direct physical interaction between both recombinant proteins."
- **Evidence pointer** Section 3.1, Figures 1 and 2 (not provided)
- **Concern** The central experimental claim of a physical interaction relies entirely on Far-Western data presented in Figures 1 and 2, which are not included in the provided manuscript. Without seeing the actual blots, including appropriate positive and negative controls, molecular weight markers, and replicates, the specificity and reproducibility of the interaction cannot be assessed. The authors mention controls using anti-His and anti-EhPC4 antibodies, but the results are only described textually.
- **Why it matters** The Far-Western assay is the only direct experimental evidence for the interaction. If the figures are not available or contain artifacts (e.g., non-specific binding, incomplete washing), the entire premise of the study collapses. The claim of a "direct physical interaction" requires visual confirmation of the data.
- **Resolution test** Provide the actual Far-Western blots with all controls, including a non-interacting protein as negative control, and demonstrate that the interaction is specific and reproducible across at least three independent experiments.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validity
- **Claim pointer** "The 3D structure of the EhPC4 protein was generated using a distance-based protein structure prediction approach by deep learning with the RAPTOR-X server."
- **Evidence pointer** Section 2.3, Section 3.2, Figure 3 (not provided)
- **Concern** The EhPC4 model is generated de novo using RAPTOR-X, a threading-based server, without experimental validation (e.g., SAXS, NMR, or cross-linking). The model quality is only assessed via Ramachandran plot statistics, which is insufficient to establish conformational accuracy, especially for the N-terminal region that is predicted to be flexible. The MD simulations are performed on this unvalidated model, and the resulting conformers are used for docking. Errors in the initial model will propagate through the entire computational pipeline.
- **Why it matters** The structural conclusions, including the identification of the hotspot and the claim that DNA-binding and RNA-recognition motifs remain accessible, depend entirely on the accuracy of the EhPC4 model and the docking predictions. If the model is incorrect, the proposed interaction interface and its functional implications are unreliable.
- **Resolution test** Validate the EhPC4 model using experimental techniques (e.g., circular dichroism, size-exclusion chromatography with multi-angle light scattering, or cross-linking mass spectrometry) or at minimum benchmark the model against known PC4 structures from other species with explicit RMSD values for the conserved domains. Provide a clear justification for the choice of RAPTOR-X over other methods and discuss the confidence of the predicted N-terminal conformation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation
- **Claim pointer** "Our findings suggest that EhCFIm25 serves as a molecular scaffold that physically couples transcription and polyadenylation, providing a structural framework for the efficient regulation of virulence-related genes in this parasite."
- **Evidence pointer** Section 4, Section 5
- **Concern** The manuscript proposes a functional model where EhCFIm25 couples transcription and polyadenylation, and links this to virulence gene regulation. However, no functional experiments are presented to test this model. There are no data on the consequences of disrupting the EhPC4-EhCFIm25 interaction, no co-localization studies in parasites, no knockdown or overexpression experiments, and no assessment of effects on mRNA processing or virulence phenotypes. The connection to virulence genes is purely speculative.
- **Why it matters** The title and conclusions promise "functional implications," but the study is purely structural and in vitro. Without functional validation, the biological relevance of the interaction remains unproven. The claim that this interface is a "plausible target" for drug development is premature without evidence that disrupting the interaction has phenotypic consequences.
- **Resolution test** Perform at least one functional experiment, such as knocking down EhPC4 or EhCFIm25 in *E. histolytica* trophozoites and assessing effects on growth, migration, erythrophagocytosis, or expression of known virulence genes. Alternatively, demonstrate that a peptide or small molecule disrupting the predicted interface affects parasite fitness in vitro.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive rigor
- **Claim pointer** "The thermodynamic stability (∆G < −8.7 kcal/mol) of the EhPC4-EhCFIm25 complex suggests a constitutive coupling mechanism."
- **Evidence pointer** Section 3.3, Section 4
- **Concern** The binding free energies are estimated using PRODIGY, which is a scoring function based on intermolecular contacts, not a rigorous thermodynamic calculation. The range of −8.7 to −11.4 kcal/mol is presented as evidence of stability, but these values are approximations and can vary significantly depending on the docking pose and the scoring function. The interpretation of "constitutive coupling" based on these estimates is an overreach, especially since no experimental binding affinity (e.g., ITC or SPR) is provided.
- **Why it matters** The claim of constitutive coupling is used to argue for biological relevance and therapeutic targeting. If the binding affinity is actually weak or transient, the proposed model would need revision. Overinterpreting computational scores as thermodynamic stability undermines the credibility of the conclusions.
- **Resolution test** Measure the binding affinity experimentally using isothermal titration calorimetry or surface plasmon resonance with purified recombinant proteins. If this is not feasible, temper the language to clearly state that the computational estimates are preliminary and require experimental confirmation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2
- **Evidence pointer** "Far-Western blotting assays"
- **Issue** The description of the Far-Western protocol is brief and lacks key details, such as the concentration of the prey protein, the blocking conditions, and the number of washes. This limits reproducibility.
- **Required correction** Expand the methods to include full details of the Far-Western protocol, including buffers, incubation times, and washing steps, or cite a detailed protocol.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Section 3.1
- **Evidence pointer** "Figure 1" and "Figure 2"
- **Issue** No statistical analysis or quantification of the Far-Western results is presented. It is unclear whether the interaction was observed in replicate experiments and whether the signal intensity is significantly above background.
- **Required correction** Provide quantification of band intensities from at least three independent experiments, with appropriate statistical tests, and include a statement on reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Section 1, Section 4
- **Evidence pointer** "Introduction" and "Discussion"
- **Issue** The discussion of PC4 functions in other organisms is limited and does not adequately address the known roles of PC4 in RNA processing beyond transcription, such as its involvement in DNA repair and chromatin organization. This narrow focus may overstate the novelty of the transcription-polyadenylation link.
- **Required correction** Broaden the discussion to include the multifunctional nature of PC4 in other systems and explicitly state how the proposed interaction with CFIm25 fits within or extends this known biology.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 3–7
- **Evidence pointer** "Figures 3–7"
- **Issue** The figures are not provided, so the quality of the structural representations, MD trajectory analyses, and docking results cannot be evaluated. In particular, the heatmap in Figure 6 and the superposition in Figure 7 are critical for the hotspot claim.
- **Required correction** Ensure all figures are of publication quality, with clear labels, color scales for heatmaps, and unambiguous representations of structural overlays.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language precision
- **Affected element** Section 5
- **Evidence pointer** "Conclusions"
- **Issue** The conclusion states the interaction is "thermodynamically stable" and "structurally non-competitive," but these terms are used loosely. "Thermodynamically stable" implies a measured free energy, which was not obtained, and "non-competitive" is not clearly defined in the context of the binding interface.
- **Required correction** Rephrase to "computationally predicted to be stable" and "does not occlude known functional domains," or provide operational definitions for these terms.

## Risk / unsupported claims
- The claim of a "direct physical interaction" between EhPC4 and EhCFIm25 is unsupported without the actual Far-Western data (Figures 1 and 2).
- The identification of a "conserved hotspot" at residues 249–255 of EhCFIm25 is based solely on computational docking and is not experimentally validated.
- The statement that EhCFIm25 "serves as a molecular scaffold that physically couples transcription and polyadenylation" is a functional interpretation not supported by any functional data.
- The claim that the interaction is "thermodynamically stable" is unsupported, as only computational estimates of binding energy are provided.
- The suggestion that the EhPC4-EhCFIm25 interface is a "plausible target" for drug development is speculative and not backed by any evidence of phenotypic consequences upon disruption.
- The assertion that the interaction regulates "virulence-related genes" is entirely hypothetical and not tested in this study.