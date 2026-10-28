## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and acknowledgments
- **Assessment boundary** Scientific validity of claims regarding AlphaFold2 and AlphaFold-Multimer performance on leucine zipper dimer prediction, based on the provided manuscript text and referenced figures/tables
- **Shared manuscript claim summary** The authors use FosB and JunD as a case study to show that AlphaFold2 and AlphaFold-Multimer predict high-confidence leucine zipper dimer structures even for dimer pairs that are known not to form in vivo due to electrostatic repulsion, and that standard confidence metrics (pLDDT, PAE, ipTM) do not reliably distinguish probable from improbable dimer interfaces
- **Visible evidence base** Text descriptions of results, references to Figures 1-7, Supplementary Figures 1-6, Table 1, Table 2, and Methods section
- **Missing materials affecting confidence** Actual figures and supplementary figures not provided; Table 1 and Table 2 contents not shown; specific numerical data for pLDDT, PAE, ipTM scores only partially reported in text; no raw AlphaFold output files or statistical analyses

## Reviewer
- **Overall assessment** This manuscript presents a timely and relevant case study on the limitations of AlphaFold2 and AlphaFold-Multimer for predicting coiled-coil dimer interfaces, specifically leucine zippers. The authors demonstrate that high confidence scores do not guarantee biologically plausible dimer structures, using the well-characterized FosB/JunD system. The work is conceptually clear and addresses an important gap in understanding AI-based structure prediction tools. However, the manuscript has several technical and presentational weaknesses that need to be addressed before the conclusions can be fully supported. The lack of quantitative comparisons, incomplete reporting of confidence metrics, and absence of statistical analysis weaken the strength of the claims. The study is potentially valuable for the structural biology and AI communities, but the current evidence base is insufficient to fully establish the central thesis.

- **Who would be interested in the results, and why** Structural biologists using AlphaFold for protein-protein interaction prediction, computational biologists developing or benchmarking AI structure prediction tools, researchers studying transcription factor networks and coiled-coil proteins, and the broader community interested in the practical limitations of AI-based methods in biology. The results are particularly relevant to those who use AlphaFold-Multimer to screen potential dimer partners or design synthetic coiled-coil systems.

- **Major strengths** The study addresses a practically important question about the reliability of AlphaFold confidence metrics. The choice of FosB/JunD as a test case is well justified given the extensive experimental data on their dimerization behavior. The authors use multiple complementary metrics (pLDDT, PAE, ipTM) and structural alignments to assess prediction quality. The inclusion of a synthetic peptide designed to be energetically unfavorable is a clever control experiment. The discussion appropriately contextualizes the findings within the broader limitations of AI-based structure prediction.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that AlphaFold-Multimer produces high-confidence structures for the FosB homodimer despite it being known not to form in vivo, and that confidence metrics do not distinguish probable from improbable dimers
- **Evidence pointer** Results section, Figures 2-4, Table 1, location not provided for specific numerical values
- **Concern** The central claim relies on comparing confidence scores across dimer pairs, but the manuscript does not provide a systematic quantitative comparison. The text reports mean pLDDT values for the L-zip regions (97.7, 95.1, 94.4) but does not report standard deviations, ranges, or statistical tests to determine whether these differences are significant. Similarly, ipTM scores are described qualitatively ("strikingly different") without reporting exact values for all constructs. The PAE analysis is described narratively but no quantitative thresholds or comparative statistics are provided.
- **Why it matters** Without quantitative evidence and statistical analysis, the reader cannot assess whether the observed differences in confidence scores are meaningful or within the noise of the prediction method. The claim that AlphaFold-Multimer "cannot differentiate" between probable and improbable dimers requires demonstrating that the confidence metrics are statistically indistinguishable for the different dimer pairs, or that the differences are not predictive of biological plausibility.
- **Resolution test** Provide a table with mean, standard deviation, and range for pLDDT, PAE, and ipTM scores for all dimer constructs (full-length and L-zip only). Perform appropriate statistical tests (e.g., ANOVA or non-parametric equivalents) to compare confidence metrics across dimer types. Report exact ipTM values for all constructs, including the synthetic peptide pair.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that the relaxation algorithms used by AlphaFold2 and AlphaFold-Multimer (Amber ff99SB force field) resolve steric clashes but do not take into account destabilizing electrostatic interactions
- **Evidence pointer** Discussion section, Methods section
- **Concern** This claim is presented as an explanation for the observed results, but no direct evidence is provided to support the assertion that the relaxation step fails to account for electrostatics. The authors do not test this hypothesis by, for example, running AlphaFold without relaxation or comparing relaxed versus unrelaxed structures. The claim is plausible but speculative, and it is presented as a definitive explanation rather than a hypothesis.
- **Why it matters** The manuscript's explanatory framework depends on this mechanistic claim. If the relaxation step does account for electrostatics in some way, or if the failure to discriminate dimers arises from a different aspect of the algorithm, the interpretation would change. The authors should either provide direct evidence for this mechanism or soften the claim to reflect its hypothetical nature.
- **Resolution test** Perform a control experiment where AlphaFold-Multimer predictions are generated with and without relaxation for the FosB homodimer and compare the resulting structures and confidence scores. Alternatively, cite specific literature evidence that directly demonstrates this limitation of the Amber ff99SB force field in the context of AlphaFold.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors extend their findings from FosB/JunD to "other human L-zip pairs" and state that "all the different L-zip pairs that we ran were predicted to form L-zip dimers by AlphaFold-Multimer"
- **Evidence pointer** Results section, Figure 6, Table 2
- **Concern** The manuscript mentions four additional protein pairs tested, but provides no details on which pairs were chosen, how they were selected, or what experimental evidence exists for their inability to dimerize. The results are summarized in a single figure with no quantitative data reported in the text. The generalizability claim is therefore based on a very small and poorly described sample.
- **Why it matters** The authors aim to show a general phenomenon, not just a single case study. Without detailed information on the additional pairs and their experimental validation, the reader cannot assess whether the sample is representative or biased. The claim of generalizability is not supported by the evidence presented.
- **Resolution test** Provide a table listing the four additional protein pairs, their UniProt IDs, the experimental evidence for their non-dimerization, and the quantitative confidence metrics (pLDDT, PAE, ipTM) for each predicted dimer. Discuss the selection criteria for these pairs and acknowledge the limitations of the small sample size.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological clarity
- **Claim pointer** The authors describe a synthetic peptide pair designed to be "as energetically unfavourable as possible" based on coupling energies from Vinson et al. (2002; 2006)
- **Evidence pointer** Results section, Figure 7, Supplementary Figure 1, Table 2
- **Concern** The design of the synthetic peptide is described only briefly. The authors state that e and g positions were filled with repelling negatively charged residues, but do not provide the full sequence, the specific coupling energies used, or the rationale for the choice of residues beyond "all Glu." The first iteration contained all Glu residues, but it is unclear if subsequent iterations were tested and what those were.
- **Why it matters** The synthetic peptide experiment is a key control that demonstrates the limits of AlphaFold-Multimer. Without full details of the peptide design, the experiment cannot be reproduced or fully evaluated. The choice of "all Glu" is a specific design decision that may not represent the most energetically unfavorable configuration possible.
- **Resolution test** Provide the full amino acid sequences of the synthetic peptides, the coupling energy calculations used for design, and a clear description of the design rationale. If multiple peptide variants were tested, report results for all of them.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, statement section
- **Issue** The abstract contains a separate "statement" paragraph that repeats the main finding in slightly different words. This is redundant and could be streamlined.
- **Required correction** Merge the statement into the main abstract text or remove it, as the abstract already conveys the key message.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 1
- **Evidence pointer** Introduction, Figure 1
- **Issue** The text refers to Figure 1 panels A-F but does not describe the content of each panel in sufficient detail. The reader cannot follow the structural descriptions without seeing the figure.
- **Required correction** Add a brief description of each panel in the figure legend or in the text where the figure is first referenced.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods section
- **Evidence pointer** Methods section, AlphaFold computations
- **Issue** The methods state that AlphaFold was accessed via Galaxy Australia with default settings, but do not specify the version of AlphaFold-Multimer or the exact parameters used for multimer prediction (e.g., number of recycles, model presets).
- **Required correction** Provide the specific version of AlphaFold-Multimer and any non-default parameters, or state explicitly that all parameters were default.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results section, electrostatic surface potentials
- **Evidence pointer** Results section, Figure 5
- **Issue** The authors state that the FosB homodimer contains "two negatively charged surfaces in close proximity" but do not quantify the electrostatic potential or provide a comparison with the heterodimer. The visual inspection of surface potentials is subjective.
- **Required correction** Provide quantitative measures of surface electrostatic potential (e.g., calculated using APBS) for the relevant regions of each dimer and report the values in the text or a table.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion mentions that AlphaFold3 is available in beta and that limitations remain, but does not provide any specific comparison or reference to AlphaFold3 performance on similar systems.
- **Required correction** Either expand on the AlphaFold3 comparison with relevant citations or remove the statement to avoid unsupported speculation.

- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of quantitative comparison and statistical analysis of confidence metrics) and R1-M2 (unsupported mechanistic claim about relaxation and electrostatics) are the primary technical failings. R1-M3 (inadequate description of additional protein pairs) also needs to be addressed to support the generalizability claim.

- **Assessment against Nature-style criteria**  
  - Originality: The manuscript addresses a known but under-documented issue with AlphaFold-Multimer, specifically the failure to account for electrostatic repulsion in coiled-coil dimers. The use of a well-characterized biological system and a designed synthetic peptide adds originality, but the core observation is not entirely novel.  
  - Scientific importance: The findings are important for the structural biology community, as they highlight a practical limitation of a widely used tool. The implications for transcription factor network modeling and synthetic design are significant.  
  - Interdisciplinary readership: The topic bridges structural biology, computational biology, and AI applications in biology. The writing is accessible to nonspecialists, though some technical details (e.g., coupling energies) may require background knowledge.  
  - Technical soundness: The experimental approach is reasonable, but the lack of quantitative data and statistical analysis weakens the technical rigor. The mechanistic explanation for the observed limitations is not directly tested.  
  - Readability for nonspecialists: The manuscript is generally well-written and clear, with helpful context on AP-1 transcription factors and AlphaFold. However, the results section relies heavily on figure descriptions that are not fully self-contained.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses a relevant and timely question, and the core observation is likely correct. However, the current evidence base is insufficient to fully establish the claims. The authors must provide quantitative confidence metrics with statistical analysis, test the proposed mechanistic explanation, and expand the description of additional protein pairs. If these issues are addressed, the manuscript would be suitable for publication in a specialized structural biology or computational biology journal.

## Risk / unsupported claims
- The claim that AlphaFold-Multimer's relaxation step does not account for electrostatic interactions is unsupported by direct evidence in the manuscript.
- The generalizability claim based on four additional protein pairs is unsupported due to lack of details on selection criteria and experimental validation.
- The statement that AlphaFold3 retains the same limitations is speculative and not supported by data or citations.
- The assertion that the synthetic peptide pair is "as energetically unfavourable as possible" is not quantitatively justified.
- The claim that low ipTM scores for full-length constructs are due to intrinsically unstructured regions is a hypothesis that is not directly tested.