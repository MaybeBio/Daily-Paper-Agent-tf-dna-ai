## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods) from bioRxiv preprint
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text; no external data or supplementary files were available for verification
- **Shared manuscript claim summary** The authors use MS2-MCP live imaging and mathematical modeling to show that mutating individual Dorsal or Twist binding sites in the snail distal enhancer reduces transcriptional output primarily by lowering transcriptional amplitude and increasing promoter off-rate (k_off), with implications for synergistic TF interactions and spatiotemporal gene control in early Drosophila embryos
- **Visible evidence base** Text descriptions of results, figure references (Figures 1-4, supplements), methods descriptions, statistical annotations (p<0.001)
- **Missing materials affecting confidence** Actual figures, supplementary videos, raw data, numerical values, statistical test details, model parameters, and code were not provided; only textual descriptions are available

## Reviewer
- **Overall assessment** The manuscript addresses a significant question in developmental gene regulation: how multiple weak TF binding sites within an enhancer collectively control transcriptional dynamics. The combination of live imaging and stochastic modeling is appropriate and timely. However, the current text lacks sufficient quantitative detail and figure inspection to fully evaluate the robustness of the claims. The central conclusion that single binding site mutations reduce mRNA production primarily via reduced amplitude and increased k_off is plausible but not fully verifiable from the provided material. The synergy claim rests on a modeling framework whose parameter constraints are only partially described.
- **Who would be interested in the results, and why** Researchers in developmental biology, transcriptional regulation, enhancer biology, and quantitative imaging. The work bridges biophysical modeling and in vivo imaging, which will appeal to those studying transcriptional bursting, morphogen gradients, and enhancer logic. The finding that weak binding sites cooperate synergistically has implications for understanding enhancer evolution and disease-associated mutations.
- **Major strengths** 1) Use of quantitative live imaging to dissect transcriptional dynamics at single-nucleus resolution in a developing embryo. 2) Systematic mutagenesis of individual TF binding sites within a defined enhancer. 3) Integration of thermodynamic and stochastic models to interpret experimental data. 4) Comparison between minimal and full enhancer contexts addresses the question of buffering by additional binding sites.
- **Major Concerns** 
  - R1-M1: The claim that mutations reduce mRNA production "mainly" via reduced transcriptional amplitude is based on comparisons of mean values, but no effect sizes, confidence intervals, or statistical test details are provided. The text states "significant decrease" with p<0.001, but the magnitude of the amplitude reduction relative to other parameters (e.g., duration, activation probability) is not quantified.
  - R1-M2: The thermodynamic model's ability to "reveal synergistic interactions" depends on parameter choices (dissociation constants, cooperativity terms) that are only briefly described. The text states that the model "failed" without cooperativity, but the failure criteria and the uniqueness of the fitted cooperativity values are not established. The risk of overfitting with multiple free parameters is not addressed.
  - R1-M3: The two-state model inference of k_on and k_off relies on a binary classification of promoter states from fluorescence trajectories (positive vs. negative slope). This method is simplistic and may be sensitive to noise; no validation against simulated data or alternative inference methods is presented.
  - R1-M4: The claim that "additional TF binding sites in the full distal enhancer" do not rescue the mutant phenotype is based on a comparison between minimal and full enhancer contexts, but the text does not specify whether the same binding sites were mutated in both contexts or whether the full enhancer contains additional Dl/Twi sites with different affinities that might compensate differently.
- **Minor Comments** 
  - R1-m1: The abstract states "a mutation in any one of these binding sites causes a drastic reduction in transcriptional amplitude," but the results section notes that the Dl1 mutation also causes earlier activation. The abstract should acknowledge this nuance.
  - R1-m2: The term "transcriptional amplitude" is used interchangeably with "Pol II loading rate" in the results; clarify whether these are operationally identical in the MS2 assay.
  - R1-m3: The methods state that "all images were taken using a Zeiss LSM800 confocal laser scanning microscope" but do not specify laser power, gain, or pinhole settings, which are critical for quantitative comparisons across embryos.
  - R1-m4: The text mentions "Figure 1 supplement 1A" and other supplements, but these are not described in the main text; a brief description of what each supplement shows would aid readability.
  - R1-m5: The discussion of "sub-optimal binding sites" would benefit from a quantitative definition of "weak" affinity (e.g., range of K_d values used in the model).
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** 
  - Originality: Moderate to high. The application of live imaging to systematically perturb TF binding sites in a developmental enhancer is not entirely novel, but the combination with stochastic modeling to extract kinetic parameters is a valuable contribution.
  - Scientific importance: High. Understanding how enhancer architecture encodes transcriptional dynamics is fundamental to developmental biology and human genetics.
  - Interdisciplinary readership: Moderate. The work bridges molecular biology and biophysics, but the presentation assumes familiarity with both live imaging and stochastic modeling; a broader audience may struggle with the model details.
  - Technical soundness: Currently not fully assessable. The experimental approach is sound in principle, but the lack of quantitative detail and figure inspection prevents verification of the statistical and modeling claims.
  - Readability for nonspecialists: Adequate but improvable. The abstract and introduction are clear, but the results section relies heavily on figure references without sufficient textual explanation of the data.
- **Recommendation posture** Supportive if technical concerns are resolved. The core question is important and the approach is promising, but the current manuscript does not provide enough quantitative evidence to fully establish the claims. The authors should provide effect sizes, model validation, and clearer descriptions of the statistical and modeling methods.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative evidence
- **Claim pointer** "The main cause of the low mRNA output was the average transcriptional amplitude" and "a mutation in any one of these binding sites causes a drastic reduction in transcriptional amplitude"
- **Evidence pointer** Results section, Figure 2E, Figure 2 supplement 1C
- **Concern** The text reports significant reductions in amplitude but does not provide effect sizes, confidence intervals, or the proportion of total mRNA reduction attributable to amplitude versus other parameters (e.g., duration, activation probability). Without these, the claim that amplitude is the "main" cause is not quantitatively supported.
- **Why it matters** The central mechanistic conclusion depends on attributing the observed mRNA reduction to specific kinetic parameters. If duration or activation probability contribute substantially, the interpretation changes.
- **Resolution test** Provide mean ± SEM for each parameter (amplitude, duration, activation time, probability) for wildtype and each mutant, along with a decomposition of total mRNA reduction into contributions from each parameter (e.g., via a simple calculation or sensitivity analysis).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Modeling validity
- **Claim pointer** "A thermodynamic Monod-Wyman-Changeux (MWC) model... reveal synergistic interactions among TF binding sites" and "the model failed to predict the experimental data" without cooperativity
- **Evidence pointer** Results section, Figure 3B-C, Methods "Equilibrium binding model"
- **Concern** The model fitting procedure is described only briefly. The number of free parameters (cooperativity terms for each pair/triplet of sites) is not stated, nor is the identifiability of these parameters addressed. The "failure" without cooperativity is not quantified (e.g., what was the error?).
- **Why it matters** The synergy claim is a key conceptual advance. If the model is overparameterized or the fit is non-unique, the conclusion that specific cooperative interactions are required is not robust.
- **Resolution test** Report the number of fitted parameters, the objective function values for models with and without cooperativity, and perform a parameter identifiability analysis (e.g., profile likelihood or bootstrap). Show that the fitted cooperativity values are stable across initial guesses.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** "We utilize an HMM to infer the promoter state based on the observed fluorescence intensity curves" and "k_off is significantly increased in mutants"
- **Evidence pointer** Results section, Figure 4C-H, Methods "Two-state model"
- **Concern** The binary classification of promoter states based on the sign of the slope between consecutive time points is a crude heuristic. Fluorescence trajectories are noisy, and this method may misclassify short-lived ON/OFF events. No validation against simulated trajectories or comparison with more sophisticated inference methods is provided.
- **Why it matters** The k_off increase is a central finding. If the state classification is biased, the inferred kinetic rates may be inaccurate, undermining the conclusion.
- **Resolution test** Validate the HMM approach on simulated trajectories with known parameters, report classification accuracy, and compare with an alternative method (e.g., a continuous-state model or a different thresholding approach).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design
- **Claim pointer** "Despite several additional Dl and Twist sites flanking the minimal enhancer, we found that the same mutations on the same TF motifs caused a similar decrease in mRNA production"
- **Evidence pointer** Results section, Figure 1I-J
- **Concern** The text does not specify whether the mutations in the full enhancer context were introduced at the same positions as in the minimal enhancer, or whether the full enhancer contains additional Dl/Twi sites that might partially compensate. The comparison is therefore difficult to interpret.
- **Why it matters** The claim that additional sites do not buffer the effect is important for the synergy argument. If the full enhancer has additional sites with different affinities, the lack of rescue could be due to the specific mutation location rather than a general property of the enhancer.
- **Resolution test** Clearly state the mutation positions in both contexts, and ideally test mutations at multiple sites in the full enhancer to confirm that the lack of buffering is general.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, Results section
- **Issue** The abstract states that mutations cause "a drastic reduction in transcriptional amplitude," but the results note that the Dl1 mutation also causes earlier activation. This nuance is not reflected in the abstract.
- **Required correction** Modify the abstract to acknowledge that amplitude reduction is the primary but not sole effect, or state that activation timing is also affected for specific mutations.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results section
- **Evidence pointer** Results section, Figure 2E
- **Issue** "Transcriptional amplitude" and "Pol II loading rate" are used interchangeably, but it is unclear if these are operationally identical in the MS2 assay.
- **Required correction** Define both terms explicitly and state whether they are measured identically or derived from the same data.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods "Live imaging"
- **Evidence pointer** Methods section
- **Issue** Imaging settings (laser power, gain, pinhole) are not specified, which is critical for quantitative comparisons across embryos.
- **Required correction** Provide full imaging parameters or cite a previous publication with the same settings.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Results section
- **Evidence pointer** Results section, Figure supplements
- **Issue** Supplementary figures are referenced but not described in the main text, making it difficult for readers to understand what each shows.
- **Required correction** Add brief descriptions of each supplementary figure in the main text or figure legends.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Quantitative definition
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The term "weak" or "sub-optimal" binding sites is used without a quantitative definition.
- **Required correction** Provide the range of dissociation constants used in the model to define "weak" affinity.

## Risk / unsupported claims
- The claim that "each site in the minimal enhancer is necessary to drive normal sna expression" is based on single and double mutations, but the text does not report whether all possible single mutations were tested or only a subset.
- The statement that "additional TF binding sites in the full enhancer are not sufficient to rescue reduced transcriptional activity" is not fully supported without specifying the mutation positions and the affinities of the flanking sites.
- The claim that "TF-DNA binding regulates spatial and temporal gene expression... by modulating transcriptional kinetics and tuning bursting rates" is a reasonable interpretation but is not directly tested; the authors do not manipulate k_off independently of the mutations.
- The model-based claim of "synergistic interactions" is not verifiable from the text alone, as the fitting procedure and parameter values are not fully described.