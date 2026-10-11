## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, conclusions, experimental section, and figure legends (figures themselves not provided).
- **Assessment boundary** Scientific content, methodological rigor, internal consistency, and alignment of claims with presented evidence. Not assessed: language editing, formatting, or literature completeness beyond what is needed for scientific evaluation.
- **Shared manuscript claim summary** The authors propose that transcriptional condensates containing BRD4 in human HAP1 cells resist coarsening and maintain a stable, exponential size distribution. They attribute this behavior to Active Model B+, a non-equilibrium field theory exhibiting reverse Ostwald ripening, and support this by comparing experimental size distributions to numerical simulations.
- **Visible evidence base** In vitro phase diagram data (Figure 1A–C, Figure S1), in vitro and live-cell FRAP (Figures 1D, 1E, S2), widefield and super-resolution images (Figures 1F, 1G, S3), size distribution histograms (Figure 3A), simulation snapshots (Figure 1H), phase diagram of Active Model B+ (Figure 3B), and representative simulated size distributions (Figure 3C). Statistical methods described in the Experimental Section.
- **Missing materials affecting confidence** Figures themselves are not provided; only legends and in-text descriptions. Raw data, image processing parameters, and full simulation details are not available. The manuscript states data availability upon reasonable request, which limits independent verification.

## Reviewer
- **Overall assessment** The manuscript addresses a significant open question in the biology of transcriptional condensates: the physical mechanism underlying their size stability in cells. The combination of quantitative imaging and a non-equilibrium field theory is timely and potentially impactful. However, the current evidence does not fully establish the central claim that reverse Ostwald ripening, as described by Active Model B+, is the operative mechanism. Key gaps include the lack of direct experimental evidence for the predicted mass transfer direction, the absence of a quantitative link between model parameters and measurable biological quantities, and the reliance on a single cell line and fixation condition for the central size distribution data. The theoretical framework is presented clearly, but its application to the experimental system requires more rigorous justification and falsifiable predictions.
- **Who would be interested in the results, and why** Researchers in the fields of biomolecular condensates, phase separation, transcription regulation, and non-equilibrium soft matter physics. The work bridges quantitative imaging of nuclear architecture with active matter theory, and would appeal to those interested in the physical principles governing intracellular organization. The proposed universality of Active Model B+ for cellular condensates could also attract theorists working on non-equilibrium pattern formation.
- **Major strengths**
  1. The study addresses a fundamental and unresolved problem: why cellular condensates do not coarsen. This is of broad interest.
  2. The combination of in vitro reconstitution, live-cell imaging, super-resolution microscopy, and numerical simulation is a strong multi-pronged approach.
  3. The theoretical framework (Active Model B+) is well-motivated and clearly explained, providing a concrete alternative to equilibrium mechanisms.
  4. The observation that widefield "monolithic" hubs resolve into clusters of smaller droplets is an important experimental finding.
  5. The quantitative comparison between experimental size distributions and simulations, using a similarity metric, is a commendable attempt to make the link quantitative.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence strength for causal mechanism
  - **Claim pointer** The manuscript claims that "the observed exponential size distribution of BRD4 foci quantitatively matches our numerical simulations, suggesting a universal physical picture for the non-equilibrium self-limitation of cellular condensates" and that "condensates reside close to the transition from macrophase to microphase separation for large negative values of the coefficient ζ."
  - **Evidence pointer** Figure 3A, Figure 3B, Figure 3C, Section "Statistics of Foci Sizes"
  - **Concern** The central claim of a quantitative match is not sufficiently supported. The comparison in Figure 3A appears to be a visual overlay of a histogram and a simulated distribution, but no statistical test of the goodness-of-fit is reported. The model parameters (ζ = −4, α = −3) are chosen to maximize similarity, but the manuscript does not report the uncertainty in these parameters, the range of parameters that give acceptable fits, or whether the fitted parameters are physically plausible for a cellular system. More critically, the claim that the system is "close to the transition" is not tested. The phase diagram in Figure 3B shows a region of reverse Ostwald ripening, but the experimental data point (if placed) is not shown. The manuscript does not provide a falsifiable prediction that distinguishes Active Model B+ from alternative mechanisms, such as viscoelastic arrest or surfactant effects, which are mentioned in the introduction but not quantitatively ruled out. The conclusion that the mechanism is "reverse Ostwald ripening" requires direct evidence of mass transfer from larger to smaller droplets, which is not provided.
  - **Why it matters** The core scientific contribution is the identification of a specific physical mechanism. Without a rigorous statistical comparison and a demonstration that the model uniquely explains the data, the conclusion is not established. The manuscript risks overinterpreting a qualitative similarity.
  - **Resolution test** Provide a quantitative goodness-of-fit test (e.g., Kolmogorov-Smirnov) between the experimental and simulated size distributions. Report the best-fit parameters with confidence intervals. Show the location of the experimental system on the phase diagram (Figure 3B). Provide a direct experimental test of the predicted mass transfer direction, for example by tracking individual droplets over time or using fluorescence recovery after photobleaching in a two-droplet configuration. Alternatively, identify a parameter regime where Active Model B+ makes a qualitatively different prediction from equilibrium models and test that prediction.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Internal consistency of experimental observations
  - **Claim pointer** The manuscript states that "in cellulo super-resolution microscopy data reveals that droplets remain stable over hours without coarsening" and that "the observed suppression of coarsening is not due to a kinetic arrest."
  - **Evidence pointer** Figure 1E, Figure 1G, Figure S3, Section "Transcription Condensates In Vitro and In Cellulo"
  - **Concern** The claim that condensates are stable over hours is based on time-lapse imaging (Figure S3), but the super-resolution size distribution (Figure 3A) is obtained from fixed cells. The manuscript does not explicitly state whether the size distribution is stable over time in living cells. If the distribution is measured only at a single time point, the claim of stability is not directly supported by the data presented. Furthermore, the FRAP data (Figure 1E) shows recovery, which is interpreted as evidence against kinetic arrest. However, FRAP recovery can occur even in arrested networks through local exchange, and the manuscript does not provide a quantitative measure of the mobile fraction or recovery half-time in cells. The statement that "we refrain from a quantitative comparison" weakens the evidential value of the FRAP data for ruling out kinetic arrest.
  - **Why it matters** The distinction between a thermodynamically stable microphase-separated state and a kinetically trapped state is central to the argument. If the system is kinetically trapped, the Active Model B+ framework is not the relevant description. The current evidence does not convincingly rule out kinetic trapping.
  - **Resolution test** Provide time-lapse super-resolution data showing that the size distribution is invariant over at least several hours. Report the mobile fraction and recovery half-time for the live-cell FRAP experiments. If possible, perform FRAP experiments on individual droplets of different sizes to test whether the exchange dynamics are consistent with the model predictions.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability of the model
  - **Claim pointer** The manuscript proposes "a universal physical picture for the non-equilibrium self-limitation of cellular condensates."
  - **Evidence pointer** Section "Conclusions"
  - **Concern** The claim of universality is based on a single protein (BRD4) in a single cell line (HAP1). While the authors acknowledge this limitation implicitly, the conclusion is phrased in general terms. The model parameters (ζ, α) are not linked to any measurable biochemical or biophysical properties of BRD4 or its environment. Without such a link, it is unclear how the model could be applied to other condensate systems or how it could be tested in a different context.
  - **Why it matters** The claim of universality is a strong statement that goes beyond the presented evidence. It is important for the field to know whether this is a general principle or a specific property of BRD4 condensates.
  - **Resolution test** Soften the claim of universality, or provide a concrete prediction for another condensate system (e.g., a different protein or a different cell type) that could be tested. Alternatively, provide a mapping between the model parameters and measurable quantities such as phosphorylation rates or binding affinities.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Methodological clarity
  - **Affected element** Size distribution analysis
  - **Evidence pointer** Section "Statistical Analysis"
  - **Issue** The manuscript states that a lower cutoff of 10 pixels is applied to the size distribution, but it does not report the total number of droplets analyzed per nucleus, the variation between nuclei, or the criteria for selecting nuclei for analysis. The number of foci (389 from 22 nuclei) is reported, but the distribution of foci per nucleus is not.
  - **Required correction** Report the number of foci per nucleus, the inter-nuclear variability, and the criteria for including/excluding nuclei. This is important for assessing whether the observed distribution is a population average or representative of individual nuclei.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical detail
  - **Affected element** In vitro phase diagram
  - **Evidence pointer** Figure 1A–C, Section "In Vitro Phase Diagram"
  - **Issue** The in vitro phase diagram is generated using the "inPhase" method, but the manuscript does not report the protein concentration range, the number of replicates, or the error bars on the phase boundaries. The statement that "the coexistence region narrows when going to larger temperatures" is qualitative.
  - **Required correction** Provide the full phase diagram with error bars, the number of replicates, and a quantitative description of the binodal curve.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Model justification
  - **Affected element** Theoretical model
  - **Evidence pointer** Section "Modeling Condensates"
  - **Issue** The model is presented in two dimensions, but the experimental system is three-dimensional. The authors do not discuss whether the 2D model is expected to capture the 3D physics, or whether the comparison between 2D simulations and 2D projections of 3D data is valid.
  - **Required correction** Add a brief discussion of the dimensionality of the model and its potential impact on the comparison with experimental data.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Figure 3A
  - **Evidence pointer** Section "Statistics of Foci Sizes"
  - **Issue** The manuscript states that the experimental distribution is compared to simulations, but it is not clear whether the simulated distribution is scaled to match the experimental data, and if so, how the scaling is performed.
  - **Required correction** Clearly describe the scaling procedure for the simulated distribution and report the scaling factor.
- **Technical failings that need to be addressed before the case is established**
  1. Lack of a statistical test for the match between experimental and simulated size distributions (R1-M1).
  2. No direct evidence for the predicted mass transfer direction (reverse Ostwald ripening) (R1-M1).
  3. The claim of stability over hours is not directly supported by time-resolved super-resolution data (R1-M2).
  4. The live-cell FRAP data is not quantitatively analyzed, weakening the argument against kinetic arrest (R1-M2).
  5. The model parameters are not linked to measurable biological quantities, limiting the testability of the model (R1-M3).
- **Assessment against Nature-style criteria**
  - **Originality** The application of Active Model B+ to transcriptional condensates is novel and represents a creative synthesis of active matter physics and cell biology. The idea that reverse Ostwald ripening could explain size control is original and thought-provoking.
  - **Scientific importance** The question of how cells control the size of condensates is of fundamental importance. If the proposed mechanism is correct, it would have broad implications for our understanding of transcriptional regulation and cellular organization. However, the current evidence is not sufficient to establish the mechanism, and the importance of the claim is therefore not yet realized.
  - **Interdisciplinary readership** The work bridges physics and biology and would appeal to a broad interdisciplinary audience. The theoretical framework is accessible, and the experimental system is biologically relevant. However, the lack of a direct experimental test of the mechanism may limit its appeal to biologists who are not familiar with active matter theory.
  - **Technical soundness** The experimental methods are generally sound, but the analysis is incomplete in several key areas (statistical comparison, time-resolved stability, quantitative FRAP). The theoretical model is well-posed, but its application to the experimental system is not fully justified.
  - **Readability for nonspecialists** The manuscript is clearly written and the concepts are explained well. The introduction and theoretical review are accessible. However, the connection between the model and the experiments could be made more explicit for a general reader.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the experimental approach is appropriate, but the current evidence does not establish the central claim. The authors need to provide a more rigorous quantitative comparison, direct evidence for the mechanism, and a clearer link between the model and the biology. If these concerns are addressed, the manuscript could make a significant contribution.

## Risk / unsupported claims
- The claim of a "quantitative match" between experimental and simulated size distributions is unsupported without a statistical test.
- The claim that condensates "remain stable over hours without coarsening" is not directly supported by time-resolved super-resolution data.
- The claim that the suppression of coarsening is "not due to kinetic arrest" is not quantitatively supported by the FRAP data.
- The claim of a "universal physical picture" is not supported by evidence from a single protein in a single cell line.
- The specific values of the model parameters (ζ = −4, α = −3) are presented as a fit, but the uncertainty and uniqueness of this fit are not reported.
- The statement that "condensates reside close to the transition from macrophase to microphase separation" is not supported by any quantitative analysis of the phase diagram.