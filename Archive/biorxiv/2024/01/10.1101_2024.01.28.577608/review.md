## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, and supplementary references) as provided
- **Assessment boundary** Scientific claims, methodological soundness, benchmarking validity, and reproducibility as presented in the provided text
- **Shared manuscript claim summary** The authors present PTF-Vāc, a generative deep learning encoder-decoder system that, guided by a universal model of TF:DNA interaction co-variability (PTFSpot), claims to perform ab-initio discovery of plant transcription factor binding sites (TFBS) and motifs without requiring predefined TF-specific models, motif matrices, or large input data volumes, and to outperform existing deep learning tools across multiple benchmarking criteria.
- **Visible evidence base** Abstract, introduction, results sections (including ablation analysis, enrichment testing, TOMCOM comparisons, cross-species validation, splice variant case study, genome-scale tea analysis), methods descriptions, and references to supplemental tables and figures
- **Missing materials affecting confidence** Actual figures and supplemental tables (including detailed benchmarking data, Grad-CAM visualizations, docking scores, and full comparative results) were not provided; exact model architecture hyperparameters, training details, and code implementation specifics are only partially described; no quantitative performance metrics (e.g., precision, recall, AUC) are reported in the text

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting and potentially impactful approach to plant TFBS discovery, addressing a real gap in cross-species applicability and removing the dependency on predefined motif models. The integration of a universal interaction model with a generative encoder-decoder architecture is novel in this domain. However, the current text provides insufficient quantitative evidence to fully evaluate the claimed performance. Key benchmarking results are described qualitatively, and critical details on model training, evaluation metrics, and statistical rigor are missing. The splice variant case study and genome-scale application are compelling but require more thorough validation and comparison with existing methods. The manuscript would benefit from clearer reporting of performance metrics, error analysis, and limitations.
- **Who would be interested in the results, and why** Plant molecular biologists, computational biologists, and bioinformaticians working on gene regulation, transcription factor biology, and genome annotation. Researchers developing deep learning methods for regulatory genomics would also find the architecture and the concept of decoupling motif discovery from binding site prediction of interest. The cross-species capability and splice variant sensitivity are particularly relevant for non-model plant species research.
- **Major strengths** 1) The conceptual advance of decoupling TFBS discovery from motif discovery and TF-specific models is significant and addresses a well-known limitation in the field. 2) The use of a universal TF:DNA interaction model trained on co-variability of structure and binding is innovative. 3) The demonstrated ability to handle single input sequences and splice variants is practically valuable. 4) The genome-scale application to tea provides a realistic use case. 5) The inclusion of Grad-CAM for interpretability is a positive step toward explainable AI in genomics.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative benchmarking evidence), R1-M2 (statistical rigor and multiple testing), R1-M3 (splice variant validation), R1-M4 (genome-scale validation completeness), R1-M5 (reproducibility and method details)
- **Assessment against Nature-style criteria** Originality: High. The concept of a generative, explainable, universal model for TFBS discovery is a clear departure from existing motif-centric tools. Scientific importance: Potentially high, as it could enable reliable TFBS annotation in non-model species and advance understanding of TF binding variability. Interdisciplinary readership: The work bridges deep learning, genomics, and plant biology, and would appeal to a broad audience if the claims are substantiated. Technical soundness: Currently not fully assessable due to missing quantitative details and incomplete benchmarking descriptions. Readability for nonspecialists: The main text is generally accessible, but some methods sections are dense and would benefit from clearer explanations of the architecture and evaluation procedures.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the preliminary evidence is encouraging, but the current manuscript does not provide sufficient quantitative and statistical evidence to fully establish the claimed performance advantages.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that PTF-Vāc "outperformed most advanced motif finding deep learning (DL) algorithms" and "consistently delivered the best performance, whether given extensive data or just a single sequence."
- **Evidence pointer** Results sections "Comparative benchmarking and performance comparison" and "Influence of input dataset sizes on TF binding site discovery"; location not provided
- **Concern** The benchmarking results are described only qualitatively. No quantitative performance metrics (e.g., precision, recall, F1-score, AUC, or enrichment significance values) are reported in the text for PTF-Vāc or the compared tools. The claim of outperformance cannot be evaluated without these data. Additionally, the criteria for "best performance" are not explicitly defined.
- **Why it matters** The central claim of the manuscript is that PTF-Vāc is superior to existing tools. Without quantitative evidence, this claim is unsupported and the scientific contribution cannot be assessed.
- **Resolution test** Provide a table or figure with quantitative performance metrics (e.g., precision, recall, F1, AUC, or similar) for PTF-Vāc and all compared tools across all benchmarking datasets, including statistical significance tests for differences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript states that PTF-Vāc motifs were "significantly enriched (binomial test p-value << 0.01)" and that TOMTOM comparisons yielded "very significant score (<<0.01)."
- **Evidence pointer** Results sections "The identified binding sites displayed significant enrichment and matched the experimentally reported motifs" and "Genome-scale analysis of TF binding sites in the Tea Genome using PTF-Vāc"; location not provided
- **Concern** The use of "p-value << 0.01" is vague and does not constitute a proper statistical report. Exact p-values should be provided. Moreover, when testing multiple TFs and multiple motifs, multiple testing corrections (e.g., Benjamini-Hochberg) should be applied and reported. The TOMTOM comparison for the tea genome is described as "very significant" without reporting the actual p-value or the number of comparisons.
- **Why it matters** Rigorous statistical reporting is essential for the credibility of the enrichment and similarity claims. Vague p-value reporting prevents the reader from assessing the strength of the evidence.
- **Resolution test** Report exact p-values for all enrichment and TOMTOM comparisons, state whether multiple testing corrections were applied, and provide the corrected significance thresholds.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation sufficiency
- **Claim pointer** The manuscript claims that PTF-Vāc can "distinguish between splice variants differential binding for any given TF" based on the ARF8 case study.
- **Evidence pointer** Results section "The curious case of splice variants of transcription factors and their differential binding preferences"; location not provided
- **Concern** The ARF8 case study is based on a single TF with two splice variants. The claim that PTF-Vāc can distinguish splice variant differential binding "for any given TF" is a strong generalization from a single example. Moreover, the validation appears to rely on ChIP-qPCR data from a previous study, but the details of how PTF-Vāc's predictions were compared to these experimental data are not provided.
- **Why it matters** Overgeneralization from a single case study undermines the credibility of the claim. The splice variant capability is a key differentiator of the tool and needs stronger validation.
- **Resolution test** Provide additional splice variant case studies across different TF families, and clearly describe the validation methodology, including how PTF-Vāc's predictions were compared to experimental binding data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Completeness of genome-scale validation
- **Claim pointer** The manuscript claims that PTF-Vāc identified 1,878 potential target genes for BES1 in tea, with 98% overlap with ChIP-seq identified targets.
- **Evidence pointer** Results section "Genome-scale analysis of TF binding sites in the Tea Genome using PTF-Vāc"; location not provided
- **Concern** While the 98% overlap is impressive, the analysis appears to be based on a single TF in a single species. The false discovery rate is not reported, and the biological significance of the identified targets is only briefly discussed. The GO and KEGG enrichment analyses are mentioned but the full results are only in supplemental materials. The claim that this demonstrates "credible genome wide runs for any TF and any species" is an overgeneralization.
- **Why it matters** Genome-scale applicability is a major claimed advantage. A single case study is insufficient to establish this, and the lack of false discovery rate analysis raises concerns about specificity.
- **Resolution test** Provide additional genome-scale validations in multiple species, report false discovery rates, and include a more detailed analysis of the biological relevance of the identified targets.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The manuscript describes the PTF-Vāc architecture and training procedure in the Methods section.
- **Evidence pointer** Methods sections "Transformer-DenseNet system", "Constructing the DenseNet architecture", "Word representations of sequence data for Transformer", "Implementation of the Transformers Encoders-Decoders", "Generating binding sites from the Transformer-Decoder output", and "Implementation of Grad-CAM"; location not provided
- **Concern** The methods description lacks critical details for reproducibility. The exact architecture hyperparameters (e.g., number of layers, hidden dimensions, number of attention heads, dropout rates) are not fully specified. Training details such as learning rate schedule, optimizer parameters, batch size rationale, and early stopping criteria are incomplete. The tokenization procedure is mentioned but not fully described. The exact procedure for generating binding sites from the decoder output and the threshold for Jaro similarity are not specified.
- **Why it matters** Reproducibility is a fundamental requirement for scientific software. Without complete methodological details, other researchers cannot implement or verify the method.
- **Resolution test** Provide a complete description of the architecture, training procedure, and all hyperparameters, or make the code publicly available with clear documentation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction; location not provided
- **Issue** The phrase "deep co-learning encoders-decoders system" is used repeatedly but not clearly defined in the abstract or introduction. The relationship between the "universal model" (PTFSpot) and the new system (PTF-Vāc) could be explained more clearly for readers unfamiliar with the previous work.
- **Required correction** Provide a brief, clear explanation of what "co-learning" means in this context and how PTF-Vāc builds upon PTFSpot.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results section "Deep co-learning by Transformer-DenseNet system on the words and structure performs consistently well"
- **Evidence pointer** Results section; location not provided
- **Issue** The term "words" is used to describe k-mer sequence representations, which may be confusing. The distinction between "words" and "k-mers" should be clarified.
- **Required correction** Define "words" explicitly as k-mer sequence representations and use consistent terminology throughout.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "Comparative benchmarking and performance comparison"
- **Evidence pointer** Results section; location not provided
- **Issue** The descriptions of the compared tools (deepRAM, DESSO, TF-MoDISco, SeqConv) are brief and somewhat generic. It is unclear whether these descriptions are accurate for the specific versions used.
- **Required correction** Provide more specific descriptions of the tools and versions used, and cite the appropriate references.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Genome-scale analysis of TF binding sites in the Tea Genome using PTF-Vāc"
- **Evidence pointer** Results section; location not provided
- **Issue** The text states "The motif reported by the authors in that work (Liu et al., 2025) on their ChIP-seq binding data, was reported by MEME." This sentence is awkwardly phrased and the reference to Liu et al. (2025) is not in the provided reference list.
- **Required correction** Rewrite the sentence for clarity and ensure all references are properly cited.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Results section "Genome-scale analysis of TF binding sites in the Tea Genome using PTF-Vāc"
- **Evidence pointer** Results section; location not provided
- **Issue** The text mentions "free energy of binding of PTF-Vāc motif for binding stability was found much higher than the motif reported by the authors." The direction of this difference is unclear (higher free energy typically means less stable binding). This should be clarified.
- **Required correction** Clarify whether "higher" free energy means more or less stable binding, and discuss the implications.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Web-server implementation section
- **Evidence pointer** Web-server implementation section; location not provided
- **Issue** The description of the scoring schemes is somewhat disorganized, with numbered items that are not clearly separated. The relationship between the different scoring schemes and the overall output is unclear.
- **Required correction** Reorganize the description of scoring schemes for clarity and explain how they relate to each other.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Accuracy
- **Affected element** Limitations section
- **Evidence pointer** Limitations section; location not provided
- **Issue** The limitation regarding "Requirement for 3D TF Protein Structures" is acknowledged, but the practical impact is not discussed. For many plant TFs, AlphaFold2 structures may not be available or may be of low confidence.
- **Required correction** Discuss the practical implications of this limitation and any potential workarounds.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section "Dataset retrieval"
- **Evidence pointer** Methods section; location not provided
- **Issue** The description of the dataset is incomplete. It is unclear how the 40 TFs were selected from the 325 in Dataset "E", and what criteria were used to ensure representativeness.
- **Required correction** Provide more details on the dataset composition and selection criteria.

## Risk / unsupported claims
- The claim that PTF-Vāc "outperformed most advanced motif finding deep learning (DL) algorithms" is unsupported without quantitative benchmarking data.
- The claim that PTF-Vāc can distinguish splice variant differential binding "for any given TF" is an overgeneralization from a single case study.
- The claim that PTF-Vāc can perform "credible genome wide runs for any TF and any species" is unsupported by the single-species, single-TF genome-scale analysis presented.
- The claim that PTF-Vāc is "completely free" from dependency on data volume is not fully supported, as the minimum input requirements are not systematically tested.
- The statement that PTF-Vāc "brings a completely new chapter in ab-initio TFBS discovery through generative AI" is promotional and not a testable scientific claim.
- The claim that the free energy of binding for PTF-Vāc motifs is "much higher" than experimentally reported motifs is ambiguous and potentially misleading without clarification of the direction of stability.