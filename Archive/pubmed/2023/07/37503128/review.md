## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, discussion) as provided
- **Assessment boundary** Scientific claims, methodological soundness, and evidence quality as presented in the provided text; no external data or unpublished materials were consulted
- **Shared manuscript claim summary** The authors report that "fountains," a novel class of chromosome organization features, emerge at enhancers upon zygotic genome activation (ZGA) in zebrafish, are dependent on cohesin-mediated loop extrusion, and are causally linked to pioneer transcription factor activity. They further propose facilitated cohesin loading at enhancers as the underlying mechanism, supported by polymer simulations and corroborated by observations in mouse cells.
- **Visible evidence base** Hi-C data from zebrafish embryos at multiple developmental stages (2.75, 5.3, 11, 25 hpf) and sperm; Hi-C from mutant embryos lacking Pou5f3, Sox19b, Nanog in various combinations; ATAC-seq, ChIP-seq (Rad21, H3K4me1, H3K27ac, H3K4me3), replication timing data; published datasets from medaka, Xenopus, mouse; polymer simulations; fontanka algorithm for fountain calling
- **Missing materials affecting confidence** Supplementary datasets (1–6) referenced but not provided; Extended Data figures referenced but not provided; detailed simulation parameters and code outputs not fully described in text; statistical details for several comparisons not fully specified

## Reviewer
- **Overall assessment** This manuscript presents a potentially significant discovery: a new class of chromosome organization features ("fountains") that emerge at enhancers upon ZGA, with evidence for a cohesin-dependent mechanism. The work combines careful Hi-C analysis, genetic perturbations, cross-species comparisons, and polymer simulations to build a coherent model. However, several technical concerns must be addressed before the central claims are fully established, particularly regarding the specificity of fountain detection, the quantitative rigor of the mutant analyses, and the directness of the causal evidence linking pioneer factors to fountain formation.
- **Who would be interested in the results, and why** Researchers in chromosome architecture, developmental biology, gene regulation, and epigenetics would find this work of high interest. The identification of a new structural element associated with enhancers and the proposed mechanism of facilitated cohesin loading have broad implications for understanding how 3D genome organization is established during development and how enhancer-promoter communication is orchestrated. The cross-species conservation (zebrafish, medaka, Xenopus, mouse) extends the relevance beyond a single model organism.
- **Major strengths**
  1. The discovery of a novel, systematically characterized chromatin feature ("fountains") that is distinct from known structures (TADs, stripes, loops) and specifically associated with enhancers.
  2. The combination of developmental time-course Hi-C, genetic perturbations (single, double, triple pioneer factor mutants), and cross-species validation provides a multi-pronged approach.
  3. The polymer simulations offer a mechanistic framework that generates testable predictions, and the authors appropriately explore multiple mechanistic variants.
  4. The fontanka algorithm is a methodological contribution that enables systematic detection of fountains, with validation against an independent approach (protractor).
  5. The observation that fountains are transient and transform into other structures (TADs, dots) over development provides a dynamic view of chromosome folding.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Statistical rigor
- **Claim pointer** The authors claim that 1460 fountains were detected at 5.3 hpf and that these are "consistent across two Hi-C replicates."
- **Evidence pointer** Results section "Fountains are transient structures emerging after ZGA"; Methods "Fountain calling with fontanka"
- **Concern** The reproducibility criterion for fountain calling is described only as "consistent across two Hi-C replicates" (line not provided). The specific threshold for consistency (e.g., overlap fraction, Jaccard index, distance between called peaks) is not stated. Furthermore, the false discovery rate of the fontanka algorithm is not quantified. Given that 1460 fountains were called from 3391 candidates (43% pass rate), the specificity of the algorithm is a critical parameter that is not rigorously established.
- **Why it matters** If the fountain-calling threshold is too permissive, many of the reported fountains may be false positives, which would weaken all downstream analyses (enrichment, mutant comparisons, cross-species claims). Conversely, if too stringent, the authors may be missing genuine features. Without a clear FDR estimate or comparison to a null model, the quantitative claims about fountain numbers and their properties are not fully reliable.
- **Resolution test** Provide a detailed description of the fontanka algorithm's decision thresholds, and report the FDR estimated from permutation tests (e.g., shuffling Hi-C maps or using a null model of random interactions). Additionally, report the overlap statistics between replicates (e.g., fraction of fountains in replicate 1 that are also detected in replicate 2, and vice versa) with a clear threshold.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The authors state that "Knockouts of pioneer transcription factors driving ZGA enhancers result in the specific loss of fountains, establishing a causal link between enhancer activation and fountain formation."
- **Evidence pointer** Results section "Pioneer factors establish open chromatin platforms for fountain formation"; Figure 3
- **Concern** The causal claim is based on the observation that fountains weaken or disappear in MZtriple mutants. However, the analysis categorizes fountains into Down (n=278), Unchanged (n=1092), and Up (n=90) groups. The fact that 75% of fountains are unchanged in the triple mutant substantially weakens the claim of a general causal link. The authors suggest these may be "PWN-independent enhancers," but this is speculative. Moreover, the threshold for "weakened" (1.5 standard deviations from zero in the difference distribution) is arbitrary and not justified. The analysis does not demonstrate that the loss of fountains is specifically due to loss of pioneer factor binding at those sites, as opposed to indirect effects of the mutants on global chromatin state.
- **Why it matters** The central mechanistic claim of the paper is that pioneer factors drive fountain formation via enhancer activation. If only 19% of fountains are affected by the triple knockout, the generality of this mechanism is questionable. The authors need to demonstrate that the affected fountains are specifically those bound by the pioneer factors, and that the unaffected fountains are not also bound by these factors (or are regulated by other mechanisms).
- **Resolution test** Perform a direct comparison of fountain strength at sites with and without pioneer factor binding (using ChIP-seq or the ATAC-seq-based inference). Show that fountains at pioneer factor-bound enhancers are specifically lost in the mutants, while fountains at unbound sites are unaffected. Additionally, provide a statistical test for the enrichment of pioneer factor motifs at Down fountains versus Unchanged fountains.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Model validation
- **Claim pointer** The authors claim that polymer simulations "demonstrate that fountains may arise as sites of facilitated cohesin loading" and that the model "closely match[es] the intensity profile of fountains."
- **Evidence pointer** Results section "Facilitated loading of loop extruding SMCs as a mechanism of fountains formation"; Figure 5
- **Concern** The simulation model is described qualitatively, and the goodness-of-fit metrics are not fully specified. The authors state that "all models have a range of parameters where they could closely approximate experimental fountains," which raises the question of model identifiability. If multiple distinct mechanisms (facilitated loading, random barriers, decoupled legs) can all produce similar fountain shapes, the simulations do not uniquely support the facilitated loading hypothesis. The parameter sweep results are presented as a heatmap (Fig. 5d) but the specific parameter ranges and the criteria for "best fit" are not clearly defined.
- **Why it matters** The simulations are used to argue for a specific mechanism (facilitated loading). If the model cannot distinguish between competing mechanisms, the mechanistic conclusion is overclaimed. The authors need to demonstrate that the facilitated loading model fits the data significantly better than alternative models, and that the fitted parameters are biologically plausible.
- **Resolution test** Provide a quantitative comparison of the three models (facilitated loading, random barriers, decoupled legs) using a formal model selection criterion (e.g., AIC or BIC). Show that the facilitated loading model is preferred, and report the uncertainty in the fitted parameters. Additionally, test whether the model can predict the observed changes in fountain patterns in the mutant embryos.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability / Cross-species claims
- **Claim pointer** The authors state that "we detected similar fountain patterns at enhancers in mouse cells" and that fountains are present in medaka and Xenopus.
- **Evidence pointer** Results section "Fountains are transient structures emerging after ZGA"; Figure 1g,h
- **Concern** The cross-species analysis is presented briefly, and the criteria for "similar fountain patterns" are not defined. For mouse, the analysis is based on published Micro-C data, but the specific cell type, developmental stage, and analysis parameters are not described in the main text. For medaka and Xenopus, the number of fountains detected and the statistical significance of the detection are not reported. The claim of conservation is therefore not quantitatively supported.
- **Why it matters** The cross-species conservation is a key argument for the general biological importance of fountains. If the detection criteria are not consistent across species, the comparison may be misleading. The authors need to demonstrate that the fountain signal in other species is statistically significant and qualitatively similar to that in zebrafish.
- **Resolution test** Provide a systematic cross-species comparison using the same fountain-calling pipeline, with FDR estimates for each species. Report the number of fountains detected, their enrichment at enhancers, and the similarity of their average shapes. For mouse, specify the cell type and developmental stage, and show that the fountain signal is present in at least two independent datasets.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Data processing
- **Claim pointer** The authors state that "we observed the formation of compartments and a strong Rabl configuration" at 5.3 hpf, and that "compartmentalization and insulation grow together, gradually and in synchrony with each other."
- **Evidence pointer** Results section "Large-scale chromosome reorganization in early zebrafish embryogenesis"; Extended Data Figure 1
- **Concern** The analysis of compartments and Rabl configuration is described only briefly. The methods for compartment calling are mentioned (eigenvector decomposition), but the criteria for defining "strong Rabl configuration" are not specified. The claim that compartmentalization and insulation grow "in synchrony" is based on a qualitative comparison of trends, and no statistical test is provided. Additionally, the potential confounding effect of the strong Rabl configuration on compartment calling is not addressed.
- **Why it matters** The developmental trajectory of genome organization is a key context for the fountain discovery. If the compartment and insulation analyses are not rigorously quantified, the claim of synchronous growth is not supported. Moreover, if the Rabl configuration biases compartment calling, the interpretation of compartmentalization changes may be incorrect.
- **Resolution test** Provide quantitative metrics for Rabl configuration strength (e.g., centromere-centromere interaction enrichment) and compartmentalization (e.g., eigenvalue-based compartment score) at each stage, with error bars across replicates. Perform a statistical test for the correlation between compartment score and insulation strength across stages. Address the potential bias of Rabl configuration on compartment calling (e.g., by excluding centromeric regions in a sensitivity analysis).

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / Reproducibility
- **Affected element** Methods section "Fountain calling with fontanka"
- **Evidence pointer** Methods, "Fountain calling with fontanka"
- **Issue** The description of the fontanka algorithm is incomplete. The four principal steps are listed, but the specific parameters (e.g., window size, thresholds for peak detection, smoothing parameters) are not provided. The filtering criteria (iv.a–iv.f) are mentioned but not defined.
- **Required correction** Provide a complete description of the algorithm, including all parameters and thresholds, either in the Methods or as a supplementary note. This is essential for reproducibility.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section "Fountains are enriched at enhancers"
- **Evidence pointer** Figure 2c; Methods "Enrichment of developmental regulatory elements at fountains"
- **Issue** The enrichment analysis reports an FDR of "FDR<<1e-4" but does not specify the number of permutations or the method for FDR estimation. The statement "based on normal distribution fit" is unclear.
- **Required correction** Specify the exact statistical test used, the number of permutations or the method for FDR estimation, and report the actual FDR value rather than an inequality.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results section "Fountains are transient structures emerging after ZGA"
- **Evidence pointer** Figure 1g,h; Supplementary Dataset 2
- **Issue** The cross-species analysis (medaka, Xenopus) is presented without quantitative details in the main text. The number of fountains detected and the statistical significance are not reported.
- **Required correction** Add a supplementary table summarizing the number of fountains detected in each species, the FDR, and the enrichment at enhancers.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section
- **Evidence pointer** Discussion, paragraph 3
- **Issue** The authors state that "fountains are not essential for formation of enhancers" based on a cited study in C. elegans. This interpretation is presented without discussion of potential differences between species or developmental contexts.
- **Required correction** Add a brief discussion of the limitations of cross-species comparisons and the possibility that fountain function may differ between organisms.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Abstract, Results, Discussion
- **Issue** The term "fountain" is used to describe a new structural feature, but the relationship to previously described "plumes" and "jets" is only briefly mentioned. The authors should clarify whether these are the same or different structures.
- **Required correction** Add a paragraph in the Introduction or Discussion explicitly comparing and contrasting fountains with plumes, jets, and other related structures, and justify the new terminology.

## Risk / unsupported claims
- The claim that fountains are "the first known enhancer-specific elements of chromosome organization" is strong and not fully supported by the data presented, as the comparison to other enhancer-associated structures is not exhaustive.
- The claim that "fountains represent starting points for chromosome folding during development" is speculative and not directly tested; the data show correlation, not causation, for the developmental trajectory.
- The statement that "fountains may arise as sites of facilitated cohesin loading" is presented as a hypothesis supported by simulations, but the simulations do not uniquely identify this mechanism (see R1-M3).
- The claim that "fountains disappear upon acute cohesin depletion" is based on mouse cell data, but the specific experimental conditions and the statistical significance of the disappearance are not fully described in the provided text.
- The assertion that "fountains are visible in medaka and Xenopus" is not quantitatively supported in the main text; the number of fountains and their significance are not reported.
- The claim that "compartmentalization and insulation grow together, gradually and in synchrony" is not statistically tested and may be an overinterpretation of qualitative trends.