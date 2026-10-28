## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends not provided)
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency based solely on the provided text
- **Shared manuscript claim summary** The authors identify a non-canonical role for the Rsc1 bromodomain 2 (BD2) in yeast RSC chromatin remodeling complexes. They report that Rsc1-BD2 lacks acetyllysine-binding activity and instead forms a DNA-binding surface with adjacent AT-hook and BAH domains. This surface is essential for viability in Candida albicans and Saccharomyces cerevisiae, contributes to nucleosome remodeling, and mediates RSC activity at polyA-rich promoters.
- **Visible evidence base** Crystal structure of C. albicans Rsc1-BD2 (PDB 9QHR); AlphaFold model of Rsc1; EMSA binding data; yeast growth assays; mass spectrometry of RSC complex composition; in vitro REA remodeling assays; MNase-seq genome-wide nucleosome mapping; ampDAP-seq for S. cerevisiae Rsc2; phylogenetic analysis of fungal BD sequences
- **Missing materials affecting confidence** Figures and supplementary figures not provided; exact numerical data for growth curves, EMSA quantification, REA activity percentages, and MNase-seq statistics not available; statistical methods and replicate numbers not fully described; PDB validation report not accessible; GEO accession numbers not yet assigned

## Reviewer
- **Overall assessment** This manuscript presents a compelling and potentially significant finding: a bromodomain that has evolved to bind DNA rather than acetyllysine, functioning within the essential RSC chromatin remodeling complex. The combination of structural, biochemical, and genomic approaches is ambitious and largely appropriate. The central claim that Rsc1-BD2 forms a DNA-binding module essential for viability is well-supported by the genetic and biochemical data described. However, several concerns temper my enthusiasm. The mechanistic link between polyA motif density and Rsc1-dependent nucleosome positioning, while correlative, requires stronger causal evidence. The quantitative contribution of Rsc1 DNA binding to RSC remodeling activity appears modest (35% reduction in vitro), and the in vivo nucleosome shifts, though genome-wide, are small (4-5 bp). The evolutionary analysis is intriguing but speculative regarding the timing and selective pressures of the functional switch. The manuscript would be strengthened by additional experiments directly testing the model that Rsc1 recruits RSC to polyA-rich promoters and by clarifying the relationship between the modest biochemical effects and the essentiality of the DNA-binding surface.
- **Who would be interested in the results, and why** Chromatin biologists studying ATP-dependent remodeling complexes, particularly those focused on SWI/SNF family mechanisms and targeting. Researchers interested in bromodomain functional diversity and evolution. Fungal biologists studying Candida albicans gene regulation and chromatin organization. Those developing antifungal therapeutics targeting chromatin regulators, given the essentiality of Rsc1 and its fungal-specific nature. The finding that a bromodomain can function as a DNA-binding module challenges assumptions about domain function and will interest structural biologists and evolutionary biologists studying protein domain neofunctionalization.
- **Major strengths** 1) The identification of a bromodomain with a non-canonical DNA-binding function is novel and conceptually important. 2) The combination of X-ray crystallography, AlphaFold predictions, and mutagenesis provides strong structural support for the DNA-binding surface. 3) The use of two yeast species (C. albicans and S. cerevisiae) demonstrates evolutionary conservation of the function. 4) The integration of in vitro biochemistry, in vivo genomics, and phylogenetic analysis provides multiple lines of evidence. 5) The unbiased motif discovery approach is appropriate and reveals a biologically relevant polyA motif.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative contribution of Rsc1 DNA binding to remodeling), R1-M2 (causal link between polyA motifs and Rsc1-dependent nucleosome positioning), R1-M3 (essentiality of individual domains within the module)
- **Assessment against Nature-style criteria** Originality: High. The finding that a bromodomain functions as a DNA-binding module is novel and challenges current understanding of domain function. Scientific importance: High for the chromatin field, as it addresses a long-standing question of how RSC is targeted to promoters. Interdisciplinary readership: Moderate. The work will primarily interest chromatin biologists and fungal geneticists; the broader cell biology community may find the domain evolution aspect interesting. Technical soundness: Generally strong, with appropriate methods and controls described. However, the modest effect sizes and correlative genomic analyses require additional validation. Readability for nonspecialists: The manuscript is clearly written and the logic is easy to follow, though some sections (particularly the structural and phylogenetic analyses) assume specialized knowledge.
- **Recommendation posture** Supportive if technical concerns are resolved. The core finding is novel and likely correct, but the manuscript would benefit from additional experiments to strengthen the causal link between polyA motifs and Rsc1 function, and to clarify the quantitative contribution of the DNA-binding surface to RSC activity.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative contribution of Rsc1 DNA binding to RSC remodeling activity
- **Claim pointer** "Rsc1 basic surface contributes to nucleosome remodeling by the RSC complex" and "this activity was reduced by 35% for RSC containing the Rsc1 BD2 mutant"
- **Evidence pointer** Figure 3D, location not provided
- **Concern** The in vitro REA assay shows only a 35% reduction in remodeling activity when the Rsc1 DNA-binding surface is mutated. This modest effect raises questions about the physiological significance of this interaction. If Rsc1 DNA binding is essential for viability (as shown in Figure 2F-G), one would expect a more substantial contribution to the core remodeling activity. The authors should address whether this 35% reduction is sufficient to explain the essentiality, or whether additional functions of the DNA-binding surface (e.g., in complex stability, recruitment to specific loci) contribute to the phenotype.
- **Why it matters** The manuscript's central claim is that Rsc1 DNA binding mediates RSC activity at polyA-rich promoters. If the biochemical contribution is only 35%, the physiological relevance of this interaction for genome-wide nucleosome positioning and cell viability needs to be more clearly established. The discrepancy between the modest biochemical effect and the strong genetic essentiality requires explanation.
- **Resolution test** Provide additional biochemical assays (e.g., nucleosome sliding assays with defined templates containing or lacking polyA motifs) to demonstrate a more substantial effect. Alternatively, perform complementation experiments with Rsc1 mutants that retain DNA binding but lack other functions to isolate the contribution of DNA binding to viability. Quantify the reduction in remodeling activity across multiple substrate concentrations and show that the effect is consistent and biologically meaningful.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal link between polyA motif density and Rsc1-dependent nucleosome positioning
- **Claim pointer** "nucleosome positioning at polyA-rich promoters depends on Rsc1 DNA binding module" and "the presence of polyA motifs in the NDR influences nucleosome remodeling by RSC in a Rsc1-dependent manner"
- **Evidence pointer** Figures 4E-G and 5A-B, location not provided
- **Concern** The manuscript establishes a correlation between polyA motif density and Rsc1-dependent nucleosome positioning, but the causal relationship is not directly tested. The authors show that genes with high polyA motif density exhibit Rsc1-dependent +1 nucleosome shifts, but they do not demonstrate that the polyA motif itself is necessary or sufficient for Rsc1 recruitment or activity. The in vitro EMSA experiments show Rsc1 binds polyA probes, but the specificity and affinity relative to other sequences are not fully characterized. The manuscript would be strengthened by experiments that directly manipulate polyA motifs (e.g., reporter constructs with or without polyA motifs) to test whether Rsc1 recruitment and nucleosome positioning depend on these sequences.
- **Why it matters** The manuscript proposes a model where polyA motifs recruit RSC via Rsc1. Without direct causal evidence, the model remains correlative. The distinction between correlation and causation is critical for the manuscript's central claim and for the broader understanding of RSC targeting mechanisms.
- **Resolution test** Perform reporter assays in C. albicans with promoters containing or lacking polyA motifs, and measure Rsc1 occupancy (ChIP) and nucleosome positioning (MNase-seq) in the presence of WT or DNA-binding mutant Rsc1. Alternatively, use a heterologous system (e.g., insert polyA motifs into a promoter that normally lacks them) to demonstrate that polyA motifs are sufficient to confer Rsc1-dependent nucleosome positioning.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Essentiality of individual domains within the Rsc1 DNA-binding module
- **Claim pointer** "Rsc1-BD2 forms an essential DNA-binding module with the AT-hook and BAH domains" and "all mutations resulted in severe growth defects"
- **Evidence pointer** Figures 2F-G and S6, location not provided
- **Concern** The manuscript shows that mutations in the basic surface of BD2, AT-hook, or BAH domains all cause severe growth defects. However, it is unclear whether these domains function independently or cooperatively in DNA binding. The EMSA experiments show that mutations in BD2 abolish DNA binding, but the individual contributions of the AT-hook and BAH domains are not dissected. The authors should test whether the AT-hook and BAH domains contribute independently to DNA binding or whether they function as a single integrated module.
- **Why it matters** Understanding the individual contributions of each domain is important for the mechanistic model. If the AT-hook and BAH domains have distinct DNA-binding specificities or functions, this would have implications for how RSC is targeted to different genomic loci. The current data do not distinguish between a model where all three domains form a single DNA-binding surface versus a model where they have partially redundant or distinct functions.
- **Resolution test** Perform EMSA experiments with individual domains (AT-hook alone, BAH alone, BD2 alone) and combinations thereof to determine their independent DNA-binding activities. Additionally, test whether mutations in individual domains have additive or synergistic effects on DNA binding and growth phenotypes.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Growth assays and EMSA quantification
- **Evidence pointer** Figures 1B-C, 2F-G, S1, S6, location not provided
- **Issue** The manuscript describes growth assays and EMSA experiments but does not report the number of biological replicates or statistical tests used to assess significance. The text states that mutations "abolished" or "nearly abolished" DNA binding and caused "severe growth defects" without providing quantitative measures of variability.
- **Required correction** Provide the number of independent experiments performed, error bars on all quantitative measurements, and the statistical tests used (e.g., t-test, ANOVA) with p-values. For growth assays, report the growth rate or area under the curve with confidence intervals.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data availability
- **Affected element** MNase-seq and ampDAP-seq datasets
- **Evidence pointer** Data availability section
- **Issue** The MNase-seq data are described as "will be deposited" with placeholder accession numbers. The ampDAP-seq data are described as using published libraries, but the specific accession numbers for the new experiments are not provided.
- **Required correction** Provide the actual GEO accession numbers for the MNase-seq data and the ampDAP-seq data, or state clearly that these are available upon request. Ensure that all data are deposited prior to publication.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** All figures
- **Evidence pointer** Not applicable
- **Issue** The manuscript text references multiple figures and supplementary figures, but the figures themselves were not provided for review. This limits the ability to assess the quality of the structural data, the clarity of the growth phenotypes, and the genome-wide nucleosome maps.
- **Required correction** Ensure that all figures are of high quality and clearly labeled. For the crystal structure, provide representative electron density maps. For the MNase-seq data, provide genome browser views of representative loci to illustrate the +1 nucleosome shifts.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** "polyA motif" vs. "A-rich motif"
- **Evidence pointer** Throughout the manuscript
- **Issue** The manuscript uses both "polyA motif" and "A-rich motif" to describe the DNA sequence element. While these terms are related, they may imply different sequence characteristics. The authors should define the motif precisely (e.g., consensus sequence) and use consistent terminology throughout.
- **Required correction** Define the motif consensus sequence and use a single term consistently. If the motif is a run of adenines, specify the length and whether it is homopolymeric or has interspersed bases.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of alternative models
- **Affected element** Discussion section
- **Evidence pointer** Discussion, location not provided
- **Issue** The discussion focuses on the proposed model where Rsc1 DNA binding recruits RSC to polyA-rich promoters. However, alternative models are not fully considered. For example, the DNA-binding surface could contribute to nucleosome remodeling processivity or stability of the RSC-nucleosome complex rather than recruitment per se. The authors should discuss these alternatives.
- **Required correction** Add a paragraph in the discussion considering alternative mechanisms by which the Rsc1 DNA-binding surface could contribute to RSC function, and how the current data distinguish between these possibilities.

## Risk / unsupported claims
- The claim that Rsc1-BD2 "lacks a functional acetyllysine-binding pocket" is supported by structural analysis and mutagenesis, but no direct binding assay with acetylated peptides is described. The manuscript would be strengthened by a direct binding experiment (e.g., ITC or NMR) with acetylated histone peptides to confirm loss of acetyllysine binding.
- The claim that the polyA motif is "specifically enriched at NDRs" is based on a de novo motif search, but the statistical significance of this enrichment and the fraction of promoters containing the motif are not reported.
- The claim that "nucleosome positioning at polyA-rich promoters depends on Rsc1 DNA binding module" is based on correlative genomic data. The causal relationship is not directly tested.
- The evolutionary analysis suggests that the DNA-binding function of Rsc1-BD2 "arose before the divergence of the Ascomycota phylum," but this is based on sequence conservation of basic residues, not functional assays in diverse species. The timing of the functional switch is speculative.
- The statement that "Rsc1 preferentially binds polyA motifs in vitro" is based on EMSA with a single polyA probe and a T/C-rich control. The specificity of binding across a broader range of sequences is not established.
- The claim that the Rsc1 DNA-binding surface is "essential for viability in both species" is supported by the data, but the manuscript does not address whether the essentiality is due to DNA binding per se or to other functions of the mutated residues (e.g., protein stability, complex assembly).