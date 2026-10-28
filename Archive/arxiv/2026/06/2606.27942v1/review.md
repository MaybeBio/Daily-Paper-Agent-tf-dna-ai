## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided.
- **Assessment boundary** Scientific soundness, methodological clarity, validity of claims relative to the presented evidence, and suitability for a high-impact general audience. The review is based solely on the provided text; figures, tables, and supplementary information are referenced but not directly examined.
- **Shared manuscript claim summary** The authors propose a coevolution-aware ancestral sequence reconstruction (ASR) framework that combines standard site-independent phylogenetic inference with Direct Coupling Analysis (DCA). They claim this approach improves reconstruction accuracy and biological plausibility compared to site-independent methods, particularly when ancestral sequences are epistatically constrained. They introduce a DCA-based forward simulator for benchmarking and apply the method to β-lactamases and DNA-binding domains.
- **Visible evidence base** Text descriptions of results (Figures 1-5 referenced), methods sections, and references to supplementary figures (S1-S10). No actual data, figures, or tables are visible in the provided material.
- **Missing materials affecting confidence** All figures, tables, and supplementary information are absent. This includes the main results figures (Figs. 1-5), the table of variable definitions (Table 1), and all supplementary figures (S1-S10). Quantitative results, statistical analyses, and parameter values are not directly verifiable.

## Reviewer
- **Overall assessment** The manuscript addresses a significant and timely problem in ancestral sequence reconstruction: the neglect of epistatic interactions. The proposed two-step approach (site-independent posterior sampling followed by DCA-informed reshuffling) is conceptually elegant and computationally tractable. The development of a DCA-based forward simulator for benchmarking is a valuable contribution. However, the manuscript as presented has several critical gaps. The most significant concern is the lack of a clear, quantitative demonstration that the coevolution-aware method outperforms existing approaches in a way that would justify its adoption. The claims of improved structural plausibility and functional relevance rest on proxy metrics (pDLLDT, RMSD) that are described but not rigorously compared against baselines or statistical significance. The choice of a single tree topology and the limited exploration of parameter space (e.g., temperature T, number of samples M) raise questions about the robustness and generalizability of the findings. The writing is generally clear but occasionally imprecise, and the motivation for specific methodological choices (e.g., the termination criterion for the reshuffling procedure) is not fully justified. Overall, the core idea is promising, but the evidence presented is insufficient to establish the method's superiority or practical utility.
- **Who would be interested in the results, and why** Researchers in molecular evolution, phylogenetics, and computational biology would be the primary audience. Specifically, those working on ancestral sequence reconstruction, protein engineering, and the study of epistasis would find the framework relevant. The benchmarking approach using a DCA-based simulator could also be of interest to method developers. The potential application to experimental resurrection of ancestral proteins would attract experimentalists in biochemistry and structural biology.
- **Major strengths**
    1.  The core conceptual contribution is strong: explicitly addressing the site-independence assumption in ASR using a biophysically interpretable model (DCA) is a logical and important step forward.
    2.  The proposed algorithm is computationally tractable, avoiding the exponential complexity of exact inference under a DCA prior.
    3.  The development of a DCA-based forward simulator for benchmarking is a significant and useful contribution, addressing a critical gap in the field.
    4.  The analysis of different evolutionary regimes (via μ_gen) and root mutability (via CDE) is thoughtful and provides a more nuanced view of ASR performance than is typical.
    5.  The discussion of the limitations of MAP estimates (over-optimization, atypical properties) is insightful and well-articulated.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence for central claim
    - **Claim pointer** The central claim is that the coevolution-aware ASR framework "improves ancestral sequence reconstruction when the true ancestor has strong epistatic constraints" and yields ensembles that are "both phylogenetically consistent and statistically compatible with natural protein families."
    - **Evidence pointer** Results Section II.5, Figure 4, Figure 5
    - **Concern** The manuscript does not provide a clear, quantitative comparison between the coevolution-aware method and the site-independent baseline. The text describes qualitative differences in DCA energy and Hamming distance but does not present statistical tests, effect sizes, or a clear metric for "improvement." For example, it is stated that the "higher-likelihood cluster of S_anc^DCA simultaneously approaches the GT in both Hamming distance and DCA energy, outperforming their site-independent counterparts," but no numbers, confidence intervals, or significance tests are provided. The claim of "improvement" is therefore not rigorously established.
    - **Why it matters** The central contribution of the paper is the claimed improvement of ASR. Without a quantitative and statistically robust demonstration of this improvement, the method's value proposition is unclear. A reader cannot assess whether the added complexity of the reshuffling step is justified by a meaningful gain in accuracy or biological plausibility.
    - **Resolution test** Provide a quantitative comparison (e.g., mean and standard deviation of Hamming distance to GT, DCA energy, pLDDT, RMSD) between S_anc, S_anc^DCA, and MAP, across all root sequences and μ_gen values. Include appropriate statistical tests (e.g., paired t-tests or Wilcoxon signed-rank tests) to demonstrate significant differences. Show these results in a clear figure (e.g., boxplots or line plots with error bars).
    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Methodological justification and robustness
    - **Claim pointer** The method's key parameters (temperature T, number of samples M, termination criterion) are presented as heuristics without sensitivity analysis.
    - **Evidence pointer** Methods Section IV.6
    - **Concern** The choice of T=0.2, M=1000, and the termination criterion (2^(M·Γ/2) attempts) are stated without justification or sensitivity analysis. The performance of the reshuffling procedure is likely highly dependent on these parameters. For instance, a different temperature could lead to either insufficient exploration (too high T) or over-conservation of the initial sample (too low T). The termination criterion is particularly opaque and its rationale is not explained.
    - **Why it matters** For a method to be adopted, its parameters must be well-justified and its performance must be robust to reasonable variations in those parameters. Without this analysis, it is impossible to know if the reported results are an artifact of a specific parameter choice or a general property of the method.
    - **Resolution test** Perform a sensitivity analysis for T (e.g., T = 0.05, 0.1, 0.2, 0.5, 1.0) and M (e.g., 100, 500, 1000, 5000) on at least one root sequence, showing the impact on Hamming distance to GT and DCA energy of the final ensemble. Justify the termination criterion with a clear explanation or a convergence analysis.
    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Validation of benchmarking framework
    - **Claim pointer** The DCA-based forward simulator is claimed to be a "realistic" and "biologically grounded" benchmarking tool.
    - **Evidence pointer** Results Section II.3, Methods Section IV.3
    - **Concern** The manuscript does not validate that the DCA-based forward simulator produces evolutionary trajectories that are realistic. While it is stated that the simulator reproduces site-wise and pairwise statistics, this is a property of the DCA model itself. The key question is whether the *dynamics* of evolution under this simulator are realistic. For example, does the simulator produce realistic levels of homoplasy, or realistic distributions of branch-specific substitutions? The manuscript also does not compare the simulator's output to real sequence data in a quantitative way.
    - **Why it matters** The benchmarking framework is a key contribution, but its validity rests on the assumption that it generates data that is representative of real protein evolution. If the simulator is unrealistic, then the conclusions drawn from benchmarking against it may not transfer to real-world ASR problems.
    - **Resolution test** Provide a validation of the simulator, e.g., by comparing the distribution of pairwise distances, site-specific substitution patterns, or other summary statistics of simulated leaves to those of the real β-lactamase alignment. Discuss the limitations of the simulator as a model of real evolution.
    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Generalizability and scope of results
    - **Claim pointer** The manuscript claims the method is applicable to "any alignment of candidate ancestors sampled from a site-independent posterior" and demonstrates it on two protein families.
    - **Evidence pointer** Results Sections II.5, II.6, and SI
    - **Concern** The main results are presented for the β-lactamase family, with DNA-binding domains relegated to the SI. The choice of these two families, and the specific roots selected within them, may not be representative. The manuscript does not discuss how the performance of the method might vary with family size, sequence diversity, or the strength of epistatic constraints. The claim of general applicability is therefore not well-supported.
    - **Why it matters** A method that works well on one or two families may not work well on others. The practical utility of the method depends on its robustness across a wide range of protein families.
    - **Resolution test** Include the DNA-binding domain results in the main text, or add a third, structurally and evolutionarily distinct protein family to the analysis. Discuss the properties of the families that might influence the method's performance.
- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity of writing
    - **Affected element** Introduction, Section I
    - **Evidence pointer** "Most studies 67 ; 8 ; 44 ; 53 ; 51 focus on the maximum-a-posteriori (MAP) estimate..."
    - **Issue** The sentence is grammatically awkward and the citation style is unusual.
    - **Required correction** Rephrase for clarity, e.g., "Most studies (67, 8, 44, 53, 51) focus on the maximum-a-posteriori (MAP) estimate..." and ensure consistent citation formatting.
    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Methodological detail
    - **Affected element** Methods Section IV.5
    - **Evidence pointer** "Rather than inferring the global mutation rate μ via maximization of the phylogenetic likelihood, we adopt a calibration procedure based on pairwise sequence divergence."
    - **Issue** The calibration procedure is described, but the rationale for choosing it over a more standard maximum-likelihood approach is not given. Is it for computational efficiency? Does it perform better?
    - **Required correction** Add a sentence explaining the motivation for this choice and, if possible, a comparison with the standard approach.
    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Interpretation of results
    - **Affected element** Results Section II.6
    - **Evidence pointer** "For GT5, however, the lower-bound RMSD is itself very large, indicating that ESMFold cannot reliably reproduce the AlphaFold structure for this root..."
    - **Issue** This is an important caveat, but it is only mentioned in passing. The implications for the interpretation of GT5 results should be discussed more explicitly.
    - **Required correction** Expand on this point, explaining that the structural analysis for GT5 is unreliable and that conclusions drawn from it should be treated with caution.
    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Reproducibility
    - **Affected element** Methods Section IV.1
    - **Evidence pointer** "For a given seed of sequences of interest, we generate a Multiple Sequence Alignment (MSA) and infer its phylogenetic tree using FastTree 45."
    - **Issue** The process of generating the MSA is not described. Which alignment tool was used? What parameters?
    - **Required correction** Specify the alignment software and parameters used.
- **Technical failings that need to be addressed before the case is established**
    - R1-M1: Lack of quantitative evidence for the central claim of improved reconstruction.
    - R1-M2: Lack of sensitivity analysis for key method parameters.
    - R1-M3: Lack of validation for the proposed benchmarking simulator.
- **Assessment against Nature-style criteria**
    - **Originality** The idea of combining DCA with ASR is not entirely new, but the specific two-step approach (posterior sampling followed by reshuffling) and the use of a DCA-based forward simulator for benchmarking are novel contributions. The work is original in its synthesis of existing ideas.
    - **Scientific importance** The problem of epistasis in ASR is of fundamental importance. If the method is proven to work, it could significantly improve the accuracy and reliability of ancestral reconstructions, with implications for understanding protein evolution and function. The importance is high, but contingent on the evidence.
    - **Interdisciplinary readership** The topic is of interest to evolutionary biologists, computational biologists, and biochemists. The methods are clearly described and should be accessible to these groups. The potential applications to protein engineering and experimental resurrection broaden the appeal. The readership is likely to be broad within these fields.
    - **Technical soundness** The core algorithmic idea is sound and the computational approach is tractable. However, the technical soundness of the *claims* is undermined by the lack of quantitative validation and sensitivity analysis. The benchmarking framework is clever but its validity is not established.
    - **Readability for nonspecialists** The abstract is clear and accessible. The introduction provides good context. The results and methods sections are more technical but generally well-written. The manuscript is readable for a scientifically literate audience, though some familiarity with phylogenetics and statistical physics is assumed.
- **Recommendation posture** Currently not established from the provided evidence. The core idea is promising and the work has the potential to be a significant contribution. However, the central claims are not supported by the quantitative evidence presented. The manuscript requires major revisions, including a rigorous quantitative comparison against baselines, a sensitivity analysis of key parameters, and a validation of the benchmarking framework, before its conclusions can be considered established.

## Risk / unsupported claims
- The claim that the coevolution-aware method "improves ancestral sequence reconstruction" is unsupported by the provided evidence, as no quantitative comparison or statistical analysis is presented.
- The claim that the DCA-based forward simulator is "realistic" and "biologically grounded" is not validated against real data or established evolutionary models.
- The claim that the method "bridges the gap between single-sequence MAP reconstruction and unconstrained posterior sampling" is a reasonable interpretation but is not directly demonstrated.
- The claim that the method is applicable to "any alignment of candidate ancestors" is an overstatement, as it is only tested on two families and the dependence on family properties is not explored.
- The claim that low DCA energy is a "reliable proxy for functionality" is based on prior literature but is not directly tested in this manuscript.