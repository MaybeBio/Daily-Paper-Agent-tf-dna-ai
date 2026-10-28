## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, and figure legends
- **Assessment boundary** Scientific claims, methodology, and evidence presented in the manuscript; no assessment of editorial fit or publication decision
- **Shared manuscript claim summary** The authors introduce species-aware DNA language models trained on over 800 fungal species spanning 500 million years of evolution. They claim these models capture regulatory elements, distinguish functional from non-functional motif instances, account for evolutionary changes in regulatory codes, and provide sequence representations that outperform existing methods on downstream prediction tasks.
- **Visible evidence base** Main text figures 1-5, supplementary figure references, methods section, and additional file descriptions
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided in full; specific model architecture details partially described; hyperparameter search details not fully specified; code availability not stated

## Reviewer
- **Overall assessment** This manuscript presents a timely and well-executed application of DNA language models to multi-species regulatory genomics. The central claim that species-aware training improves both interpretability and predictive performance is supported by multiple complementary analyses. The demonstration that reconstruction fidelity predicts in vivo binding without any labeled training data is particularly compelling. However, several technical details require clarification, and the generalizability of the approach beyond fungi remains untested. The comparison to alignment-based methods, while favorable, could be strengthened by more systematic benchmarking.

- **Who would be interested in the results, and why** Researchers in regulatory genomics, computational biology, and evolutionary genomics would find this work valuable. The demonstration that language models can serve as alignment-free conservation measures has broad implications for studying non-coding regions in understudied species. The finding that species-aware training improves downstream prediction performance will interest those building genomic foundation models. The in silico mutagenesis approach for motif discovery from model representations provides a template applicable beyond this specific system.

- **Major strengths** The study addresses a clear gap in the field by explicitly evaluating what DNA language models learn about regulatory elements across evolutionary scales. The multi-pronged evaluation strategy, combining reconstruction analysis, in vivo binding prediction, and downstream task performance, provides convergent evidence for the utility of the approach. The species-aware design is conceptually simple yet demonstrably effective. The authors are appropriately cautious in their claims and acknowledge limitations.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that species-aware training yields improved sequence representations for endogenous and MPRA-based gene expression prediction, as well as motif discovery.
- **Evidence pointer** Figure 5, Additional file 1: Table S1, Table S2
- **Concern** The comparison to baseline methods is incomplete. The authors compare against k-mer counts and, where available, published deep learning models. However, they do not compare against simpler conservation-based features (e.g., phastCons scores aggregated over the sequence) or against single-species DNA language models trained on S. cerevisiae alone. The claim that multi-species training is beneficial would be substantially strengthened by ablating the number of species in training and showing a monotonic improvement. The authors mention such ablations were performed (Additional file 1: Table S2) but the details are not visible in the provided materials.
- **Why it matters** The central contribution of the paper is the species-aware training paradigm. Without a clear demonstration that the improvement comes specifically from multi-species training rather than from the transformer architecture itself, the claim is not fully established.
- **Resolution test** Provide the full ablation results showing performance as a function of training species set. Include a single-species baseline trained on S. cerevisiae alone. Show that the improvement is not simply due to increased data volume by training on an equivalent number of sequences from a single species.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that DNA language models capture conserved regulatory elements over much further evolutionary distances than sequence alignment would allow.
- **Evidence pointer** Figure 1A-B, Figure 2A
- **Concern** The comparison to alignment is indirect. The authors show that alignment fails to align 3' UTRs beyond the genus level, while language models still reconstruct motifs. However, this is not a direct head-to-head comparison. A more rigorous test would be to compare the language model's reconstruction accuracy against a conservation score computed from a multiple sequence alignment of closely related species, or against a phylogenetic hidden Markov model that accounts for motif turnover. The phastCons comparison in Figure 3C and 3E is useful but limited to two specific cases.
- **Why it matters** The claim that language models outperform alignment-based approaches is a strong one with practical implications. If the comparison is not fair or comprehensive, the conclusion may be overstated.
- **Resolution test** Perform a systematic comparison across all motifs tested, correlating reconstruction accuracy with phastCons scores. For a subset of cases, compute alignment-based conservation using the closest alignable species and compare predictive performance for in vivo binding.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors suggest that language models may prove useful for accurate genome annotation of understudied species.
- **Evidence pointer** Figure 4, Discussion
- **Concern** The demonstration of cross-species transfer is limited to a small number of motifs and species. The analysis of the TATA box in S. pombe and S. cerevisiae is illustrative but does not establish general utility for genome annotation. The claim about utility for understudied species would be strengthened by evaluating on a species more distantly related to the training set, or by demonstrating that the model can identify novel regulatory elements not previously annotated.
- **Why it matters** The practical impact of this work depends on its generalizability beyond the well-studied species used for validation. Without evidence of broader applicability, the significance is limited.
- **Resolution test** Apply the model to a non-fungal species or a fungal species from an underrepresented lineage. Evaluate whether the model can identify regulatory elements that are validated by independent experimental data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that the species-aware model accounts for changes in the regulatory code between species, as demonstrated by the TATA box positional constraints and the Rap1 motif analysis.
- **Evidence pointer** Figure 4B-C, Additional file 1: Fig S9
- **Concern** The analysis of the Rap1 motif across species relies on BLAST matches to identify species with and without Rap1p homologs. This is a coarse proxy for the presence of the regulatory mechanism. The absence of a BLAST match does not necessarily mean the protein is absent or non-functional, and the presence of a match does not guarantee functional conservation. The interpretation that the model "correctly accounts for species context" may be over-simplified.
- **Why it matters** The claim that the model captures species-specific regulatory code evolution is a key finding. If the validation is based on unreliable species classifications, the conclusion is weakened.
- **Resolution test** Use curated orthology assignments or functional data to classify species with respect to Rap1p function. Alternatively, use a motif known to be functionally conserved across all tested species as a positive control.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, model architecture
- **Evidence pointer** Materials and methods, Masked language modeling
- **Issue** The model architecture description is brief. The authors state they used a DNABERT architecture with 12 transformer blocks and approximately 90M parameters, but do not specify the number of attention heads, hidden dimension, or other architectural details. The tokenization scheme (overlapping 6-mers) is described, but the vocabulary size and positional encoding approach are not stated.
- **Required correction** Provide complete architectural details, including hidden dimension, number of attention heads, feed-forward dimension, dropout rates, and training hyperparameters. This is necessary for reproducibility.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Figure 2A significance testing
- **Evidence pointer** Figure 2A, legend
- **Issue** The authors report that the species model significantly outperforms the best baseline using a binomial test (P < 0.05). However, multiple motifs are tested simultaneously, and no multiple testing correction is mentioned. The number of motifs tested and the total number of comparisons should be stated.
- **Required correction** Report whether multiple testing correction was applied, and if not, provide the uncorrected P values alongside the number of tests performed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Data availability
- **Evidence pointer** Materials and methods, Genome data
- **Issue** The authors state they obtained genomes from Ensembl Fungi 53 but do not provide a list of the specific species used, nor the accession numbers for the genome assemblies. The statement that 1,500 genomes comprising 806 species were used is insufficient for reproducibility.
- **Required correction** Provide a supplementary table listing all species and genome assembly accessions used in training and evaluation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Figure 5D, motif discovery
- **Evidence pointer** Figure 5D, Discussion
- **Issue** The authors recover two of four known motifs from the Cheng et al. analysis and two additional motifs not found previously. The claim that this demonstrates utility for motif discovery is reasonable, but the false discovery rate is not assessed. The number of motifs discovered by the in silico mutagenesis approach that do not match known motifs is not reported.
- **Required correction** Report the total number of motifs discovered and the proportion that match known motifs. Discuss the potential for false discoveries.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 3B-D, TATA box analysis
- **Evidence pointer** Figure 3B-D
- **Issue** The TATA box analysis in S. pombe and S. cerevisiae is presented as evidence that the model accounts for positional constraints. However, the figure shows only two species. The claim that the model "applies specific constraints when reconstructing motifs in a way that reflects the evolution of the initiation code" would be more convincing with additional species showing intermediate or divergent positional preferences.
- **Required correction** Consider adding additional species with known TATA box positional preferences to strengthen this analysis, or temper the claim to reflect the limited species sampling.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Proxy species token selection
- **Evidence pointer** Materials and methods, Masked language modeling; Additional file 1, Species Token Choice
- **Issue** The use of proxy species tokens for the held-out species S. cerevisiae is a critical methodological choice. The authors state that the choice of proxy was investigated in the supplementary material, but the details are not visible in the provided text. The selection of C. glabrata for the 3' model and K. africana for the 5' model appears arbitrary without this context.
- **Required correction** Summarize the key findings of the proxy species analysis in the main text, including how the proxies were selected and the sensitivity of results to this choice.

## Risk / unsupported claims
- The claim that language models "capture conserved regulatory elements over much further evolutionary distances than sequence alignment would allow" is not directly tested; the comparison is indirect and would benefit from a head-to-head benchmark.
- The claim that species-aware training yields improved representations is supported by the presented data, but the ablation analysis (Additional file 1: Table S2) is not visible and is essential for full evaluation.
- The claim that the model "accounts for changes in the regulatory code between species" is based on limited species sampling and indirect proxies for regulatory mechanism presence.
- The generalizability of the approach to non-fungal species is not tested and should not be inferred from the current data.
- The statement that the model can be used for "accurate genome annotation of understudied species" is speculative and not directly supported by the presented experiments.