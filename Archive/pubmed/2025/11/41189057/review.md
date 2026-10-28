## Review setup
- **Input scope** Full manuscript text including abstract, materials and methods, results, discussion, and conclusions. No supplementary figures or tables were provided beyond references to them in the text.
- **Assessment boundary** Scientific content, methodological rigor, interpretation of results, and support of claims by presented evidence. Not assessed: editorial quality, formatting, or literature completeness beyond what affects the scientific case.
- **Shared manuscript claim summary** The authors report the NMR solution structure of the Sox2 DNA-binding domain (residues 31–127) in its free state, showing that the helical fold matches the DNA-bound conformation. They propose that DNA binding proceeds via conformational selection rather than induced fit, supported by relaxation dispersion data showing a minor partially unfolded state, thermostability measurements, and MD simulations.
- **Visible evidence base** Main text figures 1–8 (referenced), Table 1 (structural statistics), Supplementary Figures S1–S23 and Tables S1–S5 (referenced but not provided), BMRB ID 34988, PDB ID 9QPF.
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S23, Tables S1–S5) were not provided. These include key data: melting curves, relaxation dispersion curves, MD simulation analyses, structural validation metrics, and the full structural statistics table. Without these, several quantitative claims cannot be independently verified.

## Reviewer
- **Overall assessment** This manuscript presents a technically rigorous NMR study of the Sox2 HMG domain in its free state, with the central claim that the folded conformation is pre-formed and that DNA binding occurs via conformational selection. The experimental work appears carefully executed, and the combination of NMR structure determination, relaxation dispersion, thermostability measurements, and MD simulations is appropriate and complementary. The main conclusions are plausible and would be of interest to the transcription factor and structural biology communities. However, the case for conformational selection over induced fit rests on several inferences that are not fully established by the data presented in the main text, and the absence of supplementary materials limits verification of key quantitative claims. The distinction between the proposed model and previously published work on related HMG proteins needs sharper articulation.

- **Who would be interested in the results, and why** Structural biologists studying DNA-binding proteins, particularly those in the HMG family, will be interested in the free-state structure and its comparison to the bound form. Researchers studying pioneer transcription factors and their mechanisms of chromatin engagement will find the conformational selection model relevant to understanding how these factors search for and bind their target sites. The methodological combination of NMR relaxation dispersion with MD simulations will interest biophysicists working on protein dynamics and folding. The thermostability data and the role of electrostatic frustration in protein stability may also appeal to protein engineers and computational chemists.

- **Major Strengths**
  1. The study addresses a significant and unresolved question: whether Sox2 DNA binding involves conformational selection or induced fit. This has implications for understanding pioneer factor function.
  2. The experimental design is comprehensive, combining multiple orthogonal techniques (NMR structure determination, relaxation dispersion, thermostability assays, MD simulations) to address the question from different angles.
  3. The NMR structure determination appears carefully executed, with appropriate use of RDC restraints and validation against an independent automated pipeline (ARTINA).
  4. The observation that the free-state fold matches the DNA-bound state, with a well-defined hydrophobic core, is a clear and important result.
  5. The identification of a minor partially unfolded state via CPMG relaxation dispersion, with population consistent with thermostability data, is a strong piece of evidence.
  6. The authors are appropriately cautious in several places, acknowledging limitations in assigning the nature of the minor state and the need for kinetic data to fully delineate the binding mechanism.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for central claim
- **Claim pointer** The authors claim that "DNA binding may thus primarily proceed via conformational selection rather than an induced fit mechanism" and that the data support a "conformational selection model in which the DNA-binding interface is pre-formed in the free-state Sox2 HMG domain."
- **Evidence pointer** Results sections on CPMG relaxation dispersion, thermostability, and MD simulations; Figure 4; Supplementary Figures S13–S15, S23
- **Concern** The central mechanistic claim of conformational selection versus induced fit is not directly tested by the experiments presented. The authors demonstrate that the free state is predominantly folded and that a minor partially unfolded state exists, and that DNA binding quenches this state. However, this is consistent with both conformational selection (the bound conformation is pre-existing and selected) and induced fit (the bound conformation is achieved after initial encounter, with the unfolded state being irrelevant to the binding pathway). The authors acknowledge that "delineation of the exact contribution of conformation selection and induced fit in binding requires detailed knowledge of the kinetic reaction rate constants," but then proceed to make a strong claim based on model calculations presented only in supplementary material. The model calculations (Supplementary Fig. S23) are not described in sufficient detail in the main text to evaluate their assumptions. The claim that the "flux through conformational selection pathway exceeds that through the induced fit pathway" requires the kinetic parameters of both pathways, which are not measured. The authors should either soften the claim to be consistent with the evidence, or provide direct kinetic evidence distinguishing the two mechanisms.
- **Why it matters** The title and abstract make a definitive claim about conformational selection. If the evidence does not distinguish between the two mechanisms, the central message of the paper is overstated. This distinction matters because the field has debated the binding mechanisms of HMG proteins, and a definitive answer requires kinetic data.
- **Resolution test** The authors should either (a) present direct kinetic evidence (e.g., stopped-flow or relaxation kinetics) that distinguishes conformational selection from induced fit, (b) substantially soften the mechanistic claim to state that the data are "consistent with" conformational selection but do not exclude induced fit, or (c) provide a more detailed and transparent description of the model calculations in the main text, including all assumptions and parameters, so that the claim can be evaluated.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Comparison to prior work
- **Claim pointer** The authors state that "the PDB contains an unpublished solution structure of the free Sox2 HMG domain (PDB: 2LE4), in which the relative orientation of the three helices is significantly different compared to the DNA-bound state" and use this to motivate their study.
- **Evidence pointer** Introduction, Results section on structure comparison; Figure 2C
- **Concern** The authors report a 3.7 Å backbone RMSD between their structure and 2LE4, and a poor Q-factor (0.76) when 2LE4 is tested against their RDC data. However, the authors do not provide a detailed analysis of why 2LE4 differs. They suggest an "assignment issue of the aromatic residues in 2LE4" but do not provide direct evidence for this claim. The comparison to 2LE4 is important because it directly contradicts a previously deposited structure, and the authors should provide a more thorough analysis of the differences. Is it possible that 2LE4 represents a genuinely different conformation that is relevant to the binding mechanism? The authors' conclusion that 2LE4 is simply wrong needs stronger support. Additionally, the authors should compare their structure to other HMG domain structures, both free and bound, to establish the generality of their finding.
- **Why it matters** The discrepancy with 2LE4 is a key motivation for the study. If the authors cannot convincingly explain why 2LE4 is incorrect, readers may question the reliability of their own structure. A thorough comparison would strengthen the paper and help resolve the discrepancy.
- **Resolution test** Provide a detailed residue-by-residue comparison of the authors' structure with 2LE4, including analysis of the putative aromatic assignment errors. Show that the authors' structure is consistent with all experimental data, including NOESY spectra, and that 2LE4 is not. If possible, re-examine the 2LE4 data to identify the specific assignment errors.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative support for claims
- **Claim pointer** The authors claim that "the folded, free protein coexists in dynamic equilibrium with partially unfolded states" and that the population of the unfolded state is approximately 1% at 293 K, increasing to 41% at 310 K.
- **Evidence pointer** Results sections on CPMG relaxation dispersion and thermostability; Figures 1E, 4; Supplementary Figures S3, S13–S15
- **Concern** The population of the unfolded state at 310 K (41%) is derived from thermostability measurements, while the CPMG data at 293 K report a minor state population of 0.69–1.20%. The authors should clarify how these two measurements are reconciled. The thermostability data are fit to a two-state unfolding model, but the CPMG data suggest multiple minor states (two groups with different exchange parameters). The relationship between the "partially unfolded states" detected by CPMG and the "unfolded state" detected by thermostability is not clearly established. Are these the same species? The authors state that the minor state "resembles a partially unfolded molecule rather than a globally unfolded state," but the thermostability analysis assumes a two-state global unfolding. This inconsistency needs to be addressed. Additionally, the extrapolation of the unfolded population to 310 K relies on the fitted thermodynamic parameters, which are not shown in the main text.
- **Why it matters** The population of the unfolded state at physiological temperature is a key parameter in the proposed model. If the relationship between the CPMG-detected minor state and the thermodynamically unfolded state is not clear, the quantitative basis of the model is weakened.
- **Resolution test** Provide a clear description of how the CPMG-detected minor states relate to the thermally unfolded state. Show the fitted thermodynamic parameters and the uncertainty in the extrapolated population at 310 K. If the CPMG and thermostability data report on different processes, state this explicitly and discuss the implications for the model.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of MD simulations
- **Claim pointer** The authors state that "molecular dynamics simulations support stable folding of HMG domain and DNA binding impact" and use MD to support the experimental findings.
- **Evidence pointer** Results section on MD simulations; Figure 6; Supplementary Tables S5
- **Concern** The MD simulations are described as supporting the experimental results, but the specific contributions of the simulations are not clearly articulated. What new information do the simulations provide beyond the experimental data? The authors mention RMSF analysis and hydrogen bond occupancy for H67 and H101, but the connection to the conformational selection model is not explicit. The simulations appear to be used primarily as confirmation of experimental findings rather than as independent tests of the model. The authors should clarify what specific predictions from the simulations were tested experimentally, or what the simulations add to the mechanistic understanding.
- **Why it matters** The inclusion of MD simulations suggests they provide additional insight. If they are merely confirmatory, the authors should state this. If they provide unique information (e.g., about the conformational landscape or the pathway of binding), this should be made explicit.
- **Resolution test** Clearly state the specific hypotheses tested by the simulations and how the simulation results inform the interpretation of the experimental data. If the simulations are confirmatory, state this and explain why they were included.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract, Discussion section
- **Issue** The term "conformational selection" is used in the title and abstract, but the authors do not define what they mean by this in the context of their system. The term can have different meanings in different contexts (e.g., selection of a pre-existing conformation vs. population shift). The authors should clarify their usage.
- **Required correction** Define "conformational selection" as used in this study, and distinguish it from "induced fit" in the context of the Sox2–DNA interaction.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of reporting
- **Affected element** Methods section on MD simulations
- **Evidence pointer** Methods section, MD simulations subsection
- **Issue** The description of the MD simulations lacks some details that would be needed for reproducibility, such as the specific version of the force field parameters, the water model details, and the analysis tools used. Some of this information is provided, but the level of detail is inconsistent with the experimental methods.
- **Required correction** Provide a more complete description of the MD simulation parameters, including any relevant citation for the force field parameters and analysis tools.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of thermostability data
- **Affected element** Results section on thermostability
- **Evidence pointer** Figure 1B–E, Supplementary Figure S3
- **Issue** The authors report that increasing salt concentration increases the melting temperature, but the mechanism is not discussed. Is this due to screening of electrostatic repulsion, as suggested later in the Discussion, or could there be other effects (e.g., on water activity)?
- **Required correction** Briefly discuss the possible mechanisms for the salt-dependent stabilization, or state that the mechanism is not fully understood.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation of structural statistics
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** The structural statistics table is referenced but not shown in the provided text. The authors should ensure that the table includes all relevant validation metrics (e.g., Ramachandran plot statistics, RMSD from ideal geometry) and that the values are within acceptable ranges.
- **Required correction** Ensure Table 1 is complete and includes all standard validation metrics for NMR structures.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The authors do not discuss the potential limitations of using a truncated construct (residues 31–127) rather than the full-length protein. The N- and C-terminal IDRs are longer in the full-length protein, and the truncation may affect the conformational behavior.
- **Required correction** Briefly discuss the potential impact of the construct design on the conclusions, and whether the findings are likely to extend to the full-length protein.

## Risk / unsupported claims
1. The claim that DNA binding proceeds "primarily via conformational selection" is not directly supported by the experimental data, which do not include kinetic measurements that would distinguish conformational selection from induced fit. The model calculations in Supplementary Fig. S23 are not described in sufficient detail to evaluate.
2. The claim that the 2LE4 structure is incorrect due to "an assignment issue of the aromatic residues" is not directly demonstrated. The authors should provide evidence for this specific claim.
3. The relationship between the CPMG-detected minor states and the thermally unfolded state is not established. The authors refer to "partially unfolded states" in the CPMG analysis but "unfolded state" in the thermostability analysis, without clarifying whether these are the same species.
4. The statement that "a high local concentration of charges, either from salt or from DNA, is crucial in screening the intramolecular repulsion" is presented as a conclusion, but the data show correlation, not causation. The mechanism is inferred, not demonstrated.
5. The claim that the findings "may be relevant for other pTFs" is speculative and not supported by data on other pTFs.

## Assessment against Nature-style criteria
- **Originality** The study provides the first NMR structure of the free Sox2 HMG domain and challenges the previously deposited structure (2LE4). The application of relaxation dispersion to study conformational dynamics in this system is novel. However, the concept of conformational selection in DNA-binding proteins is well established, and the finding that a folded domain is pre-formed is not entirely unexpected. The originality lies primarily in the specific system and the combination of methods.
- **Scientific importance** The question of how pioneer transcription factors recognize their target sites is of significant importance. The finding that the Sox2 HMG domain is pre-folded and that binding involves conformational selection has implications for understanding pioneer factor function. However, the importance is somewhat limited by the lack of direct kinetic evidence for the proposed mechanism.
- **Interdisciplinary readership** The work will primarily appeal to structural biologists, biophysicists, and researchers studying transcription factor mechanisms. The broader chromatin and gene regulation community may find the implications for pioneer factor function of interest, but the technical nature of the NMR analysis may limit accessibility.
- **Technical soundness** The NMR methodology appears sound, with appropriate use of modern techniques including RDC measurements and relaxation dispersion at high field. The structure determination is validated against an independent automated pipeline. The MD simulations are appropriately designed and analyzed. However, the lack of supplementary materials limits full assessment of technical quality.
- **Readability for nonspecialists** The manuscript is generally well-written and the main findings are presented clearly. However, the Discussion section assumes familiarity with the conformational selection versus induced fit debate, and the significance of the findings for a broader audience could be more explicitly stated. The abstract is accessible, but the mechanistic claims may be overstated relative to the evidence.

## Recommendation posture
Supportive if technical concerns are resolved. The manuscript presents a technically sound NMR study with potentially important implications for understanding Sox2 DNA binding. However, the central mechanistic claim of conformational selection is not fully established by the presented evidence, and the discrepancy with the 2LE4 structure requires more thorough analysis. The authors should either provide direct kinetic evidence for the proposed mechanism or substantially temper their claims. The manuscript would be suitable for publication in a specialized structural biology or nucleic acids journal, but the strength of the conclusions needs to be aligned with the evidence.