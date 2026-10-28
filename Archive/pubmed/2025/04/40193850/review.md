## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Model, Results, Discussion, Methods) and metadata (title, authors, journal, date, DOI/ID, URL)
- **Assessment boundary** Scientific content, technical soundness, internal consistency, and alignment with stated claims. No assessment of formatting, grammar, or editorial fit beyond Nature-style criteria.
- **Shared manuscript claim summary** The authors propose a mathematical model, derived from polymer scaling theory, that relates the transport rate of small-to-medium-sized molecules (approximately 5 nm) through the nuclear pore complex (NPC) to pore diameter. The model is validated using coarse-grained Brownian dynamics simulations with forward flux sampling, across varying pore sizes, FG-Nup lengths, and cargo surface properties.
- **Visible evidence base** Main text (Abstract, Introduction, Model, Results, Discussion, Methods), figure references (Figs 2, 3, 4, 5, 6, 7, 8), table references (Tables 1, 2), and references to supporting information (S1 Text, Appendices A-D)
- **Missing materials affecting confidence** Figures, tables, and S1 Text (including Appendices A-D) are referenced but not provided. Simulation parameter values in Tables 1 and 2 are not visible. Full derivation steps for equations (Eqs 1-6) are partially shown but some intermediate steps are omitted. Experimental validation data are not included.

## Reviewer
- **Overall assessment** The manuscript presents a theoretically motivated and computationally tested model for how NPC pore dilation affects molecular transport. The polymer scaling approach is appropriate and the model is clearly derived. The simulation results appear to support the model within the stated parameter range. However, the absence of figures, tables, and supporting information limits a full evaluation of the technical execution and the strength of the quantitative agreement. The model's biological relevance is argued but not experimentally demonstrated. The work is a solid contribution to the quantitative understanding of NPC transport, though its scope is narrow and the novelty relative to prior models is incremental rather than transformative.
- **Who would be interested in the results, and why** Biophysicists and computational biologists studying nucleocytoplasmic transport, mechanotransduction, and polymer physics in confined environments. Researchers interested in the mechanical regulation of nuclear transport and the role of FG-Nup meshwork properties would find the model useful for interpreting experimental data on pore dilation.
- **Major strengths** The model derivation is logical and grounded in established polymer scaling theory. The use of Brownian dynamics simulations with forward flux sampling is an appropriate and rigorous method for estimating rare transport events. The authors clearly state the model's assumptions and limitations, including the range of pore and cargo sizes for which it is valid. The comparison with the complementary model by Klughammer et al. is helpful for situating the work.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1 (validation completeness), R1-M2 (parameter justification), R1-M3 (biological extrapolation)
- **Assessment against Nature-style criteria** 
  - Originality: The application of polymer scaling theory to derive a closed-form relationship between pore diameter and transport rate is a useful contribution, but it builds directly on established frameworks and prior work on FG-Nup mesh size. The originality is moderate.
  - Scientific importance: The question of how pore dilation affects transport is relevant to mechanotransduction and NPC biology. However, the model is limited to a narrow size range and does not address active transport or cargo-FG-Nup interactions beyond weak, transient ones. The importance is moderate.
  - Interdisciplinary readership: The work bridges polymer physics, biophysics, and cell biology. The writing is accessible to a broad scientific audience, though the model derivation requires some familiarity with scaling concepts. The interdisciplinary appeal is moderate.
  - Technical soundness: The theoretical derivation and simulation methodology are sound in principle. However, the lack of visible figures, tables, and supporting information prevents a full assessment of the technical execution and the quality of the fit between model and simulation.
  - Readability for nonspecialists: The manuscript is clearly written and the logic is easy to follow. The use of normalized variables and clear definitions helps nonspecialists. The readability is good.
- **Recommendation posture** Supportive if technical concerns are resolved, specifically the provision of full simulation details, parameter values, and a more thorough discussion of the model's range of validity and biological extrapolation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation completeness
- **Claim pointer** The authors claim that the simulation results "demonstrated strong agreement with our model's predictions, confirming its accuracy and applicability" (Abstract) and that the data "aligned well with both full and partial transport data" (Results).
- **Evidence pointer** Figures 5, 6, 7, 8; location not provided for quantitative fit metrics
- **Concern** The claim of strong agreement is not quantitatively supported in the visible text. No goodness-of-fit statistics, error bars, or confidence intervals are reported. The figures that would show the comparison between model and simulation are not provided. Without these, the reader cannot assess whether the agreement is indeed strong or merely qualitative.
- **Why it matters** The central claim of the manuscript is that the model accurately describes transport rates. If the agreement is only qualitative or limited to a narrow parameter range, the model's utility is diminished. The absence of quantitative validation undermines the confidence in the model's predictive power.
- **Resolution test** Provide the figures with data points and model curves, along with quantitative measures of fit (e.g., R-squared, root-mean-square error) for each condition. State explicitly the range of x over which the model is accurate and the deviation outside that range.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Parameter justification
- **Claim pointer** The model relies on parameters such as the Flory exponent ν = 0.588, the Kuhn length b = σ = 0.86 nm, and the number of FG-Nups nFG = 80. The authors state that these values are based on yeast NPC characteristics.
- **Evidence pointer** Methods section, Tables 1 and 2; location not provided for parameter values
- **Concern** The choice of ν = 0.588 assumes a good solvent condition, but the authors acknowledge in the Discussion that FG-Nup behavior can vary between collapsed and extended states. The sensitivity of the model to ν is not explored. Similarly, the values for nFG, h, and the monomer volume are stated but not justified with citations or sensitivity analysis. The tables that would list these parameters are not visible.
- **Why it matters** The model's predictions depend critically on these parameters. If the values are not representative of the biological system or if the model is highly sensitive to them, the conclusions may not hold. A sensitivity analysis is needed to establish the robustness of the model.
- **Resolution test** Provide a table of all parameters with sources or justification. Perform and report a sensitivity analysis for key parameters, particularly ν and nFG, showing how the model predictions and the agreement with simulations change.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Biological extrapolation
- **Claim pointer** The authors state that the model is "relevant to a wide range of transcription factors and signaling molecules" and that it "supports the recent hypothesis linking the NPC to mechanotransduction" (Discussion).
- **Evidence pointer** Discussion section; location not provided
- **Concern** The model is validated only for inert cargoes and weakly attractive cargoes in simulations. The extrapolation to biological molecules such as transcription factors and importin-beta is based on size alone. The model does not account for specific cargo-FG-Nup interactions, active transport mechanisms, or the complex environment of the native NPC. The claim of relevance to mechanotransduction is speculative and not supported by direct evidence.
- **Why it matters** Overstating the biological applicability of the model could mislead readers and future research. The model is a useful theoretical framework, but its biological relevance needs to be demonstrated or clearly qualified.
- **Resolution test** Clearly state the assumptions and limitations of the model in the Discussion. Provide a more cautious interpretation of the biological implications, or include additional simulations with more realistic cargo-FG-Nup interactions to support the claims.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of derivation
- **Affected element** Model section, equations 1-6
- **Evidence pointer** Model section; location not provided
- **Issue** The derivation of the model equations is presented in a condensed form. Some intermediate steps, particularly the transition from Eq. 2 to Eq. 3 and the justification for the functional form of h(d/ξ), are not fully explained.
- **Required correction** Expand the derivation to include the missing steps and provide a brief justification for the assumptions made, such as the linear proportionality of free energy to volume fraction.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Definition of variables
- **Affected element** Model section, Eq. 5
- **Evidence pointer** Model section; location not provided
- **Issue** The variable α is defined as α = (3ν - 1)/ν, but its physical interpretation is not discussed. The relationship between α and the polymer quality (good vs. poor solvent) could be clarified.
- **Required correction** Add a sentence explaining the physical meaning of α and how it relates to the polymer scaling regime.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section, Figures 5-8
- **Evidence pointer** Results section; location not provided
- **Issue** The number of independent simulation runs, the standard deviation or standard error of the transport rate estimates, and the number of forward flux sampling iterations are not reported.
- **Required correction** Report the statistical uncertainty of the simulation results and the number of replicates in the figure captions or Methods.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Comparison with prior work
- **Affected element** Discussion section
- **Evidence pointer** Discussion section; location not provided
- **Issue** The comparison with the model by Klughammer et al. is brief. A more detailed discussion of the differences in assumptions, predictions, and applicable regimes would strengthen the manuscript.
- **Required correction** Expand the comparison to highlight the specific conditions under which each model is more appropriate and how they complement each other.

## Risk / unsupported claims
- The claim of "strong agreement" between model and simulation is unsupported without quantitative fit metrics and visible figures.
- The claim that the model is "relevant to a wide range of transcription factors and signaling molecules" is an extrapolation based on size alone and is not directly supported by the simulations.
- The claim that the work "supports the recent hypothesis linking the NPC to mechanotransduction" is speculative and not directly tested.
- The parameter values (e.g., nFG = 80, h = 40 nm) are stated but not justified with citations or sensitivity analysis, making their accuracy unverifiable from the provided material.
- The model's validity for cargoes with strong attractive interactions with FG-Nups is not established, and the authors acknowledge this limitation.