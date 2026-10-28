## Review setup
- **Input scope** Full manuscript text (abstract, results, discussion, methods) without figures, tables, or supplementary material
- **Assessment boundary** Scientific claims, methodological soundness, and internal consistency of the reported computational and experimental work; no assessment of figures, tables, or supplementary data that were not provided
- **Shared manuscript claim summary** The authors use MD simulations and MM/PBSA binding energy calculations to identify hot spots at the REV7:RBM protein-protein interaction interface, and validate these predictions using fluorescence polarization displacement assays with truncated and mutated RBM peptides
- **Visible evidence base** Text descriptions of computational results (Tables 1-3 referenced but not shown), FP assay results (Table 4 referenced but not shown), and methodological details in the STAR Methods section
- **Missing materials affecting confidence** All figures, all tables, all supplementary materials, and the full experimental dataset; the manuscript text alone is insufficient to verify quantitative claims

## Reviewer
- **Overall assessment** The manuscript addresses a relevant question in the field of protein-protein interaction targeting for cancer therapy, specifically the REV7:RBM interface. The combination of computational prediction and experimental validation is appropriate in principle. However, the manuscript as presented has several significant issues. The computational methodology relies on MM/PBSA, which is known to have limitations in accuracy for ranking binding contributions, and the authors explicitly neglect entropic contributions without adequate justification. The experimental validation uses a competition displacement assay rather than direct binding measurements, which complicates interpretation of the results. Most critically, there is an apparent inconsistency between the computational predictions (which suggest the beta-strand region dominates binding energy) and the experimental results (which suggest the alpha-helix region is more important for binding), and this discrepancy is acknowledged but not adequately resolved. The manuscript would benefit from a more rigorous treatment of the computational methodology and a clearer reconciliation of the computational and experimental findings.

- **Who would be interested in the results, and why** Researchers working on protein-protein interaction inhibitors, particularly those targeting DNA damage response pathways for cancer therapy. The work may also be of interest to computational chemists studying binding energy prediction methods, and to structural biologists studying HORMA domain proteins. The identification of specific hot spot residues could guide future drug design efforts.

- **Major strengths** The manuscript addresses a clinically relevant target with a combined computational and experimental approach. The selection of four structurally diverse REV7:RBM complexes for analysis is thoughtful and covers different conformational states of the dynamic adaptor region. The development of a fluorescence polarization displacement assay for this system is a practical contribution that could be useful for future screening efforts. The authors are transparent about the limitations of their computational approach, particularly regarding entropy calculations.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of computational methodology
- **Claim pointer** The authors claim that MM/PBSA binding energy calculations can identify hot spot residues contributing the majority of binding free energy to REV7:RBM interactions.
- **Evidence pointer** Methods section, "Binding energy calculations"; Results section, "Binding energy analysis for the REV7:RBM complexes"
- **Concern** The MM/PBSA method is used without entropic contributions, and the authors justify this by stating that calculations are performed for "RBMs from the same chemical series." This justification is insufficient. The four RBM peptides are not a single chemical series in the medicinal chemistry sense; they are different peptide sequences with different lengths and compositions. More importantly, the authors state that entropy was "significantly biased by fluctuations of the RBM regions that were not directly interacting with REV7," which suggests the simulations may not have converged adequately for reliable entropy estimation. The neglect of entropy in ranking binding contributions can lead to incorrect conclusions about which residues are true hot spots, as entropic penalties can vary substantially across different binding interfaces.
- **Why it matters** The central claim of the paper, that specific residues constitute druggable hot spots, depends on the reliability of the energy decomposition. If the computational ranking is unreliable due to neglected entropy or other methodological limitations, the guidance for drug design could be misleading.
- **Resolution test** The authors should either (a) perform entropy calculations using methods such as normal mode analysis or quasi-harmonic approximation, (b) provide convergence evidence demonstrating that entropy contributions are indeed negligible for their comparisons, or (c) temper their claims about hot spot identification and present the computational results as hypothesis-generating rather than definitive.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Internal consistency between computational and experimental results
- **Claim pointer** The authors state that computational studies show the beta-strand region contributes the majority of binding energy, while experimental studies show that removal of the alpha-helix region has a more significant effect on binding.
- **Evidence pointer** Results section, "Pairwise binding energy decompositions" and "Fluorescence polarization displacement assay"
- **Concern** There is a clear discrepancy between the computational predictions and experimental findings. The computational analysis suggests the beta-strand region dominates binding energy, but the experimental data show that peptides lacking the alpha-helix region are significantly less effective at displacing the full-length peptide. The authors acknowledge this discrepancy in the Discussion but do not resolve it. They suggest that entropic effects may explain the difference, but this is speculative and not supported by any quantitative analysis. This inconsistency undermines the central claim that the computational approach can reliably identify hot spots for drug targeting.
- **Why it matters** If the computational and experimental results cannot be reconciled, the utility of the computational approach for guiding drug design is questionable. The paper needs to either provide a quantitative explanation for the discrepancy or acknowledge that the computational predictions are not well-supported by the experimental data.
- **Resolution test** The authors should provide a quantitative analysis that reconciles the computational and experimental findings, such as calculating the expected change in binding free energy from the computational model for each truncated peptide and comparing it directly to the experimental IC50 values. Alternatively, they should revise their conclusions to reflect the experimental results as the primary evidence for hot spot identification.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Experimental validation approach
- **Claim pointer** The authors claim that the FP displacement assay validates their computational predictions about hot spot residues.
- **Evidence pointer** Results section, "Fluorescence polarization displacement assay"; Table 4 (referenced but not shown)
- **Concern** The FP displacement assay measures the ability of unlabeled peptides to displace a labeled peptide from a pre-formed complex. This is a competition assay that measures relative binding affinities, but it is indirect. The assay cannot distinguish between effects on association rate, dissociation rate, or binding mode. Additionally, the assay uses a single concentration of the labeled complex (100 nM), and the authors do not report the KD of the labeled peptide for REV7, which is essential for interpreting competition data. Without knowing the KD of the tracer, the IC50 values cannot be reliably converted to Ki values, and the relative potencies of different peptides may not accurately reflect their true binding affinities.
- **Why it matters** The experimental validation is a key component of the paper's claims. If the assay is not properly characterized, the conclusions drawn from it may be unreliable.
- **Resolution test** The authors should report the KD of the FAM-REV3RBM1 peptide for REV7, use the Cheng-Prusoff equation to convert IC50 values to Ki values where appropriate, and demonstrate that the assay is operating in a regime where competition is valid (e.g., tracer concentration below KD).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Completeness of computational analysis
- **Claim pointer** The authors claim to have performed MD simulations and MM/PBSA analysis on four REV7:RBM complexes, covering the range of conformations adopted by REV7.
- **Evidence pointer** Results section, "Molecular Dynamics Simulations" and "Binding energy analysis"
- **Concern** The manuscript describes 50 ns MD simulations, which is relatively short for protein-peptide binding studies. The authors do not report convergence analysis, such as RMSD stabilization over time or block averaging of energies. The MM/PBSA calculations are performed on snapshots from 10-20 ns of the trajectories, but it is unclear whether the systems were fully equilibrated by 10 ns. Additionally, the authors do not report error estimates for their calculated binding energies, which is essential for assessing whether differences between residues or complexes are statistically significant.
- **Why it matters** Without evidence of convergence and error estimates, the quantitative claims about binding energy contributions cannot be evaluated. The field standard for such calculations requires demonstration that results are stable and reproducible.
- **Resolution test** The authors should provide RMSD plots showing equilibration, block-averaged energy values with standard errors, and ideally extend simulations or perform replicate runs to demonstrate reproducibility.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and completeness of reporting
- **Affected element** Methods section, "Molecular Dynamics simulations"
- **Evidence pointer** Methods section, location not provided
- **Issue** The methods state that "Three well-equilibrated systems were generated" but do not explain what these three systems are. It is unclear whether these are three replicates of the same system or three different systems. This ambiguity affects the reproducibility of the work.
- **Required correction** Clarify whether the three systems represent replicate simulations or different starting conditions, and describe how they were generated.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Results section, "REV7:REV3RBM1 PPI"
- **Evidence pointer** Results section, location not provided
- **Issue** The text states "the energy of any individual pi-pi stacking interaction involving histidine is on the order of -3 to -4 kcal/mol,AAA" where "AAA" appears to be a placeholder or formatting artifact. This is a typographical error that should be corrected.
- **Required correction** Remove the "AAA" artifact and ensure the sentence is complete and grammatically correct.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** Results section, "REV7:RBMIPA and REV7:RANRBM PPIs"
- **Evidence pointer** Results section, location not provided
- **Issue** The text states "residues 62-65 in IPA and 177-180 in IPA" for the RANRBM peptide, but the second reference should presumably be to RAN, not IPA. This appears to be a typographical error.
- **Required correction** Correct the residue range reference to "177-180 in RAN" or similar, as appropriate.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness of data reporting
- **Affected element** Results section, "Fluorescence polarization displacement assay"
- **Evidence pointer** Table 4 (referenced but not shown)
- **Issue** The text reports IC50 values for several peptides but does not provide confidence intervals or replicate numbers. Without these, the precision of the measurements cannot be assessed.
- **Required correction** Report IC50 values with 95% confidence intervals and the number of independent replicates.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Methods section, "Fluorescence polarization displacement assay"
- **Evidence pointer** Methods section, location not provided
- **Issue** The assay description states measurements were taken at 15, 30, 60, 90, and 120 minutes, but the Results do not indicate which time point was used for the reported IC50 values. If equilibrium was not reached, the reported values may be time-dependent.
- **Required correction** Specify the time point used for IC50 determination and demonstrate that equilibrium was reached at that time.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Results section, "REV7:REV3RBM1 PPI"
- **Evidence pointer** Results section, location not provided
- **Issue** The text mentions "PDB ID 3VU7" for the REV7-REV3RBM1 complex, but the Methods section lists "PDB: 3UV7" for the same structure. These are inconsistent identifiers.
- **Required correction** Ensure the PDB identifier is consistent throughout the manuscript.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity of figure references
- **Affected element** Results section, "REV7:REV3RBM1 PPI"
- **Evidence pointer** Figure 3 (referenced but not shown)
- **Issue** The text refers to "Figure 3" for per-residue energy contributions but does not clearly describe what is shown in the figure. Without the figure, the reader cannot interpret the quantitative claims.
- **Required correction** Provide a clear description of the figure content in the text, including what quantities are plotted and how to interpret them.

## Risk / unsupported claims
- The claim that MM/PBSA calculations can reliably identify hot spot residues for drug targeting is not fully supported, given the acknowledged limitations of the method and the discrepancy with experimental results.
- The claim that the FP displacement assay validates the computational predictions is not fully supported, as the assay results appear to partially contradict the computational findings.
- The specific claim about the W2009/H57 pi-pi interaction contributing approximately 7 kcal/mol to binding energy is not verifiable from the text alone, as the computational details and error estimates are not provided.
- The claim that the identified hot spots "can be targeted with small molecules" is speculative and not supported by any experimental evidence of druggability.
- The relative importance of the alpha-helix versus beta-strand regions for binding is not clearly resolved, with computational and experimental results pointing to different conclusions.
- The manuscript's statement that the FP assay "will be essential for the evaluation of potential small molecule inhibitors" is an overstatement, as the assay has not been validated for high-throughput screening or shown to be robust across different inhibitor chemotypes.