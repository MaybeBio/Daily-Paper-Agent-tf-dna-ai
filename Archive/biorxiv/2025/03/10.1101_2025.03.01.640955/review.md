## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, limitations, conclusion, methods) as provided
- **Assessment boundary** Scientific content, methodological rigor, statistical validity, and interpretation of results as presented in the provided text; no supplementary figures or tables beyond those referenced were available for inspection
- **Shared manuscript claim summary** The authors present the first comprehensive comparison of AlphaFold 2 (AF2) predicted and experimental full-length nuclear receptor (NR) structures, analyzing RMSD, secondary structure content, domain architecture, ligand-binding pocket geometry, and backbone torsional angles across seven NRs with available full-length structures
- **Visible evidence base** Text descriptions of results, statistical values (means, CVs, correlations, p-values), and references to figures (Fig. 1-6) and Table 1; actual figures and tables not provided
- **Missing materials affecting confidence** Figures 1-6, Table 1, PDB accession details, statistical output tables, and any supplementary data were not included in the provided material; this limits verification of quantitative claims and visual comparisons

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and timely question: how well does AF2 predict full-length nuclear receptor structures compared to experimental data? The authors have assembled a useful dataset of the seven available full-length NR structures and applied multiple complementary metrics. However, the manuscript has substantial methodological weaknesses that undermine confidence in several key conclusions. The statistical analyses are incompletely described, the interpretation of domain architecture results is partly speculative, and the claim of "first comprehensive analysis" is not fully contextualized against prior benchmarking studies. The most significant issue is the lack of clarity regarding how AF2 predictions were selected (single model vs. ranked models), how alignments were performed, and whether the observed differences are within expected AF2 accuracy ranges. The discussion of biological implications, particularly regarding asymmetric homodimers, is interesting but goes beyond what the presented data can support. The manuscript would benefit from more rigorous statistical treatment, clearer presentation of methods, and more cautious interpretation of findings.

- **Who would be interested in the results, and why** Structural biologists studying nuclear receptors, computational biologists working on protein structure prediction benchmarking, and researchers involved in structure-based drug design targeting NRs. The findings on AF2 limitations in flexible regions and ligand-binding pockets are directly relevant to those using AF2 models for drug discovery. The methodological framework for comparing predicted and experimental structures could also be of interest to the broader protein structure prediction community.

- **Major strengths** 1) The study addresses a specific and important protein family with high therapeutic relevance, filling a gap in AF2 benchmarking literature. 2) The use of multiple complementary metrics (RMSD, SSE content, domain geometry, pocket properties, torsional angles) provides a multi-faceted view of prediction quality. 3) The identification of systematic AF2 limitations, particularly pocket volume underestimation and single-conformation capture in asymmetric homodimers, has practical implications for model use. 4) The authors correctly separate analysis by domain (DBD vs LBD), which is appropriate given their different structural and functional characteristics.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim to have performed "the first comprehensive analysis comparing AlphaFold 2-predicted and experimental nuclear receptor structures" and report specific RMSD values, CVs, and statistical test results
- **Evidence pointer** Abstract; Results sections "Root-mean-square deviation of the structures" and "Analysis of ligand-binding pockets"; Methods section "RMSD analysis"
- **Concern** The statistical methodology is critically underdescribed. The authors report paired t-tests, Cohen's d, Kruskal-Wallis tests, Pearson correlations, and hierarchical clustering, but do not specify: (a) how many AF2 models were used per target (rank 1 only or multiple), (b) how structural alignment was performed prior to RMSD calculation (which residues were included, whether hinge regions were excluded), (c) whether the paired t-test was applied to independent observations or repeated measures from the same structures, (d) how the CV values were computed across what sample sizes, and (e) whether multiple testing corrections were applied beyond the Bonferroni correction mentioned for SSE analysis. The reported p-value (p < 0.05) for the domain difference is marginal and the effect size (d = 0.574) is moderate, yet the authors interpret this as a significant finding. Without knowing the sample size (apparently 24 structures total across 7 NRs), the statistical power and validity of these tests cannot be assessed.
- **Why it matters** The core quantitative claims of the paper rest on these statistical analyses. If the methods are not reproducible or the tests are inappropriately applied, the conclusions about domain-specific differences, pocket volume underestimation, and prediction quality rankings are not reliable. This is particularly important because the authors use these statistics to make general claims about AF2 performance on NRs.
- **Resolution test** The authors must provide a complete description of the statistical workflow, including: number of AF2 models per target, alignment protocol, residue selection for RMSD calculation, sample sizes for each test, and justification for test choice. They should also provide the actual data distributions (e.g., boxplots with individual data points) so that the appropriateness of parametric vs. non-parametric tests can be evaluated. If the sample size is small (n < 10 per domain), the use of t-tests and Pearson correlations should be justified or replaced with appropriate alternatives.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "AF2 systematically underestimates ligand-binding pocket volumes" and report specific percentage differences (e.g., GR 3% vs 16-18%, HNF4α 111.6-120%, LXRβ 155.8-163.5%)
- **Evidence pointer** Results section "Analysis of ligand-binding pocket geometry"; Methods section "Analysis of LBP geometry"
- **Concern** The method for defining and measuring ligand-binding pocket volume is inadequately described. The authors mention using "hollow 1.3" for pocket identification and "msms 2.6.1" for surface calculation, but do not specify: (a) how the pocket boundary was defined (what constitutes the pocket opening), (b) whether the same definition was applied consistently to experimental and predicted structures, (c) how the "effective radius" was computed from the volume/surface area ratio, and (d) whether the pocket measurements were performed on the same ligand-bound vs apo states. The authors state that for apo AF2 structures, "the cutoff was calculated from the position of all merged ligands in the holo structures," which is a reasonable approach but needs more detail. More critically, the reported percentage differences are extremely large (up to 163.5% for LXRβ), which raises questions about whether the pocket definition is capturing the same physical region in both structures. The authors do not report absolute volumes, only percentages, making it impossible to assess whether these differences are biologically meaningful or an artifact of the pocket definition.
- **Why it matters** The claim of systematic pocket volume underestimation is one of the key findings with direct implications for structure-based drug design. If the pocket measurement methodology is not robust or the comparison is confounded by different pocket definitions, this conclusion is not supported. The very large differences for LXRβ suggest either a genuine structural difference or a methodological artifact that needs to be resolved.
- **Resolution test** The authors should provide: (a) a detailed description of the pocket definition algorithm and parameters, (b) absolute volume and radius values (not just percentages) for each structure, (c) visual examples of pocket boundaries overlaid on experimental and predicted structures, and (d) a sensitivity analysis showing how results change with different pocket definition parameters. They should also clarify whether the same ligand was used for pocket definition in all experimental structures and how the merged ligand approach was validated.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors claim that "AF2 captures only a single conformational state for each receptor" and that this represents a limitation for understanding NR function, particularly in asymmetric homodimers
- **Evidence pointer** Results section "Geometrical analysis of domain architecture"; Discussion section
- **Concern** The claim that AF2 captures only one conformational state is presented as a key finding, but this is a well-known and expected limitation of AF2, which is trained to predict a single static structure. The authors do not provide a systematic analysis of AF2's confidence metrics (pLDDT, PAE) to support the claim that the predicted state is not representative of the conformational ensemble. More importantly, the comparison between AF2's single prediction and experimental structures that may capture different conformational states (e.g., due to different crystal packing, ligand binding, or DNA binding) is confounded. The authors note that experimental structures of GR and HNF4α show asymmetric domain arrangements, but they do not address whether this asymmetry is functionally significant or an artifact of crystal packing. The interpretation that AF2's failure to predict asymmetry represents a limitation is speculative without additional analysis of the conformational landscape.
- **Why it matters** The claim about single-conformation capture is used to argue for the importance of experimental structures and to identify limitations of AF2 for drug design. If this claim is not properly contextualized or supported, the paper's contribution to understanding AF2's utility for NR research is weakened. The discussion of asymmetric homodimers goes beyond the data presented and needs more careful treatment.
- **Resolution test** The authors should: (a) provide PAE plots and pLDDT confidence maps for the AF2 predictions to show whether the predicted state is well-defined or represents an average of multiple states, (b) discuss whether the experimental asymmetry is consistent across different crystal forms or conditions, and (c) temper the interpretation to acknowledge that AF2's single-state prediction is an inherent limitation of the method, not a specific failure for NRs. If possible, they could compare AF2 predictions to multiple experimental structures of the same NR in different functional states to assess whether the predicted state corresponds to any experimentally observed state.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors report that "AF2 predictions show a general tendency toward higher α-helical content (mean difference = +4.2% ± 2.1% for DBDs, +3.8% ± 1.9% for LBDs, p < 0.05) and compensatory decreases in loop regions (−5.0% ± 2.3%, p < 0.05)"
- **Evidence pointer** Results section "Secondary structure element content analysis"; Methods section "SSE content analysis"
- **Concern** The SSE analysis methodology is not described in sufficient detail. The authors state that SSE content was calculated "using python scripts in PyMOL environment," but do not specify which secondary structure assignment algorithm was used (e.g., DSSP, STRIDE, or PyMOL's internal algorithm). Different algorithms can produce significantly different SSE assignments, particularly for loop vs. helical boundaries. Additionally, the authors report mean differences with standard deviations but do not specify the sample size for these comparisons. The claim of statistical significance (p < 0.05) is made without reporting the test statistic or degrees of freedom. The biological interpretation of a 4% difference in α-helical content is also not discussed; it is unclear whether this difference is functionally meaningful or within the range of variation expected from different SSE assignment methods.
- **Why it matters** The SSE analysis is one of the eight key metrics summarized in Table 1 and contributes to the overall assessment of AF2 performance. If the methodology is not reproducible or the differences are within the noise of the assignment algorithm, this finding adds little to the paper. The lack of methodological detail prevents readers from evaluating the robustness of this result.
- **Resolution test** The authors should specify the SSE assignment algorithm used, provide the sample sizes for each comparison, report the actual test statistics and p-values, and include a discussion of whether the observed differences are within the range expected from different SSE assignment methods. They should also consider reporting per-residue SSE agreement (e.g., Matthews correlation coefficient) rather than just global content percentages.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that "the structural gap in structural genomics refers to a state where a generated data from the next and third generation sequencing and the subsequent in silico prediction of protein-coding sequences grows over the time faster than the number of experimentally determined protein structures"
- **Evidence pointer** Introduction section
- **Concern** The introduction contains several unclear and grammatically problematic sentences that obscure the scientific rationale. The definition of the "structural gap" is convoluted and difficult to follow. More importantly, the introduction does not adequately review prior benchmarking studies of AF2 on nuclear receptors or other protein families. The authors claim this is the "first comprehensive analysis" but do not discuss what previous evaluations have been done, how their work differs, or what specific gaps they are filling. The introduction also does not clearly state the hypotheses or specific questions the study aims to address.
- **Why it matters** A clear and well-structured introduction is essential for establishing the scientific context and significance of the work. The current introduction does not adequately position the study within the existing literature, making it difficult for readers to assess the novelty and importance of the findings. The unclear writing also detracts from the overall quality of the manuscript.
- **Resolution test** The authors should rewrite the introduction to: (a) provide a clear definition of the structural gap, (b) review prior AF2 benchmarking studies on nuclear receptors and other protein families, (c) explicitly state the specific questions and hypotheses of the study, and (d) explain how this work advances beyond previous evaluations. The writing should be edited for clarity and precision.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Introduction, first paragraph
- **Evidence pointer** Introduction section
- **Issue** The first paragraph contains several grammatical errors and unclear phrasing. For example, "a generated data from the next and third generation sequencing" is awkward and imprecise. The sentence "By researchers in the structural biology community, the proposed solution to bridge this gap is the AlphaFold 2 (AF2) system" is grammatically incorrect.
- **Required correction** The introduction should be carefully edited for grammar and clarity. The authors should revise these sentences to be more precise and readable, for example: "The structural gap refers to the growing disparity between the number of known protein sequences and the number of experimentally determined structures. To address this gap, the structural biology community has proposed AlphaFold 2 (AF2), a computational system that combines algorithms and artificial intelligence to predict protein structures."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section, "RMSD analysis"
- **Evidence pointer** Methods section
- **Issue** The RMSD equation is referenced but not actually shown in the text. The authors state "according to the equation:" but the equation itself is missing from the provided text. Similarly, the equations for CV and Cohen's d are referenced but not displayed.
- **Required correction** The authors should ensure that all equations are properly displayed in the manuscript. If the equations were omitted in the provided text, they should be included in the final version.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results section, "Geometrical analysis of domain architecture"
- **Evidence pointer** Results section
- **Issue** The text describing the angle measurements is dense and difficult to follow. The authors introduce θ DBD,LBD and DH DBD,LBD without clearly explaining the geometric meaning of these parameters or why they are biologically relevant. The relationship between the angle measurements and the domain architecture analysis is not immediately clear.
- **Required correction** The authors should provide a brief explanation of what the angle and dihedral measurements represent geometrically and why they are informative for comparing predicted and experimental structures. A simple schematic or figure would help readers understand these parameters.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of asymmetric homodimers and their functional significance is interesting but goes beyond the data presented. The authors state that "the asymmetric organization, observed in both GR and HNF4α structures, likely reflects their need to accommodate symmetric self-association and represents a fundamental mechanism for DNA binding," but this interpretation is speculative and not directly tested in the study.
- **Required correction** The authors should either provide additional analysis to support this interpretation (e.g., comparison with other homodimeric transcription factors) or temper the language to acknowledge that this is a hypothesis that requires further investigation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results section, "The availability of structural data for human NRs in PDB"
- **Evidence pointer** Results section
- **Issue** The first paragraph of this section is a single, very long sentence that is difficult to parse. The listing of NRs and their structures is not well organized, and the reader has to work hard to extract the key information about which NRs have full-length structures available.
- **Required correction** The authors should break this paragraph into shorter sentences and consider using a table or bullet points to summarize the availability of structural data for each NR. This would improve readability and clarity.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section, "Analysis of LBP geometry"
- **Evidence pointer** Methods section
- **Issue** The authors state that "The LBPs were identified by hollow 1.3" but do not provide details on the parameters used for pocket detection. The choice of parameters can significantly affect the results, and without this information, the pocket volume measurements are not reproducible.
- **Required correction** The authors should provide the specific parameters used for pocket detection with hollow, or at minimum reference the default parameters and any modifications made.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of GPCR comparisons (reference 34) is brief and not well integrated into the main argument. The authors mention that GPCR studies "provide further evidence of these limitations" but do not explain how the GPCR findings relate to the NR results or what specific parallels exist.
- **Required correction** The authors should expand this comparison to explain what specific GPCR findings are relevant to their NR results and how they support or contrast with their conclusions.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is dense and tries to cover too many findings without sufficient context. The key message about AF2's limitations for NR prediction is not clearly stated until the end, and the abstract does not provide a clear take-home message for readers.
- **Required correction** The abstract should be restructured to clearly state the main finding (e.g., "AF2 accurately predicts core domains but fails to capture conformational diversity and pocket dynamics in nuclear receptors") and its implications for using AF2 models in drug design.

- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical methodology underdescribed), R1-M2 (pocket measurement methodology not reproducible), R1-M3 (single-conformation claim not properly supported), R1-M4 (SSE methodology not specified)

- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The study applies existing benchmarking approaches to a specific protein family (nuclear receptors) that has not been systematically evaluated. However, the general finding that AF2 performs well on ordered regions but poorly on flexible regions is not novel and has been reported in multiple prior studies. The specific focus on full-length NRs and the multi-metric approach provide some originality, but the conceptual framework is not new.
  - Scientific importance: Moderate. Nuclear receptors are important drug targets, and understanding AF2's limitations for this family has practical value. However, the study is descriptive rather than mechanistic, and the findings do not fundamentally change our understanding of AF2's capabilities or NR biology. The implications for drug design are stated but not developed in detail.
  - Interdisciplinary readership: Limited. The paper is primarily of interest to structural biologists and computational biologists working on protein structure prediction. The drug design implications are mentioned but not developed sufficiently to attract a broader pharmaceutical audience. The writing style and technical focus limit accessibility to non-specialists.
  - Technical soundness: Currently insufficient. The statistical methodology is underdescribed, the pocket measurement approach lacks reproducibility, and the interpretation of domain architecture results is partly speculative. The lack of detail on alignment protocols, sample sizes, and statistical test selection prevents evaluation of the robustness of the findings.
  - Readability for nonspecialists: Poor. The introduction is convoluted, the results sections are dense and technical, and the discussion assumes significant background knowledge of both AF2 and nuclear receptor biology. The paper would benefit from clearer explanations of the biological significance of the structural parameters being compared.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses a relevant question and has assembled a useful dataset, but the methodological weaknesses, particularly in the statistical analysis and pocket measurement, prevent the conclusions from being reliably supported. The authors need to provide a complete description of their methods, including alignment protocols, sample sizes, and statistical test selection, and should temper their interpretations where the data are not sufficient to support them. The paper could become a useful contribution to the AF2 benchmarking literature after these issues are addressed, but in its current form, the findings are not sufficiently robust to support the claims made.