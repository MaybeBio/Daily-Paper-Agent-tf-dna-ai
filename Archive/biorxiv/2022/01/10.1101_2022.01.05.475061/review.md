## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as stated in the abstract; no methods, figures, or supplementary data were provided for evaluation
- **Shared manuscript claim summary** The authors propose a therapeutic strategy for fusion-addicted pediatric sarcomas (Ewing sarcoma and alveolar rhabdomyosarcoma) that exploits the neomorphic DNA-binding properties of chimeric fusion transcription factors (EWSR1-FLI1 and PAX3-FOXO1) to drive tumor-specific expression of therapeutic payloads. They report development of a synthetic enhancer-based expression cassette, identification of GPR64 as a tumor-specific surface antigen, functional validation of targeted lentiviral transduction with anti-GPR64 pseudotyping, in vivo efficacy of thymidine kinase/valganciclovir treatment, and extension of the approach to cytokine expression and to ARMS.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials were supplied
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methods details, statistical analyses, raw data, and supplementary information are absent. This severely limits the ability to assess technical validity, reproducibility, and the strength of the evidence supporting the central claims.

## Reviewer

- **Overall assessment** The abstract presents a conceptually interesting and potentially impactful strategy for targeting fusion-driven pediatric sarcomas. The idea of exploiting neomorphic DNA-binding rather than inhibiting the fusion protein is creative and could have broad relevance. However, the evidence as presented in the abstract is insufficient to establish the validity of the key claims. Critical details regarding the design of the expression cassette, the specificity and sensitivity of GPR64 targeting, the efficiency of transduction, the magnitude and reproducibility of in vivo effects, and the generalizability to ARMS and cytokine expression are not provided. The abstract reads as a summary of a substantial body of work, but without access to the underlying data, the technical soundness and the strength of the conclusions cannot be evaluated.
- **Who would be interested in the results, and why** Researchers in pediatric oncology, particularly those studying Ewing sarcoma and alveolar rhabdomyosarcoma, would be directly interested. The work also has relevance for the broader field of transcription factor-driven cancers, gene therapy, and targeted viral transduction strategies. Investigators working on synthetic biology approaches to cancer therapy and on the exploitation of tumor-specific transcriptional dependencies would find the conceptual framework appealing.
- **Major strengths** The conceptual advance is notable: reframing an "undruggable" oncogenic transcription factor as a therapeutic switch rather than a target for inhibition is a creative and potentially paradigm-shifting idea. The proposed versatility of the approach, with evidence for applicability across two different fusion-driven sarcomas and for expression of different payload types (cytotoxic enzyme and immunomodulatory cytokines), suggests a broadly adaptable platform. The identification of GPR64 as a candidate surface antigen for targeted transduction is a practical step toward clinical translation.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that a "de novo enhancer-based, synthetic and highly potent expression cassette" can elicit EWSR1-FLI1-dependent expression of a therapeutic payload, as evidenced by episomal and CRISPR-edited genomic reporter assays.
  - **Evidence pointer** Abstract only; location not provided
  - **Concern** The abstract provides no details on the design of the expression cassette, the number of enhancer elements, the minimal promoter used, the fold-induction of expression in fusion-positive versus fusion-negative cells, or the specificity of the response. The claim of "highly potent" and "tumor-specific" cannot be assessed without quantitative data on expression levels, background activity, and dynamic range.
  - **Why it matters** The entire therapeutic strategy depends on the ability of the cassette to drive high-level, tight, and specific expression in fusion-positive tumor cells. If the cassette has significant basal activity or insufficient dynamic range, the approach would not be safe or effective. Without these data, the foundational claim of the paper is unverified.
  - **Resolution test** Provide quantitative reporter assay data showing expression levels in EWSR1-FLI1-positive versus negative cell lines, including dose-response to fusion protein levels, and demonstrate minimal background in non-target cells. Show that CRISPR-edited genomic integration recapitulates the episomal results.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that anti-GPR64-pseudotyped lentivirus can "specifically transduce EwS cells" and that this leads to "strong anti-tumorigenic, but no adverse effects in vivo."
  - **Evidence pointer** Abstract only; location not provided
  - **Concern** No data are presented on the specificity of GPR64 expression across a panel of normal tissues and other tumor types, the efficiency of lentiviral transduction in vitro and in vivo, the biodistribution of the virus, or the quantitative extent of tumor growth inhibition. The claim of "no adverse effects" is particularly strong and requires comprehensive toxicity data.
  - **Why it matters** The safety and efficacy of the approach hinge on the selectivity of GPR64 targeting and the potency of the therapeutic effect. Off-target transduction or systemic toxicity would negate the clinical utility. The abstract provides no quantitative or qualitative evidence to support these claims.
  - **Resolution test** Provide immunohistochemistry and flow cytometry data for GPR64 expression across normal tissues and tumor panels. Show transduction efficiency in vitro and in vivo, biodistribution of the pseudotyped virus, tumor growth curves, survival data, and histopathological analysis of major organs for toxicity.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Generalizability
  - **Claim pointer** The authors claim that "similar vector designs can be applied in PAX3-FOXO1-driven ARMS, and to express immunomodulatory cytokines, such as IL-15 and XCL1."
  - **Evidence pointer** Abstract only; location not provided
  - **Concern** The abstract states that similar designs "can be applied" but provides no data on the functionality, specificity, or potency of the cassette in ARMS or for cytokine expression. It is unclear whether the enhancer elements are transferable to a different fusion protein context or whether the cytokine payloads are expressed at functionally relevant levels.
  - **Why it matters** The claim of broad applicability is a major part of the paper's significance. If the approach only works in EwS with a specific payload, its impact is substantially reduced. The abstract does not provide sufficient evidence to support the generalizability claim.
  - **Resolution test** Provide functional data in ARMS cell lines showing fusion-dependent expression of the cassette, and demonstrate that IL-15 and XCL1 are expressed at levels that elicit measurable biological effects (e.g., T cell activation or chemotaxis assays).
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Terminology
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The term "neomorphic DNA-binding" is used without a clear definition of what constitutes the neomorphic feature in this context. It is not specified whether this refers to a unique DNA sequence motif, a distinct chromatin context, or a cooperative binding mechanism.
  - **Required correction** Define the neomorphic DNA-binding property explicitly, with reference to the specific sequence or structural features that distinguish the fusion protein's binding from that of the wild-type proteins.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** In vivo model description
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract mentions "in vivo" effects but does not specify the animal model used (e.g., cell line-derived xenograft, patient-derived xenograft, orthotopic model) or the treatment regimen.
  - **Required correction** Specify the in vivo model, the route and schedule of virus administration, and the dosing of valganciclovir.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Quantification
  - **Affected element** "Strong anti-tumorigenic" effect
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The term "strong" is subjective and not quantified. No tumor growth inhibition percentage, survival extension, or effect size is provided.
  - **Required correction** Provide quantitative measures of anti-tumor efficacy, such as tumor volume reduction, time to endpoint, or survival benefit, with statistical significance.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The foundational claims of cassette specificity and potency, in vivo safety and efficacy, and generalizability are all unsupported by the abstract-level evidence. Without these data, the central thesis of the paper is not established.
- **Assessment against Nature-style criteria** 
  - Originality: High. The concept of exploiting neomorphic DNA-binding for therapeutic gene expression is novel and distinct from conventional approaches that aim to inhibit fusion proteins.
  - Scientific importance: Potentially high, given the unmet need in pediatric sarcomas and the potential applicability to other fusion-driven cancers. However, the importance is contingent on the validity and generalizability of the approach, which are not yet demonstrated.
  - Interdisciplinary readership: The work bridges oncology, gene therapy, synthetic biology, and virology, and would appeal to a broad audience if the claims are substantiated.
  - Technical soundness: Not assessable from the abstract. The lack of methodological detail and quantitative data prevents evaluation of the rigor of the experiments.
  - Readability for nonspecialists: The abstract is well-written and accessible, with clear explanations of the key concepts. However, the density of claims without supporting data may confuse readers unfamiliar with the field.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual framework is promising and the work appears substantial, but the abstract alone does not provide sufficient evidence to support the key claims. A full manuscript with detailed methods, quantitative results, and rigorous statistical analysis would be required to assess whether the case is made.

## Risk / unsupported claims

- The claim of "highly potent" and "tumor-specific" expression from the synthetic cassette is unsupported without quantitative reporter data.
- The claim of "specific transduction" of EwS cells via anti-GPR64 pseudotyping is unsupported without specificity and biodistribution data.
- The claim of "strong anti-tumorigenic, but no adverse effects in vivo" is unsupported without efficacy and toxicity data.
- The claim of applicability to PAX3-FOXO1-driven ARMS and to cytokine expression is unsupported without functional data in those contexts.
- The general statement that the approach "may be translatable to other cancers" is speculative and not supported by data presented in the abstract.