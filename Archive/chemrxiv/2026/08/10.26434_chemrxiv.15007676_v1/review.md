## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as stated in the abstract; no methods, figures, or data tables were provided for verification
- **Shared manuscript claim summary** The authors report a non-monotonic, U-shaped dependence of TMPyP4 binding affinity to parallel c-MYC G4 DNA on crowder size (EG/PEG), attributed to competing effects of viscosity-induced hindrance and depletion interactions. They propose a modified Collins-Kimball-Debye formalism combined with hybrid MD simulations to explain the recovery of association rates for larger PEG crowders via polymer-free depletion cavities.
- **Visible evidence base** Steady-state and fluorescence correlation spectroscopy (FCS) measurements; kinetic analysis of FCS data; modified Collins-Kimball-Debye formalism; hybrid MD simulations. Specific figures, tables, and numerical values are not provided in the supplied material.
- **Missing materials affecting confidence** Full manuscript text, experimental methods, FCS fitting details, simulation parameters, error bars, replicate information, control experiments, and all figures/tables. Without these, quantitative claims and mechanistic conclusions cannot be independently assessed.

## Reviewer
- **Overall assessment** The abstract presents an interesting and potentially significant observation regarding the non-monotonic dependence of ligand binding to G4 DNA on crowder size. The proposed mechanistic framework, combining depletion interactions and viscosity effects, is conceptually appealing and could have broad relevance. However, the abstract alone provides insufficient detail to evaluate the rigor of the experimental design, the validity of the kinetic analysis, or the robustness of the simulation results. The central claim of a U-shaped binding affinity profile rests on data that are not visible in the supplied material, and the mechanistic interpretation, while plausible, requires substantial supporting evidence to be convincing.
- **Who would be interested in the results, and why** Researchers in nucleic acid chemistry, biophysics, and molecular crowding; scientists working on G-quadruplex-targeted drug discovery; and investigators interested in the physical chemistry of macromolecular interactions in cellular environments. The proposed link between polymer physics and ligand recognition could attract a broad readership spanning biophysics, chemical biology, and pharmaceutical sciences.
- **Major strengths** The study addresses a biologically relevant and mechanistically unresolved question. The combination of experimental kinetics (FCS) with theoretical modeling (modified Collins-Kimball-Debye formalism) and simulations represents a multi-pronged approach. The concept of crowder-size-dependent depletion cavities counteracting viscous drag is a novel and testable hypothesis that could advance the field.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The abstract claims a "pronounced non-monotonic, U-shaped dependence" of ligand binding affinity (K) on crowder size.
  - **Evidence pointer** Location not provided; no figures or tables are available in the supplied material
  - **Concern** The central observation of a U-shaped dependence is stated without any visible quantitative data. No binding affinities, rate constants, or crowder concentrations are reported. The magnitude of the effect, the number of crowder sizes tested, and the statistical significance of the non-monotonic trend are all absent.
  - **Why it matters** The entire mechanistic framework is built on this non-monotonic profile. If the effect is small, poorly replicated, or an artifact of limited crowder size sampling, the conclusions would not be supported. The abstract does not allow the reader to judge whether the U-shape is robust or coincidental.
  - **Resolution test** Provide the full dataset showing K, k_on, and k_off as functions of crowder size and concentration, with error bars and replicate numbers. Demonstrate that the non-monotonic trend is statistically significant and reproducible across independent experiments.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Mechanistic attribution
  - **Claim pointer** The abstract attributes the non-monotonic behavior to "competing effects of crowder-induced viscosity and depletion interactions" on k_on and k_off.
  - **Evidence pointer** Location not provided; kinetic analysis of FCS data is mentioned but no details are given
  - **Concern** The separation of viscosity and depletion contributions is asserted but not demonstrated. No control experiments (e.g., using crowders of similar size but different chemistry, or varying viscosity independently of crowding) are described. The claim that larger crowders create "polymer-free depletion cavities" is presented as a conclusion from simulations, but the simulation methodology and validation are not visible.
  - **Why it matters** Without explicit separation of these two physical effects, alternative explanations (e.g., crowder binding, excluded volume effects unrelated to depletion, or changes in G4 conformation) cannot be ruled out. The mechanistic claim is the core novelty of the work and must be rigorously supported.
  - **Resolution test** Show control experiments that isolate viscosity from depletion effects. Provide simulation details, including force fields, system sizes, and validation against experimental observables. Demonstrate that the depletion cavity mechanism quantitatively reproduces the experimental k_on trends.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Model validity
  - **Claim pointer** The abstract states that a "modified Collins-Kimball-Debye formalism" combined with hybrid MD simulations explains the observed trends.
  - **Evidence pointer** Location not provided; no equations or simulation details are given
  - **Concern** The modified formalism is not described. It is unclear what modifications were made to the standard Collins-Kimball-Debye theory, what assumptions were introduced, and how the model parameters were determined. The hybrid MD approach is also unspecified, including whether it couples coarse-grained and atomistic representations and how the crowding environment was modeled.
  - **Why it matters** The theoretical framework is presented as a key contribution. If the model is not clearly specified, its predictions cannot be reproduced or independently tested. The fit between model and experiment may be achieved through adjustable parameters, which would weaken the mechanistic conclusion.
  - **Resolution test** Provide the full derivation of the modified formalism, all model parameters, and a sensitivity analysis. Describe the hybrid MD methodology in sufficient detail for reproduction. Show that the model makes non-trivial predictions that are confirmed by additional experiments.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Crowder size range
  - **Evidence pointer** Location not provided
  - **Issue** The abstract mentions EG and PEG crowders but does not specify the molecular weights or size range used. The term "larger PEGs" is vague.
  - **Required correction** Specify the exact crowders used (e.g., EG, PEG 200, PEG 400, PEG 2000, PEG 8000) and their concentrations, so the reader can contextualize the size-dependent effects.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** "U-shaped dependence"
  - **Evidence pointer** Location not provided
  - **Issue** The abstract describes the dependence as "U-shaped" but does not clarify whether this refers to a function of crowder size at fixed concentration, or of crowder concentration at fixed size. These are different experimental designs.
  - **Required correction** Clarify the independent variable in the reported non-monotonic trend. If both size and concentration were varied, state this explicitly.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Biological relevance
  - **Evidence pointer** Location not provided
  - **Issue** The abstract claims relevance to "the crowded cellular milieu" but provides no data on whether the observed effects persist under conditions closer to physiological crowding (e.g., mixed crowders, protein crowders, or higher total crowder fractions).
  - **Required correction** Add a statement on the limitations of using single-component PEG/EG crowders as proxies for cellular environments, or provide preliminary data with more complex crowding agents.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing quantitative evidence for the central non-monotonic claim), R1-M2 (lack of experimental separation of viscosity and depletion effects), R1-M3 (insufficient specification of the theoretical model and simulations).
- **Assessment against Nature-style criteria**  
  Originality: The concept of crowder-size-dependent depletion cavities modulating ligand association is a fresh angle that has not been widely explored in the G4 field. This is a potential strength.  
  Scientific importance: The question of how crowding affects ligand binding to G4 DNA is of direct relevance to drug design and cellular biophysics. If the mechanism is robust, the work could have significant impact.  
  Interdisciplinary readership: The work bridges polymer physics, nucleic acid chemistry, and biophysics, which could attract a broad audience. However, the abstract currently assumes familiarity with both FCS and polymer theory, which may limit accessibility.  
  Technical soundness: Cannot be assessed from the abstract alone. The absence of any quantitative data or methodological detail precludes evaluation of experimental rigor or theoretical validity.  
  Readability for nonspecialists: The abstract is concise but uses specialized terminology (e.g., "Collins-Kimball-Debye formalism," "depletion cavities") without sufficient context. A general reader would struggle to grasp the key advance.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a plausible and interesting hypothesis, but the absence of all supporting data, methodological detail, and model specification means that the central claims cannot be verified. The manuscript may become suitable for consideration at a high-impact venue if the full paper provides rigorous experimental controls, complete kinetic datasets, and a fully specified and validated theoretical model.

## Risk / unsupported claims
- The U-shaped dependence of binding affinity on crowder size is stated without any visible data.
- The attribution of the non-monotonic behavior to competing viscosity and depletion effects is asserted without experimental controls.
- The claim that larger crowders create "polymer-free depletion cavities" that accelerate association is presented as a simulation result, but no simulation details are provided.
- The modified Collins-Kimball-Debye formalism is mentioned but not described, making its predictions untestable from the supplied material.
- The relevance to "the crowded cellular milieu" is stated without evidence that the observed effects extrapolate to more complex crowding environments.