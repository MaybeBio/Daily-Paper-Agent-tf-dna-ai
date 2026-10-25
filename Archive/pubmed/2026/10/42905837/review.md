## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary materials description
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and internal consistency based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors propose that multiple CCAN units assemble into a spherical shell-like structure in interphase DT40 kinetochores, with CENP-C cupin domains clustering at the center and CENP-T/CENP-N localizing to the shell. They use coarse-grained molecular dynamics simulations, biochemical assays, and expansion microscopy to support this model, and show that CENP-C DNA binding via a conserved basic stretch is required for proper shell formation.
- **Visible evidence base** Abstract, Introduction, Results sections (7 subsections), Discussion, Methods (partial), figure legends referenced but figures not visible, supplementary figure references, no raw data or statistical outputs visible
- **Missing materials affecting confidence** Figures and supplementary figures not provided; raw simulation trajectories not accessible; statistical analysis details incomplete; cell line validation data not shown; antibody validation data not shown; full methods for image quantification not provided

## Reviewer
- **Overall assessment** This manuscript addresses a significant open question in centromere biology: how multiple CCAN complexes organize spatially within the kinetochore. The combination of molecular dynamics simulations with expansion microscopy is innovative and potentially powerful. However, the evidence as presented has several critical gaps. The simulation model is simplified and the authors acknowledge it does not capture full cellular complexity, yet the central claim of a "spherical shell-like structure" rests heavily on this model. The experimental validation via expansion microscopy is promising but the quantification methods are incompletely described, and the key mutant experiments show relatively modest phenotypic differences. The temporal argument distinguishing direct CENP-C effects from indirect mitotic arrest effects is plausible but not fully conclusive. Overall, the work is potentially important but the current evidence does not fully establish the proposed structural model.

- **Who would be interested in the results, and why** Chromosome segregation and kinetochore biologists would be the primary audience. The work also has relevance for structural biologists studying large macromolecular assemblies in situ, and for computational biologists interested in coarse-grained modeling of chromatin-associated complexes. The finding that CENP-C DNA binding contributes to higher-order CCAN organization could inform studies of centromere establishment and maintenance, and the methodological approach of combining MD simulations with expansion microscopy may interest researchers studying other supramolecular cellular structures.

- **Major strengths** 
  1. The study addresses a genuinely important and unresolved question: how multiple CCAN copies are organized within the kinetochore
  2. The combination of computational modeling with experimental validation is methodologically ambitious and appropriate for the scale of the question
  3. The use of expansion microscopy to visualize kinetochore substructure at improved resolution is technically appropriate
  4. The authors include important control experiments, such as testing antibody specificity and ruling out fixation artifacts
  5. The temporal argument regarding CENP-C effects versus mitotic arrest effects shows careful consideration of alternative explanations

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** "multiple CCAN units form a spherical shell-like structure in interphase DT40 kinetochores"
- **Evidence pointer** Figure 4, Figure 5, Results section "The spherical shell-like structure is observed in DT40 kinetochores"
- **Concern** The central claim of a spherical shell-like structure relies on expansion microscopy images, but the figures are not provided for review. The quantification method is described as "rotational averaging followed by intensity profiling," but the details of how this averaging was performed, how many kinetochores were analyzed, and how the shell vs. filled sphere distinction was statistically evaluated are not provided in the visible text. The reported difference between wild-type (2.03 μm) and CENP-C3D (1.79 μm) shell sizes is modest, and without seeing the distribution of measurements and statistical tests, it is difficult to assess whether this represents a robust structural difference.
- **Why it matters** The entire paper hinges on the claim that a spherical shell-like structure exists and is biologically meaningful. If the imaging evidence is not rigorously quantified and presented, the central conclusion is not established.
- **Resolution test** Provide the actual images and quantification data, including the number of kinetochores analyzed, the statistical test used, and the distribution of shell sizes. Show that the shell-like appearance is not an artifact of the rotational averaging procedure by presenting raw images and comparing with alternative analysis methods.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validity
- **Claim pointer** "Molecular dynamics simulations of CCAN assembly suggest that CENP-C–DNA interactions constrain the orientation of CCAN units, supporting a spherical shell-like organization via CENP-C oligomerization"
- **Evidence pointer** Figures 1-3, Results sections "CENP-C contributes to the organized orientation of CCAN units in the presence of DNA" and "CG-MD simulations suggest a shell-like organization of multiple CCAN units around a central CENP-C core"
- **Concern** The simulation model uses only 8 CCAN units with 40 bp DNA each, which is a substantial simplification of the kinetochore containing dozens of CCAN copies on centromeric chromatin. The authors acknowledge this limitation but then use the simulation results to support the cellular model. The initial configuration places CCAN units at specific radial distances with pre-assembled CENP-C cupin dimers, which may bias the outcome toward a shell-like arrangement. The alignment index metric is described but its biological significance is not fully justified. Most critically, the simulations show that CENP-C3D reduces orientational order, but the magnitude of this effect and its relationship to the experimental observations is not quantitatively compared.
- **Why it matters** The simulation provides the mechanistic framework for interpreting the experimental results. If the model is biased or the metrics are not biologically meaningful, the interpretation of the experimental data is compromised.
- **Resolution test** Show that the shell-like arrangement emerges from unbiased initial conditions, or justify why the chosen initial configuration is appropriate. Provide quantitative comparison between simulation predictions and experimental measurements. Demonstrate that the alignment index correlates with functional outcomes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Functional significance
- **Claim pointer** "CENP-C–DNA interaction is critical for kinetochore function"
- **Evidence pointer** Figure 3F, Results section "CENP-C–DNA interaction is critical for kinetochore function"
- **Concern** The functional experiments show that CENP-C3D fails to rescue mitotic arrest in CENP-C knockout cells, with mitotic index increasing by 10-20%. However, the authors previously reported that the CENP-C cupin domain is essential for function, and the 3D mutation is in the DNA-binding basic stretch. The distinction between the role of CENP-C DNA binding in organizing the shell structure versus its role in other CENP-C functions (e.g., CENP-A binding, kinetochore assembly) is not clearly established. The abnormal mitotic phenotypes (multipolar spindles, unaligned chromosomes) could result from general kinetochore dysfunction rather than specifically from loss of shell structure.
- **Why it matters** The paper claims that the spherical shell structure is functionally important, but the experiments do not directly test whether loss of the shell structure causes the observed phenotypes, as opposed to other consequences of CENP-C3D mutation.
- **Resolution test** Perform experiments that specifically disrupt the shell structure without affecting other CENP-C functions, or show that the 3D mutation specifically affects shell formation without altering other known CENP-C activities.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Cell cycle specificity
- **Claim pointer** "The spherical shell-like structure is most pronounced during S to G2 phases"
- **Evidence pointer** Figure 6, Results section "The spherical shell-like structure is most pronounced during S to G2 phases"
- **Concern** The cell cycle analysis uses CDK1-as synchronization and EdU labeling, but the quantification of shell structure at different cell cycle stages is not described in sufficient detail. The transition from "tight, small, dot-like structures" in G1 to "shell-like structure" in S/G2 is described qualitatively. The relationship between this cell cycle-dependent reorganization and the known cell cycle-dependent changes in kinetochore composition and centromere chromatin state is not discussed.
- **Why it matters** The cell cycle dependence is presented as a key feature of the structure, but without rigorous quantification and comparison across stages, this claim is not well supported.
- **Resolution test** Provide quantitative measurements of shell structure at each cell cycle stage with appropriate statistical comparisons. Discuss how the observed reorganization relates to known cell cycle-dependent kinetochore assembly processes.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods description
- **Evidence pointer** Methods section "MD simulations"
- **Issue** The description of the coarse-grained model construction is incomplete. The authors state that AlphaFold3 predictions were combined with additional model building, but the specific residues included in the CCU model, the mapping to coarse-grained beads, and the parameters for the elastic network are not described in sufficient detail for reproduction.
- **Required correction** Provide a more detailed description of the model construction, including the specific components of the CCU, the coarse-graining procedure, and the force field parameters. Consider including a supplementary methods section with full simulation details.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Quantification of shell size
- **Evidence pointer** Results section "CENP-C–DNA interaction is required for proper formation of the spherical shell-like structure in interphase DT40 cells"
- **Issue** The shell size measurements are reported as mean values (2.03 μm, 2.16 μm, 1.79 μm) but the number of cells/kinetochores measured, the standard deviation, and the statistical test used are not stated in the visible text.
- **Required correction** Include the sample sizes, measures of variance, and statistical tests for all quantified measurements.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion of related work
- **Evidence pointer** Discussion section
- **Issue** The authors mention a related shell-like structure observed in Xenopus cells but do not discuss in detail how their findings relate to or differ from this previous observation. The relationship between the interphase shell structure and the mitotic kinetochore plate structure is mentioned but not fully developed.
- **Required correction** Expand the discussion to more thoroughly compare and contrast the proposed shell structure with previous observations and to address the structural transition from interphase to mitosis.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Expansion microscopy validation
- **Evidence pointer** Methods section "Expansion microscopy"
- **Issue** The authors state that the expansion factor varies within ±1.1, but the method for measuring this variation is not described. The potential impact of differential expansion on the observed shell structure is not discussed.
- **Required correction** Describe how the expansion factor was measured and discuss the potential effects of local expansion heterogeneity on the interpretation of the shell structure.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Supplementary materials
- **Evidence pointer** Supplementary Materials section
- **Issue** The supplementary materials are listed but their content is not described. Given the complexity of the simulation and imaging methods, the supplementary information is likely essential for evaluating the work.
- **Required correction** Ensure that all supplementary figures, tables, and videos are described in the main text and that the supplementary materials are complete and accessible.

## Risk / unsupported claims
- The claim that CCAN units form a "spherical shell-like structure" in interphase kinetochores is not fully supported by the visible evidence, as the key imaging data and quantification are not provided
- The claim that CENP-C–DNA interactions "constrain the orientation of CCAN units" is based on simplified simulations that may not capture the complexity of the cellular environment
- The functional significance of the shell structure is not directly established, as the CENP-C3D mutation may affect other CENP-C functions beyond shell formation
- The cell cycle-dependent reorganization of the shell structure is described but not rigorously quantified
- The relationship between the proposed interphase shell structure and the known mitotic kinetochore architecture is not fully addressed
- The claim that the CENP-C basic stretch is conserved across species is stated but the supporting sequence alignment is not shown
- The temporal argument distinguishing direct CENP-C effects from indirect mitotic arrest effects is plausible but not conclusive, as the authors acknowledge