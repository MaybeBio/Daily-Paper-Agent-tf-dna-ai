## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability, supplementary data description)
- **Assessment boundary** Scientific content, technical soundness, and claims as presented in the provided manuscript text. No external validation or replication was performed.
- **Shared manuscript claim summary** The authors report the crystal structure of the Deinococcus radiodurans DNA damage response protein DdrC, solved de novo by SAD phasing, revealing an asymmetric domain-swapped dimer. They propose two distinct DNA binding sites per dimer, supported by fluorescence polarization and molecular dynamics simulations, and demonstrate DdrC-mediated compaction and negative supercoiling of plasmid DNA. They propose DdrC functions as a DNA damage-induced nucleoid-associated protein.
- **Visible evidence base** Abstract, Introduction, Materials and Methods (expression/purification, crystallization, structure determination, prediction, plasmid preparation, AFM, fluorescence polarization, gel electrophoresis, SEC-MALLS, AUC, MD simulations), Results (structure, biophysical characterization, DNA binding, topology assays), Discussion, Data Availability, Funding, Conflict of Interest, Acknowledgements. Tables and figures referenced but not provided.
- **Missing materials affecting confidence** Figures and tables (including Table 1, Supp. Tables S1-S2, Supp. Figs S1-S7) are referenced but not included. PDB accession number is listed as "XXXX" and therefore unavailable. Raw data for fluorescence polarization, AFM image analysis, and gel electrophoresis are not provided. Details of MD simulation setup (force field parameters, equilibration protocol, analysis methods) are incomplete.

## Reviewer
- **Overall assessment** This manuscript presents a structurally and biochemically interesting characterization of DdrC, a protein unique to Deinococcus species and implicated in radiation resistance. The crystal structure revealing an asymmetric domain-swapped dimer is novel and potentially significant. However, the manuscript has several technical weaknesses that need to be addressed. The evidence for two distinct DNA binding sites is indirect and relies heavily on MD simulations with manually placed DNA. The functional significance of the observed DNA compaction and supercoiling activity in the context of the proposed in vivo role is not directly tested. The claim that DdrC is a nucleoid-associated protein is plausible but not experimentally demonstrated. The manuscript would benefit from additional experimental validation and a more cautious interpretation of the computational results.
- **Who would be interested in the results, and why** Researchers studying DNA damage response and repair mechanisms in bacteria, particularly those interested in Deinococcus radiodurans and its extreme radiation resistance. Structural biologists interested in novel protein folds, domain-swapped dimers, and DNA-protein interactions. The work may also be of interest to the broader community studying nucleoid-associated proteins and bacterial chromosome organization.
- **Major strengths** The de novo structure determination of a novel protein with no homologues is a significant technical achievement. The discovery of an asymmetric domain-swapped dimer is structurally interesting and rare. The combination of structural, biophysical, and computational approaches is comprehensive. The study addresses a biologically relevant question regarding radiation resistance mechanisms.
- **Major Concerns** The evidence for two distinct DNA binding sites is indirect. The functional relevance of the in vitro DNA compaction and supercoiling activities to the proposed in vivo role is not established. The MD simulations are used to support key claims but have limitations that are not fully discussed. The manuscript does not provide direct evidence that DdrC functions as a nucleoid-associated protein in vivo.
- **Minor Comments** The manuscript would benefit from a more detailed description of the MD simulation setup and analysis. The authors should clarify the statistical analysis used for the AFM data. The discussion of the potential role of DdrC in chromosome segregation is speculative and could be more clearly separated from the main conclusions.
- **Technical failings that need to be addressed before the case is established** The lack of direct experimental evidence for two distinct DNA binding sites. The absence of a functional assay linking the observed in vitro activities to the proposed in vivo role. The reliance on MD simulations with manually placed DNA without sufficient validation.
- **Assessment against Nature-style criteria** Originality: High. The structure of DdrC is novel and the asymmetric domain-swapped dimer is unusual. Scientific importance: Moderate to high. The work contributes to understanding radiation resistance mechanisms, but the direct relevance to the in vivo function is not fully established. Interdisciplinary readership: Moderate. The work will appeal to structural biologists and those studying DNA repair, but may be too specialized for a broader audience. Technical soundness: Moderate. The structural determination appears sound, but the functional characterization has weaknesses. Readability for nonspecialists: Moderate. The manuscript is generally well-written but contains technical details that may be challenging for non-specialists.
- **Recommendation posture** Supportive if technical concerns are resolved. The structural findings are novel and interesting, but the functional claims require additional experimental support.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence for two distinct DNA binding sites
- **Claim pointer** The authors claim that DdrC possesses two distinct DNA binding sites with different affinities, based on fluorescence polarization and MD simulations.
- **Evidence pointer** Results section "DdrC dimer possesses two distinct DNA binding sites", Figures 3 and 4 (not provided), Supp. Tables S1-S2, Supp. Figs S4-S6 (not provided)
- **Concern** The fluorescence polarization data show that DdrC binds to both 20-mer and 50-mer dsDNA, and the data are fitted to a two-site binding model. However, the manuscript does not provide sufficient evidence to distinguish between two independent binding sites on the dimer versus a single binding site with negative cooperativity or other more complex binding modes. The MD simulations are used to support the two-site model, but the DNA was manually placed on the protein, which introduces significant bias. The simulations show that the DNA moves to adapt to the protein surface, but this does not prove that the identified sites are the physiologically relevant binding sites.
- **Why it matters** The claim of two distinct DNA binding sites is central to the proposed model of DdrC bridging DNA duplexes. If this claim is not well-supported, the proposed mechanism of action is weakened.
- **Resolution test** The authors should provide additional experimental evidence for two distinct binding sites, such as mutagenesis of the proposed binding residues followed by binding assays, or a more rigorous analysis of the binding data that can distinguish between different models. The MD simulations should be validated by comparing the predicted contacts with experimental data, such as cross-linking or hydrogen-deuterium exchange.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional relevance of in vitro activities
- **Claim pointer** The authors propose that DdrC functions as a DNA damage-induced nucleoid-associated protein that enhances nucleoid compaction to limit dispersion of the fragmented genome and facilitate DNA repair.
- **Evidence pointer** Abstract, Discussion, Results sections "DdrC alters the topology of plasmid DNA" and "DdrC dimer possesses two distinct DNA binding sites", Figures 5 and 6 (not provided)
- **Concern** The manuscript demonstrates that DdrC can compact plasmid DNA and introduce negative supercoils in vitro. However, the link between these in vitro activities and the proposed in vivo function is not directly tested. The authors do not provide any experiments showing that DdrC affects nucleoid compaction or DNA repair in D. radiodurans cells. The claim that DdrC is a nucleoid-associated protein is based on a previous study showing its recruitment to the nucleoid, but the functional significance of this recruitment is not explored here.
- **Why it matters** The proposed in vivo function is a major conclusion of the manuscript. Without direct evidence, the significance of the structural and biochemical findings is diminished.
- **Resolution test** The authors should perform experiments to test the in vivo function of DdrC, such as examining the effect of ddrC deletion on nucleoid compaction and DNA repair efficiency in D. radiodurans. Alternatively, they could use a cell-free system to demonstrate that DdrC-mediated DNA compaction facilitates repair by specific repair pathways.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Validation of MD simulations
- **Claim pointer** The authors use MD simulations to support the stability of the DdrC dimer and the model of DNA binding.
- **Evidence pointer** Methods section "Molecular dynamics simulations", Results sections "De novo phasing of the structure of DdrC" and "DdrC dimer possesses two distinct DNA binding sites", Supp. Figs S3-S6 (not provided)
- **Concern** The MD simulation methods are described briefly. The manuscript states that two simulations were performed on the apo-DdrC structure and five on the DdrC-DNA complex, but it does not provide details on the force field parameters, the equilibration protocol, the length of the simulations (beyond 500 ns production), or the analysis methods used to assess stability and contacts. The authors state that the DNA was manually placed, which is a significant source of bias. The simulations show that the DNA moves to adapt to the protein surface, but this does not validate the initial placement.
- **Why it matters** The MD simulations are used to support the stability of the dimer and the DNA binding model. If the simulations are not well-validated, the conclusions drawn from them are weakened.
- **Resolution test** The authors should provide a more detailed description of the MD simulation setup and analysis. They should also validate the simulations by comparing the predicted contacts with experimental data, such as mutagenesis or cross-linking studies. They should discuss the limitations of the manual DNA placement and the potential for bias.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Fluorescence polarization methods
- **Evidence pointer** Methods section "Fluorescence polarization"
- **Issue** The description of the fluorescence polarization assay is brief. It is not clear how the data were analyzed, what the error bars represent, or how many independent experiments were performed. The manuscript states that the data were fitted to one of three models, but it is not clear how the best model was selected.
- **Required correction** The authors should provide more details on the fluorescence polarization assay, including the number of replicates, the error analysis, and the criteria for model selection.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** AFM data analysis
- **Evidence pointer** Methods section "Atomic Force Microscopy", Results section "DdrC alters the topology of plasmid DNA"
- **Issue** The manuscript states that the fraction of condensed plasmids was determined for each field of view, but it is not clear how many fields of view were analyzed, how many plasmids were counted, or what the error bars in Figure 5F represent.
- **Required correction** The authors should provide more details on the statistical analysis of the AFM data, including the number of fields of view, the number of plasmids counted, and the statistical tests used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of the potential role of DdrC in chromosome segregation is speculative and not directly supported by the data presented. The authors should more clearly distinguish between conclusions supported by their data and speculative hypotheses.
- **Required correction** The authors should revise the discussion to more clearly separate their findings from speculative interpretations.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data Availability section
- **Evidence pointer** Data Availability section
- **Issue** The PDB accession number is listed as "XXXX" and the manuscript states that coordinates have been deposited, but the accession number is not provided. This prevents readers from accessing the structural data.
- **Required correction** The authors should provide the PDB accession number in the final version of the manuscript.

## Risk / unsupported claims
- The claim that DdrC possesses two distinct DNA binding sites is not fully supported by the data presented. The fluorescence polarization data are consistent with a two-site model, but other models are not excluded. The MD simulations are biased by the manual placement of DNA.
- The claim that DdrC functions as a DNA damage-induced nucleoid-associated protein that enhances nucleoid compaction to facilitate DNA repair is not directly tested. The in vitro data are suggestive but do not establish the in vivo function.
- The claim that the asymmetric domain-swapped dimer is the biologically relevant form of DdrC is not directly tested. The authors do not provide evidence that the dimer is the predominant form in solution or in cells.
- The claim that DdrC can bridge DNA duplexes is based on the model of two DNA binding sites and the MD simulations, but no direct experimental evidence for bridging is provided.
- The claim that the wHTH motif of DdrC is unlikely to play a direct role in DNA binding is based on electrostatic surface potential calculations, but this is not experimentally validated.