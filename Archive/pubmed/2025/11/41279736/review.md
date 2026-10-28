## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, data availability)
- **Assessment boundary** Scientific content, methodological soundness, claim-evidence alignment, and presentation quality as presented in the preprint
- **Shared manuscript claim summary** The authors present a structure-guided atlas of human and Drosophila kinase–transcription factor interactions, built using AlphaFold-Multimer predictions scored with a new interface-aware metric (iLIS). They claim the atlas recapitulates known interaction principles, uncovers a conserved homeodomain docking motif, maps allosteric hotspots, and enables discovery of a Sgg/GSK3–Hnf4 regulatory axis controlling lipid metabolism in vivo.
- **Visible evidence base** Main text figures (referenced as Figures 1–7), supplementary figures (referenced as Supplementary Figures 1–12), supplementary data (referenced as Supplementary Data 1–5), methods section, and data availability statement
- **Missing materials affecting confidence** Supplementary figures, supplementary data files, and supplementary text sections are referenced but not provided in the submitted material. This limits full verification of benchmarking details, complete motif data, and extended validation results.

## Reviewer

- **Overall assessment** This manuscript presents a large-scale computational resource with substantial potential value for the signaling community. The iLIS scoring framework addresses a genuine limitation of global confidence metrics for transient, flexible interfaces. The benchmarking against known interactions and the experimental validation of the Sgg–Hnf4 axis provide meaningful support for the approach. However, the manuscript currently overstates several conclusions relative to the evidence shown, particularly regarding the homeodomain docking motif as a general mechanism and the therapeutic relevance of mapped allosteric hotspots. The in vitro and in vivo validations are limited in scope, and key methodological details are deferred to supplementary materials that were not available for review. The resource itself, if made fully accessible and validated, would be of interest to a broad readership.

- **Who would be interested in the results, and why** Cell signaling researchers studying kinase-substrate specificity, particularly those focused on docking interactions and intrinsically disordered regions. Computational biologists developing or applying structure prediction tools for interactome-scale studies. Drosophila geneticists studying kinase function and lipid metabolism. Drug discovery scientists interested in allosteric kinase inhibition strategies. The resource aspect (the atlas and the iLIS framework) could serve as a reference for future studies.

- **Major strengths**
  1. The iLIS metric is a thoughtful response to a recognized problem in applying AlphaFold-Multimer to transient, flexible interfaces, and the benchmarking against curated datasets is appropriate.
  2. The scale of the effort (240,000+ human pairs, 210,000+ Drosophila pairs) is impressive and the resource is made publicly available.
  3. The discovery and validation of the Sgg–Hnf4 regulatory axis provides a concrete, physiologically relevant demonstration of the atlas's utility.
  4. The binding-defined kinase tree offers a novel organizational principle that complements sequence-based classifications.
  5. The experimental validations, while limited, are well-designed and directly test the computational predictions.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The authors claim that the iLIS framework "recapitulates hallmark sequence preferences" and "confirms previously reported and functionally related protein-protein interactions" at scale.
- **Evidence pointer** Figure 1C, 1D; Supplementary Figures 1A–M; benchmarking described in Supplementary Text Sections 4–5
- **Concern** The benchmarking results are presented as ROC AUC values, but the composition of the positive and control datasets is not described in the main text. The authors state the dataset includes "774 positive and 6,004 control PPIs" from Y2H and ELM sources, but the overlap between the benchmark set and the kinase–TF pairs in the atlas is unclear. If the benchmark set is enriched for stable, well-characterized interactions, the reported performance may not generalize to the transient, flexible interactions that are the focus of the atlas.
- **Why it matters** The central claim of the manuscript is that iLIS enables reliable identification of transient, flexible interactions that global metrics miss. If the benchmark does not adequately represent this class of interactions, the performance claims are not substantiated.
- **Resolution test** Provide a detailed breakdown of the benchmark dataset composition, including the proportion of interactions mediated by short linear motifs or intrinsically disordered regions. Report iLIS performance separately for structured versus flexible interfaces. If possible, validate a random sample of atlas predictions (not just top-scoring ones) using an orthogonal method.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability of conclusions
- **Claim pointer** The authors claim that the homeodomain docking motif is "potentially widespread" and represents a "conserved docking mechanism" across homeodomain transcription factors.
- **Evidence pointer** Figure 5A–G; Supplementary Figures 8–10; Supplementary Data 4
- **Concern** The identification of the composite motif [V/I]xxWFQNRRx[K/R]x[K/R][K/R] on the third α-helix of homeodomains is intriguing, but the evidence for its generality is limited. The in silico mutagenesis was performed on only two homeodomain proteins (Ftz and Gsb) against two kinases (aPKC and p38a). The claim of a "widespread" mechanism requires demonstration across a broader panel of homeodomain proteins and kinases. Additionally, the third α-helix is known to be critical for DNA binding, and the authors acknowledge this confounding factor but do not fully address whether the observed kinase interactions are compatible with DNA-bound states of these transcription factors.
- **Why it matters** The homeodomain docking motif is presented as a major discovery of the atlas. If the mechanism is not general or is an artifact of the prediction pipeline, the significance of this finding is substantially reduced.
- **Resolution test** Expand the experimental validation to include additional homeodomain proteins from different subfamilies and additional kinases from the basophilic and MAPK families. Test whether the docking motif is functional in the presence of DNA. Provide a systematic analysis of how many homeodomain proteins in the atlas contain the motif and how many show predicted interactions with basophilic kinases.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation depth
- **Claim pointer** The authors claim that the Sgg–Hnf4 interaction "controls lipid metabolism in vivo" and that Sgg stabilizes Hnf4 via phosphorylation at S253.
- **Evidence pointer** Figure 7A–L; Methods sections on Drosophila genetics, immunostaining, and phosphoproteomics
- **Concern** The in vivo validation demonstrates that sgg knockdown reduces Hnf4 protein levels and causes lipid accumulation, and that S253 phosphorylation is Sgg-dependent. However, the manuscript does not show that S253 phosphorylation is required for Hnf4 stability in vivo. The phosphoproteomics identified S253 as a site whose phosphorylation is reduced by LiCl treatment, but no phospho-dead or phospho-mimetic mutants were tested in vivo. The causal link between S253 phosphorylation and Hnf4 stability is therefore inferred but not directly demonstrated.
- **Why it matters** The Sgg–Hnf4 axis is the primary in vivo validation of the atlas's predictive power. Without demonstrating that S253 phosphorylation is functionally required for Hnf4 stability, the mechanistic claim is incomplete.
- **Resolution test** Generate transgenic flies expressing Hnf4 with S253A (phospho-dead) and S253D (phospho-mimetic) mutations and test whether these rescue the sgg knockdown phenotype. Alternatively, test whether S253A Hnf4 is destabilized in vivo.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Therapeutic claims
- **Claim pointer** The authors state that the atlas "provides a blueprint for the rational design of docking-site-specific kinase modulators" and that mapped allosteric hotspots are "potentially inhibitable."
- **Evidence pointer** Figure 6A–H; Supplementary Data 5
- **Concern** The proof-of-concept experiments for allosteric hotspot validation used overexpressed TF fragments in cultured cells. While the results are consistent with the predictions, they do not demonstrate that these sites can be targeted by drug-like molecules. The claim that the atlas provides a "blueprint" for drug design is premature without evidence that the identified surfaces are druggable (e.g., presence of small-molecule binding pockets, accessibility in the full-length protein context).
- **Why it matters** The therapeutic relevance of the atlas is a significant part of the claimed significance. Overstating this aspect could mislead readers about the current state of the work.
- **Resolution test** Soften the language regarding therapeutic applications, or provide additional evidence such as small-molecule docking studies, fragment screening, or demonstration that the identified hotspots are conserved in human disease-relevant kinases.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical validation of iLIS
- **Claim pointer** The authors claim that iLIS "demonstrated improved performance over existing global confidence metrics" and "maintained a high predictive accuracy" for disordered complexes.
- **Evidence pointer** Figure 1C, 1D; Supplementary Figure 1A–M
- **Concern** The reported improvement of iLIS over ipTM (AUC 0.872 vs 0.822) is modest. The authors note that iLIS is highly correlated with other local metrics (actifpTM and ipSAE) and the advantage is "modest but consistent." The specific conditions under which iLIS provides a meaningful advantage need to be more clearly delineated. Additionally, the time-split benchmark is described but the results are only shown in supplementary figures.
- **Why it matters** The novelty of the iLIS framework relative to existing local metrics is a key contribution. If the advantage is marginal, the case for adopting iLIS over existing tools is weakened.
- **Resolution test** Provide a more detailed comparison of iLIS versus actifpTM and ipSAE, including statistical significance testing. Clearly state the conditions under which iLIS outperforms these alternatives and when it does not.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** iLIS threshold selection
- **Evidence pointer** Methods section, AlphaFold-Multimer prediction; Supplementary Text Sections 1–3
- **Issue** The manuscript states that a high-confidence threshold of iLIS ≥ 0.223 was established at a 10% FDR, but the procedure for determining this threshold is only described in supplementary text. The main text should include a brief description of how the FDR was calculated.
- **Required correction** Add a sentence in the Methods section describing the FDR calculation procedure, or refer readers to the specific supplementary section with a one-line summary.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Benchmark comparisons
- **Evidence pointer** Figure 1C, 1D; Supplementary Figure 1
- **Issue** The ROC AUC values are reported without confidence intervals or statistical significance testing. Given the modest differences between iLIS and other metrics, it is important to know whether these differences are statistically meaningful.
- **Required correction** Report confidence intervals for AUC values and perform statistical comparison (e.g., DeLong test) between iLIS and other metrics.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** Figure 2
- **Evidence pointer** Figure 2A–E
- **Issue** The network visualizations in Figure 2 are described in the text but the figure itself is not provided in the submitted material. The hub-and-spoke architecture and clustering of kinase families are key results that should be visible to the reader.
- **Required correction** Ensure all main text figures are included in the submission. If there are size constraints, consider moving some panels to supplementary.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** "Docking landscapes"
- **Evidence pointer** Title, Abstract, Discussion
- **Issue** The term "docking landscapes" is used throughout but is not explicitly defined. It appears to refer to the map of interaction hotspots across kinase surfaces, but the reader must infer this.
- **Required correction** Define "docking landscape" at first use in the Introduction or Results.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Experimental replication
- **Affected element** In vitro phosphorylation assay
- **Evidence pointer** Methods, In vitro phosphorylation assays; Figure 5K
- **Issue** The in vitro phosphorylation assay is described as a single experiment. For a key validation result, it would be helpful to know the number of biological replicates and whether the result was reproducible.
- **Required correction** State the number of independent experiments performed and whether representative results are shown.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability completeness
- **Affected element** Supplementary data
- **Evidence pointer** Data Availability Statement
- **Issue** The authors state that supplementary data are deposited in Zenodo, but the specific files are not listed in the manuscript. It is unclear what each supplementary data file contains.
- **Required correction** Add a brief description of each supplementary data file in the Data Availability Statement or in a supplementary table.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Comparison to existing resources
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The manuscript does not compare the atlas to existing kinase–substrate interaction resources (e.g., PhosphoSitePlus, Kinase Library, or other structure-based interaction databases). Such a comparison would help position the resource within the field.
- **Required correction** Add a paragraph in the Discussion comparing the atlas to existing resources and highlighting unique contributions.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Language precision
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "structure-guided" in the title and abstract could be interpreted as implying experimental structure determination, whereas the work is based on predicted structures. Consider clarifying that the atlas is based on predicted structures.
- **Required correction** Consider revising to "structure-prediction-guided" or adding a clarifying phrase in the abstract.

- **Technical failings that need to be addressed before the case is established**
  1. The benchmark dataset composition and its relevance to the transient, flexible interactions that are the focus of the atlas must be described in detail (R1-M1).
  2. The generality of the homeodomain docking motif requires broader experimental validation (R1-M2).
  3. The causal link between S253 phosphorylation and Hnf4 stability in vivo must be demonstrated (R1-M3).
  4. Statistical significance of iLIS performance improvements over existing metrics should be reported (R1-m2).

- **Assessment against Nature-style criteria**
  - **Originality** High. The application of AlphaFold-Multimer at interactome scale with a new interface-aware scoring metric is a novel approach. The binding-defined kinase tree and the homeodomain docking motif discovery are original contributions.
  - **Scientific importance** Moderate to high. The resource has the potential to accelerate kinase–substrate interaction discovery, but the current validation is limited to a small number of cases. The physiological relevance is demonstrated for one axis (Sgg–Hnf4), which is encouraging but not yet comprehensive.
  - **Interdisciplinary readership** Moderate. The work bridges computational biology, signaling, and Drosophila genetics. The resource aspect could attract a broad audience, but the technical nature of the iLIS framework may limit accessibility.
  - **Technical soundness** Moderate. The computational approach is well-reasoned and benchmarked, but key details are deferred to supplementary materials. The experimental validations are appropriately designed but limited in scope. The lack of statistical rigor in some comparisons (e.g., AUC differences) is a concern.
  - **Readability for nonspecialists** Moderate. The manuscript is generally well-written, but the Methods section assumes familiarity with AlphaFold-Multimer and structure prediction. The significance of the findings could be better contextualized for a general audience.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a valuable resource and a promising computational framework. However, the current evidence does not fully support the breadth of the claims, particularly regarding the generality of the homeodomain docking motif and the therapeutic relevance of the allosteric hotspots. The authors should address the major concerns outlined above, particularly the benchmark composition, the expanded validation of the homeodomain motif, and the direct demonstration of S253 function in vivo. With these revisions, the manuscript would make a strong contribution to the field.

## Risk / unsupported claims
- The claim that the homeodomain docking motif is "potentially widespread" is not supported by the limited experimental validation (only two homeodomain proteins tested).
- The claim that the atlas "provides a blueprint for the rational design of docking-site-specific kinase modulators" is premature without evidence of druggability of the identified hotspots.
- The claim that iLIS "demonstrated improved performance" over existing metrics is based on modest AUC differences without statistical testing.
- The claim that the atlas "recapitulates hallmark sequence preferences" is supported only for a few kinase families shown in the main text; the full analysis is in supplementary materials not provided.
- The claim that Sgg stabilizes Hnf4 via S253 phosphorylation is inferred but not directly demonstrated with phospho-mutant experiments in vivo.
- The generalizability of the atlas to other organisms beyond human and Drosophila is not tested and should not be implied.