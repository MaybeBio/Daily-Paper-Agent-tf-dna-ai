## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific content, methodological rigor, structural interpretation validity, and consistency of claims with presented evidence
- **Shared manuscript claim summary** The authors present cryo-EM structures of a bacterial phytochrome histidine kinase (PsBphP1) in both Pr and Pfr states, proposing a conformational cascade involving hairpin refolding, PHY domain rotation, S-helix scissoring, and CA domain repositioning that activates autophosphorylation and phosphotransfer to the response regulator AlgB
- **Visible evidence base** Cryo-EM maps at 2.8–3.4 Å resolution for the PSM and S-helix regions, lower resolution maps for the HK bidomain, SEC data, phosphotransfer assays, and AlphaFold/RoseTTAFold predictions
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; PDB validation reports not available; raw cryo-EM map quality metrics (FSC curves, local resolution estimates) not assessable; full experimental replicates and statistical details for kinetic assays not shown

## Reviewer
- **Overall assessment** This manuscript presents a significant advance in understanding bacterial phytochrome signaling by providing near-complete structural models of a full-length dimeric phytochrome histidine kinase in both photostates. The proposed conformational cascade is mechanistically plausible and well-aligned with prior biochemical data. However, the central claims regarding HK domain repositioning rely on lower resolution maps and substantial model building guided by predictions, which limits confidence in the detailed mechanistic conclusions. The phosphotransfer data are convincing but the lack of a stable complex with AlgB raises questions about the physiological relevance of the proposed signaling model. The manuscript is well-written and will interest the phytochrome and two-component signaling communities, but the structural evidence for the key mechanistic steps needs strengthening.

- **Who would be interested in the results, and why** Researchers studying phytochrome photobiology, bacterial two-component signaling systems, histidine kinase mechanisms, and cryo-EM of dynamic protein complexes. The work also has relevance for optogenetics engineering, as understanding the conformational changes that gate kinase activity could inform design of improved light-responsive tools. The proposed mechanism of S-helix scissoring as a conserved signaling relay will be of interest to those studying other phytochrome outputs beyond HKs.

- **Major strengths**
  1. First near-complete structural models of a full-length bacterial phytochrome HK in both photostates, addressing a long-standing gap in the field
  2. High-resolution PSM structures (2.8–3.3 Å) provide confident visualization of the chromophore-binding pocket and hairpin conformations
  3. The proposed conformational cascade integrates prior fragmentary structural data into a coherent mechanistic model
  4. Functional validation through phosphotransfer assays with the cognate response regulator AlgB
  5. The observation of photostate-dependent tetramerization (DoD formation) is novel and potentially functionally relevant

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural interpretation validity
- **Claim pointer** The authors claim that photoconversion to Pfr dislodges the CA domains from their Pr positions, moving the ATP-binding pockets to within 7 Å of the phosphohistidine residue His530, thereby enabling autophosphorylation
- **Evidence pointer** Figures 2c, 4, and Supplementary Figures 5, 10; location not provided for specific residue distances
- **Concern** The central mechanistic claim regarding CA domain repositioning is based on a 4.1 Å focused refinement map and a composite map at 4.4 Å resolution, with the second CA domain not visible in the density. The authors manually docked a RoseTTAFold-predicted CA domain into weak density, which introduces substantial model bias. The 7 Å distance between the ATP γ-phosphate and His530 is a critical quantitative claim that cannot be reliably established at this resolution, particularly when the CA domain placement required manual adjustment. The authors should provide local resolution estimates, cross-validation procedures, and clearly delineate which parts of the model are experimentally constrained versus prediction-based.
- **Why it matters** The proposed activation mechanism hinges on this distance change. If the CA domain positioning is not reliable, the entire model for how light activates kinase activity is called into question. The field needs confident structural information to guide mutagenesis and engineering efforts.
- **Resolution test** Provide local resolution maps for the HK region, perform focused classification to identify distinct CA domain conformations, validate the CA domain placement using independent methods (e.g., cross-linking mass spectrometry, HDX-MS, or mutational analysis with distance constraints), and show that the 7 Å distance is reproducible across multiple map reconstructions and model building strategies.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional relevance of observed oligomeric states
- **Claim pointer** The authors propose that the dimer-of-dimers (DoD) arrangement observed for Pfr is functionally relevant and "might have helped identify novel features of the highly flexible HK bidomains"
- **Evidence pointer** Figure 3, Supplementary Figure 11; SEC data shown in Supplementary Figure 11
- **Concern** The DoD formation is observed at high protein concentrations (0.117–1.17 mg/mL) in a buffer containing 175 mM KSCN, which the authors acknowledge increases kinase activity. The physiological relevance of tetramerization is unclear, and the authors do not demonstrate that DoD formation occurs at physiologically relevant concentrations or in the absence of KSCN. Furthermore, the claim that DoD formation "did not structurally impair" the photoreceptor is based on indirect evidence. The authors should address whether the DoD is a crystallization artifact, a consequence of the high concentrations used, or a genuine signaling state.
- **Why it matters** If the DoD is not physiologically relevant, the structural interpretation of the HK domain arrangement in the Pfr state is compromised. The field needs to know whether the observed tetramer is a functional signaling complex or a concentration-dependent artifact.
- **Resolution test** Perform SEC-MALS or analytical ultracentrifugation across a range of protein concentrations in both KSCN and NaCl buffers to establish the oligomeric equilibrium. Use mutagenesis to disrupt the putative tetramer interface and test whether kinase activity or phosphotransfer is affected. If possible, perform in-cell cross-linking or use a membrane-tethered system to assess oligomeric state under more native conditions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Completeness of mechanistic model
- **Claim pointer** The authors state that "the PSM and its photointerconversion mechanism" are revealed "with strong clarity" and that the models "illustrate how light absorption conformationally translates into accelerated signaling"
- **Evidence pointer** Figures 1, 3, 5; Supplementary Figures 3–5, 7, 9
- **Concern** While the PSM structures are at high resolution, the authors do not provide a quantitative comparison of the conformational changes between Pr and Pfr states. The proposed "conformational cascade" is described qualitatively, without measurements of domain rotations, hinge angles, or displacement magnitudes. The three Pfr conformations (DoD, medial, splayed) are presented but not quantitatively compared to each other or to the Pr state. This limits the ability of readers to assess the significance and reproducibility of the proposed conformational changes.
- **Why it matters** A quantitative description of the conformational changes is essential for understanding the allosteric mechanism and for designing experiments to test it. Without such analysis, the "cascade" model remains largely descriptive.
- **Resolution test** Provide quantitative measurements of domain movements (e.g., rotation angles, translation distances, hinge bending angles) with associated uncertainties. Compare the three Pfr conformations systematically and discuss which features are common versus state-specific. Consider performing principal component analysis or normal mode analysis to identify the dominant motions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Functional validation of proposed mechanism
- **Claim pointer** The authors state that "phosphotransfer assays confirmed our prediction that PsBphP1 effectively modifies PsAlgB via a canonical transmitter kinase reaction, but surprisingly without forming a tight complex either as Pr or Pfr"
- **Evidence pointer** Figure 6; methods section "Autophosphorylation and phosphotransfer"
- **Concern** The phosphotransfer data are presented as confirmation of the structural model, but the connection is indirect. The authors show that PsBphP1 can phosphorylate PsAlgB, but they do not demonstrate that the specific conformational changes proposed in the structural model are responsible for the enhanced kinase activity in the Pfr state. The lack of a stable complex between PsBphP1 and PsAlgB is interesting but raises questions about how phosphotransfer occurs efficiently in vivo. The authors should discuss alternative models, such as a "hit-and-run" mechanism, and consider whether the transient interaction is a general feature of phytochrome HK signaling.
- **Why it matters** The functional data are used to support the structural model, but the connection is not rigorously established. Without direct evidence linking the proposed conformational changes to the observed kinase activity, the mechanistic model remains speculative.
- **Resolution test** Perform mutagenesis targeting residues predicted to be critical for the conformational cascade (e.g., the S-helix hinge, the PHY domain rotation interface, or the CA domain repositioning) and measure the effects on kinase activity and phosphotransfer. Use FRET or other spectroscopic methods to monitor conformational changes in solution and correlate them with kinase activity.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and accessibility
- **Affected element** Figure 2c and related text
- **Evidence pointer** Figure 2c; Results section "Cryo-EM models of PsBphP1 as Pr"
- **Issue** The description of the HK domain placement in the Pr state is difficult to follow. The authors state that the CA domains are "placed on opposite sides of the DHp four-helix bundle and near the connecting turn between DHp helices α1 and α2," but the figure does not clearly show this arrangement, and the reader cannot easily distinguish which parts are experimentally determined versus modeled.
- **Required correction** Add a schematic diagram showing the domain organization and the proposed arrangement of the DHp and CA domains in both Pr and Pfr states. Clearly label which parts of the model are based on experimental density versus prediction. Consider adding a supplementary figure with orthogonal views at different contour levels to help readers understand the confidence in the HK domain placement.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological transparency
- **Affected element** Model building and refinement section
- **Evidence pointer** Methods section "Model building, refinement and validation"
- **Issue** The methods describe using AlphaFold and RoseTTAFold predictions to guide model building, but the specific criteria for when predictions were used versus experimental density are not clearly stated. The authors mention "manual placement" and "adjustment" but do not describe the validation metrics used to assess model quality in the low-resolution regions.
- **Required correction** Provide a more detailed description of the model building strategy, including how the AlphaFold and RoseTTAFold predictions were filtered or weighted, what validation metrics were used (e.g., Q-score, MolProbity, EMRinger), and how the authors ensured that the low-resolution HK domain placement is not over-interpreted. Consider depositing the model with appropriate validation reports.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section, final paragraphs
- **Issue** The authors do not explicitly discuss the limitations of their structural models, particularly the low resolution of the HK domains and the use of prediction-based modeling. Given that the central mechanistic claims depend on these regions, a frank discussion of the uncertainties would strengthen the manuscript.
- **Required correction** Add a paragraph in the Discussion acknowledging the limitations of the HK domain models, the potential for model bias, and the need for higher resolution structures or complementary approaches to validate the proposed conformational changes.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Functional data interpretation
- **Affected element** Figure 6 and related text
- **Evidence pointer** Figure 6b–d; Results section "PsBphP1 interacts transiently with its response regulator AlgB"
- **Issue** The phosphotransfer kinetics are described as having an apparent rate constant of 2.8(±0.3 SE)×10⁻¹ s⁻¹, but the authors do not provide a comparison to other phytochrome HK systems or to the autophosphorylation rate. This makes it difficult to assess whether the observed rate is physiologically relevant.
- **Required correction** Provide context for the measured rate constant by comparing to published values for other phytochrome HKs or two-component systems. If such data are not available, state this explicitly and discuss the implications.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 5
- **Evidence pointer** Figure 5a–f
- **Issue** The conformational changes depicted in Figure 5 are complex and the figure is dense. The reader may struggle to follow the proposed cascade from the figure alone.
- **Required correction** Consider splitting Figure 5 into two panels or adding a schematic summary diagram that outlines the proposed conformational cascade step by step. This would improve accessibility for nonspecialist readers.

## Risk / unsupported claims
- The claim that the CA domain moves to within 7 Å of His530 in the Pfr state is not reliably supported by the presented evidence, given the 4.1–4.4 Å resolution of the HK region and the manual placement of the CA domain.
- The claim that the DoD formation is functionally relevant is not established, as the authors do not demonstrate that tetramerization occurs under physiologically relevant conditions.
- The claim that the "conformational cascade" is a general mechanism for phytochrome HK signaling is speculative, as it is based on a single system and the authors do not provide comparative analysis with other phytochrome HKs.
- The statement that KSCN "did not appreciably disrupt the native 3D structure" is based on indirect evidence (spectral properties and activity assays) and does not rule out subtle structural perturbations that could affect the interpretation of the cryo-EM structures.
- The physiological relevance of the PsBphP1/PsAlgB interaction is not established, as the authors note that the function of this system in P. syringae is unknown.

## Assessment against Nature-style criteria
- **Originality** High. This work provides the first near-complete structural models of a full-length bacterial phytochrome HK in both photostates, addressing a long-standing gap. The proposed conformational cascade is a novel synthesis of prior fragmentary data.
- **Scientific importance** High. Understanding how phytochromes transduce light signals into kinase activity is fundamental to bacterial physiology and has implications for optogenetics. The work will likely influence future studies on phytochrome signaling mechanisms.
- **Interdisciplinary readership** Moderate. The work will primarily interest structural biologists, photobiologists, and those studying two-component signaling. The mechanistic detail may be less accessible to a broader readership, though the abstract is well-written.
- **Technical soundness** Moderate. The high-resolution PSM structures are technically sound, but the central claims regarding HK domain repositioning rely on lower resolution data and prediction-based modeling. The functional assays are appropriate but do not directly test the proposed mechanism.
- **Readability for nonspecialists** Good. The manuscript is clearly written and the figures are generally well-organized. However, the complexity of the conformational cascade and the reliance on structural predictions may be challenging for readers without a structural biology background.

## Risk / unsupported claims
- The claim that the CA domain moves to within 7 Å of His530 in the Pfr state is not reliably supported by the presented evidence, given the 4.1–4.4 Å resolution of the HK region and the manual placement of the CA domain.
- The claim that the DoD formation is functionally relevant is not established, as the authors do not demonstrate that tetramerization occurs under physiologically relevant conditions.
- The claim that the "conformational cascade" is a general mechanism for phytochrome HK signaling is speculative, as it is based on a single system and the authors do not provide comparative analysis with other phytochrome HKs.
- The statement that KSCN "did not appreciably disrupt the native 3D structure" is based on indirect evidence (spectral properties and activity assays) and does not rule out subtle structural perturbations that could affect the interpretation of the cryo-EM structures.
- The physiological relevance of the PsBphP1/PsAlgB interaction is not established, as the authors note that the function of this system in P. syringae is unknown.

## Recommendation posture
Supportive if technical concerns are resolved. The manuscript presents a significant advance with high-quality PSM structures and a plausible mechanistic model. However, the central claims regarding HK domain repositioning require stronger evidence, either through improved resolution of the HK region, independent validation of the CA domain placement, or functional experiments that directly test the proposed conformational cascade. The authors should also address the physiological relevance of the DoD formation and provide a more quantitative description of the conformational changes. With these revisions, the work would be suitable for publication in a high-impact journal.