## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results and discussion, conclusions, materials and methods) as provided by the user. No figures, tables, or supplementary material were available for inspection.
- **Assessment boundary** The scientific claims, methodology, and internal consistency of the presented work, based solely on the supplied text. No external validation of data, code, or raw trajectories was performed.
- **Shared manuscript claim summary** The authors use microsecond-scale atomistic molecular dynamics simulations of full-length ExsA (monomeric and dimeric, with and without DNA) to propose that a single helix-turn-helix motif drives DNA recognition and allosterically stabilizes the ligand-binding domain. They also identify putative druggable pockets, including a novel extended region at the NTD/CTD interface.
- **Visible evidence base** Text descriptions of MD simulations (system setup, force field, simulation lengths, replica counts), RMSD/RMSF analyses, PCA, Gibbs free energy landscapes, distance/angle measurements, and pocket prediction results from multiple tools (SiteMap, PeSTo, PocketMiner, APOP, PASSer). References to figures, tables, and supplementary material that were not provided.
- **Missing materials affecting confidence** All figures, tables, supplementary information, and the Zenodo repository data. Specific numerical values for RMSD/RMSF, pocket scores, interaction frequencies, and simulation convergence metrics are absent. The exact AlphaFold3 model generation parameters and validation metrics (e.g., pLDDT values beyond qualitative description) are not fully detailed.

## Reviewer
- **Overall assessment** This manuscript presents a computationally intensive study of ExsA conformational dynamics, addressing a relevant gap in understanding full-length AraC-family regulators. The work is timely and the methodological approach is generally sound, with appropriate use of long-timescale MD simulations and multiple pocket prediction tools. However, the central claim that a single HTH motif "drives" DNA recognition and "stabilizes" the ligand-binding domain is not convincingly established from the evidence described. The allosteric mechanism is inferred primarily from distance/angle changes and RMSF patterns, but the causal link between HTH dynamics and NTD stabilization remains correlative. The pocket prediction results are interesting but lack experimental validation, and the novelty of the "novel" pockets is not clearly benchmarked against existing structural knowledge. The manuscript would benefit from clearer presentation of quantitative results and a more cautious interpretation of the allosteric claim.
- **Who would be interested in the results, and why** Researchers in bacterial pathogenesis, specifically those studying type III secretion systems and their regulation. Structural biologists and computational chemists interested in conformational dynamics of transcriptional regulators and allostery. Drug discovery groups targeting virulence factors in Pseudomonas aeruginosa and related pathogens, particularly those exploring allosteric sites on AraC-family proteins. The methodological approach may also interest computational biologists working on pocket prediction and MD-based drug target identification.
- **Major strengths** The study addresses a previously unexplored aspect of ExsA biology, namely the full-length conformational dynamics and interdomain communication. The use of multi-replica microsecond-scale simulations is appropriate and adds statistical power. The combination of multiple pocket prediction tools (including allosteric-specific methods) is a thoughtful approach. The identification of the HTH1-beta barrel pocket as a robust druggable site across simulation frames is a potentially valuable finding. The authors appropriately acknowledge limitations of their approach and suggest future directions.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (allosteric claim not quantitatively established), R1-M2 (pocket novelty not benchmarked), R1-M3 (mutant simulation analysis incomplete).
- **Assessment against Nature-style criteria** **Originality**: Moderate. The application of long-timescale MD to full-length ExsA is novel, but the conceptual framework (allostery in AraC-family proteins) is well established. **Scientific importance**: Moderate. The findings could inform drug design, but the lack of experimental validation limits immediate impact. **Interdisciplinary readership**: Limited. The work is primarily of interest to computational biologists and T3SS researchers; the presentation is technical and may not attract a broad audience. **Technical soundness**: Generally sound, but with gaps in quantitative reporting and validation. **Readability for nonspecialists**: Below average. The manuscript assumes significant familiarity with MD simulation methods and AraC-family biology; key concepts are not explained for a general scientific audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core computational work appears competently executed, but the central allosteric claim requires stronger quantitative support and the pocket predictions need clearer benchmarking. The manuscript would be suitable for a specialized computational biology or structural biology journal after major revision.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The abstract and conclusions state that "a single helix-turn-helix motif seems to drive DNA recognition in each ExsA monomer and to stabilize the putative ligand-binding domain." The results section further claims that "DNA binding to the CTD influences the beta-strand subdomain of the NTD, and that the conformations of the NTD and CTD are interdependent" and that "changes in one of these domains can allosterically influence the other."
- **Evidence pointer** Results sections "Conformational Flexibility of the NTD and Its Allosteric Interplay with the CTD" and "Movements between ExsA Domains Change the Conformation of the DNA-Binding Sites"; Figures 3, 4, 5 (not provided); Tables S1, S7 (not provided)
- **Concern** The allosteric claim is the central thesis of the manuscript, yet the evidence presented is largely correlative. The authors show that DNA binding reduces RMSF in the NTD and changes specific inter-residue distances (e.g., R25-W77), but they do not demonstrate a causal pathway from HTH-DNA engagement to NTD stabilization. The proposed mechanism involving the loop connecting beta8 to alpha1 is speculative and not supported by mutational analysis or perturbation studies (e.g., simulations with the loop mutated or with the HTH-DNA interaction disrupted). The distance measurements (R25-W77, R25-Y224) are presented as mean values, but no error bars, distributions, or statistical significance tests are reported. The claim that "a single HTH motif drives DNA recognition" is also problematic given that the bipartite HTH architecture is a defining feature of AraC-family proteins, and the authors themselves note that both HTH1 and HTH2 contact DNA. The distinction between "driving" and "contributing to" is not justified.
- **Why it matters** The allosteric mechanism is the primary novel contribution of the paper. If the claim is not quantitatively established, the manuscript reduces to a descriptive MD study with limited impact. The lack of statistical rigor in the distance measurements undermines confidence in the key observations.
- **Resolution test** Provide quantitative analysis with error bars and statistical tests (e.g., bootstrap or block averaging) for all reported distances and angles. Perform additional simulations with targeted mutations (e.g., alanine substitutions at the proposed allosteric pathway residues) or with the HTH-DNA interaction disrupted to test causality. Alternatively, use perturbation-response scanning or dynamical network analysis to identify the allosteric pathway. Clearly distinguish between "driving" and "contributing" based on the evidence.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Novelty and benchmarking
- **Claim pointer** The authors state that they identified "two novel potentially druggable pockets at the NTD/CTD interface" and describe a "novel extended region including the helices alpha12 and alpha13."
- **Evidence pointer** Results section "Potential Druggable Binding Pockets and Hotspots on ExsA"; Figures 6, 7 (not provided); Tables 1, S2-S10 (not provided)
- **Concern** The claim of novelty for the identified pockets is not adequately benchmarked. The authors do not compare their predicted pockets against known ligand binding sites in homologous AraC-family proteins beyond a brief mention of ToxT, Rns, and VirF. The "novel extended region" is described qualitatively, but no structural comparison (e.g., superposition with known AraC structures) is shown. The pocket prediction results are presented as consensus across tools, but the degree of agreement between tools is not quantified. The authors acknowledge that pocket prediction tools have limitations, but they do not provide a critical assessment of the confidence in each prediction.
- **Why it matters** The identification of novel druggable pockets is a key translational outcome of the work. If the pockets are not genuinely novel or are not robustly predicted, the drug design implications are weakened. The lack of benchmarking makes it difficult to assess the significance of the findings.
- **Resolution test** Provide a systematic comparison of the predicted pockets with known structures of AraC-family proteins, including structural superposition and analysis of conserved vs. novel features. Quantify the agreement between pocket prediction tools (e.g., Jaccard index or similar). For the "novel" pockets, provide a clear structural definition and discuss why they have not been previously identified.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Completeness of mutant analysis
- **Claim pointer** The authors state that "mutation of Y250 and R257 to alanine led to decreased DNA binding activity" and that they generated alanine mutants for HTH1 (3Ala-HTH1) and HTH1/HTH2 (3Ala-HTH1/3Ala-HTH2) to investigate the role of these residues.
- **Evidence pointer** Results section "Mutants on the DNA-Binding Interface Can Lead to NTD-CTD Uncoupling"; Figure S8 (not provided)
- **Concern** The mutant simulations are described only briefly. The authors report that the 3Ala-HTH1/3Ala-HTH2 mutant shows increased NTD-CTD distance, but no details are given on the simulation length, number of replicas, or convergence for these mutant systems. The choice of mutations is not fully justified (e.g., why these specific residues, and are they conserved across AraC-family proteins?). The relationship between the mutant simulations and the proposed allosteric mechanism is not clearly articulated. The authors mention that "longer time scale unbiased simulations or better selected collective variables would be relevant to fully grasp the mutation effects," which undermines the confidence in the conclusions drawn from the mutant data.
- **Why it matters** The mutant simulations are presented as supporting evidence for the allosteric mechanism. If they are not rigorously performed and analyzed, they do not strengthen the central claim. The lack of detail makes it difficult to assess the validity of the conclusions.
- **Resolution test** Provide full details of the mutant simulation setup (length, replicas, convergence metrics). Justify the choice of mutations based on sequence conservation and structural context. Clearly state what the mutant simulations demonstrate and what they do not, and avoid over-interpretation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Methods section "Protein 3D Structure Modeling"
- **Evidence pointer** Methods section, paragraph 1
- **Issue** The description of model generation is vague. The authors state that "all other models were generated using AlphaFold via the AlphaFold Colab resource" and that "for multimer predictions, we used the AlphaFold variant developed for multimers." It is unclear which specific AlphaFold version was used, what the input sequences were, and whether any template structures were used. The statement "using the default options" is insufficient for reproducibility.
- **Required correction** Provide the exact AlphaFold version, input sequence details, and any non-default parameters. If templates were used, specify them. Consider depositing the models in a public repository (e.g., ModelArchive) for transparency.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results sections reporting RMSD, RMSF, distances, and angles
- **Evidence pointer** Results sections "Conformational Flexibility of the NTD and Its Allosteric Interplay with the CTD" and "Movements between ExsA Domains Change the Conformation of the DNA-Binding Sites"
- **Issue** The manuscript reports mean values for distances and angles (e.g., "mean value of ∠22.9°") without standard deviations, confidence intervals, or statistical comparisons between systems. It is unclear whether the observed differences between conditions are significant given the expected thermal fluctuations in MD simulations.
- **Required correction** Report distributions or at least standard deviations for all quantitative measurements. Use appropriate statistical tests (e.g., bootstrap) to compare conditions and report p-values or effect sizes.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Abstract and conclusions
- **Evidence pointer** Abstract, last sentence; Conclusions, last paragraph
- **Issue** The phrase "a single helix-turn-helix motif seems to drive DNA recognition" is imprecise. The bipartite HTH architecture consists of two HTH motifs, and the authors themselves note that both HTH1 and HTH2 contact DNA. The claim that a "single" motif drives recognition is confusing and potentially misleading.
- **Required correction** Clarify whether the authors mean that one of the two HTH motifs is primarily responsible for DNA recognition, or that the bipartite HTH as a whole drives recognition. Use precise language that reflects the actual findings.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness of pocket analysis
- **Affected element** Results section "Potential Druggable Binding Pockets and Hotspots on ExsA"
- **Evidence pointer** Results section, paragraph 1
- **Issue** The authors state that "SiteMap identified all established pockets in the monomer simulation frames" but do not provide the SiteMap scores (SiteScore, DScore) for each pocket in the main text. The criteria for classifying a pocket as "druggable" are not clearly stated beyond a general reference to scores >0.8.
- **Required correction** Provide the numerical scores for each identified pocket in the main text or a clear summary table. State the specific criteria used to classify pockets as druggable.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Conclusions section
- **Evidence pointer** Conclusions, final paragraph
- **Issue** The authors acknowledge that their findings are based on computational predictions but do not discuss the limitations of using AlphaFold models as starting points for MD simulations. The potential impact of model inaccuracies on the simulation results is not addressed.
- **Required correction** Add a brief discussion of the limitations of the computational approach, including the reliance on predicted structures and the absence of experimental validation.

## Risk / unsupported claims
- The claim that "a single helix-turn-helix motif seems to drive DNA recognition in each ExsA monomer and to stabilize the putative ligand-binding domain" is not quantitatively established from the provided evidence. The causal link between HTH dynamics and NTD stabilization is inferred but not demonstrated.
- The claim that the identified pockets are "novel" is not benchmarked against existing structural knowledge of AraC-family proteins.
- The statement that "DNA binding contributes to structural stabilization" is supported only by qualitative descriptions of RMSF and FEL analysis; no quantitative comparison or statistical significance is provided.
- The biological relevance of the "type 1 dimer" as the more relevant conformation is asserted but not experimentally validated.
- The claim that "longer time scale unbiased simulations or better selected collective variables would be relevant to fully grasp the mutation effects" indicates that the mutant analysis is incomplete and its conclusions are preliminary.
- The statement that "the identified putative orthosteric pocket is orthologous to the known lipid binding pockets in ToxT, Rns and VirF" is not supported by a structural alignment or sequence comparison in the provided text.