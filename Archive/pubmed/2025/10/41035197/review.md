## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends, tables)
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, benchmarking rigor, reproducibility, and suitability for the stated claims of ab initio discovery and cross-species generalization
- **Shared manuscript claim summary** The authors present PTF-Vāc, a deep co-learning encoder–decoder system that integrates Transformer-based sequence processing with DenseNet-based protein structure processing to generate transcription factor binding site (TFBS) motifs ab initio, without requiring predefined position weight matrices (PWMs) or species-specific models. The system is claimed to outperform existing tools across multiple benchmarks, handle single-sequence inputs, generalize across species, distinguish splice-variant binding preferences, and enable genome-scale TFBS discovery.
- **Visible evidence base** Abstract; full introduction; results sections on ablation, structural contribution, benchmarking against deepRAM, DESSO, TF-MoDISco, and SeqConv; motif enrichment analyses; molecular docking validation; splice-variant analysis for ARF8; genome-scale application in tea (Camellia sinensis); methods sections on dataset retrieval, Transformer–DenseNet architecture, and Grad-CAM implementation; Figure 1–4 and Table 1–2 descriptions; supplemental table descriptions
- **Missing materials affecting confidence** Actual figures and figure panels (only legends provided); supplemental tables (all data referenced as "Supplemental Table 1, sheets 1–7" and "Supplemental Table 2, sheets 1–5" without content); exact hyperparameter values for the final model; training curves or convergence diagnostics; statistical test details beyond p-value statements; code repository contents; detailed dataset composition beyond "48,000 instances for 40 TFs"; comparison of computational cost; full results for all 36 TFs in benchmarking

## Reviewer

- **Overall assessment** The manuscript addresses a genuinely important problem in plant genomics: the high cross-species variability of TFBSs renders traditional PWM-based approaches inadequate, and the authors propose a fundamentally different architecture that jointly learns from sequence context and protein structure. The core idea of coupling a Transformer encoder–decoder for sequence-to-sequence translation with a DenseNet for structural feature extraction is creative and well-motivated. However, the evidence presented in the manuscript text is insufficient to fully substantiate the strong claims made. Key concerns include the absence of actual data tables and figures, unclear benchmarking protocols, potential circularity in the validation approach, and insufficient detail on how the model avoids learning trivial or degenerate solutions. The splice-variant and genome-scale demonstrations are compelling in concept but require more rigorous quantitative support. The manuscript is likely to be of interest to computational biologists and plant molecular biologists, but the current evidence base does not fully establish the claimed advantages.

- **Who would be interested in the results, and why** Computational biologists working on regulatory genomics and TF–DNA interaction prediction would be interested in the architectural innovation of co-learning sequence and structure in a generative framework. Plant molecular biologists studying transcriptional regulation, particularly in non-model species, would be interested in the practical utility of ab initio TFBS discovery without species-specific training data. Researchers working on genome annotation of newly sequenced plant genomes would find the cross-species generalization claim highly relevant. The splice-variant analysis addresses a growing interest in isoform-specific regulation. The web server implementation increases accessibility for experimental biologists.

- **Major strengths** The conceptual advance of decoupling TFBS discovery from motif discovery is significant and addresses a real limitation of existing tools. The co-learning of sequence and structure is biologically well-motivated, given the known interdependence between TF structure and binding specificity. The ablation analysis showing progressive improvement from dimeric to heptameric representations is informative. The demonstration that removing structural information degrades performance provides evidence for the value of the multimodal approach. The splice-variant analysis for ARF8 is a novel and potentially important application. The genome-scale application in tea demonstrates practical utility. The web server and open-source code availability are commendable.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that PTF-Vāc "outperformed most advanced motif-finding deep-learning algorithms" across a comprehensive benchmarking study.
- **Evidence pointer** Results section "Exploring similarity and overlap in TF binding site discovery"; Figure 2C and 2D; Supplemental Tables 1 and 2
- **Concern** The benchmarking results are presented only as summary statements in the text. The actual data in Supplemental Tables 1 and 2 are not available for review. The text states that deepRAM matched for 24 of 36 TFs, DESSO for 14, TF-MoDISco for 8, and SeqConv for 4, but the criteria for "matching" are not operationally defined. It is unclear whether this refers to a p-value threshold, a similarity score threshold, or a combination. The claim of "outperforming" is therefore not quantitatively verifiable from the provided material.
- **Why it matters** The central claim of the manuscript is that PTF-Vāc is superior to existing tools. Without access to the actual comparison data, the statistical significance of the differences, the effect sizes, and the consistency across TFs cannot be assessed. This is the primary evidence for the utility of the method.
- **Resolution test** Provide the full benchmarking results for all 36 TFs, including the specific similarity metrics, p-values, and thresholds used. Report the distribution of performance differences across TFs, not just aggregate counts. Include confidence intervals or statistical tests for the comparison.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The manuscript claims that PTF-Vāc can discover binding sites "irrespective of data volume" and "even with a single input sequence."
- **Evidence pointer** Results section "Influence of input dataset size on TF binding site discovery"; Figure 2B; Supplemental Table 1, sheet 7
- **Concern** The claim of single-sequence capability is remarkable and would represent a major advance. However, the mechanism by which the model generates a binding site from a single input sequence is not explained. The model is trained on 48,000 instances, so the question is whether the model generalizes to a single test sequence. The text states that deepRAM needed at least 50 sequences, DESSO and SeqConv at least 100, and TF-MoDISco more than 200, but the actual performance metrics for PTF-Vāc at different input sizes are not reported. The figure description for Figure 2B mentions "various lengths, ranging from one sequence to the whole dataset" but the actual results are not visible.
- **Why it matters** The single-sequence capability is a key differentiator and has practical importance for species with limited data. If the model truly works with a single sequence, this needs to be demonstrated with specific examples, including the quality of the generated motif and its statistical significance. The mechanism by which the model avoids overfitting to a single input also needs clarification.
- **Resolution test** Provide quantitative results for PTF-Vāc at input sizes of 1, 5, 10, 50, 100, and the full dataset. Show the generated motifs for a single-sequence input and compare them to experimentally validated motifs. Explain the model's inference mechanism for single inputs.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation rigor
- **Claim pointer** The manuscript claims that molecular docking results "supported the TFBS motifs identified by PTF-Vāc" and that binding affinities were "very similar" to experimentally reported motifs.
- **Evidence pointer** Results section "Motif validation through molecular docking"; Table 1
- **Concern** The docking validation is presented for only five TFs. The choice of these five TFs is not justified, and the selection could introduce bias. The docking scores are reported as absolute values (e.g., ΔG = −111.33 kcal/mol), but there is no discussion of the expected range of docking scores for non-specific DNA–protein interactions. The claim that PTF-Vāc motifs have "very similar" binding affinities to experimentally reported motifs is based on visual inspection of the table, but no statistical comparison is provided. The pyDockDNA scoring function's reliability for plant TF–DNA interactions is not discussed.
- **Why it matters** Docking is used as an independent validation of the biological relevance of the predicted motifs. If the validation is based on only five TFs with no statistical framework, the evidence for biological relevance is weak. The possibility that any reasonable DNA motif would show similar docking scores needs to be excluded.
- **Resolution test** Justify the selection of the five TFs. Provide a statistical comparison of docking scores between PTF-Vāc motifs, experimentally validated motifs, and negative control motifs (e.g., random or scrambled sequences). Report the distribution of docking scores for a larger set of TFs.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The manuscript claims that PTF-Vāc "can be used to define binding motifs in newly sequenced plant genomes" and demonstrates this through the tea genome analysis.
- **Evidence pointer** Results section "Genome-scale analysis of TF binding sites in the tea genome using PTF-Vāc"; Supplemental Figures 1 and 2; Supplemental Table 3
- **Concern** The tea genome analysis identified 1878 potential BES1 target genes, of which 519 of 539 ChIP-seq-validated genes (98%) were recovered. This is a strong result. However, the false discovery rate is not reported: 1878 predicted targets versus 539 validated targets implies a large number of predictions that were not validated by ChIP-seq. The manuscript does not report how many of the 1878 predictions were not in the ChIP-seq set, nor does it discuss the potential reasons for these additional predictions. The GO and KEGG enrichment analyses are presented as supporting evidence, but the specificity of these enrichments is not compared to a background set of all genes.
- **Why it matters** The genome-scale application is the most practically relevant demonstration. The high recall (98%) is encouraging, but the precision is unclear. If the model predicts many false positives, the practical utility for genome annotation is diminished. The biological interpretation of the additional predicted targets needs discussion.
- **Resolution test** Report the precision of PTF-Vāc predictions against the ChIP-seq set. Provide an analysis of the 1359 predicted targets not validated by ChIP-seq. Compare GO/KEGG enrichment against a matched background set. Discuss the trade-off between sensitivity and specificity.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that Grad-CAM provides "explainability" and that the top-scoring k-mers "often closely matched the reported core motif" of the TF.
- **Evidence pointer** Results section "Explainable deep learning using Grad-CAM"; Figure 3; Supplemental Table 1, sheets 5 and 6
- **Concern** The agreement between Grad-CAM top-scoring regions and encoder–decoder-generated motifs ranges from 60.82% to 84.94% across TFs. This means that for some TFs, nearly 40% of the top-scoring regions do not match the generated motif. The manuscript does not discuss what these disagreeing regions represent. The claim that Grad-CAM "supports" the generated motifs is therefore only partially substantiated. The choice of the normalization layer after the multi-head attention layer as the layer of interest is justified, but the biological interpretation of the resulting importance scores is not fully developed.
- **Why it matters** Explainability is a stated feature of the system. If the explanation (Grad-CAM) and the prediction (encoder–decoder) disagree substantially for some TFs, the interpretability claim is weakened. Users need to understand when to trust the explanation.
- **Resolution test** Provide a detailed analysis of the disagreeing regions. Discuss whether these regions represent alternative binding sites, false positives, or limitations of the Grad-CAM approach. Provide examples of both agreeing and disagreeing cases.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Comparative rigor
- **Claim pointer** The manuscript claims that PTF-Vāc is "far surpassing the second-best option, DESSO" in binding-data coverage.
- **Evidence pointer** Results section "Evaluating binding-data coverage for each TF"; Figure 2D; Supplemental Table 1, sheet 4; Supplemental Table 2, sheets 1–4
- **Concern** The comparison with existing tools is complicated by the fact that these tools were designed for different purposes. deepRAM, DESSO, TF-MoDISco, and SeqConv are primarily motif discovery tools that require a set of input sequences and generate motifs, whereas PTF-Vāc generates a binding site for a single sequence given a TF structure. The comparison may not be apples-to-apples. The manuscript does not clarify whether the same input data were used for all tools, whether the tools were run with their default parameters, or whether any hyperparameter tuning was performed for the comparison.
- **Why it matters** The claim of superiority depends on a fair comparison. If the comparison protocol favors PTF-Vāc, the conclusions are not reliable. The different input requirements of the tools need to be explicitly addressed.
- **Resolution test** Describe the exact comparison protocol, including input data preparation, parameter settings, and any preprocessing steps. Discuss the conceptual differences between the tools and how these were accounted for in the comparison. Consider additional baselines, such as simple k-mer frequency analysis or position-specific scoring matrices derived from the training data.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract states that TFBS discovery "poses significant challenges due to high cross-species variability" but does not quantify this variability or provide specific examples. The term "ab initio" is used but not defined in the abstract.
- **Required correction** Briefly define "ab initio" in the context of TFBS discovery and provide one concrete example of cross-species variability to motivate the problem.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, Dataset retrieval
- **Evidence pointer** Methods section "Dataset retrieval"
- **Issue** The dataset is described as "retrieved from our previous work" with "48,000 instances for 40 TFs." The exact accession numbers, data sources, and filtering criteria are not provided in the manuscript text. The selection of "40 TFs representing 40 different families" is mentioned but the criteria for choosing these specific families are not explained.
- **Required correction** Provide the specific data sources, accession numbers, and any filtering or quality-control steps. Justify the selection of the 40 TF families.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, enrichment analysis
- **Evidence pointer** Results section "The identified binding sites display significant enrichment"
- **Issue** The manuscript states that motifs were "significantly enriched (binomial test p value << 0.01)" but does not report the actual p-values, the number of tests performed, or whether multiple-testing correction was applied. The coverage percentages (83.26% to 100%) are reported without confidence intervals.
- **Required correction** Report the actual p-values, the number of tests, and the multiple-testing correction method. Provide confidence intervals for coverage percentages.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods, Transformer–DenseNet system
- **Evidence pointer** Methods section "Transformer–DenseNet system"
- **Issue** The manuscript describes the architecture but does not provide the total number of parameters, the training time, the hardware used, or the inference time per sequence. The embedding dimension, number of attention heads, and number of Transformer layers are not specified.
- **Required correction** Provide the full architecture specification, including the number of layers, attention heads, embedding dimensions, and total parameter count. Report training time and inference speed.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, splice variant analysis
- **Evidence pointer** Results section "The curious case of TF splice variants"
- **Concern** The ARF8 splice variant analysis is presented as a case study, but the details of how the model was applied are sparse. It is unclear whether the model was given the structure of each splice variant separately, and how the predicted binding sites were compared to the experimentally reported targets.
- **Required correction** Provide the full methodological details for the splice variant analysis, including how the structures were obtained, how the model was applied, and how the predictions were validated.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Web server
- **Evidence pointer** Results section "Web server implementation"
- **Issue** The web server is described as freely accessible, but the manuscript does not specify the supported input formats, the maximum sequence length, the number of concurrent users, or the expected runtime for typical queries. The integration with TOMATO is mentioned but not described in detail.
- **Required correction** Provide a clear description of the web server's capabilities, limitations, and usage instructions.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Language
- **Affected element** Throughout
- **Evidence pointer** Multiple sections
- **Issue** The manuscript uses the term "raised" in place of "trained" (e.g., "The raised model's final assessment", "the model was raised again"). This is non-standard terminology and may cause confusion.
- **Required correction** Replace "raised" with "trained" throughout the manuscript.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Limitations
- **Evidence pointer** Discussion
- **Issue** The manuscript does not include a dedicated limitations section. The limitations mentioned in the "Limitations of PTF-Vāc" section focus on the requirement for 3D structures and the restriction to plant TFs, but do not address potential limitations of the generative approach itself, such as the risk of generating consensus-like motifs that may not capture rare but functional binding sites.
- **Required correction** Add a discussion of the potential limitations of the generative approach, including the risk of over-consensus motifs, the handling of degenerate binding sites, and the interpretability of the latent representations.

## Risk / unsupported claims
- The claim that PTF-Vāc "outperformed most advanced motif-finding deep-learning algorithms" is not quantitatively verifiable from the provided material, as the actual benchmarking data are in inaccessible supplemental tables.
- The claim that PTF-Vāc works "even with a single input sequence" is not supported by specific examples or quantitative results in the manuscript text.
- The claim that molecular docking "supported" the PTF-Vāc motifs is based on only five TFs with no statistical comparison to negative controls.
- The claim that PTF-Vāc "can be used to define binding motifs in newly sequenced plant genomes" is based on a single genome-scale application with unreported precision.
- The claim that the model "learned the shift in binding patterns with the structure and was not merely memorizing" is supported by the cross-species analysis, but the sample size (10 TFs) is small and the statistical power is unclear.
- The statement that "PTF-Vāc was found to be outstanding across all the considered parameters" in a previous benchmarking study (Jyoti et al., 2024) is cited but not independently verifiable from the current manuscript.
- The ablation analysis results are described in text but the actual accuracy values for individual representations are only partially reported.
- The claim that the model is "completely independent of any TF- or species-specific model" needs clarification, as the model is trained on a specific dataset of 40 TFs and may have inherent biases from that training set.

## Assessment against Nature-style criteria

**Originality**: The concept of using a Transformer encoder–decoder in a generative framework for TFBS discovery, coupled with co-learning of protein structure via DenseNet, is genuinely novel. The decoupling of TFBS discovery from motif discovery represents a conceptual advance. The application to splice variant discrimination is particularly innovative. However, the originality is somewhat tempered by the reliance on previously published PTFSpot as the foundation, and the incremental nature of the architectural extension needs to be clearly articulated.

**Scientific importance**: The problem addressed is of high importance. Plant genomes show substantial cross-species variability in TFBSs, and existing tools are inadequate for non-model species. The potential to perform ab initio TFBS discovery without species-specific training data would have significant impact on plant genomics. The genome-scale application in tea demonstrates practical relevance. However, the importance of the claims depends on the robustness of the validation, which is currently insufficiently documented.

**Interdisciplinary readership**: The work bridges computational biology, deep learning, and plant molecular biology. The potential readership is broad, spanning bioinformaticians developing new methods and plant biologists seeking practical tools. The web server implementation enhances accessibility. However, the manuscript assumes significant familiarity with both deep learning architectures and TF biology, which may limit accessibility to either audience individually.

**Technical soundness**: The architectural design is reasonable and well-motivated. The ablation study is a good practice. The use of multiple validation approaches (enrichment, TOMATO comparison, docking, cross-species) is commendable. However, the technical soundness is undermined by the lack of accessible data, unclear benchmarking protocols, and insufficient statistical detail. The choice of the normalization layer for Grad-CAM requires more justification. The handling of the sequence-to-structure alignment problem is not fully described.

**Readability for nonspecialists**: The manuscript is written in a style that is accessible to computational biologists but may be challenging for experimental plant biologists. The introduction provides good context, but the methods section is dense. The figures, based on the legends, appear informative but cannot be evaluated without the actual images. The abstract is clear but could benefit from a more explicit statement of the problem and the novelty of the approach.