## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, discussion, data availability, funding, acknowledgements)
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text. No supplementary figures, tables, or raw data were available for review.
- **Shared manuscript claim summary** The authors report that the meiotic chromosome axis protein Hop1 from *Saccharomyces cerevisiae* possesses intrinsic, DNA-independent ATPase activity despite lacking canonical ATP-binding/hydrolysis sequence motifs. Through computational modeling, they identify five residues (K65, N67, N139, R352, R558) as a putative ATP-binding site. Mutations K65A and N67Q abolish ATPase activity, reduce Hop1 binding to Holliday junctions and meiotic chromosomes, and increase meiotic crossover frequency by approximately 1.2-fold without affecting meiotic progression or spore viability.
- **Visible evidence base** Results sections describing ATPase assays (TLC and colorimetric), ATP-binding assays (UV cross-linking), computational modeling (I-TASSER, molecular docking, MD simulations), mutagenesis and biochemical characterization, EMSA and MST binding studies, yeast genetics (spore viability, tetrad analysis, crossover frequency), and ChIP-seq/ChIP-qPCR experiments. Figures referenced: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10. Supplementary figures referenced: S1–S10. Supplementary tables referenced: S1–S10.
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S10) were not provided. Raw kinetic data, statistical details for crossover frequency calculations, ChIP-seq quality metrics, and full experimental replicates were not available. The manuscript text references figures and tables that could not be independently assessed.

## Reviewer
- **Overall assessment** This manuscript presents a novel and potentially significant finding: the meiotic chromosome axis protein Hop1 exhibits intrinsic ATPase activity that appears to regulate crossover frequency. The discovery is unexpected given the absence of canonical ATPase motifs, and the authors employ a commendable multi-pronged approach combining computational prediction with biochemical and genetic validation. However, several technical concerns must be addressed before the central claims are fully established. The quantitative impact on crossover frequency is modest (1.2-fold), and the mechanistic link between ATP hydrolysis, chromosome association, and crossover regulation remains correlative rather than causal. The computational identification of the ATP-binding site, while plausible, requires stronger experimental validation, particularly regarding whether the observed effects are due specifically to loss of ATP hydrolysis versus structural perturbations. The manuscript would benefit from additional experiments to strengthen the mechanistic model and from clearer presentation of quantitative data.
- **Who would be interested in the results, and why** Researchers in the fields of meiosis, chromosome dynamics, DNA repair, and recombination would find these results of interest. The finding that a HORMA domain protein possesses ATPase activity expands the known functional repertoire of this protein family. The potential link between ATP hydrolysis and crossover frequency has implications for understanding the regulation of meiotic recombination, a process fundamental to sexual reproduction and genome stability. The study may also interest biochemists studying non-canonical ATPase mechanisms and computational biologists using structure prediction to identify novel functional sites.
- **Major strengths**
  1. The discovery of ATPase activity in a protein lacking canonical ATPase motifs is novel and unexpected, making a significant contribution to the field.
  2. The multi-pronged approach (computational prediction, biochemical validation, genetic analysis) is comprehensive and mutually reinforcing.
  3. The use of multiple independent assays (TLC, colorimetric, UV cross-linking, ITC, MST, EMSA) strengthens the reliability of the core biochemical findings.
  4. The inclusion of in vivo experiments (meiotic progression, spore viability, crossover frequency, ChIP-seq) extends the relevance beyond in vitro biochemistry.
  5. The authors address the potential concern of contaminating ATPase activity through multiple lines of evidence, including cell-free protein synthesis and immunoprecipitation.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "K65A and N67Q substitutions in the Hop1 N-terminal HORMA domain synergistically abrogated Hop1's ATPase activity" and that this identifies the ATP-binding/hydrolysis site.
- **Evidence pointer** Results sections "The Hop1 putative ATP-binding site is fairly conserved..." and "Amino acid substitutions in the putative ATP-binding site differentially impair Hop1 ATPase activity"; Figures 5, 6, 7
- **Concern** The manuscript does not provide sufficient evidence that the K65A and N67Q mutations specifically disrupt ATP hydrolysis rather than causing global structural destabilization or misfolding. While the authors show similar thermal stability (Figure 5F, G), thermal stability alone does not guarantee that the local structure of the ATP-binding pocket is preserved. The authors should provide additional structural validation, such as circular dichroism spectroscopy, limited proteolysis, or small-angle X-ray scattering, to demonstrate that the mutant proteins are properly folded. Furthermore, the claim of "synergistic" abrogation requires a more rigorous quantitative comparison of single versus double mutant ATPase activities, including statistical analysis of whether the double mutant effect exceeds the sum of single mutant effects.
- **Why it matters** The central conclusion that Hop1 is an ATPase depends on the specificity of the mutations. If the mutations cause global misfolding, the observed loss of ATPase activity could be an artifact rather than evidence of a specific ATP-binding site. This would undermine the primary claim of the manuscript.
- **Resolution test** Provide structural characterization of WT and mutant proteins (e.g., CD spectra, SEC-MALS, or limited proteolysis) demonstrating similar global folding. Perform quantitative ATPase assays with single and double mutants, including statistical comparison (e.g., ANOVA with post-hoc tests) to demonstrate synergistic effects. Ideally, complement with a rescue experiment where ATPase activity is restored by a second-site mutation or by chemical rescue.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "the ATPase activity of Hop1 plays an important role in regulating CO frequency" based on the 1.2-fold increase in crossover frequency in the hop1-K65A,N67Q strain.
- **Evidence pointer** Results section "Loss of Hop1 ATPase activity leads to an enhancement in meiotic CO frequency"; Figure 9; Supplementary Tables S6–S9
- **Concern** The reported increase in crossover frequency is modest (1.2-fold), and the manuscript does not provide sufficient detail on the number of tetrads analyzed, the number of biological replicates, or the statistical methods used to determine significance. The authors state that "the enhancements in map distances were significant at specific genetic intervals" but do not provide effect sizes, confidence intervals, or multiple testing corrections. Additionally, the manuscript does not address whether the increased crossover frequency is accompanied by changes in crossover interference, crossover homeostasis, or the distribution of crossovers along the chromosome. The claim that ATPase activity "regulates" crossover frequency implies a regulatory mechanism, but the data only demonstrate a correlation between reduced ATPase activity and increased crossovers.
- **Why it matters** The biological significance of the finding rests on the robustness of the crossover phenotype. A modest effect that is not rigorously quantified or replicated could be a false positive or a consequence of genetic background effects. Without detailed statistical analysis and additional phenotypic characterization, the claim of a regulatory role is not fully supported.
- **Resolution test** Provide complete tetrad data including number of tetrads scored, number of independent biological replicates, and statistical analysis with appropriate multiple testing corrections. Include analysis of crossover interference (e.g., coefficient of coincidence with confidence intervals) and crossover distribution. Ideally, complement with an independent assay for crossover frequency (e.g., Southern blot analysis of recombination intermediates or pulsed-field gel electrophoresis) to confirm the genetic data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that "the Hop1K65A,N67Q variant displayed significantly reduced affinity for the HJ and meiotic chromosomes, while enhancing the frequency of COs" and suggest that reduced chromosome association may contribute to increased crossover frequency.
- **Evidence pointer** Results sections "Substitutions of amino acids in the ATPase domain impact the HJ binding affinity of Hop1" and "ChIP-seq analyses show reduced binding of the Hop1K65A,N67Q variant to meiotic chromosomes"; Figures 8, 10
- **Concern** The mechanistic link between reduced DNA/chromosome binding and increased crossover frequency is not established. The authors propose that reduced Hop1 binding may lead to increased crossovers, but this is counterintuitive given that Hop1 is generally considered a positive regulator of meiotic recombination. The manuscript does not address how reduced Hop1 association with chromosomes could enhance crossover formation. Alternative explanations, such as altered protein-protein interactions, changes in post-translational modifications, or effects on downstream recombination mediators, are not explored. The ChIP-seq data show reduced binding but do not establish causality.
- **Why it matters** The proposed model that reduced chromosome association leads to increased crossover frequency is not mechanistically explained. Without a clear model, the biological significance of the ATPase activity remains unclear. The field would benefit from a more detailed understanding of how ATP hydrolysis by Hop1 influences its function in meiotic recombination.
- **Resolution test** Perform additional experiments to dissect the mechanism, such as examining the interaction of Hop1K65A,N67Q with known binding partners (e.g., Red1, Mek1) by co-immunoprecipitation, analyzing post-translational modifications of the mutant protein, or measuring crossover-associated events (e.g., double Holliday junction intermediates) in the mutant strain. Alternatively, the authors could test whether the increased crossover frequency is dependent on the ZMM pathway or the STR complex by combining the hop1-K65A,N67Q mutation with mutations in these pathways.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "Hop1 possesses robust DNA-independent ATPase activity" and that this activity is intrinsic to Hop1.
- **Evidence pointer** Results section "Discovery of Hop1 ATPase activity"; Figure 1; Supplementary Figure S1
- **Concern** While the authors provide several lines of evidence to exclude contaminating ATPase activity, the manuscript does not address the possibility that the ATPase activity could be due to a co-purifying protein that is not detected by SDS-PAGE or western blotting. The cell-free synthesis experiment is reassuring, but the authors do not provide quantitative data on the specific activity of the cell-free synthesized protein compared to the recombinant protein. Additionally, the manuscript does not report the ATPase activity of a catalytically dead mutant (e.g., a mutant with alanine substitutions at all five identified residues) to demonstrate that the activity is specifically attributable to the identified site.
- **Why it matters** The claim of intrinsic ATPase activity is foundational to the entire manuscript. If the activity is due to a contaminant, all subsequent conclusions are invalid. A catalytically dead mutant would provide the strongest evidence that the activity is intrinsic to Hop1.
- **Resolution test** Generate a mutant with alanine substitutions at all five identified residues (K65A, N67A, N139A, R352A, R358A) and demonstrate complete loss of ATPase activity. Additionally, perform a more rigorous contamination check, such as mass spectrometry analysis of the purified protein preparation to identify any co-purifying proteins.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "molecular docking combined with molecular dynamics simulations and biochemical assays" identified the ATP-binding site, and that the site is "fairly conserved across different species from diverse fungal lineages."
- **Evidence pointer** Results sections "Computational tools predict the existence of a putative ATP-binding site in Hop1" and "The Hop1 putative ATP-binding site is fairly conserved..."; Figure 4; Supplementary Figure S6
- **Concern** The computational identification of the ATP-binding site relies on a homology model with low confidence scores, as the authors acknowledge that "a partial structure was modeled, which had low confidence scores." The molecular docking results are presented without quantitative metrics (e.g., docking scores, binding free energies, or comparison to known ATP-binding proteins). The conservation analysis is limited to fungal species and does not include more divergent orthologs, which would provide stronger evidence for functional importance. The manuscript does not provide experimental validation of the predicted binding site beyond the mutagenesis data, which could be confounded by structural effects.
- **Why it matters** The identification of the ATP-binding site is a key contribution of the manuscript. If the computational predictions are not robust, the subsequent mutagenesis and functional studies may be targeting the wrong residues. The field would benefit from a more rigorous computational and experimental validation of the ATP-binding site.
- **Resolution test** Provide quantitative docking scores and binding free energy calculations for ATP binding to the predicted site. Include a comparison with known ATP-binding proteins to validate the docking approach. Expand the conservation analysis to include more divergent species. Ideally, obtain a crystal structure or cryo-EM structure of Hop1 with bound ATP to definitively identify the binding site.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract; Introduction paragraphs 1–3
- **Issue** The abstract and introduction assume significant prior knowledge of meiosis and recombination. Terms such as "HORMA domain," "interhomolog bias," and "ZMM proteins" are used without definition or brief explanation. The significance of the finding for a broader audience is not clearly articulated.
- **Required correction** Provide brief definitions or explanations of key terms in the introduction. Add a sentence in the abstract or introduction that explicitly states why the finding is important beyond the immediate field of meiosis research.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "Isothermal titration colorimetry"
- **Evidence pointer** Methods section "Isothermal titration colorimetry"
- **Issue** The method is described as "Isothermal titration colorimetry" but the standard term is "Isothermal titration calorimetry" (ITC). The typo appears in the section heading and may reflect a broader issue with proofreading.
- **Required correction** Correct the typo to "Isothermal titration calorimetry" throughout the manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section "ChIP-qPCR analysis"
- **Evidence pointer** Results section "ChIP-qPCR analysis"; Supplementary Figure S10
- **Issue** The authors state that "no enrichment of either WT Hop1 or Hop1K65A,N67Q variant was seen at the chromosome axis (Axis I and Axis III), ECM3 and DSV cold spot YCR093W sites." This is surprising given that Hop1 is a chromosome axis protein. The authors do not provide a possible explanation for this observation or discuss its implications.
- **Required correction** Add a brief discussion of why Hop1 is not enriched at the tested axis sites and whether this is consistent with previous studies. If this is a technical issue (e.g., primer design, chromatin shearing), address it.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph 4
- **Issue** The discussion of the relationship between Hop1 ATPase activity and Pch2 is speculative and not well-supported by the data presented. The authors suggest that Hop1 and Pch2 may have opposing functions but do not provide experimental evidence to support this claim.
- **Required correction** Either provide experimental data to support the proposed relationship between Hop1 and Pch2 or clearly label this as speculation and suggest future experiments to test the hypothesis.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Figure legends
- **Evidence pointer** Figures 1–10 (legends not provided in full)
- **Issue** The figure legends are not provided in the manuscript text, making it difficult to assess the data presented. This is a significant omission for a complete manuscript.
- **Required correction** Ensure that all figure legends are included in the manuscript and provide sufficient detail for readers to understand the experimental design and data presentation without referring to the main text.

## Risk / unsupported claims
- The claim that the identified five residues constitute the ATP-binding site is based on computational predictions with acknowledged low confidence and is not definitively validated experimentally.
- The claim that reduced Hop1 chromosome association causes increased crossover frequency is correlative; no causal mechanism is established.
- The claim that Hop1 ATPase activity "regulates" crossover frequency implies a regulatory role that is not fully supported by the modest 1.2-fold effect.
- The statement that "the ATPase activity of Hop1 plays an important role in regulating CO frequency" is not supported by direct evidence that ATP hydrolysis, rather than other effects of the mutations, is responsible for the phenotype.
- The relationship between Hop1 ATPase activity and Pch2 function is speculative and not experimentally tested.
- The absence of enrichment of Hop1 at chromosome axis sites in ChIP-qPCR is unexplained and may indicate technical issues or a need for additional validation.
- The manuscript claims that Hop1 is a "novel DNA-independent ATPase" but does not provide a thorough comparison with other known non-canonical ATPases to establish novelty.
- The conservation analysis is limited to fungal species and does not establish the functional importance of the identified residues across a broader evolutionary context.
- The kinetic parameters (Km, Vmax, kcat) are reported without clear indication of the number of replicates or statistical error, limiting the reliability of these measurements.
- The claim that "the main surprise was the finding that Hop1 possesses DNA-independent ATPase activity" is presented as a conclusion, but the biological significance of this activity remains unclear without a detailed mechanistic model.