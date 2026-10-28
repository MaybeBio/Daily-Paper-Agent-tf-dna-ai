## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, conclusions, supplementary figure/table legends, and author metadata.
- **Assessment boundary** Scientific validity, methodological rigor, clarity of claims, and alignment of evidence with conclusions. No assessment of editorial fit or publication decision.
- **Shared manuscript claim summary** The authors report that amino acid substitutions in the DNA-binding domains (MATα_HMGbox and HMG-box_ROX1-like) of mating-type proteins MAT1-1-1 and MAT1-2-1 from wild-type *Cordyceps sinensis* isolates and insect–fungal complexes alter the hydrophobicity and secondary/tertiary structures of these domains, as predicted by AlphaFold and ProtScale analyses. They further claim these structural changes may affect DNA-binding affinity and transcriptional regulation during sexual reproduction, and that the proteins originate from heterogeneous fungal sources.
- **Visible evidence base** Abstract; Sections I–IV; Figures 1–16 (referenced, not shown); Tables S1–S8 (referenced, not shown); Figures S1–S3 (referenced, not shown); author contributions; funding; data availability statement.
- **Missing materials affecting confidence** All figures and supplementary tables/figures are referenced but not provided. No sequence alignments, AlphaFold structure files, ProtScale plots, or Bayesian tree images are available for direct inspection. No statistical analysis or quantitative metrics are presented. No raw data or accession numbers are listed in the text.

## Reviewer
- **Overall assessment** The manuscript addresses a potentially interesting topic in fungal reproductive biology, specifically the structural diversity of mating-type protein DNA-binding domains in the economically important *Ophiocordyceps sinensis* complex. However, the current version is largely descriptive and relies heavily on computational predictions without experimental validation. The central claims about functional consequences of amino acid substitutions are speculative and not supported by direct evidence. The manuscript would benefit from substantial revision to clarify methods, present data transparently, and temper conclusions to match the evidence level.
- **Who would be interested in the results, and why** Researchers studying fungal mating-type systems, particularly in entomopathogenic fungi and the *Ophiocordyceps* genus. Those interested in the evolutionary dynamics of mating-type loci in heterothallic fungi and the application of AlphaFold to assess structural impacts of natural sequence variation may also find the approach relevant. The connection to the *C. sinensis* insect–fungal complex and its commercial cultivation adds applied interest for those working on artificial cultivation of this medicinal fungus.
- **Major strengths**
  1. The manuscript addresses a relevant and understudied question about structural diversity in mating-type protein DNA-binding domains in a species complex of high economic and medicinal importance.
  2. The use of publicly available AlphaFold predictions and ProtScale analyses represents a low-cost, accessible approach to generate hypotheses about structural impacts of sequence variation.
  3. The authors acknowledge the complex and impure nature of wild *C. sinensis* samples and attempt to contextualize their findings within the broader discussion of heterothallic versus homothallic reproduction.
  4. The discussion integrates prior work on mating-type gene occurrence and transcription, providing useful context for the field.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The manuscript claims that amino acid substitutions in the DNA-binding domains "result in alterations in the hydrophobicity and the secondary and tertiary structures" and that these changes "ultimately changed the DNA binding affinities, and the functionalities of gene transcriptional regulation."
  - **Evidence pointer** Section III-5, III-6, III-7, III-8; Figures 3–16; Tables S5–S8
  - **Concern** The central claim of structural alteration is based entirely on visual inspection of ProtScale plots and AlphaFold-predicted structures, none of which are shown in the provided text. No quantitative metrics (e.g., RMSD, solvent-accessible surface area changes, free energy calculations) are provided to support the assertion that the substitutions alter tertiary structure. The leap from predicted structural differences to functional consequences on DNA binding and transcriptional regulation is unsupported by any experimental data, binding assays, or functional studies. The claim that "1−3 amino acid substitutions... result in alterations" is presented as a causal relationship, but the evidence is correlational at best.
  - **Why it matters** Without quantitative structural comparisons or functional validation, the core conclusion of the paper is not established. The manuscript cannot support claims about altered DNA-binding affinity or transcriptional regulation based solely on AlphaFold predictions and ProtScale plots. This is a fundamental issue that undermines the scientific contribution.
  - **Resolution test** Provide quantitative structural comparisons (e.g., RMSD between predicted structures, changes in hydrophobicity scores with statistical significance testing). Include experimental validation such as electrophoretic mobility shift assays (EMSA) or surface plasmon resonance to demonstrate altered DNA binding. If functional data are not available, substantially temper the conclusions to state that substitutions "may" affect structure and function, and frame the work as hypothesis-generating.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological transparency
  - **Claim pointer** The methods section describes Bayesian clustering analysis and ProtScale plotting but lacks critical details needed for reproducibility.
  - **Evidence pointer** Section II-4, II-5, II-6
  - **Concern** The methods are described at a level insufficient for replication. For Bayesian clustering, the authors state "the intron regions were removed using trimAl" but do not specify how introns were identified in protein-coding sequences, nor do they provide the alignment length, model parameters beyond the optimal substitution model, or convergence diagnostics for the MCMC analysis. For ProtScale analysis, the specific scales used for hydrophobicity (Kyte-Doolittle is mentioned, but other scales for secondary structure are not specified), window parameters, and normalization procedures are not described. The AlphaFold structure comparison methodology is not described at all; it is unclear how "heteromorphic stereostructures" were compared or classified.
  - **Why it matters** Reproducibility is a cornerstone of scientific publication. The lack of methodological detail prevents other researchers from replicating or building upon this work. It also raises questions about the rigor of the analyses, particularly the classification of structures into "heteromorphic" categories.
  - **Resolution test** Expand the methods to include: (1) full parameters for MAFFT and trimAl, including how intron boundaries were determined; (2) ProtScale parameters including all scales used, window size justification, and any normalization; (3) a clear description of how AlphaFold structures were compared, including any alignment algorithms, similarity metrics, and thresholds for classifying structures as "heteromorphic"; (4) accession numbers for all sequences and AlphaFold models used.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Data availability and transparency
  - **Claim pointer** The manuscript references Figures 1–16 and Tables S1–S8, but none of these are available in the provided text.
  - **Evidence pointer** Sections III-1 through III-9; Figures 1–16; Tables S1–S8
  - **Concern** The results section is written as a narrative describing figures and tables that are not included in the provided manuscript text. This makes it impossible to evaluate the validity of the claims. For example, the Bayesian clustering trees (Figures 1–2) are described but cannot be inspected for branch support or topology. The ProtScale plots (Figures 3–16) are described but cannot be assessed for the claimed changes in hydrophobicity or secondary structure. The alignment figures (Figures S1–S2) are referenced but not shown.
  - **Why it matters** Peer review requires access to the data and figures to assess whether the conclusions are supported by the evidence. Without these materials, the manuscript cannot be properly evaluated. This is a blocking issue for the review process.
  - **Resolution test** Provide all figures and supplementary materials for review. Ensure that all figures are legible and that the data presented in tables are complete and clearly formatted.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Overinterpretation of computational predictions
  - **Claim pointer** The discussion states that "the diversity of heteromorphic MATα_HMGbox domains of the mating proteins present in wild-type C. sinensis isolates may lead to stereostructure-related functional alterations in the mating process" and that these "may indicate that mating proteins from heterogeneous fungal sources may accomplish coordinated heterothallic or hybrid reproduction."
  - **Evidence pointer** Section IV-1, IV-3
  - **Concern** The manuscript moves from describing sequence variation and predicted structural differences to speculating about functional consequences and reproductive implications without any intermediate evidence. The use of AlphaFold predictions as a proxy for actual protein structure is a significant limitation that is not adequately acknowledged. AlphaFold predictions are computational models and may not accurately represent the true in vivo structures, particularly for proteins that undergo conformational changes upon DNA binding. The discussion of heterothallic reproduction and hybrid strategies goes beyond what the data can support.
  - **Why it matters** Overinterpretation of computational results can mislead the field and lead to unsupported conclusions being cited in future work. The manuscript should clearly distinguish between what is demonstrated (sequence variation exists) and what is speculative (functional consequences of that variation).
  - **Resolution test** Revise the discussion to clearly separate observed findings from hypotheses. Add explicit statements about the limitations of AlphaFold predictions. Consider adding a "Limitations" section that acknowledges the lack of experimental validation and the speculative nature of functional claims.
  - **Concern ID** R1-M5
  - **Severity** Major
  - **Blocking** No
  - **Axis** Statistical rigor
  - **Claim pointer** The manuscript claims that substitutions "result in alterations" and that different structures cluster into distinct Bayesian clades, but no statistical support is provided.
  - **Evidence pointer** Sections III-1 through III-8; Figures 1–2; Tables S5–S8
  - **Concern** No statistical analyses are presented anywhere in the manuscript. The Bayesian clustering analysis presumably provides posterior probabilities, but these are not reported. The claim that proteins cluster into distinct clades is not supported by any quantitative measure of clade support. The comparison of ProtScale plots is entirely qualitative. There is no assessment of whether the observed differences in hydrophobicity or secondary structure predictions are statistically significant or within the range of normal variation.
  - **Why it matters** Without statistical support, the reader cannot distinguish between meaningful structural differences and random variation. The manuscript's conclusions depend on the significance of the observed differences, which is not established.
  - **Resolution test** Report posterior probabilities for all clades in the Bayesian trees. Provide quantitative comparisons of ProtScale plots, including confidence intervals or statistical tests where appropriate. If the sample sizes are too small for statistical analysis, acknowledge this limitation explicitly.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of terminology
  - **Affected element** Abstract and throughout
  - **Evidence pointer** Abstract, Section I
  - **Issue** The term "stereostructures" is used throughout but is not standard in structural biology. The more common terms are "three-dimensional structures" or "tertiary structures." The term "heteromorphic" is also used frequently but its specific meaning in this context is not defined.
  - **Required correction** Define "stereostructures" and "heteromorphic" at first use, or replace with more standard terminology such as "three-dimensional structures" and "structurally distinct."
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Nomenclature consistency
  - **Affected element** Section I
  - **Evidence pointer** Section I, paragraph 1
  - **Issue** The authors discuss the naming of *Ophiocordyceps sinensis* versus *Cordyceps sinensis* at length, but the rationale for using "C. sinensis" for the insect–fungal complex while using "O. sinensis" for the fungus is not consistently applied throughout the manuscript. For example, the title uses "Cordyceps sinensis insect‒fungal complex" while the abstract refers to "Ophiocordyceps sinensis."
  - **Required correction** Ensure consistent use of nomenclature throughout, or provide a clear statement of the naming convention at the beginning of the manuscript.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reference accuracy
  - **Affected element** Section IV-2
  - **Evidence pointer** Section IV-2, paragraph 2
  - **Issue** The authors cite "Li et al. [2016b]" for a study on *C. sinensis* isolates, but the reference list is not provided in the manuscript text. It is unclear whether this citation is accurate and whether the described findings (coexistence of multiple genotypes) are correctly attributed.
  - **Required correction** Provide a complete reference list and verify all citations for accuracy.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Language and grammar
  - **Affected element** Throughout
  - **Evidence pointer** Abstract, Sections I–IV
  - **Issue** The manuscript contains numerous grammatical errors and awkward phrasings that impede readability. Examples include "the MATα_HMGbox domains of MAT1-1 proteins (amino acids 51→225 of the reference sequence AGW27560 derived from the H. sinensis strain CS68-2-1229 [Bushley et al. 2013])" which is a very long and convoluted sentence, and "Apperantly" (misspelling of "Apparently") in Section IV-3.
  - **Required correction** Thorough proofreading and editing for grammar, spelling, and clarity. Consider restructuring long sentences for readability.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Figure quality and accessibility
  - **Affected element** Figures 1–16
  - **Evidence pointer** Sections III-5 through III-8
  - **Issue** The figures are not provided, but based on the text descriptions, they appear to be complex multi-panel figures. It is unclear whether the ProtScale plots and 3D structure representations would be legible in print or online formats.
  - **Required correction** Ensure all figures are high-resolution and legible. Consider providing separate panels for each comparison to avoid overcrowding.
  - **Concern ID** R1-m6
  - **Severity** Minor
  - **Axis** Data availability statement
  - **Affected element** Data Availability Statement
  - **Evidence pointer** Data Availability Statement
  - **Issue** The data availability statement mentions that one set of metatranscriptome sequences is currently inaccessible. This is a potential issue for reproducibility, as the authors used these data for their analysis.
  - **Required correction** Provide the data as supplementary material or in a public repository, or clearly state the limitations this imposes on the analysis.
- **Technical failings that need to be addressed before the case is established**
  1. No quantitative comparison of AlphaFold-predicted structures (R1-M1).
  2. No statistical support for clustering or structural differences (R1-M5).
  3. Insufficient methodological detail for reproducibility (R1-M2).
  4. Figures and tables not available for review (R1-M3).
  5. No experimental validation of functional claims (R1-M1, R1-M4).
- **Assessment against Nature-style criteria**
  - **Originality** The application of AlphaFold to assess structural impacts of natural sequence variation in mating-type proteins is not entirely novel, but the specific focus on *O. sinensis* and the integration with Bayesian clustering is somewhat distinctive. However, the approach is largely descriptive and does not introduce new methods or concepts.
  - **Scientific importance** The topic is of interest to fungal biologists and those studying the *C. sinensis* complex, but the findings are primarily descriptive and do not provide fundamental new insights into mating-type biology or protein structure-function relationships. The lack of experimental validation limits the significance of the claims.
  - **Interdisciplinary readership** The manuscript is likely to appeal primarily to specialists in fungal reproductive biology and *Ophiocordyceps* research. The heavy reliance on computational predictions without experimental context may limit broader appeal to structural biologists or evolutionary biologists.
  - **Technical soundness** The technical approach is reasonable as a hypothesis-generating exercise, but the lack of quantitative analysis, statistical support, and methodological detail undermines the technical rigor. The overinterpretation of computational predictions is a significant concern.
  - **Readability for nonspecialists** The manuscript is written in a dense, technical style that assumes significant background knowledge. The long, convoluted sentences and inconsistent terminology make it difficult to follow even for specialists. The abstract is somewhat more accessible but still contains jargon.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a descriptive analysis of sequence variation and computational structure predictions, but the central claims about structural and functional consequences are not supported by the evidence provided. Major revisions are required to address the concerns outlined above, particularly the lack of quantitative analysis, methodological transparency, and experimental validation. If the authors can provide the missing data, strengthen the analysis, and temper their conclusions, the work could potentially be suitable for publication in a specialized journal, though it is unlikely to meet the bar for a high-impact general journal.

## Risk / unsupported claims
- The claim that amino acid substitutions "result in alterations" in secondary and tertiary structure is unsupported without quantitative comparison of AlphaFold models or experimental structural data.
- The claim that structural changes "ultimately changed the DNA binding affinities, and the functionalities of gene transcriptional regulation" is entirely speculative and not supported by any functional data.
- The claim that mating proteins arise from "heterospecific fungal sources" is not directly supported by the data presented, as the analysis relies on sequence comparisons without definitive species identification.
- The assertion that the observed structural diversity "may lead to stereostructure-related functional alterations in the mating process" is presented as a conclusion but is only a hypothesis.
- The statement that "the observed variation in the stereostructures of the DNA-binding domains... suggest that the mating proteins arise from diverse fungal sources" overreaches the evidence, as sequence variation alone does not establish source diversity.
- The claim that "the mutant mating proteins... represent the changed functionalities of the proteins in regulating and ensuring the accuracy and genetic diversity of the heterothallic and hybrid sexual reproductive processes" is not supported by any experimental or functional evidence.