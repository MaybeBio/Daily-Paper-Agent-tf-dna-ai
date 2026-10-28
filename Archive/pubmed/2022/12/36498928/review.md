## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, conclusions) as provided by the user
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims by presented evidence; no assessment of editorial fit or publication venue suitability
- **Shared manuscript claim summary** The authors propose that non-conserved amino acid residues in classical Cys2His2 ββα zinc finger domains modulate the thermodynamics of Zn(II) binding through formation or loss of hydrogen bonds in the second coordination shell, which can alter the balance of enthalpic and entropic contributions to binding free energy. They further claim that Zn(II) binding to these domains can be entropically driven, and that this preference is not correlated with the metal binding site or secondary structure extent but with a reservoir of interactions within the protein core.
- **Visible evidence base** Computational results (classical MD, SMD, PCA, free energy surfaces, hydrogen bond analysis), spectroscopic data (CD, UV-Vis Co(II) titrations), competition experiments with chelators, ITC measurements, pKa determinations
- **Missing materials affecting confidence** Figures S1-S8 and Tables S1-S4 are referenced but not provided; raw ITC thermograms are not shown; no error bars or replicate information are visible in the text for key thermodynamic parameters; no statistical analysis is described for comparisons between peptides; the NMR structure PDB:2YTR used for homology modelling is not described in terms of sequence identity to the CP1 peptides

## Reviewer

- **Overall assessment** This manuscript addresses a relevant question in zinc finger biology: how non-conserved residues modulate Zn(II) binding thermodynamics. The combination of computational and experimental approaches is appropriate and potentially powerful. However, the evidence as presented has several gaps that prevent full evaluation of the central claims. The MD simulations show no significant conformational differences between CP1-1991 and CP1-2015, yet the authors attribute stability differences to specific hydrogen bonds identified in extracted structures. The experimental thermodynamic data are presented without visible uncertainty estimates, and the connection between specific residues and observed thermodynamic differences is inferred rather than directly demonstrated. The claim that Zn(II) binding can be entropically driven for Cys2His2 ZFs is interesting but requires stronger support given that the number of protons released is nearly identical across peptides. The manuscript would benefit from clearer presentation of replicate data, statistical comparisons, and a more direct test of the proposed hydrogen bond contributions.
- **Who would be interested in the results, and why** Researchers studying zinc finger proteins, metalloprotein thermodynamics, and protein design. The results are relevant to those interested in how sequence variation outside the metal binding site affects metal affinity and folding stability, which has implications for understanding zinc metalloproteome dynamics and for engineering zinc finger domains with tailored stability for biotechnological applications.
- **Major strengths** The combination of MD simulations with multiple experimental techniques (CD, UV-Vis, ITC, competition experiments) provides a multifaceted approach. The use of both consensus peptides and targeted mutants is a logical strategy to dissect sequence contributions. The thermodynamic decomposition into enthalpic and entropic components, including correction for proton release, is methodologically thoughtful. The identification of specific hydrogen bonds in the second coordination shell as potential modulators of stability is a testable hypothesis with design implications.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that specific hydrogen bonds between non-conserved residues (Lys13 and Asp15) and conserved hydrophobic residues stabilize the CP1-1991 structure and contribute to its higher Zn(II) affinity.
- **Evidence pointer** Section 2.1, Figure 2, Figure 3A; Section 2.4, Table 2
- **Concern** The hydrogen bonds are identified from structures extracted from free energy surface minima in classical MD simulations. However, the RMSD, RMSF, and PCA analyses show no significant differences between CP1-1991 and CP1-2015. The authors do not provide quantitative occupancy data for these hydrogen bonds across the full trajectories, nor do they demonstrate that these hydrogen bonds are absent in the CP1-2015 simulations. The connection between the presence of these hydrogen bonds and the measured thermodynamic differences is correlative. The mutant studies (K/S, D/S, K/S-D/S) show changes in thermodynamic parameters, but the authors do not directly demonstrate that loss of these specific hydrogen bonds is the causal mechanism, as opposed to other effects of the mutations such as altered electrostatics or packing.
- **Why it matters** The central mechanistic claim of the paper rests on the identification of these hydrogen bonds as the structural basis for stability differences. Without quantitative trajectory analysis and a direct test of the hydrogen bond contribution, the mechanism remains speculative.
- **Resolution test** Provide hydrogen bond occupancy analysis across full trajectories for both peptides and all mutants. Show that the specific hydrogen bonds identified are present in CP1-1991 and absent or reduced in CP1-2015 and in the mutants. Ideally, perform simulations with mutations that disrupt only the hydrogen bond without other changes, or use a computational approach such as free energy perturbation to quantify the contribution of these specific interactions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data presentation and statistical support
- **Claim pointer** The authors report thermodynamic parameters (ΔG°, ΔH°, −TΔS°) for Zn(II) binding to multiple ZF peptides and state that binding can be entropically driven for some variants.
- **Evidence pointer** Section 2.4, Table 2, Figure 6
- **Concern** The thermodynamic parameters are presented without error estimates, replicate numbers, or statistical comparisons between peptides. The ITC data analysis is described, but no information is given on the number of independent titrations performed, the reproducibility of the measurements, or the uncertainty in the fitted parameters. The claim that binding is entropically driven for CP1-K/S rests on a single set of values without demonstrated significance. Additionally, the propagation of errors from pKa determinations and proton release corrections into the final thermodynamic parameters is not described.
- **Why it matters** The distinction between enthalpically and entropically driven binding is a central conclusion of the paper. Without uncertainty estimates and statistical testing, it is impossible to determine whether the observed differences between peptides are meaningful or within experimental noise.
- **Resolution test** Provide replicate ITC measurements (at least n=3) with standard deviations or standard errors for all reported thermodynamic parameters. Perform appropriate statistical tests (e.g., t-tests or ANOVA) to compare parameters between peptides. Describe the error propagation from pKa and proton release corrections.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive consistency
- **Claim pointer** The authors state that the distant location of the three hydrogen bonds from the C-terminal α-helix suggests an allosteric role in these intermolecular interactions, and that these hydrogen bonds stabilize the α-helix.
- **Evidence pointer** Section 2.1, Figure 2, Figure 3A
- **Concern** The authors report that CP1-1991 has three hydrogen bonds stabilizing the α-β helix-sheet interaction and a larger α-helix content translated into one more hydrogen bond in CP1-1991. However, the RMSD and PCA analyses show no significant conformational differences between the two peptides. The claim of an allosteric mechanism is speculative and not supported by any perturbation analysis. If the hydrogen bonds are distant from the α-helix, how do they stabilize it? The authors do not provide a mechanistic explanation for how these distant interactions propagate to the α-helix.
- **Why it matters** The allosteric claim is presented as a finding but is not tested. Understanding the mechanism of stabilization is important for the design implications the authors discuss.
- **Resolution test** Perform additional analyses to test the allosteric hypothesis, such as correlation network analysis or perturbation response scanning. Alternatively, temper the claim to be more clearly speculative and provide a more detailed structural rationale for how these hydrogen bonds could affect α-helix stability.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of conclusions
- **Claim pointer** The authors conclude that non-conserved residues modulate Zn(II) binding thermodynamics in classical ββα zinc finger domains and that this has implications for understanding zinc finger saturation under cellular conditions.
- **Evidence pointer** Section 2.5, Conclusions
- **Concern** The study is limited to two consensus peptides and a small number of mutants derived from these sequences. The authors generalize to all classical ββα zinc finger domains, but the sequence space of natural zinc fingers is vast and diverse. The specific hydrogen bonds identified in CP1-1991 may not be present or relevant in other zinc finger contexts. The connection to cellular conditions is speculative, as the authors do not measure or model intracellular zinc availability or competition with other zinc-binding proteins.
- **Why it matters** The broader significance of the work depends on the generalizability of the findings. Overgeneralization from a limited set of peptides weakens the impact of the conclusions.
- **Resolution test** Acknowledge the limited sequence sampling and temper the generalizability claims. If possible, include additional zinc finger sequences with varying degrees of conservation in the analysis, or clearly frame the conclusions as specific to the consensus peptides studied.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.3, first paragraph
- **Evidence pointer** Section 2.3
- **Issue** The sentence "The mean rupture forces inform the strength of Zn-L interactions; however, this value reflects the mean for the four Zn-L interactions, but does exclude how the protein affects the Zn(II) unbinding?" is grammatically awkward and unclear. The question mark at the end appears to be a typo.
- **Required correction** Rewrite for clarity, for example: "The mean rupture force reflects the average strength of the four Zn-L interactions but does not directly report on how the protein environment affects the unbinding process. This information is better captured by the total work done."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.3, spectroscopic characterization
- **Evidence pointer** Section 2.3, Figure S5, Figure S6
- **Issue** The CD spectra are described as showing "similar band patterns" for all ZFs, but no quantitative comparison is provided. The authors state that all peptides form CoL complexes with similar spectral features, but the extinction coefficients are only given as "greater than 300 M−1 cm−1" without specific values for each peptide.
- **Required correction** Provide quantitative comparison of CD spectra (e.g., mean residue ellipticity values at key wavelengths) and report specific extinction coefficients for each peptide in Table S3.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Section 3.2.1, MD simulations
- **Evidence pointer** Section 3.2.1
- **Issue** The equilibration protocol is described as a "four-step" procedure, but only three steps are described (minimization, heating, NPT equilibration). The fourth step (production run) is mentioned separately. This is confusing.
- **Required correction** Clarify the protocol by either describing the production run as part of the equilibration or explicitly listing four distinct equilibration steps.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 2.4, ITC analysis
- **Evidence pointer** Section 2.4, Table 2
- **Issue** The authors state that "the most significant decrease in ΔH° values was observed for the CP1-1991-K/S peptide" but do not provide a statistical comparison to support this claim. Additionally, the interpretation that "substitution of Asp15 compensates unfavorable entropic gain" is speculative without direct structural evidence.
- **Required correction** Provide statistical analysis to support the claim of significance. Consider whether the compensation interpretation is warranted or should be presented more cautiously.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Section 2.5
- **Evidence pointer** Section 2.5
- **Issue** The comparison with the ZFY protein is brief and does not provide sufficient detail on how the previous findings relate to the current work. The reference to "an entropic gain associated with the hydrophobic core packing" in ZFY is not contextualized.
- **Required correction** Expand the comparison to explain the specific relevance of the ZFY findings to the current study and how the current work extends or differs from previous observations.

## Risk / unsupported claims
- The claim that specific hydrogen bonds between Lys13 and Asp15 and conserved hydrophobic residues are responsible for the higher stability of CP1-1991 is not directly supported by the presented data. Hydrogen bond occupancy across trajectories is not quantified, and the mutant studies do not isolate the hydrogen bond contribution from other effects.
- The claim that Zn(II) binding to Cys2His2 ZFs can be entropically driven is based on a single peptide (CP1-K/S) without demonstrated statistical significance or replicate measurements.
- The generalization from two consensus peptides to all classical ββα zinc finger domains is not supported by the limited sequence sampling.
- The statement that "non-conserved residues can alter metal-coupled folding mechanisms" is not directly tested, as the MD simulations did not observe folding/unfolding events and the experimental methods do not directly probe folding pathways.
- The biological significance discussion regarding cellular zinc availability and zinc finger saturation is speculative and not supported by direct experimental evidence in this study.
- The claim that the distant location of hydrogen bonds from the C-terminal α-helix suggests an allosteric role is speculative and not tested by any perturbation or correlation analysis.