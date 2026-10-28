## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, supplementary materials description)
- **Assessment boundary** Scientific claims, methodology, evidence quality, and internal consistency as presented in the provided text
- **Shared manuscript claim summary** The authors identify ~4,000 human-specific de novo brain enhancers in embryonic neocortex using H3K27ac ChIP-seq data and a deep learning model, and propose that single-nucleotide mutations ("essential mutations") can create enhancer activity from neutral sequence, with target genes involved in neurodevelopment and associated with cognition and neurodevelopmental disorders
- **Visible evidence base** Abstract, introduction, results sections, methods descriptions, figure legends referenced in text, supplementary table references
- **Missing materials affecting confidence** Figures S1-S16, tables S1-S13, detailed model architecture hyperparameters, validation metrics beyond auROC/auPRC, exact statistical test outputs, VISTA enhancer validation details, Hi-C data processing details

## Reviewer
- **Overall assessment** This manuscript presents a compelling computational framework integrating comparative epigenomics with deep learning to identify putative de novo human brain enhancers and the single-nucleotide mutations that may underlie their emergence. The central hypothesis, that single-nucleotide mutations can create functional enhancers from neutral sequence, is biologically plausible and supported by multiple lines of convergent evidence including allelic imbalance, eQTL enrichment, GWAS trait association, and VISTA validation. However, the strength of the conclusions depends critically on the accuracy of the deep learning model at single-nucleotide resolution, and the evidence for this accuracy is not fully presented in the provided text. The evolutionary analyses, while suggestive, rely on assumptions about ancestral state reconstruction and selection that require careful scrutiny. The manuscript is well-written and the logical flow is clear, but several technical details and validations are referenced rather than shown, limiting full assessment.

- **Who would be interested in the results, and why** Evolutionary biologists studying regulatory innovation and human-specific traits; neurodevelopmental biologists interested in gene regulatory networks underlying cortical development; computational biologists developing and applying deep learning to regulatory genomics; geneticists studying the functional impact of noncoding variants in neurodevelopmental disorders such as autism spectrum disorder. The work bridges comparative genomics, machine learning, and neurodevelopment, making it relevant across these communities.

- **Major strengths** 1) The integration of comparative epigenomic data with deep learning predictions to distinguish de novo gains from losses is methodologically innovative. 2) The identification of "essential mutations" with single-nucleotide resolution provides a tractable framework for understanding how small genetic changes can create new regulatory elements. 3) The convergence of multiple independent evidence types (allelic imbalance, eQTLs, GWAS, VISTA) strengthens the claim that identified enhancers are functional. 4) The focus on progenitor cells and interneurons provides cell-type specificity that is biologically meaningful for cortical expansion. 5) The identification of specific transcription factors (POU3F2, ISL1, SOX family) whose binding sites are created by essential mutations provides mechanistic insight.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The deep learning model can accurately predict enhancer activity with single-nucleotide sensitivity, enabling identification of essential mutations.
- **Evidence pointer** Results section "Our pipeline identifies de novo enhancer gains and the underlying essential human mutations"; Methods section "A deep convolutional neural network model for enhancer prediction"; fig. S1
- **Concern** The manuscript claims the DLM can accurately estimate the functional effect of single-nucleotide mutations on enhancer activity, but the provided text does not include a detailed validation of the model at single-nucleotide resolution. The auROC (0.9-0.94) and auPRC (0.56-0.63) values are reported for enhancer classification, but these metrics do not directly demonstrate that the model can accurately predict the direction or magnitude of activity change caused by individual nucleotide substitutions. The model's sensitivity to single-nucleotide changes is the foundational assumption for identifying essential mutations, yet no direct validation (e.g., comparison to mutagenesis experiments, MPRA data, or known functional variants) is shown in the provided text.
- **Why it matters** If the model cannot reliably distinguish the effect of a single-nucleotide change on enhancer activity, then the identification of essential mutations and all downstream analyses (evolutionary, functional, disease association) are built on an unvalidated foundation. The entire premise of the paper depends on this single-nucleotide resolution accuracy.
- **Resolution test** Provide direct validation of the model's single-nucleotide sensitivity, such as: (i) comparison of model predictions to experimentally measured effects of individual mutations (e.g., from MPRA or STARR-seq), (ii) demonstration that known functional variants (e.g., from GWAS or disease studies) are correctly predicted to alter enhancer activity, or (iii) systematic benchmarking showing the model outperforms simpler approaches at single-nucleotide resolution.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The de novo gained enhancers are "created" by essential mutations, implying a causal relationship between specific nucleotide changes and enhancer emergence.
- **Evidence pointer** Results section "De novo enhancer gain may often be attributable to a single essential mutation"; fig. 4
- **Concern** The identification of essential mutations relies on a computational procedure that introduces human alleles into macaque sequence and scores the resulting activity change. However, the manuscript does not fully describe how the "minimal number of mutations needed to activate an enhancer" is determined, nor how the threshold for "essential" is set. The claim that ~40% of de novo gained enhancers contain at least one essential mutation is striking, but the false positive rate of this procedure is not assessed. If the model has any tendency to overpredict activity changes from single-nucleotide substitutions, the number of essential mutations could be substantially overestimated. Additionally, the validation using allelic imbalance (Fig. 4C) is based on a small number of heterozygous sites and may not be representative.
- **Why it matters** The central claim of the paper is that single-nucleotide mutations can create enhancers. If the computational identification of essential mutations is not rigorously validated and the false positive rate is not characterized, the prevalence of this phenomenon may be overstated, and the downstream evolutionary and disease associations may be spurious.
- **Resolution test** Provide a clear description of the essential mutation identification algorithm, including thresholds and criteria. Assess the false positive rate using negative controls (e.g., mutations in conserved enhancers that should not create activity, or permutations of essential mutations). Increase the sample size for allelic imbalance validation and demonstrate that the effect is specific to essential mutations rather than a general property of mutations in gained enhancers.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** Essential mutations exhibit relaxed negative selection or potential positive selection, and are enriched for CNS-related GWAS traits and ASD-associated de novo mutations.
- **Evidence pointer** Results section "Essential mutations are associated with cognition and neurodevelopmental disorders"; fig. 5A; tables S7 and S8
- **Concern** The evolutionary and disease association analyses are based on small numbers of essential mutations (the text mentions 7 of 28 GWAS traits overlapping essential mutations, and specific examples for NBEA, CD40). The DoS test results (Fig. 4D) are described but the statistical significance and effect sizes are not reported in the provided text. The enrichment of ASD de novo mutations in essential mutation sites (Fig. 6G-H) is potentially interesting, but the background model for this enrichment is not described. The manuscript would benefit from a more rigorous statistical framework for these enrichment analyses, including appropriate multiple testing corrections.
- **Why it matters** The claim that essential mutations are relevant to human cognition and neurodevelopmental disorders is a key translational aspect of the paper. If the statistical support is weak or the analyses are underpowered, this claim is not established, and the broader significance of the work is diminished.
- **Resolution test** Report effect sizes, confidence intervals, and p-values for all enrichment analyses. Describe the null model used for ASD mutation enrichment. Consider whether the number of essential mutations is sufficient to support the claims, or whether the analyses should be framed as suggestive rather than definitive.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** De novo gained enhancers are more likely to be functional in the developing human brain compared to HGEs, based on VISTA enhancer validation.
- **Evidence pointer** Results section "De novo gained enhancers exhibit weaker enhancer activity but are more likely to be functional in the developing human brain compared to HGEs"; fig. 7C
- **Concern** The comparison with HGEs is a key differentiator of this work, but the VISTA validation is based on a small number of enhancers (the text mentions three examples in Fig. 7D). The claim that 57% of de novo enhancers are active in the developing brain compared to 15% of HGEs is based on an unspecified number of VISTA-tested enhancers. If the sample size is small, the confidence intervals on these proportions will be wide, and the difference may not be statistically robust. Additionally, the VISTA database is biased toward enhancers with detectable activity, which could affect the comparison.
- **Why it matters** The claim that de novo enhancers are more likely to be functional than HGEs is important for establishing the biological relevance of the identified enhancers. If this is based on a small sample, the conclusion is not robust.
- **Resolution test** Report the number of VISTA-tested enhancers in each category, the statistical test used to compare proportions, and confidence intervals. If the sample size is small, consider whether additional experimental validation is needed or whether the claim should be tempered.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction
- **Evidence pointer** Introduction, first paragraph
- **Issue** The introduction assumes familiarity with neocortical development terminology (e.g., "progenitor cells," "interneurons," "gliogenesis") without brief definitions. For a broad readership, a sentence providing context on cortical development would improve accessibility.
- **Required correction** Add a brief description of cortical development and the cell types involved, or provide a glossary of key terms.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, deep learning model
- **Evidence pointer** Methods section "A deep convolutional neural network model for enhancer prediction"
- **Issue** The model architecture is described in terms of layer counts and kernel numbers, but key hyperparameters (learning rate, batch size, dropout, activation functions, training epochs, early stopping criteria) are not reported. This limits reproducibility.
- **Required correction** Provide full hyperparameter details, or reference a public code repository where the model is implemented.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, enhancer gain/loss identification
- **Evidence pointer** Methods section "Gain and loss of enhancers"
- **Issue** The criteria for classifying an enhancer as "de novo gained" or "lost" are described qualitatively (high/low DLM score, H3K27ac detection). The specific score thresholds and statistical criteria are not provided.
- **Required correction** Report the exact thresholds used for DLM scores and H3K27ac detection, and describe how these thresholds were chosen.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, allelic imbalance analysis
- **Evidence pointer** Results section "De novo enhancer gain may often be attributable to a single essential mutation"; fig. 4C
- **Issue** The allelic imbalance analysis is described as supporting the functional impact of essential mutations, but the number of heterozygous sites analyzed and the statistical power are not reported.
- **Required correction** Report the number of sites analyzed, the distribution of read counts, and the effect size of the allelic imbalance.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Discussion
- **Evidence pointer** Discussion, first paragraph
- **Issue** The discussion of "relaxed negative selection" and "positive selection" assumes familiarity with population genetics concepts. A brief explanation of these terms and their implications would help readers from other disciplines.
- **Required correction** Add a sentence explaining the meaning and significance of relaxed negative selection and positive selection in this context.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, DoS test
- **Evidence pointer** Methods section "DoS test"
- **Issue** The DoS test is described but the interpretation of the results is not fully explained. The text states that essential mutations have the highest DoS values, but does not clarify what range of DoS values would indicate relaxed negative selection versus positive selection.
- **Required correction** Provide a brief interpretation guide for DoS values, and report the actual DoS values and confidence intervals for each mutation class.

## Risk / unsupported claims
- The claim that the DLM can accurately predict single-nucleotide effects on enhancer activity is not directly validated in the provided text; this is the foundational assumption of the paper and requires explicit demonstration.
- The claim that ~40% of de novo gained enhancers contain at least one essential mutation depends on the unvalidated single-nucleotide sensitivity of the DLM and the specific algorithm for identifying essential mutations, which is not fully described.
- The evolutionary claims (relaxed negative selection, potential positive selection) are based on DoS tests whose results are not fully reported; the statistical support is unclear.
- The enrichment of essential mutations for CNS-related GWAS traits is based on a small number of overlapping traits (7 of 28) and requires assessment of whether this is significantly different from expectation given the genomic background.
- The claim that de novo enhancers are more likely to be functional than HGEs is based on VISTA validation, but the sample size and statistical test are not reported.
- The specific examples (NBEA, CD40) are presented as case studies, but the causal link between the identified essential mutations and gene expression changes is inferred from correlation and model predictions, not experimentally demonstrated.
- The claim that de novo enhancers are "created" by single-nucleotide mutations implies a causal relationship that is not directly tested; the analysis is correlational and model-based.