## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, conclusions) as provided by the user. No supplementary files, figures, or tables were accessible.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and internal consistency of the reported findings. No assessment of editorial fit or journal-specific policy compliance.
- **Shared manuscript claim summary** The authors report the identification and characterization of novel small-molecule inhibitors (MEISi-2E, MEISi-3, MEISi-4) targeting the MEIS2 homeobox domain, validated through in silico docking, a MEIS-luciferase reporter assay, RT-qPCR, viability assays in breast cancer cell lines, and flow cytometry for apoptosis/necrosis. They claim potent anti-cancer activity with minimal toxicity to normal fibroblasts and propose a mechanism involving disruption of a MEIS2 auto-regulatory loop and rebalancing of the MEIS-TGIF1 transcriptional network.
- **Visible evidence base** Text descriptions of results from molecular docking (Figure 1), luciferase reporter assays (Figure 2B), RT-qPCR (Figure 2C,D), viability/IC50 determinations (Figures 4A–E), flow cytometry (Figure 5A–D), baseline expression analysis (Figure 6C), and synthesis characterization (Figure S1A–C). Methods sections describe docking protocols, synthesis, cell culture, reporter assays, RT-qPCR, and flow cytometry.
- **Missing materials affecting confidence** All figures and tables (including Supplementary Tables S1 and S2) were not provided. Raw data, statistical outputs, gating strategies for flow cytometry, dose-response curves, and compound characterization spectra were not accessible. No information on replicate numbers or error bar definitions beyond "mean ± standard error" was available.

## Reviewer

- **Overall assessment** This manuscript presents a potentially interesting extension of prior work on MEIS homeodomain inhibitors, with the new compounds showing promising activity in breast cancer cell lines. However, the evidence as presented is insufficient to fully support the mechanistic claims, particularly regarding the proposed auto-regulatory loop and the selectivity of the compounds. Several technical details and data presentations are missing, and the discussion contains speculative interpretations that go beyond the data shown. The work may be of interest to the cancer biology and drug discovery communities, but substantial additional validation is required before the conclusions can be considered established.

- **Who would be interested in the results, and why** Researchers working on transcription factor targeting in cancer, particularly those focused on homeodomain proteins and the MEIS/PBX/TGIF family. The drug discovery community interested in fragment-based or small-molecule approaches to protein-DNA interaction interfaces would also find this relevant. Additionally, investigators studying transcriptional addiction in breast cancer subtypes, especially HER2-amplified or specific luminal subtypes, may be interested in the potential dependency on MEIS2.

- **Major strengths**
  1. The study addresses a challenging target class (transcription factor homeodomains) and provides a clear rationale for targeting MEIS2 in breast cancer.
  2. The inclusion of multiple validation layers (docking, reporter assay, gene expression, viability, apoptosis) is commendable.
  3. The synthesis and characterization of MEISi-2E is described in detail, with appropriate spectroscopic data.
  4. The observation of differential sensitivity across breast cancer cell lines and the correlation with MEIS expression levels is potentially valuable.
  5. The discussion of the MEIS-TGIF1 balance as a therapeutic axis is intellectually interesting and testable.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "These findings establish these small molecules as promising therapeutic candidates for targeting MEIS2-dependent pathways in breast cancer" and "MEISi-2E, MEISi-3, and MEISi-4 significantly suppress MEIS-driven luciferase activity"
- **Evidence pointer** Figure 2B, Section 2.3
- **Concern** The luciferase reporter assay is described as using a MEIS1 expression vector (pCMVSPORT6-Meis1) and a reporter containing the TGACAG motif. However, the manuscript claims these are MEIS2 inhibitors. The assay validates inhibition of MEIS1-driven transcription, not MEIS2. The authors state "MEISi-2E, MEISi-3, and MEISi-4 could be targeting MEIS2 proteins effectively along with MEIS1," but no direct MEIS2-specific reporter or biochemical assay is presented. The distinction between MEIS1 and MEIS2 inhibition is critical given the title and stated focus on MEIS2.
- **Why it matters** The central claim of the manuscript is MEIS2 inhibition. If the compounds only inhibit MEIS1, the title and conclusions are misleading. If they inhibit both, this needs to be demonstrated directly. The current evidence conflates MEIS1 and MEIS2 activity.
- **Resolution test** Provide a MEIS2-specific reporter assay (e.g., using a MEIS2 expression vector) or direct biochemical evidence of MEIS2 homeodomain binding (e.g., fluorescence polarization, ITC, or NMR with purified MEIS2 homeodomain). Alternatively, clearly reframe the claims to MEIS1/2 inhibition and adjust the title accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "MEISi-2E, MEISi-3, and MEISi-4 significantly suppress MEIS-driven luciferase activity and downregulate the expression of Meis1, Meis2, and downstream genes such as IL17RB, CDH1, EGR2, PAX6, and SERPINE1 while upregulating negative regulator TGIF1 and SOX3"
- **Evidence pointer** Figure 2C,D, Section 2.3
- **Concern** The RT-qPCR data are described only in text. No information is provided on the number of biological replicates, the specific cell line used for these experiments, the time point of treatment, or the concentrations tested. The qPCR array data (Figure 2D) is presented as a single panel without statistical analysis. The downregulation of CDH1 (E-cadherin) is interpreted in the discussion as consistent with TGIF-mediated repression, but the authors also note this could represent a "non-productive or terminal EMT-like response." The data as presented cannot distinguish between direct transcriptional effects of MEIS inhibition and secondary effects of cell death.
- **Why it matters** The gene expression data is a key pillar of the mechanistic claims. Without proper replication, statistical analysis, and clear experimental conditions, the findings cannot be evaluated. The interpretation of CDH1 downregulation is particularly problematic given the established role of E-cadherin loss in promoting metastasis, which contradicts the proposed therapeutic benefit.
- **Resolution test** Provide full experimental details (cell line, time point, concentration, replicates) and show statistical analysis for all gene expression data. Include a time-course experiment to distinguish direct transcriptional effects from cell death-associated changes. Address the CDH1 paradox explicitly with additional data (e.g., protein-level analysis, functional assays for migration/invasion).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Importantly, the novel inhibitors showed minimal toxicity to healthy human dermal and MRC5 fibroblasts, suggesting a favorable safety profile"
- **Evidence pointer** Figure 3A,B, Section 2.4
- **Concern** The safety assessment is limited to two fibroblast cell lines at a single time point (72 h). No dose-response data are shown for the toxicity assessment, and the concentrations tested are not specified in the text. The claim of a "favorable safety profile" is premature given that no other normal cell types (e.g., mammary epithelial cells, hepatocytes, cardiac cells) were tested, and no in vivo data are presented. The authors themselves acknowledge in the discussion that MEIS proteins are essential for hematopoiesis and cardiac function, yet no hematopoietic or cardiac cell toxicity data are shown.
- **Why it matters** The therapeutic index claim is central to the translational potential of these compounds. A favorable profile in two fibroblast lines does not establish safety, particularly for a target with known essential functions in other tissues. Overstating the safety profile could mislead readers about the clinical potential.
- **Resolution test** Expand toxicity testing to include additional normal cell types, particularly those known to depend on MEIS function (e.g., hematopoietic progenitors, cardiomyocytes). Show dose-response curves for toxicity. If in vivo data are not available, temper the safety claims accordingly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "Lead candidates MEISi-2E, MEISi-3, and MEISi-4 were identified with binding energies ranging from −3.0 to −3.90 kcal/mol"
- **Evidence pointer** Figure 1, Section 2.1, Section 4.1
- **Concern** The binding energies reported (−3.0 to −3.90 kcal/mol) are very weak for a drug-like inhibitor. Typical fragment binding is in the range of −5 to −8 kcal/mol, and validated inhibitors usually show stronger binding. The authors do not provide any experimental binding data (SPR, ITC, MST) to corroborate the docking predictions. The docking scores alone are insufficient to claim "inhibitors" without functional validation of direct binding.
- **Why it matters** The manuscript's premise is that these compounds target the MEIS2 homeodomain. If the binding affinity is as weak as the docking scores suggest, the observed cellular effects may be off-target. Direct binding evidence is essential to establish the mechanism of action.
- **Resolution test** Provide biophysical binding data (e.g., ITC, SPR, or MST) for at least the lead compound against the purified MEIS2 homeodomain. If binding is too weak to measure, acknowledge this limitation and discuss alternative mechanisms.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** "Mechanistic studies using flow cytometry revealed that these inhibitors induce dose-dependent apoptosis and necrosis"
- **Evidence pointer** Figure 5A–D, Section 2.6
- **Concern** The flow cytometry data are described only in text. No gating strategy, representative plots, or statistical analysis are shown in the text. The distinction between apoptosis and necrosis is based on Annexin V/PI staining, which has well-known limitations. The authors do not provide any orthogonal validation of apoptosis (e.g., caspase activation, PARP cleavage, TUNEL).
- **Why it matters** The mode of cell death is a key mechanistic claim. Without proper presentation of the flow cytometry data and orthogonal validation, the conclusion that these compounds induce apoptosis and necrosis is not fully supported.
- **Resolution test** Show representative flow cytometry plots with gating strategy, provide quantitative data with statistical analysis across replicates, and include orthogonal apoptosis assays (e.g., caspase-3/7 activity, western blot for cleaved PARP).

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1, compound classification
- **Evidence pointer** Section 2.1, Section 4.2
- **Issue** The manuscript states that MEISi-2E is a "newly synthesized" compound, while MEISi-3 and MEISi-4 are "newly validated." The distinction is unclear. Were MEISi-3 and MEISi-4 previously reported? If so, what is new about their validation here? If they are also new, why are they not described as synthesized?
- **Required correction** Clarify the synthesis and validation status of each compound. If MEISi-3 and MEISi-4 were previously described, provide appropriate citations and clearly state what new data are presented.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Section 2.2, E/Z isomerism
- **Evidence pointer** Section 2.2, Section 4.2
- **Issue** The text states that MEISi-2E is the "definitively characterized E-isomer" in Section 2.2, but the chemical name in Section 4.2 uses "(Z)-" notation. This is contradictory. The discussion also refers to "the stereoselective difference between the E-isomer (MEISi-2) and Z-isomer (MEISi-2E)," which contradicts the earlier assignment of MEISi-2E as the E-isomer.
- **Required correction** Resolve the E/Z assignment. Verify the correct stereochemistry and ensure consistency between the text, chemical name, and discussion.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 4.4, cell viability
- **Evidence pointer** Section 4.4
- **Issue** The WST1 assay description states that formazan crystals were dissolved in DMSO. WST1 assays typically do not require dissolution of formazan crystals, as the formazan produced by WST1 is water-soluble. This may be a methodological error or a conflation with the MTT assay.
- **Required correction** Verify the assay protocol. If WST1 was used, remove the DMSO dissolution step. If MTT was used, correct the assay name throughout.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Section 4.8, statistical analysis
- **Evidence pointer** Section 4.8
- **Issue** The statistical methods section only mentions Student's t-test. For dose-response curves and IC50 calculations, more appropriate methods (e.g., nonlinear regression) are typically used. The number of replicates and how error bars are defined are not stated.
- **Required correction** Provide a more detailed statistical analysis section, including the number of replicates, definition of error bars, and the specific tests used for each experiment.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 4.1, docking validation
- **Evidence pointer** Section 4.1
- **Issue** The docking protocol is stated to have been "previously validated through enrichment analysis," but no details of this validation are provided. The reader cannot assess the reliability of the docking results.
- **Required correction** Provide a brief description of the enrichment analysis or cite the original work with sufficient detail for the reader to evaluate the validation.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.5, IC50 values
- **Evidence pointer** Section 2.5
- **Issue** Two different IC50 values are reported for MEISi-3 in MCF7 cells: 1.27 μM from the imaging-based assay and 0.43 μM from the WST1 assay. The discrepancy is not discussed. Additionally, the text states MEISi-3 reduced viability "up to 75% as low as 0.35 μM," which is inconsistent with an IC50 of 0.43 μM (which would imply 50% inhibition at 0.43 μM).
- **Required correction** Explain the discrepancy between the two IC50 values. Clarify the relationship between the 0.35 μM concentration and the reported IC50 values.

## Risk / unsupported claims
1. The claim that these are "MEIS2 inhibitors" is not directly supported by the data, as the reporter assay uses MEIS1. No MEIS2-specific biochemical or cellular data are presented.
2. The claim of a "favorable safety profile" is unsupported beyond two fibroblast cell lines at unspecified concentrations.
3. The proposed "auto-regulatory loop" mechanism for MEIS2 downregulation is speculative and not directly tested.
4. The binding energies from docking are presented without experimental validation and are weak for a claimed inhibitor.
5. The claim that MEISi-2E is a "definitively characterized E-isomer" is contradicted by the (Z)-designation in the chemical name.
6. The statement that MEISi-3 reduced viability "up to 75% as low as 0.35 μM" is inconsistent with the reported IC50 of 0.43 μM.
7. The discussion of MEIS2 as a tumor suppressor in breast cancer versus the observed anti-cancer effects of inhibition is not fully reconciled, and the CDH1 downregulation finding is not adequately addressed.