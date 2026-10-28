## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results, discussion, and supplementary figure/table references
- **Assessment boundary** Scientific content, technical soundness, structural claims, and functional interpretations presented in the manuscript
- **Shared manuscript claim summary** The authors report a 2.2 Å co-crystal structure of the yeast Forkhead transcription factor Fkh1 DNA-binding domain bound to a 19-bp DNA duplex. They describe a novel protein fold among Forkhead proteins, featuring an extended, well-structured Wing 2 region that forms base-specific contacts with the DNA minor groove. They combine structural analysis with molecular dynamics simulations, deep-learning predictions, and in vivo yeast assays to propose a mechanism whereby Wing 2 arginine residues (R400 and R401) modulate DNA binding through minor groove width sensing, with R400 able to substitute for R401 upon mutation.
- **Visible evidence base** Co-crystal structure (PDB ID 9EFW), X-ray diffraction statistics (Supplementary Table S2), MD simulation protocols and analyses (Supplementary Section S-II, Figs S18, S19, S22–S25, Table S4), DeepPBS and BioEMU analyses (Supplementary Figs S17, S26), yeast in vivo complementation assays (Fig. 4C, Supplementary Figs S20, S21), AF2 and AF3 predictions (Supplementary Figs S15, S16)
- **Missing materials affecting confidence** Supplementary figures and tables referenced throughout the text were not provided for review. This includes Supplementary Tables S1–S4, Supplementary Figs S1–S27, and Supplementary Sections S-II and S-III. The electron density maps and structure validation metrics beyond what is stated in the text could not be independently assessed. The SELEX-seq data referenced from prior work [13] were not included.

## Reviewer

### Overall assessment
This manuscript presents a structurally and functionally rich analysis of the Fkh1 DNA-binding domain, with a potentially significant finding: a previously unobserved Wing 2 conformation that forms base-specific minor groove contacts. The crystallographic work appears technically sound based on the described methods, and the integration of MD simulations, deep-learning tools, and in vivo functional assays provides a multi-pronged approach to validate the structural observations. However, the central claim of a "novel fold" requires careful scrutiny, as the overall winged-helix architecture is conserved; the novelty appears to reside in the extended, structured Wing 2 region rather than in a fundamentally new fold. The functional significance of the Wing 2 minor groove contacts is supported by the in vivo data, but the mechanistic interpretation regarding DNA shape sensing would benefit from more direct experimental evidence. The manuscript is generally well written and accessible, though some structural details are dense.

### Who would be interested in the results, and why
Structural biologists studying transcription factor DNA recognition, particularly winged-helix proteins, will find the Fkh1 structure of interest. Researchers working on Forkhead family proteins across species will value the comparative structural analysis, especially the Wing 2 differences. The DNA shape-mediated recognition mechanism has broader relevance to the gene regulation community, and the demonstration that AF2 can guide construct design for crystallization is a useful methodological contribution. The yeast genetics community may also be interested in the functional validation of Fkh1 wing residues.

### Major Strengths
1. The co-crystal structure at 2.2 Å resolution provides a high-quality view of a Forkhead DBD from yeast, filling a taxonomic gap in the family.
2. The identification of a structured Wing 2 with base-specific minor groove contacts is a novel observation that challenges the prevailing view of Wing 2 as a largely unstructured, backbone-interacting element.
3. The combination of structural, computational, and in vivo approaches is commendable and provides multiple lines of evidence for the functional importance of the wing regions.
4. The demonstration that R400 can compensate for R401 loss, supported by both MD simulations and yeast phenotyping, is a compelling mechanistic insight.
5. The practical use of AF2 for construct design is a useful and transferable methodological point.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural novelty claim
- **Claim pointer** The title and abstract state that the Fkh1-DBD reveals a "previously unknown protein fold among all known Forkhead proteins" and a "novel fold."
- **Evidence pointer** Results section "Novel protein fold of Fkh1-DBD", Fig. 1E, Fig. 2, Supplementary Fig. S12
- **Concern** The term "novel fold" is an overstatement. The Fkh1-DBD adopts a canonical winged-helix architecture with three core helices (H1, H2, H3), a 310-helix, and two beta strands, consistent with the conserved Forkhead domain topology. What appears novel is the extended, structured C-terminal region (Wing 2) comprising approximately 40 residues with two additional helices (H5, H6). This is an extension or elaboration of the winged-helix fold, not a new fold. The authors should temper the language to "extended winged-helix fold" or "novel Wing 2 conformation" to accurately reflect the structural findings.
- **Why it matters** Overstating the novelty of the fold could mislead readers and invite unnecessary scrutiny. The genuine novelty lies in the Wing 2 structure and its DNA contacts, which is sufficiently interesting without overclaiming. Precise language is essential for a structural paper of this type.
- **Resolution test** Revise the title and abstract to describe the finding as an extended or elaborated winged-helix fold with a uniquely structured Wing 2, rather than a "novel fold." Provide a clear structural comparison in Fig. 2 or Supplementary Fig. S12 that quantitatively demonstrates the differences in Wing 2 length and secondary structure content relative to other Forkhead proteins.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional significance of Wing 2 minor groove contacts
- **Claim pointer** The authors claim that Wing 2 forms base-specific contacts with the minor groove that contribute to binding affinity and specificity, and that R401 modulates minor groove width.
- **Evidence pointer** Results sections "DNA recognition in Fkh1-DBD–DNA complex" and "R401 residue modulates interaction with minor groove", Fig. 3C, Supplementary Figs S18, S19
- **Concern** The base-specific contacts attributed to Wing 2 are described primarily for R401 with G2 and C18'. However, the functional significance of these contacts is inferred from MD simulations and in vivo phenotyping, not from direct binding affinity measurements. The in vivo assay (complementation of pseudohyphal growth) is indirect and does not quantitatively measure DNA binding affinity or specificity. The correlation between R401 distance and minor groove width (r = −0.66) is suggestive but does not establish causality. Direct binding measurements (e.g., EMSA, ITC, or SPR) with wild-type and mutant proteins would substantially strengthen the claim that these contacts contribute to binding affinity.
- **Why it matters** The central mechanistic claim of the paper is that Wing 2 minor groove contacts, particularly via R400 and R401, are functionally important for DNA binding. Without direct binding data, the functional significance remains correlative. The in vivo data show that these residues matter for Fkh1 function, but not necessarily through direct DNA binding affinity effects.
- **Resolution test** Provide quantitative DNA binding measurements (e.g., EMSA or fluorescence anisotropy) for wild-type Fkh1-DBD and the R400A, R401A, and double mutants against the consensus and variant DNA sequences. If binding affinity differences are observed, this would directly support the claim. Alternatively, if binding affinities are unchanged, the in vivo effects may be due to other mechanisms (e.g., protein stability, cellular localization), which should be discussed.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** MD simulation methodology and interpretation
- **Claim pointer** The authors use MD simulations to support the substitution mechanism (R400 compensating for R401) and to relate conformational flexibility to function.
- **Evidence pointer** Methods section "Molecular dynamics simulations", Results sections "Mutations reveal substitution mechanism" and "Deep learning-based analyses", Supplementary Figs S18, S19, S22–S25, Supplementary Table S4
- **Concern** The MD simulation methods are described only briefly in the main text, with details relegated to Supplementary Section S-II, which was not provided. Key parameters such as force field, water model, simulation length (beyond the stated 300 ns), number of replicas, and convergence criteria are not stated in the main text. The claim that R400 substitutes for R401 in the mutant is based on distance measurements from MD trajectories, but the statistical robustness of this observation across replicas is not fully described. Additionally, the use of a single 300 ns simulation per system may be insufficient to sample the conformational space relevant to minor groove width fluctuations.
- **Why it matters** MD simulations are used as a key line of evidence for the substitution mechanism. If the simulations are not well-converged or the methods are not transparent, the conclusions drawn from them are weakened. The reader cannot assess the quality of the simulations without the supplementary methods.
- **Resolution test** Provide the full MD simulation details in the main text or ensure the supplementary methods are complete and accessible. Include information on force field, water model, temperature/pressure coupling, simulation length, number of replicas, and convergence metrics. Show that the R400 substitution in the R401A mutant is observed consistently across multiple independent simulations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** In vivo functional assay interpretation
- **Claim pointer** The authors state that yeast in vivo experiments demonstrate that wing residues interacting with flanking regions are important for Fkh1 function.
- **Evidence pointer** Results section "Functional validation of Fkh1 wing–DNA contacts and arginine substitution mechanism", Fig. 4C, Supplementary Figs S20, S21
- **Concern** The in vivo assay relies on complementation of the pseudohyphal growth phenotype in fkh1Δ fkh2Δ cells. While this is a reasonable assay for Fkh1 function, it is indirect and does not specifically report on DNA binding. The partial complementation observed with the double mutant (R400A, R401A) could be due to reduced DNA binding, but could also result from protein misfolding, reduced stability, or altered nuclear localization. The authors do not report protein expression levels or localization of the mutant proteins. Additionally, the assay is qualitative (microscopy-based classification of cell morphology), and the quantification method (percentage of cells in clusters) may not capture subtle differences in complementation efficiency.
- **Why it matters** The in vivo data are used to support the biological relevance of the structural findings. If the mutants have pleiotropic effects beyond DNA binding, the interpretation that wing-DNA contacts are specifically important for Fkh1 function is weakened. The assay should be complemented with more direct measurements of Fkh1 activity or DNA binding in vivo.
- **Resolution test** Include western blot analysis to confirm equal expression of wild-type and mutant Fkh1 proteins. Consider performing chromatin immunoprecipitation (ChIP) to assess whether the mutants affect Fkh1 occupancy at target loci in vivo. Alternatively, use a more quantitative reporter assay for Fkh1 transcriptional activity.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of structural comparisons
- **Affected element** Fig. 2 and Supplementary Fig. S12
- **Evidence pointer** Results section "Novel protein fold of Fkh1-DBD"
- **Issue** The comparison of the Fkh1-DBD structure to other Forkhead proteins is described in the text but the figure content is not fully described. It is unclear whether the structural alignment is shown with quantitative measures (e.g., RMSD values, percentage of secondary structure conservation) or merely as a visual overlay.
- **Required correction** Add a clear description of the structural alignment method and include quantitative comparison metrics (e.g., pairwise RMSD values, secondary structure assignment percentages) either in the figure or in the figure legend.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Abstract and Results
- **Evidence pointer** Abstract, Results section "DNA recognition in Fkh1-DBD–DNA complex"
- **Issue** The term "base-specific contacts" is used for Wing 2 interactions, but the described contacts include hydrogen bonds to bases (R401 with G2 and C18') as well as backbone and sugar interactions. The term "base-specific" should be reserved for contacts that discriminate between different bases, which is not fully demonstrated.
- **Required correction** Clarify which contacts are base-specific versus backbone or sugar-mediated. Consider using "base contacts" or "nucleobase contacts" where appropriate.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section "R401 residue modulates interaction with minor groove", Supplementary Fig. S18
- **Evidence pointer** Results section "R401 residue modulates interaction with minor groove"
- **Issue** The correlation coefficient of −0.66 between R401 distance and minor groove width is reported, but no confidence interval or p-value is provided. It is unclear how many data points were used for this correlation.
- **Required correction** Report the number of data points, the confidence interval, and the p-value for the correlation. If the correlation is calculated from time series data, account for autocorrelation in the statistical test.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** Fig. 4C
- **Evidence pointer** Results section "Functional validation of Fkh1 wing–DNA contacts and arginine substitution mechanism"
- **Issue** The microscopy images in Fig. 4C are described as showing cell morphology, but the scale bars and magnification are not mentioned in the text. The quantification method (percentage of cells in clusters) is described but the number of biological replicates and total cells counted are not stated.
- **Required correction** Add scale bars to the images and state the magnification. Report the number of biological replicates and the total number of cells counted for each strain in the figure legend or methods.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability completeness
- **Affected element** Data availability section
- **Evidence pointer** Data availability section
- **Issue** The data availability statement mentions the PDB deposition and links for MD protocols and microscopy images, but does not mention whether the SELEX-seq data from the prior study [13] are accessible or how to access them.
- **Required correction** Add a statement about the availability of the SELEX-seq data, either by referencing the prior publication's data availability or providing a link to the deposited data.

### Technical failings that need to be addressed before the case is established
1. The "novel fold" claim in the title and abstract is overstated and should be revised to accurately describe the extended Wing 2 structure within the conserved winged-helix framework.
2. Direct quantitative DNA binding measurements for the wing mutants are needed to substantiate the claim that Wing 2 minor groove contacts contribute to binding affinity.
3. The MD simulation methods are insufficiently described in the main text, and the supplementary methods were not available for review. Full methodological transparency is required.
4. The in vivo assay would benefit from additional controls (protein expression, localization) to rule out pleiotropic effects of the mutations.

### Assessment against Nature-style criteria
- **Originality**: The structure of a yeast Forkhead DBD with a well-ordered, extended Wing 2 forming base-specific minor groove contacts is a novel contribution. While the overall winged-helix fold is conserved, the specific Wing 2 architecture and its DNA recognition mode have not been previously described. The substitution mechanism (R400 compensating for R401) is an interesting and original observation.
- **Scientific importance**: The findings advance understanding of Forkhead protein DNA recognition, particularly the role of wing regions in minor groove interactions. The work has implications for the broader family of winged-helix transcription factors and for understanding how flanking sequences contribute to binding specificity. The demonstration that AF2 can guide construct design is a useful methodological contribution.
- **Interdisciplinary readership**: The work will appeal to structural biologists, transcription factor researchers, computational biologists, and yeast geneticists. The DNA shape-mediated recognition mechanism has relevance to the broader gene regulation field. The use of deep-learning tools (DeepPBS, BioEMU) may attract readers interested in AI-driven structural biology.
- **Technical soundness**: The crystallographic analysis appears technically sound based on the described methods, with appropriate refinement statistics. The integration of multiple computational and experimental approaches is commendable. However, the lack of direct binding measurements for the mutants and the incomplete description of MD methods are weaknesses that need to be addressed.
- **Readability for nonspecialists**: The manuscript is generally well written and accessible. The structural descriptions are clear, and the figures are well referenced. However, some sections, particularly the detailed structural comparisons and MD analyses, may be dense for nonspecialist readers. The abstract effectively summarizes the key findings.

### Recommendation posture
Supportive if technical concerns are resolved. The structural findings are novel and potentially significant, but the overstatement of the "novel fold" claim, the lack of direct binding measurements, and the incomplete description of MD methods need to be addressed before the case is fully established. The manuscript would be strengthened by tempering the language, adding quantitative binding data, and providing complete methodological details.