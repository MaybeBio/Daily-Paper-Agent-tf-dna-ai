## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Materials and Methods, Results and Discussion, Conclusions) and bibliographic metadata. No figures, tables, or supplementary materials were provided.
- **Assessment boundary** Scientific claims, methodological soundness, and internal consistency based solely on the supplied text. No external validation of data or reproducibility checks were performed.
- **Shared manuscript claim summary** The authors report that HMO1 forms complexes with DNA without significant structural changes in either component, that Box B of HMO1 binds DNA via two extended sites at the N-termini of helices I and II with intercalation of F114, and that HMO1 has approximately twofold higher affinity for DNA containing the IFHL motif compared to randomized sequence.
- **Visible evidence base** Text descriptions of CD spectroscopy, fluorescence spectroscopy, EMSA, homology modeling, and MD simulations. Quantitative Kd values (128 ± 15 nM for RO, 62 ± 8 nM for SO) and Hill coefficients are mentioned but no raw data, gels, or spectra are shown.
- **Missing materials affecting confidence** All figures (Figures 1–5, Figure S1), raw spectra, gel images, MD trajectory details, and statistical analysis outputs. Without these, the quantitative claims and structural interpretations cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant question in HMGB protein biology, specifically the molecular basis for HMO1's apparent sequence preference. The combination of biophysical and computational approaches is appropriate in principle. However, the evidence as presented in the text is insufficient to fully support the central claims. The structural model relies on homology to TFAM with only 30% sequence identity, and the claim of sequence-specific affinity is based on a single pair of DNA substrates with a modest twofold difference. The lack of raw data and statistical details limits the ability to assess robustness. The work is potentially of interest to the chromatin and transcription communities, but the current presentation does not establish the case convincingly.
- **Who would be interested in the results, and why** Researchers studying HMGB family proteins, architectural transcription factors, chromatin remodeling, and promoter-specific gene regulation in yeast. The findings on sequence-dependent DNA binding by a presumed non-specific protein could inform broader discussions of how architectural proteins achieve functional specificity in vivo.
- **Major strengths** The study combines multiple complementary techniques (CD, fluorescence, EMSA, MD) to address a focused question. The use of both randomized and IFHL-containing DNA substrates is a reasonable experimental design. The computational model provides a testable structural hypothesis. The discussion appropriately contextualizes the findings within the broader HMGB literature.
- **Major Concerns** The structural model is built on a distant homology template, and the text does not provide validation metrics. The affinity difference between RO and SO is modest and based on a single DNA pair, raising questions about generalizability. The interpretation of fluorescence quenching as evidence for tryptophan localization at the interface is indirect. The CD analysis relies on spectral subtraction, which may introduce artifacts. The Hill coefficient is mentioned but not discussed in terms of binding cooperativity or stoichiometry.
- **Minor Comments** The manuscript would benefit from clearer justification for the choice of 24 bp DNA length given the previously reported 26 bp binding site. The relationship between the two EMSA complex bands for SO DNA and the proposed two binding sites is not fully explained. The text states that HMO1 is "essential for normal cell growth" but does not provide a citation for this claim in the Introduction.
- **Technical failings that need to be addressed before the case is established** Lack of model validation metrics for the homology model; absence of statistical details for Kd comparisons; insufficient description of MD convergence and sampling; no control experiments for fluorescence quenching (e.g., free tryptophan or mutant proteins).
- **Assessment against Nature-style criteria** Originality: Moderate. The finding that a presumed non-specific HMGB protein has sequence preference is not entirely novel, but the specific focus on HMO1 and IFHL is of interest. Scientific importance: Moderate. The work has implications for understanding promoter targeting by architectural proteins, but the effect size is small and the mechanistic insight is limited. Interdisciplinary readership: Limited. The work is primarily of interest to specialists in chromatin biology and biophysics. Technical soundness: Weak as presented. The lack of raw data and validation metrics prevents full assessment. Readability for nonspecialists: Acceptable. The text is generally clear, though some methodological details are dense.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, but the central claims require stronger experimental support and more rigorous computational validation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural model validity
- **Claim pointer** The authors claim that the HMO1 Box B complex with DNA involves two extended binding sites at the N-termini of helices I and II, stabilized by intercalation of F114.
- **Evidence pointer** Section 3.2, Figure 4 (not provided)
- **Concern** The homology model is based on TFAM (30% sequence identity), and no validation metrics (e.g., Ramachandran plots, QMEAN scores, or RMSD to template) are reported. The MD simulations are described as 1000 ns, but no convergence analysis, replica information, or free energy calculations are provided to support the stability of the proposed binding mode.
- **Why it matters** The structural model is the central mechanistic claim of the paper. Without validation, the specific interactions and the role of F114 remain speculative. A distant homology template can produce artifacts, especially in loop regions and side-chain conformations.
- **Resolution test** Provide model quality metrics, show MD convergence (e.g., RMSD over time, per-residue fluctuations), and ideally validate the model with mutagenesis experiments targeting F114 and the proposed binding interface.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Affinity claim robustness
- **Claim pointer** The authors claim that HMO1 has a twofold higher affinity for DNA containing the IFHL motif (Kd = 62 ± 8 nM) compared to randomized sequence (Kd = 128 ± 15 nM).
- **Evidence pointer** Section 3.3, Figure 5 (not provided)
- **Concern** The affinity difference is based on a single pair of DNA substrates. The text does not report the number of independent experiments beyond "three," nor does it provide statistical tests (e.g., p-values or confidence intervals) for the Kd comparison. The Hill coefficient is mentioned but not discussed, and the presence of two complex bands for SO DNA suggests heterogeneous binding modes that complicate the interpretation of a single Kd.
- **Why it matters** The twofold difference is modest and could arise from experimental variability or differences in DNA sequence beyond the IFHL motif. The claim of sequence-specific recognition underpins the biological significance of the work.
- **Resolution test** Include additional DNA substrates with mutated or scrambled IFHL motifs, report full statistical analysis, and discuss the Hill coefficient and heterogeneous complex formation in the context of the measured Kd.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Fluorescence interpretation
- **Claim pointer** The authors state that fluorescence quenching upon DNA binding indicates that one or both tryptophan residues (W149, W160) are localized at the interaction interface.
- **Evidence pointer** Section 3.2, Figure 3D (not provided)
- **Concern** Fluorescence quenching can result from conformational changes, energy transfer, or changes in solvent exposure without direct contact with DNA. The text does not provide control experiments (e.g., with a W149A or W160A mutant) or a quantitative analysis of quenching (e.g., Stern-Volmer plots).
- **Why it matters** The interpretation of the fluorescence data is used to support the structural model. If the quenching is due to indirect effects, the localization claim is weakened.
- **Resolution test** Perform mutagenesis of W149 and W160, measure fluorescence in the presence of DNA, and provide Stern-Volmer analysis or alternative quenching mechanisms to support the interpretation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Experimental design
- **Affected element** DNA substrate length
- **Evidence pointer** Section 2.2, Section 3.3
- **Issue** The authors use 24 bp DNA substrates but note that the previously estimated HMO1 binding site is 26 bp. The rationale for this choice is not explained.
- **Required correction** Justify the use of 24 bp DNA or discuss how the length difference might affect binding affinity and complex stoichiometry.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Literature support
- **Affected element** Introduction statement
- **Evidence pointer** Section 1, first paragraph
- **Issue** The statement that HMO1 is "essential for normal cell growth" is not cited.
- **Required correction** Add a citation to support this claim or rephrase to reflect the cited literature.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** EMSA complex assignment
- **Evidence pointer** Section 3.3, Figure 5B
- **Issue** The text mentions two complex bands for SO DNA but does not explain their origin or relationship to the proposed two binding sites on Box A and Box B.
- **Required correction** Clarify whether the two bands represent distinct binding modes, different stoichiometries, or conformational isomers, and discuss how this affects the Kd interpretation.

## Risk / unsupported claims
- The claim that HMO1 Box B binds DNA via two extended sites at the N-termini of helices I and II is unsupported without model validation metrics and MD convergence data.
- The claim of sequence-specific affinity for the IFHL motif is weakly supported, as it relies on a single DNA pair with a modest twofold difference and no statistical testing.
- The interpretation of fluorescence quenching as evidence for tryptophan localization at the interface is not fully supported without control experiments.
- The statement that the HMO1:DNA complex forms "without noticeable changes in the structure of DNA and HMO1" is based on CD spectral similarity, which is a low-resolution technique and may not detect subtle structural changes.
- The claim that HMO1 belongs to a group of non-sequence-specific binders with increased affinity to particular sequences is speculative and not directly tested in this work.