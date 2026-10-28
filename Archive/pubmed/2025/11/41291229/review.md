## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no methods, figures, or supplementary data were available for evaluation
- **Shared manuscript claim summary** The authors report a new high-throughput method, ENTRAP-seq, for multiplexed profiling of transcriptional regulatory activity from protein-coding libraries in plant cells. They apply this method to screen 1,495 plant viruses, identify hundreds of putative transcriptional regulatory domains in proteins not previously associated with gene regulation, and combine the method with machine-guided design to engineer a plant transcription factor in a semirational manner.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials provided
- **Missing materials affecting confidence** Full methods, all figures and tables, statistical analyses, validation experiments, and any supplementary data; without these, the technical performance, reproducibility, and robustness of ENTRAP-seq cannot be independently assessed

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable technical advance in plant functional genomics. The concept of coupling a nuclear magnetic sorting-based reporter with protein-coding library delivery is innovative and could address a genuine gap in scalable in planta characterization of transcriptional regulators. However, the abstract alone provides insufficient detail to evaluate the method's sensitivity, specificity, throughput, or the validity of the biological findings. The claim of identifying "hundreds of putative transcriptional regulatory domains" from viral proteins requires careful validation that cannot be assessed from the provided material. The machine learning and machine-guided design components are mentioned but not described in any detail. The work is likely to interest plant biologists and synthetic biologists, but the evidence base is too limited to establish the case.
- **Who would be interested in the results, and why** Plant molecular biologists studying transcriptional regulation, synthetic biologists working on plant engineering, virologists interested in host-virus interactions, and researchers developing high-throughput functional assays for protein characterization. The method could enable large-scale dissection of regulatory domains and accelerate engineering of transcription factors for crop improvement.
- **Major strengths** The method addresses a clear unmet need for multiplexed, scalable characterization of transcriptional regulatory activity in plants. The combination of a nuclear magnetic sorting-based reporter with sequencing readout is conceptually elegant. The application to viral protein libraries is a creative and potentially high-impact use case. The integration of machine learning for both screening and design suggests a forward-looking approach.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  **Originality** The concept of combining nuclear magnetic sorting with sequencing for multiplexed regulatory activity profiling in plants appears novel. However, the abstract does not clarify how this differs from existing reporter-based methods beyond the scale and the sorting mechanism.  
  **Scientific importance** If the method performs as claimed, it could substantially advance plant functional genomics and synthetic biology. The identification of regulatory domains in viral structural proteins and enzymes would be a notable finding with implications for understanding viral manipulation of host transcription.  
  **Interdisciplinary readership** The work bridges plant biology, virology, high-throughput screening, and machine learning, which could attract a broad readership. However, the abstract does not sufficiently explain the method for nonspecialists.  
  **Technical soundness** Cannot be assessed from the abstract. Key parameters such as sensitivity, false positive rate, reproducibility, and validation of the identified domains are not described.  
  **Readability for nonspecialists** The abstract is dense and assumes familiarity with reporter assays, nuclear magnetic sorting, and machine-guided design. A clearer explanation of the method's workflow and significance would improve accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a promising approach, but the technical claims and biological findings require full manuscript evaluation. I would be supportive if the technical concerns are resolved in the full paper.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The abstract claims that ENTRAP-seq enables "multiplexed measurement of regulatory activity from thousands of protein variants" and that the screen of 1,495 plant viruses identified "hundreds of putative transcriptional regulatory domains."  
- **Evidence pointer** Abstract only; no methods or figures provided  
- **Concern** The abstract provides no information on the sensitivity, specificity, dynamic range, or reproducibility of ENTRAP-seq. It is unclear how the nuclear magnetic sorting-based reporter distinguishes true regulatory activity from background or false positives. The criteria for calling a "putative transcriptional regulatory domain" are not defined.  
- **Why it matters** Without these parameters, the reliability of the reported hits cannot be evaluated. High-throughput screens are prone to false positives, and the biological significance of the identified domains depends on the stringency and accuracy of the assay.  
- **Resolution test** The full manuscript must provide detailed methods for the reporter design, sorting thresholds, sequencing analysis, and statistical criteria for hit calling. Validation experiments, such as orthogonal assays for a subset of identified domains, would be necessary to confirm regulatory activity.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The abstract claims identification of "hundreds of putative transcriptional regulatory domains found in structural proteins and enzymes not associated with gene regulation."  
- **Evidence pointer** Abstract only; no validation data provided  
- **Concern** The claim that regulatory domains exist in proteins not previously associated with gene regulation is surprising and potentially important. However, the abstract provides no evidence that these domains function as transcriptional regulators in their native context or that the activity observed in the reporter assay reflects endogenous function.  
- **Why it matters** If these findings are not validated, the central biological claim of the paper is unsupported. The presence of a domain that can drive reporter activity in an artificial assay does not necessarily indicate a natural regulatory role.  
- **Resolution test** The full manuscript should include validation experiments, such as loss-of-function or gain-of-function studies in plants, to demonstrate that the identified domains have regulatory roles in relevant biological contexts.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The abstract claims that ENTRAP-seq was combined with machine learning to screen viral libraries and with machine-guided design to engineer a plant transcription factor.  
- **Evidence pointer** Abstract only; no details on the machine learning approach provided  
- **Concern** The abstract does not describe the machine learning models, training data, feature sets, or validation procedures. It is unclear how the models were used to prioritize candidates or guide design, and whether the predictions were experimentally confirmed.  
- **Why it matters** Machine learning components are increasingly common in high-throughput biology, but their utility depends on rigorous training and validation. Without details, the contribution of the machine learning to the results cannot be assessed.  
- **Resolution test** The full manuscript must describe the machine learning methodology, including data splits, model selection, and independent validation. The engineered transcription factor should be characterized experimentally to demonstrate that the design achieved the intended activity.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Reproducibility  
- **Claim pointer** The abstract implies that ENTRAP-seq is a scalable and generalizable method for plant cells.  
- **Evidence pointer** Abstract only; no information on generalizability provided  
- **Concern** The abstract does not specify which plant species or cell types were used, nor whether the method is applicable across different plant systems. The scalability claim is not supported by data on throughput limits or consistency across biological replicates.  
- **Why it matters** For a method paper, generalizability and reproducibility are key criteria for adoption by the community. If the method only works in a narrow context, its impact is limited.  
- **Resolution test** The full manuscript should include data from multiple plant species or cell types, replicate experiments, and a discussion of the method's limitations and potential for adaptation.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Method name and workflow description  
- **Evidence pointer** Abstract, first sentence  
- **Issue** The acronym ENTRAP-seq is introduced without a clear explanation of the workflow. The term "nuclear trans-elements reporter assay" is not self-explanatory.  
- **Required correction** Provide a brief, plain-language description of the method steps in the abstract or a schematic figure in the full manuscript.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Abstract, second sentence  
- **Evidence pointer** Abstract, "nuclear magnetic sorting-based reporter"  
- **Issue** The mechanism of "nuclear magnetic sorting" is not explained. Nonspecialist readers may not understand what this entails.  
- **Required correction** Add a brief explanation of the sorting mechanism, such as magnetic labeling of nuclei based on reporter activity, to improve accessibility.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Abstract, final sentence  
- **Evidence pointer** Abstract, "scalable protein function assays deployed in planta"  
- **Issue** The broader implications for "natural and synthetic coding diversity" are stated but not elaborated. The abstract would benefit from a sentence on potential applications, such as engineering stress-tolerant crops or understanding viral pathogenesis.  
- **Required correction** Expand the final sentence to briefly mention specific potential applications or follow-up directions.

## Risk / unsupported claims
- The claim of identifying "hundreds of putative transcriptional regulatory domains" is unsupported without validation data or criteria for hit calling.
- The claim that ENTRAP-seq enables "multiplexed measurement of regulatory activity from thousands of protein variants" is unverifiable without performance metrics.
- The claim of "semirational" engineering of a plant transcription factor is not supported by any description of the design process or experimental outcome.
- The generalizability of the method to different plant systems is not assessable from the abstract.
- The biological relevance of regulatory domains found in viral structural proteins and enzymes is not established.