## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) without supplementary materials, figures, or tables
- **Assessment boundary** Scientific claims, phylogenetic inference methodology, structural prediction interpretation, evolutionary conclusions; not editorial or stylistic quality
- **Shared manuscript claim summary** The authors propose that land plant Type I (M-type) and Type II (MIKC-type) MADS-box transcription factors both originated from MEF2-type genes through a duplication in the most recent common ancestor of land plants, revising the previous hypothesis that Type I and II are orthologous to animal SRF and MEF2 genes respectively. They further hypothesize SRF-type gene loss in the Archaeplastida ancestor and propose a scenario of MEF2-type duplication followed by Keratin-like domain acquisition and loss.
- **Visible evidence base** Phylogenetic analyses (maximum likelihood, Bayesian, neighbor-joining) of MADS-box sequences from 175 eukaryotic species; AU tests comparing competing topologies; AlphaFold2 and OmegaFold structure predictions compared against experimentally resolved structures (HsSRF, HsMEF2A, AtSEP3); presence/absence patterns across eukaryotic lineages
- **Missing materials affecting confidence** Supplementary tables S1–S3 (species list, structure prediction scores, sequence accessions), supplementary figures S1–S8 (detailed phylogenies, structure overlays, AU test results), alignment files, structure prediction confidence metrics, and full methodological parameters for ColabFold runs

## Reviewer
- **Overall assessment** This manuscript presents a well-motivated re-evaluation of a long-standing hypothesis in MADS-box gene evolution, leveraging expanded taxonomic sampling and modern structure prediction tools. The central claim, that plant Type I and II genes are both MEF2-type rather than Type I being SRF-type, is a significant revision with broad implications for plant evolutionary developmental biology. The phylogenetic evidence appears consistent across multiple methods, and the structure predictions provide an independent line of support. However, the strength of the conclusions depends critically on supplementary data not visible in this review, particularly the AU test results, the structure similarity scores, and the completeness of taxonomic sampling. The evolutionary scenario proposed, while parsimonious, involves several inferential steps that require careful scrutiny.
- **Who would be interested in the results, and why** Plant evolutionary biologists studying transcription factor family evolution, particularly those working on MADS-box genes and their roles in floral development and terrestrialization. Researchers interested in the origin and diversification of gene regulatory networks in land plants. The revised nomenclature proposal and the evolutionary scenario for Type I/II divergence will also be relevant to the broader community studying gene family evolution and the genetic basis of plant adaptation to land.
- **Major strengths** 1) The study addresses a long-standing and influential hypothesis with substantially expanded taxonomic sampling, including previously underrepresented protist and algal lineages. 2) The combination of phylogenetic inference with structure prediction provides two independent lines of evidence. 3) The authors acknowledge limitations of their approach and test alternative topologies explicitly. 4) The proposed evolutionary scenario is clearly articulated and testable. 5) The nomenclature recommendations are practical and address a known source of confusion in the field.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** The core phylogenetic claim requires verification of the AU test results and support values for the critical nodes separating Type I/II from SRF-type. The structure prediction evidence needs quantitative comparison scores and confidence metrics. The absence of SRF-type genes in Archaeplastida needs confirmation that the HMM searches were sensitive enough to detect highly divergent sequences.
- **Assessment against Nature-style criteria** 
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Phylogenetic support
- **Claim pointer** The central claim that land plant Type I and II MADS-box TFs both cluster within the MEF2 clade, and that no SRF-type gene exists in land plants.
- **Evidence pointer** Results section "Land Plant Type I and II MADS-box TFs are Both MEF2-type"; Figures 3 and 4; supplementary figures S1–S3
- **Concern** The manuscript states that three different phylogenetic methods consistently support the placement of Type I and II within the MEF2 clade, but the actual support values for the critical nodes are not reported in the visible text. The AU test results, which are essential for demonstrating that the previous SRF-type hypothesis is significantly rejected, are only referenced as supplementary figure S4. Without these values, the reader cannot assess whether the phylogenetic signal is robust or marginal. The long branches of Type I sequences, acknowledged by the authors, are a known source of artifact in phylogenetic inference, and the manuscript does not describe any specific measures taken to mitigate this beyond increased sampling.
- **Why it matters** The entire revision of the evolutionary hypothesis rests on the phylogenetic placement of Type I genes. If the support for the MEF2-type placement is weak or the AU test does not strongly reject the alternative topology, the central conclusion is not established. The long-branch attraction concern is particularly relevant given the high substitution rates of Type I genes.
- **Resolution test** Report bootstrap support values, posterior probabilities, and AU test p-values for the critical nodes in the main text or a clearly visible supplementary table. Demonstrate that the alternative topology (Type I within SRF clade) is significantly rejected with p < 0.05. Show that the results are robust to alignment method and taxon sampling, particularly with and without the fastest-evolving Type I sequences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Structure prediction evidence
- **Claim pointer** The claim that predicted structures of plant Type I and II TFs resemble MEF2-type rather than SRF-type structures, supporting the phylogenetic inference.
- **Evidence pointer** Results section "MADS Domains of SRF-type and MEF2-type TFs Form Distinct Structures"; Figure 2; supplementary tables S2 and S3
- **Concern** The manuscript describes qualitative comparisons of predicted structures to experimentally resolved structures, stating that Type I and II TFs "resemble" MEF2-type structures. However, no quantitative similarity scores (e.g., TM-scores, RMSD values) are reported in the visible text. The distinction between SRF and MEF2 structures is described as a "kink" in the second helix, but the manuscript does not specify how this kink is detected in predicted structures or how confident the predictions are. AlphaFold2 and OmegaFold predictions can vary in reliability, particularly for regions with low sequence coverage or for proteins with few homologs, and no confidence metrics (e.g., pLDDT scores) are mentioned.
- **Why it matters** The structure predictions are presented as independent confirmation of the phylogenetic results. If the structural distinction between SRF and MEF2 types is subtle (a helix kink), and the predictions are not quantitatively compared or confidence-filtered, the strength of this evidence is unclear. The authors themselves acknowledge that structure alone does not completely reject the previous hypothesis, so the evidential weight of this analysis needs to be precisely stated.
- **Resolution test** Provide quantitative structure similarity scores (TM-scores or RMSD) for representative Type I and II proteins against HsSRF, HsMEF2A, and AtSEP3. Report confidence metrics for the predictions, particularly for the second helix region. Specify the threshold used to classify a structure as MEF2-like versus SRF-like, and demonstrate that the classification is robust to prediction method.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Taxonomic sampling and HMM sensitivity
- **Claim pointer** The claim that SRF-type genes were lost in the MRCA of Archaeplastida, based on their absence in all surveyed Archaeplastida genomes.
- **Evidence pointer** Results section "Loss of SRF-type Genes in the Most Recent Common Ancestor of Archaeplastida"; supplementary table S1
- **Concern** The conclusion that SRF-type genes are absent from Archaeplastida is a strong negative claim that depends on the completeness and quality of the genome assemblies and the sensitivity of the search methods. The manuscript mentions using BLASTP and HMM searches with the PF00319 profile, but does not report the number of genomes per lineage, the assembly quality, or the search thresholds used. The authors note finding "partial SRF-like MADS domains" in some core chlorophytes, which they interpret as horizontal gene transfer, but this interpretation requires careful justification. If the HMM search is not sensitive enough to detect highly divergent SRF-type sequences, or if some genomes have poor coverage of this gene family, the absence could be artifactual.
- **Why it matters** The proposed evolutionary scenario depends on SRF-type loss occurring specifically in the Archaeplastida ancestor. If SRF-type genes are present but undetected in some Archaeplastida lineages, or if the loss occurred later and independently in multiple lineages, the scenario would need substantial revision. The horizontal gene transfer interpretation for the partial chlorophyte sequences is particularly important, as it bears on the timing and mechanism of SRF-type loss.
- **Resolution test** Report the number of genomes searched per lineage, assembly quality metrics, and the search sensitivity (e.g., how many known SRF-type sequences are recovered in positive control species). Provide evidence that the HMM search would detect SRF-type sequences at the divergence levels expected in Archaeplastida. Justify the horizontal gene transfer interpretation with additional analyses, such as phylogenetic placement of the partial sequences or synteny comparisons.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Nomenclature
- **Affected element** Proposed nomenclature revision
- **Evidence pointer** Discussion section "A New Hypothesis on the Origin of Type I and II MADS-box Genes in Land Plants"
- **Issue** The authors propose restricting "Type I" and "Type II" to land plant MADS-box TFs and using "SRF-type" and "MEF2-type" for the ancient eukaryotic clades. While this is sensible, the manuscript does not discuss how this nomenclature would interact with the existing and widely used "MIKC" and "M-type" designations, beyond a brief recommendation. The potential for confusion during a transition period is not addressed.
- **Required correction** Add a brief paragraph or table clarifying the proposed mapping between old and new terminology, and acknowledge the practical challenges of nomenclature transitions in a field with extensive existing literature.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Functional inference
- **Affected element** Discussion of ancestral stress-responsive function
- **Evidence pointer** Discussion section "From Stress Response and Reproductive Induction to Complex Structural Programming"
- **Issue** The discussion of the ancestral stress-responsive function of MADS-box genes, while interesting, relies on functional data from a limited set of organisms and does not fully address alternative interpretations. The claim that stress responsiveness is ancestral and was later co-opted into developmental programs is plausible but presented somewhat speculatively.
- **Required correction** Soften the language around the ancestral function inference and explicitly acknowledge the limited taxonomic breadth of functional data. Consider citing additional examples or framing this as a testable hypothesis rather than a conclusion.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological transparency
- **Affected element** Structure prediction methods
- **Evidence pointer** Methods section "Protein Structure Prediction and Analyses"
- **Issue** The description of the ColabFold implementation is brief. The manuscript does not specify whether default parameters were used, how many recycles were performed, or whether the top-ranked model was always selected. For a study that relies on structure predictions as supporting evidence, this level of detail is insufficient for reproducibility.
- **Required correction** Provide additional methodological details, including ColabFold version, number of models generated, selection criteria, and any filtering based on prediction confidence.

## Risk / unsupported claims
- The claim that SRF-type genes were lost in the MRCA of Archaeplastida is not fully supported by the visible evidence; it depends on negative results across many genomes and the sensitivity of detection methods, which are not fully documented in the visible text.
- The claim that the predicted structures of Type I and II TFs resemble MEF2-type structures is not quantitatively supported in the visible text; no similarity scores or confidence metrics are reported.
- The claim that the AU test significantly rejects the previous topology (Type I within SRF clade) is not verifiable from the visible text; the results are only referenced as supplementary figure S4.
- The functional scenario proposing an ancestral stress-responsive role for MADS-box genes, later co-opted into developmental programs, is presented with limited direct evidence and should be considered a hypothesis rather than an established conclusion.
- The interpretation of partial SRF-like sequences in core chlorophytes as horizontal gene transfer is not fully justified in the visible text and requires additional supporting analyses.