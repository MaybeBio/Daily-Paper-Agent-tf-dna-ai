## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no methods, figures, tables, or supplementary materials were available for evaluation
- **Shared manuscript claim summary** The authors report cloning three small-effect QTLs (qPHDF11.2, qPHDF12, qPHDF10) and identifying the corresponding genes (OsGH18, OsMYB2, OsCAD3) that form a regulatory module controlling drought tolerance in rice via tri-genic epistasis. They propose an integrated strategy combining GWAS, multi-omics, and AlphaFold3 structural prediction, and report that specific allelic combinations explain 6% to 35% of field performance variation across diverse rice accessions.
- **Visible evidence base** Abstract text only; no experimental details, statistical analyses, figures, or tables provided
- **Missing materials affecting confidence** Full manuscript, methods, all figures and tables, statistical outputs, population descriptions, phenotypic data, haplotype definitions, and validation experiments

## Reviewer
- **Overall assessment** The abstract presents a potentially important advance in connecting functional genomics to quantitative genetic parameters for a complex trait. The concept of resolving tri-genic epistasis among natural alleles within a functionally validated regulatory module is intellectually appealing and could have practical breeding implications. However, the abstract alone provides insufficient evidence to evaluate the robustness of the genetic analyses, the strength of the epistatic model, or the predictive claims. Several key assertions, particularly regarding the magnitude of explained variance and the generalizability of the model, require careful scrutiny of the underlying data.
- **Who would be interested in the results, and why** Rice geneticists and breeders interested in drought tolerance improvement; quantitative geneticists studying epistasis and polygenic adaptation; plant molecular biologists working on lignin biosynthesis and transcriptional regulation; researchers developing integrative approaches that combine functional genomics with predictive modeling for complex trait improvement.
- **Major strengths** The work addresses a recognized gap between gene cloning and practical utilization in crop improvement. The integration of GWAS, multi-omics, structural prediction, and quantitative genetic modeling is methodologically ambitious. The focus on small-effect QTLs and epistatic interactions reflects the genetic architecture of complex traits more realistically than single-gene studies. The reported predictive power across multiple populations suggests potential practical utility.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality is high, as the concept of resolving multi-genic epistasis within a functionally validated module represents a novel integration of molecular and quantitative genetics. Scientific importance is potentially substantial for both fundamental understanding of complex trait architecture and applied rice breeding. Interdisciplinary readership is plausible, spanning molecular biology, quantitative genetics, and breeding. Technical soundness cannot be assessed from the abstract alone, and the statistical claims require rigorous evaluation. Readability for nonspecialists is adequate, though the abstract is dense and assumes familiarity with QTL, GWAS, and epistasis concepts.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an intriguing framework, but the core claims regarding epistasis, predictive power, and generalizability cannot be verified without full access to methods and results. A supportive posture would require that the technical concerns identified here are resolved in the full manuscript.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validity
- **Claim pointer** The abstract claims that the tri-genic epistatic model "fits well with five DT-related traits" and "shows strong predictive power (approximately 6%-35%) for field performance across diverse rice accessions from three populations."
- **Evidence pointer** Location not provided
- **Concern** The range of 6% to 35% explained variance is extremely wide, and the abstract does not specify which traits correspond to which values, how the model was validated, or whether cross-validation or out-of-sample prediction was used. The claim of "strong predictive power" is difficult to evaluate without knowing the baseline, the number of accessions, population structure considerations, or the statistical methods employed.
- **Why it matters** Predictive power is the central practical claim of the manuscript. If the 6% to 35% range reflects overfitting or population-specific effects, the generalizability of the model would be substantially weakened. The wide range also raises questions about consistency across traits and stages.
- **Resolution test** Provide detailed statistical methods including model specification, validation approach (e.g., cross-validation, independent validation sets), the number of accessions per population, and trait-specific R-squared values with confidence intervals. Demonstrate that the predictive power is robust to population structure and does not arise from overfitting.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Genetic evidence
- **Claim pointer** The abstract states that "compelling evidence demonstrates that OsGH18, OsMYB2, and OsCAD3 correspond to qPHDF11.2, qPHDF12, and qPHDF10, respectively."
- **Evidence pointer** Location not provided
- **Concern** The abstract does not describe the nature of the evidence linking the cloned genes to the QTLs. It is unclear whether this includes complementation tests, loss-of-function mutants, transgenic validation, or association evidence alone. The term "compelling evidence" is subjective and cannot be evaluated without experimental details.
- **Why it matters** The entire epistatic model depends on correct gene-to-QTL assignment. If the correspondence is based solely on association or expression data rather than functional validation, the causal claims would be weakened.
- **Resolution test** Describe the experimental approaches used to establish gene-QTL correspondence, including mutant phenotypes, complementation, or transgenic overexpression/knockdown data. Provide clear evidence that allelic variation at these genes underlies the QTL effects.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Epistasis model validity
- **Claim pointer** The abstract claims "strong epistatic interactions among alleles at these three loci" and proposes a "generalized model in which specific allelic combinations at OsMYB2, OsGH18, and OsCAD3 function as a single regulatory module."
- **Evidence pointer** Location not provided
- **Concern** The abstract does not specify how epistasis was defined, tested, or quantified. It is unclear whether the model includes only pairwise interactions, whether higher-order interactions were tested, how many allelic combinations were evaluated, and whether the model accounts for additive effects before claiming epistasis. The phrase "tri-genic epistasis" implies a three-way interaction, but the statistical evidence for this specific term is not described.
- **Why it matters** Epistasis claims are frequently sensitive to statistical methodology and can be inflated by inadequate sample sizes or failure to account for additive and pairwise effects. The central conceptual contribution of the paper depends on the robustness of this epistatic model.
- **Resolution test** Provide the statistical framework used to detect and quantify epistasis, including the model formula, the number of genotypes tested, the multiple testing correction applied, and a comparison of additive, pairwise, and three-way interaction models. Show that the tri-genic interaction term is statistically significant beyond additive and pairwise effects.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional mechanism
- **Claim pointer** The abstract states that "OsMYB2 functions as a drought-induced transcription factor that regulates OsGH18 and OsCAD3, both of which are directly involved in lignin biosynthesis" and that the module modulates "lignin biosynthesis and cell-wall lignin, thereby improving DT."
- **Evidence pointer** Location not provided
- **Concern** The regulatory hierarchy and the causal link to drought tolerance are stated as facts, but the abstract provides no experimental support. It is unclear whether the transcriptional regulation was demonstrated by ChIP-seq, DAP-seq, or reporter assays, and whether the lignin phenotype was directly measured and causally linked to drought tolerance.
- **Why it matters** The mechanistic model is a key part of the conceptual advance. If the regulatory relationships or the lignin-drought tolerance link are inferred rather than experimentally demonstrated, the strength of the conclusions would be reduced.
- **Resolution test** Provide experimental evidence for the transcriptional regulation (e.g., binding assays, expression analyses in mutants) and for the causal role of lignin modification in drought tolerance (e.g., lignin content measurements, histochemical staining, and phenotypic analysis of lignin-altered lines under drought).

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** QTL nomenclature
- **Evidence pointer** Abstract, first paragraph
- **Issue** The QTL names qPHDF11.2, qPHDF12, and qPHDF10 are introduced without explanation of the naming convention or the chromosomes on which they reside.
- **Required correction** Briefly indicate the chromosome locations or provide a supplementary table listing QTL details.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological transparency
- **Affected element** AlphaFold3 usage
- **Evidence pointer** Abstract, first paragraph
- **Issue** The abstract mentions AlphaFold3 structural prediction as part of the integrated strategy, but does not specify what structures were predicted or how the predictions informed the functional characterization.
- **Required correction** Clarify the role of AlphaFold3 predictions in the study, such as predicting protein-protein interactions or DNA-binding domains, and how these predictions were validated experimentally.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Small-effect QTLs"
- **Evidence pointer** Abstract, first paragraph
- **Issue** The term "small-effect QTLs" is used, but the abstract later reports 6% to 35% explained variance, which for individual QTLs would not typically be considered small.
- **Required correction** Clarify whether the QTLs are small-effect individually and the epistatic combination produces larger effects, or whether the 6% to 35% range refers to the combined model.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Generalizability
- **Affected element** "Three populations"
- **Evidence pointer** Abstract, second paragraph
- **Issue** The abstract states the model shows predictive power across "three populations" but does not describe the nature of these populations (e.g., subspecies, geographic origins, breeding lines).
- **Required correction** Briefly describe the three populations in terms of genetic diversity and relationship to the discovery population.

## Risk / unsupported claims
- The claim that OsGH18, OsMYB2, and OsCAD3 correspond to the three QTLs is unsupported in the abstract, as no experimental evidence is described.
- The claim of "strong tri-genic epistasis" is unsupported without statistical details on how epistasis was detected and quantified.
- The claim of "strong predictive power (approximately 6%-35%)" is unverifiable without information on validation methods, sample sizes, and trait-specific values.
- The regulatory hierarchy (OsMYB2 regulating OsGH18 and OsCAD3) is stated without supporting experimental evidence.
- The causal link between lignin biosynthesis and drought tolerance improvement is asserted without direct phenotypic or biochemical data.
- The general statement that "epistatic interactions across multiple alleles can be computationally resolved using quantitative genetic models" is presented as a broad implication that extends beyond the specific system studied and requires additional support.