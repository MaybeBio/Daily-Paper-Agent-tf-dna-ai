## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and data availability statement
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and internal consistency of the presented data and interpretations
- **Shared manuscript claim summary** The authors report that IHF binds DNA in three distinct bending modes (associated, half-wrapped, fully-wrapped) with varying sequence specificity, that only the fully-wrapped state requires the consensus sequence, that IHF can bridge two DNA duplexes non-specifically, and that these behaviors are driven by electrostatic interactions
- **Visible evidence base** AFM imaging of three DNA constructs (0λ361, 1λ306, 3λ343/478) with and without IHF; unrestrained MD simulations in implicit solvent; restrained MD simulations in explicit solvent; umbrella sampling free energy calculations; hydrogen bond analysis
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; Movies S1-S5 referenced but not provided; raw AFM image data not shown; force-distance curves or control experiments for bridging not described in detail; statistical analysis details for clustering partially described

## Reviewer
- **Overall assessment** This manuscript presents a substantial and potentially important contribution to understanding IHF-DNA interactions. The combination of AFM and MD simulations is powerful and generally well-executed. The identification of three distinct bending states with different sequence requirements is novel and mechanistically plausible. However, several concerns regarding the interpretation of AFM data, the statistical treatment of angular distributions, and the extrapolation from simulation to experimental conditions require clarification before the conclusions can be fully accepted.
- **Who would be interested in the results, and why** Researchers studying nucleoid-associated proteins, bacterial chromosome organization, DNA-protein interactions at the single-molecule level, and the biophysics of DNA bending. The work also has relevance for understanding how architectural proteins mediate DNA compaction and bridging in diverse organisms.
- **Major strengths** The combination of experimental and computational approaches is well-matched to the question. The identification of a previously unobserved low-angle binding state is significant. The free energy calculations provide quantitative support for the proposed binding hierarchy. The bridging mechanism is supported by both AFM observations and MD simulations.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: High. The three-state model for IHF binding is a clear advance over the binary specific/non-specific view. Scientific importance: High for the prokaryotic chromosome field; moderate for broader chromatin biology. Interdisciplinary readership: The work bridges biophysics, molecular biology, and computational chemistry, and should appeal to readers across these areas. Technical soundness: Generally good, but with specific concerns detailed below regarding AFM analysis and simulation interpretation. Readability for nonspecialists: The manuscript is clearly written and the figures are well-designed, though some methodological details require careful reading.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical analysis of AFM angular distributions
- **Claim pointer** The authors claim three distinct binding modes with bend angles of 73°, 107°, and 147° based on AFM measurements, and that these are present in roughly equal proportions for the specific construct.
- **Evidence pointer** Results section, Figure 4A and 4B, Supplementary Figure S3
- **Concern** The identification of three peaks in the angular distributions relies on chi-squared goodness-of-fit tests, but the details of how the number of peaks was determined are not fully described. The authors state that "two and three peaks" were found for 0λ361 and 1λ306 respectively, but the criteria for peak selection, the fitting procedure, and the confidence intervals for the peak positions are not provided. The reduced chi-square values are mentioned but the actual values and degrees of freedom are not given in the main text.
- **Why it matters** The central claim of the paper is the existence of three distinct binding modes. If the peak identification is not robust, the entire interpretive framework is compromised. The overlap between the 73° and 107° peaks, given the reported standard deviations, could potentially be explained by a single broad distribution rather than two discrete states.
- **Resolution test** Provide the full fitting procedure, including the functional form used, the number of components tested, and statistical comparison between models with different numbers of peaks (e.g., AIC or BIC values). Show the individual angular distributions with fitted peaks and confidence intervals. Demonstrate that the three-peak model is statistically preferred over the two-peak model for 1λ306.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of MD simulation clustering
- **Claim pointer** The authors claim that MD simulations confirm the three states identified by AFM, with bend angles of 66°, 115°, and 157°.
- **Evidence pointer** Results section, Figure 4C and 4D, Supplementary Figure S4
- **Concern** The clustering of MD trajectories into three groups was performed using hierarchical agglomerative clustering with RMSD as the distance metric, but the choice of three clusters appears to have been made a priori based on the AFM results. The authors do not demonstrate that three clusters are statistically preferred over two or four. Additionally, the hydrogen bond analysis used to characterize the clusters is presented as average values, but the variability within clusters and the temporal stability of these interactions are not discussed.
- **Why it matters** If the clustering is forced to three groups, the agreement with AFM is somewhat circular. The claim that simulations "confirm" the AFM states requires independent justification for the number of clusters.
- **Resolution test** Perform a systematic clustering analysis with varying numbers of clusters and report the clustering quality metrics (e.g., silhouette score, Davies-Bouldin index). Show that three clusters emerge naturally from the data rather than being imposed. Provide time series of hydrogen bond formation and breaking within each cluster to demonstrate their stability.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Free energy landscape construction
- **Claim pointer** The authors claim that the two-dimensional free energy landscape constructed from umbrella sampling simulations predicts the relative populations of the three states (32% fully-wrapped, 50% half-wrapped, 18% associated).
- **Evidence pointer** Results section, Figure 5, Supplementary Figure S4
- **Concern** The construction of the 2D free energy landscape involves several approximations that are not fully justified. The authors state that "linear interpolation was performed" between the two sets of umbrella sampling results (one with the other arm free, one with it restrained), and that the 2D landscape was "constructed by simple addition of energies." This assumes that the two reaction coordinates are independent, which is not demonstrated. The linear interpolation between two extreme conditions is a significant approximation that could introduce substantial errors in the predicted populations.
- **Why it matters** The predicted populations of the three states are used to support the biological relevance of the model. If the free energy landscape is not accurately constructed, the population estimates are unreliable, and the comparison with AFM proportions becomes questionable.
- **Resolution test** Provide a more rigorous treatment of the 2D free energy surface, either by performing true 2D umbrella sampling or by demonstrating that the interpolation and addition approximations introduce negligible error. Show convergence of the PMF calculations and provide error estimates for the free energy differences.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Bridging mechanism evidence
- **Claim pointer** The authors claim that IHF bridges two DNA duplexes through non-specific interactions, and that this is energetically favorable with a free energy difference of approximately 14 kcal/mol.
- **Evidence pointer** Results section, Figure 6, Supplementary Figure S5
- **Concern** The bridging claim relies on a single MD simulation setup where a second DNA molecule was pushed toward the IHF-DNA complex. The authors do not provide evidence that this represents a thermodynamically relevant pathway, nor do they show that the bridged state is stable over extended simulation times. The free energy difference of 14 kcal/mol is mentioned but the details of this calculation are not provided in the main text. The AFM images showing clusters are interpreted as evidence of bridging, but alternative explanations (e.g., non-specific aggregation, DNA-DNA interactions) are not fully excluded.
- **Why it matters** The bridging function of IHF is presented as a significant new finding with implications for understanding DNA compaction and biofilm formation. If the evidence is not robust, this claim is not established.
- **Resolution test** Provide details of the free energy calculation for bridging, including the reaction coordinate, the simulation length, and convergence criteria. Show that the bridged state is stable in multiple independent simulations. Include control AFM experiments with a non-DNA-binding protein or with a mutant IHF lacking the bridging surface to demonstrate specificity.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Experimental reproducibility
- **Affected element** AFM sample preparation
- **Evidence pointer** Methods section, "Atomic force microscopy acquisition and analysis"
- **Issue** The authors state that samples were prepared by adding a solution of DNA and IHF to poly-L-lysine treated mica, but the incubation time and buffer conditions are not specified in detail. The concentration range of IHF used (5-150 nM) is broad, and it is unclear how the IHF:DNA ratio was calculated for each experiment.
- **Required correction** Provide the exact incubation times, buffer composition, and the method for calculating IHF:DNA ratios. State how many independent sample preparations were performed for each condition.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Angular distribution analysis
- **Evidence pointer** Results section, Figure 4
- **Issue** The authors report mean and standard deviation for the three bend angles but do not report the number of measurements contributing to each peak or the confidence intervals for the means.
- **Required correction** Report the sample sizes for each peak and provide 95% confidence intervals for the mean bend angles.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Simulation methodology
- **Affected element** Force field validation
- **Evidence pointer** Methods section, "Unbiased molecular dynamics simulations"
- **Issue** The authors use the ff14SB and BSC1 force fields but do not discuss whether these force fields have been validated for DNA-protein interactions involving sharp bending. The choice of implicit solvent model (GBneck2) is also not justified in detail.
- **Required correction** Briefly justify the choice of force fields and solvent model, citing relevant validation studies or providing a comparison with alternative approaches.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Supplementary materials
- **Evidence pointer** Data Availability statement
- **Issue** The authors state that all relevant data is included in the main manuscript and supplementary material, but the supplementary material is not provided with the manuscript for review. This prevents full evaluation of the methods and results.
- **Required correction** Ensure that all supplementary figures, tables, and movies are made available to reviewers and readers.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion section
- **Evidence pointer** Discussion, paragraph 2
- **Issue** The authors discuss the two-step binding mechanism but do not cite or discuss the single-molecule FRET study by Ansari and co-workers in sufficient detail. The comparison with their results is brief and could be expanded.
- **Required correction** Provide a more detailed comparison with the FRET study, including a discussion of why the proportions of states differ between the two approaches.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Results
- **Evidence pointer** Abstract, Results section
- **Issue** The term "associated" for the 73° state is somewhat ambiguous, as it could be confused with the general concept of protein-DNA association. The authors should consider whether this is the most descriptive term.
- **Required correction** Consider renaming the state to something more descriptive, such as "loosely bound" or "partially associated," or provide a clear operational definition in the text.

## Risk / unsupported claims
- The claim that the three binding states are present in "roughly equal proportions" for 1λ306 is not strongly supported, as the AFM proportions (32%, 27%, 41%) differ from the MD-predicted proportions (18%, 50%, 32%), and the authors do not reconcile this discrepancy.
- The claim that the "associated" state is a form of non-specific binding is inferred from its presence in the 0λ361 construct, but the statistical test (Kolmogorov-Smirnov) did not find a significant difference between 0λ361 with and without IHF, weakening this inference.
- The statement that the free energy landscape "predicts that all three states should occur in significant proportions" is not directly comparable to the AFM data, as the simulation conditions (implicit solvent, 300 K) differ from the experimental conditions (surface-immobilized DNA, dried for AFM imaging).
- The claim that IHF bridging is relevant to biofilm formation is speculative and not directly tested in this work.
- The statement that "the general methods we have developed here for comparing AFM imaging with MD simulations have a utility that could be applied for many other protein-DNA interactions" is an overstatement, as the method is not presented as a generalizable pipeline with clear guidelines for other systems.