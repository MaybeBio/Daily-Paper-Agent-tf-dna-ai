## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and supplementary figure/table references
- **Assessment boundary** Scientific content, methodological rigor, validity of conclusions drawn from the presented computational data, and alignment with the stated claims
- **Shared manuscript claim summary** The authors propose that abnormal cytosine methylation in the NDUFA13 gene promoter of breast cancer cells (MCF7) disrupts cooperative DNA recognition by the transcription factors CEBPB and E2F1-DP1, thereby impeding formation of the enhanceosome complex and contributing to NDUFA13 downregulation. This is supported by bioinformatic identification of a hypermethylated region and microsecond-long all-atom molecular dynamics simulations comparing wild-type and methylated DNA in naked, singly bound, and co-bound states.
- **Visible evidence base** Bioinformatic analysis of ENCODE ChIP-seq and reduced representation bisulfite sequencing data for MCF7 cells; TFregulomeR motif identification; eight 1.1 μs MD simulations (WT/ME × DNA alone/CEBPB/E2F1-DP1/both); analyses of DNA deformation energy, protein-DNA contact maps, interaction energies, configurational entropies, helical and groove parameters, and ion distributions
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; simulation input files, force field parameter details for 5-methylcytosine, and convergence criteria not fully described; no experimental validation data; no error analysis for the bioinformatic identification of methylation sites

## Reviewer
- **Overall assessment** The manuscript addresses a timely and potentially important question: how promoter methylation at specific CpG sites may disrupt cooperative transcription factor binding through allosteric, DNA-mediated mechanisms. The computational approach is ambitious, combining long-timescale MD with multiple analysis methods. However, the central claims are only partially supported by the presented evidence. The bioinformatic identification of the hypermethylated region is described qualitatively without quantitative support. The MD results show small differences between WT and ME systems, often with overlapping standard deviations, and the interpretation relies heavily on mean values with near-zero standard errors derived from large sample sizes, which may overstate significance. The mechanistic narrative, while plausible, is not uniquely determined by the data. The claim that methylation "breaks" cooperative recognition is stronger than the evidence warrants, as the authors themselves note that methylation leads to stronger overall TF-DNA complexation in interaction energy terms. The manuscript would benefit from clearer articulation of the limitations of computational predictions and from tempering the causal language used in the title and discussion.
- **Who would be interested in the results, and why** Researchers in computational biophysics, epigenetics, and gene regulation would find this study of interest. Those studying transcription factor cooperativity and DNA shape readout would value the detailed analysis of DNA structural changes upon methylation. The cancer epigenetics community may be interested in the proposed mechanism linking promoter methylation to gene downregulation, though the lack of experimental validation limits immediate translational relevance. Methodologists developing or applying MD simulations to protein-DNA systems would also find the analytical approaches informative.
- **Major strengths** The study addresses a mechanistically important question with a sophisticated computational pipeline. The use of microsecond-long MD simulations is appropriate for capturing slow DNA conformational transitions. The multi-pronged analysis approach, including deformation energies, contact maps, configurational entropies, and ion distributions, provides a comprehensive view of the system. The authors are appropriately cautious in several places, acknowledging overlapping standard deviations and the need for experimental validation. The comparison of solo versus co-bound states is well designed to isolate cooperative effects.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  umber **Blocking** Yes
  - **Axis** Evidence sufficiency for central claim
  - **Claim pointer** The title and discussion state that abnormal methylation "breaks" cooperative DNA recognition by transcription factors, and that this impedes enhanceosome formation and contributes to NDUFA13 downregulation.
  - **Evidence pointer** Results sections on DNA deformation energies, protein-DNA contacts, interaction energies, and helical parameters; Discussion
  - **Concern** The central claim of disrupted cooperativity is not quantitatively established. The differences between WT and ME systems in deformation energies, interaction energies, and contact strengths are small, often within overlapping standard deviations. The authors rely on mean values with near-zero standard errors from large sample sizes, but this does not address whether the differences are biologically meaningful. Moreover, the interaction energy analysis shows that methylation leads to stronger overall TF-DNA complexation, which appears to contradict the narrative of disrupted binding. The causal link from the observed MD differences to impaired enhanceosome formation and NDUFA13 downregulation is speculative and not supported by functional data.
  - **Why it matters** The title and abstract promise a mechanistic explanation for how methylation leads to gene downregulation. If the computational differences are not robust or not clearly linked to functional outcomes, the central contribution of the paper is weakened. Overstating the conclusions could mislead readers and future research directions.
  - **Resolution test** Provide quantitative measures of effect size and statistical significance for the key differences between WT and ME systems. Clearly articulate how the observed changes in DNA structure and dynamics translate to altered binding affinity or specificity, ideally with free energy calculations or experimental binding assays. Temper the language in the title and discussion to match the strength of the evidence.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Model system validation
  - **Claim pointer** The authors state that the hypermethylated region within the NDUFA13 promoter, 130 bp from the TSS, contains binding sites for CEBPB and E2F1-DP1, and that this region was identified through bioinformatic analysis of MCF7 ChIP-seq and methylation data.
  - **Evidence pointer** Methods section on bioinformatic analyses; Supplementary Figures S1 and S2; Supplementary Table S1
  - **Concern** The bioinformatic identification of the model system is described only qualitatively. No quantitative details are provided regarding the ChIP-seq peak calling thresholds, the methylation levels at the specific CpG sites, the criteria for selecting the six methylation sites, or the confidence in the TF binding site assignments. The statement that methylation rates vary depending on the analyzing lab is mentioned but not quantified. Without these details, the relevance of the chosen model system to the actual biology of NDUFA13 regulation in breast cancer cannot be assessed.
  - **Why it matters** The entire study is built on the premise that the selected promoter region and methylation sites are biologically relevant. If the bioinformatic selection is not rigorously justified, the computational findings may not pertain to the real regulatory mechanism.
  - **Resolution test** Provide a detailed description of the bioinformatic pipeline, including data sources, quality filters, peak calling parameters, and methylation level thresholds. Show the methylation levels at each of the six CpG sites in MCF7 and other cell lines. Justify the selection of the specific region and explain why the other eight methylation sites were excluded from the study.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Simulation methodology and convergence
  - **Claim pointer** The authors state that microsecond-long MD simulations were performed for eight systems and that the first 100 ns were discarded as equilibration.
  - **Evidence pointer** Methods section on molecular dynamics simulations
  - **Concern** The manuscript does not provide sufficient details on the simulation setup to assess reproducibility and convergence. The number of replicas per system is not stated. The equilibration protocol is described briefly. No convergence metrics are provided, such as root-mean-square deviation stabilization, block averaging, or sampling convergence of the specific observables analyzed. Given that the conclusions rely on subtle differences between systems, it is critical to demonstrate that the simulations have adequately sampled the relevant conformational space.
  - **Why it matters** Without evidence of convergence, the observed differences between WT and ME systems could be artifacts of insufficient sampling. This is particularly concerning given the small effect sizes reported.
  - **Resolution test** State the number of independent simulations per system. Provide convergence analysis for key observables, such as time evolution of deformation energies, contact maps, and helical parameters. Consider block averaging or other methods to estimate statistical uncertainties. If only single trajectories were run, acknowledge this limitation and discuss its impact on the conclusions.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretation of configurational entropy changes
  - **Claim pointer** The authors state that configurational entropy calculations show that CEBPB binding decreases entropy within the E2F1-DP1 binding site in WT, facilitating E2F1-DP1 binding, and that methylation alters this effect.
  - **Evidence pointer** Results section on configurational entropies; Table 3
  - **Concern** The configurational entropy calculations are based on Schlitter's formula applied to backbone P atoms. The interpretation of entropy changes as evidence for "stabilization" or "facilitation" of binding is not straightforward. Entropy changes alone do not determine binding free energy changes, and the relationship between backbone entropy and binding affinity is indirect. The differences reported are small (0.1-1.0 kcal/mol) and the standard deviations are not reported for these differences. The claim that CEBPB "stabilizes" the E2F1-DP1 binding site based on entropy alone is an overinterpretation.
  - **Why it matters** The cooperative mechanism proposed relies partly on these entropy arguments. If the entropy changes are not robustly linked to binding affinity, the proposed mechanism is weakened.
  - **Resolution test** Provide standard deviations for the entropy differences. Discuss the limitations of entropy calculations in predicting binding affinity. Consider computing binding free energies or potentials of mean force to more directly assess the impact of methylation on binding.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of figure presentation
  - **Affected element** Figure 2
  - **Evidence pointer** Figure 2 and its caption
  - **Issue** The caption for Figure 2 states that panel (c) shows mean values with standard errors approaching zero, but the figure itself does not display error bars. The reader cannot visually assess the variability.
  - **Required correction** Add error bars to Figure 2c or state in the caption that error bars are omitted because they are smaller than the symbol size.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Terminology consistency
  - **Affected element** Throughout the manuscript
  - **Evidence pointer** Title, Abstract, Results, Discussion
  - **Issue** The terms "breaks," "impede," "disrupt," and "perturb" are used interchangeably to describe the effect of methylation on cooperative recognition. These terms have different connotations and the manuscript would benefit from consistent, precise language.
  - **Required correction** Choose a single term that accurately reflects the strength of the observed effect and use it consistently throughout.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Data availability statement
  - **Evidence pointer** Data availability statement
  - **Issue** The data availability statement says that all data are available from the corresponding author upon request. For a computational study, it is best practice to deposit simulation trajectories, input files, and analysis scripts in a public repository.
  - **Required correction** Deposit the simulation input files, parameter files, and analysis scripts in a public repository such as Zenodo or Figshare, and provide the accession number in the manuscript.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Discussion of limitations
  - **Affected element** Discussion
  - **Evidence pointer** Discussion section
  - **Issue** The discussion does not explicitly address the limitations of the computational approach, such as force field accuracy, the use of a homology model for E2F1-DP1, and the absence of experimental validation.
  - **Required correction** Add a paragraph discussing the limitations of the study and the conditions under which the conclusions might not hold.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Reference to supplementary material
  - **Affected element** Results and Methods
  - **Evidence pointer** Multiple locations
  - **Issue** The manuscript frequently refers to supplementary figures and tables, but these were not provided for review. It is difficult to fully assess the results without them.
  - **Required correction** Ensure that all supplementary material is included with the submission and is properly referenced.

## Risk / unsupported claims
- The claim that methylation "breaks" cooperative DNA recognition is not fully supported by the data, as the authors themselves note that methylation leads to stronger overall TF-DNA complexation in interaction energy terms.
- The causal link between the observed MD differences and NDUFA13 downregulation in breast cancer is speculative and not supported by functional experiments.
- The statement that the identified hypermethylated region "may significantly contribute to the downregulation of the NDUFA13 gene" is presented as a conclusion but is framed as a hypothesis in the discussion.
- The claim that CEBPB binding "stabilizes" the E2F1-DP1 binding site based on configurational entropy changes is an overinterpretation, as entropy alone does not determine binding affinity.
- The bioinformatic identification of the model system is not quantitatively supported, making the relevance of the chosen region to actual NDUFA13 regulation unverifiable from the provided material.
- The assertion that methylation "damps" allosteric communication between the two TF binding sites is based on correlation analyses with small coefficients (<0.35), and the biological significance of these differences is unclear.

## Assessment against Nature-style criteria
- **Originality** The study addresses a question of potential interest, namely how promoter methylation affects cooperative TF binding through DNA structural changes. While individual components (methylation effects on DNA structure, TF cooperativity, MD simulations of protein-DNA systems) have been studied before, the specific combination and the focus on the NDUFA13 promoter region provide some novelty. However, the conceptual framework is not entirely new, and the findings largely confirm expectations based on prior work on methylation and DNA mechanics.
- **Scientific importance** The question of how methylation at promoter regions affects gene expression is of broad importance in epigenetics and cancer biology. If the proposed mechanism were robustly established, it could have implications for understanding gene regulation and for cancer diagnostics. However, the current evidence is computational and lacks experimental validation, limiting the immediate importance of the findings.
- **Interdisciplinary readership** The topic sits at the intersection of computational biophysics, epigenetics, and cancer biology. The manuscript is written in a way that is largely accessible to specialists in these fields, but the technical details of MD simulations and the various analysis methods may be challenging for readers outside computational biophysics. The broader significance for cancer biology is stated but not developed in sufficient depth to engage a wide audience.
- **Technical soundness** The MD simulation protocol is generally sound, with appropriate force fields and simulation lengths. The analysis methods are diverse and appropriate for the questions asked. However, the lack of convergence analysis and the small effect sizes with overlapping standard deviations raise concerns about the robustness of the conclusions. The bioinformatic analysis is described too briefly to assess its rigor.
- **Readability for nonspecialists** The manuscript is clearly written but assumes familiarity with MD simulations, DNA structural parameters, and transcription factor biology. The abstract is accessible, but the results and discussion sections would be challenging for nonspecialists. The figures are informative but require careful study.

## Recommendation posture
Currently not established from the provided evidence. The manuscript presents a plausible computational model for how promoter methylation might disrupt cooperative TF binding, but the central claims are not quantitatively robust, the bioinformatic foundation is not fully described, and the link to NDUFA13 downregulation is speculative. The authors should be encouraged to strengthen the evidence base, temper the conclusions, and provide additional analyses to support their claims. If the technical concerns regarding convergence, statistical significance, and model validation are addressed, the manuscript could become a valuable contribution to the field.