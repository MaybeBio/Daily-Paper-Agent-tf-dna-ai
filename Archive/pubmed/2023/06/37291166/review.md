## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims relative to evidence presented, and suitability for a general multidisciplinary journal
- **Shared manuscript claim summary** The authors use computational methods (homology modeling, protein–protein docking, 200 ns molecular dynamics simulations, MM/PBSA binding free energy calculations, energy decomposition analysis, and configurational entropy calculations) to predict two novel binding sites for RPA2 on the tumor suppressor protein menin, and to assess the effect of the S606F point mutation on the stability and binding affinity of the menin-RPA2 complex.
- **Visible evidence base** Abstract, Introduction, Materials and Methods, Results, Discussion, Conclusion, Table 1, Table 2, Figures 1–8 (figure legends only, no actual figure images), Supplementary figure legends (S1–S4)
- **Missing materials affecting confidence** Actual figure images (Figs. 1–8, S1–S4) were not provided; supplementary annexure S1 referenced but not included; no structural coordinates, PDB files, or trajectory data; no docking pose coordinates; no validation metrics beyond those stated in text; no raw MM/PBSA energy component data beyond Table 2; no information on force field parameters beyond force field names; no convergence criteria for MD simulations; no replica or error analysis details beyond standard deviation in Table 2

## Reviewer

### Overall assessment
The manuscript addresses a biologically relevant question, namely the molecular basis of the menin-RPA2 interaction and the potential impact of a clinically observed missense mutation (S606F) on this interaction. The computational workflow is reasonable in principle, and the identification of two putative RPA2 binding sites on menin, if robustly supported, could be of interest to the fields of DNA repair and endocrine tumor biology. However, the manuscript as presented has substantial methodological gaps and inconsistencies that prevent the core claims from being adequately evaluated. Key issues include the absence of a clear rationale for selecting only three of thirty docking models, the lack of a quantitative comparison between the two binding sites, the inconsistent reporting of RMSD values in the text versus the figure legend, the absence of a statistical framework for comparing wild-type and mutant binding free energies, and the lack of any experimental or orthogonal computational validation. The claim that this is the "first study" to use configurational entropy in this context is not substantiated by a systematic literature comparison. The manuscript would require major revisions, including additional analyses and clearer presentation, before the conclusions can be considered established.

### Who would be interested in the results, and why
Researchers working on menin biology, multiple endocrine neoplasia type 1 (MEN1) syndrome, DNA damage response pathways involving replication protein A, and computational prediction of protein-protein interaction interfaces would find the results potentially relevant. The identification of specific residues mediating menin-RPA2 binding could inform future mutagenesis studies and potentially guide the design of small molecules targeting this interface. The methodological approach, combining docking, MD, and MM/PBSA with configurational entropy, may also be of interest to computational biologists studying mutation effects on protein complexes.

### Major Strengths
- The biological question is clinically motivated, with the S606F mutation previously identified in a patient cohort.
- The computational workflow integrates multiple established tools (Swiss-Model, PROCHECK, Schrodinger PIPER, GROMACS, g_mmpbsa) in a logical sequence.
- The study attempts to go beyond simple binding free energy calculations by including configurational entropy, which is often neglected.
- The authors acknowledge the lack of experimental validation as a limitation.
- The identification of two distinct binding sites on menin, if confirmed, would be a novel contribution.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Model selection and justification
- **Claim pointer** The authors state that "only 3 complexes (model 8, 28 and 9) were selected for further study on the basis of the highest delta G energy which is − 74.89 kJ/mol, − 92.04 kJ/mol, − 100.4 kJ/mol respectively."
- **Evidence pointer** Results, "Protein-protein docking and binding energy" section; Figure 1 legend
- **Concern** The selection of models 8, 28, and 9 is not adequately justified. The three selected models have delta G values of −74.89, −92.04, and −100.4 kJ/mol, yet the text states these were selected based on "highest delta G energy." It is unclear whether "highest" refers to the most negative values or the largest absolute values. If the most negative values were selected, then model 9 (−100.4 kJ/mol) would be the most favorable, followed by model 28 (−92.04) and model 8 (−74.89). However, the order of presentation in the text is 8, 28, 9, which is not consistent with a ranking by most negative delta G. Furthermore, no information is provided about the distribution of delta G values across all 30 models, the clustering criteria used in PIPER, or whether the three selected models represent distinct binding sites or merely variations of the same interface. The subsequent MD simulations show that model 9 is unstable (positive binding energy), which raises the question of why it was selected in the first place. The authors need to provide a clear, quantitative selection criterion and demonstrate that the three models are meaningfully different.
- **Why it matters** The entire downstream analysis depends on the initial model selection. If the selection is arbitrary or poorly justified, the conclusions about binding sites and mutation effects are not reliable.
- **Resolution test** Provide a table or figure showing the delta G values for all 30 models, the clustering criteria, and a clear statement of the selection threshold. Demonstrate that the three selected models represent distinct binding modes, for example by showing interface residue overlap or structural superposition.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation of homology model
- **Claim pointer** The authors state that "we found Swiss model 3D structure and PDB 2PI2 were within an acceptable quality range and were used as models for further study."
- **Evidence pointer** Results, "Protein homology modeling, preprocessing, and validation" section; Table 1
- **Concern** The validation of the menin homology model is insufficient. Table 1 reports Ramachandran plot statistics (86.9% core, 10.4% allowed, 1.9% generously allowed, 0.8% disallowed) and a G-factor of −0.14, but no other validation metrics are provided. The authors do not report the template used for homology modeling, the sequence identity between the target and template, the QMEAN score (although QMEAN is mentioned in the text as −2.76), or the GMQE value (stated as 0.76). More critically, the authors do not report whether the modeled region (residues 551–612, which are missing in the crystal structure) is structurally reliable. The S606 residue, which is the site of the mutation studied, lies in this C-terminal region. The authors state that AlphaFold was not used because "the structure of menin was not properly modelled because the menin predicted in the AlphaFold database is not properly folded into the native 3D structure," but this claim is not substantiated with any comparison or analysis. The reliability of the model in the region containing the mutation site is critical for the validity of the mutation analysis.
- **Why it matters** The S606F mutation analysis depends entirely on the structural context of residue 606. If the C-terminal region of the menin model is unreliable, the predicted effects of the mutation on binding affinity and entropy are not trustworthy.
- **Resolution test** Provide the template information, sequence identity, and per-residue model quality estimates (e.g., from QMEAN or a similar tool). Show a superposition of the modeled C-terminal region with the AlphaFold prediction and discuss any discrepancies. Ideally, validate the model using a molecular dynamics simulation of the apo protein and compare with experimental data if available.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** MD simulation convergence and quality
- **Claim pointer** The authors state that "the model exhibiting least deviation in 200 ns classical MD simulation, trajectories (200 frames) was subjected to the MM/PBSA-based BFE calculation."
- **Evidence pointer** Methods, "Molecular dynamic simulations study" section; Results, "Molecular dynamic simulation" section; Figure 3 legend
- **Concern** The manuscript does not provide sufficient evidence that the MD simulations reached equilibrium or that the trajectories are converged. The authors report only Cα-RMSD values (5.82 Å for model 8, 6.52 Å for model 9, 5.27 Å for model 28) but do not show RMSD plots over time, RMSF (root mean square fluctuation) profiles, radius of gyration, or other standard convergence metrics. The statement that model 8 "exhibited most negative binding free energy" is based on MM/PBSA calculations, but the authors do not report the number of frames used for the MM/PBSA calculation beyond "200 frames," which is ambiguous (one frame per ns? all frames?). The text mentions that model 8 showed "complete disassociation of P-P complex at the time point of 89th ns–96th ns and 120th ns–130th ns," which suggests the complex is not stable during the simulation. This is a critical issue: if the complex dissociates during the simulation, the binding free energy calculated from the trajectory is not meaningful. The authors need to clarify how the MM/PBSA calculation was performed on a trajectory that includes dissociated states.
- **Why it matters** MM/PBSA calculations are only valid if the complex remains bound throughout the simulation. If the complex dissociates, the calculated binding free energy does not reflect the stability of the bound state. The lack of convergence metrics also raises concerns about the reliability of the reported values.
- **Resolution test** Provide RMSD and RMSF plots for all simulations, show the time evolution of the complex (e.g., distance between the centers of mass of the two proteins), and clarify how the MM/PBSA calculation was performed on trajectories that include dissociated states. If the complex dissociates, consider using a different approach, such as umbrella sampling or metadynamics, to calculate binding free energies.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical analysis of binding free energies
- **Claim pointer** The authors report binding free energies of −205.624 kJ/mol (model 8), −177.382 kJ/mol (model 28), and +223.018 kJ/mol (model 9), and state that "S606F mutation in Menin, plays the vital role in reduction/increase of average RMSD and BFE."
- **Evidence pointer** Table 2; Results, "Binding free energy (BFE) calculation and energy decomposition analysis (EDA)" section
- **Concern** The manuscript does not provide any statistical analysis of the binding free energy differences between wild-type and mutant complexes. Table 2 reports mean values with standard deviations, but no p-values, confidence intervals, or effect sizes are given. The claim that the S606F mutation "plays a vital role" is based on a single comparison of mean values. Given that the standard deviations are relatively large (e.g., ±12.215 kJ/mol for model 8), the difference of −34.09 kJ/mol between wild-type and mutant model 8 may not be statistically significant. Similarly, the difference of −97.54 kJ/mol for model 28 needs to be evaluated for statistical significance. The authors also do not report the number of independent simulations or whether the standard deviations represent block averages or standard errors.
- **Why it matters** Without statistical analysis, the reader cannot assess whether the observed differences are meaningful or within the noise of the computational method. The claim that the mutation has a significant effect on binding is not supported by the evidence as presented.
- **Resolution test** Perform multiple independent MD simulations (at least 3 replicas) for each system and report the mean and standard error of the binding free energy. Use a statistical test (e.g., a two-sample t-test or a bootstrap analysis) to compare wild-type and mutant binding free energies. Report the number of frames used for the MM/PBSA calculation and the block size for error estimation.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Configurational entropy calculation
- **Claim pointer** The authors state that "the configurational entropy of mutant Menin-RPA2 model 28 was found to decreased to 1447.10 (J/mol K) at 61st ns as compared to wild type Menin-RPA2 complex (1642.70 J/mol K)."
- **Evidence pointer** Results, "Configurational entropy calculations" section; Figure 7 legend
- **Concern** The configurational entropy calculation is described only briefly, and the results are reported as single values at a specific time point (61st ns) rather than as a time series or an average over the trajectory. The Schlitter method is mentioned, but the manuscript does not specify how the covariance matrix was calculated, whether the calculation was performed on the complex or on individual proteins, or how the entropy difference between wild-type and mutant was computed. The choice of reporting entropy at a single time point (61st ns) is arbitrary and not justified. The authors also do not report the entropy for the entire trajectory or the convergence of the entropy calculation. The claim that the mutation reduces configurational entropy is based on a single time point comparison, which is not a robust basis for this conclusion.
- **Why it matters** Configurational entropy is a key component of the binding free energy, and the authors use it to support their claim of "extended stability" of the mutant complex. If the entropy calculation is not properly described or is not converged, this claim is not supported.
- **Resolution test** Provide a time series of the configurational entropy for each system, show that the entropy has converged over the simulation, and report the average entropy and its standard error. Describe the calculation in detail, including the number of atoms included, the covariance matrix calculation, and the treatment of translational and rotational degrees of freedom.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Novelty and literature context
- **Claim pointer** The authors state that "this is the first study to highlight the configurational entropy of protein-protein interactions thereby strengthening the prediction of two significant important interaction sites in menin for the binding of RPA2."
- **Evidence pointer** Abstract; Discussion
- **Concern** The claim of being the "first study" is not supported by a systematic literature review. The authors do not cite or discuss previous computational studies on menin-RPA2 interactions, nor do they compare their approach to other studies that have used configurational entropy in protein-protein interaction analysis. The statement in the Discussion that "previous studies were unable to determine the exact amino acid residue of the RPA2 binding site in menin" is not accompanied by a comprehensive review of the relevant literature. The novelty claim should be tempered or substantiated with a thorough comparison to existing work.
- **Why it matters** For a general journal, the novelty of the contribution is a key criterion. If the claim of being the first is not substantiated, the significance of the work is diminished.
- **Resolution test** Provide a more comprehensive literature review in the Introduction and Discussion, explicitly comparing the present findings to previous computational and experimental studies on menin-RPA2 interactions. If other studies have used similar approaches, acknowledge them and clearly state what is new in the present work.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract contains grammatical errors and awkward phrasing, e.g., "It's still remains unclear the specific amino acid residues" and "thereby proposing a viable model of menin-RPA2 interaction." The sentence "Collectively, this is the first study to highlight the configurational entropy of protein-protein interactions thereby strengthening the prediction of two significant important interaction sites" is unclear and contains redundancy ("significant important").
- **Required correction** Revise the abstract for clarity and grammatical correctness. For example, "The specific amino acid residues involved in the menin-RPA2 interaction remain unclear" and "This is the first study to use configurational entropy analysis to predict two important RPA2 binding sites on menin."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure quality and accessibility
- **Affected element** Figures 1–8
- **Evidence pointer** Figure legends
- **Issue** The figure legends are provided, but the actual figure images were not available for review. Based on the legends, Figures 3 and 7 appear to be complex multi-panel figures that may be difficult to interpret. Figure 3 is described as showing "Cα-RMSD of three different model complex" and "Protein viz contribution to Cα-RMSD and convergence from wild type to mutated models," which is unclear. The figures should be self-explanatory and accessible to a broad readership.
- **Required correction** Ensure that all figures are clearly labeled, with axis labels, legends, and annotations that are legible. Consider simplifying Figure 3 and Figure 7 or splitting them into multiple panels with clear subheadings.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout the manuscript
- **Evidence pointer** Abstract, Results, Discussion
- **Issue** The manuscript uses inconsistent terminology for the same concept. For example, "BFE" and "ΔGbind" are used interchangeably, and "PPI" and "PPi" are both used. The protein is referred to as both "RPA2" and "RPA-2" in different places. This inconsistency makes the manuscript harder to read.
- **Required correction** Use consistent terminology throughout the manuscript. Define abbreviations at first use and use them consistently thereafter.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reference formatting
- **Affected element** Reference list
- **Evidence pointer** Not provided in the manuscript text
- **Issue** The reference list was not provided in the manuscript text. The in-text citations are numbered, but the corresponding references are not visible. This makes it impossible to verify the accuracy and relevance of the cited literature.
- **Required correction** Ensure that the reference list is complete and correctly formatted according to the journal's style.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Supplementary material organization
- **Affected element** Supplementary Information section
- **Evidence pointer** Supplementary Information section
- **Issue** The Supplementary Information section is confusing. It states "N/A" followed by "Supplementary Information" and then a link. The supplementary material is referenced in the text (e.g., Supplementary Fig. S1, S2, S3, S4, and Annexure S1), but the organization and content of the supplementary material are not clearly described.
- **Required correction** Provide a clear list of supplementary files and their contents. Ensure that all supplementary figures and tables are referenced in the main text.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Software and tool versions
- **Affected element** Methods section
- **Evidence pointer** Methods, "Protein homology modeling, preprocessing and validation" section
- **Issue** The manuscript mentions the use of Schrodinger Maestro version 2020-3, but does not provide version information for other software tools, such as Swiss-Model, GROMACS, and g_mmpbsa. The specific parameters used for docking (e.g., PIPER settings) and MD simulations (e.g., thermostat, barostat, integration time step) are not described in sufficient detail for reproducibility.
- **Required correction** Provide complete software and version information, and describe all relevant simulation parameters in the Methods section.

### Technical failings that need to be addressed before the case is established
- R1-M1: Model selection criteria are not clearly defined or justified.
- R1-M2: Homology model validation is incomplete, particularly for the C-terminal region containing the mutation site.
- R1-M3: MD simulation convergence is not demonstrated, and the reported dissociation of the complex during simulation undermines the validity of the binding free energy calculations.
- R1-M4: No statistical analysis is provided for the binding free energy comparisons between wild-type and mutant complexes.
- R1-M5: The configurational entropy calculation is not described in sufficient detail and is reported at a single arbitrary time point.

### Assessment against Nature-style criteria
- **Originality** The manuscript addresses a specific and clinically relevant question, and the use of configurational entropy in this context is a potentially interesting methodological contribution. However, the claim of being the "first study" is not substantiated, and the overall approach (docking, MD, MM/PBSA) is standard in the field. The originality is therefore moderate and would need to be more clearly articulated.
- **Scientific importance** The menin-RPA2 interaction is relevant to DNA repair and tumor suppression, and understanding the effect of the S6 06F mutation could have implications for MEN1 syndrome. However, the study is purely computational, and the authors themselves acknowledge the lack of experimental validation. The importance of the findings is therefore limited by the absence of experimental confirmation.
- **Interdisciplinary readership** The topic is of interest to researchers in endocrinology, cancer biology, and computational biology. However, the manuscript is written in a way that assumes significant familiarity with molecular dynamics simulations and MM/PBSA calculations, which may limit its accessibility to a broader readership. The abstract and introduction could be revised to make the significance of the work clearer to non-specialists.
- **Technical soundness** The technical soundness is currently not established due to the issues identified above, particularly the lack of model selection justification, incomplete model validation, insufficient evidence of MD convergence, and the absence of statistical analysis. The reported dissociation of the complex during simulation is a major concern that needs to be addressed.
- **Readability for nonspecialists** The manuscript is generally readable but contains grammatical errors and inconsistent terminology. The figures, based on the legends, appear to be complex and may be difficult for non-specialists to interpret. The Discussion could be improved by providing more context for the biological significance of the findings.

### Recommendation posture
Currently not established from the provided evidence. The manuscript addresses a relevant question and the computational workflow is reasonable in principle, but the methodological gaps and the lack of statistical analysis prevent the core claims from being adequately supported. Major revisions are required, including a clear justification of model selection, more thorough model validation, evidence of MD convergence, statistical analysis of binding free energies, and a more detailed description of the configurational entropy calculation. If these issues are addressed, the manuscript could potentially be suitable for publication, but in its current form, the conclusions are not supported by the evidence presented.

## Risk / unsupported claims
- The claim that "this is the first study to highlight the configurational entropy of protein-protein interactions" is unsupported by a systematic literature review.
- The claim that the S606F mutation "plays the vital role in reduction/increase of average RMSD and BFE" is not supported by statistical analysis.
- The claim that "the S606F mutation in Menin might lead reduction in Menin-RPA2 flexibility and backbone deviation, thereby facilitating very strong binding of Menin-RPA2" is speculative and not directly supported by the data presented.
- The statement that "the menin predicted in the AlphaFold database is not properly folded into the native 3D structure" is made without supporting evidence or comparison.
- The biological interpretation in the Discussion, namely that the S606F mutation "strongly stabilized the extended binding with RPA2, thereby hindering the binding of NF-κB," is speculative and goes beyond the computational data presented.