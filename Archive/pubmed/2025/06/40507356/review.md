## Review setup
- **Input scope** Full manuscript text (review article with original computational docking data)
- **Assessment boundary** Scientific content, methodological soundness, claims vs. evidence, and suitability for the stated journal context
- **Shared manuscript claim summary** The manuscript proposes that cysteine alkylation via Michael addition in enzymes and transcription factors overexpressed in cancer represents a viable therapeutic strategy. It combines a narrative review of TrxR, XPO1, STAT3, NF-κB, IKKβ, and HIF-1 with local covalent docking simulations (AutoDockFR) of natural compounds (curcumin, cinnamaldehyde, zerumbone, helenalin, umbelliferone) and established drugs (CDDO-Me, STAT3-IN-1, palbociclib, sunitinib) against specific cysteine residues.
- **Visible evidence base** Literature citations (numbered references), Table 1 (cysteine residue locations), Table 2 (docking scores), Figures 1–18 (chemical structures, protein schematics, docking poses)
- **Missing materials affecting confidence** No supplementary methods file, no docking parameter details (exhaustiveness, grid box dimensions, number of runs), no statistical analysis of docking scores, no validation of docking protocol against known crystallographic complexes, no raw output files, no PDB accession validation details beyond identifiers

## Reviewer
- **Overall assessment** This manuscript combines a broad narrative review of cysteine-targeting covalent inhibitors in cancer with a modest computational docking study. The review component is reasonably comprehensive but largely derivative, summarizing well-established literature without critical synthesis or novel conceptual framing. The docking study, while technically executed, is presented with insufficient methodological detail to assess its validity, and the interpretation overreaches the data. The central claim that these simulations "demonstrate" therapeutic potential is not supported by the evidence presented. The manuscript reads as a descriptive overview rather than a hypothesis-driven investigation, and the computational results are exploratory at best. The writing is generally clear but contains redundancies and occasional unsupported generalizations. The work may be of interest to researchers in covalent drug discovery, but in its current form it does not establish a robust case for the proposed therapeutic strategy.

- **Who would be interested in the results, and why** Researchers in covalent drug discovery, particularly those focused on targeting reactive cysteines in cancer-related proteins, may find the compiled information on cysteine positions and known inhibitors useful as a reference. Computational chemists working on covalent docking methodologies might be interested in the application of AutoDockFR to these specific targets. However, the lack of experimental validation limits the audience to those seeking preliminary computational hypotheses rather than established therapeutic insights.

- **Major strengths** The manuscript provides a useful compilation of cysteine residues in several cancer-relevant proteins, with literature support for their functional importance. The selection of both natural products and approved drugs offers a reasonable comparative scope. The inclusion of multiple targets (enzyme and transcription factors) provides breadth. The docking approach using AutoDockFR with explicit covalent bond handling is appropriate for the question posed. The figures illustrating docking poses are generally clear.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of computational methods
- **Claim pointer** The manuscript claims to have performed "local docking" and "covalent docking" using AutoDockFR, with results summarized in Table 2, and interprets these scores as evidence of binding affinity and therapeutic potential.
- **Evidence pointer** Section 5, Table 2, Figures 13–18
- **Concern** The methods section lacks essential details required to evaluate the docking results. No information is provided on the number of docking runs, genetic algorithm parameters, grid box dimensions beyond a 50 Å padding, exhaustiveness settings, or how the covalent bond was defined in the ligand preparation. The manuscript states that "all possible stereoisomers" and "all possible regio-isomers" were generated for certain molecules, but does not specify how many were tested or how the "best score" was selected across isomers. Without these parameters, the docking scores in Table 2 cannot be reproduced or independently verified, and the claim of "energetically favorable binding" is not substantiated.
- **Why it matters** Docking scores are highly sensitive to protocol parameters. Without full methodological transparency, the quantitative results are not interpretable, and the central computational evidence for the manuscript's thesis is unverifiable. This is a fundamental issue that affects the validity of the entire docking-based argument.
- **Resolution test** Provide a complete methods section including software version, all docking parameters, number of runs, selection criteria for best pose, grid box coordinates and dimensions, and a validation of the protocol against a known covalent complex (e.g., redocking a crystallographic ligand). If the protocol cannot be validated, the docking results should be presented as preliminary and not used to support therapeutic claims.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The abstract and conclusions state that the study "demonstrates" binding abilities and "suggests" a "plausible mechanism" for therapeutic action, with the Simple Summary claiming the results "highlight their potential as low-toxicity therapeutic options."
- **Evidence pointer** Abstract, Simple Summary, Section 6
- **Concern** The docking scores are presented as evidence of therapeutic potential, but docking affinity alone does not demonstrate biological activity, selectivity, cellular permeability, metabolic stability, or in vivo efficacy. The manuscript does not include any experimental data, and the docking scores are not compared against known inhibitors' affinities or validated in any functional assay. The language throughout overstates what computational docking can establish. For example, the claim that "simulations predict that some alkylating compounds could significantly disrupt protein-protein interactions" is presented without any experimental or structural evidence for such disruption.
- **Why it matters** The central thesis of the manuscript is that cysteine alkylation is a viable therapeutic strategy. The evidence provided is computational prediction only, which is hypothesis-generating, not hypothesis-testing. Overstating the implications of docking results misleads readers about the strength of the evidence and could encourage unwarranted experimental investment.
- **Resolution test** Rewrite all claims to clearly distinguish between computational predictions and experimentally validated findings. Add explicit statements that the docking results are preliminary and require experimental validation. If the authors wish to maintain strong claims, they must include experimental data (e.g., biochemical assays, cellular studies) demonstrating target engagement and functional consequences.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance and novelty
- **Claim pointer** The manuscript presents itself as a "review and a proposal" exploring a therapeutic strategy, but the review component largely restates established knowledge about covalent inhibitors and the selected targets without offering a new conceptual framework, comparative analysis, or critical evaluation of the field.
- **Evidence pointer** Sections 1–4
- **Concern** The review sections provide descriptive summaries of well-known information about TrxR, NF-κB, STAT3, and related targets, and the concept of targeting cysteines with Michael acceptors is not new. The manuscript does not identify a gap in the literature, propose a testable hypothesis beyond the general idea, or offer a systematic comparison of the selected compounds' chemical properties, selectivity profiles, or clinical potential. The docking study, while adding an original element, is exploratory and does not fill a clear conceptual void.
- **Why it matters** For a review article to be impactful, it must offer synthesis, critical perspective, or novel insights. In its current form, the manuscript is largely a compilation of known facts with a small computational add-on. The scientific importance is therefore limited, and the contribution to the field is incremental at best.
- **Resolution test** Reframe the manuscript to address a specific, well-defined question (e.g., comparative selectivity of natural versus synthetic Michael acceptors across the selected targets) and provide a systematic analysis that goes beyond description. Alternatively, expand the docking study to include a broader panel of compounds and targets with rigorous statistical comparison, and discuss the implications for drug design in a way that generates new testable hypotheses.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness of docking interpretation
- **Claim pointer** The manuscript states that "no significant preference was observed between Sec 498 and Cys 497" in TrxR docking, and interprets differential docking scores across targets as meaningful affinity differences.
- **Evidence pointer** Section 5, Table 2
- **Concern** The docking scores in Table 2 range from approximately −4 to −9 kcal/mol, but no error estimates, standard deviations, or statistical comparisons are provided. The claim of "no significant preference" implies a statistical test was performed, but no such analysis is described. Furthermore, the manuscript does not discuss the known limitations of docking scores, including their poor correlation with experimental binding affinities, the influence of solvation and entropy, and the sensitivity to protonation states and conformational flexibility. The interpretation of a 1–2 kcal/mol difference between compounds as meaningful is not justified without error analysis.
- **Why it matters** Without statistical rigor and acknowledgment of docking limitations, the quantitative comparisons between compounds and targets are not reliable. Readers may draw incorrect conclusions about which compounds are most promising for which targets.
- **Resolution test** Provide replicate docking runs with standard deviations, perform appropriate statistical tests for comparisons, and include a discussion of docking score limitations. If replicates were not performed, state this explicitly and present the scores as single-point estimates with appropriate caveats.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership and accessibility
- **Claim pointer** The manuscript targets a broad audience including cancer biologists and medicinal chemists, but assumes significant prior knowledge of both computational docking and the specific structural biology of the targets.
- **Evidence pointer** Sections 4–5
- **Concern** The description of the docking methodology and the interpretation of results will be opaque to readers without computational chemistry expertise. Terms such as "gradient affinity maps," "Dunbrack rotamer library," and "regio-isomers" are used without adequate explanation. Conversely, the biological sections assume familiarity with signaling pathways and cancer biology that may not be accessible to computational chemists. The manuscript does not bridge these audiences effectively.
- **Why it matters** For a review with computational components to reach its intended interdisciplinary audience, it must explain methods and concepts at a level accessible to nonspecialists. The current presentation may limit the manuscript's impact and readability.
- **Resolution test** Add a brief, plain-language explanation of covalent docking and its limitations, define technical terms at first use, and provide a schematic overview of the workflow. Consider moving detailed technical parameters to a methods section or supplement.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and precision
- **Affected element** Section 2.1, statement on acrolein
- **Evidence pointer** Section 2.1
- **Issue** The discussion of acrolein as a model electrophile is somewhat tangential to the main thesis and could be streamlined. The relevance of acrolein's toxicity to the proposed therapeutic strategy is not clearly articulated.
- **Required correction** Either integrate acrolein more explicitly into the argument about designing selective inhibitors or remove it to maintain focus.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Terminology for cysteine residues
- **Evidence pointer** Sections 2.3, 2.4, 4
- **Issue** The manuscript refers to "Cys259," "Cys38," and "Cys179" without consistently specifying the protein context (e.g., "Cys259 of STAT3" vs. just "Cys259"). This could cause confusion when multiple proteins are discussed.
- **Required correction** Standardize terminology to always include the protein name when referring to specific cysteine residues.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 13–18
- **Evidence pointer** Figures 13–18
- **Issue** The docking pose figures are described in the text but the figure captions do not specify which isomer or stereoisomer is shown, nor do they indicate the protein surface or key interacting residues clearly.
- **Required correction** Expand figure captions to include the specific isomer shown, the coloring scheme, and the key interactions (e.g., hydrogen bonds, hydrophobic contacts) with residue labels.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Section 3, statement on SHP2
- **Evidence pointer** Section 3
- **Issue** The discussion of SHP2 as a target for covalent inhibition is introduced without a citation for the specific claim about Cys459 being the nucleophilic cysteine required for catalysis.
- **Required correction** Add appropriate references to support this statement.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Table 2
- **Evidence pointer** Table 2
- **Issue** Table 2 presents docking scores but does not include the number of isomers tested per compound, the range of scores across isomers, or the specific isomer that yielded the best score. This limits the interpretability of the data.
- **Required correction** Add columns for the number of isomers tested, score range, and isomer identifier, or provide this information in a supplementary table.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Language and style
- **Affected element** Throughout
- **Evidence pointer** Throughout
- **Issue** The manuscript contains some redundant phrasing and repetitive statements, particularly in the introduction and conclusions, where similar points are made multiple times.
- **Required correction** Streamline the text to improve conciseness and readability.

## Risk / unsupported claims
- The claim that docking scores "demonstrate" binding abilities or therapeutic potential is unsupported; docking scores are predictive, not demonstrative.
- The statement that "simulations predict that some alkylating compounds could significantly disrupt protein-protein interactions" is unsupported by any experimental or structural evidence.
- The claim of "no significant preference" between Sec 498 and Cys 497 in TrxR implies statistical analysis that is not described.
- The assertion that the selected natural compounds are "low-toxicity therapeutic options" is not supported by any toxicity data presented in the manuscript.
- The general statement that "covalent inhibitors by Michael reaction are a powerful resource" is presented as established fact without critical evaluation of limitations, off-target effects, or clinical failures in this class.
- The manuscript's claim to provide "a basis for evaluating other covalent docking algorithms in the future" is not substantiated, as no comparison with other algorithms or validation against experimental data is provided.