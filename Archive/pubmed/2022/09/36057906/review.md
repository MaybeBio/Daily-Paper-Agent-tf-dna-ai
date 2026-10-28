## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full methods, figures, tables, or supplementary data
- **Shared manuscript claim summary** The authors propose that hydrocarbon-stapled helical peptides derived from coactivator LXXLL motifs act as antidiabetic PPARgamma antagonists by binding the coactivator site. They claim that stapling improves binding affinity primarily by reducing unfavorable entropy penalty rather than increasing favorable enthalpy, and they report experimental binding and competition data supporting this.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or numerical data beyond those stated in the abstract
- **Missing materials affecting confidence** Full methods, structural analysis details, simulation parameters, energetics dissection results, fluorescence assay protocols, raw binding data, statistical analyses, and any control experiments

## Reviewer
- **Overall assessment** The abstract presents a conceptually interesting approach to PPARgamma antagonism via stapled peptides targeting the coactivator site, with a mechanistic hypothesis that distinguishes entropy-driven from enthalpy-driven binding enhancement. However, the evidence provided in the abstract is insufficient to fully evaluate the validity of the central claims. The computational and experimental results are summarized without methodological detail, and the reported improvements in binding affinity and competitive potency lack statistical context. The work may be of interest to researchers in peptide therapeutics and nuclear receptor biology, but the current abstract does not establish the case convincingly.
- **Who would be interested in the results, and why** Researchers in peptide drug design, nuclear receptor signaling, and diabetes therapeutics would be interested. The entropy-focused design rationale offers a distinct perspective on stapled peptide optimization, which could inform future work on coactivator-binding inhibitors. The competitive potency data may also appeal to those seeking alternatives to small-molecule PPARgamma modulators.
- **Major strengths** The hypothesis that stapling reduces entropy penalty rather than enhancing enthalpy is a nuanced and mechanistically informative framing. The use of multiple coactivator-derived peptides (SRC1, NCoA6, p300) provides some breadth. The combination of computational prediction with experimental validation is a positive feature.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract lacks methodological detail for both computational and experimental components, making it impossible to assess technical soundness. No statistical measures are provided for the binding affinity improvements or CC50 values. The claim that stapling "minimizes" entropy penalty is not quantitatively supported. The competitive potency data are presented without comparison to known PPARgamma ligands or controls.
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The entropy-focused design rationale is somewhat novel, but the general concept of stapled peptides targeting PPARgamma is not unprecedented.
  - Scientific importance: Moderate. PPARgamma remains a relevant target, but the clinical translation of peptide antagonists is uncertain.
  - Interdisciplinary readership: Limited. The abstract is likely to appeal mainly to specialists in peptide chemistry and nuclear receptor biology.
  - Technical soundness: Not assessable from the abstract alone. Key methods and data are missing.
  - Readability for nonspecialists: The abstract is reasonably clear but uses jargon (e.g., "LXXLL motif," "entropy penalty") without sufficient explanation for a broad audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a plausible hypothesis and preliminary data, but the lack of methodological and statistical detail prevents a supportive recommendation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that stapling "largely minimizes unfavorable entropy penalty but having only a moderate effect on favorable enthalpy contribution."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract provides no quantitative data from the energetics dissection. No values for entropy or enthalpy changes are given, nor is there any description of the computational method used to derive these terms. Without such data, the central mechanistic claim cannot be evaluated.
- **Why it matters** The entire design rationale rests on the distinction between entropy and enthalpy contributions. If this is not supported by explicit numbers and a clear method, the claim is unverifiable.
- **Resolution test** Provide a table or figure showing computed entropy and enthalpy changes for stapled versus unstapled peptides, with a description of the simulation and analysis protocol.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors report binding affinity improvements of 7.2-fold, 4.2-fold, and 5.7-fold for SRC1, NCoA6, and p300 peptides, respectively, upon stapling.
- **Evidence pointer** Abstract text; location not provided
- **Concern** No error bars, replicates, or statistical tests are reported. It is unclear whether these improvements are significant or reproducible. The assay type is mentioned as "fluorescence-based" but no details on the specific method (e.g., FP, FRET) or conditions are given.
- **Why it matters** Without statistical context, the reported fold improvements could be within experimental noise. The competitive potency values (CC50) also lack confidence intervals.
- **Resolution test** Include replicate data with standard deviations, statistical significance tests, and a description of the assay protocol and conditions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors state that the stapled peptides "efficiently" compete with unstapled counterparts for the PPARgamma coactivator site, with CC50 values of 0.096, 0.12, and 0.18 muM.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The term "efficient" is subjective and not benchmarked against any positive control or known PPARgamma coactivator peptide affinity. It is unclear whether these CC50 values represent meaningful competition in a cellular or therapeutic context.
- **Why it matters** The therapeutic relevance of the peptides depends on their ability to disrupt native PPARgamma-coactivator interactions at physiologically relevant concentrations. Without a comparator, the claim of efficiency is unsupported.
- **Resolution test** Provide a comparison with the native coactivator peptide affinity or a known PPARgamma antagonist, and discuss the physiological relevance of the CC50 values.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The phrase "decreasing unfavorable entropy penalty instead of increasing favorable enthalpy contribution" is central but could be misinterpreted. It is not clear whether the stapling reduces the entropy penalty relative to the free peptide or relative to a hypothetical ideal binding scenario.
- **Required correction** Clarify the reference state for the entropy and enthalpy comparison.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract does not state how many peptides were tested or whether any stapled peptides failed to show improved binding. This could indicate selection bias.
- **Required correction** Mention the total number of peptides designed and tested, and report any negative results.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The term "CC(50)" is used without definition. It is likely the half-maximal competitive concentration, but this should be stated explicitly.
- **Required correction** Define CC50 at first use.

## Risk / unsupported claims
- The claim that stapling reduces entropy penalty rather than increasing enthalpy is unsupported by quantitative data in the abstract.
- The reported binding affinity improvements and CC50 values lack statistical measures and methodological context.
- The statement that the peptides are "antidiabetic" is not supported by any functional or in vivo data in the abstract.
- The claim of "efficient" competitive potency is not benchmarked against any control or known standard.