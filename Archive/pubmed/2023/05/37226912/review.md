## Review setup
- **Input scope** Full manuscript text, including abstract, background, results, discussion, methods, figure legends, supplementary figure descriptions, and supplementary table descriptions.
- **Assessment boundary** Scientific content, methodological rigor, validity of claims relative to the presented evidence, and clarity of presentation. No assessment of editorial fit or journal policy.
- **Shared manuscript claim summary** The authors present a single-cell ATAC-seq atlas of in vitro cultured cynomolgus monkey embryos from 9 to 20 days post-fertilization, covering peri- and post-implantation development. They identify lineage-specific chromatin accessibility patterns, cis-regulatory interactions, and transcription factor networks for epiblast, hypoblast, and trophectoderm/trophoblast lineages. They report that chromatin opening precedes gene expression during epiblast and trophoblast specification, propose opposing roles for FGF and BMP signaling in pluripotency regulation, and identify candidate transcription factors (PATZ1, NR2F2) involved in epiblast and trophoblast lineage segregation.
- **Visible evidence base** Main text figures 1–5 (described in text), supplementary figures S1–S7 (described in text), supplementary tables S1–S8 (described in text), methods section, and references cited within the text.
- **Missing materials affecting confidence** The actual figures, supplementary figures, and supplementary tables were not provided. Statistical details, exact sample sizes per stage, quality control metrics beyond those mentioned, and the full computational pipelines were not fully accessible. The in vivo validation dataset is referenced but not described in detail.

## Reviewer

### Overall assessment
This manuscript provides a valuable single-cell chromatin accessibility atlas of primate post-implantation development, a period that remains poorly characterized at the epigenetic level. The integration of scATAC-seq with previously published scRNA-seq data is a strength, and the observation that chromatin opening can precede gene expression during lineage specification is of interest. However, several claims, particularly those regarding signaling pathway functions and transcription factor roles, are presented with limited direct experimental validation. The reliance on computational inference for key conclusions, combined with the absence of functional perturbation experiments, means that the causal claims are not fully established. The resource itself is likely to be useful to the community, but the interpretive claims require tempering or additional support.

### Who would be interested in the results, and why
Researchers studying primate embryogenesis, particularly those focused on gastrulation, lineage specification, and pluripotency regulation, would find this resource valuable. The chromatin accessibility atlas complements existing transcriptomic atlases and provides a new layer of regulatory information. Investigators working on trophoblast differentiation, placental biology, and the evolution of developmental mechanisms across mammals would also be interested. Additionally, those developing in vitro models of primate development, such as stem cell-based embryo models, may use this dataset as a reference for benchmarking.

### Major strengths
1. The study addresses a significant gap in knowledge by profiling chromatin accessibility during primate post-implantation development, a period that is technically challenging to study and ethically constrained in humans.
2. The integration of scATAC-seq with scRNA-seq data from the same culture system allows for a paired analysis of regulatory and transcriptional dynamics.
3. The identification of lineage-specific transcription factors and cis-regulatory elements provides a useful resource for hypothesis generation.
4. The observation that chromatin opening can precede gene expression during lineage specification is a notable finding that may reflect developmental priming mechanisms.
5. The cross-species comparison with mouse data, while limited, is a step toward understanding conserved and divergent regulatory features.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for causal claims
- **Claim pointer** The authors state that FGF and BMP signaling have opposing roles in pluripotency regulation during epiblast specification, and that PATZ1 and NR2F2 are involved in epiblast and trophoblast specification.
- **Evidence pointer** Results sections "Single-cell chromatin accessibility reveals regulatory mechanisms of EPI lineage" and "Transcriptional regulation of trophoblast specification"; Figures 3F, 3G, 5F, 5G; Supplementary Figures S2, S3, S7.
- **Concern** The claims regarding FGF and BMP signaling are based on correlations between gene expression of signaling components and target genes, and on motif enrichment analyses. No functional experiments, such as pathway inhibition or activation, are presented. Similarly, the roles of PATZ1 and NR2F2 are inferred from motif enrichment and expression correlations, without perturbation studies or chromatin immunoprecipitation validation. The "driving potential" calculation is a computational metric that has not been independently validated.
- **Why it matters** The manuscript presents these as mechanistic findings. Without functional validation, the causal direction remains unclear. For example, chromatin accessibility changes could be a consequence rather than a cause of lineage commitment. The field has seen multiple instances where correlative regulatory inferences from ATAC-seq data did not hold up under perturbation. Overstating these claims could mislead subsequent research efforts.
- **Resolution test** The authors should either (a) add functional validation experiments, such as chemical inhibition of FGF or BMP signaling in the embryo culture system followed by assessment of epiblast marker expression and chromatin state, or (b) substantially revise the language to clearly frame these as hypotheses or predictions rather than established mechanisms. For the transcription factor claims, siRNA knockdown or overexpression in relevant cell types, or at minimum, confirmation of binding at predicted target loci, would be needed.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validation of the central observation
- **Claim pointer** The authors report that chromatin opening precedes gene expression during epiblast and trophoblast specification, and that this is a general phenomenon during these lineage decisions.
- **Evidence pointer** Results sections "Single-cell chromatin accessibility reveals regulatory mechanisms of EPI lineage" and "Transcriptional regulation of trophoblast specification"; Figures 3C, 3D, 4G; Supplementary Figures S2E, S3A, S3B, S4D.
- **Concern** The temporal ordering of chromatin opening and gene expression is inferred from pseudotime analysis of static single-cell snapshots. Pseudotime is a computational construct, not a true time series. The authors do not present experimental validation of the temporal precedence, such as time-course experiments with chromatin accessibility and transcription measured at multiple defined time points. Additionally, the integration of scATAC-seq and scRNA-seq data relies on computational pairing, which may introduce artifacts. The observation that chromatin opening precedes expression in some loci but not others could reflect technical differences in detection sensitivity between the two assays rather than a biological phenomenon.
- **Why it matters** The claim of temporal precedence is a central finding of the paper. If this is an artifact of the computational methods, the main conceptual contribution is weakened. The field needs to know whether this is a robust biological feature or a technical artifact.
- **Resolution test** The authors should validate the temporal ordering using an orthogonal approach. For example, they could perform RNA polymerase II ChIP-seq or nuclear run-on assays to measure active transcription at the same loci, or use metabolic labeling of nascent RNA in the culture system. Alternatively, they could analyze a time series of embryos at defined developmental stages to confirm that chromatin opening at specific loci consistently precedes transcriptional activation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Completeness of the resource description
- **Claim pointer** The authors state that this is a comprehensive map of open chromatin and lineage regulators during early monkey embryogenesis.
- **Evidence pointer** Results section "scATAC-seq profiles of monkey early embryogenesis"; Figure 1; Supplementary Figure S1; Supplementary Tables S1–S8.
- **Concern** The manuscript reports 1,198 cells sequenced with 978 retained after filtering. For a developmental atlas spanning 12 days of development and multiple lineages, this is a relatively modest number of cells. The number of embryos per stage, the number of cells per embryo, and the biological replicates are not clearly stated in the main text. The authors do not report whether the observed variability between embryos was assessed. The coverage depth and the number of peaks detected per cell are not fully described. The manuscript would benefit from a more detailed characterization of the dataset's depth and reproducibility.
- **Why it matters** A resource paper should provide sufficient detail for users to assess data quality and to design follow-up studies. If the cell numbers per stage are low, rare cell types or transient states may be missed, and the conclusions about lineage trajectories may be incomplete. The absence of replicate information makes it difficult to distinguish biological variability from technical noise.
- **Resolution test** The authors should provide a supplementary table with the number of embryos, cells per embryo, and quality metrics per stage. They should also include an analysis of reproducibility, such as correlation between biological replicates at the same stage. If replicates are not available, this limitation should be explicitly acknowledged.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1B and related text
- **Evidence pointer** Results section "scATAC-seq profiles of monkey early embryogenesis", Figure 1B
- **Issue** The text states that four main cell clusters were identified in the scRNA-seq analysis, but the scATAC-seq clustering is described separately. The relationship between the scRNA-seq clusters and the scATAC-seq clusters is not immediately clear from the text. The authors mention integration, but the details of how the two modalities were aligned are not fully described in the main text.
- **Required correction** Clarify in the text how the scATAC-seq clusters were annotated using the scRNA-seq reference. A brief description of the integration approach in the main text, with details in the methods, would improve readability.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Differential peak and gene analyses
- **Evidence pointer** Methods sections "scATAC-seq dataset analysis" and "Integrated analysis of scATAC-seq and scATAC-seq datasets"
- **Issue** The thresholds for calling differentially accessible peaks and differentially expressed genes are not clearly stated. The text mentions P values in some places but does not specify the false discovery rate control or the effect size thresholds used.
- **Required correction** Provide explicit thresholds for all differential analyses, including adjusted P values and log fold change cutoffs, in the methods section.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of cross-species comparison
- **Affected element** Results section "Transcriptional regulation of trophoblast specification", Supplementary Figure S6
- **Evidence pointer** Supplementary Figure S6
- **Issue** The cross-species comparison is performed using scRNA-seq data only, as no comparable mouse scATAC-seq dataset is available. The authors note this limitation, but the interpretation of the comparison is somewhat limited. The statement that monkey EXMCs cluster with mouse mesenchyme is presented as a finding, but the significance of this overlap is not discussed in depth.
- **Required correction** Expand the discussion of the cross-species comparison to acknowledge the limitations of comparing chromatin data from one species with transcriptomic data from another, and temper the conclusions drawn from this comparison.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout the manuscript
- **Evidence pointer** Results sections, Discussion
- **Issue** The terms "epiblast (EPI)", "trophectoderm/trophoblast (TE)", and "visceral endoderm or yolk-sac endoderm (VE/YE)" are used, but the abbreviation "TE" is used for both "trophectoderm" and "trophoblast". This is potentially confusing, as these are distinct cell types at different developmental stages.
- **Required correction** Define the abbreviations clearly at first use and consider using distinct abbreviations for trophectoderm and trophoblast, or explicitly state that TE encompasses both stages.

### Technical failings that need to be addressed before the case is established
1. The causal claims regarding FGF and BMP signaling and the roles of PATZ1 and NR2F2 require functional validation or substantial softening of language (R1-M1).
2. The temporal precedence of chromatin opening over gene expression needs orthogonal validation or clear acknowledgment of its computational basis (R1-M2).
3. The dataset description lacks sufficient detail on replicates, cell numbers per stage, and quality metrics to fully assess the resource (R1-M3).

### Assessment against Nature-style criteria
- **Originality** The manuscript addresses a gap in knowledge by providing chromatin accessibility data for primate post-implantation development. While scATAC-seq has been applied to other developmental systems, the primate post-implantation period is understudied. The specific findings regarding lineage-specific regulatory networks and the potential for chromatin priming are novel contributions.
- **Scientific importance** The resource has the potential to be widely used by the developmental biology community. Understanding the regulatory logic of primate gastrulation has implications for stem cell biology, regenerative medicine, and evolutionary developmental biology. However, the importance is somewhat diminished by the lack of functional validation for the key mechanistic claims.
- **Interdisciplinary readership** The topic is of interest to developmental biologists, epigenomicists, and stem cell researchers. The manuscript is written in a way that is largely accessible to these groups, though some of the computational details may be challenging for readers without bioinformatics training.
- **Technical soundness** The core technical approach is sound, and the quality control metrics reported are reasonable. However, the lack of functional validation for the central claims and the reliance on computational inference for key conclusions reduce the technical robustness of the interpretive framework. The pseudotime-based temporal ordering is a particular concern.
- **Readability for nonspecialists** The manuscript is generally well written, but the results section is dense and assumes familiarity with both scATAC-seq methodology and primate embryology. The abstract and introduction are accessible, but the results would benefit from clearer signposting of the main findings.

### Recommendation posture
Supportive if technical concerns are resolved. The resource itself is valuable and likely to be of interest to the community. However, the manuscript currently overstates the mechanistic insights derived from correlative analyses. The authors should either provide functional validation for the signaling and transcription factor claims, or substantially revise the language to present these as hypotheses. The temporal precedence claim also requires either additional validation or a clear statement of its computational basis. With these revisions, the manuscript would make a solid contribution to the field.