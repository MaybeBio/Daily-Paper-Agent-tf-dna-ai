## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods summary, results, discussion) without supplemental files or figures
- **Assessment boundary** Scientific claims, experimental logic, and internal consistency based solely on the provided manuscript text; supplemental figures and methods are referenced but not available for verification
- **Shared manuscript claim summary** The authors propose that neutrophil CD14 is upregulated early in deep vein thrombosis (DVT) via a G-CSF/C/EBPα axis, that this upregulation drives thrombus formation through neutrophil accumulation, NETosis, and procoagulant platelet formation, and that neutrophil-specific CD14 knockdown reduces DVT severity in a flow-restriction model but not in a stasis model
- **Visible evidence base** RNA-seq, TMT proteomics, flow cytometry, ChIP-qPCR, AlphaFold3/DeepPBS predictions, lentiviral shRNA knockdown, IVC stenosis and stasis models, human neutrophil in vitro assays, ELISA, immunohistochemistry, qRT-PCR, western blot
- **Missing materials affecting confidence** Supplemental figures 1-13, supplemental methods, supplemental table, all raw data files, gating strategies, antibody validation details, lentiviral construct maps, and statistical details for several comparisons

## Reviewer

- **Overall assessment** This manuscript addresses a clinically relevant question and identifies a potentially targetable pathway in DVT. The multiomic approach is appropriate and the central observation of CD14 upregulation on neutrophils is plausible. However, the evidence as presented has several gaps that prevent full confidence in the mechanistic claims. The in vivo knockdown data are promising but the specificity and durability of the approach require closer scrutiny. The mechanistic link from CD14 to NETosis and procoagulant platelets is correlative rather than causal in the current text. The differential effect between stenosis and stasis models is interesting but under-interpreted. The human translational data are limited to in vitro stimulation and do not yet establish clinical relevance. Overall, the work is potentially important but the case is not fully established from the provided material.

- **Who would be interested in the results, and why** Vascular biologists, thrombosis researchers, and clinicians managing venous thromboembolism would be interested. The identification of a neutrophil-specific surface receptor as a driver of DVT offers a conceptually new target that could be engaged by existing antibodies or small molecules. The G-CSF/CD14 axis also connects to oncology and hematology communities, given the known prothrombotic effects of G-CSF in patients receiving it for stem cell mobilization. The differential model-specific findings will interest researchers studying flow-dependent versus stasis-dependent thrombosis mechanisms.

- **Major strengths** The study uses an unbiased multiomic approach to identify CD14, which is a strength over candidate-based approaches. The development of a neutrophil-specific knockdown strategy using an MRP8 promoter-driven lentiviral shRNA is technically innovative and addresses the lack of Cd14-floxed mice. The inclusion of both stenosis and stasis models is a thoughtful design that reveals model specificity. The human in vitro data with CD14 blockade provide some translational relevance. The mechanistic exploration of the G-CSF to CD14 to GSDMD pathway is logical and builds on prior literature.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of the knockdown approach
- **Claim pointer** "A single IV dose (2.5 × 10^7 transducing units) was sufficient to achieve ~65% CD14 knockdown up to 2-week in neutrophils whereas monocytes CD14 levels were not affected"
- **Evidence pointer** Figure 3B-C; supplemental Figure 1; location not provided for gating or transduction efficiency
- **Concern** The manuscript claims neutrophil-specific knockdown but the evidence for specificity is incomplete. The MRP8 promoter is described as driving expression, but MRP8 (S100A8) is also expressed in monocytes, and the authors state monocyte CD14 was unaffected. How was this verified? What was the transduction efficiency in neutrophils? Was the knockdown stable beyond 2 weeks? The ~65% knockdown is partial; is this sufficient to draw conclusions about the role of CD14? The vector map is only in supplemental Figure 1, which is not available for review. The authors also state that this approach "circumvent[s] the limitation of lacking Cd14fl/fl mice," but a partial knockdown with potential off-target effects in other MRP8-expressing cells is not equivalent to a genetic deletion.
- **Why it matters** The central therapeutic claim rests on the specificity and efficacy of this knockdown. If the knockdown is not truly neutrophil-specific or if the partial knockdown has off-target effects, the conclusions about CD14 as a driver are weakened. The authors use this tool to make causal claims about CD14 in DVT pathogenesis.
- **Resolution test** Provide transduction efficiency data, demonstrate knockdown specificity across all leukocyte subsets (including monocytes and eosinophils), show duration of knockdown beyond 2 weeks, and include a dose-response or a second independent shRNA sequence to confirm the phenotype is on-target.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal link between CD14 and downstream mechanisms
- **Claim pointer** "CD14 acts as a key signaling hub in neutrophils, promoting activation, NETosis, and the release of prothrombotic factors (like S100A8/A9) through the GSDMD pathway"
- **Evidence pointer** Figure 4A-G; Figure 5A-E; supplemental Figures 10, 13; location not provided
- **Concern** The manuscript shows correlations between CD14 knockdown and reduced NETosis markers, reduced S100A8/A9, and reduced procoagulant platelets, but does not demonstrate causality. The authors do not show that CD14 engagement directly triggers GSDMD cleavage in neutrophils, nor do they rescue the phenotype by adding back S100A8/A9 or by activating GSDMD independently. The in vitro human data show that CD14 blockade attenuates G-CSF and oxPAPC effects, but the pathway from CD14 to GSDMD is not dissected. Is GSDMD cleavage downstream of CD14 or is it a parallel event? The authors mention "GSDMD-dependent, nonlytic form of neutrophil activation" but do not test this with GSDMD inhibitors or Gsdmd-deficient cells.
- **Why it matters** The mechanistic claim is a central part of the paper's novelty. Without direct evidence that CD14 signaling causes GSDMD cleavage and that this is required for the prothrombotic phenotype, the pathway remains speculative. The discussion anticipates this by citing prior work on GSDMD in DVT, but the current data do not establish the link.
- **Resolution test** Use GSDMD inhibitors or Gsdmd-knockout neutrophils in vitro to show that CD14-driven NETosis and S100A8/A9 release require GSDMD. Alternatively, overexpress constitutively active GSDMD in CD14-knockdown neutrophils to rescue the phenotype. Show that CD14 engagement (e.g., with LPS or oxPAPC) directly increases GSDMD cleavage in a time- and dose-dependent manner.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Model specificity and generalizability
- **Claim pointer** "This key differential finding strongly suggests that the role of neutrophil CD14 in venous thrombosis is model-specific and highlights its crucial, nonredundant involvement in the pathobiology of flow-restricted (stenosis) thrombosis, but not in flow-arrest (stasis) thrombosis."
- **Evidence pointer** Figure 3G-I; supplemental Figure 9; location not provided
- **Concern** The differential effect between stenosis and stasis models is presented as a strength, but the interpretation is underdeveloped. The authors do not explain why CD14 would be important in one model but not the other. Is it a matter of hemodynamics, endothelial activation, or the relative contribution of neutrophils versus other cell types? The stasis model data are only in supplemental Figure 9, which is not available. The authors also do not discuss whether the stenosis model is more clinically relevant to human DVT, which typically occurs in valve pockets with complex flow patterns. The claim that CD14 is "crucial" in stenosis but "dispensable" in stasis needs mechanistic explanation.
- **Why it matters** If the therapeutic target is only relevant in one model, the translational potential is narrower. Clinicians need to know which patient populations might benefit. The differential finding could also reveal important biology about how flow conditions affect neutrophil CD14 function.
- **Resolution test** Provide the stasis model data in the main text with full statistical analysis. Discuss potential mechanisms for the differential effect, such as differences in shear stress, endothelial activation, or neutrophil recruitment pathways. Consider testing intermediate flow conditions or using a model with partial flow restriction to map the threshold of CD14 dependence.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Translational relevance
- **Claim pointer** "The conservation of this CD14-mediated pathway was confirmed in human primary neutrophils in our in vitro studies."
- **Evidence pointer** Figure 5A-E; supplemental Figure 13; location not provided
- **Concern** The human data are limited to in vitro stimulation of healthy donor neutrophils with G-CSF and oxPAPC. The authors do not show that neutrophils from DVT patients have elevated CD14, nor do they show that CD14 levels correlate with DVT severity or recurrence. The anti-CD14 antibody used is not described in terms of its epitope, affinity, or potential for clinical development. The concentration used (15 μg/mL) and the timing of pretreatment (30 minutes) are not justified. The authors also do not test whether CD14 blockade affects neutrophil functions beyond NETosis, such as chemotaxis or phagocytosis, which could have implications for infection risk.
- **Why it matters** The title claims CD14 is a "therapeutic target," but the evidence for this is indirect. In vitro blockade in healthy donor cells does not establish that targeting CD14 would be effective or safe in patients. The authors need to show that CD14 is upregulated in human DVT and that its blockade reduces prothrombotic functions in patient-derived cells.
- **Resolution test** Measure CD14 expression on neutrophils from DVT patients versus controls. Test the anti-CD14 antibody in a human whole blood thrombosis model or in a humanized mouse model. Assess the effect of CD14 blockade on neutrophil antibacterial functions to rule out immunosuppression.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 1B; Figure 2C-D; Figure 3B-E,H; Figure 4A-G; Figure 5B,D-E,G,I-J
- **Evidence pointer** Multiple figures; location not provided
- **Issue** The manuscript states "n = 3 (panel B); n = 5 (panels C-F)" for Figure 1, but the statistical tests used for each comparison are not consistently specified. For example, Figure 2C uses "2-way ANOVA followed by Holm-Šídák multiple comparisons" while Figure 2D-G uses "Mann-Whitney test," but it is unclear whether all pairwise comparisons were pre-specified. The number of independent experiments for the human neutrophil studies (Figure 5) is stated as n = 6, but it is not clear whether these are biological or technical replicates.
- **Required correction** Specify the number of independent biological replicates for each experiment, state the statistical test used for each panel, and indicate whether multiple comparisons were corrected. For the human studies, clarify whether neutrophils were from different donors or the same donor across experiments.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Sex and age considerations
- **Affected element** Methods, Mice section
- **Evidence pointer** Methods, Mice; location not provided
- **Issue** The methods state that "Ten- to 12-week-old male C57BL/6J (WT) mice were purchased from The Jackson Laboratory." The use of only male mice is justified by the potential for necrosis of reproductive organs in females, but this limits the generalizability of the findings. DVT incidence and risk differ between sexes in humans, and the therapeutic target may behave differently in females.
- **Required correction** Acknowledge this limitation more explicitly in the Discussion and consider including female mice in at least one key experiment to assess sex differences.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** RNA-seq and proteomics data
- **Evidence pointer** Methods, RNA-seq; Methods, Peptide and protein identification; location not provided
- **Issue** The manuscript does not state where the RNA-seq and proteomics data have been deposited. For a multi-omics study, data availability is essential for reproducibility and for the community to build on the findings.
- **Required correction** Provide accession numbers for the RNA-seq and proteomics data in a public repository (e.g., GEO, ProteomeXchange) and include a Data Availability statement.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality and completeness
- **Affected element** Figure 2E-F
- **Evidence pointer** Figure 2E-F; location not provided
- **Issue** The AlphaFold3 and DeepPBS predictions are presented as a single panel without showing the full structural context or the confidence metrics. The predicted binding motif is shown as a sequence logo, but the statistical significance of the motif match is not provided. The ChIP-qPCR validation (Figure 2G) is convincing, but the computational predictions add limited value without more detail.
- **Required correction** Provide the AlphaFold3 confidence scores (pLDDT) and the DeepPBS prediction confidence. Show the full structural model with the DNA-binding interface highlighted. Include a comparison with known C/EBPα binding motifs to demonstrate specificity.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Abstract, Results, Discussion
- **Evidence pointer** Abstract; Results, Multiomic profiling; Discussion; location not provided
- **Issue** The manuscript alternates between "neutrophil CD14" and "CD14" without consistently specifying the cell type. Given that CD14 is highly expressed on monocytes, this ambiguity is confusing. The title specifies "Neutrophil CD14," but the text sometimes refers to "CD14" generically.
- **Required correction** Use "neutrophil CD14" consistently when referring to the findings, and specify "monocyte CD14" when discussing the lack of effect on monocytes.

- **Technical failings that need to be addressed before the case is established** R1-M1 (knockdown specificity and efficacy), R1-M2 (causal link between CD14 and GSDMD pathway), R1-M3 (mechanistic explanation for model-specific effects)

- **Assessment against Nature-style criteria** 
  - Originality: The identification of CD14 as a neutrophil-specific driver in DVT is novel, and the G-CSF/CD14/GSDMD axis has not been previously described in this context. The use of a neutrophil-specific knockdown approach is innovative. However, the individual components (G-CSF in DVT, CD14 in inflammation, GSDMD in NETosis) have been studied separately, and the novelty lies in the integration.
  - Scientific importance: DVT is a major clinical problem, and current therapies are limited by bleeding risk. A targetable surface receptor on neutrophils could offer a new approach. The differential findings between stenosis and stasis models are important for understanding DVT pathophysiology. However, the clinical relevance is not yet established.
  - Interdisciplinary readership: The work bridges immunology, vascular biology, and thrombosis research. The multi-omics approach and the therapeutic implications would attract readers from multiple fields. The human in vitro data add translational relevance.
  - Technical soundness: The multi-omics approach is sound, and the use of multiple complementary methods (RNA-seq, proteomics, flow cytometry, ChIP-qPCR) is a strength. However, the knockdown approach has unresolved specificity issues, and the causal link to GSDMD is not directly tested. The statistical reporting is incomplete in places.
  - Readability for nonspecialists: The manuscript is generally well-written and the logic is clear. The key findings are presented in a straightforward manner. However, the Discussion is dense and assumes familiarity with NETosis, GSDMD, and thromboinflammation. A brief explanation of these concepts for a broader audience would improve accessibility.

- **Recommendation posture** Supportive if technical concerns are resolved. The central hypothesis is interesting and the multi-omics data are compelling. However, the knockdown specificity and the causal link to GSDMD need to be addressed. The model-specific findings need mechanistic interpretation. If these issues are resolved, this could be a significant contribution to the field.

## Risk / unsupported claims
- The claim that CD14 knockdown is "neutrophil-specific" is not fully supported without transduction efficiency data and demonstration of specificity across all leukocyte subsets
- The claim that CD14 promotes DVT "through the GSDMD pathway" is correlative; no direct test of GSDMD dependence is shown
- The claim that the differential effect between stenosis and stasis models indicates "crucial, nonredundant involvement" in stenosis is an interpretation that requires mechanistic support
- The claim that the findings "offer a highly specific strategy for DVT prevention and treatment" is premature given the limited in vivo data and lack of human DVT patient data
- The statement that "CD14 acts as a key signaling hub" is an overstatement given that the data show association, not causation
- The claim that the lentiviral approach "circumvent[s] the limitation of lacking Cd14fl/fl mice" is not fully justified; a partial knockdown is not equivalent to genetic deletion
- The translational relevance is not established; the human data are from healthy donors, not DVT patients