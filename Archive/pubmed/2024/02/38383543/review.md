## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, methods, and supplementary figure/table references
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and alignment with Nature-style criteria based solely on the provided manuscript content
- **Shared manuscript claim summary** The authors present a computational pipeline integrating a GRU-based variational autoencoder with Metropolis-Hastings sampling (VAE-MH), Rosetta FlexPepDock, and MD simulations with MM/GBSA to design target-specific peptide inhibitors. They report improved binding for β-catenin (6 of 12 peptides, best IC50 0.010 ± 0.06 μM, 15-fold over parent) and NEMO (2 of 4 peptides) compared to parent peptides.
- **Visible evidence base** Abstract, Introduction, Results sections for β-catenin and NEMO, Methods sections for data preparation, sequence generation, docking, MD/MM-GBSA, experimental assays, and supplementary table/figure references
- **Missing materials affecting confidence** Supplementary figures and tables (e.g., Supplementary Figs. 1-11, Supplementary Tables 1-6) are referenced but not provided; raw experimental data are not available; details of VAE architecture hyperparameters, training convergence, and MH sampling convergence diagnostics are incomplete; no code or model availability statement is visible

## Reviewer
- **Overall assessment** This manuscript describes a multi-stage computational workflow for peptide extension design and validates it experimentally on two targets. The integration of generative deep learning with structure-based biophysical methods is timely and of potential interest. However, several technical concerns limit the strength of the claims as currently presented. The modest experimental improvements, incomplete reporting of computational details, and lack of rigorous statistical treatment of the experimental data prevent full support of the conclusions from the provided evidence.
- **Who would be interested in the results, and why** Researchers in computational peptide and protein design, deep learning for biological sequences, and drug discovery targeting protein-protein interactions would find this work relevant. The combination of generative models with physics-based validation addresses a practical need for reducing search spaces in peptide design, and the experimental validation on two disease-relevant targets (β-catenin in Wnt signaling, NEMO in NF-κB pathway) broadens its appeal.
- **Major strengths**
  - The multi-stage pipeline (VAE-MH generation, FlexPepDock ranking, MD/MM-GBSA refinement) is a sensible hierarchical strategy that balances computational cost with accuracy.
  - The use of transfer learning via iterative fine-tuning with target-specific data addresses the scarcity of labeled peptide-protein binding data.
  - Experimental validation on two distinct targets with different binding surface characteristics (β-catenin groove vs. NEMO flat surface) demonstrates some generalizability.
  - The inclusion of a "mistaken" peptide as a control (CAL-7 error) is an honest and useful demonstration of specificity.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Experimental validation and statistical rigor
  - **Claim pointer** The abstract states "six exhibit improved binding affinity compared to the parent peptide" for β-catenin and "two of the four tested peptides display substantially enhanced binding" for NEMO.
  - **Evidence pointer** Results sections for β-catenin and NEMO; Tables 1 and 3; Supplementary Figs. 4 and 8
  - **Concern** The experimental validation is based on competitive binding assays (FP and HTRF) with IC50 values reported, but no statistical analysis is presented. The reported IC50 for the best peptide CAL-2 is 0.010 ± 0.06 μM, where the standard deviation exceeds the mean by sixfold, which is unusual and suggests either a typographical error or highly variable measurements. No replicates, error bars, or confidence intervals are shown for the IC50 determinations in the main text. The claim of "improved binding" for 6 of 12 β-catenin peptides and 2 of 4 NEMO peptides lacks statistical significance testing. The manuscript does not report whether these improvements are reproducible across independent experiments or whether the differences are within experimental noise.
  - **Why it matters** The central claim of the paper is that the computational pipeline successfully designs improved peptide inhibitors. Without rigorous statistical treatment of the experimental data, including appropriate replicates, error propagation, and significance testing, the improvements could be within experimental variability. This is particularly concerning given the large reported uncertainty on the best IC50 value.
  - **Resolution test** Provide full experimental details including number of independent replicates, standard error of the mean, and statistical tests (e.g., t-test or ANOVA) comparing designed peptides to parent peptides. Clarify the reported uncertainty on CAL-2 IC50 and ensure it is correctly calculated and presented. If the uncertainty is genuinely large, discuss the implications for the reliability of the improvement claim.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Computational methodology reproducibility
  - **Claim pointer** The Methods section describes the VAE-MH process, including GRU-based VAE architecture, MH sampling, and fine-tuning, but key implementation details are missing.
  - **Evidence pointer** Methods sections "Latent space encoding", "Conditional sequence generation", "Rosetta FlexPepDock", "MM/GBSA-binding free energy calculation"
  - **Concern** The manuscript does not provide sufficient details to reproduce the computational pipeline. Missing information includes: (1) VAE architecture specifics (number of layers, hidden dimensions, latent dimension size, activation functions, regularization parameters); (2) training hyperparameters (learning rate, batch size, number of epochs, optimizer choice, early stopping criteria); (3) MH sampling parameters (proposal distribution variance, number of iterations beyond the stated 500 burn-in, convergence diagnostics); (4) the exact composition of the training datasets, including the number of positive and negative examples after filtering; (5) the Rosetta FlexPepDock protocol details (number of docking poses generated, scoring function version, any constraints applied); (6) MD simulation parameters beyond those stated (thermostat/barostat algorithms, integration time step, total simulation time per system, equilibration protocol details). The statement that "each peptide–protein complex was solvated" and simulated for 10 ns in triplicate is present, but the total number of systems simulated and the computational cost are not reported.
  - **Why it matters** Reproducibility is a core requirement for computational work in a Nature-family journal. Without complete methodological details, other researchers cannot implement or benchmark the approach. The lack of code availability further compounds this issue. The claims about the superiority of the VAE-MH approach over random search or Rosetta Design cannot be independently verified without access to the exact implementation.
  - **Resolution test** Provide a comprehensive Methods section with all hyperparameters, architecture details, and training procedures. Include a data availability statement and a code availability statement with a link to a public repository. Consider providing a supplementary file with configuration files or a containerized version of the pipeline.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Benchmarking and comparison to existing methods
  - **Claim pointer** The Introduction states that "our method represents the first deep learning-based model for peptide extension" and the Results claim the VAE-MH model outperforms Rosetta Design.
  - **Evidence pointer** Introduction section; Results section "Rosetta FlexPepDock evaluation of N-terminal peptide extensions targeting β-catenin"; Figure 3c
  - **Concern** The claim of being "the first deep learning-based model for peptide extension" is strong and requires a thorough literature search to substantiate. Several deep learning approaches for peptide design have been published, including GANs, VAEs, and transformer-based models. The comparison to Rosetta Design is limited to a single target and a single set of conditions. The manuscript does not compare against other generative models (e.g., conditional VAEs, GANs, or diffusion models) that could potentially perform better. The benchmarking is also asymmetric: the VAE-MH model is fine-tuned with target-specific data, while Rosetta Design is used without such iterative refinement, which may not be a fair comparison.
  - **Why it matters** The novelty and superiority claims are central to the paper's significance. If other deep learning methods have been applied to peptide extension or if the comparison to Rosetta Design is not fair, the contribution is diminished. A rigorous benchmark against state-of-the-art methods is needed to establish the advantage of the proposed approach.
  - **Resolution test** Conduct a comprehensive literature review and either substantiate or soften the "first" claim. Add benchmark comparisons against at least one other generative deep learning method (e.g., a conditional VAE or GAN) on the same targets. Ensure the Rosetta Design comparison is fair by using equivalent iterative refinement or clearly stating the limitations of the comparison.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** MD simulation and MM/GBSA validation
  - **Claim pointer** The Methods state that MM/GBSA is used for binding affinity ranking, and the Results use MM/GBSA scores to select peptides for experimental testing.
  - **Evidence pointer** Methods section "MM/GBSA-binding free energy calculation"; Results sections for β-catenin and NEMO; Tables 1 and 3
  - **Concern** The manuscript does not validate the MM/GBSA approach against known binders or non-binders beyond the limited set of 14 β-catenin peptides in Supplementary Table 1. The correlation between MM/GBSA and experimental IC50 is reported as r² = 0.6, but the number of data points, the range of affinities, and the statistical significance of this correlation are not stated. The MM/GBSA calculations are based on 10 ns MD simulations, which may be too short to achieve converged ensembles for accurate binding free energy estimates. The manuscript does not report convergence tests or error estimates for the MM/GBSA calculations. The choice of the GB model (GB-OBC1) and the internal dielectric constant of 2 are not justified.
  - **Why it matters** The hierarchical selection strategy relies on MM/GBSA as the final computational filter before experimental testing. If the MM/GBSA ranking is not reliable, the selection of peptides for experimental testing could be suboptimal, and the reported experimental successes could be fortuitous. The lack of validation and convergence analysis undermines confidence in the computational ranking.
  - **Resolution test** Provide a more thorough validation of the MM/GBSA approach, including correlation statistics with significance testing, a wider range of known binders/non-binders, and convergence analysis of the MD simulations. Justify the choice of GB model and dielectric constant, or test sensitivity to these parameters. Consider using longer simulations or enhanced sampling methods if convergence is not achieved.

  - **Concern ID** R1-M5
  - **Severity** Major
  - **Blocking** No
  - **Axis** Library screening interpretation
  - **Claim pointer** The Results state that the OBOC library screening "failed to discover any peptides that are more potent than the parent peptide" and that this "demonstrates the power of our combined AI and structure-based design."
  - **Evidence pointer** Results section "N-terminally extended β-catenin-binding peptides from library screening"; Supplementary Tables 5 and 6
  - **Concern** The interpretation of the library screening results is problematic. The library was screened against β-catenin, and 25 hits were selected based on color intensity. However, the manuscript does not report the hit rate, the distribution of binding affinities among the hits, or whether the screening conditions were optimized. The conclusion that the library screening failure demonstrates the power of the computational approach is a negative control argument, but it is not a rigorous comparison. The library screening and the computational design are not directly comparable because they explore different sequence spaces (random vs. VAE-MH generated) and use different selection criteria. The manuscript does not discuss potential reasons for the library screening failure, such as insufficient library diversity, screening conditions, or the inherent limitations of the OBOC approach for this target.
  - **Why it matters** The comparison between library screening and computational design is used to support the value of the computational approach. If the library screening was not well-designed or the comparison is not fair, this conclusion is weakened. A more rigorous comparison would involve screening a library of computationally designed peptides alongside the random library under identical conditions.
  - **Resolution test** Provide more details on the library screening, including hit rates, the range of affinities among hits, and the criteria for selecting the 25 hits. Discuss potential reasons for the library screening failure. Consider designing a control experiment where computationally designed peptides are screened in the same OBOC format to enable a direct comparison.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of figures
  - **Affected element** Figure 1d
  - **Evidence pointer** Figure 1d
  - **Issue** The correlation plots in Figure 1d are described in the text but the figure itself is not provided in the manuscript text. The axes labels and units are not described in the caption.
  - **Required correction** Ensure all figures are included and clearly labeled. Add axis labels and units to Figure 1d. Consider adding a regression line and correlation coefficient to the plots.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Terminology consistency
  - **Affected element** Abstract and Results
  - **Evidence pointer** Abstract; Results sections
  - **Issue** The abstract states "0.010 ± 0.06 μM" for the best IC50, which appears to be a typographical error (likely 0.010 ± 0.006 μM). The Results section for NEMO states "substantially enhanced binding" without defining what constitutes "substantial."
  - **Required correction** Correct the IC50 value in the abstract. Define the threshold for "substantially enhanced" binding in the Results section.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Dataset description
  - **Affected element** Methods, Data preparation
  - **Evidence pointer** Methods section "Data preparation"
  - **Issue** The description of the training dataset is incomplete. The manuscript states that sequences from Uniprot, PixelDB, and THPdb were combined, but does not specify the exact number of sequences from each source, the filtering criteria beyond length, or the balance between positive and negative examples.
  - **Required correction** Provide a detailed breakdown of the dataset composition, including the number of sequences from each source, the filtering criteria, and the class balance.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** MD simulation parameters
  - **Affected element** Methods, MM/GBSA-binding free energy calculation
  - **Evidence pointer** Methods section "MM/GBSA-binding free energy calculation"
  - **Issue** The manuscript states that simulations were run for 10 ns in triplicate but does not report the total number of systems simulated, the computational cost, or the hardware used. The choice of 10 ns is not justified.
  - **Required correction** Report the total number of MD simulations performed, the computational resources used, and justify the simulation length. Consider discussing whether 10 ns is sufficient for convergence.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Results, Experimental validation
  - **Evidence pointer** Tables 1 and 3
  - **Issue** The IC50 values in Tables 1 and 3 are reported with uncertainties, but the number of replicates and the method for calculating the uncertainty are not stated.
  - **Required correction** Specify the number of replicates for each IC50 measurement and the method used to calculate the reported uncertainty (e.g., standard deviation, standard error, 95% confidence interval).

  - **Concern ID** R1-m6
  - **Severity** Minor
  - **Axis** Discussion of limitations
  - **Affected element** Discussion section (not present in the provided text)
  - **Evidence pointer** Not applicable
  - **Issue** The manuscript does not include a Discussion section in the provided text. A discussion of the limitations of the approach, such as the modest improvements, the reliance on computational predictions, and the generalizability to other targets, would strengthen the manuscript.
  - **Required correction** Add a Discussion section that addresses the limitations of the study, the broader applicability of the method, and the implications for future work.

## Risk / unsupported claims
- The claim that this is "the first deep learning-based model for peptide extension" is not substantiated by a comprehensive literature review within the manuscript.
- The claim that the computational approach outperforms random library screening is based on a single comparison that may not be methodologically fair.
- The reported IC50 improvement for CAL-2 (0.010 ± 0.06 μM) contains an apparent error in the uncertainty value, making the claim unreliable as presented.
- The correlation between MM/GBSA scores and experimental IC50 (r² = 0.6) is reported without statistical significance testing or the number of data points.
- The statement that "six of twelve" β-catenin peptides show improved binding is not accompanied by statistical analysis to determine if this is beyond chance.
- The generalizability of the approach to other protein targets is claimed based on only two examples, which is insufficient to establish broad applicability.
- The manuscript claims the VAE-MH model "captures target-specific features" but does not provide analysis of what features are learned or how they relate to binding.
- The effectiveness of the fine-tuning strategy is demonstrated only through aggregate score distributions, not through direct comparison of the same sequences before and after fine-tuning.