## Review setup
- **Input scope** Full manuscript text (ChemRxiv preprint, v2)
- **Assessment boundary** Methods, computational results, and conclusions as presented in the supplied text; no supplementary materials, figures, or tables were provided
- **Shared manuscript claim summary** The authors describe a virtual screening campaign targeting two sub-pockets of the SARS-CoV-2 NSP13 RNA-binding site, using the FITTED docking program within the FORECASTER suite. They employed rigid and flexible docking, followed by a consensus evaluation of poses using four approaches (docking score, graph neural network, quantum mechanics, and visualization). They also implemented templated docking using co-crystallized fragments. The manuscript states that experimental testing by the Structural Genomics Consortium is pending and that the manuscript will be updated when results are available.
- **Visible evidence base** Only the abstract-level text was provided. No figures, tables, docking scores, compound lists, or detailed methods are visible.
- **Missing materials affecting confidence** Full methods section, docking parameters, compound library details, scoring data, structural preparation steps, templated docking implementation details, and any results or validation metrics. The absence of these materials severely limits the ability to assess technical soundness and reproducibility.

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful computational workflow for targeting NSP13, but as presented, it is a methods description without results. The core claims are about the approach and its implementation, not about validated outcomes. The lack of any quantitative results, validation, or comparison to known binders means the case for the method's effectiveness is not established. The pending experimental data is acknowledged, which is appropriate, but the current version does not provide sufficient evidence to support the stated conclusions about the screening campaign's success or the utility of the templated docking approach.
- **Who would be interested in the results, and why** Computational chemists and drug discovery researchers working on SARS-CoV-2 targets, particularly those involved in structure-based virtual screening and consensus scoring methods. The CACHE challenge community would also be interested, as this manuscript documents a specific submission. The templated docking implementation within FITTED may interest developers of docking software and users seeking to incorporate fragment information into screening workflows.
- **Major strengths** The use of a multi-pronged consensus approach (docking score, machine learning, quantum mechanics, and visualization) is a thoughtful strategy to reduce false positives. The implementation of templated docking within FITTED is a novel methodological contribution that could benefit the broader docking community. The commitment to open science and updating the manuscript with experimental results is commendable.
- **Major Concerns**  
  - R1-M1: The manuscript provides no results. There are no docking scores, hit lists, enrichment metrics, or any quantitative output from the virtual screening. The claims about the approach's effectiveness are unsupported.  
  - R1-M2: The templated docking implementation is described only at a high level. No details on how templates were selected, how the method was validated, or how it performed compared to standard docking are provided.  
  - R1-M3: The consensus scoring method is not described in sufficient detail. The specific machine learning model, quantum mechanics method, and how the consensus was computed are not specified.  
  - R1-M4: The manuscript does not include any comparison to known NSP13 binders or decoy sets, which is essential to assess the screening's predictive power.
- **Minor Comments**  
  - R1-m1: The title mentions "consensus-scoring method" but the abstract does not define the exact consensus rule. Clarify whether it is a rank-based, score-based, or majority-vote consensus.  
  - R1-m2: The phrase "multi-pronged virtual screening" is vague. Specify the number of compounds screened and the hit rate.  
  - R1-m3: The abstract states "we now await the experimental testing" which is appropriate, but the manuscript should clearly state that this is a methods paper without results, to set reader expectations.  
  - R1-m4: The reference to "FITTED templated docking" should include a brief description of how it differs from standard docking, even in the abstract.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4. The absence of any results or validation means the technical case for the method's utility is not established.
- **Assessment against Nature-style criteria**  
  - Originality: The consensus approach and templated docking are not entirely novel, but the specific combination and application to NSP13 may offer incremental originality. However, without results, the novelty cannot be fully assessed.  
  - Scientific importance: Targeting NSP13 is relevant, but the importance of this specific computational workflow is not demonstrated without experimental validation or benchmark results.  
  - Interdisciplinary readership: The work is primarily of interest to computational chemists and structural biologists. The lack of results limits broader appeal.  
  - Technical soundness: Cannot be assessed from the provided material. The methods are described at a level that prevents evaluation of their correctness or reproducibility.  
  - Readability for nonspecialists: The abstract is accessible, but the lack of results and methodological detail makes it difficult for nonspecialists to gauge the significance.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript is a methods description without results. It could become supportive if the authors add quantitative results, validation, and detailed methods, but as presented, the case is not made.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Results and validation  
- **Claim pointer** The manuscript implies that the virtual screening campaign produced a set of predictions ready for experimental testing, but no results are presented.  
- **Evidence pointer** Abstract, "we now await the experimental testing of our predictions" (location not provided)  
- **Concern** The manuscript contains no quantitative results from the virtual screening. There are no docking scores, hit lists, enrichment factors, or any metrics that would allow a reader to assess the quality of the predictions.  
- **Why it matters** Without results, the claims about the approach's effectiveness cannot be evaluated. The reader cannot determine whether the consensus method or templated docking improved performance over standard approaches.  
- **Resolution test** Provide a summary of the screening results, including the number of compounds selected, the distribution of scores, and any enrichment or validation metrics against known binders or decoys.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological detail  
- **Claim pointer** The authors state they "implemented templated docking within FITTED" but provide no details on the implementation or its validation.  
- **Evidence pointer** Abstract, "we implemented templated docking within FITTED" (location not provided)  
- **Concern** The templated docking method is described only at a high level. There is no information on how templates were selected, how the method was tested, or how it compares to standard docking in FITTED.  
- **Why it matters** Templated docking is a methodological claim that requires validation. Without details, the reader cannot reproduce the method or assess its utility.  
- **Resolution test** Describe the templated docking algorithm, provide validation results (e.g., docking accuracy on a test set), and compare its performance to standard docking.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological detail  
- **Claim pointer** The authors used a consensus of four approaches (docking score, graph neural network, quantum mechanics, and visualization) but do not specify how the consensus was computed.  
- **Evidence pointer** Abstract, "the final selection being based on the consensus of all four approaches" (location not provided)  
- **Concern** The consensus method is not defined. It is unclear whether the consensus is based on ranks, scores, or a voting scheme. The specific machine learning model and quantum mechanics method are also not named.  
- **Why it matters** The consensus approach is a central claim of the manuscript. Without a clear definition, the method is not reproducible, and the reader cannot assess whether the consensus is meaningful.  
- **Resolution test** Specify the exact consensus rule, the machine learning architecture, the quantum mechanics method, and how each component was weighted or combined.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Validation  
- **Claim pointer** The manuscript implies the screening approach is effective, but there is no comparison to known NSP13 binders or decoy sets.  
- **Evidence pointer** Abstract, "we targeted each of two sub-pockets of the NSP13 RNA-binding site" (location not provided)  
- **Concern** No validation of the screening method is provided. There is no evidence that the docking and consensus scoring can distinguish known binders from non-binders.  
- **Why it matters** Without validation, the predictions cannot be trusted. The reader has no basis to believe the selected compounds are more likely to bind than random selection.  
- **Resolution test** Include a retrospective validation using known NSP13 binders or a decoy set, showing enrichment or AUC metrics for the consensus method.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Title and abstract  
- **Evidence pointer** Title, "consensus-scoring method" (location not provided)  
- **Issue** The consensus rule is not defined.  
- **Required correction** State whether the consensus is rank-based, score-based, or a majority vote.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, "multi-pronged virtual screening" (location not provided)  
- **Issue** The number of compounds screened and the hit rate are not mentioned.  
- **Required correction** Add the compound library size and the number of selected hits.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Scope  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, "we now await the experimental testing" (location not provided)  
- **Issue** The manuscript is presented as a methods description, but the abstract does not clearly state that no results are available yet.  
- **Required correction** Explicitly state that this is a methods paper without experimental results.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, "templated docking within FITTED" (location not provided)  
- **Issue** The difference between templated docking and standard docking is not explained.  
- **Required correction** Add a brief description of how templated docking works and its intended advantage.

## Risk / unsupported claims
- The claim that the consensus approach improves selection accuracy is unsupported, as no results are provided.
- The claim that templated docking supplements the consensus selection is unsupported, as no details or validation are given.
- The claim that the screening campaign targeted two sub-pockets effectively is unverifiable without structural details or results.
- The overall utility of the approach for NSP13 drug discovery is not assessable from the provided material.