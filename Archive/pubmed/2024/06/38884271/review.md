## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, data availability, and supplementary figure legends.
- **Assessment boundary** Scientific validity, technical soundness, and interpretation of the presented data. No assessment of editorial fit or journal-specific scope.
- **Shared manuscript claim summary** The authors propose that the histone methyltransferase ASH1L protects cis-regulatory elements (enhancers and promoters) from UV-induced cyclobutane pyrimidine dimer (CPD) formation, in addition to its previously described role in stimulating nucleotide excision repair. This protection is attributed to ASH1L binding at H3K4me3/H3K27ac-marked elements, with molecular dynamics simulations suggesting that an AT-hook motif alters the geometry of adjacent cytosines to disfavor dimerization. The authors further link loss of this protection to increased C→T transitions at enhancers in ASH1L-mutated skin cancers.
- **Visible evidence base** ChIP-seq data for ASH1L CTD, H3K4me1, H3K4me3, H3K27ac; CPD HS damage-seq in UV-treated U2OS cells (wildtype vs ASH1L–/–); CPD, 6–4 PP, and cisplatin damage-seq in NH1F cells; molecular dynamics simulations of an ASH1L fragment bound to a 50-bp enhancer sequence; cancer genomics analysis using cBioPortal data.
- **Missing materials affecting confidence** The manuscript text does not include the actual figures or supplementary figures, which are essential for evaluating the magnitude and statistical robustness of the reported effects. The specific genomic coordinates of the enhancer used for MD simulations are not provided. The methods for the cancer mutation analysis are described only briefly, and the criteria for defining "ASH1L-mutated" versus "ASH1L-intact" samples are not fully detailed. The statistical comparison in Figure 7 is described but the effect sizes and confidence intervals are not reported in the text.

## Reviewer
- **Overall assessment** This manuscript presents a novel and potentially important dual role for ASH1L in protecting cis-regulatory elements from UV-induced DNA damage. The combination of genomics, epigenetics, and computational modeling is ambitious and the conclusions are generally well-aligned with the presented evidence. However, the strength of the central claim, that ASH1L directly reduces CPD formation at C-containing dipyrimidines, rests heavily on the interpretation of damage-seq data and on computational predictions that are not experimentally validated. The manuscript would be substantially strengthened by additional validation, including a more detailed description of the statistical methods and effect sizes, and by addressing the potential confounding effects of chromatin accessibility and DNA sequence composition.
- **Who would be interested in the results, and why** Researchers in the fields of DNA repair, genome stability, chromatin biology, and skin cancer genetics would find these results of interest. The work connects a chromatin-modifying enzyme to lesion formation, a topic of broad relevance to understanding how chromatin context influences mutagenesis. The potential link to melanoma mutation patterns also extends the audience to cancer genomics.
- **Major strengths**
  1. The study addresses a timely and important question: how chromatin-associated factors influence the initial formation of UV-induced DNA lesions, not just their repair.
  2. The use of multiple complementary approaches, including ChIP-seq, damage-seq, and molecular dynamics, provides a multi-layered view of the phenomenon.
  3. The observation that ASH1L protects specifically C-containing dipyrimidines, which are mutagenic hotspots, is a novel and mechanistically interesting finding.
  4. The inclusion of a cancer genomics analysis provides a potential translational relevance to the findings.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The claim that ASH1L reduces CPD formation at C-containing dipyrimidines in enhancers is based on the comparison of damage-seq profiles between wildtype and ASH1L–/– cells.
  - **Evidence pointer** Results, Figures 2 and 3; Supplementary Figures S2, S3, S5.
  - **Concern** The central conclusion relies on the normalization of damage-seq data. The authors state that CPD counts were normalized using TMM and divided by naked DNA controls, but the details of this normalization, particularly how the naked DNA control was generated and whether it was matched for sequence composition, are not fully described. The observed "dip" in CPD formation at enhancer centers could be influenced by differences in chromatin accessibility, nucleosome positioning, or transcription factor occupancy, which are not controlled for. The claim of protection is also based on a comparison of CPD levels at specific dipyrimidine categories, but the statistical significance of the differences between wildtype and ASH1L–/– cells at these specific dinucleotides is not reported in the text.
  - **Why it matters** If the normalization is not robust, the observed reduction in CPD formation could be an artifact of the data processing rather than a true biological effect. The distinction between protection from lesion formation and reduced lesion detection due to chromatin context is critical for the validity of the main claim.
  - **Resolution test** The authors should provide a detailed description of the normalization procedure, including how the naked DNA control was prepared and whether it was used to correct for sequence-specific biases. They should also report the effect sizes and confidence intervals for the differences in CPD levels at C-containing dipyrimidines between wildtype and ASH1L–/– cells, and ideally demonstrate that the effect is independent of chromatin accessibility (e.g., by using ATAC-seq data or by controlling for nucleosome occupancy).
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The molecular dynamics simulations are used to propose a mechanism whereby the AT-hook motif of ASH1L alters the geometry of adjacent cytosines to disfavor CPD formation.
  - **Evidence pointer** Results, Figure 6; Supplementary Figure S7.
  - **Concern** The simulations are based on a predicted structure from RF2NA of a 440-amino acid fragment of ASH1L bound to a 50-bp DNA sequence. The choice of this specific fragment and DNA sequence is not justified, and the simulations are not validated by any experimental data, such as mutagenesis of the AT-hook or biophysical measurements of DNA binding. The relevance of the simulated conformational changes to the in vivo situation is unclear, as the full-length ASH1L protein is much larger and may interact with DNA in a more complex manner.
  - **Why it matters** The proposed mechanism is a key part of the paper's narrative. If the simulations are not robust or are not representative of the actual ASH1L-DNA interaction, the mechanistic claim is unsupported.
  - **Resolution test** The authors should provide a rationale for the choice of the ASH1L fragment and DNA sequence. They should also experimentally test the role of the AT-hook, for example by expressing an ASH1L mutant lacking this motif and measuring CPD formation at enhancers. Alternatively, they could use a more rigorous computational approach, such as enhanced sampling simulations, to confirm the observed conformational changes.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The cancer genomics analysis is used to support the biological relevance of the findings, claiming that ASH1L-mutated melanomas have higher C→T transitions at enhancers.
  - **Evidence pointer** Results, Figure 7.
  - **Concern** The analysis is based on a small number of ASH1L-mutated samples (140) compared to a larger number of wildtype samples (1373). The authors do not report the total number of mutations in each group, the distribution of mutation types, or the statistical test used to compare the proportions. The use of FANTOM5 enhancers, which are not cell-type-specific, may dilute the signal. The analysis is also confounded by the fact that ASH1L mutations may be associated with other genomic alterations that affect mutation rates.
  - **Why it matters** The cancer data is presented as a validation of the biological importance of the findings. If the analysis is not statistically robust or is confounded, it weakens the translational relevance of the study.
  - **Resolution test** The authors should provide a more detailed description of the statistical analysis, including the test used, the effect size, and the confidence intervals. They should also consider using a more specific set of enhancers (e.g., melanocyte-specific) and controlling for potential confounders such as total mutation burden.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Abstract
  - **Evidence pointer** Abstract
  - **Issue** The abstract is dense and uses specialized terminology (e.g., "cis-regulatory elements," "cyclobutane pyrimidine dimers") without defining them for a broader audience.
  - **Required correction** Consider adding brief definitions or context for these terms to make the abstract more accessible.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods, "Molecular modelling"
  - **Evidence pointer** Methods, "Molecular modelling"
  - **Issue** The description of the molecular dynamics simulations is brief. The force field parameters, the length of the simulations, and the analysis of the trajectories are not described in sufficient detail to be reproducible.
  - **Required correction** Provide more details on the simulation setup, including the software version, the number of replicates, and the convergence criteria.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Results, "ASH1L guards enhancers against C–containing dipyrimidines"
  - **Evidence pointer** Results, Figure 3
  - **Issue** The authors state that the protection is specific to C-containing dipyrimidines, but the analysis of the other dipyrimidine types (TT, TC, CT) is not shown in the text. It is unclear if the lack of protection at TT is statistically significant.
  - **Required correction** Show the data for all dipyrimidine types and report the statistical comparison between wildtype and ASH1L–/– cells for each.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Scientific importance
  - **Affected element** Discussion
  - **Evidence pointer** Discussion
  - **Issue** The discussion of the potential evolutionary advantage of ASH1L-mediated protection is speculative and not directly supported by the data.
  - **Required correction** Consider tempering this speculation or providing additional context from the literature.

## Risk / unsupported claims
- The claim that ASH1L directly protects against CPD formation at C-containing dipyrimidines is not fully supported without a more detailed description of the normalization and statistical analysis of the damage-seq data.
- The mechanistic claim based on molecular dynamics simulations is unsupported by experimental validation.
- The cancer genomics analysis is presented as supportive but is not described in sufficient detail to assess its robustness.
- The claim that the protection is specific to enhancers and promoters, and not other genomic regions, is based on the analysis of a limited set of genomic features and may not be generalizable.