## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, methods, and discussion sections
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors propose that a DNA damage-induced phosphorylation circuit involving Mec1-Ddc2 and RPA modulates checkpoint recruitment through enhanced protein-protein interactions, higher-order assembly formation, and cooperative DNA binding, with structural and biophysical evidence supporting a phosphorylation-dependent oligomerisation mechanism.
- **Visible evidence base** Abstract, introduction, results sections (partial), methods, figure legends referenced but figures not fully visible, supplementary figure references
- **Missing materials affecting confidence** Full figures and figure legends, supplementary data files, statistical analysis details, complete results section, and some experimental validation data

## Reviewer
- **Overall assessment** This manuscript presents an interesting and potentially significant advance in understanding how phosphorylation events regulate Mec1-Ddc2 recruitment to RPA-ssDNA complexes. The combination of biophysical, structural, and yeast genetic approaches is commendable and appropriate for the questions addressed. The crystal structure of the phosphorylated Ddc2 peptide in complex with Rfa1-NTD provides novel molecular insights, and the proposed model of phosphorylation-dependent higher-order assembly is conceptually appealing. However, several concerns regarding data completeness, quantitative rigor, and in vivo relevance need to be addressed before the conclusions can be fully supported.

- **Who would be interested in the results, and why** Researchers in the DNA damage response and replication stress fields, particularly those studying ATR/Mec1 signaling mechanisms, will find this work relevant. The structural insights into RPA-Ddc2 interactions and the proposed phosphorylation-dependent regulatory circuit will also interest structural biologists studying protein-protein interactions in genome maintenance pathways. The potential role of zinc in modulating checkpoint assembly may attract researchers studying metal ion signaling in cellular stress responses.

- **Major strengths** The study combines multiple complementary approaches including X-ray crystallography, biophysical binding assays, electron microscopy, and yeast genetics. The identification of a specific phosphorylation site (S11) in Ddc2 that enhances RPA binding is a novel finding with clear mechanistic implications. The crystal structure provides atomic-level detail of the interaction interface and reveals an unusual zinc coordination motif. The proposed model of higher-order assembly formation is conceptually innovative and testable.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that "Rfa1-S178 phosphorylation enhances Mec1-Ddc2 recruitment" based on biophysical and pull-down experiments
- **Evidence pointer** Results section "Phosphorylation of RPA at S178 enhances Mec1-Ddc2 recruitment", Figure 1, Supplementary Figures 1-2
- **Concern** The quantitative improvement in binding affinity for RPA S178D compared to wild-type is reported as approximately 2-fold. This modest effect, while statistically significant, may not fully support the strong claim of enhanced recruitment in a cellular context. The in vitro binding experiments use a truncated Ddc2-CC construct, and the relevance of this fragment to full-length Mec1-Ddc2 complex behavior is not fully established. Additionally, the pull-down experiments with full-length Mec1-Ddc2 are described but the quantitative data and statistical analysis are not clearly presented.
- **Why it matters** The central claim of the paper rests on the functional significance of phosphorylation-enhanced recruitment. If the effect is only 2-fold in vitro and the in vivo relevance is not directly demonstrated, the physiological importance of this mechanism remains uncertain.
- **Resolution test** Provide quantitative pull-down data with statistical analysis, demonstrate that the 2-fold affinity enhancement translates to meaningful differences in cellular recruitment, and show that the Ddc2-CC fragment faithfully recapitulates full-length Ddc2 binding behavior.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** In vivo validation
- **Claim pointer** The authors claim that "Ddc2 phosphorylation enhances Mec1-Ddc2 recruitment and is important for the DNA damage checkpoint in yeast" based on yeast growth assays and kinase activity measurements
- **Evidence pointer** Results section "Phosphorylation of the Ddc2 N-terminus enhances RPA association", Figure 2, Supplementary Figures 3-4
- **Concern** The yeast genetic experiments show that S11A mutation causes growth defects and HU sensitivity, but the direct link between this phenotype and impaired RPA recruitment is not established. The authors do not demonstrate that the S11A mutant has reduced recruitment to sites of DNA damage in vivo. The kinase activity assays show that mutant complexes retain catalytic activity, but this does not exclude other functional defects beyond recruitment. The specificity of the phenotype to the proposed mechanism needs to be more rigorously tested.
- **Why it matters** Without direct in vivo evidence linking the phosphorylation state to recruitment efficiency, alternative explanations for the observed phenotypes (e.g., altered protein stability, defective interactions with other factors) cannot be excluded.
- **Resolution test** Perform chromatin immunoprecipitation or live-cell imaging experiments to directly measure Mec1-Ddc2 recruitment to damage sites in wild-type versus S11A mutant strains. Rescue experiments with phosphomimetic mutants would strengthen the causal link.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Structural interpretation
- **Claim pointer** The authors propose that "phosphorylation-dependent higher order assemblies stabilised by Zn2+" form based on the crystal structure and EM analysis
- **Evidence pointer** Results section "Structure of Rfa1-NTD in complex with a phosphorylated Ddc2 peptide", Figure 3-4, Table 1
- **Concern** The crystal structure shows a specific packing arrangement, but the physiological relevance of the observed oligomerisation interface is not fully validated. The EM data showing Mec1-Ddc2 clustering is semi-quantitative and based on a limited number of particles. The authors should demonstrate that the crystallographic interface is relevant in solution and that the proposed higher-order assemblies form under physiologically relevant conditions.
- **Why it matters** The proposed model of supramolecular complex formation is a key conceptual advance, but if the structural interface is a crystallographic artifact or the EM clustering is not specific, the model would need substantial revision.
- **Resolution test** Perform mutagenesis of the proposed interface residues and test effects on oligomerisation in solution (e.g., by SEC-MALS or analytical ultracentrifugation). Increase the particle count for EM analysis and include negative controls. Validate the interface in the context of full-length proteins.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic model
- **Claim pointer** The authors propose a "feed-forward loop involving phosphorylation of Rfa1, which is predominantly Mec1-dependent, in recruiting and retaining checkpoint kinase at ssDNA"
- **Evidence pointer** Discussion section, Figure 5
- **Concern** The proposed feed-forward loop is speculative and not directly tested. While the individual components are supported by data, the integrated model requires experimental validation. The authors do not demonstrate that Rfa1 phosphorylation by Mec1 leads to enhanced Mec1-Ddc2 recruitment in a cyclic manner. The temporal dynamics of this proposed loop are not addressed.
- **Why it matters** The feed-forward loop model is a central conceptual contribution of the paper. If not properly validated, the model may be premature and could mislead future research directions.
- **Resolution test** Design experiments to test the proposed loop, such as time-course experiments measuring Rfa1 phosphorylation and Mec1-Ddc2 recruitment kinetics. Use mutants that specifically disrupt the proposed feedback mechanism and test for checkpoint function.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1E
- **Evidence pointer** Results section "Phosphorylation of RPA at S178 enhances Mec1-Ddc2 recruitment"
- **Issue** The Hill coefficient analysis is presented as evidence for cooperative binding, but the statistical comparison between conditions is not clearly described. The authors should specify how many independent experiments were performed and how the Hill coefficients were compared.
- **Required correction** Provide statistical analysis details for Hill coefficient comparisons, including the number of replicates and the specific statistical test used.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological clarity
- **Affected element** Zinc binding experiments
- **Evidence pointer** Results section "Structure of Rfa1-NTD in complex with a phosphorylated Ddc2 peptide", Figure 3E-G
- **Issue** The ITC experiments for zinc binding to the Ddc2 peptide show moderate affinity, but the stoichiometry of zinc binding is not clearly stated. The authors should clarify whether one or two zinc ions bind per peptide and how this relates to the crystal structure.
- **Required correction** Clearly state the binding stoichiometry in the ITC analysis and discuss how this relates to the structural observations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The discussion of zinc's potential physiological role in checkpoint regulation would benefit from more specific references to cellular zinc concentrations and known zinc-dependent signaling mechanisms in yeast.
- **Required correction** Add specific references and quantitative context for cellular zinc concentrations and known zinc-binding proteins involved in DNA damage responses.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Experimental controls
- **Affected element** EM analysis
- **Evidence pointer** Results section "Ddc2 phosphorylation promotes oligomerisation of RPA", Figure 5
- **Issue** The EM analysis of Mec1-Ddc2 clustering would benefit from additional controls, such as a mutant that cannot form the proposed higher-order assemblies, to demonstrate specificity of the observed clustering.
- **Required correction** Include a negative control in the EM analysis, such as a Ddc2 mutant lacking the phosphorylation site or the zinc-binding residues.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Structural data
- **Evidence pointer** Methods section "Crystallisation and Structure Determination"
- **Issue** The authors state that structures have been deposited in the PDB, but the accession codes are provided. It would be helpful to also provide the validation metrics and any relevant structure factors.
- **Required correction** Ensure that all structural data, including structure factors, are deposited and accessible, and provide a summary of validation statistics in the manuscript.

## Risk / unsupported claims
- The claim that "formation of supramolecular complexes of RPA and Mec1-Ddc2, modulated by phosphorylation, would allow for rapid clustering of damage foci to promote checkpoint signalling" is speculative and not directly supported by functional experiments.
- The proposed "feed-forward loop" involving Rfa1 phosphorylation and Mec1-Ddc2 recruitment is not experimentally validated as an integrated model.
- The physiological relevance of zinc binding to the Ddc2-RPA interface is inferred from in vitro experiments but not demonstrated in vivo.
- The claim that Ddc2 S11 phosphorylation is "important for the DNA damage checkpoint in yeast" is supported by growth phenotypes, but the direct mechanistic link to recruitment efficiency is not established.
- The quantitative significance of the 2-fold enhancement in binding affinity for Rfa1 S178D is not fully contextualized with respect to cellular concentrations and competition with other RPA-binding factors.