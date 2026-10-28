## Review setup
- **Input scope** Full manuscript text (abstract, results, discussion, methods) as provided
- **Assessment boundary** Statistical methodology, simulation design, biological interpretation, and claims as presented in the provided text
- **Shared manuscript claim summary** The authors propose a linear regression-based test for interactions between individual SNPs and a polygenic score (PGS) to detect gene-gene interactions in quantitative traits. They apply this to 97 phenotypes in the UK Biobank, identify 144 SNP×PGS interactions, refine these to 38 SNP×SNP interactions, and further partition PGSs by transcription factor binding sites to identify 12 TF-specific interactions. They claim this is the first rigorously tested pipeline for genome-wide SNP×PGS interaction analysis.
- **Visible evidence base** Abstract, full results section, discussion, methods (including simulation details), data/code availability statements
- **Missing materials affecting confidence** Supplementary tables (S1, S6, S7, S9, S10, S11, S12, S13, S14), supplementary figures (S3, S7, S8, S9), detailed supplementary methods, full simulation parameter details, exact p-value thresholds for all analyses, ancestry component specifications, and code

## Reviewer
- **Overall assessment** This manuscript presents a methodologically ambitious and potentially valuable approach to detecting gene-gene interactions in large-scale biobank data. The core idea of testing SNP×PGS interactions with careful controls for known confounders (LD, global epistasis, population structure) is sound and addresses important limitations of prior epistasis studies. The application to 97 traits in the UK Biobank is substantial, and the identification of 144 interactions is a notable result. However, several technical concerns need to be addressed before the case is fully established. The simulation framework, while extensive, has limitations in its coverage of realistic interaction architectures. The interpretation of the TF-partitioned PGS results requires more careful consideration of multiple testing and potential confounding. The comparison with prior work is somewhat cursory. Overall, this is a promising contribution that could be suitable for a high-impact journal if the technical concerns are adequately resolved.

- **Who would be interested in the results, and why** Statistical geneticists and computational biologists developing methods for epistasis detection would be the primary audience. Researchers studying the genetic architecture of complex traits, particularly those interested in non-additive effects, would also find this relevant. The findings on specific interactions (e.g., ABO-FUT2-TREH for ALP, IL33-ALOX15 for eosinophils) would interest investigators in those specific trait areas. The methodological framework for partitioning PGSs by TF binding sites could be of broader interest to those studying regulatory genomics.

- **Major strengths**
  1. The method addresses known pitfalls in epistasis detection (phantom epistasis, global epistasis) with principled corrections.
  2. The simulation framework is extensive, covering multiple dimensions of genetic architecture.
  3. The application to a large number of phenotypes in a well-powered sample is a significant undertaking.
  4. The identification of known and novel interactions, including the ABO-FUT2-TREH network, provides biological validation.
  5. The TF-partitioning approach is a novel and creative way to increase power and interpretability.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical methodology
- **Claim pointer** The claim that the method "avoids false positives" and is "well calibrated under the null" based on simulations.
- **Evidence pointer** Results section "Simulations", Figure 2b-c
- **Concern** The null simulations, while covering a range of architectures, may not adequately capture the complexity of real genetic data. Specifically, the simulations appear to assume a relatively simple additive genetic architecture with no population structure beyond what is captured by the Ancestry Components. Real data may contain cryptic relatedness, population substructure, and gene-environment correlations that could inflate false positive rates. The authors state that Ancestry Components are used, but the number of components and their adequacy in capturing structure is not specified. Furthermore, the simulations do not appear to include scenarios with gene-environment interactions, which the authors acknowledge their method is not designed to detect, but which could still confound results if present in real data.
- **Why it matters** If the false positive rate is not well-controlled in realistic scenarios, the 144 identified interactions could be substantially inflated, undermining the main conclusions of the paper.
- **Resolution test** The authors should provide additional simulations that include: (1) population structure beyond simple principal components (e.g., admixture or relatedness); (2) gene-environment interactions; (3) more complex interaction architectures (e.g., interactions with non-linear effects, or interactions involving multiple loci simultaneously). They should also report the genomic inflation factor (lambda) for their real data analyses to assess potential residual confounding.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical methodology
- **Claim pointer** The claim that the leave-one-chromosome-out (LOCO) PGS approach "prevents LD-driven false positives" and that the method is robust to "phantom epistasis".
- **Evidence pointer** Methods section "Leave-one-chromosome-out PGS to prevent LD-driven false positives"
- **Concern** The LOCO approach removes all SNPs on the same chromosome as the focal SNP from the PGS. While this prevents local LD from confounding the interaction test, it may also remove genuine interaction partners on the same chromosome, reducing power. More critically, the approach does not fully address the issue of long-range LD or LD with SNPs on other chromosomes that may be correlated due to population structure. The authors state that Ancestry Components are used to control for this, but the adequacy of this control is not demonstrated. Additionally, the iterative regression procedure for identifying independent hits may be sensitive to the order in which SNPs are considered, and its properties are not fully characterized.
- **Why it matters** If the LOCO approach does not fully control for LD-induced false positives, some of the reported interactions may be spurious. Conversely, if it over-corrects, genuine interactions may be missed, and the reported set may be incomplete.
- **Resolution test** The authors should provide a more detailed analysis of the LD structure around their identified interaction hits, demonstrating that they are not in LD with other variants that could explain the signal. They should also perform sensitivity analyses using different numbers of Ancestry Components and different LOCO strategies (e.g., removing only SNPs in LD with the focal SNP rather than the entire chromosome).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** The claim that identified interactions "reflect biological interdependencies between genes" and the specific interpretation of the TCF7L2-KDM2A interaction for HbA1c.
- **Evidence pointer** Results section "Interactions with partitioned PGSs", Discussion
- **Concern** The interpretation of the TF-partitioned PGS results is speculative. The authors identify an interaction between a TCF7L2 SNP and a PGS component defined by KDM2A binding sites, and interpret this in light of known functional interactions between these proteins. However, the statistical evidence for this specific interaction (p < 10^-5) is modest given the number of TF-PGSs tested. The authors do not report how many TF-PGSs were tested per SNP-trait pair, nor do they provide a clear multiple testing correction strategy beyond a Bonferroni threshold. Furthermore, the biological interpretation relies on the assumption that the TF binding site annotations are accurate and that the partitioning approach correctly identifies causal variants, which is a strong assumption.
- **Why it matters** If the TF-partitioned results are not robust to multiple testing or annotation errors, the specific biological interpretations may be overinterpreted, and the broader claim that these interactions reflect biological mechanisms would be weakened.
- **Resolution test** The authors should report the total number of TF-PGSs tested, the effective number of independent tests, and provide a more nuanced multiple testing correction. They should also perform sensitivity analyses using different TF binding site prediction methods and different thresholds for defining binding sites. For the TCF7L2-KDM2A interaction specifically, they should provide additional evidence, such as colocalization with eQTL data or functional validation in relevant cell types.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The claim that the method is a "rigorously tested pipeline" that can be applied to any quantitative trait.
- **Evidence pointer** Methods section, Code availability statement
- **Concern** The code and detailed methods are not currently available, only "upon request" and "upon publication." This limits the ability of other researchers to reproduce the results or apply the method to their own data. The methods section, while detailed, omits several key parameters (e.g., number of Ancestry Components, exact thresholds for LD pruning, details of the iterative regression procedure) that would be needed for replication.
- **Why it matters** Reproducibility is a core requirement for a methodological contribution. Without access to code and full methodological details, the claims cannot be independently verified, and the utility of the method for the broader community is limited.
- **Resolution test** The authors should make the code and a detailed step-by-step protocol available at the time of submission, either as supplementary material or in a public repository. They should also provide a complete list of all analysis parameters.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract states "Association studies have linked many genetic variants to a variety of phenotypes" which is somewhat vague. It would be clearer to specify the scale (e.g., "genome-wide association studies") and the type of variants (e.g., "common single-nucleotide polymorphisms").
- **Required correction** Revise to: "Genome-wide association studies have linked many common genetic variants to a wide range of phenotypes..."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section "SNP×PGS interactions"
- **Evidence pointer** Results, paragraph 2
- **Issue** The authors state "81 remain significant at a stricter threshold of 5 × 10−8/97" but do not explain the rationale for this threshold. It appears to be a Bonferroni correction for the number of traits, but this is not stated explicitly.
- **Required correction** Clarify the multiple testing correction strategy: "81 remain significant after Bonferroni correction for the number of traits tested (5 × 10−8/97)."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Biological interpretation
- **Affected element** Results section "SNP×SNP interactions"
- **Evidence pointer** Results, paragraph 4
- **Issue** The statement "distinct coding mutations in the same gene, APOE, are associated with interactions for different traits" is interesting but the authors do not elaborate on the potential mechanism or whether these are independent signals.
- **Required correction** Provide additional context or analysis on whether these APOE variants interact with different PGS components or affect different biological pathways.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph 1
- **Issue** The discussion of prior epistasis studies is brief and does not fully contextualize the novelty of the approach. The authors mention "marginal epistasis" and "variance effects" but do not discuss how their method relates to or improves upon these approaches in detail.
- **Required correction** Expand the discussion to more thoroughly compare and contrast the proposed method with existing approaches, highlighting specific advantages and limitations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 4
- **Evidence pointer** Results, paragraph 3
- **Issue** The description of Figure 4 mentions "lighter colours for subsets of related traits" but it is unclear how relatedness is defined and whether this is based on a formal clustering or simply visual inspection.
- **Required correction** Clarify the criteria for grouping traits in Figure 4 and whether the grouping is statistically motivated.

## Risk / unsupported claims
- The claim that the method "exhausts the additive signal" of the PGS is not fully supported; the iterative algorithm is described but its convergence and optimality properties are not formally demonstrated.
- The claim that the TF-partitioned PGS approach identifies "interactions involving functionally partitioned scores" that "directly reflect known regulatory relationships" is based on a small number of examples and requires more systematic validation.
- The statement that "the present study is the first to propose a rigorously tested pipeline for performing such analyses at scale" is a strong claim that is difficult to verify without a comprehensive literature review.
- The biological interpretation of the IL33-ALOX15 interaction for eosinophil levels relies on prior knowledge of these genes' roles in asthma, but the statistical evidence for this specific interaction is not presented in detail.
- The generalizability of the findings beyond the UK Biobank European-ancestry sample is not discussed; the authors should acknowledge potential limitations in applying this approach to other populations.