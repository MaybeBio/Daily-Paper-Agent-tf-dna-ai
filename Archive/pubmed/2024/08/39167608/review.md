## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results and discussion, conclusion, and supplementary figure/table references.
- **Assessment boundary** Genetic mapping, candidate gene identification, phylogenetic analysis, protein structure prediction, and computational modeling of protein complexes. No experimental validation of protein interactions or gene function is included.
- **Shared manuscript claim summary** The authors propose that the common bean T gene encodes a seven-bladed β-propeller WD40 repeat (WDR) protein and the Z gene encodes an R2R3 MYB protein. These are proposed to function as components of an MBW (MYB-bHLH-WDR) complex regulating flavonoid biosynthesis and seed coat patterning. Mutant alleles are shown to carry structural alterations predicted to disrupt complex formation or DNA binding.
- **Visible evidence base** Genetic cosegregation data, sequence comparisons, phylogenetic trees, AlphaFold2 and AlphaFold-Multimer structure predictions, PISA interface analysis, and RMSD comparisons with experimental structures.
- **Missing materials affecting confidence** Supplementary figures and tables referenced in the text were not provided. Experimental validation of protein-protein interactions (e.g., yeast two-hybrid, co-immunoprecipitation) is absent. No functional complementation or gene expression data directly linking the candidate genes to the T and Z phenotypes beyond genetic cosegregation.

## Reviewer
- **Overall assessment** This manuscript presents a well-structured candidate gene identification study for two historically important seed coat patterning loci in common bean. The genetic mapping and cosegregation data are convincing, and the phylogenetic analyses appropriately place the candidates within known flavonoid regulatory families. The structural modeling is thorough and represents a useful contribution, particularly the first computational model of a plant MBW complex. However, the central claim that T and Z encode WDR and MYB proteins respectively, while strongly supported by genetic and bioinformatic evidence, is not experimentally validated. The functional significance of the predicted structural differences between wild-type and mutant proteins remains speculative. The manuscript would be strengthened by experimental confirmation of the proposed protein interactions and by functional assays demonstrating that the candidate genes rescue or recapitulate the expected phenotypes.
- **Who would be interested in the results, and why** Researchers studying flavonoid biosynthesis regulation, particularly those interested in MBW complex evolution and function across plant species. The work also has relevance for common bean breeding programs targeting seed coat color and patterning traits, as the identified candidate genes and associated markers could be used for marker-assisted selection. The structural modeling approach may interest computational biologists working on protein complex prediction.
- **Major strengths** The genetic mapping approach is rigorous, using multiple populations and cosegregation analysis. The candidate gene identification is well supported by phylogenetic analysis and sequence conservation. The structural modeling is comprehensive, including monomer predictions, complex assembly, and analysis of mutant variants. The comparison with experimental crystal structures provides validation for the modeling approach. The identification of a potential β-MoRF in the MYB protein is a novel observation with potential broader significance.
- **Major Concerns** The lack of experimental validation for the proposed protein interactions and functions is the most significant weakness. The manuscript relies entirely on computational predictions and genetic correlation, which, while suggestive, do not establish causality. The functional significance of the predicted structural changes in mutant proteins is not tested. The population genetics analysis of allele frequencies is limited and does not address whether the identified variants are actually responsible for phenotypic variation in diverse germplasm.
- **Minor Comments** The manuscript would benefit from clearer presentation of the genetic mapping data, including recombination events and LOD scores. The description of the P bHLH homodimer modeling is somewhat confusing, particularly the discussion of symmetry axes. Some figures are referenced but not described in sufficient detail in the text. The conclusion section overstates the significance of the findings given the lack of experimental validation.
- **Technical failings that need to be addressed before the case is established** The absence of any experimental validation of protein-protein interactions or DNA binding activity is a critical gap. The claim that the identified mutations are causative for the T and Z phenotypes requires functional complementation or gene editing experiments. The predicted structural differences between wild-type and mutant proteins need to be confirmed experimentally.
- **Assessment against Nature-style criteria** Originality: Moderate. The application of AlphaFold2 to model a plant MBW complex is novel, and the identification of a potential β-MoRF is original. However, the overall approach of candidate gene identification through mapping and phylogenetics is well established. Scientific importance: Moderate. The work provides useful information for common bean genetics and contributes to understanding MBW complex evolution, but the lack of functional validation limits its broader impact. Interdisciplinary readership: Limited. The manuscript is primarily of interest to plant geneticists and molecular biologists. Technical soundness: Generally sound for the computational and genetic analyses, but the lack of experimental validation is a significant technical gap. Readability for nonspecialists: The manuscript is clearly written but assumes familiarity with plant genetics and protein structure concepts.
- **Recommendation posture** Supportive if technical concerns are resolved. The genetic and bioinformatic evidence is strong, but the manuscript requires experimental validation of the proposed protein interactions and functions before the central claims can be fully established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation
- **Claim pointer** The authors claim that T encodes a WDR protein and Z encodes an R2R3 MYB protein that function as components of an MBW complex regulating flavonoid biosynthesis.
- **Evidence pointer** Results and discussion, sections "Identifying T and Z candidate genes" and "Protein modeling of T, Z, and P"; location not provided
- **Concern** The manuscript provides no experimental evidence that the candidate genes actually function as proposed. All evidence is genetic (cosegregation) or computational (phylogeny, structure prediction). No complementation tests, gene silencing, overexpression, or protein interaction assays are presented.
- **Why it matters** Genetic cosegregation and sequence similarity are necessary but not sufficient to establish gene function. Many candidate genes identified by mapping fail to show the expected function when tested experimentally. The central claim of the manuscript depends on functional validation.
- **Resolution test** Provide experimental evidence such as: (1) complementation of the tt or zz phenotype with the wild-type candidate gene, (2) CRISPR-mediated knockout or silencing showing loss of function, or (3) yeast two-hybrid or co-immunoprecipitation demonstrating physical interaction between Z MYB, P bHLH, and T WDR proteins.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causative variant identification
- **Claim pointer** The authors claim that specific mutations in the T and Z candidate genes (the 39-bp deletion in t65-73, the 1-bp deletion in tEW, and the G315T SNP in zEW) are responsible for the mutant phenotypes.
- **Evidence pointer** Results and discussion, sections "T WDR and z MYB polymorphisms among common bean genotypes" and "Structural prediction for mutant T and Z alleles gene products"; location not provided
- **Concern** The manuscript identifies sequence variants in the candidate genes but does not demonstrate that these variants are causative. The variants are only shown to be associated with the mutant phenotypes through cosegregation. No functional assays link the specific mutations to the observed loss of function.
- **Why it matters** Without demonstrating that the identified mutations are causative, the manuscript cannot exclude the possibility that other linked variants in the same genes or nearby genes are responsible for the phenotypes. This is a common pitfall in candidate gene studies.
- **Resolution test** Perform functional assays comparing wild-type and mutant alleles, such as: (1) expressing the mutant allele in a wild-type background to show dominant-negative effects, (2) complementation with wild-type and mutant versions of the gene, or (3) in vitro DNA binding assays comparing wild-type and mutant MYB proteins.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Structural interpretation
- **Claim pointer** The authors claim that the tEW WDR protein, lacking the sixth and seventh blades of the β-propeller, would have compromised stability and binding surfaces, and that the zEW MYB K105N substitution would disrupt DNA binding.
- **Evidence pointer** Results and discussion, sections "Structural prediction for mutant T and Z alleles gene products" and "Effects of mutant Z MYB and T WDR proteins on common bean MBW complex interactions"; location not provided
- **Concern** The structural predictions for mutant proteins are based solely on AlphaFold2 models. The authors acknowledge that the tEW WDR model predicts an unclosed five-bladed structure with exposed hydrophobic surfaces, which they note could lead to false interfaces. The interpretation of the zEW MYB effect relies on homology to the WER protein, but no direct experimental evidence supports the predicted loss of DNA binding.
- **Why it matters** The manuscript presents these structural predictions as providing "insight into the structure and protein interactions" of the MBW complex. If the predictions are not validated, the conclusions drawn from them are speculative and could be misleading.
- **Resolution test** Validate the structural predictions experimentally, such as: (1) circular dichroism or size-exclusion chromatography to assess protein stability, (2) electrophoretic mobility shift assays to test DNA binding of wild-type and mutant MYB proteins, or (3) mutagenesis of the predicted interface residues followed by interaction assays.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Genetic mapping results
- **Evidence pointer** Results and discussion, section "Genetic analysis of the T and Z genes"; location not provided
- **Issue** The genetic mapping data are described qualitatively but no LOD scores, recombination fractions, or confidence intervals are provided. The number of recombinants and the physical intervals are not clearly stated.
- **Required correction** Provide a table or figure summarizing the mapping data, including marker names, genetic distances, LOD scores, and the number of recombinants observed in each population.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** P bHLM homodimer modeling section
- **Evidence pointer** Results and discussion, section "Modeling of the P bHLM homodimer and Z MYB/P bHLM heterodimer"; location not provided
- **Issue** The discussion of the P bHLM homodimer is confusing, particularly the statement that "the large disordered regions between each of the dimer interfaces do not structurally predicate that there is a single global axis, but more likely, three individual local 2-fold symmetry axes." This is difficult to follow and the significance is unclear.
- **Required correction** Clarify the description of the homodimer modeling, perhaps with a simplified diagram or a more explicit explanation of the limitations of the symmetry assumption.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Use of "conversed" in the conclusion
- **Evidence pointer** Conclusion, final paragraph; location not provided
- **Issue** The word "conversed" appears to be a typographical error for "conserved" in the sentence "complex structure is not entirely conversed, and phenotypic function is plastic relative to complex structure."
- **Required correction** Correct the typographical error to "conserved."

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion of MBW complex structural diversity
- **Evidence pointer** Introduction and Discussion; location not provided
- **Issue** The manuscript does not discuss the known structural diversity of MBW complexes across species, particularly the variation in WDR protein blade number or the presence of multiple MYB partners. This context would strengthen the significance of the findings.
- **Required correction** Add a brief discussion of how the proposed bean MBW complex structure compares to known MBW complexes in Arabidopsis, maize, or other species, and what the observed differences might mean functionally.

## Risk / unsupported claims
- The claim that T and Z encode WDR and MYB proteins, respectively, is supported by genetic and bioinformatic evidence but is not experimentally validated.
- The claim that the identified mutations are causative for the mutant phenotypes is not supported by functional assays.
- The claim that the tEW WDR protein would have compromised stability and binding surfaces is based solely on computational prediction and is not experimentally confirmed.
- The claim that the zEW MYB K105N substitution would disrupt DNA binding is inferred from homology and is not experimentally tested.
- The claim that the modeled MBW complex represents the first computational model of a plant MBW complex is plausible but cannot be fully verified without a comprehensive literature search.
- The functional significance of the predicted β-MoRF in the Z MYB protein is speculative and requires experimental validation.