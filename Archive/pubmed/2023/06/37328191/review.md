## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, materials and methods, and data availability statement.
- **Assessment boundary** Scientific content, technical soundness, logical coherence, and support of claims by presented evidence. Editorial or stylistic issues are noted only where they affect comprehension.
- **Shared manuscript claim summary** The authors report a new crystal structure of the JBP1 J-DNA-binding domain (JDBD) with an ordered loop (residues 529–537) previously missing, use computational docking and molecular dynamics to model the JDBD:J-DNA interaction, identify Arg448 and Asn455 as new residues involved in J-DNA binding, and use AlphaFold modeling to propose that the N-terminal region of JBP1 contributes to J-DNA binding, supported by truncation experiments.
- **Visible evidence base** New crystal structure (PDB 8BBM), molecular dynamics simulations, HADDOCK docking, mutagenesis with fluorescence polarization binding assays, thermal stability measurements, SAXS comparisons, AlphaFold model analysis, sequence alignments.
- **Missing materials affecting confidence** Supplementary figures and tables (Figs S1–S14, Tables S1–S5) are referenced but not provided in the submitted text. Crystallographic table (Table 2) content not visible. Full binding curves and raw fluorescence polarization data not shown. AlphaFold PAE plots for species other than L. tarentolae not shown.

## Reviewer

### Overall assessment
This manuscript presents a solid, incremental advance in understanding how JBP1 recognizes base-J-containing DNA. The new crystal structure with the ordered loop is a useful contribution, and the identification of Arg448 and Asn455 as functionally relevant residues is supported by the mutagenesis data. The N-terminal truncation experiments are straightforward and the results are clear. However, the computational modeling sections are largely confirmatory of prior work, and the proposed model for full-length JBP1 bound to J-DNA remains speculative, as the authors themselves acknowledge. The link between the structural observations and the proposed biological implications for base-J replication is plausible but not directly tested. The manuscript is clearly written and the work is technically sound within its scope, but the overall advance is modest.

### Who would be interested in the results, and why
Researchers studying DNA modification and epigenetic regulation in kinetoplastid parasites, particularly those interested in base-J biology, the TET-JBP protein family, and DNA-binding protein mechanisms. The structural and computational methods may also interest specialists in protein-DNA docking and modeling. The potential relevance of JBP1 as a drug target for Leishmania infections could attract parasitologists and drug discovery researchers.

### Major strengths
1. The new crystal structure provides a previously missing piece of structural information, and the authors are appropriately cautious about why the loop is ordered in this crystal form.
2. The combination of computational modeling with experimental validation (mutagenesis, binding assays) is a sound approach.
3. The identification of Arg448 and Asn455 as new residues involved in J-DNA binding is a concrete, testable advance.
4. The N-terminal truncation experiments are simple, direct, and clearly interpreted.
5. The manuscript is generally well written and the logic is easy to follow.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** No
- **Axis** Evidence strength for functional claims
- **Claim pointer** The authors state that Arg448 and Asn455 are "involved in J-DNA binding" based on mutagenesis and fluorescence polarization.
- **Evidence pointer** Results section "Computational modeling provides new insight into JDBD mediated J-DNA recognition", Fig 4, Table S3
- **Concern** The fluorescence polarization data for the point mutants are described only in terms of approximate fold changes in affinity (e.g., "∼500-fold reduction" for R448A). The actual binding curves, Kd values with errors, and the number of independent replicates are not shown in the main text. Without these details, it is difficult to assess the reliability of the reported affinities, particularly for mutants with very weak binding where the assay may be operating near its detection limit.
- **Why it matters** The central new experimental claim of the paper rests on these binding measurements. If the affinities are not robustly determined, the conclusion that Arg448 and Asn455 contribute to J-DNA binding is weakened.
- **Resolution test** Provide the full binding isotherms, Kd values with standard errors from at least three independent experiments, and a clear statement of the assay detection limit. Show that the mutants are properly folded (e.g., circular dichroism or size-exclusion chromatography) to rule out misfolding as the cause of reduced binding.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Support for the proposed full-length JBP1:J-DNA model
- **Claim pointer** The authors propose that "the combined binding of the THD and JDBD to J-DNA is accompanied by structural rearrangements which likely include DNA bending to allow simultaneous binding of the JDBD and THD-mediated hydroxylation of a thymidine that is located 13 nucleotides downstream in the opposing DNA strand, followed by the N-terminal region wrapping around DNA, and stabilizing the complex."
- **Evidence pointer** Results section "New insights through AI-based modeling of JBP1", Fig 7F
- **Concern** This model is presented as a proposal, but the figure (Fig 7F) is not visible in the submitted text, and the reasoning chain from the AlphaFold model, the failed docking attempts, and the truncation data to this specific model is not fully articulated. The authors state that "several modeling attempts did not yield a model that fits with the SAXS data," but the details of these attempts, the criteria for failure, and the alternative models considered are not described. The proposed DNA bending is not supported by any direct experimental evidence.
- **Why it matters** This model is the culmination of the paper and frames the proposed mechanism of base-J replication. If the model is not well supported or clearly explained, the reader cannot evaluate its plausibility.
- **Resolution test** Provide a more detailed description of the modeling attempts and why they failed. Show the proposed model figure with clear labeling. If possible, provide experimental evidence for DNA bending (e.g., FRET or cyclization assays) or clearly state that this is a speculative hypothesis requiring future testing.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the N-terminal contribution claim
- **Claim pointer** The authors state that "the N-terminal residues are involved in J-DNA binding" based on truncation experiments in L. tarentolae.
- **Evidence pointer** Results section "New insights through AI-based modeling of JBP1", Fig 7E, Table S5
- **Concern** The truncation experiments were performed only in L. tarentolae. The authors note that the N-terminal region is not conserved in Trypanosoma species, and they use this to explain species differences in base-J essentiality. However, the binding affinities reported for the truncated constructs (20.8 nM for Δ23-JBP1 and 31.2 nM for Δ38-JBP1) are only 3- to 5-fold weaker than wild-type (6.4 nM). This is a modest effect, and the biological significance of this difference is not discussed in the context of the proposed model. Is a 3-fold change in affinity sufficient to explain the proposed stabilizing role of the N-terminus?
- **Why it matters** The claim that the N-terminus contributes to J-DNA binding is used to support a broader evolutionary argument about species differences. If the effect is small, the biological relevance may be limited.
- **Resolution test** Discuss the quantitative relationship between the observed affinity changes and the proposed functional role. If possible, test the N-terminal contribution in a Trypanosoma species or in a chimeric construct to directly test the evolutionary hypothesis.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of crystallographic reporting
- **Affected element** Results section "A new crystal structure for JDBD with an ordered loop", Table 2
- **Evidence pointer** Table 2 (content not visible in submitted text)
- **Issue** The crystallographic table is referenced but its content is not visible. Standard crystallographic statistics (resolution, R-factor, R-free, completeness, etc.) should be reported.
- **Required correction** Ensure Table 2 is included in the final submission with all relevant statistics.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Interpretation of HDX-MS data
- **Affected element** Results section "Computational modeling provides new insight into JDBD mediated J-DNA recognition", Fig 4
- **Evidence pointer** Fig 4A and B
- **Issue** The authors state that the α1 helix "is positioned towards J-DNA as in the docking models" based on HDX-MS reduction. However, the HDX-MS data were obtained in the absence of DNA (from previous work), and the reduction is interpreted as indicating DNA interaction. This is a reasonable inference, but the authors should clarify that the HDX-MS data are from the apo protein and that the reduction upon DNA binding is inferred, not directly measured in this study.
- **Required correction** Clarify the origin of the HDX-MS data and the interpretation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting of binding data
- **Affected element** Results section "Computational modeling provides new insight into JDBD mediated J-DNA recognition", Table S3
- **Evidence pointer** Table S3
- **Issue** The affinities in Table S3 are reported without errors or replicate numbers. For a quantitative binding study, this is insufficient.
- **Required correction** Report Kd values with standard deviations and the number of independent replicates.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract, Discussion
- **Issue** The abstract states that the N-terminus and JDBD "recognize base-J." The data show that the N-terminus contributes to binding affinity, but there is no evidence that the N-terminus specifically recognizes base-J (as opposed to contributing to overall DNA binding affinity through non-specific contacts). This overstates the finding.
- **Required correction** Rephrase to indicate that the N-terminus contributes to J-DNA binding, not that it recognizes base-J specifically.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness of methods for reproducibility
- **Affected element** Materials and Methods, "Docking base-J containing DNA to JBP1 with HADDOCK"
- **Evidence pointer** Materials and Methods section
- **Issue** The methods for generating the J-DNA starting structure and the docking protocol are described, but the specific parameters for the base-J residue (charges, atom types) are not provided. This limits reproducibility.
- **Required correction** Provide the base-J parameters as supplementary material or reference where they can be obtained.

### Technical failings that need to be addressed before the case is established
1. The binding data for point mutants need to be presented with full statistical details (R1-M1).
2. The proposed full-length model requires clearer presentation and a more explicit reasoning chain (R1-M2).
3. The quantitative significance of the N-terminal truncation effects needs discussion (R1-M3).

### Assessment against Nature-style criteria
- **Originality** Moderate. The new crystal structure is a useful addition, but the overall approach (docking, MD, mutagenesis) follows established methods. The identification of new residues is incremental rather than conceptually novel.
- **Scientific importance** Moderate. The work advances understanding of JBP1-DNA recognition, which is relevant to base-J biology and potentially to drug development for Leishmania. However, the mechanistic insights are limited and the proposed model is speculative.
- **Interdisciplinary readership** Limited. The work is primarily of interest to structural biologists and parasitologists. The methods and findings are unlikely to attract a broad interdisciplinary audience.
- **Technical soundness** Generally sound within the scope of the experiments presented. The crystallography appears well done, and the computational methods are appropriate. The main weaknesses are in the statistical reporting of binding data and the speculative nature of the full-length model.
- **Readability for nonspecialists** The manuscript is clearly written and the logic is easy to follow. However, the computational sections may be challenging for readers without a structural biology background. The abstract is accessible.

### Recommendation posture
Supportive if technical concerns are resolved. The core experimental findings (new structure, identification of Arg448 and Asn455, N-terminal contribution) are likely valid, but the manuscript would be strengthened by fuller reporting of binding data, a clearer presentation of the proposed model, and a more measured interpretation of the N-terminal contribution. The work is a solid contribution to a specialized field but does not represent a major conceptual advance.

## Risk / unsupported claims
1. The claim that the N-terminus "recognizes base-J" (abstract) is not supported by the data, which show only a modest contribution to overall binding affinity.
2. The proposed model of full-length JBP1 bound to J-DNA with DNA bending is speculative and not directly supported by experimental evidence.
3. The statement that "the lack of the positively charged N-terminal region and Asn455 in Trypanosomal JBP1 contribute to lower affinity for J-DNA compared with Leishmania JBP1" is an extrapolation from L. tarentolae data without direct comparative measurements in Trypanosoma species.
4. The claim that the new docking model is "compatible with SAXS data" is based on fits that are described as having "slightly elevated" χ2 values, which is not a strong validation.
5. The biological significance of the 3- to 5-fold reduction in binding affinity for the N-terminally truncated constructs is not established.