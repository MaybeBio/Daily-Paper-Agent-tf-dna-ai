## Review setup

- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and supplementary information sections as provided.
- **Assessment boundary** Scientific validity, methodological soundness, interpretation of results, and alignment with stated claims. Editorial and formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors use mD-VcMD enhanced sampling simulations to compute free-energy landscapes for binding of ribocil A (non-binder) and ribocil B (binder) to the FMN riboswitch aptamer domain. They report a funnel-like free-energy landscape for ribocil B and a rugged landscape for ribocil A, identify two potential binding pathways through front and rear gates, and propose that non-native π-π stacking stabilizes an encounter complex that facilitates binding.
- **Visible evidence base** Main text figures (Figures 1-7), supplementary figures referenced (Figures S1-S12), supplementary tables (Tables S1-S4), and methods descriptions. No raw simulation trajectories, force field parameter files, or convergence diagnostics beyond those described in the text were available for direct inspection.
- **Missing materials affecting confidence** The following were not available for verification: (1) the actual free-energy values and error bars for the reported landscapes, (2) the complete set of simulation parameters and input files, (3) the full convergence analysis data beyond the summary provided, (4) the specific atom group definitions in Table S1, (5) the force field parameter validation for the ribocil ligands, and (6) the raw data underlying Figures 2-7.

## Reviewer

- **Overall assessment** This manuscript presents a computationally intensive study of ligand binding to an RNA riboswitch using an enhanced sampling method. The central observation that the free-energy landscape differs between a binder and non-binder pair of optical isomers is potentially interesting. However, the manuscript has several significant weaknesses that currently prevent the conclusions from being fully established. The most critical issues are: (1) the lack of quantitative free-energy comparisons between the two systems, (2) the absence of a clear statistical error analysis, (3) the limited discussion of force field accuracy for the specific RNA-ligand interactions, and (4) the speculative nature of the proposed binding mechanism without direct kinetic evidence. The work may be of interest to computational biophysicists and RNA biologists, but the current presentation does not provide sufficient evidence to support all claims made.
- **Who would be interested in the results, and why** Computational chemists and biophysicists working on ligand-RNA interactions would find the application of mD-VcMD to an RNA system of interest. Researchers studying riboswitch mechanisms, particularly the FMN riboswitch as a potential antibiotic target, would be interested in the proposed binding pathways and the role of non-native stacking. Methodologists developing enhanced sampling techniques may also find the application to a binder/non-binder pair useful as a test case. However, the impact would be substantially increased if the authors provided more quantitative comparisons and addressed the force field limitations more thoroughly.
- **Major strengths** (1) The study addresses a biologically relevant question about differential binding of structurally similar compounds to an RNA target. (2) The use of mD-VcMD with multiple reaction coordinates is appropriate for exploring ligand binding pathways. (3) The identification of two potential entry pathways (front and rear gates) is a novel observation that could stimulate further experimental work. (4) The authors are transparent about the limitations of their force field and sampling, and they provide access to representative structures via BSM-Archives. (5) The convergence analysis using the E_local function is a reasonable approach, although more detail would be helpful.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative support for central claim
- **Claim pointer** The authors claim that the free-energy landscape of ribocil B binding is "funnel-like" while that of ribocil A is "rugged," and that this difference "agrees qualitatively with an experiment" showing ribocil B binds more strongly.
- **Evidence pointer** Figures 2 and 4, Section 3.1, Section 3.2
- **Concern** The central claim of differential binding is supported only by qualitative visual inspection of density contours. No quantitative free-energy differences are reported. Specifically, the authors do not provide: (a) the free-energy difference between the bound and unbound states for each system, (b) the free-energy barrier heights for binding/unbinding, or (c) any statistical uncertainty estimates for these quantities. The statement that the landscapes "agree qualitatively with an experiment" is not supported by any quantitative comparison, such as computed binding free energies versus experimental Kd values. Without these numbers, the reader cannot assess whether the observed difference between ribocil A and B is statistically significant or biologically meaningful.
- **Why it matters** The primary conclusion of the paper rests on the claim that the two systems have qualitatively different free-energy landscapes. If this difference is within statistical error or is an artifact of the force field, the main conclusion would be invalidated. Quantitative free-energy values are essential for the reader to evaluate the significance of the findings and to compare with experimental data.
- **Resolution test** The authors should provide: (1) the computed free-energy difference between bound and unbound states for both systems with error bars, (2) the barrier heights for the binding pathways, and (3) a quantitative comparison with experimental binding affinities if available. If the free-energy difference between ribocil A and B is small relative to the estimated error, the claim of differential binding should be moderated accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Force field validation for ligand parameters
- **Claim pointer** The authors state that "Force field parameters for ribocil A and B were modeled by us" using RESP charges at HF/6-31G* level and GAFF2 parameters.
- **Evidence pointer** Section 2.1, no validation data provided
- **Concern** The ligand force field parameters are custom-generated, but no validation is presented. The authors do not show: (1) comparison of the generated parameters with any experimental or high-level quantum mechanical data, (2) tests of the ligand conformational preferences against known structures, or (3) sensitivity analysis of the results to parameter choices. Given that the central conclusion depends on subtle differences between two optical isomers, the accuracy of the ligand force field is critical. The authors acknowledge this concern in the Discussion but do not provide any quantitative assessment of the potential impact.
- **Why it matters** The observed difference between ribocil A and B could be an artifact of the force field rather than a real physical effect. Without validation, the reader cannot determine whether the computed free-energy landscapes are reliable. This is particularly important because π-π stacking interactions, which are central to the proposed mechanism, are known to be challenging for classical force fields.
- **Resolution test** The authors should provide: (1) validation of the ligand parameters against quantum mechanical calculations or experimental data, (2) a discussion of the known limitations of GAFF2 for describing π-π interactions, and (3) ideally, a sensitivity analysis showing that the main conclusions are robust to reasonable parameter variations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Statistical analysis and error estimation
- **Claim pointer** The authors report free-energy landscapes and density distributions without any statistical uncertainty estimates.
- **Evidence pointer** Figures 2-7, Sections 3.1-3.5
- **Concern** No error bars, confidence intervals, or statistical tests are provided for any of the reported quantities. The manuscript does not describe how many independent simulations were performed, how the data were block-averaged, or how the statistical quality of the free-energy estimates was assessed. The convergence analysis using E_local is mentioned but not shown in sufficient detail to evaluate whether the sampling was adequate in all relevant regions of the configurational space.
- **Why it matters** Enhanced sampling methods can produce biased results if the sampling is insufficient or if the reweighting procedure is not properly converged. Without error estimates, the reader cannot distinguish between genuine physical differences and statistical noise. This is especially important for the comparison between ribocil A and B, where the differences may be subtle.
- **Resolution test** The authors should provide: (1) error estimates for the free-energy values, (2) a description of the statistical analysis methods used, and (3) a more detailed presentation of the convergence diagnostics, including how the E_local criterion was applied and what fraction of the relevant configurational space met the criterion.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of the rear gate pathway
- **Claim pointer** The authors state that "the simulation showed another pathway, which also led the ligands to the binding site" through a rear gate, and that this pathway requires overcoming a free-energy barrier with large ligand rotation.
- **Evidence pointer** Figures 4-6, Section 3.5
- **Concern** The biological relevance of the rear gate pathway is unclear. The authors note that this pathway is "not important biophysically" because of the high barrier, yet they spend considerable space discussing it. The connection to the "ligand orientation selection mechanism exerted by a membrane protein" appears speculative and is not developed into a testable hypothesis. The authors do not provide quantitative estimates of the flux through each pathway or the relative probability of rear versus front gate entry.
- **Why it matters** The paper would be strengthened by a clearer focus on the biologically relevant binding pathway. If the rear gate pathway is negligible, its detailed characterization may distract from the main findings. Alternatively, if the rear gate pathway is relevant, the authors should provide quantitative evidence for its importance.
- **Resolution test** The authors should either: (1) provide quantitative estimates of the relative importance of the two pathways (e.g., flux calculations or free-energy comparisons), or (2) clearly state that the rear gate pathway is a minor route and focus the discussion on the front gate pathway.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Comparison with experimental data
- **Claim pointer** The authors claim their results "agree qualitatively with an experiment" regarding the differential binding of ribocil A and B.
- **Evidence pointer** Section 3.4, Discussion
- **Concern** The comparison with experiment is vague. The authors do not provide specific experimental binding affinities or kinetic data for ribocil A and B to the FMN riboswitch. The statement that the free-energy landscape is "funnel-like" for the binder and "rugged" for the non-binder is not a quantitative comparison with any experimental observable. The authors should either provide a more detailed comparison with experimental data or temper their claim of agreement.
- **Why it matters** A key selling point of computational studies is their ability to explain or predict experimental observations. Without a specific quantitative comparison, the reader cannot evaluate how well the simulations reproduce known biology. This weakens the impact of the study.
- **Resolution test** The authors should provide: (1) specific experimental binding data (e.g., Kd values, binding free energies) for ribocil A and B to the FMN riboswitch, and (2) a quantitative comparison of their computed free-energy differences with these experimental values. If such data are not available, the authors should state this clearly and moderate their claim of agreement.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Section 2.2, Figure 1c
- **Evidence pointer** Section 2.2, Figure 1c
- **Issue** The description of the three reaction coordinates is difficult to follow without the actual atom group definitions. The text refers to "two atom groups" but the specific atoms are only listed in Table S1, which was not fully visible in the provided material. The notation for the atom groups is not clearly defined in the main text.
- **Required correction** The authors should provide a clearer description of the atom groups in the main text, possibly with a simplified schematic in Figure 1c that labels the specific atoms or residues involved. The notation should be defined explicitly before first use.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout the manuscript
- **Evidence pointer** Abstract, Sections 3.1-3.5
- **Issue** The terms "front gate" and "rear gate" are introduced without formal definition. The relationship between these gates and the "front" and "rear" views of the aptamer domain (defined in Figure S1) is not explicitly stated. Additionally, the term "density tunnel" is used but not clearly defined in the main text.
- **Required correction** The authors should formally define these terms when first introduced, possibly with reference to the specific structural features of the aptamer domain. A brief description of the geometric relationship between the gates and the views would improve clarity.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 2-7
- **Evidence pointer** Figures 2-7
- **Issue** The figures are described in the text but were not fully visible in the provided material. Based on the descriptions, it is unclear whether the figures include sufficient labels, color scales, and annotations to be interpretable without extensive reference to the text.
- **Required correction** The authors should ensure that all figures are self-contained with clear labels, color bars for density maps, and annotations for key features. Figure captions should be sufficiently detailed to allow interpretation without reading the full text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Section 4 (Discussion)
- **Evidence pointer** Section 4
- **Issue** The Discussion section is relatively brief and does not fully address the limitations of the study. In particular, the authors do not discuss the potential impact of the force field choice on the π-π stacking interactions, which are central to their proposed mechanism. The comparison with the GPCR study is interesting but could be developed further.
- **Required correction** The authors should expand the Discussion to include a more thorough treatment of limitations, including force field accuracy, sampling completeness, and the sensitivity of the results to simulation parameters. The comparison with the GPCR system could be used to generate testable predictions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data Availability section
- **Evidence pointer** Data Availability section
- **Issue** The data availability statement indicates that datasets are available from the corresponding author on reasonable request, but no details are provided about what specific data would be shared (e.g., trajectories, analysis scripts, input files). The BSM-Archives link provides only representative snapshots.
- **Required correction** The authors should provide a more detailed data availability statement that specifies what data and code will be shared, and under what conditions. Consider depositing the full simulation trajectories and analysis scripts in a public repository to enhance reproducibility.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Writing quality
- **Affected element** Throughout
- **Evidence pointer** Abstract, Introduction, Results
- **Issue** The manuscript contains several typographical errors and awkward phrasings (e.g., "maned" for "named", "hirst" for "first", "robocil" for "ribocil", "exserted" for "exerted", "Bibo-A" for "Ribo-A"). These errors detract from the professional quality of the manuscript.
- **Required correction** The manuscript should be carefully proofread and edited for typographical errors and grammatical issues. A professional editing service may be beneficial.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Reference formatting
- **Affected element** Reference list
- **Evidence pointer** Reference list
- **Issue** The reference list appears to be incomplete or inconsistently formatted in the provided material. Some references are cited in the text but not listed, and the formatting style is not consistent.
- **Required correction** The authors should ensure that all references are properly cited in the text and listed in a consistent format according to the journal's guidelines.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Supplementary material organization
- **Affected element** Supplementary Information
- **Evidence pointer** Supplementary Information sections
- **Issue** The supplementary information is organized into sections but the figures and tables are referenced inconsistently in the main text. Some references are to "Figure S1" while others are to "Figures S1a-c" without clear explanation of the sub-panels.
- **Required correction** The authors should ensure consistent referencing of supplementary figures and tables throughout the main text, and provide clear descriptions of all sub-panels in the figure captions.

## Risk / unsupported claims

1. The claim that the free-energy landscape of ribocil B is "funnel-like" while that of ribocil A is "rugged" is not quantitatively supported. No free-energy differences, barrier heights, or error estimates are provided.
2. The statement that the results "agree qualitatively with an experiment" is not supported by specific experimental data or quantitative comparison.
3. The claim that non-native π-π stacking "supports the molecular orientation e↑ to be parallel to v↑" and facilitates binding is based on visual inspection of a limited number of snapshots and is not quantitatively validated.
4. The assertion that the rear gate pathway is "not important biophysically" is not supported by quantitative flux or probability calculations.
5. The statement that the "superior stability of ribocil B against ribocil A may be induced by the non-native stacking" is speculative and not directly tested.
6. The claim that the simulation "showed another pathway" through the rear gate is based on the density tunnel observation, but the statistical significance of this pathway is not established.
7. The convergence of the free-energy calculations is asserted based on the E_local criterion, but the details of this analysis are not fully presented, and the adequacy of sampling in all relevant regions is not demonstrated.
8. The force field parameters for the ribocil ligands are custom-generated but not validated, and the potential impact of force field inaccuracies on the conclusions is not quantitatively assessed.