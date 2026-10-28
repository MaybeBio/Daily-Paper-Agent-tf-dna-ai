## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Materials and methods, Results and discussion, Concluding remarks, Data availability)
- **Assessment boundary** Scientific soundness, structural novelty, consistency between claims and evidence, technical adequacy of methods, and readability for a broad audience
- **Shared manuscript claim summary** The authors report the first experimental three-dimensional structures of the genome-organizing protein p6 from *Bacillus subtilis* phage phi29, obtained through rational construct design guided by AlphaFold2 predictions. They propose a novel protein fold, characterize dimerization and oligomerization interfaces, and present a structural model of the p6–DNA nucleoprotein complex supported by docking, molecular dynamics simulations, and analytical ultracentrifugation. They further propose that the acidic C-terminal tail modulates DNA binding through an electrostatic shielding mechanism.
- **Visible evidence base** Crystallographic data for two C-terminal truncation variants (p6CΔ31 at 1.59 Å, p6CΔ20 at 2.30 Å), AlphaFold2 and AlphaFold-Multimer predictions, circular dichroism spectroscopy, analytical ultracentrifugation (sedimentation velocity and equilibrium), molecular dynamics simulations, and comparative structural analysis across 35 Salasvirus p6 sequences
- **Missing materials affecting confidence** Electron density maps and validation metrics (Ramachandran statistics, B-factors, coordinate errors) are not shown in the provided text. The supplementary figures and tables referenced throughout (Supplementary Figures S1–S13, Supplementary Tables 1–3, Supplementary Movies S1–S6) are not available for inspection. The specific MD simulation parameters, convergence criteria, and force field details are only partially described. The raw AUC data and fitting residuals are not shown.

## Reviewer
- **Overall assessment** This manuscript addresses a long-standing gap in the structural biology of a well-studied but structurally uncharacterized viral DNA-binding protein. The authors combine computational prediction with experimental validation in a pragmatic and largely convincing manner. The crystallographic structures of the truncated variants are likely to be of significant interest to the phage and DNA-protein interaction communities. The proposed model of the nucleoprotein complex is plausible and consistent with a substantial body of prior biochemical data. However, the manuscript would be strengthened by a more critical discussion of the limitations of the computational models, particularly the use of AlphaFold2 predictions as the basis for crystallographic construct design and the interpretation of the solution-state data. The claim of a "novel fold" is supported by the absence of structural homologs in DALI and other servers, but the authors should acknowledge the inherent limitations of such searches for small, potentially dynamic domains. Overall, the work is technically sound in its core crystallographic and biophysical components, but the extrapolation to the full-length protein and the in vivo context requires more cautious framing.
- **Who would be interested in the results, and why** Researchers studying bacteriophage biology, particularly the phi29 system and its relatives, will find the structures and functional models directly relevant. The broader community interested in protein-DNA recognition, especially minor-groove interactions and nucleoprotein complex assembly, will also be interested. Additionally, the methodological approach of using AlphaFold2 to guide construct design for crystallization of previously intractable proteins is a timely and useful demonstration that may appeal to structural biologists more generally.
- **Major strengths** The manuscript provides the first experimental structures of p6, resolving a long-standing gap. The combination of crystallography, computational modeling, and solution biophysics is complementary and mutually reinforcing. The proposed model of the p6-DNA filament is consistent with a wide range of previously published biochemical and biophysical data, lending credibility to the structural interpretation. The comparative analysis across the Salasvirus genus adds evolutionary context and strengthens the generalizability of the findings. The writing is generally clear and the figures are well-referenced in the text.
- **Major Concerns** The following concerns are detailed below.
- **Minor Comments** The following comments are detailed below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (novel fold claim), R1-M2 (full-length model extrapolation), R1-M3 (AUC interpretation), R1-M4 (MD simulation validation)
- **Assessment against Nature-style criteria**  
  *Originality*: The work is original in providing the first experimental structures of p6 and a comprehensive structural model of its nucleoprotein complex. The fold appears to be novel, although this claim requires careful validation.  
  *Scientific importance*: The findings are important for the phi29 field and for understanding a class of small, basic DNA-binding proteins that organize viral genomes. The work resolves a long-standing question and provides a framework for future functional studies.  
  *Interdisciplinary readership*: The topic is somewhat specialized, but the methodological approach (AlphaFold-guided crystallography) and the general principles of protein-DNA recognition may attract readers beyond the immediate phage community.  
  *Technical soundness*: The crystallographic analyses appear sound based on the reported resolution and R-factors, but the lack of validation metrics in the provided text limits full assessment. The computational modeling and AUC analyses are reasonable but require more detail and critical discussion.  
  *Readability for nonspecialists*: The manuscript is generally well-written and accessible, though some sections (e.g., the detailed structural descriptions) may be dense for nonspecialists. The abstract and introduction provide adequate context.
- **Recommendation posture** Supportive if technical concerns are resolved. The core crystallographic results are likely to be publishable, but the manuscript requires revisions to address the concerns below, particularly regarding the strength of the claims made from the computational models and the interpretation of the solution data.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim strength vs. evidence
- **Claim pointer** The authors state: "A search for proteins structurally related to phi29 protein p6 with servers DALI, PDBeFold, CATH, COFACTOR, SMART and ProFunc, yielded no statistically significant matches. For this reason, we propose that the overall p6 structure is unique, presenting a novel fold that does not currently resemble any structure deposited in the PDB."
- **Evidence pointer** Results and discussion, section "The three-dimensional structure of phi29 protein p6 monomer reveals a novel fold"
- **Concern** The claim of a "novel fold" is a strong statement that requires robust evidence. The authors report that searches with multiple servers yielded no significant matches, but the specific Z-scores, alignment lengths, and coverage values from DALI and PDBeFold are not provided. For a small protein domain (~70 residues in the folded core), DALI searches can often return low-confidence matches that are not statistically significant but may still indicate structural similarity. The authors should provide the quantitative output from these searches (e.g., top Z-scores, RMSD values, sequence identity) to support the claim. Additionally, the authors should consider whether the fold could be classified as a variant of an existing fold (e.g., an OB-fold or SH3-like barrel) rather than a completely new topology.
- **Why it matters** The claim of a novel fold is a key selling point of the paper. If the fold is actually a distant relative of a known fold, the novelty claim would be weakened. Providing quantitative search results would allow readers to assess the strength of this claim.
- **Resolution test** Provide the top hits from DALI and PDBeFold with their Z-scores, RMSDs, and alignment coverage. If no hits above a reasonable threshold (e.g., Z-score > 2) are found, the claim is supported. If marginal hits are found, the authors should discuss them and temper the "novel fold" claim accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validation
- **Claim pointer** The authors state: "By means of protein–DNA docking and molecular dynamic simulations, we have generated a comprehensive structural model for the nucleoprotein complex that consistently aligns with its established biochemical and thermodynamic parameters."
- **Evidence pointer** Results and discussion, section "Protein p6–DNA complex"
- **Concern** The structural model of the p6–DNA complex is a central result of the paper, but it is derived from computational docking and MD simulations rather than experimental structure determination. The authors validate the model by comparing its dimensions and periodicity with prior biochemical data (e.g., 12 bp per monomer, 63 bp per turn), which is reasonable. However, the manuscript does not provide sufficient detail on the docking methodology, the scoring function used, the selection criteria for the final model, or the convergence and stability of the MD simulations. The authors state that the model was generated using pyDockDNA with a single external restraint, but the details of the docking runs (e.g., number of models generated, clustering, ranking) are not described. The MD simulation length, force field, and analysis of convergence are also not fully specified. Without these details, the reliability of the model cannot be fully assessed.
- **Why it matters** The proposed model is used to explain a large body of experimental data and to make mechanistic claims about p6 function. If the model is not robustly validated, these claims are weakened.
- **Resolution test** Provide a detailed description of the docking protocol, including the number of models generated, the scoring function, and the criteria for selecting the final model. For the MD simulations, specify the force field, simulation length, temperature/pressure coupling, and provide evidence of convergence (e.g., RMSD vs. time plots, energy drift). If possible, perform additional validation, such as comparing the model with experimental data not used in the modeling (e.g., hydroxyl radical footprinting patterns).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Data interpretation
- **Claim pointer** The authors state: "At a concentration of 10 μM, the observed increase in buoyant molecular weight for both wt p6 and p6CΔ20 corresponded to 19.2 and 21.6 protein monomers, respectively, consistent with previously reported data for wt p6."
- **Evidence pointer** Results and discussion, section "The C-terminal tail of protein p6 plays a crucial role in dimerization and modulates its DNA-binding properties"
- **Concern** The interpretation of the AUC data relies on the assumption that the increase in buoyant molecular weight corresponds directly to the number of bound protein monomers. However, the buoyant molecular weight of a protein-DNA complex depends on the partial specific volumes of both components, and the calculation of the number of bound proteins from the buoyant mass increment requires accurate knowledge of these values. The authors state that the partial specific volumes were calculated from amino acid composition, but the uncertainty in these values and its propagation into the binding stoichiometry is not discussed. Additionally, the binding isotherm shown in Figure 7B appears to be fitted with a Hill equation, but the Hill coefficient and the goodness of fit are not reported.
- **Why it matters** The stoichiometry of the p6-DNA complex is a key parameter that supports the proposed model. If the stoichiometry is incorrect, the model may be wrong.
- **Resolution test** Provide a more detailed error analysis of the AUC-derived stoichiometry, including the uncertainty in the partial specific volumes and its effect on the calculated number of bound proteins. Report the Hill coefficient and the goodness of fit for the binding isotherm. If possible, validate the stoichiometry using an independent method (e.g., native mass spectrometry or size exclusion chromatography with multi-angle light scattering).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical validation
- **Claim pointer** The authors state: "The MD simulations indicated a potential interaction between the acidic tail and the basic patch of its corresponding monomer within the dimer, consistently supporting the stable maintenance of this electrostatic interaction over time."
- **Evidence pointer** Results and discussion, section "The C-terminal tail of protein p6 plays a crucial role in dimerization and modulates its DNA-binding properties"
- **Concern** The MD simulations are used to support a mechanistic model for the role of the C-terminal tail in modulating DNA binding. However, the manuscript does not provide sufficient detail on the simulation setup, including the starting structure, the solvation conditions, the ionic strength, and the length of the simulations. The authors state that the simulations were run for "at least 250 ns," but it is unclear how many independent simulations were performed and whether the observed interaction between the acidic tail and the basic patch was stable across all simulations. The authors also do not report the free energy of binding or other quantitative measures of the interaction strength.
- **Why it matters** The proposed electrostatic shielding mechanism is a novel and interesting hypothesis, but it needs to be supported by robust simulation data. If the interaction is not stable or is an artifact of the simulation setup, the mechanism would be called into question.
- **Resolution test** Provide a detailed description of the MD simulation setup, including the number of independent simulations, the ionic strength, and the length of the simulations. Show the time evolution of the distance between the acidic tail and the basic patch for each simulation. If possible, calculate the binding free energy using a method such as MM-PBSA or umbrella sampling to quantify the strength of the interaction.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract states: "The genome-organizing protein p6 of *Bacillus subtilis* bacteriophage phi29 plays an essential role in viral development by activating the initiation of DNA replication and participating in the early-to-late transcriptional switch." This is a long and dense sentence that could be split for clarity.
- **Required correction** Consider splitting into two sentences, e.g., "The genome-organizing protein p6 of *Bacillus subtilis* bacteriophage phi29 plays an essential role in viral development. It activates the initiation of DNA replication and participates in the early-to-late transcriptional switch."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Materials and methods, "Analytical ultracentrifugation assays"
- **Evidence pointer** Materials and methods, "Sedimentation velocity (SV) assays"
- **Issue** The SV experiments are described, but the rotor speed used for the SV runs is not stated. The rotor speed is a critical parameter for interpreting sedimentation coefficients.
- **Required correction** Add the rotor speed for the SV experiments.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results and discussion, "The C-terminal tail of protein p6 plays a crucial role in dimerization and modulates its DNA-binding properties"
- **Evidence pointer** Results and discussion, Figure 7C
- **Issue** The text states that the C-terminal tail contributes to protein stability, resulting in a decrease in Tm of around 10°C for the truncation mutant. However, it is not clear whether this is an increase or decrease in stability. A decrease in Tm indicates reduced stability, which should be stated explicitly.
- **Required correction** Clarify that the truncation mutant has a lower Tm, indicating reduced thermal stability.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Results and discussion, "Comparative structural analysis of protein p6 within the Salasvirus genus of phages"
- **Evidence pointer** Results and discussion, Figure 8
- **Issue** The text refers to "four regions (R-I, R-II, R-III and R-IV; Figure 8)" but does not explicitly state which residues correspond to each region in the figure legend or text. This makes it difficult for the reader to follow the discussion.
- **Required correction** Add a table or a sentence in the text listing the residue ranges for each region.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Materials and methods, "Molecular dynamics (MD) simulations"
- **Evidence pointer** Materials and methods, "Molecular dynamics (MD) simulations"
- **Issue** The MD simulations are described, but the force field parameters for the DNA and protein are not explicitly stated. The authors mention "ff14SB AMBER force field and PARMBSC1 modifications," but it is unclear whether the DNA parameters were taken from a specific parameter set (e.g., OL15 or bsc1).
- **Required correction** Specify the exact force field parameters used for both protein and DNA.

## Risk / unsupported claims
- The claim of a "novel fold" is not fully supported by the quantitative data provided. The authors should provide the output of the DALI and PDBeFold searches to allow readers to assess the significance of the structural similarity searches.
- The structural model of the p6–DNA complex is based on computational docking and MD simulations, but the validation of this model is indirect. The authors should provide more detail on the modeling methodology and the convergence of the simulations to support the reliability of the model.
- The stoichiometry of the p6–DNA complex derived from AUC experiments is dependent on the accuracy of the partial specific volumes used in the analysis. The authors should provide an error analysis to support the reported stoichiometry.
- The claim that the C-terminal tail acts as an electrostatic shield is based on MD simulations that are not fully described. The authors should provide more detail on the simulation setup and the stability of the observed interaction.