## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors characterize the regulatory region of the B. abortus omp25 gene and identify three BvrR binding sites (boxes 1-3) within the upstream region, proposing that BvrR directly regulates omp25 expression through these sites, potentially with other transcription factors
- **Visible evidence base** Reporter fusion assays, EMSA, DNase I footprinting, fluorescence anisotropy, molecular docking, sequence alignments
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; raw data for β-galactosidase assays not shown; detailed experimental conditions for some assays not fully described

## Reviewer
- **Overall assessment** The manuscript presents a systematic characterization of the omp25 regulatory region and provides evidence for three BvrR binding sites. The combination of experimental approaches (EMSA, DNase I footprinting, fluorescence anisotropy) strengthens the identification of binding sites. However, several concerns regarding the functional significance of the identified boxes, the interpretation of the reporter assay data, and the reliance on computational predictions without experimental validation limit the current impact of the work. The study is a useful contribution to the field of Brucella gene regulation but requires additional experiments to fully support the proposed model.
- **Who would be interested in the results, and why** Researchers studying two-component regulatory systems in Brucella and related Rhizobiales, investigators interested in transcriptional regulation of outer membrane proteins in Gram-negative pathogens, and those working on BvrR/BvrS regulon mapping. The findings may also be relevant to comparative studies of OmpR-family response regulators across bacterial species.
- **Major strengths** 1) Systematic deletion analysis using reporter fusions to define the minimal regulatory region. 2) Multiple complementary biochemical approaches (EMSA, DNase I footprinting, fluorescence anisotropy) to identify and validate binding sites. 3) Identification of three distinct binding sites with defined boundaries. 4) Sequence analysis revealing potential repeat structures within the binding sites. 5) The proposed model has broader implications for BvrR regulon mapping in Brucella and related species.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** The functional significance of the three binding sites for transcriptional regulation is not experimentally demonstrated. The reporter assays only show that the region containing the binding sites is necessary for activity, but do not show that BvrR binding to these specific sites is required. Mutational analysis of the binding sites is needed.
- **Assessment against Nature-style criteria** 
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation
- **Claim pointer** The authors claim that BvrR directly regulates omp25 expression by binding to three DNA regulatory boxes, and that the 111-bp region upstream of these boxes is needed for wild-type transcriptional levels
- **Evidence pointer** Results sections "A 111-bp long fragment at position −262 to −152 is needed for transcriptional activity" and "The upstream omp25 regulatory region displays three BvrR binding sites"; Figures 1-5
- **Concern** The manuscript demonstrates that BvrR can bind to three sites in vitro and that a region containing these sites is necessary for transcriptional activity. However, the direct link between BvrR binding to these specific boxes and transcriptional regulation is not established. The reporter assays compare different length fragments but do not include mutations in the identified binding boxes. Without mutational analysis of boxes 1-3, the functional requirement of these specific sites for BvrR-mediated regulation remains correlative rather than causal. Additionally, the authors do not show whether BvrR binding to these sites is sufficient for activation, nor do they test the effect of BvrR overexpression or deletion on the reporter activity.
- **Why it matters** The central claim of the paper is that BvrR regulates omp25 through these three specific binding sites. Without functional validation through mutagenesis, the physiological relevance of the identified boxes is not established. The field requires evidence that these sites are not merely bound in vitro but are functionally important for regulation in vivo.
- **Resolution test** Mutate each of the three identified boxes individually and in combination in the context of the full-length reporter construct and measure β-galactosidase activity in wild-type and bvrR mutant backgrounds. Alternatively, complementation assays with BvrR variants defective in DNA binding could establish the requirement for these sites.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative data support
- **Claim pointer** The authors state that the 111-bp fragment from −262 to −152 is "needed for transcriptional activity" and that B151 shows "significantly reduced" but "some basal transcriptional activity"
- **Evidence pointer** Results section "A 111-bp long fragment at position −262 to −152 is needed for transcriptional activity"; Figure 1B; Supplementary Table 3
- **Concern** The β-galactosidase data are presented only as a single representative figure without quantitative details in the main text. The statistical analysis is mentioned but the actual values, number of biological replicates, and effect sizes are not reported in the visible text. The claim of "significantly reduced" activity for B151 requires the actual data to be assessed. Furthermore, the comparison between B392 and B262 shows "no significant statistical differences," but the trend appears to show B262 with lower activity at some time points. The interpretation that the 111-bp region is "needed" for activity is based on a single deletion construct, and the possibility of position-dependent effects or disruption of spacing between regulatory elements is not addressed.
- **Why it matters** The functional conclusion about the importance of the 111-bp region is a key finding of the paper. Without access to the actual quantitative data and statistical details, the strength of this conclusion cannot be evaluated. The distinction between "needed for activity" versus "needed for optimal activity" is important for the proposed model.
- **Resolution test** Provide the full quantitative data for all reporter assays including individual data points, means, standard deviations, and statistical test results. Include the number of independent biological replicates. Consider testing additional deletion constructs to determine whether the effect is due to specific sequences or general spacing requirements.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Computational prediction validation
- **Claim pointer** The authors use molecular docking to predict specific amino acid-nucleotide interactions between BvrR and the three boxes, and state that the docking results "predicted the possibility of hydrogen bonds and non-bonded contacts between 13, 15, and 14 amino acid residues" and the boxes
- **Evidence pointer** Results section "Molecular docking and sequence alignment of the three DNA regulatory boxes predict BvrR recognition of inverted and non-inverted DNA repeats"; Figure 6; Supplementary Figures 2-3; Supplementary Tables 4-6
- **Concern** The molecular docking analysis is presented as supporting evidence for the binding interactions, but the quality of the BvrR model is acknowledged to be "low to medium" based on sequence identity to the template. The docking predictions are not validated experimentally, and the specific interactions predicted are not tested. The authors themselves note that the model quality is limited. The use of docking results to support the biological model is premature without experimental validation of the predicted contacts.
- **Why it matters** The docking analysis is used to strengthen the claim that BvrR specifically recognizes these boxes. However, computational predictions with a low-quality model can be misleading. The field requires experimental validation of predicted contacts, such as mutagenesis of the predicted interacting residues, to support the docking conclusions.
- **Resolution test** Validate the docking predictions experimentally by mutating key predicted interacting residues in BvrR and testing DNA binding by EMSA or fluorescence anisotropy. Alternatively, perform alanine scanning mutagenesis of the predicted contact residues and assess binding affinity changes.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Model generalizability
- **Claim pointer** The authors propose that "This gene regulation model could apply to other BvrR target genes and to orthologs of the TCS BvrR/BvrS and Omp25 in phylogenetically closed Rhizobiales"
- **Evidence pointer** Discussion section, final paragraph
- **Concern** The generalization of the proposed model to other BvrR target genes and Rhizobiales orthologs is speculative. The authors have characterized only one target gene (omp25) and have not provided evidence that the identified binding site features (inverted and non-inverted repeats) are conserved in other BvrR-regulated promoters or in orthologous systems. While this is presented as a possibility, the statement could be interpreted as a broader conclusion than the data support.
- **Why it matters** The broader significance of the work depends on whether the identified regulatory mechanism is generalizable. Without comparative analysis of other BvrR target promoters or experimental evidence from orthologous systems, the generalizability claim is not supported.
- **Resolution test** Perform a bioinformatic analysis of other known or predicted BvrR target promoters to assess whether similar binding site features are present. Alternatively, test BvrR binding to promoters of other target genes experimentally.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Experimental detail
- **Affected element** EMSA methodology
- **Evidence pointer** Materials and methods, "Electrophoretic mobility shift assay (EMSA)"
- **Issue** The EMSA methods describe using GST-BvrR, but the text later refers to "P-BvrR" (phosphorylated BvrR). The phosphorylation step is mentioned, but the efficiency of phosphorylation and the ratio of phosphorylated to unphosphorylated protein are not described. Additionally, the concentration range of BvrR used in the direct EMSA experiments is not stated.
- **Required correction** Provide details on the phosphorylation efficiency, the concentration range of BvrR used, and whether the GST tag was cleaved before the assays. This information is important for reproducibility and for interpreting the binding affinities.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1B
- **Evidence pointer** Results section "A 111-bp long fragment at position −262 to −152 is needed for transcriptional activity"; Figure 1B
- **Issue** The β-galactosidase activity data in Figure 1B are presented as a line graph over time, but the statistical comparisons are only mentioned in the text. It would be helpful to indicate on the figure which time points show significant differences between strains.
- **Required correction** Add significance indicators (e.g., asterisks) to Figure 1B at time points where significant differences were observed, or provide a separate panel with the statistical comparisons.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Sequence analysis
- **Affected element** Figure 7A
- **Evidence pointer** Results section "Molecular docking and sequence alignment of the three DNA regulatory boxes predict BvrR recognition of inverted and non-inverted DNA repeats"; Figure 7A
- **Issue** The manual sequence alignment of the three boxes is described, but the alignment itself is not shown in the visible text. The inverted and non-inverted repeats are described in the text, but the actual sequences and their alignment would help the reader evaluate the significance of the identified motifs.
- **Required correction** Include the sequence alignment in the main figure or as a supplementary figure, with the repeats clearly marked.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "DNA regulatory boxes"
- **Evidence pointer** Throughout the manuscript
- **Issue** The term "DNA regulatory boxes" is used to describe the BvrR binding sites. While this is acceptable, the term "box" is not standard in the field of bacterial two-component system regulation. More common terms include "binding site," "operator," or "recognition motif." The authors may want to clarify whether these boxes correspond to previously described BvrR binding motifs or are novel.
- **Required correction** Consider using more standard terminology or explicitly defining what is meant by "DNA regulatory box" in the context of this study.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion mentions that "few regulatory regions of BvrR direct target genes have been studied" but does not provide a comprehensive comparison with the limited existing studies on BvrR binding sites. A more detailed comparison with the previously reported BvrR binding motifs (e.g., from Ramírez-González et al., 2019 and Rivas-Solano et al., 2022) would strengthen the context.
- **Required correction** Expand the discussion to include a more detailed comparison of the identified boxes with previously reported BvrR binding motifs, including any similarities or differences in sequence and position.

## Risk / unsupported claims
- The claim that the 111-bp region is "needed" for transcriptional activity is based on a single deletion construct without addressing potential spacing or positional effects
- The generalization of the regulatory model to other BvrR target genes and Rhizobiales orthologs is speculative and not supported by direct evidence
- The molecular docking predictions of specific amino acid-nucleotide interactions are not experimentally validated and rely on a model of low to medium quality
- The statement that BvrR "probably interacts with other transcription factors to regulate omp25 expression" is presented as a conclusion but is not directly tested in this study
- The functional significance of the three binding sites for BvrR-mediated regulation is not demonstrated through mutational analysis
- The claim that the boxes show "78.57 and 71.42% similarity to the 14-bp long consensus sequence" is presented without showing the actual alignment or the consensus sequence