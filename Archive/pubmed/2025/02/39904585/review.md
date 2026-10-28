## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results and discussion, conclusions, and materials and methods
- **Assessment boundary** Scientific claims, methodological soundness, internal consistency, and support of conclusions by presented evidence
- **Shared manuscript claim summary** The authors propose that binding of EndoIII to dsDNA stabilizes the oxidized [4Fe4S] cluster through structural reorganization, as evidenced by FTIR spectral shifts, DFT calculations, and machine learning predictions of binding distances, with a 150 mV electrochemical stabilization potential correlating to DNA-binding properties
- **Visible evidence base** FTIR spectra (mid-IR and far-IR), DFT calculations on a [4Fe4S]2+ cluster model, machine learning regression results, thermodynamic calculations, and reference to PDB structure 1P59
- **Missing materials affecting confidence** Raw spectral data, machine learning training details and hyperparameters, experimental replicates and error analysis, direct electrochemical measurements supporting the 150 mV claim, PDB structure validation details, and code or data availability statements

## Reviewer
- **Overall assessment** The manuscript addresses an interesting question regarding the redox-dependent DNA scanning mechanism of EndoIII, combining experimental spectroscopy with computational approaches. However, the evidence presented does not adequately support several central claims. The FTIR peak assignments lack rigorous controls and quantitative analysis, the machine learning methodology is insufficiently described to assess validity, and the thermodynamic analysis relies on assumed parameters rather than measured values. The connection between the observed spectral changes and the specific claim of oxidized cluster stabilization is not directly established. The manuscript would benefit from substantial additional experiments and more rigorous analytical approaches before the conclusions can be considered supported.
- **Who would be interested in the results, and why** Researchers in the fields of DNA repair mechanisms, iron-sulfur cluster biochemistry, and redox biology would find this work relevant. The broader community studying protein-DNA interactions and the application of machine learning to spectroscopic data may also have interest. The potential link between redox state and DNA scanning dynamics in repair enzymes is a topic of active investigation.
- **Major strengths** The interdisciplinary approach combining FTIR, DFT, and machine learning is ambitious and potentially informative. The focus on dynamic redox modulation of DNA repair enzymes addresses an important mechanistic question. The use of far-IR spectroscopy to probe Fe-S vibrations is a technically interesting approach.
- **Major Concerns** 
  - R1-M1: The central claim that DNA binding stabilizes the oxidized [4Fe4S] cluster is not directly supported by the presented data. The FTIR spectral shifts are interpreted as evidence of this stabilization, but no direct redox measurements or oxidation state assignments are provided.
  - R1-M2: The machine learning methodology is critically underdescribed. The training data generation, feature selection rationale, validation approach, and the relationship between spectral features and "actual distances" are unclear. The circularity of deriving distances from spectral shifts and then predicting those same distances from spectral features is a significant concern.
  - R1-M3: The thermodynamic analysis is based on assumed values (Kd = 10 μM, ΔH = −30 kJ/mol) rather than measured parameters, yet the results are presented as meaningful findings. The positive ΔG value is acknowledged as nonspontaneous, which contradicts the observed binding.
  - R1-M4: The DFT calculations are performed on a simplified model system with ethyl thiolate ligands, and the connection between these calculations and the experimental FTIR spectra of the full protein-DNA complex is not clearly established.
  - R1-M5: The 150 mV stabilization potential is mentioned repeatedly but no experimental electrochemical data are presented in the manuscript to support this value.
- **Minor Comments**
  - R1-m1: The manuscript would benefit from a clearer description of how the second derivative spectra were processed and how peak assignments were made.
  - R1-m2: The relationship between the PDB structure 1P59 distances and the machine learning predictions should be more explicitly described.
  - R1-m3: The statement that "both the dsDNA feature and the EndoIII/dsDNA feature had a strong influence" should be quantified with actual coefficient values.
  - R1-m4: The manuscript should clarify whether the neural network and Ridge regression results are consistent with each other.
  - R1-m5: The disappearance of peaks at 890 and 967 cm−1 upon binding should be quantified and discussed in the context of potential artifacts from background subtraction.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The application of combined FTIR/DFT/machine learning to study redox-dependent DNA binding is somewhat novel, but the underlying concepts are established in the field.
  - Scientific importance: Moderate. The question of how redox state modulates DNA repair enzyme function is important, but the current evidence does not substantially advance understanding beyond existing literature.
  - Interdisciplinary readership: The combination of spectroscopy, computation, and machine learning could appeal to a broad audience, but the technical presentation limits accessibility.
  - Technical soundness: Insufficient. Several methodological aspects are underdescribed or rely on assumptions that are not adequately justified.
  - Readability for nonspecialists: The manuscript is reasonably well-written but assumes significant background knowledge in multiple specialized areas.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses an interesting question but requires substantial additional experimental work, particularly direct redox measurements, more rigorous machine learning validation, and measured thermodynamic parameters, before the central claims can be considered supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** "Our results reveal shifts in Fe–S bond vibrational modes, suggesting stabilization of the oxidized [4Fe4S] cluster in proximity to negatively charged DNA"
- **Evidence pointer** Results and Discussion, Protein–DNA Interaction section; Figure 2
- **Concern** The claim that the oxidized [4Fe4S] cluster is stabilized upon DNA binding is inferred solely from FTIR spectral shifts. No direct measurement of the cluster oxidation state (e.g., electrochemistry, EPR, or X-ray absorption spectroscopy) is presented. The interpretation of the observed shifts as evidence of oxidized state stabilization is speculative without such direct evidence.
- **Why it matters** The central thesis of the manuscript is that redox state modulates DNA binding. Without direct evidence of the oxidation state change, the mechanistic conclusion is not supported.
- **Resolution test** Provide direct electrochemical or spectroscopic measurements of the cluster oxidation state in the presence and absence of DNA, or clearly frame the claim as a hypothesis rather than a finding.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** "A machine learning model, trained on the spectral features of the EndoIII/DNA complex, predicted the enzyme-DNA binding distance"
- **Evidence pointer** Results and Discussion, Machine Learning section; Figure 3; Materials and Methods, Machine Learning for FTIR Data Analysis
- **Concern** The machine learning methodology is critically underdescribed. The "actual distances" used as training labels are derived from the same spectral shifts used as features, creating a circular validation. The process by which spectral shifts are converted to distances (eq 1) is not clearly derived or validated against independent measurements. The training set size, data augmentation, and cross-validation details are insufficient to assess model robustness.
- **Why it matters** The machine learning results are presented as a key finding, but without a clear and non-circular methodology, the predictive claims are not credible.
- **Resolution test** Describe the full data generation pipeline, provide independent validation of the distance predictions (e.g., against known structures or molecular dynamics simulations), and clarify how the model avoids circularity.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Data support for conclusions
- **Claim pointer** "The following thermodynamic parameters were computed: ΔG = 28.52 kJ/mol, ΔH = −30.00 kJ/mol, and ΔS = −196.39 J/mol·K"
- **Evidence pointer** Results and Discussion, Thermodynamic Analysis section; Materials and Methods, Thermodynamic Analysis
- **Concern** The thermodynamic parameters are computed from assumed values (Kd = 10 μM, ΔH = −30 kJ/mol) rather than measured experimentally. The resulting positive ΔG indicates nonspontaneous binding, which contradicts the observed complex formation. The authors acknowledge this but do not resolve the contradiction or provide measured values.
- **Why it matters** Thermodynamic conclusions derived from assumed parameters are not meaningful and could mislead readers about the driving forces of binding.
- **Resolution test** Measure Kd and ΔH experimentally (e.g., via ITC or surface plasmon resonance) and recompute the thermodynamic parameters, or remove this analysis if direct measurements are not feasible.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational-experimental alignment
- **Claim pointer** "DFT calculations supported the experimental findings, predicting comparable shifts in the vibrational frequencies of Fe–S bonds upon DNA binding"
- **Evidence pointer** Results and Discussion, Protein–DNA Interaction section; Materials and Methods, Computational Details
- **Concern** The DFT calculations are performed on a simplified [4Fe4S]2+ cluster model with ethyl thiolate ligands, without including the protein environment or DNA. The comparison between these gas-phase calculations and the experimental FTIR spectra of the full protein-DNA complex is not quantitatively established. No calculated spectra are shown alongside experimental spectra for direct comparison.
- **Why it matters** The claim of computational support for experimental findings requires a more realistic model and direct spectral comparison to be convincing.
- **Resolution test** Present calculated and experimental spectra overlaid, and discuss the limitations of the simplified model in reproducing the experimental conditions.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence availability
- **Claim pointer** "We correlated the electrochemical stabilization potential of 150 mV in the [4Fe4S] cluster with the enzyme's DNA-binding properties"
- **Evidence pointer** Results and Discussion, Correlating Redox Stabilization section
- **Concern** The 150 mV stabilization potential is referenced throughout the manuscript, but no experimental electrochemical data are presented. No voltammograms, potential measurements, or citations to the source of this value are provided in the visible text.
- **Why it matters** The correlation between electrochemical stabilization and DNA binding is a central claim, but without the underlying data, it cannot be evaluated.
- **Resolution test** Provide the electrochemical measurements or a clear citation to the original source of the 150 mV value, and describe how it was obtained.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** FTIR spectral analysis
- **Evidence pointer** Results and Discussion, Protein–DNA Interaction section; Figure 2
- **Issue** The processing of second derivative spectra and the criteria for peak assignment are not described in sufficient detail.
- **Required correction** Provide a description of the spectral processing steps, including smoothing parameters and peak picking criteria.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Interpretability
- **Affected element** PDB structure comparison
- **Evidence pointer** Results and Discussion, Machine Learning section; Figure 4
- **Issue** The comparison between distances from PDB structure 1P59 and the machine learning predictions is described qualitatively but not quantified.
- **Required correction** Provide a quantitative comparison, such as a table of distances or a statistical measure of agreement.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Quantification
- **Affected element** Feature importance
- **Evidence pointer** Results and Discussion, Machine Learning section
- **Issue** The statement that both features had "a strong influence" on predictions is not supported by numerical values.
- **Required correction** Report the actual coefficients or feature importance scores from the model.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Model comparison
- **Evidence pointer** Materials and Methods, Machine Learning for FTIR Data Analysis
- **Issue** Both a neural network and a Ridge regression model are mentioned, but only the Ridge regression results are discussed in the results section.
- **Required correction** Either present results for both models or clarify why only one is discussed.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data interpretation
- **Affected element** Peak disappearance
- **Evidence pointer** Results and Discussion, Protein–DNA Interaction section
- **Issue** The disappearance of peaks at 890 and 967 cm−1 upon binding is stated but not quantified, and potential artifacts from background subtraction are not discussed.
- **Required correction** Quantify the changes and discuss potential sources of artifact, including control experiments.

## Risk / unsupported claims
- The claim that DNA binding stabilizes the oxidized [4Fe4S] cluster is unsupported by direct redox measurements.
- The 150 mV electrochemical stabilization potential is referenced but not experimentally demonstrated in this manuscript.
- The thermodynamic parameters (ΔG, ΔH, ΔS) are computed from assumed values and do not represent measured quantities.
- The machine learning predictions of binding distances are potentially circular, as the "actual distances" are derived from the same spectral data used as features.
- The DFT calculations on a simplified model are presented as supporting experimental findings without direct spectral comparison or discussion of model limitations.