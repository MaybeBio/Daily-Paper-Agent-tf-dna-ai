## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, experimental section, and author contributions. No figures, tables, or supplementary materials were provided.
- **Assessment boundary** Assessment is limited to the claims and evidence as presented in the text. Figures, tables, and supplementary information are referenced but not available for direct evaluation.
- **Shared manuscript claim summary** The authors report that functional six-finger zinc finger nucleases (ZFNs) can be constructed via modular assembly of publicly available zinc finger modules, and that structural modeling using AlphaFold, Coot, and Rosetta can improve genome editing efficiency in HEK293T cells. They report obtaining two functional ZFN pairs out of ten tested, and that specific point mutations introduced via RosettaDNA increased editing efficiency from 22% to 27%.
- **Visible evidence base** Text descriptions of experimental procedures and results, including T7E1 assay outcomes, SSA reporter assay results, off-target analysis, and structural modeling parameters. Specific numerical values for editing efficiency are provided for some constructs.
- **Missing materials affecting confidence** All figures, tables, and supplementary information are absent. This includes the primary T7E1 gel data (Figure 1b, 1d, 1e), SSA assay data (Figure S2), off-target analysis data (Figure S3, S6), structural models (Figure 2, 3), and supporting tables (Tables S1-S4). Without these, the quantitative claims and the structural interpretations cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in the genome editing field, namely the construction and improvement of ZFNs, which are of interest for applications requiring small nuclease size. The authors combine modular assembly with structural modeling, which is a potentially useful approach. However, the evidence presented in the text is insufficient to fully support the central claims. The reported improvements in editing efficiency are modest, and the mechanistic interpretation of the mutations relies heavily on structural models that are not shown. The lack of primary data in the provided material prevents a rigorous assessment of the methodology and conclusions.
- **Who would be interested in the results, and why** Researchers in the fields of genome editing, gene therapy, and protein engineering would be interested. Specifically, those working on ZFN-based approaches for in vivo delivery, where the small size of ZFNs is an advantage, would find the potential for improved efficiency relevant. The use of structural modeling tools to guide protein engineering is also of general interest to the protein design community.
- **Major strengths**
  1. The problem addressed is significant. Improving ZFN efficiency is a bottleneck for their broader application, and the small size advantage of ZFNs is well articulated.
  2. The approach of combining modular assembly with publicly available resources and structural modeling is pragmatic and potentially accessible to other laboratories.
  3. The authors test their engineered ZFNs in a relevant cell line (HEK293T) and include an assessment of off-target effects at predicted sites.
  4. The study includes a negative result (2027L v2) which is informative, suggesting that increasing GNN recognition is not universally beneficial.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "the engineering of ZFNs using AlphaFold, Coot, or Rosetta increases the efficiency of genome editing by 5%".
- **Evidence pointer** Results section, "Engineering of ZF-ND1 Based on Structural Modeling"; Figure 3b; Discussion.
- **Concern** The central quantitative claim of a 5% increase in editing efficiency is presented in the text, but the primary data supporting this are not available in the provided material. The text states that specific mutations (P105S, V109K, A133S) led to efficiencies of 25%, 27%, and 26% respectively, compared to 22% for wild-type. However, without the actual gel images, densitometry data, or replicate information, it is impossible to assess the statistical significance, variability, or robustness of this difference. The claim that this represents a general improvement from structural modeling is also not fully supported, as only one ZFN pair (2027L+R) was improved, while the other functional pair (9299L+R) was not subjected to the same mutational analysis.
- **Why it matters** The primary conclusion of the manuscript rests on this quantitative improvement. If the effect is not robust or is within experimental noise, the central thesis is weakened. The lack of primary data prevents the reader from evaluating this.
- **Resolution test** Provide the raw T7E1 assay data (gel images and densitometry) for all replicates, with statistical analysis (e.g., mean, SD, number of independent experiments). Show that the improvement is reproducible and statistically significant.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that structural modeling with AlphaFold, Coot, and Rosetta is "effective in improving its function" and that specific mutations (e.g., V109K) improve efficiency by stabilizing the protein-DNA interaction.
- **Evidence pointer** Results section, "Structural Modeling of ZF-ND1 Through AlphaFold, Coot, and Rosetta" and "Engineering of ZF-ND1 Based on Structural Modeling"; Figures 2, 3, S4, S7.
- **Concern** The mechanistic interpretation of why specific mutations improve efficiency is based on structural models. The text states that V109K "may not directly interact with the phosphate backbones" but that the total score was lower, suggesting stability. This is a correlative, not causal, link. The structural models themselves (Figure 2, 3) are not provided, so the quality of the models, the rationale for the specific mutations chosen, and the validity of the RosettaDNA predictions cannot be assessed. The claim that the approach is "effective" is based on a single successful example (2027R) and is not generalized.
- **Why it matters** The novelty of the approach lies in the use of structural modeling to guide engineering. If the structural rationale is not clearly demonstrated and validated, the approach may be seen as a case-by-case empirical exercise rather than a generalizable method.
- **Resolution test** Show the structural models with the mutated residues highlighted, and provide a clear structural rationale for each mutation. Ideally, validate the predicted interactions with an orthogonal method, such as binding assays or molecular dynamics simulations. Demonstrate the generalizability of the approach by applying it to more than one ZFN pair.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and completeness
- **Claim pointer** The authors state that "two out of the 10 ZF-ND1 pairs cleaved the target DNA" and that the efficiency of the initial functional pairs was "low (≈11%)".
- **Evidence pointer** Results section, "Development of Functional ZF-ND1 Pairs"; Figure 1b.
- **Concern** The success rate of 2 out of 10 is a key metric for the modular assembly approach. However, the details of the 8 unsuccessful pairs are not provided. Were they completely inactive, or just below a detection threshold? The text mentions that 9299L+R had lower activity, but the range of activities across the 10 pairs is not described. This information is critical for understanding the reliability of the modular assembly method.
- **Why it matters** The authors claim that modular assembly is "useful for creating 6-finger ZF-ND1s". A 20% success rate, while potentially useful, needs to be contextualized. Without data on the failures, it is difficult to know if the method is broadly applicable or if the two successes were fortuitous.
- **Resolution test** Provide a table or figure showing the activity of all 10 ZFN pairs, including the negative ones. Discuss the potential reasons for the failures (e.g., poor expression, incorrect folding, weak DNA binding).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Evidence sufficiency
- **Claim pointer** The authors state that "No additional bands were detected between the non-transfected and transfected cells" in off-target analysis, indicating no mutations at the tested sites.
- **Evidence pointer** Results section, "Development of Functional ZF-ND1 Pairs" and "Engineering of ZF-ND1 Based on Structural Modeling"; Figures S3, S6.
- **Concern** The off-target analysis is limited to the "two highest potential off-target sites" identified by nucleotide BLAST. This is a very limited assessment. The sensitivity of the T7E1 assay is known to be limited, and the choice of only two sites based on sequence similarity may miss off-target effects at other loci. The text does not specify the number of mismatches allowed in the BLAST search or the criteria for ranking.
- **Why it matters** Off-target activity is a critical safety concern for any genome editing tool. A limited analysis that does not detect off-targets does not establish safety, only that no off-targets were detected at the specific sites tested.
- **Resolution test** Provide a more comprehensive off-target analysis, such as whole-genome sequencing or GUIDE-seq, to support the claim of specificity. At minimum, describe the BLAST search parameters and justify the selection of only two sites.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and reproducibility
- **Affected element** Experimental section, "Modeling of Protein-DNA Interactions"
- **Evidence pointer** Experimental section, "Modeling of Protein-DNA Interactions"
- **Issue** The description of the modeling procedure is brief. The text states that AlphaFold was used to model the protein, Coot for the DNA, and Rosetta for refinement and mutation. However, the specific parameters for the RosettaDNA run, such as the score function, the number of models, and the criteria for selecting the "top 10" models, are not fully detailed. The text mentions a "RosettaScripts XML-like protocol file" but does not provide it or a link to it.
- **Required correction** Provide a more detailed description of the modeling protocol, including all relevant parameters and the protocol file as supplementary material, to ensure the work is reproducible.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results section, "Development of Functional ZF-ND1 Pairs"
- **Evidence pointer** Results section, "Development of Functional ZF-ND1 Pairs"; Figure 1e.
- **Issue** The text reports that cold shock enhanced editing efficiency to 22%, 16%, and 26% for 2027L+R, 9299L+R, and 9299L(v2)+R, respectively. However, the baseline efficiencies for these pairs under standard conditions are not all explicitly stated in the text. The baseline for 9299L+R is implied to be lower than 9299L(v2)+R, but the exact values are not given.
- **Required correction** Clearly state the baseline efficiency for each pair under standard conditions (37°C) alongside the cold shock data, so the magnitude of the enhancement can be directly assessed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The authors state that "this study is the first to demonstrate the high functionalization of ZFNs through structural modeling using AlphaFold, Coot, and Rosetta." This is a strong claim. While the combination of these specific tools may be novel, structural modeling has been used to engineer ZFNs before. The claim of "first" should be tempered or more carefully qualified.
- **Required correction** Soften the claim of "first" and instead state that this is a novel application of these specific tools in combination, or provide a more thorough literature review to support the claim of priority.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that engineering "increases the efficiency of genome editing by 5%". This is a specific number, but it is not clear if this is an absolute increase (e.g., from 22% to 27%) or a relative increase. The text in the results clarifies this is absolute, but the abstract alone is ambiguous.
- **Required correction** Clarify in the abstract whether the 5% increase is absolute or relative.

## Risk / unsupported claims
- The claim that structural modeling "increases the efficiency of genome editing by 5%" is unsupported without the primary data from Figure 3b and the associated replicates.
- The claim that the approach is "effective" for improving ZFN function is weakly supported, as it is based on a single successful example (2027R) and the mechanistic link is correlative.
- The claim that the modular assembly system is "useful" is partially supported, but the 20% success rate needs more context and data on the failures.
- The claim of being "the first" to demonstrate this specific combination of tools is not verifiable from the provided text and is likely overstated.
- The off-target analysis is too limited to support any strong claim of specificity.