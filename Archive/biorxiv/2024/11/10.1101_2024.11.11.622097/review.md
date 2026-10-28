## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv)
- **Assessment boundary** Scientific content, methodology, claims, and evidence as presented in the provided text; no external data or supplementary materials were accessed
- **Shared manuscript claim summary** The authors report a large-scale systematic effort ("Codebook") to determine DNA sequence specificity for 332 poorly characterized human transcription factors (TFs). Using over 4,000 experiments across multiple in vitro and in vivo assays, they report motifs for 177 TFs (53%), most of which are unique. They report that in vitro motifs are enriched at cellular binding sites, identify tens of thousands of conserved direct TF binding sites (CTOP sites) across the human genome, and show that these sites are predictive of gene expression across tissues and cell types.
- **Visible evidence base** Main text, figure legends (Figures 1-6), methods summary, data availability statement, supplementary table descriptions
- **Missing materials affecting confidence** Full methods details, all supplementary tables and documents, extended data figures, accompanying companion papers (references 12-15), detailed statistical analyses, PWM quality metrics, and complete results for individual TFs

## Reviewer

### Overall assessment
This manuscript describes an ambitious and potentially valuable community resource: a systematic determination of DNA-binding motifs for poorly characterized human transcription factors. The scale of the experimental effort is substantial, and the integration of multiple assay platforms is methodologically sound in principle. The central claims, that over half of the tested putative TFs display sequence-specific DNA binding and that the resulting motifs are enriched at functional genomic sites, are of considerable interest to the gene regulation community. However, the present manuscript functions more as a project overview or resource announcement than as a self-contained scientific paper. The depth of analysis presented in the main text is insufficient to fully evaluate the robustness of the key claims, and the authors repeatedly defer critical technical details to companion papers and supplementary materials. The claim of "tens of thousands" of conserved binding sites, while plausible, cannot be adequately assessed from the evidence presented here. The manuscript would be strengthened by including more quantitative validation, clearer definitions of success criteria, and a more critical discussion of failure cases and potential false positives.

### Who would be interested in the results, and why
This work will be of direct interest to researchers studying human gene regulation, transcription factor biology, and genome function. The community of scientists who use TF binding motifs for enhancer prediction, variant interpretation, and regulatory network reconstruction will find the expanded motif catalog valuable. The identification of transposon-derived TFs and their binding preferences will interest evolutionary genomicists. The resource aspects, including the web portal and PWM collections, will be used broadly by computational biologists. The companion papers describing specific assays (GHT-SELEX) and detailed analyses will attract methodologically oriented readers.

### Major Strengths
1. The scale and systematic nature of the effort is impressive: 332 putative TFs, 4,804 experiments, and multiple orthogonal assay platforms.
2. The integration of in vitro (HT-SELEX, SMiLE-seq, PBM) and in vivo (ChIP-seq) approaches is a significant methodological strength, allowing cross-validation of motifs.
3. The explicit treatment of failure cases, including manual re-assessment of unsuccessful TFs and identification of likely true negatives, is commendable and adds credibility.
4. The demonstration that in vitro motifs are enriched at ChIP-seq binding sites provides an important validation of the biological relevance of the identified motifs.
5. The analysis of allele-specific binding and integration with disease-associated variants and eQTLs provides a clear path toward functional interpretation.
6. The updated census of human TF motif coverage (1,421 TFs) represents a valuable community resource.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Evidence sufficiency
- **Claim pointer** The authors claim that "binding motifs identified in vitro are strongly enriched within cellular binding sites" and that this validates the biological relevance of the motifs.
- **Evidence pointer** Figure 2, Extended Data Figure 4, "Overview of the Codebook project" section
- **Concern** The enrichment analysis presented in the main text is described only qualitatively. The authors state that motifs are "strongly enriched" at ChIP-seq peaks, but no quantitative metrics (e.g., enrichment fold, AUROC values, statistical significance thresholds, comparison to background models) are provided in the main text. The median AUROC of 0.71 on HEK293 data is mentioned only for external datasets, not for the Codebook ChIP-seq data itself. Without these quantitative details, the strength of the in vitro-in vivo concordance cannot be evaluated.
- **Why it matters** The claim that in vitro-derived motifs reflect genuine in vivo binding preferences is central to the utility of the entire resource. If the enrichment is modest or driven by a subset of TFs, the practical value of the motifs for genome interpretation would be substantially reduced. The authors need to demonstrate that the enrichment is consistent across TFs and not an artifact of, for example, GC content or CpG density.
- **Resolution test** Provide quantitative enrichment statistics (e.g., fold enrichment over matched genomic background, AUROC distributions across TFs, fraction of TFs with significant enrichment) for the Codebook ChIP-seq data. Show that the enrichment is not explained by simple sequence composition features. Include a comparison of motif enrichment at ChIP-seq peaks versus matched control regions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Reproducibility
- **Claim pointer** The authors state that "if we obtained similar motifs for the same protein from two or more different experimental platforms, and these motifs were predictive of data across platforms, then we considered the experiments producing these motifs to be successful."
- **Evidence pointer** "Overview of the Codebook project" section, Supplementary Table 4
- **Concern** The success criteria for motif derivation are described only in general terms. The specific thresholds for "similar motifs" and "predictive of data across platforms" are not defined in the main text. The authors do not specify how many TFs were successful on only one platform, how many required manual curation, or what the inter-platform concordance rates were. The potential for circularity in the success criteria (using cross-platform prediction to define success, then using the same motifs to claim cross-platform validity) needs to be addressed.
- **Why it matters** The reliability of the 177 reported motifs depends entirely on the rigor of the success criteria. If the criteria are too lenient, the resource will contain false positive motifs; if too stringent, the reported success rate (53%) will be misleading. The lack of transparency in these criteria undermines confidence in the resource.
- **Resolution test** Provide a detailed description of the success criteria, including quantitative thresholds for motif similarity (e.g., Pearson correlation of PWMs, distance metric) and cross-platform prediction (e.g., AUROC thresholds). Report the number of TFs successful on each platform combination, the concordance rates between platforms, and the number of TFs that required manual adjudication. Discuss the potential for circularity and how it was avoided.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance / Interpretation
- **Claim pointer** The authors claim that "the data reveal tens of thousands of previously unknown, conserved, and direct TF binding sites across the human genome."
- **Evidence pointer** "Codebook TF binding sites suggest functions for tens of thousands of conserved elements" section, Figure 4
- **Concern** The definition and derivation of CTOP sites is described only briefly. The authors state that CTOPs are the overlap of ChIP-seq peaks, GHT-SELEX peaks, and PWM matches, but the specific thresholds, the fraction of ChIP-seq peaks that meet all three criteria, and the relationship between CTOP count and TF are not presented. The claim of "tens of thousands" of sites is striking, but the number seems to depend heavily on the threshold choices and the set of TFs analyzed. The functional significance of these sites is inferred primarily from conservation, which is an indirect measure.
- **Why it matters** The claim of identifying tens of thousands of functional TF binding sites is a major scientific assertion that goes beyond the primary goal of motif discovery. If the CTOP definition is too permissive, the number will be inflated; if too restrictive, the resource will miss genuine sites. The biological interpretation of these sites as "functional" requires stronger evidence than conservation alone.
- **Resolution test** Provide a detailed description of the CTOP identification pipeline, including threshold selection, the distribution of CTOP counts across TFs, and the fraction of ChIP-seq peaks that qualify. Validate a sample of CTOP sites using an independent method (e.g., reporter assays, CRISPR perturbation, or comparison to existing functional genomics data). Discuss the relationship between CTOP sites and known regulatory elements.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Completeness
- **Claim pointer** The authors state that "many of the Codebook TFs are now among the best characterized human DNA-binding proteins in terms of their sequence specificity."
- **Evidence pointer** "Completing the human TF codebook" section, Figure 6
- **Concern** The manuscript presents an updated census of 1,421 human TFs with characterized sequence specificities, but the criteria for inclusion in this census are not fully described. The authors mention that 33 additional TFs were curated from external sources, but the quality assessment of these external motifs is not detailed. The claim that the Codebook TFs are "among the best characterized" is difficult to evaluate without a systematic comparison of data quality across resources.
- **Why it matters** The census figure is likely to be widely cited and used as a reference. If the inclusion criteria are inconsistent or the quality of external motifs is variable, the census will be misleading. The claim of superior characterization needs to be substantiated with quantitative comparisons.
- **Resolution test** Provide a clear definition of what constitutes a "characterized" TF and the criteria for including a motif in the census. Describe the quality assessment of external motifs and compare the information content, cross-platform validation, and predictive performance of Codebook motifs to those from other resources.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / Interpretation
- **Claim pointer** The authors state that "the majority [of motifs] are unique to a single protein, thereby extending the vocabulary of sequence recognition encoded by human TFs by approximately 100 distinct motifs."
- **Evidence pointer** Figure 3, Extended Data Figure 6, "Most of the Codebook TF motifs are unique" section
- **Concern** The clustering analysis that defines motif uniqueness is described only briefly. The authors mention using a similarity metric and clustering procedure, but the specific thresholds for defining distinct motifs are not provided. The statement that 92 of 613 clusters contain only Codebook proteins is presented without discussion of whether these clusters represent truly novel motifs or variations of known motifs that were not captured by the clustering threshold.
- **Why it matters** The claim of expanding the human TF motif vocabulary by approximately 100 motifs is a key outcome of the study. If the clustering is too stringent, the number of novel motifs will be inflated; if too lenient, the novelty will be understated. The biological significance of these novel motifs depends on their distinctness from known motifs.
- **Resolution test** Provide the clustering parameters and similarity thresholds used. Show examples of the novel motif clusters and their relationship to known motifs. Discuss the potential functional significance of the novel motifs and whether they are enriched in specific genomic contexts.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / Reproducibility
- **Affected element** Methods section, "DNA binding assays"
- **Evidence pointer** "DNA binding assays" subsection
- **Issue** The methods section states that "we followed previously-described protocols" for ChIP-seq, PBMs, and SMiLE-seq, but does not provide sufficient detail for a reader to understand the key parameters (e.g., antibody used for ChIP, array design for PBM, sequencing depth). The authors also mention a "novel variant" of HT-SELEX called GHT-SELEX, but the description of this method is minimal.
- **Required correction** Provide a more detailed description of the experimental protocols, particularly for GHT-SELEX, or clearly indicate that full details are available in the companion papers. Include key parameters such as the number of biological replicates, sequencing depth, and quality control metrics.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** "Codebook TF motifs predict gene expression levels across tissues and cell types" section, Figure 5
- **Evidence pointer** Figure 5, Extended Data Figure 8
- **Issue** The MARA analysis is described briefly, and the statistical framework is not fully explained. The authors report correlations between motif activity and TF expression, but the significance thresholds, multiple testing corrections, and the handling of correlated motifs are not described.
- **Required correction** Provide a more detailed description of the MARA methodology, including the statistical model, the handling of multiple testing, and the criteria for identifying significant motif-tissue associations. Include a discussion of potential confounding factors (e.g., correlated TF expression, motif similarity).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation / Context
- **Affected element** "Codebook TF binding sites suggest functions for tens of thousands of conserved elements" section
- **Evidence pointer** Figure 4
- **Issue** The authors state that CTOP sites are enriched in promoters and CpG islands, but the discussion of the biological significance of this enrichment is limited. The relationship between CTOP sites and known regulatory elements (e.g., ENCODE cCREs, FANTOM5 enhancers) is not systematically explored.
- **Required correction** Expand the discussion of the genomic distribution of CTOP sites and their relationship to known regulatory elements. Consider whether the promoter/CpG island enrichment reflects a genuine biological property of these TFs or an artifact of the assay systems used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Resource description
- **Affected element** Data availability statement
- **Evidence pointer** "Data availability" section
- **Issue** The data availability statement lists multiple repositories (SRA, GEO, Zenodo) and web portals, but does not provide a clear summary of what data is available where, or how the different resources relate to each other.
- **Required correction** Provide a clear summary table or structured description of the data products, their locations, and their relationships. Include instructions for accessing the web portal and downloading the PWM collections.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation / Accessibility
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The schematic in Figure 1 is described as providing an overview of the project, but the figure itself is not shown in the provided text. The description of the figure in the text is minimal.
- **Required correction** Ensure that the figure is self-explanatory and includes all key elements of the experimental workflow, including the number of TFs at each stage, the assays used, and the criteria for success.

### Technical failings that need to be addressed before the case is established
1. The success criteria for motif derivation are not quantitatively defined (R1-M2).
2. The enrichment of in vitro motifs at ChIP-seq peaks is not quantified (R1-M1).
3. The CTOP identification pipeline and the claim of "tens of thousands" of sites require more detailed methodological description and validation (R1-M3).
4. The clustering analysis defining motif uniqueness needs transparent thresholds and parameters (R1-M5).

### Assessment against Nature-style criteria
- **Originality** The work is original in its systematic scope and integration of multiple assay platforms for poorly characterized TFs. The concept of a "codebook" for TF sequence specificity is not entirely new, but the scale and comprehensiveness of this effort represent a meaningful advance.
- **Scientific importance** The potential importance is high. A reliable catalog of TF motifs is fundamental to understanding gene regulation, interpreting noncoding variation, and building predictive models of regulatory activity. The resource aspect of this work could have broad impact.
- **Interdisciplinary readership** The work will appeal primarily to molecular biologists, computational biologists, and genomicists. The methods and resources may also interest bioinformaticians and evolutionary biologists. The breadth of interest is moderate to high, though the presentation is somewhat specialized.
- **Technical soundness** The experimental design is generally sound, but the lack of quantitative detail in the main text prevents full evaluation. The reliance on companion papers for critical methodological information is a concern for a standalone manuscript.
- **Readability for nonspecialists** The manuscript is clearly written but assumes substantial background knowledge in TF biology and genomics. The main text is accessible to graduate students and researchers in related fields, but the methods sections are dense and would be challenging for nonspecialists.

### Recommendation posture
Supportive if technical concerns are resolved. The manuscript describes a valuable resource and presents plausible results, but the current version does not provide sufficient quantitative evidence to fully establish the central claims. The authors should either include more detailed analyses in the main text or restructure the manuscript to make clear that it is a resource announcement with full validation to appear in companion papers. The claims of "tens of thousands" of functional binding sites and the expansion of the TF motif vocabulary by approximately 100 motifs require stronger support. If the authors can provide the missing quantitative details and address the concerns raised above, this work would be suitable for publication in a high-impact venue.

## Risk / unsupported claims
1. The claim that "binding motifs identified in vitro are strongly enriched within cellular binding sites" is not quantitatively supported in the provided text.
2. The claim of "tens of thousands of previously unknown, conserved, and direct TF binding sites" is not fully supported by the evidence presented; the CTOP identification methodology is described only briefly.
3. The claim that "the resulting 177 motifs are largely different from one another, and from the motifs of previously-studied human TFs" is presented without quantitative comparison to existing motif databases.
4. The statement that "most of the unsuccessful putative TFs are likely not DNA-binding proteins or bind DNA with little or no sequence specificity" is an interpretation that cannot be fully evaluated from the provided evidence.
5. The claim that "the Codebook data expands the lexicon of human TFs by at least 15%" depends on the clustering methodology, which is not fully described.
6. The assertion that "many of the Codebook TFs are now among the best characterized human DNA-binding proteins" is subjective and not substantiated with comparative metrics.