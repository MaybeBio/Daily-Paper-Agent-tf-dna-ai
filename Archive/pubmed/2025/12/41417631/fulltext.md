# MOKA: a pipeline for multiomics bridged SNP-set kernel association test


## Abstract
  The explosion of genomic and multiomics data has created a need for scalable, reproducible tools that integrate functional annotations into genome-wide association studies (GWAS). We introduce the multiomics data bridged Kernel Association test (MOKA) pipeline, a Snakemake-based workflow that automates SNP-set kernel-based association testing by incorporating multiomics data, including gene expression, transcription factor binding, evolutionary conservation scores, and neural network-derived features. This data-bridged architecture enhances variant prioritization and aggregation, improving statistical power in GWAS. MOKA supports population structure correction via spectral decomposition, parallel computation, and post-GWAS analyses, including visualization, Gene Ontology annotation, pathway enrichment, and validation. As a use case, we applied MOKA to a schizophrenia GWAS cohort, identified 89 Bonferroni-significant genes, with a 15.7% validation rate in the disease-specific DisGeNET database and enrichment in pathways relevant to neuropsychiatric disease. MOKA provides a robust, scalable, and extensible framework for functional multiomics integration in genetic studies. It is open-source and available at https://github.com/davidenoma/moka.


## Introduction
  Genome-wide association studies (GWAS) have been instrumental in identifying genetic variants associated with complex traits and diseases (Wu et al. 2010; Dehghan 2018). However, a large proportion of heritability remains unexplained, particularly due to limitations in detecting the cumulative effects of causal variants (Manolio et al. 2009). Leveraging functional multiomics data has shown promise in improving GWAS by enabling more informed variant selection and aggregation (Wu et al. 2010).

  Our previous work introduced kernel-based association tests using a data-bridged architecture (Cao et al. 2021), which integrates external multiomics data to guide variant prioritization and aggregation in downstream analyses. This framework has been successfully applied to diverse modalities, including gene expression (Cao et al. 2022a), brain imaging-derived phenotypes (He et al. 2024 ), transcription factor occupancy (He et al. 2022), and transcription factor binding-informed trans-variants (He et al. 2025). A public database resource was also developed to disseminate genome-wide results (Cao et al. 2022b).

  As genomic and multiomics datasets continue to expand in scale and complexity, there is a growing need for robust, scalable, and reproducible tools that streamline processing and analysis. Workflow management systems such as Snakemake (Koster and Rahmann 2018) have gained popularity due to their reproducibility, scalability, and ease of integration with high-performance computing environments. Despite the increasing complexity of the multiomics studies (Cooper and Shendure 2011 ), there is a lack of automated pipelines tailored for kernel-based association tests, a class of statistical methods that model the joint effects of multiple variants in genetic studies. Several related workflows exist. Nf-GWAS pipeline (Song et al. 2021) and Compile GWAS (Hill et al. 2022) provide automated orchestration of conventional GWAS analyses, focusing on quality control, association testing, and result summarization. The Ensembl post-GWAS tool focuses primarily on fine-mapping and credible set identification but does not perform genome-wide testing or integrate functional annotations. Importantly, none of these workflows incorporates external variant-level functional weights or provides end-to-end biological interpretation within a unified framework.

  To address these gaps, we introduce the Multiomics Kernel-based Association (MOKA) pipeline, a fully automated analysis workflow built on the Snakemake workflow management system (Koster and Rahmann 2018). MOKA is a modular, reproducible, and scalable framework that integrates externally derived functional weights directly into kernel-based gene-level association tests. This pipeline streamlines the entire analysis process, from multiomics data integration and kernel-based association testing (with correction for population structure) to result visualization, biological annotation, disease database validation, Gene Ontology enrichment, and pathway analysis.


## Methods

### Design of MOKA
  The MOKA pipeline is implemented using the Snakemake workflow management system (Koster and Rahmann 2018). Installation requires only a few simple steps, as outlined in the MOKA online documentation (https://github.com/davidenoma/moka).


### Configuration, data and software requirements
  MOKA requires input genotype data in PLINK binary format (bed, bim, fam) (Purcell et al. 2007). Configuration is handled through a YAML file (config/config.yaml, see Table 1), which specifies input files, parameters, and auxiliary scripts. To optimize computational efficiency, MOKA supports chromosome-level parallelization by invoking GNU Parallel (Tange 2018) within a single Snakemake rule. Gene regions are defined as ±500 kb from gene boundaries based on the hg38 human genome reference (Mudge et al. 2025). This is a pragmatic choice that captures most proximal regulatory variants. Gene-based GWAS workflows use 1 Mb windows (upstream and downstream) (Barbeira et al. 2018; Kerimov et al. 2021; He et al. 2024); MOKA offers a configurable parameter (default 500 kb) so users can configure those settings and adapt to their needs (Table 1).


### Multiomics data bridge
  Multiomics data sources include user-defined functional genomic annotations at the nucleotide level, capturing biologically relevant features (Fig. 1a), such as cis-regulatory variants, transcription factor binding (He et al. 2022, 2025 ), evolutionary conservation scores (Hubisz and Pollard 2014), gene expression changes (Li et al. 2024), imaging-derived weights, neural network-based (Li et al. 2023) approaches (Enoma et al. 2022), and others that promise to uncover disease-associated variants and genes (Cooper and Shendure 2011). MOKA accepts variant-level functional weights as optional input to incorporate biologically informed priors into the kernel-based association framework. These weights are numerical scores that quantify the presumed functional relevance of individual variants and can be derived from a broad range of multiomics resources, including evolutionary conservation metrics, eQTL effect sizes, neural network-based regulatory predictions, transcription factor occupancy data, or imaging-derived annotations.

  The input weight file must be provided in comma-separated format (CSV) with 4 columns (SNP_ID, Chromosome, Position, and Weight) (Table 1), where each row corresponds to a SNP present in the genotype dataset. An example is shown below in Box 1:

  Variants not included in the file are automatically assigned a default weight of 1. Weight values are typically continuous between 0 and 1, but MOKA does not impose a specific range, reflecting the relative importance of each SNP.

  Currently, MOKA supports a single weight file per analysis run to ensure computational efficiency and interpretability. However, users may conduct multiple analyses using different omics-derived weight sets or combine several sources into a composite weight file prior to analysis. In this way, MOKA provides a flexible and extensible framework for integrating biologically informed priors from diverse omics layers with genome-wide genotype data within a unified kernel-based association model.


### Kernel-based association testing with multiomics weights
  Within the input GWAS dataset, each SNP set or gene region is tested using a kernel-based method, which flexibly models epistatic and nonlinear effects of SNPs (Wu et al. 2010). For each individual, a weighted kernel is constructed using the SNPs and the corresponding data-bridged weights (Fig. 1b).

  where X is the genotype matrix for the SNPs in each gene region, Wmo is a diagonal matrix defined as Wmo = diag (β^1,…,β^p), with p being the number of selected variants. The weights β^i are derived from multiomics data integration. This data-bridged weighted kernel (Kw) is used in the association analysis implemented through a kernel-based test. The test statistic is defined as:

  where Y is the vector of phenotype values from the GWAS dataset, and Kw is the weighted kernel matrix defined above. Under the null hypothesis, Q follows a mixture of chi-squared distributions.

  The Q-score test statistic evaluates whether the SNPs within the gene regions contribute to the observed phenotypic variation. The significance of the association for each gene region is assessed by calculating the P-value at a 0.05 threshold (prior to multiple testing correction), based on the null distribution of Q.


### Data transformation to control population structure
  Uneven genetic relatedness will cause population structure, leading to inflated P-values (Kang et al. 2010). Linear mixed models are usually used for controlling this in single-SNP analysis (Lippert et al. 2011). However, here we are carrying out a gene-based set test and aggregating SNPs within the gene region. To handle this problem, we use a transformation based on the spectral decomposition of the genomic relationship matrix (GRM).

  Previous work was done for both GWAS (Long et al. 2013) and gene expression analysis (Long et al. 2016) to decorrelate artifacts caused by uneven genetic relatedness using the same decompositions, which we implement as a feature in the MOKA snakemake pipeline (https://github.com/davidenoma/moka).

  Assuming the Linear Mixed model without the fixed effect of a SNP takes form:

  where Y is the phenotype vector with n samples, Z is the covariate matrix, and β is the vector of fixed effect sizes. g represents the random genetic effects, with σg2 denoting the genetic variance and G being the genomic relationship matrix (GRM). ϵ denotes the residual effects, and σe2 is the residual variance.

  Then, the variance of Y is given by Var(Y)=σg2G+σe2I, and the unknown parameters (σg2and σe2) can be efficiently estimated using methods such as restricted maximum likelihood (REML) (Lippert et al. 2011; Yang et al. 2011a). Residual structure in G can inflate the genome-wide test statistics, a phenomenon usually summarized by the genomic inflation factor λGC, defined as the ratio of the median observed chi-square (χ2) statistic to its null expectation (Devlin and Roeder 1999).

  We denote the eigen decomposition of GRM to be G=USUT, where U is an orthogonal matrix, whose columns are the eigenvectors of G, and S is a diagonal matrix containing the corresponding eigenvalues.

  Substituting this into Var(Y), we obtain:

  Next, we define a transformation matrix D=(σg2S+σe2I)−12UT.

  Subsequently, the transformed varian=Ice of Y becomes:

  The last step holds because (σg2S+σe2I) is a diagonal matrix.

  Now, we apply this transformation to both the phenotype Y (with n samples) and the genotype X (with n samples and p variants), defining Y~=DY and X~=DX. This transformation ensures that the covariance matrix of Y~ is the identity matrix, ie Var(Y~)=I.

  So, we apply the MOKA test to the transformed data, we compute the test statistic:

  where Kw=X~WmoX~Tp is the kernel matrix and is Wmo a weight matrix that reflects the multiomics weight-specific contribution of each variant and used for MOKA. Spectral decomposition is available as a default functionality in MOKA, which can be toggled on or off in the configuration file of the pipeline (see Table 1).


### Genomic inflation factor (λGC) calculation
  Following Devlin and Roeder (1999), we first convert each gene-level P-value to its equivalent χ² statistic via the inverse cumulative-distribution function (inverse CDF) of a χ² distribution with one degree of freedom. χobs2~ denotes the median of these observed statistics. We then divide this value by the theoretical median of a χ² distribution with one degree of freedom, CDFχ2(1)-1(0.5):

  Because the denominator is approximately by theory, λGC ≈ 1 indicates well-calibrated test statistics, whereas λGC > 1.4 signals genomic inflation arising from unmodeled population structure or other confounding effects (Yang et al. 2011b); however, they show that even with perfect population structure matching, λGC rises roughly in proportion to polygenicity, so gene-level statistics with many contributing variants can have values well above 1 without implying confounding.


### Post-GWAS annotation and gene set enrichment
  The output structure is organized into easily navigable folders, including “output_plots” and “result_folder.” KEGG pathway enrichment (snakemake –cores 1 kegg_pathway_analysis) is performed using PathfindR (Ulgen et al. 2019) package, and the Gene Ontology analysis (snakemake –cores 1 go_analysis) is performed with g:Profiler (Reimand et al. 2007) package (Fig. 1c).

  DisGeNET (Pinero et al. 2017) is a database encompassing 1,134,942 gene-disease associations (GDAs) involving 21,671 genes and 30,170 traits. DisGeNET provides specific summaries for each disease within this platform, detailing gene associations and information on identified significant genes after multiple testing corrections and the proportions of associations are in the database (Fig. 1e) (snakemake –cores 1 disgenet_annotation_005).


## Results

### Configuration of MOKA and multiomics data bridge
  In this demonstration, we used 17-way human and primates accelerated conservation scoring (Siepel et al. 2005; Pollard et al. 2010) as weights (Wmo) for each variant. The acceleration measures quantify the extent of human-specific sequence change, such as sites that have diverged more rapidly than expected under neutrality. Negative phyloP (Pollard et al. 2010) scores already encode acceleration as −log₁₀p from a likelihood-ratio test, so negative values (eg phyloP ≤ −3, corresponding to P ≤ 10⁻³) signal human-specific evolution and associated disorder. These annotations are of particular interest in schizophrenia, a human-complex disease (Doan et al. 2016; Levchenko et al. 2018), providing a biologically informed basis for SNP aggregation.

  In the neural-network weights’ data bridge, weights (Wmo) were obtained by taking the element-wise sum of the variant-specific encoder and decoder weight matrices from a variational auto-encoder (VAE) (Kingma and Welling 2013) model, as previously described by Enoma. The network was trained on the input genotype data, so after tuning and convergence, the neural network weights learnt in the training process of the latent representations for reconstruction are extracted (Unterthiner et al. 2020; Herrmann et al. 2024).


### Association results
  Figure 2 presents a Manhattan plot of association results using negative conservation score–based weights, with genes on chromosomes 1 to 22 plotted against –log₁₀. The Bonferroni-corrected significance threshold (P = 2.64e−06) is shown as a horizontal line. Using human accelerated conservation scores as weights, 89 genes were significantly associated with schizophrenia. The top-associated gene, TMEM17, encodes a transmembrane protein involved in ciliogenesis and neural signaling, and has previously been implicated in schizophrenia (Bigdeli et al. 2021).


### External database validation
  For validation, we used DisGeNET disease-specific database as a reference database (schizophrenia in this case). The validation proportion was calculated as the fraction of false discovery rate (FDR)-significant genes at P- < 0.05 (Benjamini and Hochberg 1995), that overlapped with DisGeNET entries, ie the number of significant genes found in DisGeNET divided by the total number of significant genes identified in the analysis.

  Applying the MOKA association test to the schizophrenia GWAS dataset identified 2,245 significant genes, of which 15.7% (n = 351) were also reported in the DisGeNET database. To benchmark performance, we compared these results with 2 established association methods: SKAT (Wu et al. 2010), a kernel-based test aggregating variant effects across genomic regions; and REGENIE (Mbatchou et al. 2021), a scalable whole-genome regression framework designed for large-scale association studies. SKAT identified 2,530 genes, of which 13.3% (n = 337) overlapped with DisGeNET (genomic-inflation factor of λGC ≈ 113), and REGENIE identified 958 genes, with 12.0% (n = 115) supported by DisGeNET. These overlap proportions represent the fraction of genes detected by each method that were independently annotated in DisGeNET as schizophrenia-associated, providing an external indicator of the biological plausibility and validity of the detected associations.


### Spectral transformation controls genomic inflation factor
  The MOKA pipeline incorporates a transformation based on the spectral decomposition of the variance component to correct for test statistic inflation in kernel-based association analyses. This procedure improves calibration while preserving the biological relevance conveyed by functional variant weights (see Method). We define several modes of operation for clarity. MOKA-Ph refers to a MOKA run using phyloP evolutionary conservation scores as per-SNP functional weights, whereas MOKA-ED uses encoder–decoder (VAE)–derived weights (Enoma et al. 2025). The “-COR” suffix indicates that spectral correction is applied to the genomic relationship matrix; runs without “-COR” omit this step. These options are specified in the configuration file (config.yaml) by setting the appropriate weight file and toggling the spectral_correction parameter (true/false).

  In our schizophrenia GWAS, SKAT (Wu et al. 2010) yielded a highly inflated genomic inflation factor of λGC ≈ 113, indicating substantial confounding and false positives. REGENIE's whole-genome mixed model reduced this to ≈ 4.7, but lingering stratification remains. Using phyloP acceleration scores in MOKA (MOKA-Ph) reduced SKAT's inflation to 10.5. Applying MOKA's spectral correction (MOKA-Ph-COR) further lowered λGC to ≈ 4.3. While still above the ideal benchmark of <1.2, this matches REGENIE's calibration while retaining mechanistically informed weighting for improved power.

  The cohort-wide comparison (Table 2) shows SKAT inflates the test statistics (λGC ≈ 6.9 to 112.8), while REGENIE reduced this to 3.3 to 4.7. Incorporating encoder–decoder VAE weights in MOKA (MOKA-ED) reduces the inflation to 4.0 to 10.1, but remains above REGENIE. The decisive improvement comes from the spectral decomposition of the GRM: MOKA-ED-COR further reduces inflation to 2.5 to 4.6. In schizophrenia, λGC drops from 113 (SKAT) to 10.1 (MOKA-ED) and 4.6 (MOKA-ED-COR), comparable to REGENIE. These findings demonstrate that MOKA with spectral correction yields well-calibrated, biologically informed association tests, although additional adjustment for population structure may still be beneficial.


### Gene ontology analysis
  Gene ontology analysis in MOKA (Fig. 3) of FDR-significant results (P < 0.05) identified top terms for cellular component (cytoplasm, P = 2.0e−31), molecular function (protein binding, P = 5.0e−28), and biological process (anatomical structure development, P = 1.6e−12) for schizophrenia, respectively.


### KEGG pathway enrichment
  KEGG pathway enrichment analysis in MOKA (Fig. 4) of FDR-significant results (P < 0.05) identified several significantly enriched pathways. The top 5 pathways were Proteasome (P = 1.0e−11), human cytomegalovirus infection (P = 2.0e−10), nucleocytoplasmic transport (P = 4.0e−9), prion disease (P = 8.0e−9), and T-cell receptor signaling pathway (P = 1.2e−8).


## Conclusion
  MOKA is a scalable, automated Snakemake pipeline that enhances GWAS by integrating multiomics data through SNP-set kernel association tests and applying spectral decomposition to control genomic inflation and population structure. It supports comprehensive post-GWAS analyses and visualization.

  In the schizophrenia GWAS, SKAT produced extreme inflation (λGC ≈ 113) with a validation proportion of 13.3%. MOKA, using negative phyloP conservation scores as variant-level weights, reduced λGC to 10.5 and improved validation to 15.7%. Activating the spectral decorrelation step, which applies a spectral decomposition of the genomic relationship matrix to correct for population structure and test statistic inflation, further reduced inflation to 4.3. Across WTCCC and schizophrenia datasets, SKAT yielded λGC values between 6.9 and 113, while MOKA with correction reduced this to 2.5 to 4.6, comparable to REGENIE. Liu et al.(Liu et al. 2013) demonstrated that gene-based tests are susceptible to inflation from gene length and allele-frequency heterogeneity, and that single-SNP genomic control can be overly conservative. MOKA addresses these challenges by providing a robust, flexible, and user-friendly framework for multiomics integration and kernel-based association analysis, accessible to the broader research community.


## Data availability
  The genotype datasets are from the Molecular Genetics of Schizophrenia—nonGAIN Sample (MGS_nonGAIN) (dbGaP Study Accession: phs000167.v1.p1) are available at https://www.ncbi.nlm.nih.gov/projects/gap/cgi-bin/study.cgi?study_id=phs000167.v1.p1 and Wellcome Trust Case Control Consortium (WTCCC GWAS) (Wellcome Trust Case Control 2007) are in the public domain.

  The MOKA Pipeline is freely available on GitHub under the MIT license at https://github.com/davidenoma/moka. The official Docker image is provided at: https://hub.docker.com/r/davidenoma/moka-gwas. We have provided a test genotype dataset (genotype_data/) along with corresponding phyloP conservation scores (test_geno_weights) to facilitate software testing and reproducibility. The test dataset comprises randomly simulated genotypes containing 100 SNPs per chromosome across all 22 chromosomes, with simulated phenotypes for 1,000 cases and 1,000 controls. This example dataset allows users to verify installation, confirm correct execution of the pipeline, and explore the input and output structure of MOKA.

  The Conjoint Health Research Ethics Board (CHREB) at the University of Calgary approved this work with ID REB23-0045_REN. The PhyloP (Pollard et al. 2010) conservation scores for each variant position may be downloaded from the UCSC genome browser(Nassar et al. 2023).


## Funding
  This work is partly supported by the Mathison Centre Graduate Recruitment Scholarship (D.E.), ACHIR Graduate Scholarship (D.E.), the Alberta Innovates Graduate Scholarship (A.K. and D.W.), the Indigenous and Black Momentum Scholarship in Science (A.K.), and the Agriculture Funding Consortium through the Western Grains Research Foundation (D.E. and R.O.P.).


## Acknowledgments
  We want to acknowledge group members of the Quan Long Lab (Cumming School of Medicine, University of Calgary) that developed models showing the utility of the data-bridged architecture, which is now automated in the Multi omics kernel-based association testing (MOKA) pipeline to promote ease of use of reproducibility.