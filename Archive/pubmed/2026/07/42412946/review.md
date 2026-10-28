## Review setup
- **Input scope** Full manuscript text (Results, Discussion, Methods) and figure legends as provided
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical soundness based solely on the supplied text
- **Shared manuscript claim summary** The authors identify a ligandable pocket in the ERG PNT domain, develop a small-molecule probe (PBITE-1) that binds this pocket, and demonstrate that PBITE-1 suppresses ERG-dependent oncogenic phenotypes in cell lines, organoids, and in vivo xenograft models
- **Visible evidence base** Text descriptions of results, figure callouts (Figs. 1-7, SI Appendix Figs. S1-S7), methods summaries, and data availability statement
- **Missing materials affecting confidence** Actual figures and SI Appendix figures not provided; numerical data, statistical outputs, and raw sequencing analyses not accessible; compound synthesis details and characterization data not provided; NMR spectra and structural coordinates not available

## Reviewer
- **Overall assessment** This manuscript addresses a significant and long-standing challenge in prostate cancer therapeutics: the druggability of the ERG transcription factor. The authors provide a compelling narrative from target validation through chemical probe development to functional characterization. The central claim that the ERG PNT domain contains a ligandable pocket is supported by multiple orthogonal assays including DSF, biolayer interferometry, NMR, and cellular thermal shift assays. However, several technical concerns regarding binding affinity interpretation, selectivity assessment, and the mechanistic link between PNT binding and transcriptional inhibition require clarification. The in vivo data are promising but limited in scope, and the manuscript would benefit from additional validation of the proposed mechanism of action.

- **Who would be interested in the results, and why** Researchers in cancer biology, particularly those focused on prostate cancer and transcription factor targeting; medicinal chemists and chemical biologists interested in protein-protein interaction inhibitors and targeted protein degradation; clinicians and translational researchers working on castration-resistant prostate cancer; and the broader community investigating "undruggable" targets in oncology.

- **Major strengths** The study addresses a clinically relevant and previously intractable target with a clear unmet medical need. The authors employ a rigorous multi-assay approach to validate target engagement, including orthogonal biophysical and cellular methods. The use of an inactive analog (Y0747) as a negative control throughout the study strengthens the specificity claims. The demonstration of functional consequences across multiple model systems, including patient-derived organoids, adds translational relevance. The identification of a specific binding interface via NMR provides structural insight that will guide future medicinal chemistry efforts.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Binding affinity and specificity
- **Claim pointer** "PBITE-1 bound the PNT domain of ERG with an improved Kd = 264 ± 54 µM compared to F0341"
- **Evidence pointer** Results section "Biochemical and In Vitro Evaluation of Lead Compound PBITE-1", Fig. 3C
- **Concern** The reported Kd of 264 µM represents a very weak binding affinity. While the authors describe this as "improved" relative to the initial hit, this affinity is substantially weaker than typical drug-like binding interactions. The manuscript does not address whether such weak affinity is sufficient to explain the observed functional effects, particularly the selective inhibition of ERG-positive cells and the in vivo efficacy. The authors should discuss the relationship between this micromolar affinity and the observed cellular and in vivo activities, and provide evidence that the functional effects are specifically attributable to PNT binding rather than off-target effects.
- **Why it matters** The central claim of the manuscript is that ERG is "directly targetable" through the PNT domain. A Kd in the high micromolar range raises questions about whether the observed biological effects are truly mediated by PNT engagement or by non-specific mechanisms. This is critical for establishing the therapeutic potential of this approach.
- **Resolution test** Provide a quantitative correlation between PNT binding affinity and functional potency across a panel of analogs. Demonstrate that the cellular and in vivo effects of PBITE-1 are abolished in ERG constructs lacking the PNT domain or containing mutations in the identified binding pocket. Show that PBITE-1 does not affect ERG-negative cells at concentrations up to the maximum tested in vivo.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Selectivity
- **Claim pointer** "F0341 exhibited dose-dependent binding to the PNT domain with a calculated dissociation constant (Kd) of 392 ± 72 µM but showed no detectable binding to the ETS domain"
- **Evidence pointer** Results section "Identification of F0341, a Small-Molecule Binder of the ERG PNT Domain", Fig. 2C
- **Concern** The manuscript claims selectivity for the PNT domain over the ETS domain, but this is a limited selectivity assessment. The PNT domain is conserved among several ETS family members, and the authors acknowledge in the Discussion that binding "is selective to PNT domain-containing ETS family members, including ERG and FLI1." However, no data are presented on selectivity against other PNT domain-containing proteins, nor against a broader panel of unrelated proteins. The potential for off-target effects in cellular and in vivo experiments is not adequately addressed.
- **Why it matters** For a compound with micromolar affinity, selectivity is a major concern. Without a broader selectivity profile, it is difficult to attribute the observed biological effects specifically to ERG inhibition. This is particularly important given that the authors propose this as a foundation for therapeutic development.
- **Resolution test** Provide a selectivity panel including other PNT domain-containing ETS factors (e.g., FLI1, ETV6) and unrelated proteins. Assess PBITE-1 binding to a broad protein panel or use a proteomic approach to identify potential off-targets. Demonstrate that the functional effects of PBITE-1 correlate with ERG expression/activity across a wider panel of cell lines.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic link between PNT binding and functional inhibition
- **Claim pointer** "PBITE-1 significantly suppressed ERG target genes, including TDRD1, PLAT, and PLA1A, in ERG+ VCaP cells" and "PBITE-1 selectively suppressed ERG-dependent transcriptional programs"
- **Evidence pointer** Results section "PBITE-1 Inhibits ERG-Mediated Oncogenic Activities", Fig. 5D-F
- **Concern** The manuscript demonstrates that PBITE-1 suppresses ERG transcriptional activity, but the mechanism by which PNT domain binding leads to transcriptional inhibition is not established. The PNT domain is known to mediate protein-protein interactions, but the authors do not show whether PBITE-1 disrupts specific protein-protein interactions, alters ERG DNA binding, affects ERG subcellular localization, or induces conformational changes that impact transcriptional activity. The RNA-seq overlap with ERG knockdown is suggestive but does not establish the mechanism.
- **Why it matters** Understanding the mechanism of action is essential for rational optimization of the compound and for predicting potential resistance mechanisms. Without mechanistic insight, it is unclear whether the observed effects are due to direct inhibition of ERG function or indirect consequences of PNT binding.
- **Resolution test** Perform mechanistic studies including: (a) assessment of ERG DNA binding in the presence of PBITE-1 (e.g., ChIP-seq or electrophoretic mobility shift assays), (b) analysis of ERG subcellular localization, (c) identification of disrupted protein-protein interactions (e.g., co-immunoprecipitation of known PNT interaction partners), and (d) structural studies to understand the conformational consequences of PBITE-1 binding.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** In vivo efficacy and pharmacokinetics
- **Claim pointer** "PBITE-1 treatment resulted in a dose-dependent reduction in viability and organ growth in ERG+ human lines" and "PBITE-1 induces cellular apoptosis in the VCaP xenograft model in vivo"
- **Evidence pointer** Results sections "PBITE-1 Selectively Suppresses the Growth of ERG-Positive Prostate Organoids" and "PBITE-1 Induces Cellular Apoptosis in the VCaP Xenograft Model In Vivo", Figs. 6-7
- **Concern** The in vivo studies are limited to a short-term pharmacodynamic assessment (5 days of treatment) in a single xenograft model. No data are presented on tumor growth inhibition over extended treatment periods, compound pharmacokinetics, bioavailability, or toxicity. The doses used in vivo are not clearly specified in the provided text, and the relationship between the in vitro affinity (Kd = 264 µM) and achievable in vivo concentrations is not addressed.
- **Why it matters** For a manuscript claiming therapeutic potential, the in vivo data are critical. The current data demonstrate target engagement and apoptosis induction but do not establish therapeutic efficacy. Pharmacokinetic properties and toxicity profiles are essential for assessing the translational potential of this approach.
- **Resolution test** Provide extended efficacy studies with tumor growth curves over a longer treatment period. Include pharmacokinetic analysis of PBITE-1 in plasma and tumor tissue. Assess tolerability and toxicity at the doses used. If possible, include a second in vivo model to demonstrate generalizability.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Structural validation of binding site
- **Claim pointer** "These PBITE-1-responsive clusters form a continuous surface on the PNT 3D structure (PDB ID: 1SXE), suggesting the presence of a coherent binding pocket"
- **Evidence pointer** Results section "NMR and Molecule Docking Analyses Defines the PBITE-1 Binding Interface on the ERG PNT Domain", Fig. 4F-H
- **Concern** The binding interface is defined by NMR chemical shift perturbations and molecular docking, but no co-crystal structure or high-resolution structural validation is provided. The docking model is not described in sufficient detail to assess its reliability, and no experimental validation of the predicted binding mode (e.g., mutagenesis of predicted contact residues) is presented.
- **Why it matters** A high-confidence structural model of the binding interface is essential for structure-based drug design and for understanding the molecular basis of PNT domain ligandability. The current evidence, while suggestive, does not provide definitive structural proof.
- **Resolution test** Provide a co-crystal structure of PBITE-1 bound to the PNT domain, or alternatively, validate the docking model through systematic mutagenesis of predicted binding site residues and demonstrate loss of binding. Provide details of the docking methodology and scoring function used.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Fig. 1A
- **Evidence pointer** Results section "ERG Dependency in the VCaP Metastatic Prostate Cancer Cell Line"
- **Issue** The DepMap analysis is described as showing "strong negative dependency scores" for VCaP and a subset of hematologic cell lines, but the specific scores and the threshold used to define "strong" dependency are not provided.
- **Required correction** Provide the specific Chronos scores for the cell lines discussed and clearly state the threshold used to define dependency.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Multiple figures
- **Evidence pointer** Throughout Results
- **Issue** The manuscript states that "Statistical significance was determined with a P-value less than 0.05" but does not specify the statistical tests used for each comparison, the number of replicates, or whether multiple testing corrections were applied.
- **Required correction** Provide detailed statistical information in each figure legend, including the specific test used, sample sizes, and correction methods where applicable.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Compound characterization
- **Affected element** PBITE-1 and analogs
- **Evidence pointer** Methods section "Differential Scanning Fluorimetry" and Results section "SAR-Guided Optimization Yields PBITE-1"
- **Issue** The synthesis and chemical characterization of PBITE-1 and the more than 100 analogs are not described. Purity, solubility, and stability data are not provided.
- **Required correction** Include a chemistry methods section with synthetic schemes, compound characterization data (NMR, MS, HPLC purity), and physicochemical properties for key compounds.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Selectivity of transcriptional effects
- **Affected element** Fig. 5D-F
- **Evidence pointer** Results section "PBITE-1 Inhibits ERG-Mediated Oncogenic Activities"
- **Issue** The RNA-seq analysis shows overlap between PBITE-1 treatment and ERG knockdown, but the extent of this overlap and the specificity of the transcriptional changes are not quantified. It is unclear whether PBITE-1 affects a broader transcriptional program beyond ERG targets.
- **Required correction** Provide quantitative measures of the overlap (e.g., Jaccard index, enrichment statistics) and discuss the specificity of the transcriptional response.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The Discussion does not adequately address the limitations of the study, including the weak binding affinity, the lack of a co-crystal structure, and the limited in vivo efficacy data.
- **Required correction** Add a limitations paragraph that candidly discusses these issues and outlines future directions to address them.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** External validation
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The authors reference unpublished work by Parabilis Medicines as independent support for PNT domain druggability. This is not a citable source and does not provide verifiable evidence.
- **Required correction** Remove this reference or replace it with published, peer-reviewed work supporting PNT domain druggability.

## Risk / unsupported claims
- The claim that ERG is "directly targetable" is supported by binding data, but the weak affinity (Kd = 264 µM) and lack of structural validation make this claim premature
- The selectivity claim is limited to the ETS domain and does not address broader off-target potential
- The mechanistic link between PNT binding and transcriptional inhibition is not established
- The in vivo efficacy data are limited to short-term pharmacodynamic effects and do not demonstrate therapeutic efficacy
- The reference to Parabilis Medicines' unpublished work as independent validation is not verifiable
- The claim that PBITE-1 "selectively" inhibits ERG-positive cells is based on a limited panel of cell lines
- The relationship between the in vitro binding affinity and the concentrations used in cellular and in vivo experiments is not clearly established
- The docking model is not experimentally validated and should be treated as preliminary
- The claim that the PNT domain represents a "therapeutically relevant binding site" requires additional validation through optimized compounds with improved affinity and demonstrated in vivo efficacy