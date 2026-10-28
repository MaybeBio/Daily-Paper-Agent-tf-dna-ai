## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the supplied abstract text
- **Shared manuscript claim summary** The authors describe PredictProtein, a web server for protein sequence analysis operating since 1992, and report recent updates including infrastructure relocation, use of MMseqs2 for sequence search, improved user interface, and addition of new prediction methods including deep learning embeddings and binding site prediction. They state the server is freely accessible and queried by over 3,000 users monthly in 2020.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials provided
- **Missing materials affecting confidence** Full manuscript, methods descriptions, performance benchmarks, validation datasets, user statistics methodology, and any comparative analyses against other servers

## Reviewer
- **Overall assessment** The abstract presents a descriptive overview of a long-standing bioinformatics resource with claims of recent improvements and new features. While the historical significance of PredictProtein is notable, the abstract lacks quantitative evidence for the stated improvements, such as runtime reduction, prediction accuracy, or user impact. The scientific case for novelty and technical soundness cannot be adequately assessed from the supplied material.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians developing or using protein structure and function prediction tools would be interested. Experimental biologists seeking accessible prediction servers for sequence analysis may also find the resource useful. The community maintaining or benchmarking such servers would value updates on infrastructure and method additions.
- **Major strengths** The abstract highlights a long operational history since 1992, establishing PredictProtein as a pioneering resource. The integration of deep learning embeddings and binding prediction methods indicates responsiveness to current methodological trends. The commitment to free availability and open source scripts supports reproducibility and broad accessibility.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality is partially evident given the historical claim of being the first Internet server for protein predictions, but the abstract does not demonstrate novel scientific contributions in the current update. Scientific importance is plausible for the bioinformatics community, but the abstract lacks evidence of broad impact or significant advances. Interdisciplinary readership is limited by the absence of context for nonspecialists. Technical soundness cannot be evaluated without methods or benchmarks. Readability for nonspecialists is moderate, but technical terms are used without explanation.
- **Recommendation posture** Currently not established from the provided evidence. The abstract alone does not support the core claims of improved performance or novel functionality, and a full manuscript with quantitative validation is required.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The abstract states that the use of MMseqs2 sequence search reduced runtime five-fold.  
- **Evidence pointer** Location not provided  
- **Concern** The claim of a five-fold runtime reduction is presented without any benchmark data, comparison baseline, or experimental conditions. No details are given on the hardware, dataset size, or query types used to measure this improvement.  
- **Why it matters** Runtime improvements are a key selling point for web servers, and unsupported quantitative claims undermine the credibility of the resource. Without reproducible benchmarks, users cannot verify the stated performance.  
- **Resolution test** Provide a methods section with benchmark protocols, including dataset descriptions, hardware specifications, and comparative runtime measurements against the previous version. Include error bars or statistical significance tests.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The abstract states that new prediction methods were added, including deep learning embeddings for GO and secondary structure, and a method for predicting proteins and residues binding DNA, RNA, or other proteins.  
- **Evidence pointer** Location not provided  
- **Concern** No performance metrics, validation datasets, or comparisons to existing methods are provided for any of the new prediction methods. The abstract does not specify the training data, model architectures, or evaluation protocols.  
- **Why it matters** For a resource that aims to provide reliable predictions, the accuracy of new methods is critical. Without validation, the scientific community cannot assess whether these additions represent genuine improvements or merely incremental changes.  
- **Resolution test** Include a detailed methods section with training and test datasets, cross-validation procedures, and performance metrics such as accuracy, precision, recall, or area under the curve. Compare against state-of-the-art methods on standard benchmarks.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Scientific importance  
- **Claim pointer** The abstract claims that PredictProtein was the first Internet server for protein predictions and pioneered combining evolutionary information and machine learning.  
- **Evidence pointer** Location not provided  
- **Concern** The historical claims are stated without citations or contextual evidence. The abstract does not reference prior publications or historical records that substantiate these pioneering contributions.  
- **Why it matters** Historical precedence is a strong claim that requires documentation. Without references, the assertion cannot be verified, and the scientific importance of the resource is weakened.  
- **Resolution test** Add citations to original publications or historical documentation that establish the timeline and pioneering nature of PredictProtein. Provide a brief historical context in the introduction.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Readability for nonspecialists  
- **Affected element** Abstract text  
- **Evidence pointer** Location not provided  
- **Issue** Terms such as "deep learning embeddings," "GO terms," and "MMseqs2" are used without definition or context, which may alienate experimental biologists who are a stated target audience.  
- **Required correction** Briefly define or explain these terms in the abstract or provide a glossary in the full manuscript.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Availability statement  
- **Evidence pointer** Location not provided  
- **Issue** The abstract states that all scripts and methods are freely available, but no version numbers, software dependencies, or usage examples are provided.  
- **Required correction** Specify the software versions, dependencies, and provide a link to documentation or a quick-start guide in the full manuscript.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** User impact  
- **Affected element** User statistics claim  
- **Evidence pointer** Location not provided  
- **Issue** The claim of over 3,000 monthly users in 2020 is presented without details on how this number was measured, such as unique vs. total queries or geographic distribution.  
- **Required correction** Describe the methodology for counting users and provide a breakdown of usage patterns if available.

## Risk / unsupported claims
- The five-fold runtime reduction from MMseqs2 is unsupported due to lack of benchmark data.
- The performance of new prediction methods, including deep learning embeddings and binding prediction, is unassessable without validation metrics.
- The historical claim of being the first Internet server for protein predictions is unverified without citations.
- The user count of over 3,000 monthly is unverifiable without methodology details.
- The statement that PredictProtein provides "reliable predictions" is a general assertion not backed by accuracy data in the abstract.