## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results, discussion, conclusion, and supplementary figure/table legends. No supplementary files were provided for review.
- **Assessment boundary** The review is limited to the content presented in the supplied manuscript text. Claims regarding experimental procedures, data analysis, and conclusions are assessed based on the information available in the text alone.
- **Shared manuscript claim summary** The authors report a genome-wide identification of 177 GRAS transcription factor genes in hexaploid wheat, their phylogenetic classification into 14 subfamilies, analysis of gene structure, conserved motifs, chromosomal distribution, duplication events, promoter cis-elements, miRNA targeting, in-silico expression profiling, qRT-PCR validation under drought, salt, and heat stress, and molecular dynamics simulations of three GRAS proteins. They propose TaGRAS27 as a candidate gene for improving abiotic stress tolerance in wheat.
- **Visible evidence base** The manuscript text includes descriptions of results, figures (Figs 1–7), supplementary tables (S1–S7), and supplementary figures (S1–S6). However, none of the actual figures, tables, or supplementary data files were provided for this review. The evidence base is therefore limited to the textual descriptions of these results.
- **Missing materials affecting confidence** All figures, tables, and supplementary data files are missing. This includes the phylogenetic tree (Fig 1), chromosomal distribution map (Fig 2), synteny plots (Fig 3, 4), expression heatmaps (Supplementary Fig 6), qRT-PCR data (Fig 6, Supplementary Figs 7–8), MD simulation trajectories (Fig 7, Table 3), and all supplementary tables (S1–S7). Without these, the accuracy of the reported numbers, the quality of the analyses, and the validity of the conclusions cannot be independently verified.

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive bioinformatics-driven characterization of the GRAS gene family in wheat, a topic of potential interest to the plant stress biology community. The authors have employed a standard suite of computational tools for gene family analysis and have supplemented this with qRT-PCR expression data under three abiotic stress conditions. However, the manuscript has several significant weaknesses that currently prevent it from being considered a robust contribution. The most critical issues are the lack of methodological detail in several key areas, the absence of statistical analysis for the expression data, the unclear presentation of the MD simulation results, and the lack of any functional validation beyond expression profiling. The claim that TaGRAS27 is a candidate gene for improving stress tolerance is not supported by the evidence presented, which is largely descriptive. The manuscript would require substantial revision, including the addition of missing methodological information, proper statistical treatment of data, and a more cautious interpretation of the results, before it could be considered for publication.
- **Who would be interested in the results, and why** Researchers working on plant transcription factor families, particularly GRAS genes, would find this manuscript of interest as a reference for the wheat GRAS family. The phylogenetic classification, gene structure analysis, and identification of stress-responsive candidates could serve as a starting point for more detailed functional studies. Additionally, researchers interested in the evolutionary dynamics of gene families in polyploid genomes, and those working on wheat stress tolerance breeding, may find the catalog of stress-responsive GRAS genes and the proposed candidate TaGRAS27 useful for further investigation.
- **Major strengths** The manuscript addresses a relevant topic and provides a systematic genome-wide analysis of a gene family in an important crop. The use of the latest wheat genome assembly (IWGSC_v2.1) is a positive aspect. The combination of in-silico prediction with qRT-PCR validation for a subset of genes is a reasonable approach. The inclusion of MD simulations, while not fully described, is an attempt to add structural insights, which is a step beyond standard gene family analyses.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical soundness
    - **Claim pointer** The manuscript claims to have identified 177 GRAS genes in wheat, but the text also states that three genes (TaGRAS71, TaGRAS72, TaGRAS103) were excluded due to short sequence lengths, leading to a discrepancy in the total count.
    - **Evidence pointer** Results section "Identification and annotation of TaGRAS genes in wheat", location not provided.
    - **Concern** The manuscript states "we identified 177 wheat genes... designated as TaGRAS1 to TaGRAS180" and then states "the sequence lengths of three genes, namely TaGRAS71, TaGRAS72, and TaGRAS103, were relatively short, posing challenges to the alignment procedure. Therefore... these genes were excluded from further analysis." This is a direct numerical contradiction. If 180 genes were initially identified and named, and three were excluded, the final number should be 177, but the naming convention (TaGRAS1 to TaGRAS180) implies 180 genes. The authors must clarify the total number of genes identified, the number excluded, and the final number analyzed. This inconsistency undermines the accuracy of the entire dataset.
    - **Why it matters** A core claim of the paper is the identification of a specific number of GRAS genes. A numerical inconsistency in this central result raises questions about the rigor of the data curation and analysis process, and makes it difficult for readers to trust the subsequent analyses.
    - **Resolution test** The authors must provide a clear and consistent count of the total number of GRAS genes identified, the number excluded, and the final number used in each analysis. The naming convention should be consistent with the final count.
    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical soundness
    - **Claim pointer** The manuscript claims that qRT-PCR results show significant differential expression of GRAS genes under drought, salt, and heat stress, and that TaGRAS27 is a promising candidate for enhancing stress tolerance.
    - **Evidence pointer** Results section "TaGRAS genes are involved in the response to abiotic stresses", Figure 6, location not provided.
    - **Concern** The qRT-PCR results are described only in terms of "fold change" or "expression level" without any mention of statistical tests, error bars, or the number of biological replicates used in the analysis. The methods section mentions "three biological replicates of each genotype," but the results do not present any measure of variability (e.g., standard deviation, standard error) or statistical significance (e.g., p-values). Without this information, it is impossible to determine if the observed expression changes are meaningful or simply biological noise. The claim that TaGRAS27 is a "candidate gene" is based on this unvalidated expression data.
    - **Why it matters** The central functional claim of the paper, that specific GRAS genes respond to abiotic stress, rests entirely on the qRT-PCR data. Without proper statistical validation, the conclusion is not supported by the evidence. The identification of TaGRAS27 as a candidate for breeding is a strong claim that requires robust evidence.
    - **Resolution test** The authors must present qRT-PCR data with measures of variability (e.g., error bars) and the results of appropriate statistical tests (e.g., t-test, ANOVA) comparing stressed vs. control conditions for each gene and time point. The number of biological and technical replicates must be clearly stated.
    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical soundness
    - **Claim pointer** The manuscript claims to have performed molecular dynamics simulations to study GRAS domain-DNA interactions, and that the results provide information about protein stability and structural changes.
    - **Evidence pointer** Methods section "Molecular modelling and molecular dynamics (MD) simulations", Results section "MD simulation analysis", Figure 7, Table 3, location not provided.
    - **Concern** The MD simulation section is severely under-described. The methods do not state which three GRAS proteins were selected for simulation or the rationale for their selection. The simulation parameters are incomplete (e.g., the force field is mentioned, but the simulation time is only implied to be 20 ns). The results are presented as a narrative description of RMSD and RMSF values without any clear link to a biological question or hypothesis. The selection of only three proteins out of 177, without justification, makes the analysis seem arbitrary. The connection between the MD results and the stress response is not made clear.
    - **Why it matters** The MD simulation is presented as a novel aspect of the study, but as presented, it is an isolated analysis that does not contribute to the main narrative of stress response. The lack of methodological detail and clear rationale prevents the reader from evaluating the validity or significance of the results.
    - **Resolution test** The authors must clearly state which proteins were simulated and why. They must provide complete simulation parameters. The results should be interpreted in the context of the GRAS protein function and the stress response, explaining what the structural stability or flexibility of these specific proteins tells us about their potential role.
    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Originality / Scientific importance
    - **Claim pointer** The manuscript claims to be the first systematic study of the GRAS gene family in wheat, including molecular dynamics modeling.
    - **Evidence pointer** Abstract, Introduction, Discussion, location not provided.
    - **Concern** The authors state in the abstract that "no systematic study of the GRAS gene family and their functions under heat, drought, and salt stress tolerance and molecular dynamics modeling in wheat has been reported." However, in the discussion, they cite two previous studies on the wheat GRAS gene family (Liu et al., 2022; Kumar et al., 2022). While the authors argue their study is different (e.g., using a newer genome assembly, adding MD simulations), the claim of being the "first" is overstated and not accurate given the existence of prior systematic studies. The novelty of this work is incremental, not absolute.
    - **Why it matters** The claim of being the first to do a systematic study is a strong statement of novelty. If this is not accurate, it misrepresents the contribution of the work. The actual novelty, such as the use of a new assembly or the addition of MD simulations, should be stated more precisely.
    - **Resolution test** The authors should revise their claims of novelty to accurately reflect the existing literature. They should clearly state what their study adds beyond the previous reports, such as the use of a newer genome assembly, the specific stress conditions tested, or the new structural insights from MD simulations.
- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Readability for nonspecialists
    - **Affected element** Abstract and Introduction
    - **Evidence pointer** Abstract, Introduction, location not provided.
    - **Issue** The abstract and introduction are dense and contain several grammatical errors and awkward phrasings that impede readability. For example, "is an rich source" in the introduction and the sentence "using transgenic technology to develop stress-tolerant cultivars is a viable option" are grammatically incorrect. The flow of the introduction could be improved to provide a clearer rationale for the study.
    - **Required correction** The manuscript should be carefully edited for grammar and clarity. Sentences should be restructured to improve flow and readability for a broad scientific audience.
    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Technical soundness
    - **Affected element** Methods section "Identification and annotation of TaGRAS genes in wheat"
    - **Evidence pointer** Methods, location not provided.
    - **Issue** The methods for identifying GRAS genes are described briefly. It is not clear what specific criteria were used to confirm a gene as a GRAS gene (e.g., presence of the GRAS domain, E-value thresholds for the HMM search). The source of the wheat proteome is given as a URL, but the version is not specified in the text (though the discussion mentions IWGSC_v2.1).
    - **Required correction** The authors should provide more detail on the identification criteria, including the HMM model used, the E-value cutoffs, and the confirmation steps. The exact version of the wheat genome assembly used should be stated in the methods.
    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Technical soundness
    - **Affected element** Results section "Identification of orthologous and paralogous GRAS genes"
    - **Evidence pointer** Results, location not provided.
    - **Issue** The text states that "Ka_Ks ratios were generally greater than 1 for segmentally duplicated TaGRAS gene pairs" and then concludes that "these results suggested that the TaGRAS gene family may have been the target of strong purifying selection during evolution." This is contradictory. A Ka/Ks ratio greater than 1 indicates positive or diversifying selection, not purifying selection, which is indicated by a ratio less than 1.
    - **Required correction** The authors must correct this error. If the Ka/Ks ratios are indeed greater than 1, the conclusion should be about positive selection. If they meant purifying selection, the data must be re-evaluated and the text corrected.
    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Readability for nonspecialists
    - **Affected element** Results section "TaGRAS genes are involved in the response to abiotic stresses"
    - **Evidence pointer** Results, Figure 6, location not provided.
    - **Issue** The text describing the qRT-PCR results is confusing. It mentions different genotypes for different stresses (e.g., C306 and WL711 for drought, HD2009 and KRL213 for salt, RAJ3765 and HS277 for heat), but the figure legend for Figure 6 mentions different genotype names (e.g., Kharchia65 and HD2687 for salt). This inconsistency makes it difficult to follow which data corresponds to which experiment.
    - **Required correction** The authors must ensure consistency between the text, the figure legends, and the figures themselves regarding the genotypes used for each stress treatment.

## Risk / unsupported claims
- The claim that "TaGRAS27 is a candidate gene for functional research, and to improve abiotic stress tolerance in the wheat by molecular breeding" is unsupported by the data presented. The evidence is limited to expression analysis, which is correlative, not functional.
- The claim that the MD simulation results "will pave the way for researchers to investigate the interaction between the GRAS domain and DNA and discover critical residues involved in maintaining the interaction" is speculative and not supported by the presented data, which is a basic stability analysis.
- The numerical claim of identifying 177 GRAS genes is internally inconsistent with the text describing the exclusion of three genes from a set of 180.
- The conclusion that "tandem and segmental duplication played a role in the growth of the TaGRAS family" is a standard interpretation but is not strongly supported by the data presented in the text, as the actual analysis is not shown.
- The statement that "the majority of the identified GRAS genes exhibited significant differential expression" is unsupported as no statistical analysis is presented.
- The claim of being the "first" to perform a systematic study with MD modeling is not supported given the cited prior studies on the wheat GRAS family.

## Assessment against Nature-style criteria
- **Originality**: The work is largely confirmatory and incremental. While the use of the latest genome assembly and the addition of MD simulations provide some novelty, the core analysis (identification, phylogeny, expression) has been reported for wheat and many other species. The claim of being the first is not accurate.
- **Scientific importance**: The identification of stress-responsive GRAS genes in wheat has potential utility for the plant breeding community. However, the lack of functional validation limits the immediate importance of the findings. The study is primarily a descriptive catalog.
- **Interdisciplinary readership**: The topic is of interest to plant molecular biologists, geneticists, and breeders. The use of bioinformatics and MD simulations could appeal to computational biologists, but the limited depth of the MD analysis may not satisfy that audience.
- **Technical soundness**: The technical soundness is currently questionable due to the numerical inconsistency in gene counts, the lack of statistical analysis for expression data, the incomplete description of the MD methods, and the contradictory interpretation of Ka/Ks ratios. The manuscript requires significant corrections to be considered technically sound.
- **Readability for nonspecialists**: The manuscript is written in a style that is generally accessible but is hampered by grammatical errors and some confusing passages. The flow could be improved to make the rationale and conclusions clearer.

## Recommendation posture
Currently not established from the provided evidence. The manuscript addresses a relevant topic and has the potential to be a useful resource, but it has several major technical flaws and unsupported claims that must be addressed. The numerical inconsistency in the core gene count, the lack of statistical validation for the key expression results, and the incomplete and contradictory methodological details prevent the conclusions from being supported. A major revision is required to address these concerns before the manuscript can be considered for publication.