## Review setup
- **Input scope** Full manuscript text (abstract, results, discussion, methods) without figures or supplementary data
- **Assessment boundary** Scientific claims and evidence as presented in the text; figures, tables, and supplementary materials referenced but not directly examined
- **Shared manuscript claim summary** The authors report that HpARI1 and HpARI2, but not HpARI3, bind heparan sulphate (HS) via a positively charged patch in their CCP1 domains, and that this binding extends the in vivo half-life of HpARI2 at the site of administration. DNA binding is also mapped to CCP1, and a pentaR mutant lacking both DNA and HS binding shows reduced in vivo half-life.
- **Visible evidence base** Text descriptions of EMSA, gel filtration, pull-down assays, flow cytometry, isothermal calorimetry, AlphaFold modelling, and in vivo mouse experiments; specific figures referenced but not viewable
- **Missing materials affecting confidence** All figures, figure supplements, and numerical data; exact experimental replicates and statistical outputs; full methods details for some assays; uncropped western blot (referenced as supplement)

## Reviewer
- **Overall assessment** This manuscript presents a clear and potentially important advance in understanding how helminth immunomodulatory proteins achieve localised, sustained activity. The identification of HS binding as a determinant of in vivo half-life is mechanistically plausible and well supported by the described experiments. However, the absence of key quantitative data, particularly for the in vivo half-life measurements and the HS binding affinities, limits the strength of the central claim. The manuscript would benefit from clearer presentation of the relationship between DNA binding, HS binding, and the observed in vivo effects.
- **Who would be interested in the results, and why** Researchers studying helminth immunomodulation, IL-33 biology, and protein engineering for therapeutic applications. The finding that extracellular matrix binding can prolong the half-life of small immunomodulatory proteins has direct relevance for the design of protein therapeutics, and the HpARI family provides a tractable model system for studying how parasites achieve tissue-localised immunoregulation.
- **Major strengths** The study addresses a clear and important question: how do HpARI proteins achieve sustained local effects despite their small size? The use of domain-swapped chimeras and a targeted pentaR mutant provides a rigorous approach to dissecting the molecular determinants of HS and DNA binding. The combination of biochemical, biophysical, and in vivo approaches is appropriate and complementary. The finding that HpARI3 lacks HS binding, correlating with its distinct functional role, adds biological coherence to the model.
- **Major Concerns** The central claim that HS binding extends in vivo half-life is supported by only one timepoint (15 min) for IL-33 release and indirect measurements of downstream responses. The quantitative relationship between HS binding affinity and half-life is not established. The physiological relevance of the measured HS binding affinities (micromolar range) is not discussed in the context of extracellular HS concentrations. The manuscript does not address whether the pentaR mutant has any structural perturbations beyond the loss of the charged patch.
- **Minor Comments** The abstract states that HpARI1 showed a "similar trend" in the IL-33 release assay that did not reach significance; this should be clarified. The discussion of Hp-TGM proteins, while interesting, is somewhat lengthy relative to the direct findings. The term "half-life" is used to describe what appears to be persistence of functional activity, which should be defined more precisely.
- **Technical failings that need to be addressed before the case is established** The in vivo half-life measurements are not directly quantified; the manuscript relies on functional readouts (eosinophilia, ILC2 activation) at a single 24 h timepoint. The ITC data for HpARI1-HS binding is described as 9.6 μM, but the stoichiometry and thermodynamic parameters are not reported. The pentaR mutant is described as lacking both DNA and HS binding, but the manuscript does not show that this mutant retains normal protein folding or stability.
- **Assessment against Nature-style criteria** Originality: High. The identification of HS binding as a determinant of in vivo half-life for helminth immunomodulatory proteins is novel and conceptually important. Scientific importance: High. The findings have implications for understanding helminth-host interactions and for protein therapeutic design. Interdisciplinary readership: Moderate. The work will appeal primarily to immunologists and parasitologists, with some interest from protein engineers. Technical soundness: Moderate. The experimental approaches are appropriate, but the lack of direct half-life quantification and limited biophysical characterisation weaken the central claim. Readability for nonspecialists: Good. The manuscript is clearly written and the logic is easy to follow, though some specialised terminology is used without definition.
- **Recommendation posture** Supportive if technical concerns are resolved. The core finding is likely correct and important, but the manuscript needs direct quantification of in vivo half-life and more complete biophysical characterisation of the HS binding interaction before the case is fully established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for central claim
- **Claim pointer** "This extracellular matrix binding extends the half-life of HpARI2 in vivo at the site of administration."
- **Evidence pointer** Results section "HpARI fusion proteins show unexpected effects on IL-33 responses in vivo"; Figures 2 and 3 (referenced, not viewable)
- **Concern** The central claim that HS binding extends in vivo half-life is supported by indirect functional readouts (eosinophilia, ILC2 activation) at a single 24 h timepoint, rather than direct measurement of protein persistence or clearance. The 15 min IL-33 release measurement (Fig 2B) assesses tethering, not half-life. The experiments where HpARI proteins were administered 1, 3, or 7 days prior to Alternaria (Fig 3) provide a timecourse, but the readout is still downstream functional activity, not protein concentration. This is a meaningful distinction because the authors propose a mechanism (HS-mediated retention) that should be directly testable by measuring protein levels in tissue or bronchoalveolar lavage over time.
- **Why it matters** The title and abstract make a specific mechanistic claim about in vivo half-life. Without direct measurement of protein persistence, the data are consistent with alternative explanations, such as differences in intrinsic protein stability or differential cellular uptake. The distinction matters for the proposed model and for any therapeutic applications.
- **Resolution test** Provide direct measurement of HpARI2, HpARI2_pentaR, and HpARI3 protein levels in lung tissue or bronchoalveolar lavage at multiple timepoints after administration, using a quantitative assay (e.g., ELISA, western blot with known standards, or labelled protein tracking). Alternatively, provide pharmacokinetic data showing differential clearance rates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative characterisation of HS binding
- **Claim pointer** "HpARI1 had an affinity for HS of 9.6 μM, while HpARI2 had a slightly higher affinity of 4.2 μM."
- **Evidence pointer** Results section "HpARI2 binds to heparan sulphate"; Figure 4D-F (referenced, not viewable)
- **Concern** The ITC experiments are described as showing micromolar affinities, but the manuscript does not report stoichiometry, enthalpy, entropy, or the number of replicates beyond "done twice." The HS tetrasaccharide used is a minimal binding unit, and the affinity for full-length heparan sulphate chains or cell-surface proteoglycans may differ substantially. The relationship between these in vitro affinities and the proposed in vivo retention mechanism is not quantitatively addressed.
- **Why it matters** The physiological relevance of micromolar affinity for HS is unclear. Many HS-binding proteins have affinities in the nanomolar range, and the local concentration of HS in the extracellular matrix is not discussed. Without a quantitative framework, it is difficult to assess whether the proposed retention mechanism is plausible at the measured affinities.
- **Resolution test** Report full ITC parameters (stoichiometry, ΔH, ΔS) and show representative titration curves. Discuss the measured affinities in the context of known HS-binding proteins and estimated extracellular HS concentrations. If possible, measure binding to cell-surface proteoglycans or intact extracellular matrix.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Structural validation of the pentaR mutant
- **Claim pointer** "A pentaR mutant of HpARI2 (with each of the indicated Arg resides mutated to Ala) was expressed. HpARI2_pentaR had identical IL-33 suppressive activity in vitro as compared to HpARI2 wild-type... lacked binding to both heparin and DNA."
- **Evidence pointer** Results section "HpARI2:HS interactions are mediated by CCP1 arginine residues"; Figure 6 (referenced, not viewable)
- **Concern** The manuscript shows that the pentaR mutant retains IL-33 suppressive activity, which is a functional readout, but does not demonstrate that the mutant is properly folded or structurally equivalent to the wild-type protein. Alanine mutations of five arginine residues could cause local or global structural perturbations beyond the loss of the charged patch. The conclusion that the charged patch specifically mediates HS and DNA binding would be strengthened by structural validation.
- **Why it matters** If the pentaR mutations cause misfolding or aggregation, the loss of HS and DNA binding could be a non-specific consequence rather than evidence for the specific role of the charged patch. This would weaken the mechanistic model.
- **Resolution test** Provide circular dichroism spectra, size-exclusion chromatography profiles, or a crystal structure of the pentaR mutant to demonstrate structural integrity. Alternatively, show that a mutant with a disrupted charged patch but preserved overall structure (e.g., charge-neutralising mutations that are not alanine) has the same phenotype.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of data presentation
- **Affected element** Figure 1B-C and accompanying text
- **Evidence pointer** Results section "HpARI1 and HpARI2 bind to DNA, while HpARI3 does not"; Figure 1 (referenced, not viewable)
- **Issue** The text states that HpARI1 showed a "similar trend" to HpARI2 in suppressing IL-33 release, but this did not reach statistical significance. The distinction between a trend and a significant effect is important for interpreting the relative activities of HpARI1 and HpARI2.
- **Required correction** Clarify whether the lack of significance reflects low statistical power or a genuinely weaker effect. Report the effect size and confidence intervals for the HpARI1 comparison.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Use of "half-life" throughout
- **Evidence pointer** Abstract; Results section "HpARI fusion proteins show unexpected effects on IL-33 responses in vivo"; Discussion
- **Issue** The term "half-life" is used to describe functional persistence (e.g., ability to suppress responses when administered days before challenge), but no pharmacokinetic measurement is presented. This conflation could mislead readers.
- **Required correction** Use "functional persistence" or "duration of activity" where direct protein measurement is not available, and reserve "half-life" for instances where protein concentration is directly measured over time.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Cell binding assays
- **Evidence pointer** Methods section "Cell binding assays"
- **Issue** The methods describe preparation of HpARI tetramers and staining of lung cells, but do not specify how binding was quantified (e.g., median fluorescence intensity, percentage of positive cells) or how background binding was controlled.
- **Required correction** Provide details on the gating strategy for tetramer-positive cells, the use of a negative control (e.g., HpARI3 tetramer or a non-binding mutant), and the statistical test used to compare binding between proteins.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of alternative explanations
- **Affected element** Discussion section
- **Evidence pointer** Discussion, paragraph on the proposed model
- **Issue** The discussion proposes a model where HpARI3 diffuses freely to amplify IL-33 responses at distal sites, but does not consider whether the lack of HS binding might instead result in more rapid clearance and therefore reduced activity. The authors should address this alternative interpretation.
- **Required correction** Add a sentence acknowledging that the lack of HS binding could also lead to faster clearance, and explain why the data support the diffusion model over the clearance model.

## Risk / unsupported claims
- The claim that HS binding "extends the half-life" of HpARI2 is not directly supported by protein persistence measurements; the data show extended functional activity, which is a related but distinct claim.
- The statement that HpARI1 and HpARI2 "have long-lasting effects at the site of deposition" is inferred from the HS binding data and the in vivo experiments with HpARI2, but no direct evidence for HpARI1 persistence is presented.
- The physiological relevance of the measured HS binding affinities (micromolar range) is not established, and the manuscript does not discuss whether these affinities are sufficient for retention in the extracellular matrix.
- The claim that the pentaR mutant specifically disrupts the HS/DNA binding surface is not supported by structural validation; the mutations could have non-specific effects on protein folding or stability.
- The model proposing that HpARI3 diffuses to distal sites to amplify IL-33 responses is speculative and not directly tested.