## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, and materials and methods
- **Assessment boundary** Scientific validity of claims, methodological soundness, and consistency between computational predictions and experimental results
- **Shared manuscript claim summary** The authors combine extended all-atom molecular dynamics simulations with yeast-based transactivation assays to characterize the structural and functional consequences of mutations at positions 337 and 352 in the p53 tetramerization domain, including the clinically relevant R337H and R337C variants
- **Visible evidence base** Figures 1-5, Supplementary Figures S1-S4, computational methods (Gromacs, Amber14sb), yeast reporter assays, Western blot analysis
- **Missing materials affecting confidence** Full simulation parameters and convergence criteria, raw RMSD trajectories, statistical analysis details for contact map comparisons, complete Western blot images, replicate numbers for luciferase assays, and exact galactose concentrations used

## Reviewer

### Overall assessment
This manuscript presents a combined computational and experimental study of p53 tetramerization domain mutations, focusing on the R337H and R337C variants and rationally designed mutations targeting the R337-D352 salt bridge. The work addresses a clinically relevant question, particularly given the prevalence of R337H in southern Brazil. The computational approach using extended all-atom MD simulations represents an improvement over earlier studies, and the yeast-based functional assays provide a useful platform for assessing transactivation potential and specificity. However, several technical concerns regarding simulation validation, statistical treatment of experimental data, and the strength of the structure-function conclusions need to be addressed before the case is fully established.

### Who would be interested in the results, and why
Cancer geneticists and clinicians managing Li-Fraumeni syndrome families, particularly those in regions with high R337H prevalence, would find the functional characterization of these variants relevant. Structural biologists studying p53 oligomerization and researchers developing pharmacological strategies to stabilize mutant p53 would also be interested. The demonstration that TET domain mutations can alter transactivation specificity, not just overall activity, has implications for understanding genotype-phenotype correlations in p53-associated cancer predisposition.

### Major strengths
- The combination of extended MD simulations with functional assays in a defined genetic system provides complementary perspectives on mutation effects
- The inclusion of multiple protonation states for histidine in R337H is a thoughtful approach given the pH-dependent phenotype of this variant
- The use of isogenic yeast reporter strains with different response elements allows assessment of transactivation specificity, which is often overlooked in p53 functional studies
- The rationally designed mutations (R337D, D352R, and the double mutant) provide a systematic test of the salt bridge hypothesis

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of computational methods
- **Claim pointer** The claim that disease-associated substitutions destabilize the p53 TET domain conformation based on 2 µs MD simulations
- **Evidence pointer** Section 2.1, Figure 2, Figure S1
- **Concern** The manuscript does not provide sufficient validation that the 2 µs simulations have converged. No RMSD convergence plots, no replicate simulations, and no block-averaging or other statistical analysis of the trajectories are shown. The authors state that R337Hδε showed "no stability alterations" compared to WT, but it is unclear whether this reflects true biophysical behavior or insufficient sampling. Additionally, the criteria for defining "destabilization" from RMSD or contact map analyses are not explicitly stated.
- **Why it matters** Without demonstrated convergence and statistical rigor, the computational predictions that form the basis for the experimental design and the structure-function conclusions cannot be reliably interpreted. The distinction between R337Hδε (stable) and R337Hδ/R337Hε (destabilized) is a key finding that requires robust evidence.
- **Resolution test** Provide convergence analysis (e.g., RMSD vs time plots, block standard deviation), run replicate simulations or extend simulation time, and define quantitative criteria for classifying a mutant as destabilized versus stable.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical treatment of experimental data
- **Claim pointer** The claim that R337H exhibits a "subtle transactivation defect" and that D352R shows "much higher transactivation potential than WT p53" on the p21-SP2 reporter
- **Evidence pointer** Section 2.2, Figure 5, Figure S3
- **Concern** The luciferase assay data are presented without error bars, statistical tests, or replicate numbers in the main figures. The authors state that "five independent transformants were tested" but do not report whether the data shown are means, medians, or individual values. The claim of enhanced activity for D352R on p21-SP2 is based on visual inspection of the figures, and no statistical comparison is provided. The Western blot in Figure S4 is described as confirming equal expression, but quantification details are not given.
- **Why it matters** The key experimental finding is that TET domain mutations can alter transactivation specificity in a response element-dependent manner. This conclusion requires rigorous statistical support, particularly for the subtle effects attributed to R337H. Without error bars and statistical tests, the reader cannot assess the reliability of the reported differences.
- **Resolution test** Provide mean values with standard deviations or standard errors, perform appropriate statistical tests (e.g., ANOVA with post-hoc comparisons) for each reporter strain and expression level, and report exact p-values. Include replicate numbers for each condition.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Strength of structure-function conclusions
- **Claim pointer** The statement that "these results define the mechanism by which residue variations in positions 337 and 352 destabilize the TET domain of p53 and predict a structure-function relationship"
- **Evidence pointer** Section 2.1, Section 3
- **Concern** The manuscript demonstrates correlations between computational predictions and experimental outcomes, but the claim of defining a "mechanism" is overstated. The authors do not provide structural analysis beyond contact maps and interchain distances. No free energy calculations, no detailed analysis of which specific interactions are disrupted, and no structural snapshots showing the proposed destabilization pathway are presented. The link between TET domain destabilization and altered transactivation specificity remains mechanistically unexplained.
- **Why it matters** The title and framing of the manuscript promise a structural basis for mutation-dependent tetramerization deficiency. To deliver on this promise, the authors need to provide more mechanistic insight into how specific mutations disrupt the tetramer interface and how this disruption translates into altered DNA binding and transactivation behavior.
- **Resolution test** Provide structural analysis identifying specific disrupted interactions (e.g., hydrogen bonds, salt bridges, hydrophobic contacts) for each mutant, and discuss how these changes might affect tetramer stability and DNA binding cooperativity. If possible, relate the computational findings to the observed functional differences.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Completeness of experimental validation
- **Claim pointer** The claim that the transactivation assay results "confirm" the computational predictions
- **Evidence pointer** Section 2.2, Figure 5, Figure S3
- **Concern** The experimental system uses a yeast-based assay with a GAL1,10 promoter and firefly luciferase reporter. While this is a well-established system, the authors do not directly measure tetramerization status or stability in the experimental system. The connection between the computational predictions of tetramer stability and the observed transactivation differences is inferred rather than directly demonstrated. Additional experiments such as native gel electrophoresis, cross-linking, or biophysical characterization of the mutant proteins could strengthen the link.
- **Why it matters** The central thesis is that tetramerization domain mutations affect function through altered tetramer stability. Without direct experimental evidence of tetramer destabilization, alternative explanations (e.g., altered protein folding, degradation, or nuclear localization) cannot be excluded.
- **Resolution test** Perform biochemical characterization of tetramer formation for the mutant proteins (e.g., native PAGE, analytical ultracentrifugation, or cross-linking) to directly demonstrate differences in tetramer stability that correlate with the computational predictions.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The figure legend does not clearly indicate whether the structure shown is the WT p53 tetramerization domain and how the R337 and D352 residues are highlighted. The figure is referenced in the introduction but not described in sufficient detail.
- **Required correction** Expand the figure legend to describe the structural context, the specific residues highlighted, and whether the image represents a crystal structure or a model.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Section 4.1
- **Evidence pointer** Section 4.1
- **Issue** The simulation protocol lacks several details: the number of water molecules, the specific ion concentration calculation, the equilibration procedure, and the temperature/pressure coupling parameters beyond the coupling constants. The choice of the Amber14sb force field is stated but not justified.
- **Required correction** Provide a more complete description of the simulation setup, including system size, equilibration protocol, and any validation of the force field parameters for this system.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 5 and Figure S3
- **Evidence pointer** Figure 5, Figure S3
- **Issue** The figures show transactivation data but the y-axis labels are not clearly described. It is unclear whether the values represent relative light units, fold activation over background, or normalized values. The galactose concentrations on the x-axis are not specified numerically.
- **Required correction** Clearly label axes with units and provide the exact galactose concentrations used. State the normalization procedure in the figure legend.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Section 1
- **Evidence pointer** Section 1
- **Issue** The introduction mentions the Lwin et al. study as the only systematic computational study of the TET domain, but there may be other relevant computational or experimental studies of p53 tetramerization mutations that are not cited.
- **Required correction** Consider citing additional relevant studies on p53 tetramerization domain mutations and their structural consequences to provide a more complete context.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section 2.1
- **Evidence pointer** Section 2.1
- **Issue** The term "fluid salt-bridging cluster" is used without definition. It is unclear what distinguishes a "fluid" cluster from a static one in this context.
- **Required correction** Define the term or use more standard terminology to describe the dynamic behavior of the salt bridge network.

### Technical failings that need to be addressed before the case is established
- Lack of convergence analysis and statistical treatment of MD simulation data (R1-M1)
- Absence of error bars and statistical tests for luciferase assay data (R1-M2)
- Overstated mechanistic conclusions not fully supported by the presented data (R1-M3)
- No direct experimental validation of tetramer destabilization (R1-M4)

## Risk / unsupported claims
- The claim that the results "define the mechanism" of mutation-dependent tetramerization deficiency is not supported by the level of structural analysis provided
- The statement that D352R shows "much higher transactivation potential than WT p53" on the p21-SP2 reporter is not statistically substantiated
- The assertion that R337Hδε showed "no stability alterations" compared to WT is based on a single simulation without convergence validation
- The claim that the transactivation assay results "confirm" the computational predictions overstates the strength of the correlation, as the experimental system does not directly measure tetramer stability
- The prediction of a "structure-function relationship" is presented as a conclusion rather than a hypothesis, given the indirect nature of the experimental validation