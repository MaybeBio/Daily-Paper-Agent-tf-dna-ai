## Review setup
- **Input scope** Full manuscript text (abstract, methods, supplementary material description, data/code availability statements)
- **Assessment boundary** Scientific claims, methodological soundness, and reproducibility as presented in the provided text; no figures, tables, or supplementary files were available for inspection
- **Shared manuscript claim summary** The authors present SPARK, a simulation software package that models transcription factor (TF) spatial distributions from molecular diffusion and binding kinetics alone, and claim that condensate-like TF clusters can emerge from these principles without invoking phase separation or other higher-order processes
- **Visible evidence base** Abstract, complete methods section, simulation parameters for Dorsal, Bicoid, and Sox2, imaging protocols, and code availability statement
- **Missing materials affecting confidence** All figures, tables, supplementary figures, validation datasets, comparison plots against experimental data, and the actual code repository contents; the manuscript text references figures and comparisons that cannot be independently assessed

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful simulation tool for exploring whether TF clustering can arise from simple molecular kinetics. The software architecture is thoughtfully designed, with attention to reproducibility, batch processing, and HPC deployment. However, the central scientific claim that condensate-like structures emerge from kinetics alone is not adequately supported by the evidence presented in the text. The manuscript lacks quantitative validation against experimental data, provides no statistical analysis of clustering behavior, and does not demonstrate that the simulated clusters are qualitatively or quantitatively similar to those observed experimentally. The absence of figures and quantitative comparisons makes it impossible to evaluate whether the simulations recapitulate experimental observations as claimed.
- **Who would be interested in the results, and why** Researchers studying transcription factor dynamics, nuclear organization, and gene regulation would find this tool of interest. The software addresses a genuine need for simulating TF spatial distributions from first principles, which could complement experimental studies of transcriptional condensates. The community investigating whether phase separation is necessary for TF clustering would also be interested, as the tool provides a testbed for exploring kinetic explanations. Developers of biophysical simulation tools may find the technical implementation useful.
- **Major strengths** The software design emphasizes reproducibility through seed management and batch processing, which is commendable. The inclusion of multiple operational modes (interactive, batch, HPC) increases accessibility. The treatment of binding-site dynamics using fractional Brownian motion with Davies-Harte construction is technically sophisticated. The authors are transparent about AI assistance in code development, which is appropriate. The integration of image formation (PSF convolution, voxelization) with molecular simulation addresses the need to compare simulations directly with microscopy data.
- **Major Concerns** 
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "recapitulates the clustering behavior of experimentally characterized transcription factors"
  - **Evidence pointer** Figures referenced but not provided; "location not provided"
  - **Concern** The central claim that the simulations recapitulate experimental clustering behavior is not supported by any quantitative comparison presented in the text. The methods describe simulations for Dorsal, Bicoid, and Sox2, and mention comparisons to published data, but no statistical measures, correlation coefficients, or quantitative metrics are provided. The statement that "condensate-like structures can emerge" is presented without defining what constitutes a condensate-like structure in the simulation output or how this was assessed.
  - **Why it matters** The primary scientific contribution is the demonstration that kinetic processes alone can produce clustering. Without quantitative validation against experimental data, the claim remains anecdotal. The manuscript cannot establish that the simulated clusters resemble those observed experimentally in size, density, dynamics, or other measurable properties.
  - **Resolution test** Provide quantitative comparisons between simulated and experimental cluster properties (e.g., size distributions, density profiles, FRAP recovery curves) with appropriate statistical tests. Define criteria for "condensate-like" and demonstrate that simulated clusters meet these criteria.
  
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "condensate-like structures can emerge from molecular kinetics principles without invoking higher-order processes like phase separation"
  - **Evidence pointer** Methods section, "Simulations generated for this manuscript"; "location not provided"
  - **Concern** The manuscript does not demonstrate that the observed clustering is not an artifact of the simulation parameters or implementation. The Hill coefficient of 100 for cooperative binding is extremely high and may effectively create clusters by construction rather than by emergent kinetics. The parameter choices are not justified, and no sensitivity analysis is presented. The claim that clustering emerges "without invoking higher-order processes" is undermined if the cooperative binding parameters are tuned to produce clustering.
  - **Why it matters** The distinction between emergent clustering from simple kinetics versus clustering driven by strong cooperative interactions is central to the paper's thesis. If the clustering requires extreme parameter values, the biological relevance is questionable. The claim of emergence requires demonstrating that clustering occurs across a reasonable parameter range and is not a consequence of parameter fine-tuning.
  - **Resolution test** Provide a parameter sensitivity analysis showing clustering behavior across a range of cooperative binding strengths, Hill coefficients, and concentrations. Justify the choice of Hill coefficient 100 with reference to experimental measurements or theoretical arguments.
  
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility
  - **Claim pointer** "All simulated data can be reproduced using the provided code"
  - **Evidence pointer** Data Availability and Code Availability statements
  - **Concern** While the code is available on Zenodo, the manuscript does not provide sufficient detail to reproduce the specific simulations shown. The parameter sets are said to be available in the GUI dropdown or "interactive_presets.csv," but the specific parameters used for each figure are not listed in the text. The version of the code used for the manuscript is not specified, and there is no documentation of the computational environment required.
  - **Why it matters** Reproducibility is a core requirement for computational papers. Without explicit parameter listings and version information, other researchers cannot verify the results or build upon them. The claim of reproducibility cannot be evaluated from the provided materials.
  - **Resolution test** Provide a table of all parameters used for each simulation shown in the figures, specify the code version and commit hash, and document the software environment (Python version, package versions).
  
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Validation
  - **Claim pointer** "The software simulates microscopy data and FRAP experiments"
  - **Evidence pointer** Methods, "Image formation" and "FRAP module"; "location not provided"
  - **Concern** The image formation model uses a Gaussian PSF and simple voxelization, which may not accurately represent the optical properties of the specific microscopy modalities used for comparison (lattice light-sheet, spinning disk confocal). The FRAP module bleaches molecules in a spherical region and measures recovery, but no validation is shown that this produces realistic FRAP curves comparable to experimental data.
  - **Why it matters** If the simulated images and FRAP curves do not faithfully reproduce experimental artifacts and noise characteristics, comparisons with experimental data may be misleading. The claim that the software simulates microscopy data requires validation against known experimental benchmarks.
  - **Resolution test** Compare simulated images with experimental images of known structures, quantify image similarity metrics, and validate FRAP recovery curves against analytical solutions or experimental data.
  
  - **Concern ID** R1-M5
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** "Our results demonstrate that condensate-like structures can emerge from molecular kinetics principles without invoking higher-order processes like phase separation"
  - **Evidence pointer** Abstract; "location not provided"
  - **Concern** The broader scientific context is not adequately addressed. The manuscript does not discuss how these findings relate to the extensive literature on phase separation in transcription, nor does it clearly articulate what new biological insight is gained. The claim that kinetics alone can produce clustering is presented as novel, but the relationship to existing models of TF dynamics and clustering is not explored.
  - **Why it matters** For a broad-impact journal, the manuscript must clearly articulate the advance over existing work and the implications for understanding transcriptional regulation. Without this context, the significance of the finding is unclear.
  - **Resolution test** Expand the discussion to address how these simulations inform the ongoing debate about phase separation versus other mechanisms of TF clustering, and what predictions the model makes that could be tested experimentally.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Methods, "State space"
  - **Evidence pointer** "The simulator supports two state schemes:" with no further description
  - **Issue** The two state schemes are mentioned but not described. This is a critical omission for understanding the model.
  - **Required correction** Describe both state schemes explicitly, including the states in each and how they differ.
  
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Methods, "Intensity normalization"
  - **Evidence pointer** "Two mutually exclusive normalization modes are supported:" with no further description
  - **Issue** The normalization modes are not described, making it impossible to understand how image intensities are scaled.
  - **Required correction** Describe both normalization modes and their intended use cases.
  
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Methods, "Davies-Harte construction"
  - **Evidence pointer** "via the circulant embedding of the autocovariance matrix:" with no further detail
  - **Issue** The description ends abruptly without explaining the implementation.
  - **Required correction** Provide a complete description of the Davies-Harte construction as implemented, or reference a standard text.
  
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Methods, "HPC implementation"
  - **Evidence pointer** "There are two operational differences:" with no further description
  - **Issue** The differences between the HPC and GUI versions are not described.
  - **Required correction** List the two operational differences explicitly.
  
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Methods, "Batch mode"
  - **Evidence pointer** "Per-row reproducibility is controlled by three optional CSV columns:" with no further description
  - **Issue** The three columns are not named or described.
  - **Required correction** Name and describe the three optional CSV columns.
  
  - **Concern ID** R1-m6
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Methods, "Output products"
  - **Evidence pointer** "Three image products may be saved per frame (as TIFFs):" with no further description
  - **Issue** The three image products are not listed.
  - **Required correction** List and describe the three image products.
  
  - **Concern ID** R1-m7
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Methods, "Cross-frame conditioning"
  - **Evidence pointer** The equation for Δx0bridge is presented without derivation or explanation of terms
  - **Issue** The notation is not fully explained, particularly the meaning of γ1 and the relationship to the Davies-Harte construction.
  - **Required correction** Define all terms in the equation and explain the conditioning procedure more clearly.
  
  - **Concern ID** R1-m8
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Methods, "Simulations generated for this manuscript"
  - **Evidence pointer** "Full parameter sets for each displayed example can be found and reused from the dropdown menu of the GUI"
  - **Issue** The parameter sets are not listed in the manuscript, making it difficult to assess the simulations without accessing the software.
  - **Required correction** Include a supplementary table with all parameters used for each simulation.
  
  - **Concern ID** R1-m9
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Methods, "Imaging"
  - **Evidence pointer** "Dorsal images are from heterozygous progeny from the lines yw; Dorsal-mNeonGreen/Cyo; and nos>MCP-mCherry (III) crossed with males containing an MS2 reporter."
  - **Issue** The description of the genetic cross is incomplete and difficult to follow.
  - **Required correction** Provide a clearer description of the genetic cross and the purpose of the MS2 reporter.
  
  - **Concern ID** R1-m10
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Methods, "Image Analysis"
  - **Evidence pointer** "Data from other papers (Fig. 2) was directly approximated from figures using PlotDigitizer"
  - **Issue** The use of PlotDigitizer to extract data from published figures introduces potential inaccuracies that are not discussed.
  - **Required correction** Acknowledge the limitations of this approach and describe how the accuracy of the digitization was verified.

## Risk / unsupported claims
- The claim that simulations "recapitulate the clustering behavior of experimentally characterized transcription factors" is unsupported without quantitative comparisons to experimental data
- The claim that "condensate-like structures can emerge from molecular kinetics principles" is not substantiated without a clear definition of condensate-like and statistical analysis of simulation outputs
- The assertion that clustering emerges "without invoking higher-order processes like phase separation" is weakened by the use of a Hill coefficient of 100, which may effectively build in clustering
- The statement that "all simulated data can be reproduced using the provided code" cannot be verified without version information and complete parameter listings
- The claim that the software "simulates microscopy data" is not validated against experimental imaging artifacts or noise characteristics
- The relevance of the simulations to biological systems is asserted but not demonstrated through predictive power or novel testable hypotheses