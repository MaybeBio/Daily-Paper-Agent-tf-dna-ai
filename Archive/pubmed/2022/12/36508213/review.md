## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, discussion, supplementary material references)
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text. No external data or unpublished materials were consulted.
- **Shared manuscript claim summary** The authors propose that autoxidated linolenic acid (AL) inhibits aflatoxin (AF) biosynthesis in *Aspergillus flavus* by activating the imizoquin (IMQ) biosynthetic pathway, with the transporter ImqJ serving as a potential receptor for AL. They support this with multiomics data, 13C-labeling flux analysis, thermal proteome profiling, molecular dynamics simulations, and genetic experiments using overexpression and knockout strains.
- **Visible evidence base** Figures 1–6, Tables 1 and S1–S19, supplementary figures S1–S16, as referenced in the text. Specific data values and statistical details are not fully visible in the provided text.
- **Missing materials affecting confidence** Full figure panels with numerical data, statistical test details and effect sizes, raw omics datasets, complete MD simulation parameters and convergence criteria, strain construction details for OE::imqK and ΔimqK, and the full supplementary methods. These are referenced but not provided in the submitted text.

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question in food safety and fungal biology: how oxylipins regulate aflatoxin biosynthesis. The authors present a multi-layered approach combining transcriptomics, metabolomics, proteomics, flux analysis, and computational modeling. The identification of the IMQ pathway as a key mediator of AL-induced AF inhibition is novel and potentially significant. However, several technical concerns and gaps in evidence weaken the current case. The causal link between AL binding to ImqJ and downstream pathway activation is inferred rather than directly demonstrated. The genetic evidence is partially contradictory, and the evolutionary analysis, while interesting, is not fully integrated into the mechanistic model. The manuscript would benefit from clearer statistical reporting and additional functional validation.
- **Who would be interested in the results, and why** Researchers in fungal secondary metabolism, aflatoxin mitigation, food safety, and oxylipin signaling. The work also has applied relevance for agricultural biotechnology and crop protection, as it suggests potential targets for biological control of AF contamination.
- **Major strengths** 1) Comprehensive multiomics approach integrating transcriptomics, metabolomics, lipidomics, and proteomics. 2) Novel identification of the IMQ pathway as a mediator of AL effects. 3) Use of 13C-flux analysis to confirm TCA cycle activation. 4) Integration of computational predictions (MD simulations) with experimental data. 5) Evolutionary analysis adds a comparative dimension.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Causal mechanism
  - **Claim pointer** "AL was found to interact with a transporter (ImqJ) located in the IMQ gene cluster, primarily through hydrophobic interactions" and "ImqJ as a potential AL-interacting receptor protein"
  - **Evidence pointer** Results section "ImqJ as a Potential AL-Interacting Receptor Protein" and "ImqJ Interacted with AL through Hydrophobic Interactions"; Figure 5
  - **Concern** The claim that ImqJ is a receptor for AL is based on thermal proteome profiling (TPP) and MD simulations. However, TPP identifies proteins with altered thermal stability upon ligand binding, which is suggestive but not definitive evidence of direct physical interaction. The MD simulations are computational predictions and do not provide experimental validation of binding. No direct binding assay (e.g., surface plasmon resonance, isothermal titration calorimetry, or pull-down) is presented.
  - **Why it matters** The central mechanistic claim of the paper rests on the AL-ImqJ interaction. Without direct biochemical evidence, the model remains speculative. If ImqJ is not a bona fide receptor, the proposed signaling cascade is unsupported.
  - **Resolution test** Provide direct binding data (e.g., ITC, SPR, or cellular thermal shift assay with a negative control) demonstrating specific AL-ImqJ interaction. Alternatively, show that mutations in the predicted binding pocket abolish AL-mediated effects on IMQ expression and AF production.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Genetic evidence
  - **Claim pointer** "IMQ biosynthesis was negatively correlated with AF production" and "this pathway was critical for AL-mediated inhibition of AF biosynthesis"
  - **Evidence pointer** Results section "IMQ Biosynthesis Was Negatively Correlated with AF Production"; Figure 4A–F
  - **Concern** The data show that OE::imqK completely inhibits AF production, but ΔimqK only partially reduces AL-mediated inhibition (Figure 4E,F). This partial effect suggests that IMQ is not the sole mediator of AL's inhibitory action. The claim that the pathway is "critical" is overstated given the residual inhibition in the knockout strain. Additionally, the growth phenotypes of the mutant strains are not fully described; if OE::imqK or ΔimqK have altered growth, this could confound AF measurements.
  - **Why it matters** The genetic data are the core functional validation. The partial phenotype of ΔimqK indicates that other mechanisms contribute to AL-mediated AF inhibition, which is not adequately discussed. Overstating the role of IMQ weakens the mechanistic model.
  - **Resolution test** Quantify the proportion of AL-mediated inhibition attributable to IMQ. Discuss alternative pathways. Provide growth curves and sporulation data for all strains to rule out indirect effects on AF production.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Statistical rigor
  - **Claim pointer** "Targeted metabolite analyses and qRT-PCR showed that the IMQ biosynthetic pathway was distinctly upregulated"
  - **Evidence pointer** Results sections "AL-Induced Transcriptomic Changes" and "AL Activated the IMQ Biosynthetic Pathway"; Figures 3 and S8
  - **Concern** The manuscript does not report statistical details for the omics and qRT-PCR data. It is unclear how many biological replicates were used for each time point, whether multiple testing corrections were applied to the transcriptomic data, and what the effect sizes and confidence intervals are for the key comparisons. The PCA plots show separation, but the variance explained by each component is not stated.
  - **Why it matters** Without proper statistical reporting, the robustness of the differential expression and metabolite accumulation claims cannot be assessed. This is particularly important given the large number of comparisons in omics datasets.
  - **Resolution test** Provide full statistical methods, including the number of replicates, multiple testing correction methods, and effect sizes for all key comparisons. Include confidence intervals or dispersion measures in the figures.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Evolutionary interpretation
  - **Claim pointer** "genes involved in the IMQ pathway were positively selected in A. oryzae"
  - **Evidence pointer** Results section "IMQ Biosynthesis Was Negatively Correlated with AF Production"; Figure 4G–I; Table S16
  - **Concern** The evolutionary analysis is presented as supporting evidence, but the logic is not fully developed. Positive selection in A. oryzae is interpreted as indicating a role in AF non-production, but positive selection could also reflect other adaptive functions unrelated to AF. The manuscript does not discuss alternative explanations or test whether the positively selected sites affect protein function.
  - **Why it matters** The evolutionary data are used to strengthen the claim that IMQ is functionally important. If the interpretation is flawed, this line of evidence is weakened.
  - **Resolution test** Provide functional validation of the positively selected sites (e.g., site-directed mutagenesis) or discuss alternative selective pressures. Clarify the statistical model used for positive selection detection.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 1E
  - **Evidence pointer** Results section "AL-Induced Transcriptomic Changes"
  - **Issue** The growth specificity index (gsi) is introduced but not clearly defined in the main text. The interpretation of the gsi density plots is not intuitive.
  - **Required correction** Provide a clear definition of gsi in the main text or figure legend, and explain what the density plots show in plain language.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** MD simulation methods
  - **Evidence pointer** Materials and Methods section "MD Simulations"
  - **Issue** The description of the MD simulation setup is incomplete. The force field parameters for AL molecules, the lipid bilayer composition, and the criteria for identifying binding events are not fully specified.
  - **Required correction** Provide complete simulation parameters, including the AL parameterization method, lipid type, salt concentration, and the definition of a "contact" or "binding" event.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Omics datasets
  - **Evidence pointer** Materials and Methods section "Transcriptomics" and "Proteomics"
  - **Issue** The accession numbers for the raw omics datasets are not provided in the text.
  - **Required correction** Provide database accession numbers (e.g., GEO, SRA, PRIDE) for all raw omics data.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Figure 2B
  - **Evidence pointer** Results section "AL Enhanced Primary Metabolism"
  - **Issue** The statement "most of the differentially accumulated primary metabolites were upregulated in AL samples" is vague. It is unclear which classes of metabolites were most affected and whether this pattern was consistent across time points.
  - **Required correction** Provide a breakdown of metabolite classes and specify which time points showed the most significant changes.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Model clarity
  - **Affected element** Figure 6
  - **Evidence pointer** Results section "Proposed Model of AL-Mediated AF Inhibition"
  - **Issue** The proposed model is complex and includes many components. The figure legend does not explain the directionality of all arrows or the evidence supporting each connection.
  - **Required correction** Expand the figure legend to explain each interaction and indicate which connections are directly supported by data versus hypothesized.
- **Technical failings that need to be addressed before the case is established** R1-M1 (direct binding evidence for AL-ImqJ), R1-M2 (partial phenotype of ΔimqK and overstatement of IMQ's role), R1-M3 (incomplete statistical reporting).
- **Assessment against Nature-style criteria**  
  *Originality*: The identification of the IMQ pathway as a mediator of oxylipin effects on AF biosynthesis is novel and not previously reported. The integration of TPP with MD simulations is a creative approach.  
  *Scientific importance*: Aflatoxin contamination is a major global food safety issue. Understanding regulatory mechanisms could lead to new control strategies. The work has clear applied relevance.  
  *Interdisciplinary readership*: The work spans fungal biology, metabolomics, computational biology, and food safety. It would appeal to a broad audience, though the technical depth in each area may limit accessibility.  
  *Technical soundness*: The multiomics approach is generally sound, but the lack of direct binding data for the key claim and incomplete statistical reporting are significant weaknesses. The MD simulations are well-designed but require experimental validation.  
  *Readability for nonspecialists*: The manuscript is clearly written but assumes familiarity with fungal genetics and omics technologies. The model figure helps, but the main text could benefit from a more accessible summary of the proposed mechanism.
- **Recommendation posture** Supportive if technical concerns are resolved. The core hypothesis is interesting and potentially important, but the current evidence does not fully establish the causal mechanism. Direct binding data for AL-ImqJ, a more nuanced interpretation of the genetic data, and complete statistical reporting are required before the claims can be fully accepted.

## Risk / unsupported claims
- The claim that ImqJ is a receptor for AL is not directly supported by experimental binding data; it is inferred from TPP and MD simulations.
- The claim that the IMQ pathway is "critical" for AL-mediated AF inhibition is overstated given the partial phenotype of the ΔimqK strain.
- The evolutionary interpretation that positive selection of IMQ genes in A. oryzae is related to AF non-production is speculative and not functionally validated.
- The proposed model in Figure 6 includes many hypothesized connections that are not all directly supported by the data presented.