## Review setup
- **Input scope** Full manuscript text (abstract, methods, results, discussion) without supplementary figures/tables
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and structural modeling conclusions as presented in the main text
- **Shared manuscript claim summary** The authors identify sae2 alleles specifically impaired in hairpin resolution, characterize sae2-ΔC23 (lacking the last 23 amino acids) as selectively defective in MRX endonuclease activation while preserving other Sae2 functions, and use AlphaFold3 modeling to propose a structural mechanism involving phosphorylated S267 and T279 in stabilizing the Mre11-Rad50-Sae2 cutting state.
- **Visible evidence base** Main text figures referenced (Figures 1-7), methods descriptions, and in-text data presentations; supplementary materials not directly examined
- **Missing materials affecting confidence** Supplementary Figures S1-S4, Supplementary Tables S1-S5, full strain lists, complete western blot images, and raw quantitative data

## Reviewer
- **Overall assessment** This manuscript presents a focused genetic and structural analysis of the Sae2 C-terminus in regulating MRX endonuclease activity. The genetic screen identifying sae2 alleles and the subsequent characterization of sae2-ΔC23 are well-executed and provide meaningful functional separation between Sae2 roles in endonuclease activation versus checkpoint regulation. The AlphaFold3-based structural modeling is intriguing and generates testable hypotheses, but the reliance on computational predictions without experimental validation of the proposed interface contacts weakens the mechanistic claims. The manuscript is of interest to the DNA repair community, though the advance over existing knowledge is incremental rather than transformative.

- **Who would be interested in the results, and why** Researchers studying DNA double-strand break repair, particularly those focused on the MRX/MRN complex, Sae2/CtIP function, and the regulation of endonuclease activity. The work also has relevance for those interested in meiotic recombination and the removal of protein-DNA adducts. The structural modeling approach may interest computational biologists studying protein-DNA repair complexes.

- **Major strengths** The genetic screen is well-designed and successfully identifies separation-of-function alleles. The functional characterization of sae2-ΔC23 is thorough, demonstrating specificity for endonuclease activation while preserving checkpoint functions. The combination of genetics, biochemistry, and structural prediction provides multiple lines of evidence. The identification of T279 as a potentially important phosphorylation site adds new information.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for structural claims
- **Claim pointer** The authors claim that AlphaFold3 modeling reveals specific interactions between Sae2 C-terminus residues and Rad50 that are "critical for stabilizing the association between Sae2 and Rad50, thereby ensuring the correct positioning of Mre11 in its active endonucleolytic state."
- **Evidence pointer** Results section "AlphaFold3-based modeling of the Sae2 C-terminus bound to Rad50", Figures 4-7
- **Concern** The central mechanistic conclusion relies heavily on AlphaFold3 predictions without experimental validation of the predicted interface contacts. While the genetic rescue experiments (charge-swap mutations) provide some support, these are indirect and only test a subset of predicted interactions. The manuscript does not present direct binding assays, structural validation (e.g., crosslinking, NMR, crystallography), or in vitro reconstitution experiments to confirm the predicted Sae2-Rad50-Mre11 tripartite interface.
- **Why it matters** The claim that specific residues form a "network of interactions" that stabilize the active conformation is a strong structural statement. Without experimental validation, the mechanistic model remains speculative. The field has been misled before by confident computational predictions that did not hold up experimentally.
- **Resolution test** Provide direct biochemical evidence for the predicted interactions, such as co-immunoprecipitation with specific point mutants, surface plasmon resonance or isothermal titration calorimetry binding assays, or crosslinking mass spectrometry. Alternatively, validate the model using an orthogonal structural method or demonstrate that the predicted interface mutations abolish complex formation in vitro.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Functional significance of T279 phosphorylation
- **Claim pointer** The authors state that "the phosphorylated Thr279 residue" is part of the Rad50-Sae2 interface and that T279 phosphorylation is "mandatory for AlphaFold3 to construct the model in cutting state."
- **Evidence pointer** Results section "AlphaFold3-based modeling of the Sae2 C-terminus bound to Rad50", Figures 5-6
- **Concern** The functional data for T279 are limited to a single genetic experiment (sae2-T279A showing reduced recombination, sae2-T279E showing increased recombination). The manuscript does not directly demonstrate that T279 is phosphorylated in vivo, identify the kinase responsible (beyond citing prior work on Mec1/Tel1), or show that phosphorylation at T279 is required for Sae2-Rad50 interaction. The claim that T279 phosphorylation is "mandatory" for the cutting state is based solely on computational modeling.
- **Why it matters** The manuscript introduces T279 as a potentially novel regulatory site, but the evidence is insufficient to establish its physiological relevance. If T279 phosphorylation is truly important, this would be a significant finding; however, the current data do not distinguish between a genuine regulatory mechanism and a computational artifact.
- **Resolution test** Demonstrate T279 phosphorylation in vivo using phospho-specific antibodies or mass spectrometry. Show that T279 phosphorylation is regulated by DNA damage or cell cycle. Test whether a phospho-null mutant (T279A) fails to interact with Rad50 in co-immunoprecipitation assays while the phospho-mimetic (T279E) retains interaction.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative data presentation and statistical rigor
- **Claim pointer** The authors report "decreased rates of Lys+ recombinants" and "increased resistance to CPT and phleomycin" for various mutants, and state that double mutants "exhibited a recombination rate higher than that of the more severe" single mutant.
- **Evidence pointer** Results sections "Identification of sae2 alleles specifically impaired in hairpin resolution" and "Evaluation of the Sae2 and Rad50 interface by targeted mutagenesis", Figures 1, 6, 7
- **Concern** The manuscript does not present quantitative data with error bars, statistical significance values, or replicate numbers for the recombination rate measurements and drug sensitivity assays. The text describes differences as "decreased" or "increased" without providing the magnitude of effects or statistical analysis. The methods section mentions t-tests but does not specify how many biological replicates were performed or how significance was determined for each comparison.
- **Why it matters** The genetic rescue experiments are central to validating the structural predictions. Without proper quantitative presentation and statistical analysis, it is impossible to assess the robustness of the conclusions, particularly for the charge-swap experiments where the differences between single and double mutants may be subtle.
- **Resolution test** Provide bar graphs with individual data points, error bars, and p-values for all quantitative assays. Specify the number of biological and technical replicates. For the genetic rescue experiments, show that the observed suppression is statistically significant and reproducible across multiple independent transformants.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of structural model to human CtIP
- **Claim pointer** The authors state that "although Sae2 and CtIP may have undergone structural reorganization during evolution, their ability to stabilize the active conformation of MRX could be conserved" and present a human CtIP model in the supplementary data.
- **Evidence pointer** Discussion section, Supplementary Figure S3
- **Concern** The extrapolation from yeast Sae2 to human CtIP is based on a single AlphaFold3 model presented only in supplementary data. The sequence conservation between Sae2 and CtIP in the C-terminal region is noted to be low, yet the authors suggest functional conservation of the mechanism. The manuscript does not experimentally test any predictions in the human system.
- **Why it matters** The claim of evolutionary conservation has implications for human disease understanding, but the evidence is too thin to support this extrapolation. Overstating conservation without experimental support could mislead researchers working on human CtIP.
- **Resolution test** Either temper the claims about human CtIP to clearly state these are speculative predictions requiring experimental validation, or provide experimental evidence in human cells or with purified human proteins to support the conservation claim.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of mutant nomenclature
- **Affected element** Results section "Identification of sae2 alleles specifically impaired in hairpin resolution"
- **Evidence pointer** Figure 1B
- **Issue** The manuscript describes sae2-L302* and sae2-L323* as "nonsense" mutations but does not clearly explain the predicted truncation lengths or whether these truncations remove known functional domains beyond the C-terminus.
- **Required correction** Provide a schematic of Sae2 domain structure with the positions of all mutations indicated, and clarify what is known about the functional importance of the deleted regions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methods detail for AlphaFold3 modeling
- **Affected element** Methods section "Structural bioinformatics"
- **Evidence pointer** Methods, "Structural bioinformatics" subsection
- **Concern** The description of AlphaFold3 modeling lacks important parameters: number of models generated, ranking criteria, confidence thresholds used for interface analysis, and how the "cutting state" was defined or validated.
- **Required correction** Add details on model generation, selection criteria, and validation steps. Specify how the cutting state was identified and whether alternative conformations were observed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Presentation of ChIP data
- **Affected element** Results section "The lack of the Sae2 C-terminus maintains Sae2 function in inhibiting Rad53 activation"
- **Evidence pointer** Figure 3D-F
- **Issue** The ChIP data for Mre11, Tel1, and Rad9 are described qualitatively in the text without clear presentation of the magnitude of enrichment differences or the statistical significance.
- **Required correction** Include quantitative ChIP data with error bars and statistical analysis, or clearly reference supplementary figures where these data are shown.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of alternative interpretations
- **Affected element** Discussion section
- **Evidence pointer** Discussion, first paragraph
- **Issue** The discussion does not address alternative explanations for the observed phenotypes, such as potential effects of the C-terminal truncation on Sae2 protein stability in specific contexts or indirect effects on other protein interactions.
- **Required correction** Add a paragraph discussing alternative interpretations and limitations of the genetic approach.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality and data accessibility
- **Affected element** Figures 4-7
- **Evidence pointer** Figures 4-7
- **Issue** The structural figures are described but not shown in the main text provided. The quality of the AlphaFold3 models and the clarity of the interface representations cannot be assessed.
- **Required correction** Ensure structural figures clearly show the predicted interfaces with labeled residues, and consider providing a supplementary video or interactive model for clarity.

## Risk / unsupported claims
- The claim that T279 phosphorylation is "mandatory" for the cutting state conformation is unsupported by experimental evidence and relies entirely on computational modeling.
- The extrapolation of the structural mechanism to human CtIP is speculative and not supported by experimental data in human systems.
- The statement that the identified interactions are "critical for stabilizing the association between Sae2 and Rad50" is not directly tested; the genetic data show functional effects but do not demonstrate changes in binding affinity or complex stability.
- The claim that sae2-ΔC23 "maintains Sae2 functions in resection of an endonuclease-induced DSB" is based on a single assay (Southern blot detection of resection) and may not capture all aspects of resection function.
- The manuscript does not provide evidence that the sae2-T279E mutant is "even more active than the wild-type counterpart" beyond a single recombination rate measurement, which is a strong claim requiring additional validation.