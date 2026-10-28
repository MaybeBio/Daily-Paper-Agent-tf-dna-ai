## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methodology, results, discussion, conclusion, and supplementary figure legends as provided.
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims relative to presented evidence, and alignment with Nature-style criteria. Editorial or stylistic preferences are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors propose that specific natural small molecules (Withanone, Withaferin-A, Cucurbitacin-B, CAPE, Artepillin C) can restore transcriptional activation function of p53 in cancer cells harbouring wild-type or p53(Ser46) mutant p53, via two mechanisms: (1) restoring the elongated conformation of the p53 TAD2 domain to enhance p53-p62 binding, and (2) abrogating mortalin-p53 interaction. Computational predictions are supported by in vitro experiments in U2OS and HSC3 cell lines.
- **Visible evidence base** Computational docking scores (Table 2), MD simulation analyses (RMSD, hydrogen bonding, MM/GBSA binding energies, Figures 1-2), protein-protein docking results (Figure 3, Tables 3-4), Western blotting and immunocytochemistry data (Figure 4A-B), luciferase reporter assays (Figure 4C), and HSC3 cell data (Figure 4D-E).
- **Missing materials affecting confidence** Raw MD trajectory data, force field parameters, convergence criteria details, uncropped Western blot images, full statistical outputs, cell viability assay data referenced but not shown, and supplementary figures referenced but not fully described in the provided text.

## Reviewer
- **Overall assessment** The manuscript addresses a clinically relevant question, namely whether natural compounds can restore p53 function in cancers harbouring a specific p53 mutant. The dual computational and experimental approach is commendable in principle. However, the evidence presented does not fully establish the central mechanistic claims. The computational analyses lack sufficient validation and methodological detail, and the experimental data are limited in scope, with key controls and quantitative analyses missing. The link between the computational predictions and the observed cellular outcomes is correlative rather than causal. The manuscript would benefit from substantial additional work to support the conclusions.
- **Who would be interested in the results, and why** Researchers in cancer biology, specifically those studying p53 reactivation strategies, natural product pharmacology, and computational drug discovery. The findings may also interest clinicians exploring adjuvant therapies for p53-mutant cancers, particularly oral squamous cell carcinoma. The comparative analysis of five compounds provides a useful starting point for prioritising candidates for further development.
- **Major strengths** The study addresses an important and under-explored problem, namely the p53(Ser46) mutant, which is clinically relevant but rarely targeted. The combination of computational and experimental approaches is appropriate for the research question. The inclusion of multiple natural compounds allows for comparative ranking. The use of both wild-type and mutant cell lines is a strength. The authors identify a specific conformational mechanism (helix-to-string transition) that is testable and mechanistically plausible.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5, R1-M6.
- **Assessment against Nature-style criteria** 
  - **Originality** Moderate. The concept of reactivating p53 with small molecules is not new, and several of the compounds studied have been previously investigated for p53-related effects. The specific focus on the Ser46 mutant and the conformational mechanism is somewhat novel, but the overall approach is incremental.
  - **Scientific importance** Potentially high if the claims were fully substantiated, given the clinical relevance of p53 mutants. However, the current evidence is insufficient to establish therapeutic potential, and the mechanistic link is not proven.
  - **Interdisciplinary readership** The topic bridges computational biology, structural biology, and cancer pharmacology, which could appeal to a broad audience. However, the current presentation is unlikely to attract readers beyond a specialist niche due to the limited scope of validation.
  - **Technical soundness** The computational methods are standard but applied with insufficient rigour and validation. The experimental methods are basic and lack the quantitative depth expected for the claims made. Several technical issues are detailed in the concerns below.
  - **Readability for nonspecialists** The manuscript is generally readable, but the results section is dense and would benefit from clearer organisation. Some terminology is used imprecisely, and the figures are not described in sufficient detail for a nonspecialist to follow the key points.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, but the central claims are not supported by the data as presented. Major revisions and additional experiments are required before the case can be made.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Validity of computational model
- **Claim pointer** The authors claim that Wi-N, Wi-A, and Cuc-B can restore p53-p62 interaction for phosphorylation-deficient p53 mutants, and that Wi-N specifically reverses the α-helical structure into an elongated string-like conformation similar to wild-type p53.
- **Evidence pointer** Figures 1-2, Tables 2-3, section "Interaction of natural metabolites on p53S46PΔ- p62 complex"
- **Concern** The central computational claim rests on the observation that Wi-N restores a "string-like" conformation in the p53 TAD2 domain. However, the manuscript does not provide a quantitative definition of what constitutes a "string-like" versus "helix-like" conformation. No secondary structure analysis (e.g., DSSP) is presented, no time-averaged structural ensembles are shown, and no comparison of conformational populations between wild-type, mutant, and drug-bound states is provided. The claim that Wi-N "caused a reversal" is based on visual inspection of a single representative structure, which is not a robust basis for such a strong conclusion. Furthermore, the MM/GBSA binding energies are reported as single values without error estimates or statistical comparison across replicate simulations.
- **Why it matters** The conformational restoration mechanism is the central hypothesis of the paper. If this is not rigorously established, the entire computational rationale for compound selection and the subsequent experimental work is undermined.
- **Resolution test** Provide quantitative secondary structure analysis over the full simulation trajectory, including time-averaged helix content, per-residue conformational assignments, and a comparison of conformational ensembles (e.g., via principal component analysis or clustering) between wild-type, mutant, and drug-bound states. Report MM/GBSA values as mean ± standard deviation from at least three independent simulations, with statistical significance testing.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors claim that the compounds cause reactivation of p53 function, supported by increased p53 and p21 expression in U2OS cells and increased p21 in HSC3 cells.
- **Evidence pointer** Figure 4A-E, section "Experimental evidence to the effect of natural metabolites on reactivation of p53"
- **Concern** The experimental evidence is limited to measuring p53 and p21 protein levels. p21 is a downstream target of p53, but its upregulation alone is not sufficient evidence of restored transcriptional activation function, particularly in the context of a specific p53 mutant. The authors do not measure direct transcriptional targets of p53 relevant to apoptosis (e.g., BAX, PUMA, NOXA) or cell cycle arrest (e.g., GADD45). The luciferase reporter assay uses a generic p53-responsive promoter, which does not specifically test the Ser46-dependent transcriptional programme. Additionally, the HSC3 data are based on a single Western blot for p21, with no quantification, no loading control shown in the described figure, and no assessment of p53 status in these cells beyond stating the mutant protein was not detected. The claim that p21 upregulation "endorses reactivation of wild-type p53 function" is an overstatement.
- **Why it matters** The clinical relevance of the study depends on demonstrating that the compounds restore the specific transcriptional programme lost in p53(Ser46) mutants. Without direct evidence of Ser46-specific transcriptional activation, the mechanism remains speculative.
- **Resolution test** Include quantitative analysis of multiple p53 transcriptional targets, particularly pro-apoptotic genes known to depend on Ser46 phosphorylation. Perform RNA-seq or qRT-PCR for a panel of p53 target genes in both U2OS and HSC3 cells treated with the compounds. For HSC3 cells, confirm the p53 mutation status and provide evidence that the observed p21 upregulation is p53-dependent (e.g., using p53 knockdown or a p53-null cell line as control). Provide quantification of Western blots with appropriate statistical analysis.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Missing controls
- **Claim pointer** The authors claim that the compounds specifically disrupt mortalin-p53 binding and that this contributes to p53 reactivation.
- **Evidence pointer** Figure 3, Tables 3-4, section "Effect of natural metabolites on p53-mortalin binding"
- **Concern** The computational analysis of mortalin-p53 abrogation lacks essential controls. No positive control (e.g., a known disruptor of mortalin-p53 interaction such as MKT-077) or negative control (e.g., a compound not expected to bind) is included in the docking or simulation studies. The claim that Cuc-B binds to both p53 and mortalin binding sites is based on docking scores and visual inspection, but no competition experiments or binding assays are presented. The experimental section does not directly test whether the compounds disrupt mortalin-p53 interaction in cells; the only evidence is indirect, via p53 and p21 levels. The authors do not show co-immunoprecipitation or proximity ligation assays to demonstrate disruption of the endogenous mortalin-p53 complex.
- **Why it matters** The dual mechanism proposed (restoring p53-p62 binding and disrupting mortalin-p53) is a key selling point of the paper. Without direct evidence for the latter, the mechanistic story is incomplete and the specificity of the compounds is not established.
- **Resolution test** Include co-immunoprecipitation experiments to show that compound treatment reduces mortalin-p53 complex formation in cells. Include a known disruptor as a positive control. For the computational part, include docking of a known non-binder as a negative control and validate binding poses with longer simulations or free energy perturbation methods.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that the compounds cause a significant increase in p53 and p21 expression and that the effects are statistically significant.
- **Evidence pointer** Figure 4, section "Experimental evidence to the effect of natural metabolites on reactivation of p53"
- **Concern** The statistical analysis is described only in the figure legend as "p values" with a general threshold. No information is provided on the number of independent experiments (beyond "three or more"), the statistical test used for each comparison, whether multiple testing corrections were applied, or whether the data met assumptions of normality. The figure legend states "p > 0.05 (ns), p ≤ 0.05 (∗), p ≤ 0.01 (∗∗), p ≤ 0.001 (∗∗∗), and p ≤ 0.0001 (∗∗∗∗)" but does not specify which comparisons were tested or the exact p-values. The bar graphs appear to show mean ± SD, but error bars are not defined in the text.
- **Why it matters** Reproducibility and interpretability of the experimental results depend on clear and correct statistical reporting. The current presentation does not allow the reader to assess the robustness of the findings.
- **Resolution test** Provide full statistical details in the figure legends or methods, including the number of replicates, the specific test used for each comparison, exact p-values, and whether corrections for multiple comparisons were applied. Consider showing individual data points alongside bar graphs.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Methodological detail
- **Claim pointer** The authors claim to have performed MD simulations and MM/GBSA calculations to support their conclusions.
- **Evidence pointer** Methods section "Pre-processing and preparation of target protein as well as ligands", "Molecular docking of ligands", "MD simulation in water", "MM/GBSA free energy calculations"
- **Concern** Several methodological details are missing or unclear. (1) The mutation of Ser46 to alanine (or to a phospho-dead mutant) is described as "mutated to normal ser46" which is ambiguous. The authors should specify the exact mutation introduced. (2) The protonation states of the phosphorylated serine in the wild-type simulation are not described. (3) The equilibration protocol is described as "seven steps" but the specific steps are not listed. (4) The number of MD replicates is not stated. (5) The MM/GBSA method is described but the specific parameters (e.g., dielectric constant, solvent model) are not provided. (6) The convergence criteria for the 200 ns simulations are not defined beyond visual inspection of RMSD plots.
- **Why it matters** Reproducibility of computational results is a core expectation in this field. The lack of detail prevents other researchers from repeating the simulations and undermines confidence in the results.
- **Resolution test** Provide a complete description of the simulation setup, including the exact mutation protocol, protonation states, equilibration steps, number of replicates, and MM/GBSA parameters. Deposit input files and trajectories in a public repository or provide them as supplementary material.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Dose-response and specificity
- **Claim pointer** The authors claim that the compounds are effective at the concentrations used and that the effects are specific to p53 reactivation.
- **Evidence pointer** Section "Drug preparation and treatments", Figure 4
- **Concern** The manuscript does not report dose-response experiments. Only a single concentration is used for each compound, and the choice of concentration is justified only by reference to earlier reports. It is unclear whether the observed effects are specific to p53 reactivation or are due to off-target effects, particularly at the relatively high concentrations used (e.g., 300 μM for Artepillin C). No experiments with p53-null cells or p53 knockdown are shown to demonstrate that the effects on p21 and cell growth are p53-dependent.
- **Why it matters** The therapeutic relevance of the compounds depends on their potency and specificity. Without dose-response data and genetic controls, the observed effects could be non-specific.
- **Resolution test** Include dose-response experiments for each compound, measuring p53 and p21 levels and cell viability across a range of concentrations. Include a p53-null cell line (e.g., HCT116 p53-/-) or siRNA-mediated p53 knockdown to demonstrate that the effects on p21 and growth are p53-dependent.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The term "p53(Ser46) mutant" is used throughout, but the specific mutation is not defined. It is unclear whether this refers to a Ser46Ala substitution, a Ser46 phosphorylation-deficient mutant, or a different mutation. The authors should specify the exact mutation.
- **Required correction** Define the mutation precisely, e.g., "p53(S46A)" or "p53 with a serine-to-alanine substitution at residue 46", and use this consistently.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 4
- **Evidence pointer** Figure 4A-E
- **Issue** The Western blot images are described but not shown in the text. The authors state that "Blots (A and D) were probed with β-Actin as an internal loading positive control," but the figure legend does not indicate whether the blots are representative or show all replicates. The immunocytochemistry images are described but not quantified.
- **Required correction** Provide representative blot images with molecular weight markers, indicate the number of replicates, and provide quantitative analysis of immunocytochemistry images (e.g., mean fluorescence intensity).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Methods
- **Evidence pointer** Methods section
- **Issue** The authors do not state where the simulation data, trajectories, or analysis scripts can be accessed. This limits reproducibility.
- **Required correction** Add a data availability statement indicating where the computational data and scripts can be accessed, or state that they are available upon request.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reference accuracy
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The statement "Phosphorylation of Ser46 has been reported to be essential for binding of p53 with other cofactors like p300, p62[TFIIH], CBP, GCN5, and PC4" is supported by a single reference (Sullivan et al., 2018). Given the importance of this claim, additional supporting references would strengthen the statement.
- **Required correction** Add additional references to support this claim, or clarify if this is based on a single study.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language precision
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The phrase "Cuc-B and Wi-N showed an increase in binding energy and significant interaction with residues Lys19 and Gln97 which is seen in wildtype p53" is grammatically awkward and ambiguous. It is unclear whether the interaction is "seen in wildtype p53" or "seen in the drug-bound mutant."
- **Required correction** Rewrite for clarity, e.g., "Cuc-B and Wi-N increased the binding energy and restored interactions with Lys19 and Gln97, similar to what is observed in wild-type p53."

## Risk / unsupported claims
- The claim that Wi-N restores a "string-like" conformation in p53 TAD2 is not quantitatively supported by the data presented.
- The claim that the compounds "restore transcriptional activation function" is not directly demonstrated; only p21 and p53 levels are measured, which are indirect markers.
- The claim that Cuc-B has "multimodal p53-activating potential" is not supported by direct evidence of both mechanisms in the same experimental system.
- The statement that "ARC and CAPE failed to establish a stable interaction with p53S46PΔ" is based on visual inspection of RMSD plots without quantitative criteria for stability.
- The claim that the compounds "can restore wild-type p53 activity in Ser46 phospho-deficient mutant, at least in part" is not supported by direct measurement of p53 transcriptional activity in the mutant context.
- The relevance of the computational findings to the cellular context is not established; no structural or biophysical validation (e.g., NMR, ITC, SPR) is provided.