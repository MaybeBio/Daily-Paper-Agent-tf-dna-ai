## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and funding information
- **Assessment boundary** Scientific validity, technical soundness, and support of claims based solely on the provided manuscript content
- **Shared manuscript claim summary** The authors present a combined computational and experimental study characterizing PRC2-DNA interactions, proposing that PRC2 complexes cooperatively induce DNA looping through allosteric communication mediated by DNA bending, with the SUZ12 C2 domain modulating binding affinity and AEBP2 regulating this process
- **Visible evidence base** Homology models of three PRC2 conformations, all-atom MD simulations, coarse-grained simulations with free energy calculations, single-molecule force spectroscopy experiments, and comparisons to prior experimental data
- **Missing materials affecting confidence** Supplementary figures and tables referenced throughout (Figures S1-S16, Tables S1) are not provided; detailed simulation parameters and free energy calculation protocols are only partially described; raw experimental force-extension curves beyond representative traces are not shown; statistical details of experimental replicates are not provided

## Reviewer
- **Overall assessment** This manuscript presents an ambitious multi-scale computational and experimental study of PRC2-DNA interactions. The combination of homology modeling, atomistic and coarse-grained simulations, and single-molecule experiments is commendable and appropriate for the questions addressed. The central claim of cooperative DNA looping by multiple PRC2 complexes via allosteric communication through DNA is interesting and potentially significant for understanding PRC2 function in chromatin organization. However, several technical concerns must be addressed, particularly regarding the validation of the coarse-grained force field, the interpretation of single-molecule experiments, and the robustness of the cooperative looping mechanism. The manuscript is generally well-written and accessible, though some methodological details require clarification.

- **Who would be interested in the results, and why** Researchers in chromatin biology, epigenetic regulation, and genome organization would find these results relevant. The study addresses fundamental questions about how PRC2 interacts with DNA and potentially organizes chromatin architecture, which has implications for understanding gene silencing mechanisms. Computational biophysicists studying protein-DNA interactions and coarse-grained modeling would also be interested in the methodological aspects, particularly the parameterized protein-DNA force field and the free energy calculation approach.

- **Major strengths** 
  1. The multi-scale approach combining homology modeling, all-atom and coarse-grained simulations, and single-molecule experiments provides complementary perspectives on PRC2-DNA interactions
  2. The study addresses a biologically important question about cooperative DNA binding and looping by PRC2, with potential implications for chromatin organization
  3. The prediction of C2 domain involvement in DNA binding is a testable hypothesis that could guide future experiments
  4. The comparison with prior experimental data (binding affinities, AFM observations) helps contextualize the computational predictions

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that their coarse-grained force field, with the modified knowledge-based statistical potential, accurately predicts protein-DNA binding free energies, citing agreement with experimental values for PRC2-DNA binding.
- **Evidence pointer** Methods section "Coarse-grained protein-DNA model"; Results section "Coarse-grained modeling of PRC2-DNA interactions"; Figure 2
- **Concern** The validation of the modified statistical potential is presented only through a correlation coefficient of 0.77 for nine protein-DNA complexes. The authors state that the potential was modified "to avoid double counting of electrostatic interactions and best fit experimental values," but the fitting procedure is not described in sufficient detail. The manuscript does not specify which experimental values were used for fitting, how many parameters were adjusted, or whether the validation set is independent from the fitting set. This raises concerns about potential overfitting and the generalizability of the force field.
- **Why it matters** The entire computational framework depends on the accuracy of this force field. If the potential is overfit to specific complexes, the predicted binding free energies for PRC2 conformations may not be reliable. The central conclusions about differential DNA binding between PRC2b and PRC2f hinge on the accuracy of these calculations.
- **Resolution test** The authors should provide a clear description of the fitting procedure, including which experimental data were used for fitting versus validation. Cross-validation or leave-one-out analysis should be performed to demonstrate that the potential generalizes. Additionally, the authors should show that the predicted binding free energies are robust to reasonable variations in the fitting parameters.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that two PRC2 complexes cooperatively loop DNA, with the free energy difference between open and looped states shifting from 4.7 to -10.8 kBT for PRC2f and from 2.7 to -2.2 kBT for PRC2b upon adding a second complex.
- **Evidence pointer** Results section "Cooperative PRC2 binding loops DNA"; Figure 4A; Supplementary Figure S9
- **Concern** The cooperative effect is quantified by comparing free energy differences between one and two PRC2 complexes. However, the manuscript does not provide sufficient detail on how the free energy profiles were computed for the two-protein systems. The methods section mentions "in silico pulling" and "umbrella sampling" but does not describe the reaction coordinates, the sampling protocol, or the convergence criteria for the two-protein simulations. The structural clustering analysis identifies a "hairpin-like" structure in 60% of the PRC2f simulations, but the statistical uncertainty of this population estimate is not reported. Furthermore, the claim of "allosteric communication" implies a mechanistic explanation that is not directly demonstrated; the authors infer communication from the non-additive free energy changes but do not show a causal pathway.
- **Why it matters** The cooperative looping mechanism is the central novel claim of the manuscript. If the free energy calculations are not converged or the sampling is insufficient, the predicted cooperativity could be an artifact. The mechanistic interpretation of allosteric communication requires more direct evidence or at least a more careful discussion of alternative explanations.
- **Resolution test** The authors should provide detailed convergence analysis for the free energy calculations, including block averaging or bootstrap estimates of statistical uncertainty. The umbrella sampling protocol should be described in sufficient detail to be reproducible. The claim of allosteric communication should be supported by additional analyses, such as examining the correlation between the binding modes of the two complexes or performing simulations with mutations that disrupt the proposed communication pathway.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that single-molecule force spectroscopy experiments support PRC2-mediated DNA looping, with rupture events observed for PRC2 4mer but not for PRC2-AEBP2 5mer.
- **Evidence pointer** Results section "Single-molecule experiments support conformation-dependent DNA binding of PRC2"; Figure 6; Supplementary Figure S13
- **Concern** The single-molecule experiments are presented as supporting evidence for the computational predictions, but the manuscript provides limited experimental detail. The number of independent experiments, the number of molecules tested, the criteria for identifying rupture events, and the statistical significance of the difference between 4mer and 5mer conditions are not reported. The authors state that "rupture events can no longer be detected" for the 5mer, but this negative result could be due to insufficient sampling, different binding kinetics, or experimental artifacts rather than a genuine absence of looping. The manuscript also does not discuss potential alternative interpretations of the rupture events, such as non-specific DNA-protein interactions or experimental noise.
- **Why it matters** The experimental data are used to validate the computational predictions, but the current presentation does not provide sufficient evidence to distinguish between genuine PRC2-mediated looping and alternative explanations. The claim that AEBP2 regulates looping by blocking C2-DNA interactions requires experimental support that is not currently provided.
- **Resolution test** The authors should provide quantitative analysis of the force spectroscopy data, including the number of experiments, the frequency of rupture events, the distribution of rupture forces, and appropriate statistical tests comparing 4mer and 5mer conditions. Control experiments with non-specific proteins or mutated PRC2 complexes should be performed to rule out artifacts. The authors should also discuss the relationship between the timescales of the pulling experiments and the predicted stability of the looped states.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that "accessory proteins may regulate the genomic location of PRC2 by interfering with its DNA interactions" and that AEBP2's effect "can be partly understood from its association with the C2 domain, blocking C2 from DNA binding."
- **Evidence pointer** Abstract; Discussion section
- **Concern** The biological implications of the findings are discussed in broad terms, but the connection between the in vitro DNA looping observed here and PRC2 function in cells is speculative. The authors mention prior Hi-C experiments detecting PRC-mediated chromatin loops, but do not provide a detailed discussion of how their mechanism would operate in the context of chromatin, where PRC2 interacts with nucleosomes rather than bare DNA. The role of AEBP2 in regulating PRC2's genomic localization is likely more complex than simply blocking C2-DNA interactions, given that AEBP2 also affects PRC2's enzymatic activity and chromatin binding through other mechanisms.
- **Why it matters** The broader significance of the work depends on the relevance of the proposed mechanism to PRC2 function in vivo. If the authors cannot connect their in vitro observations to cellular processes, the impact of the study is substantially reduced.
- **Resolution test** The authors should provide a more nuanced discussion of how their findings relate to PRC2 function in chromatin, considering the differences between bare DNA and nucleosomal substrates. They should also discuss alternative mechanisms by which AEBP2 could regulate PRC2's genomic targeting and acknowledge the limitations of their in vitro system.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Methods section "Coarse-grained protein-DNA model"
- **Evidence pointer** Equation 1
- **Issue** The contact potential functional form is presented without sufficient context for readers unfamiliar with this type of potential. The meaning of the parameters W, η, and r0 is not fully explained, and the relationship between this potential and the electrostatic interactions mentioned in the text is unclear.
- **Required correction** Provide a brief explanation of the physical meaning of each parameter and how the contact potential complements the electrostatic term. Consider adding a schematic figure or a more detailed description in the supplementary information.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section "Cooperative PRC2 binding loops DNA"
- **Evidence pointer** Figure 5C
- **Issue** The correlation between the number of contacts of the first PRC2 and the loop length formed by the second PRC2 is presented as evidence for allosteric communication, but the statistical significance of this correlation is not reported. The figure appears to show a trend, but the scatter of the data points and the number of independent observations are not clear.
- **Required correction** Report the correlation coefficient and its statistical significance. If the correlation is weak or based on limited data, temper the claim of allosteric communication accordingly.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Discussion section
- **Evidence pointer** Discussion, paragraph 3
- **Issue** The discussion of the relationship between the current findings and prior Hi-C experiments is brief and does not fully address the potential discrepancies between in vitro DNA looping and in vivo chromatin organization. The authors mention that "PRC proteins mediated chromatin loops have been detected" but do not discuss whether the loop sizes and stability predicted here are consistent with those observed in cells.
- **Required correction** Expand the discussion to address the quantitative relationship between the predicted loop sizes and those observed in Hi-C experiments, and discuss potential reasons for any discrepancies.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section "Single-molecule force spectroscopy experiments"
- **Evidence pointer** Methods section
- **Issue** The experimental conditions for the force spectroscopy experiments are described briefly, but the buffer composition, temperature, and the specific pulling protocol (e.g., pulling speed, feedback mode) are not fully specified. This limits the reproducibility of the experiments.
- **Required correction** Provide complete experimental details, including buffer composition, temperature, pulling speed, and any other relevant parameters.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results section "Structural modeling of the PRC2 core complex"
- **Evidence pointer** Figure 1
- **Issue** The description of the three PRC2 conformations (PRC2b, PRC2f, PRC2d) is clear, but the figure labels and the relationship between the conformations and the experimental conditions under which they are observed could be clarified. The reader is left to infer which conformation corresponds to which experimental condition.
- **Required correction** Add a brief statement in the figure legend or text clarifying the relationship between the modeled conformations and the experimental conditions (e.g., presence or absence of AEBP2).

## Risk / unsupported claims
- The claim that "accessory proteins may regulate the genomic location of PRC2 by interfering with its DNA interactions" is speculative and not directly supported by the data presented, as the study does not examine PRC2 localization in cells.
- The claim of "allosteric communication" between PRC2 complexes through DNA is inferred from free energy calculations but is not directly demonstrated mechanistically.
- The statement that "the presented mechanisms on PRC2-DNA binding are robust" to force field parameters is only partially supported, as the authors show one comparison (with and without the statistical potential) but do not systematically vary other parameters.
- The absence of rupture events for PRC2 5mer in force spectroscopy is interpreted as consistent with weaker looping, but the authors acknowledge this could be due to experimental limitations; this negative result should not be over-interpreted.
- The quantitative agreement between simulated and experimental binding free energies for PRC2-DNA is based on a single comparison point and should be treated with caution given the limited validation set.