## Review setup

- **Input scope** Full manuscript text, including main text, methods, appendices, and figure captions as provided.
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims by presented evidence. No assessment of formatting, grammar, or journal fit beyond Nature-style criteria.
- **Shared manuscript claim summary** The authors claim that conjugating short peptide tails to G2 PAMAM dendrimers transforms them from pH-insensitive DNA-condensing agents into pH-responsive DNA-binding systems, with histidine-containing conjugates showing the strongest pH dependence, and that charge regulation and collective effects play key roles.
- **Visible evidence base** Potentiometric titration data (experimental and simulated), DNA precipitation assays, coarse-grained Langevin dynamics simulations with constant-pH Monte Carlo, potential of mean force calculations, 31P NMR spectra, and supporting figures (Figs. 3–13, 14–17) and tables (Tables 1–5).
- **Missing materials affecting confidence** No raw numerical data for precipitation assays or titrations; no error bars or statistical replicates reported for experimental measurements; no simulation trajectory data or convergence metrics beyond block analysis; no explicit description of how many independent simulations were performed; no details on peptide purity or conjugation efficiency beyond average numbers; no data on dendrimer size distribution or polydispersity effects.

## Reviewer

- **Overall assessment** This manuscript presents a systematic and well-structured investigation of how short peptide conjugation modulates the pH-dependent DNA association and condensation behavior of G2 PAMAM dendrimers. The combination of experimental titrations, precipitation assays, and coarse-grained simulations with charge regulation is appropriate and generally well executed. The central finding, that histidine-containing conjugates exhibit strong pH-dependent condensation while unmodified G2 does not, is interesting and potentially useful for designing pH-responsive gene delivery vectors. However, several technical concerns, particularly regarding the quantitative interpretation of precipitation data, the treatment of phosphate effects, and the extrapolation from single-conjugate simulations to collective condensation behavior, need to be addressed before the case is fully established.

- **Who would be interested in the results, and why** Researchers in gene delivery and non-viral vector design, particularly those working on polycation-based systems and pH-responsive materials. The work also speaks to the broader community studying polyelectrolyte–DNA interactions, charge regulation phenomena, and coarse-grained simulation of biomolecular complexes. The mechanistic insights into how short peptide tails alter the pH sensitivity of dendrimer-mediated DNA condensation could inform rational design of next-generation delivery vehicles.

- **Major Strengths**  
  1. The combination of experimental and computational approaches is complementary and well integrated, with simulations providing molecular-level interpretation of experimental trends.  
  2. The systematic variation of peptide composition (K4S5, H4S5, E4S1H4) allows clear attribution of pH-dependent behavior to specific amino acid residues.  
  3. The inclusion of charge regulation in the simulation model is a significant methodological strength, capturing an effect often neglected in coarse-grained studies.  
  4. The authors are appropriately cautious in distinguishing between single-molecule association (PMF) and collective condensation behavior, acknowledging the limitations of their simulations.

- **Major Concerns**

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence quality and interpretation  
- **Claim pointer** The claim that "DNA condensation by unmodified G2 remains largely insensitive to pH within the studied range" is based on precipitation assays shown in Fig. 4.  
- **Evidence pointer** Fig. 4, Section 3.1  
- **Concern** The precipitation assay data are presented without error bars, statistical replicates, or quantitative metrics (e.g., EC50 values or confidence intervals). The authors state "no significant differences" but provide no statistical test to support this. The slight trend toward reduced condensation at higher pH could be real but underpowered.  
- **Why it matters** The pH-insensitivity of G2 is a key baseline claim against which all conjugate behavior is compared. If this baseline is not robustly established, the central conclusion that peptide conjugation introduces pH sensitivity is weakened.  
- **Resolution test** Provide replicate measurements (at least n=3) with error bars and appropriate statistical analysis (e.g., ANOVA or equivalent) for the precipitation data in Figs. 4, 12, and 13. Report quantitative metrics such as the fraction of DNA precipitated or the r_mol required for 50% condensation.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness of simulations  
- **Claim pointer** The claim that "the interaction strength between conjugates and DNA depends on both peptide composition and pH" is based on PMF calculations from umbrella sampling.  
- **Evidence pointer** Fig. 11, Section 3.3, Appendix C.5  
- **Concern** The PMF calculations are performed for a single conjugate interacting with a fixed, rigid DNA. The authors acknowledge this limitation but do not address whether the PMF differences (e.g., between G2 and G2-K4S5 at pH 5) are statistically significant given the reported uncertainties. No error bars or confidence intervals are shown for the PMF curves. Additionally, the simulation box size and the cutoff for electrostatic interactions are not fully justified for the PMF calculations, particularly given the long-range nature of electrostatic forces.  
- **Why it matters** The PMF results are used to explain the experimental condensation trends. If the PMF differences are within statistical noise, the mechanistic interpretation is not supported.  
- **Resolution test** Provide uncertainty estimates for the PMF curves (e.g., from block averaging or bootstrapping) and demonstrate that the differences between systems are significant. Justify the box size and electrostatic cutoff for the PMF calculations, or show convergence with respect to these parameters.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Interpretation and mechanistic claims  
- **Claim pointer** The claim that "histidine-containing conjugates exhibit the strongest response, with condensation efficiency decreasing markedly as the pH increases" is presented as a key result.  
- **Evidence pointer** Fig. 12, Section 3.4  
- **Concern** The mechanistic explanation for the pH-dependent condensation of histidine-containing conjugates is largely speculative. The authors suggest that neutralized histidine residues contribute little to DNA binding, but the PMF calculations show that G2-H4S5 and G2-E4S1H4 have similar PMF profiles to G2 at pH 7, which does not explain why condensation is so strongly inhibited at this pH. The authors invoke "collective effects" but do not provide any simulation or experimental evidence for these effects.  
- **Why it matters** The central mechanistic claim of the paper, that peptide composition modulates pH-responsive condensation, requires a coherent explanation that connects single-molecule binding to collective condensation behavior. The current explanation is incomplete.  
- **Resolution test** Either provide multi-conjugate simulations that directly probe collective effects, or present additional experimental data (e.g., dynamic light scattering, zeta potential measurements, or atomic force microscopy) that characterize the condensates formed at different pH values and peptide compositions.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Experimental controls and confounding factors  
- **Claim pointer** The claim that "the ionization of G2 dendrimers is strongly affected by both pH and proximity to DNA" is based on simulation results shown in Fig. 3.  
- **Evidence pointer** Fig. 3, Section 3.1  
- **Concern** The simulations predict charge regulation effects, but the experimental titration data for the conjugates (Fig. 6) show poor agreement with simulations, which the authors attribute to phosphate binding. However, the phosphate content is only quantified for the conjugates (Appendix E), not for the free G2 dendrimers used in the pH-insensitivity experiments. If free G2 also retains phosphate, the interpretation of the pH-dependent condensation experiments could be affected.  
- **Why it matters** The discrepancy between simulation and experiment for the conjugates raises questions about the reliability of the simulation predictions for the unmodified G2 system, which are used to support the pH-insensitivity claim.  
- **Resolution test** Quantify phosphate content in free G2 samples as well, and discuss how phosphate binding might affect the precipitation assay results for all systems.

- **Minor Comments**

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity and reproducibility  
- **Affected element** Methods section, Section 2.3  
- **Evidence pointer** Section 2.3  
- **Issue** The precipitation assay description lacks details on the concentration range of dendrimers/conjugates tested, the number of replicates, and the exact protocol for measuring absorbance (e.g., whether samples were centrifuged before measurement, and how the supernatant was handled).  
- **Required correction** Provide a more detailed protocol, including the range of r_mol values tested, the number of independent experiments, and the exact steps for sample preparation and measurement.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Data presentation  
- **Affected element** Fig. 12  
- **Evidence pointer** Fig. 12  
- **Issue** The precipitation curves in Fig. 12 are presented as line plots, which may imply interpolation between discrete data points. It would be clearer to show individual data points with a fitted curve or a stepwise representation.  
- **Required correction** Present the data as scatter plots with a fitted sigmoidal curve or a non-parametric representation, and include error bars if replicates were performed.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Technical detail  
- **Affected element** Section 2.5, Appendix C.1  
- **Evidence pointer** Section 2.5, Appendix C.1  
- **Issue** The simulation model uses a Debye-Hückel approximation for electrostatics, which is known to be less accurate at high ionic strengths or for multivalent ions. The ionic strength is stated as 17 mM, but the presence of divalent phosphate ions in the experimental system is not captured in the simulations.  
- **Required correction** Discuss the limitations of the Debye-Hückel approximation in the context of the experimental conditions, and justify why this level of approximation is sufficient for the qualitative conclusions drawn.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** Section 3.4, last paragraph  
- **Evidence pointer** Section 3.4  
- **Issue** The statement that "the resulting increase in the charge of the DNA-conjugate complexes may enhance their interactions with negatively charged endosomal membranes" is speculative and not directly supported by any data in the manuscript.  
- **Required correction** Either provide supporting evidence or clearly label this as a hypothesis for future work, rather than a conclusion from the present study.

- **Technical failings that need to be addressed before the case is established**  
  R1-M1 (lack of statistical rigor in precipitation assays), R1-M2 (lack of uncertainty estimates for PMF calculations), and R1-M3 (incomplete mechanistic explanation connecting single-molecule binding to collective condensation) are the primary technical issues. These need to be resolved before the central claims of the manuscript can be considered fully supported.

- **Assessment against Nature-style criteria**  
  - **Originality**: The work is original in its systematic comparison of different peptide compositions and its integration of charge regulation into coarse-grained simulations. However, the concept of pH-responsive polycations for gene delivery is not new, and the specific findings, while useful, do not represent a conceptual breakthrough.  
  - **Scientific importance**: The results are of moderate importance to the gene delivery and polyelectrolyte communities. The identification of histidine-containing conjugates as pH-responsive condensing agents is practically relevant, but the mechanistic insights are incomplete, limiting the broader impact.  
  - **Interdisciplinary readership**: The work bridges experimental physical chemistry, computational biophysics, and applied gene delivery. It could appeal to readers across these fields, but the technical depth in each area may limit accessibility to a general interdisciplinary audience.  
  - **Technical soundness**: The experimental and computational methods are generally appropriate, but the lack of statistical rigor in key experiments and the absence of uncertainty estimates in simulations are significant weaknesses that need to be addressed.  
  - **Readability for nonspecialists**: The manuscript is clearly written and the main findings are accessible. However, the methods sections and appendices are dense and may be challenging for readers without a background in simulations or titration analysis. The abstract and introduction are well crafted for a broad audience.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses a relevant problem with a reasonable approach and produces interesting results. However, the lack of statistical rigor in the key experimental measurements, the absence of uncertainty estimates in the simulations, and the incomplete mechanistic explanation for the collective condensation behavior prevent the case from being fully established at this stage. If the authors can address these concerns with additional data and analysis, the manuscript would be suitable for publication in a specialized journal.