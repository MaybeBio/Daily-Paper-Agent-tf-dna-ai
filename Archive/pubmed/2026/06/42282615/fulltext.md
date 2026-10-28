# Simulation of transcription factor clustering in nuclei from molecular kinetics


## Abstract
  Transcription factors form clusters often described as condensates that exhibit emergent biophysical properties. Here we present a software package to simulate transcription factor spatial distributions from molecular diffusion and binding kinetics alone. The software simulates microscopy data and FRAP experiments and recapitulates the clustering behavior of experimentally characterized transcription factors. Our results demonstrate that condensate-like structures can emerge from molecular kinetics principles without invoking higher-order processes like phase separation.


## Methods

### Simulator overview
  SPARK is a browser-based tool implemented in Streamlit/Python, used to generate ground truth and "microscope-like” images from molecular data. The simulator consists of an interactive mode, which allows users to simulate and visualize results from a single set of parameters in the browser, and a batch mode where users can upload a CSV specifying a range of simulation parameters, the results of which can be downloaded. A single physics engine drives both modes. Additionally, a command-line implementation of the same engine enables running simulations on high-performance computing cores. Note that all simulated data are intended as helpful, intuition-building visualizations and not ground truth data.


#### Geometry and molecule count
  The nucleus and transcription factor (TF) molecules are modelled as spheres. The number of TF molecules is set from the user-supplied bulk concentration and the nuclear volume:  N=⌊c⋅10−9⋅Vnuc⋅10−15⋅NA⌋  with c in nM, Vnuc in μm3 and NA = 6.022 × 1023. All distances internal to the engine are tracked in micrometres; nanometres are used for image-space parameters (PSF, voxel size, slice spacing).


#### Time stepping and exposure averaging
  Three timescales coexist:

  For each output frame, molecule positions are compressed to a single per-molecule centroid by averaging across the exposure window. Molecule states (see below) are compressed by mode (most frequent state during the window); site positions are averaged; site occupancy is the logical OR across the window (a site is marked occupied if it was occupied at any point during exposure). This produces a faithful integration of motion and switching during the camera exposure rather than a single instantaneous snapshot.


#### Molecule states and dynamics

##### State space
  The simulator supports two state schemes:


##### Initial populations
  The user supplies the initial percentages of mobile molecules in Free, Intermediate, and Non-Specifically bound states. Initial positions are drawn uniformly inside the nucleus and states are sampled from the supplied distribution.


##### Per-state diffusion
  At every physics step Δt, every mobile molecule is assigned a diffusion coefficient D drawn from a Gaussian whose mean and standard deviation depend on its current state. Negative draws are clipped to a small positive value. Specifically bound molecules are pinned to their cognate site for the duration of binding and move along with the site.


##### First-order state transitions
  At every Δt, mobile molecules undergo Markov transitions at user-specified rates. NS-bound molecules return to the mobile pool with probability Δt/τNS where τNS is the user-specified mean non-specific residence time (1/τNS = koff or the non-specific off-rate). After unbinding, molecules get assigned to the Free or Intermediate state in proportion to the user-set Free:Intermediate population ratio (in 2-state mode the destination is always Free). Newly transitioned molecules are immediately re-assigned a state-appropriate diffusion coefficient.


##### Specific binding
  At each Δt, the positions of mobile molecules are queried against a k-d tree of binding-site coordinates (rebuilt only when sites have moved). Any mobile molecule within the user-set capture radius of a free site can bind with probability Pon. When cooperative binding is enabled, this probability becomes pon · [1 + (αn)h] clipped to 1, where n is the number of already-bound sites in that cluster, α is the cooperativity strength, and h is the Hill coefficient. Multiple molecules competing for the same site are resolved by a random shuffle and uniqueness pass such that each site can only be occupied by one molecule. On binding, the molecule is locked to the site position, the cluster's occupancy counter increments, and an unbind time is drawn:  tres=t+max(0.1,N(τres⋅s,σres⋅S))  where s is the site strength multiplier and τres, σres are user-set residence-time mean and standard deviation. Bound molecules are returned to the mobile pool (Free or Intermediate state) sampled by the same ratio used for NS unbinding.


##### Diffusive step and boundary
  Mobile molecules are propagated by an isotropic Gaussian step with per-axis standard deviation 2DΔt. Any mobile molecule whose updated position lies outside the nuclear sphere is projected radially back onto the surface.


#### Binding-site population

##### Spatial distribution and clustering
  A user-specified number of binding sites NBS are distributed within the nuclear volume following a user-specified cluster-size distribution. For simplicity, the user defines up to five cluster-size bins (binding sites per cluster) and a percentage of total sites in each bin, after which the simulator places clusters whose centres are drawn uniformly at random inside the nucleus. The binding sites for each cluster are drawn uniformly inside a ball of radius rcluster around the cluster centre. Any sites or centres that would fall outside the nuclear envelope are projected back onto the surface. After the requested clusters are placed, any remaining binding sites are distributed uniformly in the nucleus as singletons.


##### Optional synthetic site array
  In addition to the endogenous site population, an optional synthetic cluster (synthetic site array) of Nsyn sites can be placed; its centre is drawn uniformly inside the inner 70% of the nuclear radius and its members are drawn uniformly inside a ball of radius rsyn around that centre. The synthetic site clusters are distinctly colored in the ground truth images, and their positions over time are recorded for downstream analysis.


##### Binding-site strengths
  Each site is assigned a strength multiplier drawn from a five-bin categorical distribution with user-defined multipliers and bin probabilities. Strengths can be drawn either independently per site or correlated within each cluster (all sites in a cluster receive the same strength). Synthetic sites bypass this distribution and receive the user-set synthetic strength.


##### Site dynamics
  Each cluster of binding sites is assigned a diffusion coefficient drawn from a Gaussian with mean and standard deviation specified by the user (clipped at a small positive floor). Cluster centroids then move under fractional Brownian motion (fBm) with a Hurst exponent H (the default is H = 0.25, showing sub-diffusive Rouse-like polymer motion). B(t) is a unique zero-mean Gaussian random variable showing the position of the cluster at time t under fBm. The covariance of the trajectory between time t and a future timepoint s is given by:  Cov[BH(s),BH(t)]=12(∣s∣2H+∣t∣2H−∣s−t∣2H)  The discrete increments ξk=B(kΔt)−B((k−1)Δt) form the fractional Gaussian noise (fGn), a stationary sequence whose autocovariance at lag k (the separation between two increments) is:  C(k)=σ22(∣k−1∣2H−2∣k∣2H+∣k+1∣2H)  where σ2 = 2DΔt is the per-step variance and D is the cluster diffusion coefficient. The normalized autocovariance γ(k) = C(k)/σ2 satisfies γ(0) = 1. For H = ½, increments are uncorrelated (standard Brownian motion); H < ½ yields sub-diffusive (anti-persistent) increments (default); H > ½ yields super-diffusive (persistent) increments.


###### Davies–Harte construction.
  At each display frame, n fGn increments are generated simultaneously for all clusters and all three spatial axes via the circulant embedding of the autocovariance matrix:


###### Cross-frame conditioning.
  A Davies-Harte block drawn independently at each frame boundary would break the global autocorrelation structure of fBm. The first increment of each new frame block is therefore conditioned on the terminal increment of the previous frame Δx−1 via the exact conditional distribution of a stationary Gaussian process (Gaussian bridge):  Δx0bridge=γ1Δx−1+1−γ(1)2σ,Z,Z∼N(0,I3)  where γ(1) = ½(22H − 2) is the lag-1 normalized autocovariance. The remaining Davies-Harte increments are mean-corrected by the kriging update:  Δxkcond=ΔxkDH+γ(k)(Δx0bridge−Δx0DH),k=1,…,nf  This approximation preserves the long-range autocorrelation structure of fBm across frame boundaries while keeping memory bounded to a single step.

  On top of cluster motion, every individual site receives an independent Gaussian “jiggle” at every physics step, to reflect changing conformations of binding sites that are close to each other. Sites are constrained to remain at least one capture radius inside the nuclear surface so that no capture sphere is clipped by the boundary.


#### Image formation

##### Voxelization and point-spread function
  For each output frame the recorded positions across the exposure window are concatenated and binned onto an isotropic 3D grid with a user-set voxel size, corresponding to the detector pixel size. Each binned position is convolved with an anisotropic 3D Gaussian point-spread function (PSF) with separately specified lateral and axial full-widths at half maximum (FWHMxy, FWHMz). Standard deviations are obtained as σ=FWHM∕(22ln2). The PSF kernel is truncated at 3σ in each axis and normalized to unit mass before deposition such that each molecule represents 1 intensity unit. Voxels falling outside the nuclear sphere are set to zero.


##### Z-slice projection
  The 3D voxel grid is sliced into 2D z-planes spaced at the user-set inter-slice distance. Each slice is the single voxel layer at the z-coordinate (no axial integration beyond what the PSF already provides). Slices are saved as multi-page TIFFs.


##### Intensity normalization
  Two mutually exclusive normalization modes are supported:


##### Output products
  Three image products may be saved per frame (as TIFFs):

  A CSV containing the positions and state of each molecule in each frame is also available to download. When a synthetic site array is present, a centroid CSV is also written, giving the centre-of-mass of the synthetic cluster. Finally, a .pkl file that saves the rendered images can be downloaded, allowing users to upload it to perform FRAP at a later time.


#### Reproducibility
  To support exact replay and to support comparing nominally identical conditions across rendering parameters, the simulator has an integer-seed mechanism that makes every random draw — site positions, strengths, per-cluster diffusion coefficients, fBm increments and jiggle, initial molecule placements, state transitions, binding dice, and residence-time draws — deterministic.


##### Interactive mode
  A "Use random seed (reproducible)" checkbox in the General Parameters panel exposes an integer seed input. When checked, the engine calls numpy.random.seed(seed) once at entry, before any random draw. The user can choose whether to freeze the trajectories (visualization parameters can be changed) or only the binding site characteristics (molecule kinetic parameters can also be changed).


##### Batch mode
  Per-row reproducibility is controlled by three optional CSV columns:

  The per-row seed is resolved as: (1) the row's sim_seed cell, if a usable integer; otherwise (2) base_seed + row_index, where base_seed is the UI-supplied base integer (mirroring the SLURM --seed convention); otherwise (3) operating-system entropy. Because every random draw inside the engine is reached deterministically from a single global seed, two rows that share a sim_group and seed produce identical output, and two rows that share a site_group and seed produce identical sites with independent motion — the same operational guarantee as the HPC implementation, achieved without an explicit cache. The seed used for every row is logged to seeds_used.csv inside the output ZIP.


#### FRAP Module
  This allows the user to FRAP a cluster in a simulated nucleus. The molecules in the FRAP user-defined spherical region-of-interest are turned to an irreversible dark, “bleached” state. A recovery curve is generated, measuring the intensity within the same region. The post-FRAP images and intensity values are available to download.


#### Batch processing
  A batch run is driven by a CSV in which each row is a complete parameter set. A pre-filled template is generated by the application from the same defaults used by the interactive mode, with the optional reproducibility columns (sim_seed, sim_group, site_group) appended at the end. Rows are processed sequentially and outputs are bundled into a single downloadable ZIP with a top-level subfolder per row. When auto-normalize brightness mode is selected, the simulator runs in two phases: all rows are simulated and gridded in phase 1 to establish the global maximum intensity; phase 2 then renders all rows against that single vmax so that intensities are directly comparable across the entire batch.


#### HPC implementation
  The same physics is also implemented as a standalone command-line tool for parallel processing on an HPC. There are two operational differences:


### Simulations generated for this manuscript
  All simulations, except for the FRAP and fusion examples, were generated using the HPC version of SPARK. Dorsal concentrations on the ventral side of the embryo (500 nM) were obtained from published work13 and the concentrations on the medial (406 nM) and lateral (219 nM) sides were estimated through intensity calibrations. The molecules were modelled with cooperative binding with a Hill coefficient of 100, as detailed previously10. Bicoid concentrations along the anterior-posterior gradient (20%: 25 nM, 30%: 16 nM, 40%: 11 nM, 50%: 7 nM, and 60%: 3.5 nM) were estimated from published work17. Bicoid clusters in SPARK-generated images were segmented using a previously-published custom segmentation pipeline developed in the lab9,10 and were overlaid on the molecular count images to obtain the number of molecules per cluster. Five nuclei were simulated for each concentration and the results were pooled. Sox2 concentrations and the clustering of binding sites in mouse ES cells were obtained from published work20,21. Renderings were generated from the positions of only the specifically bound molecules. Virtual FRAP was done for a simulated protein with BRD4-like characteristics (high concentration, large number of binding sites), and intensities were normalized to the pre-bleach intensity within the bleached ROI. Many examples of cluster fusion were seen across various simulations - the displayed example is for the BRD4-like protein.

  Full parameter sets for each displayed example can be found and reused from the dropdown menu of the GUI, or in the “interactive_presets.csv” present in the zipped folder.


### Imaging

#### Fly lines used
  The fly line used for bicoid imaging was yw; his2av-mrfp1; BcdE1, egfp-bcd. Dorsal images are from heterozygous progeny from the lines yw; Dorsal-mNeonGreen/Cyo; and nos>MCP-mCherry (III) crossed with males containing an MS2 reporter.


#### Embryo preparation for live imaging
  Drosophila embryos were manually dechorionated by gently rolling them on double-sided tape using a blunt needle. Dechorionated embryos were arranged on an agar pad and transferred onto an adhesive heptane-acrylic spot on a 25mm glass coverslip (lattice light-sheet) or the hydrophobic side of a semi-permeable membrane in a 3D printed sample holder (benchtop confocal).


#### Lattice light-sheet imaging
  Lattice light-sheet volumetric imaging of Bicoid was performed on a Multimodal Optical Scope with Adaptive Imaging Correction (MOSAIC)22. The 488 nm excitation laser was used at 10% (0.552 mW at the back focal plane of the excitation objective) to excite eGFP. A volume of 18.9 μm sampling z-planes spaced 0.3 μm apart was acquired at various positions along the anterior-posterior axis of the embryo, with 30 ms exposure time. Dorsal images were obtained from previously published work10.


#### Spinning disk confocal imaging
  Confocal imaging was performed on an Andor BC43 Spinning Disk Confocal Microscope with a 20x/0.8 NA objective to obtain a full-embryo image. The 488 nm excitation laser was used at 15% (16.9 mW) to excite eGFP. A volume of 34 μm sampling z-planes spaced 0.3 μm apart was acquired, with 100 ms exposure time.


### Image Analysis
  Lattice light-sheet images were pre-processed using GPU-accelerated 3D deconvolution via CUDA23. Deconvolution was done using a Richardson-Lucy based algorithm with 5 iterations, utilizing point spread functions (PSFs) captured from bead images acquired on the day of imaging to ensure accurate correction.

  All images were processed, scaled and visualized in FIJI or Napari. Displayed kymographs were constructed by taking a 600 nm maximum projection across z-slices, generating a kymograph for each column in the red rectangle, and max-projecting the 5 resulting kymographs.

  Data from other papers (Fig. 2) was directly approximated from figures using PlotDigitizer24.


### Software Development and AI Assistance
  SPARK was implemented in Python by the authors with the assistance of a large language model (Anthropic Claude Opus, online and through Claude Code). Claude was used for code generation, GUI creation, editing, and for the suggestion and implementation of algorithms such as the Davies–Harte construction and cross-frame conditioning for approximate fractional Brownian motion. All AI-assisted code and text were reviewed, tested, and validated by the authors, who take full responsibility for the correctness of the implementation.


## Supplementary Material

## Data Availability:
  All simulated data can be reproduced using the provided code.


## Code Availability:
  Developed code is available on Zenodo: https://doi.org/10.5281/zenodo.20533508.


## Acknowledgements
  We thank all members of the Mir lab for insightful discussions, rigorous testing of the software, and critical feedback on initial versions of the manuscript. We especially thank Dr. Apratim Mukherjee for construction of the lattice light-sheet microscope and Dr. Samantha Fallacaro for developing the custom cluster segmentation pipeline and providing Dorsal-mNeonGreen images. We thank Dr. Mariko L. Bennett for access to their lab’s confocal microscope (Andor BC43 Spinning Disk Confocal Microscope). The work was supported by National Institutes of Health grant DP2HD108775 (M.M.) and Howard Hughes Medical Institute, Freeman Hrabowski Scholars Program (M.M).