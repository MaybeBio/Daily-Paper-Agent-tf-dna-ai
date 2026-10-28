## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, conclusions) as provided
- **Assessment boundary** Scientific content, experimental design, data interpretation, and internal consistency of the reported findings
- **Shared manuscript claim summary** The authors report that natural compounds from licorice and turmeric, particularly isoliquiritin (ILQ) and curcumin (CUR), bind to the HIV-NCp7 C-terminal zinc finger domain via noncovalent interactions, with ILQ showing the strongest binding. The binding is proposed to involve π-π stacking with tryptophan, and a three-step mechanism of noncovalent recognition followed by zinc ejection and cysteine oxidation is suggested for ILQ.
- **Visible evidence base** Fluorescence quenching data (Figures 3, S1-S3), mass spectrometry data (Figures 4, S4-S8, Table 1), CD spectroscopy (Figures 2, 5), molecular docking (Figure 6)
- **Missing materials affecting confidence** Raw fluorescence titration curves with quantitative binding constants, full mass spectra with peak assignments for all species, CD spectra with quantitative secondary structure analysis, docking scores and validation metrics, experimental replicates and statistical analysis, positive/negative control data for the assays

## Reviewer
- **Overall assessment** The manuscript addresses a potentially interesting question regarding the molecular basis of antiviral activity of natural compounds from licorice and turmeric against HIV-NCp7. The combination of fluorescence, mass spectrometry, CD spectroscopy, and molecular docking is appropriate for studying protein-ligand interactions. However, the study is largely qualitative and preliminary. The key claims regarding binding strength and mechanism are not quantitatively supported. The proposed three-step mechanism involving zinc ejection and cysteine oxidation is speculative and not directly tested. The manuscript would benefit from quantitative binding measurements, more rigorous mass spectrometry analysis, and direct experimental evidence for the proposed mechanism.
- **Who would be interested in the results, and why** Researchers in the fields of antiviral drug discovery, natural product chemistry, and HIV biology may find the results of interest. The study provides a preliminary screening of natural compounds against a validated HIV target and suggests a potential mechanism of action. However, the lack of quantitative data and functional assays limits the impact for medicinal chemists seeking to optimize lead compounds or virologists seeking to validate the target.
- **Major strengths** The study addresses a relevant and under-explored target (HIV-NCp7) for antiviral intervention. The use of multiple complementary biophysical techniques (fluorescence, MS, CD, docking) is commendable. The selection of natural compounds from traditional medicines with known anti-HIV activity provides a logical rationale for the study. The observation of noncovalent adducts by mass spectrometry is a useful qualitative finding.
- **Major Concerns** 
  - R1-M1: The claim that ILQ has the "strongest binding ability" is not quantitatively supported. Fluorescence quenching is presented only as qualitative observations without calculated binding constants, Stern-Volmer analysis, or thermodynamic parameters.
  - R1-M2: The mass spectrometry data are not presented with sufficient detail to support the assignment of noncovalent versus covalent adducts. The relative intensities of species are described qualitatively, and the claim that "noncovalent recognition will gradually induce covalent binding" is not supported by time-course data showing a transition.
  - R1-M3: The proposed three-step mechanism (noncovalent binding, zinc ejection, cysteine oxidation) is speculative. No direct experimental evidence is provided for zinc ejection or cysteine oxidation. The observation of a minor covalent adduct for ILQ does not establish this mechanism.
  - R1-M4: The CD spectroscopy data are used to claim that the zinc finger structure is formed and that ligand binding does not change the secondary structure. However, the data are not quantitatively analyzed, and the sensitivity of CD to detect subtle conformational changes is limited.
  - R1-M5: The molecular docking results are presented without scoring functions, validation, or consideration of alternative binding modes. The claim of "edge-to-face" and "face-to-face" π-π stacking is based on visual inspection of a single docking pose.
- **Minor Comments**
  - R1-m1: The fluorescence assay for LQ is confounded by its intrinsic fluorescence, as acknowledged. However, no alternative method is used to assess LQ binding, and the statement that LQ has "similar extent of quenching" is not interpretable.
  - R1-m2: The manuscript states that "the inhibiting activity of ILQ towards the binding between the zinc finger peptide and nuclear acid should be tested in the future." This is a significant limitation that should be acknowledged more prominently in the abstract and conclusions.
  - R1-m3: The methods section lacks details on the number of replicates, error analysis, and statistical treatment of the data.
  - R1-m4: The docking grid box size (20 Å × 20 Å × 20 Å) is relatively small for a peptide of this size, and the choice of the binding site is not justified.
  - R1-m5: The manuscript would benefit from a positive control (e.g., a known NCp7 inhibitor) to validate the assay conditions.
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative binding), R1-M2 (MS data rigor), R1-M3 (mechanistic evidence), R1-M4 (CD analysis)
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The application of biophysical methods to study natural compound binding to NCp7 is not entirely novel, though the specific compounds tested add some originality.
  - Scientific importance: Moderate. NCp7 is a validated target, but the study does not provide functional data linking binding to antiviral activity, limiting its significance.
  - Interdisciplinary readership: Limited. The study is primarily of interest to biophysical chemists and natural product researchers; the lack of virological data reduces its appeal to a broader readership.
  - Technical soundness: The techniques are appropriate, but the analysis is insufficiently rigorous and quantitative to support the claims.
  - Readability for nonspecialists: The manuscript is generally readable, but the significance of the findings for antiviral therapy is not clearly articulated for a general audience.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires substantial additional quantitative data and direct mechanistic evidence before the claims can be considered supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative support for binding affinity
- **Claim pointer** "ILQ has the strongest binding ability among the tested compounds, followed by curcumin"
- **Evidence pointer** Figure 3, Figure S2, Section 2.2
- **Concern** The claim of differential binding strength is based on qualitative fluorescence quenching observations. No binding constants (Kd), Stern-Volmer constants, or other quantitative parameters are reported. The titration data shown in Figure S2 are not analyzed to extract thermodynamic or kinetic information. Without quantitative analysis, the ranking of binding affinities is not supported.
- **Why it matters** The central conclusion of the manuscript is that ILQ is the strongest binder. Without quantitative binding data, this conclusion cannot be evaluated, and the study does not provide useful information for structure-activity relationship analysis or compound prioritization.
- **Resolution test** Provide Stern-Volmer analysis or calculate binding constants from the fluorescence titration data. Report Kd values with errors for each compound. Alternatively, use an orthogonal quantitative method such as isothermal titration calorimetry or surface plasmon resonance.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Mass spectrometry data interpretation
- **Claim pointer** "The observation of noncovalent species and free zinc finger indicates the noncovalent binding mode between ILQ and the zinc finger at the early time points" and "noncovalent recognition will gradually induce covalent binding"
- **Evidence pointer** Figure 4, Figures S4-S8, Table 1, Section 2.3
- **Concern** The mass spectrometry data are presented without sufficient detail. The relative intensities of the noncovalent adduct versus free zinc finger are described qualitatively. The claim that noncovalent binding "gradually induces" covalent binding implies a time-dependent transition, but the time-course data (Figure S4) are described as showing "similar" relative intensities at different time points, which contradicts this claim. The identification of the covalent adduct as an "oxidized peptide with ILQ" is not supported by detailed fragmentation data or MS/MS analysis.
- **Why it matters** The proposed mechanism depends on the distinction between noncovalent and covalent binding modes and the temporal relationship between them. If the data do not show a time-dependent increase in covalent adduct, the proposed mechanism is not supported.
- **Resolution test** Provide quantitative relative abundances of all species at each time point. Show MS/MS fragmentation data to confirm the site and nature of the covalent modification. Demonstrate a clear time-dependent increase in the covalent adduct to support the "gradual induction" claim.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic evidence
- **Claim pointer** "Firstly, the molecule recognizes and binds NC noncovalently; in the second step, the ejection of zinc from the noncovalent adduct deprotects the cysteine amino acid in zinc finger; in the final step, the oxidation of cysteine is induced by the unsaturated keto group of ILQ"
- **Evidence pointer** Section 2.3, Section 2.4
- **Concern** The proposed three-step mechanism is presented as a conclusion, but no direct experimental evidence is provided for zinc ejection or cysteine oxidation. The CD data show no change in secondary structure upon ligand binding, which does not support zinc ejection. The observation of a minor covalent adduct for ILQ is insufficient to establish this specific mechanism. The role of the "unsaturated keto group" is not tested with analogs or mutants.
- **Why it matters** The mechanistic claim is a major part of the manuscript's significance. Without direct evidence, the mechanism remains speculative, and the study does not provide a clear understanding of how these compounds might inhibit NCp7 function.
- **Resolution test** Use zinc-sensitive fluorescent dyes or atomic absorption spectroscopy to directly measure zinc release upon ligand binding. Use thiol-reactive probes to detect cysteine oxidation. Test ILQ analogs lacking the unsaturated keto group to establish its role. Perform mutagenesis of the cysteine residues to confirm the modification site.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** CD spectroscopy analysis
- **Claim pointer** "Incubation with CUR or ILQ for 2 h does not change the secondary structure of ZF"
- **Evidence pointer** Figure 5, Section 2.4
- **Concern** The CD spectra are presented without quantitative analysis. The similarity between the spectra is assessed visually. No secondary structure deconvolution or quantitative comparison (e.g., root-mean-square deviation) is provided. The sensitivity of CD to detect local conformational changes in a small peptide is limited.
- **Why it matters** The CD data are used to support the noncovalent binding mode by showing no structural change. However, the lack of quantitative analysis weakens this conclusion, and the interpretation may be overreaching given the limitations of CD.
- **Resolution test** Perform secondary structure deconvolution of the CD spectra and report the percentage of each secondary structure element. Provide a quantitative comparison of the spectra with appropriate statistical analysis. Consider complementary techniques such as NMR or molecular dynamics simulations.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Docking validation
- **Claim pointer** "Molecular docking revealed edge-to-face π-π stacking between the protein tryptophan and ILQ aromatic ring" and "face-to-face π-π stacking was observed between the protein tryptophan and CUR aromatic ring"
- **Evidence pointer** Figure 6, Section 2.4
- **Concern** The docking results are presented without scoring functions, binding energies, or any validation of the docking protocol. Only a single pose is shown for each compound. No consideration is given to alternative binding modes, conformational flexibility, or the reliability of the docking predictions.
- **Why it matters** Docking results are highly dependent on the protocol and scoring function. Without validation and quantitative scores, the proposed binding modes are not reliable, and the structural interpretation may be misleading.
- **Resolution test** Report docking scores and estimated binding energies. Perform redocking with different protocols or software to confirm the results. Consider ensemble docking or molecular dynamics simulations to account for flexibility. Validate the docking predictions with experimental data such as mutagenesis or NMR chemical shift perturbations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Assay interference
- **Affected element** Fluorescence data for LQ
- **Evidence pointer** Section 2.2, Figure S1
- **Issue** The intrinsic fluorescence of LQ interferes with the quenching measurement, as acknowledged. However, no alternative method is used to assess LQ binding, and the statement that LQ has "similar extent of quenching" is not interpretable given the interference.
- **Required correction** Either exclude LQ from the quantitative comparison or use an alternative method (e.g., ITC, MST) to assess LQ binding. Clearly state that LQ binding could not be reliably assessed by fluorescence.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Scope of conclusions
- **Affected element** Abstract and Conclusions
- **Evidence pointer** Abstract, Section 4
- **Issue** The abstract and conclusions state that the study provides "scientific evidence and hints of the antiviral activity of turmeric and licorice." However, no antiviral activity data are presented, and the link between NCp7 binding and antiviral activity is not established.
- **Required correction** Soften the language to clearly state that the study provides preliminary biophysical characterization of binding, and that the relevance to antiviral activity remains to be established.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Experimental replicates
- **Affected element** All experiments
- **Evidence pointer** Section 3.2
- **Issue** No information is provided on the number of replicates for any experiment. The fluorescence, MS, and CD data appear to be from single measurements.
- **Required correction** Provide information on the number of replicates and report data as mean ± standard deviation where applicable. For MS, indicate the number of independent experiments.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Docking methodology
- **Affected element** Section 3.2.4
- **Issue** The docking methodology lacks important details, including the preparation of the protein structure, the search space definition, the exhaustiveness parameter, and the scoring function used.
- **Required correction** Provide a complete description of the docking protocol, including software version, parameters, and validation of the docking setup.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Positive control
- **Affected element** Fluorescence assay
- **Evidence pointer** Section 2.2
- **Issue** No positive control is used to validate the fluorescence quenching assay. A known NCp7 binder or a tryptophan-quenching compound would help confirm the assay is working as expected.
- **Required correction** Include a positive control in the fluorescence assay to validate the experimental setup.

## Risk / unsupported claims
- The claim that ILQ has the "strongest binding ability" is unsupported due to lack of quantitative binding data.
- The claim that "noncovalent recognition will gradually induce covalent binding" is unsupported by the time-course data presented.
- The proposed three-step mechanism (noncovalent binding, zinc ejection, cysteine oxidation) is speculative and not directly tested.
- The statement that the study provides "scientific evidence and hints of the antiviral activity" is unsupported as no antiviral activity data are presented.
- The claim of specific π-π stacking interactions from docking is not validated and should be considered preliminary.