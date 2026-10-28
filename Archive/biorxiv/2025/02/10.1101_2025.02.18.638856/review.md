## Review setup
- **Input scope** Full manuscript text (abstract, introduction, related works, methodology, results, limitations, conclusion) as provided
- **Assessment boundary** Scientific content, methodological soundness, claims vs. evidence, database utility, and presentation quality
- **Shared manuscript claim summary** The authors present BENDER DB, a database of predicted protein binding sites across proteomes of pathogens associated with neglected diseases, built from AlphaFold-predicted structures and integrating outputs from five binding site prediction tools. They also introduce BENDER AI, a meta-predictor combining these outputs, and report that it outperforms individual methods on several metrics.
- **Visible evidence base** Text descriptions of methods and results; references to Figures 1–8 and Tables 1–3; performance metrics for BENDER AI (MCC 0.64, AUC 0.89); case study on CYP51 (Q7Z1V1, PDB 2WUZ) with precision comparisons
- **Missing materials affecting confidence** Figures and tables not provided; no supplementary data, benchmark details, dataset descriptions, or code availability information; no details on how COACH datasets were processed or how predictions were standardized across tools

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful community resource for neglected disease research. The concept of integrating multiple binding site predictors on AlphaFold structures is reasonable and timely. However, the current manuscript lacks critical technical details needed to evaluate the quality and utility of the database. The BENDER AI meta-predictor is presented with limited benchmarking information, and the case study is narrow. The claims of outperformance are not fully supported by the evidence provided. The manuscript would benefit from clearer descriptions of data processing, validation, and comparison with existing resources.
- **Who would be interested in the results, and why** Researchers in neglected disease drug discovery, structural bioinformatics, and computational biology would find this resource relevant. Those working on target identification and repurposing for pathogens such as Trypanosoma cruzi, Leishmania, and others could use the database to prioritize binding sites for experimental validation. The integration of multiple predictors and the consensus approach may also interest method developers in the binding site prediction community.
- **Major strengths** The focus on neglected diseases addresses an important gap, as most existing databases emphasize human proteins or well-studied pathogens. The use of AlphaFold structures enables proteome-wide coverage where experimental structures are scarce. The integration of five complementary predictors and the provision of consensus views is a practical approach. The web interface with interactive visualization tools appears user-friendly and accessible to non-specialists.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (benchmarking), R1-M2 (data processing details), R1-M3 (case study scope), R1-M4 (database accessibility and utility)
- **Assessment against Nature-style criteria** Originality: moderate. While the combination of multiple predictors on neglected disease proteomes is somewhat novel, the individual components are established. Scientific importance: potentially high for the neglected disease community, but the current evidence does not fully demonstrate the resource's value. Interdisciplinary readership: the database could appeal to both computational and experimental researchers, but the manuscript is written primarily for a bioinformatics audience. Technical soundness: not fully established due to missing details on data processing, benchmarking, and validation. Readability for nonspecialists: the manuscript is generally clear, but some sections assume familiarity with binding site prediction tools and metrics.
- **Recommendation posture** Supportive if technical concerns are resolved. The resource has potential value, but the manuscript requires substantial revisions to establish the reliability and utility of the database and the meta-predictor.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "BENDER AI outperformed all individual methods in 4 out of 5 evaluated metrics. Specifically, it achieved an MCC of 0.64 and an AUC of 0.89, surpassing the highest MCC of 0.63 and the highest AUC of 0.84 obtained by individual predictors."
- **Evidence pointer** Table 2, Section 4.2
- **Concern** The benchmarking of BENDER AI is described only in text with reference to Table 2, which is not provided. Critical details are missing: What datasets were used for evaluation? Were the COACH training and test sets used directly, or were they filtered or modified? How were the five individual predictors run on these datasets? Were their default parameters used? How was the decision tree trained and evaluated? What was the cross-validation procedure? The reported MCC of 0.64 and AUC of 0.89 are presented without confidence intervals or statistical significance testing. Additionally, the comparison with individual methods is unclear: were the individual methods evaluated on the same test set with the same residue-level labels?
- **Why it matters** The central claim of the manuscript is that BENDER AI provides improved binding site prediction. Without a clear and reproducible benchmarking protocol, this claim cannot be verified. The scientific community needs to understand exactly how the meta-predictor was trained and tested to assess its reliability and generalizability.
- **Resolution test** Provide full details of the training and evaluation procedure, including dataset descriptions, preprocessing steps, hyperparameter settings, cross-validation strategy, and statistical comparisons. Make the evaluation code and datasets publicly available. Report confidence intervals or perform significance tests for the performance differences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "The results were standardized and cataloged in the BENDER DB, providing a comprehensive resource for binding site analysis across multiple proteomes."
- **Evidence pointer** Section 3.2, Section 3.3
- **Concern** The manuscript states that outputs from five predictors were standardized to a residue format, but the details of this standardization are not described. Different tools produce outputs in different formats: some may output pocket centers, others residue lists, others atom-level probabilities. How were these converted to a common residue-level representation? How were conflicts resolved when tools disagreed on the definition of a binding site? What thresholds were used to define a residue as part of a binding site for each tool? The description of how GRaSP, P2Rank, PointSite, DeepPocket, and PUResNet outputs were processed is insufficient.
- **Why it matters** The utility of the database depends on the reliability and consistency of the underlying data. If the standardization process is not clearly described, users cannot interpret the results correctly. Inconsistent or arbitrary thresholds could lead to misleading conclusions about binding site locations.
- **Resolution test** Provide a detailed description of the data processing pipeline, including specific thresholds, conversion rules, and handling of edge cases. Include a flowchart or pseudocode of the standardization process. Discuss potential biases introduced by the standardization and how they were addressed.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "To illustrate how results from BENDER DB can be applied in drug discovery and repositioning studies, we focus on Sterol 14-alpha demethylase (CYP51) with the UniProt accession Q7Z1V1."
- **Evidence pointer** Section 4.3, Table 3
- **Concern** The case study is limited to a single protein and primarily reports precision values for different predictors against PDB and BioLip annotations. While this demonstrates that BENDER AI has fewer false positives, it does not show how the database can be used in a real drug discovery workflow. The case study does not include any docking, virtual screening, or comparison with known inhibitors beyond the general discussion of CYP51 as a drug target. The choice of this single protein may not be representative of the broader utility of the database.
- **Why it matters** The manuscript claims the database can accelerate drug discovery efforts, but the case study does not convincingly demonstrate this. A more compelling demonstration would show how a researcher could use BENDER DB to identify novel binding sites, prioritize targets, or guide experimental validation.
- **Resolution test** Expand the case study to include multiple proteins or a more realistic drug discovery scenario. Show how the consensus and BENDER AI predictions could be used to select targets or design experiments. Alternatively, provide a user scenario or workflow example that illustrates the practical utility of the database.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "BENDER DB is available at https://benderdb.ufv.br"
- **Evidence pointer** Section 3.5, Section 4.1
- **Concern** The manuscript describes the web server and its features, but no information is provided about the database schema, query capabilities, download options, or API access. It is unclear whether users can download the full dataset, search by protein or organism, or programmatically access the data. The manuscript also does not describe how the database will be maintained, updated, or versioned. The availability statement is minimal and does not include information about data licensing or usage terms.
- **Why it matters** For a database resource, accessibility and usability are critical. The scientific community needs to know how to access, query, and download the data. Without clear documentation of the database structure and access methods, the resource may not be widely adopted.
- **Resolution test** Provide a detailed description of the database schema, search functionality, download options, and any API endpoints. Include information about data licensing, update frequency, and long-term maintenance plans. Consider adding a user guide or tutorial.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 3.2
- **Evidence pointer** Section 3.2
- **Issue** The descriptions of the five binding site predictors are brief and do not provide enough context for readers unfamiliar with these tools. The criteria for selecting these specific tools are not clearly stated.
- **Required correction** Expand the descriptions of each tool, including their underlying methodology, input requirements, and known limitations. State the selection criteria explicitly and justify why these five tools were chosen over other available options.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 3.3
- **Evidence pointer** Section 3.3
- **Issue** The description of how DeepSeek results were filtered using a 70% confidence threshold is unclear. The manuscript states that exceptions occur when no pockets exceed 70% confidence, in which case the five best-ranked pockets are noted. The rationale for this threshold and the exception rule is not explained.
- **Required correction** Clarify the confidence threshold selection process and justify the exception rule. Discuss how this filtering affects the overall quality and coverage of the database.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 4.2
- **Evidence pointer** Section 4.2
- **Issue** The description of the consensus approach is somewhat repetitive with Section 3.4. The relationship between the mean consensus and the BENDER AI predictions could be explained more clearly.
- **Required correction** Streamline the description of the consensus approach and clearly differentiate between the mean consensus and BENDER AI. Consider moving some of the detailed description to the methodology section.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 5
- **Evidence pointer** Section 5
- **Issue** The limitations section is brief and does not address potential issues with the underlying AlphaFold structures, such as low-confidence regions or the impact of conformational flexibility on binding site predictions.
- **Required correction** Expand the limitations section to discuss the known limitations of AlphaFold structures for binding site prediction, including potential inaccuracies in flexible regions and the lack of conformational diversity.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 4.3
- **Evidence pointer** Table 3
- **Issue** The precision values in Table 3 are reported without context. It is unclear how many total residues were predicted by each method, how many were true positives, and what the recall values were for each method in this specific case.
- **Required correction** Provide additional metrics for the case study, including recall, F1, and the number of predicted residues. This will give readers a more complete picture of the performance trade-offs.

## Risk / unsupported claims
- The claim that BENDER AI "outperformed all individual methods in 4 out of 5 evaluated metrics" is not fully supported without details on the evaluation protocol, dataset composition, and statistical significance.
- The claim that the database "can accelerate drug discovery efforts" is not demonstrated by the case study, which only shows precision comparisons for a single protein.
- The claim that the database provides a "comprehensive resource" is not verifiable without information on database completeness, coverage, and quality control measures.
- The performance metrics reported in Table 2 are not reproducible without access to the evaluation code and datasets.
- The statement that "BENDER DB offers unique features" is not fully supported, as the manuscript does not provide a detailed comparison with existing databases such as HProteome-BSite or CavitySpace in terms of features and functionality.