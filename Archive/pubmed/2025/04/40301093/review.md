## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report that the Okinawa spiny rat (Tokudaia muenninki, TMU) carries multiple copies of Sry, all with an alanine-to-serine substitution at position 21 of the HMG box. They claim this substitution is unique among 225 surveyed species, that the encoded proteins retain DNA-binding ability despite slightly reduced affinity relative to mouse SRY, and that Sry expression is absent in adult testis, liver, and brain, leading to the conclusion of a loss of regulatory function.
- **Visible evidence base** Abstract text only; mentions of sequence comparison across 225 species, structural predictions, DNA docking simulations, electrophoretic mobility shift assays, fluorescence anisotropy, and RNA-seq data are described but not shown
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methodological details, sequence alignment data, statistical analyses, raw expression data, and any supplementary information

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting case of Sry evolution in a species with a unique sex chromosome system. The combination of in silico and in vitro approaches is appropriate for a species where experimental samples are scarce. However, the abstract alone does not provide sufficient detail to evaluate the robustness of the key claims, particularly the uniqueness of the substitution, the quantitative comparison of DNA-binding affinity, and the interpretation of absent adult expression as evidence for loss of regulatory function. The conclusion that the intact sequence combined with absent expression indicates loss of regulatory function is plausible but requires careful consideration of alternative explanations, such as developmental-stage-specific expression.
- **Who would be interested in the results, and why** Researchers studying sex determination and sex chromosome evolution, particularly those interested in the degeneration of sex-determining genes and the fate of duplicated gene copies. The work may also appeal to evolutionary biologists studying the molecular mechanisms underlying reproductive isolation and species-specific adaptations, as well as those working on endangered species genomics where functional assays are constrained by sample availability.
- **Major strengths** The study addresses a long-standing question about the functionality of Sry copies in a species with a unique karyotype. The use of multiple complementary approaches (sequence comparison, structural prediction, docking, EMSA, fluorescence anisotropy) strengthens the claim regarding DNA-binding ability. The rarity of the A21S substitution across 225 species is a striking observation that underscores the evolutionary singularity of this system.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1 (uniqueness claim not verifiable from abstract), R1-M2 (quantitative affinity comparison lacks statistical detail), R1-M4 (interpretation of absent adult expression as loss of regulatory function is under-supported)
- **Assessment against Nature-style criteria**  
  Originality: The finding of a unique A21S substitution in the HMG box of Sry in TMU is novel and potentially significant for understanding the evolutionary flexibility of sex-determining genes.  
  Scientific importance: The work contributes to a narrow but active field of sex chromosome evolution; the broader implications for mammalian sex determination are moderate.  
  Interdisciplinary readership: The topic is likely to attract evolutionary biologists, geneticists, and reproductive biologists, but the appeal beyond these fields is limited.  
  Technical soundness: The combination of in silico and in vitro methods is reasonable, but the abstract does not provide enough detail to assess the rigor of the analyses, particularly the structural predictions and binding assays.  
  Readability for nonspecialists: The abstract is generally clear, but terms such as "HMG box" and "neo-sex chromosomes" may require prior knowledge; the logic from binding retention to loss of regulatory function is not fully transparent.
- **Recommendation posture** Supportive if technical concerns are resolved. The core claims are interesting and potentially important, but the abstract alone does not establish the case. Full evaluation of the data, methods, and statistical analyses is required before the conclusions can be accepted.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The authors claim that TMU is the only species with a substitution at the 21st position of the HMG box among 225 species compared.  
- **Evidence pointer** Abstract, "A comparison of SRY sequences from 225 species showed that TMU is the only species with a substitution at the 21st position."  
- **Concern** The abstract states this uniqueness claim without providing any information about the taxonomic representation of the 225 species, the alignment methodology, or the criteria for defining a "substitution" at this position. It is unclear whether the comparison includes closely related species within Muridae or is biased toward particular clades.  
- **Why it matters** The claim of uniqueness is central to the paper's narrative of evolutionary singularity. If the species sample is not phylogenetically representative or if alignment quality is variable, the claim could be overstated.  
- **Resolution test** Provide a supplementary table listing all 225 species, their taxonomic groups, and the amino acid at position 21. Include alignment quality metrics and a phylogenetic tree showing the distribution of the substitution. If possible, confirm the absence of the substitution in additional closely related species.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Quantitative rigor  
- **Claim pointer** The authors claim that DNA-binding ability is retained, although the affinity is slightly lower than that of the mouse homolog.  
- **Evidence pointer** Abstract, "electrophoretic mobility shift assays and fluorescence anisotropy showed that although the affinity was slightly lower than that of the mouse homolog, DNA-binding ability was retained."  
- **Concern** The abstract does not report the magnitude of the affinity difference, the number of replicates, the statistical significance, or the specific DNA sequences used in the binding assays. Without these details, "slightly lower" is not a quantitative claim that can be evaluated.  
- **Why it matters** The conclusion that the A21S substitution does not abolish DNA binding is a key functional claim. If the affinity reduction is substantial or if the assays lack appropriate controls, the interpretation could change.  
- **Resolution test** Report dissociation constants (Kd) with confidence intervals for both TMU and mouse SRY, include at least three independent replicates, and show representative binding curves. State the DNA probe sequences and confirm that they correspond to known SRY target sites.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** Interpretive validity  
- **Claim pointer** The authors state that the complete absence of Sry expression in adult tissues, despite an intact sequence, strongly indicates a loss of regulatory function.  
- **Evidence pointer** Abstract, "Sry expression was not detected in the testis, liver or brain in adult TMU. The complete absence of Sry expression in the adult tissues, despite an intact sequence, strongly indicates a loss of regulatory function."  
- **Concern** The absence of expression in adult tissues does not necessarily indicate loss of regulatory function, as Sry is typically expressed during a narrow developmental window in the embryonic gonad. The abstract does not mention whether embryonic or fetal tissues were examined, nor does it address the possibility that expression occurs only during sex determination.  
- **Why it matters** The conclusion that the gene has lost regulatory function is a strong evolutionary claim. If expression occurs only during development, the gene could still be functional, and the A21S substitution might be compatible with that function.  
- **Resolution test** Provide data on Sry expression during embryonic development, particularly in the genital ridge at the time of sex determination. If such samples are unavailable, explicitly acknowledge this limitation and temper the conclusion accordingly.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The authors imply that the combination of in silico and in vitro analyses provides a coherent picture of Sry function in TMU.  
- **Evidence pointer** Abstract, "we performed in silico and in vitro analyses to investigate the molecular properties and function of SRY using recently obtained whole-genome sequence and RNA-seq data."  
- **Concern** The abstract does not clarify how the RNA-seq data were used beyond the adult expression analysis, nor does it describe the source of the protein used in the binding assays (e.g., recombinant full-length protein or HMG domain only). The relationship between the structural predictions and the experimental binding data is not explained.  
- **Why it matters** The coherence of the evidence chain is essential for the paper's conclusions. If the in vitro assays used only the HMG domain, the relevance to full-length SRY function is limited. If the RNA-seq data are from a single individual or pooled samples, the absence of expression could be a sampling artifact.  
- **Resolution test** Describe the protein constructs used in the binding assays, the source and quality of the RNA-seq data, and how the structural predictions informed the experimental design. Provide details on the number of biological replicates for the expression analysis.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract, first sentence  
- **Evidence pointer** Abstract, "The mammalian sex-determining gene SRY is highly conserved across species, with only a few exceptions."  
- **Issue** The statement is vague regarding what "highly conserved" means in terms of sequence identity or functional conservation, and which exceptions are being referenced.  
- **Required correction** Specify the metric of conservation (e.g., amino acid identity of the HMG domain) and provide one or two examples of known exceptions to contextualize the TMU case.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** Abstract, "neo-sex chromosomes"  
- **Evidence pointer** Abstract, "The Okinawa spiny rat T. muenninki (TMU) acquired neo-sex chromosomes with multiple Sry copies by sex chromosome-autosome fusions."  
- **Issue** The term "neo-sex chromosomes" is used without definition, which may be unclear to readers outside the field of chromosome evolution.  
- **Required correction** Provide a brief parenthetical explanation, such as "chromosomes formed by fusion of ancestral sex chromosomes with autosomes."

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Abstract, final sentence  
- **Evidence pointer** Abstract, "These findings provide insight into the unique evolution of the Sry gene in this species."  
- **Issue** The concluding sentence is generic and does not specify what insight is gained, particularly regarding the evolutionary fate of duplicated Sry copies.  
- **Required correction** Replace with a more specific statement, such as "These findings suggest that the A21S substitution may represent an early step in the degeneration of Sry, with loss of regulatory function preceding loss of DNA-binding ability."

## Risk / unsupported claims
- The claim that TMU is the only species with a substitution at position 21 of the HMG box among 225 species is unsupported in the abstract because the species list, alignment methods, and quality metrics are not provided.
- The claim that DNA-binding ability is retained with "slightly lower" affinity is unsupported because no quantitative data, statistical tests, or experimental details are given.
- The claim that absence of Sry expression in adult tissues "strongly indicates a loss of regulatory function" is unsupported because developmental-stage-specific expression is not addressed.
- The overall conclusion that the findings provide insight into the unique evolution of Sry is not fully supported by the abstract, as the link between binding retention and regulatory loss is not established.