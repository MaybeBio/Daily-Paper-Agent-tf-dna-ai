## Review setup
- **Input scope** Full manuscript text (abstract, introduction, experimental, results and discussion, conclusion) as provided
- **Assessment boundary** Scientific content, technical soundness, and internal consistency of the provided manuscript material only; no external literature verification or supplementary information review
- **Shared manuscript claim summary** The authors report the synthesis, structural characterization, antimicrobial evaluation, and preliminary mechanistic studies of six Ru(II) pyrazolyl–pyridine half-sandwich complexes (C1–C6). They claim selective activity of C6 against Acinetobacter baumannii (MIC 16 µg/mL), with supporting biophysical evidence for DNA minor groove binding and histidine coordination as potential mechanisms of action.
- **Visible evidence base** Abstract, Introduction, Experimental (Materials, X-Ray Crystal Structure Determination, Biological Evaluation, Biophysical Chemistry subsections), Results and Discussion (Synthesis and Characterization, Antimicrobial Evaluation, Cytotoxicity, Evaluation of Antimicrobial Activity, Stability of Complex C6, Mechanistic Studies, DNA Binding Studies, C6 Interaction with Amino Acids), Conclusion, Funding, Conflicts of Interest, Data Availability Statement, Acknowledgments
- **Missing materials affecting confidence** Supplementary information (ESI) referenced for synthetic methods, full biological assay protocols, crystallographic tables (Table S1), and additional figures (Fig. S1–S3); Table 1, Table 2, Table 3, Table 4, Scheme 1, Scheme 2, Figure 1, Figure 2, Figure 3, Figure 4, Figure 5 are referenced but not visible in the provided material; full crystallographic data (CIF files) not available

## Reviewer

- **Overall assessment** This manuscript presents a straightforward extension of previously reported Ru(II) pyrazolyl–pyridine complexes into antimicrobial screening, with one compound (C6) showing modest activity against A. baumannii. The synthetic work appears sound but is largely recycled from the authors' prior publication. The antimicrobial data are limited to a single active compound with MIC values that are modest compared to established antibiotics. The mechanistic studies are preliminary and suffer from a critical error in the reported Stern-Volmer constant, which undermines confidence in the quantitative biophysical analysis. The manuscript reads more like a progress report than a complete study establishing a new class of antimicrobial agents.

- **Who would be interested in the results, and why** Researchers in the field of metalloantibiotics and inorganic medicinal chemistry may find interest in the expansion of Ru(II) arene complexes into Gram-negative pathogens, particularly A. baumannii. The structure-activity relationship discussion regarding counterion effects and lipophilicity could be useful for those designing related complexes. However, the broader antimicrobial community is unlikely to be strongly engaged given the modest activity and preliminary mechanistic depth.

- **Major strengths**
  1. The manuscript addresses a clinically relevant pathogen (A. baumannii) for which new antimicrobial scaffolds are genuinely needed.
  2. The combination of experimental biophysical methods (fluorescence, LD) with computational approaches (docking, MD) provides a multi-pronged preliminary mechanistic picture.
  3. The authors appropriately acknowledge limitations of docking studies and in vitro assays in their interpretation.
  4. The stability/pH speciation study for C6 is a thoughtful addition that many similar studies omit.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors report a Stern-Volmer constant of KSV = 1.067 ± 0.03 × 10–3 M–1 for C6 quenching of ctDNA-bound ethidium bromide.
- **Evidence pointer** Section "DNA Binding Studies", Figure 4b, Equation (2)
- **Concern** The reported KSV value of 1.067 × 10–3 M–1 is physically implausible for a quenching experiment. The Stern-Volmer constant is typically on the order of 10^3–10^5 M–1 for effective quenchers. A value of 10^–3 M–1 implies essentially no quenching, yet the authors describe "concentration-dependent quenching" and use this data to support DNA binding. The units appear to be misreported, or the calculation is erroneous. The authors themselves note the value is "orders of magnitude lower" than literature comparisons, which should have triggered a re-examination of the calculation.
- **Why it matters** The quantitative biophysical analysis is central to the mechanistic claim of DNA interaction. An erroneous KSV value undermines the credibility of the entire DNA binding section and the derived conclusions about binding affinity and mode.
- **Resolution test** Recalculate KSV from the raw fluorescence data. Verify the slope of the Stern-Volmer plot. Report the value with correct units and compare appropriately to literature. If the quenching is genuinely weak, state this clearly and discuss what it means for the biological relevance of DNA binding.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that C6 "interacts with DNA via partial intercalation and groove contacts" and that this may contribute to its antibacterial activity.
- **Evidence pointer** Section "Mechanistic Studies", "DNA Binding Studies", Figure 3, Figure 4
- **Concern** The evidence for the DNA binding mode is weak and partially contradictory. The LD data show only a "minimal" decrease in the DNA signal at 260 nm, which the authors interpret as minor groove binding. However, the docking study shows a preference for the intercalator-bound DNA structure (4E1U) over the groove-binding structure (425D). The MD simulation describes reorientation from intercalation to minor groove binding. These three lines of evidence do not converge on a consistent binding mode. Furthermore, the fluorescence quenching data, if the KSV is corrected, may not support significant binding at all. The authors do not provide a clear, coherent model of how C6 interacts with DNA.
- **Why it matters** The DNA interaction is presented as a potential mechanism of action. If the binding mode is unclear or the binding is weak, the mechanistic claim is not established. The manuscript needs a coherent, evidence-based model or a clear statement of uncertainty.
- **Resolution test** Reconcile the docking, MD, LD, and fluorescence data into a single coherent binding model. If the data are insufficient to distinguish between intercalation and groove binding, state this explicitly and design experiments that can differentiate (e.g., viscosity measurements, DNA melting studies, competition assays with known groove binders vs. intercalators).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Internal consistency
- **Claim pointer** The antimicrobial activity of C6 is reported as MIC 16 µg/mL against A. baumannii in the Abstract, Results, and Conclusion, but the same compound is reported with MIC 32 µg/mL against A. baumannii in the Cytotoxicity section context.
- **Evidence pointer** Abstract; Section "Antimicrobial Evaluation"; Section "Cytotoxicity (CC50), Hemolytic Activity (HC50), and Cytopathic Effects"; Conclusion
- **Concern** The manuscript contains an internal inconsistency in the reported MIC value for C6 against A. baumannii. The Abstract, Results, and Conclusion state 16 µg/mL, while the Cytotoxicity section states 32 µg/mL. This discrepancy is not explained. It is unclear if these are different strains, different assay conditions, or an error.
- **Why it matters** The MIC value is the central quantitative claim of antimicrobial activity. An unresolved inconsistency in this value across sections of the manuscript is a serious reporting error that must be corrected.
- **Resolution test** Verify the correct MIC value from the primary assay data. Ensure all sections of the manuscript report the same value, or clearly distinguish if different strains or conditions were used.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state that "C1–C3 were inactive against the majority of the pathogens studied, with MICs over 32 μg mL−1" and that C4 and C5 were not carried forward due to lack of activity, leaving C6 as the sole active compound.
- **Evidence pointer** Section "Antimicrobial Evaluation", Table 2
- **Concern** The study reports only one active compound out of six, with modest activity (16 µg/mL against A. baumannii). The structure-activity relationship discussion is largely speculative, based on a single active compound. The claim that this represents a "new metallic line of defense" is overstated given the preliminary nature of the data and the lack of a clear SAR trend.
- **Why it matters** The significance of the study rests on the potential of this compound class. With only one active compound and no clear SAR, the generalizability of the findings is limited. The title and framing overstate the significance relative to the data.
- **Resolution test** Either provide additional active analogs to establish a SAR trend, or temper the claims in the title and abstract to reflect the preliminary nature of the findings.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "selective efficacy of complexes C1–C3 against Acinetobacter baumannii," but the Results section states C1–C3 were inactive (MIC > 32 µg/mL) and only C6 was active. This is a direct contradiction.
- **Required correction** Correct the abstract to state that C6 was the active compound against A. baumannii, not C1–C3.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Equation (2) and associated text
- **Evidence pointer** Section "DNA Binding Studies", Equation (2)
- **Concern** The Stern-Volmer equation is written as I0/I = 1 + KSV[Q] = 1 + kqτ0[Q]. The bimolecular quenching constant kq is then reported as 4.63 × 10^4 M–1 s–1. However, if KSV = 1.067 × 10^–3 M–1 and τ0 = 23 ns, then kq = KSV/τ0 = 4.64 × 10^4 M–1 s–1, which is consistent. The issue is the magnitude of KSV itself, which is implausibly low.
- **Required correction** Re-examine the KSV calculation. If the value is correct, discuss the implications of such weak quenching. If incorrect, recalculate and report the correct value.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Antimicrobial evaluation
- **Evidence pointer** Section "Antimicrobial Evaluation", Table 2
- **Issue** The manuscript reports MIC values but does not provide minimum bactericidal concentration (MBC) data or time-kill kinetics. For a compound proposed as an antimicrobial, these are standard and informative assays.
- **Required correction** Add MBC data or time-kill curves for C6 against A. baumannii to strengthen the antimicrobial claim.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 2
- **Evidence pointer** Section "Stability of Complex C6", Figure 2
- **Issue** The pH speciation study reports two pKa values (5.55 and 10.60), but the chemical interpretation of these values is not discussed. What protonation/deprotonation events do these correspond to? The proposed scheme in Figure 2c is not described in sufficient detail.
- **Required correction** Provide a clear chemical interpretation of the pKa values and a more detailed description of the proposed speciation scheme.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Docking studies
- **Evidence pointer** Section "Mechanistic Studies", Table 3, Table 4
- **Issue** The docking scores are described as "low overall" and "modest," yet the authors use them to support biological relevance. The manuscript does not provide a comparison with a known DNA intercalator or groove binder as a positive control for the docking methodology.
- **Required correction** Include docking of a known DNA-binding agent (e.g., ethidium bromide, Hoechst 33258) as a positive control to calibrate the scoring function and provide context for the C6 scores.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section "Evaluation of Antimicrobial Activity"
- **Evidence pointer** Section "Evaluation of Antimicrobial Activity"
- **Issue** This section contains extensive discussion of literature comparisons and future optimization strategies that would be better placed in a dedicated discussion section. The current structure mixes results interpretation with broad speculation.
- **Required correction** Restructure to separate results interpretation from speculative discussion of future directions.

## Risk / unsupported claims
- The claim that C6 acts via "partial intercalation and groove contacts" is not fully supported by the presented data, which show weak quenching, minimal LD changes, and contradictory docking/MD results.
- The claim that histidine coordination is a potential mechanism of action is based solely on NMR peak appearance and docking scores; no functional assays (e.g., enzyme inhibition) are provided.
- The statement that "C1–C3 were inactive" is contradicted by the abstract's claim of "selective efficacy of complexes C1–C3 against A. baumannii."
- The reported KSV value of 1.067 × 10^–3 M–1 is physically implausible and likely erroneous.
- The claim that the compounds represent "a new metallic line of defense" is overstated given that only one of six compounds showed activity, and the activity was modest.
- The stability of C6 under biological assay conditions is inferred from pH speciation studies in buffer, but the manuscript does not report the actual speciation under MIC assay conditions (e.g., in Mueller-Hinton broth).
- The conclusion that "the antibacterial activity of C6 may arise from multiple interacting mechanisms" is speculative and not directly tested.