## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods)
- **Assessment boundary** Scientific content, experimental logic, structural modelling claims, and consistency with the stated conclusions. No assessment of editorial fit or publication venue.
- **Shared manuscript claim summary** The authors propose that a single DNA binding site of the DprA dimer is sufficient to facilitate RecA filament nucleation, based on biochemical assays with short oligodeoxythymidylate substrates, in vivo conjugation experiments, and a full-atomic model of the RecA-DprA-ssDNA complex.
- **Visible evidence base** In vivo Hfr conjugation frequency measurements (Table 1); ATPase/dATPase hydrolysis assays with RecA and RecA Bsu on (dT) n substrates (Figures 1-3); molecular modelling of the RecA-DprA-ssDNA complex (Figure 4); methods sections for protein purification, conjugation, and modelling.
- **Missing materials affecting confidence** Raw kinetic traces for ATPase/dATPase assays; statistical details for replicate experiments beyond stated "at least three times"; coordinates or validation metrics for the molecular model; strain construction details for the ΔdprA mutant; induction level quantification for DprA/DprA Bsu expression; control experiments for protein purity and activity.

## Reviewer
- **Overall assessment** The manuscript addresses a mechanistically interesting question regarding the minimal requirements for DprA-mediated RecA loading onto ssDNA. The in vivo conjugation data provide a clear demonstration that DprA Bsu can stimulate recombination in a heterologous context. The biochemical experiments with short oligonucleotides are thoughtfully designed to isolate nucleation from filament extension. However, the central claim that "a single DNA binding site of the DprA dimer is required" is not directly tested. The experiments show that DprA Bsu stimulates RecA activity on short substrates, but no variant with a single functional DNA binding site is examined. The structural model is presented as supportive but is built from heterogeneous sources and lacks validation. The connection between the in vivo and in vitro data is suggestive but not definitive. The manuscript would benefit from direct mutagenesis of the DprA DNA binding site to test the single-site hypothesis, and from more rigorous presentation of the modelling methodology and validation.

- **Who would be interested in the results, and why** Researchers studying homologous recombination, particularly the mechanisms of mediator proteins such as DprA, RecA, and Rad51. The work also has relevance for those interested in horizontal gene transfer mechanisms, natural competence, and the evolution of recombination mediator function across bacterial species. The heterologous complementation data may interest those studying cross-species protein interactions.

- **Major strengths** The in vivo conjugation assay provides a physiologically relevant readout and demonstrates a striking 17-19 fold stimulation of recombination frequency. The use of short defined oligonucleotides to isolate nucleation from elongation is a sound experimental strategy. The combination of biochemical, in vivo, and modelling approaches is ambitious and potentially informative. The observation that DprA Bsu can function with E. coli RecA highlights evolutionary conservation of mediator function.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence mismatch
- **Claim pointer** The title and abstract state that "a single DNA binding site of DprA dimer is required to facilitate RecA filament nucleation."
- **Evidence pointer** Figures 2-3; Section 2.3-2.4
- **Concern** The central claim of the manuscript is that only one of the two DNA binding sites in the DprA dimer is required for RecA nucleation. However, no experiment directly tests this. The biochemical data show that DprA Bsu stimulates RecA or RecA Bsu ATPase/dATPase activity on short (dT) n substrates, but this does not distinguish between one or two functional DNA binding sites. No DprA variant with a mutated or deleted DNA binding site is presented. The structural model in Figure 4 is used to argue for steric feasibility, but modelling alone cannot establish functional requirement.
- **Why it matters** The title and abstract make a specific mechanistic claim that is not supported by the experimental evidence presented. If the claim is to be maintained, direct mutagenesis of the DprA DNA binding site(s) is required to show that a single-site variant retains full nucleation activity.
- **Resolution test** Provide experiments with DprA variants carrying mutations in one or both DNA binding sites, demonstrating that a single-site variant retains the ability to stimulate RecA nucleation on short ssDNA substrates, while a double-site variant does not.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of structural model
- **Claim pointer** Section 2.5 states that a "full-atomic model of the spatial structure of the RecA-ssDNA-DprA complex" was constructed and that the model "describes sterically possible form of the RecA–ssDNA-DprA complex capable to explain the experimental data."
- **Evidence pointer** Section 2.5; Figure 4; Section 4.5
- **Concern** The structural model is assembled from multiple sources: the RecA filament (PDB 3CMX), the DprA Hpy -ssDNA complex (PDB 4LJR), and a docking model of the RecA-DprA complex from a previous study. The bridging nucleotides were modelled by energy minimization. No validation metrics are provided, such as Ramachandran statistics, clash scores, or RMSD values for the superimpositions. The homology model of the E. coli DprA dimer is described but not validated. The model is used to support the central mechanistic claim, yet its quality and accuracy cannot be assessed from the provided information.
- **Why it matters** The structural model is a key pillar of the proposed mechanism. Without validation, the model cannot be considered reliable evidence for the steric feasibility of the proposed complex, nor for the conclusion that only one DNA binding site participates.
- **Resolution test** Provide validation statistics for the model, including Ramachandran analysis, clash scores, and superimposition RMSDs. Ideally, deposit coordinates or provide a detailed methods description that would allow reproduction. Alternatively, temper the claims made from the model and rely on experimental data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative data presentation
- **Claim pointer** Section 2.2 states that DprA Bsu "effectively stimulates RecA under analogous conditions and concentration ratios as observed in the referenced study" and that "the maximum rate of RecA-mediated ATP hydrolysis is achieved in the presence of 1 DprA Bsu monomer per 150-nt of DNA."
- **Evidence pointer** Figure 1; Section 2.2
- **Concern** The ATPase data are presented as steady-state rates, but no raw kinetic traces are shown. The lag phase is described qualitatively but not quantified. The stoichiometry of 1 DprA monomer per 150-nt is stated but the basis for this calculation is not clear. Replicate numbers are stated as "at least three" but no error bars or statistical analysis are visible in the figure descriptions.
- **Why it matters** The quantitative claims regarding stimulation magnitude and stoichiometry cannot be evaluated without proper data presentation. This limits the ability to assess the robustness of the biochemical conclusions.
- **Resolution test** Provide representative raw kinetic traces, show error bars and statistical tests for all reported rates, and clarify the calculation of the DprA-to-nucleotide stoichiometry.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** In vivo data interpretation
- **Claim pointer** Section 2.1 states that DprA Bsu expression leads to a 17-19 fold increase in FRE values, and that "DprA Bsu efficiently replaces DprA in E. coli cells."
- **Evidence pointer** Table 1; Section 2.1
- **Concern** The FRE measurements are presented as fold changes relative to empty vector, but the absolute FRE values, the number of biological replicates, and the statistical significance of the differences are not reported in the text. The statement that DprA Bsu "efficiently replaces" DprA is based on similar fold increases, but the comparison is indirect. The temperature dependence of the effect (37°C vs 30°C) is noted but not mechanistically explained.
- **Why it matters** The in vivo data are the only physiological evidence for DprA function in this context. Without proper statistical reporting and absolute values, the magnitude and reproducibility of the effect cannot be assessed.
- **Resolution test** Report absolute FRE values with standard deviations and statistical tests for all conditions. Clarify the number of independent experiments and the basis for the "efficiently replaces" conclusion.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Section 2.1, first paragraph
- **Evidence pointer** Section 2.1
- **Issue** The sentence "The DprA Bsu protein when expressed from a plasmid. By controlling the time of protein induction and temperature incubation, we demonstrate an almost twenty-fold increase in FRE." is grammatically incomplete and confusing.
- **Required correction** Rewrite for clarity, e.g., "When DprA Bsu was expressed from a plasmid, and by controlling the time of protein induction and temperature incubation, we observed an almost twenty-fold increase in FRE."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout
- **Evidence pointer** Section 2.4; Section 2.5
- **Issue** The manuscript alternates between "DprA Bsu " and "DprA" without consistent definition. The abbreviation "DprA Bsu " is defined in the introduction, but later sections sometimes use "DprA" alone, which could cause confusion.
- **Required correction** Use "DprA Bsu " consistently when referring to the B. subtilis protein, or define a clear convention at first use.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 4
- **Evidence pointer** Section 2.5
- **Issue** The figure description mentions a molecular model but does not specify what is shown in terms of colour coding, orientation, or key interactions. The reader cannot interpret the figure without additional annotation.
- **Required correction** Provide a detailed figure legend that explains the components, colour scheme, and key interactions depicted.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Section 1, Introduction
- **Evidence pointer** Section 1
- **Issue** The introduction mentions that DprA is present in non-competent species and suggests multifunctionality, but does not discuss any prior work on DprA function outside natural transformation beyond the cited references.
- **Required correction** Briefly summarize what is known about DprA functions beyond transformation to better frame the novelty of the current study.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Methods detail
- **Affected element** Section 4.4, Conjugation
- **Evidence pointer** Section 4.4
- **Issue** The conjugation method states that "The yield of thr + Str r and ara + Str r recombinants in all independent crosses (5–7% relative to donors) was normalized according to the mating ability of each recipient used." The normalization procedure is not fully described.
- **Required correction** Clarify how the normalization was performed and what the "mating ability" control entails.

- **Technical failings that need to be addressed before the case is established** R1-M1 (claim-evidence mismatch for the single DNA binding site conclusion) and R1-M2 (unvalidated structural model) are the primary technical issues. R1-M3 (quantitative data presentation) also needs to be addressed to allow proper evaluation of the biochemical results.

- **Assessment against Nature-style criteria** Originality: The question of how many DNA binding sites of DprA are required for RecA nucleation is a specific and relatively novel mechanistic question. However, the experimental approach does not directly test the stated hypothesis, limiting the originality of the conclusion. Scientific importance: The work has potential importance for understanding mediator protein function in homologous recombination, but the incomplete testing of the central claim reduces its impact. Interdisciplinary readership: The topic is primarily of interest to molecular biologists and biochemists studying recombination; the broader interdisciplinary appeal is limited. Technical soundness: The biochemical assays are reasonable in design, but the lack of direct mutagenesis and the unvalidated structural model are significant weaknesses. Readability for nonspecialists: The manuscript is generally readable but contains some unclear passages and would benefit from more careful editing.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript contains interesting observations, particularly the in vivo conjugation data and the demonstration that DprA Bsu can stimulate RecA activity on short substrates. However, the central claim regarding a single DNA binding site is not directly tested, and the structural model is not adequately validated. The authors should either provide direct experimental evidence for the single-site hypothesis or revise the title and conclusions to match what the data actually support.