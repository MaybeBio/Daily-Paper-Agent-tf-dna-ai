## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results, discussion, and conclusions. Figures and supplementary materials referenced but not fully accessible.
- **Assessment boundary** Scientific validity of the computational workflow, experimental validation, and conclusions as presented in the provided text. No assessment of editorial fit or journal-specific policy compliance beyond scientific soundness.
- **Shared manuscript claim summary** The authors present an integrated machine learning and virtual screening workflow to identify natural product inhibitors of RORγt. They report that coptisine and berberine directly bind RORγt, inhibit Th17 cell differentiation and antigen-specific Th17 cell expansion, and that coptisine ameliorates imiquimod-induced psoriasis-like skin inflammation in mice.
- **Visible evidence base** Full methods and results text, figure legends, and supplementary file descriptions. Figures themselves, supplementary tables, and supplementary data files were not provided in the submitted material.
- **Missing materials affecting confidence** Figure images, Supplementary Tables S1 and S2, Supplementary Figures S1 through S6, and Supplementary Data Files 1 through 3 were not accessible. These are essential for evaluating the quality of the ML model performance, the docking poses, the molecular dynamics trajectories, and the histological and flow cytometry data.

## Reviewer
- **Overall assessment** The manuscript presents a potentially interesting application of machine learning to natural product discovery for RORγt inhibition. The integration of computational screening with in vitro, ex vivo, and in vivo validation is commendable. However, several technical concerns limit the strength of the conclusions as currently presented. The binding affinities reported are weak, the ML model validation is incomplete without access to the supplementary data, and the in vivo efficacy data require more rigorous quantitative analysis. The claim of direct RORγt binding by berberine as a novel finding is plausible but not fully established given the micromolar affinity and lack of a demonstrated functional link between binding and the observed cellular effects.
- **Who would be interested in the results, and why** Researchers in drug discovery, particularly those focused on nuclear receptor modulators, natural product screening, and computational approaches to immunology. The work may also interest investigators studying Th17-mediated autoimmune diseases such as psoriasis, as it identifies a potential lead compound with in vivo activity. The methodological framework combining ML, chemotaxonomy, and experimental validation could be of broader interest to the natural product drug discovery community.
- **Major strengths** The study integrates multiple computational and experimental approaches in a logical workflow. The use of a counter-screen to filter non-specific compounds is a thoughtful design element. The inclusion of SPR binding data, Th17-specific functional assays, and an in vivo disease model provides a multi-level validation strategy. The chemotaxonomic filtering step is a rational approach to prioritize natural product scaffolds.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (ML model validation), R1-M2 (binding affinity interpretation), R1-M3 (in vivo efficacy quantification), R1-M4 (selectivity evidence).
- **Assessment against Nature-style criteria** 
  - **Originality** Moderate. The application of ML to natural product screening is not new, and RORγt inhibitors are an active area of research. The specific finding that berberine directly binds RORγt may be novel, but the overall approach is incremental.
  - **Scientific importance** Moderate. Psoriasis is a significant disease, and new therapeutic leads are of interest. However, the weak binding affinities and the early-stage nature of the in vivo data limit the immediate translational significance.
  - **Interdisciplinary readership** The work spans computational chemistry, immunology, and pharmacology, which could attract a broad readership. However, the depth in each area is limited, and the manuscript may not fully satisfy specialists in any single discipline.
  - **Technical soundness** The computational methods are standard, but the validation is incomplete without access to supplementary data. The SPR and cellular assays are appropriate, but the interpretation of the binding data is problematic. The in vivo study design is reasonable but the quantitative analysis is insufficient.
  - **Readability for nonspecialists** The manuscript is generally well-written and accessible. The workflow is clearly described, and the figures are well-referenced in the text. However, some technical details in the ML and MD sections may be challenging for nonspecialist readers.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, but the technical concerns, particularly regarding the interpretation of binding affinity and the completeness of the ML model validation, must be resolved before the central claims can be accepted.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that their ML models demonstrate "consistently high predictive performance across datasets, supporting the model's generalization capability" based on external validation on BBBP, HIV, and BACE datasets.
- **Evidence pointer** Results section, "Development of Machine learning models for RORγt inhibitor discovery"; Supplementary Table S1
- **Concern** The external validation on BBBP, HIV, and BACE datasets is not a valid test of the model's ability to predict RORγt inhibition. These are generic molecular property benchmarks unrelated to RORγt biology. The model's performance on these datasets says nothing about its ability to generalize to RORγt-specific chemical space. The authors do not provide any external validation on an independent RORγt dataset, which would be the appropriate test.
- **Why it matters** The entire screening workflow depends on the reliability of the ML model. If the model's predictive performance is not properly validated on RORγt-relevant data, the prioritization of compounds for experimental testing is not justified. This undermines the foundation of the study.
- **Resolution test** Provide external validation on an independent RORγt inhibition dataset (e.g., a held-out set from a different source or a published RORγt dataset). Report precision, recall, and enrichment factors for the top-ranked compounds. If such a dataset is not available, acknowledge this limitation and temper the claims of model generalization.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of results
- **Claim pointer** The authors state that SPR "clearly showed that both Cop and Ber were directly bound to RORγt-ligand binding domain (LBD) with equilibrium dissociation constants (KD) of 59.7 and 108.1 μM, respectively."
- **Evidence pointer** Results section, "Surface plasmon resonance"; Figure 5A and 5B
- **Concern** The reported KD values are in the micromolar range, which is generally considered weak binding for a drug-like molecule. The authors interpret this as direct binding, but the functional relevance of such weak affinity is questionable. The cellular assays show inhibition of Th17 differentiation at concentrations that are not clearly related to the KD values. The manuscript does not address whether these concentrations are achievable in vivo or whether the observed cellular effects are actually mediated by RORγt binding.
- **Why it matters** The central claim of the paper is that these compounds are RORγt inhibitors. If the binding affinity is weak and the link between binding and functional outcome is not established, the claim is not supported. The in vivo efficacy could be due to off-target effects or other mechanisms.
- **Resolution test** Provide a clear dose-response relationship between RORγt binding and Th17 inhibition. Show that the concentrations used in cellular assays are consistent with the KD values and that the effects are RORγt-dependent (e.g., using RORγt-deficient cells or a selective control compound). Discuss the physiological relevance of micromolar binding affinity in the context of the in vivo model.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that coptisine "significantly ameliorates Th17/γδT17-driven skin inflammation in a mouse model of psoriasis."
- **Evidence pointer** Results section, "Coptisine treatment ameliorates the induction and progression of psoriasis-like skin inflammation"; Figure 6
- **Concern** The in vivo data are presented as changes in ear thickness and representative images, with flow cytometry data on cell numbers. However, the manuscript does not provide quantitative histological scoring, statistical details of the ear thickness measurements across all time points, or a clear description of the number of independent experiments and animals per group. The representative images in Figure 6C are not quantified. The claim of "significant" amelioration requires a more rigorous statistical analysis.
- **Why it matters** The in vivo efficacy is a key selling point of the paper. Without proper quantification and statistical rigor, the claim of therapeutic benefit is not fully supported. This is particularly important given the weak binding affinity of the compound.
- **Resolution test** Provide a full time-course of ear thickness measurements with statistical analysis (e.g., two-way ANOVA with post-hoc tests). Include a quantitative histological scoring system (e.g., epidermal thickness, inflammatory cell count) with blinded analysis. Report the number of animals per group and confirm that the experiments were repeated independently.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors suggest that coptisine and berberine are "selective inhibitors of Th17 differentiation and function" based on the lack of effect on Th1 differentiation.
- **Evidence pointer** Results section, "Inhibitory effects of protoberberine alkaloids on Th17 cell differentiation in vitro"; Supplementary Figure S3
- **Concern** The selectivity claim is based on a single experiment showing no effect on Th1 differentiation. This is insufficient to establish selectivity. The authors do not test other T helper subsets (e.g., Th2, Treg) or other immune cell types. The mechanism of selectivity is not addressed.
- **Why it matters** Selectivity is a critical property for a therapeutic candidate. If the compounds affect other immune pathways, the in vivo efficacy could be due to broader immunosuppression rather than specific RORγt inhibition. This would change the interpretation of the results.
- **Resolution test** Test the compounds' effects on other T helper subsets and innate immune cells. Provide a more comprehensive assessment of selectivity, including a panel of related nuclear receptors. If selectivity is not fully established, temper the claims accordingly.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** ML model training data
- **Evidence pointer** Materials and methods, "Data preparation"
- **Issue** The description of the data preparation states that compounds with activity scores between 40 and 100 were labeled as "active." The rationale for this threshold is not provided, and the sensitivity of the results to this cutoff is not explored.
- **Required correction** Justify the activity score threshold or provide a sensitivity analysis showing that the model performance is robust to reasonable variations in this cutoff.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Molecular dynamics section
- **Evidence pointer** Results section, "Molecular dynamics study"
- **Issue** The description of the molecular dynamics simulation is brief and lacks key parameters such as the force field used for the ligand, the simulation temperature and pressure, and the number of replicates. The statement about a "transition around 300 ns" is not clearly explained.
- **Required correction** Provide more detail on the MD simulation parameters and a clearer explanation of the observed transition and its significance for ligand binding stability.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Chemotaxonomic analysis
- **Evidence pointer** Results section, "Virtual screening of natural products and selection of protoberberine alkaloids"
- **Issue** The chemotaxonomic filtering step is described qualitatively. The authors state that they "manually investigated" the activity records and prioritized the protoberberine alkaloids, but the specific criteria for this prioritization are not fully transparent.
- **Required correction** Provide a more explicit description of the decision criteria used in the chemotaxonomic filtering, or present the data in a more systematic and reproducible manner.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Discussion of berberine
- **Evidence pointer** Discussion section
- **Issue** The authors note that berberine is a well-known natural product with diverse activities, but they do not discuss the existing literature on berberine and RORγt or Th17 in sufficient depth. This context is important for assessing the novelty of the finding.
- **Required correction** Expand the discussion to more thoroughly address prior work on berberine and Th17/RORγt, and clearly state what is new about the present findings.

## Risk / unsupported claims
- The claim that the ML model demonstrates "generalization capability" based on validation on BBBP, HIV, and BACE datasets is unsupported, as these datasets are not relevant to RORγt inhibition.
- The claim that coptisine and berberine are "selective inhibitors of Th17 differentiation" is not fully supported, as only Th1 differentiation was tested as a control.
- The claim that coptisine "significantly ameliorates" psoriasis-like skin inflammation is not fully supported without quantitative histological data and a complete statistical analysis.
- The statement that the molecular dynamics simulation shows a "transition" that is relevant to binding stability is not clearly explained and is difficult to evaluate without the supplementary figures.
- The novelty of berberine as a direct RORγt binder is not fully established, as the authors do not adequately discuss prior literature on this topic.