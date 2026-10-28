## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, figure legends, and supplementary figure legends
- **Assessment boundary** Scientific content, methodological rigor, validity of conclusions, and presentation quality. Not assessed: editorial fit, ethical compliance, or data availability beyond what is stated.
- **Shared manuscript claim summary** The authors survey histone diversity across 5,869 archaeal genomes, identify five histone clusters based on physical properties, define seven genomic strategies for histone combinations, correlate strategies with taxonomy and environmental factors, and use AlphaFold3 and molecular dynamics simulations to predict that most histone strategies form stable nucleosome-like structures with DNA.
- **Visible evidence base** Main text figures 1-5, tables 1-2, supplementary figures 1-13 (referenced), supplementary tables 1-4 (referenced), methods section, and source data references
- **Missing materials affecting confidence** Supplementary figures and tables were not provided in full. Source data files were not accessible. The interactive iTOL tree was not reviewed. Raw simulation trajectories and analysis scripts were not provided.

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive bioinformatic survey of archaeal histone diversity, expanding the known sequence space considerably and proposing a classification scheme based on physical properties rather than sequence similarity alone. The identification of acidic histones as a major and common feature of archaeal genomes is a notable finding that challenges the assumption that histones must be basic to bind DNA. The structural predictions and molecular dynamics simulations are a reasonable first step, but the authors appropriately acknowledge the limitations of these approaches. The taxonomic and environmental correlations are intriguing but remain largely descriptive. The manuscript is clearly written and will be of interest to the chromatin and archaeal biology communities. However, several technical concerns regarding the clustering methodology, the interpretation of simulation results, and the strength of the environmental correlations need to be addressed before the conclusions are fully supported.

- **Who would be interested in the results, and why** Chromatin biologists studying histone evolution and the origins of eukaryotic nucleosomes will find the expanded sequence diversity and the proposed universal histone signature motifs valuable. Archaeal microbiologists interested in genome organization and evolution will benefit from the taxonomic mapping of histone strategies. Researchers studying extremophiles, particularly halophiles, will be interested in the correlations between histone strategy and environmental conditions. The work also provides a practical guide for selecting representative organisms for future experimental studies.

- **Major Strengths** The manuscript addresses a significant gap in our understanding of archaeal histone diversity. The use of physical properties for clustering is a creative approach that captures functional similarities beyond sequence identity. The systematic mapping of histone strategies onto a taxonomic tree is a valuable resource. The authors are appropriately cautious in interpreting AlphaFold3 predictions and acknowledge the need for experimental validation. The identification of conserved histone signature motifs across the full diversity of archaeal histones strengthens the argument for a universal mechanism of histone-DNA interaction.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of clustering methodology
- **Claim pointer** The authors claim that DBSCAN clustering using four physical parameters (length, pI, GRAVY, instability index) produces five distinct, robust clusters of archaeal histones.
- **Evidence pointer** Methods "DBSCAN clustering", Figure 1a, Table 1, Supplementary Figure 1
- **Concern** The clustering methodology is not described with sufficient detail to assess its robustness. The optimization of epsilon and min_samples parameters is mentioned only as "optimized for a silhouette score of 0.25 (e=0.5 n=40)" but the procedure for arriving at these values is not described. More critically, the validation of cluster stability is limited to "three random subsets" without specifying the size of these subsets or the variance in cluster assignments across subsets. The choice of a silhouette score of 0.25 as a target is unusually low and suggests weak cluster separation. The authors do not report the distribution of silhouette scores for individual points, which would reveal whether some clusters are much better defined than others. Finally, the use of only four physical parameters, while pragmatic, may not capture the full structural diversity of these proteins, and the authors do not demonstrate that these parameters are sufficient to distinguish functionally distinct histone classes.
- **Why it matters** The five clusters are the foundation of the entire manuscript. If the clustering is not robust or the parameters are not well chosen, all downstream analyses, including the definition of the seven strategies, the taxonomic mapping, and the structural predictions, are built on an unstable base. A reader cannot evaluate the validity of the classification without understanding the sensitivity of the clustering to parameter choices and input data.
- **Resolution test** Provide a detailed description of the parameter optimization procedure, including the range of values tested and the metric used for selection. Report the distribution of silhouette scores for individual points within each cluster. Perform a stability analysis by perturbing the input data (e.g., bootstrapping or jackknifing) and reporting the frequency with which the same five clusters are recovered. Demonstrate that the four chosen physical parameters are sufficient by, for example, showing that adding additional parameters (e.g., molecular weight, aromaticity) does not substantially alter the cluster assignments.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validity of structural predictions and simulation conclusions
- **Claim pointer** The authors claim that "structure predictions and simulations suggest similar histone-DNA binding modes for most strategies" and that most histone strategies form stable nucleosome-like structures with DNA.
- **Evidence pointer** Results "Structural prediction of histone complexes", Figure 5, Supplementary Figures 7-9, Methods "Structural prediction" and "Molecular dynamics simulations"
- **Concern** The manuscript does not provide sufficient quantitative data from the molecular dynamics simulations to support the claim of stability. Figure 5b shows DNA RMSD values, but the criteria for classifying a simulation as "stable" versus "unstable" are not defined. The authors state that simulations were run in triplicate, but the variance between replicates is only shown as error bars in Figure 5b without statistical testing. More critically, the authors do not report on the behavior of the histone proteins themselves, only the DNA. A nucleosome-like structure could maintain DNA wrapping while the histone core undergoes significant conformational changes. The manual placement of cluster 4 histones into the cluster 3 nucleosome structure (described in the text) is a subjective step that could bias the simulation outcome. The authors acknowledge that AlphaFold3 predictions have limitations, but they do not provide a systematic assessment of prediction confidence for the specific complexes studied, beyond reporting IPTM scores in supplementary figures.
- **Why it matters** The claim that most histone strategies form stable nucleosome-like structures is a central conclusion of the paper. If the simulation criteria for stability are not defined, or if the simulations are not sufficiently rigorous, this conclusion is not supported. The manual placement step introduces a potential source of bias that is not addressed. The distinction between "stable" and "unstable" complexes is crucial for the interpretation of which histone strategies are likely to be functional in DNA organization.
- **Resolution test** Define quantitative criteria for stability (e.g., RMSD thresholds, contact persistence, hydrogen bond occupancy) and apply them consistently across all simulations. Report the protein RMSD and the root-mean-square fluctuation (RMSF) per residue for the histone cores. Provide a sensitivity analysis for the manual placement of cluster 4 histones, testing multiple initial positions and orientations. Report the IPTM and pLDDT scores for all predicted complexes in the main text or a clearly referenced supplementary table. Consider running simulations at multiple salt concentrations for the halophilic complexes, not just 2 M KCl, to assess the robustness of the conclusions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Strength of environmental correlation claims
- **Claim pointer** The authors claim that "some strategies correlate with environmental pressures," specifically citing anaerobic conditions for combination 1 and 2 and extreme salinity for combination 3 and 4.
- **Evidence pointer** Results "Selective pressures may influence histone strategy", Figure 4d, Supplementary Table 2
- **Concern** The environmental correlation analysis is based on keyword matching of sample location annotations, which the authors acknowledge is difficult to quantify and verify. The statistical analysis is described as using the "Shapiro test" (likely a typo for Mann-Whitney U or Kruskal-Wallis test, as Shapiro-Wilk tests for normality, not group differences), and the specific test used is not clearly stated. The authors do not report effect sizes or confidence intervals for the observed correlations. The analysis does not account for phylogenetic non-independence, which is a major concern given that closely related species are more likely to share both environmental niches and histone strategies. The statement that "the correlations have to be taken with caution" is appropriate, but the analysis as presented does not provide a strong basis for even tentative conclusions.
- **Why it matters** The environmental correlation is presented as a notable finding that links histone strategy to ecological adaptation. If the statistical analysis is flawed or the correlations are not robust to phylogenetic correction, this claim is weakened. The authors themselves acknowledge the limitations, but the analysis should be strengthened to provide a more solid foundation for the claim.
- **Resolution test** Clearly state the statistical test used and justify its choice. Report effect sizes and confidence intervals for all comparisons. Perform a phylogenetic comparative analysis (e.g., using phylogenetic generalized least squares or independent contrasts) to test whether the correlations hold after accounting for evolutionary relationships. Provide a more detailed description of the keyword coding scheme and its validation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of conclusions from representative genomes
- **Claim pointer** The authors claim that their structural predictions and simulations, based on representative genomes for each strategy, provide insight into "how they might interact with DNA" for the majority of archaeal histones.
- **Evidence pointer** Results "Structural prediction of histone complexes", Table 2, Methods "Structural prediction"
- **Concern** The selection of representative genomes is based on the centroid in the four-dimensional physical property space. While this is a reasonable approach for selecting a typical member of each cluster, it does not address the within-cluster diversity. The authors do not report how much variation in physical properties exists within each cluster, nor do they demonstrate that the structural predictions and simulation results are representative of the cluster as a whole. For example, the cluster 1 basic singlets are described as having two sub-clusters (1-A and 1-B) with different pI values, but the structural analysis only considers one representative. It is unclear whether the conclusions drawn from the representative would hold for other members of the cluster.
- **Why it matters** The conclusions about histone-DNA interactions are meant to be generalizable to the entire diversity of archaeal histones. If the representatives are not truly representative, or if the within-cluster diversity is large, the conclusions may not apply broadly. The authors should demonstrate that their findings are robust to the choice of representative.
- **Resolution test** Perform structural predictions and simulations on multiple members of each cluster, particularly for clusters with high within-cluster variance in physical properties. Report the range of IPTM scores and simulation outcomes across these additional representatives. Alternatively, provide a quantitative analysis showing that the physical property variation within each cluster is small enough that the representative is likely to be typical.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure presentation
- **Affected element** Figure 1a
- **Evidence pointer** Figure 1a
- **Issue** The three-dimensional scatter plot in Figure 1a is difficult to interpret in static form. The clusters are color-coded, but the overlap between clusters in the projected view makes it hard to assess the separation. The black dots marking centroids are not clearly visible for all clusters.
- **Required correction** Consider providing multiple two-dimensional projections of the clustering, or an interactive figure that allows the reader to rotate the plot. Increase the size and contrast of the centroid markers.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 4
- **Evidence pointer** Figure 4, Methods "Metadata correlation"
- **Issue** The statistical comparisons in Figure 4 are not fully described. The text mentions the "Shapiro test" which is a test for normality, not for group differences. The specific test used for the boxplot comparisons is not stated.
- **Required correction** Clearly state the statistical test used for each comparison in the figure legend and methods. If the Shapiro-Wilk test was used to check normality assumptions, describe the subsequent test used for group comparisons.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout
- **Evidence pointer** Abstract, Results, Discussion
- **Issue** The term "hypernucleosome" is used to describe the nucleosome-like structures formed by archaeal histones, but the definition is not provided until the Discussion. The abstract uses the term without explanation.
- **Required correction** Define "hypernucleosome" at first use in the abstract or introduction.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Methods "Molecular dynamics simulations"
- **Evidence pointer** Methods "Molecular dynamics simulations"
- **Issue** The methods state that simulations were run for 100 ns in triplicate, but do not report the equilibration protocol, the thermostat and barostat settings, or the integration time step. The "Tug" function in ChimeraX is mentioned but not described in sufficient detail to be reproducible.
- **Required correction** Provide a complete description of the simulation protocol, including equilibration steps, ensemble (NPT or NVT), temperature and pressure coupling methods, and any restraints applied during the simulation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The authors acknowledge the limitations of AlphaFold3 predictions, but do not discuss the limitations of the DBSCAN clustering approach or the potential biases in the underlying genome database. The overrepresentation of halophiles is mentioned briefly but not discussed in depth.
- **Required correction** Add a paragraph discussing the potential biases in the genome database and how they might affect the conclusions. Discuss the limitations of clustering based on physical properties and the potential for functionally distinct histones to be grouped together.

- **Technical failings that need to be addressed before the case is established** R1-M1 (clustering robustness) and R1-M2 (simulation stability criteria) are the primary technical issues that must be resolved. The clustering methodology is the foundation of the entire analysis, and the simulation conclusions are a central claim. Without addressing these, the case for the manuscript's main conclusions is not fully established. R1-M3 (environmental correlations) and R1-M4 (representative generalizability) are important but less critical; they should be addressed to strengthen the claims but do not necessarily invalidate the core findings.

- **Assessment against Nature-style criteria** 
  - **Originality**: The manuscript is original in its comprehensive approach to surveying archaeal histone diversity using physical properties rather than sequence similarity. The identification of acidic histones as a major class is a novel finding. The systematic mapping of histone strategies onto a taxonomic tree is a new contribution.
  - **Scientific importance**: The work addresses a fundamental question about the diversity and evolution of chromatin proteins. The finding that most archaeal histones, including acidic ones, are predicted to form nucleosome-like structures has implications for our understanding of the origins of eukaryotic chromatin. The identification of universal histone signature motifs is potentially important.
  - **Interdisciplinary readership**: The work will appeal to chromatin biologists, archaeal microbiologists, evolutionary biologists, and computational biologists. The use of multiple methods (bioinformatics, structure prediction, molecular dynamics) broadens the potential audience.
  - **Technical soundness**: The technical soundness is currently not fully established due to the concerns raised about clustering robustness and simulation stability criteria. The methods are generally appropriate, but the lack of detail and validation in key areas weakens the overall technical quality.
  - **Readability for nonspecialists**: The manuscript is generally well-written and accessible. The concepts are introduced clearly, and the figures are informative. However, some sections, particularly the methods, assume familiarity with bioinformatic and simulation techniques. The abstract is clear and accessible.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important topic and presents a valuable resource for the community. The core findings are potentially significant, but the clustering methodology and simulation analysis need to be strengthened to fully support the conclusions. The authors should also address the statistical analysis of environmental correlations and demonstrate the generalizability of their structural predictions. If these concerns are adequately addressed, the manuscript would be a strong contribution to the field.