## Review setup
- **Input scope** Full manuscript text (abstract, introduction, computational methods, results and discussion, conclusions) as provided by the user. No supplementary material, figures, or tables were included in the supplied text.
- **Assessment boundary** The review is limited to the content of the provided manuscript text. Claims, methods, and results are assessed based solely on what is written in the supplied material. No external literature, experimental data, or supplementary information was available for verification.
- **Shared manuscript claim summary** The authors use molecular dynamics (MD) and alchemical free energy (AFE) simulations to compute relative binding free energies of seven flavonoids in the transcriptional regulator TtgR from Pseudomonas putida DOT-T1E. They report distinct binding geometries, interaction patterns, and dynamics, and propose that structural features such as ring planarity and substituent patterns modulate binding affinity. They also suggest that artocarpin is the most potent binder and could be a subnanomolar ligand.
- **Visible evidence base** The manuscript text includes descriptions of methods, results, and discussion, with references to figures (Figures 1-10), tables (Tables 1, S1-S6), and supplementary material. However, none of these figures, tables, or supplementary files were provided to the reviewer. Only the textual narrative is available for assessment.
- **Missing materials affecting confidence** All figures, tables, and supplementary information are missing. This includes the key data supporting the free energy calculations (Table 1, Figure 4, Figure 5), interaction analyses (Figures 6-8, Table S2), and dynamics results (Figures 9-10, Tables S3-S5). Without these, the quantitative claims and the validity of the computational results cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript presents a computational study of flavonoid binding to the transcriptional regulator TtgR, combining MD and AFE simulations. The topic is relevant to antimicrobial resistance and the molecular basis of ligand recognition in the TetR family. The methodological approach is appropriate and the authors demonstrate awareness of best practices in alchemical free energy calculations, including convergence checks and error estimation. However, the manuscript as provided is incomplete for a full evaluation, as all figures, tables, and supplementary data are absent. The textual description suggests a coherent study, but the core quantitative results and their statistical robustness cannot be assessed. The claims regarding binding free energy trends and the prediction of artocarpin as a subnanomolar binder are plausible but not verifiable from the supplied material. The writing is generally clear, though some sections are dense and would benefit from improved accessibility for a broad readership.
- **Who would be interested in the results, and why** Researchers in computational chemistry, biophysics, and structural biology, particularly those studying protein-ligand interactions, efflux pump regulation, and the TetR family of transcriptional regulators. The study also has potential relevance for medicinal chemists interested in flavonoid-based antimicrobial agents and for microbiologists studying resistance mechanisms in Pseudomonas putida. The methodological details on AFE simulations may interest practitioners in free energy calculations.
- **Major strengths** The study addresses a biologically and clinically relevant problem, namely antimicrobial resistance, through a well-established computational framework. The combination of MD and AFE simulations is appropriate for the research question. The authors include convergence analyses, error estimates, and comparisons between MBAR and TI methods, which are good practices. The systematic comparison of seven structurally related flavonoids allows for a structure-activity relationship analysis. The discussion of interaction types, including CH/π and π-π interactions, adds mechanistic insight.
- **Major Concerns** The primary concern is the lack of access to the actual data, figures, and tables, which prevents verification of the quantitative claims. Additionally, the manuscript does not provide a clear statement of the force field validation or the sensitivity of the results to the chosen parameters. The prediction of artocarpin as a subnanomolar binder is based on a single experimental reference point and extrapolation, which may be overinterpreted. The manuscript also does not discuss potential limitations of the AFE approach for ligands with significant conformational flexibility, such as naringenin. The absence of a comparison with experimental binding affinities for more than one compound limits the validation of the computational predictions.
- **Minor Comments** The manuscript would benefit from a more explicit statement of the novelty of the work relative to previous computational studies on TtgR. The introduction could be streamlined to focus more directly on the gap the study addresses. The methods section is detailed but could be more accessible to non-specialists, particularly the description of the AFE setup. The discussion of the dynamics results is somewhat brief and could be expanded to connect the observed motions to functional implications. The conclusion section is somewhat repetitive and could be tightened.
- **Technical failings that need to be addressed before the case is established** The manuscript does not provide the actual free energy values, error bars, or convergence plots in the text, making it impossible to assess the reliability of the results. The claim that artocarpin could be a subnanomolar binder is not supported by direct calculation or experimental data within the provided text. The manuscript does not discuss the potential impact of the choice of force field or water model on the results. The lack of a clear validation against experimental data for multiple ligands weakens the case for the predictive power of the simulations.
- **Assessment against Nature-style criteria** Originality: The study is incremental, applying established methods to a specific system. The novelty lies in the systematic comparison of flavonoids, but the approach is not methodologically new. Scientific importance: The topic is important, but the findings are largely confirmatory of known interaction patterns in TtgR. The prediction of artocarpin as a high-affinity binder is interesting but requires experimental validation. Interdisciplinary readership: The work is primarily of interest to computational chemists and structural biologists; the broader antimicrobial resistance community may find the results relevant but the technical focus may limit appeal. Technical soundness: The methods are appropriate and the authors demonstrate good practices, but the lack of data prevents a full assessment of the technical execution. Readability for nonspecialists: The manuscript is written in a technical style that may be challenging for readers outside the computational biophysics field. The abstract and introduction are accessible, but the methods and results sections are dense.
- **Recommendation posture** Supportive if technical concerns are resolved. The study has merit and the methodological approach is sound, but the manuscript as provided is incomplete and the key quantitative results are not verifiable. The authors should provide the missing data and address the concerns regarding validation and interpretation before the case is fully established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript reports relative binding free energies (ΔΔGbind) for seven flavonoids, with values ranging over 7.32 kcal/mol and standard errors within 0.16 kcal/mol.
- **Evidence pointer** Table 1, Figure 4, Figure 5, Table S1, Table S6 (none provided)
- **Concern** The core quantitative results of the study, namely the ΔΔGbind values and their associated errors, are not presented in the text. The authors reference Table 1 and Figure 4, but these are not available to the reviewer. Without the actual numbers, the magnitude of the reported effects, the statistical significance of the differences between ligands, and the convergence of the calculations cannot be assessed. The claim that artocarpin is the most potent binder with a ΔΔGbind of -7.32 kcal/mol relative to chrysin is a central finding, but its reliability cannot be evaluated.
- **Why it matters** The entire scientific case of the manuscript rests on the accuracy and precision of the free energy calculations. If the data are not available for scrutiny, the conclusions are unsupported. The reader cannot determine whether the differences between ligands are meaningful or within the noise of the method.
- **Resolution test** The authors should provide the full data in the manuscript or supplementary material, including the ΔΔGbind values for all pairwise comparisons, the standard errors, and the convergence plots. The data should be presented in a way that allows the reader to verify the claims independently.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation
- **Claim pointer** The authors state that the predicted ΔΔGbind value for quercetin relative to naringenin (-0.36 kcal/mol) aligns closely with isothermal titration calorimetry experiments, which report a difference of 0.39 ± 0.02 kcal/mol.
- **Evidence pointer** Section "Relative binding free energies of the flavonoids", reference 7
- **Concern** The manuscript uses a single experimental comparison to validate the computational approach. While this is a positive step, it is insufficient to establish the predictive power of the method across the range of ligands studied. The agreement for one pair of compounds could be fortuitous, and the authors do not discuss the uncertainty in the experimental measurement or the potential sources of systematic error in the simulations. Furthermore, the extrapolation from this single validation to the prediction that artocarpin is a subnanomolar binder is a significant leap that is not supported by the data presented.
- **Why it matters** The credibility of the computational predictions depends on their ability to reproduce known experimental results. A single data point is not a robust validation. The claim about artocarpin's affinity is a strong statement that could mislead experimentalists if it is not well-founded.
- **Resolution test** The authors should either provide additional experimental comparisons for other ligands or temper the claims about artocarpin's affinity. If no further experimental data are available, the manuscript should clearly state the limitations of the validation and avoid overinterpretation of the predicted binding affinity.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological rigor
- **Claim pointer** The authors state that the AFE simulations use the AMBER ff14SB and GAFF2 force fields, the TIP4P/Ew water model, and the ACES approach for enhanced sampling.
- **Evidence pointer** Section "Alchemical free energy simulations"
- **Concern** The manuscript does not provide sufficient detail on the setup of the AFE simulations to allow for reproducibility. Key parameters such as the number of λ windows, the total simulation time per window, the equilibration protocol, and the specific implementation of the ACES method are not described in sufficient detail. The authors mention that the first 0.5 ns of the production runs were discarded, but the total production time is not stated. The choice of the common core and softcore regions is described qualitatively, but the specific atoms involved in each transformation are not listed.
- **Why it matters** Reproducibility is a cornerstone of scientific research. Without a detailed description of the simulation parameters, other researchers cannot replicate the calculations or assess the quality of the results. The lack of detail also makes it difficult to evaluate whether the simulations were sufficiently converged.
- **Resolution test** The authors should provide a complete description of the simulation setup, including all relevant parameters, in the methods section or in the supplementary material. This should include the number of λ windows, the simulation time per window, the equilibration protocol, and the specific settings for the ACES method.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The authors conclude that "both aromaticity and the presence of hydroxyl substituent groups play important roles in facilitating the interactions between flavonoids and TtgR" and that "TtgR consistently demonstrates an affinity for molecules with aromatic components."
- **Evidence pointer** Section "Conclusions"
- **Concern** The conclusions are drawn from the analysis of only seven compounds, which may not be sufficient to establish general principles about the determinants of binding affinity. The authors do not perform a systematic structure-activity relationship analysis, such as a quantitative comparison of the contributions of different substituents or a statistical analysis of the correlation between structural features and binding free energies. The statement about the importance of aromaticity is based on qualitative observations of the binding poses and interaction patterns, but no quantitative measure of the contribution of π-π or CH/π interactions to the overall binding free energy is provided.
- **Why it matters** The conclusions are presented as general insights into ligand recognition by TtgR, but they are based on a limited dataset and qualitative analysis. Overgeneralization could lead to incorrect assumptions about the design of new ligands or the interpretation of experimental results.
- **Resolution test** The authors should either expand the analysis to include a more systematic evaluation of the contributions of different structural features or temper the conclusions to reflect the limited scope of the study. A quantitative decomposition of the binding free energy into individual interaction terms would strengthen the claims.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction
- **Evidence pointer** Section "Introduction"
- **Issue** The introduction provides a general background on antimicrobial resistance and efflux pumps but could be more focused on the specific gap the study addresses. The transition from the general topic to the specific study of flavonoids in TtgR is somewhat abrupt.
- **Required correction** The authors should briefly state what is currently unknown about flavonoid binding to TtgR and how this study addresses that gap, to better frame the significance of the work.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section "Molecular interactions between flavonoids and the TtgR transcriptional regulator"
- **Evidence pointer** Section "Molecular interactions between flavonoids and the TtgR transcriptional regulator"
- **Issue** The description of the binding poses and interaction patterns is dense and relies heavily on references to figures that are not provided. Without the figures, the textual description is difficult to follow.
- **Required correction** The authors should provide a more self-contained description of the key interactions, including the specific residues involved and the nature of the interactions, so that the text can be understood without the figures.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section "Confined flavonoid dynamics in the active site of TtgR"
- **Evidence pointer** Section "Confined flavonoid dynamics in the active site of TtgR"
- **Issue** The section on dynamics is brief and does not fully explain the functional implications of the observed restricted motions. The connection between the dynamics and the binding affinity or specificity is not clearly articulated.
- **Required correction** The authors should expand the discussion to explain how the restricted dynamics relate to the stability of the bound complex and what this means for the biological function of TtgR.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Language
- **Affected element** Throughout
- **Evidence pointer** Throughout the manuscript
- **Issue** There are several instances of awkward phrasing and minor grammatical errors, such as "The position restrained were applied" and "a wide arrange of favorable interactions."
- **Required correction** The manuscript should be carefully proofread to correct grammatical errors and improve the flow of the text.

## Risk / unsupported claims
- The claim that artocarpin could be a subnanomolar binder of TtgR is not supported by direct calculation or experimental data within the provided text. This is an extrapolation based on a single experimental reference point and should be presented as a hypothesis rather than a prediction.
- The statement that "both aromaticity and the presence of hydroxyl substituent groups play important roles" is a qualitative conclusion that is not quantitatively supported by the data presented.
- The claim that the predicted ΔΔGbind values align closely with experimental data is based on a single comparison and cannot be generalized to the other ligands.
- The manuscript states that "in no cases were there statistically significant differences between the MBAR and TI free energy estimates," but the actual values and statistical tests are not provided, making this claim unverifiable.
- The assertion that the simulations reveal "distinct binding geometries and free energies" is plausible but cannot be verified without the figures and tables.