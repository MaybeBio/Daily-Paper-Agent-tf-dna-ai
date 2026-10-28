## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, declarations) as provided.
- **Assessment boundary** Scientific content, methodological soundness, validity of claims, and presentation quality. Not an assessment of editorial fit or language editing.
- **Shared manuscript claim summary** The authors report a drought-response transcriptome of *Prosopis cineraria* (Thar desert tree), identify 54 up-regulated AP2/ERF transcription factors, classify 232 AP2/ERF proteins into 15 phylogenetic groups, document copy-number expansion relative to drought-sensitive species, identify inter-cultivar polymorphisms, and use AlphaFold modeling plus all-atom molecular dynamics simulations to argue that *P. cineraria* AP2/ERF proteins form more stable DNA contacts and bind the GCC-box with higher affinity than *Arabidopsis thaliana* orthologs.
- **Visible evidence base** Abstract, full methods, results narrative, discussion, figure legends (referenced but figures not provided), supplementary table legends (contents not provided).
- **Missing materials affecting confidence** Figures 1-7 and Supplementary Figures S1-S4 (not provided); Supplementary Tables S1-S5 (not provided); raw sequencing data (accession given but not inspected); qPCR primer sequences (referenced as Table S4, not provided); AlphaFold confidence metrics (pLDDT, PAE) not reported; MD simulation parameters and convergence criteria not fully detailed.

## Reviewer
- **Overall assessment** This manuscript addresses a timely and important question: what molecular features underlie exceptional drought tolerance in a keystone desert tree? The transcriptomic dataset from a non-model, stress-tolerant tree is a valuable resource. The observation that AP2/ERF genes are expanded and induced in *P. cineraria* is plausible and consistent with prior literature. However, the central mechanistic claim, that structural differences in the DNA-binding domain confer higher DNA-binding affinity in *P. cineraria* versus *A. thaliana*, is not convincingly established from the evidence presented. The comparative analysis relies on a small number of modeled structures, lacks experimental validation, and does not account for the possibility that the observed hydrogen-bonding differences arise from sequence divergence unrelated to affinity. The copy-number analysis is descriptive and does not establish a causal link to drought tolerance. The manuscript would benefit from a more rigorous quantitative framework, explicit statistical comparisons, and experimental validation of binding affinity.
- **Who would be interested in the results, and why** Plant stress biologists, particularly those studying drought tolerance mechanisms and transcription factor families; researchers interested in extremophile plants and desert adaptation; computational biologists working on protein-DNA interactions and molecular dynamics; breeders seeking candidate genes for engineering drought tolerance in crops.
- **Major strengths** 1) The study provides a new transcriptomic resource for a non-model, stress-tolerant tree species, which is of broad value. 2) The phylogenetic classification of the AP2/ERF superfamily in *P. cineraria* is a useful contribution. 3) The combination of transcriptomics, genomics, and structural modeling is ambitious and integrative. 4) The identification of inter-cultivar polymorphisms is a novel angle with potential applied relevance.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (copy-number claim), R1-M2 (binding-affinity claim), R1-M3 (MD simulation support), R1-M4 (qPCR validation), R1-M5 (polymorphism analysis).
- **Assessment against Nature-style criteria**  
  - *Originality*: Moderate. The transcriptomic dataset is new, but the general finding that AP2/ERF genes are involved in drought responses is well established. The structural comparison of DNA-binding domains across species is a relatively novel angle, though not unprecedented.  
  - *Scientific importance*: Potentially high, if the mechanistic claims were rigorously supported. As presented, the importance is diminished by the lack of experimental validation and the descriptive nature of the copy-number analysis.  
  - *Interdisciplinary readership*: The topic bridges plant biology, genomics, and structural biology, which could attract a broad audience. However, the technical presentation may limit accessibility for non-specialists.  
  - *Technical soundness*: Mixed. The transcriptomic and phylogenetic analyses appear sound, but the structural modeling and MD simulation sections lack sufficient detail and validation to be considered technically robust.  
  - *Readability for nonspecialists*: The manuscript is generally well written, but the structural biology sections assume significant prior knowledge. A clearer explanation of the significance of hydrogen-bonding differences and binding free energies would improve accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has merit and potential, but the central mechanistic claims require substantial additional analysis and experimental validation before the case is convincing.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Copy-number claim
- **Claim pointer** "The *P. cineraria* genome contains more copies of AP2/ERF genes than drought-sensitive plants" (Abstract; Section 3.7).
- **Evidence pointer** Section 3.7, Figure 5 (not provided)
- **Concern** The copy-number comparison is based on a small and potentially biased sample of species. The authors compare 10 drought-tolerant and 10 drought-sensitive species, but the selection criteria for these species are not stated, and the phylogenetic relationships among them are not accounted for. Copy-number differences can arise from lineage-specific whole-genome or segmental duplications unrelated to drought tolerance. The analysis does not include a statistical test for the difference in copy numbers between the two groups, and the figure (Figure 5) is not available for inspection.
- **Why it matters** The claim that copy-number expansion is a drought-adaptation mechanism is a central pillar of the manuscript. Without a phylogenetically controlled, statistically rigorous comparison, the claim is not supported.
- **Resolution test** Provide a phylogenetically informed analysis (e.g., independent contrasts or phylogenetic generalized least squares) that accounts for shared ancestry. Include a statistical test (e.g., Mann-Whitney U or t-test) with effect sizes and confidence intervals. State the criteria for classifying species as drought-tolerant versus drought-sensitive, ideally with a quantitative metric.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Binding-affinity claim
- **Claim pointer** "Using all-atom molecular dynamics simulations, we teased out a higher number of specific DBD-DNA hydrogen bonds in *P. cineraria*, leading to a stronger DNA-binding affinity compared to drought-sensitive *Arabidopsis thaliana*" (Abstract; Section 3.9).
- **Evidence pointer** Sections 3.8, 3.9, Figure 7 (not provided)
- **Concern** The claim of higher binding affinity is based on a comparison of two modeled structures per group (one from *P. cineraria*, one from *A. thaliana*). This is a sample size of one per species per group, which is insufficient to draw general conclusions. The hydrogen-bonding differences are not tested for statistical significance, and the relationship between hydrogen-bond count and binding free energy is not established. The MM/GBSA calculations are mentioned but the results are not presented in detail, and the error estimates are not reported. The authors do not discuss the possibility that the observed differences are within the noise of the computational methods.
- **Why it matters** The claim of differential binding affinity is the most novel and impactful assertion in the manuscript. If it is not rigorously supported, the manuscript loses its central mechanistic contribution.
- **Resolution test** Increase the number of ortholog pairs analyzed per group. Report the distribution of hydrogen-bond counts and binding free energies with standard deviations across replicates. Perform a statistical test (e.g., t-test or bootstrap) comparing the two species. Validate the computational predictions with an experimental assay, such as electrophoretic mobility shift assay (EMSA) or surface plasmon resonance (SPR), measuring binding affinity of the purified DNA-binding domains to the GCC-box.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** MD simulation support
- **Claim pointer** "All-atom molecular dynamics simulations" (Section 2.12) and "stable hydrogen bonds" (Section 3.9).
- **Evidence pointer** Sections 2.12, 2.13, 3.9, Table S5 (not provided)
- **Concern** The methods section for MD simulations is incomplete. The force field parameters, water model, salt concentration, temperature and pressure coupling schemes, and simulation length are stated, but key details are missing: the initial structure preparation, the equilibration protocol, the criteria for defining a "stable" hydrogen bond, and the convergence of the simulations. The authors state that three replicates of 200 ns were performed, but the reproducibility of the hydrogen-bond analysis across replicates is not reported. The hydrogen-bond analysis is based on a 50% occupancy threshold, but the rationale for this threshold is not given.
- **Why it matters** The MD simulations are the primary evidence for the binding-affinity claim. If the simulations are not rigorously described and analyzed, the conclusions drawn from them are not reliable.
- **Resolution test** Provide a complete description of the simulation protocol, including equilibration steps, thermostat/barostat parameters, and hydrogen-bond definition. Report the time evolution of hydrogen-bond counts and the root-mean-square fluctuation of the protein-DNA interface. Show that the simulations have converged (e.g., by block averaging or comparing independent replicates). Justify the hydrogen-bond occupancy threshold.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** qPCR validation
- **Claim pointer** "Up-regulation of 54 APETALA2/Ethylene-Responsive Factor (AP2/ERF) transcription factor genes, validated by real-time PCR" (Abstract; Section 3.3).
- **Evidence pointer** Section 3.3, Figure 3A (not provided)
- **Concern** The qPCR validation is described for five genes, but the criteria for selecting these five genes are not stated. The figure (Figure 3A) is not available, so the magnitude and statistical significance of the expression changes cannot be assessed. The authors do not report the number of biological replicates, the reference genes used for normalization, or the statistical test applied.
- **Why it matters** The qPCR validation is presented as confirmation of the transcriptomic results. Without proper reporting, the validation is not convincing.
- **Resolution test** State the selection criteria for the five genes. Report the number of biological and technical replicates, the reference genes, and the statistical test used. Show the expression changes with error bars and significance levels.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Polymorphism analysis
- **Claim pointer** "We identified sequence polymorphisms in AP2/ERF genes between Arabian and Indian cultivars of *P. cineraria*" (Abstract; Section 3.6).
- **Evidence pointer** Section 3.6, Table 2 (not provided)
- **Concern** The polymorphism analysis is presented as a result, but the functional significance of the identified polymorphisms is not discussed. The authors do not state whether the polymorphisms are in coding or non-coding regions, whether they alter protein sequence, or whether they are predicted to affect function. The table (Table 2) is not available for inspection.
- **Why it matters** The claim of inter-cultivar polymorphism is presented as a finding, but without functional interpretation, its relevance to drought tolerance is unclear.
- **Resolution test** Classify the polymorphisms (synonymous vs. non-synonymous, coding vs. non-coding). For non-synonymous changes, predict the effect on protein structure or function. Discuss whether any polymorphisms fall within the DNA-binding domain or other functional regions.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Differential expression analysis (Section 2.1, Section 3.1)
- **Evidence pointer** Section 3.1, Figure 1A (not provided)
- **Issue** The authors state that 2,434 genes were up-regulated and 1,377 down-regulated, but the thresholds for significance (FDR and fold-change) are stated in the methods. However, the number of biological replicates and the statistical model used (e.g., DESeq2 default) are not described in sufficient detail.
- **Required correction** Specify the number of biological replicates per condition and the exact model and contrast used in DESeq2/edgeR.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Transcriptome assembly (Section 2.2)
- **Evidence pointer** Section 2.2
- **Issue** The authors state that a de novo assembly was generated, but the assembly statistics (e.g., number of transcripts, N50, BUSCO completeness) are only partially reported. The BUSCO score is given for both assemblies, but the N50 is given only for the two assemblies, not for the final set of transcripts used in the analysis.
- **Required correction** Provide full assembly statistics, including the number of transcripts, the total length, and the N50 for the final transcript set.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** All figures
- **Evidence pointer** Figures 1-7 (not provided)
- **Issue** The figures are not available for review. The figure legends are present but do not provide sufficient detail to evaluate the data.
- **Required correction** Ensure that all figures are self-explanatory, with clear axis labels, legends, and statistical annotations.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section 3.8
- **Evidence pointer** Section 3.8
- **Issue** The authors state that the DNA-binding domain is "relatively conserved" but do not provide a quantitative measure of conservation (e.g., percent identity or similarity).
- **Required correction** Provide a quantitative measure of sequence conservation for the DNA-binding domain across the species compared.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Section 4 (Discussion)
- **Evidence pointer** Section 4
- **Issue** The discussion does not acknowledge the limitations of the computational approach, such as the lack of experimental validation of binding affinity and the small number of structures compared.
- **Required correction** Add a paragraph discussing the limitations of the study and the need for experimental validation.

## Risk / unsupported claims
- The claim that *P. cineraria* AP2/ERF proteins have "greater DNA-binding affinity" than *A. thaliana* orthologs is not supported by the evidence presented. The comparison is based on a small number of modeled structures, lacks statistical analysis, and is not validated experimentally.
- The claim that copy-number expansion of AP2/ERF genes is a drought-adaptation mechanism is not supported by a phylogenetically controlled analysis.
- The claim that "these results directly support copy number expansion of AP2/ERF transcription factors and the evolution of their structures for more efficient DNA search and binding as drought adaptation mechanisms" is an overstatement given the descriptive nature of the copy-number analysis and the lack of experimental validation of the structural claims.
- The functional significance of the identified inter-cultivar polymorphisms is not established.
- The qPCR validation is not fully reported, and the statistical significance of the expression changes cannot be assessed from the provided information.