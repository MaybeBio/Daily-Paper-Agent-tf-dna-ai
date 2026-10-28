## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary information descriptions
- **Assessment boundary** Scientific content, methodological rigor, validity of conclusions, and alignment with Nature-style criteria. No assessment of editorial fit or journal-specific policy.
- **Shared manuscript claim summary** The authors use molecular dynamics simulations, partial nudged elastic band path optimization, transition path sampling, and Markov state modeling to characterize the ATP-driven translocation mechanism of XPD and its bacterial homolog DinG on single-stranded DNA. They identify seven functional states for XPD and five for DinG, describe alternating binding affinities at two constrictions that enable directional translocation, and map disease-associated mutations onto key functional residues.
- **Visible evidence base** Abstract, full results section with figure descriptions, discussion, methods, and supplementary information listing. No actual figures, tables, or supplementary data files were provided for direct inspection.
- **Missing materials affecting confidence** All figures, supplementary figures, supplementary movies, source data, and the reporting summary. The manuscript references specific PDB structures (6RO4, 6FWS, 6FWR) but these were not independently examined. No raw simulation trajectories or analysis scripts were available.

## Reviewer

- **Overall assessment** This manuscript presents a computationally intensive and potentially valuable analysis of the translocation mechanism of XPD, a clinically important helicase. The authors employ a sophisticated combination of enhanced sampling methods and Markov state modeling to propose a detailed mechanistic model involving seven metastable states and two constrictions with alternating affinities. The connection between disease mutations and functionally critical residues is a compelling and clinically relevant aspect. However, the manuscript as presented has several significant limitations. The reliance on homology modeling for the ATP- and ADP-bound states of human XPD, the absence of direct experimental validation, and the lack of accessible figures and quantitative validation metrics for the Markov state models substantially weaken the current claims. The comparative analysis with DinG is interesting but the functional significance of the differences is not fully explored. The disease mutation analysis, while suggestive, is largely correlative and would benefit from a more systematic statistical framework. Overall, the work has the potential to be an important contribution, but the current evidence base is insufficient to fully establish the proposed mechanism.

- **Who would be interested in the results, and why** Structural biologists and computational biochemists studying helicase mechanisms and ATP-driven conformational changes would be the primary audience. Researchers in the DNA repair field, particularly those focused on nucleotide excision repair and the functional consequences of XPD mutations, would find the disease mutation mapping of significant interest. The comparative analysis with DinG may also appeal to evolutionary biologists studying mechanistically related helicases. The work could inform future experimental studies on XPD function and potentially guide interpretation of disease-associated variants.

- **Major strengths**
  1. The methodological approach is sophisticated and appropriate for the question. The combination of PNEB path optimization, transition path sampling, and Markov state modeling is a state-of-the-art approach for studying conformational transitions in large biomolecular systems.
  2. The identification of seven distinct functional states along the translocation pathway provides a more detailed mechanistic picture than previously available, extending the simpler two-step model proposed for DinG.
  3. The concept of two constrictions with alternating binding affinities is a clear and testable mechanistic hypothesis that provides a structural basis for the 5'-3' polarity of XPD.
  4. The mapping of disease-associated mutations onto functionally critical residues is clinically relevant and provides potential targets for future functional studies.
  5. The comparative analysis between XPD and DinG is valuable for understanding both conserved and divergent features of SF2 helicase translocation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim to have identified seven functional states (S1-S7) for XPD and five (SD1-SD5) for DinG using Markov state modeling, with corresponding kinetic rates estimated from mean first passage times.
- **Evidence pointer** Results section, Figure 2, Supplementary Figures 22 and 23
- **Concern** The manuscript states that Markov state models were built with 1500 microstates and 10 macrostates, with seven on-path states for XPD. However, no quantitative validation metrics are presented in the main text. The implied timescale analysis and model validation are relegated to supplementary figures that were not available for review. The choice of lag time (1500 ps) and the statistical uncertainty in the estimated transition rates are not discussed. Without these validation details, it is difficult to assess whether the identified states are statistically robust or artifacts of the clustering and projection methods.
- **Why it matters** The central claims of the paper rest on the reliability of the MSM and the identified metastable states. If the model is not properly validated or the states are not statistically well-separated, the entire mechanistic model could be called into question. The estimated kinetic rates are used to support the biological relevance of the mechanism, so their accuracy is critical.
- **Resolution test** Provide the implied timescale plot, the Chapman-Kolmogorov test results, and the statistical uncertainties (e.g., via Bayesian MSM or bootstrapping) for the transition rates. Show that the seven states are robust to changes in the number of microstates, the lag time, and the feature set used for TICA. Ideally, demonstrate that the states are kinetically distinct with clear separation of timescales.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors constructed models of human XPD in ATP- and ADP-bound states by homology modeling based on the E. coli DinG structure (PDB 6FWS), since no human XPD structures in these states are available.
- **Evidence pointer** Methods section, Model building
- **Concern** The manuscript does not provide sufficient detail on how the homology models were constructed, validated, or equilibrated. The sequence identity between human XPD and E. coli DinG is not stated, and no RMSD or structural quality metrics are provided. The functional conclusions depend critically on the accuracy of these models, particularly the ATP-bound conformation which drives the translocation mechanism. The authors also do not discuss potential limitations of using a bacterial homolog to model the human protein, given the known structural differences in the Fe-S and Arch domains that they themselves describe.
- **Why it matters** If the homology models are inaccurate, particularly in the positioning of key residues involved in ATP binding or DNA interactions, the entire mechanistic model could be misleading. The authors acknowledge structural differences between XPD and DinG in the Fe-S and Arch domains, yet they use DinG as the template for the nucleotide-bound states of XPD. This could introduce errors in the very regions that are central to their proposed mechanism.
- **Resolution test** Provide sequence identity/similarity between XPD and DinG, structural validation metrics (e.g., Ramachandran statistics, MolProbity scores), and a detailed description of the modeling protocol. Ideally, validate the homology models against any available biochemical or crosslinking data. Discuss how the known structural differences between XPD and DinG might affect the conclusions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that DNA- or ATP-binding residues directly involved in translocation are hotspots for genetic disease mutations, and that this provides insight into the etiology of XPD-associated genetic syndromes.
- **Evidence pointer** Results section, Disease mutations section, Figure 8
- **Concern** The analysis of disease mutations appears to be largely descriptive and correlative. The authors categorize mutations into three classes (A, B, C) based on their location relative to functional sites, but no statistical analysis is presented to demonstrate that disease mutations are significantly enriched at these positions compared to benign polymorphisms. The manuscript does not discuss whether the proposed mechanistic impact of each mutation class is supported by existing experimental data on specific mutants. The connection between the structural analysis and clinical phenotypes is suggestive but not rigorously established.
- **Why it matters** The claim that the findings shed light on disease etiology is a significant part of the paper's broader impact. If the mutation analysis is not statistically robust or does not integrate with existing functional data, this claim is overstated. A more rigorous analysis would strengthen the clinical relevance of the work.
- **Resolution test** Perform a statistical enrichment analysis of disease mutations versus benign variants at functional sites. For representative mutations in each class, compare the predicted mechanistic impact with published experimental data on mutant XPD activity, ATPase function, or DNA binding. If such data are limited, explicitly acknowledge this limitation and frame the predictions as hypotheses for future testing.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors report estimated translocation timescales of approximately 4 ms per nucleotide for XPD and 9 ms for DinG, and state these are underestimated by about an order of magnitude relative to experiments.
- **Evidence pointer** Discussion section
- **Concern** The comparison between computed and experimental timescales is presented in a single paragraph without a detailed discussion of the assumptions and uncertainties involved. The experimental values cited are from single-molecule experiments on human XPD, but the simulations are on the human protein while the DinG comparison is unclear. The manuscript does not discuss whether the computed rates are expected to be directly comparable to the experimental measurements, given differences in conditions, the presence of other proteins in the experimental system, and the approximations inherent in the computational approach.
- **Why it matters** The agreement with experimental timescales is used to validate the computational model. If the comparison is not rigorous, this validation is weakened. A more careful discussion of the uncertainties and assumptions would strengthen the credibility of the rate estimates.
- **Resolution test** Provide a more detailed comparison of the computational and experimental systems, including a discussion of the assumptions made in estimating rates from the MSM. If possible, compute rates under conditions that more closely match the experimental setup. Acknowledge the limitations of the comparison and avoid overstating the level of agreement.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction, Results
- **Evidence pointer** Introduction, Results section
- **Issue** The manuscript assumes significant familiarity with helicase mechanisms and enhanced sampling methods. Terms such as "PNEB," "TICA," and "Markov state modeling" are used without brief explanations for readers who may not be computational specialists. The biological significance of the two-constriction mechanism could be explained more clearly in the context of known helicase mechanisms.
- **Required correction** Add brief explanations of key computational methods when first introduced. Consider adding a schematic figure or a more accessible description of the proposed translocation mechanism in the introduction or early results.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, MD simulations
- **Evidence pointer** Methods section, Molecular dynamics simulations
- **Issue** The methods state that simulations were performed on the Summit supercomputer but do not provide details on the number of replicas, total simulation time, or the specific system sizes. The equilibration protocol is described but the production run lengths are not stated. This makes it difficult to assess the statistical sampling quality.
- **Required correction** Provide the total simulation time per system, the number of independent simulations, and the system size (number of atoms). State the total aggregate sampling across all replicas and systems.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the relationship between the proposed mechanism and the broader SF2 helicase family is brief. The authors note that the mechanism may be general but do not discuss how their findings might apply to other SF2 helicases with different functions or polarities.
- **Required correction** Expand the discussion to consider the generality of the proposed mechanism across the SF2 family, referencing specific examples of other helicases and how their features might support or contradict the proposed model.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Results, Disease mutations
- **Evidence pointer** Results section, Disease mutations section
- **Issue** The classification of mutations into classes A, B, and C is clear, but the clinical relevance of each class could be more explicitly stated. The text mentions phenotypes but does not clearly link specific mutation classes to specific clinical outcomes.
- **Required correction** Add a brief summary statement linking each mutation class to the associated clinical phenotypes and the proposed mechanistic basis for the phenotype.

- **Technical failings that need to be addressed before the case is established**
  R1-M1 (MSM validation), R1-M2 (homology model quality). These are the primary technical issues that must be resolved before the proposed mechanism can be considered established.

- **Assessment against Nature-style criteria**
  - **Originality**: The work is original in its application of advanced computational methods to the specific question of XPD translocation. The identification of seven states and the two-constriction model extends previous work. However, the conceptual framework of alternating affinities in helicase translocation is not entirely new, having been proposed for other helicase families. The originality lies in the specific application to XPD and the level of detail provided.
  - **Scientific importance**: The work addresses a fundamental question in DNA repair biology with direct clinical relevance. Understanding XPD translocation is important for understanding NER and the molecular basis of XP, TTD, and CS. The potential to link specific mutations to mechanistic defects is of high importance. However, the current evidence is largely computational and would be significantly strengthened by experimental validation.
  - **Interdisciplinary readership**: The work bridges structural biology, computational biophysics, and clinical genetics. The disease mutation analysis broadens the appeal beyond a purely biophysical audience. However, the heavy reliance on specialized computational methods may limit accessibility to readers without a computational background.
  - **Technical soundness**: The methodological approach is appropriate and sophisticated, but the lack of detailed validation for the MSM and homology models is a significant concern. The manuscript does not provide sufficient evidence to fully assess the reliability of the proposed states and rates.
  - **Readability for nonspecialists**: The manuscript is generally well-written but assumes significant background knowledge. The abstract is accessible, but the results section would be challenging for non-specialists. The clinical relevance is clear, but the mechanistic details may be difficult to follow.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a potentially important computational analysis of XPD translocation with clinical relevance. However, the lack of detailed validation for the Markov state models and homology models prevents full confidence in the proposed mechanism. If the authors can provide robust validation metrics and address the concerns raised, the work could be a valuable contribution. The current evidence base is not sufficient to fully establish the proposed mechanism without these additional analyses.