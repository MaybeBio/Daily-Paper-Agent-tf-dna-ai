## Review setup
- **Input scope** Full manuscript text (abstract, main text sections, methods) as provided
- **Assessment boundary** Scientific content, methodology, statistical approach, interpretation, and reporting quality based solely on the supplied material
- **Shared manuscript claim summary** The authors report identification of 535 two-point (bQTL-fQTL) and 185 three-point (bQTL-fQTL-sex) epistatic interactions involving 9 nuclear hormone receptors across 768 UK Biobank traits at FDR < 0.05, using a targeted machine learning approach (TarGene). They report replication of ~32% of two-point interactions across different trans-acting variants, and propose plausible molecular mechanisms via transcription factor binding alterations.
- **Visible evidence base** Abstract, main text sections (Replicated 2-point interactions, Epistasis yields plausible biological mechanisms, Replicated sex-differential interactions, Discussion), Methods (definitions, QTL curation, TarGene description), figure references (Figs. 2-4, S1-S7), table references (Tables 1-3, S1-S6)
- **Missing materials affecting confidence** Figures and tables referenced but not provided; Supplementary Materials (including analytical power derivations) not provided; full statistical details of FDR control procedure not provided; complete results tables not available for independent verification

## Reviewer
- **Overall assessment** This manuscript addresses an important and long-standing question in human genetics: whether epistatic interactions contribute meaningfully to complex trait variation. The authors combine a biologically motivated targeting strategy (transcription factor binding QTLs) with a semi-parametric estimation framework (TarGene) to reduce the multiple testing burden that has hampered genome-wide epistasis scans. The approach is innovative and the results, if robust, would represent a significant advance. However, the manuscript as presented has several critical gaps that prevent full evaluation: the key figures and tables are not available, the replication claim requires closer scrutiny, and the biological interpretation sections, while plausible, need more rigorous support. The statistical framework is well-described conceptually but lacks sufficient detail on practical implementation and validation. The writing is generally clear but some sections are dense and would benefit from improved accessibility for a broad readership.

- **Who would be interested in the results, and why** Statistical geneticists and computational biologists developing methods for interaction detection would be interested in the TarGene framework and its application. Human geneticists studying complex trait architecture, particularly those focused on regulatory variation and transcription factor biology, would find the identified interactions and their potential mechanisms relevant. Researchers working on sex differences in disease susceptibility would be interested in the three-point interactions involving sex. The findings could also be relevant to those studying specific traits highlighted (bone disorders, gall bladder disease, sleep disorders, viral disease susceptibility) and to researchers interested in the evolutionary dynamics of transcription factor binding sites.

- **Major strengths**
  1. The biological targeting strategy is well-motivated and represents a thoughtful approach to the statistical power problem in epistasis detection.
  2. The use of model-independent definitions of ATE and AIE is conceptually sound and avoids parametric assumptions that may not hold for complex traits.
  3. The integration of multiple data types (bQTLs, eQTLs, hQTLs, globQTLs) to define facilitator sets is comprehensive.
  4. The replication of interactions across different trans-acting variants for the same bQTL-trait pair is an interesting and potentially powerful validation strategy.
  5. The identification of sex-specific epistatic interactions addresses an understudied aspect of genetic architecture.
  6. The authors are appropriately cautious about the need for independent replication and acknowledge limitations of their approach.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validity and reproducibility
- **Claim pointer** The authors claim identification of 535 significant two-point interactions and 185 three-point interactions at FDR < 0.05 per trait.
- **Evidence pointer** Methods "Epistasis estimation with TarGene"; Results sections; Tables S3 and S5 (not provided)
- **Concern** The manuscript does not provide sufficient detail on the multiple testing correction procedure. The authors state "FDRH < 0.05" but do not specify the exact method (e.g., Benjamini-Hochberg, Storey q-value), how the false discovery rate is estimated across the large number of tests performed (number of bQTL-fQTL pairs × 768 traits), or whether the procedure accounts for the correlation structure among tests. Given the scale of testing (9 NHRs, multiple bQTLs and fQTLs each, 768 traits), the potential for inflated false discovery rates is substantial. The authors reference their prior work for details, but for a standalone manuscript, this information is essential.
- **Why it matters** Without a clear and defensible multiple testing procedure, the reported number of significant interactions cannot be evaluated for credibility. The central claim of the paper depends entirely on the validity of these significance calls.
- **Resolution test** Provide a detailed description of the FDR control procedure, including the total number of tests performed, the method used, and any adjustments for correlation. Ideally, include a permutation-based or simulation-based calibration demonstrating the FDR is controlled at the claimed level.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Replication validity
- **Claim pointer** The authors claim that 173 of 535 (32.3%) two-point interactions replicated, defined as involving the same bQTL-trait pair but different fQTLs.
- **Evidence pointer** Results "Replicated 2-point interactions for the progesterone receptor"; Table 2 (not provided)
- **Concern** The replication definition is unusual. Typically, replication requires independent confirmation of the same variant-variant interaction in a different sample or dataset. Here, the authors define replication as the same bQTL interacting with different fQTLs for the same trait. This is not replication in the conventional sense; it is evidence of consistency across different trans-acting variants. While this is interesting, it does not address whether the original interaction would replicate in an independent cohort. The authors acknowledge this in the Discussion ("confidence in these interaction results would increase if they were successfully replicated in an independent data set"), but the use of the term "replicated" in the Results is misleading.
- **Why it matters** The replication claim is a key selling point of the paper. If the definition of replication is non-standard, readers may overestimate the robustness of the findings. The distinction between "replication" and "consistency across trans-acting variants" is important for accurate interpretation.
- **Resolution test** Either (a) provide true replication in an independent dataset, or (b) clearly re-label the finding as "consistency across trans-acting variants" and adjust the language throughout the manuscript to avoid implying independent replication.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation and causal inference
- **Claim pointer** The authors state that "Epistasis causes an individual's genetic background to modulate a DNA variant's effect on trait" and interpret their findings as evidence of "plausible molecular mechanisms of action."
- **Evidence pointer** Abstract; Results "Epistasis yields plausible biological mechanisms"; Discussion
- **Concern** The leap from statistical epistasis to biological mechanism is substantial. The authors identify bQTL-fQTL interactions where the bQTL alters transcription factor binding and the fQTL alters transcription factor abundance. However, the causal chain from altered binding to altered gene expression to altered trait is not directly tested. The authors note that some bQTLs are also eQTLs for nearby genes, but this is correlational evidence. The claim of "plausible molecular mechanisms" is reasonable as a hypothesis-generating statement, but the manuscript sometimes presents this as more established than it is. For example, the statement about ANXA2's role in bone mineralization contributing "epistatically through hormone-modulated altered AR binding" is speculative.
- **Why it matters** The biological interpretation is a major part of the paper's appeal. Overstating the mechanistic evidence could mislead readers and undermine the credibility of the work. The distinction between statistical interaction and biological interaction is critical.
- **Resolution test** Soften the language to clearly indicate that the proposed mechanisms are hypotheses. Consider adding functional validation experiments (e.g., reporter assays, CRISPR perturbation) or at minimum, clearly state that such validation is needed. Alternatively, present the mechanistic interpretations as speculative and clearly separated from the statistical findings.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and population specificity
- **Claim pointer** The authors state their results are "consistent with widespread epistatic interactions in humans."
- **Evidence pointer** Discussion
- **Concern** The analysis is restricted to the self-reported "White British" population in UK Biobank. This is a reasonable choice for reducing population stratification, but it limits generalizability. The authors do not discuss how their findings might differ in other ancestral groups, nor do they address the potential for population-specific epistatic interactions. Given known differences in linkage disequilibrium patterns and allele frequencies across populations, the specific interactions identified may not generalize.
- **Why it matters** If the goal is to understand the role of epistasis in human traits broadly, the restriction to a single population is a limitation that should be explicitly acknowledged and discussed. The claim of "widespread epistatic interactions in humans" is too broad given the population-specific analysis.
- **Resolution test** Acknowledge this limitation explicitly in the Discussion. If possible, perform a sensitivity analysis in a non-European population (e.g., UK Biobank African or South Asian subsets) to assess generalizability, or clearly state that such analysis is needed.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Methodological validation
- **Claim pointer** The authors claim TarGene provides "maximal power and minimal bias" and has "mathematical guarantees of desirable statistical properties."
- **Evidence pointer** Methods "Epistasis estimation with TarGene"
- **Concern** While the conceptual framework is sound, the manuscript does not provide sufficient validation of the method in the context of this specific application. The authors reference prior work for details, but the performance of TarGene for detecting epistatic interactions at this scale (768 traits, many variant pairs) is not demonstrated. Key questions include: How does the method perform under realistic genetic architectures with small effect sizes? What is the power to detect interactions of the magnitude expected for complex traits? How does the method compare to alternative approaches (e.g., interaction testing in linear mixed models) in terms of false positive control and power?
- **Why it matters** The credibility of the findings depends on the reliability of the method. Without validation in this specific context, it is difficult to assess whether the reported interactions are genuine or artifacts of the estimation procedure.
- **Resolution test** Provide simulation studies calibrated to the specific analysis performed (e.g., using realistic effect sizes, allele frequencies, and sample sizes) demonstrating the method's power and false positive control. Alternatively, provide a comparison with a more standard approach on a subset of the data.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of definitions
- **Affected element** Methods "Model-independent definition of ATE and AIE"
- **Evidence pointer** Methods section
- **Issue** The notation for genotypes (e.g., "bb", "bB", "BB") is introduced without explicit definition. It is implied that these refer to the number of effect alleles at the bQTL and fQTL, but this should be stated explicitly. Additionally, the use of "b" and "f" for the two loci is not immediately intuitive.
- **Required correction** Define the genotype notation clearly at first use. For example, state that for a biallelic variant, "b" denotes the non-effect allele and "B" the effect allele, and similarly for "f" and "F". Consider using a more standard notation (e.g., 0/1/2) for clarity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** Figures 2-4
- **Evidence pointer** Results sections referencing Figures 2-4
- **Issue** The figures are referenced extensively but not provided. Based on the text, they appear to be complex multi-panel figures. Without seeing them, it is difficult to assess whether they effectively communicate the key findings.
- **Required correction** Ensure figures are self-contained and clearly labeled. Consider adding a schematic diagram in Figure 1 that explains the overall study design and the interpretation of two-point and three-point interactions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reporting of effect sizes
- **Affected element** Results sections
- **Evidence pointer** Results "Replicated 2-point interactions for the progesterone receptor"
- **Issue** The manuscript reports p-values for specific interactions but does not consistently report effect sizes or confidence intervals. For example, the interaction for 'fracture head & neck' is described with a p-value but no measure of the magnitude of the interaction effect.
- **Required correction** Report effect sizes (e.g., AIE estimates) with confidence intervals for all significant interactions, at least in the supplementary tables. This is essential for assessing the biological relevance of the findings.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The Discussion acknowledges the need for replication but does not address other important limitations, such as the potential for residual population stratification despite restricting to White British individuals, the use of self-reported traits (which may have measurement error), and the fact that the analysis is cross-sectional and cannot establish causality.
- **Required correction** Add a more comprehensive limitations paragraph that addresses these issues and their potential impact on the findings.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Software availability
- **Affected element** Methods "Epistasis estimation with TarGene"
- **Evidence pointer** Methods section
- **Issue** The manuscript mentions TarGene software but does not provide a URL or citation for the software. This makes it difficult for readers to access and use the method.
- **Required correction** Provide a URL or citation for the TarGene software, and ideally a link to the code repository.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Consistency of terminology
- **Affected element** Throughout
- **Evidence pointer** Abstract, Results, Discussion
- **Issue** The terms "two-point interaction" and "three-point interaction" are used, but "three-point" is used for both bQTL-fQTL-sex and bQTL-fQTL-fQTL interactions. This could be confusing. Consider using more specific terms (e.g., "sex-modulated interaction" vs. "three-locus interaction").
- **Required correction** Clarify terminology to distinguish between the two types of three-point interactions.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Evolutionary interpretation
- **Affected element** Results "Replicated 2-point interactions for the progesterone receptor"
- **Evidence pointer** Results section
- **Issue** The statement that the bQTL's derived allele is "the stronger binding allele" and is present in Neanderthals but not in other apes is interesting but underdeveloped. The evolutionary implications are not discussed.
- **Required correction** Either expand on the evolutionary interpretation or remove this observation as it is not central to the main findings.

## Risk / unsupported claims
1. The claim of "widespread epistatic interactions in humans" is not supported by the data, which is limited to 9 NHRs and a single population. This is an overgeneralization.
2. The claim that TarGene provides "maximal power" is not substantiated with comparative analyses or simulations in this specific context.
3. The biological mechanism claims (e.g., ANXA2 in bone mineralization, miRNA regulation of viral replication) are speculative and not directly tested.
4. The replication claim (32.3%) uses a non-standard definition and should not be interpreted as independent replication.
5. The statement that "nearly a third of 2-point interactions replicated" could be misleading without the caveat that this is replication across different trans-acting variants, not independent sample replication.
6. The claim that "these epistatic mechanisms of altered transcription factor binding provide both plausible molecular mechanisms of action, and insight into sex-biased genetic risk" is an interpretation that goes beyond the statistical evidence presented.
7. The manuscript does not provide effect sizes or confidence intervals for the reported interactions, making it impossible to assess their biological significance.
8. The FDR control procedure is not described in sufficient detail to evaluate the validity of the significance calls.
9. The generalizability of findings to non-European populations is not addressed.
10. The manuscript does not discuss the potential for false positives due to the large number of tests performed, beyond the brief mention of FDR control.