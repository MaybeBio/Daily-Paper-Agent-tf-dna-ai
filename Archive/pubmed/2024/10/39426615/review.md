## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, materials and methods, and supplementary figure references
- **Assessment boundary** Scientific content, methodological rigor, evidence quality, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors identify a stable folding intermediate in the RRM2 domain of TDP-43, characterize its residual structure using biophysical methods, and propose that a specific hydrophobic core involving V193, V195, and V232 stabilizes this intermediate state, with implications for TDP-43 misfolding and ALS pathogenesis
- **Visible evidence base** Far-UV CD, near-UV CD, tyrosine fluorescence, SEC-SAXS, NMR spectroscopy (HSQC, triple resonance assignments), steered molecular dynamics simulations, alanine scanning mutagenesis, and replica-averaged metadynamics
- **Missing materials affecting confidence** Full experimental details for SAXS data collection and analysis, complete NMR assignment tables, supplementary figures S1-S9, detailed fitting parameters for all thermodynamic models, and the full metadynamics simulation parameters

## Reviewer

### Overall assessment
This manuscript presents a comprehensive biophysical characterization of a folding intermediate in the RRM2 domain of TDP-43, combining multiple experimental and computational approaches. The work addresses a significant question in protein folding and neurodegeneration, and the combination of techniques is commendable. However, several concerns regarding data interpretation, the relationship between computational and experimental results, and the broader claims about disease relevance require careful consideration. The central claim that a specific hydrophobic core stabilizes the intermediate state is supported by the data, but the quantitative rigor and the strength of some conclusions need improvement.

### Who would be interested in the results, and why
Researchers in protein folding, biophysics, and structural biology would find this work valuable for understanding intermediate states in RNA recognition motifs. The ALS research community would be interested in the structural characterization of TDP-43 domains and the potential implications for misfolding mechanisms. Additionally, those studying hydrophobic core contributions to protein stability and folding landscapes would benefit from the methodological approach combining simulations with experimental validation.

### Major strengths
1. The combination of multiple orthogonal biophysical techniques (CD, fluorescence, SAXS, NMR) provides a robust experimental foundation
2. The integration of computational methods (SMD, metadynamics) with experimental validation through mutagenesis is well conceived
3. The identification of specific residues (V193, V195, V232) as critical for intermediate state stability offers a testable mechanistic model
4. The use of multiple secondary structure prediction algorithms from NMR chemical shifts strengthens the structural conclusions
5. The work addresses a biologically relevant question with potential implications for understanding TDP-43 pathology

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for structural characterization
- **Claim pointer** The authors claim that the intermediate state "consists of collapsed residual secondary structure localized to the N-terminal half of RRM2, while the C-terminus is largely disordered"
- **Evidence pointer** Figure 3B, Table S2, NMR section
- **Concern** The secondary structure predictions in the intermediate state rely on chemical shift analysis at 6.5 M urea, but the manuscript does not provide complete validation of these predictions. The authors note that the three algorithms differ in their predictions for β1 and β5, yet the conclusions are stated with considerable confidence. Additionally, the claim that the intermediate state is "collapsed" is based primarily on SAXS data, but the SAXS measurements at high urea concentrations may be complicated by urea-induced changes in the solvent background and potential preferential interactions.
- **Why it matters** The central structural model of the intermediate state underpins all subsequent interpretations about hydrophobic core stabilization and disease relevance. If the residual structure is not accurately characterized, the mechanistic conclusions about which contacts stabilize the intermediate would be compromised.
- **Resolution test** Provide a more detailed comparison of the three prediction algorithms with explicit discussion of discrepancies, and include validation of the SAXS data at high urea concentrations, possibly with additional controls or complementary techniques such as size-based methods.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational-experimental integration
- **Claim pointer** The authors state that "steered molecular dynamics simulations and mutagenesis studies yielded key stabilizing hydrophobic contacts that, when mutated to alanine, severely disrupt the overall fold of RRM2"
- **Evidence pointer** Figures 5-7, S6-S8, SMD section
- **Concern** The SMD simulations use a construct with three mutations (S191R, G192K, G200E) relative to the wild-type sequence, yet the manuscript does not adequately justify how these mutations affect the interpretation of the unfolding pathway. The authors also do not provide sufficient detail on the force-dependent behavior and whether the observed intermediate state in simulations corresponds to the same state characterized experimentally. The correlation between specific contact loss and the experimentally observed destabilization is inferred but not quantitatively demonstrated.
- **Why it matters** The computational results are used to identify specific contacts critical for intermediate stability, and these predictions are then tested experimentally. If the simulations do not faithfully represent the experimental system, the identified contacts may not be the true determinants of intermediate stability.
- **Resolution test** Provide a clear justification for the use of the mutated construct in simulations, demonstrate that the simulated intermediate state matches the experimentally characterized state (e.g., through structural overlap or contact analysis), and include a quantitative comparison of contact stability between simulations and experimental mutational effects.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Disease relevance claims
- **Claim pointer** The authors suggest that "these findings suggest a role for this RRM intermediate in normal TDP-43 function as well as serving as a template for misfolding and aggregation"
- **Evidence pointer** Discussion section
- **Concern** The connection between the biophysical characterization of an isolated RRM2 domain intermediate and the disease relevance in full-length TDP-43 is largely speculative. The manuscript does not provide direct evidence that this intermediate state is populated in cells, that it contributes to TDP-43 aggregation, or that it is relevant to ALS pathogenesis. The discussion of potential disease mechanisms is reasonable but not supported by experimental data presented in this work.
- **Why it matters** The broader significance of the work for the ALS field depends on the relevance of this intermediate state to disease. Overstating the disease implications without direct evidence could mislead readers and future research directions.
- **Resolution test** Either temper the disease-related claims to clearly distinguish speculation from experimentally supported conclusions, or provide additional evidence linking the intermediate state to cellular or pathological processes, such as studies in cell models or with disease-associated mutations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Thermodynamic analysis rigor
- **Claim pointer** The authors report thermodynamic parameters for the unfolding transitions, including ΔG values of 4.30±0.10 kcal mol−1 and 3.38±0.13 kcal mol−1 for the N⇆I and I⇆U transitions, respectively
- **Evidence pointer** Table 1, Table S4, Table S5, Methods section
- **Concern** The manuscript does not provide sufficient detail on the fitting procedures, including the choice of models, the handling of baselines, and the statistical treatment of the data. The use of a three-state model for the wild-type protein and two-state models for Class I mutants is described, but the criteria for model selection and the confidence in the parameter estimates are not fully documented. Additionally, the relationship between the urea and Gdn-HCl denaturation data is not clearly reconciled.
- **Why it matters** The thermodynamic parameters are used to support the claim that mutations destabilize the native state and increase intermediate population. If the fitting procedures are not rigorous, the quantitative conclusions about stability changes could be unreliable.
- **Resolution test** Provide complete details of the fitting procedures, including equations, baseline treatments, and statistical analysis. Include a comparison of fits with different models and a discussion of parameter uncertainties and correlations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1, Introduction
- **Issue** The description of the RRM2 topology and the location of the extra β-strand (β4) is somewhat confusing, particularly regarding the numbering of secondary structure elements and how they relate to the standard RRM fold.
- **Required correction** Clarify the secondary structure element labeling and provide a clearer schematic that highlights the unique features of RRM2 compared to canonical RRM domains.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological transparency
- **Affected element** SAXS analysis
- **Evidence pointer** Methods section, Figure 2C-D
- **Issue** The SAXS data analysis is described briefly, and the manuscript does not specify the software used, the fitting range for the Guinier approximation, or the quality metrics for the fits.
- **Required correction** Provide additional details on the SAXS data processing and analysis, including software, fitting ranges, and quality assessment criteria.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Mutational analysis
- **Evidence pointer** Table S4, Table S5, Figure 5
- **Issue** The number of replicates for the mutational studies and the statistical significance of the differences between mutants are not clearly reported.
- **Required correction** Specify the number of independent experiments and include appropriate statistical tests to support the claims about differential destabilization among mutants.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the potential role of the RRM2 intermediate in TDP-43 function and disease would benefit from a more thorough comparison with existing literature on TDP-43 folding, dynamics, and aggregation mechanisms.
- **Required correction** Expand the discussion to more comprehensively address how these findings relate to and extend previous studies on TDP-43 structure and function.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 6
- **Evidence pointer** Figure 6, S6
- **Issue** The representative structures shown in Figure 6 are described but the figure itself is not available for review. The description of conformational states I-VI would benefit from clearer structural representations.
- **Required correction** Ensure that the final figures clearly show the structural transitions described, with appropriate labels and possibly supplementary movies or additional views.

### Technical failings that need to be addressed before the case is established
1. The SMD simulations use a mutated construct (S191R, G192K, G200E) without adequate justification for how these mutations affect the interpretation of the unfolding pathway and the identified stabilizing contacts
2. The relationship between the computationally identified intermediate state and the experimentally characterized intermediate is not rigorously established
3. The SAXS data at high urea concentrations require additional validation to ensure that the observed changes in Rg are not artifacts of the denaturant conditions
4. The thermodynamic fitting procedures are not described in sufficient detail to assess the reliability of the reported parameters

### Assessment against Nature-style criteria
**Originality**: The work presents a novel combination of techniques applied to a specific question about TDP-43 RRM2 folding. The identification of specific hydrophobic contacts stabilizing an intermediate state is a valuable contribution, though the general concept of hydrophobic cores stabilizing folding intermediates is well established.

**Scientific importance**: The RRM2 domain of TDP-43 is biologically significant given its link to ALS. Understanding the structural basis of intermediate state stability could inform therapeutic strategies. However, the direct relevance to disease mechanisms remains speculative.

**Interdisciplinary readership**: The work bridges biophysics, computational biology, and neurobiology, making it potentially interesting to a broad audience. The methods are accessible to specialists, but the broader significance for non-specialists could be strengthened.

**Technical soundness**: The experimental approaches are generally sound, but the computational-experimental integration has gaps that need addressing. The thermodynamic analyses require more rigorous documentation. The structural characterization of the intermediate state would benefit from additional validation.

**Readability for nonspecialists**: The manuscript is generally well-written and logically organized. However, some sections, particularly the computational methods and the discussion of chemical shift-based secondary structure prediction, may be challenging for non-specialists. The abstract effectively communicates the key findings.

### Recommendation posture
Supportive if technical concerns are resolved. The manuscript presents a valuable contribution to understanding the RRM2 folding intermediate of TDP-43, with a well-designed combination of experimental and computational approaches. However, the concerns about the computational-experimental integration, the rigor of the thermodynamic analyses, and the overstatement of disease relevance need to be addressed before the conclusions can be fully accepted.

## Risk / unsupported claims
1. The claim that the intermediate state serves as a "template for misfolding and aggregation" in ALS is not directly supported by the data presented
2. The assertion that the identified hydrophobic contacts are "critical" for intermediate stability is based on computational predictions and limited mutational analysis, and the quantitative relationship between contact loss and destabilization is not fully established
3. The statement that the intermediate state "consists of collapsed residual secondary structure" is based on indirect measurements and would benefit from additional structural validation
4. The claim that the findings have implications for "therapeutic interventions" is speculative and not supported by the experimental data
5. The relationship between the urea-induced intermediate and any physiologically relevant state is not established, and the authors do not address whether this intermediate is populated under conditions relevant to cellular function or disease