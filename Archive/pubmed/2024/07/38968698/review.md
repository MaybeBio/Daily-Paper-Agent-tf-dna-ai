## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure references
- **Assessment boundary** Scientific content, technical soundness, claims versus evidence, and suitability for a Nature-style journal
- **Shared manuscript claim summary** The authors characterize a 1,2-propanediol-responsive transcription factor (PocR) from Salmonella typhimurium in E. coli, identify its limited operational and dynamic ranges, dissect its inducer-binding and RNAP-interaction mechanisms using AlphaFold and mutagenesis, engineer variants with altered inducer specificity (glycerol) and improved dynamic range (PocR-ARE), and convert PocR into a repressor via promoter engineering to create a bifunctional regulation system
- **Visible evidence base** Figures 1–6 and Supplementary Figures S1–S5 as referenced; methods section; no raw data, plasmid maps, or sequence files provided
- **Missing materials affecting confidence** Raw fluorescence data, plasmid maps, full promoter sequences, AlphaFold structure coordinates, docking parameters, statistical analysis details, and strain/plasmid tables (referenced as Supporting Information Table 1 but not provided)

## Reviewer
- **Overall assessment** This manuscript presents a systematic and well-executed study on the characterization and engineering of a transcription factor-based biosensor for 1,2-propanediol. The work addresses a genuine gap in the biosensor repertoire for short-chain alcohols and demonstrates a logical progression from characterization to mechanism dissection to rational engineering. The engineering outcomes, particularly the PocR-ARE variant with improved dynamic and operational ranges and the conversion of an activator to a repressor, are useful contributions. However, several technical concerns regarding data presentation, statistical rigor, and mechanistic claims need to be addressed before the case is fully established.
- **Who would be interested in the results, and why** Researchers in synthetic biology, metabolic engineering, and biosensor development would be the primary audience. Those working on dynamic regulation of metabolic pathways, high-throughput screening for strain improvement, and engineering of transcription factor-based tools would find the bifunctional regulation system and the glycerol-responsive variant directly applicable. The mechanistic insights into an RNAP-recruiting AraC-family activator may also interest structural biologists and protein engineers.
- **Major strengths** The study fills a clear gap by expanding the limited biosensor toolbox for short-chain alcohols. The work is logically structured, moving from characterization to mechanism to engineering. The use of AlphaFold predictions combined with targeted mutagenesis is a practical approach. The conversion of an activator to a repressor through promoter engineering is a notable conceptual advance. The bifunctional regulation system demonstrates a creative application of a single regulator for dual control.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical analysis), R1-M2 (dose-response data completeness), R1-M3 (mechanistic claim for glycerol specificity), R1-M4 (bifunctional circuit characterization)
- **Assessment against Nature-style criteria** Originality: moderate to high. While the general concept of TF-based biosensors is established, the specific focus on PocR and its engineering for 1,2-PD and glycerol sensing is novel. Scientific importance: moderate. The work provides useful tools for metabolic engineering but does not fundamentally advance understanding of transcription factor function or biosensor design principles. Interdisciplinary readership: limited. The work is primarily of interest to synthetic biology and metabolic engineering specialists. Technical soundness: generally sound but with gaps in statistical reporting and dose-response characterization. Readability for nonspecialists: adequate, though some sections assume familiarity with biosensor terminology and concepts.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are promising and likely valid, but the manuscript requires additional data presentation and statistical rigor to fully support its claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript reports dynamic ranges, operational ranges, and fold activations for various PocR variants without providing statistical measures of variability or significance.
- **Evidence pointer** Figures 1D, 2B, 3B, 3D, 4B, 4C, 5B, 5C, 6A, 6C, 6E; Methods section "PocR Performance Determination"
- **Concern** The methods state that all tests were performed using three biological repeats, but no error bars, standard deviations, or statistical tests are shown in any figure. The reader cannot assess the reproducibility or significance of the reported differences between variants.
- **Why it matters** Without measures of variability, it is impossible to determine whether the observed differences between wild-type and mutant biosensors are meaningful or within experimental noise. This is particularly critical for claims of improved dynamic range and altered specificity.
- **Resolution test** Add error bars to all figures, report the number of independent replicates, and perform appropriate statistical tests (e.g., t-tests or ANOVA) for key comparisons. State significance thresholds in figure legends.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data completeness
- **Claim pointer** The manuscript claims specific operational ranges for wild-type PocR (0–1 mM 1,2-PD) and PocR-ARE (0–20 mM 1,2-PD), and for the glycerol-responsive variant (0–20 mM glycerol).
- **Evidence pointer** Figures 1D, 5C, 4C; text in Results sections "Establishing and Characterizing the PocR Regulation System", "Optimizing the PocR Activation System", "Altering the Inducer Specificity of PocR"
- **Concern** The dose-response curves appear to show only a limited number of inducer concentrations. For wild-type PocR, the operational range is stated as 0–1 mM, but it is unclear how many intermediate concentrations were tested and whether the response saturates or continues beyond 1 mM. Similarly, for the engineered variants, the full dose-response curve is not clearly presented.
- **Why it matters** Accurate determination of operational range requires testing a sufficient number of inducer concentrations spanning the full response curve, including saturation. Incomplete dose-response data may lead to incorrect conclusions about the operational range and the magnitude of improvement achieved by engineering.
- **Resolution test** Provide complete dose-response curves with at least 6–8 inducer concentrations spanning the full response range, including concentrations above the apparent saturation point. Clearly indicate the tested concentrations in the figures or legends.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic claim
- **Claim pointer** The manuscript claims that the F46R/G106D variant has "altered inducer specificity to glycerol" and that this was achieved by "improving the hydrophilicity of these residues" near the methyl group of 1,2-PD.
- **Evidence pointer** Figure 4A, 4B, 4C, 4D; text in Results section "Altering the Inducer Specificity of PocR"
- **Concern** The claim of altered specificity is based on the observation that the variant no longer responds to 1,2-PD but responds to glycerol. However, the mechanism is inferred from the AlphaFold model and docking simulations without direct binding measurements. The authors do not demonstrate that the variant actually binds glycerol with higher affinity or that the loss of 1,2-PD response is due to altered binding rather than loss of protein stability or folding.
- **Why it matters** The claim of "altered specificity" implies a mechanistic understanding that supports the rational design approach. If the observed phenotype is due to nonspecific effects such as reduced protein stability, the design principle may not be generalizable.
- **Resolution test** Provide direct binding measurements (e.g., isothermal titration calorimetry, surface plasmon resonance, or differential scanning fluorimetry) for the wild-type and variant proteins with 1,2-PD and glycerol. Alternatively, demonstrate that the variant retains proper folding and DNA-binding activity.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Functional validation
- **Claim pointer** The manuscript claims that the bifunctional regulation system (V1, V2, V3) achieves "1,2-PD triggered bifunctional regulation" with simultaneous activation of RFP and repression of eGFP.
- **Evidence pointer** Figure 6C, 6D, 6E; text in Results section "Developing a Bifunctional Regulation Circuit Based on PocR"
- **Concern** The bifunctional circuits are tested only in a single condition (one IPTG concentration, one time point). The authors do not demonstrate that the system works across a range of inducer concentrations, that the activation and repression are coordinated, or that the system responds dynamically over time. Additionally, the fold changes reported for the bifunctional circuits are compared to single-module performance, but the comparison is not systematic.
- **Why it matters** For a bifunctional regulation system to be useful in metabolic engineering, it must be predictable and tunable. The current data do not establish whether the system can be fine-tuned or whether the activation and repression modules interfere with each other.
- **Resolution test** Characterize the bifunctional circuits across a range of 1,2-PD concentrations and IPTG levels. Show time-course data demonstrating dynamic response. Compare the performance of the integrated system to the individual modules under identical conditions.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Nomenclature consistency
- **Affected element** Variant naming
- **Evidence pointer** Abstract, Results sections, Figure legends
- **Issue** The manuscript uses inconsistent naming for the engineered variants. The abstract mentions "PcoR-F46R/G105D" while the Results section describes "PocR-F46R/G106D". Additionally, the final variant is referred to as both "PocR-Q107A/S192R/A203E" and "PocR-ARE" without a clear definition of when each name is used.
- **Required correction** Standardize variant naming throughout the manuscript. Define "PocR-ARE" at first use and use it consistently thereafter. Correct the residue numbering discrepancy (G105D vs G106D) and verify against the actual sequence.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 1C
- **Evidence pointer** Figure 1C
- **Issue** The text states that Pcob and Ppdu show "minimal expression of around 750 and 50 AU" in the absence of PocR, but the figure appears to show only one bar for each promoter without clear indication of which value corresponds to which promoter. The y-axis scale may also make it difficult to distinguish low values.
- **Required correction** Ensure figure labels clearly indicate which bar corresponds to which promoter. Consider using a log scale or insets to show low values clearly.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methods detail
- **Affected element** Docking simulation
- **Evidence pointer** Methods section
- **Issue** The methods mention AlphaFold prediction and docking simulations but do not provide parameters for the docking (e.g., grid size, exhaustiveness, scoring function) or the version of AlphaFold used. This limits reproducibility.
- **Required correction** Add a brief description of the AlphaFold version and docking parameters, or cite the relevant software and settings.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion depth
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of the bifunctional regulation system's advantages over existing approaches is brief. The authors mention that other systems require two orthogonal regulators or dCas9, but do not discuss potential limitations of their approach, such as the reduced dynamic range in the bifunctional configuration or potential crosstalk between modules.
- **Required correction** Expand the discussion to address limitations and compare more thoroughly with existing bifunctional systems.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Supplementary data
- **Affected element** Supporting Information
- **Evidence pointer** Methods section, Supplementary Material
- **Issue** The manuscript references Supporting Information Table 1 for strains and plasmids, and Figures S1–S5, but these are not provided in the submitted materials. The reader cannot verify the strain genotypes, plasmid construction details, or the supplementary data referenced in the text.
- **Required correction** Ensure all supplementary materials are included with the submission and referenced appropriately.

## Risk / unsupported claims
- The claim that the F46R/G106D variant has "altered inducer specificity to glycerol" is not fully supported without direct binding measurements or structural evidence.
- The claim that the bifunctional regulation system achieves "versatile performances" is based on limited characterization at a single condition.
- The statement that "the crystallization of the PocR functional complexes... is highly demanded" is presented as a future direction, but the manuscript does not discuss whether the authors have attempted crystallization or what specific questions it would answer beyond the current AlphaFold model.
- The claim that the engineered variants "hold significant potentials for metabolic engineering applications" is speculative and not demonstrated through any application example.
- The assertion that "RNAP-recruiting biosensors such as PocR" have "substantial advantages" over other biosensor types is not quantitatively supported by the data presented.