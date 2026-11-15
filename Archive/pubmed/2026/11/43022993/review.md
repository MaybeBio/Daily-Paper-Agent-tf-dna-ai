## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results and discussion, conclusion, and supplementary data references.
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and alignment with Nature-style criteria. Editorial or formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors propose a mechanistic model for mismatched DNA recognition by TaqMutS, involving a push-pull mechanism mediated by residues S57 and D472 that modulates F39-DNA π-stacking, and an electrostatic synergy between K61 and R473 that regulates non-specific binding. Two mutants (V57S and K61H) are reported to show improved specificity and are proposed as error-correction tools for DNA synthesis.
- **Visible evidence base** Experimental EMSA binding data for wild-type and mutant proteins across multiple DNA substrates; GaMD simulation analyses of hydrogen bonding, contact frequencies, and distances; alanine scanning and homologous substitution mutagenesis; sequence conservation analysis; solubility and aggregation predictions; error-removal assay with next-generation sequencing readouts.
- **Missing materials affecting confidence** Supplementary figures and tables (Figs. S1-S12, Tables S1-S3) are referenced but not provided. Raw EMSA gel images are not shown for all mutants. Simulation convergence metrics, force field validation, and replica information are not described. Statistical details for sequencing-based error-removal data are incomplete. Structural coordinates or AlphaFold3 confidence metrics are not provided.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in DNA synthesis error correction and provides a plausible mechanistic hypothesis for TaqMutS specificity. The combination of experimental mutagenesis and molecular dynamics simulation is appropriate. However, the central mechanistic claims are supported by indirect evidence, and several key controls and quantitative analyses are missing. The claim that V57S and K61H are improved error-correction tools is not fully established from the data presented, particularly given the modest effect sizes and the lack of statistical rigor in the sequencing-based assay. The manuscript is technically sound in its overall approach but requires substantial additional evidence to support the proposed push-pull and electrostatic synergy mechanisms.
- **Who would be interested in the results, and why** Researchers in DNA repair mechanisms, particularly those studying MutS homologs and mismatch recognition; synthetic biologists and bioengineers working on DNA synthesis error correction and DNA data storage; protein engineers interested in specificity modulation through single-point mutations. The mechanistic insights into how local DNA strain and electrostatic interactions govern recognition could inform rational design of DNA-binding proteins beyond the MutS family.
- **Major strengths** The study combines multiple complementary approaches (mutagenesis, simulation, functional assays) to address a specific mechanistic question. The identification of specific residues (S57, D472, K61, R473) and the proposal of a push-pull mechanism provide a testable framework. The use of homologous substitution based on sequence comparison with EcoMutS is a logical strategy. The error-removal assay with a defined DNA pool is a practical demonstration of potential application.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency for mechanistic claim
  - **Claim pointer** The authors claim that S57 and D472 cooperatively regulate F39-mediated mismatched DNA recognition through a push-pull mechanism, where S57 forms hydrogen bonds with DNA to stabilize F39 π-stacking and D472 repels the DNA backbone via electrostatic effects.
  - **Evidence pointer** Results section "Push-pull mechanism involving the cooperative regulation of F39-mediated mismatched DNA recognition by V57 and D472"; Figs. 5-7
  - **Concern** The push-pull mechanism is inferred primarily from distance and contact frequency analyses in GaMD simulations. The D472N mutant could not be experimentally characterized, leaving the functional role of D472 unvalidated. The D472E rescue experiment is presented as confirmation, but the data are only shown as binding percentages without statistical analysis or comparison to the predicted mechanism. The inverse correlation between residue 472 and residue 57 distances is based on single simulations without error estimates or replicate analysis.
  - **Why it matters** The central mechanistic claim of the paper rests on this push-pull model. Without experimental validation of D472 function and without statistical robustness in the simulation data, the mechanism remains speculative. The inability to characterize D472A is a critical gap, as this is one of the two key residues in the proposed mechanism.
  - **Resolution test** Provide experimental characterization of D472 mutants through alternative approaches (e.g., suppressor mutations, compensatory mutations, or alternative expression systems). Include replicate simulations with error bars for distance distributions. Demonstrate that the proposed push-pull mechanism can predict the behavior of additional mutants beyond those tested.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Quantitative rigor of functional claims
  - **Claim pointer** The authors claim that V57S and K61H exhibit enhanced binding efficiency for mismatched DNA and reduced affinity for perfectly matched DNA, and that they show improved error-removal performance compared to wild-type.
  - **Evidence pointer** Results sections "Mismatched DNA binding and error-removal performance of V57S and K61H"; Figs. 3, 9, S11, S12
  - **Concern** The binding percentages are presented as mean values without error bars in several figures (e.g., Fig. 3) or with unclear statistical treatment. The error-removal assay shows reductions in mismatched fractions, but no statistical comparison between wild-type and mutants is provided. The claim of "enhanced" and "reduced" binding is based on absolute percentage differences that may be within experimental variability. The sequencing data lack information on read depth, replicate variability, and significance testing.
  - **Why it matters** The practical utility of the mutants as error-correction tools depends on statistically robust demonstration of improved performance. Without proper statistical analysis, the reported improvements cannot be distinguished from noise, and the recommendation of these mutants for application is not justified.
  - **Resolution test** Provide error bars and statistical tests (e.g., t-tests or ANOVA) for all binding and error-removal comparisons. Report sequencing depth, number of replicates, and confidence intervals for the error-removal data. Demonstrate that the improvements are reproducible and significant.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Methodological transparency and validation
  - **Claim pointer** The authors use GaMD simulations to support mechanistic conclusions about protein-DNA interactions and conformational dynamics.
  - **Evidence pointer** Methods section "Molecular dynamics simulation"; Results sections on local conformational strain and push-pull mechanism
  - **Concern** The simulation methodology lacks critical details: no information on simulation length convergence, number of replicas, equilibration criteria, or validation of the AlphaFold3-generated starting structures. The choice of GaMD over conventional MD is not justified. The force field combination (ff14SB for protein, OL15 for DNA) is appropriate but no validation against experimental data is provided. The analysis of hydrogen bonds and contact frequencies is not described in sufficient detail to be reproducible.
  - **Why it matters** The mechanistic conclusions depend heavily on simulation data. Without proper methodological transparency and validation, the reliability of these conclusions cannot be assessed. The lack of convergence analysis is particularly concerning for a study that draws quantitative conclusions from distance distributions.
  - **Resolution test** Provide detailed simulation protocols including convergence metrics, replica information, and validation of starting structures. Include analysis of simulation stability (RMSD, energy drift). Justify the choice of GaMD and demonstrate that the observed differences are robust across simulation conditions.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of presentation
  - **Affected element** Figure 1
  - **Evidence pointer** Results section "Evaluation of mismatched DNA recognition ability of EcoMutS and TaqMutS"
  - **Issue** The figure legend is incomplete. It does not describe the experimental conditions, the DNA substrate sequences, or the statistical treatment of the data. The panel labels (a-d) are not explained in the legend.
  - **Required correction** Expand the figure legend to include full experimental details, substrate descriptions, and statistical information.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness of supplementary data
  - **Affected element** Supplementary figures and tables
  - **Evidence pointer** Multiple references to Figs. S1-S12 and Tables S1-S3
  - **Issue** The supplementary materials are not provided with the manuscript. Several key pieces of evidence (e.g., SDS-PAGE gels, sequence alignments, primer sequences, additional simulation analyses) are only available in the supplementary files.
  - **Required correction** Ensure all supplementary materials are included with the submission and referenced appropriately in the text.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Binding percentage data
  - **Evidence pointer** Results sections on alanine scanning and homologous substitutions; Fig. 3
  - **Issue** The binding percentages are reported as single values or means without standard deviations in several instances. The number of independent experiments is not consistently stated.
  - **Required correction** Report all quantitative data with appropriate measures of variability and specify the number of replicates for each experiment.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretation of simulation data
  - **Affected element** Distance and contact frequency analyses
  - **Evidence pointer** Results sections on push-pull mechanism and electrostatic synergy; Figs. 5-8
  - **Issue** The interpretation of distance distributions as evidence for specific interactions is somewhat speculative. For example, the statement that a distance of 5-6 Å between V57 and DG9 indicates a "push" effect is not clearly justified. The relationship between contact frequency and functional significance is not explained.
  - **Required correction** Provide clearer criteria for interpreting simulation metrics and relate them more explicitly to the proposed mechanistic model.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Discussion of limitations
  - **Affected element** Conclusion section
  - **Evidence pointer** Conclusion
  - **Issue** The conclusion does not acknowledge the limitations of the study, such as the inability to characterize D472A, the reliance on simulations for key mechanistic claims, and the lack of structural validation (e.g., crystallography or cryo-EM).
  - **Required correction** Add a limitations paragraph to the discussion or conclusion to provide a balanced assessment of the evidence.

## Risk / unsupported claims
- The claim that S57 and D472 operate via a push-pull mechanism is not fully supported, as D472 function was not experimentally validated and the simulation evidence is based on single trajectories without statistical analysis.
- The claim that V57S and K61H are "promising error-correction tools" is not quantitatively supported, as the error-removal data lack statistical comparison and the effect sizes are modest.
- The statement that "the local bulging distortion within mismatched DNA serves as the key determinant for recognition" is an overgeneralization from a single mismatch type (A/G) and limited simulation data.
- The claim that K61 and R473 exhibit "electrostatic synergy" is inferred from contact frequency analysis but is not directly tested experimentally.
- The assertion that the two mutants "exhibited enhanced binding efficiency for mismatched DNA and reduced affinity for perfectly matched DNA" is not consistently supported across all mismatch types, and the statistical significance is not established.
- The mechanistic model is presented as general, but the study only examined A/G mismatches in detail, with limited data on other mismatch types.

## Assessment against Nature-style criteria
- **Originality** Moderate. The application of a push-pull model to MutS-mediated mismatch recognition is somewhat novel, but similar concepts have been proposed for other DNA-binding proteins. The specific combination of alanine scanning, homologous substitution, and GaMD is not particularly innovative.
- **Scientific importance** Moderate. The work addresses a practical problem in DNA synthesis error correction, which is relevant to the growing field of DNA data storage. However, the mechanistic insights are incremental and do not fundamentally change the understanding of MutS function.
- **Interdisciplinary readership** Limited. The manuscript is primarily of interest to specialists in DNA repair and protein engineering. The broader synthetic biology community may find the error-correction application relevant, but the mechanistic focus narrows the audience.
- **Technical soundness** The experimental approaches are generally sound, but the lack of statistical rigor in key quantitative claims and the incomplete simulation methodology reduce confidence. The inability to characterize D472A is a significant technical gap.
- **Readability for nonspecialists** The manuscript is reasonably well written but assumes familiarity with MutS biology and molecular dynamics terminology. The mechanistic sections are dense and may be challenging for readers outside the immediate field.

## Recommendation posture
Supportive if technical concerns are resolved. The manuscript presents a plausible and potentially useful mechanistic framework, but the central claims require stronger experimental validation and more rigorous quantitative analysis. Specifically, the D472 role must be experimentally addressed, simulation data need statistical robustness, and the error-removal performance claims require proper statistical comparison. If these concerns are adequately addressed, the work could make a meaningful contribution to the field of DNA synthesis error correction.