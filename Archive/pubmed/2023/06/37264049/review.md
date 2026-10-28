## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and alignment with Nature-style criteria
- **Shared manuscript claim summary** The authors report identification of a covert evolutionary pathway between two protein folds, helix-turn-helix (HTH4) and winged helix (wH), in bacterial response regulators. They use multiple statistical methods on ~600,000 sequences, phylogenetic analyses, ancestral sequence reconstruction, and AlphaFold2 modeling to support a stepwise mutation mechanism for fold switching, with potential functional consequences in expanded DNA-binding specificity.
- **Visible evidence base** Abstract, full main text, figure legends (Figures 1-6), methods section, supplementary information descriptions
- **Missing materials affecting confidence** Supplementary Tables 1-5, Supplementary Figures 1-9, Supplementary Datasets 1-3, actual phylogenetic trees, AlphaFold2 model confidence metrics, sequence alignment details, and raw statistical outputs were not provided for direct verification

## Reviewer
- **Overall assessment** This manuscript presents a compelling and potentially significant claim: that a covert evolutionary pathway exists between two distinct protein folds, HTH4 and wH, in bacterial response regulators. The authors marshal an impressive array of computational evidence, including large-scale sequence analysis, phylogenetic inference, ancestral sequence reconstruction, and structural prediction. The central claim that stepwise mutations can interconvert α-helices and β-sheets within a conserved protein context is provocative and, if substantiated, would challenge conventional views on protein fold evolution. However, the manuscript's reliance on computational predictions without experimental validation, combined with several methodological concerns, leaves the central thesis not fully established. The authors themselves acknowledge that AlphaFold2 predicts only one dominant conformation for fold-switching proteins, which introduces uncertainty about whether the predicted ancestral structures are reliable. The statistical support for the bridge clade, while suggestive, requires more rigorous validation. The functional claim regarding expanded DNA-binding specificity is based on a small sample size and lacks direct experimental evidence. Overall, this is an interesting and well-written manuscript with a novel approach, but the evidence presented does not yet fully support the strong claims made.

- **Who would be interested in the results, and why** Evolutionary biologists studying protein fold evolution and the origins of structural diversity would find this work directly relevant. Structural biologists interested in fold-switching mechanisms and conformational plasticity would also be engaged. Additionally, computational biologists developing methods for detecting remote homology and ancestral sequence reconstruction would benefit from the methodological framework. The potential link between fold switching and functional diversification in two-component signaling systems may interest microbiologists studying bacterial signal transduction and regulatory networks.

- **Major strengths** 
  1. The study leverages an exceptionally large sequence dataset (~600,000 sequences) to overcome limitations of previous work, providing substantial statistical power for homology inference.
  2. The multi-method approach, combining BLAST, PSI-BLAST, jackhmmer, phylogenetic analysis, ancestral reconstruction, and AlphaFold2, is comprehensive and mutually reinforcing.
  3. The identification of a bridge clade with sequences annotated as HTH4 but positioned between the two fold families in phylogenetic space is an elegant and novel finding.
  4. The authors provide a practical step-by-step guide for identifying fold-switching events in other protein families, enhancing the broader utility of their approach.
  5. The writing is clear and accessible, with well-designed figures that effectively communicate complex structural and phylogenetic concepts.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "all lines of evidence consistently point to an evolutionary trajectory by which an α-helix transformed into a β-sheet through stepwise mutation(s)."
- **Evidence pointer** Results sections "Phylogenetic analyses of HTH4 and wH proteins" and "A mutational pathway between two folds"; Figures 3 and 4
- **Concern** The central claim of a stepwise evolutionary pathway relies heavily on AlphaFold2 predictions of ancestral sequences. The authors acknowledge that AlphaFold2 generally predicts only one dominant conformation for proteins that can switch between two folds. This creates a circularity problem: if the ancestral sequences were genuinely capable of adopting both folds, AlphaFold2 would likely predict only one, potentially biasing the interpretation toward the observed HTH4 predictions. The manuscript does not address how this limitation affects the reliability of the ancestral structural predictions. Furthermore, the bridge clade consists of only 12 sequences, which is a small sample for making strong claims about an evolutionary transition. The statistical support for this clade's position and its role as an evolutionary intermediate requires more rigorous testing, such as alternative tree topologies or model-based tests of character evolution.
- **Why it matters** The entire thesis of the paper rests on the identification of a specific evolutionary pathway. If the ancestral reconstructions are unreliable or the bridge clade is not truly intermediate, the claim of a covert evolutionary pathway collapses. The small sample size and the acknowledged limitations of AlphaFold2 for fold-switching proteins undermine confidence in the central conclusion.
- **Resolution test** The authors should provide additional validation of the ancestral sequence predictions, such as experimental characterization of the reconstructed ancestral proteins using circular dichroism or NMR spectroscopy to determine their actual folds. Alternatively, they could employ molecular dynamics simulations to assess the conformational ensembles of the ancestral sequences. For the bridge clade, they should perform more robust phylogenetic tests, such as approximately unbiased tests comparing alternative placements of the bridge sequences, and assess whether the bridge clade is statistically distinguishable from a random assortment of sequences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The authors claim that "the use of full-length sequences in our analyses, rather than isolated domains, is both legitimate and necessary to identify the relationship" between HTH4 and wH domains.
- **Evidence pointer** Results section "Apparent homology between bacterial response regulators with HTH4 and wH CTDs"; Figure 1
- **Concern** The authors dismiss the possibility of homologous overextension, where strong N-terminal domain similarity could erroneously produce alignments in the C-terminal domains. While they provide some evidence against this, the argument is not fully convincing. The initial BLAST alignment covered only 52% of the CTD sequence, which is a substantial portion left unaligned. The authors do not provide a quantitative comparison of alignment scores between full-length and CTD-only searches, nor do they assess whether the observed cross-fold alignments are significantly better than what would be expected from random sequences with similar amino acid compositions. The reciprocal jackhmmer searches are suggestive but do not definitively rule out overextension, especially given the low sequence identity between the HTH4 and wH domains.
- **Why it matters** If the cross-fold homology is an artifact of homologous overextension, then the entire premise of the paper, that these two folds share an evolutionary relationship, would be invalid. The distinction between true homology and alignment artifact is fundamental to the study's conclusions.
- **Resolution test** The authors should perform a rigorous statistical test for homologous overextension, such as comparing the distribution of alignment scores from real sequences to those from shuffled or simulated sequences with similar compositional biases. They could also use profile-profile comparisons or hidden Markov model-based searches that are less susceptible to overextension. Additionally, they should provide a detailed analysis of the alignment quality in the CTD region, including the number of gaps, conserved positions, and the statistical significance of the alignment independent of the NTD.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Functional evidence
- **Claim pointer** The authors claim that "this structural transformation likely expanded DNA-binding specificity" based on the observation that wH domains contact more nucleotides on average than HTH4 domains.
- **Evidence pointer** Results section "Evolution from HTH4 to wH may have expanded DNA-binding specificity"; Figure 5
- **Concern** The functional claim is based on a comparison of only 16 HTH4-DNA and 15 wH-DNA complex structures. This is a small sample size, and the difference in nucleotide contacts (17 vs. 22) is presented without statistical testing. The authors do not account for potential confounding factors, such as differences in DNA sequence preferences, binding site lengths, or the specific biological contexts of the complexes analyzed. The claim that this difference "likely" expanded binding specificity is speculative and not supported by direct experimental evidence. No binding assays, specificity profiling, or functional experiments are presented.
- **Why it matters** The functional significance of the fold switch is a key part of the paper's narrative. If the claim of expanded DNA-binding specificity is not well supported, the evolutionary driving force behind the fold switch remains unclear, weakening the overall story.
- **Resolution test** The authors should perform statistical tests (e.g., t-test or Mann-Whitney U test) on the contact number distributions and provide effect sizes. They should also discuss potential confounding factors and ideally provide experimental data, such as electrophoretic mobility shift assays or surface plasmon resonance experiments, comparing the DNA-binding affinities and specificities of representative HTH4 and wH proteins. Alternatively, they could analyze a larger set of structures or use computational predictions to strengthen the correlation.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 2
- **Evidence pointer** Figure 2 legend
- **Issue** The figure legend for Figure 2 is dense and difficult to follow. The description of the color coding for secondary structure alignments is particularly confusing, and the relationship between the heatmap in panel (a) and the structural alignments in panel (b) is not immediately clear.
- **Required correction** The legend should be rewritten to more clearly explain the color scheme and how to interpret the relationship between the sequence identity matrix and the secondary structure alignments. A step-by-step guide to reading the figure would be helpful.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section
- **Evidence pointer** Methods section "Identifying large sets of response regulators' genomic sequences"
- **Issue** The methods for sequence retrieval and filtering are described briefly. The authors state that sequences with fewer than 162 or more than 300 residues were removed, but the rationale for these specific cutoffs is not provided. Additionally, the details of the greedy clustering algorithm are not fully specified, making it difficult to reproduce.
- **Required correction** The authors should provide a clear rationale for the length cutoffs and a more detailed description of the clustering algorithm, including pseudocode or a reference to a previously published implementation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 5
- **Evidence pointer** Figure 5 legend
- **Issue** The box-and-whisker plot in Figure 5a shows the distribution of DNA contacts, but no statistical information is provided. The authors state that wH domains have "5 fewer DNA contacts" on average, but the variance and sample size are not clearly indicated in the figure or legend.
- **Required correction** The figure should include error bars or confidence intervals, and the legend should report the sample sizes and the results of any statistical tests performed.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Abstract and Introduction
- **Issue** The term "covert" in the title and abstract is evocative but not precisely defined. It is unclear whether this refers to the difficulty of detection, the low sequence identity, or the unexpected nature of the relationship.
- **Required correction** The authors should define what they mean by "covert" in the context of their study, perhaps in the introduction, to avoid ambiguity.

- **Technical failings that need to be addressed before the case is established** 
  1. The potential circularity in using AlphaFold2 to predict ancestral structures when the method is known to predict only one conformation for fold-switching proteins (R1-M1).
  2. The insufficient exclusion of homologous overextension as an alternative explanation for the cross-fold alignments (R1-M2).
  3. The lack of statistical testing for the functional claim regarding DNA-binding specificity (R1-M3).
  4. The small sample size of the bridge clade (12 sequences) and the lack of robustness testing for its phylogenetic position (R1-M1).

- **Assessment against Nature-style criteria** 
  - **Originality**: The work is highly original. While fold-switching has been observed in individual proteins, the systematic identification of an evolutionary pathway between two folds in a large protein family is novel. The concept of "covert" evolutionary pathways that are only detectable with large-scale data and multiple methods is a fresh contribution.
  - **Scientific importance**: The findings have the potential to reshape understanding of protein fold evolution. If the claims are substantiated, they would demonstrate that fold switching can occur through stepwise mutations in nature, not just in laboratory evolution experiments. This has implications for protein engineering, evolutionary biology, and our understanding of the protein structure universe.
  - **Interdisciplinary readership**: The work bridges evolutionary biology, structural biology, and computational biology. It would appeal to researchers in all three fields, as well as to microbiologists studying two-component signaling systems. The methodological framework is transferable to other protein families, broadening its appeal.
  - **Technical soundness**: The computational methods are generally appropriate and state-of-the-art, but the concerns raised above about AlphaFold2 usage, overextension, and statistical rigor need to be addressed. The lack of experimental validation is a significant gap for a claim of this magnitude.
  - **Readability for nonspecialists**: The manuscript is well-written and accessible. The authors do an excellent job of explaining complex concepts, such as PSI-BLAST and ancestral sequence reconstruction, in a way that is understandable to a broad audience. The figures are informative, though Figure 2 could be improved as noted above.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a novel and potentially important finding, but the central claims are not yet fully established from the provided evidence. The authors must address the concerns regarding AlphaFold2 circularity, homologous overextension, and statistical rigor before the case for a covert evolutionary pathway is convincing. Experimental validation of at least one ancestral protein's structure would greatly strengthen the argument. I recommend major revision with the expectation that the authors can address these concerns.

## Risk / unsupported claims
- The claim that "all lines of evidence consistently point to an evolutionary trajectory" is not fully supported, as the AlphaFold2 predictions may be biased and the bridge clade is small.
- The claim that the structural transformation "likely expanded DNA-binding specificity" is unsupported by direct experimental evidence and is based on a small, non-statistically tested sample.
- The claim that the use of full-length sequences is "necessary" to identify the relationship is not rigorously demonstrated, as the possibility of homologous overextension is not fully excluded.
- The generalizability of the proposed step-by-step guide to other protein families is asserted but not demonstrated with examples beyond the response regulator family.