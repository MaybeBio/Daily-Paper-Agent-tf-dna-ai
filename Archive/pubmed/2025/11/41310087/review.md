## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) without supplementary datasets or source data files
- **Assessment boundary** Scientific claims, methodological soundness, and interpretive validity as presented in the main text and referenced figures/tables; no assessment of supplementary files beyond what is described
- **Shared manuscript claim summary** The authors use AlphaFold-guided structural phylogenetics across hundreds of metazoan species to argue that ORC6, a subunit of the origin recognition complex previously thought essential for origin licensing, has been lost independently in multiple metazoan lineages. They further claim that the ORC3 tether, which supports an ORC6-independent MCM loading pathway, is broadly conserved even in ORC6-negative species, suggesting physiological relevance of ORC6-independent licensing mechanisms and greater heterogeneity in metazoan origin licensing than previously recognized.
- **Visible evidence base** Main text figures (Fig 1-4, EV1-EV5 as described), Table EV1 (referenced), Methods section describing BLAST searches, AlphaFold2 monomer and multimer predictions, multiple sequence alignments, percent identity calculations, and statistical tests
- **Missing materials affecting confidence** Supplementary datasets (EV1-EV3) containing the actual sequence lists, AlphaFold models, and per-species interaction scores; source data files for Figures 2-4; the multiple sequence alignment file; detailed per-species results tables; code scripts for average models score calculation

## Reviewer
- **Overall assessment** This manuscript presents a creative and potentially valuable application of AlphaFold-based structural prediction to a question in evolutionary cell biology. The central observation, that ORC6 has been lost in multiple metazoan lineages while the ORC3 tether remains broadly conserved, is interesting and could have implications for understanding the diversity of DNA replication initiation mechanisms. However, the manuscript as presented has several significant limitations that prevent full evaluation of the claims. The reliance on computational predictions without experimental validation, the potential circularity in using AlphaFold to assess conservation of a binding interface that AlphaFold itself may not predict well, and the absence of key methodological details and supplementary data make it difficult to assess the robustness of the conclusions. The phylogenetic sampling strategy and the criteria for defining "loss" of ORC6 require more careful justification. The interpretive leap from sequence/structure conservation to physiological relevance is substantial and not fully supported by the data presented.

- **Who would be interested in the results, and why** Researchers studying DNA replication initiation mechanisms, particularly those interested in the evolutionary diversity of origin licensing across eukaryotes. The work also speaks to the broader community using AlphaFold for evolutionary analyses, as it demonstrates a novel application of structural prediction to questions of protein interaction conservation. Cell cycle biologists and those studying Meier-Gorlin syndrome may find the evolutionary context of ORC6 function relevant. The methodological approach may interest computational biologists developing tools for large-scale interaction prediction.

- **Major strengths** 
  1. The question addressed is significant: whether the multiple MCM double hexamer loading pathways identified in human cells are evolutionarily conserved or represent lineage-specific adaptations.
  2. The application of AlphaFold to phylogenetic questions is creative and timely, demonstrating a novel use of structural prediction beyond traditional structure determination.
  3. The observation of convergent ORC6 loss across multiple metazoan lineages is striking and potentially important.
  4. The authors appropriately acknowledge limitations of their approach, including the possibility of undetected divergent ORC6 orthologs and the known limitations of AlphaFold for flexible regions.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that ORC6 has been "lost" in multiple metazoan lineages based on BLAST searches failing to identify orthologs.
- **Evidence pointer** Results section "Multiple metazoan taxonomic groups lack ORC6"; Figure 1C; Table EV1; Methods "ORC1-6 ortholog search"
- **Concern** The inference of gene loss from negative BLAST results is problematic. The authors used human ORC6 as the query sequence for all searches. Given that ORC6 is the most divergent ORC subunit, with a distinct lineage from ORC1-5 and sharing homology with TFIIB, it is plausible that highly divergent ORC6 orthologs exist in these lineages but are undetectable by standard BLAST searches against the human sequence. The authors mention that DELTA-BLAST was used for increased sensitivity and could detect yeast ORC6, but this does not establish that the method would detect all possible divergent ORC6 orthologs across the full diversity of Metazoa. The manuscript does not report reciprocal searches, profile-based searches (e.g., HMMER against Pfam or eggNOG), or synteny-based approaches that would strengthen the gene loss inference. The distinction between true gene loss and sequence divergence below detection threshold is critical for the central claim of the paper.
- **Why it matters** The entire premise of the paper rests on the correct identification of ORC6-negative species. If some of these species actually possess highly divergent ORC6 orthologs, the conclusion about convergent gene loss and the physiological relevance of ORC6-independent licensing would be substantially weakened.
- **Resolution test** The authors should provide evidence from multiple search strategies (e.g., profile HMMs, hidden Markov model searches, synteny analysis where possible) that ORC6 is genuinely absent from these lineages. They should also report the search sensitivity for known divergent ORC6 orthologs and provide the full list of species examined with their search results in the supplementary data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors use AlphaFold2 Multimer predictions to assess conservation of ORC3-ORC6 and ORC3-MCM2 interactions across species, concluding that ORC3-ORC6 interactions are lost in ORC6-negative species while ORC3-MCM2 interactions are conserved.
- **Evidence pointer** Results sections "Degeneracy of the ORC6-binding domain disrupts in silico ORC3-ORC6 interactions" and "The ORC3 tether is conserved across Metazoa for ORC6-independent MCM loading"; Figures 3 and 4; Methods "AlphaFold2 predictions"
- **Concern** The use of AlphaFold2 Multimer to assess interaction conservation has inherent limitations that are not fully addressed. First, AlphaFold2 Multimer is known to have variable performance depending on the protein pair and may produce false negatives for weak or transient interactions. The ORC3-ORC6 interaction in humans is described as low affinity, and the authors themselves note that ORC6 is loosely associated in human and Xenopus. Using AlphaFold to assess conservation of a weak interaction is methodologically risky. Second, the authors use human ORC6 as the binding partner for all cross-species predictions with ORC3 from ORC6-negative species. This is a reasonable approach given the lack of native ORC6, but it introduces potential artifacts: the human ORC6 may not fold or interact properly with highly divergent ORC3 orthologs, and the absence of predicted interaction could reflect incompatibility of the cross-species pair rather than true loss of interaction capability. Third, the average models score threshold of 0.5 is described as previously established, but the manuscript does not provide validation of this threshold for the specific types of interactions being tested. The authors should provide more detailed validation of their approach, including positive and negative controls, and should discuss the limitations of using cross-species pairs.
- **Why it matters** The conclusion that ORC6-negative species have nonfunctional ORC6 binding sites in ORC3 depends on the reliability of AlphaFold2 Multimer predictions. If the method produces false negatives for cross-species pairs, the conclusion would be incorrect. Similarly, the claim that ORC3-MCM2 interactions are conserved relies on the same methodology.
- **Resolution test** The authors should provide validation of their AlphaFold2 Multimer approach, including benchmarking against known interacting and non-interacting pairs, assessment of false negative rates for weak interactions, and ideally experimental validation for at least one ORC6-negative species (e.g., C. elegans) showing that ORC3 cannot bind ORC6. They should also report the distribution of average models scores more completely, not just medians, to show the separation between confident and non-confident predictions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors claim that their findings "argue that ORC6-independent origin licensing occurs naturally in physiological environments" and that "origin licensing mechanisms in multicellular eukaryotes are more diverse and adaptable than previously recognized."
- **Evidence pointer** Discussion section; Abstract
- **Concern** The leap from computational predictions of sequence and structure conservation to claims about physiological relevance is substantial and not adequately supported. The authors show that ORC6 has been lost in some lineages and that the ORC3 tether is conserved, but they do not provide any direct evidence that ORC6-independent licensing actually occurs in these organisms. The in vitro biochemical data from human cells showing an ORC6-independent pathway (MO-II) does not establish that this pathway is physiologically relevant in any organism, let alone in the diverse lineages where ORC6 is absent. The authors acknowledge this limitation in their discussion of future work, but the abstract and title present the conclusion more strongly than the evidence warrants. The title states "surprising heterogeneity in metazoan replication origin licensing mechanisms" as if this heterogeneity is established, when the data only show heterogeneity in the presence/absence of a protein and its binding site, not in the mechanisms themselves.
- **Why it matters** The significance of the paper depends on the claim that ORC6-independent licensing is a real, physiologically relevant mechanism in diverse species. If the authors are only showing sequence-level variation without functional evidence, the importance of the work is considerably reduced.
- **Resolution test** The authors should temper their conclusions to match the evidence, clearly distinguishing between computational predictions and experimentally validated mechanisms. Alternatively, they could provide additional evidence, such as experimental validation in at least one ORC6-negative species, to support the physiological relevance claim.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "there is no significant difference in the average pLDDT score between ORC3 orthologs from species with and without ORC6" (Figure 2C), supporting the reliability of their models across both groups.
- **Evidence pointer** Results section "Loss of ORC6 correlates with poor conservation of the ORC6-binding region in ORC3"; Figure 2C; Methods "Statistical analysis"
- **Concern** The statistical comparison of pLDDT scores between groups addresses overall model quality but does not address the specific reliability of the ORC6-BD region in ORC6-negative species. The authors note that pLDDT scores for the ORC6-BD region are lower in ORC6-negative species (median just above 70), but they do not report whether this difference is statistically significant or whether the lower confidence in this specific region affects their conclusions about structural degeneration. A median pLDDT of approximately 70 is at the threshold for reliable backbone prediction, and individual models may have substantially lower confidence in this region. The authors should report the distribution of pLDDT scores specifically for the ORC6-BD region, not just the overall model quality, and should discuss how lower confidence in this region affects their interpretation of structural degeneration.
- **Why it matters** The claim that the ORC6-BD is structurally degenerate in ORC6-negative species depends on the reliability of the predicted structures in this specific region. If the lower pLDDT scores indicate unreliable predictions rather than true structural degeneration, the conclusion would be weakened.
- **Resolution test** The authors should report pLDDT scores specifically for the ORC6-BD region, compare these between groups statistically, and discuss the implications of lower confidence in this region for their structural interpretations. They should also consider whether alternative approaches (e.g., AlphaFold3, or experimental structure determination for at least one representative species) would strengthen their conclusions.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and reproducibility
- **Affected element** Methods section "AlphaFold2 predictions"
- **Evidence pointer** Methods; no specific figure/table
- **Issue** The description of the AlphaFold2 prediction parameters is incomplete. The authors state they used AlphaFold v2.3.2 with max_template_date=2021-11-01 and the monomer_ptm model, but do not specify the number of recycles, whether early stopping was used, the MSA depth, or other key parameters that can affect prediction quality. For the multimer predictions, they reference the preprint by Evans et al. but do not specify whether they used the default multimer settings or made modifications.
- **Required correction** Provide a complete description of all AlphaFold2 parameters used, including any non-default settings, and specify the version of ColabFold or the local installation used. This is essential for reproducibility of the computational predictions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Supplementary datasets EV1-EV3
- **Evidence pointer** Methods; Supplementary information
- **Issue** The manuscript references three supplementary datasets (EV1-EV3) containing the sequence lists and AlphaFold prediction results, but these are not provided with the manuscript for review. Without access to these datasets, it is impossible to verify the completeness of the taxonomic sampling, the criteria used for species inclusion, or the per-species results that support the summary statistics presented in the figures.
- **Required correction** Ensure that all supplementary datasets are provided with the manuscript submission and are accessible to reviewers. Consider also providing a summary table of all species included in the analysis with their taxonomic classification and key results (ORC6 presence/absence, ORC6-BD conservation status, ORC3-MCM2 interaction score) as a main text or extended data table.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretive caution
- **Affected element** Discussion section, paragraph on rotifers
- **Evidence pointer** Discussion; no specific figure/table
- **Issue** The discussion of rotifers as "particularly intriguing" because they lack both ORC6 and the ORC3 tether is speculative. The authors suggest that rotifers may possess "alternative mechanisms to direct MCM loading orientation," but provide no evidence or specific hypotheses about what these mechanisms might be. While speculation is appropriate in a discussion section, the framing here implies that the absence of ORC6 and the ORC3 tether in rotifers is well-established, when it is based on the same BLAST-based inference that may have false negatives.
- **Required correction** Soften the language around rotifers and acknowledge more explicitly that the apparent absence of both ORC6 and the ORC3 tether could reflect limitations of the detection methods rather than true absence. Consider discussing alternative explanations, such as the presence of highly divergent functional analogs.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 1C and Figure 4F
- **Evidence pointer** Figure 1C; Figure 4F
- **Issue** The phylogenetic trees in Figures 1C and 4F are described as based on "widely accepted metazoan phylogeny" with "arbitrary" branch distances. While this is appropriate for schematic representation, the figures would benefit from clearer labeling of which branches represent ORC6-positive versus ORC6-negative taxa, and the number of species sampled per branch. Currently, the reader cannot assess the density of sampling or the confidence in the phylogenetic placement of the losses.
- **Required correction** Consider adding species counts to each branch of the phylogenetic trees, and use clearer visual distinction (e.g., colored branches or symbols) to indicate ORC6 presence/absence. This would improve the readability and informational content of these key figures.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods section "Identification of conserved or non-conserved ORC6 binding domains and ORC3 tethers in ORC3 AlphaFold models"
- **Evidence pointer** Methods; no specific figure/table
- **Issue** The criteria for classifying ORC6-BD as "conserved" or "non-conserved" are described only as manual inspection of structural superpositions. This is inherently subjective and may not be reproducible by other researchers. The authors do not provide quantitative criteria (e.g., RMSD thresholds, presence of specific secondary structure elements, or sequence identity cutoffs) for their classifications.
- **Required correction** Provide more objective and quantitative criteria for classifying ORC6-BD conservation. This could include specific structural metrics (e.g., Cα RMSD over the ORC6-BD region), or a decision tree based on the presence/absence of the three canonical α-helices with clear definitions. Ideally, the classification should be reproducible by an independent researcher.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction; Discussion
- **Issue** The manuscript would benefit from a more thorough discussion of previous work on ORC6 conservation and divergence across eukaryotes. The authors mention that ORC6 has a distinct lineage and is loosely associated in some species, but do not cite or discuss the full range of prior studies on ORC6 evolution, including work on trypanosomes and other divergent eukaryotes that have unusual ORC configurations. This context would strengthen the framing of the current findings.
- **Required correction** Expand the introduction and/or discussion to include a more comprehensive review of what is known about ORC6 and ORC subunit evolution across eukaryotes, including non-metazoan lineages. This would help position the current findings within the broader evolutionary context.

## Risk / unsupported claims
- The claim that ORC6 has been "lost" in multiple metazoan lineages is based solely on BLAST-based detection and may include false negatives due to sequence divergence. This is acknowledged in the discussion but the strength of the claim in the abstract and title is not fully matched by the evidence.
- The claim that ORC6-independent MCM loading "occurs naturally in physiological environments" is not directly supported by any experimental data. The authors provide computational evidence for conservation of the ORC3 tether and loss of ORC6, but do not demonstrate that the proposed mechanism actually functions in any ORC6-negative species.
- The use of AlphaFold2 Multimer with human ORC6 as a cross-species binding partner for ORC3 from ORC6-negative species may produce artifacts. The absence of predicted interaction in these cross-species pairs is interpreted as evidence of nonfunctional ORC6 binding sites, but could also reflect incompatibility of the cross-species protein pair.
- The classification of ORC6-BD as "conserved" or "non-conserved" based on manual structural inspection is subjective and not quantitatively defined, making the results difficult to reproduce or verify.
- The statement that "all three human MCM loading mechanisms are broadly conserved across Metazoa" (Discussion) is an extrapolation beyond the data, which only directly address conservation of ORC6 and the ORC3 tether, not the full set of molecular interactions involved in each pathway.
- The phylogenetic trees presented in Figures 1C and 4F are schematic with arbitrary branch distances, and the density of taxonomic sampling per branch is not indicated, limiting the ability to assess the robustness of the inferred evolutionary patterns.