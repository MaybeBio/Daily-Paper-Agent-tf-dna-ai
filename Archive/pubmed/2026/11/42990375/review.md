## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors present ChAI-Net, a deep learning model that predicts locus-specific chromatin co-accessibility maps from DNA sequence in mouse embryonic stem cells, and claim that model interpretation reveals sequence motifs and regulatory grammar (motif orientation, spacing, positioning, co-occurrence) that are specific to co-accessibility and missed by average accessibility models.
- **Visible evidence base** Abstract text only; no quantitative results, model performance metrics, validation details, or comparison data are provided
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, model architecture details, training and evaluation protocols, datasets, and code availability

## Reviewer
- **Overall assessment** The abstract describes a potentially valuable integration of single-molecule long-read footprinting with deep learning to infer regulatory grammar governing chromatin co-accessibility. The conceptual framing is clear and the motivation is well articulated. However, the abstract provides no quantitative evidence, no model performance metrics, no validation strategy, and no concrete examples of the claimed regulatory grammar. As presented, the core claims are plausible but entirely unsupported by visible evidence. The work may be of interest to the chromatin biology and regulatory genomics communities, but the current abstract does not establish the case.
- **Who would be interested in the results, and why** Researchers studying transcriptional regulation, chromatin structure, transcription factor cooperativity, and cis-regulatory element function would be interested. The work also speaks to the growing community applying deep learning to interpret genomic sequence, and to those developing single-molecule footprinting technologies. The promise of extracting regulatory rules that are invisible to bulk accessibility assays could inform both basic regulatory biology and the design of predictive models for variant interpretation.
- **Major strengths** The conceptual advance of moving from average accessibility to co-accessibility as a modeling target is well motivated and timely. The combination of single-molecule footprinting with deep learning is a natural and potentially powerful pairing. The emphasis on interpretability and in silico perturbation experiments is aligned with current best practices in regulatory genomics. The abstract is clearly written and accessible to a broad readership.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality is high in concept, as co-accessibility as a modeling target is a relatively unexplored direction. Scientific importance is potentially high, but cannot be assessed without evidence that the model works and that the inferred grammar is biologically meaningful. Interdisciplinary readership is plausible, spanning genomics, machine learning, and chromatin biology. Technical soundness cannot be evaluated from the abstract alone. Readability for nonspecialists is good, with clear motivation and plain language, though some terms such as "co-accessibility maps" and "regulatory grammar" would benefit from brief definition.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising but lacks all quantitative support. A full manuscript with model performance, validation, and concrete examples of learned motifs and grammar would be required to assess the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that ChAI-Net "predicts these locus-specific chromatin co-accessibility maps from the underlying DNA sequence" and that model interpretation reveals regulatory grammar.
- **Evidence pointer** Abstract only; no performance metrics, validation, or architecture details provided
- **Concern** No quantitative evidence of model performance is presented. There is no mention of prediction accuracy, correlation with held-out data, comparison to baseline models, or any measure of generalization. Without such metrics, the central claim that the model successfully learns co-accessibility from sequence cannot be evaluated.
- **Why it matters** The entire premise of the paper rests on the model being able to predict co-accessibility maps accurately. If the model performs poorly or only trivially, all downstream interpretation claims are undermined. The abstract must at least report key performance statistics to establish that the model works.
- **Resolution test** Provide in the abstract or full manuscript the model's predictive performance on held-out loci, including correlation coefficients or similar metrics, and a comparison to appropriate baselines such as models trained on average accessibility.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The authors claim that "many of these motifs are missed when modeling average accessibility, suggesting a specific role in coordinated binding" and that the model highlights "the importance of TF motif orientation, spacing, positioning, and co-occurrence in driving co-accessibility."
- **Evidence pointer** Abstract only; no examples, figures, or quantitative comparisons provided
- **Concern** The abstract asserts that the model learns unique motif combinations and regulatory grammar, but provides no concrete examples, no enrichment statistics, no comparison to motifs learned from average accessibility models, and no demonstration that the identified features are biologically meaningful. The claim that motifs are "missed" by average accessibility models is not supported by any visible data.
- **Why it matters** The biological insight is the main contribution of the work. Without showing specific motifs, their enrichment, and their relationship to known regulatory elements, the claims remain anecdotal. The reader cannot judge whether the discovered grammar is novel, reproducible, or functionally relevant.
- **Resolution test** Include in the abstract or full manuscript specific examples of motifs identified by ChAI-Net, with enrichment statistics relative to background and to average accessibility models, and demonstrate that these motifs are associated with coordinated TF binding or functional regulatory activity.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors state that "through model interpretation and in silico experiments" they show the model's learned grammar, implying a complete analytical pipeline.
- **Evidence pointer** Abstract only; no methods, data availability, or code availability mentioned
- **Concern** No information is provided about the data used, the model architecture, training procedure, hyperparameters, or how in silico experiments were designed. There is no mention of data or code availability. This makes the work impossible to reproduce or even to assess for methodological rigor.
- **Why it matters** Reproducibility is a core requirement for computational biology. Without details on data and methods, the claims cannot be verified by the community. The abstract should at least indicate that full methods and resources will be made available.
- **Resolution test** Provide in the full manuscript a complete methods section, including data sources, model architecture, training details, and in silico experiment protocols, and state data and code availability.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract terminology
- **Evidence pointer** Abstract, first paragraph
- **Issue** The term "co-accessibility maps" is used without a precise definition. It is not clear whether this refers to pairwise correlations, joint probabilities, or some other measure of simultaneous accessibility.
- **Required correction** Define co-accessibility explicitly in the abstract, for example as the frequency of simultaneous accessibility at pairs of positions on individual molecules.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Scope
- **Affected element** Abstract claims
- **Evidence pointer** Abstract, final sentence
- **Issue** The abstract claims the framework "lays the groundwork to elucidate how these rules vary across cellular contexts," but no evidence is presented that the model or approach generalizes beyond mouse embryonic stem cells.
- **Required correction** Soften this claim or provide preliminary evidence of generalizability, such as application to another cell type or mention of planned validation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract results
- **Evidence pointer** Abstract, results section
- **Issue** The abstract does not report the number of loci analyzed, the number of motifs identified, or any measure of effect size. This limits the reader's ability to gauge the scale and significance of the findings.
- **Required correction** Include basic quantitative descriptors, such as the number of enhancers, promoters, and CTCF-bound sites analyzed, and the number of motifs or grammar rules identified.

## Risk / unsupported claims
- The claim that ChAI-Net successfully predicts co-accessibility maps is unsupported without performance metrics.
- The claim that motifs are "missed" by average accessibility models is unsupported without comparative analysis.
- The claim that motif orientation, spacing, positioning, and co-occurrence are important is unsupported without specific examples and statistics.
- The claim that the framework expands understanding of TF cooperativity is unsupported without functional validation.
- The claim that the approach lays groundwork for cross-context analysis is speculative and unsupported.