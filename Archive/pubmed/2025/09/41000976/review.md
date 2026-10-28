## Review setup
- **Input scope** Full manuscript text (abstract, main text sections, supplementary figure/table references) as provided by the user
- **Assessment boundary** Scientific and technical evaluation of the claims, methods, and evidence as presented in the supplied text. No assessment of code, data, or supplementary materials beyond what is referenced in the text.
- **Shared manuscript claim summary** The authors present RFdiffusion3 (RFD3), a diffusion model that generates all-atom protein structures in the context of non-protein molecules including ligands, nucleic acids, and other atoms. The model is claimed to outperform prior approaches on in silico benchmarks at reduced computational cost, and to enable experimental design of DNA-binding proteins and cysteine hydrolases with measurable activity.
- **Visible evidence base** Main text descriptions of architecture, training data, in silico benchmarks (protein binders, DNA binders, small molecule binders, enzyme scaffolds), and two experimental validations (one DNA binder with EC50, one esterase with Kcat/Km). Supplementary figures and tables are referenced but not provided.
- **Missing materials affecting confidence** Supplementary figures (S1-S12), supplementary tables (S1), detailed methods, benchmark definitions, experimental protocols, raw data, and code. The experimental section lacks statistical detail, replicate numbers, and negative control descriptions.

## Reviewer
- **Overall assessment** This manuscript describes a substantial advance in generative protein design, with a conceptually clean all-atom diffusion formulation that simplifies conditioning and enables joint sampling of protein and non-protein coordinates. The in silico benchmarks are broad and the experimental validations, while limited in number, demonstrate real functional outcomes. However, the evidence as presented is incomplete in several critical areas. The experimental section is thin, with only one DNA binder and one enzyme reported, and the text does not provide sufficient detail on screening stringency, hit rates, or reproducibility. The in silico benchmarks rely heavily on AF3-based metrics, and the relationship between these metrics and experimental success is not critically examined. The claim of "unprecedented control" is supported by the architecture but the quantitative limits of that control are not fully characterized. The computational efficiency claim is clear and well supported by the architecture description. Overall, the work is likely to be of high interest to the protein design community, but the current evidence base is insufficient to fully establish the breadth of the claims made.

- **Who would be interested in the results, and why** Protein engineers and computational biologists working on de novo binder design, enzyme design, and nucleic acid binding protein design. The all-atom formulation and joint sampling capability will also interest researchers developing generative models for molecular systems beyond proteins. The reduced computational cost makes the method accessible to a wider range of laboratories, which broadens its potential impact.

- **Major strengths**
  1. The all-atom diffusion formulation is conceptually elegant and removes the need for hybrid residue-atom representations, simplifying the specification of atom-level constraints.
  2. The architecture is lean (168M parameters) and the reported speedup over RFdiffusion2 is substantial and likely to be practically important.
  3. The breadth of conditioning modalities (hydrogen bonding, burial, center of mass, symmetry) is impressive and directly addresses known limitations of prior methods.
  4. The experimental validation, while limited, demonstrates that the method can produce functional DNA binders and enzymes, which is a high bar.
  5. The benchmark against RFdiffusion2 on the AME set with improvement on 37/41 cases is a clear and quantitative comparison.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental evidence sufficiency
- **Claim pointer** "we demonstrate the broad applicability of RFD3 by designing and experimentally characterizing DNA binding proteins and cysteine hydrolases"
- **Evidence pointer** Section "Experiments", Figure 4, Figure S7, Figure S8
- **Concern** The experimental validation is limited to one DNA-binding protein and one enzyme. For the DNA binder, a single construct with an EC50 of 5.89 ± 2.15 μM is reported. For the enzyme, 35 multi-turnover designs out of 190 screened are reported, with the best Kcat/Km = 3557. The text does not provide the number of independent replicates, the distribution of activities across the 35 designs, or the criteria used to define "multi-turnover." No negative controls (e.g., designs predicted to be inactive) are described. The claim of "broad applicability" is not supported by two examples, particularly when the in silico benchmarks cover five protein targets, three DNA sequences, and four small molecules.
- **Why it matters** The central claim of the paper is that RFD3 enables functional design across diverse targets. Two examples, without detailed characterization, are insufficient to establish this. The reader cannot assess whether the reported successes are representative or exceptional.
- **Resolution test** Provide additional experimental validation, either more targets or more detailed characterization of the reported designs. Include replicate numbers, hit rate definitions, negative controls, and a discussion of how the reported successes compare to failure cases.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Benchmark validity
- **Claim pointer** "RFD3 outperforms RFD1 for 4/5 targets when considering all backbones; notably, when clustering the generated backbones (by TM-score 0.6), we find that RFD3 finds significantly more unique solutions to each binding problem"
- **Evidence pointer** Section "Design of protein-binding proteins", Figure 3, Figure S2
- **Concern** The in silico success criteria rely on AF3 prediction confidence metrics (inter-chain pAE, binder pTM, RMSD). The relationship between these AF3-based metrics and experimental success is not established in this manuscript. The authors do not report how many of the in silico "successful" designs were tested experimentally, or whether the AF3 metrics correlate with the observed experimental outcomes. The comparison to RFD1 uses a single set of thresholds, and it is unclear whether these thresholds were chosen a priori or tuned to favor RFD3.
- **Why it matters** If the AF3-based metrics are not predictive of experimental success, the benchmark results may not reflect real-world utility. The reader needs to know whether the improved in silico metrics translate to improved experimental outcomes.
- **Resolution test** Provide a calibration of the AF3 metrics against experimental results, either from this study or from prior work. Report the number of in silico successes that were experimentally tested and the concordance between prediction and outcome. Justify the choice of thresholds.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalization of joint sampling claim
- **Claim pointer** "the simultaneous generation of protein backbone and sidechains enables the backbone to better encode residues that make productive atomic contacts with target molecules"
- **Evidence pointer** Section "Experiments", Figure S9
- **Concern** The claim that joint backbone-sidechain generation improves contact encoding is supported only by a post-hoc analysis showing that MPNN recapitulates some designed interactions. This is an indirect test. The authors do not directly compare RFD3 to a version of the model that generates backbone only and relies on MPNN for sidechains, which would be the appropriate control. The text states that "fixing these interactions and only redesigning the remaining residues does not significantly affect the refolding metrics," but the metrics used are not specified and the comparison is not shown in the main text.
- **Why it matters** The joint generation of backbone and sidechains is a key architectural choice. If the benefit is marginal, the added complexity may not be justified. The current evidence is suggestive but not conclusive.
- **Resolution test** Perform an ablation study comparing RFD3 to a backbone-only generation mode followed by MPNN sidechain placement, using the same benchmarks and experimental readouts. Report the difference in success rates and contact quality.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Training data leakage and benchmark contamination
- **Claim pointer** "We trained on all complexes in the Protein Data Bank (PDB) including protein-protein, protein-small molecule, and protein-DNA interface design tasks, as well as scaffolding functional motifs (Table S1) and a set of high quality AlphaFold2 (AF2) distillation structures"
- **Evidence pointer** Section "RFdiffusion3 architecture and training"
- **Concern** The training set includes PDB entries through December 2024. The benchmark targets (PD-L1, InsulinR, IL-7Ra, Tie2, IL-2Ra) are well-studied proteins with many PDB structures. It is unclear whether the benchmark evaluation structures or closely related complexes were included in the training set. The AME benchmark uses 41 active sites from the PDB, and it is not stated whether these were excluded from training. The DNA sequences used for benchmarking were stated to be excluded from training, but the small molecule ligands and their complexes are not discussed in this context.
- **Why it matters** If the benchmark targets or their close homologs were in the training set, the reported performance may be inflated. The reader cannot assess the generalization of the method without knowing the overlap between training and evaluation data.
- **Resolution test** Provide a detailed analysis of the overlap between training structures and benchmark targets, including sequence and structural similarity. State explicitly which benchmark structures or complexes were excluded from training.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Training procedure
- **Evidence pointer** Section "RFdiffusion3 architecture and training"
- **Issue** The hierarchical training procedure is described in one sentence. The text states "pre-train on a mix of AF2 predictions and PDB, then fine-tune on a larger fraction of DNA and PPI" but does not specify the proportions, the number of steps, or the learning rate schedule.
- **Required correction** Provide a more detailed description of the training schedule, including data mixing ratios, number of steps, and any curriculum.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** DNA binder EC50
- **Evidence pointer** Section "Experiments", Figure 4
- **Issue** The EC50 of 5.89 ± 2.15 μM is reported without the number of replicates or the fitting method. The error bar is large, and it is unclear whether this represents a single experiment or multiple independent measurements.
- **Required correction** Report the number of independent replicates, the fitting procedure, and the confidence interval.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Comparison fairness
- **Affected element** Small molecule binder benchmark
- **Evidence pointer** Section "Designing small molecule binders", Figure 3c
- **Concern** The comparison to RFdiffusionAA is described as "significantly outperforms" but the text does not state whether the same AF3 evaluation criteria were used for both methods, or whether the RFdiffusionAA results were taken from the original publication or re-computed.
- **Required correction** Clarify the source of the RFdiffusionAA benchmark results and confirm that identical evaluation criteria were applied.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "De novo" claim
- **Evidence pointer** Title and Abstract
- **Issue** The title uses "De novo Design" but the method is trained on PDB structures and AF2 predictions, and the experimental validation involves screening multiple designs. The term "de novo" is used loosely here, as the method is not generating proteins from first principles but rather sampling from a learned distribution.
- **Required correction** Consider using a more precise term such as "generative design" or clarify the meaning of "de novo" in this context.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Model availability
- **Evidence pointer** Section "RFdiffusion3 architecture and training"
- **Issue** The text does not state whether the model weights, training code, or inference code will be made publicly available. Given the impact of RFdiffusion1 and RFdiffusion2, this information is important for the community.
- **Required correction** Add a data and code availability statement.

## Risk / unsupported claims
- The claim of "broad applicability" is not supported by the limited experimental evidence (one DNA binder, one enzyme).
- The claim that joint backbone-sidechain generation improves contact encoding is not directly tested with an appropriate ablation.
- The in silico benchmark results may be inflated if training and evaluation sets overlap, and this overlap is not analyzed.
- The relationship between AF3-based in silico success metrics and experimental outcomes is not established.
- The statement "RFD3 produces novel and diverse folds" (Section "Enzyme design") is not quantified or compared to any baseline.
- The claim of "unprecedented control" over atom-level constraints is qualitative and not benchmarked against any quantitative measure of control precision.
- The text states "we found that RFD3 was able to generate scaffolds that house the active site geometry in both subunits in all cases" for symmetric enzyme design, but the number of cases and the evaluation criteria are not specified in the main text.