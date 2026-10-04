## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The authors report molecular dynamics simulations of 22 cancer hotspot mutations across 10 oncogene families, modeled as histone-DNA complexes. They claim that thermodynamic effects are predominantly localized within 6 Å of the DNA-histone interface (mean capture 104%), that van der Waals interactions dominate at thermodynamic extremes, that RAS family mutations stabilize nucleosomes (mean ΔΔG = −4.82 kcal mol⁻¹) while kinase domain mutations destabilize them (mean ΔΔG = +40.12 kcal mol⁻¹), and that this difference is statistically significant (Mann-Whitney U, p = 0.008). They propose an interface-specific mechanism and a gene-family-correlated thermodynamic pattern as a biophysical framework for cancer hotspot biology.
- **Visible evidence base** Abstract text only. No methods, simulation parameters, force fields, system setup, convergence criteria, error estimates, statistical details, or raw data are available.
- **Missing materials affecting confidence** Full manuscript, methods section, simulation protocols, force field parameters, system construction details, convergence and equilibration data, uncertainty quantification, statistical analysis details, figures, tables, and any supplementary information. Without these, the quantitative claims cannot be independently assessed.

## Reviewer
- **Overall assessment** The abstract presents an intriguing hypothesis that oncogenic mutations may exert their effects through localized thermodynamic perturbations at the nucleosome-DNA interface, with a gene-family-correlated pattern. However, the evidence base provided is insufficient to evaluate the validity of the central claims. Key methodological details are absent, the reported ΔΔG values raise concerns about sign conventions and physical plausibility, and the statistical analysis appears underpowered for the conclusions drawn. The work has potential interest but is not currently established from the supplied material.
- **Who would be interested in the results, and why** Researchers in cancer genomics, chromatin biology, and biophysical simulation would be interested. The claim of a gene-family-correlated thermodynamic signature at nucleosome interfaces could inform hypotheses about mutation hotspot selection and chromatin-level effects of oncogenic drivers. Computational biophysicists studying protein-DNA interactions may also find the methodological approach relevant.
- **Major strengths** The study addresses a timely and underexplored question, namely the biophysical basis of cancer mutation hotspots at the nucleosome level. The comparative design across multiple oncogene families is a reasonable exploratory strategy. The focus on local interface effects rather than global structural changes is a testable and mechanistically meaningful hypothesis.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4  
  - R1-M5
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1 (sign and magnitude of ΔΔG values), R1-M2 (statistical validity), R1-M3 (missing methodological detail), R1-M4 (physical plausibility of the mechanism), R1-M5 (generalizability of the hotspot selection)
- **Assessment against Nature-style criteria**  
  - Originality: The hypothesis is moderately original, applying thermodynamic simulation to cancer hotspot mutations in a nucleosome context. However, the conceptual framework of local versus global effects is not new in protein biophysics.  
  - Scientific importance: Potentially high if the claims hold, as it could link mutation hotspots to chromatin-level thermodynamics. However, the current evidence does not establish this.  
  - Interdisciplinary readership: The topic bridges cancer biology and computational biophysics, which could attract a broad audience, but the abstract is too technical and under-supported for nonspecialists to evaluate.  
  - Technical soundness: Not assessable from the abstract alone. The reported values and statistical approach raise concerns that require full methods.  
  - Readability for nonspecialists: The abstract is dense and assumes familiarity with ΔΔG conventions and MD simulation. The sign convention issue would confuse most readers.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is interesting and warrants a full review of the complete manuscript, but the abstract alone does not support the central claims.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Quantitative claim validity  
- **Claim pointer** The abstract reports mean ΔΔG = −4.82 kcal mol⁻¹ for RAS family mutations (stabilization) and mean ΔΔG = +40.12 kcal mol⁻¹ for kinase domain mutations (destabilization).  
- **Evidence pointer** Abstract, results section (location not provided)  
- **Concern** The sign convention for ΔΔG is not defined. In standard biophysical usage, a negative ΔΔG for a mutation typically indicates destabilization of the bound state relative to the unbound state, not stabilization. The abstract states that RAS mutations stabilize nucleosomes with a negative ΔΔG, which is counter to common convention. Additionally, the magnitude of +40.12 kcal mol⁻¹ for kinase mutations is extraordinarily large for a single point mutation effect on binding free energy, exceeding typical values by an order of magnitude.  
- **Why it matters** If the sign convention is reversed or the magnitudes are erroneous, the entire interpretation of the results changes. A reader cannot evaluate the biological meaning of the claims without clarity on this fundamental point.  
- **Resolution test** The authors must define the ΔΔG sign convention explicitly and provide per-mutation values with error bars. The +40 kcal mol⁻¹ value must be reconciled with known physical limits for single-residue effects on protein-DNA binding.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical validity  
- **Claim pointer** The abstract claims a statistically significant difference between RAS and kinase family effects (Mann-Whitney U, p = 0.008).  
- **Evidence pointer** Abstract, results section (location not provided)  
- **Concern** With only 22 mutations total across 10 families, the subgroup sizes for RAS and kinase families are likely very small (possibly 2-4 per group). A Mann-Whitney U test with such small sample sizes can yield low p-values by chance, and the abstract does not report effect sizes, confidence intervals, or correction for multiple comparisons across 10 families.  
- **Why it matters** The gene-family-correlated pattern is a central claim of the paper. If the statistical evidence is fragile, the conclusion of a family-dependent thermodynamic signature is not supported.  
- **Resolution test** Provide the number of mutations per family, the full distribution of ΔΔG values, effect sizes with confidence intervals, and a multiple-comparison correction. A permutation-based test or Bayesian analysis would be more appropriate for small samples.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological transparency  
- **Claim pointer** The abstract describes molecular dynamics simulations of histone-DNA complexes but provides no methodological detail.  
- **Evidence pointer** Abstract, methods section (not provided)  
- **Concern** No information is given on the simulation software, force field, water model, salt concentration, simulation length, number of replicas, equilibration protocol, or convergence criteria. Free energy calculations (e.g., MM-PBSA, FEP, TI) are highly sensitive to these choices. Without this information, the reported ΔΔG values cannot be reproduced or evaluated.  
- **Why it matters** The central quantitative claims depend entirely on the simulation methodology. If the methods are not standard or are underpowered, the results are not credible.  
- **Resolution test** Provide a full methods section with all simulation parameters, convergence checks, and validation against experimental data where available.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Mechanistic interpretation  
- **Claim pointer** The abstract claims that thermodynamic effects are predominantly localized within 6 Å of the DNA-histone interface (mean capture 104%) and that van der Waals interactions drive the effect at thermodynamic extremes.  
- **Evidence pointer** Abstract, results section (location not provided)  
- **Concern** The term "mean capture 104%" is undefined and confusing. It is unclear what is being captured and why the mean exceeds 100%. The claim that van der Waals interactions dominate at "thermodynamic extremes" is vague, as it does not specify which extremes or how this was determined.  
- **Why it matters** These claims are presented as key mechanistic findings, but they are not interpretable from the abstract. The reader cannot assess whether the localization analysis is meaningful or whether the van der Waals claim is supported.  
- **Resolution test** Define "mean capture" precisely, provide the spatial resolution of the analysis, and specify the criteria for "thermodynamic extremes." Show per-mutation decomposition of energy contributions.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** No  
- **Axis** Generalizability  
- **Claim pointer** The abstract implies that the 22 hotspots across 10 oncogene families are representative of cancer hotspot mutations broadly.  
- **Evidence pointer** Abstract, introduction and results (location not provided)  
- **Concern** The selection criteria for the 22 hotspots and 10 families are not described. It is unclear whether these were chosen randomly, based on prevalence, or for convenience. The abstract does not discuss how the findings might generalize to other hotspots or families.  
- **Why it matters** The broader claim of a "biophysical framework for understanding nucleosome-level contributions to cancer hotspot mutation biology" requires that the sample is representative or at least that limitations are acknowledged.  
- **Resolution test** Describe the selection criteria, discuss potential selection bias, and temper the generalizability claims to the specific families studied.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract, first sentence  
- **Evidence pointer** Abstract, introduction (location not provided)  
- **Issue** The phrase "non-random rates and specific hotspots" is redundant and could be streamlined.  
- **Required correction** Revise to "Oncogenic mutations occur at non-random rates and cluster at specific hotspots."

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Units and notation  
- **Affected element** Abstract, results  
- **Evidence pointer** Abstract, results section (location not provided)  
- **Issue** The units "kcal mol -1 " are written with a space before the superscript, which is nonstandard.  
- **Required correction** Use "kcal mol⁻¹" consistently.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Statistical reporting  
- **Affected element** Abstract, results  
- **Evidence pointer** Abstract, results section (location not provided)  
- **Issue** The p-value is reported without any measure of effect size or confidence interval.  
- **Required correction** Add effect size (e.g., rank-biserial correlation) and a confidence interval for the difference.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** Abstract, results  
- **Evidence pointer** Abstract, results section (location not provided)  
- **Issue** The term "thermodynamic extremes" is used without definition.  
- **Required correction** Define what constitutes an extreme in this context, or replace with a more precise description.

## Risk / unsupported claims
- The claim that thermodynamic effects are "predominantly localized to within 6 Å" is unsupported without spatial analysis details.
- The claim that van der Waals interactions drive effects at "thermodynamic extremes" is unsupported without energy decomposition data.
- The claim of a statistically significant family-correlated pattern is unsupported without sample sizes and effect sizes.
- The reported ΔΔG values, particularly +40.12 kcal mol⁻¹, are not physically plausible without additional context and are therefore unsupported.
- The generalizability of the findings to cancer hotspot biology broadly is unsupported given the lack of selection criteria and limited family coverage.