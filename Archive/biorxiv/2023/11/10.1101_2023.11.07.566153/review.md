## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, supplementary file descriptions)
- **Assessment boundary** Scientific content, methodological soundness, reproducibility, and claims as presented in the provided text. No external validation of data, code, or supplementary materials was performed.
- **Shared manuscript claim summary** The authors present a comprehensive comparative analysis of computational tools for plant transcription factor binding region (TFBR) discovery, covering three stages: peak calling, TFBR identification, and motif discovery. They report that most existing tools are not maintained, contain bugs, and fail in cross-species applications, with PTFSpot and PTF-Vāc emerging as the only reliable solutions for plant-specific and cross-species TFBR and motif discovery.
- **Visible evidence base** Text descriptions of methods and results, references to figures (Figures 1-11), tables (Tables 1-4), and supplementary materials (S1-S5). No actual data, code, or supplementary files were provided for inspection.
- **Missing materials affecting confidence** All figures, tables, supplementary materials, code repositories, and raw data. The manuscript references these extensively but they were not included in the provided scope, preventing independent verification of quantitative claims.

## Reviewer
- **Overall assessment** This manuscript addresses a genuinely important gap in plant genomics: the lack of reliable, cross-species computational tools for TFBR discovery. The authors have undertaken a substantial benchmarking effort across 19 tools and three computational stages, and they report practical contributions including bug fixes and corrected scripts. However, the manuscript as presented has significant structural and scientific weaknesses. The methods section is incomplete, lacking essential details on data processing, evaluation protocols, and statistical analyses. The results are presented as narrative summaries without supporting data, making quantitative claims unverifiable. The discussion, while thoughtful, contains overgeneralizations and some claims that exceed the evidence presented. The writing is often informal and imprecise, with grammatical errors and unclear phrasing throughout. The manuscript would benefit from substantial revision, including a complete methods section, presentation of actual results with statistical rigor, and a more measured discussion that acknowledges limitations.

- **Who would be interested in the results, and why** Plant molecular biologists, computational biologists, and bioinformaticians working on gene regulation, transcription factor biology, and genome annotation would be the primary audience. The comparative benchmarking data and the identification of PTFSpot and PTF-Vāc as robust tools would be practically useful for researchers selecting computational methods for TFBR discovery in non-model plant species. The documentation of software bugs and the release of corrected scripts is a community service that would be appreciated by practitioners. The discussion of genomic variability between plants and animals and its implications for tool transferability is conceptually interesting and would appeal to researchers studying genome evolution and regulatory divergence.

- **Major strengths**
  1. The manuscript addresses a real and underappreciated problem: the poor transferability of animal-derived computational tools to plant genomes, which have different genomic architectures and higher variability.
  2. The scope of the benchmarking is broad, covering three distinct computational stages (peak calling, TFBR identification, motif discovery) and 19 tools, which provides a comprehensive landscape of the field.
  3. The authors did not merely evaluate tools but actively debugged them and released corrected scripts, which is a tangible and useful contribution to the community.
  4. The identification of PTFSpot and PTF-Vāc as superior tools for plant-specific and cross-species applications is a clear, actionable finding.
  5. The discussion of why cross-species transfer fails, grounded in TF structural variability and genomic differences, provides a conceptual framework that goes beyond simple benchmarking.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and methodological completeness
- **Claim pointer** The manuscript claims to provide a comprehensive comparative analysis of 19 tools across three datasets, with quantitative performance metrics.
- **Evidence pointer** Methods section, Results section, Figures 6-10, Tables 1-4, Supplementary Tables S1-S8
- **Concern** The methods section is critically incomplete. It lacks essential details on how datasets were constructed, how tools were configured, how hyperparameter optimization was performed, what computational resources were used, and how performance metrics were calculated. The results section references figures and tables that were not provided, making it impossible to verify any of the quantitative claims. For example, the claim that PTFSpot achieved 96.14% accuracy on Dataset B is presented without any confidence intervals, statistical tests, or comparison of variance across tools. The description of the benchmarking protocol is insufficient to allow replication.
- **Why it matters** Without a complete methods section and access to the actual results data, the scientific claims cannot be evaluated or reproduced. This is a fundamental requirement for any benchmarking study, as the value of such work depends entirely on the rigor and transparency of the methodology.
- **Resolution test** The authors must provide a complete methods section detailing dataset construction, tool configuration, evaluation protocol, and statistical analysis. All figures and tables must be included with full data. The code and data must be made available for independent verification.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validity of cross-species conclusions
- **Claim pointer** The manuscript claims that "barring PTFSpot, almost all of these studied tools appeared failing to deliver" in cross-species applications, and that PTFSpot is "the most reliable tool for cross-specific and practical application to identify TFBRs in plants."
- **Evidence pointer** Results section, Figure 8D, Supplementary Table S4 Sheet 3
- **Concern** The cross-species evaluation appears to be based on only five common TFs between Arabidopsis thaliana and Zea mays. This is a very small sample size from which to draw such strong conclusions about the general superiority of PTFSpot. The manuscript does not report how these five TFs were selected, whether they are representative of the broader TF population, or whether the results would hold for other TF families or other plant species pairs. The claim that PTFSpot works for "unseen TFs and species" is presented as a conclusion but the evidence for this is not shown in the provided text.
- **Why it matters** The central practical recommendation of the manuscript is that researchers should use PTFSpot for cross-species TFBR discovery. This is a strong claim that requires robust evidence across multiple species pairs, TF families, and data types. A five-TF, two-species comparison is insufficient to support such a definitive recommendation.
- **Resolution test** The authors should expand the cross-species evaluation to include more TFs and more species pairs, and should report the results in full. They should also discuss the limitations of their cross-species test and temper their conclusions accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Conceptual framing of TFBS versus TFBR
- **Claim pointer** The manuscript argues that "the problem of transcription factor binding region discovery is closely knitted with motif discovery, where the enriched motifs are assumed to be the binding site. While the fact is that both the problem are separate" and proposes redefining TFBS as "binding region marker motifs."
- **Evidence pointer** Introduction, Results section, Discussion section
- **Concern** The conceptual distinction between TFBR and TFBS is presented as a novel insight, but this distinction is already well established in the field. The proposal to rename TFBS as "binding region marker motifs" is a semantic change that does not add scientific value and may create confusion, as the term TFBS is widely used and understood. The manuscript does not provide a rigorous operational definition of what constitutes a "marker motif" versus a TFBS, nor does it explain how this redefinition would change practice.
- **Why it matters** The manuscript positions this redefinition as a key contribution, but it is not clear that this is a meaningful scientific advance. Overstating the novelty of well-known concepts undermines the credibility of the manuscript.
- **Resolution test** The authors should either provide a substantive operational framework for how the TFBR/TFBS distinction changes tool development or usage, or remove this claim of novelty and instead frame the discussion as a clarification of existing concepts.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of findings
- **Claim pointer** The manuscript states that "most of the existing tools have centered around the motifs and used them as the marker of positive datasets and involved negative datasets devoid of them completely," and that this is a key reason for poor performance.
- **Evidence point** Results section, Discussion section
- **Concern** This claim is presented as a general finding, but the manuscript does not provide a systematic analysis of how each of the 19 tools constructed their positive and negative datasets. The claim appears to be based on the authors' reading of the tools' documentation rather than on a controlled experiment. The manuscript also does not test whether alternative negative dataset construction strategies would improve tool performance, which would be the logical next step given this hypothesis.
- **Why it matters** The manuscript makes a causal claim about why tools fail, but does not provide direct evidence for this causality. Without a controlled comparison of different negative dataset strategies, the claim remains speculative.
- **Resolution test** The authors should either provide a systematic analysis of each tool's dataset construction methodology, or conduct a controlled experiment varying negative dataset construction to test their hypothesis.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and precision of writing
- **Affected element** Abstract, Introduction, Discussion
- **Evidence point** Multiple sections
- **Issue** The manuscript contains numerous grammatical errors, awkward phrasings, and informal expressions. Examples include "a range of of published software tools," "the area which had started with merely reporting the motifs and calling it TFBS," and "It is a worth millions of dollars question indeed!" These issues detract from the professional tone expected in a scientific manuscript.
- **Required correction** The manuscript should be carefully edited for grammar, style, and precision. Informal expressions should be replaced with professional scientific language.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure and table accessibility
- **Affected element** All figures and tables
- **Evidence point** Figures 1-11, Tables 1-4
- **Issue** The figures and tables are referenced extensively but were not provided in the manuscript text. Based on the descriptions, some figures appear to be highly complex (e.g., Figure 5 with panels A-I, Figure 8 with panels A-D). Without seeing them, it is not possible to assess whether they are legible and effectively communicate the results.
- **Required correction** The authors should ensure that all figures are of high quality, legible, and accompanied by clear captions that allow them to be understood independently of the main text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout
- **Evidence point** Multiple sections
- **Issue** The manuscript uses "TFBS" and "TFBR" in ways that are sometimes interchangeable and sometimes distinct. The proposed redefinition of TFBS as "binding region marker motifs" is introduced but not consistently applied throughout the text.
- **Required correction** The authors should define their terminology clearly at the outset and use it consistently throughout the manuscript.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Supplementary material organization
- **Affected element** Supplementary file descriptions
- **Evidence point** Supplementary Tables S1-S8, Supplementary Materials S1-S5
- **Issue** The supplementary material is extensive but the descriptions provided in the text are brief. It is not clear how the supplementary tables and materials relate to each other or to the main figures.
- **Required correction** The authors should provide a clear index or guide to the supplementary materials, explaining what each file contains and how it supports the main text.

- **Technical failings that need to be addressed before the case is established**
  1. Incomplete methods section preventing replication (R1-M1)
  2. Insufficient evidence for the strong cross-species claims (R1-M2)
  3. Unsupported causal claims about why tools fail (R1-M4)
  4. No statistical analysis of performance differences between tools
  5. No discussion of potential biases in the benchmarking datasets
  6. No analysis of computational resource requirements, which is practically important for tool selection

- **Assessment against Nature-style criteria**
  - **Originality**: The manuscript is not highly original in its conceptual framing, as the TFBR/TFBS distinction is known. However, the systematic benchmarking of 19 tools across three stages, with a focus on plant-specific challenges, is a useful and relatively novel contribution. The documentation of software bugs and the release of corrected scripts is a practical contribution not commonly found in the literature.
  - **Scientific importance**: The problem addressed is important. Plant genomes are diverse and complex, and the field lacks reliable cross-species tools. The finding that most tools fail in cross-species applications, and the identification of PTFSpot as an exception, has practical significance. However, the importance is somewhat diminished by the limited scope of the cross-species validation.
  - **Interdisciplinary readership**: The manuscript would appeal to a niche audience of computational biologists and plant molecular biologists. It is unlikely to attract broad interdisciplinary interest, as the content is highly specialized and the presentation is not accessible to nonspecialists.
  - **Technical soundness**: The technical soundness cannot be fully assessed because the methods are incomplete and the results data are not provided. The narrative descriptions suggest a reasonable approach, but the lack of detail and statistical rigor is a significant concern.
  - **Readability for nonspecialists**: The manuscript is not written for nonspecialists. It assumes significant prior knowledge of TF biology, machine learning, and bioinformatics. The writing is also not sufficiently clear and precise for a general scientific audience.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses an important problem and has the potential to be a useful resource for the plant genomics community. However, the incomplete methods, unverifiable results, and overgeneralized conclusions prevent the case from being made. The authors should be encouraged to revise the manuscript substantially, providing full methodological detail, presenting actual results with statistical analysis, and tempering their claims to match the evidence. If these revisions are made successfully, the manuscript could become a valuable contribution.