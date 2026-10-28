## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific validity, methodological soundness, clarity, and support of claims based solely on the supplied text
- **Shared manuscript claim summary** The authors present JEDII, a template-based method that predicts both DNA-binding residues and the cognate DNA sequence for a given protein structure by superimposing hydrogen-bonding donor and acceptor atoms. They report high accuracy on a curated dataset (PDNA-285) and benchmark comparisons against existing methods.
- **Visible evidence base** Abstract, Introduction, Methods (sections 1-4), Results (sections 1-2), Discussion, Conclusion, and references to figures and tables (Figure 1-5, Tables 1-7, Supplementary Table 1, Appendix 19)
- **Missing materials affecting confidence** Figures and tables are referenced but not provided; Supplementary Table 1 and Appendix 19 are not included; no code or data availability statement; no detailed algorithmic pseudocode or parameter settings beyond brief descriptions

## Reviewer
- **Overall assessment** The manuscript addresses an important gap in DNA-protein interaction prediction by attempting to unify residue-level and sequence-level predictions within a single template-based framework. The core idea, relying on structural conservation of hydrogen-bonding patterns, is biologically plausible and potentially valuable. However, the evidence presented is insufficient to fully establish the method's superiority or generalizability. Key limitations include incomplete reporting of benchmark details, lack of statistical significance testing, and unclear handling of ambiguous cases. The method's performance on the PDNA-129 dataset, where it underperforms GraphBind, raises questions about its robustness, particularly for structures solved by electron microscopy. The manuscript would benefit from clearer methodological descriptions, additional validation, and a more critical discussion of failure modes.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein-DNA interactions, structural biologists studying transcription factors and DNA-binding proteins, and researchers developing template-based or structure-based prediction tools. The method's potential extension to RNA-protein complexes could also interest RNA biologists.
- **Major strengths** The manuscript addresses a novel integrative problem, combining two traditionally separate prediction tasks. The template-based approach using hydrogen-bonding pattern conservation is conceptually elegant and mechanistically grounded. The authors test robustness across multiple scenarios (unbound conformations, absence of close homologs, protein models), which is commendable. The comparison with existing methods on multiple benchmark datasets provides a useful context for evaluating performance.
- **Major Concerns** 
  - R1-M1: The manuscript claims JEDII outperforms most methods across four datasets, but the reported metrics are not accompanied by statistical significance tests or confidence intervals. Without such analysis, it is unclear whether observed differences are meaningful or within noise.
  - R1-M2: The PDNA-129 dataset includes 27 electron microscopy structures with average resolution 4.4 Å, yet the template database is limited to X-ray structures with resolution better than 3 Å. The authors attribute JEDII's underperformance to this resolution mismatch, but no analysis is provided to quantify the impact or explore potential remedies.
  - R1-M3: The DNA sequence prediction evaluation relies heavily on similarity scores, but the definition of "correct" prediction varies across comparisons (e.g., highest-frequency nucleotide matching). The manuscript does not clarify how ambiguous positions in PWMs are handled, which could inflate reported accuracy.
  - R1-M4: The method's dependence on template availability is acknowledged but not systematically analyzed. The authors report reduced performance with a 40% non-redundant template set, but do not investigate how performance scales with template diversity or size.
  - R1-M5: The clash and contact criteria for model filtering are described briefly, but the thresholds (1.5 Å for clashes, 3.5 Å for contacts) are not justified. The potential for false positives or negatives in model selection is not discussed.
- **Minor Comments** 
  - R1-m1: The abstract states "62% accuracy" for DNA sequence prediction, but the Results section reports an average similarity score of 0.62. The relationship between these two metrics should be clarified.
  - R1-m2: The manuscript mentions "three iterations at 90, 60 and 40% identity" for clustering, but the rationale for this multi-step approach is not explained.
  - R1-m3: The description of the query overlap percentage formula is incomplete; the variables n and t are defined but the formula itself is not shown.
  - R1-m4: The Discussion claims the method "could be extended to RNA-protein complexes," but no preliminary evidence or feasibility analysis is provided.
  - R1-m5: The manuscript uses "recoognized" (typo) in the Methods section, and "of of" in the same section; proofreading is needed.
- **Technical failings that need to be addressed before the case is established** 
  - Lack of statistical significance testing for performance comparisons
  - Incomplete reporting of benchmark dataset compositions and evaluation protocols
  - No analysis of failure cases or systematic error patterns
  - Unclear handling of ambiguous positions in PWM-based evaluations
  - No sensitivity analysis for key parameters (clash threshold, contact distance, query overlap cutoff)
- **Assessment against Nature-style criteria** 
  - Originality: The integrative approach is novel, but the underlying principles (template-based prediction, hydrogen-bond conservation) are not entirely new. The originality lies in combining residue and sequence prediction, which is a meaningful contribution.
  - Scientific importance: The problem is relevant, and a reliable method could have broad applications. However, the current evidence does not convincingly demonstrate a major advance over existing tools, particularly given the underperformance on PDNA-129.
  - Interdisciplinary readership: The topic bridges structural biology, bioinformatics, and molecular biology. The manuscript is generally accessible, but some methodological details are dense and may limit broader readability.
  - Technical soundness: The approach is logically coherent, but several technical aspects are under-specified (e.g., formula for query overlap, handling of ambiguous PWM positions). The lack of statistical rigor weakens the technical case.
  - Readability for nonspecialists: The abstract and introduction are clear, but the methods and results sections assume familiarity with structural biology and prediction benchmarks. Figures and tables, if provided, would likely aid comprehension.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea has merit, and the authors have done substantial validation work. However, the manuscript currently does not fully establish the method's reliability or superiority, and several methodological gaps need to be addressed before the claims can be accepted.

## Risk / unsupported claims
- The claim that JEDII "outperformed most methods over all these data sets" is not supported by statistical testing and may overstate the findings.
- The assertion that the method "could be extended to RNA-protein complexes" is speculative and not backed by any preliminary data.
- The statement that "the accuracy of predictions is correlated with the query overlap (0.84) and the sequence identity (0.60)" is based on correlation coefficients but no significance levels or confidence intervals are provided.
- The claim that JEDII is "robust" for unbound conformations is based on a single dataset (HOLO-APO 82) without analysis of variability across protein families or conformational change magnitudes.
- The reported "94% accuracy" for DNA-binding residue prediction on PDNA-285 is not contextualized with baseline or random expectation, making it difficult to assess its practical value.