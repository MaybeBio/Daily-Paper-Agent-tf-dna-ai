## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, experimental procedures, and figure legends
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors investigate structural and functional differences between the related transcription factors MAFA and MAFB, focusing on how non-DNA-binding regions, particularly the C-terminal tail, influence Insulin gene regulation. Using mutagenesis of crystallographically defined DNA-contact residues, functional reporter assays, and AlphaFold 2 structural predictions, they identify that MAFAR272A uniquely retains activity while the analogous MAFBR256A does not, and that chimeric proteins reveal C-terminal region contributions to cooperative activation with islet-enriched transcription factors such as PDX1, ISL1, and GLIS3.
- **Visible evidence base** Abstract; Results sections with Figures 1-6 and Supplementary Figures S1-S8 as referenced; Discussion; Experimental procedures; Data availability statement
- **Missing materials affecting confidence** Raw numerical data for reporter assays (individual data points, exact n values per experiment); full gel shift images without cropping; AlphaFold 2 model coordinates or confidence metrics (pLDDT, PAE); statistical test outputs beyond p-value ranges; Supplementary Figures S1-S8 content not fully described in text; exact construct sequences for chimeras

## Reviewer
- **Overall assessment** This manuscript addresses a meaningful question in transcription factor biology, namely how closely related MAF family proteins achieve distinct regulatory outcomes on a shared target gene. The combination of structure-guided mutagenesis, AlphaFold 2 prediction, and functional assays is timely and potentially informative. However, the central claims regarding the functional importance of predicted structural differences in the C-terminal region rest heavily on computational predictions that are not experimentally validated at the structural level, and the chimeric approach, while clever, introduces interpretational ambiguities that are not fully resolved. The study is descriptive rather than mechanistic, and several conclusions extend beyond what the data can support. The work may be of interest to specialists in islet biology and transcription factor regulation, but the current evidence does not fully establish the proposed structure-function relationships.

- **Who would be interested in the results, and why** Researchers studying pancreatic islet transcription factor networks, particularly those focused on MAFA and MAFB function in beta-cell identity and Insulin gene regulation. The work may also interest investigators using AlphaFold 2 to generate hypotheses about intrinsically disordered regions in transcription factors, and those studying cooperative transcriptional regulation at enhancers. The pathogenic variant analysis (MAFASer64Phe and MAFBSer70Ala) could attract clinical investigators interested in monogenic diabetes mechanisms.

- **Major strengths** The study addresses an important gap in understanding how highly related transcription factors achieve distinct regulatory functions. The combination of structure-guided mutagenesis with AlphaFold 2 predictions is a modern and potentially powerful approach. The use of chimeric proteins to map functional domains is a classic and effective strategy. The inclusion of pathogenic variants adds translational relevance. The experimental system (HeLa cells with defined transcription factor cotransfection) is clean and avoids confounding endogenous expression.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for structural claims
- **Claim pointer** The authors state that AlphaFold 2 predicts "unique structural features" and "differences in the three-dimensional organization" of MAFA and MAFB, and that these differences are functionally relevant.
- **Evidence pointer** Results section "AlphaFold 2 predicts structurally unique regions within the MAFA, MAFB, and their pathogenic variant proteins"; Figures 3, S3, S4
- **Concern** The manuscript relies on AlphaFold 2 predictions to claim structural differences between MAFA and MAFB, and between wild-type and pathogenic variants, but provides no experimental validation of these predicted structures. AlphaFold 2 is a prediction tool, not an experimental method, and its accuracy for intrinsically disordered regions, which the authors themselves describe as lacking "specific conformation," is particularly uncertain. The RMSD values reported (e.g., 0.123 between MAFAWT and MAFASer64Phe) are presented without context or statistical significance testing, and it is unclear whether such differences are meaningful given the inherent variability across the five seeds and 25 models. The claim that the C-terminal tail of MAFA "leads to a more divergent conformation" is based entirely on visual inspection of models, not quantitative analysis.
- **Why it matters** The central thesis of the manuscript is that structural differences in non-DNA-binding regions explain functional differences between MAFA and MAFB. If the structural predictions are not reliable, the functional interpretations built upon them are not supported. The authors need to either provide experimental structural validation (e.g., SAXS, NMR, cross-linking) or substantially temper their claims to acknowledge that AlphaFold 2 predictions are hypothesis-generating, not confirmatory.
- **Resolution test** Provide experimental validation of at least one predicted structural difference (e.g., via limited proteolysis, hydrogen-deuterium exchange, or cross-linking) or revise the claims to clearly frame the AlphaFold 2 results as untested predictions. Additionally, provide quantitative metrics of model confidence (pLDDT scores) for the regions where structural differences are claimed, and statistical comparison of RMSD distributions across the 25 models.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional significance of chimeric constructs
- **Claim pointer** The authors claim that chimeric proteins "retained the unique three-dimensional properties predicted by AlphaFold 2" and that results with chimeras demonstrate that C-terminal region structural differences influence cooperative activation with ISL1 and PDX1.
- **Evidence pointer** Results section "Analyzing how the predicted structurally unique regions of MAFA and MAFB affect ISL1 and PDX1 activation"; Figures 6, S7
- **Concern** The chimeric approach is confounded by the fact that swapping large domains (e.g., amino acids 1-208 of MAFA linked to residues 189-323 of MAFB) changes not only structure but also primary sequence, which could affect protein stability, post-translational modification sites, or interaction surfaces in ways unrelated to the predicted structural differences. The authors do not demonstrate that the chimeras are expressed at comparable levels to wild-type proteins, nor do they show that the chimeras fold properly. The claim that the chimeras "retained the unique three-dimensional properties" is based on AlphaFold 2 predictions of the chimeras, which is circular reasoning. Furthermore, the interpretation that loss of ISL1 cooperativity in MAFB/A reflects C-terminal structural requirements is complicated by the fact that the N-terminal swap also removes potential interaction surfaces.
- **Why it matters** The chimeric experiments are the primary functional evidence linking predicted structural differences to differential transcription factor cooperativity. If the chimeras are misfolded, unstable, or differentially expressed, the functional results cannot be attributed to the specific structural features the authors propose. The conclusions drawn from these experiments may be artifacts of the construct design rather than reflections of genuine biological differences.
- **Resolution test** Provide Western blot quantification of chimera expression levels relative to wild-type proteins. Include a control experiment showing that the chimeras retain DNA-binding activity comparable to wild-type. Consider generating more targeted mutations (e.g., swapping only the C-terminal tail) rather than large domain swaps. If the authors wish to claim structural retention, they should provide experimental evidence (e.g., limited proteolysis or CD spectroscopy) rather than relying on AlphaFold 2 predictions of the chimeras.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of functional conclusions
- **Claim pointer** The authors conclude that "the distinct structural features within full-length MAFA and MAFB mediate key functional interactions with other essential islet-enriched TFs" and that these findings "have revealed key structural features of these closely related proteins that impact their ability to regulate gene expression."
- **Evidence pointer** Results sections on cooperative activation; Discussion
- **Concern** All functional assays are performed in HeLa cells using a single reporter construct (Insulin -238 WT) and overexpression of transcription factors. This artificial system may not reflect the endogenous context of pancreatic beta cells, where chromatin structure, endogenous expression levels, and additional cofactors could substantially alter the observed cooperativity. The authors acknowledge this limitation in the Discussion but do not provide any validation in a more physiologically relevant system. The claim that these structural features are "key" for gene regulation is not supported by experiments in relevant cell types or at endogenous loci.
- **Why it matters** The manuscript aims to draw conclusions about the role of MAFA and MAFB in Insulin gene regulation, which is physiologically relevant to beta-cell function and diabetes. Overexpression in HeLa cells is a useful screening tool but cannot establish physiological relevance. Without confirmation in beta-cell lines, primary islets, or in vivo models, the broader claims about the importance of these structural features for Insulin regulation remain speculative.
- **Resolution test** Validate at least one key finding (e.g., the differential cooperativity with ISL1 or PDX1) in a beta-cell line such as MIN6 or EndoC-betaH1, or in primary human or mouse islets. Alternatively, use CRISPR-based approaches to introduce the relevant mutations at the endogenous MAFA or MAFB loci and assess effects on Insulin expression.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor of reporter assays
- **Claim pointer** The authors report statistically significant differences in reporter activity between wild-type and mutant MAF proteins, and between different cotransfection conditions.
- **Evidence pointer** Results sections; Figures 2, 5, 6; Statistical analysis section
- **Concern** The manuscript reports p-values and n values (n = 3-4) but does not provide effect sizes, confidence intervals, or information about the distribution of the data. For a study where the key findings are differences in fold-activation between conditions, it is essential to show the actual data distribution, not just summary statistics. Additionally, the use of n = 3-4 independent experiments is relatively low for drawing firm conclusions about modest differences in activation. The statistical methods are described as "mixed-effects analysis or 2-way ANOVA" but it is unclear which test was applied to which comparison.
- **Why it matters** The conclusions about differential cooperativity between MAFA and MAFB with other transcription factors rest on quantitative comparisons of reporter activity. If the data are noisy or the statistical approach is not clearly specified, the reliability of these conclusions is uncertain. The authors need to provide more transparent and rigorous quantitative analysis to support their claims.
- **Resolution test** Provide individual data points for all reporter assays (e.g., as dot plots overlaid on bar graphs). Specify which statistical test was used for each comparison and report effect sizes with confidence intervals. Consider increasing the number of independent experiments to strengthen the statistical power.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure presentation
- **Affected element** Figure 2C and 2D
- **Evidence pointer** Results section; Figure 2
- **Issue** The gel shift images are described as having dashed lines indicating where images were cropped for increased exposure. This practice can obscure the relationship between the original and enhanced images and makes it difficult to assess the quality of the data.
- **Required correction** Provide full uncropped gel images in the supplementary material, with clear labeling of the exposure times and any adjustments made.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** AlphaFold 2 modeling
- **Evidence pointer** Experimental procedures section
- **Issue** The methods state that AlphaFold 2 models were generated with ColabFold using model parameters version 2.3, but do not provide key parameters such as the number of recycles, whether templates were used, or the specific settings for the five seeds. This limits reproducibility.
- **Required correction** Provide the full command or configuration used for ColabFold runs, including all relevant parameters, and consider depositing the model coordinates in a public repository.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of RMSD values
- **Evidence pointer** Results section; Figure S3
- **Issue** The RMSD values comparing different models are reported without context. It is unclear what threshold would indicate a meaningful structural difference, and whether the observed values are within the expected variability of AlphaFold 2 predictions for the same protein.
- **Required correction** Provide a comparison of RMSD values between independent runs of the same protein (e.g., MAFAWT seed 1 vs. seed 2) to establish a baseline, and discuss whether the reported differences between variants exceed this baseline.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract; Discussion
- **Issue** The term "unique structural features" is used repeatedly, but the manuscript does not define what constitutes "unique" in this context. The structural differences described are based on computational predictions and are not experimentally confirmed.
- **Required correction** Replace "unique" with more precise language, such as "predicted structural differences" or "computationally predicted conformational variations," to accurately reflect the evidence level.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Control experiments
- **Affected element** Cotransfection experiments
- **Evidence pointer** Results section; Figure 5
- **Issue** The cotransfection experiments with PDX1, ISL1, NEUROD1, and GLIS3 do not include a control with an unrelated transcription factor to demonstrate specificity of the observed cooperativity.
- **Required correction** Include a control transcription factor (e.g., a non-islet bZIP factor) in the cotransfection experiments to show that the observed effects are specific to the tested islet-enriched factors.

## Risk / unsupported claims
- The claim that AlphaFold 2 predicts "unique structural features" that are functionally relevant is not supported by experimental structural validation; the predictions are presented as established facts rather than hypotheses.
- The statement that chimeric proteins "retained the unique three-dimensional properties predicted by AlphaFold 2" is circular and unsupported by any experimental structural data on the chimeras.
- The conclusion that "the distinct structural features within full-length MAFA and MAFB mediate key functional interactions" is an overstatement given that all functional data come from overexpression in HeLa cells with a single reporter construct.
- The claim that "differences in transactivation potential are unlikely due to differential target sequence affinity" is based on qualitative gel shift comparisons without quantitative binding affinity measurements.
- The assertion that "the newly defined structural regions identified are essential to MAFA and MAFB activity" is not supported by loss-of-function experiments targeting these specific regions.
- The relevance of the pathogenic variants (MAFASer64Phe and MAFBSer70Ala) to the structural predictions is not clearly established; the manuscript does not demonstrate that these mutations specifically alter the predicted structural features.