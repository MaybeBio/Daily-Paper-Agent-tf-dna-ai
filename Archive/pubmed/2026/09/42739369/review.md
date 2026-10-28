## Review setup
- **Input scope** Full manuscript text (review article)
- **Assessment boundary** Scientific content, structure, claims, and evidence as presented in the provided text
- **Shared manuscript claim summary** The review argues that deep learning models applied to plant genomic sequences can predict components of the cis-regulatory code, but that prediction, physical contact, and causal function must be distinguished. It surveys architectures (CNN, Transformer, graph), applications (TF binding, chromatin accessibility, expression, variant prioritisation, design), and evaluation practices, concluding that current evidence supports predictive utility but not broad causal or cross-context generalisation.
- **Visible evidence base** The manuscript text includes descriptions of published studies, tables referenced but not shown, figures referenced but not shown, and a reference list not provided. No raw data, code, or supplementary materials were available.
- **Missing materials affecting confidence** Figures 1–4, Tables 1–2, the full reference list, and any supplementary information were not provided. These are essential for assessing the accuracy of the reported comparisons, the provenance of the resource table, and the validity of the architecture summaries.

## Reviewer
- **Overall assessment** This is a well-organised, cautious, and conceptually clear review of a rapidly moving field. The authors consistently distinguish prediction from causality, computational attribution from biological function, and statistical dependency from physical contact. This discipline is commendable and rare in the literature. The manuscript is likely to be useful to plant biologists and computational researchers seeking an entry point into deep learning for cis-regulatory analysis. However, the review is largely descriptive rather than critical. It does not provide a quantitative synthesis of model performance, does not identify which architectures win on which tasks, and does not offer a clear set of recommendations for practitioners. The absence of the figures and tables in the provided material makes it impossible to verify the accuracy of the comparative claims. The review would be strengthened by a more evaluative stance, explicit performance comparisons where available, and a clearer articulation of open problems.
- **Who would be interested in the results, and why** Plant molecular biologists interested in gene regulation and non-coding variation; computational biologists working on regulatory genomics; breeders using sequence-based prediction for trait improvement; and developers of genomic foundation models who need to understand plant-specific challenges such as polyploidy, transposable elements, and the absence of CTCF.
- **Major strengths** The conceptual framework distinguishing prediction, contact, and causality is applied consistently throughout. The review covers a broad range of architectures and applications without oversimplifying. The treatment of evaluation design, including leakage, holdout types, and independent testing, is sophisticated and practically useful. The inclusion of plant-specific constraints, such as transposable element mapping bias and polyploidy, is a valuable contribution. The authors are appropriately cautious about overclaiming, particularly regarding foundation models and generative design.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality
  - **Claim pointer** The review states that "Plant-specific benchmarks and pangenome-aware representations will be most informative when they yield predictions that can be tested experimentally" and implies that current benchmarks are inadequate.
  - **Evidence pointer** Section 6.1, Section 4.4, Table 2 (not provided)
  - **Concern** The review repeatedly criticises the field for lacking standardised benchmarks and independent evaluation, but it does not itself provide a synthesis of what is known. Without the tables and figures, the reader cannot see which models were compared, on which datasets, with what results. The claim that benchmarks are inadequate is plausible but not demonstrated in the text provided.
  - **Why it matters** A review that identifies a problem without providing a structured account of the evidence base is less useful than one that does. The reader is left without a clear picture of the state of the field.
  - **Resolution test** Provide Tables 1 and 2 and Figures 1–4, and add a section that explicitly compares model performance across tasks, datasets, and evaluation designs, even if the comparison is qualitative.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The review states that "long-range model outputs" should be interpreted as "predicted statistical dependencies unless contact assays and independent enhancer–gene tests support a stronger interpretation."
  - **Evidence pointer** Section 2.3, Section 3.3
  - **Concern** This is a sensible caution, but the review does not explain how a reader or practitioner would determine whether a given model output is a statistical dependency or something more. The distinction is asserted but not operationalised.
  - **Why it matters** Without operational guidance, the distinction remains abstract and may not influence how readers interpret specific model outputs.
  - **Resolution test** Add a short subsection or box that provides concrete criteria or examples for when a long-range prediction can be interpreted as contact or function.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The review concludes that "the next gains are likely to come from representative datasets with accurate biological and technical metadata, leakage-resistant evaluation and transparent separation of internal, external-dataset and independent-team testing."
  - **Evidence pointer** Section 7, Section 6.1
  - **Concern** This is a reasonable conclusion, but it is generic. The review does not identify which specific datasets, species, or tasks are most in need of attention, nor does it propose a concrete roadmap for the field.
  - **Why it matters** A review that ends with generic recommendations is less actionable than one that prioritises specific gaps.
  - **Resolution test** Add a short "Priorities" subsection that lists the top three to five concrete actions for the field, with justification.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Section 2.2
  - **Evidence pointer** Section 2.2, paragraph 1
  - **Issue** The sentence "AssayingThe assay for transposase-accessible chromatin using sequencing (ATAC-seq) instead profiles transposase-accessible chromatin without antibodies" contains a typographical error ("AssayingThe").
  - **Required correction** Correct to "The assay for transposase-accessible chromatin using sequencing (ATAC-seq) instead profiles transposase-accessible chromatin without antibodies."
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Section 5.2
  - **Evidence pointer** Section 5.2, paragraph 2
  - **Issue** The sentence "A reference-versus-alternative score can prioritise a candidate regulatory variant but A reference-versus-alternative score can prioritise a candidate regulatory variant but does not establish causality" contains a duplicated phrase.
  - **Required correction** Remove the duplicated phrase.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section 4.2
  - **Evidence pointer** Section 4.2, paragraph 2
  - **Issue** The review mentions PlantCAD2 as published in Cell Genomics in 2026 but does not provide a citation number in the text provided.
  - **Required correction** Ensure the full citation is included in the reference list.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 6.3
  - **Evidence pointer** Section 6.3, paragraph 1
  - **Issue** The term "digital twin" is introduced without a definition or example, which may confuse readers unfamiliar with the concept.
  - **Required correction** Add a brief definition or example of a digital twin in the context of plant biology.
- **Technical failings that need to be addressed before the case is established** The manuscript cannot be fully assessed without Figures 1–4 and Tables 1–2. The figures are referenced as central to the conceptual framework and architecture comparisons, and Table 2 is described as a comprehensive comparison of models. Without these, the review's comparative claims are unverifiable. The typographical errors in Sections 2.2 and 5.2 should be corrected. The duplicated phrase in Section 5.2 is a clear error that must be fixed.
- **Assessment against Nature-style criteria**  
  *Originality*: The conceptual framework is not entirely new, but the consistent application of the prediction/contact/causality distinction to plant regulatory genomics is a useful contribution. The review does not present novel data or a novel synthesis.  
  *Scientific importance*: The topic is important and timely. The review correctly identifies key limitations in the field, but it does not provide a quantitative or structured account of the evidence, which limits its impact.  
  *Interdisciplinary readership*: The review is accessible to both plant biologists and computational researchers, but it may be too detailed for a general audience and not detailed enough for specialists. The balance is reasonable for a review in a specialised journal.  
  *Technical soundness*: The technical descriptions are accurate as far as they can be checked, but the missing figures and tables prevent full verification. The evaluation of model performance is not quantitative.  
  *Readability for nonspecialists*: The writing is clear and well-structured. The use of jargon is appropriate and generally explained. The typographical errors are minor but should be fixed.
- **Recommendation posture** Supportive if technical concerns are resolved. The review is conceptually sound and likely to be useful, but the missing figures and tables must be provided for full assessment, and the typographical errors must be corrected. The authors should consider adding a more evaluative synthesis of model performance to increase the review's impact.

## Risk / unsupported claims
- The claim that "plant-specific benchmarks and pangenome-aware representations will be most informative when they yield predictions that can be tested experimentally" is a reasonable opinion but is not supported by specific evidence in the text provided.
- The statement that "the evidence supports a clear distinction between prediction and causality, computational attribution and biological function, and long-range sequence dependency and physical contact" is a summary of the authors' interpretation, but the evidence base for this distinction is not fully presented in the text provided.
- The claim that "generalisation is constrained by uneven species and genotype sampling, sparse single-cell data, transposable-element mapping and reference bias, and polyploidy" is plausible but is not supported by specific examples or data in the text provided.
- The description of PlantCAD2 as "published in Cell Genomics in 2026" cannot be verified without the reference list.
- The claim that "the resources considered here do not provide a single standardised benchmark spanning all plant cis-regulatory tasks" is plausible but is not demonstrated with specific examples in the text provided.