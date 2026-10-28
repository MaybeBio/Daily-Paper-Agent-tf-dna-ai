## Review setup
- **Input scope** Full manuscript text including abstract, introduction, experimental methods, results, discussion, conclusions, and supplementary figure references.
- **Assessment boundary** Scientific validity, methodological soundness, interpretation of results, and alignment with claims made in the abstract and conclusions. No assessment of formatting or editorial style beyond readability.
- **Shared manuscript claim summary** The authors claim that multivalent cations stabilize DNA duplexes beyond simple charge neutralization, with stability first increasing then decreasing with cation concentration, and maximum stability increasing with cation valence. They propose a mechanism involving cation embedding in the DNA minor groove and interstrand clamping, supported by single-molecule magnetic tweezers experiments and all-atom molecular dynamics simulations.
- **Visible evidence base** Experimental data from HRM assays (dye-based and probe-based), magnetic tweezers force-unpeeling measurements, and MD simulation analyses including groove widths, clamping fractions, and ion distributions. Figures referenced include Fig. 1–5, Tables S1, and supplementary figures S1–S9.
- **Missing materials affecting confidence** The full supplementary information (SI) is not provided, including Method S1, Method S2, Fig. S1–S9, and Table S1. Raw data files, simulation trajectories, and analysis scripts are not available. The manuscript states data are in the SI but the SI itself is not part of the provided material.

## Reviewer
- **Overall assessment** The manuscript addresses a significant and timely question in nucleic acid biophysics: how multivalent cations modulate DNA duplex stability in regimes where condensation complicates traditional measurements. The combination of single-molecule force spectroscopy with all-atom simulations is appropriate and potentially powerful. The central observation that maximum duplex stability increases monotonically with cation valence is interesting and, if robust, would constitute a useful contribution. However, several technical and interpretive issues need to be resolved before the case is fully established. The attribution of the stability increase to minor-groove clamping is plausible but not definitively proven by the presented data, and the quantitative framework derived from the Rouzina–Bloomfield model requires more careful justification and error analysis. The manuscript is generally well written and accessible, but some methodological details are insufficiently described in the main text.
- **Who would be interested in the results, and why** Researchers in nucleic acid biophysics, single-molecule mechanics, DNA nanotechnology, and chromatin biology would find these results relevant. The work provides a methodological approach for measuring DNA stability under condensing conditions and offers mechanistic hypotheses that could inform the design of ion-responsive DNA-based materials and improve understanding of intracellular ionic regulation of genome stability.
- **Major strengths** The experimental design cleverly circumvents condensation artifacts by applying high tension during unpeeling, enabling equilibrium measurements under conditions where bulk methods fail. The systematic variation of cation valence from monovalent to a highly charged protein provides a clear trend. The MD simulations complement the experiments and offer a structural hypothesis for the observed valence dependence. The manuscript is clearly written and the figures appear well organized.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative free energy extraction), R1-M2 (simulation concentration selection), R1-M3 (mechanistic attribution), R1-M4 (statistical robustness).
- **Assessment against Nature-style criteria** Originality: The approach of using force-unpeeling to avoid condensation is creative, though the underlying physics of cation–DNA interactions is well studied. Scientific importance: The question of how multivalent ions affect DNA stability is of broad relevance, and the proposed clamping mechanism could have implications for understanding chromatin and DNA packaging. Interdisciplinary readership: The work bridges single-molecule biophysics, computational chemistry, and nucleic acid biology, making it potentially interesting to a broad audience. Technical soundness: The experimental methodology is sound in principle, but the quantitative analysis and simulation design have weaknesses that need addressing. Readability for nonspecialists: The manuscript is largely accessible, though some sections assume familiarity with single-molecule techniques and MD simulation conventions.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding the quantitative free energy extraction, simulation concentration choices, and statistical robustness of the key claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative analysis
- **Claim pointer** The authors claim to determine the chemical free energy change of DNA duplex dissociation (ΔGchem) from measured unpeeling forces using the Rouzina–Bloomfield framework, and report maximum values of 3.33 kBT/bp for Na+ increasing to 3.98 kBT/bp for protamine.
- **Evidence pointer** Results and discussion, Fig. 3A–C, Eq. 1
- **Concern** The extraction of ΔGchem from the measured unpeeling force relies on Eq. 1, but the derivation and assumptions of this framework are not fully explained in the main text. The relationship between the applied force, the measured extension change (Δl), and the chemical free energy is nontrivial, especially for a heterogeneous sequence with two GC-content segments. The manuscript does not specify how Δl is averaged over the sequence, how the 21-bp GC island affects the calculation, or how the force-extension behavior of ssDNA and dsDNA is modeled. Additionally, the reported ΔGchem values are presented without error bars or confidence intervals, making it impossible to assess whether the differences between cations are statistically significant.
- **Why it matters** The central quantitative claim of the paper, that maximum duplex stability increases with cation valence, depends entirely on the accuracy of this free energy extraction. If the framework is misapplied or the uncertainties are large, the monotonic trend could be an artifact.
- **Resolution test** Provide a detailed derivation or citation for the Rouzina–Bloomfield framework as applied here, including how Δl is determined for each force cycle and how sequence heterogeneity is handled. Report standard errors or confidence intervals for ΔGchem values, ideally from multiple independent tethers and force cycles. Show that the extracted ΔGchem is insensitive to reasonable variations in the assumed force-extension models.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Simulation design
- **Claim pointer** The authors state that MD simulations were performed at "near-neutralization concentration for each cation" and list 1000 mM Na+, 100 mM Ca2+, 2 mM SPD3+, 0.1 mM PLL6+, and 1 µM protamine.
- **Evidence pointer** Experimental section, MD experiments; Results and discussion, Fig. 4A–D
- **Concern** The choice of concentrations is not justified quantitatively. The authors claim these are "near-neutralization" concentrations, but no calculation or reference is provided to show that these concentrations correspond to similar degrees of DNA charge neutralization. For Na+ at 1000 mM, the Debye length is very short and the ionic atmosphere is quite different from that at 1 µM protamine, where the ionic strength is negligible. Comparing structural features such as groove widths and clamping fractions across such vastly different ionic conditions may conflate concentration effects with valence effects. Additionally, the protamine concentration of 1 µM is far below the other concentrations, and it is unclear whether the simulation box contains enough protamine molecules to represent a meaningful ensemble.
- **Why it matters** The mechanistic conclusion that higher-valent cations preferentially clamp the minor groove is based on comparisons across these simulations. If the concentrations are not matched in terms of charge neutralization, the observed differences in clamping could be due to differences in ion occupancy rather than valence per se.
- **Resolution test** Provide a quantitative definition of "near-neutralization" and show that the chosen concentrations achieve similar fractional charge neutralization of the DNA, for example by computing the ion atmosphere from the simulations. Alternatively, perform simulations at matched ionic strengths or matched degrees of neutralization to isolate the effect of valence. Justify the protamine concentration and describe how many protamine molecules are present in the simulation box.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic interpretation
- **Claim pointer** The authors claim that "higher-valent cations preferentially embed in the minor groove of DNA and clamp the minor groove, in contrast to the major-groove clamping reported for RNA, thereby stabilizing the helix more efficiently."
- **Evidence pointer** Results and discussion, Fig. 5A and B; Table S1
- **Concern** The causal link between minor-groove clamping and increased duplex stability is inferred from correlation: simulations show more clamping and experiments show higher stability for higher-valent cations. However, the manuscript does not demonstrate that the clamping is the cause of the increased stability. Other factors, such as changes in water activity, ion correlation effects, or sequence-specific binding, could also contribute. The comparison to RNA is made without direct experimental or simulation evidence in this work, relying on prior reports. The statement that clamping "stabilizes the helix more efficiently" is not supported by a quantitative comparison of stabilization per bound ion or per clamping event.
- **Why it matters** The proposed mechanism is a key part of the paper's novelty. If the mechanism is not convincingly established, the paper becomes primarily a phenomenological report of valence-dependent stability, which is less impactful.
- **Resolution test** Perform additional analyses to test causality, such as mutating the DNA sequence to alter minor-groove geometry, or using simulations with modified cations that cannot clamp. Quantify the energetic contribution of clamping contacts to the overall binding free energy. Provide a direct comparison with RNA under the same simulation conditions to support the claimed contrast.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical robustness
- **Claim pointer** The authors report unpeeling forces and derived free energies for six different cations, with the claim that maximum stability increases monotonically with valence.
- **Evidence pointer** Results and discussion, Fig. 2D, Fig. 3B and C
- **Concern** The number of independent measurements (tethers, molecules, force cycles) is not reported. The representative trace in Fig. 2C shows a single example, and it is unclear how many molecules were measured per condition. The differences in Fmaxe between Na+ (64.52 pN) and Ca2+ (65.21 pN) are small (about 1%), and without error bars or statistical tests, it is not possible to determine whether these differences are significant. The monotonic trend across six cations could be driven by a few outliers.
- **Why it matters** The main experimental claim is a quantitative trend. Without statistical rigor, the trend may not be reproducible or may not reflect a real physical effect.
- **Resolution test** Report the number of independent measurements for each condition, with standard errors or confidence intervals for Fmaxe and ΔGchem. Perform appropriate statistical tests (e.g., ANOVA or pairwise comparisons) to support the claim of a monotonic increase with valence.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Methodological clarity
- **Affected element** Experimental section, MT experiments
- **Evidence pointer** Fig. 2A and B; Method S1 (not provided)
- **Issue** The description of the DNA construct and the tethering geometry is complex and difficult to follow. The role of the 21-bp GC island and the rationale for the two-segment design are not clearly explained in the main text.
- **Required correction** Provide a clearer schematic or step-by-step description of the construct and how the force is applied to the duplex end. Move some details from the SI to the main text if they are essential for understanding the experiment.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Fig. 3A–C
- **Evidence pointer** Results and discussion, Fig. 3
- **Issue** The figures show trends but do not include individual data points or error bars. The reader cannot assess the scatter or the reliability of the reported values.
- **Required correction** Add error bars or shaded confidence intervals to all panels in Fig. 3, and consider showing individual data points as overlaid scatter.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction, Results and discussion
- **Evidence pointer** Introduction, paragraphs 1–2; Results and discussion, final paragraph
- **Issue** The discussion of prior work on polyamine–DNA interactions is brief and does not fully contextualize the novelty of the current findings. The claim that this is the first single-molecule measurement of DNA stability under condensing conditions is not explicitly stated but implied.
- **Required correction** Add a more thorough comparison with prior single-molecule studies of DNA melting and with bulk studies of polyamine effects, clarifying what is new here.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract, Results and discussion
- **Evidence pointer** Abstract, "clamp the minor groove"; Results and discussion, "clamping contacts"
- **Issue** The term "clamping" is used to describe cation-mediated interstrand contacts, but it is not formally defined. It is unclear whether this refers to a specific geometric arrangement or a general electrostatic bridging.
- **Required correction** Define "clamping" operationally in the methods or results section, with a clear criterion based on distances or contacts.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Experimental section, HRM experiments
- **Evidence pointer** Experimental section, HRM experiments
- **Issue** The HRM experiments are described briefly, and the concentration ranges for each cation are not specified in the main text. The reader cannot reproduce the experiments without the SI.
- **Required correction** Provide the concentration ranges for each cation in the main text or a table, and specify the number of replicates.

## Risk / unsupported claims
- The claim that maximum DNA duplex stability increases monotonically with cation valence is not statistically supported because no error bars or replicate numbers are provided for the magnetic tweezers measurements.
- The claim that minor-groove clamping is the mechanistic cause of increased stability is not causally established; it is inferred from correlative simulation and experimental data.
- The comparison with RNA major-groove clamping is made without direct evidence in this work and relies on prior reports that are not critically evaluated.
- The statement that the approach provides an "intrinsic thermodynamic benchmark" is not fully justified, as the free energy extraction depends on model assumptions that are not validated.
- The biological relevance claims in the discussion are speculative and not directly supported by the experimental data presented.