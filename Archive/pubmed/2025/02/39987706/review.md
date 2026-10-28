## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results and discussion, conclusion, methods, and supplementary figure/table references
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and internal consistency of the presented work
- **Shared manuscript claim summary** The authors propose that substitutions at rheostat position 52 of LacI alter the protein's conformational landscape, particularly in the regulatory domains, and that these changes can reverse the allosteric effect of the ligand ONPF for the V52A variant. They support this with molecular dynamics simulations and experimental validation.
- **Visible evidence base** Simulation results (1 μs trajectories, multiple conditions), in vivo repression assays, in vitro biolayer interferometry binding assays, structural metrics (angles, distances, radii of gyration), hydration analyses
- **Missing materials affecting confidence** Supplementary figures S1–S16 and tables S1 are referenced but not provided; full statistical model details are in supplementary files not available; raw simulation trajectories and analysis scripts not provided; experimental raw data (flow cytometry, BLI traces) not shown in main text

## Reviewer

- **Overall assessment** This manuscript presents a well-structured investigation into the long-range effects of substitutions at a rheostat position in LacI. The combination of extensive molecular dynamics simulations with experimental validation is commendable and the central prediction regarding V52A's inverted allosteric response to ONPF is both novel and potentially significant. However, the manuscript has several weaknesses that need to be addressed. The lack of clear correlations between simulated conformational changes and functional outcomes for most variants weakens the general claim. The presentation of simulation results is somewhat descriptive, and the experimental validation, while supportive, is limited to a single variant. The manuscript would benefit from a more quantitative analysis of the simulation data and a clearer articulation of how the observed conformational shifts relate to the functional parameters measured.

- **Who would be interested in the results, and why** Researchers in protein biophysics, allostery, and molecular dynamics simulation would find this work of interest. The study provides a detailed example of how substitutions at a distant position can influence the conformational landscape of a protein, with implications for understanding allosteric regulation. The successful prediction and validation of an inverted allosteric response is a notable result that could inform future studies on protein engineering and drug design. The work also contributes to the ongoing discussion about the mechanisms underlying rheostat positions in proteins.

- **Major strengths** The study combines long-timescale (1 μs) all-atom MD simulations with multiple perturbations (pressure, ligand) to map conformational landscapes, which is a robust approach. The prediction of an inverted allosteric effect for V52A, followed by experimental validation in both in vivo and in vitro systems, is a strong point that demonstrates the utility of the simulation approach. The manuscript is generally well-written and the figures are informative.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors state that "no clear correlations were found between the conformational changes of the DNA binding domains and changes in DNA binding affinities and specificities" and that "complex combinations of dynamic parameters and/or additional simulations in the presence of DNA are needed to explain this functional change."
- **Evidence pointer** Results and Discussion, "Simulations of V52X variants display both short- and long-range conformational changes" section; Figure 4; Figure 5
- **Concern** The central claim of the paper is that substitutions at V52 have long-range effects on the conformational landscape. However, the authors explicitly state that no direct correlation was found between the observed conformational changes and the functional outcomes (DNA binding affinity/specificity) for most variants. This is a significant limitation. The paper would be strengthened by a more quantitative attempt to link the simulation data to the functional parameters, even if the relationship is complex. As presented, the claim that the conformational changes "explain" the functional differences is not well-supported for the majority of the variants studied.
- **Why it matters** The paper's main hypothesis is that rheostat substitutions alter function by altering the conformational landscape. If the observed conformational changes do not correlate with functional changes, the causal link is weakened. The authors need to either provide a more nuanced analysis that identifies specific dynamic or structural features that correlate with function, or temper their conclusions about the mechanism.
- **Resolution test** The authors should perform a more detailed analysis of the simulation trajectories to identify specific conformational features (e.g., specific domain orientations, inter-domain contacts, or dynamic correlations) that can be quantitatively compared to the measured binding affinities and allosteric responses. Alternatively, they could perform additional simulations in the presence of DNA to see if the conformational differences become more pronounced and functionally relevant.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the results suggest that complex combinations of dynamic parameters and/or additional simulations in the presence of DNA are needed to predict DNA binding specificity."
- **Evidence pointer** Results and Discussion, "Simulations of V52X variants display both short- and long-range conformational changes" section; Figure 4; Figure 5
- **Concern** The manuscript does not provide a clear, quantitative analysis of the simulation data. The results are presented largely through descriptive statements and visual inspection of figures (e.g., "large deviations were noted", "shifted in the opposite direction"). While the figures are helpful, a more quantitative analysis, such as calculating free energy differences between states, principal component analysis of the trajectories, or time-averaged distances/angles with error bars, would significantly strengthen the conclusions. The lack of quantitative metrics makes it difficult to assess the significance of the observed differences between variants.
- **Why it matters** The conclusions about the effects of the substitutions and perturbations are based on qualitative observations. A quantitative analysis would provide a more rigorous basis for the claims and allow for a more direct comparison between variants and conditions.
- **Resolution test** The authors should provide quantitative measures of the conformational ensembles, such as the mean and standard deviation of the key metrics (θ, d) for each variant and condition, and perform statistical tests to determine if the differences between variants are significant. They could also calculate the free energy landscape along the defined reaction coordinates.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Evidence quality
- **Claim pointer** The authors state that "the simulations predicted that ONPF is an inducer of V52A" and that this was "experimentally validated in vivo and in vitro."
- **Evidence pointer** Results and Discussion, "Experimental validation of ONPF anti-induction for V52A" section; Figure 8; Figure 9
- **Concern** The experimental validation is a key part of the paper, but the presentation is limited. The in vivo data in Figure 8 shows a clear effect for V52A, but the in vitro BLI data in Figure 9 is described as showing "diminished DNA binding" without providing quantitative details such as the number of replicates, error bars, or statistical analysis. The BLI experiment is described as having a potential issue with protein aggregation at high concentrations, which could confound the results. More detail on the experimental design, replicates, and analysis is needed to fully assess the strength of the validation.
- **Why it matters** The experimental validation is the strongest evidence for the paper's central prediction. If the in vitro data is not robust, the overall impact of the finding is diminished.
- **Resolution test** The authors should provide a more complete description of the BLI experiments, including the number of independent replicates, the error associated with the measurements, and a statistical comparison of the binding in the presence and absence of ONPF. They should also address the potential issue of protein aggregation and how it was accounted for in the analysis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that "the data that support the findings of this study are available from the corresponding author upon reasonable request."
- **Evidence pointer** Data Availability Statement
- **Concern** The data availability statement is restrictive. For a study that relies heavily on computational simulations, it is standard practice to make the simulation input files, parameter files, and analysis scripts publicly available in a repository (e.g., Zenodo, Figshare, or a GitHub repository). This is essential for reproducibility and for other researchers to build upon this work. The same applies to the experimental data and analysis code.
- **Why it matters** Without access to the underlying data and code, it is impossible for other researchers to reproduce the results or verify the conclusions. This limits the impact and credibility of the work.
- **Resolution test** The authors should deposit all simulation input files, topologies, and analysis scripts in a public repository and provide a link in the manuscript. They should also make the raw experimental data (e.g., flow cytometry files, BLI traces) and analysis code available.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1
- **Evidence pointer** Introduction, Figure 1
- **Issue** The manuscript refers to Figure 1 for a summary of the functional effects of V52X variants, but the figure is not provided in the text. It is difficult to assess the functional context without seeing this figure.
- **Required correction** Ensure Figure 1 is included and clearly labeled, summarizing the known functional data for the V52X variants.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, "System setup"
- **Evidence pointer** Methods, "System setup" section
- **Issue** The description of the system setup mentions that the "modified crystal structure of dimeric LacI (PBD code 1EFA)" was used, but the details of how the mutations were modeled are brief. It is stated that "mutations were modeled onto the initial WT structure using the PyMOL software," but the specific method (e.g., the rotamer chosen) is not described.
- **Required correction** Provide more detail on the mutation modeling procedure, including the specific PyMOL commands or the method used to select the side chain rotamers.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, "Molecular dynamics simulations"
- **Evidence pointer** Methods, "Molecular dynamics simulations" section
- **Issue** The methods state that simulations were performed at 300 K and 1 bar and 3 kbar. The equilibration protocol is described, but the total simulation time is only mentioned as "up to 1000 ns". It is unclear if all simulations were run for the full 1 μs, and if not, what the lengths of the individual simulations were.
- **Required correction** Clearly state the total simulation time for each system and condition, and specify if any simulations were shorter than 1 μs.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results and Discussion, "Conformational changes of the WT LacI regulatory domains serve as a reference landscape"
- **Evidence pointer** Results and Discussion, "Conformational changes of the WT LacI regulatory domains serve as a reference landscape" section; Figure 6
- **Issue** The description of the reference landscape is clear, but the figure is not provided. It would be helpful to see the landscape and the positions of the reference states (O, O', C) to better understand the subsequent discussion of the variant results.
- **Required correction** Ensure Figure 6 is included and clearly shows the reference landscape and the positions of the O, O', and C states.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results and Discussion, "Experimental validation of ONPF anti-induction for V52A"
- **Evidence pointer** Results and Discussion, "Experimental validation of ONPF anti-induction for V52A" section; Figure 9
- **Issue** The description of the BLI experiment is brief. It is not clear how the "equilibrium" phase was determined, and the potential issue of protein aggregation is mentioned but not discussed in detail.
- **Required correction** Provide a more detailed description of the BLI data analysis, including how the equilibrium signal was determined and how the potential aggregation was addressed.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Conclusion
- **Evidence pointer** Conclusion
- **Issue** The conclusion is somewhat brief and could be strengthened by a more explicit summary of the key findings and their implications for understanding rheostat positions and allostery.
- **Required correction** Expand the conclusion to more clearly summarize the main findings, the successful prediction, and the broader implications for the field.

## Risk / unsupported claims
- The claim that "complex combinations of dynamic parameters and/or additional simulations in the presence of DNA are needed to predict DNA binding specificity" is a statement of limitation, but it is not supported by a specific analysis. It is presented as a conclusion, but it is more of an admission that the current approach is insufficient.
- The claim that the simulations "support the hypothesis that substituting rheostat positions can alter function by altering the relative populations on protein conformational landscapes" is only directly supported for the V52A variant, where the prediction was experimentally validated. For the other variants, the link between the observed conformational changes and functional outcomes is not established.
- The statement that "the fact that three different simulations populate this region of the conformational landscape suggests that it is readily accessible" is an interpretation of the simulation data, but without experimental evidence for this state, it remains speculative.
- The claim that the "changes in hydration of the hinge helices" are important for the conformational changes is plausible but is not directly tested or quantified in a way that establishes a causal link.