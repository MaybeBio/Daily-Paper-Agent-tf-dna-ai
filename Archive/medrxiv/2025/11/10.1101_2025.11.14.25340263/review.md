## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The authors propose a statistical test for interactions between single SNPs and polygenic scores (PGS) for quantitative traits, apply it to 97 phenotypes in the UK Biobank, report 144 independent interactions across 52 traits, refine signals to detect 38 pairwise SNP-SNP interactions, and further partition PGSs by transcription factor binding sites to identify 12 additional interactions. They argue these results substantially extend known epistatic effects and reflect biological interdependencies.
- **Visible evidence base** Abstract text only; no simulation details, effect size estimates, confidence intervals, replication analyses, or functional validation are provided
- **Missing materials affecting confidence** Full methods, simulation parameters, complete results tables, figures, quality control procedures, multiple testing correction details, population stratification controls, and any sensitivity analyses

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable statistical framework for detecting SNP-by-polygenic background interactions and reports a large number of novel epistatic signals in the UK Biobank. The biological plausibility of several highlighted examples, such as the ABO-FUT2-TREH network and the IL33-ALOX15 interaction, is compelling. However, the abstract alone does not provide sufficient methodological detail to assess the validity of the test, the robustness of the findings, or the adequacy of multiple testing controls. The claim of substantially extending known epistatic effects is plausible but cannot be verified from the supplied material. The work is likely to interest genetic epidemiologists and statistical geneticists, but the current evidence base is insufficient to establish the case.
- **Who would be interested in the results, and why** Statistical geneticists developing interaction tests, genetic epidemiologists studying epistasis in large biobanks, and researchers investigating the genetic architecture of complex traits. The transcription factor partitioning approach may also appeal to regulatory genomics researchers. The specific interactions involving well-known loci such as APOE, FTO, and TCF7L2 could attract broad biomedical audiences.
- **Major strengths** The proposed test addresses a real gap in the field by targeting interactions between individual variants and polygenic background, which is a computationally tractable and biologically motivated approach. The application to 97 phenotypes in the UK Biobank is large scale. The inclusion of known interactions as positive controls, such as ABO-FUT2-TREH, lends some credibility. The transcription factor partitioning strategy is novel and could provide mechanistic insight.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not describe the statistical model, the null distribution, or the multiple testing correction approach. Without these, the reported number of interactions cannot be evaluated for false positive risk. The simulation claims of avoiding false positives and being well powered are not supported by any quantitative details. The refinement from 144 interactions to 38 pairwise SNP-SNP interactions is not explained. The transcription factor partitioning method is described only superficially.
- **Assessment against Nature-style criteria** Originality is high, as the combination of SNP-by-PGS interaction testing with transcription factor partitioning appears novel. Scientific importance is potentially high given the scale of the UK Biobank application and the biological relevance of the highlighted loci. Interdisciplinary readership is plausible, spanning statistical genetics, functional genomics, and disease biology. Technical soundness cannot be assessed from the abstract alone, which is a critical limitation. Readability for nonspecialists is adequate, though some terms such as PGS and HOCOMOCO are used without definition.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising and the approach is of interest, but the lack of methodological detail and quantitative results prevents a supportive recommendation. A full manuscript with methods, simulations, and results would be required to evaluate the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validity
- **Claim pointer** The test "avoids false positives and is well powered to find interaction networks" in realistic simulations.
- **Evidence pointer** Abstract, simulation description; location not provided
- **Concern** The abstract states that the test avoids false positives and is well powered, but provides no details on the simulation design, the null model, the number of simulations, the effect sizes tested, or the false positive rate and power estimates. Without these, the claim is unverifiable.
- **Why it matters** The entire set of reported interactions depends on the validity of the test. If the test has inflated type I error, many of the 144 interactions could be false positives. The abstract provides no basis to assess this.
- **Resolution test** Provide full simulation methods, including the generative model, the range of parameters tested, and quantitative false positive rates and power curves. Show that the test is calibrated under realistic LD and population structure conditions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Multiple testing and reproducibility
- **Claim pointer** "We identify 144 independent interactions affecting 52 different traits."
- **Evidence pointer** Abstract, results description; location not provided
- **Concern** The abstract does not describe how multiple testing was controlled across 97 phenotypes and a large number of SNP-by-PGS tests. The threshold for significance, the method for defining independence among interactions, and any replication or sensitivity analyses are not stated.
- **Why it matters** With a large search space, the number of reported interactions is highly sensitive to the significance threshold and the correction method. Without this information, the reported count cannot be interpreted, and the risk of false discoveries is unknown.
- **Resolution test** Specify the multiple testing correction procedure, the significance threshold, and the criteria for independence. Provide replication in a holdout sample or sensitivity analyses to demonstrate robustness.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** "We develop approaches to refine identified signals and detect 38 pairwise interactions between SNPs."
- **Evidence pointer** Abstract, refinement description; location not provided
- **Concern** The refinement process from 144 SNP-by-PGS interactions to 38 pairwise SNP-SNP interactions is not described. It is unclear whether the 38 are a subset of the 144, whether they are newly discovered, or how the refinement avoids circularity.
- **Why it matters** The pairwise interactions are presented as a key result, but the logic of the refinement is opaque. If the refinement uses the same data to select and test interactions, the reported pairwise effects may be overfitted.
- **Resolution test** Describe the refinement algorithm in detail, including how candidate SNPs are selected, how the pairwise tests are performed, and how overfitting is avoided. Provide validation of the 38 pairwise interactions in independent data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Biological interpretation
- **Claim pointer** "We identify 12 interactions affecting eight traits, two of which directly reflect known regulatory relationships such as that between TCF7L2 and KDM2A."
- **Evidence pointer** Abstract, transcription factor partitioning results; location not provided
- **Concern** The abstract claims that the transcription factor partitioning approach identifies interactions that reflect known regulatory relationships, but the statistical evidence for these 12 interactions is not presented. The link between the partitioned PGS and the biological mechanism is asserted rather than demonstrated.
- **Why it matters** The claim that statistical interactions reflect biological interdependencies is a central message of the paper. Without quantitative evidence for the 12 interactions and a clear explanation of how the partitioning works, this claim is not supported.
- **Resolution test** Provide effect sizes, confidence intervals, and p-values for the 12 interactions. Show that the transcription factor partitioning is biologically meaningful, for example by demonstrating enrichment of known regulatory targets or by validating in independent datasets.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Definition of PGS
- **Evidence pointer** Abstract, first paragraph; location not provided
- **Issue** The term "polygenic score" is used without specifying how it was constructed, such as which variants, weights, or LD clumping procedures were used.
- **Required correction** Define the PGS construction in the abstract or refer to the methods section with a brief description.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Population description
- **Evidence pointer** Abstract, application description; location not provided
- **Issue** The abstract states "European samples in the UK Biobank" but does not specify the sample size, the number of SNPs tested, or the quality control filters applied.
- **Required correction** Include the sample size and the number of variants analyzed, or state that these are provided in the methods.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Use of "epistatic effects"
- **Evidence pointer** Abstract, final sentence; location not provided
- **Issue** The term "epistatic effects" is used broadly, but the statistical interactions detected may not correspond to biological epistasis in the classical sense. This distinction is not addressed.
- **Required correction** Clarify the definition of epistasis used in the paper and acknowledge the limitations of statistical interaction as a proxy for biological interaction.

## Risk / unsupported claims
- The claim that the test "avoids false positives and is well powered" is unsupported without simulation details.
- The claim of "144 independent interactions affecting 52 different traits" is unverifiable without significance thresholds and multiple testing correction.
- The claim that the 38 pairwise interactions are "refined" from the 144 is not explained and may be overfitted.
- The claim that the 12 transcription factor partitioning interactions "directly reflect known regulatory relationships" is not supported by quantitative evidence.
- The general claim that "statistical interactions can reflect biological interdependencies between genes" is plausible but not established from the abstract alone.