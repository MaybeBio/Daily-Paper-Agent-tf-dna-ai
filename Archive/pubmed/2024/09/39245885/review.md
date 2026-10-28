## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, discussion, figure legends not provided)
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided text. Figures and supplementary materials referenced but not directly examined.
- **Shared manuscript claim summary** The authors propose that the IncN plasmid pKM101 relaxase TraI is recruited to the origin-of-transfer (oriT) by the RHH accessory factor TraK through a dynamic interaction involving TraI's C-terminal unstructured domain (TraICTD) wrapping around TraK's C-proximal tetramerization domain. They further propose that upon relaxosome assembly, this contact is disrupted, and TraICTD self-association occurs as a prerequisite for downstream catalytic or substrate engagement functions.
- **Visible evidence base** AlphaFold2/3 structural predictions; His-tag pull-down assays; bacterial two-hybrid (BACTH) assays; in vivo site-directed photocrosslinking with pBPA incorporation; conjugation assays with TraI deletion and truncation variants.
- **Missing materials affecting confidence** Figures 1–4 and all supplementary figures (S1–S5) were not provided; exact numerical data, Western blot images, statistical details, and AlphaFold confidence metrics (pLDDT, PAE) are not directly assessable; plasmid construction details in Table 1 and oligonucleotide sequences in Table 2 are not available.

## Reviewer

- **Overall assessment** The manuscript addresses a significant and understudied aspect of bacterial conjugation: the molecular basis of relaxase recruitment to oriT by accessory factors. The combination of structural prediction and experimental validation is appropriate and the findings are potentially of broad interest to the conjugation and horizontal gene transfer community. However, the evidence as presented in the text alone is incomplete in several respects. The pull-down and crosslinking data are described qualitatively without quantitative support, the AlphaFold confidence metrics are only partially reported, and the functional significance of the TraICTD–TraK interaction is not directly tested beyond deletion phenotypes. The claim that TraICTD self-association is a prerequisite for catalytic function or substrate engagement is speculative and not experimentally addressed. The manuscript is technically sound in its overall approach but the case for the dynamic model would be strengthened by additional functional data, particularly testing whether TraICTD self-association is required for nicking activity or T4CP engagement.

- **Who would be interested in the results, and why** Researchers studying bacterial conjugation, type IV secretion systems, relaxosome assembly, and horizontal gene transfer. The findings are also relevant to those interested in the structure and function of RHH DNA-binding proteins and intrinsically disordered protein regions in protein–protein interactions. The potential to target relaxosome assembly as an anti-resistance strategy adds translational relevance for antimicrobial resistance researchers.

- **Major Strengths**
  - Addresses a poorly understood step in conjugation: how relaxases are recruited to oriT by accessory factors.
  - Combines computational prediction (AlphaFold2/3) with multiple experimental approaches (pull-down, BACTH, photocrosslinking, conjugation assays).
  - The identification of a specific, experimentally validated interface between TraICTD and TraK is a novel contribution.
  - The dynamic model proposing conformational change upon relaxosome assembly is conceptually interesting and testable.
  - The work is clearly written and logically organized.

- **Major Concerns**

  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "TraI's C-terminal unstructured domain (TraICTD) wraps around TraK's C-proximal tetramerization domain" and "TraICTD self-associates as a prerequisite for relaxase catalytic functions or substrate engagement with the transfer channel."
  - **Evidence pointer** Results sections "The TraICTD is predicted to wrap around the TraK αRH tetramerization domain" and "TraICTD–TraK contacts are detected by in vivo site-directed photocrosslinking"; Figures 2, 3, 4
  - **Concern** The central structural claim relies heavily on AlphaFold predictions, but the reported confidence metrics are incomplete. The authors state that the overall complex confidence is low and that only "four AlphaFold2 models with the highest confidence" show the TraICTD–TraK contact. However, the specific pLDDT and PAE values for the interface residues are not reported. Without these, it is difficult to assess whether the predicted interface is reliable. Furthermore, the functional claim that TraICTD self-association is a "prerequisite" for catalytic or substrate engagement functions is not directly tested. The deletion of the CTD abolishes conjugation, but this could be due to protein instability (as the authors themselves note the ΔCTD mutant is poorly detected) rather than a specific functional role of the CTD in self-association or downstream interactions.
  - **Why it matters** The manuscript's central thesis rests on the TraICTD–TraK interface and the functional importance of TraICTD self-association. If the structural prediction is not robustly supported, or if the functional role of the CTD is merely stability-related, the conclusions are substantially weakened.
  - **Resolution test** Provide AlphaFold confidence metrics (pLDDT, PAE) for the TraICTD–TraK interface. Include a direct test of whether TraICTD self-association is required for nicking activity, e.g., by introducing mutations that disrupt self-association without affecting protein stability and testing their effect on conjugation and in vitro nicking. Alternatively, demonstrate that the ΔCTD phenotype is not solely due to protein degradation by expressing the mutant from a stronger promoter or by stabilizing the protein.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** No
  - **Axis** Quantitative evidence
  - **Claim pointer** "TraI's C terminus contributes to protein stability and function" and "Truncation variants deleted of the TraICTD (1–911, 317–911) failed to retain TraK at detectable levels, however, the TraICTD alone (residues 912–1078) retained TraK in the pulldowns."
  - **Evidence pointer** Results section "TraI's C terminus contributes to protein stability and function"; Figures 1, 3, S2
  - **Concern** The pull-down and Western blot data are described only qualitatively. No quantification of band intensities, no replicates, and no statistical analysis are reported. The statement that the ΔCTD mutant is "faintly detected" is ambiguous and could reflect either low expression, instability, or poor antibody accessibility. Similarly, the pull-down results showing TraICTD retention of TraK are not quantified, making it difficult to assess the strength and specificity of the interaction.
  - **Why it matters** The conclusions about which domains mediate TraK binding and the functional importance of the CTD depend on the reliability and reproducibility of these biochemical assays. Without quantitative data, the reader cannot evaluate the robustness of the findings.
  - **Resolution test** Provide quantification of Western blots (e.g., band intensities normalized to loading controls) with error bars from at least three independent experiments. Include statistical tests where appropriate. For the ΔCTD mutant, show that the reduced detection is not due to reduced transcription/translation by measuring mRNA levels or by using a different epitope tag.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Functional relevance
  - **Claim pointer** "In the presence of pKM101 the TraI–TraK complex undergoes a conformational change(s) that disrupts the TraK–TraICTD interaction."
  - **Evidence pointer** Results section "TraICTD–TraK contacts are detected by in vivo site-directed photocrosslinking"; Figures 4, S3
  - **Concern** The loss of crosslinking in the presence of pKM101 is interpreted as a conformational change disrupting the TraICTD–TraK interface. However, an alternative explanation is that the presence of pKM101 alters the stoichiometry or localization of TraI and TraK, or that the plasmid DNA competes for binding. The authors do not rule out these possibilities. Additionally, the observation that the F1040pBMA substitution mutant behaves differently in the presence of pKM101 versus poriT is not fully explained.
  - **Why it matters** The dynamic model proposed in the Discussion depends on this interpretation. If the loss of crosslinking is due to a trivial reason (e.g., reduced protein levels in the presence of pKM101), the model is not supported.
  - **Resolution test** Control for protein levels in the presence and absence of pKM101. Perform crosslinking with a mutant TraK that cannot bind DNA to determine whether DNA binding per se is responsible for the loss of crosslinking. Alternatively, use a biochemical approach (e.g., size-exclusion chromatography) to directly demonstrate a conformational change in the TraI–TraK complex upon DNA binding.

- **Minor Comments**

  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Introduction, last paragraph
  - **Evidence pointer** "Here, we present an AlphaFold model depicting a specific TraK–TraI interaction characterized by wrapping of the largely unstructured TraICTD around TraK's αRH homotetramerization domain."
  - **Issue** The term "αRH" is used inconsistently. In the Introduction it is "αRH", in the Results it is "αRH" and "α-helical rich", and in the Discussion it is "α-helical rich". Please standardize the terminology.
  - **Required correction** Use a single consistent term, e.g., "α-helical-rich domain" or "αRH", throughout the manuscript.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Materials and Methods, Bacterial two-hybrid assay
  - **Evidence pointer** "Detection of protein interactions with the bacterial two-hybrid assay (BACTH) was carried out with the BTH System Kit (EUROMEDEX)] [28]."
  - **Issue** There is a stray closing bracket after "EUROMEDEX" and the reference citation format is inconsistent with the rest of the text.
  - **Required correction** Remove the stray bracket and ensure reference citations are formatted consistently throughout.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion, paragraph 2
  - **Evidence pointer** "It is enticing to suggest that CTDs associated with TraIKM and TraIF and other relaxases of the MobF family function generally to coordinate assembly of relaxosomes..."
  - **Issue** The word "enticing" is informal and subjective. The speculation is reasonable but should be framed more objectively.
  - **Required correction** Replace "enticing" with a more neutral phrase, e.g., "It is plausible" or "It is tempting to speculate".

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Results section "TraI's C terminus contributes to protein stability and function"
  - **Evidence pointer** "A deletion of the LD strongly attenuated TraI function as assessed by mating assays, and the ΔLD mutant protein was abundantly detected by immunostaining (Fig. 1B, C)."
  - **Issue** The conjugation assay data are reported as "strongly attenuated" without numerical values or statistical analysis in the text. It is unclear whether the effect is partial or complete.
  - **Required correction** Provide quantitative transfer frequencies (e.g., transconjugants per donor) with standard deviations and p-values in the text or figure legend.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Incomplete AlphaFold confidence metrics and lack of direct functional test for TraICTD self-association requirement.
  - R1-M2: Lack of quantitative data for pull-down and Western blot experiments.
  - R1-M3: Alternative explanations for loss of crosslinking in the presence of pKM101 not excluded.

## Risk / unsupported claims
- The claim that TraICTD self-association is a "prerequisite for relaxase catalytic functions or substrate engagement with the transfer channel" is not directly supported by the data presented. The deletion phenotype could be due to protein instability.
- The claim that "conformational changes disrupt this contact" upon relaxosome assembly is inferred from loss of crosslinking but alternative explanations (e.g., competitive binding, altered stoichiometry) are not ruled out.
- The generalization of the TraK–TraI interaction model to other RHH factor–relaxase pairs (Discussion) is speculative and not experimentally tested.
- The statement that "TraK directs formation of a stable TraJ–TraB complex" (Introduction) is presented without citation or data in this manuscript; it is unclear if this is from prior work or new findings.