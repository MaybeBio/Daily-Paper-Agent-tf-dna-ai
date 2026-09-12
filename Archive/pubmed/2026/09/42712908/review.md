## Review setup
- **Input scope** Full manuscript
- **Assessment boundary** The manuscript as provided, including all sections, figures, and tables described in the text. No supplementary material was available for review.
- **Shared manuscript claim summary** The authors claim that the FDA-approved drugs lansoprazole and nitazoxanide are functional inhibitors of the orphan nuclear receptor NR2F2, and that their antiproliferative effects in the gastric cancer cell line GCIY are mediated through NR2F2-dependent mechanisms, based on a combination of computational predictions, luciferase reporter assays, and siRNA-mediated silencing experiments.
- **Visible evidence base** Computational: SiteMap, blind docking, molecular docking (Glide XP), molecular dynamics (3x500 ns replicas), BPMD, MM-GBSA, virtual screening of FDA library. Experimental: NR2F2-specific NanoLuc reporter assay in HeLa cells, SRB and CellTiter-Glo proliferation assays in GCIY cells, siRNA-mediated NR2F2 silencing with Western blot validation.
- **Missing materials affecting confidence** Supplementary Tables S1 and S2, Supplementary Figure S1, and the full supplementary material were not provided. Raw data for dose-response curves (e.g., IC50 values, exact n numbers for each experiment) are not reported. The complete interaction profiles for all identified ligands (Table 3) are referenced but not fully visible in the provided text. The authors state that raw data will be made available upon request, but no data repository link is provided.

## Reviewer
- **Overall assessment** This manuscript presents a computational and experimental workflow to identify FDA-approved drugs as potential NR2F2 inhibitors, with a focus on repurposing for gastric cancer. The study is well-structured and the combination of in silico and in vitro approaches is appropriate. However, several critical experimental gaps prevent the core claims from being fully supported. The most significant issues are the lack of direct binding evidence (e.g., SPR, ITC, or cellular thermal shift assay), the absence of selectivity data against other NR2F family members (NR2F1, NR2F6), and the incomplete characterization of the reporter assay (e.g., no demonstration that the compounds directly engage the LBD rather than acting through indirect signaling pathways). The siRNA rescue experiments are a strength, but the effect size is modest and the statistical framework is incompletely described. The manuscript would benefit from additional biophysical and selectivity data before the repurposing claim can be considered established.
- **Who would be interested in the results, and why** Researchers in nuclear receptor biology, drug repurposing, and gastric cancer pharmacology would be interested. The identification of clinically used drugs as NR2F2 modulators provides potential starting points for therapeutic development, and the computational workflow may be of interest to medicinal chemists. The study also contributes to the growing evidence that NR2F2 is a ligandable orphan receptor.
- **Major strengths** 1. The study employs a multi-layered computational approach (SiteMap, docking, MD, BPMD, MM-GBSA) to characterize two putative binding sites on NR2F2, which is methodologically sound. 2. The use of an NR2F2-specific luciferase reporter assay with appropriate controls (NR2F6, LBD-deleted NR2F2) is a strong feature for functional validation. 3. The siRNA-mediated silencing experiments provide a direct test of NR2F2 dependence for the antiproliferative effects of the compounds. 4. The focus on FDA-approved drugs is clinically relevant and aligns with drug repurposing strategies.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Experimental validation – binding
    - **Claim pointer** The authors claim that lansoprazole, nitazoxanide, lapatinib, and glyburide are "functional interactors" of NR2F2 and that lansoprazole and nitazoxanide exert antiproliferative effects via NR2F2.
    - **Evidence pointer** Results – Experimental validation; Discussion; Conclusion
    - **Concern** The manuscript lacks any direct biophysical or biochemical evidence that the identified compounds bind to the NR2F2 protein. The entire claim of "functional interaction" rests on a luciferase reporter assay, which measures transcriptional output, not direct binding. The authors acknowledge this limitation in the conclusion ("Future investigations using dedicated biophysical binding assays... will be required"), but the central claim of the manuscript—that these compounds are NR2F2 inhibitors—is not supported without such evidence. The reporter assay could be influenced by off-target effects, indirect signaling pathways, or compound-mediated modulation of co-regulators. The authors do not demonstrate that the compounds bind to the NR2F2 LBD, nor do they provide evidence that the observed reporter modulation is a direct consequence of LBD occupancy.
    - **Why it matters** Without direct binding data, the mechanism of action remains speculative. The compounds could be acting through other known targets (e.g., lapatinib inhibits EGFR/HER2, glyburide targets K_ATP channels, lansoprazole inhibits H+/K+-ATPase, nitazoxanide has multiple proposed mechanisms). The claim of "repurposing as NR2F2 inhibitors" requires evidence that the compounds physically engage the receptor. This is a fundamental requirement for a study that nominates specific molecules as NR2F2-targeted agents.
    - **Resolution test** Provide direct binding data using a biophysical method such as surface plasmon resonance (SPR), isothermal titration calorimetry (ITC), or a cellular thermal shift assay (CETSA) for at least lansoprazole and nitazoxanide. Alternatively, a radioligand or fluorescent probe displacement assay could be used. The binding affinity (Kd or Ki) should be reported. If direct binding is not feasible, the authors should clearly reframe the claims to state that the compounds "modulate NR2F2-dependent transcription" rather than "bind to" or "inhibit" NR2F2.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Selectivity
    - **Claim pointer** The authors claim that the compounds are NR2F2 inhibitors, but the study does not assess selectivity against the closely related family members NR2F1 and NR2F6.
    - **Evidence pointer** Results – Luciferase assays; Discussion
    - **Concern** The luciferase reporter assay includes a control showing that NR2F6 does not activate the reporter, and that an NR2F2 LBD-deleted derivative is inactive. However, the authors do not test whether the identified compounds modulate the activity of NR2F1 or NR2F6 in a comparable reporter assay. Given the high sequence homology between NR2F1 and NR2F2 (98% DBD, 96% LBD), it is plausible that the compounds could also interact with NR2F1. Without selectivity data, the claim that these compounds are "NR2F2 inhibitors" is overstated. They could be pan-NR2F modulators.
    - **Why it matters** Selectivity is a critical parameter for any chemical probe or therapeutic candidate. If the compounds also modulate NR2F1 or NR2F6, the observed antiproliferative effects in GCIY cells could be mediated through multiple NR2F family members, undermining the specificity of the NR2F2 silencing experiments. The authors' conclusion that the effects are "NR2F2-dependent" is weakened without evidence that the compounds do not affect other family members.
    - **Resolution test** Perform luciferase reporter assays for NR2F1 and NR2F6 using the same or analogous reporter constructs, testing the four hit compounds at the same concentrations used in the NR2F2 assay. If NR2F1 or NR2F6 reporters are not available, the authors should at minimum acknowledge this limitation and discuss the potential for cross-reactivity. Alternatively, demonstrate that siRNA-mediated silencing of NR2F1 or NR2F6 does not affect the antiproliferative response to the compounds.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Experimental design – reporter assay
    - **Claim pointer** The authors claim that the reporter assay is "NR2F2-specific" and that the LBD is required for transactivation.
    - **Evidence pointer** Results – Figure 14; Methods – Luciferase assays
    - **Concern** The reporter assay uses a single NR2F2 response element from the NGF1A promoter. While the authors show that NR2F6 does not activate this reporter, and that an LBD-deleted NR2F2 is inactive, the assay does not demonstrate that the compounds directly engage the LBD. The LBD-deleted construct lacks the entire LBD, which could affect protein stability, nuclear localization, or DNA binding, not just ligand responsiveness. A more rigorous control would be to test a point mutant in the predicted binding pocket (e.g., Arg385Ala) that is predicted to disrupt compound binding but preserve overall LBD structure. Additionally, the authors do not report whether the compounds affect the activity of the LBD-deleted construct, which would help rule out LBD-independent effects.
    - **Why it matters** The central mechanistic claim of the paper is that the compounds modulate NR2F2 activity through LBD binding. The current controls are insufficient to exclude the possibility that the compounds act through other domains of NR2F2 (e.g., the DBD or N-terminal domain) or through indirect effects on co-regulators that are independent of LBD engagement. This weakens the link between the computational predictions (which focus on LBD binding) and the functional data.
    - **Resolution test** 1. Test the compounds in the reporter assay using the LBD-deleted NR2F2 construct. If the compounds still modulate reporter activity, this would indicate an LBD-independent mechanism. 2. Generate and test a point mutant in the predicted binding site (e.g., Arg385Ala for Site 1) to demonstrate that compound activity is dependent on the predicted binding pocket. 3. Alternatively, perform a competition experiment with a known LBD-binding ligand (e.g., 1-deoxysphingolipids) to show that the compounds compete for the same binding site.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Data presentation and statistics
    - **Claim pointer** The authors claim that lansoprazole and nitazoxanide exert antiproliferative effects that are "mitigated by NR2F2 silencing."
    - **Evidence pointer** Results – Figure 15; Methods – Proliferation assays
    - **Concern** The description of the proliferation and siRNA experiments is insufficiently detailed. The authors state that "dose–response analysis performed in the presence of NR2F2 siRNAs revealed a reduced ability of the compounds to inhibit cell growth across all effective concentrations tested," but the exact concentrations tested, the number of independent experiments (n), and the statistical test used for the comparison between siRNA and control conditions are not clearly reported. The figure legend for Figure 15 is not provided in the manuscript text, making it impossible to assess the data. The authors state that "two replicates were performed for each experimental point" for the luciferase assay, but the number of replicates for the proliferation assays is not stated. The use of a two-tailed unpaired Student's t-test is mentioned, but it is unclear whether this was applied to the siRNA comparison or only to the compound vs. vehicle comparison.
    - **Why it matters** The siRNA rescue experiment is the key experiment supporting the claim that the antiproliferative effects are NR2F2-dependent. Without clear reporting of the experimental design, sample size, and statistical analysis, the robustness of this conclusion cannot be evaluated. The modest effect size (the text states "mitigated" but does not quantify the degree of rescue) further underscores the need for rigorous statistical reporting.
    - **Resolution test** 1. Clearly report the number of independent biological replicates (n) for each proliferation experiment. 2. Provide the exact concentrations tested for each compound. 3. Report the statistical test used for the siRNA vs. control comparison (e.g., two-way ANOVA with post-hoc test) and the resulting p-values. 4. Quantify the degree of rescue (e.g., "NR2F2 silencing reduced the antiproliferative effect by X% at Y µM concentration"). 5. Include the figure legend for Figure 15 in the manuscript text.

    - **Concern ID** R1-M5
    - **Severity** Major
    - **Blocking** No
    - **Axis** Computational validation – binding site relevance
    - **Claim pointer** The authors claim that two binding sites (Site 1 and Site 2) on the NR2F2 LBD are druggable and that CIA1 binds to both.
    - **Evidence pointer** Results – SiteMap, Molecular docking, Molecular dynamics
    - **Concern** The computational analysis identifies two putative binding sites, but the biological relevance of Site 2 is unclear. The authors show that CIA1 binds to both sites in silico, but there is no experimental evidence that Site 2 is functionally relevant for NR2F2 modulation. The MM-GBSA calculations show similar binding energies for both sites, but the BPMD data for Site 2 show a PoseScore of 2.394 for the docked pose (above the 2 Å threshold for stability) and a CompScore of 2.674 for the MD pose, which is higher than the Site 1 CompScore of -1.238. This suggests that the Site 2 binding mode may be less stable. The authors do not discuss whether the identified FDA compounds are predicted to bind to Site 1, Site 2, or both. The virtual screening results indicate that six compounds were identified for Site 1 and two for Site 2, but the experimental validation focuses on the Site 1 compounds. The role of Site 2 in the observed biological effects is not addressed.
    - **Why it matters** If the compounds are predicted to bind to different sites, the mechanism of action could be complex and site-dependent. The lack of experimental validation for Site 2 leaves a gap in the computational model. Furthermore, if the compounds bind to Site 1, the authors should discuss whether Site 2 is a genuine allosteric site or an artifact of the apo-structure. The alignment with RXR-gamma (Supplementary Table S1) suggests that Site 1 is near the canonical ligand-binding pocket, but Site 2 may be a non-canonical site. The authors should clarify the functional significance of Site 2.
    - **Resolution test** 1. Clearly state which binding site(s) each of the four hit compounds is predicted to bind to. 2. If Site 2 is considered a genuine binding site, provide experimental evidence for its functional relevance (e.g., by testing a Site 2-selective compound or by mutating key residues in Site 2 and assessing the effect on compound activity). 3. Alternatively, acknowledge that the role of Site 2 is currently speculative and focus the claims on Site 1.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Data presentation
    - **Affected element** Figure 15
    - **Evidence pointer** Results – RNA interference experiments
    - **Issue** The figure legend for Figure 15 is not included in the manuscript text. The description of the figure in the results section is insufficient to interpret the data. The authors refer to "Figure 15B (left, upper panel)" and "Figure 15B, right, upper panel" but the layout of the figure is not described.
    - **Required correction** Provide a complete figure legend for Figure 15, including a description of each panel, the axes labels, the meaning of error bars, and the statistical annotations.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Reproducibility
    - **Affected element** Methods – Luciferase assays
    - **Evidence pointer** Methods – Luciferase assays
    - **Issue** The authors state that "two replicates were performed for each experimental point" for the luciferase assay. This is a very low number of replicates. For a dose-response curve, at least three independent biological replicates (each with technical duplicates or triplicates) are standard.
    - **Required correction** Clarify whether the "two replicates" refer to technical or biological replicates. If they are biological replicates, the authors should acknowledge the limited statistical power. Ideally, additional replicates should be performed.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Data presentation
    - **Affected element** Results – Virtual screening
    - **Evidence pointer** Results – Virtual screening and FDA compounds repurposing
    - **Issue** The authors list eight compounds identified from the virtual screening (six for Site 1, two for Site 2) but only four (lapatinib, glyburide, nitazoxanide, lansoprazole) are tested in the reporter assay. The rationale for selecting these four over the others (ticagrelor, aliskiren, pentostatin, ribavirin) is not clearly stated. Aliskiren is later used as a negative control, but the basis for its selection as a negative control is not explained.
    - **Required correction** Provide a clear rationale for why only four of the eight compounds were selected for experimental testing. Explain why aliskiren was chosen as a negative control (e.g., it was predicted to bind but did not modulate reporter activity in preliminary tests).

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Results – Molecular dynamics
    - **Evidence pointer** Results – Stability analysis
    - **Issue** The authors state that "the systems exhibited an RMSD of approximately 4.4 Å for the system with CIA1 bound to Site 1 and 4.0 Å for the system with CIA1 bound to Site 2." An RMSD of 4-4.5 Å for the Cα atoms of a protein of this size is relatively high and may indicate significant conformational changes or drift. The authors should comment on whether this is expected for an apo-structure or if it indicates instability.
    - **Required correction** Add a brief discussion of the observed RMSD values. Compare them to typical RMSD values for MD simulations of nuclear receptor LBDs. If the high RMSD is due to loop flexibility, this should be stated.

    - **Concern ID** R1-m5
    - **Severity** Minor
    - **Axis** Completeness
    - **Affected element** Methods – Molecular dynamics
    - **Evidence pointer** Methods – Molecular dynamics and MM-GBSA
    - **Issue** The authors state that "Three Na+ were added to neutralize charges." The total charge of the system should be calculated and reported. The number of counterions should be explicitly justified.
    - **Required correction** Report the total charge of the protein-ligand complex and the number of counterions added to achieve neutrality.

    - **Concern ID** R1-m6
    - **Severity** Minor
    - **Axis** Data presentation
    - **Affected element** Results – BPMD
    - **Evidence pointer** Results – Binding pose metadynamics (BPMD)
    - **Issue** The BPMD results are reported as single values (e.g., PoseScore of 4.063 for the docked pose in Site 1). For 10 independent simulations, the mean and standard deviation (or range) should be reported, not just a single value.
    - **Required correction** Report the BPMD scores as mean ± SD or as a range across the 10 independent simulations.

    - **Concern ID** R1-m7
    - **Severity** Minor
    - **Axis** Clarity
    - **Affected element** Results – Molecular dynamics
    - **Evidence pointer** Results – Residues mobility analysis
    - **Issue** The authors state that "the average RMSF values of these residues on Site 2 are lower than 1 Å: Leu215 (0.99 Å), Arg218 (0.93 Å), Met219 (0.86 Å), Ser222 (0.84 Å), Asn256 (0.63 Å) and Cys260 (0.90 Å)." These values are very low and may indicate that the binding site is rigid. The authors should discuss whether this is expected for a binding site in an apo-structure or if it suggests that the site is pre-organized for ligand binding.
    - **Required correction** Add a brief comment on the implications of the low RMSF values for the binding site dynamics.

    - **Concern ID** R1-m8
    - **Severity** Minor
    - **Axis** Reproducibility
    - **Affected element** Methods – Cell cultures
    - **Evidence pointer** Methods – Cell cultures and chemical compounds
    - **Issue** The GCIY cell line is described as "RCB0555, Riken." The authors should confirm that the cell line was authenticated (e.g., by STR profiling) and tested for mycoplasma contamination.
    - **Required correction** State whether the GCIY cell line was authenticated and tested for mycoplasma. If not, this should be noted as a limitation.

- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of direct binding evidence), R1-M2 (lack of selectivity data against NR2F1/NR2F6), R1-M3 (insufficient controls in the reporter assay to demonstrate LBD-dependent mechanism), R1-M4 (incomplete reporting of proliferation and siRNA experiments).

## Risk / unsupported claims
- The claim that lansoprazole, nitazoxanide, lapatinib, and glyburide are "functional interactors" or "inhibitors" of NR2F2 is not supported by direct binding evidence. The data only support that these compounds modulate NR2F2-dependent reporter activity and that the antiproliferative effects of lansoprazole and nitazoxanide are partially dependent on NR2F2 expression. The term "inhibitor" implies direct binding and functional antagonism, which has not been demonstrated.
- The claim that the compounds bind to the predicted binding sites (Site 1 and/or Site 2) is unsupported by experimental data. The computational predictions are plausible but require biophysical validation.
- The claim that the antiproliferative effects of lansoprazole and nitazoxanide are "mediated through NR2F2-dependent mechanisms" is partially supported by the siRNA data, but the effect size is modest and the possibility of additional, NR2F2-independent mechanisms cannot be excluded.
- The claim that the reporter assay is "NR2F2-specific" is supported by the NR2F6 and LBD-deleted controls, but the assay has not been validated against NR2F1, which shares high sequence homology with NR2F2.
- The claim that Site 2 is a functionally relevant binding site is not supported by any experimental data.