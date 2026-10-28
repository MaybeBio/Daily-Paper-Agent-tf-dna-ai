## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, materials and methods, and supplementary text description
- **Assessment boundary** Scientific validity of claims, experimental design, data interpretation, and consistency between results and conclusions
- **Shared manuscript claim summary** The authors report identification of small-molecule compounds that compete with Apicomplexan AP2 (ApiAP2) transcription factor DNA binding domains in Plasmodium falciparum, with in vitro binding competition, transcriptomic perturbation consistent with AP2-EXP target gene dysregulation, and multi-stage antiplasmodial activity including mosquito-stage P. berghei development inhibition
- **Visible evidence base** In silico docking screen description, EMSA competition data (referenced figures), growth inhibition IC50 values, transcriptomic microarray analysis, ChIP-seq peak calling and comparison, mosquito-stage P. berghei injection assays, molecular dynamics simulations
- **Missing materials affecting confidence** Actual figures and supplementary tables not provided; raw data files not accessible; ChIP-seq quality metrics not shown; statistical details for transcriptomic analyses not fully described; compound structural information not shown; dose-response curves not visible

## Reviewer
- **Overall assessment** This manuscript presents a potentially interesting approach to targeting ApiAP2 transcription factors in Plasmodium, a parasite-specific protein family with no human homologs. The combination of in silico docking, biochemical validation, transcriptomic correlation, and in vivo mosquito-stage testing is commendable in scope. However, several critical issues undermine the strength of the central claims. The evidence that compounds act specifically through AP2 domain competition in vivo is correlative rather than causal. The transcriptomic perturbation data show only partial overlap with AP2-EXP targets, and the lack of direct evidence for on-target engagement in parasites is a significant gap. The mosquito-stage data are intriguing but limited by the use of a single non-AP2 control compound and lack of dose-response information. The manuscript would benefit from clearer presentation of statistical analyses and more rigorous controls to distinguish specific from nonspecific effects.

- **Who would be interested in the results, and why** Researchers in antimalarial drug discovery, particularly those focused on transcription factors as therapeutic targets, would find this work relevant. The malaria biology community studying gene regulation during the intraerythrocytic development cycle would also be interested in the AP2-EXP ChIP-seq data and the proposed chemical genetic approach. Additionally, investigators working on chemical probes for parasite-specific processes may find the compound scaffolds useful as starting points. The work may also appeal to those studying the druggability of protein-DNA interactions more broadly.

- **Major strengths** The study addresses an underexplored target class for antimalarial development, namely ApiAP2 transcription factors, which are parasite-specific and essential. The multi-pronged approach combining computational screening, biochemical validation, transcriptomic analysis, and in vivo mosquito-stage testing is comprehensive. The generation of endogenously tagged AP2-EXP lines and ChIP-seq data provides useful resources for the community. The observation that compound activity timing correlates with AP2-EXP expression is a thoughtful experimental design element.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for on-target mechanism
- **Claim pointer** The manuscript claims that compound activity is "consistent with the disruption of gene regulation" and that AP2-EXP is inhibited in vivo based on transcriptomic overlap and ChIP-qPCR
- **Evidence pointer** Results sections on transcriptome analysis and ChIP-qPCR; Figure 4 and Figure S20
- **Concern** The central claim that compounds act through AP2 domain inhibition in vivo rests on correlative evidence. The transcriptomic overlap between compound-treated parasites and AP2-EXP targets is 46/93 genes, which is substantial but not complete. More critically, the ChIP-qPCR experiment showing decreased AP2-EXP occupancy at five loci after compound treatment is performed at only one time point (30-35 hpi) with a single compound concentration, and the magnitude of the effect is not reported. No evidence is provided that the compound reaches the nucleus at sufficient concentrations to inhibit DNA binding, nor is there any demonstration that the compound binds to AP2-EXP in cells. The possibility that the observed transcriptomic changes result from off-target effects or general toxicity is not adequately excluded.
- **Why it matters** The therapeutic rationale for targeting ApiAP2 proteins depends on demonstrating that the compounds engage their intended target in the parasite. Without direct evidence of on-target engagement, the mechanistic claims are not established, and the compounds cannot be positioned as specific chemical probes for ApiAP2 function.
- **Resolution test** Provide direct evidence of compound binding to AP2-EXP in parasites, such as cellular thermal shift assays, or demonstrate that resistance mutations in AP2-EXP confer compound resistance. Alternatively, show that a structurally related inactive analog does not produce the same transcriptomic changes or ChIP-qPCR effects.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Specificity of compounds for ApiAP2 over other DNA binding proteins
- **Claim pointer** The manuscript claims that compounds B and C demonstrate specificity for Apicomplexan AP2 domains in vitro based on lack of competition against AtERF1 and SOX2
- **Evidence pointer** Results section on EMSA controls; Figure S6
- **Concern** The specificity assessment is limited to only two non-apicomplexan DNA binding proteins. The claim of specificity for ApiAP2 domains is not supported by testing against a broader panel of DNA binding proteins, including other Plasmodium transcription factors or human transcription factors with similar domain architectures. Furthermore, the manuscript does not report whether compounds B and C were tested for binding to other AP2 domains within the ApiAP2 family beyond the four tested, leaving open the possibility of broad reactivity across the family. The EMSA results are described qualitatively without quantification of binding affinities or competition efficiencies.
- **Why it matters** Specificity is a prerequisite for both therapeutic development and use as chemical probes. If compounds inhibit multiple DNA binding proteins, the observed phenotypic effects cannot be attributed to ApiAP2 inhibition, and the therapeutic window may be narrow.
- **Resolution test** Test compounds against a panel of recombinant DNA binding domains from diverse families, including additional ApiAP2 domains and unrelated transcription factors. Quantify competition efficiencies and report IC50 values for each protein tested.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor of transcriptomic analysis
- **Claim pointer** The manuscript reports 463 transcripts decreased by log2 fold change >2 in the presence of compound C and identifies 46 AP2-EXP targets among these
- **Evidence pointer** Results section on transcriptome analysis; Figure 4; Table S3
- **Concern** The transcriptomic analysis relies on a fold-change threshold without clear reporting of statistical significance criteria. The use of LIMMA is appropriate, but the manuscript does not state the adjusted p-value threshold used to define differentially expressed genes. The overlap analysis between compound-perturbed genes and AP2-EXP targets would benefit from a statistical enrichment test to determine whether the overlap is greater than expected by chance. Additionally, the biological replicates for the microarray experiment are not specified, and the correlation between compound-treated and control samples at the 30 hpi time point is reported as a single value without confidence intervals.
- **Why it matters** The claim that compound C perturbs AP2-EXP target genes specifically depends on demonstrating statistically significant enrichment of targets among differentially expressed genes. Without this, the observed overlap could be coincidental, particularly given the large number of genes affected.
- **Resolution test** Report adjusted p-values for differential expression, perform a hypergeometric or permutation-based enrichment test for AP2-EXP target overlap, and specify the number of biological replicates used.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Dose-response relationship and compound concentration relevance
- **Claim pointer** The manuscript states that compound C was used at 12 µM (0.66x IC50) for transcriptomic analysis and 40 µM for ChIP-qPCR and phenotyping assays
- **Evidence pointer** Materials and methods sections on transcriptomics, ChIP-qPCR, and phenotyping
- **Concern** The concentrations used for mechanistic studies (12 µM and 40 µM) are substantially higher than the reported IC50 values (range 11-170 µM across compounds). The manuscript does not explain why 40 µM was chosen for phenotyping when the IC50 for compound C is not explicitly stated in the text. The use of concentrations near or above the IC50 for transcriptomic analysis raises concerns that observed changes may reflect general growth inhibition or cytotoxicity rather than specific transcriptional effects. No viability data are shown for the conditions used in the transcriptomic and ChIP experiments.
- **Why it matters** Interpretation of mechanistic studies requires that compound concentrations be within a range where specific target engagement is plausible and where nonspecific toxicity is minimal. Without dose-response data for the transcriptomic and ChIP effects, the specificity of the observed changes is unclear.
- **Resolution test** Perform transcriptomic and ChIP-qPCR experiments at multiple compound concentrations and correlate the magnitude of effects with the dose-response curve for parasite growth inhibition. Report viability data for all experimental conditions.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of mosquito-stage findings
- **Claim pointer** The manuscript claims that compounds B and C inhibit P. berghei sporozoite development in vivo
- **Evidence pointer** Results section on mosquito-stage assays; Figure 6
- **Concern** The mosquito-stage experiments use P. berghei, a rodent malaria parasite, rather than P. falciparum, the human pathogen that is the focus of the manuscript. While P. berghei is a reasonable model for mosquito-stage biology, the relevance to P. falciparum transmission is not directly demonstrated. The manuscript does not report whether the compounds were tested against P. falciparum gametocytes or ookinetes. Additionally, the compound concentrations used for mosquito injections are not reported, and the specificity of the effect (AP2 inhibition versus general toxicity to the mosquito or parasite) is not addressed.
- **Why it matters** The claim of transmission-blocking potential for human malaria requires evidence in P. falciparum or at least a clear rationale for why P. berghei results are predictive. Without this, the translational significance is limited.
- **Resolution test** Test compounds against P. falciparum gametocyte production and ookinete development in vitro, or provide a clear argument for the conservation of AP2-EXP function between P. berghei and P. falciparum in mosquito stages.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of compound nomenclature
- **Affected element** Results section, Figure 1
- **Evidence pointer** Figure 1A, 1B
- **Issue** The manuscript uses alphabetical identifiers A-I for compounds but does not provide chemical names or structures in the main text. The relationship between compound identifiers and their chemical structures is only shown in supplementary figures.
- **Required correction** Include a table in the main text listing compound identifiers, chemical structures, and sources, or clearly reference the supplementary table where this information is provided.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reporting of ChIP-seq quality metrics
- **Affected element** Materials and methods, ChIP-seq analysis
- **Evidence pointer** Materials and methods section on ChIP-seq data analysis
- **Issue** The manuscript does not report standard ChIP-seq quality metrics such as number of reads, mapping rates, peak numbers per replicate, or FRiP scores. This limits assessment of data quality.
- **Required correction** Add a supplementary table with ChIP-seq quality metrics for each replicate and sample.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Incomplete description of molecular dynamics simulations
- **Affected element** Materials and methods, Molecular dynamics simulations
- **Evidence pointer** Materials and methods section on molecular dynamics
- **Issue** The manuscript states that simulations were performed for 500 ns but does not report convergence criteria, force field validation, or analysis of simulation stability. The conclusion that compound B-3 "moves away from the protein" is qualitative.
- **Required correction** Provide quantitative analysis of simulation trajectories, including RMSD plots and binding energy calculations, or temper the conclusions drawn from the simulations.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Inconsistent reporting of IC50 values
- **Affected element** Results section, Figure 1A
- **Evidence pointer** Figure 1A
- **Issue** The manuscript states that all nine compounds kill parasites at concentrations ranging 11-170 µM but does not provide individual IC50 values for each compound in the text or a table.
- **Required correction** Include a table with IC50 values for all nine compounds with confidence intervals.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Limited discussion of compound selectivity for AP2-EXP over other AP2 domains
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The manuscript demonstrates that compounds B and C compete with multiple AP2 domains (AP2-EXP, AP2-I, AP2-HS, PfSIP2) but does not discuss the implications of this broad reactivity for therapeutic development or for interpreting phenotypic effects.
- **Required correction** Add a paragraph in the Discussion addressing the potential for multi-AP2 targeting and its implications for specificity and toxicity.

## Risk / unsupported claims
- The claim that compounds act through AP2-EXP inhibition in vivo is not directly supported; evidence is correlative
- The claim of specificity for Apicomplexan AP2 domains is based on testing against only two non-apicomplexan proteins
- The claim that compound activity timing correlates with AP2-EXP expression is based on limited temporal sampling
- The mosquito-stage activity in P. berghei is presented without evidence of relevance to P. falciparum transmission
- The molecular dynamics simulation conclusions are qualitative and not supported by quantitative analysis
- The transcriptomic overlap with AP2-EXP targets is reported without statistical significance testing for enrichment
- The manuscript states that AP2-EXP is essential based on prior literature, but the essentiality of the specific DNA binding domain targeted by compounds is not established