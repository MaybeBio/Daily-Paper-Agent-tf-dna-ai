## Review setup
- **Input scope** Full manuscript text (including Introduction, Results, Discussion, Materials and Methods, and supplemental figure/table legends as referenced)
- **Assessment boundary** Scientific soundness, structural and biochemical evidence, consistency of claims with data presented, and suitability for a general microbiology readership
- **Shared manuscript claim summary** The authors report the crystal structure of the CRP-family protein DdrI from Deinococcus radiodurans in the absence of cAMP, showing a fully folded C-helix and an active-like conformation. They report that DdrI binds DNA in a cAMP-independent manner, that cAMP slightly reduces DNA binding, and that Mn2+ enhances DNA binding, particularly to RDRM-mimicking sequences. Molecular dynamics simulations are used to propose a mechanism for Mn2+ enhancement.
- **Visible evidence base** Crystal structure (PDB 8YZ7), SEC elution profile, EMSA gels, MST binding curves, MD simulation analyses, sequence alignments, electrostatic surface potential calculations
- **Missing materials affecting confidence** Supplemental figures and tables (Table S1, S2, S3; Fig. S1, S2) were referenced but not provided in the submitted text. Raw MST traces, full EMSA gel images with molecular weight markers, and MD simulation convergence metrics were not available for assessment.

## Reviewer
- **Overall assessment** This manuscript presents a structurally and biochemically interesting study of a CRP-family regulator from D. radiodurans that appears to have evolved a cAMP-independent activation mechanism. The structural data are of good quality and the observation that the apo form resembles the active conformation of classical CRPs is compelling. However, several quantitative claims, particularly regarding the effects of cAMP and Mn2+ on DNA binding, are not fully supported by the data as presented. The MD simulations are suggestive but not conclusive, and the physiological relevance of the Mn2+ effect remains speculative. The manuscript would benefit from additional experiments to strengthen the mechanistic claims and from clearer presentation of the quantitative binding data.
- **Who would be interested in the results, and why** Researchers studying bacterial transcription regulation, CRP/FNR family proteins, allosteric regulation, and stress response in extremophiles. The work also has relevance for understanding the evolution of allostery in bacterial regulators and for the growing interest in cAMP-independent CRP variants.
- **Major strengths** The crystal structure of DdrI is a valuable addition to the CRP family, and the observation that the apo form adopts an active-like conformation is an important finding. The combination of structural, biochemical, and computational approaches is appropriate. The identification of a Mn2+-sensitive DNA-binding interface is novel and potentially significant for understanding metal-dependent regulation in D. radiodurans.
- **Major Concerns** 
  - R1-M1: The claim that DdrI binds DNA in a cAMP-independent manner is supported, but the quantitative comparison of DNA binding affinity with and without cAMP is not fully convincing. The reported Kd values show only a modest effect of cAMP, and the statistical significance of the difference is not stated.
  - R1-M2: The Mn2+ enhancement of DNA binding is based on a single set of MST experiments and EMSA gels. The magnitude of the effect is large, but the mechanism proposed from MD simulations is not experimentally validated. The claim that Mn2+ acts by neutralizing the negatively charged interface is plausible but not directly tested.
  - R1-M3: The physiological relevance of the Mn2+ effect is speculative. The authors do not demonstrate that Mn2+ concentrations in D. radiodurans cells are in a range that would affect DdrI binding, nor do they show that DdrI binding to RDRM-mimicking sequences occurs in vivo.
  - R1-M4: The structural comparison with ecCRP is informative, but the claim that the DdrI structure "resembles the activated CRP form" is based primarily on the fully folded C-helix. The functional significance of the other structural differences (shortened α2, additional α7) is not discussed in depth.
- **Minor Comments** 
  - R1-m1: The manuscript would benefit from a clearer statement of the number of replicates for each MST measurement and the error bars in Figure 4A.
  - R1-m2: The EMSA experiments in Figure 3D and Figure S2A should include a no-protein control and a competition control with unlabeled DNA to confirm specificity.
  - R1-m3: The MD simulation methods should include a description of how convergence was assessed and how many independent simulations were performed for the second round.
  - R1-m4: The Discussion would benefit from a more explicit comparison of DdrI with other cAMP-independent CRP family members, such as SdrP, to place the findings in a broader evolutionary context.
  - R1-m5: The statement that "ecCRP may well not be typical of the family" is provocative but not fully supported by the data presented. A more nuanced discussion of CRP family diversity would be appropriate.
- **Technical failings that need to be addressed before the case is established** 
  - R1-M1 (quantitative binding data with cAMP)
  - R1-M2 (mechanistic basis of Mn2+ enhancement)
  - R1-M4 (structural basis of the active-like conformation)
- **Assessment against Nature-style criteria** 
  - Originality: High. The finding that a CRP family member can adopt an active conformation without cAMP is novel and challenges the paradigm established by ecCRP.
  - Scientific importance: Moderate to high. The work has implications for understanding the diversity of regulatory mechanisms in the CRP family and for the evolution of allostery. However, the physiological significance of the Mn2+ effect is not established.
  - Interdisciplinary readership: Moderate. The work will appeal primarily to structural biologists and microbiologists. The broader significance for fields such as metal homeostasis or stress response is not fully developed.
  - Technical soundness: Generally good, but with some gaps in the quantitative binding data and MD simulation validation.
  - Readability for nonspecialists: Good. The manuscript is clearly written and the figures are well organized. The Introduction and Discussion provide sufficient context for readers unfamiliar with CRP biology.
- **Recommendation posture** Supportive if technical concerns are resolved. The structural findings are solid and the manuscript is likely to be of interest to the field. However, the quantitative claims regarding cAMP and Mn2+ effects need to be strengthened, and the physiological relevance of the Mn2+ effect should be addressed or tempered.

## Risk / unsupported claims
- The claim that Mn2+ enhances DdrI binding to RDRM-mimicking DNA in a physiologically relevant manner is not supported by in vivo or cellular data.
- The claim that the Tyr113n-Arg55-Glu65 interaction "effectively mimics the cAMP binding" is an interpretation based on structural comparison and is not directly tested.
- The statement that "ecCRP may well not be typical of the family" is an extrapolation from a single example and is not supported by a comprehensive phylogenetic or functional analysis.
- The claim that the additional α7 helix in DdrI may facilitate RNAP prerecruitment is speculative and not experimentally tested.
- The MD simulation results are presented as supporting evidence for the Mn2+ mechanism, but the simulations are not validated by experimental mutagenesis or binding assays with mutant proteins.