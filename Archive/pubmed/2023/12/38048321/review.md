## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods summary, results, discussion) without supplementary data or figures
- **Assessment boundary** Scientific claims, methodological soundness, and logical coherence based solely on the provided text; no assessment of supplementary figures, tables, videos, or raw data
- **Shared manuscript claim summary** The authors propose that MDP1, an intrinsically disordered protein, compacts mycobacterial DNA via a "double-sided tape" mechanism in which its IDR electrostatically cross-links adjacent DNA duplexes, thereby inducing a dormant, non-replicating state. They combine HS-AFM imaging with CGMD simulations to support this model.
- **Visible evidence base** Text descriptions of HS-AFM imaging results, gel retardation assays, biolayer interferometry, CGMD simulation outcomes, bacterial growth and viability assays, and electron microscopy
- **Missing materials affecting confidence** All supplementary figures, tables, videos, detailed methods, simulation parameters, and raw quantitative data; the full methods section is not provided in the visible text

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question in mycobacterial biology: how an intrinsically disordered protein mediates DNA compaction to induce dormancy. The combination of HS-AFM and CGMD simulation is innovative and well suited to the problem. The central claim, that MDP1 acts as a monomeric "double-sided tape" cross-linking adjacent DNA duplexes via its IDR, is plausible and supported by the qualitative imaging data described. However, several critical issues limit the strength of the conclusions as presented. The quantitative evidence for key claims (e.g., monomeric state, length-dependent effects, dormancy induction) is not fully visible in the provided text, and the causal link between in vitro DNA compaction and in vivo dormancy requires stronger experimental support. The manuscript is well written and will interest a broad readership, but the case is not fully established from the provided evidence.

- **Who would be interested in the results, and why** Researchers studying mycobacterial persistence, dormancy, and tuberculosis latency will find this work directly relevant. The study also appeals to investigators interested in intrinsically disordered proteins, bacterial nucleoid organization, and the biophysics of protein-DNA interactions. The methodological combination of HS-AFM with CGMD simulation may attract biophysicists and structural biologists. The potential implications for drug development against latent tuberculosis broaden the audience to translational researchers.

- **Major strengths** The study addresses a fundamental question with clinical relevance. The use of HS-AFM for real-time single-molecule observation of IDR-mediated DNA compaction is technically impressive and appropriate. The combination with CGMD simulation provides a mechanistic framework that is testable. The authors carefully consider alternative explanations, such as the role of DNA supercoiling and the potential contribution of HUR dimerization. The cross-species comparison with other bacteria possessing similar polycationic tails adds generalizability.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "monomeric MDP1 bundles two adjacent DNA duplexes side-by-side via IDR" and that this is the primary mechanism of DNA compaction.
- **Evidence pointer** Results section "mIDR bands or tapes two dsDNAs together by the monomer form"; Figure 3; Supplementary Figure S4
- **Concern** The claim that MDP1 acts as a monomer is central to the proposed model, yet the evidence for the monomeric state under the relevant conditions is not fully presented in the visible text. The authors reference SV-AUC and glutaraldehyde cross-linking data, but these are only described qualitatively. The SV-AUC data show approximately 98% monomer for MDP1Mtb, but for MDP1Msm, the major peak is only 71.1% monomer with a substantial dimer fraction (19.8%). The functional significance of this dimer population is not addressed. Moreover, the HS-AFM observations of "1HUR-1TRX" sets are interpreted as monomers, but the resolution limits of HS-AFM for distinguishing monomeric versus dimeric protein complexes on DNA are not discussed.
- **Why it matters** If a significant fraction of MDP1 exists as dimers under physiological conditions, the proposed monomeric "double-sided tape" model may not fully explain DNA compaction. The model's predictive power and its distinction from the dimeric HU mechanism depend on establishing the functional monomeric state.
- **Resolution test** Provide quantitative analysis of the proportion of DNA cross-linking events attributable to monomeric versus dimeric MDP1 in HS-AFM. Show that purified monomeric MDP1 (e.g., via size-exclusion chromatography) retains full DNA compaction activity. Address whether the dimeric fraction contributes to or interferes with the proposed mechanism.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The authors claim that "mIDR induces mycobacterial dormancy" based on growth suppression and viability assays with MDP1 and HU-IDR fusion proteins.
- **Evidence pointer** Results section "mIDR induces mycobacterial dormancy"; Figure 6F-H
- **Concern** The causal link between DNA compaction by mIDR and the induction of dormancy is not fully established. The authors show that mIDR expression suppresses growth and reduces CFU without substantial cell death, which is consistent with dormancy. However, dormancy is a complex phenotype that should be verified by multiple criteria (e.g., metabolic activity, gene expression profiles, resuscitation capacity). The text does not describe whether the "dormant" cells can resume growth upon removal of mIDR expression, which is a defining feature of dormancy. Additionally, the heterogenous expression of the constructs is acknowledged but not controlled for in the interpretation.
- **Why it matters** The clinical relevance of this work depends on the claim that MDP1-mediated DNA compaction induces a reversible dormant state. If the observed growth suppression is due to toxicity or irreversible damage, the model's implications for latent tuberculosis would be weakened.
- **Resolution test** Demonstrate resuscitation of the non-replicating cells upon cessation of mIDR expression. Measure metabolic markers of dormancy (e.g., reduced ATP levels, altered lipid metabolism). Compare the transcriptional profile of mIDR-induced cells with established dormancy models.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor
- **Claim pointer** The authors claim that "DNA compaction is dependent on mIDR length" and that specific truncation mutants show graded activity.
- **Evidence pointer** Results section "mIDR length-dependent DNA compaction and growth suppression"; Figure 5C-D; Supplementary Figure S8
- **Concern** The length-dependent effects are described qualitatively, but the quantitative data (e.g., compaction percentages, binding affinities, growth curves) are not presented in the visible text. The threshold between T155 (56 residues) and T137 (38 residues) appears to be a critical transition, but the structural basis for this threshold is not explained. The relationship between in vitro DNA compaction activity and in vivo chromosome compaction is not quantitatively correlated.
- **Why it matters** The proposed model predicts a specific relationship between IDR length and function. Without quantitative data, it is difficult to assess whether the model is quantitatively predictive or merely qualitatively consistent.
- **Resolution test** Provide quantitative measurements of DNA compaction (e.g., percentage of compacted plasmids, compaction kinetics) for each mutant. Correlate in vitro compaction activity with in vivo chromosome compaction and growth suppression using regression analysis. Explain the structural basis for the length threshold.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Model validation
- **Claim pointer** The authors claim that CGMD simulations "revealed the novel dynamic DNA cross-linking model" and that electrostatic interactions are sufficient to drive compaction.
- **Evidence pointer** Results section "CGMD model of the DNA cross-linking by MDP1 mIDR"; Figure 4
- **Concern** The CGMD simulation is described as supporting the "double-sided tape" model, but the validation of the simulation against experimental data is not described in the visible text. The force field parameters, the representation of the IDR, and the timescales simulated are not provided. The authors do not discuss whether the simulation can distinguish between the proposed model and alternative mechanisms (e.g., DNA bending, bridging by multivalent cations).
- **Why it matters** The simulation is a key pillar of the proposed mechanism. Without proper validation and discussion of limitations, the model remains speculative.
- **Resolution test** Describe the simulation parameters and validation against known IDR behavior. Perform control simulations with mutated or truncated IDRs to test the model's specificity. Compare simulation predictions with quantitative experimental measurements (e.g., binding affinities, compaction kinetics).

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract; Introduction
- **Issue** The term "double-sided tape" is used repeatedly as a mechanistic description. While evocative, it may be misleading, as it implies a static adhesive interaction rather than the dynamic, electrostatic cross-linking described in the text.
- **Required correction** Consider using a more precise term such as "dynamic electrostatic cross-linking" or "IDR-mediated DNA bridging" in the abstract and key conclusions, while retaining "double-sided tape" as a descriptive analogy.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods
- **Evidence pointer** Materials and Methods section "Other methods"
- **Issue** The visible methods section is extremely brief, with most experimental details relegated to supplementary data. This limits the reader's ability to assess the rigor of the experiments.
- **Required correction** Provide a more complete methods summary in the main text, particularly for the HS-AFM imaging conditions, the CGMD simulation parameters, and the statistical analysis of the growth and viability data.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section, comparison with H-NS
- **Issue** The comparison with H-NS is interesting but underdeveloped. The authors note that H-NS forms rigid superhelical scaffolds, whereas MDP1 forms flexible, reversible cross-links. However, the functional implications of this difference for gene regulation and cell survival are not explored.
- **Required correction** Expand the discussion of how the flexible, reversible nature of MDP1-mediated compaction might enable the "resuscitable" phenotype, in contrast to the more rigid H-NS structures.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Generalizability
- **Affected element** Discussion
- **Evidence pointer** Discussion section, final paragraph
- **Issue** The claim that similar polycationic IDRs in other bacteria "could be a common mechanism" is speculative and not supported by direct evidence in this study.
- **Required correction** Soften this claim or provide additional bioinformatic or experimental evidence to support the generalizability.

- **Technical failings that need to be addressed before the case is established** R1-M1 (monomeric state evidence), R1-M2 (causal link to dormancy), R1-M3 (quantitative data for length dependence)

- **Assessment against Nature-style criteria**  
  *Originality*: The study presents a novel mechanistic model for IDR-mediated DNA compaction, which is distinct from previously described HU and H-NS mechanisms. The "double-sided tape" model is original and conceptually interesting.  
  *Scientific importance*: The work addresses a clinically relevant question (mycobacterial dormancy) and provides a potential molecular basis for a key phenotype. The findings could have implications for understanding latent tuberculosis and developing new therapeutics.  
  *Interdisciplinary readership*: The combination of biophysics, structural biology, and microbiology will appeal to a broad audience. The clinical relevance extends the readership to infectious disease researchers.  
  *Technical soundness*: The technical approach is appropriate and innovative, but the visible evidence is insufficient to fully assess the rigor of the methods and the strength of the quantitative claims. The reliance on supplementary data for critical details is a concern.  
  *Readability for nonspecialists*: The manuscript is generally well written and accessible. The use of the "double-sided tape" analogy helps convey the mechanism, though it may oversimplify the dynamic nature of the interaction.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is novel and potentially important, and the methodological approach is well suited to the question. However, the evidence presented in the visible text is insufficient to fully establish the monomeric mechanism, the causal link to dormancy, and the quantitative length-dependent effects. These issues must be addressed with additional data and analysis before the case is convincing.

## Risk / unsupported claims
- The claim that MDP1 acts primarily as a monomer in its functional state is not fully supported by the visible quantitative data; the substantial dimer fraction for MDP1Msm is not adequately addressed.
- The claim that mIDR "induces mycobacterial dormancy" is not fully established; the evidence shows growth suppression and reduced CFU, but the defining features of dormancy (reversibility, metabolic state) are not demonstrated in the visible text.
- The claim that the "double-sided tape" mechanism is "novel" and distinct from other DNA compaction mechanisms is plausible but not rigorously established without quantitative comparison to alternative models.
- The claim that similar polycationic IDRs in other bacteria represent a "common mechanism" is speculative and not supported by direct evidence in this study.
- The quantitative relationship between mIDR length and DNA compaction activity is described qualitatively; the specific threshold between T155 and T137 is not mechanistically explained.
- The CGMD simulation results are described as supporting the model, but the simulation parameters, validation, and limitations are not presented in the visible text, making the simulation's contribution difficult to assess.