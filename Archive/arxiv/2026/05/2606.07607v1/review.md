## Review setup
- **Input scope** Full manuscript text (preprint, arXiv:2606.07607v1)
- **Assessment boundary** Scientific claims, methodology, evidence quality, and reporting standards as presented in the provided text. No external verification of data, code, or cited literature was performed.
- **Shared manuscript claim summary** The authors argue that interpretable machine learning (IML) evaluation in genomics relies on anecdotal, cherry-picked validation. They support this with a large-scale literature mapping study (3,575 papers) and an empirical audit on transcription factor (TF) binding prediction using three foundation models and five IML methods, showing inconsistency, unfaithfulness, and biological misalignment.
- **Visible evidence base** Main text (Sections 1-6), Appendix A (prompt details), Appendix B (agreement rates), Appendix C (predictive performance), Appendix D (per-model/per-TF disagreement), Appendix E (faithfulness), Appendix F (biological alignment). Figures 1-4 and Tables 1-3 are referenced but not fully visible in the provided text.
- **Missing materials affecting confidence** Full figures and tables (only referenced, not shown). Details of the literature search query (only described qualitatively). Exact hyperparameters, training details, and fine-tuning protocols for the three foundation models. Full details of the LLM extraction prompt (only abbreviated descriptions provided). Statistical significance testing for the reported differences.

## Reviewer
- **Overall assessment** This is a timely and important position paper that addresses a critical gap in genomic interpretability research. The authors combine a large-scale mapping study with a well-designed empirical audit to demonstrate that current IML evaluation practices are inadequate. The core argument is compelling and the proposed tiered guidelines are practical and actionable. However, the manuscript has several technical weaknesses that need to be addressed before the case is fully established, particularly regarding the completeness of the empirical audit, the robustness of the LLM-based extraction, and the generalizability of the findings beyond the specific TF binding task.
- **Who would be interested in the results, and why** Computational biologists, machine learning researchers working on interpretability, and genomics researchers who use deep learning models for regulatory genomics. The paper is also relevant for method developers in the broader interpretable ML community, as it highlights domain-specific evaluation challenges. The proposed guidelines could influence reporting standards in genomics journals.
- **Major strengths** 1) The paper addresses a significant and under-appreciated problem in a high-impact field. 2) The combination of a broad literature mapping with a focused empirical audit is a powerful approach. 3) The empirical audit is well-designed with thoughtful selection of TFs as stress tests (positive controls, compositional bias, resolution). 4) The proposed tiered guidelines are practical and could be readily adopted. 5) The paper is clearly written and accessible to a broad audience.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (LLM extraction reliability), R1-M2 (completeness of empirical audit), R1-M3 (generalizability), R1-M4 (statistical rigor).
- **Assessment against Nature-style criteria** **Originality:** High. The paper identifies a specific, systemic problem in genomic IML evaluation and provides both evidence and a solution framework. The combination of a meta-analysis with a controlled empirical audit is novel. **Scientific importance:** High. The findings have direct implications for how genomic interpretability results are reported and interpreted, potentially affecting a large number of studies. **Interdisciplinary readership:** Moderate to high. The topic is relevant to both ML and genomics communities, but the specific focus on TF binding may limit broader appeal. The writing is accessible to both audiences. **Technical soundness:** Moderate. The empirical audit is well-designed, but the reliance on LLM-based extraction without full validation details, and the lack of statistical significance testing, weaken the technical foundation. **Readability for nonspecialists:** Good. The paper is well-structured and explains concepts clearly, though some familiarity with deep learning and genomics is assumed.
- **Recommendation posture** Supportive if technical concerns are resolved. The core message is important and the proposed guidelines are valuable. However, the manuscript requires revisions to strengthen the evidence base and address the technical concerns outlined below.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology / Evidence quality
- **Claim pointer** The mapping study claims that 86% of papers use a single IML method, and that validation is largely subjective and cherry-picked.
- **Evidence pointer** Section 2.1, Appendix A, Appendix B, Table 2
- **Concern** The entire mapping study relies on LLM-based extraction (gemini-3-flash-preview) from full-text papers. While the authors report a 98% agreement rate on a random sample of 100 papers, the details of this validation are insufficient. The per-category agreement rates in Table 2 are referenced but not shown in the provided text. More critically, the prompt details in Appendix A are abbreviated, making it impossible to assess potential biases in the extraction process. For example, how was "successful instance" defined and extracted? How were subjective validation methods classified? The self-reflection stage is described but its effectiveness is not quantified separately.
- **Why it matters** The mapping study is the foundation for the paper's central claim that the field relies on anecdotal evaluation. If the extraction methodology is biased or unreliable, the entire premise of the paper is weakened. The 98% agreement rate, while high, is based on a single annotator and a small sample, and the potential for systematic errors in the LLM's interpretation of complex scientific text is not adequately addressed.
- **Resolution test** Provide the full prompt text, the complete per-category agreement table, and a detailed analysis of the types of errors the LLM made. Ideally, have a second annotator independently code a subset of papers to assess inter-annotator reliability. Show examples of the LLM's extraction vs. the gold standard for each category.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology / Evidence quality
- **Claim pointer** The empirical audit claims to demonstrate that IML methods (1) yield contradictory explanations, (2) fail to localize known regulatory motifs, and (3) fail to reflect the model's internal decision process.
- **Evidence pointer** Section 3, Figures 2-4, Tables 1 and 3, Appendices D-F
- **Concern** The empirical audit is described in the text, but the actual figures and tables are not visible in the provided manuscript. This makes it impossible to evaluate the strength of the evidence. For example, Figure 2b shows average Spearman correlations below 0.4, but the range and variance across sequences are not described. Figure 4a shows median Perception scores, but the full distributions are only in the appendix. More importantly, the choice of the "Perception score" as the sole metric for biological alignment is questionable. It measures overlap with a known motif, but does not account for the possibility that the model may have learned alternative, valid regulatory mechanisms (e.g., indirect binding, cooperative interactions) that are not captured by the single motif annotation.
- **Why it matters** The empirical audit is the primary evidence for the paper's claims about the unreliability of IML methods. Without seeing the full data, it is impossible to assess whether the conclusions are robust. The Perception score may be too simplistic a metric to capture the complexity of regulatory genomics, and the lack of alternative metrics (e.g., enrichment of known motif instances, comparison to random expectation) weakens the case.
- **Resolution test** Provide the full figures and tables. Include statistical significance testing for the differences between methods and TFs. Add additional metrics for biological alignment, such as motif enrichment analysis or comparison to a null model. Discuss the limitations of the Perception score and justify its use as the primary metric.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability / Scope
- **Claim pointer** The paper argues that genomic model research must move beyond anecdotal evaluation, implying that the findings from the TF binding audit generalize to other genomic tasks.
- **Evidence pointer** Section 3, Section 6
- **Concern** The empirical audit is limited to a single task (TF binding prediction) and a specific set of five TFs. While the authors chose these TFs as "stress tests," it is unclear whether the findings generalize to other genomic tasks such as gene expression prediction, splicing, or chromatin accessibility. The choice of TFs, while thoughtful, may not represent the full diversity of regulatory mechanisms. For example, TFs with very strong, well-defined motifs (like CTCF) may be easier for IML methods to recover than TFs with weak or degenerate motifs.
- **Why it matters** The paper's central argument is that the field as a whole must change its evaluation practices. If the empirical evidence is only from one task, the generalizability of the claim is limited. The authors should either provide evidence from multiple tasks or temper their claims to be specific to TF binding.
- **Resolution test** Add a discussion of the generalizability of the findings, or ideally, include a small-scale audit on a second task (e.g., gene expression) to demonstrate that the issues are not task-specific.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The paper claims that IML methods "often" yield contradictory explanations, "fail" to localize motifs, and "fail" to reflect model decisions.
- **Evidence pointer** Section 3, Figures 2-4
- **Concern** The manuscript does not report any statistical significance testing for the observed differences between IML methods or between TFs. For example, is the difference in Perception score between CTCF and GATA1 statistically significant? Is the correlation between ISM and LIME significantly different from zero? Without such testing, it is difficult to distinguish real effects from noise, especially given the large number of sequences (88,000) and the potential for multiple testing issues.
- **Why it matters** The paper's claims are strong and prescriptive. To support such claims, the evidence must be statistically robust. The lack of significance testing weakens the conclusions and makes it difficult for readers to assess the reliability of the findings.
- **Resolution test** Add appropriate statistical tests (e.g., permutation tests, bootstrap confidence intervals) for the key comparisons. Report effect sizes and confidence intervals, not just point estimates.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / Reporting
- **Affected element** Section 2.1, literature search query
- **Evidence pointer** Section 2.1
- **Issue** The exact search query used for the Web of Science search is not provided. The authors state they applied a query to abstracts but do not give the query string.
- **Required correction** Provide the full search query in the main text or appendix to allow reproducibility.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodology / Reporting
- **Affected element** Section 3, dataset construction
- **Evidence pointer** Section 3, Table 1
- **Issue** The details of negative sample generation are not described. How were negative sequences (non-binding regions) selected? Were they matched for GC content or other confounding factors? This is critical for the compositional bias tests (SP1, TBP).
- **Required correction** Describe the negative sample generation procedure in detail, including any matching or filtering steps.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity / Terminology
- **Affected element** Section 3.2, faithfulness metrics
- **Evidence pointer** Section 3.2
- **Issue** The terms "deletion-AUC" and "insertion-AUC" are used, but the exact definition of AUC in this context is not fully explained. Is it the area under the probability curve as a function of the number of masked/restored positions?
- **Required correction** Provide a clear mathematical definition of the AUC metrics used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scope / Completeness
- **Affected element** Section 4, guidelines
- **Evidence pointer** Section 4
- **Issue** The guidelines are presented as a "tiered framework," but the criteria for moving between tiers are not explicitly defined. When should a practitioner consider the "moderate" tier sufficient versus the "high" tier?
- **Required correction** Add explicit decision criteria or a decision tree to help practitioners determine which tier of evaluation is appropriate for their context.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity / Presentation
- **Affected element** Section 5, alternative views
- **Evidence pointer** Section 5
- **Issue** The discussion of alternative views is thorough but could benefit from a more explicit acknowledgment of the cost-benefit trade-off. The authors argue for rigorous evaluation but do not fully address the computational and financial costs of such evaluation, particularly for smaller labs.
- **Required correction** Add a brief discussion of the practical costs of the proposed guidelines and how they might be scaled to different resource settings.

## Risk / unsupported claims
- The claim that "the vast majority of studies (86%) employed only a single IML method" is based on LLM extraction, and the reliability of this specific statistic is not fully established without the full validation details.
- The claim that IML methods "fail to localize known regulatory motifs" is based on the Perception score, which may not capture all valid regulatory mechanisms. The paper does not rule out the possibility that the models learned alternative, biologically meaningful features.
- The claim that the findings from the TF binding audit generalize to other genomic tasks is not supported by direct evidence.
- The paper does not provide statistical significance testing for the key empirical results, making it difficult to assess the robustness of the claims.
- The paper does not provide a full description of the literature search query, limiting the reproducibility of the mapping study.