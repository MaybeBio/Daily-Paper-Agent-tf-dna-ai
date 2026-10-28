## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, conclusions, methods) as provided
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and presentation quality as assessable from the provided text
- **Shared manuscript claim summary** The authors combine extended atomistic molecular dynamics simulations with supervised machine learning to identify structural determinants of binding specificity among four Wnt proteins (Wnt1, Wnt3a, Wnt5a, Wnt8a) and the Wls membrane protein. They develop a novel RMSD-based local structural alignment algorithm to map residues across divergent Wnt sequences, apply a two-stage hierarchical clustering strategy for feature reduction, and train a Random Forest classifier that distinguishes among the four Wnt-Wls systems. Feature importance analysis identifies both known and novel residue pairs, with the top-ranked features located near the palmitoleoylation site and conserved W-C-C motif.
- **Visible evidence base** Abstract; Sections 1-5 (Introduction, Results, Discussion, Conclusions, Methods); Figure references (Figures 1-5); Supplementary figure references (S1-S7); Table 1 reference; Supplementary Tables S1-S3 references
- **Missing materials affecting confidence** Figures and supplementary materials not provided; experimental validation data not included; detailed force field parameter derivation not fully described; sequence alignment details not shown; code repository not inspected

## Reviewer

- **Overall assessment** This manuscript presents a methodologically ambitious integration of long-timescale atomistic simulations with interpretable machine learning to address a biologically important question: how a single receptor (Wls) recognizes multiple divergent ligands (Wnts) with specificity. The development of an RMSD-based local structural alignment strategy to enable cross-system comparison is a genuine methodological contribution, and the application of autocorrelation-based data partitioning to prevent temporal leakage in MD-derived training data is thoughtful. However, the manuscript as presented has several significant limitations that temper enthusiasm. The reported test accuracy of 88.47% for the multiclass classifier, while respectable, is presented without confidence intervals or statistical comparison to baselines. The feature importance analysis yields modest scores, and the biological interpretation relies heavily on literature correlation rather than direct validation. The claim of novelty for the structural alignment approach requires clearer articulation against existing structural alignment methods. The writing is generally clear but contains some redundancy and occasional imprecise statements. The work is potentially publishable in a specialized computational biology journal, but the current evidence does not fully establish the central claims of biological insight and generalizability.

- **Who would be interested in the results, and why** Researchers studying Wnt signaling and Wls-mediated secretion would be interested in the specific residue-level insights into Wnt-Wls binding determinants. Computational biologists developing machine learning approaches for protein-protein interaction analysis from molecular dynamics data would find the methodological framework, particularly the structural alignment and temporal data partitioning strategies, of interest. The broader community working on interpretable ML for biomolecular simulations would also find value in the demonstration that relatively simple models like Random Forests can extract biologically meaningful features from complex simulation data.

- **Major strengths** The study addresses a biologically significant question with a technically sophisticated approach. The combination of extended atomistic simulations (1.5 μs per system) with rigorous ML methodology is commendable. The development of a structural alignment algorithm to overcome sequence divergence is a creative solution to a real problem in comparative analysis of homologous protein complexes. The autocorrelation-based data partitioning strategy to prevent temporal leakage is a methodologically important contribution that addresses a common pitfall in ML applications to time-series simulation data. The use of both multiclass and one-vs-rest classifiers provides complementary perspectives on feature importance. The identification of the W-C-C motif and PAM-adjacent residues as key determinants aligns with existing experimental literature, providing some biological validation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The Random Forest classifier achieved high predicting accuracy, with test accuracy of 88.47% on the held-out test set.
- **Evidence pointer** Section 2.3; Figure 5; location not provided
- **Concern** The reported accuracy of 88.47% is presented without any measure of uncertainty, such as confidence intervals or standard deviation across multiple runs. Given that the test set comprises early simulation frames (0 to τ) where structural variability is highest, it is unclear whether this accuracy is stable or highly dependent on the specific temporal partitioning. Furthermore, no comparison is provided against baseline models (e.g., majority class classifier, logistic regression, or a model trained on randomly permuted labels) to establish that the classifier is learning meaningful signal beyond trivial temporal correlations. The claim of "high predicting accuracy" is therefore not rigorously supported.
- **Why it matters** Without uncertainty quantification and baseline comparisons, the reader cannot assess whether the reported accuracy reflects genuine discriminative signal in the contact features or is an artifact of the specific data split, model initialization, or temporal autocorrelation. This is central to the manuscript's claim that ML can effectively distinguish among Wnt binding modes.
- **Resolution test** Provide accuracy with confidence intervals (e.g., bootstrap or repeated runs with different random seeds), compare against appropriate baseline models, and report precision, recall, and F1-score per class. Additionally, demonstrate that the temporal partitioning strategy does not introduce systematic bias by showing results across multiple τ values or alternative partitioning schemes.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The feature importance analysis reveals both previously known and novel key residue pairs responsible for distinguishing among the Wnt systems, with the most predictive being I185-L297, located adjacent to the PAM site.
- **Evidence pointer** Section 2.3; Figure 5; location not provided
- **Concern** The biological interpretation of the feature importance results relies on correlation with existing literature, but no direct validation is provided. The claim that I185 and its structural counterparts "may facilitate the structural recognition or binding of Wnt proteins to Wls" is speculative. The manuscript does not include any mutational analysis, binding free energy calculations, or experimental validation to test the predicted importance of these residues. Furthermore, the feature importance scores are described as "relatively small" (highest 0.0498), and the authors acknowledge that permutation importance may underestimate correlated features, yet they proceed to draw strong biological conclusions from these modest values.
- **Why it matters** The central biological claim of the manuscript is that specific residue pairs determine Wnt-Wls binding specificity. Without validation, the identified features remain computational predictions of unknown reliability. The modest importance scores raise questions about whether the model is truly capturing specificity determinants or merely weak statistical associations.
- **Resolution test** Provide additional computational validation, such as in silico mutagenesis, binding free energy calculations (e.g., MM-PBSA or alchemical methods), or comparison with known functional mutation data. Alternatively, clearly frame the identified residues as hypotheses requiring experimental testing, and temper the strength of the biological claims accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological novelty
- **Claim pointer** We developed a novel, RMSD-based local structural alignment algorithm to map residue pairs across all four Wnt-Wls complexes to a shared structural reference.
- **Evidence pointer** Section 2.2; Section 5.1; Figure 2; location not provided
- **Concern** The novelty of the structural alignment algorithm is not clearly established. The manuscript does not compare this approach to existing structural alignment methods (e.g., TM-align, CE, or local structural superposition methods) or demonstrate its advantages over sequence-based alignment followed by structural refinement. The description of the algorithm in the Methods section is insufficiently detailed to allow reproduction, and no validation of alignment quality is provided beyond the RMSD distribution shown in Figure 2B. The claim of novelty requires a clearer articulation of what distinguishes this method from existing approaches.
- **Why it matters** The methodological contribution is a key selling point of the manuscript. If the alignment approach is not genuinely novel or is not demonstrably superior to existing methods, the manuscript's contribution is substantially diminished. Reproducibility is also a concern given the incomplete algorithmic description.
- **Resolution test** Provide a more detailed algorithmic description, compare alignment results against established structural alignment methods on benchmark datasets, and demonstrate specific advantages of the approach (e.g., accuracy, speed, or ability to handle divergent sequences).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** We used an approach based on building the force field parameter files by leveraging existing ones for similar molecules and we were able to describe Wnt-Wls interactions and capture PAM's essential function.
- **Evidence pointer** Section 5.1; Supplementary Table S2; location not provided
- **Concern** The derivation of force field parameters for the palmitoleoylated serine (SERP) residue is described only briefly. The manuscript states that parameters were derived by analogy to existing molecules, but no validation of these parameters is provided. It is unclear whether the parameters were tested against quantum mechanical calculations, experimental data, or compared to alternative parameterization approaches. The accuracy of the SERP parameters directly affects the reliability of the simulation results, particularly for interactions involving the PAM site, which is a key finding of the study.
- **Why it matters** Force field parameter accuracy is critical for the validity of molecular dynamics simulations. If the SERP parameters are inaccurate, the simulation results, and consequently the ML findings, may be compromised. The manuscript's claim that the parameterization is "sufficient" for the study's goals requires more rigorous justification.
- **Resolution test** Provide validation of the SERP parameters, such as comparison with quantum mechanical reference data, reproduction of known experimental observables, or sensitivity analysis showing that results are robust to reasonable parameter variations.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Evidence sufficiency
- **Claim pointer** Our findings highlight that the binding specificity across different systems arises from the distributed nature of interactions across the protein binding surface.
- **Evidence pointer** Section 3; Figure 5; location not provided
- **Concern** The claim that binding specificity arises from distributed interactions is not quantitatively supported. The manuscript identifies individual top-ranked features but does not analyze the spatial distribution of important features across the binding interface, nor does it compare the importance distribution to what would be expected by chance. The statement appears to be a qualitative interpretation rather than a demonstrated finding.
- **Why it matters** This claim is presented as a key insight of the study, but without quantitative support it remains an assertion. A more rigorous analysis would involve mapping important features onto the three-dimensional structure and statistically testing whether they cluster in specific regions or are uniformly distributed.
- **Resolution test** Provide a spatial analysis of feature importance, such as a heatmap of importance scores mapped onto the binding interface, and a statistical test comparing the observed distribution to a null model.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2, Figure 2B
- **Evidence pointer** Section 2.2; Figure 2B; location not provided
- **Issue** The description of the RMSD threshold selection is vague. The manuscript states that a 10 Å cutoff was determined "through visual inspection of the simulations," which is not a reproducible criterion.
- **Required correction** Provide a more objective and reproducible method for threshold selection, such as analysis of the RMSD distribution with clear criteria for distinguishing reliable from unreliable alignments.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 3, Discussion
- **Evidence pointer** Section 3; location not provided
- **Issue** The Discussion contains some redundancy with the Results section, particularly regarding the description of the structural alignment algorithm and the ML pipeline. Some statements are repeated nearly verbatim.
- **Required correction** Streamline the Discussion to focus on interpretation and implications rather than restating results. This would improve readability and reduce the manuscript length.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Section 5.1, Methods
- **Evidence pointer** Section 5.1; location not provided
- **Issue** The manuscript states that "Cα-Cα distances" are used as features in the ML pipeline, but earlier in the Results section, the contact definition is described using "CL-CL distances." The inconsistency between Cα and CL atom references is confusing.
- **Required correction** Clarify which atom types are used for distance calculations and ensure consistency throughout the manuscript.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 5.1, Methods
- **Evidence pointer** Section 5.1; location not provided
- **Issue** The manuscript mentions that "two independent sets of simulations" were performed for each system, but the rationale for this choice and the criteria for assessing convergence and reproducibility between replicas are not fully described.
- **Required correction** Provide additional details on how replicas were compared and why the analysis proceeded with Replica 1 only, beyond the RMSF comparison described.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 4, Conclusions
- **Evidence pointer** Section 4; location not provided
- **Issue** The Conclusions section contains a typographical error: "Ur approach" should be "Our approach."
- **Required correction** Correct the typographical error.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Section 2.1, Figure 1
- **Evidence pointer** Section 2.1; Figure 1; location not provided
- **Issue** The bibliometric analysis used to justify protein selection is described in the text but the specific metrics and their interpretation are not fully explained. The relationship between bibliometric indicators and scientific relevance is assumed rather than argued.
- **Required correction** Provide a brief justification for why bibliometric indicators are appropriate proxies for scientific relevance, and clarify how the metrics informed the final selection.

- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of uncertainty quantification and baseline comparisons for classifier performance), R1-M2 (absence of validation for identified feature importance), R1-M4 (insufficient validation of force field parameters). These issues must be addressed before the central claims of the manuscript can be considered established.

- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The combination of MD simulations with interpretable ML for protein-protein interaction analysis is not entirely new, building on prior work by Cappella et al. and Pavlova et al. The structural alignment algorithm and ACF-based data partitioning are novel elements, but their distinctiveness from existing methods requires clearer articulation.
  - Scientific importance: Moderate. The biological question of Wnt-Wls binding specificity is important, and the identification of specific residue pairs could inform future experimental studies. However, the lack of validation limits the immediate impact of the findings.
  - Interdisciplinary readership: Moderate. The work bridges computational biophysics, machine learning, and Wnt biology, which could appeal to readers across these fields. However, the technical depth may limit accessibility to a broader audience.
  - Technical soundness: Currently insufficient. The concerns regarding uncertainty quantification, baseline comparisons, and force field validation must be addressed. The methodological approach is generally sound but requires more rigorous evaluation.
  - Readability for nonspecialists: Adequate. The manuscript is generally well-written and provides sufficient context for readers unfamiliar with MD simulations or ML. However, some sections, particularly the Methods, may be challenging for nonspecialists.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important biological question with a sophisticated computational approach, and the methodological framework has potential value. However, the current evidence does not fully establish the central claims. The lack of uncertainty quantification for the classifier performance, the absence of validation for the identified features, and the insufficient validation of force field parameters are significant issues that must be addressed. If these concerns are resolved through additional analysis and validation, the manuscript could make a meaningful contribution to the field.