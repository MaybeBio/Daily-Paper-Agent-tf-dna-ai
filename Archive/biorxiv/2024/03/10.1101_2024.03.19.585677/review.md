## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplemental figure/table legends
- **Assessment boundary** Scientific content, experimental logic, evidence quality, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors report identification of PSB15, a previously uncharacterized 15 kDa protein encoded by integrative filamentous phages, which binds the phage packaging signal (PS) DNA, targets it to the inner membrane via cardiolipin interaction, and is released by thioredoxin (Trx), establishing what they describe as a PS-dependent assembly checkpoint critical for phage assembly and egress
- **Visible evidence base** Suppressor screening data, phage production assays, EMSA binding studies, liposome flotation assays, chromatin immunoprecipitation, live-cell TIRF microscopy, and biochemical characterization of recombinant PSB15 and mutants
- **Missing materials affecting confidence** Full figures and figure legends, supplemental tables S1-S3 with quantitative binding data, supplemental figures S1-S3, movies S1-S7, raw microscopy data, statistical analysis details, and complete strain/plasmid construction information

## Reviewer
- **Overall assessment** This manuscript presents a potentially significant advance in understanding filamentous phage assembly, specifically for integrative filamentous phages that lack canonical Ff assembly components. The identification of PSB15 as a PS-binding protein that mediates membrane targeting and is released by Trx is novel and could redefine the current model of phage assembly. However, several technical concerns and gaps in evidence weaken the current claims. The genetic suppressor screening approach is elegant, and the combination of in vitro biochemistry with in vivo imaging is commendable. The major weaknesses include incomplete quantitative data presentation, lack of direct binding affinity comparisons for key mutants, insufficient controls in some experiments, and overinterpretation of the "checkpoint" concept without direct evidence of regulation or gating. The manuscript would benefit from additional experiments to establish the mechanistic order of events and to demonstrate that the proposed checkpoint is truly regulatory rather than simply a required assembly factor.

- **Who would be interested in the results, and why** Virologists studying filamentous phage biology, particularly those working on integrative phages of Gram-negative pathogens including Vibrio cholerae, Yersinia pestis, and Pseudomonas aeruginosa. Structural biologists interested in protein-DNA interactions and membrane-associated assembly processes. Microbiologists studying host-pathogen interactions where filamentous phages contribute to virulence. Researchers working on phage therapy and phage-derived biotechnological applications would also find the assembly mechanism relevant. The demonstration of a new host protein (Trx) interaction in phage assembly may interest cell biologists studying redox proteins in membrane-associated processes.

- **Major strengths** 
  1. The suppressor screening strategy is well-designed and successfully identifies a novel protein involved in phage assembly
  2. The study addresses a significant gap in knowledge regarding integrative filamentous phage assembly, which has been largely uncharacterized
  3. The combination of genetic, biochemical, and imaging approaches provides multiple lines of evidence
  4. The identification of distinct functional domains within PSB15 (DNA-binding N-terminus, membrane-binding helix 2/C-terminus, Trx-binding linker) is well-supported
  5. The live-cell imaging data provide novel direct observation of phage assembly protein dynamics
  6. The work has broad implications for understanding assembly diversity among filamentous phages

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that PSB15 directly binds to PS DNA with a conformational change, and that suppressor mutations relieve DNA binding specificity constraints
- **Evidence pointer** Figure 2C, 2E, 2G, 3D, 3F, Table S1, Table S2
- **Concern** The EMSA data are described qualitatively, and the Kd,app values are only presented in supplemental tables without clear statistical comparisons. The claim that T7A and T22A "relieve DNA binding specificity constraints" is based on binding to PS(-) DNA, but the quantitative comparison of binding affinities between WT and mutant proteins for both PS and PS(-) DNA is not clearly presented in the main text. The conformational change claim relies on tryptophan fluorescence, but only W10 is monitored, and the interpretation that the blue shift indicates movement to a less polar environment is speculative without structural data or additional biophysical characterization.
- **Why it matters** The central claim of the paper is that PSB15 is a PS-binding protein whose binding specificity is modulated by suppressor mutations. Without clear quantitative binding data with appropriate statistical analysis, the specificity and affinity claims cannot be properly evaluated. The conformational change interpretation is important for the mechanistic model but is currently under-supported.
- **Resolution test** Provide full binding curves with Kd values and error bars for WT and mutant PSB15 proteins against PS, PS(-), and control DNA substrates. Include statistical comparisons. For the conformational change claim, provide additional evidence such as circular dichroism spectroscopy, limited proteolysis, or hydrogen-deuterium exchange to demonstrate structural changes upon DNA binding.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental logic
- **Claim pointer** The authors claim that PSB15 recruits PS DNA to the inner membrane and that this is an essential checkpoint for phage assembly
- **Evidence pointer** Figure 4A, 4B, 4G-4J, 5C, 5D, 5E, 5F, chromatin immunoprecipitation section
- **Concern** The chromatin immunoprecipitation experiment is described but the results are not shown in the main text figures. The claim that PSB15 recruits DNA to the IM is based on co-fractionation of PSB15 with IM markers and liposome binding assays, but the direct demonstration that PSB15 brings DNA to the membrane in cells is missing. The liposome flotation assays show PSB15 binding to cardiolipin-containing liposomes, but the experiment showing PSB15-dependent recruitment of PS DNA to liposomes is only described in Figure 5F without clear quantitative data. The in vivo relevance of the in vitro liposome data is not established.
- **Why it matters** The proposed model depends on PSB15 functioning as a bridge between PS DNA and the membrane. If the DNA recruitment to membranes is not directly demonstrated, the mechanistic model is incomplete. The distinction between PSB15 being required for assembly versus actively recruiting DNA to the membrane is important for the proposed checkpoint function.
- **Resolution test** Show the chromatin immunoprecipitation results with appropriate controls. Provide quantitative data for the liposome recruitment assay showing PSB15-dependent association of PS DNA with liposomes. Ideally, demonstrate in vivo that PSB15 is required for PS DNA localization to the membrane using fluorescence microscopy or biochemical fractionation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation
- **Claim pointer** The authors claim that the PS/PSB15/Trx complex establishes a regulatory phage assembly checkpoint critical for phage infection and life cycles
- **Evidence pointer** Discussion section, Figure 7
- **Concern** The term "checkpoint" implies a regulatory gate that monitors conditions and prevents or allows assembly to proceed. The data presented show that PSB15 is required for assembly and that Trx releases the complex from the membrane, but there is no evidence for regulation, gating, or quality control. The observation that loss of PSB15 or its activities compromises assembly could simply mean that PSB15 is an essential assembly factor, not a checkpoint regulator. The authors do not demonstrate that the assembly process is monitored or that the checkpoint can be bypassed or regulated under different conditions.
- **Why it matters** The "checkpoint" concept is a strong claim that goes beyond the data. If the authors wish to use this terminology, they need to provide evidence for regulatory control, such as conditions that modulate checkpoint activity, evidence that the checkpoint prevents aberrant assembly, or demonstration that the system responds to cellular or environmental signals.
- **Resolution test** Either provide evidence for regulatory function (e.g., conditions that alter checkpoint stringency, evidence that the checkpoint prevents assembly errors) or revise the terminology to describe PSB15 as an essential assembly factor rather than a checkpoint regulator.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical rigor
- **Claim pointer** The authors claim that Trx binding releases PSB15 from the membrane and that this is essential for assembly
- **Evidence pointer** Figure 5D, 5E, 5F, in vivo imaging data
- **Concern** The in vitro data show that Trx reduces PSB15 binding to liposomes, but the mechanism is unclear. The authors suggest that Trx binding to the linker region adjacent to the membrane-binding domain neutralizes positive charges, but this is speculative. The in vivo imaging data show increased dwell time of PSB15 mutants that cannot bind Trx, but the connection between dwell time and assembly function is not directly established. The concentration of Trx used in the in vitro assays (0.1 to 100 μM) spans a wide range, and the physiological relevance of these concentrations is not discussed.
- **Why it matters** The Trx-mediated release mechanism is a key part of the proposed model. Without understanding the mechanism and demonstrating its functional importance, the model remains incomplete. The in vivo dwell time data need to be connected to functional outcomes.
- **Resolution test** Provide mechanistic studies on how Trx binding causes release (e.g., mutagenesis of specific residues in the linker, biophysical characterization of the Trx-PSB15 complex). Demonstrate that Trx binding is required for efficient phage production in vivo using strains with Trx binding-deficient PSB15 mutants.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Completeness
- **Claim pointer** The authors claim that PSB15 is conserved among Xanthomonas and Stenotrophomonas filamentous phages and that the findings redefine the model of integrative filamentous phage assembly
- **Evidence pointer** Figure 2D, Discussion
- **Concern** The conservation analysis is limited to sequence alignment of a small number of phages. The claim that this redefines the model of integrative filamentous phage assembly is broad, given that only one phage system (ϕLf-UK) is studied in detail. The authors do not test whether PSB15 homologs from other phages function similarly, nor do they address the diversity of integrative filamentous phages beyond Xanthomonas and Stenotrophomonas.
- **Why it matters** The broader significance of the findings depends on the generality of the mechanism. Without functional validation in other phage systems, the claim of redefining the model is premature.
- **Resolution test** Either test PSB15 homologs from other phages for functional complementation or DNA binding, or temper the claims about generalizing the model.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "PSB15 interacts with phospholipid cardiolipin via its basic helix and C-terminus" but does not mention the linker region, which is later shown to be important for Trx binding. The abstract also uses the term "checkpoint" without defining it.
- **Required correction** Clarify the domain organization of PSB15 in the abstract and briefly define what is meant by "checkpoint" in this context.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1C
- **Evidence pointer** Figure 1C
- **Issue** The phage production data are presented as fold changes or relative values without clear absolute numbers or statistical details. The y-axis label is not described.
- **Required correction** Provide clear axis labels, absolute values where possible, and statistical test details in the figure legend.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Protein refolding
- **Evidence pointer** Methods, PSB15 purification
- **Issue** The refolding of PSB15 from inclusion bodies is described, but the efficiency of refolding and the confirmation of proper folding are not discussed. The functional activity of refolded protein is assumed based on binding assays.
- **Required correction** Include a statement about refolding efficiency and any quality control measures (e.g., circular dichroism, activity comparison with natively folded protein if available).

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Controls
- **Affected element** EMSA experiments
- **Evidence pointer** Figure 2C, 2E
- **Issue** The EMSA experiments lack clear negative controls showing that PSB15 does not bind to unrelated DNA sequences of similar length and structure.
- **Required correction** Include EMSA experiments with non-specific DNA controls to demonstrate sequence specificity.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Dwell time measurements
- **Evidence pointer** Figure 6
- **Issue** The dwell time measurements are presented as mean values with standard deviations, but the number of cells, number of puncta analyzed, and statistical comparisons between conditions are not clearly described.
- **Required correction** Provide detailed statistical information including sample sizes, statistical tests used, and p-values for all comparisons.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The manuscript does not adequately discuss the relationship between PSB15 and other known phage assembly proteins, particularly the Ff system proteins that are mentioned but not compared in detail. The discussion of Trx in Ff assembly is brief given that this is a key finding.
- **Required correction** Expand the discussion of how PSB15 function compares to and contrasts with Ff assembly proteins, and provide more context on the proposed role of Trx in Ff assembly.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Throughout
- **Issue** The term "packaging signal" is used interchangeably with "PS" and "PS DNA" without consistent definition. The relationship between the PS sequence and the ϕLf-UK genome position is not clearly described.
- **Required correction** Define the packaging signal clearly, including its location in the genome and its proposed secondary structure, and use consistent terminology throughout.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement
- **Evidence pointer** Data availability statement
- **Issue** The data availability statement says "The original contributions presented in the study are included in the article" but does not mention the supplemental materials or any repository for raw data.
- **Required correction** Clarify where raw data, plasmids, and strains will be deposited and provide accession numbers where applicable.

## Risk / unsupported claims
- The "checkpoint" concept is not supported by the data; the evidence shows PSB15 is required for assembly but does not demonstrate regulatory gating or quality control
- The claim that suppressor mutations "relieve DNA binding specificity constraints" is not quantitatively supported without full binding data comparisons
- The conformational change of PSB15 upon DNA binding is inferred from a single tryptophan fluorescence measurement and lacks independent biophysical validation
- The claim that PSB15 recruits PS DNA to the inner membrane in vivo is not directly demonstrated; the chromatin immunoprecipitation results are mentioned but not shown
- The generalization of findings to all integrative filamentous phages is premature given that only one phage system is studied in detail
- The statement that PSB15 is "crucial for encapsidation" is supported by loss-of-function data, but the specific step at which it acts in the assembly pathway is not precisely defined
- The in vivo relevance of the Trx-mediated release mechanism is inferred from in vitro liposome assays and imaging data but not directly linked to phage production efficiency in a quantitative manner