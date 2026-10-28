## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods, results, discussion) without figures or supplementary material
- **Assessment boundary** Scientific claims, methodological soundness, and internal consistency based solely on the provided text; figures and tables are referenced but not directly inspectable
- **Shared manuscript claim summary** The authors use oxDNA2 coarse-grained molecular dynamics simulations to show that negative supercoiling in a 672-bp DNA minicircle promotes the formation of stable denaturation bubbles at AT-rich sequences, that these bubbles co-localize with apical loops, and that synthetic mismatches of ≥5 bp can bias the conformational dynamics of the minicircle by driving loop migration
- **Visible evidence base** Abstract, introduction, materials and methods, results, discussion, acknowledgments, author contributions, declaration of interests; figure and table captions are present but the figures themselves are not available for inspection
- **Missing materials affecting confidence** Figures 1–6, Tables S1–S2, Figures S1–S12, full DNA sequence, simulation parameter details in supporting material, and the experimental benchmark data used for time rescaling

## Reviewer

- **Overall assessment** This manuscript addresses a timely and important question: how sequence and supercoiling jointly govern the structural dynamics of DNA minicircles. The authors employ a well-established coarse-grained model (oxDNA2) and present a systematic exploration across six superhelical densities with multiple replicates. The central observations, namely that AT-rich sequences host stable denaturation bubbles under high negative supercoiling and that these bubbles can pin the conformational dynamics of the minicircle, are potentially significant for understanding DNA-protein interactions and for DNA nanotechnology applications. However, the manuscript as presented has several limitations that prevent full evaluation. The figures and supporting material are not available for inspection, which is critical for assessing the quality of the simulation data and the robustness of the quantitative claims. The time-rescaling procedure, while justified in principle, relies on a single experimental benchmark and a global scaling factor that may not adequately capture the sequence-dependent kinetics of bubble formation and dissolution. The comparison with experimental data from Fogg and co-workers is qualitative and would benefit from a more direct quantitative mapping. The claim that synthetic mismatches can "pin" the dynamics of the minicircle is intriguing but the mechanistic explanation remains somewhat speculative. Overall, the work is promising and likely of interest to the biophysics and DNA nanotechnology communities, but the current evidence base is insufficient to fully establish the central claims.

- **Who would be interested in the results, and why** Researchers studying DNA supercoiling, DNA-protein interactions, and the mechanical properties of DNA would find these results relevant. The demonstration that sequence-dependent bubble formation can bias the global conformation of a DNA minicircle has implications for understanding how supercoiling regulates gene expression and for designing DNA-based nanostructures with controlled mechanical responses. The methodological approach, using oxDNA2 to explore supercoiling-dependent dynamics, will also be of interest to the computational biophysics community. The potential connection to indirect readout mechanisms in DNA-protein recognition broadens the appeal to molecular biologists.

- **Major strengths** The study addresses a question of fundamental biological and nanotechnological importance with a systematic computational approach. The use of multiple replicates and six superhelical densities provides a reasonable sampling of the parameter space. The observation that bubble formation is sequence-dependent and co-localizes with AT-rich regions is consistent with prior experimental work and adds mechanistic detail. The introduction of synthetic mismatches as a tool to manipulate minicircle dynamics is a creative and potentially useful contribution. The manuscript is generally well-written and the logical flow from observation to mechanistic interpretation is clear.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The manuscript claims that denaturation bubbles at AT-rich stretches exhibit extended lifetimes and "pin" the conformational dynamics of the minicircle, particularly at σ = −0.1.
- **Evidence pointer** Results section, Figures 2, 4, 5; location not provided for specific data points
- **Concern** The central claim that bubbles "pin" the dynamics of the minicircle is based on visual inspection of trajectories and qualitative co-localization analysis. The quantitative support, such as the distribution of bubble lifetimes and the statistical significance of the co-localization between bubbles and apical loops, is not presented in the visible text. The scatter plot in Figure 4 is described but the actual data are not available for inspection. Without a rigorous statistical analysis demonstrating that the co-localization is non-random and that the pinning effect is robust across replicates, this claim remains insufficiently supported.
- **Why it matters** The pinning mechanism is the central novel contribution of the paper. If the evidence is only qualitative or based on a limited number of trajectories, the claim is not established. A quantitative analysis with appropriate error bars and statistical tests is essential to convince the reader that the effect is real and not a stochastic fluctuation.
- **Resolution test** Provide a quantitative analysis of the co-localization between bubbles and apical loops, including a null model or permutation test to establish statistical significance. Report the distribution of bubble lifetimes with confidence intervals and demonstrate that the pinning effect is reproducible across all replicates at σ = −0.1.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validity
- **Claim pointer** The manuscript states that a time-rescaling factor of 3000 was applied to the simulation timescales, based on agreement between oxDNA simulations and experimental DNA hybridization rates.
- **Evidence pointer** Results section, "Lifetime of DNA denaturation bubbles"; location not provided
- **Concern** The time-rescaling procedure is described in a single sentence with a reference to a previous study. The validity of applying a global scaling factor of 3000 to all processes in the simulation, including bubble nucleation, growth, and dissolution, is not justified. Bubble dynamics may involve different free-energy barriers than hybridization of short oligonucleotides, and the rescaling may not be uniformly applicable across different sequence contexts or supercoiling regimes. The manuscript does not provide a sensitivity analysis or discuss the uncertainty in this rescaling factor.
- **Why it matters** The quantitative claims about bubble lifetimes (e.g., 20–100 μs) depend entirely on this rescaling. If the rescaling is inaccurate or not universally applicable, the reported lifetimes could be misleading. The comparison with experimental data from Altan-Bonnet and co-workers is used to validate the rescaling, but the agreement may be coincidental if the underlying processes are not equivalent.
- **Resolution test** Provide a more detailed justification for the rescaling factor, including a discussion of its limitations. Perform a sensitivity analysis by varying the rescaling factor and showing that the qualitative conclusions are robust. If possible, compare the simulated bubble dynamics with experimental measurements on the same or similar sequences to validate the rescaling more directly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Completeness of evidence
- **Claim pointer** The manuscript claims that the oxDNA2 force field may misrepresent the behavior of positively supercoiled scenarios, and that the results for σ > 0 require further scrutiny.
- **Evidence pointer** Results section, first subsection; location not provided
- **Concern** The authors acknowledge a potential limitation of the force field for positive supercoiling but do not elaborate on the nature of this limitation or its implications for the interpretation of the σ = +0.06 and σ = +0.1 results. If the force field is unreliable for positive supercoiling, the corresponding data should either be excluded or clearly flagged as preliminary. The current presentation leaves the reader uncertain about the validity of the positive-supercoiling results.
- **Why it matters** The manuscript aims to characterize the impact of supercoiling across a range of densities, including positive values. If the positive-supercoiling data are unreliable, the conclusions about the symmetry or asymmetry between positive and negative supercoiling are weakened. The reader needs to know which results can be trusted and which are suspect.
- **Resolution test** Either provide a detailed analysis of the force-field limitations for positive supercoiling, with supporting evidence, or remove the positive-supercoiling data from the main text and relegate it to the supplementary material with a clear caveat.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The manuscript describes a three-step MD protocol for system preparation and equilibration, but the details of the protocol are not fully specified in the visible text.
- **Evidence pointer** Materials and methods, "System setup and simulation protocol"; location not provided
- **Concern** The description of the simulation protocol is incomplete. The manuscript mentions a "swift relaxation stage" with a modified backbone potential, but does not specify the duration of this stage, the criteria for determining when equilibration is complete, or the parameters of the modified potential. The production run length is stated as 5 × 10^8 MD steps, but the number of independent replicates and the total simulation time per condition are not clearly summarized. The choice of the Bussi thermostat parameters is mentioned but not justified.
- **Why it matters** Reproducibility is a cornerstone of computational research. Without a complete description of the simulation protocol, other researchers cannot replicate the results or assess the quality of the sampling. The lack of detail also makes it difficult to evaluate whether the simulation lengths are sufficient for the processes being studied.
- **Resolution test** Provide a complete description of the simulation protocol, including all parameters, equilibration criteria, and the total simulation time per condition. If the details are in the supporting material, refer to them explicitly and ensure they are accessible.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Equation 2
- **Evidence pointer** Materials and methods, "Structural analysis of the DNA minicircle"
- **Issue** The definition of the local writhe in Equation 2 is not fully explained. The summation limits and the meaning of the indices are not defined, and the relationship between this local measure and the global writhe is not discussed.
- **Required correction** Provide a brief explanation of the notation in Equation 2 and clarify how the local writhe relates to the standard definition of writhe.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1 caption
- **Evidence pointer** Results section, first paragraph
- **Issue** The color bar in Figure 1 is described as being defined upon the value of the unsigned local writhe, but the range of values and the color mapping are not specified.
- **Required correction** Specify the range of the color bar and the color scale used in Figure 1.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Table 1
- **Evidence pointer** Results section, "Bubbles drive the structural dynamics of DNA minicircles"
- **Issue** The table reports average dwelling times and the ratio κ, but the number of replicates and the statistical uncertainty in these values are not reported.
- **Required correction** Add the number of replicates and the standard error or confidence interval for each reported value in Table 1.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion section
- **Evidence pointer** Discussion, first paragraph
- **Issue** The statement that "the release of the excess mechanical stress associated with moderate-to-high levels of negative supercoiling occurs through local strand separation phenomena" is presented as a conclusion, but the causal relationship between supercoiling and strand separation is not explicitly demonstrated in the results.
- **Required correction** Rephrase to indicate that this is an interpretation consistent with the observations, rather than a directly demonstrated mechanism.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Introduction
- **Evidence pointer** Introduction, first paragraph
- **Issue** The introduction cites several experimental studies on DNA supercoiling and denaturation but does not provide a critical comparison of their findings with the present work.
- **Required correction** Add a brief discussion of how the present results compare with or extend previous experimental and computational findings.

## Risk / unsupported claims
- The claim that denaturation bubbles "pin" the conformational dynamics of the minicircle is not quantitatively established from the visible text; the supporting analysis is described qualitatively and the relevant figures are not available for inspection.
- The time-rescaling factor of 3000 is applied without a sensitivity analysis or a detailed justification for its applicability to bubble dynamics across different sequence contexts and supercoiling regimes.
- The statement that the oxDNA2 force field "likely misrepresents" positively supercoiled scenarios is not elaborated, leaving the validity of the positive-supercoiling results uncertain.
- The comparison with experimental data from Fogg and co-workers is qualitative and does not include a direct quantitative mapping between simulated and experimental observables.
- The claim that synthetic mismatches of ≥5 bp can "force the translocation of a target DNA stretch into an apical loop, regardless of the nucleotide sequence" is based on a limited set of simulations and the generality of this claim is not established.