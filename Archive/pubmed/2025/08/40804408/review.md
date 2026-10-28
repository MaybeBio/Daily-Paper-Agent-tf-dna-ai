## Review setup
- **Input scope** Full manuscript text, including abstract, background, methods, results, discussion, conclusions, and supplementary information descriptions.
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and alignment with stated objectives. Editorial and formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors use computational approaches (multiple sequence alignment, phylogenetics, structural modeling with AlphaFold3) to identify conserved residues in the HPV E2 protein across human Alpha, Beta, and Gamma genera. They report that conserved residues cluster near the DNA-binding surface in the C-terminal domain and at critical interaction sites in the N-terminal transactivation domain. They further characterize a T309P substitution in HPV52 sublineage B2, predicting structural changes that may affect DNA-binding function and oncogenic potential.
- **Visible evidence base** Full manuscript text, including two tables of conserved residues, seven figures (genome maps, phylogenetic tree, structural models, contact maps, DNA shape analyses), and descriptions of three supplementary files.
- **Missing materials affecting confidence** Supplementary files (Additional files 1-3) were not provided for direct inspection. Raw sequence data, alignment files, AlphaFold3 prediction parameters, and validation metrics beyond pLDDT scores were not available. No experimental validation data were presented.

## Reviewer

- **Overall assessment** This manuscript presents a computational analysis of sequence conservation in the HPV E2 protein and uses structural modeling to infer functional significance. The topic is relevant to the virology community, and the multi-scale approach from genus-level conservation to specific variant analysis is conceptually sound. However, the study is entirely computational and descriptive, with no experimental validation. The central claims regarding the functional impact of the T309P variant are speculative and not supported by direct evidence. The manuscript would benefit from substantial revision to clarify the novelty of the findings relative to existing literature, strengthen the analytical rigor, and temper conclusions to match the evidence level.

- **Who would be interested in the results, and why** Researchers studying HPV biology, particularly those focused on E2 structure-function relationships, viral pathogenesis, and genotype-specific differences in oncogenic risk. The conservation data and structural models may serve as a reference for those designing mutagenesis studies or therapeutic interventions targeting E2. Clinically oriented investigators interested in HPV52 variants and their association with cancer in East Asian populations may also find the T309P analysis relevant.

- **Major strengths**
  1. The multi-scale analytical approach, moving from broad genus-level conservation to specific variant analysis, provides a logical framework.
  2. The use of up-to-date computational tools (AlphaFold3, GROMACS, DNAproDB) is appropriate for the stated aims.
  3. The inclusion of both solved crystal structures and predicted models strengthens the structural analysis.
  4. The identification of native proline at the T309-homologous position in HPV33 and HPV58 is an interesting observation that adds context to the HPV52 variant discussion.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that the T309P substitution "likely induces conformational changes within the DNA-binding domain that may impact its regulatory functions" and links this to "increased oncogenic risk."
- **Evidence pointer** Results section, Figure 7, Discussion
- **Concern** The functional significance of the T309P variant is presented as a central finding, yet the evidence is limited to AlphaFold3-predicted structural differences between wild-type and variant models. AlphaFold3 is a prediction tool, not an experimental method, and its accuracy for assessing the impact of single amino acid substitutions is not well established. The predicted "kink" and secondary structure changes are based on computational inference without experimental corroboration (e.g., circular dichroism, NMR, X-ray crystallography, or DNA-binding assays). Furthermore, the association between T309P and "increased oncogenic risk" is cited from epidemiological studies of the HPV52 B2 sublineage, but no direct evidence links this specific residue change to altered E2 function or oncogenicity.
- **Why it matters** The manuscript's conclusion that T309P "may impact its regulatory functions" and the implication that this contributes to oncogenic potential is a strong claim that cannot be supported by computational modeling alone. Overinterpretation of predicted structural changes as functional consequences risks misleading readers and overstating the significance of the findings.
- **Resolution test** The authors should either (a) provide experimental data demonstrating functional differences between T309 and P309 E2 variants (e.g., DNA-binding affinity, transcriptional repression activity, replication assays), or (b) substantially temper the language to clearly state that the functional consequences are hypothetical and require experimental validation. The claim of "increased oncogenic risk" should be explicitly separated from the structural predictions and presented only as an epidemiological association.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Novelty and literature integration
- **Claim pointer** The manuscript presents the identification of conserved residues and their structural mapping as a novel contribution, stating that previous research "suggests that mutations within a 12-base pair segment of the long control region that encompasses the E2 binding sites may influence the oncogenic potential of certain HPV strains."
- **Evidence pointer** Background, Results, Discussion
- **Concern** The manuscript does not adequately differentiate its findings from prior published work on HPV E2 conservation and structure. The E2 protein has been extensively studied for decades, and multiple structural and functional analyses of conserved residues exist in the literature. The authors cite some foundational work (e.g., Gaston lab, Morgan lab) but do not systematically compare their conservation results with previously published mutagenesis data or structural studies. The claim that this study "refines our understanding" is not substantiated by a clear statement of what new information is being added beyond what is already known.
- **Why it matters** For a computational study with no experimental component, the novelty must be clearly established through comprehensive comparison with existing data. Without this, the contribution is largely confirmatory rather than innovative, which weakens the case for publication in a high-impact venue.
- **Resolution test** The authors should add a dedicated section comparing their conservation findings with published experimental data on E2 residues (e.g., known functional mutants, disease-associated variants). They should explicitly state which findings are novel and which confirm prior work. If the conservation analysis largely recapitulates known information, the manuscript should be reframed to emphasize the specific new contributions (e.g., the T309P structural analysis or the genus-level comparison).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological transparency
- **Claim pointer** The methods state that "Structural modeling using AlphaFold3" was performed, and that "further structural analyses of the AlphaFold-predicted models, including the corroboration of backbone dihedral angles and hydrogen bond patterns, were performed using GROMACS."
- **Evidence pointer** Methods section, Structural modeling and analysis
- **Concern** The description of the structural modeling and analysis is insufficiently detailed for reproducibility. Key parameters are missing, including: the specific AlphaFold3 version and settings used, the sequence input format, whether multiple models were generated and how the best model was selected, the criteria for defining "conserved residue clusters," and the specific GROMACS commands and force field parameters used. The statement that GROMACS was used to "corroborate" AlphaFold predictions is unclear, as GROMACS is a molecular dynamics package, not a structure validation tool per se. The use of DSSP for secondary structure assignment is appropriate, but the workflow from AlphaFold3 output to GROMACS analysis to final structural interpretation is not clearly described.
- **Why it matters** Reproducibility is a core requirement for computational studies. Without detailed methodological information, other researchers cannot replicate the analysis or assess its validity. The unclear role of GROMACS in the workflow raises questions about whether the analyses were performed appropriately.
- **Resolution test** The authors should provide a detailed, step-by-step description of the computational workflow, including software versions, parameters, and analysis criteria. If GROMACS was used for energy minimization or short MD simulations to relax the AlphaFold models, this should be stated explicitly with appropriate parameters. Alternatively, if GROMACS was used only for dihedral angle analysis, this should be clarified.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical and quantitative rigor
- **Claim pointer** The manuscript reports that threonine at the T309-homologous position is present in only ~2.3% of analyzed types, proline in ~1.9%, and lysine in ~60.9%.
- **Evidence pointer** Results section, Sequence variation at the HPV52 E2 T309 homologous locus
- **Concern** The manuscript presents these percentages as descriptive statistics without any measure of uncertainty or statistical testing. It is unclear whether these frequencies are based on the full 215-sequence dataset or a subset. The claim that lysine is "the most prevalent amino acid" is presented without confidence intervals or a formal test of whether this prevalence differs significantly from what would be expected by chance. Additionally, the manuscript does not report the total number of sequences analyzed at this position, which is important because alignment gaps or missing data could affect the percentages.
- **Why it matters** The frequency data at the T309 locus is used to support the argument that the proline substitution is unusual and potentially significant. Without proper statistical context, this argument is weakened. The lack of quantitative rigor undermines the reliability of the conclusions drawn from this analysis.
- **Resolution test** The authors should report the exact number of sequences analyzed at this position, provide confidence intervals for the reported frequencies, and perform a simple statistical test (e.g., chi-square or Fisher's exact test) to assess whether the distribution of amino acids at this position deviates from expected frequencies. If the analysis is purely descriptive, this should be stated explicitly.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and terminology
- **Affected element** Abstract and Background
- **Evidence pointer** Abstract, Background section
- **Issue** The abstract states that the study identifies "conserved residues" and their "structural and functional roles," but the manuscript does not experimentally test function. The term "functional roles" is used throughout without clear distinction between experimentally validated functions and computationally inferred roles.
- **Required correction** Revise the language throughout to distinguish between experimentally established functions (from cited literature) and computationally predicted or inferred roles. For example, use "predicted functional significance" or "inferred structural roles" where appropriate.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure quality and accessibility
- **Affected element** Figures 5 and 6
- **Evidence pointer** Results section, Figures 5 and 6
- **Issue** The residue-nucleotide contact maps and DNA helical parameter plots are described as generated by DNAproDB, but the figures are not included in the provided manuscript text. The descriptions suggest complex multi-panel figures, but without seeing them, it is difficult to assess their clarity and whether they effectively communicate the intended information.
- **Required correction** Ensure that the figures are legible at publication resolution, with clear labels for all residues, nucleotides, and structural elements. Consider adding a simplified schematic summary figure that highlights the key findings for nonspecialist readers.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reference accuracy
- **Affected element** Discussion section
- **Evidence pointer** Discussion, paragraph on T309P
- **Issue** The manuscript cites references [42, 43] for the association of the HPV52 B2 sublineage with "heightened pathogenic potential," but the specific nature of these studies (e.g., epidemiological, clinical, molecular) is not described. This makes it difficult to assess the strength of the evidence.
- **Required correction** Briefly describe the nature of the cited studies when introducing this association, and note any limitations (e.g., sample size, population specificity, lack of functional data).

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Supplementary material accessibility
- **Affected element** Additional files 1-3
- **Evidence pointer** Supplementary Information section
- **Issue** The supplementary files are described as PDF documents containing alignments and sequence lists. While this is acceptable, machine-readable formats (e.g., FASTA, ALN) would facilitate reuse by the community.
- **Required correction** Consider providing the alignments in a standard machine-readable format in addition to PDF, and ensure that the supplementary files are clearly referenced at the appropriate points in the main text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language and readability
- **Affected element** Throughout
- **Evidence pointer** Multiple sections
- **Issue** Some sentences are overly long and complex, which may impede readability for nonspecialists. For example, the sentence in the Discussion beginning "Our comparative analysis reinforces..." contains multiple clauses and could be broken into shorter sentences.
- **Required correction** Revise for clarity and conciseness. Aim for shorter sentences and clearer logical flow, particularly in the Discussion section where complex ideas are synthesized.

## Risk / unsupported claims
- The claim that T309P "likely induces conformational changes within the DNA-binding domain that may impact its regulatory functions" is unsupported by direct experimental evidence and relies entirely on AlphaFold3 predictions.
- The implication that T309P contributes to "increased oncogenic risk" conflates epidemiological association with causal mechanism and is not supported by functional data.
- The statement that conserved residues "cluster near the DNA-binding surface" and "at critical interaction sites" is based on structural modeling and literature inference, but the manuscript does not provide quantitative measures of clustering or direct evidence of functional importance.
- The claim that "species-specific adaptations... could modulate oncogene expression" is speculative and not directly tested.
- The assertion that "conserved regions represent attractive therapeutic targets" is a reasonable suggestion but is not supported by any drug design or targeting analysis within this study.
- The manuscript's statement that previous research from the authors' laboratory "suggests that mutations within a 12-base pair segment... may influence oncogenic potential" is referenced but not described in sufficient detail to evaluate its relevance to the current findings.