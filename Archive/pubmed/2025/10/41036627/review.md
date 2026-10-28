## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Materials and Methods, Results, Discussion, Funding, Data availability, Acknowledgements)
- **Assessment boundary** Scientific content, methodological rigor, internal consistency, and support of claims by presented evidence. No assessment of editorial fit or journal-specific policy.
- **Shared manuscript claim summary** The authors present an integrative structural biology study combining SAXS, HDX-MS, and MD simulations to characterize the RAR/RXR heterodimer bound to four DNA response elements (DR0, DR0L, DR1, DR5, IR0) in complex with corepressor NCoRNID or coactivator TIF-2NRID. They report DNA-sequence-dependent conformational differences in the heterodimer, long-range allosteric effects propagating from DNA to the ligand-binding domains, and differential coregulator recruitment modulated by DNA identity.
- **Visible evidence base** Abstract, full Introduction, full Materials and Methods, full Results, full Discussion, Funding, Data availability, Acknowledgements. Supplementary figures and tables are referenced but not provided.
- **Missing materials affecting confidence** Supplementary Figures S1–S9, Supplementary Tables S1–S4, crystallographic data for the IR0 complex, raw SAXS curves, HDX-MS differential plots, MD simulation trajectories, and the deposited structure (PDB 9QJ9) were not available for inspection. These are essential for verifying key claims.

## Reviewer
- **Overall assessment** This manuscript presents a technically ambitious integrative study addressing an important question in nuclear receptor biology: how DNA response elements allosterically modulate coregulator recruitment to the RAR/RXR heterodimer. The combination of solution biophysics (SAXS, HDX-MS) with MD simulations is appropriate and potentially powerful. However, the manuscript as presented has several significant issues. First, the central claim of DNA-dependent conformational differences is supported primarily by SAXS data with modest resolution and by MD simulations whose validation depends on fitting to those same SAXS data, creating a circularity concern. Second, key quantitative results (binding affinities, HDX differences) are presented without adequate statistical treatment or error analysis in the visible text. Third, the functional significance of the observed conformational differences is inferred rather than directly demonstrated. The study is potentially valuable but the case is not fully established from the provided evidence.
- **Who would be interested in the results, and why** Structural biologists studying nuclear receptor complexes, researchers in transcriptional regulation and allosteric signaling, and investigators interested in retinoid signaling pathways. The methodological approach combining SAXS, HDX-MS, and MD simulations for dynamic protein-DNA complexes will also interest biophysicists developing integrative structural biology workflows.
- **Major strengths** 1) The study addresses a significant gap in understanding how DNA response elements influence coregulator recruitment to nuclear receptor heterodimers. 2) The combination of multiple orthogonal techniques (SAXS, HDX-MS, MD, MST, fluorescence anisotropy) is methodologically rigorous in principle. 3) The inclusion of noncanonical response elements (DR0, IR0) alongside canonical ones (DR1, DR5) provides a useful comparative framework. 4) The identification of a potential role for the intermediate region (IR) of NCoR in heterodimer interactions is novel and testable.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (SAXS resolution and model validation circularity), R1-M2 (statistical treatment of quantitative data), R1-M3 (functional significance claims), R1-M4 (HDX-MS interpretation).
- **Assessment against Nature-style criteria** **Originality**: The work is original in its systematic comparison of four DNA response elements and its identification of the NCoR IR region as a potential interaction interface. However, the general concept of DNA allosteric effects on nuclear receptors is established. **Scientific importance**: The question is important, and the findings could have implications for understanding retinoid signaling specificity. However, the functional significance of the observed conformational differences is not directly demonstrated, limiting current impact. **Interdisciplinary readership**: The topic will interest structural biologists, biochemists, and transcriptional regulation researchers. The methodological integration is commendable. **Technical soundness**: The individual techniques are well-established, but concerns about SAXS resolution, statistical treatment, and potential circularity in model validation need addressing. **Readability for nonspecialists**: The manuscript is generally well-written and accessible, though some sections assume familiarity with nuclear receptor biology and biophysical methods.
- **Recommendation posture** Supportive if technical concerns are resolved. The study has potential but requires additional validation, clearer statistical presentation, and more direct functional evidence to fully establish the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Model validation
- **Claim pointer** The manuscript claims that "the heterodimer adopts distinct conformations depending on the DNA sequence, influencing interdomain distances and receptor interactions" based on SAXS and MD simulations.
- **Evidence pointer** Results section, Figure 1, Supplementary Table S2, Molecular dynamics simulation subsection in Materials and Methods
- **Concern** The SAXS data provide low-resolution structural information (Rg ~4.0 nm, Dmax ~13 nm), and the differences between DNA conditions appear modest based on the described parameters. The MD simulations are validated by fitting to the same SAXS data (via Bayesian reweighting), which creates a potential circularity: the simulations are adjusted to match the experimental data and then used to interpret those data. The manuscript does not clearly describe how independent validation was achieved. Additionally, the claim of "distinct conformations" requires quantitative comparison of the SAXS profiles (e.g., statistical tests on Rg or Dmax distributions) that is not presented in the visible text.
- **Why it matters** The central conclusion of DNA-dependent conformational differences rests on the ability to distinguish genuine structural variation from noise or fitting artifacts. Without independent validation and statistical comparison, the claim is not robustly supported.
- **Resolution test** Provide statistical comparison of SAXS-derived parameters across DNA conditions (e.g., error bars, significance tests). Describe how MD simulations were validated independently of the SAXS fitting (e.g., cross-validation, comparison to known structures, or replicate simulations with different initial conditions). If possible, include an independent experimental method (e.g., FRET, crosslinking) to corroborate the conformational differences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor / Reproducibility
- **Claim pointer** The manuscript reports binding affinities (Kd values) for NCoRNID and TIF-2NRID interactions with RAR/RXR-DNA complexes, and HDX-MS differences between conditions.
- **Evidence pointer** Results section, Table 1, Table 2, Supplementary Figures S2 and S7
- **Concern** The Kd values in Table 2 are presented with "confidence ranges" for MST data, but the number of replicates, the statistical test used to compare conditions, and the error propagation are not described in the visible text. For fluorescence anisotropy data, no error estimates are provided. The HDX-MS differences are described qualitatively (e.g., "strong protection," "diffuse and less intense protection") without quantitative thresholds or statistical significance testing. This makes it difficult to assess whether the reported differences between DNA conditions are robust.
- **Why it matters** The manuscript makes quantitative claims about differential affinities and protection levels across DNA conditions. Without proper statistical treatment, these claims cannot be evaluated, and the conclusions may not be reproducible.
- **Resolution test** Provide clear descriptions of replicate numbers, error calculations, and statistical tests for all quantitative measurements. For HDX-MS, include confidence intervals or significance thresholds for differential protection. Ensure all data underlying the reported Kd values and HDX differences are available.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional significance / Claim support
- **Claim pointer** The manuscript states that "DNA plays a role in stabilizing the TRR complex" and that "DR1 displayed the strongest protective effect on the corepressor and ligand interface," implying functional relevance of DNA sequence in coregulator recruitment.
- **Evidence pointer** Results section, Discussion section, Figures 3 and 4
- **Concern** The functional significance of the observed conformational and binding differences is inferred from structural and biophysical data but not directly tested. For example, the claim that DR1 stabilizes the repressive complex is based on HDX-MS protection patterns, but no functional assay (e.g., transcriptional reporter, chromatin immunoprecipitation, or in vitro transcription) is presented to link these structural observations to biological outcomes. The manuscript would be strengthened by demonstrating that the observed differences in coregulator affinity or stability translate to differences in transcriptional activity.
- **Why it matters** The broader significance of the study depends on the claim that DNA sequence modulates coregulator recruitment in a functionally meaningful way. Without functional validation, the physiological relevance of the structural findings remains speculative.
- **Resolution test** Include at least one functional assay (e.g., reporter gene assay, qPCR of endogenous target genes, or in vitro transcription) comparing the activity of RAR/RXR on the different response elements in the presence of coregulators. Alternatively, clearly frame the study as purely structural and temper the functional claims accordingly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation / Technical soundness
- **Claim pointer** The manuscript claims that "DNA binding likely caused a substantial destabilization to RXR LBD's H2-H3 loop and H11" and that this "reinforces RXR's subordinate role."
- **Evidence pointer** Results section, Figure 2K and 2L
- **Concern** The interpretation of HDX-MS deprotection as "destabilization" is reasonable but requires careful consideration of alternative explanations. Deprotection could also result from conformational changes that increase solvent accessibility without necessarily destabilizing the domain. Additionally, the claim that this "reinforces RXR's subordinate role" is an interpretive leap that goes beyond the data. The manuscript does not discuss potential caveats of HDX-MS interpretation, such as the possibility of local unfolding versus global destabilization, or the effects of the N-terminal truncation of the constructs used.
- **Why it matters** The interpretation of HDX-MS data underpins several key conclusions. Overinterpretation could mislead readers about the mechanistic implications of the findings.
- **Resolution test** Provide a more nuanced discussion of HDX-MS interpretation, acknowledging alternative explanations for deprotection. If possible, include complementary data (e.g., limited proteolysis, thermal stability assays) to support the destabilization interpretation. Temper the claim about RXR's "subordinate role" or provide additional evidence.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / Reproducibility
- **Affected element** Materials and Methods, DNA preparation section
- **Evidence pointer** "The forward and reverse oligonucleotides corresponding to the different RAREs motifs (DR0, DR0L, DR1, DR5, and IR0) were purchased from Integrated DNA Technologies (IDT) (Supplementary Table S1)."
- **Issue** The sequences of the oligonucleotides are only provided in the Supplementary Material, which was not available for review. Without these sequences, the reader cannot assess the design of the DNA constructs or the validity of the comparisons between different response elements.
- **Required correction** Include the oligonucleotide sequences in the main text or ensure they are clearly accessible in the Supplementary Material. Consider adding a brief description of the design rationale (e.g., flanking sequences, length) in the main text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity / Completeness
- **Affected element** Results section, SAXS analysis
- **Evidence pointer** "No deviations from linearity were observed in the Guinier region of all DNA conditions, indicating no sample aggregation or interparticle effects (Fig. 1A–D, inset)."
- **Issue** The manuscript does not report the quality metrics of the SAXS data (e.g., resolution range, I(0) values, excluded volume) or the goodness of fit for the P(r) functions. This limits the reader's ability to assess the reliability of the structural parameters.
- **Required correction** Provide standard SAXS quality metrics (e.g., Rg from Guinier and P(r), I(0), Dmax, quality estimates) in the main text or Supplementary Material. Consider including a table summarizing these parameters for all conditions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity / Interpretation
- **Affected element** Discussion section, paragraph on NCoRNID IR region
- **Evidence pointer** "This new interface of interaction appeared to have reduced local interaction time compared to CoRNR1 and CoRNR2 with the heterodimer"
- **Issue** The term "local interaction time" is not defined, and the basis for this claim (MD simulations? HDX-MS?) is not clearly stated. This makes the statement difficult to evaluate.
- **Required correction** Clarify the basis for this claim and define "local interaction time" (e.g., residence time from MD simulations, occupancy). Provide quantitative data or clearly label this as a qualitative observation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity / Reproducibility
- **Affected element** Materials and Methods, Molecular dynamics simulation section
- **Evidence pointer** "The structures of the DBDs complexed with DNA were obtained from PDB ID: 6XWG for DR5, SASBDB ID: SASDFT8 for DR0, and from the structure solved in this study for IR0."
- **Issue** The structure "solved in this study for IR0" is mentioned but not described in the main text. It is unclear whether this is a crystal structure, a model, or a cryo-EM structure. The methods for solving this structure are not provided.
- **Required correction** Provide details of the IR0 structure determination (method, resolution, refinement statistics) or clearly state that it is a model generated for this study. If it is a model, describe the modeling approach and its validation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity / Completeness
- **Affected element** Results section, HDX-MS analysis
- **Evidence pointer** "After obtaining a nearly complete sequence coverage of RAR and RXR (Supplementary Figs S5 and S6), we calculated the differences in HDX induced by the binding to the different DNA elements."
- **Issue** The manuscript does not report the sequence coverage percentages for RAR and RXR, nor the number of peptides used for the analysis. This information is critical for assessing the reliability of the HDX-MS data.
- **Required correction** Report sequence coverage and peptide counts in the main text or Supplementary Material. Consider including a summary table of HDX-MS statistics.

## Risk / unsupported claims
- The claim that "DR1 displayed the strongest protective effect on the coregulator and ligand interface" is based on HDX-MS data that are not fully presented with statistical analysis in the visible text. The claim is therefore not fully supported as presented.
- The statement that "DNA binding likely caused a substantial destabilization to RXR LBD's H2-H3 loop and H11" is an interpretation of HDX-MS deprotection that is plausible but not uniquely determined by the data. Alternative explanations (e.g., conformational change without destabilization) are not excluded.
- The claim that the NCoR IR region "mainly interacts with RXR" is based on MD simulations and HDX-MS data, but the functional significance of this interaction is not demonstrated. The claim that this interaction is "not responsive to the ligand or DNA" is based on negative results that are not statistically validated.
- The manuscript states that "the DNA provided an additional stabilization of RAR and a destabilization of RXR" in the agonist-bound complex. This is based on HDX-MS data, but the quantitative basis for this claim is not clearly presented.
- The functional significance of the observed DNA-dependent conformational differences for transcriptional regulation is inferred but not directly tested. The claim that these differences "could explain the repressiveness response of RAR/RXR complexes on DR1 elements" is speculative.