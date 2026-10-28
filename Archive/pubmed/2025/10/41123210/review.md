## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results, discussion, data availability, and supplementary figure legends as referenced.
- **Assessment boundary** Scientific content, technical soundness, structural interpretation, and consistency of claims with the presented evidence. No assessment of editorial fit or publication decision.
- **Shared manuscript claim summary** The manuscript reports cryo-EM structures of H2AX- and γH2AX-containing mononucleosomes, revealing three stacked nucleosome architectures with parallel dyad axes. The authors propose that BRCT domain binding to γH2AX disrupts nucleosome stacking, potentially contributing to chromatin decondensation during DNA damage signaling.
- **Visible evidence base** Cryo-EM reconstructions and models (PDB 9MMK, 9MMT, 9MLN, 9MLR, 9MMM, 9MMN, 9MMO, 9MLL; EMD-48392, 48376, 48375, 48379, 48394, 48395, 48396, 48406, 48547), biochemical binding assays (FP, EMSA, MST), and geometric analysis of 666 NCP structures from the PDB.
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S19), supplementary movies (S1–S7), and detailed methods for the geometric analysis and MD simulations are referenced but not provided. This limits full verification of the stacking parameter analysis and simulation protocols.

## Reviewer
- **Overall assessment** This manuscript presents a substantial body of cryo-EM data on H2AX- and γH2AX-containing nucleosomes, including several novel stacked architectures. The observation that BRCT domain binding disrupts nucleosome stacking is potentially interesting, but the evidence for this claim is indirect, as no BRCT density was observed in the cryo-EM reconstructions. The geometric analysis of NCP stacking across the PDB is a useful contribution, though the presentation is dense and the novelty of the stacking modes relative to prior literature requires clearer articulation. The manuscript would benefit from a more critical discussion of the limitations of the in vitro system and the physiological relevance of the proposed decondensation model.
- **Who would be interested in the results, and why** Researchers in chromatin structure, DNA damage response, and histone post-translational modification biology. The cryo-EM structures of γH2AX nucleosomes and the analysis of stacking geometries will be of interest to structural biologists studying chromatin fiber organization. The proposed model linking BRCT binding to nucleosome unstacking may interest those studying the early events of DNA damage signaling.
- **Major strengths**
  1. The cryo-EM reconstructions of H2AX- and γH2AX-nucleosomes at 3.2–3.6 Å resolution provide useful structural data, including three distinct stacked states.
  2. The geometric analysis of 666 NCP structures from the PDB is a systematic and potentially valuable resource for understanding nucleosome stacking principles.
  3. The biochemical validation of BRCT binding specificity for γH2AX over unphosphorylated H2AX using multiple orthogonal methods (FP, EMSA, MST) is thorough.
  4. The one-step purification and one-pot NCL approach for producing γH2AX-containing octamers is a practical methodological advance.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence supports claim
- **Claim pointer** The abstract and discussion state that BRCT binding to γH2AX nucleosomes "disrupts stacking" and that this "could contribute to chromatin decondensation during DNA damage signaling."
- **Evidence pointer** Results section "BRCTs interact specifically with γH2Ax containing NCPs and disrupt NCP–NCP stacking"; Figure 5; Supplementary Fig. S5
- **Concern** The claim that BRCT binding disrupts nucleosome stacking is based solely on the observation that grids prepared with BRCTs showed no stacked particles, whereas grids without BRCTs did. However, no BRCT density was observed in any cryo-EM reconstruction, and the authors acknowledge that the BRCTs may be "flexible" and "dynamic." An alternative explanation is that the BRCTs simply did not bind stably to the nucleosomes under the cryo-EM conditions, and the absence of stacking reflects a different grid preparation artifact or a competitive interaction with the grid surface rather than a specific BRCT-induced unstacking. The claim of "disruption" implies a mechanistic effect that is not directly demonstrated.
- **Why it matters** The central mechanistic proposal of the paper, that BRCT recognition of γH2AX promotes chromatin decondensation by disrupting nucleosome stacking, rests on this observation. If the absence of stacking is due to non-specific effects, the proposed model is not supported.
- **Resolution test** Provide direct evidence of BRCT binding to γH2AX nucleosomes under cryo-EM conditions, for example by showing a reconstruction with BRCT density, or by demonstrating that BRCT addition specifically and reproducibly reduces stacking in a concentration-dependent manner while a control protein does not. Alternatively, use a biochemical assay (e.g., native gel or analytical ultracentrifugation) to show that BRCT binding alters the oligomeric state of γH2AX nucleosomes.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript states that "no clear densities for BRCT proteins were observed" in the complex samples, yet the samples were "crosslinked with 0.05% glutaraldehyde" to stabilize interactions.
- **Evidence pointer** Materials and methods, "Cryo-EM grid preparation and data processing"
- **Concern** The use of glutaraldehyde crosslinking is mentioned, but no details are provided on crosslinking conditions (time, temperature, quenching), nor is there any validation that crosslinking preserved BRCT-nucleosome interactions. If crosslinking was intended to stabilize a complex, the absence of BRCT density suggests either that the crosslinking was ineffective, that the interaction is too weak or transient, or that the BRCTs dissociated during grid preparation. The manuscript does not report any negative-stain or preliminary screening results that might have informed the decision to proceed with cryo-EM on these samples.
- **Why it matters** The interpretation of the "complex" samples as containing BRCT-bound nucleosomes is central to the claim of stacking disruption. Without evidence that the BRCTs were actually bound to the nucleosomes in the vitrified sample, the observed absence of stacking cannot be attributed to BRCT binding.
- **Resolution test** Provide details of the crosslinking protocol and include a control experiment showing that crosslinked BRCT-nucleosome complexes remain intact (e.g., by SDS-PAGE or mass spectrometry). Alternatively, perform the cryo-EM analysis without crosslinking and show that the same unstacking behavior is observed.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The geometric analysis of 666 NCP structures is used to conclude that "the mode of NCP-NCP stacking does not depend on the type of histone variant present, including H2AX or γH2AX."
- **Evidence pointer** Results section "Analysis of experimental structures reveal plasticity in NCP–NCP stacking"; Supplementary Tables S1 and S2
- **Concern** The methodology for the geometric analysis is described only briefly. The criteria for selecting the 30 distinct stacked structures from 666 entries are not fully detailed, and the parameters used to define the reference frame (shift, slide, rise, tilt, roll, twist) are described in a supplementary section that was not provided. Without a clear description of the selection criteria and the statistical treatment, it is difficult to assess whether the conclusion about histone variant independence is robust.
- **Why it matters** The claim that stacking modes are independent of histone variant is a general statement about chromatin biology. If the analysis is biased by the selection criteria or by the limited number of structures with H2AX or γH2AX, the conclusion may be overstated.
- **Resolution test** Provide the full methodology for the geometric analysis, including the selection criteria, the definition of the reference frame, and the statistical comparison between histone variant groups. If possible, include a table listing all 30 stacked structures with their relevant parameters.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Evidence supports claim
- **Claim pointer** The discussion states that "the distance between the centers of γH2AX-NCPs in a stacked conformation is ∼63 Å" and that "this 22-residue tail can extend up to ∼77 Å," leading to the conclusion that "the unstacking of NCPs is likely required for efficient BRCT domain binding."
- **Evidence pointer** Discussion section "DNA damage triggers chromatin relaxation"; Figure 3
- **Concern** The geometric argument assumes that the γH2AX C-terminal tail must be fully extended to reach the BRCT domain, and that the stacked conformation prevents this. However, the tail is disordered and could potentially sample extended conformations even in a stacked arrangement. The argument also assumes that the BRCT domain must bind to the tail in a specific orientation that is incompatible with stacking, which is not demonstrated. The MD simulations are referenced as supporting this, but the simulation details are not provided.
- **Why it matters** The proposed model of BRCT-induced unstacking relies on this geometric argument. If the tail can access the BRCT domain in the stacked state, the model loses its mechanistic basis.
- **Resolution test** Provide the MD simulation data showing that the γH2AX tail cannot access the BRCT domain in the stacked conformation. Alternatively, perform a binding assay with a pre-stacked nucleosome array to test whether BRCT domains can bind without prior unstacking.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Abstract and introduction
- **Evidence pointer** Abstract; Introduction, paragraph 1
- **Issue** The abstract states that γH2AX acts as a "master control switch," a phrase that is not defined or contextualized. The introduction would benefit from a brief explanation of why this term is used and what it implies mechanistically.
- **Required correction** Define the term "master control switch" in the introduction, or replace it with a more precise description of γH2AX's role in DNA damage signaling.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical clarity
- **Affected element** Materials and methods, "Fluorescence polarization"
- **Evidence pointer** Materials and methods, "Fluorescence polarization"
- **Issue** The fluorescence polarization assay is described briefly, but the peptide concentration (50 nM) and the protein concentration range are not stated. The KD values are mentioned in the results but not reported numerically in the text or a table.
- **Required correction** Report the KD values for both BRCT domains with the γH2AX peptide, and state the concentration range of the BRCT proteins used in the FP assay.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results, "BRCTs interact specifically with γH2Ax containing NCPs and disrupt NCP–NCP stacking"
- **Evidence pointer** Figure 4
- **Issue** The EMSA and MST data are presented in Figure 4, but the figure legend is not provided in the manuscript text. It is unclear what the labels and error bars represent.
- **Required correction** Ensure the figure legend clearly describes the experimental conditions, the concentrations used, and the number of replicates for each assay.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, "γH2AX can induce DNA destabilization without altering nucleosome core conformation"
- **Evidence pointer** Discussion, paragraph 2
- **Issue** The authors state that the observed DNA destabilization in γH2AX-NCP classes is "consistent with previous biochemical reports," but they do not discuss the possibility that the DNA destabilization may be an artifact of the cryo-EM grid preparation or the specific DNA sequence used (W601).
- **Required correction** Add a sentence acknowledging that the observed DNA flexibility may be influenced by the experimental conditions and that further validation with different DNA sequences or under different ionic conditions would strengthen the conclusion.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Data availability
- **Evidence pointer** Data availability section
- **Issue** The MD simulation protocols and the in-house algorithms for stacking analysis are stated to be "available from the corresponding authors upon reasonable request." This is acceptable but not ideal for reproducibility.
- **Required correction** Consider depositing the simulation input files and the analysis scripts in a public repository (e.g., Zenodo or GitHub) to facilitate reproducibility.

## Risk / unsupported claims
- The claim that BRCT binding "disrupts" nucleosome stacking is not directly supported by the cryo-EM data, as no BRCT density was observed. The absence of stacking in the presence of BRCTs could be due to non-specific effects.
- The geometric argument that the γH2AX tail cannot access the BRCT domain in a stacked conformation is plausible but not rigorously demonstrated without the MD simulation details.
- The conclusion that "the mode of NCP-NCP stacking does not depend on the type of histone variant present" is based on a PDB analysis whose methodology is not fully described in the provided materials.
- The statement that "BRCT recognition of γH2AX nucleosomes could contribute to chromatin decondensation during DNA damage signaling" is speculative and goes beyond the direct evidence presented.