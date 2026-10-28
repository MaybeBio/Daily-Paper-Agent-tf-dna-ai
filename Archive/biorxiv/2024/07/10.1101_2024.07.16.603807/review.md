## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, declarations) as provided
- **Assessment boundary** Scientific content, methodological soundness, evidence quality, and internal consistency of the claims as presented in the supplied text
- **Shared manuscript claim summary** The authors report the in silico identification of eight PAX family proteins in the land snail *Lissachatina fulica* using a custom HMM profile built from 91 molluscan PAX sequences, with validation by domain search, secondary and tertiary structure prediction, molecular docking against DNA, and phylogenetic analysis. They assign the eight proteins to five PAX subfamilies (I, III, IV, β, and Pox-Neuro) and propose these as a starting point for functional studies, particularly in relation to eye regeneration.
- **Visible evidence base** Abstract; Introduction; Materials and Methods (sections on database compilation, protein prediction, verification, structure prediction, docking, phylogenetics, BLAST); Results (including references to Table 1, Table 2, Table 3, Figures 1–5, and supplementary tables S1 and S2); Discussion; Declarations
- **Missing materials affecting confidence** Tables 1–3 and Figures 1–5 are referenced but not provided in the submitted text. Supplementary Tables S1 and S2 are referenced but not provided. No sequence data, alignment files, HMM profile parameters, or docking output files are included. No accession numbers for the 91 reference sequences are listed in the visible text. The methods section lacks specific software versions for some tools (e.g., InterProScan version, HADDOCK version is given, but not all parameters). No statistical or quality metrics for the phylogenetic tree (e.g., bootstrap values beyond the stated 1000 replicates) are visible.

## Reviewer
- **Overall assessment** This manuscript presents a straightforward bioinformatics pipeline for the identification and preliminary classification of PAX family proteins in a non-model gastropod. The work is descriptive and largely confirmatory in nature, applying established tools (HMMER, InterProScan, AlphaFold2, HADDOCK, MEGA) to a publicly available proteome. The core claim, that eight proteins belong to five PAX subfamilies, is plausible but the evidence as presented is incomplete. The absence of the actual tables, figures, and supplementary data makes it impossible to verify the central conclusions. The docking analysis, in particular, is presented in a way that conflates HADDOCK scores with binding affinity without adequate statistical context. The phylogenetic analysis appears to have been performed with a limited taxon sampling that may not robustly support subfamily assignments. The manuscript would benefit from a more critical interpretation of the results, particularly regarding the partial domains and the functional implications drawn from structural predictions alone. The writing is generally clear but contains several typographical and grammatical errors that should be corrected.

- **Who would be interested in the results, and why** Researchers working on the molecular biology and evolution of transcription factors in molluscs, particularly those interested in PAX gene family diversity in Lophotrochozoa. The work may also be of interest to the small community studying *Lissachatina fulica* as a model for regeneration, as it provides candidate gene sequences for future functional studies. However, the impact is limited by the descriptive nature of the study and the lack of experimental validation.

- **Major strengths**
  1. The study addresses a genuine gap: PAX proteins in *L. fulica* have not been previously characterized, and the lack of an annotated genome makes in silico prediction a reasonable first step.
  2. The methodological pipeline is logical and uses widely accepted, publicly available tools, which enhances reproducibility in principle.
  3. The authors acknowledge the limitations of their approach, particularly regarding the incomplete domains and the absence of transcriptomic confirmation.
  4. The discussion of PAX6 variant diversity in molluscs, particularly the comparison with cephalopod isoforms, is informative and well-contextualized.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that eight proteins of *L. fulica* contain PAX characteristic sequences and are categorized into five subfamilies (I, III, IV, β, and Pox-Neuro).
- **Evidence pointer** Results section, references to Table 1, Table 2, Table 3, Figures 1–5, Tables S1 and S2
- **Concern** The central results are presented only as references to tables and figures that are not included in the submitted text. Without the actual sequence alignments, domain annotations, phylogenetic tree, docking scores, and BLAST hit tables, it is impossible to assess whether the eight sequences genuinely contain PAX domains, whether the subfamily assignments are statistically supported, or whether the docking results are meaningful. The reader cannot verify the authors' interpretations.
- **Why it matters** The entire conclusion of the paper rests on these data. A review cannot establish the validity of the claims without access to the primary evidence. This is a fundamental issue that prevents any meaningful evaluation of the scientific content.
- **Resolution test** Provide all referenced tables and figures, including supplementary data, with clear labels and legends. Ensure that sequence accession numbers, alignment coordinates, domain boundaries, bootstrap values, and docking statistics are fully visible and interpretable.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The authors state that molecular docking was used to compare the DNA-binding ability of the predicted proteins with a control Paired box domain, and that HADDOCK scores and z-scores were used to infer relative affinity.
- **Evidence pointer** Materials and Methods, DNA-Protein docking simulation; Results, DNA-Protein docking findings, Table 2
- **Concern** The docking methodology is described at a superficial level. No details are given on how the DNA fragment was prepared, how the protein structures were prepared (e.g., protonation, energy minimization), how the docking was run (e.g., number of models generated, which scoring function was used), or how the results were interpreted. The authors appear to interpret HADDOCK scores and z-scores as direct proxies for binding affinity, which is an oversimplification. HADDOCK scores are relative and depend heavily on the input restraints and the quality of the starting structures. The comparison with the control domain is mentioned but no statistical test is described to determine whether differences are significant.
- **Why it matters** The docking results are used to support functional claims about DNA-binding capacity. If the methodology is not rigorous or the interpretation is flawed, the conclusions drawn from this analysis are not reliable. This is particularly important because the authors use docking data to differentiate between closely related sequences (e.g., Afu016671 vs. Afu016672).
- **Resolution test** Provide a detailed description of the docking protocol, including all parameters, input files, and the number of models generated. Clarify how the HADDOCK score and z-score were used to infer binding affinity. Include a statistical comparison between the predicted proteins and the control. If possible, provide a figure showing the docked complexes with the DNA interface highlighted.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Phylogenetic robustness
- **Claim pointer** The authors state that phylogenetic analysis, along with BLAST, was used to determine the subfamily membership of the predicted proteins.
- **Evidence pointer** Materials and Methods, Phylogenetic analysis; Results, Phylogenetic and BLAST analyses, Figure 3, Table 3
- **Concern** The phylogenetic analysis is described only briefly. The taxon sampling is not specified in the visible text, and it is unclear how many sequences from each subfamily were included. The tree in Figure 3 is not visible, so the branch support values and the placement of the *L. fulica* sequences cannot be assessed. The authors note that Afu015865 and Afu004298 occupy an "intermediate position" between subfamilies I and II, which suggests the tree may not be fully resolved. The BLAST results (Table 3) are described as showing "no definitive matches" with the phylogenetic findings, which is a concerning inconsistency that is not adequately explained.
- **Why it matters** The subfamily assignments are a key output of the study. If the phylogenetic signal is weak or the taxon sampling is inadequate, the assignments may be incorrect. The inconsistency between BLAST and phylogenetic results needs to be resolved or explained, as it undermines confidence in the classification.
- **Resolution test** Provide the full phylogenetic tree with all sequences labeled, including accession numbers and bootstrap support values. Specify the taxon sampling strategy and the number of sequences per subfamily. Explain the discrepancy between BLAST and phylogenetic results, and discuss how the final assignments were made in cases of conflict.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Functional interpretation
- **Claim pointer** The authors suggest that the identified PAX proteins may play a significant role in eye regeneration in *L. fulica*, based on the known role of PAX proteins in eye development.
- **Evidence pointer** Introduction; Discussion
- **Concern** The link between the identification of PAX proteins and their proposed role in regeneration is speculative. The authors do not provide any expression data, functional assays, or even a literature-based argument specific to *L. fulica* that would support this connection. The statement that "we believe that they likely play a significant part in the regeneration process" is presented without supporting evidence. While this is framed as a motivation for future work, it is stated in a way that could be misread as a finding of the study.
- **Why it matters** The introduction and discussion frame the entire study around the regeneration question. If the connection is purely speculative, this should be clearly stated as a hypothesis, not implied as a conclusion. Overstating the implications of descriptive bioinformatics work can mislead readers.
- **Resolution test** Revise the discussion to clearly distinguish between the findings of this study (identification and classification of PAX proteins) and the hypothesis for future work (their potential role in regeneration). Avoid language that implies a functional link without direct evidence.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and accuracy
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "Prediction of snail PAX group proteins in Lisachatina fulica was performed" is grammatically awkward. The species name is misspelled as "Lisachatina" instead of "Lissachatina" in the abstract and in the title.
- **Required correction** Correct the species name spelling throughout. Rephrase the opening sentence, for example: "We performed in silico prediction of PAX family proteins in the land snail *Lissachatina fulica*."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Results, Phylogenetic and BLAST analyses
- **Evidence pointer** Results section, paragraph on phylogenetic analysis
- **Issue** The text states "Afu016671 and Afu016671" twice in the same sentence, where the second instance should presumably be "Afu016672". This appears to be a typographical error.
- **Required correction** Correct the typo to "Afu016671 and Afu016672".

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Materials and Methods, Verification
- **Evidence pointer** Materials and Methods, Verification section
- **Issue** The version of InterProScan is not specified. The authors state that InterPro integrates 13 signature databases, but the current version may integrate more. This is a minor accuracy issue.
- **Required correction** Specify the version of InterProScan used and update the number of integrated databases if necessary.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Supplementary Information
- **Evidence pointer** Supplementary Information section
- **Issue** The supplementary information section states "available at https://doi.org/XXX" with a placeholder DOI. This is not acceptable for a submitted manuscript.
- **Required correction** Provide the actual DOI or a working link to the supplementary materials.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language and style
- **Affected element** Throughout
- **Evidence pointer** Multiple sections
- **Issue** The manuscript contains several typographical and grammatical errors, including "containg" (Introduction), "BALST" (Results heading), "homodomain" (Discussion), and inconsistent use of italics for gene names.
- **Required correction** Perform a thorough language edit to correct all typographical and grammatical errors.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reference accuracy
- **Affected element** Introduction
- **Evidence pointer** Introduction, paragraph on PAX subfamilies
- **Issue** The authors state that "subfamily PAX-β is declared to be specific to the Lophotrochozoa" and cite Schmerer et al. 2009. However, the text does not provide a full reference list in the visible portion of the manuscript. It is unclear whether references are formatted correctly.
- **Required correction** Ensure all references are complete and correctly formatted. Verify that the cited literature supports the specific claims made.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 5
- **Evidence pointer** Results, Discussion
- **Issue** The authors reference Figure 5 as showing the result of 3D structure alignment with an RMSD of 3.940 Å. It is unclear what is being aligned (e.g., the two predicted proteins against each other, or against a known structure). The figure is not visible.
- **Required correction** Clarify in the text what is being aligned in Figure 5 and what the RMSD value represents. Ensure the figure legend is descriptive.

## Risk / unsupported claims
- The claim that eight proteins belong to five PAX subfamilies is unsupported in the visible text because the underlying data (Tables 1–3, Figures 1–5, Supplementary Tables S1–S2) are not provided.
- The claim that docking results indicate "potentially lower affinity" of most predicted proteins for DNA compared to the control is not supported by any statistical analysis or by a clear description of how HADDOCK scores were interpreted.
- The claim that Afu016671 and Afu016672 may be similar to the Drosophila Eyg protein is speculative and based on incomplete domain structure alone; no functional or evolutionary evidence is provided.
- The claim that Afu013869 represents a PAX6 variant with an inserted octapeptide and deleted homeodomain is a hypothesis that cannot be evaluated without the sequence alignment and phylogenetic tree.
- The statement that PAX proteins "likely play a significant part in the regeneration process" in *L. fulica* is an unsupported extrapolation from the known role of PAX genes in eye development in other species.
- The claim that the subfamily PAX-β is "specific to the Lophotrochozoa" is presented as established fact but is not critically discussed in light of the authors' own findings.