## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided
- **Assessment boundary** Scientific claims, methodology, evidence quality, and internal consistency based solely on the supplied text
- **Shared manuscript claim summary** The authors report that AlphaFold 2 (AF2) frequently predicts confident but unrealistic β-solenoid structures for artificial perfect repeat sequences, whereas AlphaFold 3 (AF3), ESMFold, and RoseTTAFold-All-Atom (RFAA) do not share this tendency. They support this with structural classification, validation scores, disorder predictions, molecular dynamics simulations, and comparisons to natural repeat proteins.
- **Visible evidence base** Text descriptions of results, figures referenced (Figures 1-15), tables referenced (Table S1), methods descriptions
- **Missing materials affecting confidence** Figures and tables themselves are not provided; numerical data (pLDDT values, TM-scores, Verify3D scores, RMSD values) are only described qualitatively; sequence details and exact statistical analyses are not available; supplementary materials are referenced but not included

## Reviewer
- **Overall assessment** This manuscript addresses a potentially important limitation of AF2 in the context of perfect repeat sequences. The observation that AF2 can produce confident but implausible β-solenoid predictions for random repeat sequences is interesting and could have implications for interpreting structure predictions of natural repeat proteins. However, the evidence as presented is largely qualitative, with key quantitative data relegated to figures that are not available for assessment. The manuscript would benefit from clearer statistical treatment, more systematic analysis, and a more rigorous comparison across methods. The claim that this is a specific AF2 bias, rather than a general limitation of structure prediction methods, requires stronger support given the variability in how different methods handle low-complexity or repetitive sequences.
- **Who would be interested in the results, and why** Researchers using AF2 for structure prediction of repeat proteins, particularly those studying mucins, adhesins, and other proteins with low-complexity or repetitive regions. The work also has relevance for the broader community assessing the reliability of deep learning-based structure prediction tools, and for developers of such tools who may need to address systematic biases. The findings could inform how structural biologists interpret AF2 predictions for proteins with unusual sequence properties.
- **Major strengths** The manuscript addresses a timely and important question about the reliability of AF2 predictions for a specific protein class. The use of multiple complementary approaches (structural classification, validation tools, alternative prediction methods, disorder predictions, MD simulations) is commendable. The comparison with natural repeat proteins adds practical relevance. The authors are appropriately cautious in their conclusions and acknowledge limitations of their study.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The observation of a potential AF2 bias for β-solenoids in perfect repeat sequences is novel and not widely documented. Scientific importance: Moderate to high, as it identifies a potential systematic error in a widely used tool, with implications for interpreting predictions of natural repeat proteins. Interdisciplinary readership: The topic is of interest to structural biologists, computational biologists, and bioinformaticians, but the presentation is somewhat narrow and may not attract a broad interdisciplinary audience. Technical soundness: The methods are appropriate but the analysis is largely qualitative; quantitative rigor is lacking in several places. Readability for nonspecialists: The manuscript is generally readable but assumes familiarity with structure prediction tools and validation metrics; some sections could be clearer for a general scientific audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core observation is interesting and potentially important, but the evidence needs to be presented more rigorously and quantitatively to establish the case convincingly.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that AF2 frequently predicts confident β-solenoid structures for random perfect repeat sequences, with 32 of 78 models classified as β-solenoids.
- **Evidence pointer** Results section, Figure 2, Figure S1
- **Concern** The classification of β-solenoid structures relies on STRPsearch with an E-value threshold of 0.1-10.0, but the authors do not report how many models were classified with high confidence versus borderline E-values. The manual selection of classifiers for models with no or multiple classifications introduces potential subjectivity. Furthermore, the claim that 32 of 78 (41%) proteins were predicted as β-solenoids is presented without confidence intervals or statistical context. The authors also do not report how many of these 32 were classified as "problematic" based on their criteria, making it difficult to assess the prevalence of the alleged bias.
- **Why it matters** The central claim of the manuscript depends on the reliability and objectivity of the structural classification. If the classification is uncertain or subjective, the prevalence of β-solenoid predictions may be overestimated, weakening the core argument.
- **Resolution test** Provide a breakdown of STRPsearch E-values for all 78 models, report inter-rater reliability for manual classifications, and present the number of β-solenoid predictions with confidence intervals. Ideally, use an additional independent classification method to confirm the β-solenoid assignments.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that AF2 assigns high confidence (pLDDT >70) to many β-solenoid models that are implausible based on Verify3D scores and internal charged residue stacking.
- **Evidence pointer** Results section, Figures 3, 5, 6
- **Concern** The relationship between pLDDT and Verify3D scores is described qualitatively. The authors state that 20 of 32 β-solenoid models received an average Verify3D score <0.1, and 16 of these had pLDDT >70, but no statistical analysis is provided to show whether this association is significant. The threshold of 0.1 for Verify3D is adopted based on analysis of only seven crystal structures, three of which failed categorically, suggesting the threshold may not be robust. The authors do not report the distribution of Verify3D scores for the crystal structures versus the models, nor do they provide a statistical comparison.
- **Why it matters** The claim that AF2 produces confident but unrealistic predictions depends on demonstrating a systematic discrepancy between AF2 confidence and structural plausibility. Without quantitative evidence, the association could be coincidental or driven by a few outliers.
- **Resolution test** Provide a scatter plot of pLDDT versus Verify3D score for all 32 β-solenoid models and the seven crystal structures, with statistical tests (e.g., correlation, t-test) to compare the two groups. Report the distribution of Verify3D scores and justify the threshold with a larger set of known β-solenoid structures.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that molecular dynamics simulations demonstrate instability of AF2-predicted β-solenoid models with internal charged residue stacking, compared to a natural β-solenoid crystal structure.
- **Evidence pointer** Methods, Results section, Figure 14
- **Concern** The MD simulations are described for only two AF2 models and one crystal structure. The authors report that the models became twisted or unfolded during 1 µs simulations, but no quantitative metrics (e.g., RMSD over time, radius of gyration, secondary structure content) are provided. The choice of force field (CHARMM36) and simulation parameters are described, but the analysis is qualitative. The authors do not report whether the simulations were replicated, nor do they provide error estimates. The comparison to a single crystal structure is insufficient to establish that the instability is specific to AF2 models rather than a general property of β-solenoids in MD simulations.
- **Why it matters** The MD results are used to support the claim that AF2 predictions are unrealistic. Without quantitative analysis and appropriate controls, the instability could be an artifact of the simulation setup or a general feature of β-solenoid proteins.
- **Resolution test** Provide quantitative MD analysis (e.g., RMSD, RMSF, secondary structure over time) for all simulated systems, include at least one additional natural β-solenoid as a control, and report replicate simulations with statistical measures of variability.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that alternative methods (AF3, ESMFold, RFAA) do not share AF2's tendency to predict confident β-solenoids for perfect repeat sequences, and that this disagreement supports the hypothesis of an AF2-specific bias.
- **Evidence pointer** Results section, Figures 7-10
- **Concern** The comparison across methods is described qualitatively. The authors state that ESMFold and AF3 frequently disagreed with AF2 in structure, pLDDT, or both, but no quantitative metrics (e.g., TM-score distributions, pLDDT comparisons) are provided. The claim that AF3 and ESMFold predict disordered structures for these sequences is based on visual inspection of figures. The authors do not report how many of the 32 sequences showed disagreement, nor do they provide statistical tests to show that the differences are significant. The observation that AF3 sometimes predicts long helical structures is noted but not systematically analyzed.
- **Why it matters** The claim that this is an AF2-specific bias, rather than a general limitation of structure prediction methods, is central to the manuscript's significance. Without quantitative comparison, the differences between methods could be within normal variation or due to differences in how methods handle low-complexity sequences.
- **Resolution test** Provide quantitative comparisons, such as TM-score distributions between AF2 and each alternative method, pLDDT distributions for each method, and statistical tests (e.g., paired t-tests, Wilcoxon tests) to establish significant differences. Report the proportion of sequences where methods disagree and the nature of the disagreements.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that AF2 predicts "confident but unrealistic β-solenoid structures" but does not define what constitutes "unrealistic" in this context. The term is used throughout the manuscript but is only operationally defined later in the results section.
- **Required correction** Briefly define the criteria for "unrealistic" in the abstract, such as internal charged residue stacking or low Verify3D scores, to set expectations for the reader.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction
- **Evidence pointer** Introduction, paragraph 3
- **Issue** The introduction mentions that AF2 was used to predict structures of new β-solenoids in 2023 (Mesdaghi et al., 2023), but does not explain why this prior work did not identify the bias described here. This is a missed opportunity to contextualize the novelty of the current findings.
- **Required correction** Add a sentence explaining how the current work extends or differs from the 2023 study, particularly regarding the identification of the β-solenoid bias.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Methods, Sequence generation
- **Evidence pointer** Methods, Sequence & model generation
- **Issue** The random sequence generation uses equal frequency for each amino acid, which the authors acknowledge in the conclusions but not in the methods. This is an important detail that affects the generalizability of the findings to natural proteins, where amino acid frequencies are not equal.
- **Required correction** State explicitly in the methods that amino acids were sampled with equal frequency, and discuss in the discussion section how this might affect the relevance to natural sequences.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Methods, MD simulations
- **Evidence pointer** Methods, All-atom molecular dynamics with GROMACS
- **Issue** The methods describe the simulation protocol but do not specify the temperature coupling algorithm, pressure coupling, or the equilibration procedure in detail. This makes it difficult to reproduce the simulations.
- **Required correction** Provide full simulation parameters, including thermostat and barostat algorithms, coupling constants, and the specific steps of the equilibration protocol.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, HHPred search
- **Evidence pointer** Results, HHPred search section
- **Issue** The authors note that only three of 32 sequences produced significant hits in HHPred searches, but do not discuss what this means for the interpretation of the other 29 sequences. If most sequences have no similarity to known proteins, this strengthens the argument that AF2 is predicting structures de novo, but this point is not made explicitly.
- **Required correction** Add a sentence interpreting the low hit rate, noting that the majority of sequences have no detectable similarity to known proteins, which supports the idea that AF2 is generating novel predictions.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Conclusions
- **Evidence pointer** Conclusions & further studies
- **Issue** The conclusions section is somewhat repetitive of the results and could be more focused on the broader implications and future directions. The discussion of why AF2 might have this bias is speculative and could be more clearly separated from the conclusions.
- **Required correction** Streamline the conclusions to focus on the key findings and their implications, and move the speculative discussion of mechanisms to a separate paragraph or to the discussion section.

## Risk / unsupported claims
- The claim that AF2 has a "blind spot" for β-solenoids in perfect repeat sequences is supported by the data presented, but the prevalence and generalizability of this bias are not quantitatively established.
- The claim that alternative methods (AF3, ESMFold, RFAA) do not share this bias is based on qualitative comparisons and requires quantitative support.
- The assertion that the MD simulations demonstrate instability of AF2 models is based on only two simulations without quantitative metrics or appropriate controls.
- The claim that this bias may impact prediction of natural repeat proteins is speculative and based on limited analysis of mucin proteins; the authors acknowledge this but do not provide systematic evidence.
- The statement that AF2 "effectively learned an energy function" (Roney & Ovchinnikov, 2022) is used to explain the bias but is not directly tested in this manuscript.
- The relevance of the findings to natural proteins is uncertain given the use of random sequences with equal amino acid frequencies, which do not reflect natural sequence composition.