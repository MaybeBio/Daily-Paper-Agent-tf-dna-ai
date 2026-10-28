## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods) as provided
- **Assessment boundary** Scientific content, experimental logic, claims versus evidence, and technical soundness based solely on the supplied text
- **Shared manuscript claim summary** The authors report variable orthogonality among three related large serine integrases (ϕC31, ϕBT1, TG1) and their recombination directionality factors (RDFs), with TG1 integrase being the most active and selective, ϕC31 integrase the least selective, and structural predictions from AlphaFold2-multimer suggesting conserved RDF binding surfaces with integrase-driven specificity.
- **Visible evidence base** Results sections describing sequence alignments, AlphaFold2-multimer structural predictions, in vivo recombination assays using fluorescent reporters, and in vitro recombination assays with purified proteins; figures referenced (Figures 1–8) but not directly viewable
- **Missing materials affecting confidence** Figures and their underlying data (gels, fluorescence images, quantifications, statistical analyses) are not provided; plasmid construction details are incomplete; AlphaFold2 model confidence metrics (pLDDT, PAE) are not reported; raw numerical data for recombination extents are absent

## Reviewer
- **Overall assessment** This manuscript addresses a relevant question in the synthetic biology and phage biology fields, namely the degree of orthogonality among closely related integrase–RDF pairs. The experimental design is logical and the inclusion of both in vivo and in vitro assays strengthens the study. However, the absence of the actual data figures and statistical details limits the ability to fully evaluate the claims. The finding that TG1 integrase is highly selective while ϕC31 is promiscuous is potentially useful, but the mechanistic interpretation relies heavily on AlphaFold2 predictions without experimental validation. The manuscript is technically sound in its approach but requires additional data presentation and some clarification before the conclusions can be fully supported.
- **Who would be interested in the results, and why** Researchers in synthetic biology, particularly those developing genetic switches, logic gates, and genome engineering tools using serine integrases. The work also has relevance for phage biologists studying integrase–RDF co-evolution and specificity determinants. The comparative analysis of three related integrases provides practical guidance for tool selection.
- **Major strengths** 1. Systematic comparison of three related integrase–RDF pairs using both in vivo and in vitro assays. 2. Inclusion of integrase–RDF fusion constructs to probe the effect of covalent linkage on specificity. 3. Use of AlphaFold2-multimer to generate testable structural hypotheses. 4. Practical implications for synthetic biology applications, particularly the identification of TG1 as a clean-switching candidate.
- **Major Concerns** 
  - R1-M1: The core claim of "variable orthogonality" is presented qualitatively without quantitative thresholds or statistical comparisons. The manuscript states percentages for some reactions (e.g., 76%, 54%, 92% for integrative recombination; 76%, 29%, 94% for excisive recombination with cognate RDFs) but does not provide error bars, replicates, or statistical tests. Without these, the reader cannot assess whether differences between integrases are significant.
  - R1-M2: The AlphaFold2-multimer predictions are used to support a mechanistic claim about specificity determinants, but no confidence metrics (pLDDT, PAE) are reported. The statement that "specificity is determined more by the integrase than the RDF" is inferred from sequence conservation of the binding surface, but this is not directly tested experimentally. The manuscript acknowledges this is a prediction, but the Discussion treats it as a relatively firm conclusion.
  - R1-M3: The in vitro excisive recombination data for ϕC31 integrase show 35–44% conversion of attP x attB in the presence of RDF, indicating incomplete inhibition. The manuscript attributes this to equilibrium effects, but alternative explanations (e.g., RDF concentration, binding affinity) are not experimentally addressed. The claim that ϕC31 is "least selective" is based on this partial inhibition, but the mechanism remains unclear.
  - R1-M4: The effect of covalent integrase–RDF fusion is described for ϕBT1 integrase, where non-cognate RDFs become more effective when fused. However, the manuscript does not provide a mechanistic explanation for this observation, and it is unclear whether this is due to increased local concentration, conformational effects, or altered stoichiometry. This is a potentially interesting finding but is left under-interpreted.
- **Minor Comments** 
  - R1-m1: The manuscript states that TG1-RDF activity "has not been demonstrated in vivo or in vitro" prior to this study, but the Results section does not clearly indicate whether the authors are the first to demonstrate this. This should be clarified.
  - R1-m2: The Discussion mentions "the plot if Figure 7a" (typo, should be "of"). The manuscript should be carefully proofread for such errors.
  - R1-m3: The Materials and Methods section for in vivo recombination assays describes the ϕC31 system in detail but is less specific about how the ϕBT1 and TG1 substrates were constructed. More detail on cloning strategies would improve reproducibility.
  - R1-m4: The manuscript does not report the number of biological or technical replicates for any of the assays. This information is essential for evaluating the reliability of the reported percentages.
  - R1-m5: The statement that "TG1 integrase is the most active among the three" is based on in vitro data, but the in vivo data show near-complete recombination for all three integrases. The manuscript should reconcile these observations more explicitly.
- **Technical failings that need to be addressed before the case is established** 
  - R1-M1 (lack of quantitative data and statistics)
  - R1-M2 (AlphaFold2 confidence metrics not reported)
  - R1-M3 (mechanism of incomplete inhibition not addressed)
  - R1-M4 (fusion effect not mechanistically interpreted)
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The study provides a comparative analysis of three integrase–RDF pairs, which is useful but not conceptually novel. The use of AlphaFold2 for this purpose is timely but not groundbreaking.
  - Scientific importance: Moderate. The findings have practical implications for synthetic biology tool selection, but the mechanistic insights are limited and largely speculative.
  - Interdisciplinary readership: Limited. The work will primarily appeal to synthetic biologists and phage biologists; the broader impact is modest.
  - Technical soundness: The experimental approaches are appropriate, but the lack of quantitative data and statistical analysis weakens the technical rigor.
  - Readability for nonspecialists: The manuscript is generally well-written and accessible, though some sections (e.g., the AlphaFold2 discussion) assume familiarity with structural biology concepts.
- **Recommendation posture** Supportive if technical concerns are resolved. The core observations are potentially valuable, but the manuscript requires quantitative data, statistical analysis, and clearer mechanistic interpretation before the claims can be fully supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor
- **Claim pointer** The manuscript claims "variable orthogonality" among the three integrase–RDF pairs and reports specific percentages for recombination extents (e.g., 76%, 54%, 92% for integrative; 76%, 29%, 94% for excisive).
- **Evidence pointer** Results sections "Recombination activities of ϕC31, ϕBT1, and TG1 integrases" and "Effects of RDFs on the recombination activities of ϕC31, ϕBT1, and TG1 integrases"; Figures 5 and 6
- **Concern** The manuscript reports recombination extents as single percentages without error bars, replicate numbers, or statistical comparisons. It is impossible to determine whether the observed differences between integrases (e.g., 76% vs. 54% for ϕC31 vs. ϕBT1 integrative recombination) are biologically meaningful or within experimental noise.
- **Why it matters** The central claim of the paper is that orthogonality varies among the three pairs. Without quantitative support, this claim is not established. The reader cannot assess the reliability or significance of the reported differences.
- **Resolution test** Provide replicate data (at least three independent experiments) with error bars and appropriate statistical tests (e.g., ANOVA or t-tests) for all reported recombination extents. State the number of replicates in figure legends and methods.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural prediction validity
- **Claim pointer** The manuscript states that "AlphaFold2-multimer predicts very similar structural interactions between each cognate integrase–RDF pair" and that "specificity is determined more by the integrase than the RDF."
- **Evidence pointer** Results section "Sequence alignment and predicted structures of ϕC31, ϕBT1, and TG1 integrases and their recombination directionality factors (RDFs)"; Figures 4 and 8
- **Concern** No confidence metrics (pLDDT, PAE) are reported for the AlphaFold2-multimer models. The claim that the RDF binding surface is more conserved than the integrase binding surface is based on sequence conservation analysis, but this is not experimentally validated. The manuscript acknowledges the models are predictions, but the Discussion treats the specificity conclusion as relatively firm.
- **Why it matters** Structural predictions are used to support a mechanistic claim about specificity determinants. Without confidence metrics or experimental validation (e.g., mutagenesis), the claim remains speculative and cannot be evaluated.
- **Resolution test** Report pLDDT and PAE scores for the models, or provide experimental validation (e.g., mutagenesis of the predicted binding interface) to support the specificity claim. Alternatively, soften the language to clearly indicate the speculative nature of the conclusion.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic interpretation
- **Claim pointer** The manuscript states that for ϕC31 integrase, 35–44% of attP x attB substrate is converted in the presence of RDF, and attributes this to "weak directionality for the attR x attL reaction" and equilibrium effects.
- **Evidence pointer** Results section "Effects of RDFs on the recombination activities of ϕC31, ϕBT1, and TG1 integrases"; Figure 6
- **Concern** The incomplete inhibition of ϕC31 integrase by its cognate RDF is attributed to equilibrium effects, but alternative explanations (e.g., insufficient RDF concentration, weak binding affinity, or partial activity of the RDF) are not experimentally addressed. The manuscript does not provide titration experiments or binding affinity measurements to support the equilibrium interpretation.
- **Why it matters** The claim that ϕC31 is "least selective" is based on this partial inhibition. If the incomplete inhibition is due to experimental conditions rather than intrinsic properties, the conclusion could be misleading.
- **Resolution test** Perform RDF titration experiments to show that inhibition is concentration-dependent and reaches a plateau consistent with equilibrium. Alternatively, measure binding affinities between ϕC31 integrase and each RDF to support the interpretation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic interpretation
- **Claim pointer** The manuscript reports that covalent fusion of non-cognate RDFs to ϕBT1 integrase increases their effectiveness in activating excisive recombination and inhibiting integrative recombination.
- **Evidence pointer** Results section "Effects of RDFs on the recombination activities of ϕC31, ϕBT1, and TG1 integrases"; Figures 5 and 6
- **Concern** The observation that fusion increases the effectiveness of non-cognate RDFs is reported but not mechanistically explained. The manuscript does not discuss whether this is due to increased local concentration, conformational changes, or altered stoichiometry. This is a potentially interesting finding that is left under-interpreted.
- **Why it matters** Understanding why fusion alters specificity could provide insights into the determinants of integrase–RDF recognition and inform the design of synthetic fusions for biotechnology applications.
- **Resolution test** Provide a mechanistic hypothesis and design experiments to test it (e.g., varying linker length, measuring binding affinities of fused versus unfused proteins, or performing structural analysis of the fusion).

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction and Results
- **Evidence pointer** Results section "Effects of RDFs on the recombination activities of ϕC31, ϕBT1, and TG1 integrases"
- **Issue** The manuscript states that TG1-RDF activity has not been previously demonstrated, but it is unclear whether the authors are claiming to be the first to demonstrate this. This should be clarified.
- **Required correction** Explicitly state whether this is the first demonstration of TG1-RDF activity and cite the relevant prior work if applicable.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Language quality
- **Affected element** Discussion
- **Evidence pointer** Discussion section, paragraph on tunable switches
- **Issue** The text contains a typo: "the plot if Figure 7a" should be "the plot of Figure 7a". The manuscript should be proofread for similar errors.
- **Required correction** Correct the typo and perform a thorough proofreading pass.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Materials and Methods
- **Evidence pointer** Materials and Methods section "in vivo recombination reactions"
- **Issue** The construction of ϕBT1 and TG1 substrate plasmids is described only briefly ("Similar plasmid substrates for ϕBT1 and TG1 integrases were made by cloning the corresponding att sites"). More detail is needed for reproducibility.
- **Required correction** Provide full details of the cloning strategy, including primer sequences, restriction sites, and vector backbones.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results
- **Evidence pointer** Results sections on recombination activities; Figures 5 and 6
- **Issue** The number of replicates for each assay is not reported. This is essential for evaluating the reliability of the data.
- **Required correction** State the number of independent experiments and technical replicates in the figure legends and methods.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results and Discussion
- **Evidence pointer** Results section "Recombination activities of ϕC31, ϕBT1, and TG1 integrases"; Discussion section
- **Issue** The in vivo data show near-complete recombination for all three integrases, while the in vitro data show differences (e.g., 76%, 54%, 92%). The manuscript does not explicitly reconcile these observations or discuss why in vivo conditions may mask differences.
- **Required correction** Add a brief discussion of the potential reasons for the discrepancy between in vivo and in vitro results.

## Risk / unsupported claims
- The claim that "specificity is determined more by the integrase than the RDF" is based solely on AlphaFold2 predictions and sequence conservation analysis, without experimental validation. This is a speculative claim that is not fully supported by the data presented.
- The claim that ϕC31 integrase is "least selective" is based on incomplete inhibition data (35–44% conversion) without a mechanistic explanation or titration experiments to rule out experimental artifacts.
- The statement that TG1 integrase is "the most active" is based on in vitro data, but the in vivo data show near-complete recombination for all three integrases, making the claim context-dependent and potentially misleading without further qualification.
- The manuscript does not provide quantitative data (error bars, statistics) for any of the reported recombination extents, making it impossible to assess the significance of the observed differences.