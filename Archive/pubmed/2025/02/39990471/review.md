## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Results, Discussion, Materials and methods) as provided
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency based solely on the supplied text
- **Shared manuscript claim summary** The authors report that the homeodomain protein Sxi1α in Cryptococcus deneoformans has a previously unrecognized role as a negative regulator of α-α cell fusion during unisexual reproduction, and that Sxi1α and Sxi2a regulate distinct, non-overlapping gene sets in both unisexual and α-a sexual reproduction, suggesting independent functions beyond their canonical heterodimer activity.
- **Visible evidence base** Results sections describing structural predictions (Fig 1), gene deletion and phenotyping (Figs 2-3), fusion assays (Fig 4), and RNA-seq analyses (Fig 5, S1-S5 Figs, Tables S1-S2); Materials and methods sections for all experiments
- **Missing materials affecting confidence** Raw RNA-seq data, differential expression tables (Table S1), strain genotypes (Table S3), primer sequences (Table S4), Biolog raw data, and supplementary figures S1-S7 were not provided. Statistical details for fusion assays beyond p-values are incomplete. No information on how the "helper strain" Ménage à trois system was validated for the specific fusion measurements.

## Reviewer
- **Overall assessment** This manuscript presents a well-structured investigation into the roles of Sxi1α and Sxi2a in Cryptococcus deneoformans sexual reproduction, with a focus on unisexual mating. The finding that Sxi1α negatively regulates α-α cell fusion is novel and potentially significant. The transcriptomic data support distinct regulatory roles for the two HD proteins. However, several technical concerns, particularly regarding the fusion assay interpretation, the exclusion of a replicate, and the limited validation of the homodimer hypothesis, temper the strength of the conclusions. The manuscript is clearly written and will interest fungal biologists and those studying sexual development.
- **Who would be interested in the results, and why** Researchers studying fungal sexual reproduction, mating-type determination, and homeodomain transcription factor function. The work also has relevance for those interested in the evolution of unisexual reproduction in pathogenic fungi, particularly Cryptococcus, and for comparative studies with model systems like Saccharomyces cerevisiae and Ustilago maydis.
- **Major strengths**
  1. The identification of a novel, Sxi2a-independent role for Sxi1α in negatively regulating α-α cell fusion is a significant and unexpected finding that challenges the current heterodimer-centric model.
  2. The combination of structural prediction (AlphaFold3), genetic deletion, phenotypic analysis, and transcriptomics provides a multi-faceted approach.
  3. The comparative analysis of gene expression in unisexual versus α-a crosses is informative and reveals distinct regulatory programs.
  4. The manuscript is well-written and places the findings in a strong evolutionary and comparative context.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Experimental design and interpretation
  - **Claim pointer** The claim that Sxi1α has an inhibitory role in α-α cell fusion is based on increased fusion frequency in sxi1αΔ mutants.
  - **Evidence pointer** Results section "Sxi1α is critical for unisexual cell-cell fusion", Fig 4B
  - **Concern** The fusion assay relies on the Ménage à trois system with a "helper strain" as a pheromone donor. The authors report that wild-type α x α crosses have fusion frequencies below 5.04×10⁻⁸, while sxi1αΔ crosses show frequencies of 1.13×10⁻⁶ (bilateral) and 3.17×10⁻⁶ (unilateral). While these differences are statistically significant, the absolute frequencies are extremely low. The authors also note that haploid NAT/Neo resistant colonies were detected in some crosses, suggesting that the assay may overestimate fusion frequency due to genome recombination. This is a critical caveat. If a significant fraction of the "fusion products" are actually haploid recombinants rather than true diploid fusion products, the calculated fusion frequencies could be substantially inflated. The authors must provide a more detailed breakdown of the ploidy analysis for all crosses, not just a subset, and clarify how the potential for recombination artifacts was addressed in the calculation of fusion frequencies. Without this, the central claim of Sxi1α as a negative regulator of fusion is not robustly established.
  - **Why it matters** The central novel claim of the paper rests on the accuracy of the fusion frequency measurements. If the assay is confounded by recombination or other artifacts, the conclusion that Sxi1α inhibits cell-cell fusion is unsupported.
  - **Resolution test** Provide a full accounting of the ploidy (diploid vs. haploid) of all NAT/Neo resistant colonies from all crosses. Recalculate fusion frequencies excluding haploid colonies. If the significant difference between wild-type and sxi1αΔ crosses persists after this correction, the claim is strengthened. Additionally, provide a more detailed description of the Ménage à trois system and how it was validated to ensure that the "helper" strain does not contribute to the observed fusion events.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Data analysis and interpretation
  - **Claim pointer** The claim that Sxi1α and Sxi2a have distinct, non-overlapping transcriptional roles is based on the identification of unique DEG sets in sxi1αΔ and sxi2aΔ mutants.
  - **Evidence pointer** Results section "Sxi1α and Sxi2a regulate expression of unique subsets of genes in unisexual crosses", Fig 5A-5C
  - **Concern** The authors state that there were no shared DEGs between sxi1αΔ and sxi2aΔ in solo cultures. This is a striking result, but the analysis is based on a relatively small number of DEGs (19 and 23, respectively). The power to detect shared DEGs is limited by the small effect sizes and the stringent thresholds used. The authors should provide the full list of DEGs (Table S1) and the effect sizes and p-values for all genes, not just those passing the threshold. It is possible that genes with smaller effect sizes are shared between the two mutants but were excluded by the arbitrary |log2FC| ≥ 1 cutoff. A more nuanced analysis, such as a rank-based comparison or a gene set enrichment analysis, would be more convincing. Furthermore, the exclusion of one sxi1αΔ replicate (S1C Fig) needs to be justified more thoroughly. If the replicate was excluded due to technical issues, this should be stated clearly. If it was excluded because it was an outlier, this could bias the results.
  - **Why it matters** The conclusion that Sxi1α and Sxi2a have independent functions is a key part of the paper's thesis. If the analysis is underpowered or biased, this conclusion is weakened.
  - **Resolution test** Provide the full DEG tables with all statistics. Perform a more comprehensive analysis, such as a rank-rank hypergeometric overlap test or a GSEA, to assess the overlap between the two mutant transcriptomes. Justify the exclusion of the replicate with a clear technical rationale.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretation of structural predictions
  - **Claim pointer** The claim that Sxi1α may form homodimers is based on low-confidence AlphaFold3 predictions.
  - **Evidence pointer** Results section "Sxi1α and Sxi2a are predicted to form a heterodimer", Fig 1D
  - **Concern** The AlphaFold3 predictions for Sxi1α-Sxi1α and Sxi2a-Sxi2a homodimers have very low ipTM scores (0.14 and 0.20, respectively). These scores are well below the threshold typically considered indicative of a confident model. The authors acknowledge this, but then use these predictions to support the hypothesis that Sxi1α may function as a homodimer. This is a significant logical leap. The low-confidence predictions are not sufficient to support the homodimer hypothesis. The authors should either provide experimental evidence for homodimerization (e.g., co-immunoprecipitation, yeast two-hybrid, or size-exclusion chromatography) or temper their claims about the functional significance of homodimers.
  - **Why it matters** The homodimer hypothesis is used to explain the Sxi2a-independent functions of Sxi1α. If the structural basis for this hypothesis is weak, the functional interpretation is also weak.
  - **Resolution test** Provide experimental evidence for Sxi1α homodimerization. Alternatively, revise the discussion to clearly state that the homodimer hypothesis is speculative and requires further testing.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and completeness
  - **Affected element** Methods section "Mating and cell-cell fusion assay"
  - **Evidence pointer** Materials and methods
  - **Issue** The description of the Ménage à trois mating assay is brief. It is unclear how the "helper strain" (JEC20 or JEC21) is used and how the fusion frequency is calculated. Specifically, the denominator for the fusion frequency (total cells plated) is mentioned, but the numerator (number of fusion products) is not clearly defined. Are all NAT/Neo resistant colonies considered fusion products, or only those confirmed to be diploid?
  - **Required correction** Provide a more detailed description of the assay, including a clear definition of a "fusion product" and how the frequency is calculated. Include a schematic if possible.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Fig 5I
  - **Evidence pointer** Results section "SXI1α and SXI2a have distinct and overlapping transcriptional effects in unisexual and α-a sexual crosses"
  - **Issue** The logic for classifying genes as "heterodimer-repressed" or "heterodimer-activated" is described in the text, but the figure is not shown. It is difficult to assess the validity of this classification without seeing the underlying data.
  - **Required correction** Ensure that Fig 5I clearly shows the expression changes for all genes in all crosses, and that the classification criteria are visually apparent.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion section
  - **Evidence pointer** Discussion
  - **Issue** The authors state that "unisexual reproduction is likely regulated in a manner that is at least partially distinct from α x a sexual reproduction." This is a reasonable conclusion, but it is based on the observation that Sxi1α and Sxi2a are dispensable for unisexual morphology. The authors should be more cautious, as the transcriptomic data do show significant changes in gene expression in the mutants during unisexual reproduction, even if these do not translate into obvious morphological phenotypes.
  - **Required correction** Soften the statement or provide additional evidence to support the claim that the regulatory programs are truly distinct.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1: The fusion assay may be confounded by haploid recombinants, which could inflate the reported fusion frequencies. A detailed ploidy analysis of all fusion products is required.
  - R1-M2: The transcriptomic analysis is underpowered to detect shared DEGs between sxi1αΔ and sxi2aΔ, and the exclusion of a replicate needs better justification.
  - R1-M3: The homodimer hypothesis is based on low-confidence structural predictions and requires experimental validation.
- **Assessment against Nature-style criteria**
  - **Originality** The finding that Sxi1α negatively regulates α-α cell fusion is novel and challenges the prevailing model of HD protein function in Cryptococcus. The idea that these proteins have independent functions beyond their heterodimer is also original.
  - **Scientific importance** The work has significant implications for understanding the regulation of sexual reproduction in a major human fungal pathogen. The potential link between metabolic state and mating regulation is also of interest. However, the importance is somewhat limited by the focus on a single, relatively niche species.
  - **Interdisciplinary readership** The work will primarily appeal to fungal biologists, molecular geneticists, and those studying sexual development. The broader cell biology and evolutionary biology communities may also find it of interest, but the appeal is not broad.
  - **Technical soundness** The experimental design is generally sound, but the concerns about the fusion assay and the transcriptomic analysis need to be addressed. The structural predictions are used appropriately, but the interpretation of the homodimer predictions is overreaching.
  - **Readability for nonspecialists** The manuscript is clearly written and the logic is easy to follow. The use of figures and tables is appropriate. The abstract is concise and accessible.
- **Recommendation posture** Supportive if technical concerns are resolved. The central claim of Sxi1α as a negative regulator of cell fusion is potentially significant, but the current evidence is not fully convincing due to the potential for assay artifacts. The transcriptomic analysis also needs to be more robust. If the authors can address these concerns, the manuscript would be a valuable contribution to the field.

## Risk / unsupported claims
- The claim that Sxi1α forms a functional homodimer is unsupported by the low-confidence AlphaFold3 predictions and requires experimental validation.
- The claim that Sxi1α and Sxi2a have "opposing regulatory effects" on MAT genes is not fully supported by the data presented, as the direction of regulation is not clearly shown for all genes.
- The statement that the widespread conservation of SXI1α suggests it is "under positive selection" is speculative and not directly tested in this study.
- The potential role of Sxi1α in linking metabolic state to mating regulation is an interesting hypothesis but is not directly tested.