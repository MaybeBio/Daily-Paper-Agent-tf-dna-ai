## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, acknowledgements, author contributions) without figures or supplementary materials
- **Assessment boundary** Scientific claims, experimental design, computational modeling, and internal consistency as presented in the provided text
- **Shared manuscript claim summary** The authors propose a fully humanized DUX4 DNA-binding domain (DBD) and a DBD-KRAB fusion protein as competitive inhibitors and epigenetic silencers of DUX4-FL transcriptional activity, supported by cell-based reporter assays and three complementary computational models, as a potential therapeutic strategy for FSHD
- **Visible evidence base** Reporter assay data in HEK293T and C2C12 cells (described in Sections 2.3, 3.1-3.3), computational models (Sections 2.5-2.7, 3.4-3.6), plasmid construction details (Section 2.1)
- **Missing materials affecting confidence** Figures 1 and 2 (all panels), raw data files, statistical analysis outputs, supplementary methods, plasmid maps, model code documentation beyond the GitHub link, and any experimental replicates beyond what is described in text

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting extension of prior work on DUX4 DBD-based competitive inhibition, with the addition of a KRAB domain being a logical and potentially valuable innovation. However, the experimental evidence as described is limited to transient transfection reporter assays in immortalized cell lines, and the computational models are presented with substantial caveats that undermine their current utility. The manuscript would benefit from validation in patient-derived myotubes and more rigorous quantitative analysis before the therapeutic claims can be considered established.
- **Who would be interested in the results, and why** Researchers in the FSHD field, particularly those working on DUX4-targeted therapeutic strategies; investigators interested in competitive inhibition of transcription factors and epigenetic silencing approaches; computational biologists studying transcription factor binding dynamics and spatial diffusion in syncytial tissues; and gene therapy developers focused on muscle diseases.
- **Major strengths** The concept of converting DUX4 from an activator to a repressor using a fully humanized construct is elegant and addresses known limitations of Cas-based systems. The inclusion of three complementary computational models demonstrates a thoughtful approach to dosing and delivery considerations. The authors are appropriately cautious in their interpretation of the computational results and acknowledge key limitations.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of direct binding evidence), R1-M2 (unvalidated computational models), R1-M3 (inadequate cell model), R1-M4 (statistical reporting deficiencies)
- **Assessment against Nature-style criteria** Originality: moderate. The DBD competitive inhibition concept is not new, though the KRAB fusion is a novel combination. Scientific importance: potentially high if validated, but current evidence is insufficient. Interdisciplinary readership: the work spans molecular biology, computational modeling, and therapeutic development, which could appeal to a broad audience. Technical soundness: the experimental work is straightforward but incomplete; the computational models have significant unvalidated assumptions. Readability for nonspecialists: the manuscript is generally well-written and accessible, though some computational details are dense.
- **Recommendation posture** Currently not established from the provided evidence. The core claims require additional experimental validation and more rigorous computational treatment before the therapeutic potential can be assessed.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental evidence
- **Claim pointer** The authors claim that DBD acts as a competitive inhibitor of DUX4-FL at its genomic target sites, and that DBD-KRAB enhances this repression through epigenetic silencing
- **Evidence pointer** Sections 3.1-3.3, Figure 1 (not provided)
- **Concern** The manuscript does not provide direct evidence of competitive binding between DBD and DUX4-FL at DNA target sites. The reporter assay demonstrates reduced transcriptional output, but this could result from multiple mechanisms, including squelching, non-specific DNA binding, or indirect effects on cell viability. No electrophoretic mobility shift assays, chromatin immunoprecipitation, or surface plasmon resonance experiments are described. Furthermore, the claim that KRAB-mediated epigenetic silencing occurs is inferred solely from increased repression, without direct measurement of histone modifications (e.g., H3K9me3) or chromatin accessibility changes at DUX4 target loci.
- **Why it matters** The mechanistic claims are central to the therapeutic rationale. Without direct evidence of competitive binding and epigenetic remodeling, the observed repression could be attributed to alternative, potentially less specific mechanisms. This distinction is critical for predicting efficacy and safety in vivo.
- **Resolution test** Provide direct binding assays (e.g., EMSA or ChIP) demonstrating that DBD occupies DUX4 consensus sites and that DUX4-FL binding is reduced in the presence of DBD. For the KRAB fusion, perform ChIP for H3K9me3 or KAP1 recruitment at known DUX4 target genes in treated versus untreated cells.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational model validity
- **Claim pointer** The authors claim that the three computational models "illustrate how DBD concentration, intracellular diffusion, and population-level cell state transitions may relate to therapeutic efficacy"
- **Evidence pointer** Sections 2.5-2.7, 3.4-3.6, Figure 2 (not provided)
- **Concern** The computational models are presented with substantial caveats that limit their interpretability. The competitive binding model assumes equal dissociation constants for DBD and DUX4-FL without experimental justification. The diffusion model relies on an interpolated diffusion coefficient that has not been empirically measured for DBD. The ODE model is described as using "exploratory assumptions" for key parameters, and the infection rate is not explicitly coupled to DBD concentration in the current version. The authors state that the ODE model "illustrates the temporal structure" rather than quantifying treatment effects, which significantly limits its contribution. Without parameter validation or sensitivity analyses presented in the text, these models currently serve as illustrative exercises rather than predictive tools.
- **Why it matters** The computational framework is presented as a key contribution of the manuscript. If the models cannot make quantitative predictions or be validated against experimental data, their value in guiding dosing and delivery strategies is unclear. The authors themselves acknowledge that the models are not yet predictive, which undermines their stated purpose.
- **Resolution test** Validate model parameters experimentally where feasible (e.g., measure DBD-DNA binding affinity). Present sensitivity analyses for all key parameters. Explicitly couple the ODE model to DBD concentration and validate model predictions against time-course experimental data. If the models are intended as illustrative, state this clearly and describe what specific insights they provide beyond qualitative expectations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Physiological relevance
- **Claim pointer** The authors state that "validation in human FSHD-patient-derived myotubes... is essential" and acknowledge that their experiments used "DUX4-FL concentrations that exceeded physiological FSHD levels"
- **Evidence pointer** Section 4 (Discussion)
- **Concern** All experimental data were generated in HEK293T and C2C2 cells using transient transfection with supraphysiological DUX4-FL levels. While the authors acknowledge this limitation, the absence of any data in patient-derived or primary muscle cells means that the therapeutic potential of the constructs in the actual disease context remains entirely unaddressed. The C2C12 experiments, while in a muscle lineage, still used overexpression conditions that do not recapitulate the sporadic, low-level DUX4 expression characteristic of FSHD.
- **Why it matters** The therapeutic claim is predicated on the ability of DBD/DBD-KRAB to suppress DUX4 activity at physiologically relevant concentrations. Overexpression conditions may mask efficacy failures that would be apparent at lower, more relevant DUX4 levels. Additionally, the chromatin environment and transcriptional machinery in immortalized cell lines may differ substantially from patient-derived myotubes.
- **Resolution test** Repeat key experiments in FSHD patient-derived myotubes with endogenous DUX4 expression. If this is not feasible, provide a clear rationale for why the current models are sufficient to support the therapeutic claims, or temper the claims accordingly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors report statistically significant differences between DBD and DBD-KRAB treatments at various doses
- **Evidence pointer** Sections 3.2-3.3
- **Concern** The statistical methods are described only as "Two-way ANOVA" with "Tukey's multiple comparisons test," but no effect sizes, confidence intervals, or exact p-values are reported in the text. The number of biological replicates is stated as "biological replicates" without specifying the number. The normalization procedure (background subtraction, setting negative values to 1) could introduce bias, particularly for conditions with very low fluorescence. The claim that DBD-KRAB at 25x "brought fluorescence to the background levels of untransfected conditions" while also reporting a 949-fold decrease requires clarification of how background was defined and whether this represents a floor effect.
- **Why it matters** The quantitative claims of differential efficacy between DBD and DBD-KRAB are central to the manuscript's contribution. Without transparent reporting of variability and statistical parameters, the robustness of these claims cannot be assessed.
- **Resolution test** Report exact p-values, effect sizes, confidence intervals, and the number of independent biological replicates for all comparisons. Provide raw data or a clear data availability statement. Justify the normalization procedure and discuss its potential impact on the results.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Nomenclature
- **Affected element** Section 3.3
- **Evidence pointer** "C12C12 cells" (likely a typo for C2C12)
- **Issue** The cell line is referred to as "C12C12" in Section 3.3, which appears to be a typographical error.
- **Required correction** Correct to "C2C12" throughout.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Section 2.7 vs. Section 3.6
- **Evidence pointer** Section 2.7 states the ODE model includes "stochastic gene expression using the Poisson-Beta distribution framework" and "the infection rate β... was modulated dynamically by the real-time DBD:FL ratio," while Section 3.6 states the ODE model "illustrates the temporal behavior... in the absence of an explicit DBD intervention"
- **Issue** There is an apparent contradiction between the methods description, which describes DBD-dependent modulation, and the results description, which states the model was run without DBD intervention.
- **Required correction** Clarify whether the ODE model includes DBD-dependent effects or not, and reconcile the methods and results descriptions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Section 3.1
- **Evidence pointer** "constructed from a previously validated DUX4-sensitive reporter. 1"
- **Issue** The reference number "1" appears to be incorrect, as reference 1 in the introduction is cited for FSHD epidemiology.
- **Required correction** Verify the correct reference for the reporter construct and update the citation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Methods detail
- **Affected element** Section 2.3
- **Evidence pointer** "Media was replaced six hours after transfection with media containing doxycycline (250 ng/mL)"
- **Issue** The concentration is given as "250 ng/mL" but later in Section 3.5 it is stated as "25 ng/µL," which is equivalent to 25,000 ng/mL. This is a 100-fold discrepancy.
- **Required correction** Correct the concentration to be consistent between methods and results.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Model description
- **Affected element** Section 2.5
- **Evidence pointer** "K D is the dissociation constant, assumed to be the same for both DBD and DUX4-FL, and is 1.4 μM. 51"
- **Issue** The assumption of equal K D values for DBD and DUX4-FL is stated but not justified. If the KRAB domain alters the binding affinity or if the truncated DBD has different DNA-binding characteristics, this assumption may be invalid.
- **Required correction** Provide justification for this assumption or discuss the potential impact of unequal K D values on model predictions.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Figure availability
- **Affected element** Figures 1 and 2
- **Evidence pointer** Not provided in the manuscript text
- **Issue** The manuscript references Figures 1 and 2 extensively, but these are not included in the provided text. The statistical results and model outputs cannot be fully evaluated without the figures.
- **Required correction** Ensure figures are included in any submission and that all data points, error bars, and statistical annotations are clearly presented.

## Risk / unsupported claims
- The claim that DBD acts as a competitive inhibitor at genomic target sites is unsupported by direct binding data; the reporter assay is consistent with but does not prove this mechanism
- The claim that DBD-KRAB produces epigenetic silencing is inferred from reporter repression without direct chromatin analysis
- The computational models are presented as illustrative but the text implies they provide dosing guidance; the models are not validated against experimental data and key parameters are assumed
- The claim that the approach "may help circumvent the immunogenicity and delivery limitations of Cas-based systems" is speculative, as no immunogenicity or delivery data are presented
- The statement that DBD "comprising both homeodomains" acts as a competitive inhibitor is presented as established, but the text notes this is a "strategy" and "aims to" rather than demonstrated fact
- The diffusion model prediction that a nucleus 250 µm away could receive ~20% of the dose is presented without experimental validation or discussion of the simplifying assumptions' impact on this estimate