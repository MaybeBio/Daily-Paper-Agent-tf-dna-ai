## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and data availability statements.
- **Assessment boundary** The scientific claims, experimental design, data interpretation, and conclusions as presented in the provided manuscript. No external literature or unpublished data were consulted.
- **Shared manuscript claim summary** The authors report that the C-terminal PHDVC5HCH tandem domain of NSD2 is a combinatorial reader of unmodified H3K4 and tri-methylated H3K27 (H3K27me3). They support this with structural, biophysical, and computational data, and further show that mutations disrupting this interaction impair NSD2-dependent upregulation of cell adhesion genes and associated H3K27ac deposition in a multiple myeloma cell model.
- **Visible evidence base** Crystallographic structure (PDB 9GBF), NMR chemical shift assignments (BMRB 51637), NMR titration data, ITC binding data, molecular dynamics simulations, RNA-seq, ChIP-seq, and CUT&RUN data. Data availability statements for GEO and BMRB are provided.
- **Missing materials affecting confidence** Supplementary figures and tables are referenced but not provided. Specific numerical values for some ITC measurements (e.g., Kd for H3K27me3 binding to PHDVC5HCHNSD2) are not fully reported in the main text. Details of the RNA-seq, ChIP-seq, and CUT&RUN analysis pipelines are not fully described. The manuscript does not include a detailed description of the steered MD protocol parameters.

## Reviewer
- **Overall assessment** This manuscript presents a compelling and novel finding: the PHDVC5HCH tandem domain of NSD2 functions as a combinatorial reader of a dual histone mark, unmodified H3K4 and H3K27me3. The biophysical characterization is thorough, and the functional data linking this reading function to transcriptional regulation of adhesion genes in a disease-relevant model adds significant weight. The work is of high technical quality and will be of interest to the chromatin biology and epigenetics communities. However, several concerns regarding the strength of the functional link, the generalizability of the findings, and the completeness of the presented data need to be addressed.
- **Who would be interested in the results, and why** Chromatin biologists, epigeneticists, and cancer researchers, particularly those studying multiple myeloma, histone methylation, and the NSD family of methyltransferases. The finding of a novel combinatorial readout mechanism and its link to a specific transcriptional program in a clinically relevant context will be of broad interest.
- **Major strengths**
    1.  The identification of a novel combinatorial readout mechanism for a PHD tandem domain, specifically the recognition of unmodified H3K4 and H3K27me3, is a significant and original contribution.
    2.  The combination of structural (X-ray), biophysical (NMR, ITC), and computational (MD) methods provides a robust and multi-faceted characterization of the binding mechanism.
    3.  The functional validation in a multiple myeloma cellular model, using point mutants that specifically disrupt the identified interaction, effectively translates the biochemical findings into a disease-relevant context.
    4.  The manuscript is clearly written and logically structured, making a complex story accessible to a broad audience.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Functional validation and causality
    - **Claim pointer** The authors claim that the PHDVC5HCH domain's ability to read H3K27me3 is "critical" for the removal of H3K27me3 and the activation of cell adhesion genes.
    - **Evidence pointer** Results sections "Mutations within PHDVC5HCH affect the expression of NSD2 regulated cell adhesion genes" and "Mutations within PHDVC5HCH of NSD2 result in incomplete loss of H3K27 methylation throughout the genome", Figures 6-8.
    - **Concern** The manuscript demonstrates a strong correlation between the loss of H3K27me3 binding (via point mutations) and the failure to upregulate a subset of genes and to reduce H3K27me3 at those loci. However, the causal link is not fully established. The authors do not show that the PHD domain is directly responsible for recruiting NSD2 to these specific loci. It is possible that the mutations have other, uncharacterized effects on NSD2 function, such as altering its interaction with other proteins or its stability at chromatin. The claim of "critical" is too strong based on the presented data.
    - **Why it matters** The central thesis of the paper is that the reading function of the PHD domain is functionally important for NSD2's oncogenic program. Without direct evidence of recruitment or a more detailed mechanistic link, the conclusion remains correlative.
    - **Resolution test** To strengthen the causal link, the authors could perform ChIP-seq for NSD2 (WT vs. mutants) to demonstrate that the mutants have reduced occupancy at the target gene loci. Alternatively, a more targeted approach, such as an in vitro reconstitution assay or a forced-targeting experiment, could be used to show that the PHD domain is necessary and sufficient for recruitment to H3K27me3-containing chromatin.
    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** No
    - **Axis** Generalizability and disease relevance
    - **Claim pointer** The authors suggest that the PHDVC5HCH domain plays a role in modulating gene expression in multiple myeloma and that its targeting "might constitute a novel intervention strategy against MM."
    - **Evidence pointer** Discussion section, Figure 10.
    - **Concern** The functional studies are performed exclusively in a single cell line (KMS11). While this is a relevant model, the generalizability of the findings to other t(4;14)+ MM cell lines or primary patient samples is not demonstrated. The therapeutic implication is speculative without evidence that this mechanism is broadly operative in the disease.
    - **Why it matters** The clinical relevance of the finding is a key part of the paper's significance. A single cell line is insufficient to establish that this is a general mechanism in MM.
    - **Resolution test** The authors should validate the key findings (gene expression changes, H3K27me3/H3K27ac changes) in at least one additional t(4;14)+ MM cell line. If possible, analysis of patient-derived data (e.g., from public datasets) to show a correlation between NSD2 expression and the expression of the identified adhesion genes would significantly strengthen the disease relevance.
    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Structural and mechanistic detail
    - **Claim pointer** The authors propose a "hierarchical" mechanism for the combinatorial readout, where H3K4 binding is a prerequisite for H3K27me3 recognition.
    - **Evidence pointer** Results section "Three-dimensional model of the double-anchor recognition of H3K27me3 by PHDvC5HCHNSD2", Figure 5.
    - **Concern** The model is based on computational simulations and is not supported by a high-resolution structure of the complex. The claim of a "hierarchical" mechanism is inferred from the MD simulations and the observation that a short H3K27me3 peptide cannot bind. This is a reasonable hypothesis, but it is not directly proven. The authors do not provide a detailed energetic or kinetic analysis of the two binding events.
    - **Why it matters** The proposed mechanism is a key conceptual advance. Without direct structural or detailed biophysical evidence, the "hierarchical" and "cooperative" nature of the interaction remains a model.
    - **Resolution test** A high-resolution co-crystal structure of the PHDVC5HCHNSD2 domain in complex with a dual-modified H3 peptide would be the definitive evidence. Alternatively, a detailed mutational analysis combined with ITC or surface plasmon resonance (SPR) could map the energetic contributions of each binding site and test the proposed hierarchy.
- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Data presentation
    - **Affected element** ITC data
    - **Evidence pointer** Table 2
    - **Issue** The ITC data in Table 2 would be more informative if the stoichiometry (N) and thermodynamic parameters (ΔH, -TΔS) were reported alongside the Kd values. This would provide a more complete picture of the binding energetics.
    - **Required correction** Add the missing thermodynamic parameters to Table 2.
    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Data presentation
    - **Affected element** Supplementary Figures
    - **Evidence pointer** Supplementary Figures S1, S3, S4, S5
    - **Issue** The manuscript relies heavily on supplementary figures for key data, such as the validation of the point mutants (S3) and the details of the MD simulations (S4, S5). These are not available for review.
    - **Required correction** Ensure all supplementary figures are included in the submission for review.
    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Discussion
    - **Evidence pointer** Discussion section
    - **Issue** The discussion of the potential therapeutic implications is somewhat brief and speculative. A more nuanced discussion of the challenges and opportunities of targeting a PHD domain, as opposed to the catalytic SET domain, would be valuable.
    - **Required correction** Expand the discussion on therapeutic implications, addressing the potential challenges of targeting protein-protein interactions like the one described.
    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Methodology
    - **Affected element** CUT&RUN and ChIP-seq
    - **Evidence pointer** Methods section
    - **Issue** The methods for CUT&RUN and ChIP-seq are described briefly. More details on the analysis, such as the exact parameters used for peak calling and the statistical tests used for differential analysis, would improve reproducibility.
    - **Required correction** Provide a more detailed description of the bioinformatics analysis for CUT&RUN and ChIP-seq data.
- **Technical failings that need to be addressed before the case is established**
    - R1-M1: The lack of direct evidence (e.g., NSD2 ChIP-seq) linking the PHD domain's binding to the recruitment of NSD2 at target loci is a significant gap that needs to be filled to support the central claim.
- **Assessment against Nature-style criteria**
    - **Originality** High. The discovery of a PHD tandem domain that combinatorially reads unmodified H3K4 and H3K27me3 is novel and significantly advances the understanding of NSD2 function.
    - **Scientific importance** High. The work provides a mechanistic link between a non-catalytic domain of an oncoprotein and its specific transcriptional output, which has implications for understanding oncogenesis and for therapeutic development.
    - **Interdisciplinary readership** Moderate to High. The work will appeal to structural biologists, biochemists, and molecular biologists, as well as cancer researchers. The clear writing style helps broaden its accessibility.
    - **Technical soundness** High. The biophysical and structural methods are applied rigorously. The functional studies are well-designed, though the causal link could be strengthened.
    - **Readability for nonspecialists** Good. The manuscript is well-written and the figures are clear. The abstract and introduction effectively set the stage for the non-expert.
- **Recommendation posture** Supportive if technical concerns are resolved. The core finding is novel and significant, and the technical quality is high. However, the major concern regarding the causal link between the PHD domain's binding and its functional consequences (R1-M1) needs to be addressed with additional experiments. The generalizability concern (R1-M2) is also important for establishing the full impact of the work.

## Risk / unsupported claims
- The claim that the PHD domain is "critical" for the removal of H3K27me3 and gene activation is not fully supported by the data, which show correlation but not direct causation.
- The claim that targeting the PHD domain "might constitute a novel intervention strategy against MM" is speculative and not supported by any in vivo or therapeutic data.
- The generalizability of the functional findings to multiple myeloma as a whole is not supported, as only one cell line was used.
- The proposed "hierarchical" binding mechanism is a model based on computational and indirect biophysical data, not a directly demonstrated mechanism.