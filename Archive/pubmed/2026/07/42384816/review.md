## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, materials and methods, and supplementary materials description
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and interpretation as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors report identification of previously unrecognized Scm3/HJURP orthologs across metazoan lineages, including zebrafish and C. elegans, using remote homology detection, structural prediction, and functional validation. They further propose that Drosophila CAL1 is a true ortholog rather than a functional analog, and that rapid sequence divergence has obscured broad conservation of centromeric chaperone machinery.
- **Visible evidence base** Abstract, full introduction, full results section, full discussion, materials and methods, supplementary figure/table legends as referenced in text
- **Missing materials affecting confidence** Supplementary figures S1-S12, tables S1-S4, data S1-S3, movies S1, and all figure images are referenced but not provided. This limits verification of structural predictions, phylogenetic analyses, microscopy data, and quantitative results.

## Reviewer
- **Overall assessment** This manuscript presents a compelling and potentially field-advancing claim: that Scm3/HJURP orthologs are broadly conserved across Metazoa, including in lineages previously thought to lack them, and that Drosophila CAL1 is a true ortholog. The combination of remote homology detection, structural prediction, and functional genetics is appropriate and powerful. However, the strength of the central claims depends critically on evidence presented in supplementary materials that were not available for review. The functional validation in zebrafish and C. elegans is a major strength, but the genetic evidence in C. elegans is incomplete, and the evolutionary analyses require closer scrutiny regarding statistical support and potential artifacts. The manuscript is well-written and the argument is logically structured, but several technical concerns must be resolved before the case is fully established.

- **Who would be interested in the results, and why** Cell biologists studying centromere specification and kinetochore assembly; evolutionary biologists interested in deep homology and rapid sequence divergence; chromosome segregation researchers using model organisms; and the broader chromatin biology community. The work provides new tools (identified orthologs in zebrafish and C. elegans) and a generalizable bioinformatic pipeline for finding deeply diverged orthologs.

- **Major strengths** 1) The combination of multiple computational approaches (PSI-BLAST, HMM, HHpred, AlphaFold) with functional validation is rigorous and appropriate for the question. 2) The identification and validation of drHJURP in zebrafish and NEFR-1 in C. elegans fills genuine gaps in the field. 3) The use of a "living fossil" genome (coelacanth) as an evolutionary stepping stone is clever and well-justified. 4) The functional data in C. elegans, particularly the auxin-degradation experiments, directly address the question of essentiality. 5) The manuscript is clearly written and the logic is easy to follow even for nonspecialists.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that NEFR-1 is essential for embryonic cell division and CENPAHCP-3 deposition, based on auxin-mediated depletion experiments.
- **Evidence pointer** Results section "C. elegans nefr-1 encodes a bona fide HJURP ortholog"; Figure 5
- **Concern** The auxin-degradation experiments are described but the quantitative data are not presented in the text. The authors state that embryos "almost invariantly failed to hatch" following NEFR-1 depletion, but no numbers, statistical tests, or control comparisons are provided in the visible text. The claim of essentiality requires quantitative support, including demonstration that the AID tag does not itself impair function and that depletion is efficient and specific.
- **Why it matters** The essentiality claim is central to establishing NEFR-1 as the functional C. elegans HJURP ortholog. Without quantitative evidence, the reader cannot assess the strength of this conclusion or compare it to prior work suggesting C. elegans may use alternative mechanisms.
- **Resolution test** Provide quantitative hatching rates with sample sizes, statistical comparisons to controls, western blot or immunofluorescence evidence of depletion efficiency, and a rescue experiment or demonstration that the AID-tagged allele is functional in the absence of auxin.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Phylogenetic support
- **Claim pointer** The authors claim that phylogenetic analyses support monophyletic origin of Scm3/HJURP orthologs across Metazoa, including the placement of CAL1 within this clade.
- **Evidence pointer** Results sections "HJURP orthologs are broadly conserved across deuterostomes, including teleosts" and "Drosophila CAL1 is a true HJURP ortholog"; Figures 1B, 3E, 4B, S4A, S7, S8A
- **Concern** The phylogenetic trees are described as "generally congruent" with species trees, but no statistical support values (bootstrap, posterior probability) are mentioned in the text. Given the extreme sequence divergence claimed, the phylogenetic signal may be weak, and the placement of highly divergent sequences (especially CAL1) could be sensitive to alignment and model choice. The authors do not describe how alignment uncertainty or compositional heterogeneity was handled.
- **Why it matters** The claim that CAL1 is a true ortholog rather than a convergent analog rests on phylogenetic evidence. If the phylogenetic signal is weak, the orthology claim is correspondingly weakened, and the central thesis of the paper is undermined.
- **Resolution test** Provide statistical support values for key nodes, describe sensitivity analyses (e.g., different alignment methods, site-heterogeneous models, removal of fast-evolving sites), and show that the orthology conclusion is robust to these choices.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Structural evidence
- **Claim pointer** The authors claim that AlphaFold-multimer predictions reveal a conserved scm3 fold and interaction interface across diverse metazoan HJURP orthologs, including the prediction of an additional helix in zebrafish.
- **Evidence pointer** Results sections "HJURP orthologs are broadly conserved across deuterostomes, including teleosts" and "Drosophila CAL1 is a true HJURP ortholog"; Figures 1D, 3F, 6B; Figure S12
- **Concern** The structural predictions are described qualitatively. No confidence metrics (pLDDT scores, PAE values) are reported in the text, and the authors do not state how many of the predicted structures met quality thresholds. The claim that the zebrafish prediction includes an additional helix "reminiscent of" the CAL1 structure is suggestive but not quantitatively compared.
- **Why it matters** Structural predictions are used to support both the orthology claim and the functional significance of conserved residues. If the predictions are low-confidence in key regions, the structural arguments are weakened.
- **Resolution test** Report pLDDT and PAE values for the key interface residues, state quality thresholds used, and provide quantitative structural comparisons (e.g., RMSD values across predicted ortholog structures) rather than qualitative descriptions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Evolutionary rate analysis
- **Claim pointer** The authors claim that dN/dS analysis shows HJURP evolves roughly an order of magnitude faster than HIRA and ASF1, and that positive selection is detectable in primate HJURP.
- **Evidence pointer** Results section "Scm3/HJURP orthologs are broadly conserved across Metazoa"; Figure 6E, 6F
- **Concern** The dN/dS analysis is described briefly. The authors do not specify which codon model was used for the whole-gene comparisons, how alignment quality was assessed for such divergent sequences, or whether the elevated dN/dS could be an artifact of misalignment. The positive selection analysis in primates is mentioned but the specific sites, their locations, and the statistical support are not described in the text.
- **Why it matters** The claim of rapid evolution is used to explain why standard homology detection failed. If the rate estimate is inflated by alignment error, the explanation is weakened. The positive selection result is also used to support the centromere drive hypothesis, so its robustness matters.
- **Resolution test** Provide details of the codon models used, alignment quality metrics, and the specific sites under positive selection with their posterior probabilities. Show that the rate difference is robust to alignment method.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1A
- **Evidence pointer** Results section "HJURP orthologs are broadly conserved across deuterostomes, including teleosts"
- **Issue** The text states that the coelacanth protein was identified by homology outside the scm3 domain, but the figure legend is not available. It is unclear what is shown in Figure 1A and how the stepping-stone logic is visualized.
- **Required correction** Clarify in the text what Figure 1A displays and how the coelacanth identification enabled subsequent searches.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Recombinant protein pulldown assays
- **Evidence pointer** Materials and Methods "Amylose pulldown"
- **Issue** The pulldown experiments are described, but the authors do not state how many biological or technical replicates were performed, nor how binding was quantified. The statement that NEFR-1 binds HCP-3/H4 "more strongly" than H3/H4 is qualitative.
- **Required correction** Provide replicate numbers and a quantitative measure of binding (e.g., densitometry) with statistical comparison.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion of C. elegans paternal genome
- **Evidence pointer** Discussion section
- **Issue** The authors state that NEFR-1 may reestablish CENPA on the paternal genome, but this is speculative. The data show NEFR-1 localizes to the paternal pronucleus, but no functional test of this specific role is provided.
- **Required correction** Clearly distinguish this as a hypothesis and consider alternative explanations, such as NEFR-1 being maternally loaded and functioning in both parental genomes.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Zebrafish phenotype quantification
- **Evidence pointer** Results section "The zebrafish gene si:dkeyp-117 h8.4 encodes HJURP"; Figure 2C-F
- **Issue** The text reports "gross morphological defects and extensive signs of necrotic tissue" and a "~65% reduction" in CENPA intensity, but no sample sizes, statistical tests, or variance measures are provided in the visible text.
- **Required correction** Report sample sizes, statistical tests used, and effect sizes with confidence intervals.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Use of "living fossil"
- **Evidence pointer** Discussion section
- **Issue** The term "living fossil" is used for coelacanth and horseshoe crab genomes. This term is imprecise and potentially misleading, as these lineages have continued to evolve.
- **Required correction** Use more neutral terminology such as "slowly evolving lineages" or "early-branching lineages."

- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative support for essentiality), R1-M2 (phylogenetic support values and robustness), R1-M3 (structural confidence metrics), R1-M4 (dN/dS methodological detail)

- **Assessment against Nature-style criteria** 
  - Originality: High. The claim that Scm3/HJURP orthologs are broadly conserved across Metazoa, including in lineages previously thought to lack them, directly challenges the prevailing view and would represent a significant conceptual advance.
  - Scientific importance: High. Centromere specification is fundamental to chromosome segregation, and understanding the conservation of this machinery has broad implications for cell biology, evolution, and human disease (HJURP is implicated in cancer).
  - Interdisciplinary readership: Moderate to high. The work bridges evolutionary genomics, structural biology, and cell biology. The generalizable pipeline for finding deeply diverged orthologs will interest a broad audience.
  - Technical soundness: Currently not fully assessable. The computational approach is appropriate, but key evidence (phylogenetic support, structural confidence, quantitative functional data) is in supplementary materials not provided. The described methods are generally sound but lack sufficient detail in several areas.
  - Readability for nonspecialists: Good. The manuscript is clearly written, the logic is easy to follow, and the significance of the findings is well-articulated. The use of figures is appropriate, though figure content could not be evaluated.

- **Recommendation posture** Supportive if technical concerns are resolved. The central claims are potentially important and the approach is appropriate, but the evidence as presented in the visible text is insufficient to fully establish the case. The authors must provide quantitative functional data, phylogenetic support values, and structural confidence metrics. If these are satisfactory, this would be a strong contribution. Currently not established from the provided evidence.

## Risk / unsupported claims
- The claim that NEFR-1 is essential for embryonic cell division is not quantitatively supported in the visible text.
- The claim that CAL1 is a true ortholog rather than a convergent analog requires phylogenetic support values not provided.
- The claim that the scm3 fold is conserved across all identified orthologs requires structural confidence metrics not provided.
- The claim that HJURP evolves an order of magnitude faster than HIRA and ASF1 requires methodological detail not provided.
- The claim that positive selection on primate HJURP supports centromere drive requires site-specific evidence not provided.
- The claim that the coelacanth genome assembly error explains the missing scm3 domain is plausible but not directly demonstrated.
- The claim that NEFR-1 reestablishes CENPA on the paternal genome is speculative and not functionally tested.