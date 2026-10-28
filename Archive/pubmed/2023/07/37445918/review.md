## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results and discussion, methods)
- **Assessment boundary** Bioinformatics analyses, structural predictions, phylogenetic conservation, and proposed functional model for a putative Z-DNA binding domain (Zτ) in topoisomerase IIα
- **Shared manuscript claim summary** The authors propose that topoisomerase IIα contains a phylogenetically conserved winged-helix domain (Zτ) that is structurally similar to the canonical Zα domain of ADAR1, binds left-handed Z-DNA with very high affinity, is flanked by a GTP-binding site, and that this domain enables novel functions including a putative "conformase" activity that converts B-DNA to Z-DNA at specific genomic loci
- **Visible evidence base** Sequence alignments, structural similarity scores (RMSD, p-values from FATCAT), NSitePred binding predictions, SNP enrichment analysis, molecular docking scores, and a proposed mechanistic scheme (Figure 9)
- **Missing materials affecting confidence** Figures 1-9 are referenced but not provided; Supplementary Files S1-S6 are referenced but not provided; experimental validation data (biochemical binding assays, mutagenesis, functional studies) are absent; raw docking scores and statistical details are not fully reported in the text

## Reviewer
- **Overall assessment** This manuscript presents an intriguing bioinformatics-driven hypothesis that topoisomerase IIα contains a previously unrecognized Z-DNA binding domain (Zτ) with high affinity for left-handed DNA, and that this domain may confer novel cellular functions beyond canonical topoisomerase activity. The phylogenetic conservation analysis across diverse taxa is a strength, and the integration of prior biochemical data with new computational predictions is thoughtful. However, the central claims rest entirely on computational predictions without any experimental validation. The structural similarity to Zα is modest (low sequence identity, moderate RMSD), the docking results are described as "illustrative yet inconclusive" by the authors themselves, and the proposed "conformase" activity is purely speculative. The manuscript would be substantially strengthened by experimental evidence demonstrating Zτ-Z-DNA binding, GTP effects on binding, and functional consequences in cells.

- **Who would be interested in the results, and why** Researchers studying Z-DNA biology, non-B DNA structures, and their interaction with nuclear proteins would find the identification of a putative Z-DNA binding domain in topoisomerase IIα of interest. The proposed link between Z-DNA recognition and chromosome dynamics during mitosis could attract cell biologists studying chromosome condensation and segregation. Additionally, the potential implications for cancer therapy, given that topoisomerase II is a major drug target, may interest pharmacologists and oncologists. The phylogenetic analysis across the tree of life could appeal to evolutionary biologists studying conservation of DNA structure recognition mechanisms.

- **Major strengths** 1) The phylogenetic conservation analysis is comprehensive, examining nearly 1500 sequences across diverse taxa and demonstrating conservation of the Zτ domain and GTP-binding site. 2) The integration of prior experimental data (Table 1) with new computational predictions provides a coherent narrative. 3) The identification of deleterious SNPs within the predicted functional regions adds translational relevance. 4) The proposed mechanistic scheme (Figure 9) is creative and generates testable hypotheses. 5) The authors acknowledge limitations of their computational approach in several places.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The manuscript claims that Zτ constitutes a "putative structural homolog of Zα" and that topoII exhibits "very high affinity for left-handed Z-DNA" based on the Zτ domain
  - **Evidence pointer** Section 2.1, Table 2, Figure 4
  - **Concern** The structural similarity between Zτ and Zα is supported only by computational predictions. The sequence identity is reported as very low (<10%) in all pairwise comparisons, and the RMSD of 2.4 Å with 64 equivalent positions, while statistically significant, does not establish functional equivalence. The authors themselves note the docking results are "illustrative yet inconclusive." No experimental data (e.g., electrophoretic mobility shift assays, isothermal titration calorimetry, surface plasmon resonance) are provided to demonstrate that Zτ actually binds Z-DNA with high affinity.
  - **Why it matters** The central thesis of the manuscript rests on the claim that topoII is a bona fide Z-DNA binding protein through the Zτ domain. Without experimental validation of Zτ-Z-DNA binding, the entire framework of the "B-Z-TopoII" hypothesis lacks empirical support. The prior biochemical data from 30 years ago (Table 1) were obtained with full-length topoII and do not specifically implicate Zτ.
  - **Resolution test** Provide experimental evidence of Zτ-Z-DNA binding using purified recombinant Zτ domain (e.g., EMSA, ITC, or SPR). Demonstrate that mutations in key Zτ residues abolish or reduce Z-DNA binding. Show that the full-length topoII protein binds Z-DNA through the Zτ domain specifically.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Functional significance
  - **Claim pointer** The manuscript proposes that topoII exhibits a "single-turnover 'conformase' activity" that converts B-DNA to Z-DNA at specific loci ("Z-flipins"), and that this activity is essential for chromosome condensation during mitosis
  - **Evidence pointer** Section 2.5, Figure 9, Table 4
  - **Concern** The proposed "conformase" activity is entirely speculative. No experimental evidence is provided for B-to-Z conversion by topoII. The authors cite a study showing that bending alone can promote B-to-Z transitions under physiological conditions, but this does not demonstrate that topoII catalyzes such transitions. The claim that this activity is "essential" for mitosis is unsupported by any functional data.
  - **Why it matters** The conformase hypothesis represents a major conceptual advance beyond the established topoisomerase function. If incorrect, it could misdirect future research. The manuscript presents this as a plausible mechanism without adequate caveats about its speculative nature, and the word "essential" overstates the evidence.
  - **Resolution test** Provide experimental evidence for B-to-Z conversion by topoII using in vitro assays (e.g., circular dichroism, 2D gel electrophoresis of plasmid DNA with Z-forming sequences). Demonstrate that topoII mutants lacking Zτ or with disrupted Zτ cannot promote B-to-Z transitions. Show that Z-flipin sequences are required for proper chromosome condensation in vivo.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical rigor
  - **Claim pointer** The manuscript claims that a "very significant GTP-binding site" exists in topoII and that GTP binding "dramatically increases" Z-DNA affinity while inhibiting topoisomerase activity
  - **Evidence pointer** Section 2.2, Figure 5C, Supplementary File S2
  - **Concern** The GTP-binding site prediction relies solely on the NSitePred tool, which is a sequence-based predictor. The authors do not validate this prediction with structural analysis, mutagenesis, or direct binding assays. The claim that GTP dramatically increases Z-DNA affinity is based on the 30-year-old biochemical data (Table 1), but the connection between the predicted GTP site and the observed biochemical effects is not established. The proximity of the predicted GTP site to the Zτ domain is noted but not functionally demonstrated.
  - **Why it matters** The GTP regulation of Z-DNA binding is a key component of the proposed mechanism. If the GTP-binding site prediction is incorrect or the GTP effect is not mediated through this site, the mechanistic model would need substantial revision. The manuscript does not adequately distinguish between the predicted site and the experimentally observed GTP effects.
  - **Resolution test** Mutate key residues in the predicted GTP-binding site and test effects on GTP binding (e.g., using fluorescent GTP analogs) and on Z-DNA affinity. Determine the crystal structure of topoII with bound GTP to confirm the binding site. Test whether GTP hydrolysis is required for the observed effects.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretive caution
  - **Claim pointer** The manuscript states that the Zτ domain is "phylogenetically conserved across the tree of life" and implies functional importance based on this conservation
  - **Evidence pointer** Section 2.3, Figures 6-7
  - **Concern** The conservation analysis is described but the actual alignment data are not shown in the text provided. The authors state that nearly 1500 sequences were inspected and 1131 were used, but the criteria for inclusion/exclusion and the statistical significance of the conservation are not fully described. The claim of conservation "across the tree of life" may be overstated if the analysis is primarily focused on metazoans (as suggested by the mention of "all known metazoan topoisomerases").
  - **Why it matters** Evolutionary conservation is often used as evidence of functional importance. If the conservation analysis is not rigorously presented or is limited in taxonomic scope, the strength of this argument is diminished. The manuscript should clarify the taxonomic distribution and provide quantitative measures of conservation.
  - **Resolution test** Provide the full alignment data or a clear visualization showing conservation across diverse phyla. Report quantitative conservation scores (e.g., ConSurf, conservation indices) for Zτ residues. Clarify the taxonomic sampling and discuss any lineages where Zτ is absent or divergent.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Terminology
  - **Evidence pointer** Section 2.5, Figure 9
  - **Issue** The term "conformase" is introduced without clear definition or precedent in the literature. The distinction between "Z-flipons" (pre-existing Z-DNA forming sequences) and "Z-flipins" (sequences converted by topoII) may confuse readers.
  - **Required correction** Define "conformase" explicitly and discuss its relationship to existing concepts such as "flipase" or "helicase." Provide a clear operational definition of Z-flipins and how they differ experimentally from Z-flipons.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods detail
  - **Evidence pointer** Section 3.5
  - **Issue** The molecular docking procedure is described briefly. The HDOCK and PATCHDOCK parameters are stated as "default" but the specific scoring functions, number of models generated, and selection criteria for the best models are not described.
  - **Required correction** Provide more detail on docking parameters, including the number of models generated, the scoring function used, and the criteria for selecting representative models. Report the actual docking scores for the interactions shown in Figures 7B and 8.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** SNP enrichment
  - **Evidence pointer** Section 2.2, Supplementary File S1
  - **Issue** The enrichment of deleterious SNPs in the GTP-binding and Zτ regions is mentioned but no statistical test or enrichment analysis is described. The significance of this enrichment is not quantified.
  - **Required correction** Perform and report a statistical test for SNP enrichment (e.g., Fisher's exact test comparing SNP density in these regions versus the rest of the protein). Report odds ratios and confidence intervals.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Discussion of prior work
  - **Evidence pointer** Section 2.6
  - **Issue** The discussion of mitosis and topoII function would benefit from more explicit engagement with recent structural studies of topoII-DNA complexes and the role of the WHD in DNA binding and cleavage.
  - **Required correction** Cite and discuss recent high-resolution structures of topoII-DNA complexes to contextualize the proposed Zτ domain within the known architecture of the enzyme.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Figure accessibility
  - **Affected element** Figures
  - **Evidence pointer** Figures 1-9
  - **Issue** The figures are referenced extensively but not provided in the manuscript text. Without seeing the figures, it is difficult to assess the quality of the structural alignments, docking models, and conservation data.
  - **Required correction** Ensure all figures are included in the final submission with clear legends. Consider providing a supplementary figure showing the full multiple sequence alignment with the Zτ region highlighted.

## Risk / unsupported claims
- The claim that Zτ is a "putative structural homolog of Zα" is unsupported by experimental evidence; only computational predictions are provided
- The claim that topoII has "very high affinity" for Z-DNA specifically through Zτ is not directly demonstrated; prior biochemical data used full-length protein
- The proposed "conformase" activity (B-to-Z conversion) is entirely speculative with no experimental support
- The claim that Zτ and the GTP-binding site are "phylogenetically conserved across the tree of life" may be overstated given the apparent focus on metazoans
- The functional significance of the identified deleterious SNPs is inferred but not experimentally validated
- The GTP-mediated regulation of Z-DNA binding and topoisomerase inhibition is based on 30-year-old data and not re-validated in this study
- The docking results are acknowledged by the authors as "illustrative yet inconclusive" and should not be used to support strong claims about binding modes or affinities
- The proposed role of Zτ in mitosis and chromosome condensation is a hypothesis without direct experimental evidence