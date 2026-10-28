## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors report development of a modular bioPROTAC system using an engineered RBCC-derived RS80E degradation domain fused to AI-designed peptide binders or nanobodies targeting PCNA and BCL6. They claim identification of PCNA binders via ProteinMPNN, RFdiffusion, AlphaFold3, AlphaFold2, and HADDOCK, and design of PCNA and BCL6 nanobodies via fragment-based and alanine scanning approaches with CDR3 grafting. They further claim that these bioPROTACs degrade PCNA and BCL6, activate p53, and promote apoptosis, suggesting therapeutic potential and a generalizable platform.
- **Visible evidence base** Abstract text only; no experimental data, structural models, degradation assays, or statistical analyses are visible
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methods details, construct sequences, degradation and apoptosis data, structural validation, and any control experiments

## Reviewer
- **Overall assessment** The abstract presents an ambitious and potentially interesting concept that combines computational protein design with targeted protein degradation. However, the claims substantially exceed the evidence visible in the abstract. No quantitative degradation data, structural validation, or functional assays are shown. The methodological logic is plausible but the key assertions regarding degradation efficiency, p53 activation, and apoptosis are unsupported in the provided material. The work may have merit, but the current evidence base is insufficient to establish the central claims.
- **Who would be interested in the results, and why** Researchers in targeted protein degradation, chemical biology, and cancer therapeutics would be interested if the claims are substantiated. Computational protein designers and those working on AI-driven binder design would also find value. The potential modularity of the platform could attract a broad audience in protein engineering and drug discovery.
- **Major strengths** The concept of combining AI-driven binder design with a bioPROTAC scaffold is timely and innovative. The use of multiple state-of-the-art computational tools is commendable. The focus on PCNA and BCL6 as difficult targets addresses an important unmet need in cancer therapy.
- **Major Concerns** The abstract provides no experimental evidence for the central claims. Degradation efficiency, specificity, p53 activation, and apoptosis are stated as results but no data are shown. The computational design pipeline is described but not validated. The claim of a "modular and rapid pathway" is not supported by any demonstrated reproducibility or generalizability.
- **Minor Comments** The abstract contains some vague phrasing, such as "exploration other intractable therapeutic targets," which should be corrected. The relationship between the peptide binders and nanobodies is unclear in terms of which was used for which target and how they compare. The abstract would benefit from stating quantitative outcomes, such as degradation percentages or binding affinities.
- **Technical failings that need to be addressed before the case is established** No visible experimental validation of degradation, no structural confirmation of designed binders, no functional data for p53 activation or apoptosis, and no controls or statistical measures are provided in the abstract.
- **Assessment against Nature-style criteria** Originality is high, as the combination of AI-designed binders with bioPROTACs is novel. Scientific importance is potentially high for cancer therapeutics, but this cannot be assessed without data. Interdisciplinary readership is likely, given the blend of computational design and biology. Technical soundness is not assessable from the abstract alone. Readability for nonspecialists is moderate, though some terms are used without definition.
- **Recommendation posture** Currently not established from the provided evidence. The concept is promising, but the abstract alone does not support the key claims. A full manuscript with experimental validation would be required to assess the work properly.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that their bioPROTACs degrade PCNA and BCL6, activate p53, and promote apoptosis.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract states these outcomes as results but provides no quantitative data, experimental traces, or statistical analysis. No degradation assays, Western blots, cell viability data, or apoptosis markers are shown.
- **Why it matters** These are the central functional claims of the work. Without experimental evidence, the therapeutic potential and the utility of the platform cannot be evaluated.
- **Resolution test** Provide degradation curves or endpoint data with appropriate controls, p53 activation measurements, and apoptosis assays with statistical significance.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation of computational design
- **Claim pointer** The authors claim identification of PCNA binders and design of nanobodies targeting PCNA and BCL6 using computational methods.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract lists computational tools but does not show any validation of the designed binders, such as binding affinity measurements, structural characterization, or functional confirmation. The use of AlphaFold3 and HADDOCK is mentioned but no predicted models or experimental corroboration are presented.
- **Why it matters** Computational predictions can be inaccurate. Without experimental validation, the designed binders may not actually bind their targets, undermining the entire bioPROTAC approach.
- **Resolution test** Show binding data, such as surface plasmon resonance or isothermal titration calorimetry, and structural validation, such as crystallography or cryo-EM, for at least one designed binder per target.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Specificity and off-target effects
- **Claim pointer** The authors claim enhanced specificity of degradation through their bioPROTAC system.
- **Evidence pointer** Abstract text; location not provided
- **Concern** No data are provided on selectivity of degradation. It is unclear whether the RS80E domain or the binders cause off-target degradation or toxicity.
- **Why it matters** Specificity is critical for therapeutic applications. Off-target effects could negate any therapeutic benefit and raise safety concerns.
- **Resolution test** Provide proteomics or targeted assays demonstrating that PCNA and BCL6 are degraded without significant off-target effects, and include cell viability controls.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract wording
- **Evidence pointer** Abstract text; location not provided
- **Issue** The phrase "exploration other intractable therapeutic targets" is grammatically incorrect and unclear.
- **Required correction** Revise to "exploration of other intractable therapeutic targets."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methodological description
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract does not clarify whether peptide binders and nanobodies were used interchangeably or for different targets, and how their performance compared.
- **Required correction** Specify which binder type was used for each target and provide comparative context.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Use of "bioPROTACs"
- **Evidence pointer** Abstract text; location not provided
- **Issue** The term "bioPROTACs" is used without definition or context for readers unfamiliar with the concept.
- **Required correction** Define the term at first use, such as "biological proteolysis-targeting chimeras."

## Risk / unsupported claims
- The claim that the bioPROTAC system degrades PCNA and BCL6 is unsupported by visible data.
- The claim that degradation activates p53 and promotes apoptosis is unsupported.
- The claim that the designed binders and nanobodies are functional is unsupported.
- The claim of a "modular and rapid pathway" for other targets is not evidenced.
- The overall therapeutic potential is asserted without experimental backing.