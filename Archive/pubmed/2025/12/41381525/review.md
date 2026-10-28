## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary figure/table legends as referenced.
- **Assessment boundary** Scientific content, technical soundness, and support of claims based solely on the provided manuscript text. No external data, supplementary files, or unpublished materials were accessed.
- **Shared manuscript claim summary** The authors report the structural and functional characterization of HLp, a tetrameric histone-fold protein from the bacterium *Leptospira perolatii*. They claim that HLp forms stable tetramers in solution, binds DNA nonspecifically, wraps approximately 60 bp of DNA around its core, compacts DNA in vitro, and reorganizes the *E. coli* nucleoid upon heterologous expression. They further propose that this represents the first experimental demonstration of DNA wrapping by a bacterial histone and that HLp functions as a chromatin organizer in *Leptospira*.
- **Visible evidence base** Crystal structures of free HLp (PDB 9QT0) and two DNA-bound forms (PDB 9QT1, 9QT2); SEC-MALS; CD spectroscopy; EMSA; MST; MNase digestion; TPM; topoisomerase I relaxation assay; ligase-mediated circularization assay; all-atom MD simulations (1 µs each); steered MD; heterologous expression in *E. coli* with fluorescence microscopy.
- **Missing materials affecting confidence** Supplementary figures, supplementary tables, supplementary methods, source data files, and movies were not provided. Coordinates and structure factors were not independently validated. Details of MD simulation convergence, force-field parameters, and system construction are not fully assessable. The manuscript states that full protocols are in Supplementary Methods, which were not available for review.

## Reviewer
- **Overall assessment** This manuscript presents a structurally and biophysically well-characterized new bacterial histone, HLp, and provides multiple lines of evidence supporting a DNA-wrapping mode distinct from the dimeric bacterial histone HBb. The crystallographic work is of high quality, and the combination of in vitro assays, MD simulations, and in vivo heterologous expression is commendable. However, several claims, particularly regarding the predominance of the wrapping mode under physiological conditions and the functional role of HLp in native *Leptospira* cells, are not fully supported by the data presented. The evidence for wrapping is largely indirect, and the in vivo experiments rely on a heterologous system with potential artifacts. The manuscript would be strengthened by more direct demonstration of wrapping geometry, quantitative comparison with known wrapping proteins, and acknowledgment of the limitations of the heterologous expression system.
- **Who would be interested in the results, and why** Researchers in chromatin biology, prokaryotic genome organization, histone evolution, and structural biology. The work extends the known diversity of histone architectures into bacteria and provides a second experimentally characterized bacterial histone, which will be of interest to those studying the evolutionary origins of chromatin. The demonstration of a tetrameric wrapping histone in bacteria also has implications for understanding minimal requirements for DNA compaction.
- **Major strengths**
  1. High-resolution crystal structures of both free and DNA-bound HLp, providing atomic-level detail of the tetrameric assembly and DNA-binding interfaces.
  2. The identification of a conserved tetramerization interface distinct from eukaryotic and archaeal nucleosomal histones, with supporting sequence analysis across bacterial lineages.
  3. The combination of multiple orthogonal biophysical and biochemical assays (EMSA, MST, SEC-MALS, MNase, TPM, topology) to characterize DNA binding and compaction.
  4. The use of long-timescale all-atom MD simulations to compare wrapping and bridging modes, including free-energy landscape analysis.
  5. The in vivo heterologous expression experiments, which, despite limitations, provide functional context and demonstrate nucleoid reorganization.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The central claim that HLp wraps approximately 60 bp of DNA around its core is presented as the primary finding of the study.
- **Evidence pointer** Results, "Crystal structures of HLp bound to DNA"; Results, "Molecular dynamics (MD) simulation"; Results, "HLp is wrapped by DNA in vitro"
- **Concern** The evidence for a wrapping mode is indirect. The two crystal structures show short DNA fragments (16 bp and 15 nt) bound at distinct, non-overlapping sites on the tetramer surface. The authors infer wrapping by superimposing these structures and noting that the binding sites are distributed along the tetramer perimeter. The MD simulations, while supportive, were initiated from models constructed by the authors and may bias the outcome. The MNase digestion pattern shows protected fragments of 35–72 bp, which is consistent with wrapping but also with other modes of protection. The TPM assay shows compaction but does not distinguish wrapping from other compaction mechanisms. Direct evidence for wrapping, such as a structure with a full-length DNA wrapped around the tetramer, or a quantitative assay that directly measures the wrapping geometry, is lacking.
- **Why it matters** The claim of DNA wrapping is the central novelty of the manuscript and distinguishes HLp from the dimeric HBb. If the wrapping mode is not definitively established, the manuscript's primary contribution is reduced to the characterization of another bacterial histone structure, which is less impactful.
- **Resolution test** Provide a structure of HLp bound to a DNA fragment long enough to fully wrap the tetramer (e.g., 60–70 bp), or provide a quantitative assay (e.g., DNA cyclization, FRET, or atomic force microscopy) that directly demonstrates the wrapping geometry. Alternatively, the authors could temper the claim and present wrapping as a plausible model supported by indirect evidence.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The MD simulations are used to support the stability and predominance of the wrapping mode over the bridging mode.
- **Evidence pointer** Results, "Molecular dynamics (MD) simulation"; Supplementary Figures 9–19; Supplementary Movies 1, 2
- **Concern** The MD simulation methodology is described only briefly in the main text, with full details relegated to Supplementary Methods, which were not provided. Key parameters such as the force field used, water model, ionic conditions, temperature/pressure coupling, and the method for constructing the initial wrapping and bridging models are not assessable. The authors state that two independent starting conformations were generated for each mode, but the degree of difference between these conformations is unclear. The free-energy landscape analysis is mentioned but not shown in the main text. Without these details, the reliability and interpretation of the simulations cannot be evaluated.
- **Why it matters** The MD simulations provide a key piece of evidence for the wrapping mode and are used to argue that wrapping is likely to predominate under physiological conditions. If the simulations are not technically sound or are biased by the initial model construction, this conclusion is unsupported.
- **Resolution test** Provide the full simulation protocols, including force field parameters, system construction, equilibration, and analysis methods. Show the free-energy landscapes for both modes. Demonstrate that the simulations are converged and that the results are robust to the choice of initial conditions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Claim support
- **Claim pointer** The in vivo experiments are used to support a role for HLp in bacterial chromatin organization.
- **Evidence pointer** Results, "HLp binds to genomic DNA in vivo"; Figure 7; Figure 8
- **Concern** The in vivo experiments are performed in *E. coli*, a heterologous host. While this is a reasonable model system, the authors do not discuss potential artifacts, such as overexpression-induced aggregation, non-physiological protein:DNA stoichiometry, or differences in nucleoid structure between *E. coli* and *Leptospira*. The microscopy images show nucleoid decondensation, but the mechanism is not explored. The MNase digestion of genomic DNA from HLp-expressing *E. coli* shows a ladder, but the pattern is described as "irregular" and distinct from HMfB. The authors do not provide a quantitative analysis of the protected fragment sizes or a comparison with the in vitro pattern. The claim that HLp functions as a chromatin organizer in *Leptospira* is extrapolated from these heterologous data and from the genomic context, but no direct experiments in *Leptospira* are presented.
- **Why it matters** The in vivo data are used to support the functional relevance of HLp. If the heterologous system is not carefully validated, the conclusions about HLp's role in native *Leptospira* cells are speculative.
- **Resolution test** Provide additional controls for the *E. coli* experiments, such as a DNA-binding-deficient HLp mutant, and discuss potential artifacts. Alternatively, temper the claims about the in vivo role of HLp and present the *E. coli* data as preliminary evidence that requires validation in *Leptospira*.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The stoichiometry of the HLp-DNA complex is determined by SEC-MALS, showing a complex of HLp tetramer with two 30-bp DNA duplexes.
- **Evidence pointer** Results, "HLp binds to DNA in vitro"; Figure 3d
- **Concern** The SEC-MALS experiment shows a single peak with a molecular weight of 69.2 ± 5.7 kDa, which the authors interpret as a complex of one HLp tetramer (28.4 kDa) with two 30-bp DNA duplexes (~18.4 kDa each, total ~36.8 kDa, sum ~65.2 kDa). However, the molecular weight of the complex is close to the sum of the components, and the interpretation depends on the assumption that the complex is a single species. The authors do not show the SEC-MALS profile of the DNA alone or the protein alone under the same conditions, nor do they show a titration to demonstrate that the stoichiometry is fixed. The possibility of a mixture of species (e.g., 1:1 and 1:2 complexes) cannot be excluded.
- **Why it matters** The stoichiometry is used to support the wrapping model, as two DNA duplexes bound to one tetramer could represent two halves of a wrapped DNA. If the stoichiometry is not robustly determined, this support is weakened.
- **Resolution test** Provide SEC-MALS data for the individual components and for multiple protein:DNA ratios. Show that the complex peak is homogeneous and that the molecular weight is consistent with a single stoichiometry. Alternatively, use an orthogonal method such as analytical ultracentrifugation or native mass spectrometry.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that HLp "wraps ~60 bp of DNA around its core" but does not mention the uncertainty in this estimate or the indirect nature of the evidence.
- **Required correction** Consider rephrasing to "wraps approximately 60 bp of DNA around its core, as supported by structural and biophysical analyses" or similar, to avoid overstating the certainty of the claim.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, "HLp binds to DNA in vitro"
- **Evidence pointer** Figure 3c
- **Issue** The MST data are presented as a comparison of HLp binding to 80-bp and 80-bp-GC40 DNA fragments, but the dissociation constants are only given in the text as "low micromolar range." The exact values and the number of replicates are not stated in the main text.
- **Required correction** Provide the exact Kd values with standard deviations in the text or figure legend.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, "HLp is wrapped by DNA in vitro"
- **Evidence pointer** Figure 6c
- **Issue** The ladder EMSA shows that HLp alters the mobility of DNA fragments in a size-dependent manner, with fragments >2000 bp migrating faster and fragments <1000 bp migrating slower. The interpretation that this is due to wrapping is plausible but not unique; other protein-DNA interactions could produce similar effects.
- **Required correction** Acknowledge alternative interpretations or provide additional evidence to support the wrapping interpretation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion states that HLp "represents the first experimental characterization of a bacterial histone belonging to the FtF subgroup," but the authors do not discuss whether any FtF histones from archaea have been experimentally characterized, which would provide important context.
- **Required correction** Add a brief comparison with archaeal FtF histones, if any have been characterized, or state that none have been.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods, "Crystallization, data collection, and structure determination"
- **Evidence pointer** Methods
- **Issue** The methods state that structures were deposited in the PDB but do not provide the resolution, R-factors, or other quality metrics for the structures in the main text.
- **Required correction** Include key crystallographic statistics in the main text or a supplementary table.

## Risk / unsupported claims
- The claim that HLp wraps ~60 bp of DNA is not directly demonstrated; it is inferred from crystal structures with short DNA fragments and supported by MD simulations and indirect biophysical assays.
- The claim that the wrapping mode is likely to predominate under physiological conditions is based on MD simulations whose details are not fully provided.
- The claim that HLp functions as a chromatin organizer in *Leptospira* is extrapolated from heterologous expression in *E. coli* and genomic context, with no direct experiments in *Leptospira*.
- The stoichiometry of the HLp-DNA complex (1 tetramer: 2 DNA duplexes) is based on a single SEC-MALS experiment without full controls.
- The functional significance of the conserved genomic neighborhood (hlp adjacent to SMC, MAP, etc.) is speculative and not experimentally tested.