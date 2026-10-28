## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends not provided)
- **Assessment boundary** Technical and conceptual evaluation of the D&D-seq method, its validation, and the biological claims derived from its application
- **Shared manuscript claim summary** The authors present D&D-seq, a single-cell immuno-tethering technology that couples nanobodies to a cytosine base editor (DddA) to map DNA-protein interactions via targeted C-to-U deamination. They demonstrate its application to CTCF, GATA1, GATA2, and p300 in cell lines and primary cells, integrate it with scATAC-seq, single-cell genotyping, and 10x Multiome, and use the resulting data for 3D genome structure prediction and analysis of IDH2-mutant clonal hematopoiesis.
- **Visible evidence base** Main text figures referenced (Figures 1, 2, 3, 4), supplementary figures referenced (S1–S5), tables referenced (S1–S3), methods descriptions
- **Missing materials affecting confidence** Figure panels and legends not provided; supplementary tables and data files not accessible; detailed bioinformatics parameters partially described; no raw data or quality metrics for ChIP-seq comparisons shown; no statistical details for differential binding analysis

## Reviewer

- **Overall assessment** This manuscript describes a conceptually novel approach to single-cell DNA-protein interaction mapping that addresses a genuine gap in the field. The core idea of using targeted deamination as a molecular footprint is creative and potentially transformative. However, the evidence presented raises several concerns about specificity, sensitivity, and the robustness of the biological conclusions. The method's reliance on antibody accessibility in fixed cells, the relatively low per-cell editing events, and the indirect nature of the readout require more rigorous validation. The biological applications, particularly the IDH2-mutant analysis, are intriguing but preliminary. The manuscript would benefit from clearer demonstration of the method's advantages over existing approaches and more careful control experiments.

- **Who would be interested in the results, and why** Researchers in gene regulation, epigenomics, and single-cell biology would find this method of interest. The ability to profile TF binding in single cells alongside chromatin accessibility and transcriptome could enable studies of cell-to-cell variability in regulatory mechanisms, developmental trajectories, and disease states. The integration with genotyping could appeal to those studying somatic mosaicism and clonal hematopoiesis. The method's potential compatibility with existing 10x workflows makes it practically accessible to a broad community.

- **Major strengths**
  1. Conceptual novelty: The use of base editing as a molecular footprint for protein-DNA interactions is a new idea that could circumvent limitations of tagmentation-based approaches.
  2. Technical integration: The method is shown to be compatible with multiple single-cell platforms (scATAC-seq, Multiome, GoT-ChA), demonstrating versatility.
  3. Demonstrated utility in primary samples: Application to PBMCs and CHIP samples shows potential for clinical relevance.
  4. Orthogonal validation: The use of motif analysis, ChIP-seq comparison, and correlation analyses provides multiple lines of evidence for specificity.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "D&D-seq couples an antibody-binding nanobody to a cytosine base editor, a combination that enables detection of weak or transient factor binding through targeted cytosine-to-uracil editing at protein-bound genomic sites."
- **Evidence pointer** Figures 1E–1G, S1I–S1K; Methods "Extraction of D&D signal"
- **Concern** The manuscript does not adequately demonstrate that the observed C-to-T edits are specifically due to antibody-tethered deaminase activity at the target protein's binding sites, rather than non-specific deamination from free or weakly-bound enzyme. The split-enzyme design is described as providing "switch-like control," but the activation step (addition of DddA_CT) occurs after washing away unbound nb-DddA_NT. It is unclear how the authors rule out that some nb-DddA_NT remains non-specifically associated with chromatin and becomes active upon addition of the C-terminal peptide. The negative controls shown (Figures S1M and S1N) use ATAC-seq without the D&D reaction, which does not control for the presence of the deaminase enzyme itself.
- **Why it matters** If non-specific deamination contributes significantly to the signal, the method's specificity claims are undermined, and the interpretation of all downstream analyses (footprints, peak calling, differential binding) would be compromised.
- **Resolution test** The authors should include a control where cells are incubated with nb-DddA_NT in the absence of primary antibody (or with an irrelevant antibody), followed by the full activation and sequencing workflow. This would directly measure background deamination from non-targeted enzyme. Additionally, a control with a catalytically dead DddA mutant would help distinguish deamination-dependent signal from other sources of C-to-T artifacts.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "We identified an increased C>T (or G>A) mutation signature in reads overlapping respective ENCODE ChIP-seq peaks versus remaining reads" and "D&D-seq data recapitulated ChIP-seq-identified peaks"
- **Evidence pointer** Figures 1E–1G, 1Q; Methods "Evaluation of D&D signal"
- **Concern** The quantitative comparison between D&D-seq and ChIP-seq is not rigorously presented. The manuscript states that D&D-seq "recapitulated" ChIP-seq peaks, but the overlap statistics, precision-recall curves, or correlation coefficients are not provided in the text. The comparison appears to be qualitative. Furthermore, the signal-to-noise ratio calculation (dividing C-to-T counts by other variant counts) assumes that non-C-to-T variants are uniformly distributed, which may not hold in repetitive or low-complexity regions. The manuscript does not report how many of the D&D peaks were validated by ChIP-seq, nor the false discovery rate.
- **Why it matters** Without quantitative benchmarking against an established method, the reader cannot assess whether D&D-seq provides accurate, genome-wide maps of TF binding. The claim of "recapitulation" is too vague to support the method's utility.
- **Resolution test** Provide a detailed comparison: (1) precision-recall curves for D&D-seq peaks versus ChIP-seq peaks at multiple score thresholds; (2) the fraction of D&D peaks overlapping ChIP-seq peaks and vice versa; (3) a correlation analysis of signal intensity between D&D-seq and ChIP-seq at shared peaks; (4) an analysis of the false discovery rate using a control antibody or a TF with no known binding sites.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "IDH2R140Q mutation... exhibited a global reduction in CTCF binding, which perturbed chromatin architecture and reshaped the co-accessibility of specific TADs."
- **Evidence pointer** Figures 4H–4N, S4J–S4P; Methods "CTCF binding in IDH2 wild-type immune cells"
- **Concern** The analysis of CTCF binding differences between IDH2-mutant and wild-type cells is based on a small number of cells (329 mutant CD8 T cells in replicate 1, 486 in replicate 2). The manuscript uses a linear mixed model to account for batch effects, but the statistical power to detect differential binding at individual loci is limited. The finding of "global reduction" in CTCF binding is based on a comparison of normalized edit counts after regressing out ATAC fragment counts, but the manuscript does not report the magnitude of the effect or the number of significant loci. The downstream analyses (C.Origami predictions, Cicero co-accessibility) are based on these potentially underpowered data.
- **Why it matters** The biological conclusion that IDH2 mutations disrupt CTCF binding and chromatin architecture in primary cells is potentially important, but the evidence presented is preliminary. Overinterpretation of underpowered data could mislead the field.
- **Resolution test** Increase the number of cells analyzed, particularly for the mutant population. Report the number of differentially bound CTCF sites, the effect sizes, and the confidence intervals. Validate the findings with an independent method (e.g., immunofluorescence for CTCF or a targeted chromatin conformation assay). Consider analyzing additional CHIP samples to confirm the reproducibility of the effect.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "By coupling D&D-seq with whole-genome sequencing, we captured CTCF binding in both active and inactive chromatin compartments."
- **Evidence pointer** Figure 1R–1T; Methods "Bulk PTA"
- **Concern** The use of PTA (primary template-directed amplification) for whole-genome amplification after deamination introduces potential artifacts. PTA is known to have amplification bias and error profiles that may not be uniform across the genome. The manuscript does not describe how amplification errors are distinguished from true deamination events. The claim of capturing CTCF binding in "inactive chromatin compartments" (heterochromatin) is interesting, but the manuscript does not provide details on how these compartments were defined or how the signal-to-noise ratio in these regions compares to euchromatin.
- **Why it matters** If amplification errors are misclassified as deamination events, the method's specificity in low-complexity or repetitive regions (common in heterochromatin) would be questionable. The claim of detecting binding in inactive compartments is a key differentiator from other methods and needs robust support.
- **Resolution test** Include a detailed error analysis: sequence a control sample without the deaminase but with PTA amplification, and compare the mutation spectra. Report the false discovery rate of C-to-T calls in heterochromatic regions. Validate a subset of the "inactive compartment" CTCF binding sites with an orthogonal method (e.g., ChIP-seq in sorted heterochromatin fractions or single-molecule imaging).

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "D&D-seq enables scalable, single-cell-resolved interrogation of TF:DNA interactions within a multi-omic context, facilitating direct linkage between regulatory binding events and transcriptional output."
- **Evidence pointer** Figure 5; Methods "Preprocessing of 10X Multiome data"
- **Concern** The erythropoiesis experiment demonstrates the method's integration with Multiome, but the biological insight is limited. The manuscript identifies 48 putative GATA1 target genes, but does not validate these targets functionally (e.g., by knockdown or overexpression). The claim of "partially decoupled temporal patterns" between GATA1 binding and target gene expression is based on correlation analysis, but the manuscript does not provide a statistical framework for assessing this decoupling.
- **Why it matters** The method's value proposition is its ability to link binding to function. Without functional validation or a more sophisticated analysis of the binding-expression relationship, the biological significance of the erythropoiesis data is unclear.
- **Resolution test** Validate a subset of the predicted GATA1 targets by perturbing GATA1 in the same differentiation system and measuring expression changes. Provide a statistical test for the temporal decoupling (e.g., a mixed-effects model with time as a covariate). Consider comparing the D&D-seq-derived regulatory network with known GATA1 targets from the literature.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction
- **Evidence pointer** Introduction, paragraph 1
- **Issue** The introduction assumes familiarity with the technical limitations of existing methods (e.g., ChIP-seq, CUT&Tag) without briefly explaining why these methods fail in single cells. A reader outside the epigenomics field may struggle to appreciate the novelty of D&D-seq.
- **Required correction** Add one or two sentences explaining the fundamental limitations of antibody-based enrichment and tagmentation in single-cell contexts (e.g., efficiency, sensitivity, background).

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "D&D binding and activation"
- **Evidence pointer** Methods section, location not provided
- **Issue** The concentration of nb-DddA_NT used (1–5 μL of 10–50 μM) is described, but the stoichiometry relative to the number of cells and the primary antibody is not specified. This makes it difficult to assess the reproducibility of the reaction conditions.
- **Required correction** Provide the molar ratio of nb-DddA_NT to primary antibody, or state the final concentration in the reaction volume. Include a note on the range of cell numbers tested and the consistency of results across that range.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion, paragraph 3
- **Evidence pointer** Discussion, location not provided
- **Issue** The discussion of future applications (e.g., integration with CITE-seq, ASAP-seq) is speculative and not tied to any preliminary data. While such speculation is common, the manuscript would be strengthened by a more focused discussion of the method's current limitations and the most immediate next steps.
- **Required correction** Replace the list of potential integrations with a more critical assessment of the method's current sensitivity and specificity, and propose one or two concrete experiments to address these limitations.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Target prediction linear regression model"
- **Evidence pointer** Methods section, location not provided
- **Issue** The feature engineering for the logistic regression model is described, but the choice of features and the rationale for the interaction terms are not explained. The model's performance is reported as AUC values, but the precision-recall AUC is not consistently reported across all validation sets.
- **Required correction** Provide a brief justification for the selected features and the interaction terms. Report precision-recall AUC for all validation sets, not just the test set.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Results, "D&D-seq maps DNA-protein binding via molecular footprinting"
- **Evidence pointer** Results section, location not provided
- **Issue** The description of the split-enzyme design and its activation is technically dense. A schematic or a more accessible explanation of why the split design is necessary would help readers understand the key innovation.
- **Required correction** Add a brief explanation of why the split-enzyme design is used (e.g., to prevent non-specific deamination before antibody binding) and consider adding a schematic to Figure 1.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Results, "Linking genotype to DNA-protein interaction profiles and chromatin landscapes in single cells"
- **Evidence pointer** Results section, location not provided
- **Issue** The analysis of IDH2-mutant cells is limited to a single patient sample. The manuscript does not discuss the generalizability of the findings or the potential confounding effects of the patient's specific genetic background.
- **Required correction** Acknowledge the limitation of a single patient sample and discuss the need for replication in additional CHIP cohorts. Consider analyzing a second patient with a different driver mutation to assess the specificity of the observed effects.

## Risk / unsupported claims
- The claim that D&D-seq can detect "weak or transient" factor binding is not directly supported by experimental evidence. No comparison to a method known to capture weak/transient interactions (e.g., ChIP-exo or kinetic binding assays) is provided.
- The claim that D&D-seq "captured CTCF binding in both active and inactive chromatin compartments" is based on a single experiment (Figure 1R–1T) without detailed validation of the inactive compartment assignments.
- The statement that "D&D-seq achieves higher motif-driven specificity consistent with direct binding events" compared to scCUT&Tag is based on a limited comparison (one TF, one cell type) and may not generalize.
- The biological significance of the IDH2-mutant findings is presented as a "global reduction" in CTCF binding, but the statistical support for this claim is not fully described.
- The use of C.Origami for 3D structure prediction is described as "preliminary," which is appropriate, but the manuscript does not clearly state the limitations of this approach for single-cell data.