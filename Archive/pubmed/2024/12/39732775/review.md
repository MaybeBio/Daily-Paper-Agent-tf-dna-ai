## Review setup
- **Input scope** Full manuscript text (Introduction, Results, Discussion, Conclusion, Materials and Methods) as provided by the user. Supplementary figures and tables are referenced but not supplied.
- **Assessment boundary** Scientific soundness, methodological rigor, internal consistency, and support of claims by the presented evidence. Editorial or stylistic issues are noted only where they affect comprehension or reproducibility.
- **Shared manuscript claim summary** The authors propose a hybrid in silico and in vitro workflow to identify natural compounds that activate Nrf2. They report in vitro screening of five Vietnamese medicinal plant extracts, machine learning model development and prediction of active compounds, molecular docking and dynamics of top hits, ADME/toxicity prediction, and LC-MS/MS-based chemical profiling of three active extracts. They identify corilagin as a lead compound.
- **Visible evidence base** Main text figures (Figures 1–4), Tables 1–3, and methodological descriptions. Supplementary Tables S1–S4 and Figures S1–S7 are referenced but not provided.
- **Missing materials affecting confidence** Supplementary information (Tables S1–S4, Figures S1–S7), raw data for in vitro assays, machine learning training and test datasets, docking pose coordinates, MD simulation trajectories, and LC-MS/MS raw spectra. These are essential for full verification of the reported results.

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful integrated workflow combining in vitro screening, machine learning, and computational structural analysis for identifying Nrf2-activating natural compounds. The in vitro data are straightforward and the machine learning model performance is reasonable. However, several methodological details are missing or unclear, and some claims in the Discussion extend beyond what the data can support. The identification of corilagin as a lead compound is plausible but not fully established without dose-response data or direct binding assays. The manuscript would benefit from clearer reporting of experimental parameters, additional validation of the computational predictions, and a more measured interpretation of the results.
- **Who would be interested in the results, and why** Researchers in natural product drug discovery, computational pharmacology, and oxidative stress biology. The hybrid workflow may be of interest to those seeking to integrate machine learning with experimental bioassays for compound screening. The specific findings on Vietnamese medicinal plants and corilagin may interest ethnopharmacologists and those studying Nrf2 activators for skin-related oxidative stress.
- **Major strengths** 1) The integration of multiple complementary approaches (in vitro, machine learning, docking, MD, ADME, LC-MS/MS) is commendable and reflects a modern screening paradigm. 2) The in vitro screening covers a reasonable panel of extracts and sub-fractions with appropriate controls. 3) The machine learning model performance metrics are reported transparently. 4) The LC-MS/MS chemical profiling provides a direct link between computational predictions and actual extract composition.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Experimental design and controls
  - **Claim pointer** The in vitro screening results are used to identify extracts with Nrf2-activating potential, and the positive control tBHQ at 10 µM is reported to increase Nrf2 activity by over 450%.
  - **Evidence pointer** Figure 1, Results section "In vitro screening", Methods section "In vitro Nrf2 activity screening assay"
  - **Concern** The in vitro assay is described as a reporter gene assay, but the manuscript does not report whether the extracts were tested for interference with the luciferase assay itself (e.g., via luciferase inhibition or autofluorescence). Natural product extracts, particularly complex mixtures, are known to cause false positives or negatives in reporter assays. Additionally, the concentration of 100 µg/mL for crude extracts is high and may cause nonspecific effects or cytotoxicity, which is not addressed. The manuscript does not report cell viability data alongside the Nrf2 activity data, despite the Methods stating that viability was measured.
  - **Why it matters** Without evidence that the observed Nrf2 activity is specific and not confounded by assay interference or cytotoxicity, the primary in vitro screening results may not be reliable. This is the foundation upon which the rest of the study is built.
  - **Resolution test** Provide cell viability data for all tested extracts and sub-fractions. Include a control experiment demonstrating that the extracts do not inhibit luciferase activity directly (e.g., by spiking recombinant luciferase with extract). If possible, include a dose-response curve for the most active extracts to demonstrate specificity and rule out nonspecific effects.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Machine learning methodology and validation
  - **Claim pointer** The SVM model with Morgan3 fingerprints achieved the highest performance (Accuracy 0.87, Sensitivity 0.88, Specificity 0.86, AUC 0.93, F1 0.89) and was used to predict 16 active compounds from a natural product library.
  - **Evidence pointer** Results section "Machine learning model performance", Tables S1 and S2 (not provided), Methods section "Data collection and preparation for machine learning" and "ML model optimization and testing"
  - **Concern** The manuscript does not report the size of the training and test sets, the source of the natural product library used for prediction, or the criteria for selecting the 16 predicted actives. The claim that the Tanimoto index between training and test compounds is less than 0.26 is presented as evidence of diversity, but the number of compounds in the test set (99) and the training set (613) is only mentioned in passing. More critically, the manuscript does not report any external validation of the model predictions, such as testing the predicted compounds in the in vitro assay. The 16 predicted compounds are not listed in the main text, and their docking scores are only partially shown in Table 1.
  - **Why it matters** The machine learning model is a central component of the hybrid workflow. Without clear reporting of dataset composition, model selection criteria, and external validation, the predictive power of the model cannot be assessed. The claim that the model successfully predicted active compounds is not supported by experimental confirmation.
  - **Resolution test** Provide the full dataset composition (training and test sizes, class balance), the list of 16 predicted compounds, and the docking scores for all of them. Most importantly, test the predicted compounds in the in vitro Nrf2 assay to confirm their activity. If this is not feasible, clearly state that the predictions are computational only and require experimental validation.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretation of molecular dynamics results
  - **Claim pointer** The MD simulations show that the Keap1/Nrf2-geraniin complex has higher RMSD values (1.5–2.25 Å) than the other complexes, and the authors interpret the overall results as indicating stable binding of the ligands to Keap1.
  - **Evidence pointer** Results section "Molecular dynamics simulation", Figures 3 and 4
  - **Concern** The RMSD of the geraniin complex is higher than that of the apo protein, which could indicate either a conformational change upon binding or poor stability of the complex. The authors do not discuss this distinction. The RMSF analysis shows elevated fluctuations for the geraniin complex at residues 570–600, but the functional significance of these residues is not discussed. The FEL analysis is presented qualitatively, and the claim that "the binding of three selected compounds hindered the motion of the Keap1 backbone atoms" is not directly supported by the data shown. The PCA results are only mentioned in the text and the figure is in the supplementary materials.
  - **Why it matters** The MD simulations are used to support the claim that the selected compounds bind stably to Keap1. If the interpretation is incorrect or over-stated, the conclusion that these compounds are promising leads is weakened.
  - **Resolution test** Provide quantitative analysis of the MD trajectories, including binding free energy calculations (e.g., MM-PBSA), per-residue energy decomposition, and a more detailed discussion of the structural significance of the fluctuating regions. Clarify whether the higher RMSD of the geraniin complex indicates a stable but distinct binding mode or an unstable complex.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Chemical profiling and compound identification
  - **Claim pointer** LC-MS/MS analysis identified compounds in the active extracts, including corilagin in P. amarus stems, which was the sole sample to enhance Nrf2 expression.
  - **Evidence pointer** Results section "LC-QTOF-MS/MS: based chemical profiles", Table 3, Discussion section
  - **Concern** The LC-MS/MS analysis identified compounds in the crude extracts, but the manuscript does not report quantitative data (e.g., relative abundance) or confirm the identity of the compounds with authentic standards. The claim that corilagin was the "sole sample to enhance Nrf2 expression" is confusing, as it suggests that corilagin was the only compound in the P. amarus extract that was active, but this is not directly tested. The correlation between the presence of corilagin in the extract and the observed Nrf2 activity is circumstantial.
  - **Why it matters** The identification of corilagin as a lead compound is a key conclusion. Without quantitative data and confirmation of compound identity, the link between the computational predictions, the chemical profiling, and the biological activity is not firmly established.
  - **Resolution test** Provide quantitative MS data (e.g., peak areas) for the identified compounds. If possible, test purified corilagin in the in vitro Nrf2 assay to directly confirm its activity. Alternatively, clearly state that the identification is tentative and requires further confirmation.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and reproducibility
  - **Affected element** Methods section "In vitro Nrf2 activity screening assay"
  - **Evidence pointer** Methods section, location not provided
  - **Issue** The formula for calculating relative Nrf2 activity is presented in a LaTeX format that may not render correctly in all contexts. The description of the assay could be clearer regarding the exact timing of treatment, the number of replicates, and the statistical analysis used.
  - **Required correction** Ensure the formula is properly formatted. Provide details on the number of experimental replicates, the statistical tests used, and how significance was determined (e.g., p-values, error bars in figures).
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Table 1
  - **Evidence pointer** Table 1, location not provided
  - **Issue** The table lists docking scores and amino acid residues for 16 compounds, but the compounds are only identified by ID numbers. The chemical names or structures are not provided in the main text.
  - **Required correction** Provide the chemical names or structures of the 16 compounds, either in the table or in a supplementary table, to allow readers to assess the chemical diversity of the predicted actives.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Language and terminology
  - **Affected element** Throughout the manuscript
  - **Evidence pointer** Various sections, location not provided
  - **Issue** There are several instances of awkward phrasing and grammatical errors (e.g., "zhiromes" instead of "rhizomes" in the Results section, "binded" instead of "bound" in the Results section). Some sentences are overly long and difficult to follow.
  - **Required correction** A thorough language edit is recommended to improve clarity and readability.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness of reporting
  - **Affected element** Methods section "Molecular dynamics (MD) simulations"
  - **Evidence pointer** Methods section, location not provided
  - **Issue** The methods state that the CHARMS-36 force field was used, but the correct name is CHARMM36. The description of the ligand topology preparation is vague ("using appropriate python codes to manually include ligands topology").
  - **Required correction** Correct the force field name. Provide more detail on the ligand parameterization process, including the software and any validation steps.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Figure quality
  - **Affected element** Figure 4
  - **Evidence pointer** Figure 4, location not provided
  - **Issue** The FEL plots are described as having a color gradient from blue (minimum energy) to red (maximum energy), but the figure appears to be in grayscale in the provided text. This makes the interpretation difficult.
  - **Required correction** Ensure the figure is in color or provide a grayscale-compatible representation with clear labels.
- **Technical failings that need to be addressed before the case is established** 1) Lack of evidence for assay specificity (no luciferase interference controls, no cytotoxicity data). 2) Incomplete reporting of machine learning dataset and lack of experimental validation of predicted compounds. 3) Over-interpretation of MD simulation results without quantitative binding free energy analysis. 4) Tentative compound identification without authentic standards or quantitative data.
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The combination of machine learning, docking, MD, and in vitro assays is not entirely novel, but the specific application to Vietnamese medicinal plants and the integration of LC-MS/MS adds some originality.  
  *Scientific importance*: Moderate. Nrf2 activators are of interest for oxidative stress-related diseases, and the identification of new natural leads is valuable. However, the study is largely exploratory and does not provide deep mechanistic insights.  
  *Interdisciplinary readership*: The work spans computational chemistry, pharmacology, and natural product chemistry, which may appeal to a broad audience. However, the depth in each area is limited.  
  *Technical soundness*: The in vitro and computational methods are generally sound, but key details are missing (as noted above). The lack of experimental validation of the computational predictions is a significant weakness.  
  *Readability for nonspecialists*: The manuscript is generally readable, but some sections (e.g., MD simulation analysis) may be challenging for readers without a computational background. The language could be improved for clarity.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a potentially useful workflow and identifies a plausible lead compound, but the current evidence is insufficient to fully support the claims. The authors should address the major concerns, particularly the assay specificity, machine learning validation, and MD interpretation, before the case is established.

## Risk / unsupported claims
- The claim that the machine learning model "successfully predicted 16 active compounds" is unsupported without experimental validation of these predictions.
- The claim that corilagin is a promising Nrf2 activator is not directly supported by the data, as the compound was not tested in isolation.
- The interpretation that the selected compounds "hindered the motion of the Keap1 backbone atoms" is not quantitatively supported by the presented MD data.
- The statement that "the water fraction of P. sarmentosum roots and O. indicum stems exhibited an outstanding ability to enhance over 1000% of Nrf2 activity" is based on a single concentration (100 µg/mL) and lacks dose-response data.
- The ADME/toxicity predictions are based solely on in silico tools and are presented without acknowledgment of their limitations.