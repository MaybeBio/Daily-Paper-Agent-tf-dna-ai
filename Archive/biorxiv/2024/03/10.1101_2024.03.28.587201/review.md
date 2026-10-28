## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and support of claims based solely on the supplied text
- **Shared manuscript claim summary** The authors present a coarse-grained Monte Carlo model of DNA-protein interactions with an isotropic binding potential and imposed valency, combined with an unsupervised machine learning pipeline (PCA + Gaussian mixture model) to classify DNA-protein complex conformations. They apply this to HIV integrase-mediated DNA compaction and claim that protein-protein attractions are critical for forming looped "rosette" intermediates observed experimentally, and that stronger attractions and longer DNA promote compaction at lower protein concentrations.
- **Visible evidence base** Abstract, Introduction, Methods (coarse-grained DNA model, protein model, semi-grand canonical simulation details), Results and Discussion (machine learning classification, two compaction pathways, rate analysis), Conclusion, Acknowledgments, one footnote
- **Missing materials affecting confidence** Figures (Figs. 2-6) referenced but not provided; Supplemental Material referenced but not provided; experimental data from Ref. (39) not independently accessible; no quantitative comparison metrics between simulation and experiment; no error bars or statistical significance tests reported; no code or data availability statement

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful coarse-grained modeling framework and a novel application of unsupervised learning to classify DNA-protein complex conformations. The methodological approach is clearly described and the authors make a reasonable effort to connect simulation parameters to experimental measurements. However, the central claim that protein-protein interactions are "critical" for rosette formation rests on qualitative visual comparisons to experiments that are not shown in the provided material. The rate analysis and master curve collapse are suggestive but lack rigorous statistical treatment. The manuscript would benefit from quantitative validation against experimental observables and a clearer demonstration that the machine learning classification is robust and not an artifact of the chosen parameters.
- **Who would be interested in the results, and why** Researchers in biophysics, computational biology, and soft matter physics studying DNA-protein interactions, chromatin organization, and viral genome packaging. The coarse-grained model and unsupervised classification pipeline could be of interest to those developing simulation tools for mesoscale biomolecular complexes. Experimentalists studying DNA compaction by proteins (e.g., HIV integrase, SMC complexes) may find the predicted pathways and phase behavior useful for interpreting their data.
- **Major strengths** 1) The coarse-grained model is simple and generic, avoiding assumptions about binding geometry that are often poorly constrained. 2) The use of experimental binding strengths to parameterize the model is a commendable effort to connect simulation to experiment. 3) The unsupervised machine learning pipeline provides a systematic, quantitative method for classifying complex conformational ensembles, which is a genuine methodological contribution. 4) The identification of two distinct compaction pathways (bridging vs. rosette) depending on protein-protein interactions is a clear and testable prediction.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative validation), R1-M2 (statistical rigor), R1-M3 (classification robustness), R1-M4 (rate analysis assumptions)
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. Coarse-grained models of DNA-protein interactions exist, and unsupervised learning has been applied to biomolecular conformations, but the specific combination and the focus on valency-limited isotropic binding with a classification pipeline is somewhat novel.  
  *Scientific importance*: Moderate. The work addresses a biologically relevant question (how proteins compact DNA) and provides a framework that could be broadly applicable, but the specific findings are not yet demonstrated to be general or quantitatively predictive.  
  *Interdisciplinary readership*: Moderate. The topic bridges biophysics, computational biology, and virology, but the presentation is heavily simulation-focused and may not be immediately accessible to experimental biologists without additional context.  
  *Technical soundness*: The simulation methodology is standard and appears sound, but the analysis and validation have gaps as detailed in the concerns.  
  *Readability for nonspecialists*: The abstract and introduction are clear, but the methods and results sections assume familiarity with coarse-grained simulations, PCA, and GMM. The significance statement helps, but the manuscript could benefit from more explicit explanations of key concepts.
- **Recommendation posture** Supportive if technical concerns are resolved. The framework is promising and the qualitative findings are interesting, but the central claims require quantitative validation and more rigorous statistical analysis before the case is fully established.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "We find that protein-protein interactions are critical to the formation of looped intermediate structures seen experimentally" (Abstract, Introduction, Conclusion)  
- **Evidence pointer** Results and Discussion, Figs. 3-5 (not provided); experimental comparison to Ref. (39)  
- **Concern** The central claim that protein-protein interactions are "critical" for rosette formation is supported only by qualitative visual comparison of simulation snapshots to experimental observations from Ref. (39). No quantitative metrics (e.g., loop size distribution, rosette frequency, compaction ratio) are provided to demonstrate agreement between simulation and experiment. The figures that would show this comparison are not included in the provided material.  
- **Why it matters** Without quantitative validation, the claim of "critical" importance cannot be distinguished from a qualitative coincidence. The authors assert agreement with experiments, but the reader cannot assess the degree of agreement or whether the model captures the essential physics or merely produces visually similar structures.  
- **Resolution test** Provide quantitative comparison between simulated and experimental observables (e.g., distribution of DNA loop lengths, number of rosettes per DNA molecule, compaction kinetics) with appropriate statistical measures. If such data are not available, temper the claim to "consistent with" rather than "critical."

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical rigor  
- **Claim pointer** "We find that protein-protein attractions promote DNA compaction; Fig. 3 C,D clearly shows that DNA compaction in systems with 2 k B T protein-protein attraction sets in at lower protein concentrations than in systems without protein-protein attraction" (Results and Discussion)  
- **Evidence pointer** Results and Discussion, Figs. 3, 5, 6 (not provided)  
- **Concern** The manuscript reports results from 10-12 independent simulations per condition but provides no error bars, confidence intervals, or statistical tests for the compaction rates or the onset concentrations. The "typical trajectory" selection criterion is described but the variability across simulations is not quantified. The master curve collapse in Fig. 6 is presented without a measure of goodness of fit or uncertainty in the fitted parameters.  
- **Why it matters** The conclusions about the effect of protein-protein attraction strength and DNA length on compaction depend on distinguishing real differences from stochastic variation. Without statistical rigor, the reader cannot assess whether the observed trends are robust or could arise from sampling noise.  
- **Resolution test** Report mean and standard deviation (or standard error) for compaction rates and onset concentrations across the 10-12 simulations. Perform appropriate statistical tests (e.g., bootstrap, hypothesis testing) to support claims of differences between conditions. Provide confidence intervals for fitted parameters in the rate law.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** Methodological robustness  
- **Claim pointer** "We find that, in our case, the Gaussian mixture model (GMM) provides a satisfactory distinction of the different groups in the PC landscape" and "the optimum number of groups is seven" (Results and Discussion)  
- **Evidence pointer** Results and Discussion, Fig. 2 (not provided), Supplemental Material (not provided)  
- **Concern** The choice of seven clusters is justified by BIC and clustering entropy, but the sensitivity of the classification to the number of clusters, the choice of order parameters, and the PCA dimensionality reduction is not systematically explored. The authors note that some order parameters are redundant but do not test whether removing them changes the classification. The stability of the clusters across different random seeds or initialization conditions for the GMM is not reported.  
- **Why it matters** The classification underpins the identification of distinct conformational states and the compaction pathways. If the clustering is sensitive to arbitrary choices, the reported pathways may not be robust. The authors claim the method is "systematic and quantitative," but this requires demonstrating that the results are not artifacts of the specific implementation.  
- **Resolution test** Perform a sensitivity analysis: vary the number of clusters around the BIC optimum, remove correlated order parameters, and test different random seeds for the GMM. Report the stability of cluster assignments and the resulting pathway classifications.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Model assumptions  
- **Claim pointer** "Assuming that the start of compaction in our simulations is a rare event which has a censored exponential distribution... we can approximate the rate λ" (Results and Discussion)  
- **Evidence pointer** Results and Discussion, Eq. 3, Fig. 6 (not provided)  
- **Concern** The assumption of a censored exponential distribution for the onset of compaction is stated but not justified. The authors do not test whether the waiting times to compaction are indeed exponentially distributed, nor do they discuss alternative models (e.g., Weibull, gamma distributions) that might fit the data better. The rate law in Eq. 4 is presented as a fit to the master curve, but the functional form is not derived from a mechanistic model.  
- **Why it matters** The rate law and the master curve collapse are used to make quantitative claims about how compaction depends on protein concentration and DNA length. If the underlying distributional assumption is incorrect, the extracted rates and the fitted parameters may be biased, undermining the quantitative conclusions.  
- **Resolution test** Perform goodness-of-fit tests for the exponential assumption (e.g., Kaplan-Meier survival analysis, Q-Q plots). Compare fits with alternative distributions. Justify the functional form of the rate law from a mechanistic model or provide empirical evidence that it captures the data.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Methods, coarse-grained DNA model  
- **Evidence pointer** Methods section, "Coarse-grained model for DNA"  
- **Issue** The equations for the FENE spring potential, WCA potential, and bending potential are referenced but not explicitly written out in the provided text. The parameters (e.g., k, r0, epsilon, k_theta) are given in text but the functional forms are missing.  
- **Required correction** Include the explicit functional forms of the potentials in the main text or clearly reference the Supplemental Material where they are defined.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Methods, semi-grand canonical simulations  
- **Evidence pointer** Methods section, "Semi-grand canonical simulations to model DNA-protein mixtures"  
- **Issue** The details of the grand-canonical insertion and removal moves (e.g., acceptance criteria, chemical potential calculation, how the reservoir concentration is mapped to the simulation) are not fully described. The restriction of insertion/deletion to a spherical volume is mentioned but the rationale and the choice of padding (5 r_c) are not justified.  
- **Required correction** Provide a more detailed description of the grand-canonical scheme, including how the chemical potential is related to the protein concentration, and justify the choice of the insertion/deletion volume.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** Results and Discussion, two pathways  
- **Evidence pointer** Results and Discussion, "Two pathways for the protein-mediated compaction of DNA"  
- **Issue** The authors state that the two pathways are "completely separate" and that there is "no pathway between the bridging and rosette states." This is a strong claim based on finite simulation time. It is possible that transitions between these states occur on timescales longer than the simulation window.  
- **Required correction** Soften the claim to "no pathway observed within the simulation timescales" or provide evidence (e.g., very long simulations, free energy calculations) that the states are kinetically separated.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Presentation  
- **Affected element** Abstract and Significance  
- **Evidence pointer** Abstract, Significance statement  
- **Issue** The abstract and significance statement emphasize the application to HIV integrase, but the model is claimed to be "broadly applicable." The generalizability is not demonstrated beyond this one system.  
- **Required correction** Either provide a brief discussion of how the model could be extended to other systems or temper the claim of broad applicability.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Methods, protein model  
- **Evidence pointer** Methods section, "Coarse-grained model for proteins"  
- **Issue** The protein is modeled as a sphere with an isotropic binding potential and valency restriction, but the physical interpretation of the valency (e.g., number of DNA binding sites) and how it relates to the actual HIV integrase tetramer is not discussed.  
- **Required correction** Add a brief explanation of how the valency parameter maps to the biological system and whether the model captures known features of integrase-DNA binding.

## Risk / unsupported claims
- The claim that protein-protein interactions are "critical" for rosette formation is not quantitatively validated against experimental data (R1-M1).
- The claim that the two compaction pathways are "completely separate" is unsupported by the provided evidence (R1-m3).
- The claim that the model is "broadly applicable" to DNA-binding proteins is not demonstrated (R1-m4).
- The rate law in Eq. 4 and the master curve collapse are presented without statistical justification or goodness-of-fit measures (R1-M2, R1-M4).
- The statement that the machine learning classification is "systematic and quantitative" is not supported by a sensitivity analysis (R1-M3).
- The assertion that the simulated complexes "are in good agreement with experimental observations" (Significance) is not backed by quantitative comparison metrics in the provided material.