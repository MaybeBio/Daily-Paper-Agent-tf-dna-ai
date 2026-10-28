## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results and discussion, conclusions, methods) as provided
- **Assessment boundary** Scientific content, technical soundness, structural and biophysical data interpretation, and support of claims by the presented evidence
- **Shared manuscript claim summary** The authors report the first crystal structure of the TetR family regulator CecR from Escherichia coli at 1.91 Å resolution, classify it as belonging to TetR subfamily D, describe a tunnel-like ligand-binding cavity containing PEG fragments, measure binding affinities to cefepime, cefoxitin, and chloramphenicol via spectral shift, perform molecular docking to predict ligand interactions, and validate key residues (Q126, F74) through site-directed mutagenesis
- **Visible evidence base** Crystal structure (PDB 9I1X), spectral shift binding data (Table 1, Fig. 3), molecular docking results, sequence conservation analyses (MAST, ConSurf, WebLogo), structural comparisons (PDBeFold), phylogenetic distribution analysis
- **Missing materials affecting confidence** Electron density maps (other than described omit map), full refinement statistics beyond Table 3 (not shown in provided text), raw spectral shift curves, docking scoring details, validation metrics for docking, sequence alignment data, coordinates of docked poses, experimental replicates for mutagenesis binding assays

## Reviewer

- **Overall assessment** This manuscript presents the first crystal structure of CecR, a TetR family regulator implicated in antibiotic sensing and efflux pump regulation in Enterobacteriales. The structural work appears technically sound, and the classification of CecR into subfamily D is well supported by both sequence and structural analyses. However, the functional conclusions regarding ligand recognition are weakened by the absence of a ligand-bound structure, the inability to achieve saturation in binding assays for two of the three ligands, and the reliance on docking without experimental validation of the predicted binding mode. The physiological relevance of the measured affinities, particularly for chloramphenicol (Kd > 50 mM), is not convincingly established. The manuscript would benefit from additional experimental evidence, such as a ligand-bound structure, mutagenesis of additional predicted residues, or cellular assays linking binding affinity to regulatory function.

- **Who would be interested in the results, and why** Researchers studying TetR family regulators, transcriptional regulation of antibiotic resistance, and structural biology of bacterial transcription factors. The work is also relevant to those investigating the molecular basis of antibiotic sensing in Gram-negative pathogens, particularly within the Enterobacteriales order. The structural characterization of a previously poorly understood regulator fills a gap in the TFR structural landscape and may inform studies on related regulators in pathogenic species.

- **Major strengths** The first crystal structure of CecR is a valuable contribution. The classification into subfamily D is supported by multiple independent analyses (MAST motifs, structural comparison with PhlH and RutR). The description of the tunnel-like ligand-binding cavity and the comparison with PhlH provides useful structural context. The combination of structural, biophysical, and computational approaches is commendable. The identification of conserved ligand-binding residues through sequence analysis across homologs adds evolutionary perspective.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation
- **Claim pointer** The authors state that site-directed mutagenesis of Q126 and F74 "confirms the role" of these residues in ligand binding, and that the binding data support a proposed binding mode
- **Evidence pointer** Section "Site-directed mutagenesis of CecR confirms the role of Q126 and F74 in ligand binding", Fig. 4G,H
- **Concern** The mutagenesis experiments show that Q126A and F74A mutants bind cefepime more weakly than wild-type, but saturation was not achieved even at 10-fold higher antibiotic concentrations. This means Kd values could not be determined for the mutants, and the magnitude of the affinity reduction is not quantified. The claim of "confirmation" is therefore overstated. The data are consistent with a role for these residues, but they do not confirm a specific binding mode or establish the relative contribution of each residue. Additionally, only two of the five predicted binding residues were tested, leaving the proposed binding model incompletely validated.
- **Why it matters** The functional significance of the structural findings rests on the identification of key ligand-binding residues. Without quantitative binding data for the mutants, the conclusion that Q126 and F74 are critical for ligand recognition is not firmly established. This weakens the central functional claim of the manuscript.
- **Resolution test** Provide quantitative Kd values for the mutant proteins if achievable, or alternatively use complementary methods (e.g., isothermal titration calorimetry, NMR) to demonstrate reduced binding affinity. If saturation cannot be achieved, the authors should temper the language from "confirms" to "supports" and acknowledge the limitation explicitly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Physiological relevance
- **Claim pointer** The authors suggest that the measured affinities are relevant to antibiotic sensing in vivo, and that the weak binding of chloramphenicol (Kd > 50 mM) may still be physiologically meaningful due to potential intracellular accumulation
- **Evidence pointer** Section "CecR affinity varies for different antibiotics", Discussion of chloramphenicol accumulation citing Haemophilus influenzae
- **Concern** The Kd for chloramphenicol could not be determined and is reported as > 50 mM. The argument for physiological relevance relies on a single example from a different bacterial species (H. influenzae) where intracellular chloramphenicol reached ~30 mM. This extrapolation is speculative. No data are presented on intracellular antibiotic concentrations in E. coli under relevant conditions, nor on the CecR occupancy at physiologically plausible antibiotic concentrations. The claim that weak binding may still be relevant is not supported by direct evidence.
- **Why it matters** The manuscript positions CecR as an antibiotic sensor. If the physiologically relevant ligands are bound with millimolar affinities, the biological significance of the sensing mechanism is questionable. The authors need to either provide evidence supporting the relevance of these affinities or moderate their claims about the physiological role of CecR in antibiotic sensing.
- **Resolution test** Provide measurements or calculations of intracellular antibiotic concentrations in E. coli under conditions relevant to CecR-mediated regulation. Alternatively, perform cellular assays (e.g., reporter assays) demonstrating that CecR-mediated regulation responds to antibiotic concentrations consistent with the measured Kd values.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Structural interpretation
- **Claim pointer** The authors state that the CecR structure with PEG fragments may represent either the apo or ligand-bound state, and that the distance between helices α3 and α3' is a factor determining the protein state
- **Evidence pointer** Section "CecR has a tunnel-like ligand-binding cavity", comparison with CgmR structures
- **Concern** The manuscript does not provide a definitive assignment of the CecR-PEG structure to either the apo or ligand-bound state. The comparison with CgmR is informative but does not resolve the question for CecR. The authors acknowledge this limitation, but the ambiguity affects the interpretation of the structural features described, particularly the significance of the tunnel-like cavity and the position of the α8a helix. Without a ligand-free structure or a structure with a physiological ligand, the conformational state of the reported structure remains uncertain.
- **Why it matters** The structural basis of antibiotic sensing by CecR depends on understanding the conformational changes associated with ligand binding. If the reported structure represents an intermediate or non-physiological state, the conclusions about ligand recognition mechanisms may be compromised.
- **Resolution test** Attempt to obtain a ligand-free structure (e.g., by removing PEG from crystallization conditions) or a structure with a bound physiological ligand. Alternatively, use solution methods (SAXS, HDX-MS) to compare the conformational state of CecR in the presence and absence of ligands.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Docking validation
- **Claim pointer** The authors use molecular docking to predict interactions between CecR and antibiotics, and these predictions are used to explain differential binding affinities
- **Evidence pointer** Section "Docking of antibiotics to the CecR-ligand-binding site reveals potential regulator-effector interactions", Fig. 3B,D,F,H
- **Concern** The docking results are presented without validation. The only validation mentioned is redocking of the PEG fragment, which does not validate the docking of antibiotics. No scoring function benchmarks, cross-docking studies, or comparison with experimental data (e.g., SAR from related compounds) are provided. The predicted interactions, particularly the hydrogen bond between Q126 and the amide group of cefepime, are plausible but not experimentally verified. The explanation for differential affinities based on docking poses is speculative.
- **Why it matters** The docking results are used to rationalize the observed binding affinities and to identify key residues for mutagenesis. If the docking is inaccurate, the interpretation of the binding data and the design of mutagenesis experiments may be misguided.
- **Resolution test** Provide additional validation of the docking protocol, such as enrichment studies, comparison with known ligand-receptor complexes of similar TFRs, or experimental verification of predicted contacts (e.g., through structural studies of ligand complexes or NMR chemical shift perturbation).

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Data completeness
- **Claim pointer** The authors report Kd values for CecR with cefepime (79.27 ± 7 μM) and cefoxitin (6.07 ± 2.8 mM), and state that chloramphenicol binding could not be saturated
- **Evidence pointer** Table 1, Fig. 3C,E,G
- **Concern** The spectral shift data are presented as mean ± SD from three independent experiments, but individual data points, confidence intervals, and the quality of the fits are not shown in the provided text. The dynamic range of the spectral shift signal, the signal-to-noise ratio, and the reproducibility of the measurements are not documented. For the chloramphenicol experiments, the interference from DMSO is described, but the control experiments (e.g., DMSO-only titrations) are not shown.
- **Why it matters** The reliability of the reported Kd values depends on the quality of the underlying measurements. Without access to the raw data or fit statistics, the reader cannot assess whether the reported affinities are robust.
- **Resolution test** Include representative spectral shift curves with fitted isotherms, show the residuals of the fits, and provide the confidence intervals for each Kd determination. For chloramphenicol, show control experiments demonstrating the DMSO effect and the inability to reach saturation.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract describes CecR as a "HTH-type transcriptional dual regulator" without explaining what "dual" refers to in this context. The term is used without definition or subsequent elaboration.
- **Required correction** Define "dual regulator" (e.g., both activator and repressor) or remove the term if it is not essential to the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Experimental detail
- **Affected element** Methods, spectral shift analysis
- **Evidence pointer** Section "Spectral shift analysis"
- **Issue** The methods state that the spectral shift experiment was repeated at least three times, but do not specify whether these are technical replicates, biological replicates, or independent protein preparations. The variability between protein batches is not addressed.
- **Required correction** Specify the nature of the replicates and whether the reported mean and SD are derived from independent protein preparations.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion of CecR state
- **Evidence pointer** Section "CecR has a tunnel-like ligand-binding cavity"
- **Issue** The authors note that the distance between helices α3 and α3' is variable in apo TFR structures, but do not provide the measured distance for CecR or a quantitative comparison with known apo and ligand-bound structures.
- **Required correction** Provide the measured α3-α3' distance for CecR and compare it quantitatively with a set of representative TFR structures in different states.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction, Discussion
- **Evidence pointer** Section "Introduction", Section "CecR conserved motifs contain residues responsible for ligand recognition"
- **Issue** The manuscript does not discuss whether the predicted ligand-binding residues in CecR align with known ligand-binding residues in other subfamily D members beyond the structural comparison with PhlH. A sequence alignment of subfamily D members showing the conservation of these specific residues would strengthen the analysis.
- **Required correction** Include a multiple sequence alignment of subfamily D TFRs highlighting the conservation of the predicted ligand-binding residues.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Fig. 4
- **Evidence pointer** Fig. 4G,H
- **Issue** The binding curves for the Q126A and F74A mutants are described as not reaching saturation, but the figure is not available in the provided text. The reader cannot visually assess the quality of the data or the extent of the binding deficit.
- **Required correction** Ensure the figure clearly shows the lack of saturation and includes appropriate controls (e.g., wild-type curve for comparison, DMSO controls).

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** The table presents Kd values with standard deviations, but the number of independent experiments and the statistical test used to compare Kd values between ligands are not stated.
- **Required correction** State the number of independent experiments and the statistical methods used for comparisons.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Multiple sections
- **Issue** The manuscript uses "ligand-binding cavity" and "ligand-binding tunnel" interchangeably. While related, these terms may imply different geometries. Consistency would improve clarity.
- **Required correction** Use a single term consistently, or define both and explain when each is appropriate.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Scope
- **Affected element** Conclusions
- **Evidence pointer** Section "Conclusions"
- **Issue** The conclusion states that the results are "an important contribution to the understanding of the CecR-related mechanisms underlying antimicrobial resistance." This is a broad claim given that no functional assays linking CecR structure to resistance phenotypes are presented.
- **Required correction** Moderate the claim to reflect that the structural and biophysical data provide a foundation for future functional studies.

## Risk / unsupported claims
- The claim that mutagenesis "confirms" the role of Q126 and F74 in ligand binding is not fully supported, as quantitative Kd values for the mutants could not be determined
- The physiological relevance of the chloramphenicol binding affinity (Kd > 50 mM) is speculative and relies on extrapolation from a different bacterial species
- The assignment of CecR to subfamily D is well supported, but the statement that the additional structural elements (α8a and loop) are "characteristic" of subfamily D members is based on limited structural data (only PhlH and RutR are cited)
- The prediction that CecR may recognize ligands beyond antibiotics in plant pathogens is speculative and not experimentally tested
- The docking-based explanation for differential binding affinities is not validated experimentally
- The statement that the CecR-PEG structure may represent the ligand-bound state is not resolved, and the functional implications of this ambiguity are not fully addressed