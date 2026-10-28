## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific content, methodological soundness, evidence quality, and internal consistency of the claims as presented in the supplied material
- **Shared manuscript claim summary** The authors characterize the DNA-binding properties of mycobacterial Ku (mKu) using in silico and in vitro approaches, reporting that mKu binds linear dsDNA with high affinity, exhibits positive cooperativity for dsDNA ≥40 bp, stabilizes both protein and DNA upon binding, protects DNA ends from exonuclease degradation, and forms higher-order oligomeric assemblies that may function in NHEJ synapsis.
- **Visible evidence base** MD simulation data (RMSD, Rg), DSF thermal shift data, SPR kinetic data, EMSA data, AUC sedimentation data, and negative-stain EM images, as described in the text and referenced figures
- **Missing materials affecting confidence** Figures and supplementary tables referenced throughout (Fig 1-7, S1 Tables 1-6, S1 Figs 1-5) were not provided. Raw data, statistical details, and experimental replicates are not accessible. The methods section is incomplete (Section 2 is empty). No sequence alignment data, model validation metrics, or raw sensorgrams are visible.

## Reviewer

### Overall assessment
This manuscript addresses a relevant and under-explored question in mycobacterial DNA repair: the biochemical and biophysical characterization of the Ku protein from M. tuberculosis. The combination of computational and experimental approaches is appropriate in principle, and the authors have generated a substantial body of data. However, the manuscript as presented has significant limitations. The most critical issue is that the key claims, particularly those regarding positive cooperativity, DNA end protection, and higher-order oligomer formation, are not fully supported by the evidence as described. The absence of the actual figures and supplementary data makes a rigorous assessment impossible. Furthermore, several methodological details are missing, and some interpretations appear to overreach the data presented. The claim regarding a role in NHEJ synapsis is speculative and not directly tested. The manuscript would require substantial revision, additional controls, and a more cautious interpretation of the data before it could be considered for publication in a high-impact venue.

### Who would be interested in the results, and why
Researchers in the fields of mycobacterial biology, DNA repair mechanisms, and host-pathogen interactions would find this work of interest. The study addresses a fundamental gap in understanding how M. tuberculosis survives genotoxic stress during dormancy, which is clinically relevant given the global burden of tuberculosis. The characterization of mKu's DNA-binding properties could inform future studies on NHEJ inhibition as a therapeutic strategy. Additionally, the comparative aspects with human Ku70/80 may interest the broader DNA repair community, particularly those studying the evolution of NHEJ machinery across domains of life.

### Major Strengths
- The study addresses a significant knowledge gap regarding prokaryotic Ku proteins, particularly in a clinically important pathogen
- The multi-technique approach (computational modeling, biophysics, biochemistry, and structural biology) is comprehensive in scope
- The authors appropriately acknowledge limitations of their SPR-based affinity measurements
- The work has potential translational relevance for tuberculosis drug development
- The comparative analysis with human Ku70/80 provides useful context

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that mKu exhibits positive cooperativity for dsDNA ≥40 bp based on Hill coefficients derived from SPR and EMSA experiments.
- **Evidence pointer** Section 3.5, Fig 4, Fig 5, S1 Fig 4
- **Concern** The Hill coefficient values reported from SPR (n = 2.45 ± 0.34 for 40 bp DNA) and EMSA (n = 1.5 ± 0.3) are inconsistent with each other. The authors do not explain this discrepancy. Moreover, the SPR experiments were performed with one end of the DNA immobilized on the chip, which the authors acknowledge may not reflect natural binding. The calculation of Hill coefficients from SPR data with heterogeneous binding populations (as suggested by the multiple complex sizes in EMSA) is problematic. The claim of positive cooperativity requires more rigorous analysis, including proper controls for non-specific binding and a demonstration that the cooperativity is not an artifact of the experimental setup.
- **Why it matters** Positive cooperativity is a central claim of the manuscript and is used to support the proposed model of mKu function. If this claim is not robust, the mechanistic conclusions are weakened.
- **Resolution test** The authors should provide raw binding data, show replicate experiments, perform proper curve fitting with statistical comparison of models (e.g., Hill vs. non-cooperative), and reconcile the discrepancies between SPR and EMSA results. Ideally, an independent method (e.g., ITC or fluorescence anisotropy) should be used to confirm cooperativity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors claim that mKu protects DNA ends from exonuclease degradation, based on approximately 50% signal retention in the presence of mKu.
- **Evidence pointer** Section 3.4, Fig 3
- **Concern** The exonuclease assay as described shows only partial protection (50%) even at a 2:1 mKu dimer to DNA ratio. The authors attribute this to mKu sliding on DNA, but this interpretation is not directly tested. The assay design does not distinguish between end protection and other mechanisms (e.g., enzyme inhibition by mKu, aggregation effects, or fluorescence artifacts). The concentration of ExoIII used (50 U/ml) may be excessive, and no titration of enzyme or mKu is shown. The authors do not demonstrate that the protected DNA fraction corresponds to end-capped molecules.
- **Why it matters** The protective function of mKu is a key physiological claim with implications for its role in NHEJ. Without rigorous evidence, this claim is not established.
- **Resolution test** The authors should perform a time-course experiment, vary mKu and ExoIII concentrations, include a control with a non-DNA-binding protein, and directly visualize the protected DNA ends (e.g., by gel electrophoresis). A competition experiment with unlabeled DNA ends would also strengthen the interpretation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretive validity
- **Claim pointer** The authors claim that mKu forms higher-order oligomeric assemblies with DNA, including filament-like structures, and that this may indicate a role in NHEJ synapsis.
- **Evidence pointer** Section 3.6, Fig 6, Fig 7
- **Concern** The AUC data show a heterogeneous peak with a sedimentation coefficient of approximately 25S, which the authors interpret as higher-order oligomers. However, the expected size of a 2:1 mKu dimer-DNA complex is not clearly stated, and the calculation of the theoretical sedimentation coefficient is not shown. The EM images show filament-like structures, but the authors do not provide quantitative analysis (e.g., length distribution, width measurements, or comparison with controls). The possibility that these filaments are artifacts of negative staining or non-specific aggregation is not excluded. The authors present two speculative models for filament formation but do not provide evidence to distinguish between them.
- **Why it matters** The claim of higher-order oligomerization and its proposed role in synapsis is the most novel aspect of the manuscript. If this claim is not rigorously supported, the manuscript's contribution is substantially diminished.
- **Resolution test** The authors should provide quantitative EM analysis, include control samples (DNA alone, mKu alone, and a non-specific protein-DNA complex), perform cross-linking experiments to confirm oligomer stoichiometry, and use a defined in vitro synapsis assay (e.g., FRET-based or single-molecule) to directly test the synapsis hypothesis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** The authors claim to have performed molecular dynamics simulations showing that mKu binding stabilizes both the protein and DNA.
- **Evidence pointer** Section 3.2, Fig 1, S1 Tables 5-6, S1 Fig 2
- **Concern** The MD simulation methodology is described only briefly. Key details are missing: force field parameters for the DNA-protein complex, simulation box size, equilibration protocol, number of replicates, convergence criteria, and error analysis. The RMSD values reported (9.5 ± 1.9 Å and 8.3 ± 1.18 Å for the apo mKu dimer) are unusually high for a stable protein dimer, suggesting either a highly flexible protein or potential simulation instability. The authors do not show RMSD plots over time, which would be essential to assess convergence. The comparison between apo and bound states is made without statistical analysis.
- **Why it matters** The computational results are used to support the experimental findings. If the simulations are not rigorously performed and analyzed, the conclusions drawn from them are unreliable.
- **Resolution test** The authors should provide complete simulation details, show time-series data for RMSD and Rg, perform replicate simulations, and apply appropriate statistical tests to compare apo and bound states.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Internal consistency
- **Claim pointer** The authors state in the Discussion that mKu showed the highest affinity for the shortest DNA (20 bp), but in the Results section they report the lowest K_M for 20 bp DNA, which is consistent. However, the relationship between K_M and binding affinity is not straightforward in the context of a two-site binding model, and the authors do not clarify this.
- **Evidence pointer** Section 3.5, Section 4, Fig 4
- **Concern** The authors use K_M values from Michaelis-Menten fitting of SPR data to discuss binding affinity. This is conceptually problematic because K_M is a kinetic parameter that reflects both binding and unbinding rates, not a true equilibrium dissociation constant. The authors do not derive K_D from the SPR data, and the EMSA-derived K_D (0.33 ± 0.08 nM) is not compared to the SPR-derived K_M values. The interpretation of the SPR data in terms of affinity is therefore not rigorous.
- **Why it matters** The quantitative comparison of binding affinities across DNA lengths is a key result. If the analysis is conceptually flawed, the conclusions about length-dependent binding are not reliable.
- **Resolution test** The authors should perform proper kinetic analysis of the SPR data (e.g., global fitting to a 1:1 or two-site model) to derive association and dissociation rate constants, and calculate equilibrium dissociation constants. They should also compare these with the EMSA-derived K_D.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, line "positive cooperativity for dsDNAs (ζ40bp)"
- **Issue** The symbol "ζ" is used without definition. It appears to mean "greater than or equal to" but this is not standard notation.
- **Required correction** Replace "ζ40bp" with "≥40 bp" or define the symbol at first use.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section
- **Evidence pointer** Section 2
- **Issue** The Methods section is empty in the provided manuscript. This is a critical omission that prevents assessment of experimental reproducibility.
- **Required correction** Provide a complete Methods section with all experimental details, including buffer compositions, instrument settings, data analysis procedures, and statistical methods.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Section numbering
- **Evidence pointer** Sections 3.1-3.6
- **Issue** The Results section is numbered 3.1-3.6, but the Methods section is numbered 2 and the subsections in Methods (3.1-3.5) overlap with Results numbering. This is confusing.
- **Required correction** Renumber the Methods subsections (e.g., 2.1-2.5) to avoid confusion with Results numbering.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Section 3.5, Fig 4
- **Evidence pointer** Section 3.5
- **Issue** The authors report K_M values with standard errors but do not state the number of replicates or the statistical test used to compare values across DNA lengths.
- **Required correction** State the number of independent experiments, the statistical tests used, and the significance thresholds.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 3.6, Fig 7
- **Evidence pointer** Section 3.6
- **Issue** The authors state that "no cross dimer-dimer interaction or filament-like structures were seen for mKu in absence of DNA" but do not show this control data.
- **Required correction** Include the control images for mKu alone in the main figures or supplementary material.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Section 1, Section 4
- **Issue** The authors mention that human Ku70/80 has been reported to preserve DNA termini from DNase I digestion, but they do not cite the specific reference in the text (reference 11 is listed in the reference list but not cited in the text at that point).
- **Required correction** Ensure all references are cited in the text at the appropriate locations.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Language
- **Affected element** Throughout
- **Evidence pointer** Various locations
- **Issue** There are several grammatical and stylistic issues throughout the manuscript (e.g., "the our observations" in Section 3.6, "the the" in Section 3.2).
- **Required correction** Perform a thorough language edit to correct grammatical errors and improve readability.

### Technical failings that need to be addressed before the case is established
- R1-M1: Inconsistent Hill coefficient values between SPR and EMSA; lack of rigorous cooperativity analysis
- R1-M2: Incomplete exonuclease protection assay with no mechanistic distinction
- R1-M3: Unsupported claims of higher-order oligomerization and synapsis without quantitative analysis or direct functional assays
- R1-M4: Inadequate description of MD simulation methodology and lack of statistical analysis
- R1-M5: Conceptual issues with using K_M as a measure of binding affinity

### Assessment against Nature-style criteria
- **Originality**: Moderate. The study addresses a relatively unexplored area (mycobacterial Ku biochemistry), but the approaches used are largely standard for the field. The claim of a potential role in synapsis is novel but not directly tested.
- **Scientific importance**: Moderate. Understanding mKu function is relevant for tuberculosis biology, but the study does not provide a major conceptual advance beyond what is known about Ku proteins in other organisms.
- **Interdisciplinary readership**: Limited. The manuscript is primarily of interest to specialists in mycobacterial DNA repair and protein-DNA interactions. The broader significance for fields such as drug development or host-pathogen interactions is not clearly articulated.
- **Technical soundness**: Insufficient. Several key claims are not supported by the evidence as presented, and methodological details are missing. The lack of raw data and figures prevents a full assessment.
- **Readability for nonspecialists**: Acceptable. The manuscript is generally well-written and the logic is clear, but the technical jargon and lack of context for the significance of NHEJ in tuberculosis may limit accessibility.

### Recommendation posture
Currently not established from the provided evidence. The manuscript addresses a relevant topic and has generated a substantial dataset, but the key claims are not rigorously supported. The authors would need to provide the missing data, address the methodological concerns, and substantially revise their interpretations before the manuscript could be considered for publication. The potential for a revised version to be suitable for a specialized journal is present, but the current form is not sufficient for a high-impact general audience.

## Risk / unsupported claims
- The claim of positive cooperativity for dsDNA ≥40 bp is not robustly supported due to inconsistent Hill coefficients and methodological concerns.
- The claim that mKu protects DNA ends from exonuclease degradation is only partially supported and alternative explanations are not excluded.
- The claim that mKu forms higher-order oligomeric assemblies with a role in NHEJ synapsis is speculative and not directly tested.
- The claim that mKu binding stabilizes both protein and DNA is based on MD simulations with inadequate methodological description and no statistical analysis.
- The claim that mKu shares the closest sequence similarity with Omega phage is based on sequence identity values that are not placed in a phylogenetic context.
- The claim that the apo form of mKu is "compact" while the DNA-bound form is "loose" is based on Rg values without statistical comparison.
- The claim that mKu may undergo irreversible binding with DNA, similar to human Ku, is speculative and not tested.