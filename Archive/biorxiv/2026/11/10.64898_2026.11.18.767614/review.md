## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present a computational pipeline that uses AlphaFold3 to model zebrafish transcription factors (TFs) with candidate DNA motifs derived from accessible chromatin, and NA-MPNN to infer binding motifs from high-confidence structural predictions. They report that predicted motifs match experimentally characterized motifs for 44% of 210 TFs with known orthologs, and that the resulting database, ZebraMotif, covers all 2,543 zebrafish TFs, 2.8 times the number covered by CisBP. They further claim the approach is applicable to any species lacking experimental binding data.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials were provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methods details, validation statistics, database contents, and code documentation were not provided. The abstract alone is insufficient to assess the technical soundness of the pipeline or the robustness of the reported performance metrics.

## Reviewer

- **Overall assessment** The abstract describes a potentially valuable computational approach to a well-recognized problem in genomics, namely the scalable inference of TF binding motifs for species with limited experimental data. The reported 44% match rate against known motifs is modest but could be useful if the method's precision and recall characteristics are well characterized. However, the abstract does not provide sufficient methodological detail or validation evidence to assess whether the claims are technically sound. The comparison to CisBP is presented without context regarding the quality or completeness of the CisBP zebrafish collection, and the claim of general applicability to any species is not supported by evidence presented here. The work may be of interest to the genomics and gene regulation communities, but the case is not established from the abstract alone.
- **Who would be interested in the results, and why** Researchers studying gene regulation, particularly those working on non-model organisms or species with limited TF binding data, would be interested. The approach could also appeal to computational biologists developing structure-based prediction methods and to zebrafish geneticists seeking to interpret regulatory element data. The database resource itself may be useful to the broader zebrafish research community.
- **Major strengths** The problem addressed is important and timely, as experimental TF binding assays do not scale well across proteomes. The approach is conceptually novel in combining AlphaFold3 structural prediction with NA-MPNN for motif inference at proteome scale. The reported coverage improvement over CisBP suggests a practical contribution. The stated generality of the method, requiring only a proteome and candidate motifs, is an appealing feature.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The claim that predicted motifs match known motifs for 44% of 210 TFs with experimentally characterized orthologs.
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract reports a 44% match rate but provides no details on how "match" was defined, what threshold was used, what comparison metric was applied, or how the 210 TF set was selected. Without this information, the performance claim cannot be interpreted or compared to existing methods.
  - **Why it matters** The 44% figure is the central quantitative claim supporting the method's utility. If the match definition is lenient or the test set is biased toward easy cases, the reported performance could be misleading. Conversely, if the definition is strict, the method may be more useful than the number suggests. The lack of context makes the claim uninterpretable.
  - **Resolution test** Provide the full validation methodology, including the definition of a motif match, the comparison metric (for example, Pearson correlation on position weight matrices or fraction of matched positions), the threshold used, and the criteria for selecting the 210 TF test set. Report precision and recall separately, and include a comparison to existing prediction methods on the same test set.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The claim that the approach is applicable to any species lacking experimental binding data.
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract states the method requires only a proteome and a set of candidate motifs, but no evidence is presented that the pipeline generalizes beyond zebrafish. The candidate motif derivation from accessible chromatin may depend on species-specific data quality, and the AlphaFold3 modeling step may perform differently across proteomes with varying structural diversity.
  - **Why it matters** The generality claim is a major part of the paper's significance. If the method fails or degrades substantially on other species, the contribution is considerably weakened. The abstract provides no cross-species validation or discussion of potential limitations.
  - **Resolution test** Provide validation on at least one additional species with known TF motifs, ideally one that is evolutionarily distant from zebrafish. Report performance metrics comparable to those used for zebrafish and discuss any species-specific factors that affect the pipeline's success.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Scientific importance
  - **Claim pointer** The claim that ZebraMotif covers 2.8 times as many TFs as CisBP's zebrafish collection.
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The comparison to CisBP is presented without context. It is unclear whether the additional coverage represents high-confidence predictions or low-quality inferences that merely inflate the count. The abstract does not state how many of the 2,543 TFs have predicted motifs with confidence scores above a useful threshold.
  - **Why it matters** Coverage numbers are only meaningful if the added predictions are reliable. If the additional motifs are mostly low-confidence, the database could mislead users. The comparison to CisBP also needs a description of how CisBP's zebrafish collection was curated and whether the two resources are directly comparable.
  - **Resolution test** Report the distribution of confidence scores across all 2,543 predicted motifs, and provide the number of motifs above a pre-specified confidence threshold. Describe the CisBP zebrafish collection used for comparison, including its version and curation status. Consider benchmarking a sample of the additional predictions against experimental data where available.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The abstract uses NA-MPNN without explaining what this tool is or why it is appropriate for motif inference. Readers unfamiliar with the protein design literature may not understand the role of this component.
  - **Required correction** Add a brief phrase describing NA-MPNN as a neural network for protein sequence design adapted here for DNA motif inference, or provide a one-sentence explanation of its function in this context.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The abstract does not state how the 44% match rate compares to a null expectation or to existing computational prediction methods. Without a baseline, it is unclear whether the method adds value over simpler approaches such as homology-based transfer.
  - **Required correction** Include a comparison to at least one baseline method, such as direct homology transfer from human or mouse motifs, on the same 210 TF test set.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interdisciplinary readership
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The phrase "links accessible regulatory elements to candidate upstream regulators genome-wide" is vague. It is unclear what kind of linking is performed and how the motif predictions are used to make these links.
  - **Required correction** Specify the nature of the linking analysis, for example whether it involves scanning accessible chromatin regions for predicted motif matches and assigning statistical significance, and report a representative result from this analysis.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The central performance claim is not interpretable without validation details, the generality claim lacks cross-species evidence, and the coverage comparison lacks context regarding prediction confidence.
- **Assessment against Nature-style criteria** Originality is potentially high, as the combination of AlphaFold3 and NA-MPNN for proteome-scale motif inference appears novel. Scientific importance is substantial if the method performs reliably, given the widespread need for TF motif information in non-model organisms. Interdisciplinary readership is plausible, spanning structural biology, genomics, and gene regulation. Technical soundness cannot be assessed from the abstract alone, as the validation methodology and performance metrics are not described. Readability for nonspecialists is adequate but could be improved with brief explanations of the computational tools used.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a promising approach and a useful resource, but the central quantitative claims are not interpretable without methodological detail and validation evidence. A full manuscript with detailed methods, validation statistics, and cross-species tests would be needed to assess whether the case is established.

## Risk / unsupported claims

- The 44% match rate is uninterpretable without a definition of "match" and a description of the test set.
- The claim of applicability to any species is unsupported by cross-species validation.
- The coverage comparison to CisBP is not contextualized with respect to prediction confidence or CisBP curation.
- The claim that the approach "links accessible regulatory elements to candidate upstream regulators genome-wide" is vague and not supported by specific results.
- The overall utility of the ZebraMotif database cannot be assessed without information on confidence scoring and error rates.