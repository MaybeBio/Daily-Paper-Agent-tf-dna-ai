## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, data availability, funding)
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and alignment with stated conclusions. No assessment of formatting or editorial style beyond readability.
- **Shared manuscript claim summary** The authors use microsecond-long atomistic MD simulations to show that sequence-specific DNA flexibility within AP-1 response elements, modulated by 4–6 flanking nucleotides, regulates the stability and specificity of Yap1–DNA complexes, and that this correlates with gene expression levels in a reporter assay.
- **Visible evidence base** MD trajectories (1.1 μs, AMBER14SB/Parmbc1, one Cufix replicate), helical parameter analysis (Curves+), contact analysis, MMPBSA/MMGBSA free energy estimates, analysis of 12 published BZIP–DNA crystal structures, and re-analysis of published expression data (Salin et al., Boer et al.).
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S26) are referenced but not provided. Force field parameters, input PDB files, and MD run details (e.g., thermostat, barostat, integration time step) are not fully described. The MMPBSA/MMGBSA methodology is only briefly mentioned. The exact statistical tests for the expression data re-analysis are not fully specified.

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question: how DNA sequence and flanking context modulate transcription factor binding beyond the core response element. The use of microsecond-scale MD simulations is appropriate and the focus on Yap1, a less-studied AP-1 family member, adds value. The central hypothesis, that flanking sequences modulate the conformational adaptability of the response element and thereby influence binding stability and gene expression, is plausible and mechanistically interesting. However, the evidence presented is largely correlative and derived from a single computational approach. The link between simulated binding stability and measured gene expression is indirect, and the statistical power of the expression data re-analysis is limited. The manuscript would be strengthened by experimental validation (e.g., binding assays with flanking sequence variants) or by more direct quantitative comparison between simulation and experiment. The writing is generally clear, though some mechanistic claims outpace the evidence.
- **Who would be interested in the results, and why** Researchers studying transcription factor–DNA recognition, particularly the BZIP/AP-1 family; computational biologists interested in DNA flexibility and protein–DNA docking; and molecular biologists studying gene regulation and promoter architecture. The findings may also be relevant to those developing predictive models of transcription factor binding.
- **Major strengths** (1) The study addresses a relatively underexplored aspect of TF–DNA recognition: the role of flanking sequences beyond the core response element. (2) The use of microsecond-long MD simulations is state-of-the-art and appropriate for capturing slow conformational transitions. (3) The analysis of helical parameters and contacts is detailed and systematic. (4) The inclusion of a Cufix force field replicate for one system is a good control. (5) The attempt to connect simulation results to gene expression data, while limited, is a valuable step toward biological relevance.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence strength
  - **Claim pointer** The authors claim that "the stability of Yap1–DNA complexes, modulated by the flanking environment, influences the gene expression levels."
  - **Evidence pointer** Results section "Bioinformatics analysis of model genes expression levels", Figure 4, Supplementary Figures S24–S25
  - **Concern** The link between simulated binding stability and gene expression is indirect. The expression data are derived from a published study (Salin et al.) and re-analyzed here, but the analysis is limited to two genes (ATR1 and OYE2) and a small number of promoter variants. The statistical comparison between ATR1 and OYE2 environments is based on very few unique sequence instances (e.g., one for YRE1, one for YRE2). The authors acknowledge this limitation but do not provide a quantitative measure of confidence (e.g., effect size, confidence intervals) for the expression differences. The claim that binding stability "influences" expression levels implies causation, which cannot be established from correlative data.
  - **Why it matters** The central biological conclusion of the manuscript rests on this correlation. Without experimental validation (e.g., mutagenesis of flanking sequences followed by binding and expression assays) or a more robust statistical framework, the claim is not fully supported.
  - **Resolution test** Provide experimental binding data (e.g., EMSA or ITC) for Yap1 binding to response elements with different flanking sequences, and/or measure expression from reporter constructs with systematically varied flanking sequences. Alternatively, perform a more comprehensive statistical analysis of the existing expression data, including confidence intervals and effect sizes, and clearly state the limitations.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors state that "microsecond-long MD simulations are sufficient for the complexed DNA to reach its bioactive conformation starting from B-DNA."
  - **Evidence pointer** Results section "Yap1–DNA contacts", Supplementary Table S2, Figure S5
  - **Concern** The convergence test compares simulations starting from B-DNA with those starting from a crystal-structure-derived DNA conformation. The RMSD values (max 1.8–2.5 Å) are reported as evidence of convergence. However, RMSD alone is a weak metric for conformational convergence, especially for DNA, where local helical parameters can vary significantly without large global RMSD changes. The authors do not report whether the helical parameters (shift, slide, twist) converge to the same values in both sets of simulations. Additionally, only two systems (YRE2–ATR1 and YRE2–OYE2) are tested, and the Cufix replicate is only for one system. The claim that one microsecond is sufficient for all systems is not fully justified.
  - **Why it matters** If the simulations have not fully converged, the observed differences in helical parameters and contacts between systems could be artifacts of insufficient sampling rather than genuine sequence-specific effects.
  - **Resolution test** Report time-series of helical parameters for all systems, showing convergence to stable values. Compare the distributions of shift/slide/twist between B-DNA-initiated and crystal-structure-initiated simulations. Consider extending simulation length or using enhanced sampling methods to confirm convergence.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Evidence strength
  - **Claim pointer** The authors propose that "the described molecular mechanism... allows the transcription factor to regulate the opening of gene promoters and subsequently their firing potentials."
  - **Evidence pointer** Conclusion section, Discussion of twist and supercoiling
  - **Concern** The connection between local DNA flexibility (shift/slide adjustments) and promoter opening/supercoiling is speculative. While the authors cite their previous work on MafB, the current manuscript does not provide direct evidence that Yap1 binding alters DNA supercoiling or promoter opening. The discussion of twist changes and supercoiling is plausible but not supported by data presented here.
  - **Why it matters** This is a significant mechanistic claim that extends beyond the simulation data. If presented as a hypothesis, it should be clearly labeled as such; if presented as a conclusion, it requires experimental support.
  - **Resolution test** Either soften the language to clearly present this as a hypothesis, or provide experimental evidence (e.g., supercoiling assays, promoter opening measurements) linking Yap1 binding to changes in DNA topology.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The authors use MMPBSA/MMGBSA to estimate binding free energies and state that the results "agree with our conclusions that the ATR1 environment is more favourable."
  - **Evidence pointer** Results section "Bioinformatics analysis of model genes expression levels", Supplementary Table S3
  - **Concern** MMPBSA/MMGBSA is known to be highly sensitive to the choice of parameters (e.g., solute dielectric constant, entropy estimation method) and often produces large errors. The authors report high standard deviations (18–23 kcal/mol) but do not provide details on the calculation setup (e.g., number of frames used, entropy calculation method, dielectric constants). Without this information, the reliability of the ΔG estimates is unclear.
  - **Why it matters** The free energy estimates are used to support the conclusion that the ATR1 environment is more favorable. If the calculations are not robust, this support is weakened.
  - **Resolution test** Provide full details of the MMPBSA/MMGBSA calculations, including parameter choices and convergence of the estimates. Consider using more rigorous free energy methods (e.g., FEP or TI) for at least one system to validate the ranking.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Methods section "Molecular dynamics simulations"
  - **Evidence pointer** Methods section, location not provided
  - **Issue** The description of the MD simulation protocol is incomplete. Key parameters such as the thermostat/barostat algorithm, coupling constants, integration time step, and the number of replicates are not stated.
  - **Required correction** Provide a complete description of the simulation protocol, including all relevant parameters and the number of independent simulations performed.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Results section "Bioinformatics analysis of model genes expression levels"
  - **Evidence pointer** Figure 4, Supplementary Figures S24–S25
  - **Issue** The statistical analysis of the expression data is not fully described. The authors mention a Student t-test but do not specify whether it was one- or two-tailed, whether corrections for multiple testing were applied, or how the data were normalized.
  - **Required correction** Provide a clear description of the statistical methods used, including all relevant parameters and any corrections for multiple testing.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Results section "Impact of DNA flanking environment"
  - **Evidence pointer** Figure 3, Supplementary Figures S13–S16
  - **Issue** The description of the helical parameter analysis is dense and difficult to follow. The authors use terms like "shift" and "slide" without clearly defining them for the non-specialist reader.
  - **Required correction** Provide a brief definition of the helical parameters used and a more accessible explanation of their biological significance.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Data availability statement
  - **Evidence pointer** Data availability section
  - **Issue** The data availability statement says that all data are available "upon request," which is not in line with current best practices for computational studies. The simulation trajectories and analysis scripts should be deposited in a public repository.
  - **Required correction** Deposit the simulation input files, trajectories, and analysis scripts in a public repository (e.g., Zenodo, Figshare) and provide a DOI in the manuscript.
- **Technical failings that need to be addressed before the case is established** R1-M1 (correlation vs. causation in expression data), R1-M2 (convergence of MD simulations not fully demonstrated), R1-M4 (MMPBSA/MMGBSA methodology not sufficiently detailed).
- **Assessment against Nature-style criteria**  
  *Originality*: The study addresses a relatively novel question (role of flanking sequences in TF–DNA binding) and uses a state-of-the-art computational approach. However, the concept that DNA flexibility influences TF binding is not entirely new, and the manuscript builds on prior work from the same group.  
  *Scientific importance*: The question of how TFs achieve specificity beyond the core motif is of broad interest. If the conclusions are robust, the findings could have implications for understanding gene regulation and for predictive models of TF binding. However, the current evidence is not strong enough to fully establish the claims.  
  *Interdisciplinary readership*: The topic is relevant to molecular biology, biophysics, and computational biology. The manuscript is written in a way that is largely accessible to these audiences, though some sections (e.g., helical parameter analysis) may be challenging for non-specialists.  
  *Technical soundness*: The MD simulations are well-designed in principle, but the convergence testing and free energy calculations have limitations that need to be addressed. The re-analysis of expression data is statistically weak.  
  *Readability for nonspecialists*: The abstract and introduction are clear, but the results section is dense and would benefit from more accessible explanations of the technical concepts.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an interesting and important question, and the computational approach is appropriate. However, the central claims are not fully established from the provided evidence. The authors should address the convergence testing, provide more detail on the MMPBSA/MMGBSA calculations, and either strengthen the link between simulation and expression data or soften the causal language. Experimental validation would significantly increase the impact of the study.

## Risk / unsupported claims
- The claim that flanking sequences "regulate" gene expression levels via modulation of DNA flexibility is not fully supported; the expression data are correlative and limited to two genes.
- The claim that the proposed mechanism is "universal for BZIP factors" is extrapolated from a single TF (Yap1) and a small set of crystal structures.
- The hypothesis that local DNA flexibility impacts promoter opening and supercoiling is speculative and not directly tested.
- The MMPBSA/MMGBSA free energy estimates are presented as supportive evidence but are not sufficiently validated or described.