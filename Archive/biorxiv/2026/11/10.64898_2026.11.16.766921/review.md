## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure/table legends
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and alignment with stated conclusions
- **Shared manuscript claim summary** The authors investigate the evolution of HIV-1 integrase under constraints from folding stability and functional interactions, using molecular dynamics simulations and phylogenetic inference to show that drug-resistance mutations generally have marginal effects on stability and DNA binding, that some mutations alter catalytic site geometry and loop flexibility, and that long-term evolution shows temporal fluctuations in these properties consistent with marginal stability.
- **Visible evidence base** Results text, methods text, Figures 1-6 (described), Tables S1-S2, Figures S1-S8, Figures S2.1-S2.12 (described), data availability repository
- **Missing materials affecting confidence** Actual figure images, numerical values for ΔG and binding energies, statistical test outputs, simulation convergence metrics, force field validation details, phylogenetic tree figure, ancestral sequence reconstruction quality metrics

## Reviewer
- **Overall assessment** The manuscript addresses an important question about how drug-resistance mutations affect the fitness landscape of HIV-1 integrase, combining molecular dynamics simulations with phylogenetic inference. The topic is timely and relevant for understanding viral evolution and antiretroviral therapy. However, the current presentation has several significant gaps that prevent full evaluation of the claims. The results section lacks quantitative detail, making it difficult to assess the magnitude of reported effects. The methods section describes standard approaches but omits critical validation steps. The phylogenetic component is underdeveloped relative to its stated importance. The manuscript would benefit from clearer presentation of numerical results, additional validation of simulation convergence, and a more rigorous treatment of the evolutionary analysis.
- **Who would be interested in the results, and why** Researchers studying HIV drug resistance evolution, computational biologists interested in protein stability and evolution, virologists studying integrase function, and evolutionary biologists working on marginal stability theory. The findings on how specific drug-resistance mutations affect integrase stability and DNA binding could inform understanding of resistance pathways and potentially guide treatment strategies.
- **Major strengths** The study addresses a clinically relevant question with a combination of computational approaches. The focus on both folding stability and DNA binding is more comprehensive than many previous studies. The inclusion of ancestral sequence reconstruction adds an evolutionary dimension. The discussion of marginal stability as a framework for understanding integrase evolution is conceptually interesting.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: moderate. The application of MD simulations to HIV-1 integrase drug-resistance mutations is not entirely new, but the combination with ancestral reconstruction and the focus on marginal stability provides some novelty. Scientific importance: potentially high for the HIV evolution community, but the clinical implications are not fully developed. Interdisciplinary readership: the work bridges virology, structural biology, and evolutionary biology, which could appeal to a broad audience if presented accessibly. Technical soundness: currently not fully established due to missing validation and quantitative detail. Readability for nonspecialists: the abstract is accessible, but the results section assumes significant background knowledge in MD simulations and phylogenetics.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential but requires substantial revision to address the technical concerns and provide sufficient quantitative support for the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "DRMs generally altered protein folding stability and protein-DNA interactions to a marginal extent" based on MD simulations.
- **Evidence pointer** Results section, Figures 2 and 3
- **Concern** The manuscript does not provide quantitative values for the folding stability (ΔG) or binding free energies. The reader cannot assess what "marginal extent" means in numerical terms. No error bars, confidence intervals, or statistical comparisons are reported. The claim that approximately 20% of variants showed increased stability is presented without supporting numbers or statistical tests.
- **Why it matters** Without quantitative data, the central claim of the paper cannot be evaluated. The magnitude of effects is essential for determining whether the conclusions are justified.
- **Resolution test** Provide a table with mean and standard error for ΔG and binding free energy for all variants. Include statistical comparisons (e.g., t-tests or ANOVA) between wild-type and mutant variants. State explicitly what threshold defines "marginal" versus "significant" effects.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "several DRMs altered catalytic site geometry, including alteration of magnesium coordination within the catalytic triad and modulation of enzymatic activity by changes in flexibility of the 140-149 loop."
- **Evidence pointer** Results section, Figure 4, Figures S2 and S3
- **Concern** The description of catalytic site alterations is qualitative. The authors mention "spatial rearrangements" and "pronounced deviation" but do not provide quantitative measures such as distances, angles, or RMSD values with statistical significance. The correlation between D116-Mg2+ distance and binding energy is mentioned but the correlation coefficient and p-value are not reported in the main text.
- **Why it matters** The claim that DRMs alter catalytic site geometry is central to the mechanistic interpretation. Without quantitative measures, it is unclear whether the observed changes are biologically meaningful or within normal thermal fluctuations.
- **Resolution test** Report specific distances between catalytic residues and Mg2+ ions for wild-type and mutant variants with standard errors. Provide correlation coefficients and p-values for the reported correlations. Include statistical tests comparing mutant and wild-type geometries.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "long-term evolution of the HIV-1 integrase" shows "temporal fluctuations in folding stability and DNA-binding affinity" based on ancestral sequence reconstruction.
- **Evidence pointer** Results section, Figures 5 and 6, Figure S5 and S6
- **Concern** The phylogenetic analysis is described only briefly. The authors do not report the number of sequences analyzed, the alignment length, the support values for the phylogenetic tree, or the quality of ancestral sequence reconstruction. The statement that stability "remained relatively constant along intermediate branches" is not supported by any quantitative data. The comparison with the previous study by Olabode et al. is mentioned but not systematically evaluated.
- **Why it matters** The evolutionary claims depend entirely on the accuracy of ancestral sequence reconstruction and the phylogenetic framework. Without details on the methods and quality assessment, these claims cannot be evaluated.
- **Resolution test** Provide details on the sequence dataset, alignment, phylogenetic inference, and ancestral reconstruction quality (e.g., posterior probabilities). Report numerical values for stability and binding across the tree with confidence intervals. Include a figure showing the distribution of these properties across the phylogeny.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "we performed five independent analyses, and the presented results correspond to their mean and standard error" for MD simulations.
- **Evidence pointer** Methods section, Molecular dynamics simulations
- **Concern** The manuscript does not report simulation convergence. No RMSD or RMSF plots over time are shown in the main text. The choice of 120 ns production time is not justified. The authors do not state how many independent simulations were performed per variant or whether the five replicates are truly independent (e.g., different initial velocities). The use of FoldX on MD trajectories is unusual and requires validation.
- **Why it matters** MD simulations are only meaningful if they have converged and sampled equilibrium distributions. Without convergence assessment, the reported energies may not be reliable.
- **Resolution test** Show RMSD and RMSF plots over the simulation time for representative variants. Report the equilibration period and justify the production time. Describe how the five replicates were generated and whether they were statistically independent. Validate the FoldX approach against experimental data or alternative methods.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "integrating biophysical properties with evolutionary modeling provides a robust framework for understanding how structural constraints influence the fixation of adaptive mutations."
- **Evidence pointer** Discussion section
- **Concern** The integration of biophysical properties with evolutionary modeling is not demonstrated. The authors use a structurally constrained substitution model for ancestral reconstruction, but they do not show how the MD-derived stability and binding data inform or validate the evolutionary model. The connection between the two approaches is asserted rather than demonstrated.
- **Why it matters** The stated conclusion of the paper is that this integration provides a robust framework. If the integration is not shown, the main conclusion is unsupported.
- **Resolution test** Provide a clear analysis showing how the biophysical measurements relate to the evolutionary patterns. For example, test whether variants with higher predicted stability are more likely to be fixed in the phylogeny, or whether the structural constraints improve the fit of the evolutionary model.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that "DRMs generally altered protein folding stability and protein-DNA interactions to a marginal extent" but this is contradicted by the later statement that "several DRMs altered catalytic site geometry." The relationship between these two findings is unclear.
- **Required correction** Clarify in the abstract whether the marginal effects on stability and binding are consistent with the observed changes in catalytic site geometry, or whether these are separate findings.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods section, General setup
- **Issue** The methods state that structures were assembled from PDB entries 6PUT and 6VDK, but the specific chain assignments and the handling of missing residues are not described in sufficient detail.
- **Required correction** Provide a more detailed description of the structure assembly, including which chains were used, how missing loops were modeled, and how the final model was validated.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results
- **Evidence pointer** Results section, Drug-resistance mutations affect folding stability
- **Issue** The statement that "the fraction of variants with improved stability increased progressively from one to four mutations" is based on a small number of variants, and no statistical test is reported.
- **Required correction** Report the number of variants in each category and perform a statistical test (e.g., chi-square or Fisher's exact test) to support the claim of a progressive trend.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results
- **Evidence pointer** Results section, Long-term evolution
- **Issue** The authors mention "patient-derived" variants in the discussion but do not describe how these were obtained or analyzed in the methods.
- **Required correction** Clarify whether patient-derived variants were included in the analysis and, if so, describe their source and how they were processed.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Figures
- **Evidence pointer** Figures 2 and 3
- **Issue** The figures are described in the text but not shown in the provided material. The reader cannot verify the claims without seeing the actual data.
- **Required correction** Ensure that all figures are included in the manuscript and that they clearly show the data with appropriate labels and error bars.

## Risk / unsupported claims
- The claim that "DRMs generally altered protein folding stability and protein-DNA interactions to a marginal extent" is unsupported without quantitative data.
- The claim that "several DRMs altered catalytic site geometry" is unsupported without quantitative geometric measurements.
- The claim that "temporal fluctuations in folding stability and DNA-binding affinity" occur over evolutionary time is unsupported without details on ancestral reconstruction quality and numerical results.
- The claim that the study provides "a robust framework for understanding how structural constraints influence the fixation of adaptive mutations" is not demonstrated by the presented analysis.
- The comparison with the previous study by Olabode et al. (2017) is mentioned but not systematically evaluated, making the claimed discrepancy unverifiable.
- The statement that "the study variants describe functional and viable evolutionary pathways" is not supported by any direct evidence of functionality or viability.