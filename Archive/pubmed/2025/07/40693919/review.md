## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and conclusions
- **Assessment boundary** Scientific soundness, methodological rigor, claim-evidence alignment, and general interest assessment only. No assessment of editorial fit or publication policy matters.
- **Shared manuscript claim summary** The authors use MD and PaCS-MD simulations to show that the FUS ZnF specifically recognizes the GGU RNA sequence, while the flanking RGG2 IDR contributes nonspecific charge interactions that lower the dissociation constant approximately 2-fold. They further propose a general mechanism whereby proteins with one or few nucleic acid binding motifs use flanking disordered regions to achieve strong binding, supported by a DisProt database analysis.
- **Visible evidence base** Main text figures (referenced as Figures 1-5 and S1-S14), tables (S1-S2), simulation methods descriptions, and database analysis description. Figure content itself was not directly viewable; only figure captions and in-text descriptions were available.
- **Missing materials affecting confidence** Actual figure images, supplementary movies, detailed simulation parameters, convergence diagnostics, and the full DisProt analysis methodology and results. The manuscript text references figures extensively but the figures themselves were not provided for inspection.

## Reviewer
- **Overall assessment** This manuscript presents a computationally intensive and carefully executed study of the FUS ZnF-RNA binding mechanism, with a plausible two-state model linking sugar puckering to binding affinity. The central claim that the IDR contributes nonspecific stabilizing interactions is reasonably supported by the simulation data as described. However, several technical concerns regarding force field validation, sampling convergence, and the statistical treatment of the database analysis prevent full confidence in the conclusions as currently presented. The generalization claim from a single system to a broad biological principle is ambitious and would benefit from additional supporting evidence or more cautious framing.
- **Who would be interested in the results, and why** Researchers studying RNA-protein interactions, particularly those focused on FUS biology and ALS/FTD pathogenesis. Computational biophysicists interested in enhanced sampling methods and IDR-mediated binding mechanisms. Structural biologists studying ZnF domains and their nucleic acid recognition properties. The proposed general mechanism of IDR-assisted binding may interest a broader community studying nucleic acid binding proteins.
- **Major strengths** The study addresses an important and timely question about how a single ZnF achieves strong and specific RNA binding. The combination of conventional MD with PaCS-MD enhanced sampling is appropriate for studying dissociation pathways. The authors are transparent about discrepancies between their results and previous experimental observations. The connection between sugar puckering and binding free energy provides a mechanistically interesting and testable hypothesis. The database analysis, while limited, attempts to place the findings in a broader context.
- **Major Concerns** 
  - R1-M1: Force field validation is insufficient for the specific system studied
  - R1-M2: Sampling convergence and statistical reliability of the free energy calculations are not fully demonstrated
  - R1-M3: The DisProt database analysis methodology is underdescribed and the interpretation may overreach
  - R1-M4: The relationship between the two metastable states and experimental observations requires clarification
- **Minor Comments**
  - R1-m1: The use of AI tools for language improvement should be acknowledged more prominently
  - R1-m2: The manuscript would benefit from a clearer statement of the novelty relative to prior computational studies of FUS
  - R1-m3: The discussion of the biological implications for ALS/FTD is somewhat speculative and could be better grounded
  - R1-m4: The figure numbering and referencing in the text is occasionally unclear
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The specific application to FUS ZnF is novel, and the sugar puckering analysis provides a fresh angle. However, the general concept of IDR-assisted binding is established in the literature.
  - Scientific importance: Moderate to high. Understanding FUS RNA binding has implications for neurodegenerative disease research. The proposed general mechanism, if validated, could be impactful.
  - Interdisciplinary readership: Limited. The work is primarily of interest to computational biophysicists and RNA biology specialists. The technical nature of the methods may limit broader accessibility.
  - Technical soundness: The simulation methodology is generally appropriate, but concerns about force field validation and sampling convergence (detailed below) prevent full confidence in the quantitative conclusions.
  - Readability for nonspecialists: The manuscript is clearly written but assumes substantial background in molecular dynamics simulation methodology. The biological context is well explained.
- **Recommendation posture** Supportive if technical concerns are resolved. The core simulation work appears carefully executed, and the mechanistic insights are potentially valuable. However, the force field validation, convergence demonstration, and database analysis need strengthening before the conclusions can be fully accepted.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the combination of ff19SB, ZAFF, and DES Amber force fields with TIP4P-D water accurately models the FUS ZnF-RNA system, citing reproduction of experimental radii of gyration for other disordered proteins and improved RNA tetranucleotide structure reproduction.
- **Evidence pointer** Methods section, "Modeling of the FUS-RNA Complex Structure" subsection
- **Concern** The force field validation is indirect. The authors validate the RNA force field (DES Amber) on tetranucleotides and the protein force field (ff19SB) on other disordered proteins, but not the specific combination on the FUS ZnF-RNA system. The ZAFF parameters for zinc are mentioned but not validated in this context. The authors note a discrepancy with NMR NOE distances for the U1-W440 pair, which they attribute to "larger fluctuations at the end of the RNA chain or conditional differences" but this could also indicate force field inaccuracies. The statement that "the combination of ff19SB and TIP4P-D was tested on other disordered proteins" does not establish validity for a ZnF domain with a coordinated metal ion.
- **Why it matters** The central conclusions about binding free energies, interaction networks, and sugar puckering preferences all depend on the accuracy of the force field. If the force field biases certain conformations or interactions, the mechanistic conclusions could be artifacts. The U1-W440 discrepancy is particularly concerning because W440 is identified as a key residue for RNA recognition.
- **Resolution test** Provide additional validation of the force field combination on the FUS ZnF-RNA system specifically, such as comparison of simulated conformational ensembles against the full set of NMR restraints, or reproduction of experimentally measured binding affinities for multiple RNA sequences. Alternatively, demonstrate that the U1-W440 discrepancy does not affect the conclusions by showing similar results with an alternative force field or with modified treatment of this interaction.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the free energy landscape and binding free energies calculated from PaC-MD simulations are reliable, with values of -6.6 ± 1.7 kcal/mol for the full construct and -5.2 ± 0.8 kcal/mol for the structured region alone.
- **Evidence pointer** Results section, "Classification of the Trials into High and Low Free Energy Dissociations" subsection; Methods section, "PaCS-MD Simulation" and "Trajectory Analysis, MSM Construction, and Free Energy Calculation" subsections
- **Concern** The manuscript does not provide sufficient evidence for convergence of the free energy calculations. The MSM is constructed from PaCS-MD trajectories, but the number of trials (32) and the clustering parameters (15 clusters, 20 ps lag time) are stated without justification for this specific system. The authors note a discrepancy between the MSM-derived binding free energy and the experimental value, and they acknowledge that the standard binding free energy "might be affected by the selection ratio of the initial structures." The classification of trials into high and low free energy groups appears to be post hoc, and the statistical significance of the 2.6 kcal/mol difference between groups is not assessed. The correlation coefficient of 0.63 between free energy of the dissociation starting point and binding free energy is reported without confidence intervals.
- **Why it matters** The quantitative claims about binding free energies and the 2-fold difference in Kd between constructs with and without the IDR depend on the reliability of the free energy calculations. If the sampling is insufficient or the MSM is not converged, the reported values and the mechanistic conclusions drawn from them could be unreliable.
- **Resolution test** Provide convergence diagnostics for the MSM, such as implied timescale plots showing plateau behavior, Chapman-Kolmogorov tests, and comparison of free energies calculated from independent runs. Report statistical uncertainties on all reported free energy values and the Kd estimates. Demonstrate that the classification into high and low free energy trials is robust to the choice of clustering parameters and lag time.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The authors claim that "the binding of the IDR exhibits a 2-fold lower dissociation constant" and that the database analysis "suggests that the stabilization of protein-RNA binding by only one or a few nucleic acid binding motifs with flanking disordered regions... is a common mechanism."
- **Evidence pointer** Results section, "Possible General Mechanisms of Nucleic Acid Binding Assisted by Flanking Disordered Regions" subsection; Discussion section
- **Concern** The 2-fold Kd claim appears to be based on the difference between the calculated binding free energies of the full construct (-6.6 kcal/mol) and the structured region alone (-5.2 kcal/mol), which the authors interpret as a 2.6 kcal/mol contribution from the IDR. However, the authors also state that the structured region alone has a Kd in the submillimolar range and the full construct has a Kd in the micromolar range, which would be a much larger difference than 2-fold. The relationship between the calculated free energy difference and the experimentally measured Kd values is unclear. Additionally, the DisProt analysis is described only briefly: the authors state that 43% of RNA binding sites in proteins with one RNA binding site are flanked by disordered regions versus 19% in proteins with ≥5 sites, but no statistical analysis is presented, and the methodology for identifying "flanking" disordered regions is not described.
- **Why it matters** The generalization from the FUS case to a common biological mechanism is a major claim of the paper. If the statistical basis for this claim is weak, or if the interpretation of the FUS data is inconsistent, the broader significance of the work is substantially diminished.
- **Resolution test** Clarify the relationship between the calculated free energy difference and the experimentally measured Kd values. Provide a more detailed description of the DisProt analysis methodology, including how flanking disordered regions were defined, and include appropriate statistical tests (e.g., chi-square or Fisher's exact test) with effect sizes and confidence intervals. Consider whether the observed difference (43% vs 19%) is robust to the choice of thresholds for defining "flanking" and "one or few" binding sites.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The authors claim that "the structured region specifically recognizes the GGU sequence of RNA" and that "the IDR interacts nonspecifically with the RNA backbone and distorts it," with sugar puckering linked to binding free energy.
- **Evidence pointer** Results section, "Interactions between RNA and IDR Determine Differences in Binding Affinity" and "Sugar-Puckering Is Linked to the Binding Free Energy" subsections
- **Concern** The relationship between the two metastable states identified in the free energy landscape and the experimentally observed binding mode is not fully clarified. The authors state that the NMR structures are distributed around the M2 minimum, but the M1 minimum is the lowest free energy state. This raises the question of whether the M1 state is physiologically relevant or an artifact of the simulation conditions. The claim that sugar puckering is "linked to binding free energy" is based on a correlation observed in the simulations, but the causal relationship is not established. The authors suggest that the IDR "distorts" the RNA, but it is unclear whether this distortion is functionally important or simply a consequence of nonspecific interactions.
- **Why it matters** The mechanistic model proposed (specific recognition by ZnF, nonspecific stabilization by IDR, sugar puckering as a key determinant) is the main conceptual contribution of the paper. If the relationship between the computational states and experimental reality is not clearly established, the model remains speculative.
- **Resolution test** Provide a more detailed comparison between the M1 and M2 states and the NMR structures, including specific structural metrics. Discuss whether the M1 state would be populated under physiological conditions and whether experimental evidence supports its existence. Consider performing additional simulations starting from the M1 state to test its stability.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Transparency
- **Affected element** Acknowledgements section
- **Evidence pointer** Acknowledgements section
- **Issue** The use of ChatGPT and DeepL for language improvement is acknowledged, but the statement "all content was reviewed and edited by the authors" is vague. Given increasing concerns about AI use in scientific writing, more specific disclosure of how these tools were used would be appropriate.
- **Required correction** Specify the extent of AI assistance (e.g., grammar checking, sentence restructuring) and confirm that all scientific content, data analysis, and interpretation were performed solely by the authors.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Context
- **Affected element** Introduction and Discussion sections
- **Evidence pointer** Introduction section, paragraphs 1-3; Discussion section, paragraph 2
- **Issue** The novelty of the computational approach relative to prior MD studies of FUS is not clearly stated. The authors mention that a previous study reported progressive distortions with the OL3 force field, but do not systematically compare their approach and findings with other computational studies of FUS-RNA interactions.
- **Required correction** Add a brief paragraph in the Introduction or Discussion explicitly stating what is new about this study compared to previous computational work on FUS, and how the findings extend or correct prior understanding.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scope
- **Affected element** Discussion section, paragraph 4
- **Evidence pointer** Discussion section, paragraph 4
- **Issue** The discussion of disease implications (ALS, FTD) is brief and somewhat disconnected from the main findings. The connection between the proposed binding mechanism and disease pathogenesis is not developed.
- **Required correction** Either expand the discussion of disease implications with specific mechanistic links, or explicitly state that the disease relevance is indirect and requires further investigation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure references throughout
- **Evidence pointer** Results section, all subsections
- **Issue** The text frequently refers to figures without clear descriptions of what is shown. For example, "Figure 1a,b" is referenced without explaining what panels a and b display. This makes it difficult to follow the results without constantly cross-referencing.
- **Required correction** Add brief parenthetical descriptions when referencing figures, e.g., "Figure 1a,b (simulation system and RMSF analysis)" to improve readability.

## Risk / unsupported claims
- The claim that the IDR contributes approximately -2.6 kcal/mol to the binding free energy is based on the difference between two simulation sets with different constructs, but the statistical significance of this difference is not established.
- The claim that the binding of the IDR "exhibits a 2-fold lower dissociation constant" is inconsistent with the reported Kd values (submillimolar vs micromolar range) and requires clarification.
- The generalization to a "common mechanism" based on the DisProt analysis is not statistically supported as presented.
- The statement that "the structured region specifically recognizes the GGU sequence" is based on simulations with a single RNA sequence (UGGUG); the specificity claim would be strengthened by simulations or experiments with mutated RNA sequences.
- The biological relevance of the M1 state (lowest free energy minimum) is not established, given that NMR structures cluster around the M2 state.
- The claim that sugar puckering is "linked to binding free energy" is correlational and the causal direction is not established.