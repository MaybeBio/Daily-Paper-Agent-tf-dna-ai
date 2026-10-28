## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) with figures referenced but not provided
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and internal consistency based solely on the supplied text
- **Shared manuscript claim summary** The authors propose that protein-protein interactions (PPIs) can be classified into two paradigms: a static paradigm where affinity is rankable from static co-crystal structures, and a dynamic paradigm where affinity ranking requires molecular dynamics (MD) sampled ensembles. They argue that local frustration analysis of the binding interface provides a mechanistic link between interfacial dynamics and binding funnel topography, and that this framework can guide the choice of affinity prediction strategy.
- **Visible evidence base** Abstract, full introduction, full methods (sections 2.1-2.6), full results (sections 3.1-3.5), full discussion, full conclusions, figure legends referenced but figures not provided, supplementary figures referenced but not provided
- **Missing materials affecting confidence** All figures (Figs. 1-7), all supplementary figures (Figs. S1-S11), all supplementary tables (Tables S1-S2), raw data, simulation input files, and code repository contents. Without these, quantitative claims cannot be independently verified.

## Reviewer

- **Overall assessment** This manuscript addresses a significant and timely question in computational biophysics: why static structure-based affinity prediction fails for some PPI systems and succeeds for others. The authors identify two well-controlled nanobody-antigen datasets that appear to exemplify distinct binding paradigms, and they propose local frustration as a mechanistic and predictive descriptor. The conceptual framework is appealing and potentially impactful. However, the evidence presented in the text alone is insufficient to establish the central claims. Key quantitative results are described but not shown, the statistical treatment is not described, and the generalizability claim rests on a single additional example pair. The manuscript would benefit from substantial revision and additional analysis before it could be considered for a high-impact venue.

- **Who would be interested in the results, and why** Computational biophysicists and structural biologists working on protein-protein interaction prediction, affinity engineering, and drug design would be the primary audience. The proposed framework for deciding when MD-based sampling is necessary could have practical implications for antibody and nanobody engineering pipelines. Researchers interested in energy landscape theory and its application to biomolecular recognition would also find the conceptual framing relevant.

- **Major strengths**
  1. The identification of two nanobody-antigen datasets with near-identical binding modes but divergent affinity prediction behavior is a clever and potentially powerful experimental design.
  2. The conceptual unification of static and dynamic binding paradigms under a single frustration-based framework is intellectually appealing and could provide practical guidance.
  3. The use of multiple computational methods (Rosetta, FireDock, Bluues, ZDock, IRAD) for cross-validation of the static scoring failure is commendable.
  4. The temperature-dependent MD analysis and the convergence checks (triplicate runs) indicate attention to methodological rigor.
  5. The validation attempt on an independent nanobody pair (Nb1/Nb6) is a positive step toward demonstrating generalizability.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "the 2P4X series, the static co-crystal structures are sufficient to rank the experimental affinity, with co-efficient r=0.80" and "for the 7Z1X series, the static-structure based co-efficient r= -0.41" and that MD-ensemble based scoring yields r=0.82 for 7Z1X and r=0.29 for 2P4X.
- **Evidence pointer** Section 3.2, Fig. 3 (not provided)
- **Concern** The central quantitative claims of the paper rest on correlation coefficients that are reported in the text but not shown in any visible figure or table. Without the actual scatter plots, correlation analyses, or statistical significance tests, it is impossible to assess whether these correlations are robust, whether outliers drive the results, or whether the differences between static and dynamic paradigms are statistically meaningful. The sample sizes are small (9 and 10 nanobodies respectively), and no confidence intervals or p-values are reported.
- **Why it matters** The entire thesis of the manuscript depends on the reliability and significance of these correlation coefficients. If the correlations are not statistically robust, the proposed paradigm distinction collapses.
- **Resolution test** Provide the actual data points, scatter plots with regression lines, correlation coefficients with confidence intervals, and appropriate statistical tests (e.g., Spearman rank correlation, permutation tests) for both static and MD-based scoring across both series.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validity
- **Claim pointer** The authors claim that "local frustration analysis establishes a mechanistic bridge between interfacial dynamics and landscape topology" and that "dynamic interfaces exhibit increased frustration upon thermal sampling."
- **Evidence pointer** Section 3.4, Fig. 5 (not provided)
- **Concern** The frustration analysis is described qualitatively in the text, but the actual quantitative results are not presented. The claim that MD sampling increases frustration in the dynamic series but not the static series is central to the mechanistic argument, yet no numerical values, statistical comparisons, or effect sizes are provided. Additionally, the frustratometeR software is used with "default parameters" but the specific parameters and their appropriateness for nanobody-antigen interfaces are not discussed.
- **Why it matters** The frustration analysis is the proposed mechanistic bridge and the basis for the practical diagnostic tool. Without quantitative evidence, the claim that frustration patterns distinguish static from dynamic paradigms is unsupported.
- **Resolution test** Provide the frustration values (percentage of highly frustrated pairs) for each nanobody in each series, for both PDB and MD-derived structures, with appropriate statistical comparisons (e.g., t-tests or non-parametric equivalents) between series and between PDB vs. MD conditions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validity
- **Claim pointer** The authors claim that "the relative motion between binding partners (Δ RMSF) is temperature-sensitive, with optimal affinity correlation at 298 K" for the dynamic series, and that "in the static series, Δ RMSF is minimal and insensitive to temperature."
- **Evidence pointer** Section 3.3, Fig. 4 (not provided)
- **Concern** The temperature-dependent behavior of Δ RMSF is described as showing a nonmonotonic relationship with an optimum near 295-300 K, but the actual data are not shown. The quadratic fit (R² = 0.757) is mentioned but the fit parameters, residuals, and the number of data points are not provided. More critically, the claim that the optimal correlation at 298 K reflects physical sampling of functional microstates, rather than an artifact of the scoring function or simulation protocol, is not rigorously tested. The authors do not compare against alternative explanations, such as force field accuracy at different temperatures or the temperature dependence of the Rosetta scoring function itself.
- **Why it matters** The temperature dependence is used to argue that the dynamic paradigm requires sampling at the physiologically relevant temperature. If this is an artifact of the computational protocol, the entire framework is compromised.
- **Resolution test** Provide the full temperature-dependent correlation data, the Δ RMSF values at each temperature for each nanobody, and control analyses (e.g., scoring with a different force field or scoring function, or testing whether the temperature optimum shifts with different simulation lengths).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability
- **Claim pointer** The authors claim that "applying the conceptual framework to Nb1 and Nb6 successfully identified their dynamic and static binding natures" and that this "demonstrates that our findings... are applicable to additional nanobody PPIs."
- **Evidence pointer** Section 4, Fig. S11 (not provided)
- **Concern** The generalizability claim rests on a single additional example pair (Nb1/Nb6). While this is a reasonable first step, it is insufficient to establish broad applicability. The authors do not discuss how the framework would perform on a diverse set of PPIs with varying interface sizes, chemistries, or flexibilities. The selection criteria for these additional nanobodies are not described, and there is no discussion of potential failure modes or limitations of the frustration-based classification.
- **Why it matters** The practical value of the proposed framework depends on its generalizability beyond the two primary datasets. A single validation example is anecdotal evidence, not systematic validation.
- **Resolution test** Apply the frustration-based classification to a larger, diverse set of PPI systems with known binding thermodynamics and dynamics, and report sensitivity, specificity, and predictive accuracy.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Data quality and curation
- **Claim pointer** The authors state that they "collected all reported nanobody-antigen co-crystal structures with experimental affinity measurements from the SAbDab-nano database" and supplemented with 10 additional data points, yielding 83 structures for analysis.
- **Evidence pointer** Section 2.1, Table S1 (not provided)
- **Concern** The curation process is described only briefly. The criteria for including or excluding structures are not stated, and the handling of multiple measurements for the same nanobody-antigen pair, different experimental conditions, or conflicting affinity values is not described. The conversion of Kd to ΔG uses the equation ΔG = RT ln(Kd), but the temperature at which Kd was measured is not consistently reported, and the authors do not discuss the potential impact of assay type (e.g., SPR vs ITC) on the reliability of the affinity values.
- **Why it matters** The quality of the experimental affinity data underpins all correlation analyses. Inconsistent or unreliable affinity measurements could produce spurious correlations or mask real ones.
- **Resolution test** Provide a detailed curation protocol, including inclusion/exclusion criteria, handling of duplicate or conflicting measurements, and a sensitivity analysis showing that the main conclusions are robust to reasonable variations in the curation choices.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1, equation for ΔG conversion
- **Evidence pointer** Section 2.1
- **Issue** The equation for converting Kd to ΔG is mentioned but not explicitly written out in the text. The sentence reads "we converted Kd values to binding free energies (ΔG exp) via: where R is the gas constant..." with the equation apparently missing or not rendered.
- **Required correction** Ensure the equation is explicitly displayed and correctly formatted.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Section 3.3 vs. Section 3.2
- **Evidence pointer** Section 3.2, Section 3.3
- **Issue** In Section 3.2, the optimal correlation for the 7Z1X series is reported as r=0.82 from MD-based scoring. In Section 3.3, the optimal correlation is stated to occur at 295 K (r=0.90) and 300 K (r=0.81). It is unclear whether the r=0.82 in Section 3.2 corresponds to the 300 K simulation or to an average across temperatures. This ambiguity should be clarified.
- **Required correction** State explicitly which temperature (or temperature range) was used for the MD-based scoring reported in Section 3.2, and ensure consistency with Section 3.3.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.4, MD simulation details
- **Evidence pointer** Section 2.4
- **Issue** The methods state that 100 ns production simulations were performed, but the equilibration protocol, the number of replicates (beyond the triplicate runs at 295, 300, 305 K), and the criteria for assessing convergence are not fully described. The authors mention "RMSD analysis from 100 ns MD simulations shows that the modeled structures are comparably stable to co-crystal structures (Fig. S1)" but do not describe how this stability was quantified.
- **Required correction** Provide additional details on the equilibration protocol, convergence criteria, and the specific RMSD values and their uncertainties.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Section 3.5, hotspot analysis
- **Evidence pointer** Section 3.5, Fig. 6 (not provided)
- **Issue** The hotspot analysis uses a threshold of |ΔΔG| >= 1 kcal/mol to classify residues as hotspots. The choice of this threshold is not justified, and the sensitivity of the conclusions to this threshold is not explored. Additionally, the statistical significance of the difference in hotspot percentages between the two series (75% vs. 41.2%) is not assessed.
- **Required correction** Justify the threshold choice, provide a sensitivity analysis, and report appropriate statistical tests for the comparison between series.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.6, frustration analysis
- **Evidence pointer** Section 2.6
- **Issue** The frustratometeR package is cited, but the specific version, the parameters used for the frustration calculation (e.g., the number of decoys, the energy function), and the definition of "interface center" are not fully specified. The radial distribution function calculation is described but the bin size and the range of distances analyzed are not stated.
- **Required correction** Provide complete parameter specifications and software versions to ensure reproducibility.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.1, Fig. 2
- **Evidence pointer** Section 3.1, Fig. 2 (not provided)
- **Issue** The text states that "a well-formed binding funnel is characterized by a strong correlation between iRMS and interface energy" but the specific correlation coefficient or statistical measure used to classify funnels is not defined. The criteria for classifying a structure as "funneled" vs. "non-funneled" are not stated quantitatively.
- **Required correction** Define the quantitative criteria used to classify funnels and report the values for the 78 funneled and 5 non-funneled structures.

## Risk / unsupported claims
- The claim that "static and dynamic binding paradigms" are general features of PPI systems is not supported by the evidence presented, which is limited to two nanobody-antigen series and one additional pair.
- The claim that "local frustration is the underlying determinant of interfacial dynamics" is asserted but not rigorously established; the correlation between frustration and dynamics does not demonstrate causation.
- The claim that "room temperature provides the appropriate thermal energy to sample the functional ensemble" is based on a single observation of optimal correlation near 298 K and requires additional validation.
- The claim that the modeled structures for the 7Z1X series (generated via SWISS-MODEL) are reliable proxies for experimental structures is not fully supported; the validation is limited to RMSD stability over 100 ns, which does not guarantee that the modeled conformations are biologically relevant.
- The generalizability of the frustration-based classification framework to non-nanobody PPIs is entirely unaddressed and cannot be assessed from the provided material.