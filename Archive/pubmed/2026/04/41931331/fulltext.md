# Study on material basis and network mechanism of the Guizhi Fuling pills in the treatment of endometriosis and endometrial polyps


## Abstract
  To explore the material basis and network mechanism of the Guizhi Fuling pills in the treatment of endometriosis and endometrial polyps based on network pharmacology and machine learning. The effective constituents and targets of the Guizhi Fuling pills were obtained based on the TCMSP and SymMAP databases. Endometrial polyps disease genes were retrieved by GenCards and OMIM databases. The active component–common disease target was obtained using Venn Diagram, which was uploaded to the STRING database and Cytoscape software to construct the protein interaction network and analyze its molecular biological mechanism. Random walk with restart was run on the compound network and protein–protein interaction network to detect core compounds, targets, and the stability of the relapse network. Then, the biological function and pathway enrichment analysis of the core targets were carried out with the help of the DAVID database, and the key targets of the pathway were further obtained. Finally, molecular docking verification was conducted. A total of 30 disease targets were obtained. According to gene ontology analysis, the treatment of endometriosis and endometrial polyps with Guizhi Fuling pills mainly focused on biological processes such as rhythm process, mechanical stimulation response, DNA binding regulation, and other biological processes. The signaling pathways are mainly concentrated in apoptosis, TNF signaling pathway, IL-17 signaling pathway, toll-like receptor signaling pathway, VEGF signaling pathway, estrogen signaling pathway, nuclear factor-kappa B signaling pathway, hepatitis signaling pathway, etc. Then, the 10 effective components and 10 target proteins were further verified by molecular docking. The results showed that β-sitosterol, luteolin, and quercetin were the most closely connected with the target NR3C1 and MMP9, respectively, which may be the key compounds and core target proteins in the “different diseases and the same treatment” of the Guizhi Fuling pills. The mechanisms of its comorbidity mainly involved estrogen, tumor, inflammation, immune response, and other signaling pathways, and were closely related to several biological processes. It can provide research direction for further research on the mechanism of “treating different diseases with the same treatment” of the Guizhi Fuling pills.


## 1. Introduction
  Endometriosis (EMs) is characterized by the presence of endometrial glands and stroma outside the uterus. EMs affects about 10% to 15% of women of reproductive age, resulting in dysmenorrhea, infertility, and decreased quality of life. At present, the treatment of EMs is mainly based on nonsteroidal analgesics, oral contraceptives, gonadotropin-releasing hormone agonists, and surgical treatment. However, drug withdrawal or high recurrence rate after surgery are still problems to be solved urgently.[1]

  Endometrial polyps (EPs) are peduncle or sessile vegetations protruding from the surface of the endometrium. It is composed of endometrial glands and fibrotic endometrial stroma containing thick-walled blood vessels. EP can cause abnormal uterine bleeding, affect endometrial receptivity or lead to infertility or abortion due to local biochemical abnormalities of the endometrium. At present, hysteroscopic endometrial polypectomy is the main treatment method, but it cannot fundamentally improve the endometrial environment. Therefore, the postoperative recurrence rate is high.[2]

  EP is a focal hyperplastic growth of endometrial glands and stroma, whereas EMs is an ectopic growth of endometrial glands and stroma, and both disorders include overgrowth of the endometrium. In 1996, McBean[3] first reported the correlation between the 2 diseases. Several subsequent studies have shown a higher prevalence of EP in patients with EMs than in women without EMs.[4–6] Pan et al[7] retrospectively analyzed the data of 3960 patients with endometrial polyps in Union Hospital in 3 years and found that among the complications of EP, uterine fibroids (52.5%), and EMs/adenomyosis (32.3%) accounted for >80%. They also proposed that endometrial polyps are likely to be a local phenotype of EMs/adenomyoses, and the awareness of “thinking about the abnormality by polyps” should be improved.

  Guizhi Fuling pill is a classic prescription of Jingui Yaolue (Synopsis of the Golden Chamber), which is composed of 5 Chinese herbs: Guizhi, fuling, peach kernel, red peony, and Danpi. Modern pharmacological experiments and clinical studies have shown that this prescription has a significant effect on EMs and EP,[8–13] which reflects the characteristics of “treating different diseases with the same treatment.” However, there is still a lack of systematic research on the common mechanism of the 2 diseases and the effect of the Guizhi Fuling pill.

  However, traditional Chinese medicine compound generally has the characteristics of “multi-component, multi-target, and multi-pathway,” and it is difficult to systematically and completely elucidate its mechanism of action in traditional pharmacological research. Network pharmacology can comprehensively analyze the mechanism of main drug components in the treatment of diseases by constructing a “drug-component-target-disease-pathway” network. Weighted gene co-expression network analysis (WGCNA) constructed a weighted network based on gene–gene interactions to discover important modules highly related to clinical traits and screen out key genes. Molecular docking can simulate the binding of key components of drugs to their targets and evaluate the interaction between drugs and related genes. In this study, machine learning algorithms, network pharmacology methods, and molecular docking methods were used to explore the common mechanism between the 2 diseases and the molecular biological role played by Guizhi Fuling pill in the process of “treating different diseases with the same treatment,” to provide preliminary evidence and guidance for subsequent experimental verification.


## 2. Methods
  All computational analyses were conducted using R (version 3.5.2; R Foundation for Statistical Computing, Vienna, Austria), Cytoscape (version 3.7.2; Cytoscape Consortium, San Diego), AutoDock Tools (version 1.5.7; The Scripps Research Institute, La Jolla), AutoDock Vina (version 1.2.3; Center for Computational Structural Biology, Scripps Research, La Jolla), and Discovery Studio Visualizer (version 21.1.0; BIOVIA, Dassault Systèmes, San Diego).


### 2.1. Screening and target of active ingredients of the Guizhi Fuling pill
  The databases TCMSP, SymMap, GeneCards, and OMIM were used to comprehensively collect potential targets. For GeneCards (https://www.genecards.org), disease-related targets were retrieved using the keywords “endometrial polyps” and “endometriosis.” Only genes with a relevance score ≥10.0 were retained to reduce noise and improve reliability, as GeneCards typically returns thousands of genes with highly variable confidence.

  For OMIM (https://omim.org/), the same search terms were used (“endometrial polyps” and “endometriosis”), and the database was accessed on March 5, 2024. Only manually curated entries with established gene–disease associations were included.

  The TCMSP database (version 2.3, accessed on March 5, 2024) and SymMap database (version 2.0, accessed on March 5, 2024) were used to identify chemical constituents of the 5 herbal components of Guizhi Fuling pill. The selection was based on pharmacokinetic criteria of oral bioavailability ≥30% and drug likeness ≥0.18. Corresponding protein targets were collected and standardized via the UniProt database (https://www.uniprot.org, accessed on March 5, 2024) for conversion of protein names to official gene symbols (Homo sapiens).


### 2.2. Acquisition of active ingredient–disease common targets
  Gene expression profiles of EMs were downloaded from the gene expression omnibus (GEO) database and WGCNA was performed. The R Programming Language was used to calculate the expression correlation between all genes and construct a weighted gene co-expression network. A soft threshold is set to cluster genes with expression correlation into the same module, and then the gene module is associated with the phenotype of interest (such as disease presence). The study aimed to investigate the relationship between a specific gene module and the occurrence of the disease, focusing on the identification of core genes within this module. The analytical workflow comprised several steps: firstly, the selection of the top 25% of genes with the highest variance; subsequently, the establishment of a soft threshold to construct a gene co-expression similarity matrix; followed by the detection of co-expressed gene modules; the grouping of similar modules through clustering techniques; and ultimately, the integration of gene expression patterns with functional modules. These operations were conducted systematically to elucidate the molecular basis underlying the disease phenotype. Endometrial polyps targets by GeneCards database (https://www.genecards.org) and OMIM database (https://omim.org/) are collected. The intersection of drug active ingredient targets and disease target data sets was obtained by Venn diagram. As a common target database of EP and EMs for the “treating different diseases with the same treatment” of the Guizhi Fuling pill.

  Prior to conducting WGCNA, thorough preprocessing of gene expression data is imperative. This preprocessing encompasses outlier removal, normalization, and rigorous data cleaning steps to refine the gene expression matrix. Following data preparation, pairwise correlation coefficients are computed using the selected gene expression data, commonly employing Pearson correlation coefficient or Spearman rank correlation coefficient to quantify both linear and nonlinear relationships between genes. Critical parameters for constructing the gene co-expression network are carefully determined, notably including the selection of a similarity threshold (or soft threshold) to weigh the correlation matrix. This pivotal step in soft threshold selection serves to enhance weaker correlation signals while attenuating strong correlation signals, thus facilitating the discovery of modular structures within the network. Subsequently, hierarchical clustering or alternative clustering algorithms are employed to organize genes into modules characterized by high internal connectivity. The choice of clustering methods and associated parameter settings directly influences the quantity and size of the detected modules. Each identified module undergoes meticulous definition and annotation, involving comprehensive descriptions of gene characteristics within the modules and subsequent performance of functional enrichment analysis.


### 2.3. Compound network construction and protein–protein interaction (PPI) network
  The 5 Chinese herbs, active ingredients, and targets in the Guizhi Fuling pill were uploaded to Cytoscape3.7.2. The Merge function was used to merge them and finally draw a compound network diagram. The active ingredient–disease common targets were uploaded to the STRING database (https://string-db.org/), and the species was selected as “human.” The STRING database (version 11.5; accessed on March 8, 2024) was used to analyze protein–protein interactions. The species was limited to Homo sapiens, and the minimum required interaction score was set to 0.7 (high confidence) to ensure the reliability of the PPI data.

  Both experimental and predicted interactions were included (text mining, experiments, databases, co-expression, and neighborhood). The resulting PPI network file was exported in TSV format, which contained the interaction adjacency matrix, including the following main fields:

  protein1: UniProt ID of the first protein; protein2: UniProt ID of the second protein; combined_score: confidence score of the interaction (0–1 range).

  This adjacency table was then imported into Cytoscape (version 3.7.2) for visualization and topological analysis. Network topological parameters such as degree, betweenness centrality, and closeness centrality were calculated using the NetworkAnalyzer plug-in Table S1, Supplemental Digital Content, https://links.lww.com/MD/R452 provides the full adjacency table used for the Cytoscape analysis, listing each protein–protein interaction pair and its combined score.

  Note: The adjacency table represents high-confidence protein–protein interactions identified from STRING (version 11.5, Homo sapiens, minimum interaction score = 0.7). This dataset was used for Cytoscape visualization and network topology analysis.

  The target protein interaction network diagram and protein interaction network data files were downloaded and imported into Cytoscape3.7.2 for PPI analysis. In the analysis of network topology, we employed CytoNCA to identify core targets based on 3 key parameters: degree centrality, closeness centrality, and betweenness centrality. These parameters provide valuable insights into the functional significance and impact of nodes within the network, with higher values indicating greater relevance and influence on network behavior. Degree centrality reflects the number of connections (edges) a node has within the network, highlighting nodes with high interaction potential. Cellular component (CC) measures how closely connected a node is to other nodes, indicating nodes that can efficiently communicate with the rest of the network. Betweenness centrality identifies nodes that act as crucial bridges between other nodes, facilitating the flow of information through the network.


### 2.4. Core compounds and target discovery
  To assess the importance of a node to a particular network, it can be measured in terms of network propagation. Taking medicinal ingredients and drug targets as seed nodes, Random Walk with Restart (RWR) was run on the “disease-medicine-medicine-ingredient-target” compound network and PPI network, respectively.[14] After a certain number of walks, the affinity scores of the medicinal ingredients to the TCM compound network and the drug targets to all nodes in the PPI network will be obtained. Usually, the top 10 nodes with affinity scores are desirable as important effective components or targets.[15] RWR is helpful to find out the drug component nodes which are most closely related to “disease-drug-target” and the most valuable targets in the PPI network while grasping the global information. The RWR algorithm was executed using the dnet package (version 1.1.4) in the R language (version 3.5.2), and the restart probability was set to the default value of 0.75.

  The restart probability (α) is a critical parameter in the RWR algorithm, governing the likelihood of the random walk restarting from the initial seed nodes during each iteration. Typically ranging between 0 and 1, a higher α value amplifies the influence of seed nodes on the random walk, resulting in a more focused exploration around these nodes. The transition probability matrix (P) defines the probabilities of transitioning between nodes within the network. In RWR, this matrix is calculated considering the graph structure and edge weights, adapting to both local connectivity and the broader network structure. A convergence threshold is established to determine when to halt the random walk iterations. The algorithm continues until the change in node scores (or probabilities) between successive iterations falls below a predefined threshold value. To ensure convergence and prevent infinite loops, the RWR algorithm sets a maximum number of iterations. If the convergence threshold is not reached within this limit, the algorithm concludes, and the node scores are finalized. Seed nodes serve as the starting points for the random walk, each assigned with initial scores reflecting their significance or prior knowledge in the analysis. The RWR algorithm iteratively updates node scores based on the random walk process originating from these seed nodes. This approach enables efficient exploration and ranking of nodes within complex networks, providing valuable insights into network dynamics and node importance.

  The RWR algorithm was applied to prioritize nodes within both the compound and PPI networks. The restart probability (α) was set to 0.75, which is the default value in most RWR implementations and reflects a 75% chance that the walker returns to the initial seed nodes during each iteration.

  For the compound network, the seed nodes corresponded to the active medicinal ingredients and their direct targets, derived from TCMSP and SymMap. For the PPI network, the seed nodes were the disease-related target genes identified from GeneCards and OMIM. Each seed node was initialized with an equal starting probability, that is, a normalized initial score of 1/N, where N represents the total number of seed nodes.

  The transition matrix W was column-normalized to ensure that each column summed to 1. The iterative update followed the standard RWR equation:

  where p(0) is the initial seed vector.

  Convergence was achieved when the L1-norm difference between successive probability vectors satisfied and convergence typically occurred within 18 iterations.

  After convergence, the steady-state probability vector represented each node’s affinity score, quantifying its network proximity to the seeds.

  All nodes were subsequently ranked by their affinity scores, and the complete ranked list is provided in Table S2, Supplemental Digital Content, https://links.lww.com/MD/R452. This ranking allows the identification of core compounds and targets with the strongest network associations to the Guizhi Fuling pill and the diseases.


### 2.5. Network stability test of traditional Chinese medicine compound
  The performance of a multilayer network depends on its stability (survivability). When some nodes of a network are destroyed (removed), the network remains connected. Such network resilience is widely used in complex microbial communities or microbial communities. We introduced this measure of damage resistance to the multilayer network, which can reflect the biological significance of the integrity and stability of the multilayer network of the Chinese herbal compound treated by the Guizhi Fuling pill. Its detailed principle and calculation formula are recorded in the article by Wu et al.[16] The specific calculation formula is as follows:

  The R language (version 3.5.2) custom function was used to execute the network stability algorithm, and the number of removed nodes was 30.


### 2.6. Biological and pathway enrichment analysis
  Gene ontology (GO) and Kyoto encyclopedia of genes and genomes (KEGG) enrichment analyses were conducted to explore the biological functions and signaling pathways of the identified target genes. The analysis was performed using clusterProfiler (version 4.4.4) in R (version 4.3.2). The background gene list was defined as the 303 unique drug targets collected from TCMSP and SymMap databases, ensuring enrichment was evaluated relative to the pharmacologically relevant gene space rather than the entire human genome.

  A hypergeometric test (equivalent to Fisher exact test) was applied to evaluate the statistical significance of enrichment. The resulting P-values were adjusted for multiple comparisons using the Benjamini–Hochberg false discovery rate (FDR) method. Terms were considered significantly enriched if P <.05 and FDR <0.05.

  Functional categories were derived from the GO database (version released November 2023), including the biological process, CC, and molecular function ontologies.

  Pathway analysis was based on the KEGG database (release 2023.09). Complete enrichment tables, including term name, gene count, raw P-value, adjusted FDR, and associated genes, are provided in Table S3 (GO) and Table S4 (KEGG) in Supplemental Digital Content, https://links.lww.com/MD/R452. GO and KEGG pathway enrichment analysis was completed by the GOcluster package[17] in R language software, and a visual drawing display was achieved by the GOplot package.[18]


### 2.7. Molecular docking
  The mol2 structure of the ligand was downloaded from TCMSP and, after processing with Autodock Tools, saved as a pdbqt structure. The 3D structure of the receptor was obtained from RCSB, and after removing water molecules and separating the ligand and receptor by Discovery Studio, the binding sites were calculated by Autodock Tools. Save the receptor as a pdbqt file. The docking simulation was performed by Autodock Vina. According to the minimum binding energy of the ligand–receptor obtained after docking, a heat map was constructed and the relevant binding sites and interaction forces of amino acid residues were analyzed.

  Docking simulations were carried out using AutoDock Vina (version 1.2.3). The grid box was centered on the receptor active site (center coordinates: X = 25.64, Y = 34.27, Z = 52.81 Å), covering the entire binding pocket identified from the co-crystallized ligand.

  The grid box dimensions were 40 × 40 × 40 Å, ensuring full coverage of the active region. The exhaustiveness parameter was set to 8, energy range to 3 kcal·mol−1, and 9 binding modes were generated for each ligand.

  Receptor and ligand preparation, including the addition of Gasteiger charges and assignment of torsions, was performed using AutoDock Tools (version 1.5.7). Protonation states of ligands and receptors were adjusted to pH 7.4. All water molecules were removed from receptor structures except those directly participating in the binding pocket.

  Ligand tautomers were selected according to their most stable forms under physiological conditions. Visualization and hydrogen-bond interaction analyses were performed using Discovery Studio Visualizer (version 21.1.0).


## 3. Results

### 3.1. Screening and target of active ingredients of the Guizhi Fuling pill
  According to the critical value of oral bioavailability ≥30% and DL ≥0.18, a total of 296 active ingredients were extracted. Among them, 141 were Cinnamomum twigs, 49 were Poria cocos, 74 were red peonies, 42 were Moutan peonies and 43 were peach kernel. After the PubChem database and target correspondence, a total of 81 active components of compounds and 303 related targets were obtained.


### 3.2. Acquisition of disease targets
  The gene expression profiling data of EMs (GSE7305) were downloaded from the GEO database. After analysis by WGCNA, gene modules (purple, blue, and tuequoise modules) that were significantly associated with EMs pathogenesis were extracted, with a total of 1502 genes, as shown in Figure 1A and B. EPs targets were collected through GeneCards and OMIM databases, totaling 1646 genes. The names of predicted pathogenic targets associated with EM and EP were standardized using the UniProt online database. Then, the therapeutic targets of the Guizhi Fuling pill and the pathogenic targets of the 2 diseases were intersected to obtain 30 predicted therapeutic targets, as shown in Figure 1C.

  The dataset GSE7305 was obtained from the GEO database (https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE7305). It was generated using the Affymetrix Human Genome U133 Plus 2.0 Array (GPL570) platform. The dataset included 20 samples in total: 10 EMs ectopic endometrial samples (cases) and 10 eutopic endometrial samples from healthy controls (Table 1).

  The raw CEL files were downloaded and processed using the affy and WGCNA packages in R (version 3.5.2). Background correction and quantile normalization were performed using the Robust Multi-array Average method. Probe IDs were mapped to gene symbols using the GPL570 annotation file. When multiple probes mapped to the same gene, their expression values were averaged. Genes with low expression variance (bottom 25%) were filtered out to improve network robustness.

  Sample quality was assessed by hierarchical clustering using Euclidean distance based on gene expression. Two samples (GSM177600 and GSM177614) were identified as outliers (Z-score <‐2.5) and removed prior to network construction (Fig. 1D). Batch effects were examined using principal component analysis and found negligible; thus, no batch correction was applied.

  The soft thresholding power (β) was selected using the pickSoftThreshold function in WGCNA to approximate a scale-free topology fit index (R2) ≥0.85 (Fig. 1E). The optimal β was determined as β = 9, balancing scale-free topology and mean connectivity. A signed adjacency matrix was built and transformed into a topological overlap matrix. Modules were detected using dynamic tree cutting with a minimum module size of 30 genes and merged with a module eigengene correlation threshold of 0.25.

  The module–trait relationship heatmap was plotted to visualize correlations between module eigengenes and clinical traits (case/control status). Correlation coefficients and P-values were calculated by Pearson correlation (Fig. 1F). Modules with |correlation| >0.5 and P <.05 were considered significantly associated with EMs.

  Hub genes were identified based on module membership >0.8 and gene significance >0.2, which together represented strong intra-module connectivity and clinical relevance.


### 3.3. Construction of traditional Chinese medicine compound network and PPI network
  Cytoscape 3.7.2 software was used to process the 5 Chinese herbs, active components, and their targets of the Guizhi Fuling pill, and the compound network map of the Guizhi Fuling pill was constructed (Fig. 2). The 119 nodes are connected by 234 edges. Among them, the red node represents the disease, the green node represents the 5 herbs, the yellow node represents the action component, and the blue node represents the target. It can be seen that the active ingredients and action targets of the Guizhi Fuling pill have multilevel and multidimensional cross-corresponding relationships at the molecular biological level, forming a complex network system.

  The 30 predicted therapeutic targets were uploaded to the STRING 11.0 online database (https://string-db.org/) to obtain the corresponding PPI information. Cytoscape 3.7.2 software was used to construct a PPI network, including 30 nodes connected by 110 edges, as shown in Figures 3 and 4.


### 3.4. Core compounds and target discovery
  The RWR algorithm was implemented in the “disease-drug-drug-ingredient-target” compound network. We found that the top 10 ingredients most closely associated with the whole compound network were quercetin, beta-sitosterol, (R)-P-menth-1-En-4-Ol, kaempferol, baicalein, hederagenin, luteolin and Hemo-Sol, acetic acid, and ellagic acid. The common targets of these 10 key active ingredients may play a role in “treating different diseases with the same treatment” for EPs and EM.

  The restart random walk algorithm is implemented in the PPI network. The top 10 most closely related targets in the whole PPI network were CASP3, MAPK8, EGF, NR3C1, PPARG, MMP9, NFKBIA, CASP9, CYCS, and PRKCB. Therefore, these 10 targets may play a key role in the action of the Guizhi Fuling pill.

  Machine learning plays a critical role in drug discovery and development. This study leveraged large-scale biological information datasets, including gene expression data and protein–protein interaction networks, to conduct drug and core gene screening. These findings provide a theoretical basis for clinical practitioners when selecting medications.


### 3.5. Network stability test of traditional Chinese medicine compound
  The index of natural connectivity can be used to accurately characterize the subtle differences in network stability. As more nodes are removed from the disease–medical–ingredient–target compound network, its natural connectivity gradually and robustly decreases. That is to say, the stability and integrity of compound treatment can be explained from the perspective of network stability. In this study, 30 nodes were randomly removed from the compound network, and the natural connectivity of the Guizhi Poring pill in the treatment of EPs and EM did not decrease significantly, reflecting the therapeutic stability of the TCM compound, as shown in Figure 5A. The natural connectivity (Λ) index was used to quantify the topological robustness of the compound network, as proposed by Wu et al.[16] The mathematical definition is:

  where λi represents the eigenvalues of the adjacency matrix, and NNN is the total number of nodes in the network.

  This parameter reflects the redundancy of alternative paths and overall structural robustness; a higher Λ indicates greater stability.

  To evaluate stability, we performed node removal experiments on the compound network (composed of 5 herbs, 81 active ingredients, and 303 targets).

  Both random node deletion and targeted hub-node deletion were simulated, each repeated 100 times. The mean ± standard deviation of natural connectivity values were plotted against the proportion of removed nodes (Fig. 5B and C).

  Statistical testing was carried out using a two-tailed paired Student t test, comparing Λ values before and after node removal. A significant decrease was defined as P <.05 and a relative change |ΔΛ|/Λ0 >5%. In contrast, if P ≥.05 or |ΔΛ|/Λ0 ≤5%, the change was considered ``not significant,’’ indicating that the network retained its structural robustness under perturbation.

  The results showed that the natural connectivity did not decrease significantly (meanΔΛ = −3.2%, P = .18) when up to 30 nodes were randomly deleted, suggesting that the compound network of Guizhi Fuling pill has strong tolerance to node loss.

  This study leveraged large-scale biological information datasets, including gene expression data and protein–protein interaction networks. Machine learning approaches can expedite drug screening and design, demonstrating the efficacy of the Guizhi Fuling pill in treating EMs. This underscores how machine learning models, utilizing personalized patient data and clinical indicators, can forecast disease progression trends to aid physicians in formulating more rational treatment plans and preventive measures.


### 3.6. Results of GO and KEGG enrichment analysis
  The top 5 FDR values of biological process, CC, and molecular function obtained by GO enrichment analysis are shown in Figure 6A. The targets of the Guizhi Fuling pill on EP and EMs of “simultaneous treating different diseases with the same treatment” are mainly through biological processes such as rhythm process, mechanical stimulation response, and DNA binding regulation. Based on cellular components such as membrane rafts and plasma membrane microdomains, it plays molecular functions such as regulating endopeptidase activity, cysteine endopeptidase activity, apoptosis signaling pathways involved in cysteine endopeptidase activity, nuclear receptor activity, and ligand-activated transcription factor activity.

  The top 20 signaling pathways obtained by KEGG signaling pathway enrichment analysis are shown in Figure 6B. It mainly involves cell apoptosis, TNF signaling pathway, IL-17 signaling pathway, Toll-like receptor signaling pathway, VEGF signaling pathway, estrogen signaling pathway, nuclear factor-kappa B (NF-κB) signaling pathway, hepatitis, and other signaling pathways.

  Then, the 10 important targets calculated by RWR in the PPI network were taken as the abscissa, and the important signaling pathways obtained by KEGG were taken as the ordinate to construct the target-pathway interaction diagram, as shown in Figure 6C. We found that the active ingredients of the Guizhi Fuling pill could act through multiple targets and pathways.


### 3.7. Molecular docking
  To further explore the key molecular mechanism of the Guizhi Fuling pill in the intervention of EMs and EPs. The docking results are shown in Figure 7 with 10 selected active components as ligands and 10 target proteins as receptors. The abscissa represents the target protein, the ordinate represents the active component, and the color depth represents the magnitude of binding energy. The results showed that the minimum binding energy of β-sitosterol, quercetin, luteolin, and other active ingredients docking with CASP3, MAPK8, MMP9, NR3C1, PPARG, PRKCB, and other target proteins was <‐6.0 kcal·mol‐1, which had the best binding ability. In general, except for acetic acid and Hemo-Sol, it showed good docking binding ability with all target proteins.

  The top 3 groups of proteins with better binding ability were screened based on the lowest binding energy of molecular docking, as shown in Figure 7. A hydrogen bond was formed between β-sitosterol and NR3C1 through the GLN570 site. Luteolin formed 3 hydrogen bonds with the target MMP9 at ALA189, ALA242, and GLN227. Quercetin formed 6 hydrogen bonds with its target MMP9 at ALA189, GLN227, TYR245, and LEU243. Therefore, these 3 compounds and 2 proteins may be the key compounds and core target proteins in the “simultaneous treating different diseases with the same treatment” of the Guizhi Fuling pill and also provide a molecular biological basis for further experimental verification, as shown in Figures 8 and 9.

  To ensure the reliability of the docking procedure, a validation docking was performed by re-docking the co-crystallized ligand of the receptor (PDB ID: 3ERT) into its original active site using the same grid box and parameters as for the test ligands.

  The root mean square deviation between the predicted pose and the crystallographic pose was 1.62 Å, confirming the accuracy of the docking protocol (root mean square deviation <2.0 Å is generally accepted for reliable reproduction).

  In addition, decoy ligands with similar molecular weights but unrelated scaffolds were docked to the same receptor as negative controls. Their binding affinities were significantly weaker (>−4.0 kcal·mol−1) compared with those of the screened bioactive compounds (−7.1 to −9.4 kcal·mol−1), demonstrating the specificity of the docking interactions.

  Detailed interaction analysis revealed that the key compound quercetin formed 2 hydrogen bonds with ARG120 (2.1 Å) and GLU353 (2.4 Å), and exhibited π–π stacking with PHE404 and hydrophobic contacts with LEU387 and ILE424. The 2D ligand–receptor interaction diagrams with labeled residues and bond distances are shown in Figure 10A–C.


## 4. Discussion
  Guizhi Fuling pill has the effect of activating blood circulation and removing blood stasis. Pharmacological studies have shown that the Guizhi Fuling pill has anti-inflammatory, analgesic, antitumor, immune regulation, endocrine regulation, and other effects,[19,20] and is widely used in the treatment of gynecological diseases.

  This study aims to screen and calculate the core compounds and targets of the Guizhi Fuling pill for the treatment of EP and EMs. The results of molecular docking showed that β-sitosterol, luteolin, and quercetin may play a greater role in the treatment process. Quercetin and luteolin are natural flavonoids with various pharmacological effects such as antioxidant, anti-inflammatory, antitumor, antiviral, antiangiogenesis, and immune regulation.[21] Animal experiments have found that quercetin inhibits the growth of ectopic endometrium by inhibiting cell proliferation, inducing apoptosis, and anti-inflammation in mouse models of EMs.[22] It can also play a role by inhibiting the synthesis and expression of HSP70 and VEGF.[23] Luteolin inhibits the development of EMs by regulating the expression of I3K/AKT and MAPK signaling proteins and CCNE1 in vitro and in vivo.[24] It can also inhibit the growth and induce apoptosis of human EMs cells by activating the caspase family.[25] β-Sitosterol is one of the most common phytosterols, which has various biological activities such as resisting bacterial invasion, regulating cholesterol, anti-inflammatory and analgesic, anti-oxidation, and antitumor.[26] However, the related research literature on the direct effects of these 3 compounds on EP has not been reviewed, and further research is needed.

  Moreover, CASP3, MAPK8, MMP9, NR3C1, PPARG, and PRKCB were identified as the important target proteins by implementing the RWR algorithm in the PPI network combined with molecular docking results. MMP9 is an important member of the matrix metalloproteinase family and plays an important role in angiogenesis and cell migration. Its expression was first found to be upregulated in inflammation and some cancers, and its role in tumor invasion and metastasis is closely related to its promotion of angiogenesis. At present, more and more studies have found that it is highly expressed in both EMs and EP patients.[27,28] CASP3 plays a crucial role in the regulation and execution of apoptosis.[29] MAPK8, a member of the protein mitogenic kinase family, acts as an integration point for a variety of biochemical signals and is involved in various cellular processes, such as proliferation, differentiation, transcriptional regulation, and development.[30] NR3C1 can affect the processes of growth, metabolism, inflammation, and stress response, and participate in the regulation of p53 activity.[31] PPARG, a member of the nuclear receptor transcription factor superfamily, is involved in regulating the transcription of a variety of genes, including key enzymes for estrogen synthesis and matrix metalloproteinases.[32]

  GO and KEGG enrichment analysis showed that the Guizhi Fuling pill played a regulatory role in the treatment of different diseases mainly by participating in the regulation of cell apoptosis, TNF signaling pathway, IL-17 signaling pathway, Toll-like receptor signaling pathway, VEGF signaling pathway, estrogen signaling pathway, NF-κB signaling pathway, hepatitis, and other multiple pathways. The NF-κB signaling pathway is involved in multiple processes such as immunity, proliferation, invasion, and inflammation of the body, and plays an important role in the occurrence and development of EMS.[33] Toll-like receptors, which act as inflammatory mediators in the immune response, are highly expressed in endometrioid tissues.[34] Li et al[35] used the Guizhi Fuling pill to treat EMS patients by reducing the expression of the TLR4 receptor, thereby blocking the NF-κB pathway and causing the apoptosis of EMs cells, to achieve the purpose of treatment. NF-κB is also a transcription factor involved in endometrial pathology. Bozkurt et al[36] found that the activity of NF-κB was significantly reduced after hysteroscopic EP resection. At present, most studies believe that EMs and EP are estrogen-dependent diseases.[37] Ectopic tissues of EMs have abnormal estrogen secretion, increased estrogen receptor, and decreased progesterone receptor. Studies have found that Huoxue Huayu prescription can down-regulate the expression of ESR1, ESR2, GPER, and epidermal growth factor receptor in ectopic endometrial tissue, and reduce the expression levels of estrogen and VEGF in the tissue.[38] The formation of EP may be related to the excessive expression of estrogen leading to endometrial hyperplasia. However, the low progestogen state does not play a countervative role in preventing the endometrium from turning to the secretory phase, thus causing EP.

  Through network pharmacology, this study directly shows that the “treating different diseases with the same treatment” of the Guizhi Fuling pill exerts its effect through multicomponents and multi-targets, which provides a theoretical basis for further experimental verification and clinical application. However, due to the limitations of network pharmacology, it needs to be further verified by rigorous in vivo and in vitro experiments.


## Author contributions
  Conceptualization: Xiaoou Xue.

  Data curation: Jia Yang, Yu Wang, Wei Xie.

  Formal analysis: Jia Yang.

  Investigation: Yu Wang.

  Methodology: Lianghui Cui.

  Software: Lianghui Cui.

  Validation: Yuli Zhang.

  Visualization: Yuli Zhang.

  Writing – original draft: Lianghui Cui, Jia Yang.

  Writing – review & editing: Xiaoou Xue.


## Supplementary Material