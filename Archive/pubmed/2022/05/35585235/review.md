## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, and supplementary information descriptions
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical soundness as presented in the provided text
- **Shared manuscript claim summary** The authors propose that MCM complexes act as physical barriers that restrict cohesin-mediated loop extrusion, based on in vivo (mouse zygotes, HCT116 cells), in silico (polymer simulations), and in vitro (single-molecule imaging) evidence
- **Visible evidence base** Abstract, main text figures referenced (Figs. 1-4), extended data figures referenced, methods descriptions, supplementary figure/video descriptions
- **Missing materials affecting confidence** Actual figures, extended data panels, supplementary figures, and videos are not provided; specific numerical values for key measurements (e.g., peak strengths, p-values beyond those stated) are not fully detailed; raw sequencing data and analysis code are not accessible

## Reviewer
- **Overall assessment** This manuscript presents a compelling and multi-faceted investigation into the role of MCM complexes as barriers to cohesin-mediated loop extrusion. The combination of in vivo genomics, in silico modeling, and in vitro single-molecule biochemistry provides a strong triangulation of evidence. The findings are novel and have broad implications for understanding genome architecture, cohesin function, and the MCM paradox. However, several technical concerns regarding data presentation, statistical rigor, and the interpretation of the in vitro assays need to be addressed to fully establish the case.
- **Who would be interested in the results, and why** Chromatin biologists, researchers studying genome organization and loop extrusion, investigators focused on cohesin and SMC complexes, DNA replication scientists interested in MCM function, and computational biologists developing polymer models of chromatin. The work bridges multiple disciplines and provides a new paradigm for how DNA-bound machines can shape the 3D genome.
- **Major strengths**
  1. The study uses a powerful combination of complementary approaches (in vivo Hi-C/Micro-C, polymer simulations, and single-molecule imaging) to address a fundamental question.
  2. The identification of MCMs as a new class of loop extrusion barriers is conceptually novel and provides a potential explanation for the MCM paradox.
  3. The use of the mouse zygote system, with its transcriptional quiescence, elegantly disentangles direct effects of MCM loss on chromatin structure from indirect transcriptional effects.
  4. The single-molecule roadblock assay provides direct physical evidence for MCMs impeding cohesin translocation.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that MCM loss results in increased CTCF-anchored loop strength and TAD boundary insulation in mouse zygotes (Fig. 1d, f).
- **Evidence pointer** Fig. 1d, f; Extended Data Fig. 3a-c; Methods: snHi-C data analysis
- **Concern** The snHi-C data are described as sparse, yet the authors use 12,000 loop coordinates from mouse embryonic fibroblasts to quantify aggregate peaks. The manuscript does not provide sufficient detail on how the sparsity of snHi-C data affects the statistical power and reliability of these aggregate measurements. Specifically, the number of nuclei per condition (n=13-16) is relatively small, and the manuscript lacks a clear demonstration that the observed differences are not driven by a few outlier nuclei or by technical variation between libraries.
- **Why it matters** The central in vivo conclusion rests on the robustness of these snHi-C measurements. If the aggregate peak and TAD strength differences are not statistically robust given the data sparsity, the primary claim that MCMs impede loop extrusion in vivo is weakened.
- **Resolution test** Provide a detailed power analysis or bootstrap resampling of nuclei to demonstrate that the observed differences are stable. Show per-nucleus distributions of peak/TAD strength, not just aggregate averages. Include a clear statement on the minimum number of nuclei required to detect the observed effect size.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that simulations with MCMs as semi-permeable barriers quantitatively reproduce the experimental peak strengths and Pc(s) curves (Fig. 3b, d).
- **Evidence pointer** Fig. 3b-d; Extended Data Fig. 6e-h; Supplementary Figs. 2-5; Methods: Loop extrusion simulations
- **Concern** The parameter fitting procedure is described qualitatively ("we found a narrow range of values"). The manuscript does not provide a formal parameter estimation or uncertainty quantification. It is unclear how unique the identified parameter set is, and whether other combinations of MCM density, permeability, cohesin processivity, and cohesin density could equally well reproduce the data. The statement that MCM permeability was "essential" needs a more rigorous demonstration, such as a likelihood profile or a comparison of model fits with and without MCM barriers.
- **Why it matters** The in silico model is a key pillar of the paper, used to interpret the in vivo data and make mechanistic predictions. Without rigorous parameter identifiability analysis, the claim that the model uniquely supports the semi-permeable barrier hypothesis is not fully established.
- **Resolution test** Perform a systematic parameter sweep and present the goodness-of-fit landscape. Show that the identified parameter set is a unique global optimum, or at least that all equally good fits share the same qualitative features (e.g., semi-permeable MCMs). Provide confidence intervals for key parameters.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the YFD motif in human MCM3 causes cohesin pausing, based on the chimeric MCM-YFD experiments (Fig. 4c-e).
- **Evidence pointer** Fig. 4c-e; Methods: Single-molecule imaging and data analysis
- **Concern** The single-molecule assay uses a chimeric yeast MCM complex with a human MCM3 YFD motif. The manuscript does not adequately address whether the observed pausing is due to a specific interaction between the YFD motif and cohesin, or whether it could be a non-specific effect of the chimeric protein on MCM structure or DNA binding. The authors should include a control with a scrambled or mutated YFD motif to demonstrate specificity.
- **Why it matters** The claim that MCMs are "active" barriers with specific binding sites is a major conceptual advance. If the pausing is non-specific, the interpretation of MCMs as active barriers is weakened, and the connection to the in vivo mechanism becomes less clear.
- **Resolution test** Include a control experiment with a mutated YFD motif (e.g., YFD to AAA) in the same chimeric MCM background. Show that this mutant does not induce pausing, demonstrating sequence-specificity.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors suggest that MCMs determine the genomic sites at which sister chromatid cohesion is established.
- **Evidence pointer** Discussion section
- **Concern** This is a speculative claim that goes beyond the data presented. The manuscript does not provide any direct evidence linking MCM-barrier-mediated loop restriction to the establishment of sister chromatid cohesion. While this is an interesting hypothesis, it is presented with insufficient caveats and could be misinterpreted as a finding rather than a speculation.
- **Why it matters** Overinterpretation of results can mislead the field and dilute the impact of the solid findings presented. The distinction between data-supported conclusions and hypotheses should be crystal clear.
- **Resolution test** Soften the language in the discussion to clearly frame this as a speculative hypothesis that requires future testing. Alternatively, add a preliminary experiment (e.g., cohesion establishment assay in MCM-depleted cells) to provide initial support.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is dense and uses field-specific jargon (e.g., "TAD boundary insulation", "semi-permeable barriers") without brief definitions. A general reader may struggle to grasp the significance of the findings.
- **Required correction** Add a brief explanatory phrase for key terms, e.g., "topologically associating domains (TADs), which are self-interacting genomic regions" and "semi-permeable, meaning some cohesin complexes can pass through".

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods: snHi-C data analysis
- **Evidence pointer** Methods: snHi-C data analysis
- **Issue** The description of the normalization of snHi-C data is incomplete. The authors state "Heat maps were normalized to an equal number of cis contacts" but do not specify the exact method (e.g., iterative correction, coverage-based normalization).
- **Required correction** Provide the specific normalization algorithm and software version used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods: RNA-seq analysis
- **Evidence pointer** Methods: RNA-seq analysis
- **Issue** The differential expression analysis uses Sleuth with a Wald test, but the manuscript does not state the significance threshold (e.g., q-value < 0.05) or how multiple testing correction was applied.
- **Required correction** State the false discovery rate threshold and the number of genes tested.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Fig. 4d
- **Evidence pointer** Fig. 4d
- **Issue** The probability of cohesin passing MCM is reported, but the number of independent experiments and the total number of events analyzed are not stated in the main text.
- **Required correction** Add the number of biological replicates and total events to the figure legend or methods.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of the MCM paradox and its implications for Meier-Gorlin syndrome is brief and could be expanded to engage a broader clinical audience.
- **Required correction** Add one or two sentences explaining how these findings might inform future studies on Meier-Gorlin syndrome pathology.

- **Technical failings that need to be addressed before the case is established**
  R1-M1 (snHi-C statistical robustness), R1-M2 (simulation parameter identifiability), R1-M3 (YFD motif specificity control)

- **Assessment against Nature-style criteria**
  - **Originality**: High. The concept of MCMs as barriers to loop extrusion is novel and challenges the prevailing view that CTCF is the primary barrier. The study opens a new avenue of research into how DNA-bound machines shape genome architecture.
  - **Scientific importance**: High. The findings have broad implications for understanding genome organization, cohesin function, DNA replication, and the MCM paradox. The potential link to sister chromatid cohesion establishment is particularly significant.
  - **Interdisciplinary readership**: Good. The work will appeal to molecular biologists, biophysicists, computational biologists, and clinicians interested in developmental disorders. The multi-technique approach is a strength.
  - **Technical soundness**: Currently not fully established. The three major concerns above (snHi-C statistics, simulation parameter identifiability, YFD specificity) need to be addressed. The in vitro assay is elegant but requires a critical control.
  - **Readability for nonspecialists**: Adequate but could be improved. The abstract and introduction are dense, and some terms are not defined for a general audience. The figures are likely to be complex, but the text is generally clear.

- **Recommendation posture** Supportive if technical concerns are resolved. The core hypothesis is novel and the multi-pronged approach is impressive. However, the statistical robustness of the in vivo data, the uniqueness of the simulation parameters, and the specificity of the YFD effect must be rigorously demonstrated. If these concerns are adequately addressed, this work would be a significant contribution to the field.

## Risk / unsupported claims
- The claim that MCMs determine the genomic sites of sister chromatid cohesion establishment is speculative and not directly supported by the data presented.
- The statement that MCMs are "active" barriers with binding sites is only supported by a single chimeric construct without a specificity control.
- The quantitative agreement between simulations and experiments is claimed but not rigorously demonstrated due to lack of parameter uncertainty analysis.
- The generalizability of the findings from mouse zygotes and HCT116 cells to all cell types is not established, though the authors do not overclaim this.
- The claim that MCM loss has "little effect" on Pc(s) below 1 Mb is based on visual inspection of curves; a quantitative comparison with error bars is needed.