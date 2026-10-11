## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no access to full manuscript, figures, tables, or methods
- **Shared manuscript claim summary** The authors report that aloe-emodin (AED) associates with two human telomeric G-quadruplex (G4) models, wHTel26 (hybrid-2 in K+) and HTel22 (antiparallel basket in Na+), based on UV-visible, fluorescence, and circular dichroism spectroscopy. Apparent binding constants span approximately 10^3 to 10^5 M^-1. The interaction is described as non-intercalative. Thermal stabilization of approximately 14 degrees C is reported for wHTel26 in K+, but not for HTel22 in Na+. Docking poses are presented as supportive, hypothesis-generating evidence. AED reduces MCF-7 metabolic viability with an estimated IC50 of 18.82 microM. Telomerase inhibition and intracellular G4 engagement were not investigated.
- **Visible evidence base** Abstract text only; no numerical data, spectra, titration curves, docking parameters, or experimental protocols are provided
- **Missing materials affecting confidence** Full methods, all figures and tables, raw spectroscopic data, binding constant calculations, thermal melting curves, docking methodology and scoring, cell viability assay details, statistical analyses, and any supplementary information

## Reviewer

- **Overall assessment** The abstract presents a straightforward spectroscopic characterization of AED binding to two G4 models, with a cautious and appropriately hedged interpretation. The authors are transparent about the limitations of their study, particularly the inability to attribute observed differences to cation versus sequence/topology effects, and the absence of cellular target engagement data. However, the abstract alone provides insufficient detail to evaluate the technical rigor of the binding measurements, the reliability of the reported binding constants, or the validity of the thermal stabilization claim. The biological relevance of the MCF-7 viability data is unclear given the lack of mechanistic follow-up. The manuscript may be of interest to specialists in G4-ligand interactions, but the current evidence base is too limited to establish the stated conclusions.
- **Who would be interested in the results, and why** Researchers working on G4-targeting small molecules, natural product screening for nucleic acid ligands, and the biophysics of ligand-G4 interactions. The study may also be of interest to those studying anthraquinone derivatives as potential anticancer agents, though the lack of cellular mechanistic data limits this audience.
- **Major strengths** The authors explicitly acknowledge the confounding variables in their system comparison, which is scientifically honest. The use of multiple spectroscopic techniques provides complementary perspectives on the interaction. The classification of docking as hypothesis-generating rather than confirmatory is appropriate. The abstract clearly states what was not done, which helps readers calibrate the scope of the claims.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The abstract reports apparent binding constants spanning approximately 10^3 to 10^5 M^-1 across different techniques.
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** The reported binding constants vary by two orders of magnitude depending on the technique used. The abstract attributes this to distinct optical and conformational observables and non-linear titration profiles, but no details are given regarding how these constants were derived, what models were used for fitting, or whether the titrations reached saturation. A two-order-of-magnitude spread across methods raises the question of whether any of these values reliably reflects the true binding affinity.
  - **Why it matters** Binding constants are central quantitative claims of the study. If the values are not robustly determined, the conclusion that AED associates with both G4 models is weakened, and the comparison between the two systems becomes unreliable.
  - **Resolution test** Provide full titration data, fitting models, residuals, and justification for the chosen binding models. Show that the derived constants are reproducible and that the spread across techniques can be explained by the physical basis of each observable.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The abstract reports an apparent thermal stabilization of approximately 14 degrees C for wHTel26 in K+ and no comparable stabilization for HTel22 in Na+.
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** No melting curves, experimental conditions, or analysis methods are provided. The abstract correctly notes that the two systems differ in sequence, flanking residues, topology, and cation, so the difference cannot be attributed to the ionic environment alone. However, the claim of 14 degrees C stabilization is presented as a quantitative result without any indication of error, replicates, or the concentration of AED used.
  - **Why it matters** Thermal stabilization is a key biophysical readout for G4-ligand interactions. Without supporting data, the magnitude of the effect and the contrast between the two systems cannot be evaluated.
  - **Resolution test** Provide melting curves, replicate measurements, standard deviations, and the AED concentrations used. Clarify whether the 14 degrees C value represents a maximum or a representative value.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Scientific importance
  - **Claim pointer** The abstract states that AED reduced MCF-7 metabolic viability with an estimated IC50 of 18.82 microM.
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** The IC50 value is presented without any indication of the assay format, exposure time, concentration range tested, or statistical variability. More importantly, the abstract explicitly states that telomerase inhibition and intracellular G4 target engagement were not investigated. Without these data, the relevance of the viability effect to G4 binding is entirely speculative.
  - **Why it matters** The viability data may imply biological relevance, but the absence of mechanistic linkage means the result does not support any claim about AED acting through G4 interactions in cells.
  - **Resolution test** Provide full assay details and error estimates. If the biological relevance is to be claimed, add experiments addressing telomerase inhibition or intracellular G4 engagement, or explicitly reframe the viability data as preliminary and unrelated to the G4 binding claims.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Abstract text
  - **Evidence pointer** Abstract text; location not provided
  - **Issue** The phrase "Docking generated plausible AED association poses was used only as supportive, hypothesis-generating evidence" contains a grammatical error and is awkwardly phrased.
  - **Required correction** Revise to "Docking generated plausible AED association poses and was used only as supportive, hypothesis-generating evidence" or restructure the sentence for clarity.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Binding constant range
  - **Evidence pointer** Abstract text; location not provided
  - **Issue** The range 10^3 to 10^5 M^-1 is very broad. If this spread is real, it should be discussed more explicitly in terms of what each technique measures and why the values differ so substantially.
  - **Required correction** Add a sentence in the abstract or main text explaining the physical basis for the spread, or provide a single best estimate with justification.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Scientific importance
  - **Affected element** Conclusion framing
  - **Evidence pointer** Abstract text; location not provided
  - **Issue** The abstract ends with a call for future studies, which is appropriate, but the phrasing "establishing sequence- and cation-controlled G4 selectivity" implies that selectivity is a goal rather than a finding. This is fine, but the abstract could more clearly state what the current study actually establishes versus what it does not.
  - **Required correction** Consider adding a sentence that summarizes the concrete findings of the current study before the future directions.
- **Technical failings that need to be addressed before the case is established** R1-M1 (binding constant reliability), R1-M2 (thermal stabilization data), R1-M3 (viability data without mechanistic context)

## Risk / unsupported claims

- The claim that AED produces approximately 14 degrees C thermal stabilization of wHTel26 is unsupported without melting data.
- The claim that binding constants span 10^3 to 10^5 M^-1 is unverifiable without fitting details and raw titration data.
- The statement that the interaction is non-intercalative is weakly supported by the abstract alone, as the limited wavelength shifts and preserved CD signatures are indirect evidence.
- The MCF-7 IC50 value is presented without assay details and is not linked to any G4-related mechanism.
- The docking results are appropriately described as hypothesis-generating, but no details are provided to assess their quality.
- The overall conclusion that AED associates with both G4 models is plausible but not fully established from the abstract-level evidence.

## Assessment against Nature-style criteria

- **Originality** The study applies known spectroscopic methods to a natural product and two G4 models. The combination of AED with telomeric G4s may be novel, but the abstract does not clearly position this against prior work on anthraquinone-G4 interactions.
- **Scientific importance** The findings are incremental. The study does not resolve the cation versus sequence/topology question, and the absence of cellular mechanistic data limits the significance. The work may be useful to specialists but does not address a broad scientific question.
- **Interdisciplinary readership** The topic sits at the interface of chemistry, biophysics, and cancer biology. However, the abstract is written in a way that is accessible to specialists in G4 biology and ligand design, but the lack of mechanistic or cellular context reduces its appeal to a broader audience.
- **Technical soundness** Cannot be fully assessed from the abstract. The spread in binding constants and the absence of melting data are concerns. The authors are transparent about limitations, which is commendable, but the technical execution cannot be verified.
- **Readability for nonspecialists** The abstract is generally clear but uses field-specific terminology without much explanation. The grammatical error in the docking sentence detracts from readability.

## Recommendation posture

Currently not established from the provided evidence. The abstract is honest about its limitations, but the quantitative claims (binding constants, thermal stabilization, IC50) cannot be evaluated without full data. The study may be publishable in a specialized journal if the full manuscript provides robust supporting data, but the case for a significant advance is not made at the abstract level. Supportive if technical concerns are resolved and if the full manuscript provides the missing experimental details.