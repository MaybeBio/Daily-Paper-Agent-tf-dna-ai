## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results and discussion, conclusions, funding)
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided text. No supplementary figures or tables were available for review.
- **Shared manuscript claim summary** The authors report the characterization of three chemical series of small molecules identified from a high-content screen as inhibitors/disruptors of androgen receptor (AR) protein-protein interactions (PPIs) with the TIF2 coactivator. They propose that these compounds act as negative allosteric modulators (NAMs) of AR, engaging a novel binding pocket (BP-1) adjacent to the orthosteric ligand-binding site or the known BF-3 allosteric pocket, thereby disrupting coactivator recruitment and transcriptional activation, and potentially serving as leads for metastatic castration-resistant prostate cancer (mCRPC) therapy.
- **Visible evidence base** Text descriptions of results from: AR-TIF2 PPI biosensor assays (inhibition and disruption), mammalian two-hybrid (M2H) assays with TIF2 and SRC-1, PSA-luciferase reporter assays in C4-2 cells, PSA expression/secretion western/dot blot assays, H3-DHT radioligand binding assays, TIF2 and AR western blotting CETSA, AlphaScreen AR CETSA, and molecular docking studies. Tables 1-3 and Figures 1-6 are referenced but not provided.
- **Missing materials affecting confidence** All figures and tables, including dose-response curves, IC50/GI50 values, western blot images, CETSA data, and docking poses. Supplementary figures. Statistical details (n, replicates, error bars, statistical tests). Compound purity and structural characterization data. Details of the molecular docking methodology and scoring functions.

## Reviewer
- **Overall assessment** This manuscript describes a substantial body of work characterizing three series of small molecules as putative negative allosteric modulators of the androgen receptor, with the potential to disrupt AR-coactivator interactions relevant to mCRPC. The experimental strategy is logical and the use of orthogonal assays is commendable. However, the manuscript as presented has significant limitations. The absence of all primary data figures and tables makes it impossible to evaluate the quality and robustness of the reported results. Several claims, particularly regarding the proposed mechanism of action (allosteric modulation via BP-1), are not fully supported by the data described. The molecular docking studies appear preliminary and lack validation. The differential cytotoxicity claims are based on a limited set of cell lines without clear statistical analysis. The manuscript would benefit from a more critical interpretation of the data, particularly regarding the distinction between true allosteric modulation and other potential mechanisms such as aggregation, off-target effects, or general cytotoxicity. The writing is dense and at times repetitive, and the introduction could be more focused. Overall, the work is potentially interesting but the current evidence base is insufficient to establish the central claims.
- **Who would be interested in the results, and why** Researchers in the fields of prostate cancer biology, nuclear receptor signaling, and drug discovery, particularly those focused on protein-protein interaction inhibitors and allosteric modulators. The potential to evade resistance mechanisms to current AR-targeted therapies is of high interest to medicinal chemists and translational researchers. The identification of a novel putative binding pocket (BP-1) could also be of interest to structural biologists.
- **Major strengths**
  1. The use of a high-content screening approach to identify PPI modulators is a strength, as it directly targets a therapeutically relevant interaction.
  2. The application of multiple orthogonal assays (biosensor, M2H, reporter, CETSA, binding) to characterize the compounds is a rigorous approach.
  3. The inclusion of AR-V7, a clinically relevant splice variant, in the transcriptional assays is a significant strength.
  4. The demonstration that compounds reduce endogenous and DHT-induced PSA expression and secretion in a relevant CRPC cell line (C4-2) is a valuable functional readout.
  5. The use of CETSA to demonstrate target engagement in cells is a modern and appropriate technique.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality and reproducibility
  - **Claim pointer** The manuscript claims that compounds from three series inhibit AR PPIs with TIF2 and SRC-1, block transcriptional activation, and inhibit growth of AR-positive cell lines with differential cytotoxicity.
  - **Evidence pointer** Figures 1, 2, Tables 1, 2, 3 (location not provided)
  - **Concern** The manuscript references Figures 1 and 2 and Tables 1-3 for the primary quantitative data (IC50, GI50 values) supporting the central claims. However, none of these data are provided in the manuscript text. It is impossible to assess the potency, efficacy, or statistical significance of the reported effects. The dose-response curves, replicate numbers, and error analysis are not visible.
  - **Why it matters** The central thesis of the paper rests on the quantitative potency and selectivity of these compounds. Without access to the primary data, the claims of "low micromolar" or "mid-micromolar" activity cannot be verified. The claim of "differential cytotoxicity" towards AR-positive cell lines is a key piece of evidence for on-target activity, but it cannot be evaluated without the actual GI50 values and statistical comparisons for all five cell lines.
  - **Resolution test** Provide all primary data in the figures and tables. Include full dose-response curves with error bars and statistical analysis for all compounds in all assays. Show the GI50 values for all five cell lines (AR-positive and AR-negative) with appropriate statistical tests to support the claim of differential cytotoxicity.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Mechanistic support
  - **Claim pointer** The manuscript claims that the compounds act as negative allosteric modulators (NAMs) of AR, based on CETSA data showing reduced efficacy and right-shifted EC50 of DHT-enhanced AR thermal stabilization.
  - **Evidence pointer** Figures 4, 5, Supplementary Figures 2, 3 (location not provided)
  - **Concern** The CETSA data are described as showing that compounds "reduced the maximum efficacy and right shifted the EC50 of DHT-enhanced AR thermal stabilization." This is a key piece of evidence for the proposed NAM mechanism. However, the data are not shown. Furthermore, the interpretation is not straightforward. A reduction in maximum efficacy and a rightward shift in EC50 could also be explained by non-specific protein destabilization, compound aggregation, or cellular toxicity at the concentrations used. The manuscript does not describe control experiments to rule out these alternative explanations. The claim that S2-6 blocked DHT-enhanced AR thermal stabilization "below DMSO baseline levels" is particularly concerning and suggests a non-specific effect.
  - **Why it matters** The proposed mechanism of action is the central novelty of the paper. If the CETSA data are not robust and specific, the entire premise of the compounds being allosteric modulators is weakened. The distinction between a true NAM and a non-specific protein destabilizer is critical for the future development of these compounds.
  - **Resolution test** Show the full CETSA data (western blots and AlphaScreen) with proper controls, including a known AR antagonist (e.g., enzalutamide) and a negative control compound. Demonstrate that the compounds do not cause general protein degradation or aggregation at the concentrations used. Provide a quantitative analysis of the EC50 shifts and efficacy changes with statistical significance. Consider using a cellular thermal shift assay with a non-AR protein to demonstrate target specificity.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Structural and computational support
  - **Claim pointer** The manuscript claims that molecular docking studies suggest S1-1 and S2-6 engage a novel binding pocket (BP-1) adjacent to the orthosteric ligand-binding site, while S3-11 occupies the BF-3 allosteric pocket.
  - **Evidence pointer** Figure 6 (location not provided)
  - **Concern** The molecular docking results are presented as a key finding to support the proposed binding sites. However, the methodology is described in a single sentence, and the results are not shown. There is no information on the docking software parameters, the receptor preparation, the ligand preparation, the scoring functions, or the validation of the docking protocol (e.g., redocking of known ligands). The claim of a "novel binding pocket (BP-1)" is a strong statement that requires robust structural evidence, such as mutagenesis studies or co-crystallization, which are not presented.
  - **Why it matters** The identification of a novel binding pocket is a significant claim that would be of high interest to the field. However, computational docking alone, without experimental validation, is insufficient to establish the existence and functional relevance of a new binding site. Overinterpretation of docking poses can mislead future medicinal chemistry efforts.
  - **Resolution test** Provide a detailed description of the docking methodology. Show the docking poses for all three compounds. Validate the docking protocol by redocking a known ligand and comparing the pose to the crystal structure. Most importantly, provide experimental validation of the proposed binding sites, such as site-directed mutagenesis of key residues in BP-1 and BF-3, followed by functional assays.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Data interpretation and alternative mechanisms
  - **Claim pointer** The manuscript claims that the weak activity in the H3-DHT and TIF2 box 3 LXXLL-peptide binding assays suggests that direct antagonism at the orthosteric site or AF-2 surface is unlikely.
  - **Evidence pointer** Figure 2E, 2F, Tables 1, 2, 3 (location not provided)
  - **Concern** The authors interpret the weak activity in the H3-DHT and LXXLL-peptide binding assays as evidence against a direct competitive mechanism. While this is a reasonable interpretation, it is not the only possibility. The compounds could be binding to a different site on the AR-LBD that allosterically affects both DHT and coactivator peptide binding, or they could be acting through an indirect mechanism involving other cellular factors. The manuscript does not discuss these alternative possibilities in sufficient depth. Furthermore, the H3-DHT binding assay is a competition assay, and a compound that binds to an allosteric site could still affect DHT binding through conformational changes, as the authors themselves suggest for the CETSA data.
  - **Why it matters** A thorough understanding of the mechanism of action is critical for compound optimization. If the compounds are not direct competitors but allosteric modulators, their structure-activity relationships (SAR) may be different from what would be expected for competitive antagonists. The manuscript should more carefully consider and discuss alternative mechanisms.
  - **Resolution test** Perform additional experiments to distinguish between competitive and allosteric mechanisms, such as Schild analysis or kinetic binding studies. Test the compounds in a broader panel of AR-related assays, including those that measure AR N/C-terminal interaction, AR-DNA binding, and AR nuclear translocation. Discuss the possibility of off-target effects and include appropriate counter-screens.
  - **Concern ID** R1-M5
  - **Severity** Major
  - **Blocking** No
  - **Axis** Functional relevance and selectivity
  - **Claim pointer** The manuscript claims that compounds inhibited the growth of five prostate cancer cell lines, with many exhibiting differential cytotoxicity towards AR-positive cell lines.
  - **Evidence pointer** Figure 2J, 2K, 2L, Tables 1, 2, 3 (location not provided)
  - **Concern** The claim of differential cytotoxicity is a key piece of evidence for on-target activity. However, the data are not shown. The manuscript does not provide the GI50 values for each cell line, nor does it provide a statistical comparison between AR-positive and AR-negative cell lines. The choice of cell lines is also not fully justified. For example, PC-3 and DU-145 are AR-negative but also have different genetic backgrounds and growth rates compared to AR-positive lines like LNCaP and C4-2. The observed differential cytotoxicity could be due to factors other than AR expression, such as differences in drug metabolism, efflux, or general sensitivity to the compounds.
  - **Why it matters** The selectivity of the compounds for AR-positive cells is important for their potential therapeutic window. If the differential cytotoxicity is not robust or is due to off-target effects, the therapeutic potential of these compounds is significantly reduced.
  - **Resolution test** Show the full dose-response curves and GI50 values for all cell lines. Perform a statistical analysis to demonstrate a significant difference between AR-positive and AR-negative cell lines. Include additional AR-negative cell lines and non-prostate cancer cell lines to assess general cytotoxicity. Consider using isogenic cell line pairs (e.g., PC-3 with and without AR expression) to more directly assess AR-dependent effects.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and completeness
  - **Affected element** Methods section, molecular docking
  - **Evidence pointer** Methods, "Molecular docking studies"
  - **Issue** The description of the molecular docking methodology is extremely brief and lacks critical details. The names of the software packages are mentioned, but the specific parameters, scoring functions, and validation steps are not described.
  - **Required correction** Provide a detailed description of the docking protocol, including receptor and ligand preparation, search algorithms, scoring functions, and any validation steps (e.g., redocking of co-crystallized ligands). This is essential for the reproducibility of the computational results.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Results and discussion, "Inhibition of androgen receptor regulated prostate specific antigen biomarker expression and secretion"
  - **Evidence pointer** Figure 3, Supplementary Figure 1 (location not provided)
  - **Issue** The text describes western blot and dot blot experiments for PSA expression and secretion, but the data are not shown. The description of the quantification method is also brief.
  - **Required correction** Show the representative blots and the quantified data. Provide details on the normalization method (e.g., to β-actin) and the statistical analysis used to compare conditions.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Results and discussion, "Inhibition of AR-V7 splice variant transcriptional activation"
  - **Evidence pointer** Figure 2H, 2I, Tables 1, 2, 3 (location not provided)
  - **Concern** The manuscript states that it is "perhaps surprising" that the compounds inhibit AR-V7 activity since it lacks a ligand-binding domain. The authors suggest a potential mechanism involving disruption of AR-V7 interactions with full-length AR. This is an interesting hypothesis, but it is not tested.
  - **Required correction** Acknowledge that the mechanism of AR-V7 inhibition is not addressed in this study and suggest it as a topic for future investigation. Alternatively, if data are available, include experiments that directly test the proposed mechanism.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Introduction and Discussion
  - **Evidence pointer** Introduction, "Prostate cancer (PC) is the most common solid tumor..."
  - **Issue** The introduction provides a comprehensive overview of prostate cancer and AR signaling, but the discussion of allosteric modulators of AR could be more focused. The authors mention the BF-3 pocket and previous work, but a more detailed comparison with existing AR allosteric modulators would strengthen the novelty claim.
  - **Required correction** Add a more detailed discussion of previously reported AR allosteric modulators, including their mechanisms and limitations, to better contextualize the current findings.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Throughout
  - **Evidence pointer** Abstract, "allosteric modulators"
  - **Issue** The term "allosteric modulator" is used throughout, but the manuscript does not clearly define whether these are positive or negative modulators in the context of AR signaling. The data suggest they are negative modulators, but this is not consistently stated.
  - **Required correction** Use consistent terminology, such as "negative allosteric modulators" (NAMs), throughout the manuscript to clearly convey the proposed mechanism.

## Risk / unsupported claims
- The claim that compounds act as negative allosteric modulators is not fully supported by the data presented. The CETSA data are described but not shown, and alternative explanations for the observed effects are not ruled out.
- The claim of a "novel binding pocket (BP-1)" is based solely on preliminary molecular docking studies without experimental validation. This is a strong claim that requires structural or mutagenesis data.
- The claim of "differential cytotoxicity" towards AR-positive cell lines is not supported by the data shown, as the GI50 values and statistical analyses are not provided.
- The claim that compounds "might evade the resistance mechanisms to existing prostate cancer drugs" is speculative and not directly tested in this manuscript.
- The claim that compounds "reduced the maximum efficacy and right shifted the EC50 of DHT-enhanced AR thermal stabilization" is described but the data are not shown, making it impossible to assess the magnitude or significance of the effect.
- The manuscript states that "S2-6 blocked DHT-enhanced AR thermal stabilization below DMSO baseline levels," which is an unusual finding that could indicate non-specific effects and requires further investigation.

## Assessment against Nature-style criteria
- **Originality** The concept of targeting AR-coactivator PPIs with small molecules is not entirely new, but the identification of a putative novel binding pocket (BP-1) and the focus on allosteric modulation to evade resistance mechanisms adds an element of originality. However, the novelty is diminished by the lack of experimental validation of the proposed binding site.
- **Scientific importance** The work addresses a significant clinical need (mCRPC resistance) and the potential to develop a new class of AR-targeting agents is important. If the claims are substantiated, the findings could have translational relevance. However, the current evidence is insufficient to establish the importance of these specific compounds.
- **Interdisciplinary readership** The topic is of interest to cancer biologists, pharmacologists, and medicinal chemists. The use of diverse techniques (screening, cell biology, biophysics, computational chemistry) could appeal to a broad readership, but the presentation is currently too specialized and lacks the broader context that would make it accessible to a general scientific audience.
- **Technical soundness** The experimental design is generally sound, with the use of orthogonal assays being a strength. However, the lack of primary data, the incomplete description of the docking methodology, and the potential for non-specific effects in the CETSA assays are significant technical weaknesses that need to be addressed.
- **Readability for nonspecialists** The manuscript is dense and uses specialized terminology without sufficient explanation. The introduction is long and could be more focused. The results and discussion are intertwined, which makes it difficult to follow the logical flow. The manuscript would benefit from clearer organization and more accessible language.

## Recommendation posture
Currently not established from the provided evidence. The manuscript presents a potentially interesting set of compounds and a plausible hypothesis, but the evidence base is incomplete. The absence of all primary data figures and tables is a critical issue that prevents a full evaluation. The mechanistic claims, particularly regarding allosteric modulation and the novel binding pocket, require additional experimental support. The manuscript is not suitable for publication in its current form. A revised manuscript that includes all primary data, addresses the alternative mechanisms, and provides experimental validation of the proposed binding sites could be reconsidered.