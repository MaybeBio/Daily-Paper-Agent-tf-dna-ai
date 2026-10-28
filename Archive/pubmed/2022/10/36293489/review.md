## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, and interpretation as presented in the provided manuscript
- **Shared manuscript claim summary** The authors use MD simulations and frustration analysis to compare conformational heterogeneity and energy landscape frustration in wild-type p53 and four hotspot mutants (R175H, R248Q, R273H, R282W), reporting mutation-dependent modulation of collective motions and local frustration that correlates with functional regions.
- **Visible evidence base** Abstract, Introduction, Results and Discussion (Sections 2.1-2.3), Computational Methods (Sections 3.1-3.4), Conclusions, Figures 1-11, Tables 1-2
- **Missing materials affecting confidence** No supplementary information, no raw MD trajectory data, no convergence metrics, no error bars on frustration indices, no statistical significance testing, no PDB accession codes for models, no force field validation details

## Reviewer
- **Overall assessment** The manuscript addresses an interesting question regarding how cancer-associated mutations modulate the conformational landscape of p53, a key tumor suppressor. The combination of MD simulations with frustration analysis is appropriate and timely. However, the study is limited by the use of a single monomer model built with medium confidence, short simulation times relative to p53's disorder, and a largely qualitative analysis that lacks statistical rigor. The central claims about mutation-specific effects and functional correlations are plausible but not fully established from the provided evidence.
- **Who would be interested in the results, and why** Researchers studying p53 structure-function relationships, particularly those interested in how hotspot mutations affect conformational dynamics and DNA binding. The frustration analysis approach may also appeal to computational biophysicists working on energy landscape theory and its application to disease-related proteins. The connection between frustration and intrinsic disorder could interest the broader IDP community.
- **Major strengths** The study addresses a clinically relevant problem using a physically motivated framework (frustration theory). The comparison across multiple mutants within a consistent computational pipeline is a reasonable strategy. The qualitative correlation between high frustration and collective motions is an interesting observation that could stimulate further work. The authors appropriately acknowledge the limitations of their monomer model and the need for experimental validation.
- **Major Concerns** The modeling strategy relies on a medium-confidence I-TASSER model for the full-length monomer, which may not accurately represent the conformational ensemble of p53. The simulation length (150 ns per run) is short for a protein with significant intrinsic disorder, and no convergence analysis is provided. The frustration analysis is performed on only the last 10 ns of each trajectory, which may not be representative. The comparison between mutants is largely qualitative, with no statistical testing or error analysis. The claim that frustration correlates with collective motions is based on visual inspection rather than quantitative correlation.
- **Minor Comments** The manuscript would benefit from a clearer description of how the five independent runs were used in the analysis. The choice of the specific frustration index threshold (0.6 nm) for marking displacements is not justified. The discussion of GOF is speculative and could be better grounded in experimental literature. Some figure labels are not fully explained in the text.
- **Technical failings that need to be addressed before the case is established** R1-M1 (model quality), R1-M2 (simulation convergence), R1-M3 (statistical rigor), R1-M4 (quantitative correlation)
- **Assessment against Nature-style criteria** Originality: Moderate. The application of frustration analysis to p53 mutants is relatively novel, but the overall approach is not groundbreaking. Scientific importance: High for the p53 field, but the conclusions are limited by methodological constraints. Interdisciplinary readership: The topic could appeal to structural biologists, biophysicists, and cancer researchers, but the presentation is somewhat specialized. Technical soundness: The methods are standard, but the implementation has notable weaknesses as detailed above. Readability for nonspecialists: The manuscript is generally clear, but some sections assume familiarity with MD and frustration theory.
- **Recommendation posture** Currently not established from the provided evidence. The study has merit, but the technical concerns regarding model quality, simulation convergence, and statistical rigor must be addressed before the claims can be considered robust.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validity
- **Claim pointer** The authors claim that their model provides "a realistic starting point for the MD simulation to investigate the intrinsic flexibility of p53" (Section 3.1).
- **Evidence pointer** Section 3.1, Figure 1
- **Concern** The full-length p53 monomer model is built using I-TASSER with a C-score of 2.37 and TM score of 0.44-0.14, which the authors themselves describe as "medium confidence." The model is based on the DBD structure from 1TUP, but the NTD and CTD are predicted de novo. Given that p53 is intrinsically disordered in these regions, the predicted structures may not represent the actual conformational ensemble. The authors do not validate the model against experimental data (e.g., SAXS, NMR chemical shifts) or compare with other available full-length p53 models.
- **Why it matters** The entire analysis depends on the quality of the starting structure. If the model is not representative, the MD trajectories and subsequent frustration analysis may not reflect the true behavior of p53. This is particularly critical for the disordered regions, which are central to the authors' claims about functional correlations.
- **Resolution test** Provide validation of the model against experimental data, or use multiple independent starting structures (e.g., from different modeling approaches or experimental ensembles) to demonstrate that the results are robust to model choice.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Simulation convergence
- **Claim pointer** The authors state that "the last 100 ns of the runs have been used for the data collection" (Section 2.1) and that the frustration analysis is based on "100 snapshots sampled in the last 10 ns" (Section 3.4).
- **Evidence pointer** Sections 2.1, 3.2, 3.4, Figure 2
- **Concern** No convergence analysis is provided. The RMSD plots (Figure 1B) show a "rapid increase" in the first 5 ns and a "slower increase" completed within 50 ns, but it is unclear whether the systems have truly equilibrated by 50 ns, especially for a protein with large disordered regions. The frustration analysis is based on only the last 10 ns of each trajectory, which may be too short to sample the relevant conformational states, particularly for mutants with altered dynamics. No block averaging or autocorrelation analysis is shown to demonstrate that the properties are stable over the analysis window.
- **Why it matters** If the simulations are not converged, the reported properties (RMSD, RMSF, frustration indices) may be biased by the initial conditions and not representative of the equilibrium ensemble. This undermines the reliability of the comparisons between wild-type and mutants.
- **Resolution test** Provide convergence metrics (e.g., RMSD vs. time for multiple blocks, autocorrelation times for key observables) and extend the analysis window if necessary. Show that the frustration indices are stable when computed over different time windows.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors report differences in RMSD, RMSF, and frustration indices between wild-type and mutants (Sections 2.1-2.3, Tables 1-2), and state that "punctual mutations can significantly modulate frustration" (Section 2.3).
- **Evidence pointer** Tables 1-2, Figures 3-11
- **Concern** The manuscript reports average values and standard deviations for some properties (Table 1), but no statistical significance testing is performed. For the frustration indices, only a single value is reported for each system (Table 2), with no error estimate. The qualitative comparisons between mutants (e.g., "wider collective motions" for R248Q) are based on visual inspection of figures, with no quantitative measure of uncertainty. The five independent runs are mentioned, but it is unclear how they are used in the analysis (e.g., are the reported values averages over runs? Are the standard deviations across runs?).
- **Why it matters** Without error estimates and significance testing, it is impossible to determine whether the observed differences between wild-type and mutants are meaningful or within the noise of the simulations. This is essential for supporting the claim that mutations modulate frustration and collective motions.
- **Resolution test** Report the frustration indices with standard deviations across the five runs and perform appropriate statistical tests (e.g., t-test or ANOVA) to compare wild-type and mutants. Provide error bars on all reported quantities and clarify how the five runs are combined.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative correlation
- **Claim pointer** The authors state that "regions characterized by wide collective motions are also characterized by a high frustration level" (Section 2.3) and that this correlation "suggests a close interplay between these two aspects."
- **Evidence pointer** Sections 2.2-2.3, Figures 4-11
- **Concern** The correlation between frustration and collective motions is based on qualitative visual comparison of figures (e.g., comparing Figure 4A with Figure 7). No quantitative measure is provided, such as a correlation coefficient between per-residue frustration indices and per-residue displacement amplitudes from the ED analysis. The authors also do not test whether this correlation is statistically significant or specific to certain regions.
- **Why it matters** The claimed correlation is a central finding of the paper, but without quantitative support, it remains an anecdotal observation. A rigorous analysis would strengthen the case for a mechanistic link between frustration and dynamics.
- **Resolution test** Compute per-residue frustration indices and per-residue RMSF or displacement values from the first few eigenvectors, and calculate a correlation coefficient (e.g., Spearman's rho) with a significance test. Report the results for all systems.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1, Table 1
- **Evidence pointer** Table 1
- **Issue** The table reports "average and the corresponding standard deviation" for RMSD, SASA, and Rg, but it is unclear whether these are averages over time, over the five runs, or both. The text does not clarify the exact procedure.
- **Required correction** Specify in the table caption or text how the averages and standard deviations are computed (e.g., "averaged over the last 100 ns of each of the five independent runs, with standard deviation across runs").

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Justification
- **Affected element** Section 2.2, Figure 3
- **Evidence pointer** Figure 3
- **Issue** The choice of the first 10 eigenvalues for the analysis (Table 2) is not justified. It is unclear why 10 was chosen and whether the results are sensitive to this cutoff.
- **Required correction** Provide a brief justification for the cutoff, or show that the results are robust to the number of included eigenvectors.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 2.3, Figures 6-11
- **Evidence pointer** Figures 6-11
- **Issue** The labeling of clusters (C1-C6, O1-O5) is described in the text, but the figures are not always easy to interpret. The relationship between the clusters and specific structural features (e.g., secondary structure elements, binding sites) could be made clearer.
- **Required correction** Add annotations to the figures or a supplementary table that maps each cluster to the corresponding residues and structural features.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.2
- **Evidence pointer** Section 3.2
- **Issue** The manuscript states that "five independent runs were performed" but does not specify how the initial velocities were generated or whether the runs were started from the same or different initial structures.
- **Required correction** Provide details on the initialization of the independent runs (e.g., different random seeds, different initial velocities) to ensure reproducibility.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Section 1, Introduction
- **Evidence pointer** Section 1
- **Issue** The introduction mentions that p53 is an IDP and that frustration is relevant, but it does not discuss prior computational studies of p53 dynamics or frustration in other IDPs. This limits the novelty of the work in context.
- **Required correction** Add a brief review of previous MD studies on p53 and frustration analyses of other IDPs to position the current work within the existing literature.

## Risk / unsupported claims
- The claim that "punctual mutations can significantly modulate frustration" is unsupported due to lack of error estimates and statistical testing.
- The claim that "regions characterized by wide collective motions are also characterized by a high frustration level" is unsupported due to lack of quantitative correlation analysis.
- The claim that "the investigated mutations do not drastically affect the global dynamics of p53" is based on qualitative comparison and lacks statistical support.
- The statement that "wider collective motions are detected for p53R248Q" is based on visual inspection and is not quantitatively verified.
- The speculation that "high frustration could be the result of an evolution to fulfil their functional role" is not directly supported by the data presented.
- The assertion that "the loss of frustration could be related to a decrease in the p53R175H functionality" is speculative and not tested.