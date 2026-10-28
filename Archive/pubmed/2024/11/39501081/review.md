## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, methods, and figure legends
- **Assessment boundary** Technical and scientific evaluation of the presented methods, results, and claims based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors present a deep learning-based method for three-dimensional localization and tracking of chromosomal loci in live E. coli cells using astigmatism-based PSF engineering, achieving sub-61 nm precision at low signal-to-background ratios, and report that some loci localize to the nucleoid periphery and exhibit subdiffusive motion both longitudinally and radially
- **Visible evidence base** Main text figures 1-5, supplementary figures referenced (1-15), supplementary tables (S1), and supplementary data files (Dataset S1, Dataset S2)
- **Missing materials affecting confidence** Supplementary Information sections A.1-A.10 referenced but not provided in full; Supplementary Figures 1-15 not available for direct inspection; detailed statistical analyses and reproducibility data not fully accessible; raw imaging data and code availability not stated

## Reviewer
- **Overall assessment** This manuscript addresses a technically challenging problem in bacterial cell biology: three-dimensional tracking of chromosomal loci throughout the cell cycle. The methodological development combining deep learning with astigmatism-based PSF engineering is sound and represents a meaningful advance. The key biological finding, that some loci occupy the nucleoid periphery and exhibit subdiffusive radial motion, is potentially interesting but requires stronger validation given the technical complexity of the measurements. The manuscript is generally well-written and the methods are described in sufficient detail for reproduction, though several concerns regarding validation, statistical rigor, and interpretation need to be addressed.

- **Who would be interested in the results, and why** Researchers in bacterial cell biology, chromosome organization and dynamics, and single-molecule microscopy would find this work of interest. The methodological advance in 3D localization at low signal-to-background ratios in live cells has broader applicability for studying other DNA-binding proteins and cellular structures. The biological findings on nucleoid periphery localization and subdiffusive motion contribute to ongoing discussions about chromosome architecture and its functional implications.

- **Major Strengths**
  1. The development of a deep learning approach for 3D localization under challenging low signal-to-background conditions with heterogeneous cellular background is technically impressive and addresses a real need in the field.
  2. The use of a small 12-site operator array (malO) rather than large arrays reduces potential physiological perturbations, a thoughtful experimental design choice.
  3. The combination of multiple validation approaches (bead measurements, CRLB calculations, PALM experiments, MSD analysis) provides a multi-faceted assessment of localization performance.
  4. The observation of radial symmetry in y and z distributions serves as an internal consistency check, strengthening confidence in the 3D localization accuracy.
  5. The finding that individual loci explore the full radial width on minute timescales, while being subdiffusive, provides new dynamic information not previously accessible.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validation
- **Claim pointer** The claim that the method achieves "a precision better than 61 nm at a signal-to-background ratio of ~4 on a heterogeneous cell background"
- **Evidence point** Figure 2, Supplementary Figures 8-9, Section "Determining the Z-range in which the 3D localization precision is stable"
- **Concern** The localization precision is characterized using immobilized fluorescent beads, not actual chromosomal loci in cells. While the signal-to-background ratio was matched, the bead measurements do not account for potential sources of error specific to loci imaging in live cells, such as motion blur during exposure, cell drift, or the complex photophysical behavior of MalI-YFP bound to the operator array. The manuscript does not clearly demonstrate that the precision achieved on beads translates to equivalent precision for loci in living cells. Additionally, the statement that precision is "better than 61 nm" appears to be derived from a specific z-range, but the range over which this precision holds and how it varies across the full z-range of interest is not clearly specified.
- **Why it matters** The central technical claim of the paper rests on the localization precision achieved. If the precision in live cells is substantially worse than on beads, the biological conclusions about subdiffusive motion and nucleoid periphery localization could be compromised. The distinction between precision on static beads versus moving loci in cells is critical for interpreting the MSD measurements.
- **Resolution test** Provide validation of localization precision using a biologically relevant control, such as loci immobilized by chemical fixation or in cells where motion is arrested. Alternatively, demonstrate through simulations that the bead-based precision estimates are conservative and account for the additional error sources in live cells. Quantify the expected contribution of motion blur to localization error at the exposure times used.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The claim that loci exhibit "subdiffusive movement both longitudinally and radially" based on MSD analysis
- **Evidence point** Figure 4, Supplementary Figure 13, Section "3D tracking of single loci demonstrates subdiffusive movement radially and longitudinally"
- **Concern** The MSD analysis combines data from two different timescales (seconds and minutes) with different experimental protocols. The manuscript does not clearly describe how these datasets were integrated, whether the number of trajectories and time points are sufficient for reliable MSD estimation at each lag time, or how the localization error term (ε) was estimated and incorporated. The alpha values reported (0.40 without error correction, 0.53 with) show substantial sensitivity to the error model, yet the manuscript does not discuss which value is more reliable or how the error term was determined. Additionally, the radial MSD analysis is based on the assumption of a ring-shaped distribution, but the manuscript does not fully address whether the observed plateau could be an artifact of the limited z-range or the localization error.
- **Why it matters** The subdiffusive behavior is a key biological finding. If the MSD analysis is not statistically robust or is sensitive to the error model, the conclusion about subdiffusive motion could be overstated. The distinction between alpha = 0.4 and 0.53 is biologically meaningful and needs to be resolved with confidence.
- **Resolution test** Provide a more detailed description of the MSD analysis, including the number of trajectories, the range of lag times used for fitting, the method for estimating the localization error term, and a sensitivity analysis showing how alpha varies with different error estimates. Consider using complementary analysis methods (e.g., velocity autocorrelation, van Hove functions) to confirm subdiffusive behavior.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** The claim that "some loci are at the periphery of the nucleoid for large parts of the cell cycle" and the interpretation that this may be due to "interactions with the cell membrane or proximity to highly expressed genes"
- **Evidence point** Figure 3, Section "3D localization of chromosomal loci throughout the cell cycle"
- **Concern** The biological interpretation of the nucleoid periphery localization is speculative and not directly tested. The manuscript does not provide independent evidence for membrane interactions or gene expression proximity. Furthermore, the comparison between the three loci (oriC, midway, ter) is descriptive rather than quantitative. The manuscript does not report statistical tests comparing the radial distributions of the three loci, nor does it address whether the observed differences could be explained by differences in the local chromatin environment, DNA replication timing, or other factors. The claim that this has "not been directly observed before" should be more carefully qualified, as previous studies have suggested non-random chromosome positioning.
- **Why it matters** The biological significance of the work depends on the interpretation of the spatial distributions. If the periphery localization is not robustly demonstrated or could be explained by technical artifacts, the biological conclusions would be weakened. The speculative interpretation without direct testing may overreach the data.
- **Resolution test** Provide quantitative comparisons of the radial distributions between loci with appropriate statistical tests. Consider additional experiments or analyses to test the proposed mechanisms (e.g., colocalization with membrane markers, comparison with gene expression data). Alternatively, temper the interpretation and clearly distinguish between observed phenomena and proposed explanations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological completeness
- **Claim pointer** The claim that the method enables "three-dimensional localization and tracking of chromosomal loci throughout the Escherichia coli cell cycle"
- **Evidence point** Figures 3-5, Section "3D tracking of single loci demonstrates subdiffusive movement radially and longitudinally"
- **Concern** The manuscript demonstrates tracking over timescales of seconds to minutes, but the claim of tracking "throughout the cell cycle" implies coverage of the full cell cycle duration. The manuscript does not clearly state the total duration of tracking for individual loci, how many complete cell cycles were observed, or how tracking was maintained through cell division when loci are duplicated and segregated. The analysis appears to pool data from many cells rather than following individual loci through complete cell cycles. The relationship between the tracking data and cell cycle progression (e.g., using cell length or division events as markers) is not clearly established.
- **Why it matters** The title and abstract make a strong claim about tracking throughout the cell cycle. If the data do not actually cover complete cell cycles for individual loci, the claim is overstated. Understanding how loci behave through replication and division is a key biological question that the method should address.
- **Resolution test** Clarify the duration of tracking relative to cell cycle length, describe how many complete cell cycles were captured, and explain how tracking was maintained through division events. If complete cell cycle tracking was not achieved, revise the claims accordingly.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1
- **Evidence point** Figure 1, Section "Mapping 3D loci positions to internal cell coordinates"
- **Issue** The description of the coordinate transformation from image coordinates to internal cell coordinates is brief. The definition of the "backbone" as a second-degree polynomial and the handling of cell curvature are not fully explained.
- **Required correction** Provide a more detailed description of the coordinate transformation, including how the backbone is fitted, how the origin is defined, and how cells with significant curvature are handled.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Training data generation
- **Evidence point** Section "Simulating ground truth data and training the field-dependant neural network", Supplementary Figure 1
- **Issue** The manuscript states that simulated images were used for training but does not provide sufficient detail on the simulation parameters (e.g., number of training images, range of signal-to-background ratios, cell density variations) to allow reproduction.
- **Required correction** Include a more detailed description of the simulation procedure, including all relevant parameters, in the Methods or Supplementary Information.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 4
- **Evidence point** Figure 4, Section "3D tracking of single loci demonstrates subdiffusive movement radially and longitudinally"
- **Issue** The manuscript reports that MSD values are based on >=167 trajectories but does not specify how many cells or independent biological replicates these trajectories come from, nor how variability between replicates was handled.
- **Required correction** Report the number of independent biological replicates, the number of cells per replicate, and how between-replicate variability was incorporated into the error estimates.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Code and data availability
- **Evidence point** Throughout the manuscript
- **Issue** No statement is provided regarding the availability of the trained neural network models, analysis code, or raw imaging data.
- **Required correction** Add a data and code availability statement describing what is available and how to access it.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence point** Section "Discussion"
- **Issue** The discussion of the biological implications is relatively brief and does not fully contextualize the findings within the broader literature on bacterial chromosome organization and dynamics.
- **Required correction** Expand the discussion to more thoroughly compare the findings with previous studies and discuss the implications for understanding chromosome organization and gene regulation.

## Risk / unsupported claims
1. The claim of "precision better than 61 nm" is based on bead measurements and may not directly translate to live cell conditions; the manuscript does not adequately address this gap.
2. The subdiffusive behavior conclusion is sensitive to the error model used in MSD analysis, and the manuscript does not provide sufficient sensitivity analysis.
3. The biological interpretation of nucleoid periphery localization (membrane interactions, gene proximity) is speculative and not directly tested.
4. The claim of tracking "throughout the cell cycle" is not fully supported by the presented data, which appear to cover shorter timescales.
5. The statement that the radial symmetry of y and z distributions confirms the accuracy of 3D localization is reasonable but should be more rigorously quantified.
6. The manuscript does not provide a direct comparison of the new method's performance against existing 3D localization approaches for chromosomal loci, making it difficult to assess the relative advantage.