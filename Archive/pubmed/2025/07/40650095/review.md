## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and conclusions as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors report that NsrR, a nitric-oxide-sensing transcriptional repressor, represses σE-dependent small RNAs (rybB, micA, micL) and rpoE itself in E. coli, independently of the canonical anti-sigma factor RseA. They propose that NsrR acts as a noncanonical anti-sigma factor through direct protein-protein interaction with RpoE, supported by bacterial two-hybrid assays and AlphaFold3 structural modeling.
- **Visible evidence base** Results sections 2.1-2.7, including reporter assays, growth/morphology data, time-course kinetics, BACTH interaction data, and AlphaFold3 modeling; Materials and Methods sections 4.1-4.8
- **Missing materials affecting confidence** Figures and supplementary figures referenced but not provided; strain/plasmid/primer tables (Tables 1-3) not provided; raw data and statistical details not fully accessible; EMSA/DNase I footprinting/in vitro transcription data described only as negative results without figures

## Reviewer

- **Overall assessment** The manuscript presents an interesting and potentially significant observation that NsrR, a well-characterized NO-sensing repressor, may modulate the σE envelope stress response through a mechanism independent of RseA. The genetic data showing NsrR-dependent repression of σE targets are reasonably convincing, and the time-course kinetics comparison with RseA is a thoughtful experimental design. However, the central mechanistic claim of a direct NsrR-RpoE protein-protein interaction rests on limited evidence: BACTH data are presented without quantitative detail, and the AlphaFold3 modeling yields low confidence scores that the authors themselves acknowledge. The negative in vitro DNA-binding results are handled honestly but leave the mechanism unresolved. The manuscript would be strengthened by additional biochemical validation of the proposed interaction and by addressing whether the observed repression could be explained by indirect transcriptional effects.

- **Who would be interested in the results, and why** Researchers studying bacterial stress responses, particularly envelope stress and sigma factor regulation, would find this work relevant. The potential cross-talk between nitrosative stress sensing and envelope homeostasis is of interest to those studying bacterial pathogenesis, as both stress conditions are encountered in host environments. The broader community studying anti-sigma factor mechanisms and noncanonical regulators of sigma factor activity would also be interested. The work may also appeal to those using AlphaFold for protein-protein interaction prediction in bacterial systems.

- **Major strengths** 
  1. The identification of NsrR as a regulator of σE-dependent sRNAs extends the known regulatory network of the envelope stress response in an unexpected direction, linking NO sensing to envelope homeostasis.
  2. The genetic evidence is multi-layered: overexpression phenotypes, deletion analysis, and additive effects in rseA mutants collectively support an RseA-independent pathway.
  3. The time-course kinetic comparison between NsrR and RseA repression is a well-designed experiment that provides meaningful mechanistic discrimination.
  4. The authors honestly report negative in vitro DNA-binding results, which strengthens the credibility of their alternative hypothesis.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic claim
- **Claim pointer** "NsrR directly interacts with σE in bacterial two-hybrid assays" and "NsrR functions as a noncanonical anti-sigma-like modulator of σE"
- **Evidence pointer** Section 2.7, Figure 7
- **Concern** The central mechanistic claim of a direct NsrR-RpoE interaction rests on BACTH data that are described only qualitatively ("detectable colony color") and a single quantitative assay without reported values, replicates, or statistical analysis. The AlphaFold3 modeling yields low confidence scores (pTM 0.48, ipTM 0.17 for the heterodimer), which the authors acknowledge. The interaction is not validated by any orthogonal biochemical method such as co-immunoprecipitation, pull-down, or surface plasmon resonance.
- **Why it matters** The title and abstract assert a "noncanonical mechanism" of NsrR-RpoE interaction. If the interaction evidence is weak, the central claim of the paper is not established. The low AlphaFold confidence scores and lack of biochemical validation leave open the possibility that the observed genetic effects are indirect.
- **Resolution test** Provide quantitative BACTH data with appropriate controls and statistics, and validate the interaction with at least one independent biochemical method (e.g., co-purification, pull-down, or cross-linking). Alternatively, demonstrate that the genetic repression phenotypes require the predicted interaction interface through mutagenesis.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic alternative
- **Claim pointer** "NsrR may not repress these promoters via classical DNA binding" and the conclusion that repression occurs through protein-protein interaction with RpoE
- **Evidence pointer** Section 2.5, Section 2.7
- **Concern** The authors report negative results from EMSA, DNase I footprinting, and in vitro transcription assays but do not provide the data or experimental details. The possibility that NsrR represses rpoE transcription indirectly through another regulator is not experimentally excluded. The time-course kinetics showing similar repression rates for NsrR and RseA are suggestive but not definitive, as indirect regulatory cascades can also produce rapid effects.
- **Why it matters** The manuscript presents three potential mechanisms in the introduction but does not systematically exclude the indirect repression model. Without ruling out indirect effects, the conclusion that NsrR acts through direct RpoE interaction is premature.
- **Resolution test** Provide the negative in vitro data in full, and include experiments that distinguish direct from indirect effects, such as testing whether NsrR repression requires ongoing protein synthesis (e.g., chloramphenicol chase) or whether the effect persists in a translation-incompetent background.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Physiological relevance
- **Claim pointer** "NsrR functions as a noncanonical anti-sigma-like modulator of σE, integrating redox and envelope stress signals to maintain membrane homeostasis"
- **Evidence pointer** Section 2.2, Section 3.1
- **Concern** The physiological relevance of NsrR-mediated σE regulation under native conditions is not established. The overexpression experiments demonstrate that high levels of NsrR can repress σE targets, and the ΔnsrR experiments show modest derepression, but the conditions under which endogenous NsrR modulates σE activity in response to physiologically relevant signals are not explored. The connection to NO sensing is inferred but not tested directly.
- **Why it matters** The claim of signal integration between NO and envelope stress is a key conceptual advance of the paper. Without demonstrating that NO-dependent inactivation of NsrR leads to σE derepression under relevant conditions, this claim remains speculative.
- **Resolution test** Test whether NO donors or nitrosative stress conditions lead to derepression of σE targets in wild-type but not ΔnsrR backgrounds. Examine whether the NsrR [Fe-S] cluster status correlates with σE activity under combined NO and envelope stress.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Structural modeling interpretation
- **Claim pointer** "AlphaFold3 modeling supports a plausible NsrR–RpoE interaction interface"
- **Evidence pointer** Section 2.7, Figure 7C-D, Figure S1
- **Concern** The AlphaFold3 modeling of the NsrR-RpoE heterodimer yields low confidence scores, and the authors note that RpoE orientation varies across the five predicted models. The interpretation of these results as "supporting" an interaction is generous given the acknowledged model uncertainty. The comparison with RpoE conformations in different complexes (6JBQ vs 1OR7) is descriptive but does not provide mechanistic insight into how NsrR binding would inhibit σE activity.
- **Why it matters** The structural modeling is presented as corroborating evidence for the interaction, but the low confidence and variable predictions do not provide strong support. Overinterpreting weak computational predictions could mislead readers about the strength of the evidence.
- **Resolution test** Provide a more critical assessment of the modeling limitations, and consider whether the predicted interface is consistent with known functional surfaces of RpoE (e.g., the region that binds RseA or RNA polymerase). If possible, validate key predicted contact residues through mutagenesis.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Section 2.2, Figure 3
- **Evidence pointer** Figure 3A-D
- **Issue** The text states that ΔnsrR increases rybB-lacZ expression approximately 2-fold in rseA+ cells and that the increase in rseA mutants is "much greater at approximately 7-fold in the exponential phase and 4-fold in the stationary phase." However, the text also notes that the ΔnsrR ΔrseA double mutant did not show an increase over ΔrseA alone in exponential phase, which is inconsistent with an additive model. This discrepancy is acknowledged but not explained.
- **Required correction** Provide a more detailed discussion of the non-additive effects in the double mutant, including possible explanations such as ceiling effects or genetic interactions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Experimental detail
- **Affected element** Section 2.5, Section 4.6
- **Evidence pointer** Section 4.6
- **Issue** The negative results from EMSA, DNase I footprinting, and in vitro transcription are described without any data shown. The statement "The protocol details are available upon request" is not appropriate for a published manuscript.
- **Required correction** Include representative data from these experiments in the main text or supplementary materials, or at minimum provide a detailed description of the conditions tested and the limits of detection.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 2.7, Figure 7B
- **Evidence pointer** Figure 7B
- **Issue** The quantitative β-galactosidase assay confirming the BACTH interaction is described but the number of replicates, statistical test used, and significance thresholds are not reported in the text.
- **Required correction** Report the statistical details for the BACTH quantitative assay, including the number of biological replicates and the specific test used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Section 3.3
- **Evidence pointer** Section 3.3
- **Issue** The discussion of "dual-function regulators" combining transcriptional repression with sigma factor binding cites only the Bacillus subtilis SigB system. A broader discussion of other examples, if they exist, would strengthen the conceptual framing.
- **Required correction** Consider whether other examples of such dual-function regulators exist in the literature and cite them if appropriate.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Section 2.1, Figure 2
- **Evidence pointer** Figure 2A-B
- **Issue** The microscopy data are described qualitatively. The proportion of cells showing filamentation is not quantified, and representative images are not shown in the provided text.
- **Required correction** Provide quantification of the filamentation phenotype (e.g., percentage of cells with abnormal morphology) and ensure representative images are included.

## Risk / unsupported claims
- The claim that NsrR "directly interacts" with RpoE is not fully supported by the evidence presented; BACTH data are qualitative and AlphaFold3 confidence is low.
- The claim that NsrR "integrates redox and envelope stress signals" is speculative, as no experiments directly link NO sensing to σE regulation.
- The statement that NsrR functions as a "noncanonical anti-σE factor" is a mechanistic interpretation that requires stronger biochemical validation.
- The physiological relevance of NsrR-mediated σE repression under native conditions is not established, as the experiments rely primarily on overexpression.
- The negative in vitro DNA-binding results are reported without data, making them impossible to evaluate.
- The non-additive effects in the ΔnsrR ΔrseA double mutant for rpoE-lacZ are not explained, leaving uncertainty about the proposed independent pathway model.