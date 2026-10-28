## Review setup
- **Input scope** Full manuscript text including abstract, introduction, materials and methods, results, discussion, data availability, and supplementary figure legends
- **Assessment boundary** Scientific validity of claims, experimental design, data interpretation, and consistency between results and conclusions
- **Shared manuscript claim summary** The authors report that RecG binds directly and specifically to the carboxy-terminal tip (SSB-Ct) of E. coli SSB through a conserved pocket in the RecG HD2 domain, that this interaction is important for RecG function in vivo, and that the SSB intrinsically disordered linker (IDL) PxxP motifs are not required for RecG binding or major SSB cellular functions.
- **Visible evidence base** Fluorescence anisotropy binding assays with SSB peptides; isothermal titration calorimetry with full-length SSB and SSB-Ct peptide; AlphaFold-Multimer structural predictions; yeast two-hybrid interaction assays; ATPase activity assays; in vivo phenotyping including UV sensitivity, SOS induction, microscopy, and competition assays; western blotting; whole-genome sequencing
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; raw binding isotherms and ITC thermograms not shown in main text; AlphaFold model confidence metrics not fully described; statistical details for some comparisons not fully specified

## Reviewer

### **Overall assessment**
This manuscript addresses a significant question in bacterial genome maintenance: whether RecG interacts with SSB through the canonical SSB-Ct binding mode or through a proposed alternative mode involving PxxP motifs in the SSB IDL. The authors use a combination of in vitro biophysical assays, structural prediction, and in vivo genetics to provide compelling evidence that RecG is a canonical SSB-Ct-binding protein. The work directly challenges previously published claims about RecG-IDL interactions and provides a clear resolution to this controversy. The experimental approach is generally rigorous, with complementary methods supporting the central conclusions. The in vivo studies demonstrating that SSB IDL deletions are well tolerated in E. coli are valuable and extend the significance beyond the RecG-specific question. However, some concerns regarding quantitative interpretation of binding data, the strength of in vivo phenotypic evidence, and the generalizability of the IDL deletion conclusions warrant attention.

### **Who would be interested in the results, and why**
Researchers studying bacterial DNA replication, recombination, and repair will find this work directly relevant. The SSB interaction network is a central organizing principle in bacterial genome maintenance, and understanding how SSB recruits and regulates partner proteins is of broad interest. The study also has implications for those studying protein-protein interactions involving intrinsically disordered regions, as it provides a counterexample to the proposed PxxP-mediated interaction model. Additionally, the demonstration that large IDL deletions are tolerated in E. coli will interest researchers studying SSB structure-function relationships and those using SSB as a model for understanding disordered protein regions. The methodological approach combining biophysics, structural prediction, and genetics provides a template for similar studies of other SSB-interacting proteins.

### **Major strengths**
1. The study directly addresses a controversy in the field with rigorous biochemical approaches using purified components, avoiding potential artifacts of overexpression-based co-purification methods used in prior studies.
2. The combination of fluorescence anisotropy and ITC provides complementary thermodynamic and stoichiometric information, strengthening the conclusion that SSB-Ct is both necessary and sufficient for RecG binding.
3. The use of AlphaFold-Multimer predictions to guide mutagenesis, followed by experimental validation, represents a modern and effective approach to identifying protein interaction interfaces.
4. The in vivo studies using chromosomally encoded mutants avoid overexpression artifacts and provide physiologically relevant assessment of mutant phenotypes.
5. The demonstration that SSB IDL deletions are tolerated in E. coli, including competition assays, provides important new information about SSB structure-function relationships.
6. The authors thoughtfully address potential confounding factors, including checking for gene duplication events and suppressor mutations.

### **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative analysis of binding data
- **Claim pointer** The authors report a KD of 3.1 ± 0.4 μM for RecG binding to the SSB-Ct peptide and similar affinity for full-length SSB, concluding that SSB-Ct comprises the complete binding site for RecG.
- **Evidence pointer** Results section "RecG binds directly and specifically to the SSB-Ct", Figure 2, Table 1
- **Concern** The fluorescence anisotropy binding data are fit to a one-site binding model, but the manuscript does not provide sufficient detail on the quality of the fits, the concentration ranges tested, or whether the peptide concentration (10 nM) is sufficiently below the KD to allow accurate determination. For the ITC experiments, the reported stoichiometry of 0.92 ± 0.08 for the SSB-Ct peptide and 1.05 ± 0.07 for full-length SSB is close to 1.0, but the manuscript does not report the confidence intervals for the KD values from ITC or discuss potential systematic errors. Additionally, the claim that full-length SSB and SSB-Ct peptide binding are thermodynamically indistinguishable relies on comparison of ΔH° and TΔS° values, but the error analysis for these parameters is not presented in sufficient detail to support the claim of "remarkably similar" values.
- **Why it matters** The central conclusion that SSB-Ct is sufficient for RecG binding depends on quantitative comparison of binding affinities and thermodynamics between full-length SSB and the SSB-Ct peptide. If the binding parameters are not determined with sufficient precision, the conclusion that other SSB regions do not contribute to binding could be overstated.
- **Resolution test** Provide full binding curves with fit residuals, report the concentration ranges tested and the fraction of peptide bound at saturation, include confidence intervals for all thermodynamic parameters from ITC, and perform a statistical comparison (e.g., extra sum-of-squares F test) to demonstrate that the one-site model is appropriate and that full-length SSB and SSB-Ct peptide binding parameters are not significantly different.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Structural prediction validation
- **Claim pointer** The authors state that AlphaFold-Multimer predictions identified a SSB-Ct binding pocket on the RecG HD2 domain framed by Arg474, Arg467, and Arg614, and that this pocket is evolutionarily conserved.
- **Evidence pointer** Results section "Identification of the SSB-binding pocket on the HD2 domain of RecG", Figure 3
- **Concern** The manuscript describes that "in each of the five highest-confidence models, the SSB-Ct motif of SSB docked against the same surface-exposed pocket in the HD2 domain of RecG" but does not provide quantitative metrics for model confidence (e.g., pLDDT scores, predicted aligned error, or ranking scores). The conservation analysis is described as showing these residues are "highly conserved among RecG proteins," but the specific conservation scores or the number of sequences analyzed are not presented. Without these details, it is difficult to assess the robustness of the structural predictions and the strength of the conservation claim.
- **Why it matters** The structural model guides the mutagenesis strategy and provides the mechanistic framework for interpreting the functional data. If the model confidence is low or the conservation analysis is based on limited sequence sampling, the interpretation of the mutagenesis results could be affected.
- **Resolution test** Provide the AlphaFold-Multimer confidence metrics (pLDDT, PAE) for the predicted complex, show the predicted alignment of the SSB-Ct peptide in the RecG pocket, and present the conservation analysis with the number of sequences analyzed and the scoring method used.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** In vivo phenotypic interpretation
- **Claim pointer** The authors conclude that "formation of the RecG/SSB complex is important in vivo" based on UV sensitivity and SOS induction in strains expressing RecG SSB-binding pocket mutants.
- **Evidence pointer** Results section "Interaction with SSB is critical for RecG function in vivo", Figure 5
- **Concern** The UV sensitivity phenotypes for the recG point mutants appear to be intermediate between wild-type and ΔrecG, and the SOS induction data show variability between mutants. The manuscript does not clearly demonstrate that the observed phenotypes are specifically due to loss of SSB binding rather than to other effects of the mutations on RecG function. While the ATPase data for RecG R474E support proper folding, this is only shown for one mutant. The authors do not present data on whether the RecG mutants retain DNA binding, helicase, or translocase activities, which would help exclude the possibility that the phenotypes result from defects unrelated to SSB interaction.
- **Why it matters** The claim that SSB interaction is critical for RecG function in vivo requires that the observed phenotypes be specifically attributable to loss of SSB binding. If the mutations also affect other RecG activities, the interpretation would be confounded.
- **Resolution test** Assess additional RecG activities (DNA binding, helicase, translocase) for the SSB-binding pocket mutants, or complement the mutant strains with a RecG variant that restores SSB binding to demonstrate phenotypic rescue. Alternatively, provide epistasis analysis showing that the recG mutant phenotypes are suppressed by mutations that bypass the need for SSB interaction.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalization of IDL deletion conclusions
- **Claim pointer** The authors conclude that "the SSB PxxP motifs are not major contributors to SSB cellular functions" based on the normal growth and DNA repair phenotypes of SSB IDL deletion strains.
- **Evidence pointer** Results section "Cell expressing large chromosomally-encoded SSB IDL deletion variants are indistinguishable from wildtype E.coli", Figures 6-8
- **Concern** The study examines a limited set of phenotypes (growth rate, UV sensitivity, ciprofloxacin and mitomycin C sensitivity, SOS induction, competition fitness). While these are important phenotypes, the conclusion that PxxP motifs are not major contributors to SSB cellular functions is broad. The authors do not examine other conditions where SSB-IDL interactions might be important, such as replication restart, homologous recombination, or specific stress conditions. Additionally, the SSB IDL deletion strains show reduced SSB protein levels (approximately 2-3-fold lower for the largest deletion), which could confound interpretation of the phenotypic results.
- **Why it matters** The conclusion about PxxP motif dispensability extends beyond the specific conditions tested. If the IDL deletions affect SSB protein levels, the phenotypes (or lack thereof) may reflect altered SSB abundance rather than loss of specific protein-protein interactions.
- **Resolution test** Test additional conditions relevant to SSB function (e.g., replication restart assays, recombination assays, growth under various stress conditions). Address the reduced SSB levels by either normalizing for protein abundance or by expressing the IDL deletion variants from an inducible promoter to match wild-type levels.

### **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Experimental detail
- **Affected element** Fluorescence anisotropy assay description
- **Evidence pointer** Materials and Methods, "Fluorescence anisotropy" section
- **Issue** The manuscript states that experiments were performed in triplicate but does not specify whether these are technical or biological replicates, and does not describe how the KD values and errors were calculated from the triplicate data.
- **Required correction** Clarify the nature of replicates and describe the error propagation method used to determine the reported uncertainties in KD values.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** ITC data
- **Evidence pointer** Figure 2B-E, Supplementary Figure S2
- **Issue** The ITC thermograms and binding isotherms are presented in the main text, but the thermodynamic parameters (ΔH°, ΔS°, and their errors) are only reported in Table 1 without showing the fitted curves with residuals.
- **Required correction** Include representative ITC fits with residuals in the supplementary material to allow assessment of fit quality.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** UV sensitivity and SOS induction data
- **Evidence pointer** Figure 5
- **Issue** The manuscript does not clearly state the statistical tests used to compare UV sensitivity and SOS induction between strains, and the number of biological replicates is not specified for these experiments.
- **Required correction** Provide details of statistical analyses, including the tests used, the number of replicates, and the criteria for significance.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion of prior RecG-IDL interaction studies
- **Evidence pointer** Discussion section
- **Concern** The authors mention that prior studies proposed PxxP-mediated interactions but do not discuss in detail why those studies may have produced different results. A more thorough discussion of potential reasons for the discrepancy (e.g., overexpression artifacts, differences in assay conditions) would strengthen the manuscript.
- **Required correction** Expand the discussion of discrepancies with prior work, addressing potential methodological differences that could explain conflicting results.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 3
- **Evidence pointer** Figure 3
- **Issue** The AlphaFold model images in Figure 3 may be difficult to interpret without more detailed labeling of the residues and secondary structure elements.
- **Required correction** Add clearer labeling of the key residues (R467, R474, R614, R484) and consider showing a zoomed view of the predicted interaction interface.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Use of "canonical" vs "alternative" binding modes
- **Evidence pointer** Throughout
- **Issue** The manuscript uses the term "canonical" to describe SSB-Ct binding, which is appropriate given the literature, but the authors could more explicitly define what they mean by this term in the context of the SSB interaction network.
- **Required correction** Briefly define "canonical SSB-Ct binding" in the introduction to ensure clarity for readers unfamiliar with the SSB interaction literature.

### **Technical failings that need to be addressed before the case is established**
1. Quantitative details of binding assays (R1-M1) need to be provided to support the KD and thermodynamic comparisons.
2. AlphaFold model confidence metrics and conservation analysis details (R1-M2) should be presented to validate the structural predictions.
3. Additional characterization of RecG mutant activities (R1-M3) is needed to exclude off-target effects of the mutations.
4. Consideration of reduced SSB protein levels in IDL deletion strains (R1-M4) is required for proper interpretation of phenotypic data.

### **Assessment against Nature-style criteria**
- **Originality**: The work addresses a specific controversy in the SSB interaction field and provides a clear resolution. While the finding that RecG binds SSB-Ct is not entirely unexpected given the broader literature on SSB-interacting proteins, the direct demonstration against the proposed PxxP-mediated model is novel and important.
- **Scientific importance**: The SSB interaction network is central to bacterial genome maintenance, and understanding the molecular basis of SSB partner recognition has broad implications. The demonstration that the IDL PxxP motifs are dispensable for major SSB functions challenges current models and will influence future studies.
- **Interdisciplinary readership**: The work will primarily interest researchers in DNA replication, repair, and recombination, as well as those studying protein-protein interactions. The findings may also be relevant to those studying disordered protein regions, though the interdisciplinary reach is moderate.
- **Technical soundness**: The experimental approach is generally rigorous, with complementary in vitro and in vivo methods. However, the quantitative analysis of binding data and the characterization of mutant protein activities need strengthening to fully support the conclusions.
- **Readability for nonspecialists**: The manuscript is clearly written and the logic is easy to follow. The figures are generally well-designed, though some (particularly the AlphaFold models) could benefit from more detailed labeling. The abstract effectively summarizes the key findings.

### **Recommendation posture**
Supportive if technical concerns are resolved. The central claims are well-supported by the experimental data, and the study addresses an important question in the field. However, the quantitative analysis of binding data, validation of the structural model, and additional characterization of RecG mutant activities should be addressed to fully establish the case. The in vivo IDL deletion studies are valuable but would benefit from consideration of the reduced SSB protein levels in the mutant strains.

## Risk / unsupported claims
1. The claim that SSB-Ct is "sufficient" for RecG binding is supported by the observation that full-length SSB and SSB-Ct peptide show similar binding thermodynamics, but this conclusion depends on the precision of the thermodynamic comparison, which is not fully documented.
2. The claim that the RecG SSB-binding pocket is "evolutionarily conserved" is not fully supported by the data presented, as the conservation analysis details are not provided.
3. The conclusion that "the SSB PxxP motifs are not major contributors to SSB cellular functions" is broader than what the experimental data can support, given the limited set of conditions tested and the reduced SSB protein levels in the deletion strains.
4. The statement that prior co-purification results were potentially confounded by plasmid incompatibility is speculative and not directly tested in this study.
5. The claim that the IDL functions as a spacer between the OB domain and SSB-Ct is a reasonable interpretation of the data but is not directly tested.