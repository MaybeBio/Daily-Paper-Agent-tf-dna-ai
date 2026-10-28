## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods) without figures, tables, or supplementary material
- **Assessment boundary** Scientific claims, methodological soundness, and logical coherence based solely on the provided text
- **Shared manuscript claim summary** The authors propose that non-consensus nucleotides (NCNs) in bacterial transcription factor binding sites (TFBSs) are sometimes conserved by negative selection, and that this conservation is explained by selection maintaining a specific binding energy level, implying epistatic interactions between positions within TFBSs
- **Visible evidence base** Text descriptions of multispecies conservation analysis, selection pressure estimation via 4Nes, and a shuffling experiment; references to figures and tables not visible to this reviewer
- **Missing materials affecting confidence** All figures, tables, supplementary materials, and methodological details for the shuffling procedure and energy calculations

## Reviewer
- **Overall assessment** The manuscript addresses an interesting and potentially important question in regulatory evolution: whether non-consensus nucleotides in TFBSs can be evolutionarily conserved and what mechanisms explain this conservation. The authors present a multi-pronged approach combining conservation metrics, selection pressure estimation, and a shuffling experiment. However, the provided text is insufficient to fully evaluate the robustness of the analyses. Key methodological details are missing, particularly regarding the shuffling procedure, energy calculations, and the interpretation of the 4Nes estimates. The logical connection between the observed conservation of NCNs and the proposed epistatic explanation is plausible but not fully established from the visible evidence. The manuscript would benefit from clearer presentation of the statistical methods and more explicit discussion of alternative explanations.
- **Who would be interested in the results, and why** Researchers studying transcriptional regulation, molecular evolution, and population genetics would be interested. The work addresses fundamental questions about the evolutionary constraints on regulatory sequences and the fitness landscape of TFBSs. The finding that NCNs can be under negative selection and may participate in epistatic interactions has implications for understanding regulatory evolution, predicting functional variants, and interpreting genome-wide association studies in regulatory regions.
- **Major strengths** The authors address a relatively under-explored question about the evolutionary significance of non-consensus nucleotides. The multi-species comparative approach across three bacterial families provides breadth. The consideration of multiple alternative explanations (unknown regulatory elements, TF evolution) is commendable. The use of both a conservation metric and direct selection pressure estimation provides complementary evidence.
- **Major Concerns** 
  - R1-M1: The definition and identification of consensus vs. non-consensus nucleotides is not fully operationalized in the visible text. The authors state an "empiric definition" based on frequency thresholds and palindromic structure, but the specific criteria are not provided.
  - R1-M2: The shuffling experiment, central to the epistasis claim, is described only in a figure caption reference. The procedure, controls, and interpretation are not described in the visible text.
  - R1-M3: The 4Nes estimation relies on comparing observed substitution rates to a neutral control, but the validity of the neutral control (synonymous third positions) is acknowledged as potentially non-neutral by the authors themselves, creating a logical tension.
  - R1-M4: The correlation analysis between NCN conservation and energy conservation (Figure 6) is described qualitatively. The statistical approach and the interpretation of the R ratio are not fully explained.
  - R1-M5: The authors state that results for Bacillaceae and Enterobacteriaceae are "qualitatively similar" but provide no quantitative comparison in the visible text.
- **Minor Comments**
  - R1-m1: The abstract claims "frequent conservation" but the text does not provide a quantitative measure of frequency.
  - R1-m2: The discussion of the mesa vs. crater fitness landscape is brief and the connection to the main findings is not fully developed.
  - R1-m3: The manuscript would benefit from a more explicit statement of the null hypothesis being tested in the shuffling experiment.
  - R1-m4: The authors mention "minor changes in the text" in the footnotes, which is unusual and should be clarified.
- **Technical failings that need to be addressed before the case is established** The shuffling procedure is not described in the visible text, making the central epistasis claim unevaluable. The operational definition of CN vs. NCN is incomplete. The statistical framework for comparing conservation distributions (Mann-Whitney test on D values) needs justification given potential non-independence of sites within alignments.
- **Assessment against Nature-style criteria** 
  - Originality: The question of NCN conservation is relatively novel, though related work exists on TFBS evolution. The epistatic explanation is an interesting contribution.
  - Scientific importance: Moderate to high. Understanding the evolutionary constraints on regulatory sequences is important for both basic and applied research.
  - Interdisciplinary readership: The work bridges molecular biology, evolution, and computational biology, but the presentation is likely to appeal primarily to specialists in regulatory evolution.
  - Technical soundness: Cannot be fully assessed from the visible text. The approaches are reasonable in principle, but key details are missing.
  - Readability for nonspecialists: The manuscript is generally well-written but assumes familiarity with TFBS biology and evolutionary genetics concepts. The abstract is accessible, but the methods section is dense.
- **Recommendation posture** Supportive if technical concerns are resolved. The core question is interesting and the approach is promising, but the visible evidence is insufficient to fully establish the claims. The authors should provide complete methodological details and address the concerns about the neutral control and the shuffling experiment.

## Risk / unsupported claims
- The claim that NCNs are conserved by negative selection is supported by the visible text but requires the full figures and tables for verification.
- The claim that NCNs depend epistatically on other loci is not fully supported by the visible text, as the shuffling procedure is not described.
- The claim that TF binding preferences do not change within bacterial families is based on a single example (FadR) and is overgeneralized.
- The statement that "at least some NCNs are conserved" is vague and not quantified.
- The fitness landscape analysis (mesa vs. crater) is mentioned but not described in the visible text, making the conclusion unevaluable.