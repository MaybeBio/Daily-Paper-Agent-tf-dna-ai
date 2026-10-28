## Review setup
- **Input scope** Full manuscript text (review article), including main text, figures, and tables as described. Supplementary information mentioned but not provided.
- **Assessment boundary** Scientific content, technical soundness, clarity of claims, and alignment with stated scope. Not assessed: editorial quality, formatting, or literature completeness beyond what is cited.
- **Shared manuscript claim summary** The authors present a narrative review of AlphaFold 3 (AF3) for protein complex analysis in plant science, covering AF3's architecture improvements over AF2, input/output features, applications in plant and fungal systems, comparisons with alternative tools (ClusPro, AlphaPulldown), limitations (mutation-induced structural changes, protein dynamics, protein-DNA binding), and proposed solutions (force-field methods, MD simulations, motif-based tools). They include original test cases using AF3 predictions for NPR1-TGA3, NPR1-MYC1, BRI1-BAK1, SKOR mutants, and ORE1-DNA interactions.
- **Visible evidence base** Main text, Figures 1-5, Tables 1-3, and references cited. Supplementary Note 1, Supplementary Note 2, Figure S1A/B, and Additional file1 are referenced but not provided.
- **Missing materials affecting confidence** Supplementary figures (S1A/B), Supplementary Notes 1-2, and Additional file1 are not available. Raw AF3 prediction outputs (e.g., PAE matrices, pLDDT values, full score distributions) are not shown. Methodological details for the test cases (e.g., AF3 server version, input parameters, sequence selection criteria) are not described.

## Reviewer
- **Overall assessment** This is a useful and timely review of AF3's capabilities and limitations in the context of plant science. The authors provide a clear overview of AF3's technical advances, a practical comparison with existing tools, and a balanced discussion of limitations with proposed solutions. The inclusion of original test cases adds value, but the evidence presented is largely anecdotal and lacks systematic validation. The manuscript is well-structured and accessible to a broad biological audience, but several claims are under-supported by the data shown, and the review would benefit from more rigorous benchmarking and clearer methodological transparency.
- **Who would be interested in the results, and why** Plant biologists, structural biologists, and computational biologists interested in protein complex prediction and its applications in crop improvement, stress responses, and signalling. The review is also relevant to researchers using or developing AI-based structure prediction tools, as it highlights practical considerations for input selection, confidence scoring, and integration with experimental methods.
- **Major strengths** 1. Clear and concise explanation of AF3's architectural improvements over AF2, particularly the Pairformer and Diffusion modules, with a useful comparison table. 2. Practical guidance on input selection (e.g., domain vs. full-length sequences) supported by an original test case. 3. Balanced discussion of limitations, including mutation effects, protein dynamics, and protein-DNA binding, with concrete suggestions for complementary approaches. 4. Accessible writing style suitable for nonspecialists, with helpful figures summarising workflows and outputs.
- **Major Concerns** 
  - R1-M1: The claim that AF3 can "distinguish between known and poor protein interactions" is based on only two test cases (NPR1-TGA3 vs NPR1-MYC1), with no statistical analysis or broader benchmarking. The ipTM threshold interpretation is not validated against a larger dataset.
  - R1-M2: The conclusion that "domains are preferred over full-length sequences" is drawn from a single test case (BRI1-BAK1). The generalisability of this finding is unclear, and the authors do not discuss cases where full-length input might be necessary or preferable.
  - R1-M3: The claim that AF3 "may struggle to accurately predict mutation-induced structural changes" is based on a single visual alignment (SKOR D312N/L271P) with no quantitative metric (e.g., RMSD) or comparison to alternative methods. The evidence is insufficient to support a general limitation.
  - R1-M4: The protein-DNA binding test case (ORE1) shows that AF3 correctly identifies the DNA-binding domain but mispredicts the DNA motif. This is presented as a limitation, but the authors do not quantify the error or compare against other tools, weakening the claim that AF3 lacks "motif-specific recognition capabilities."
  - R1-M5: The comparison with ClusPro and AlphaPulldown is descriptive and lacks quantitative benchmarking. The authors do not provide side-by-side performance data on the same test cases, so the claimed advantages of AF3 are not empirically demonstrated.
- **Minor Comments** 
  - R1-m1: Figure 1 is dense and may be difficult to parse; consider simplifying or splitting into separate panels.
  - R1-m2: The text states "the predicted 3D structure which ranked the highest among the five predicted models" but does not explain how ranking is determined (e.g., by pTM, ipTM, or composite score).
  - R1-m3: The statement "AF3's ability to predict protein-DNA interaction sites has been greatly improved" is not supported by a specific citation or data in the text.
  - R1-m4: The authors mention "the downloadable database" in Figure 1 but do not describe its contents or access details in the text.
  - R1-m5: The conclusion that AF3 is "a popular choice" is not supported by usage statistics or adoption data.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5. The core claims regarding AF3's discriminative power, input preferences, and limitations are not rigorously established from the provided evidence.
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The review synthesises existing knowledge and adds a few original test cases, but these are not sufficiently systematic to constitute a novel methodological contribution.
  - Scientific importance: High for the plant science community, as AF3 adoption is growing and practical guidance is needed. However, the importance is more applied than conceptual.
  - Interdisciplinary readership: Moderate. The manuscript bridges structural biology, plant science, and computational biology, but the depth in each area is limited.
  - Technical soundness: Weak in places. The test cases are under-powered and lack quantitative validation. The comparison with other tools is not evidence-based.
  - Readability for nonspecialists: Good. The writing is clear, and figures aid understanding, though Figure 1 is overly complex.
- **Recommendation posture** Supportive if technical concerns are resolved. The review has clear value, but the original test cases and comparative claims need to be strengthened with quantitative data, broader benchmarking, and clearer methodology before the conclusions are fully convincing.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "AF3 functions as a robust complement to the experimental determination of protein interactions" based on ipTM scores distinguishing known (NPR1-TGA3) from poor (NPR1-MYC1) interactions.
- **Evidence pointer** Figure 3, Section "Distinguishing between known and poor protein interactions"
- **Concern** The conclusion is drawn from two test cases only, with no statistical analysis, no replicate predictions, and no comparison to a larger set of known interacting and non-interacting pairs. The ipTM threshold (0.6) is cited from the AF3 paper, but the authors do not demonstrate that this threshold holds for plant proteins specifically.
- **Why it matters** The claim that AF3 can reliably distinguish interacting from non-interacting proteins is central to the review's practical recommendations. Without broader validation, readers may over-trust ipTM scores for plant protein pairs, leading to incorrect biological conclusions.
- **Resolution test** Provide a systematic evaluation using a benchmark set of plant protein pairs with known interaction status (e.g., from databases like IntAct or BioGRID), reporting sensitivity, specificity, and ROC curves for ipTM-based classification. Alternatively, clearly frame the test cases as illustrative rather than conclusive.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalisability
- **Claim pointer** "Domains are preferred over full-length sequences" for AF3 input, based on higher ipTM/pTM scores for BRI1-BAK1 interacting domains.
- **Evidence pointer** Table 2, Section "Domains are preferred over full-length sequences"
- **Concern** The recommendation is based on a single protein pair. The authors hypothesise that disordered regions in full-length proteins reduce accuracy, but they do not test this across multiple complexes or protein families. It is unclear whether this finding applies to other plant protein complexes, especially those with well-folded full-length structures.
- **Why it matters** Input selection is a practical decision for users. An overgeneralised recommendation could lead to suboptimal predictions for complexes where full-length input is necessary (e.g., when domain boundaries are unknown or when inter-domain interactions are critical).
- **Resolution test** Test multiple protein complexes with known interaction interfaces, comparing full-length vs. domain-only input across a diverse set of plant proteins. Report the distribution of score differences and identify cases where full-length input is superior.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "AF3 may struggle to accurately predict mutation-induced structural changes" based on the SKOR D312N/L271P example.
- **Evidence pointer** Figure 4, Section "Predicting mutation-induced structural change"
- **Concern** The evidence is a single visual alignment with no quantitative metric (e.g., RMSD, TM-score) and no comparison to the wild-type prediction or to other methods. The authors do not show whether the low similarity is due to AF3's limitations or to the inherent flexibility of the mutant protein.
- **Why it matters** The claim that AF3 is unreliable for mutant structures is significant, as this is a common use case in plant research (e.g., studying natural variants or engineered mutations). Without quantitative evidence, the claim is not actionable.
- **Resolution test** Provide RMSD or TM-score values for the AF3-predicted mutant vs. the cryo-EM structure, and compare with predictions for the wild-type protein. Include additional mutant cases to assess consistency.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "AF3 lacks motif-specific recognition capabilities" for protein-DNA interactions, based on the ORE1 example.
- **Evidence pointer** Figure 5, Section "Predicting protein-DNA binding"
- **Concern** The authors show that AF3 mispredicts the DNA motif but do not quantify the error (e.g., number of incorrect base pairs, shift in position) or compare against other tools like RoseTTAFold2NA. The claim that AF3 lacks motif-specific recognition is not supported by a systematic analysis.
- **Why it matters** Protein-DNA binding is a key application in plant gene regulation research. A clear understanding of AF3's limitations is needed, but the current evidence is too anecdotal to guide users.
- **Resolution test** Test AF3 on a set of transcription factors with known DNA-binding motifs, quantify prediction accuracy (e.g., motif position, base-pair identity), and compare with at least one alternative tool.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative evidence
- **Claim pointer** The comparison of AF3 with ClusPro and AlphaPulldown implies AF3 is superior in applicability and user-friendliness.
- **Evidence pointer** Table 3, Section "Comparative performance with other tools"
- **Concern** The comparison is purely descriptive and does not include any quantitative performance data on the same test cases. The authors do not run ClusPro or AlphaPulldown on their examples, so the claimed advantages (e.g., broader applicability, handling of non-protein molecules) are not demonstrated.
- **Why it matters** Readers may use this comparison to choose tools. Without empirical benchmarking, the relative strengths and weaknesses are not established, and the comparison risks being misleading.
- **Resolution test** Run all three tools on a common set of plant protein complexes and report accuracy, runtime, and ease of use. Alternatively, clearly state that the comparison is based on published features, not direct benchmarking.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The figure combines multiple concepts (inputs, functions, limitations, applications) in a single panel, making it difficult to follow.
- **Required correction** Consider splitting into separate panels or using a flowchart format to improve readability.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical clarity
- **Affected element** Section "The inputs and outputs of AlphaFold 3"
- **Evidence pointer** Figure 2
- **Issue** The text does not explain how the "top-ranked" model is selected among the five predictions.
- **Required correction** Add a sentence clarifying the ranking criterion (e.g., composite score, pTM, or ipTM).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Evidence support
- **Affected element** Section "Detecting structural changes of chemical modification"
- **Evidence pointer** Section text
- **Issue** The claim that AF3 improves backbone prediction accuracy by 20% with chemical modifications is cited to Abramson et al. (2024), but the specific context (e.g., which modifications, which test set) is not described.
- **Required correction** Provide more detail on the cited result or rephrase to avoid overgeneralisation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "AlphaFold protein structure database as a downloadable resource"
- **Evidence pointer** Section text
- **Issue** The authors mention "the downloadable database" in Figure 1 but do not describe its contents, access, or limitations in the text.
- **Required correction** Add a brief description of the database's scope and how to access it.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Support for claims
- **Affected element** Conclusions
- **Evidence pointer** Section "Conclusions"
- **Issue** The statement that AF3 is "a popular choice" is not supported by any data or citation.
- **Required correction** Either provide evidence of adoption (e.g., citation counts, user statistics) or soften the claim.

## Risk / unsupported claims
- The claim that AF3 can reliably distinguish known from poor protein interactions is unsupported beyond two illustrative test cases.
- The recommendation that domain sequences are preferred over full-length sequences is not generalisable from a single example.
- The claim that AF3 struggles with mutation-induced structural changes is based on one visual alignment without quantitative metrics.
- The assertion that AF3 lacks motif-specific DNA recognition is not quantified or compared with alternatives.
- The comparative advantages of AF3 over ClusPro and AlphaPulldown are asserted without direct benchmarking.
- The statement that AF3's backbone prediction accuracy improves by 20% with chemical modifications is cited but not contextualised.
- The claim that AF3 is "a popular choice" is unsupported by data.