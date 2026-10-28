## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods, figure legends not provided)
- **Assessment boundary** Scientific content, technical rigor, and claims as presented in the provided text. Figures, tables, and supplementary materials referenced but not available for direct inspection.
- **Shared manuscript claim summary** The authors map the functional evolution of five mouse developmental enhancers by testing orthologous sequences from 480 mammalian genomes with MPRA, develop a deep learning-guided reconstitution strategy to identify causal mutations, and demonstrate asymmetric predictability of enhancer ablation versus enhancement.
- **Visible evidence base** Abstract, main text (Results, Discussion), Methods section. Figure references (Fig. 1-5, Extended Data Figs. 1-3, Supplementary Figs. S1-S11) and tables (Table S1-S2) are cited but not provided.
- **Missing materials affecting confidence** All figures, tables, supplementary information, and extended data. Statistical details, raw data, model performance metrics, and validation results are referenced but not directly assessable.

## Reviewer
- **Overall assessment** This manuscript presents a conceptually ambitious and technically sophisticated approach to dissecting mammalian enhancer evolution at nucleotide resolution. The combination of ancestral sequence resurrection, massively parallel reporter assays, and deep learning-guided mutagenesis is novel and potentially impactful. However, the central claims regarding the asymmetry between ablation and enhancement predictability, and the broader conclusions about enhancer evolution, rest on analyses that cannot be fully evaluated from the text alone. The manuscript would benefit from clearer presentation of quantitative results and more explicit discussion of model limitations.
- **Who would be interested in the results, and why** Evolutionary biologists studying cis-regulatory evolution, developmental biologists interested in enhancer function, computational biologists developing sequence-to-function models, and synthetic biologists seeking to engineer gene expression. The demonstration that deep learning models can guide enhancer editing with asymmetric success has implications for both understanding natural evolution and for therapeutic or biotechnological applications.
- **Major strengths** 1) The scale of the phylogenetic sampling (480 genomes) is unprecedented for functional enhancer assays. 2) The combination of ancestral reconstruction with deep learning-guided mutagenesis is methodologically innovative. 3) The identification of epistasis in evolutionary trajectories addresses a fundamental question in molecular evolution. 4) The asymmetry between ablation and enhancement predictability is a practically important finding for genome engineering.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** The manuscript's central claims about the decoupling of sequence and functional conservation, the role of specific mutations in gain-of-function, and the asymmetry in model-guided editing all require the figures and supplementary data to be properly evaluated. The text alone provides insufficient quantitative detail to assess the robustness of these conclusions.
- **Assessment against Nature-style criteria** 
- **Recommendation posture** Supportive if technical concerns are resolved and the full dataset supports the claims as presented.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim summary** The authors claim that "ablation of enhancer function required as few as one to seven mutations, whereas enhancement was constrained by element-specific activity ceilings" based on model-guided editing of five enhancers.
- **Evidence pointer** Results section "Model-guided tuning of endogenous activity reveals asymmetry between enhancement and ablation"; Fig. 5; Fig. S10-S11
- **Concern** The asymmetry claim is central to the paper's practical implications, but the text provides no quantitative details on how activity ceilings were determined, how many mutations were tested per enhancer, or how the "ceiling" was distinguished from model failure. The claim that enhancement "saturates" could reflect model limitations rather than biological constraints, and the authors acknowledge this but do not provide sufficient analysis to distinguish these possibilities.
- **Why it matters** If the asymmetry is primarily a model artifact, the conclusion about the "reliability of current sequence-to-function models" would be overstated. The practical guidance for enhancer engineering depends on understanding whether the ceiling is biological or computational.
- **Resolution test** Provide quantitative data on the distribution of activity changes across all tested mutations, statistical comparisons between ablation and enhancement trajectories, and analysis of whether the activity ceiling correlates with any sequence features. Show that the ceiling is not simply a function of the model's training distribution.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validation
- **Claim summary** The authors state that ChromBPNet, a model trained on chromatin accessibility, "exhibited the strongest correspondence with MPRA measurements" among evaluated deep learning models.
- **Evidence pointer** Results section "Synthetic reconstitution of gain-of-function trajectories reveals epistasis and TFBS affinity tuning"; Supplementary Note 1; Extended Data Figs. 1-3
- **Concern** The selection of ChromBPNet is critical to all downstream analyses, but the comparison with other models is only described in supplementary materials. The text does not report the actual performance metrics, the range of models tested, or the criteria for "strongest correspondence." Without this information, it is impossible to assess whether the model choice introduces systematic biases into the evolutionary conclusions.
- **Why it matters** If ChromBPNet systematically underestimates the effects of certain mutation types or overestimates others, the conclusions about which mutations drove evolutionary transitions could be artifacts of model choice.
- **Resolution test** Report the quantitative comparison of model performance in the main text or clearly reference specific metrics in the supplement. Show that the key conclusions are robust to model choice, or explicitly discuss how model limitations affect the interpretation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretational validity
- **Claim summary** The authors conclude that the Gata4 enhancer's parietal endoderm activity is "a derived feature specific to the rodent lineage" and "largely to the Mus genus," based on the observation that non-rodent orthologs are inactive in PYS-2 cells.
- **Evidence pointer** Results section "Mutational basis of a Mus genus-specific gain-of-function in the Gata4 enhancer"; Fig. 1c; Fig. 2
- **Concern** The conclusion that activity is Mus-specific depends entirely on the assumption that PYS-2 cells faithfully recapitulate the parietal endoderm regulatory environment across all mammals. The authors validated this for mouse, but the trans-regulatory environment of PYS-2 cells may not be representative of the ancestral mammalian parietal endoderm. Inactive orthologs in other species could reflect either loss of cis-regulatory function or incompatibility with the mouse trans-regulatory environment.
- **Why it matters** The claim of Mus-specific gain-of-function is a key evolutionary finding. If the inactivity of non-rodent orthologs is due to trans-regulatory incompatibility rather than cis-regulatory evolution, the interpretation would be fundamentally different.
- **Resolution test** Provide evidence that the trans-regulatory environment is conserved across mammals, or acknowledge this limitation explicitly and discuss how it affects the evolutionary conclusions. Consider testing orthologs in a more evolutionarily distant but relevant cell type if available.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim summary** The authors report that "order-dependent variability in mutational effect sizes was 2-3-fold greater than experimental noise, indicating that epistatic interactions among evolutionarily derived mutations substantially influenced functional trajectories."
- **Evidence pointer** Results section "Synthetic reconstitution of gain-of-function trajectories reveals epistasis and TFBS affinity tuning"; Fig. 4
- **Concern** The comparison between order-dependent variability and experimental noise is described only qualitatively. The text does not report the statistical test used, the number of replicates, or the confidence intervals around this ratio. The claim of "substantial" epistasis requires more rigorous quantification.
- **Why it matters** Epistasis is a central finding with implications for evolutionary theory. If the effect is marginal or driven by a few outlier mutations, the conclusion would need to be tempered.
- **Resolution test** Provide the statistical framework used to compare variability sources, report effect sizes with confidence intervals, and show that the epistasis signal is consistent across mutations and enhancers rather than driven by specific cases.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "densely mapped" is vague. The density of mapping could refer to phylogenetic sampling, mutational coverage, or both.
- **Required correction** Specify what "densely" means in quantitative terms, e.g., "we tested orthologs from 480 mammalian genomes and performed saturation mutagenesis at every position."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, ChromBPNet model training
- **Evidence pointer** Methods section "ChromBPNet model training"
- **Issue** The description of model training lacks key hyperparameters and does not specify the version of ChromBPNet used.
- **Required correction** Provide the specific version, training epochs, learning rate, and any other critical hyperparameters. State whether default parameters were used and what "default" means in this context.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, phylogenetic coverage
- **Evidence pointer** Results section "Phylogenetic distributions of activity for 1,871 extant and ancestral enhancer orthologs"; Table S1
- **Issue** The text reports that phylogenetic coverage varied from 55.3% to 99.6% across enhancers but does not discuss the potential impact of missing orthologs on the conclusions.
- **Required correction** Add a brief discussion of how missing data might affect the observed patterns, particularly for the Lama1 enhancer with the lowest coverage.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, limitations
- **Evidence pointer** Discussion section, third paragraph
- **Issue** The limitation about ancestral sequence reconstruction uncertainty is mentioned but not discussed in the context of the specific claims about the Gata4 and Epas1 enhancers.
- **Required correction** Briefly discuss how reconstruction uncertainty might affect the identification of specific causal mutations in the evolutionary trajectories.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Results, enhancer selection
- **Evidence pointer** Results section "Selection of five parietal endoderm-specific enhancers and validation of a surrogate cell system"
- **Issue** The criteria for selecting these five enhancers from the eight identified are not stated.
- **Required correction** State the selection criteria, or note that all eight were carried forward and five are reported for specific reasons.

## Risk / unsupported claims
- The claim that the Gata4 enhancer's parietal endoderm activity is "largely to the Mus genus" is not fully supported without evidence that the PYS-2 trans-regulatory environment is representative across mammals.
- The claim of "pervasive context-dependent epistasis" is based on a qualitative comparison of variability sources and requires statistical validation.
- The asymmetry between ablation and enhancement predictability is presented as a general property but is based on only five enhancers in a single cell type.
- The statement that "model-optimized trajectories outperformed nearly all random trajectories" is not quantified, and the exceptions are not discussed.
- The conclusion that "sequence constraint is an unreliable guide to regulatory function" is based on a correlation analysis (ρ < 0.02) that is reported without confidence intervals or power analysis.
- The claim that the Epas1 enhancer's Foxa2-Sox17-Gata4/6 module "arose in the inferred Boreoeutherian ancestor" depends on the accuracy of ancestral state reconstruction, which is acknowledged as uncertain but not quantified.