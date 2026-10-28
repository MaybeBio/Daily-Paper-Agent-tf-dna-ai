## Review setup
- **Input scope** Full manuscript text (abstract, significance statement, results, discussion, materials and methods) without figures, tables, or supplementary information
- **Assessment boundary** Scientific claims, experimental logic, and internal consistency based solely on the provided text; figures, tables, and SI Appendix referenced but not directly assessable
- **Shared manuscript claim summary** The authors propose that in teleosts, the oxygen sensor FIH activates NF-κB signaling by competitively displacing p65 from IκBα through a hydroxylation-independent mechanism, mediated by a teleost-specific interaction interface involving the FIH Lys305 residue and IκBα Glu284 residue, and that this mechanism is absent in mammals due to C-terminal structural differences in IκBα
- **Visible evidence base** Transcriptomic data (referenced), luciferase reporter assays, co-immunoprecipitation, immunofluorescence, AlphaFold3 structural predictions, domain-swap and point-mutant experiments, CRISPR/Cas9 zebrafish knockout, larval LPS and adult Vibrio challenge models, RT-qPCR, histology, immunohistochemistry
- **Missing materials affecting confidence** All figures, SI Appendix figures and tables, raw data, statistical details, plasmid maps, antibody validation data, and the deposited GEO dataset (GSE319394) are not available for direct verification

## Reviewer
- **Overall assessment** This manuscript presents a potentially interesting and novel mechanism linking oxygen sensing to innate immune regulation in teleosts, with evolutionary implications. The core claim, that FIH activates NF-κB via competitive IκBα binding rather than hydroxylation, is supported by a reasonable combination of biochemical, cellular, and in vivo experiments. However, the evidence as presented in the text has several gaps that prevent full confidence in the conclusions. The structural modeling is used heavily to support the mechanism but is not experimentally validated at the structural level. The in vivo data, while suggestive, rely on a single knockout line and specific infection doses. The evolutionary argument, while intriguing, is based on computational predictions across species without experimental validation in non-teleost aquatic species. The manuscript would benefit from clearer presentation of quantitative data and statistical rigor, which cannot be assessed from the text alone.

- **Who would be interested in the results, and why** Researchers in comparative immunology, fish biology, and aquaculture health would find this directly relevant. The work also speaks to the broader field of oxygen sensing and innate immunity, potentially interesting to those studying hypoxia-immune crosstalk in other contexts. The evolutionary angle on lineage-specific immune regulation may attract readers interested in adaptive evolution and host-pathogen interactions under environmental stress.

- **Major strengths** The study addresses a clear gap in understanding how FIH, a well-known oxygen sensor, regulates NF-κB in a lineage-specific manner. The combination of transcriptomics, biochemistry, structural prediction, and in vivo knockout models provides a multi-level approach. The identification of a specific residue (Lys305) and the competitive binding model are mechanistically concrete and testable. The evolutionary comparison between teleosts and mammals is a valuable conceptual contribution.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency for the competitive binding mechanism
  - **Claim pointer** The authors claim that FIH activates NF-κB by competitively displacing p65 from IκBα, mediated by FIH Lys305 competing with p65 Arg247 for IκBα Glu284
  - **Evidence pointer** Results section "FIH Activates NF-κB by Competing With P65 for IκBα Binding Under Hypoxia"; Figures 2D-2U; SI Appendix Figures S4G-S4N
  - **Concern** The competitive binding model rests on co-immunoprecipitation experiments and AlphaFold3 predictions. The text states that reduced FIH levels increase IκBα-p65 binding and that the K305A mutant loses this effect, but the actual binding affinities, stoichiometry, and kinetics are not reported. The structural prediction of a ternary complex with the K305A mutant is mentioned but not experimentally validated (e.g., by size-exclusion chromatography, surface plasmon resonance, or isothermal titration calorimetry). The claim that FIH "competes" with p65 implies a direct, measurable displacement, which is not demonstrated quantitatively.
  - **Why it matters** The central mechanistic claim of the paper depends on demonstrating that FIH directly and competitively displaces p65 from IκBα. Without quantitative binding data or a structural validation, the proposed mechanism remains a plausible but unproven model. The distinction between competition and allosteric modulation or simple steric interference is important for the mechanistic interpretation.
  - **Resolution test** Provide quantitative binding data (e.g., ITC, SPR, or fluorescence polarization) showing that FIH and p65 compete for IκBα with measurable affinities, and that the K305A mutation reduces FIH binding to IκBα. Alternatively, provide a high-resolution structure (X-ray, cryo-EM, or NMR) of the FIH-IκBα complex showing the predicted interface.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** In vivo evidence for the proposed mechanism
  - **Claim pointer** The authors claim that FIH deficiency inhibits the inflammatory response and antibacterial immunity in vivo, and that this is due to the competitive mechanism
  - **Evidence pointer** Results section "FIH Deficiency Inhibits the Inflammatory Response and Antibacterial Immunity In Vivo"; Figures 3A-3K; Figure 4A-4E
  - **Concern** The in vivo experiments use a single drfih knockout zebrafish line. The text reports survival differences and inflammatory gene expression changes, but the specificity of the phenotype to the proposed mechanism is not established. The authors do not show that the K305A mutation or the competitive binding is responsible for the in vivo phenotype. The LPS and Vibrio challenge models are described, but the doses, time points, and statistical power are not reported in the text. The claim that FIH deficiency "suppresses hypoxia-induced activation of NF-κB in vivo" is based on immunohistochemistry and RT-qPCR, but the quantitative data and statistical analysis are not presented.
  - **Why it matters** The in vivo data are essential to demonstrate physiological relevance. Without a rescue experiment (e.g., expressing wild-type FIH vs. K305A mutant in the knockout background) or a direct demonstration that the competitive mechanism operates in vivo, the phenotype could be due to other FIH functions, developmental defects, or off-target effects of the CRISPR knockout.
  - **Resolution test** Provide a rescue experiment in drfih-/- zebrafish with wild-type FIH and the K305A mutant to show that the inflammatory phenotype is specifically due to the competitive mechanism. Include quantitative data with appropriate statistical tests for all in vivo measurements.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Evolutionary claims
  - **Claim pointer** The authors claim that the competitive mechanism is teleost-specific and lost in terrestrial vertebrates due to C-terminal structural differences in IκBα
  - **Evidence pointer** Results section "Evolutionary Changes in IκBα May Underlie the Loss of Mammalian FIH Competitive Inhibition"; Figures 5A-5L, 6A-6B
  - **Concern** The evolutionary argument is based on structural predictions across species and a single chimeric experiment in HEK293T cells. The authors show that human FIH does not affect NF-κB in HEK293T cells, and that a chimeric IκBα (human with teleost C-terminus) partially restores the effect. However, the phylogenetic analysis and cross-species structural predictions are computational and not experimentally validated. The claim that the mechanism is "teleost-specific" is not supported by functional experiments in other aquatic species (e.g., amphibians, crustaceans) that are predicted to have the interface.
  - **Why it matters** The evolutionary narrative is a major selling point of the paper. If the mechanism is present in other aquatic species, the claim of teleost-specificity is overstated. If it is truly teleost-specific, the authors should provide more evidence for the evolutionary transition, such as ancestral sequence reconstruction or functional assays in a broader range of species.
  - **Resolution test** Perform functional assays (e.g., FIH overexpression and NF-κB reporter assays) in at least one non-teleost aquatic species predicted to have the interface (e.g., Xenopus or a crustacean cell line) and one additional terrestrial species to strengthen the evolutionary claim. Alternatively, soften the claim to "aquatic-specific" if the data do not support teleost exclusivity.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Mechanistic independence from hydroxylation
  - **Claim pointer** The authors claim that FIH activates NF-κB independently of its hydroxylase activity, based on the D202A mutant
  - **Evidence pointer** Results section "FIH Employs an Identical Competitive Mechanism to Activate NF-κB Under Normoxia"; SI Appendix Figure S4Q-S4S
  - **Concern** The D202A mutant is used to show hydroxylase independence, but the text does not report whether this mutant retains any residual hydroxylase activity or whether it affects FIH protein stability, folding, or subcellular localization. The authors also do not test whether the competitive binding is affected by the presence of oxygen or 2-oxoglutarate, which are co-substrates for FIH hydroxylase activity. The claim of hydroxylase independence would be strengthened by showing that the competitive binding occurs even under conditions where hydroxylation is impossible (e.g., in the presence of a hydroxylase inhibitor or under anoxic conditions).
  - **Why it matters** The novelty of the mechanism depends on it being distinct from FIH's canonical hydroxylase function. If the D202A mutant is misfolded or mislocalized, the results could be misleading. Demonstrating that the competitive binding is truly independent of hydroxylase activity is critical for the conceptual advance.
  - **Resolution test** Characterize the D202A mutant for protein stability, folding, and localization. Test the competitive binding in vitro with purified proteins in the presence and absence of co-substrates (oxygen, 2-oxoglutarate, iron) to show that binding is not affected by hydroxylation conditions.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** All quantitative experiments
  - **Evidence pointer** Throughout Results; figure legends not provided
  - **Issue** The text reports differences between groups (e.g., "significantly increased", "robustly activated") without providing effect sizes, confidence intervals, or exact p-values. The number of biological and technical replicates is not stated.
  - **Required correction** Provide full statistical details in figure legends or methods, including exact p-values, effect sizes, and replicate numbers.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Transcriptomic data presentation
  - **Affected element** Figure 1A and SI Appendix Figures S1A-S1C
  - **Evidence pointer** Results section "FIH Positively Regulates NF-κB Under Hypoxia"
  - **Issue** The transcriptomic analysis is mentioned but the differential expression criteria, number of replicates, and the full list of differentially expressed genes are not described in the text. The KEGG enrichment analysis is mentioned but the specific enriched pathways are not listed.
  - **Required correction** Provide the differential expression thresholds, replicate numbers, and a summary of the key enriched pathways in the main text or SI.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Structural model quality
  - **Affected element** AlphaFold3 predictions (Figures 2J, 2P-2Q, 5G-5H, 5K)
  - **Evidence pointer** Results sections on structural predictions
  - **Issue** The text does not report confidence metrics (e.g., pLHDT scores, predicted aligned error) for the AlphaFold3 models beyond a general statement about excluding low-confidence regions. The authors do not discuss the limitations of AlphaFold3 for predicting protein-protein interaction interfaces.
  - **Required correction** Report the relevant confidence metrics for the key predictions and discuss the limitations of the computational approach.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Antibody validation
  - **Affected element** Co-IP and immunofluorescence experiments
  - **Evidence pointer** Materials and Methods; Figures 2D-2U, 5A, 5F, 5L
  - **Issue** The text does not specify whether antibodies used for endogenous protein detection (e.g., drp65 in zebrafish) were validated for specificity, particularly in the context of the knockout line.
  - **Required correction** Provide antibody validation data (e.g., knockout or knockdown controls) in the SI.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Normoxia vs. hypoxia distinction
  - **Affected element** Results sections on normoxia and hypoxia
  - **Evidence pointer** Figures 1F-1M, SI Appendix Figures S4A-S4P
  - **Issue** The text presents normoxia and hypoxia experiments separately but does not directly compare the magnitude of the FIH effect under both conditions. The claim that the mechanism operates "under both hypoxia and normoxia" would benefit from a direct statistical comparison.
  - **Required correction** Add a direct comparison of FIH effects on NF-κB activity under normoxia vs. hypoxia, with appropriate statistics.

  - **Concern ID** R1-m6
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Title and abstract
  - **Evidence pointer** Title; Abstract
  - **Issue** The term "oxygen-immunity axis" is used in the title and significance statement but is not formally defined or contextualized in the text. The relationship between this axis and previously described oxygen-sensing pathways could be clarified.
  - **Required correction** Define the term and place it in the context of existing literature on oxygen sensing and immunity.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Quantitative binding data for the competitive mechanism are missing
  - R1-M2: In vivo rescue experiments are lacking
  - R1-M3: Evolutionary claims are based on computational predictions without functional validation in non-teleost species
  - R1-M4: Hydroxylase independence is not rigorously established

## Risk / unsupported claims
- The claim that FIH "competitively displaces" p65 from IκBα is not quantitatively supported; the data show correlation but not direct competition
- The claim that the mechanism is "teleost-specific" is not supported by functional data across species; only computational predictions are provided
- The claim that FIH activates NF-κB "independently of hydroxylase activity" is based on a single point mutant without characterization of the mutant's structural or functional integrity
- The in vivo phenotype in drfih-/- zebrafish is not causally linked to the proposed competitive mechanism
- The statement that "not all of these predicted regions were associated with the C terminus of IκBα" in aquatic species is vague and not supported by specific data in the text
- The claim that FIH "stabilizes" IκBα is based on cycloheximide experiments that are only described in the SI and not quantified in the main text

## Assessment against Nature-style criteria
- **Originality** The proposed mechanism, in which FIH activates NF-κB via competitive IκBα binding rather than hydroxylation, is conceptually novel and distinct from previously described FIH functions. The evolutionary angle is also original. However, the originality is somewhat tempered by the fact that FIH-IκBα interactions have been previously reported, and the novelty lies in the functional consequence and lineage specificity.
- **Scientific importance** The work has potential importance for understanding how aquatic animals adapt to hypoxic environments and maintain immune function. It could have implications for aquaculture and for understanding climate-driven hypoxia effects on fish health. The broader relevance to mammalian biology is limited, as the mechanism appears to be absent in mammals.
- **Interdisciplinary readership** The work bridges comparative immunology, oxygen sensing, and evolutionary biology. It would appeal to researchers in fish biology, immunology, and evolutionary physiology. The broader cell biology and biochemistry communities may find the mechanistic aspects interesting, but the teleost-specific focus may limit the breadth of appeal.
- **Technical soundness** The experimental design is generally reasonable, with appropriate use of multiple approaches (biochemistry, cell biology, in vivo models, structural prediction). However, the lack of quantitative binding data, the absence of rescue experiments, and the reliance on computational predictions for key claims reduce the technical rigor. The statistical reporting is insufficient for full assessment.
- **Readability for nonspecialists** The manuscript is generally well-written and the logic is clear. The significance statement is accessible. However, the heavy reliance on structural modeling terminology and the density of experimental details may make it challenging for nonspecialists to fully appreciate the strength of the evidence. The figures, which are not available for review, would be critical for readability.

## Recommendation posture
Supportive if technical concerns are resolved. The core idea is interesting and potentially significant for the field of comparative immunology. However, the current evidence does not fully establish the competitive binding mechanism, the in vivo relevance, or the evolutionary claims. The authors should be encouraged to provide quantitative binding data, rescue experiments, and functional validation in at least one non-teleost species before the case is fully established.