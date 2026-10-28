## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results and discussion, methods, and figure legends as provided.
- **Assessment boundary** Scientific content, technical soundness, interpretation of results, and support of claims by the presented evidence. Editorial or formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors report the first crystal structure of an apo estrogen receptor α (ERα) ligand binding domain (LBD) from the teleost *Melanotaenia fluviatilis*, revealing a third distinct helix-12 (H12) conformation. They propose a "ternary switch" model in which H12 adopts three discrete states (apo, active, inactive) and is displaced by ligand binding through steric clashes with residues L525, L536, and L540. They further show that oncogenic mutations Y537S and D538G destabilize the apo H12 conformation, providing a structural basis for constitutive activation.
- **Visible evidence base** X-ray crystallography (2.0 Å, PDB: 9MDV), native mass spectrometry, SEC-SAXS, HDX-MS, all-atom MD simulations (5 µs triplicates), Markov state modeling, fluorescence polarization coactivator recruitment assays, evolutionary sequence analysis of 11,547 NR LBD sequences, and structural comparisons with published structures.
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S12, Tables S1–S4) are referenced but not provided. Source data files are not available. The previously published companion study (PDB: 9D8Q) is referenced but not fully described. Coordinates and structure factors for the new apo structure are not independently verified.

## Reviewer
- **Overall assessment** This manuscript presents a potentially significant advance in understanding ERα LBD conformational regulation. The crystal structure of an apo ER LBD has been a long-standing gap in the field, and the proposed ternary switch model is conceptually appealing. However, several technical concerns must be addressed before the case is fully established. The use of a teleost ortholog as a model for human ERα requires stronger validation of functional equivalence, particularly given the modest sequence identity. The HDX-MS data showing no significant change in H12 deuterium uptake between apo and E2-bound states is somewhat counterintuitive given the proposed conformational switch and warrants more detailed discussion. The MD simulation timescales (5 µs) may be insufficient to capture the proposed transitions, and the MSM analysis relies on these trajectories. The evolutionary analysis is interesting but its direct relevance to the mechanistic claims is not fully articulated. Overall, the work is original and likely to be of interest to the nuclear receptor and structural biology communities, but the current evidence does not fully establish the universality of the proposed model.
- **Who would be interested in the results, and why** Structural biologists studying nuclear receptor conformational dynamics; cancer biologists investigating ERα-driven breast cancer and endocrine resistance; medicinal chemists and drug developers working on SERMs/SERDs; and evolutionary biologists interested in nuclear receptor functional diversification. The apo H12 structure fills a critical gap and the ternary switch model provides a new framework for understanding ligand-dependent and -independent ERα regulation.
- **Major strengths** 1) First crystal structure of an apo ER LBD, addressing a long-standing gap in the field. 2) Multi-technique approach (crystallography, HDX-MS, native-MS, SAXS, MD, MSM, FP assays) providing complementary evidence. 3) The ternary switch model is conceptually novel and provides a testable framework. 4) Structural basis for oncogenic mutations Y537S and D538G is clinically relevant. 5) Evolutionary analysis across 11,547 NR sequences adds a broad perspective.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (ortholog validity), R1-M2 (HDX-MS interpretation), R1-M3 (MD/MSM sampling), R1-M4 (evolutionary analysis relevance).
- **Assessment against Nature-style criteria** **Originality:** High. The apo ER LBD structure is novel and the ternary switch model is a new conceptual framework. **Scientific importance:** High for the nuclear receptor and breast cancer fields, with potential therapeutic implications. **Interdisciplinary readership:** Moderate to high. The work bridges structural biology, biophysics, computational biology, and cancer biology. **Technical soundness:** Generally sound but with concerns regarding ortholog validation, HDX-MS interpretation, and MD sampling. **Readability for nonspecialists:** The main text is largely accessible, though some sections (MSM, TICA) may be challenging for non-experts. The figures are well-designed and the schematic models aid comprehension.
- **Recommendation posture** Supportive if technical concerns are resolved. The core structural finding is significant, but the functional equivalence of the teleost ortholog and the interpretation of HDX-MS data require strengthening. The proposed model is plausible but its universality is not yet established from the provided evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Model system validity
- **Claim pointer** The authors state that the rfERα LBD is a suitable model for investigating regulatory mechanisms in human ERα, citing high sequence identity (63.75%) and near-identical LBP, AF2, and H11-H12 regions.
- **Evidence pointer** Figure 1b; Results section "X-ray crystal structure of the apo rfERα LBD reveals a unique H12 conformation"; Introduction.
- **Concern** The manuscript relies on a teleost ortholog to draw conclusions about human ERα regulation, yet the sequence identity is only 63.75% across the LBD. While the authors note conservation of key regions, the functional equivalence is not directly demonstrated. The companion study (PDB: 9D8Q) is referenced for E2-bound rfERα, but the key question is whether the apo H12 conformation observed in rfERα is representative of human ERα. The authors state that human apo ERα was refractory to crystallization, but this does not establish that the rfERα conformation is conserved. The HDX-MS comparison between rfERα and hERα shows similar overall behavior, but this is indirect. The authors should provide additional evidence, such as cross-linking mass spectrometry, solution NMR, or mutagenesis of human ERα residues to test whether the apo conformation is conserved.
- **Why it matters** The central claim of the manuscript is that the apo H12 conformation is a distinct, stable state that is relevant to human ERα biology and disease. If the teleost conformation is not representative, the structural and mechanistic conclusions may not translate to human ERα, undermining the clinical relevance of the findings.
- **Resolution test** Provide direct experimental evidence that the apo H12 conformation is conserved in human ERα, or clearly articulate and justify the limitations of the ortholog model. This could include: (a) mutagenesis of human ERα residues predicted to stabilize the apo conformation and demonstration of constitutive activity; (b) cross-linking or FRET experiments in human ERα consistent with the apo conformation; (c) a more detailed comparative analysis of the apo conformation across ER orthologs.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data interpretation
- **Claim pointer** The authors state that "H12 showed minimal change (<5%) in deuterium uptake/exchange" between apo and E2-bound states, and use this to support the claim that H12 exists in a stable, distinct conformation prior to ligand binding.
- **Evidence pointer** Figure 2d, 2e; Results section "H12 maintains a third discrete conformation in apo rfERα LBD".
- **Concern** The HDX-MS data show no significant difference in H12 deuterium uptake between apo and E2-bound states. The authors interpret this as evidence that H12 is stable in both states. However, this interpretation is problematic. If H12 undergoes a conformational switch from the apo to the active state, one might expect changes in solvent accessibility or hydrogen bonding that would be reflected in HDX-MS. The lack of difference could indicate that (a) H12 is indeed stable in both states, as the authors claim; (b) the HDX-MS peptide coverage or resolution is insufficient to detect local changes; or (c) the conformational change does not significantly alter the hydrogen bonding or solvent accessibility of H12 in a way that HDX-MS can detect. The authors should address these alternative explanations. Additionally, the HDX-MS data are presented as percentage differences, but the statistical analysis and effect sizes for individual peptides are not fully described. The claim that H12 is "stable" in the apo state is also somewhat at odds with the MD simulations showing conformational heterogeneity in the apo state.
- **Why it matters** The HDX-MS data are a key piece of evidence supporting the claim that H12 is in a stable, distinct conformation in the apo state. If this interpretation is incorrect or overstated, the central model is weakened.
- **Resolution test** Provide a more detailed analysis of the HDX-MS data, including per-peptide deuterium uptake plots, confidence intervals, and a discussion of alternative interpretations. Consider whether the HDX-MS resolution is sufficient to detect the proposed conformational differences. If possible, use complementary techniques (e.g., NMR, cross-linking) to validate the stability of the apo H12 conformation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational sampling
- **Claim pointer** The authors use 5 µs all-atom MD simulations (in triplicate) and Markov state modeling to characterize the conformational landscapes of apo and E2-bound rfERα LBD, concluding that H12 maintains a stable conformation in both states.
- **Evidence pointer** Figure 2f–h; Results section "H12 maintains a third discrete conformation in apo rfERα LBD"; Methods section "Markov modelling".
- **Concern** The MD simulations are 5 µs per replicate, which may be insufficient to capture the full conformational landscape of a protein domain, particularly for transitions between distinct H12 states. The MSM analysis relies on these trajectories, and the implied timescales for transitions between metastable states are reported to be on the order of hundreds of microseconds. This is concerning because the simulation length (5 µs) is shorter than the timescales of the transitions being characterized. The MSM may therefore be extrapolating beyond the sampled data. The authors should provide convergence tests, validation of the MSM (e.g., Chapman-Kolmogorov tests are mentioned but not shown), and a discussion of the statistical uncertainty in the MSM predictions. Additionally, the choice of collective variables (pairwise distances between selected residues) may bias the analysis.
- **Why it matters** The MD/MSM analysis is used to support the claim that H12 is stable in the apo state and that the conformational landscape is distinct between apo and E2-bound states. If the sampling is insufficient, the conclusions may not be reliable.
- **Resolution test** Provide evidence of convergence of the MD simulations (e.g., RMSD convergence, replica exchange or enhanced sampling methods). Show the Chapman-Kolmogorov test results and discuss the statistical uncertainty in the MSM. Consider using longer simulations or enhanced sampling techniques to validate the metastable states and transition timescales.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Evolutionary analysis interpretation
- **Claim pointer** The authors state that "residues within this region are poorly conserved between NRs and vary in chemical properties compared to those which form the AF2 binding cleft," supporting the notion that ligand-activation mechanisms vary widely among nuclear receptors.
- **Evidence pointer** Figure 4c, 4d; Results section "Ligand-dependent activation mechanisms are diverse among NRs".
- **Concern** The evolutionary analysis of 11,547 NR LBD sequences is presented as supporting evidence for the diversity of activation mechanisms. However, the analysis is described only briefly, and the specific methods for calculating conservation (Jensen-Shannon divergence) and the statistical significance of the findings are not fully described. The connection between sequence conservation and mechanistic diversity is not direct. Low conservation in a region could indicate functional flexibility, but it could also indicate that the region is simply not under strong selective pressure. The authors should provide more detail on the evolutionary analysis and clarify how it supports the mechanistic claims.
- **Why it matters** The evolutionary analysis is used to contextualize the ternary switch model within the broader NR family. If the analysis is not rigorous or the interpretation is overstated, this weakens the broader implications of the work.
- **Resolution test** Provide a more detailed description of the evolutionary analysis methods, including the alignment procedure, the calculation of JSD, and the statistical significance of the conservation differences. Clarify how the conservation patterns specifically support the claim of diverse activation mechanisms.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1d
- **Evidence pointer** Figure 1d
- **Issue** The description of the side chain interactions in Figure 1d is somewhat brief. The text states that "residues L536 and L540 of the H12 LxxLL motif interact with M343 and T347 (H3), W383 (H5), and L525 (H11) to form a buried hydrophobic cluster," but the figure legend does not clearly indicate which interactions are shown. It would be helpful to label the key residues and interactions directly in the figure or provide a more detailed legend.
- **Required correction** Add labels to Figure 1d indicating the key residues and interactions, or expand the figure legend to describe the specific interactions shown.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** HDX-MS analysis
- **Evidence pointer** Methods section "Hydrogen-deuterium exchange detected by mass-spectrometry"
- **Issue** The methods state that "statistical significance for the differential HDX data is determined by an unpaired t-test for each time point," but the results do not report the number of peptides, the false discovery rate, or the criteria for significance. The volcano plots or similar representations are not shown.
- **Required correction** Provide additional statistical details for the HDX-MS analysis, including the number of peptides analyzed, the significance thresholds, and the false discovery rate. Consider showing volcano plots or similar representations of the differential uptake data.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Fluorescence polarization assays
- **Evidence pointer** Methods section "Fluorescence polarisation coactivator recruitment assays"
- **Issue** The methods describe the FP assay but do not provide details on the protein concentrations used, the peptide probe concentration, or the buffer conditions for the assay. The Kd values are mentioned but not reported in the results.
- **Required correction** Provide the Kd values for the FP assays and include details on the assay conditions, such as protein and probe concentrations, in the methods.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** MD simulation data
- **Evidence pointer** Methods section "Molecular dynamics (MD) simulations"
- **Issue** The methods state that MD simulations were performed but do not provide details on the software version, force field parameters, or the system setup (e.g., box size, water model, ion concentration). The trajectories are not deposited in a public repository.
- **Required correction** Provide full details of the MD simulation setup and consider depositing the trajectories in a public repository (e.g., Zenodo, Figshare) to facilitate reproducibility.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that the apo H12 conformation "partially obscures" the AF2, but the functional significance of this partial obscurement is not fully explained. It would be helpful to clarify whether this partial obscurement is sufficient to prevent coactivator binding or whether it merely reduces affinity.
- **Required correction** Clarify the functional consequence of the partial AF2 obscurement in the abstract or results.

## Risk / unsupported claims
- The claim that the apo H12 conformation is "stable" is supported by crystallography, HDX-MS, and MD, but the HDX-MS interpretation is not fully resolved (see R1-M2) and the MD sampling may be insufficient (see R1-M3).
- The claim that the ternary switch model is universal across ERs and other NRs is not fully supported. The authors acknowledge this limitation, but the evolutionary analysis (R1-M4) does not directly establish universality.
- The claim that Y537S and D538G mutations "disrupt residue contacts critical for stabilising apo H12 conformation" is supported by MD simulations and FP assays, but direct structural evidence of the mutant apo conformations is not provided.
- The functional equivalence of rfERα and hERα is asserted but not directly demonstrated (see R1-M1).
- The statement that "small molecules which can facilitate displacement of the apo H12 conformation and share chemical similarity to the core scaffold may possess SERM- and SERD-like behaviour" is speculative and not directly tested in this manuscript.