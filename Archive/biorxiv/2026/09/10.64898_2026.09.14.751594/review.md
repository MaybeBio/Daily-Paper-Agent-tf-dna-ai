## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods, figure legends not fully provided)
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical soundness based on the provided text
- **Shared manuscript claim summary** The authors propose that SMCHD1's weak, sequence-independent DNA binding activity, mediated by its hinge domain, is not required for initial recruitment to chromatin but is essential for stable retention, particularly at the inactive X chromosome, and that this retention supports full SMCHD1 function in gene repression and chromatin state regulation.
- **Visible evidence base** Abstract, main text narrative, methods sections for mouse generation, cell culture, ChIP-seq, RNA-seq, FLIM-FRET, FRAP, FFS, and lattice light-sheet microscopy. Figure references are cited but figure panels are not viewable.
- **Missing materials affecting confidence** Figure panels and legends, supplementary figures, extended data figures, supplementary tables, and statistical details within figures. Without these, quantitative assessment of effect sizes, variability, and data quality is limited.

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question in chromatin biology: how weak, non-sequence-specific DNA binding contributes to the function of chromatin-associated proteins. The authors employ a comprehensive suite of techniques, including a novel switchable mouse model, genomics, and advanced live-cell imaging, to dissect the role of SMCHD1's DNA binding activity. The central conclusion, that DNA binding stabilizes chromatin retention rather than promoting initial recruitment, is well-supported by the convergent evidence from multiple imaging modalities and genomic analyses. The work is technically ambitious and the findings are likely to be of broad interest. However, the manuscript's impact is currently constrained by the lack of visible data presentation, which prevents full evaluation of the robustness of the quantitative imaging analyses and the magnitude of the reported effects. The distinction between recruitment and retention, while conceptually clear, requires careful scrutiny of the experimental systems used, particularly given the known role of SMCHD1 in establishing X inactivation during development.

- **Who would be interested in the results, and why** This work will appeal to researchers studying epigenetic regulation, chromatin dynamics, X chromosome inactivation, and the structure-function relationships of SMC family proteins. The methodological integration of genomics with quantitative live-cell imaging provides a template for studying other chromatin regulators. The findings also have relevance for understanding the molecular basis of diseases associated with SMCHD1 mutations, such as facioscapulohumeral muscular dystrophy (FSHD) and Bosma arhinia microphthalmia syndrome (BAMS), as the R1867G variant is disease-associated.

- **Major strengths**
  1. The development of a switchable mouse model to replace endogenous SMCHD1 with wild-type or mutant versions is a significant technical achievement that allows for controlled, isogenic comparisons.
  2. The combination of multiple orthogonal imaging techniques (FRAP, FFS, FLIM-FRET, lattice light-sheet) provides a multi-scale view of SMCHD1 dynamics, from molecular binding to chromosome territory behavior.
  3. The study directly addresses a fundamental question about the role of weak DNA binding in chromatin protein function, moving beyond simple recruitment models.
  4. The use of spike-in normalization for ChIP-seq and the inclusion of a knockout control for RNA-seq strengthen the genomic conclusions.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data presentation and verification
- **Claim pointer** The manuscript claims that the R1867G mutation reduces SMCHD1 enrichment at the inactive X chromosome and increases its mobility, based on imaging and genomic data.
- **Evidence pointer** Figures 1, 2, 4, 5; Extended Data Figures 1, 2, 4, 5
- **Concern** The manuscript text describes quantitative results from immunofluorescence, ChIP-seq, FRAP, FFS, and lattice light-sheet experiments, but the actual data panels, statistical annotations, and figure legends are not provided in the submitted material. This makes it impossible to assess the magnitude of the reported differences, the variability between biological replicates, the robustness of the fitting procedures, or the appropriateness of the statistical tests. For example, the claim that R1867G shows a "substantially higher apparent diffusion coefficient" within the Xi (0.4046 vs 0.06843 µm²·s⁻¹) needs to be evaluated in the context of the spread of the data and the number of cells analyzed. Similarly, the ChIP-seq differential analysis identifying only one region with significantly increased occupancy in R1867G requires visualization of the data to understand the effect size and biological relevance.
- **Why it matters** The central thesis of the paper rests on quantitative comparisons between wild-type and mutant SMCHD1. Without access to the primary data representations, the reader cannot verify the strength of the evidence. This is a critical barrier to assessing the validity of the conclusions.
- **Resolution test** The authors must provide all main and extended data figures with complete legends, including exact p-values, effect sizes, confidence intervals, and sample sizes (n numbers) for each experiment. Representative images and quantification must be shown for all imaging modalities.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Conceptual framework and interpretation
- **Claim pointer** The manuscript states that DNA binding "supports maintenance, rather than initial recruitment, of chromatin-bound SMCHD1 both during interphase and mitosis."
- **Evidence pointer** Figures 4, 5, 6; Discussion
- **Concern** The distinction between "recruitment" and "maintenance" is a central conceptual pillar of the paper. However, the experimental system used is a switchable model where SMCHD1 is already expressed and has had time to associate with chromatin before the mutation is introduced. The FRAP and FFS experiments measure steady-state dynamics of an established population. The claim that DNA binding is dispensable for "initial recruitment" is inferred from the observation that the mutant still localizes to the Xi and that association rates are similar. This is an indirect inference. The lattice light-sheet experiments during mitosis are more directly relevant, as they track re-accumulation after cell division, but the text notes that the initial onset of accumulation is similar, with differences emerging later. This supports a maintenance role, but the term "initial recruitment" in the context of a post-mitotic cell is still a re-accumulation process, not a de novo recruitment to a naive chromatin state. The authors should more carefully define what they mean by "initial recruitment" and acknowledge the limitations of their system in directly testing this.
- **Why it matters** The paper's title and abstract emphasize this recruitment-versus-maintenance distinction. If the experimental system cannot fully separate these processes, the interpretation may be overstated. A more nuanced discussion of what the experiments can and cannot show is needed.
- **Resolution test** The authors should either provide direct experimental evidence for a recruitment step that is unaffected by the mutation (e.g., a pulse-chase experiment or a system where SMCHD1 is induced and its initial binding kinetics are measured) or temper the language in the abstract and discussion to reflect that the data support a role in retention/stabilization, with recruitment being inferred rather than directly demonstrated.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Functional significance and mechanistic depth
- **Claim pointer** The manuscript claims that impaired DNA binding produces a "hypomorphic" SMCHD1 state, weakening gene repression and chromatin-state regulation.
- **Evidence pointer** Figure 3; Extended Data Figure 3
- **Concern** The RNA-seq analysis shows that R1867G produces a partial transcriptional phenotype relative to full knockout. While this is consistent with a hypomorphic interpretation, the manuscript does not provide a clear mechanistic link between the observed changes in SMCHD1 dynamics (increased mobility, reduced Xi retention) and the specific transcriptional and chromatin-state changes. For example, are the genes affected in R1867G the same as those affected in the knockout? Is the reduced H3K27me3 at specific loci a direct consequence of reduced SMCHD1 retention, or could it be an indirect effect? The manuscript would be strengthened by a more detailed analysis of the relationship between SMCHD1 binding dynamics and functional outcomes at specific loci.
- **Why it matters** The paper aims to provide a framework for understanding how weak DNA binding supports function. To do this convincingly, it needs to show that the dynamic changes directly translate to functional deficits at the molecular level, not just at the level of global gene expression.
- **Resolution test** The authors should perform a more detailed integrative analysis, such as correlating changes in SMCHD1 occupancy (from ChIP-seq) with changes in gene expression and H3K27me3 at individual loci. They could also examine whether the genes most affected in R1867G are those with the greatest reduction in SMCHD1 binding.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and precision
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The abstract states that DNA binding "enables its stable retention on chromatin" but the introduction discusses the general problem of weak DNA binding in chromatin proteins. The connection between the specific findings and the broader framework could be made more explicit.
- **Required correction** Consider revising the abstract to more directly state how the findings on SMCHD1 provide a generalizable principle for other chromatin proteins with weak DNA binding activity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods, FRAP analysis
- **Evidence pointer** Methods, FRAP section
- **Issue** The FRAP analysis uses a "one binding state model" for Xi data and a "diffusion model" for nucleoplasmic data. The rationale for using different models in different compartments is not fully explained.
- **Required correction** Provide a brief justification for the model choice in each compartment, and discuss any potential limitations of this approach.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data interpretation
- **Affected element** Results, "Impaired DNA binding has limited effects on SMCHD1 occupancy outside the Xi"
- **Evidence pointer** Figure 2
- **Concern** The text notes that autosomal binding is "largely preserved" in R1867G cells. However, the differential analysis identified one region with increased occupancy. The biological significance of this single region is unclear.
- **Required correction** Discuss the potential significance of the single region with increased occupancy, or state clearly that it is likely a minor effect.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion mentions the possibility of secondary changes in Xi chromatin state contributing to the phenotype but does not fully explore this caveat.
- **Required correction** Expand the discussion of this limitation and consider whether any control experiments could address it.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure legends (not provided)
- **Evidence pointer** Location not provided
- **Issue** The text refers to statistical tests in figure legends, but these are not available for review.
- **Required correction** Ensure all figure legends include complete statistical details, including the specific test used, the number of biological and technical replicates, and the exact p-values.

## Risk / unsupported claims
- The claim that DNA binding is dispensable for "initial recruitment" is not directly supported by the experimental design, which measures steady-state dynamics and post-mitotic re-accumulation. This is an inference that should be clearly labeled as such.
- The claim that the R1867G variant produces a "hypomorphic" state is supported by the RNA-seq data, but the quantitative extent of the hypomorphism (e.g., the fraction of genes affected relative to knockout) is not assessable without the data figures.
- The statement that "DNA binding constrains SMCHD1 mobility and supports maintenance... both during interphase and mitosis" is supported by the imaging data, but the magnitude of the effects and the statistical confidence are not verifiable without the figures.
- The generalizability of the findings to "other chromatin proteins with sequence-independent DNA binding activity" is a reasonable speculation but is not directly tested in this manuscript.