## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv, 2023)
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text
- **Shared manuscript claim summary** The authors propose that a composite DNA motif ("Coordinator"), comprising an E-box and a homeodomain (HD) binding site, directs cooperative and selective binding between the bHLH factor TWIST1 and multiple HD transcription factors in face and limb mesenchyme. This cooperativity is proposed to integrate cell-type and positional identity programs, shape chromatin accessibility and enhancer activity, and contribute to facial morphology and evolution.
- **Visible evidence base** Results sections, figure legends (Figures 1-7, S1-S6), Materials and Methods, supplementary table descriptions
- **Missing materials affecting confidence** Full figure panels and supplementary figures not viewable; exact statistical values and sample sizes for many comparisons not provided in text; detailed bioinformatics parameters for some analyses not fully described; raw data and code not assessable

## Reviewer
- **Overall assessment** This manuscript presents a compelling and comprehensive investigation into DNA-guided transcription factor cooperativity, a mechanism of gene regulation that is conceptually important but poorly understood in cellular contexts. The authors identify a composite motif, Coordinator, that is specifically enriched in face and limb mesenchyme, and they provide strong evidence that TWIST1 and HD factors cooperatively bind this motif. The combination of genomics, genetics, biochemistry, and structural biology is impressive and generally well-integrated. The major claims are largely supported by the data presented, though several technical and interpretive concerns need to be addressed to fully establish the model. The work is likely to be of broad interest to developmental biologists, gene regulation researchers, and those studying human craniofacial variation.

- **Who would be interested in the results, and why** Developmental biologists studying craniofacial and limb morphogenesis will be interested in the identification of a cis-regulatory grammar that integrates TWIST1 and HD factor function. Researchers in gene regulation and transcription factor biology will be interested in the demonstration of DNA-guided cooperativity as a mechanism for achieving specificity among closely related TFs. Human geneticists studying craniofacial anomalies and normal facial variation will be interested in the links between Coordinator-binding TFs and facial shape heritability. Evolutionary biologists will be interested in the potential role of this mechanism in facial evolution.

- **Major strengths**
  1. The study addresses a fundamental and unresolved question: how TFs with similar DNA-binding specificities achieve distinct regulatory outcomes. The focus on DNA-guided cooperativity is timely and important.
  2. The identification of the Coordinator motif as a specific feature of face and limb mesenchyme is a significant finding, and the multi-species and multi-tissue analysis (ENCODE, mouse embryos, chick) strengthens this conclusion.
  3. The use of an in vitro human ESC-to-CNCC differentiation model, combined with endogenous tagging and degron-based depletion, is a powerful approach to study TF function in a relevant, genetically tractable system.
  4. The combination of genomics (ChIP-seq, ATAC-seq, RNA-seq), biochemistry (IP-MS), and structural biology (X-ray crystallography) provides a multi-layered and convincing case for the proposed mechanism.
  5. The connection to human facial shape variation via GWAS and heritability enrichment analyses adds a compelling translational dimension.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Data interpretation
- **Claim pointer** The authors claim that "TWIST1 is required for HD binding and open chromatin at Coordinator sites" and that "HD TFs stabilize TWIST1 occupancy at Coordinator and titrate it away from HD-independent sites."
- **Evidence pointer** Results section "TWIST1 facilitates homeodomain TF binding, chromatin opening, and enhancer activity"; Figures 4, 5
- **Concern** The central claim of a hierarchical relationship, where TWIST1 is the primary pioneer factor and HD factors are secondary stabilizers, relies heavily on the interpretation of acute depletion experiments. The text states that TWIST1 depletion leads to loss of ALX4 binding and chromatin accessibility at Coordinator sites. However, the data presented in the text do not clearly distinguish between a direct requirement for TWIST1 in HD factor binding versus an indirect effect due to loss of chromatin accessibility. The authors should clarify whether the loss of ALX4 binding is a primary effect or a consequence of chromatin closing. Conversely, the claim that HD factors "titrate" TWIST1 away from other sites is based on the observation that TWIST1 binding increases at double E-box sites upon HD loss. This is an interesting model, but the quantitative evidence (e.g., the magnitude of the shift, the number of sites affected) is not fully presented in the text. The authors should provide a more detailed quantitative analysis of the redistribution of TWIST1 binding.
- **Why it matters** The proposed hierarchical and titrative model is a key conceptual advance of the paper. If the evidence is not robust, the model may be overstated. A clear demonstration of the direct versus indirect effects is essential for the validity of the proposed mechanism.
- **Resolution test** The authors should present a more detailed analysis of the acute depletion time course, showing the kinetics of loss of ALX4 binding and chromatin accessibility. They should also perform an analysis of TWIST1 binding redistribution, quantifying the number of sites that gain or lose binding and the correlation with HD factor loss. Ideally, they could perform an in vitro binding assay with purified proteins and DNA to demonstrate direct cooperativity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Data interpretation
- **Claim pointer** The authors claim that "Coordinator guides cooperative and selective binding between the bHLH family mesenchymal regulator TWIST1 and a collective of HD factors associated with regional identities in the face and limb."
- **Evidence pointer** Results section "TWIST1 binds Coordinator across tissues with diverse homeodomain TF expression"; Figures 2, 3
- **Concern** The selectivity of the interaction is a central claim. The authors show that TWIST1 binds Coordinator in tissues with different HD factor repertoires, and that multiple HD factors (ALX1, ALX4, MSX1, PRRX1) can bind at these sites. However, the text does not clearly demonstrate that this is a selective interaction. The key question is: why does TWIST1 not cooperate with HD factors at other composite sites, or why do other bHLH factors not cooperate with HD factors at Coordinator sites? The authors show that NEUROD1 cannot cooperate with ALX4, but this is a single example. The structural data (Figure 6) provides a potential explanation, but the text does not fully explore the specificity determinants. The authors should discuss the potential role of the specific DNA sequence of the Coordinator motif (beyond just the E-box and HD half-sites) in conferring selectivity, and they should ideally test the effect of mutations in the spacer region or flanking sequences.
- **Why it matters** The claim of selectivity is what elevates this from a description of a composite motif to a mechanism for TF specificity. Without a clear demonstration of why this specific combination is selective, the broader implications for gene regulation are weakened.
- **Resolution test** The authors should perform a more systematic analysis of the sequence features of Coordinator that are important for cooperative binding. This could include mutagenesis of the spacer region, testing different E-box and HD half-site combinations, and testing a wider panel of bHLH and HD factors in the in vitro or cell-based assays.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Data interpretation
- **Claim pointer** The authors claim that "Coordinator guides cooperative and selective binding... ultimately shapes facial morphology and evolution."
- **Evidence pointer** Results section "The roles of Coordinator-binding TFs in facial shape variation"; Figure 7
- **Concern** The link to facial morphology and evolution is the most speculative part of the manuscript. The GWAS and heritability enrichment analyses are suggestive, but they are correlative. The text states that loci encoding Coordinator-binding TFs are associated with facial shape variation and that Coordinator-containing regions are enriched for facial shape heritability. However, the text does not provide a direct test of whether variation in the Coordinator motif itself, or in the binding of these TFs, is causally linked to facial shape changes. The evolutionary argument is based on the observation of sequence conservation and the human-chimp enhancer activity differences, but the text does not present a clear evolutionary analysis of the Coordinator motif across species.
- **Why it matters** The claim that this mechanism shapes facial morphology and evolution is a major conclusion that goes beyond the molecular and genomic data. If the link is only correlative, the claim should be tempered.
- **Resolution test** The authors should either provide a more direct test of the causal link (e.g., by introducing a Coordinator mutation into an animal model and assessing facial shape) or temper the conclusion to state that the data are consistent with, but do not prove, a role in facial variation and evolution.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / Readability
- **Affected element** Results section "The 'Coordinator' motif is active specifically in embryonic face and limb mesenchyme"
- **Evidence pointer** Figure 1
- **Issue** The description of the bioinformatics pipeline for identifying Coordinator activity across ENCODE datasets is brief. The criteria for "Coordinator activity" (top 10,000 distal peaks, ranking thresholds) are stated, but the rationale for these specific thresholds is not fully explained.
- **Required correction** Please provide a more detailed explanation of the choice of thresholds and the robustness of the analysis to these choices.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section "TWIST1 binds Coordinator across tissues with diverse homeodomain TF expression"
- **Evidence pointer** Figure 2
- **Issue** The text states that "TWIST1 is the only TF with a known motif that spans both the E-box and the HD motif." This is a strong statement. It is unclear if this is based on a comprehensive search of all known TF motifs or only a subset.
- **Required correction** Please clarify the scope of the motif database used for this analysis and acknowledge potential limitations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results section "Homeodomain TFs cooperate with TWIST1 to open chromatin at Coordinator sites"
- **Evidence pointer** Figure 5
- **Issue** The text mentions that "accessibility effects of the long-term TWIST1 depletion are well correlated with the acute 24 h depletion (r = 0.664)." This correlation is moderate. The text should discuss the potential reasons for the incomplete correlation (e.g., indirect effects, compensatory mechanisms).
- **Required correction** Please add a brief discussion of the factors that might contribute to the incomplete correlation between acute and long-term depletion effects.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity / Readability
- **Affected element** Discussion section
- **Evidence pointer** N/A
- **Issue** The discussion of the structural basis of cooperativity is somewhat brief. The text mentions a "direct contact interface" between TWIST1 and ALX4 loops, but does not describe the nature of this interaction in detail.
- **Required correction** Please expand the discussion of the structural data to explain how the specific contacts mediate cooperativity and how they might be modulated by sequence variation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Materials and Methods, "S-LDSC analysis"
- **Evidence pointer** N/A
- **Issue** The description of the S-LDSC analysis is brief. The text states that "LD scores were created for each annotation... using the 1000G Phase 3 population reference." It is not clear if the analysis was performed using the recommended baseline LD model and if all relevant covariates were included.
- **Required correction** Please provide more details on the S-LDSC parameters and quality control steps.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results section "The roles of Coordinator-binding TFs in facial shape variation"
- **Evidence pointer** Figure 7
- **Issue** The text states that "loci encoding each of the Coordinator-binding TFs analyzed in this study have at least one facial shape associated SNP." It is not clear if these are independent associations or if they are driven by linkage disequilibrium with a single causal variant.
- **Required correction** Please clarify whether the identified SNPs represent independent association signals.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: The direct versus indirect effects of TWIST1 depletion on HD factor binding and chromatin accessibility need to be more clearly distinguished.
  - R1-M2: The molecular basis for the selectivity of the TWIST1-HD cooperativity at Coordinator motifs needs to be more thoroughly explored.
  - R1-M3: The causal link between Coordinator function and facial morphology/evolution is not established; the claims should be tempered or supported by additional data.

- **Assessment against Nature-style criteria**
  - **Originality:** High. The concept of DNA-guided cooperativity as a general mechanism for TF specificity is not new, but the identification of a specific composite motif that integrates bHLH and HD factor function in a developmental context is a novel and significant contribution.
  - **Scientific importance:** High. The work addresses a fundamental question in gene regulation and provides a mechanistic framework that could be broadly applicable. The links to human craniofacial variation and evolution increase its importance.
  - **Interdisciplinary readership:** Moderate to high. The work will be of interest to developmental biologists, molecular biologists, and human geneticists. The structural biology component may appeal to a broader structural biology audience. The clinical and evolutionary implications broaden the potential readership.
  - **Technical soundness:** Generally strong, but with some concerns. The combination of methods is impressive, and the use of endogenous tagging and degron-based depletion is rigorous. However, the interpretation of the depletion experiments (R1-M1) and the selectivity claims (R1-M2) need to be strengthened. The statistical rigor of some analyses (e.g., S-LDSC) should be verified.
  - **Readability for nonspecialists:** The manuscript is well-written and the logic is clear. The abstract and introduction are accessible. However, the results section is dense and may be challenging for nonspecialists. The figures are likely to be complex, but the text does a good job of guiding the reader.

- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are novel and important, and the multi-faceted approach is commendable. However, the key mechanistic claims regarding the hierarchy of TF binding and the selectivity of the cooperativity need to be more rigorously supported. The link to facial morphology and evolution should be either strengthened or presented more cautiously.