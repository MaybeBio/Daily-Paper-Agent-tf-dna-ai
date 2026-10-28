## Review setup
- **Input scope** Full manuscript text (Background, Methods, Results, Discussion, Conclusion) as provided by the user, without access to figures, tables, or supplementary materials beyond what is described in the text.
- **Assessment boundary** Evaluation is limited to the scientific content, methodological soundness, and interpretative claims presented in the supplied text. No external data, raw sequences, or reproducibility checks were performed.
- **Shared manuscript claim summary** The authors report an in silico analysis of promoter regions, transcription start sites (TSS), regulatory motifs, transcription factor binding sites, CpG islands, and phylogenetic relationships for 15 mitochondrial protein-coding genes in Metarhizium anisopliae strain ME1, with the aim of identifying regulatory elements relevant to bio-pesticide function.
- **Visible evidence base** Text descriptions of methods and results, including one table (Table 1: TSS counts and predictive scores), one table (Table 2: candidate motifs), one table (Table 3: matching transcription factors), one table (Table 4: GO terms), and references to six figures (Figs. 1–6) that were not directly viewable in the supplied material.
- **Missing materials affecting confidence** Figures 1–6 (sequence logos, motif distributions, interaction networks, dinucleotide plots, phylogenetic tree) were not provided. Raw sequence data, accession numbers, and detailed algorithm parameters (e.g., MEME settings beyond defaults) are not fully specified. The phylogenetic tree (Fig. 6) and its alignment details are not assessable without the figure.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant topic in fungal bio-pesticide research, specifically the regulatory genomics of M. anisopliae. However, the work is largely descriptive and computational, with several methodological ambiguities and overinterpretations. The central claim that identified motifs and transcription factors will contribute to strain improvement is not substantiated by functional validation or robust statistical support. The analysis is technically plausible but incomplete in its current form, and the presentation lacks clarity in key areas.
- **Who would be interested in the results, and why** Researchers in fungal genomics, entomopathogenic fungi biology, and bio-pesticide development may find the preliminary promoter characterization of interest. The identification of candidate regulatory motifs could inform future experimental studies on gene expression regulation in M. anisopliae. However, the audience is narrow and specialized, and the practical implications for bio-pesticide improvement remain speculative.
- **Major strengths** 1. The study addresses a gap in knowledge regarding promoter regions in M. anisopliae strain ME1. 2. The use of multiple bioinformatics tools (NNPP, MEME, TOMTOM, RSAT, GSEA) is appropriate for the stated goals. 3. The inclusion of phylogenetic analysis adds an evolutionary perspective. 4. The authors acknowledge the need for experimental validation, which is a reasonable limitation statement.
- **Major Concerns** 
  - R1-M1: The claim that identified motifs and transcription factors will contribute to strain improvement is unsupported by functional evidence.
  - R1-M2: The statistical and methodological basis for TSS identification and motif significance is inadequately described.
  - R1-M3: The phylogenetic analysis is presented without sufficient detail on alignment, model selection, or interpretation of bootstrap values.
  - R1-M4: The relevance of CpG island analysis to mitochondrial genes in fungi is questionable and not well justified.
  - R1-M5: The connection between the identified regulatory elements and bio-pesticide function is not established.
- **Minor Comments** 
  - R1-m1: The abstract and background sections contain redundant statements about the importance of bio-pesticides.
  - R1-m2: The methods section lacks specific version numbers for some tools (e.g., CLC Genomics Workbench) and does not specify default parameters for MEME beyond motif distribution.
  - R1-m3: Table 1 includes negative distances from the start codon, which are not clearly explained.
  - R1-m4: The discussion cites several references but does not critically compare findings with other fungal promoter studies.
  - R1-m5: The conclusion overstates the practical implications without experimental support.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5.
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The application of promoter analysis to M. anisopliae is novel, but the methods are standard and the findings are descriptive.
  - Scientific importance: Low to moderate. The results are preliminary and do not provide mechanistic insights or broadly applicable principles.
  - Interdisciplinary readership: Limited. The work is primarily of interest to fungal genomics and bio-pesticide specialists, not a broad scientific audience.
  - Technical soundness: Weak. Several methodological details are missing, and the statistical support for key claims is insufficient.
  - Readability for nonspecialists: Poor. The manuscript assumes familiarity with bioinformatics tools and mitochondrial genomics, and the flow is disrupted by unclear figure references and inconsistent terminology.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires substantial revisions, including clearer methodology, stronger statistical support, and a more cautious interpretation of findings, before it can be considered for publication.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim validity
- **Claim pointer** The conclusion states that identified motifs and transcription factors "are likely expected to contribute for better understanding of gene expression and strain improvement of M. anisopliae Strain ME1 for its bio-pesticides role."
- **Evidence pointer** Conclusion section; no experimental validation provided.
- **Concern** The claim of contribution to strain improvement is speculative and not supported by any functional experiments, such as gene expression assays, knockout studies, or phenotypic analyses. The in silico predictions alone cannot establish a causal link between the identified motifs and bio-pesticide efficacy.
- **Why it matters** Without functional validation, the practical relevance of the findings remains unproven, and the conclusion overreaches the evidence.
- **Resolution test** Provide experimental data (e.g., reporter assays, gene expression analysis under infection conditions) or explicitly reframe the conclusion as a hypothesis for future work.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The methods state that TSS were identified using NNPP with a default cutoff of 0.8, and motifs were found using MEME with default settings, but no details on statistical significance thresholds or background models are given.
- **Evidence pointer** Methods section, "Determination of transcription start site and promoter regions" and "Analysis of sequence motif and transcription factors"; location not provided.
- **Concern** The description of the TSS prediction and motif discovery is insufficient. It is unclear how the cutoff value was applied, whether multiple testing corrections were performed, and what statistical measures (e.g., p-values, E-values) were used to filter significant motifs. The E-value for Mtrn I is reported, but the criteria for selecting the five motifs from the thirteen generated are not explained.
- **Why it matters** Reproducibility and reliability of the results depend on transparent and rigorous bioinformatics parameters. Without this, the identified motifs and TSS may be artifacts.
- **Resolution test** Specify all algorithm parameters, statistical thresholds, and post-processing steps. Provide a supplementary table with all motifs and their significance scores.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The phylogenetic analysis claims "homologues evolutionary ancestor supported with a bootstrap value of 100%" for M. anisopliae trn gene clusters.
- **Evidence pointer** Results section, "Phylogenetic analysis of mitogenome trn gene clusters"; Fig. 6 not viewable.
- **Concern** The phylogenetic tree is described but not shown in the supplied material. The methods for alignment, model selection, and tree construction are not detailed. The bootstrap value of 100% is mentioned for some clusters, but the overall tree topology and the significance of the relationships are not assessable.
- **Why it matters** Phylogenetic claims require robust methodology and clear presentation to be evaluated. Without the figure and methods, the evolutionary conclusions cannot be verified.
- **Resolution test** Include the phylogenetic tree as a figure, describe the alignment and model selection methods, and discuss bootstrap support for all major clades.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Relevance
- **Claim pointer** The analysis of CpG islands in mitochondrial genes is presented as a result, with the finding of "poor possible occurrence of CGIs in both promoter and gene body regions."
- **Evidence pointer** Results section, "Determination of CpG islands"; location not provided.
- **Concern** The relevance of CpG island analysis in mitochondrial genomes is not justified. Mitochondrial genomes in fungi are typically small, AT-rich, and lack the CpG methylation machinery found in nuclear genomes. The authors do not explain why CpG islands would be expected or what their presence/absence implies for gene regulation.
- **Why it matters** Including an analysis with unclear biological relevance distracts from the main findings and may confuse readers.
- **Resolution test** Provide a rationale for CpG analysis in mitochondrial context, or remove this section if it does not contribute to the main conclusions.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim validity
- **Claim pointer** The background states that "understanding promoter regions... is crucial" and the conclusion implies that the identified regulatory elements are relevant to bio-pesticide function.
- **Evidence pointer** Background and Conclusion sections; location not provided.
- **Concern** The link between the analyzed genes (mitochondrial trn gene clusters) and bio-pesticide activity is not established. The manuscript does not explain how these specific genes relate to pathogenicity or insecticidal activity, nor does it connect the regulatory elements to known virulence pathways.
- **Why it matters** The stated purpose of the study is to support bio-pesticide development, but the biological connection is missing, weakening the overall significance.
- **Resolution test** Clarify the functional role of the analyzed genes in bio-pesticide activity, or reframe the study as a general promoter characterization without overstating applied implications.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Background
- **Evidence pointer** Background section, first paragraph; location not provided.
- **Issue** The background repeats the importance of bio-pesticides and the role of M. anisopliae in multiple sentences, which is redundant.
- **Required correction** Condense the introductory statements to avoid repetition and focus on the specific gap being addressed.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section, "Analysis of CpG islands" and "Phylogenetic tree construction"; location not provided.
- **Issue** Tool versions are incomplete (e.g., CLC Genomics Workbench version is given, but MEME and NNPP versions are not fully specified), and default parameters are not listed for all tools.
- **Required correction** Provide complete tool versions and all non-default parameters in the methods or supplementary materials.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Table 1
- **Evidence pointer** Table 1, distances from start codon; location not provided.
- **Issue** Negative distances (e.g., – 1450) are listed without explanation, which may confuse readers about the coordinate system used.
- **Required correction** Define the coordinate system (e.g., upstream of ATG) and explain why some distances exceed the 1 kb upstream region.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section, paragraph on transcription factors; location not provided.
- **Issue** The discussion cites studies on transcription factors but does not critically compare the identified motifs with known fungal promoter elements, limiting the interpretive depth.
- **Required correction** Add a comparative discussion with existing fungal promoter databases or known regulatory motifs.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language
- **Affected element** Conclusion
- **Evidence pointer** Conclusion section; location not provided.
- **Issue** The conclusion uses tentative language ("likely expected to contribute") that is appropriate but could be more precise about the study's limitations.
- **Required correction** Strengthen the statement of limitations and explicitly call for experimental validation.

## Risk / unsupported claims
- The claim that identified motifs and transcription factors will contribute to strain improvement is unsupported without functional validation.
- The phylogenetic claim of a "homologues evolutionary ancestor" with 100% bootstrap support is not verifiable without the tree figure and detailed methods.
- The relevance of CpG island analysis to mitochondrial gene regulation is not justified.
- The connection between the analyzed genes and bio-pesticide function is not established.
- The statistical significance of TSS predictions and motif discoveries is not fully reported, making the results difficult to evaluate.