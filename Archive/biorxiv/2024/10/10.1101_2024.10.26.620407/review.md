## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, supplemental figure/table legends as referenced)
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text. No assessment of editorial fit or journal-specific policy.
- **Shared manuscript claim summary** The manuscript reports that UPF2, a core nonsense-mediated mRNA decay (NMD) factor, binds nucleic acids preferentially as single-stranded RNA (ssRNA) via its MIF4G domains 1 and 3, exhibits RNA unfolding and annealing activities, undergoes conformational compaction upon ssRNA binding, and that these activities are maintained in the presence of UPF1 and UPF3B, supporting a role for UPF2 in mRNP remodeling during NMD.
- **Visible evidence base** EMSA, fluorescence anisotropy, fluorescence spectroscopy (molecular beacon), circular dichroism spectroscopy, negative-stain electron microscopy with 2D class averaging, and computational structure prediction (AlphaFold2, Rosetta Relax, RNA folding algorithms). Figures referenced: 1, 2, 3, 4, 5, 6; Supplemental Figures S1–S8; Supplemental Table S1.
- **Missing materials affecting confidence** Raw quantification data for EMSA band intensities, anisotropy binding curves with replicates and error analysis, statistical tests for Kd comparisons, negative-stain EM particle counts and resolution estimates, and full methods details for fluorescence spectroscopy and CD data processing. No source data files or uncropped gel images were provided.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant gap in NMD biology by characterizing UPF2’s nucleic acid binding properties. The authors present a systematic domain-level analysis and identify a novel RNA remodeling activity for UPF2. However, several key claims, particularly regarding RNA unfolding versus annealing, the specificity of the observed conformational changes, and the functional relevance of the proposed mechanism, are not fully supported by the data as presented. The evidence is suggestive but incomplete, and the manuscript would benefit from additional quantitative analyses and controls.
- **Who would be interested in the results, and why** Researchers studying NMD mechanisms, RNA-binding proteins, RNA helicases and mRNP remodeling, and those interested in the structural dynamics of multi-domain RNA-binding factors. The findings may also be relevant to those investigating UPF2 mutations in genetic disorders and cancer.
- **Major strengths** 1. Systematic domain-level dissection of UPF2 nucleic acid binding using multiple complementary biophysical methods. 2. Identification of a previously uncharacterized RNA annealing activity for MIF4G-D3. 3. Demonstration of UPF2-induced conformational changes in RNA and protein using orthogonal approaches (EMSA, fluorescence, CD, EM). 4. Contextualization of findings within the NMD pathway and existing literature on UPF1 helicase regulation.
- **Major Concerns** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (RNA unfolding vs. annealing ambiguity), R1-M2 (lack of quantitative rigor in Kd determinations), R1-M3 (insufficient evidence for functional relevance), R1-M4 (EM data interpretation and presentation).
- **Assessment against Nature-style criteria** **Originality:** Moderate. The finding that UPF2 binds RNA is not entirely new, but the identification of specific domains, the annealing activity, and the conformational compaction upon ssRNA binding provide novel elements. **Scientific importance:** Moderate to high. Understanding UPF2’s RNA interactions could refine models of NMD activation and mRNP remodeling. However, the direct functional impact of the observed activities on NMD remains speculative. **Interdisciplinary readership:** Moderate. The work will appeal primarily to RNA biology and NMD specialists; the biophysical methods are standard within the field. **Technical soundness:** The methods are generally appropriate, but the lack of quantitative rigor and the ambiguity in interpreting the EMSA results weaken the technical foundation. **Readability for nonspecialists:** The manuscript is clearly written and the logic is easy to follow, though some specialized terminology is used without full explanation.
- **Recommendation posture** Supportive if technical concerns are resolved. The core observations are potentially interesting, but the current evidence does not fully establish the central claims regarding RNA unfolding versus annealing and the functional significance of the observed activities.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data interpretation / claim support
- **Claim pointer** The authors claim that UPF2L "unfolds our reporter hairpin-RNA structure" (Abstract) and that MIF4G-D3 exhibits "RNA annealing activity" (Results, Discussion). These two activities are presented as distinct, but the data do not clearly distinguish between them.
- **Evidence pointer** Results section "UPF2 remodels structured RNA"; Figures 1C, 1D, 4B–4E; Supplemental Figure S4.
- **Concern** The EMSA experiments show a new, slower-migrating RNA species in the presence of UPF2L or MIF4G-D3. The authors interpret this as either unfolding (for UPF2L) or annealing (for MIF4G-D3). However, the molecular beacon experiments (Figure 4D) show that the new species formed by MIF4G-D3 is still quenched, indicating a double-stranded conformation, which supports annealing. For UPF2L, the molecular beacon experiment was inconclusive ("not shown"), and the fluorescence spectroscopy data (Figure 4E) show increased fluorescence, which the authors attribute to unfolding. However, this increased fluorescence could also be explained by protein-induced fluorescence enhancement (PIFE) alone, as the authors acknowledge, or by partial melting of the hairpin stem without full unfolding. The claim that UPF2L "unfolds" the hairpin is therefore not strongly supported. The distinction between unfolding and annealing is critical, as these are mechanistically different activities. The authors need to provide more direct evidence for unfolding, such as using a non-annealing RNA substrate (e.g., a hairpin with a non-complementary loop) or a single-molecule FRET assay.
- **Why it matters** The central novelty of the manuscript hinges on the claim that UPF2 can remodel RNA structure. If the observed effect is primarily annealing of two RNA molecules rather than unfolding of a single hairpin, the proposed mechanism for UPF2’s role in mRNP remodeling would be different. The current ambiguity prevents a clear mechanistic interpretation.
- **Resolution test** Perform a molecular beacon experiment with UPF2L under conditions where annealing is impossible (e.g., using a hairpin with a non-complementary 5' overhang or a single-molecule FRET assay). Alternatively, use a gel-based assay with a radiolabeled hairpin and a complementary unlabeled RNA to directly test for annealing versus unfolding. If unfolding is claimed, show that the new species is single-stranded (e.g., by nuclease sensitivity).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor / data analysis
- **Claim pointer** The authors report Kd values for UPF2 variants binding to various nucleic acids (Figure 3A–C) and state that UPF2L preferentially binds ssRNA (Kd 135 nM) over dsRNA (454 nM) and ssDNA (431 nM).
- **Evidence pointer** Results section "UPF2L preferentially binds single-stranded RNA"; Figure 3; Supplemental Table S1.
- **Concern** The Kd values are presented without error bars, replicates, or statistical analysis. It is unclear how many independent experiments were performed and whether the differences between Kd values (e.g., 135 nM vs 223 nM for ssRNA vs hpRNA) are statistically significant. The authors also do not report the goodness-of-fit for their binding curves. The statement that UPF2L "preferentially binds" ssRNA is based on a single set of measurements. Furthermore, the Kd for MIF4G-D3 binding to ssRNA is reported as 694 nM in one experiment (Figure 3A) and 529 nM in another (Figure 3C), and the authors attribute this to sequence differences, but this is not tested directly.
- **Why it matters** The quantitative comparison of binding affinities is a key part of the manuscript’s conclusions. Without proper error analysis and statistical testing, the claim of preferential ssRNA binding is not robust. This is particularly important given the modest differences in Kd values.
- **Resolution test** Provide Kd values with standard deviations from at least three independent experiments. Perform a statistical test (e.g., one-way ANOVA with post-hoc test) to compare Kd values across different nucleic acid substrates. Show representative binding curves and fits.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional relevance / overinterpretation
- **Claim pointer** The authors propose that UPF2’s RNA binding and unfolding activity "may support UPF1’s helicase and mRNP remodeling activity and, in combination with UPF3B, stabilize UPF1’s association with nonsense mRNA" (Abstract, Discussion).
- **Evidence pointer** Discussion section; Figure 6.
- **Concern** The functional model presented in Figure 6 is highly speculative and goes beyond the data presented. The authors show that UPF2 can bind and remodel RNA in vitro, but they do not provide any evidence that this activity is relevant for NMD in cells. The claim that UPF2 "stabilizes UPF1’s association with nonsense mRNA" is not directly tested. The model is presented as a logical conclusion, but it is one of several possible interpretations.
- **Why it matters** Overinterpretation of in vitro data can mislead the field. The proposed model needs to be clearly framed as a hypothesis, not a conclusion. The manuscript would be strengthened by a more cautious discussion of the limitations of the in vitro system and the need for future in vivo validation.
- **Resolution test** Either provide direct experimental evidence for the functional role of UPF2’s RNA binding/unfolding activity in NMD (e.g., using a UPF2 mutant that is defective in RNA binding but retains UPF1 binding) or temper the claims in the Discussion and clearly state that the functional relevance remains to be tested.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Data presentation / methodology
- **Claim pointer** The authors state that negative-stain EM shows "more defined particles" and "less variability" for UPF2L in the presence of ssRNA, and that this indicates a conformational change to a more compact state (Figure 5).
- **Evidence pointer** Results section "Single-stranded RNA binding induces compact UPF2L conformations"; Figure 5A–C; Supplemental Figure S6.
- **Concern** The negative-stain EM analysis is qualitative. The authors do not provide quantitative metrics for particle shape distribution (e.g., percentage of particles in each class) or any measure of inter-observer variability. The classification into "elongated" vs. "compact" is subjective. The authors also do not show a representative micrograph for the UPF2L/ssRNA sample, making it difficult to assess the quality of the data. The claim that ssRNA binding induces a conformational change would be strengthened by a more quantitative analysis, such as measuring the distribution of particle dimensions or using a classification algorithm that is blinded to the sample identity.
- **Why it matters** The EM data is used to support the claim that UPF2 undergoes a conformational change upon RNA binding, which is a key part of the proposed mechanism. Qualitative analysis is insufficient to support this claim.
- **Resolution test** Provide a quantitative analysis of particle shapes (e.g., aspect ratio distribution) for each condition, with a clear description of the classification criteria. Show representative raw micrographs. Consider using a blinded analysis to avoid bias.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / reproducibility
- **Affected element** Methods section "Florescence anisotropy measurements"
- **Evidence pointer** Methods section; typographical error in section title.
- **Issue** The section title contains a typo: "Florescence" should be "Fluorescence".
- **Required correction** Correct the typo in the section title.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1F and accompanying text
- **Evidence pointer** Results section "MIF4G domains mediate RNA binding of UPF2"; Figure 1F.
- **Issue** The authors state that "All UPF2 constructs tested, with the exception of MIF4G-D1, bound ssRNA" but the figure legend does not clearly indicate which bands correspond to which construct. The use of blue and orange stars is helpful, but a more detailed figure legend or a table summarizing the binding and remodeling activity of each construct would improve clarity.
- **Required correction** Add a summary table or a more detailed figure legend that clearly indicates the binding and remodeling activity of each UPF2 variant.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data interpretation
- **Affected element** Results section "UPF2L preferentially binds single-stranded RNA"; Figure 3C.
- **Evidence pointer** Figure 3C.
- **Issue** The authors state that UPF2L has a "slight preference for binding dsDNA" over ssDNA, but the Kd values (334 nM vs 431 nM) are not statistically compared. This statement is not supported without error analysis.
- **Required correction** Either provide statistical analysis for this comparison or soften the statement to indicate a trend that is not statistically significant.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction; Discussion.
- **Issue** The authors mention that UPF2’s MIF4G-D3 domain binds RNA (Kadlec et al. 2004; Bufton et al. 2022), but they do not discuss the structural basis for RNA binding by MIF4G domains in general. A brief discussion of known RNA-binding modes of MIF4G domains would help contextualize the findings.
- **Required correction** Add a brief discussion of the structural features of MIF4G domains that may contribute to RNA binding.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 4F and accompanying text
- **Evidence pointer** Results section "UPF2 remodels structured RNA"; Figure 4F.
- **Issue** The CD spectra are presented as raw data without error bars or replicates. It is unclear if the observed shifts are reproducible.
- **Required correction** Provide representative spectra from at least three independent experiments, or state that the spectra are representative of multiple experiments.

## Risk / unsupported claims
- The claim that UPF2L "unfolds" the hairpin RNA is not fully supported; the data are also consistent with partial melting or protein-induced fluorescence enhancement (R1-M1).
- The claim that UPF2L "preferentially binds" ssRNA is not supported by statistical analysis (R1-M2).
- The proposed functional model (Figure 6) is speculative and not directly tested (R1-M3).
- The claim that UPF2L undergoes a conformational change upon ssRNA binding is based on qualitative EM analysis (R1-M4).
- The statement that "UPF2’s RNA binding and unfolding activity may support UPF1’s helicase and mRNP remodeling activity" is a hypothesis, not a conclusion, and is not directly supported by the data.
- The Kd values for MIF4G-D3 binding to ssRNA differ between experiments (694 nM vs 529 nM), and the authors' explanation of sequence dependence is not directly tested.