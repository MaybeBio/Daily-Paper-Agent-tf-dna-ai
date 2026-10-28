## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results and discussion, materials and methods, conclusions, and figure/table legends as provided.
- **Assessment boundary** Scientific soundness, technical rigor, validity of claims relative to presented evidence, and suitability for a general molecular bioscience readership. No assessment of editorial fit or journal policy.
- **Shared manuscript claim summary** The authors report the prokaryotic expression and purification of the ecdysone receptor (EcR) and ultraspiracle (USP) ligand-binding domains from *Plutella xylostella*, demonstrate heterodimer formation via transmission electron microscopy and zeta potential measurements, show enhanced binding of the natural ecdysteroid PonA to the EcR/USP heterodimer versus the EcR monomer using radioligand assays, compare binding with the insecticide tebufenozide, and propose a structural basis for differential binding via molecular docking.
- **Visible evidence base** Results sections 2.1–2.6, Figures 1–4, Table 1, Materials and Methods sections 3.1–3.7, and Conclusions. No raw data files, statistical analysis details, or supplementary information were provided.
- **Missing materials affecting confidence** Raw radioligand binding data, replicate numbers, statistical test details, negative control data for nonspecific binding, validation of homology models (e.g., Ramachandran plots, RMSD values), and uncropped Western blot images. The manuscript states "location not provided" for several methodological details.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant topic in insect endocrinology and pesticide development, namely the in vitro characterization of ecdysone receptor–ligand interactions. The experimental approach combines protein biochemistry, biophysical characterization, and computational modeling, which is commendable in scope. However, several technical concerns undermine the strength of the central claims. The radioligand binding data lack sufficient experimental detail and statistical rigor to support the quantitative conclusions, particularly the reported 20-fold affinity enhancement. The molecular docking results are presented without adequate validation of the homology models or docking protocols. The zeta potential and TEM data, while suggestive of heterodimer formation, are interpreted with limited quantitative support. The manuscript would benefit from additional controls, clearer presentation of raw data, and more cautious interpretation of computational results.
- **Who would be interested in the results, and why** Researchers in insect toxicology, pesticide science, and structural biology of nuclear receptors would find the methodological advances in recombinant protein production and in vitro binding assays of interest. The comparative binding analysis of a natural ecdysteroid versus a commercial insect growth regulator has practical implications for the design of next-generation insecticides. The proposed hydrogen bonding network involving Glu307 and Arg382 could inform structure-based drug design efforts, though this claim requires stronger experimental validation.
- **Major strengths** The use of a prokaryotic expression system to produce functional EcR and USP domains is a practical advance over prior in vitro transcription–translation methods, potentially enabling higher-throughput screening. The combination of biophysical techniques (TEM, zeta potential) with radioligand binding and molecular modeling provides a multifaceted approach to studying receptor–ligand interactions. The comparative analysis of PonA versus tebufenozide addresses a question of direct relevance to insecticide development. The identification of specific residues (Glu307, Arg382, Asn503) involved in ligand binding offers testable hypotheses for future mutagenesis studies.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (binding affinity claim), R1-M2 (molecular modeling validation), R1-M3 (heterodimer formation evidence), R1-M4 (differential binding interpretation).
- **Assessment against Nature-style criteria** Originality: Moderate. The application of prokaryotic expression to *P. xylostella* ecdysone receptor domains is incremental, though the comparative ligand analysis adds some novelty. Scientific importance: Moderate. The work has applied value for insecticide screening but does not fundamentally advance understanding of nuclear receptor biology. Interdisciplinary readership: Limited. The topic is specialized, and the methods are largely standard biochemistry and computational chemistry. Technical soundness: Currently insufficient. Key quantitative claims lack statistical support, and computational results are not adequately validated. Readability for nonspecialists: Acceptable. The manuscript is generally clear, though some sections assume familiarity with receptor biology terminology.
- **Recommendation posture** Currently not established from the provided evidence. The core claims regarding enhanced binding affinity and the structural basis for ligand discrimination require additional experimental rigor and validation. Supportive if technical concerns are resolved.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative claim unsupported
- **Claim pointer** "The binding affinity of PonA to the EcR/USB dimer was enhanced approximately 20-fold compared with the binding affinity to the PxGST−EcR monomer."
- **Evidence pointer** Section 2.4, Figure 3B and 3C
- **Concern** The reported 20-fold enhancement in binding affinity is derived from Kd values of 48.8 nM (monomer) and 2.3 nM (dimer). However, the manuscript does not provide replicate numbers, standard errors, or confidence intervals for these Kd estimates. The saturation binding curves are described but not shown with data points or fitted curves. Without measures of variability, it is impossible to assess whether the difference between 48.8 nM and 2.3 nM is statistically significant. Additionally, the methods state that five concentrations of [3H]PonA were used, which is a minimal number for reliable saturation curve fitting and Kd estimation.
- **Why it matters** The 20-fold affinity enhancement is a central quantitative claim that underpins the conclusion that heterodimer formation is functionally important for ligand binding. If this claim is not statistically robust, the primary conclusion of the study is weakened.
- **Resolution test** Provide raw binding data with at least three independent replicates, report Kd and Bmax values with standard errors, and perform appropriate statistical comparisons (e.g., extra sum-of-squares F test for comparing Kd values). Increase the number of radioligand concentrations to at least eight for more reliable curve fitting.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational results not validated
- **Claim pointer** "Molecular simulations showed that the hydrogen bonding network formed by Glu307 and Arg382 on the EcR/USB dimer was a key factor in the affinity enhancement."
- **Evidence pointer** Section 2.6, Figure 4
- **Concern** The molecular docking and homology modeling results are presented without any validation metrics. No Ramachandran plots, ERRAT scores, or other quality assessments for the homology models are provided. The docking protocol is described only briefly, and no docking scores or enrichment statistics are given. The claim that Glu307 and Arg382 form a "key" hydrogen bonding network is based on a single docking pose without experimental corroboration, such as site-directed mutagenesis or binding assays with mutant receptors.
- **Why it matters** Computational predictions of binding modes are only as reliable as the models and protocols used. Without validation, the proposed structural explanation for differential ligand binding remains speculative. This weakens the mechanistic insight that is a stated contribution of the study.
- **Resolution test** Provide model quality metrics (e.g., Ramachandran plot, QMEAN score), docking score distributions, and a comparison of docking poses across multiple runs. Ideally, validate the role of Glu307 and Arg382 through mutagenesis experiments or at least cite structural homologs with experimentally determined binding modes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence insufficient for heterodimer formation
- **Claim pointer** "The monomeric proteins were also subjected to incubation experiments under the same conditions; however, autodimerization was not observed for either of the two monomeric proteins. Thus, GST tagging was excluded as a possible cause of dimerization in some proteins."
- **Evidence pointer** Section 2.2, Figure 2, Table 1
- **Concern** The conclusion that heterodimers form and that GST tagging does not cause dimerization is based on TEM images and zeta potential measurements. However, no quantitative analysis of particle size distributions is provided, and the TEM images are not shown with scale bars or statistical sampling information. The zeta potential data in Table 1 are presented as single values with standard deviations, but the number of replicates is not stated. The claim that "autodimerization was not observed" is based on visual inspection of TEM images, which is subjective and not a rigorous method for excluding dimerization.
- **Why it matters** The formation of a functional heterodimer is a prerequisite for the subsequent binding experiments and the interpretation of the 20-fold affinity enhancement. If heterodimer formation is not convincingly demonstrated, the interpretation of the binding data is ambiguous.
- **Resolution test** Provide quantitative size distribution analysis from TEM (e.g., measuring at least 100 particles per condition), include negative staining controls, and report zeta potential measurements with replicate numbers and statistical comparisons. Consider using size-exclusion chromatography or dynamic light scattering as orthogonal methods to confirm heterodimer formation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Overinterpretation of comparative binding data
- **Claim pointer** "These experiments further showed that the binding activity of PonA to EcR/USB complexes from different species was greater than that of tebufenozide, which bound only partially to EcR/USB complexes in lepidopteran and coleopteran insects."
- **Evidence pointer** Section 2.4, Figure 3D
- **Concern** The comparison between PonA and tebufenozide binding is based on a single competitive binding experiment with one concentration of [3H]PonA (10 nM) and varying concentrations of tebufenozide. The IC50 value of 80.58 nM is reported, but no confidence intervals or replicate data are provided. The statement that PonA binding is "greater than" tebufenozide across species is extrapolated from the current study on *P. xylostella* and cited literature, but the current data do not directly support a cross-species conclusion.
- **Why it matters** The comparative claim is used to suggest that the screening method can discriminate between ligands with different affinities, which is a practical application of the method. Overstating this claim without direct comparative data could mislead readers about the method's discriminatory power.
- **Resolution test** Perform competitive binding experiments with both PonA and tebufenozide under identical conditions with multiple replicates, and report IC50 values with confidence intervals. Restrict cross-species comparisons to cited literature or provide direct experimental data for other species.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Methodological clarity
- **Affected element** Section 3.6, binding experiments
- **Evidence pointer** "location not provided"
- **Issue** The methods for the radioligand binding assay do not specify the protein concentration used in the saturation experiments beyond a single mention of 300 µg·mL−1 for the competitive assay. It is unclear whether the same concentration was used for saturation binding.
- **Required correction** Specify the protein concentration for all binding experiments and state whether the concentration was optimized or fixed.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 3
- **Evidence pointer** "location not provided"
- **Issue** The figure legend does not indicate the number of replicates or the error bar definition (e.g., standard deviation vs. standard error). This information is essential for interpreting the variability of the data.
- **Required correction** Add replicate numbers and error bar definitions to the figure legend.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Table 1
- **Evidence pointer** "location not provided"
- **Issue** The zeta potential values are reported as mean ± standard deviation, but the number of independent measurements is not stated. Additionally, no statistical test is reported for the comparison between monomer and dimer zeta potentials.
- **Required correction** State the number of replicates and perform a statistical test (e.g., t-test) for the comparison.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature support
- **Affected element** Section 2.6
- **Evidence pointer** "location not provided"
- **Issue** The claim that Asn503 is an important residue for ligand binding across species is supported by references to other insect species, but the relevance of these homologs to *P. xylostella* is not discussed in terms of sequence conservation or structural equivalence.
- **Required correction** Provide a sequence alignment or structural superposition showing the conservation of Asn503 and the surrounding residues across the cited species.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Section 2.4
- **Evidence pointer** "location not provided"
- **Issue** The term "binding affinity" is used to describe the Kd values, but the manuscript does not clarify whether these are equilibrium dissociation constants determined under steady-state conditions. The use of "affinity" without kinetic context could be misleading.
- **Required correction** Define "binding affinity" in the context of the assay and consider using "equilibrium dissociation constant" for precision.

## Risk / unsupported claims
- The 20-fold enhancement in binding affinity for PonA to the EcR/USB dimer versus monomer is unsupported due to lack of replicate data and statistical analysis.
- The claim that Glu307 and Arg382 form a key hydrogen bonding network responsible for affinity enhancement is unsupported without model validation or experimental mutagenesis data.
- The statement that heterodimer formation is confirmed and GST tagging does not cause dimerization is weakly supported due to subjective TEM interpretation and lack of quantitative analysis.
- The cross-species generalization that PonA binding is greater than tebufenozide binding across lepidopteran and coleopteran insects is not directly supported by the data presented in this manuscript.
- The claim of "first time" characterization of physical size, zeta potential, and molecular weight of the heterodimer before and after ligand binding is not verifiable from the provided material and may be overstated.