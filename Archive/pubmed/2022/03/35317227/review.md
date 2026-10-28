## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, conclusions, methods, and figure legends. Supplementary material referenced but not provided.
- **Assessment boundary** Scientific soundness, technical rigor, clarity of claims, and alignment of evidence with conclusions. No assessment of editorial fit or publication priority beyond stated criteria.
- **Shared manuscript claim summary** The authors propose that phosphorylation of Ser282 and Ser285 in the intrinsically disordered SRR of Ets-1 inhibits DNA binding via two mechanisms: a steric block of the DNA-binding interface (electrostatic interactions between phosphoserines and positively charged residues on helix H3) and an allosteric pathway (hydrophobic/aromatic interactions between pSRR and the inhibitory module that destabilize the core domain, particularly helix H3). They support this with enhanced-sampling simulations (PTMetaD-WTE and BE-MetaD) and EMSA experiments on designed mutants.
- **Visible evidence base** Main-text figures 1–8, supplementary figures S1–S12 (referenced but not provided), methods section, and EMSA/CD experimental data.
- **Missing materials affecting confidence** Supplementary figures S1–S12, including convergence tests (S12), chemical shift validation (S2), contact maps (S4), helicity data (S5), DCC matrices (S6), EMSA full titrations (S7), CD spectra (S8), and additional FEL data (S9–S11). Without these, several quantitative claims cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript addresses a mechanistically important question: how phosphorylation of an IDR (SRR) auto-inhibits the DNA-binding activity of Ets-1. The combination of enhanced-sampling simulations with targeted mutagenesis and EMSA is appropriate and potentially powerful. The central claim that both steric and allosteric mechanisms operate is plausible and partially supported by the presented data. However, the evidence as presented has significant gaps. The simulation methodology is described but key validation and convergence data are relegated to supplementary material that was not available for review. The EMSA results, while qualitatively consistent with the hypothesis, are presented in a way that makes quantitative assessment difficult. The distinction between the two proposed mechanisms is not rigorously established; the simulations show correlated structural changes, but causal linkage is inferred rather than demonstrated. The manuscript would be strengthened by clearer presentation of the free energy landscapes, quantitative population analyses, and a more direct test of the allosteric pathway.
- **Who would be interested in the results, and why** Researchers studying transcription factor regulation, particularly the Ets family; investigators interested in IDP/IDR function and phosphorylation-dependent regulation; computational biologists using enhanced-sampling methods to study protein-DNA interactions; and those developing inhibitors targeting protein-DNA interfaces. The proposed dual mechanism (steric plus allosteric) has general implications for how phosphorylation of disordered regions can regulate folded domains.
- **Major strengths**
  1. The study combines advanced simulation techniques (PTMetaD-WTE, BE-MetaD) with experimental validation (EMSA, CD), which is a strong and increasingly important approach.
  2. The focus on both steric and allosteric mechanisms is more nuanced than prior models and may reconcile conflicting literature.
  3. The identification of specific hydrophobic/aromatic residue clusters (e.g., Y283, F286, Y291) provides testable hypotheses.
  4. The use of phosphomimetic mutants (S282D/S285D) to compare with true phosphorylation is a thoughtful control.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "both of the steric hindrance and allosteric regulation are observed" and that the allosteric mechanism involves disruption of the hydrophobic core of Ets-1, leading to H3 unfolding.
- **Evidence pointer** Figures 3–5; supplementary figures S4, S5, S9–S11 (not provided)
- **Concern** The free energy landscapes (Fig. 3A) show two minima, but the population of state b (the allosteric state) is not quantified in the main text. The claim that state b represents a significant functional state requires a quantitative population estimate. Furthermore, the causal chain from pSRR binding to the IM interface to H3 unfolding is inferred from correlated contact changes (Fig. 5B) but not demonstrated. The authors do not show that disrupting the pSRR-IM interaction specifically abolishes the allosteric effect while preserving the steric effect.
- **Why it matters** Without quantitative populations and a causal test, the relative contribution of the two mechanisms cannot be assessed. The manuscript's central thesis is that both mechanisms operate, but the evidence as presented does not establish this beyond correlation.
- **Resolution test** Provide the population of each state from the reweighted FELs. Perform a simulation or experiment where the pSRR-IM interface is specifically disrupted (e.g., mutation of W338 or Y283) and show that H3 stability is restored while the steric block is retained. Alternatively, show that the allosteric effect scales with the strength of the pSRR-IM interaction.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validation
- **Claim pointer** The authors state that the simulated ensembles of free SRR and pSRR are validated by comparison with experimental chemical shifts, with RMSE values "close to the system errors of the chemical shift calculating tool."
- **Evidence pointer** Figure S2 (not provided); Methods section
- **Concern** The RMSE values (0.67 ppm for N, 0.12 ppm for HN) are presented as validation, but the comparison is only shown in supplementary Figure S2, which was not available. More critically, the authors do not report the uncertainty in these RMSE values or compare them against a null model (e.g., a random coil ensemble). The claim that the ensembles "accurately describe the conformational space" is stronger than what RMSE values alone can support, especially for an IDP where chemical shift prediction tools have known limitations.
- **Why it matters** The entire simulation study rests on the quality of the sampled ensembles. If the ensembles are not representative, all downstream conclusions about binding mechanisms are compromised.
- **Resolution test** Provide the full chemical shift comparison in the main text or as a clearly accessible supplement. Include a comparison with a null model (e.g., an ensemble generated without phosphorylation) and report the statistical significance of the agreement. If possible, validate against additional experimental observables (e.g., SAXS, FRET).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Experimental rigor
- **Claim pointer** The EMSA experiments show that "all the mutants (MT1 to MT4) hardly bind with DNA even if the concentration of protein increase to 1.6 μM," and this is interpreted as evidence for the importance of the hydrophobic network.
- **Evidence pointer** Figure 8; Figure S7 (not provided)
- **Concern** The EMSA data are presented as a single gel image (Fig. 8) with no quantification. The claim that mutants "hardly bind" is qualitative. The mutations (L337A, W338A, L393A, Y396A) are in the core domain, not in the SRR, and could affect DNA binding directly by altering the structure of the DNA-binding interface, rather than by disrupting the allosteric pathway. The CD spectra (Fig. S8) show no overall structural change, but this does not rule out local perturbations at the binding interface.
- **Why it matters** The EMSA data are the primary experimental support for the allosteric mechanism. If the mutations simply destabilize the DNA-binding interface directly, the data do not support the proposed allosteric pathway.
- **Resolution test** Provide quantitative EMSA binding curves with error bars. Include a control mutation in the SRR that disrupts the pSRR-IM interaction but is not in the core domain. Show that the core-domain mutations do not alter the structure of the DNA-binding interface (e.g., by NMR or X-ray).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic distinction
- **Claim pointer** The authors propose that the steric mechanism involves "electrostatic interactions between the negative charged phosphorate group on pSRR and positive charged residues K383, R391 and K399 on the H3."
- **Evidence pointer** Figure 4; Figure S11 (not provided)
- **Concern** The hydrogen bond occupancies (86%, 76%, 91%) are reported for specific residue pairs, but it is unclear how these were calculated and whether they are statistically converged. The authors do not report the corresponding occupancies in the unphosphorylated system, so it is unclear whether these interactions are specific to phosphorylation. Additionally, the distinction between the steric and allosteric mechanisms is not clear-cut: the same residue pairs (e.g., pSer282-K388) could contribute to both mechanisms if the binding induces conformational changes.
- **Why it matters** The manuscript's main contribution is the dual-mechanism model. If the two mechanisms are not cleanly separable, the model is less useful.
- **Resolution test** Report occupancies for the unphosphorylated system as a control. Perform a simulation where the electrostatic interactions are screened (e.g., by increasing salt concentration) and show that the steric block is reduced while the allosteric effect remains.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 3A
- **Evidence pointer** Figure 3A
- **Issue** The free energy landscape axes are not clearly labeled in the figure legend. The x-axis is described as "interactions between pSRR and IM interface" and the y-axis as "contact numbers of hydrophobic residues within the Ets-1 core domain," but the units and ranges are not specified.
- **Required correction** Provide clear axis labels with units and ranges in the figure and legend.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Simulation protocols"
- **Evidence pointer** Methods section
- **Issue** The methods state that the SRR sequence is "RVPSYDSFDYEDYPAALPNHKP," but the numbering of residues (e.g., Ser282, Ser285) is not mapped to this sequence. It is unclear which residues correspond to the phosphorylation sites.
- **Required correction** Provide a sequence alignment or numbering scheme that maps the SRR sequence to the full-length Ets-1 numbering.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 8
- **Evidence pointer** Figure 8
- **Issue** The EMSA data are shown as a single representative gel. No replicates or error bars are shown.
- **Required correction** State the number of independent replicates and provide quantification with error bars.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Discussion, "The autoinhibition mechanism of phosphorylation"
- **Evidence pointer** Discussion section
- **Issue** The term "caution-π interactions" appears in the Results section. This is likely a typo for "cation-π interactions."
- **Required correction** Correct the typo.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, "Protein expression and purification"
- **Evidence pointer** Methods section
- **Issue** The methods describe purification of the ΔN301 protein but do not specify how the protein concentration was determined or the purity assessed.
- **Required correction** Add details on protein quantification and purity assessment.

## Risk / unsupported claims
- The claim that "more than 80% structures obey the steric mechanism" is not supported by any quantitative data presented in the main text. The percentage is mentioned in the Discussion but no calculation or figure is referenced.
- The claim that the phosphomimetic mutations (S282D/S285D) "have similar properties with the FES of WT-SRR binding" is based on Figure S9, which was not provided. This comparison is essential for understanding why phosphomimetics are weaker inhibitors than true phosphorylation.
- The statement that "the phosphorylation would increase the hydrophobic residue clusters" is supported by Figure 2B, but the quantitative difference between SRR and pSRR is not reported.
- The claim that "the dynamic correlation coefficient (DCC) matrix... are consistent with the experiment observations" is based on a qualitative comparison. No quantitative metric of agreement is provided.
- The conclusion that "our work revealed the regulation mechanism of phosphorylation on the structures and function of IDR" is broader than what the data support, as the study is limited to one IDR (SRR) in one protein (Ets-1).