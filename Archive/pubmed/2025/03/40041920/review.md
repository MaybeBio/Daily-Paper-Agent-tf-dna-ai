## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, conclusions, and figure legends.
- **Assessment boundary** Scientific validity, technical soundness, and support of claims based solely on the provided manuscript text. No external data, supplementary files, or raw datasets were available for review.
- **Shared manuscript claim summary** The authors report that the dimeric natural product panepocyclinol A (PecA) selectively inhibits STAT3 by forming a covalent homodimer through di-covalent modification of Cys712 and Cys718 residues on separate STAT3 monomers. This modification is claimed to reduce STAT3 DNA binding and transcriptional activity, with anti-tumor efficacy demonstrated in ALCL cell lines and xenograft models, including STAT3Y640F mutant contexts.
- **Visible evidence base** Cell viability screening, transcription factor activity profiling, fluorescence polarization binding assays, Western blot analysis of STAT3 dimerization, EMSA DNA binding assays, LC-MS/MS cross-linking identification, RNA-seq with GSEA, ChIP-seq, CRISPR-Cas9 knockout screening, MD simulations, KINOMEscan profiling, and in vivo xenograft studies.
- **Missing materials affecting confidence** Supplementary figures and tables (Fig. S1–S6, Tables S1–S3) are referenced but not provided. Raw LC-MS/MS spectra, MD simulation trajectories, RNA-seq and ChIP-seq datasets, and detailed statistical outputs are not available. The exact structure of PecA and its analogs is not shown in the text. No information on compound purity, solubility, or formulation is provided.

## Reviewer
- **Overall assessment** This manuscript presents a potentially interesting mechanism of action for a natural product dimer that covalently crosslinks STAT3 monomers, which is distinct from previously described STAT3 inhibitors. The combination of chemical biology, structural modeling, and in vivo efficacy data is commendable. However, several technical concerns, particularly regarding the direct evidence for di-covalent modification, the specificity of the proposed binding site, and the interpretation of MD simulation results, need to be addressed before the central claims are fully established.
- **Who would be interested in the results, and why** Researchers in the fields of cancer biology, STAT signaling, natural product drug discovery, and covalent drug development would find these results of interest. The proposed mechanism of di-covalent modification of a transcription factor dimer is conceptually novel and could inspire new approaches to targeting protein-protein interfaces.
- **Major strengths** The study identifies a new chemical scaffold for STAT3 inhibition with a unique proposed mechanism. The use of multiple orthogonal assays (cell-based, biochemical, biophysical, and in vivo) strengthens the overall conclusions. The inclusion of STAT3 mutant analysis and the demonstration of efficacy against clinically relevant STAT3Y640F mutations add translational relevance.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (direct evidence for di-covalent modification), R1-M2 (specificity of Cys712/Cys718), R1-M3 (MD simulation interpretation), R1-M4 (in vivo model relevance).
- **Assessment against Nature-style criteria**  
  *Originality*: The concept of using a dimeric natural product to covalently crosslink two monomers of a transcription factor is original and not previously described for STAT3. This represents a conceptual advance over conventional SH2 domain inhibitors.  
  *Scientific importance*: STAT3 is a high-value therapeutic target, and a new mechanism of inhibition with in vivo proof-of-concept could have significant impact. However, the clinical translatability of a covalent crosslinker with two reactive sites remains uncertain.  
  *Interdisciplinary readership*: The work bridges natural product chemistry, structural biology, computational modeling, and cancer pharmacology, which would appeal to a broad readership.  
  *Technical soundness*: The experimental design is generally sound, but the lack of direct structural evidence for the proposed di-covalent adduct and the reliance on a single computational method for mechanistic interpretation are weaknesses.  
  *Readability for nonspecialists*: The manuscript is clearly written and the logic is easy to follow, though some specialized terms (e.g., Michael acceptor, MM-PBSA) may require prior knowledge.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly those related to direct evidence for the di-covalent modification and the specificity of the proposed binding site.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for mechanism of action
- **Claim pointer** The authors claim that PecA crosslinks Cys712 and Cys718 residues in separate STAT3 monomers via two distinct Michael acceptors, forming a di-covalent adduct.
- **Evidence pointer** Results section "PecA crosslinks STAT3 monomers via Cys712 and Cys718 residues", Figure 3A, 3B
- **Concern** The identification of the crosslinked residues relies solely on LC-MS/MS analysis of a gel band, with only two potential crosslink spectra reported. No MS/MS spectra are shown, and the confidence of these assignments is not discussed. The authors also state that attempts to obtain a co-crystal structure failed, leaving the proposed binding mode without direct structural validation. The mutagenesis data (C712A/C718A) show loss of dimerization, but this does not prove that these cysteines are the sites of covalent modification, as the mutations could disrupt the binding pocket or protein folding.
- **Why it matters** The central claim of the manuscript is the di-covalent modification mechanism. Without robust evidence for the exact sites of modification and the stoichiometry of the adduct, the proposed mechanism remains speculative. This is critical for understanding the selectivity and potential off-target effects of PecA.
- **Resolution test** Provide annotated MS/MS spectra for the crosslinked peptides with clear assignment of fragment ions. Ideally, include a high-resolution mass spectrometry analysis of the intact protein-drug complex to confirm the mass shift corresponding to one PecA molecule per STAT3 dimer. Alternatively, a crystal structure or cryo-EM structure of the STAT3-PecA complex would be definitive.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Selectivity and specificity
- **Claim pointer** The authors claim that PecA is a selective STAT3 inhibitor, showing negligible interaction with STAT1.
- **Evidence pointer** Results section "Panepocyclinol A inhibits STAT3 signaling", Figure 1D, Figure S2B
- **Concern** Selectivity is demonstrated against STAT1 only. The STAT family has seven members, and the authors do not test PecA against STAT2, STAT4, STAT5A/B, or STAT6. Given the high sequence homology in the SH2 domain and the DNA binding domain across STAT family members, selectivity against only one family member is insufficient to support the claim of selective STAT3 inhibition. Furthermore, the KINOMEscan data (Table S3) is referenced but not shown, and it only covers kinases, not other potential off-targets.
- **Why it matters** Selectivity is a key claim for the potential therapeutic utility of PecA. If PecA also modifies other STAT family members or other cysteine-containing proteins, this would have significant implications for its efficacy and toxicity profile.
- **Resolution test** Perform a broader selectivity panel, including all STAT family members, and ideally a proteome-wide cysteine reactivity profiling (e.g., isoTOP-ABPP) to assess global selectivity. At minimum, test PecA against STAT2, STAT4, STAT5, and STAT6 in the same dimerization and transcriptional assays.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Computational modeling support
- **Claim pointer** The authors claim that MD simulation reveals key conformational changes in STAT3 dimers upon di-covalent binding with PecA that abolish DNA interactions.
- **Evidence pointer** Results section "Molecular dynamics simulation of STAT3 dimer", Figure 4
- **Concern** The MD simulation is based on a manually docked model of PecA, as the co-crystal structure was not obtained. The authors connect PecA to Cys712 only, while Cys718 is not included in the model due to being in a disordered region. The simulation therefore does not fully represent the proposed di-covalent modification. The MM-PBSA binding free energy calculation shows a difference of 10.8 kcal/mol between the two states, but this is a single method with known limitations, and no error estimates or replicate simulations are reported.
- **Why it matters** The MD simulation is used to provide a mechanistic explanation for how PecA inhibits STAT3 function. If the model is incomplete or the calculations are not robust, the proposed conformational mechanism is not well supported.
- **Resolution test** Provide additional validation of the MD results, such as replicate simulations with different initial velocities, error bars for the MM-PBSA calculations, and a discussion of the limitations of the model. If possible, include Cys718 in the model or use an alternative approach such as enhanced sampling or Markov state models to characterize the conformational landscape.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** In vivo model relevance
- **Claim pointer** The authors claim that PecA exhibits high efficacy against ALCL in vivo, particularly against STAT3Y640F.
- **Evidence pointer** Results section "PecA suppresses ALCL cells with STAT3 Y640F mutant in vitro and in vivo", Figure 6
- **Concern** The in vivo studies use xenograft models with cell lines engineered to overexpress STAT3 or STAT3Y640F. While this demonstrates proof-of-concept, it does not reflect the genetic heterogeneity of human ALCL, where STAT3 mutations are often accompanied by other genetic alterations such as NPM-ALK fusions. The dosing regimen, pharmacokinetics, and bioavailability of PecA are not described. The statement that PecA is "highly efficacious" is not supported by quantitative tumor growth inhibition data in the text.
- **Why it matters** The translational relevance of the findings depends on the robustness of the in vivo efficacy data and the relevance of the model system. Without pharmacokinetic data and a more clinically relevant model, the therapeutic potential of PecA remains uncertain.
- **Resolution test** Provide quantitative tumor growth inhibition data with statistical analysis, include a model with endogenous STAT3 mutations (e.g., patient-derived xenografts), and report basic pharmacokinetic parameters (e.g., plasma half-life, Cmax, bioavailability) for PecA.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1A
- **Evidence pointer** Results section "Panepocyclinol A inhibits STAT3 signaling", Figure 1A
- **Issue** The cell viability screen of 83 compounds is presented as a single panel, but the identity of the cell lines and the criteria for selecting PecA for further study are not described in the text.
- **Required correction** Clarify which cell lines were used in the primary screen, the concentration of compounds tested, and the statistical threshold used to identify PecA as a hit.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Experimental detail
- **Affected element** Western blot analysis
- **Evidence pointer** Results section "PecA selectively induces the formation of a STAT3 covalent homodimer", Figure 2A
- **Issue** The Western blot shows a ~200 kD band attributed to a STAT3 homodimer, but the authors do not specify whether the samples were run under non-reducing or reducing conditions, and whether the dimer band is resistant to SDS and reducing agents.
- **Required correction** Specify the exact sample preparation conditions (e.g., presence or absence of DTT or beta-mercaptoethanol) and include a control with a known reducible dimer to demonstrate the irreversibility of the crosslink.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Quantitative assays
- **Evidence pointer** Results sections, Figures 3C, 5A, 6A-F
- **Issue** The number of biological replicates and the statistical tests used for the quantitative assays (IC50 determinations, tumor growth curves, qPCR data) are not consistently reported in the text or figure legends.
- **Required correction** Clearly state the number of independent experiments, the error bar representation (SEM vs SD), and the specific statistical test used for each comparison.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Compound characterization
- **Affected element** PecA and analogs
- **Evidence pointer** Methods section "Reagents"
- **Issue** The purity and structural characterization of PecA and its analogs are not described. The manuscript states they were isolated from a fungal source, but no NMR, HRMS, or HPLC purity data are provided.
- **Required correction** Include a description of the purity (e.g., HPLC trace) and structural confirmation (e.g., NMR, HRMS) for PecA and all analogs used in the study.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of STAT3 inhibitors is brief and does not fully contextualize the novelty of PecA's mechanism compared to recent covalent STAT3 inhibitors or PROTACs.
- **Required correction** Expand the discussion to include recent developments in covalent STAT3 inhibition and explain how the di-covalent mechanism of PecA differs from and potentially improves upon these approaches.

## Risk / unsupported claims
- The claim that PecA forms a di-covalent adduct with Cys712 and Cys718 is not fully supported by the provided evidence; only two crosslink spectra are mentioned, and no spectra are shown.
- The claim of selectivity for STAT3 over other STAT family members is unsupported, as only STAT1 was tested.
- The MD simulation results are based on an incomplete model (Cys718 not included) and a single computational method, making the proposed conformational mechanism not fully established.
- The statement that PecA is "highly efficacious" in vivo is not quantitatively supported in the text.
- The claim that PecA can "override" the effects of STAT3Y640F mutations is based on cell line models and requires validation in more clinically relevant systems.