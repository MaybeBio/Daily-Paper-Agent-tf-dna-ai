## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and conclusion sections. Figures and tables are referenced but not fully visible; supplementary material is mentioned but not provided.
- **Assessment boundary** Evaluation is limited to the scientific content, methodological rigor, and logical coherence of the claims as presented in the provided text. Experimental data are described but primary data files, uncropped blots, raw computational outputs, and full figure panels are not available for independent verification.
- **Shared manuscript claim summary** The authors propose that the FDA-approved drugs lansoprazole and nitazoxanide act as functional inhibitors of the orphan nuclear receptor NR2F2, based on computational predictions (site mapping, docking, molecular dynamics, MM-GBSA, virtual screening) and in vitro validation (reporter assays, proliferation assays, siRNA-mediated knockdown) in the gastric cancer cell line GCIY.
- **Visible evidence base** Text descriptions of computational methods and results, reporter assay outcomes, proliferation assay outcomes, and western blot validation of knockdown efficiency. Figures 1–15 and Tables 1–3 are referenced but not directly inspectable.
- **Missing materials affecting confidence** Raw computational data (docking scores, MD trajectories, MM-GBSA energy components per frame), full figure panels with statistical annotations, uncropped western blots, dose-response curves with error bars and replicate numbers, and supplementary tables (S1, S2) are not available. This limits independent verification of quantitative claims.

## Reviewer
- **Overall assessment** The manuscript presents a plausible and potentially useful computational-to-experimental workflow for drug repurposing targeting NR2F2. The combination of site prediction, docking, MD, and MM-GBSA is methodologically sound in principle, and the use of siRNA knockdown to link compound activity to NR2F2 is a reasonable specificity control. However, several critical gaps weaken the current evidence base. The reporter assay data are described qualitatively without quantitative values or statistical analysis. The claim that lansoprazole and nitazoxanide act "via NR2F2" is supported by the siRNA rescue experiment, but the magnitude of rescue, dose-response consistency, and off-target effects are not fully documented. The computational predictions are not validated by direct binding assays (e.g., SPR, ITC), and the authors themselves acknowledge this limitation. The manuscript would be strengthened by providing quantitative reporter data, full dose-response curves with replicates, and a more rigorous statistical framework. The conclusion that these compounds are "bona fide functional interactors" is somewhat overstated given the indirect evidence.
- **Who would be interested in the results, and why** Researchers in nuclear receptor biology, particularly those studying orphan receptors and ligand discovery. Investigators interested in drug repurposing for gastric cancer. Computational chemists and structural biologists working on NR2F family members. The work may also appeal to clinicians exploring repurposed therapies for gastric malignancies, though clinical translation is distant.
- **Major strengths** The study addresses an important gap: NR2F2 is a validated oncogenic target in several cancers, yet few modulators exist. The computational pipeline is comprehensive, integrating site prediction, docking, MD, and free energy calculations. The use of an NR2F2-specific reporter assay and siRNA-mediated knockdown provides a functional link between compound activity and the target. The focus on FDA-approved drugs enhances translational relevance. The authors are transparent about the need for direct binding validation.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative reporter data missing), R1-M2 (incomplete dose-response and statistical reporting), R1-M3 (lack of direct binding evidence), R1-M4 (computational validation gaps).
- **Assessment against Nature-style criteria** **Originality**: Moderate. Drug repurposing for NR2F2 is not entirely novel, but the specific combination of computational methods and the focus on gastric cancer adds some originality. **Scientific importance**: Moderate to high. NR2F2 is a relevant target, and identifying new modulators is valuable. However, the lack of direct binding data limits the strength of the claim. **Interdisciplinary readership**: The work bridges computational chemistry, cancer biology, and pharmacology, which could attract a broad audience. **Technical soundness**: The computational methods are standard and appropriate, but the experimental validation is incomplete, particularly regarding quantitative reporting and statistical rigor. **Readability for nonspecialists**: The manuscript is generally well-written and accessible, though some computational details may be dense for experimental readers. Overall, the manuscript has potential but does not yet meet the standard for a high-impact general journal due to the evidentiary gaps.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising, and the experimental design is on the right track, but the current evidence does not fully establish that lansoprazole and nitazoxanide are direct NR2F2 inhibitors. Additional quantitative data and direct binding validation are required.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors claim that lansoprazole and nitazoxanide "modulate NR2F2-dependent reporter activity" and that this supports their status as functional interactors.
- **Evidence pointer** Results section, "Experimental validation of in silico–identified NR2F2 modulators", Figure 14
- **Concern** The reporter assay results are described qualitatively ("showed the ability to modulate") without providing quantitative luminescence values, fold changes, or statistical significance. The dose-response relationship is mentioned but no actual dose-response curves or EC50 values are presented. Without these data, it is impossible to assess the magnitude of the effect or whether it is biologically meaningful.
- **Why it matters** The reporter assay is the primary functional evidence that these compounds engage NR2F2. Without quantitative data, the claim of functional interaction is not verifiable. This is a central pillar of the manuscript's conclusion.
- **Resolution test** Provide a figure with dose-response curves for each compound, including mean ± SD from at least three independent experiments, with statistical analysis (e.g., one-way ANOVA with post-hoc tests) comparing compound-treated to vehicle-treated cells. Report EC50 values where applicable.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors claim that lansoprazole and nitazoxanide exert antiproliferative effects in GCIY cells that are "mitigated by NR2F2 silencing."
- **Evidence pointer** Results section, "Experimental validation of in silico–identified NR2F2 modulators", Figure 15
- **Concern** The proliferation assay data are described but not shown quantitatively. The text states that silencing reduces the compounds' effects, but the extent of rescue, the statistical significance of the rescue, and the dose-response relationship are not reported. Additionally, the effect of siRNA alone on proliferation is mentioned as a "modest reduction," but this is not quantified. The figure legend is not available for inspection.
- **Why it matters** The siRNA rescue experiment is the key experiment linking compound activity to NR2F2 specifically. Without quantitative data, it is unclear whether the rescue is partial or complete, and whether the effect is statistically robust. This is essential to support the claim that the compounds act via NR2F2.
- **Resolution test** Provide proliferation curves (e.g., cell viability vs. compound concentration) for control siRNA and NR2F2 siRNA conditions, with at least three independent replicates. Include statistical analysis comparing the IC50 values or area under the curve between conditions. Show that NR2F2 knockdown is efficient (e.g., western blot with quantification) and that the rescue is significant.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Direct binding evidence
- **Claim pointer** The authors conclude that lansoprazole and nitazoxanide are "bona fide functional interactors of NR2F2."
- **Evidence pointer** Conclusion section; Discussion section
- **Concern** The manuscript provides no direct binding data (e.g., SPR, ITC, MST, or cellular thermal shift assay) to demonstrate that these compounds physically bind to NR2F2. The computational predictions and reporter assays are indirect. The authors acknowledge this in the conclusion, but the claim of "bona fide interactors" is stronger than the evidence supports.
- **Why it matters** Without direct binding evidence, the mechanism of action remains speculative. The compounds could affect NR2F2 activity indirectly (e.g., via signaling pathways) rather than by direct binding. This distinction is critical for the proposed repurposing strategy.
- **Resolution test** Perform a direct binding assay (e.g., SPR or ITC) with purified NR2F2 LBD and the compounds. Report binding affinities (KD) and stoichiometry. Alternatively, a cellular thermal shift assay (CETSA) could provide in-cell binding evidence.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Computational validation
- **Claim pointer** The authors state that the computational pipeline identified two binding sites and that virtual screening yielded promising hits, with convergence between in silico predictions and experimental data.
- **Evidence pointer** Results sections on site mapping, docking, MD, MM-GBSA, and virtual screening; Figures 2–12; Tables 1–3
- **Concern** The computational results are described in detail, but key quantitative outputs are not presented. For example, docking scores for the identified compounds are not reported in the text, MM-GBSA values are only summarized in a table (not fully visible), and the criteria for selecting the six compounds for experimental testing are not explicitly stated. The MD simulation convergence is mentioned but no RMSD plots are shown in the text (only referenced as figures).
- **Why it matters** The computational pipeline is the foundation of the study. Without clear quantitative metrics and selection criteria, the reproducibility and objectivity of the virtual screening are questionable. This weakens the logical link between the computational predictions and the experimental validation.
- **Resolution test** Provide a supplementary table with docking scores, MM-GBSA binding free energies, and the selection criteria for all compounds tested. Include representative RMSD and RMSF plots for the MD simulations. State the threshold values used to define "promising binders."

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, "Cell culture and chemical compounds"
- **Evidence pointer** Materials and methods, "Cell culture and chemical compounds"
- **Issue** The concentration range used for the compounds in the proliferation and reporter assays is not stated in the text. The authors mention "various concentrations" but do not specify the range or the solvent controls used.
- **Required correction** Specify the concentration range tested (e.g., 0.1–100 µM) and the solvent (DMSO) concentration used as vehicle control. State whether the compounds were tested at equimolar concentrations across assays.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section, "Experimental validation"
- **Evidence pointer** Results section, "Experimental validation of in silico–identified NR2F2 modulators"
- **Issue** The number of independent experiments (n) for the reporter and proliferation assays is not stated. The text mentions "two replicates" for the reporter assay, which is insufficient for statistical analysis.
- **Required correction** Report the number of independent biological replicates for each experiment. For the reporter assay, increase the number of replicates to at least three independent experiments, each performed in triplicate.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement
- **Evidence pointer** Data availability statement
- **Issue** The statement says raw data "will be made available by the authors, without undue reservation," but this is vague and does not specify where or how the data will be deposited.
- **Required correction** Specify a repository (e.g., Zenodo, Figshare) and provide a data DOI or accession number, or state that data are available upon reasonable request with a clear contact point.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction; Discussion
- **Issue** The discussion of NR2F2's role in gastric cancer is brief. The authors cite Feng et al. (2017) showing tumor-suppressive effects, but the manuscript does not reconcile this with the pro-proliferative context implied by the current study. This apparent contradiction is not addressed.
- **Required correction** Add a brief paragraph in the Discussion addressing the context-dependent role of NR2F2 in gastric cancer, explaining how the current findings fit with existing literature.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 14 and 15
- **Evidence pointer** Results section, "Experimental validation"
- **Issue** The text references Figure 14B and 14C and Figure 15A and 15B, but the figures are not provided in the manuscript text. It is unclear whether the figures include error bars, statistical annotations, and full dose-response curves.
- **Required correction** Ensure all figures are included with full axis labels, error bars, and statistical annotations. Add a figure legend describing the experimental conditions and the number of replicates.

## Risk / unsupported claims
- The claim that lansoprazole and nitazoxanide are "bona fide functional interactors of NR2F2" is not fully supported by the evidence presented, as no direct binding data are provided.
- The claim that the computational predictions and experimental data "converge" is weakened by the lack of quantitative computational metrics (e.g., docking scores, MM-GBSA values) in the text.
- The statement that "NR2F2 silencing significantly impaired the growth-inhibitory effects" is not verifiable without quantitative proliferation data and statistical analysis.
- The assertion that the reporter assay is "selective" for NR2F2 is based on a single experiment with two replicates and no statistical validation.
- The translational implication that these compounds could be repurposed for gastric cancer therapy is speculative, as no in vivo data or pharmacokinetic assessments are provided.