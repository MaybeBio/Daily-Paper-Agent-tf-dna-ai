## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodological soundness, and interpretation of results as presented in the provided manuscript
- **Shared manuscript claim summary** The authors identify subtype-specific Tat protein polymorphisms across nine HIV-1 subtypes and use computational methods (AlphaFold2 structure prediction, HDOCK docking, AMBER20 molecular dynamics) to assess how these polymorphisms affect Tat-TAR binding affinity, concluding that certain subtypes (A6, CRF02_AG, C) bind more strongly than others (A1, A3), with potential implications for subtype-specific HIV pathogenesis.
- **Visible evidence base** Full manuscript text including Introduction, Materials and methods, Results, Discussion, and references to figures and tables (Fig 1-4, S1-S2 Figs, Tables 1-2, S1 Table)
- **Missing materials affecting confidence** Figures and tables referenced in the text (Fig 1-4, S1-S2 Figs, Tables 1-2, S1 Table) were not provided. Supplementary information and raw data files were not available. Sequence accession numbers or database identifiers for individual sequences were not listed.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant question in HIV biology, namely whether subtype-specific Tat polymorphisms influence Tat-TAR binding, which could have implications for understanding differential pathogenesis across HIV-1 subtypes. The computational workflow is reasonable and the authors have made efforts to validate their findings with extended simulations. However, the study is entirely in silico, and the manuscript has several significant issues that need to be addressed. The lack of statistical analysis, the absence of key methodological details, and the overinterpretation of results without experimental validation substantially weaken the conclusions. The manuscript would benefit from a more cautious interpretation of the findings and a clearer acknowledgment of the limitations of computational predictions in the absence of functional data.

- **Who would be interested in the results, and why** Researchers studying HIV-1 subtype diversity and its impact on viral pathogenesis, particularly those focused on Tat function, Tat-TAR interactions, and HIV-associated neurocognitive disorders. Computational biologists interested in applying structure prediction and molecular dynamics to viral protein-RNA interactions may also find the methodological approach of interest. Clinicians and virologists studying subtype-specific differences in HIV disease progression could find the hypotheses generated here useful for designing future experimental studies.

- **Major strengths** The study addresses an under-explored area, namely Tat-TAR interactions in non-B, non-C subtypes, which is relevant given the global distribution of HIV-1 subtypes. The computational pipeline is comprehensive, combining sequence analysis, structure prediction, docking, and molecular dynamics simulations. The use of consensus sequences is a reasonable approach for comparative subtype analysis. The authors have made an effort to validate their key findings with extended 500 ns simulations for the strongest and weakest binders. The discussion of discrepancies with previous studies is transparent and the authors provide plausible explanations for these differences.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript reports differences in binding energies between subtypes (e.g., A6 at -126.8 kcal/mol vs A1 at -57.5 kcal/mol) and attributes these to subtype-specific polymorphisms.
- **Evidence pointer** Results section, Table 1, location not provided
- **Concern** The study reports binding energy differences between subtypes but provides no statistical analysis. Only a single consensus sequence per subtype was used, and no replicates or error estimates are reported. The median and IQR are calculated across time points within a single trajectory, not across independent replicates, which does not provide a measure of inter-subtype variability or statistical significance.
- **Why it matters** Without statistical analysis, it is impossible to determine whether the observed differences in binding energies between subtypes are meaningful or within the noise of the computational methods. The conclusions about which subtypes bind more strongly may not be robust.
- **Resolution test** Provide multiple independent simulations (at least 3 replicates) per subtype, report mean and standard deviation or standard error, and perform appropriate statistical tests (e.g., ANOVA with post-hoc comparisons) to determine whether binding energy differences between subtypes are statistically significant.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validation
- **Claim pointer** The authors claim that AlphaFold2-generated models are reliable for downstream docking and MD simulations, and that the MM/GBSA binding energies are accurate.
- **Evidence pointer** Materials and methods, "Molecular docking, molecular dynamics simulations, and Tat-TAR interaction analysis", location not provided
- **Concern** The manuscript does not provide validation of the AlphaFold2 models beyond a general statement that all subtypes scored 80% or higher on Verify 3D. No comparison with experimental structures, no per-residue confidence metrics (e.g., pLDDT scores for the specific models used), and no assessment of whether the predicted structures are suitable for docking studies. Additionally, the MM/GBSA method is known to be sensitive to the choice of parameters and the conformational sampling, and the manuscript does not discuss the limitations of this approach for protein-RNA interactions.
- **Why it matters** The reliability of the entire computational pipeline depends on the quality of the starting structures. If the AlphaFold2 models are not accurate for the Tat protein, particularly in the disordered regions, the docking and MD results may be meaningless. The lack of validation undermines confidence in the reported binding energies.
- **Resolution test** Provide per-residue pLDDT scores for the models used, compare predicted structures with any available experimental structures of Tat or Tat-TAR complexes, and discuss the suitability of AlphaFold2 for predicting RNA-binding proteins. Additionally, validate the MM/GBSA approach by comparing with more rigorous free energy methods (e.g., thermodynamic integration or free energy perturbation) for at least one subtype.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation and causal claims
- **Claim pointer** The authors attribute differences in binding affinity to specific subtype-specific polymorphisms (e.g., A3: K29A and R53K, A1: R57G, A6: K53R, Q54H, and V69I, C: V69I, C31S, and 58A, CRF02_AG: N24K and N29K).
- **Evidence pointer** Results section, Discussion section, location not provided
- **Concern** The manuscript claims that specific polymorphisms are responsible for the observed differences in binding affinity, but no mutagenesis or alanine-scanning studies were performed to test the individual contribution of each polymorphism. The correlation between the presence of certain residues and binding energy is purely speculative. Furthermore, the authors do not consider the potential compensatory or synergistic effects of multiple polymorphisms within a subtype.
- **Why it matters** Without experimental validation or at least computational mutagenesis studies, the causal link between specific polymorphisms and binding affinity is not established. The claims may be overinterpreted and could mislead future research directions.
- **Resolution test** Perform in silico mutagenesis (e.g., reverting each polymorphism to the consensus or ancestral residue) and assess the effect on binding energy. Ideally, validate key findings with experimental binding assays (e.g., electrophoretic mobility shift assay or surface plasmon resonance) using Tat peptides or proteins with specific polymorphisms.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Clinical relevance
- **Claim pointer** The authors suggest that their findings "may have implications for the subtype-specific disease pathogenesis mediated by the Tat protein" and discuss correlations with clinical stages.
- **Evidence pointer** Discussion section, Table 2, location not provided
- **Concern** The clinical implications are speculative. The authors stratify sequences by clinical stage but do not provide details on how clinical stage was defined, the number of sequences in each category, or any statistical analysis of the association between polymorphisms and clinical stage. The claim that "AIDS-stage variants from best-binder subtypes A6 and CRF02_AG showed more charged basic domains" is based on a very small number of sequences and is not supported by quantitative analysis.
- **Why it matters** The clinical relevance of the findings is a key motivation for the study, but the evidence presented is insufficient to support any claims about disease progression or pathogenesis. Overstating clinical implications without data could mislead readers.
- **Resolution test** Provide detailed information on the clinical staging criteria, the number of sequences per stage per subtype, and perform appropriate statistical tests (e.g., Fisher's exact test) to assess whether specific polymorphisms are significantly associated with clinical stage. Alternatively, temper the clinical claims and clearly state that these are hypotheses requiring experimental validation.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and transparency
- **Claim pointer** The methods section describes the use of the HIV Los Alamos Database, AlphaFold2, HDOCK, and AMBER20, but lacks sufficient detail for reproduction.
- **Evidence pointer** Materials and methods, location not provided
- **Concern** The manuscript does not provide specific parameters for the molecular dynamics simulations (e.g., force field versions, water model details, temperature and pressure coupling methods, simulation time steps, etc.). The version of AlphaFold2 and the specific settings used are not mentioned. The criteria for selecting the "best" docking pose from HDOCK are not described. The MM/GBSA calculation parameters (e.g., salt concentration, interior dielectric constant) are not specified.
- **Why it matters** Reproducibility is a fundamental requirement for scientific publications. Without detailed methods, other researchers cannot replicate the study or assess the validity of the computational approach.
- **Resolution test** Provide a detailed description of all computational parameters, including software versions, force field parameters, simulation settings, and analysis protocols. Consider providing input files and scripts as supplementary material.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and organization
- **Affected element** Introduction
- **Evidence pointer** Introduction section, location not provided
- **Issue** The manuscript contains two separate Introduction sections. The first is a brief summary, and the second is a more detailed introduction. This is redundant and confusing.
- **Required correction** Merge the two Introduction sections into a single, coherent introduction that provides the necessary background and clearly states the study objectives.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results section
- **Evidence pointer** Results section, Table 1, location not provided
- **Issue** The binding energies are reported as single values without any measure of variability. The median and IQR are mentioned in the text but not presented in the table.
- **Required correction** Include the median and IQR (or mean and SD) for the binding energies in Table 1, and clearly indicate whether these are calculated across time points or across replicates.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Language and terminology
- **Affected element** Discussion section
- **Evidence pointer** Discussion section, location not provided
- **Issue** The phrase "500nm run" in the Discussion is incorrect. It should be "500 ns run" (nanoseconds, not nanometers).
- **Required correction** Correct the typo to "500 ns run".

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Discussion section
- **Evidence pointer** Discussion section, location not provided
- **Issue** The authors state that "a study by Williams [6], Gotora [44] and Ronsard [46]" showed that Tat from subtype B had higher binding affinity than subtype C. However, the reference list is not provided, and it is unclear whether these are the correct citations.
- **Required correction** Ensure all references are correctly cited and listed. Verify that the cited studies indeed support the claims made.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures
- **Evidence pointer** Fig 1-4, S1-S2 Figs, location not provided
- **Issue** The figures are not provided in the manuscript, so it is impossible to assess their quality or the accuracy of the data presented.
- **Required correction** Ensure all figures are included in the submission and are of sufficient quality to support the claims made in the text.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section
- **Evidence pointer** Results section, location not provided
- **Issue** The text mentions "median (IQR [25th, 75th]) binding energy" but the IQR is reported as "−123.3, −68.8" which appears to be a range, not an IQR. The IQR should be the difference between the 75th and 25th percentiles.
- **Required correction** Clarify the statistical reporting. If the values are the 25th and 75th percentiles, state this explicitly. If they are the IQR, report the difference.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Materials and methods
- **Evidence pointer** Materials and methods, "Retrieval of HIV subtype-specific sequences, sequence alignment, synthesis of consensus sequence", location not provided
- **Issue** The number of sequences per subtype is reported (e.g., A: n=3, A3: n=3), but for some subtypes the sample size is very small. The authors do not discuss the potential impact of small sample sizes on the consensus sequence and subsequent analyses.
- **Required correction** Add a brief discussion of the limitations of using small sample sizes for certain subtypes and how this might affect the generalizability of the findings.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Ethical compliance
- **Affected element** Materials and methods
- **Evidence pointer** Materials and methods, location not provided
- **Issue** The manuscript does not include a statement on data availability or a declaration of any competing interests.
- **Required correction** Add sections on data availability and competing interests as required by the journal.

## Risk / unsupported claims
- The claim that specific subtype-specific polymorphisms (e.g., K29A, R53K, R57G, K53R, Q54H, V69I, C31S, N24K, N29K) are responsible for the observed differences in binding affinity is unsupported without mutagenesis or experimental validation.
- The claim that the findings "may have implications for the subtype-specific disease pathogenesis" is speculative and not supported by the data presented.
- The claim that "AIDS-stage variants from best-binder subtypes A6 and CRF02_AG showed more charged basic domains" is based on an unspecified number of sequences and lacks statistical analysis.
- The statement that "200 ns MDS, confirmation using 500 ns MDS, selection of a recent, high-quality TAR structure, and use of AlphaFold2 for Tat protein modeling increased the robustness of our analyses" is not fully justified, as the robustness of the results has not been demonstrated through appropriate validation or statistical analysis.
- The comparison with previous studies (e.g., Williams, Gotora, Ronsard) is not adequately supported by the provided text, as the specific findings of these studies are not described in sufficient detail.