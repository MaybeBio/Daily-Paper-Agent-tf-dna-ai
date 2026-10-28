## Review setup
- **Input scope** Full manuscript text (main text, excluding supplementary figures/tables and detailed methods)
- **Assessment boundary** Scientific claims, methodology, evidence consistency, and interpretation as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors propose that phase separation of the TDP-43 C-terminal domain (CTD) is driven by a synergy between site-specific interactions mediated by the conserved region (CR, aa 319-341) and transient interactions involving hydrophobic residues (phenylalanine and methionine) in regions flanking the CR. This claim is supported by atomistic simulations, coarse-grained simulations, and in vitro experiments.
- **Visible evidence base** Main text results sections, figures referenced in text (Fig. 2, 3, 4, 5), methods summary, data availability statement
- **Missing materials affecting confidence** Full methods details, supplementary figures (SI Appendix Figs. S2-S13), supplementary tables (S1-S2), NMR assignment details, simulation parameter details, and experimental protocols are not provided in the supplied material

## Reviewer
- **Overall assessment** This manuscript presents a well-structured and comprehensive investigation into the molecular determinants of TDP-43 CTD phase separation. The authors combine multiple computational and experimental approaches to identify specific residue types that contribute to phase separation and propose a mechanistic model involving synergy between site-specific and transient interactions. The work is technically sound in its execution and the conclusions are largely supported by the evidence presented. However, several concerns regarding the interpretation of simulation results, the generalizability of the proposed mechanism, and the quantitative agreement between computational predictions and experimental observations need to be addressed to fully establish the case.

- **Who would be interested in the results, and why** Researchers studying biomolecular condensates and phase separation, particularly those focused on RNA-binding proteins and low-complexity domains. The findings are also relevant to investigators studying TDP-43 biology and its role in neurodegenerative diseases such as ALS and FTD. The methodological approach combining atomistic and coarse-grained simulations with experimental validation will be of interest to computational biologists and biophysicists working on disordered proteins.

- **Major strengths** The study employs a multi-scale computational approach (atomistic to coarse-grained) that is well-integrated with experimental validation. The identification of methionine as a significant contributor to phase separation expands the current understanding of the molecular grammar of low-complexity domains. The systematic mutation strategy and the use of multiple complementary techniques (simulations, microscopy, sedimentation assays, NMR) provide robust evidence for the main conclusions. The proposed mechanism of synergy between site-specific and transient interactions is conceptually novel and provides a framework for understanding similar systems.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "transient interactions involving hydrophobic residues in CR flanking regions drive the phase separation of CTD through direct enhancement of site-specific, CR-mediated interactions."
- **Evidence pointer** Results sections "Coarse-Grained Simulations Predict the Importance of Nonalanine Aliphatic Residues in TDP-43 CTD Phase Separation" and "Phenylalanine and Methionine Residues Are Crucial for TDP-43 CTD Phase Separation In Vitro"
- **Concern** The claim of a "synergy" between site-specific and transient interactions implies a direct mechanistic coupling between the two types of interactions. However, the evidence presented demonstrates that both types of residues contribute to phase separation, but does not directly show that the transient interactions enhance the site-specific CR-mediated interactions. The experiments show that mutating residues in either region reduces phase separation, but this could be interpreted as an additive effect rather than a synergistic one. The authors do not provide direct evidence of a mechanistic coupling, such as showing that the presence of flanking region interactions increases the affinity or stability of CR-mediated helix-helix contacts.
- **Why it matters** The central claim of the manuscript is the synergistic mechanism. If the evidence only supports an additive contribution of different residue types, the proposed mechanism would need to be revised. This distinction is important for understanding the fundamental principles governing phase separation of low-complexity domains and for designing interventions that target specific interactions.
- **Resolution test** Provide direct experimental or computational evidence showing that the presence of transient interactions in the flanking regions enhances the strength or stability of CR-mediated interactions. This could be achieved through: (1) comparing the free energy of CR-mediated dimerization in the presence and absence of flanking region interactions; (2) using NMR or other biophysical methods to measure changes in CR helix-helix binding affinity when flanking region residues are mutated; or (3) performing simulations that systematically vary the strength of flanking region interactions and measure the effect on CR-mediated contacts.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative agreement
- **Claim pointer** The authors state that "the variation in csat observed for CTD mutants suggests that phenylalanines in the flanking disordered regions and methionine residues present within and outside the CR region significantly contribute to the phase separation of CTD."
- **Evidence pointer** Results section "Coarse-Grained Simulations Predict the Importance of Nonalanine Aliphatic Residues in TDP-43 CTD Phase Separation" and "Phenylalanine and Methionine Residues Are Crucial for TDP-43 CTD Phase Separation In Vitro"
- **Concern** The manuscript reports qualitative agreement between simulation predictions and experimental measurements of csat changes for the mutants tested. However, the quantitative agreement is not systematically assessed. For example, the 6F→A mutation is reported to cause a >six-fold increase in csat in simulations, but the experimental csat is reported as >120 μM (at least six-fold higher than WT at ~20 μM). While the direction of change is consistent, the exact quantitative match is unclear. Similarly, for 5M→AIDR, the simulation predicts a ~two-fold increase in csat, and the experimental data show a similar trend, but the precise values are not compared. A more rigorous quantitative comparison would strengthen the validation of the computational model.
- **Why it matters** The utility of the coarse-grained model for predicting the effects of mutations on phase separation depends on its quantitative accuracy. If the model only captures qualitative trends but not quantitative magnitudes, its predictive power for designing new mutants or understanding disease-associated variants is limited.
- **Resolution test** Provide a direct quantitative comparison between simulation-predicted and experimentally measured csat values for all mutants tested. This could be presented as a table or correlation plot. If quantitative discrepancies exist, discuss their potential sources (e.g., force field limitations, finite size effects, differences in solution conditions) and their implications for the conclusions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors state that "our results suggest that other aliphatic residues except alanine may have similar contributions, expanding the molecular grammar of low-complexity domain phase separation."
- **Evidence pointer** Results section "Phenylalanine and Methionine Residues Are Crucial for TDP-43 CTD Phase Separation In Vitro" and Discussion
- **Concern** The claim that the findings can be generalized to other aliphatic residues and other low-complexity domains is based on limited evidence. The authors tested leucine as a substitute for methionine in one context (5M→LIDR) and found similar csat to WT. However, this is a single substitution test. The generalization to "other aliphatic residues" and to "other low-complexity domains" is an extrapolation that is not directly supported by the data presented. The sequence analysis of other prion-like domains (SI Appendix) is mentioned but not described in detail in the main text.
- **Why it matters** The broader significance of the work depends on whether the identified principles apply to other systems. Overstating the generalizability could lead to incorrect assumptions about other phase-separating systems.
- **Resolution test** Either (1) provide additional experimental or simulation data testing other aliphatic residues (e.g., isoleucine, valine) in the same system, or (2) temper the claim to be specific to the TDP-43 CTD system and note that generalizability to other systems remains to be tested. If the sequence analysis of other prion-like domains is used to support generalizability, provide more details on this analysis in the main text.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic interpretation
- **Claim pointer** The authors state that "the dramatic enhancement of phase separation via helix–helix contacts stabilized through methionine residues in the CR" and that "methionines are important for intermolecular contacts that mediate helical assembly and stabilize the helix."
- **Evidence pointer** Results section "Phenylalanine and Methionine Residues Are Crucial for TDP-43 CTD Phase Separation In Vitro" and "Phenylalanine and Methionine Residues Are Important for CTD Self-Assembly"
- **Concern** The NMR data show that 5M→ACR prevents CR assembly and that the helical content is slightly reduced at some positions. However, the interpretation that methionine residues directly mediate helix-helix contacts is inferred rather than directly demonstrated. The reduced helical content in the mutant could be due to the loss of intra-helical stabilizing contacts rather than inter-helical contacts. The distinction between intra-molecular (stabilizing the helix) and inter-molecular (mediating helix-helix assembly) roles of methionine is not clearly resolved by the data presented.
- **Why it matters** Understanding whether methionine residues play a structural role in stabilizing the helix conformation or a direct role in mediating inter-molecular contacts is important for the mechanistic model. This distinction affects how the synergy between site-specific and transient interactions is conceptualized.
- **Resolution test** Provide additional data that directly distinguishes between intra-molecular and inter-molecular roles of methionine. This could include: (1) measuring the oligomerization state of the 5M→ACR mutant at higher concentrations to determine if assembly is completely abolished or just weakened; (2) performing intermolecular paramagnetic relaxation enhancement (PRE) experiments to directly detect inter-molecular contacts involving methionine residues; or (3) using molecular dynamics simulations to analyze the contact network in the condensed phase and identify whether methionine-methionine contacts are predominantly intra- or inter-molecular.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 2C description
- **Evidence pointer** Results section "Both Aromatic and Aliphatic Residues Contribute toward Single-Chain Compaction"
- **Issue** The text states that "the total number of per-residue contacts summed over bb-sc and sc-sc interaction modes are shown in Fig. 2C" but does not clearly explain how the "one-dimensional" contact map is derived or what the threshold for "high number of contacts" is (greater than mean+σ of Ncontact). The statistical significance of this threshold is not discussed.
- **Required correction** Clarify the derivation of the one-dimensional contact map and provide justification for the choice of threshold (mean+σ). Consider discussing whether alternative thresholds would significantly change the identified key residues.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section
- **Evidence pointer** Methods section
- **Issue** The methods section is extremely brief and refers to SI Appendix for details. While this is common practice, the main text does not provide sufficient information for readers to assess the quality of the simulations (e.g., force field parameters, simulation length, number of replicas for PT-WTE, system size for CG simulations) or the experimental conditions (e.g., protein concentration range, buffer composition, temperature).
- **Required correction** Provide a brief summary of key simulation parameters and experimental conditions in the main text or ensure that the SI Appendix is readily accessible and clearly referenced.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion of methionine oxidation
- **Evidence pointer** Discussion section
- **Issue** The discussion of methionine oxidation as a regulatory mechanism for phase separation is interesting but somewhat speculative. The authors cite studies on other systems (yeast ataxin-2) and mention that TDP-43 CTD phase separation is disrupted by oxidation, but they do not directly test this in their system or discuss how oxidation would affect the specific interactions they identified.
- **Required correction** Either provide direct experimental evidence for the role of methionine oxidation in TDP-43 CTD phase separation or clearly label this as a speculative extension of the findings that requires further investigation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 5C
- **Evidence pointer** Results section "Phenylalanine and Methionine Residues Are Important for CTD Self-Assembly"
- **Issue** The text mentions "Fig. 5C" in the context of secondary structure analysis, but the specific data shown in this panel is not described in detail. It is unclear whether this panel shows the ΔδCα–ΔδCβ values for all residues or only for the CR region.
- **Required correction** Provide a clear description of what is shown in each panel of Figure 5, including the residue range displayed and the specific metric plotted.

- **Technical failings that need to be addressed before the case is established** The primary technical concern is the lack of direct evidence for the synergistic mechanism (R1-M1). The current data support an additive contribution of different residue types but do not demonstrate a direct enhancement of site-specific interactions by transient interactions. Additionally, the quantitative agreement between simulation and experiment (R1-M2) needs to be more rigorously assessed to establish the predictive power of the computational model.

- **Assessment against Nature-style criteria** 
  - **Originality**: The work is original in its identification of methionine as a key contributor to TDP-43 CTD phase separation and in proposing a synergistic mechanism involving both site-specific and transient interactions. This extends the current understanding of the molecular grammar of low-complexity domains.
  - **Scientific importance**: The findings are important for understanding the fundamental principles governing phase separation of disordered proteins, particularly those implicated in neurodegeneration. The identification of specific residues and interaction types that can be targeted for therapeutic intervention has potential translational relevance.
  - **Interdisciplinary readership**: The work bridges computational biophysics, experimental biochemistry, and cell biology, and will be of interest to researchers across these disciplines. The conceptual framework of synergy between different interaction types is broadly applicable.
  - **Technical soundness**: The multi-scale simulation approach is well-executed and appropriately validated against experimental data. The experimental methods (microscopy, sedimentation assays, NMR) are standard and well-established. However, the quantitative agreement between simulation and experiment needs more rigorous assessment.
  - **Readability for nonspecialists**: The manuscript is generally well-written and accessible, with clear explanations of the key concepts. The significance statement provides a good summary for a broad audience. However, some sections (particularly the simulation details) may be challenging for non-specialists.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a valuable contribution to the field with a well-executed multi-scale approach. The main claim of a synergistic mechanism needs to be more directly supported, and the quantitative agreement between simulation and experiment should be more rigorously assessed. If these concerns are addressed, the work would be suitable for publication in a high-impact journal.