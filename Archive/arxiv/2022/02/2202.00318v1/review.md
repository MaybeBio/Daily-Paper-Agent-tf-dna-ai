## Review setup
- **Input scope** Full manuscript text (main text, equations, figure captions referenced, references list)
- **Assessment boundary** Scientific content, mathematical correctness, conceptual novelty, clarity of presentation, and support for claims as presented in the provided material
- **Shared manuscript claim summary** The authors propose a generalized diffusion equation on graphs/networks combining fractional time derivatives with Mellin-transformed d-path Laplacian operators. They derive analytical solutions, characterize normal, sub-, and superdiffusive regimes in one dimension, extend the framework to time-dependent parameter alternation, and apply it to model protein diffusion on DNA as a linear chain.
- **Visible evidence base** Analytical derivations (Sections 3, 3.1, 4), numerical simulations on a path graph with N=1001 nodes (Section 5), figures referenced (Figs. 3.1, 5.1–5.5), and comparison with theoretical scaling predictions
- **Missing materials affecting confidence** Figures themselves are not visible in the provided text; numerical fitting procedures and error estimates are described only qualitatively; no code or data availability statement is provided; the relationship between the model parameters and specific biological mechanisms is asserted rather than derived

## Reviewer

- **Overall assessment** The manuscript presents a mathematically well-structured generalization of diffusion on graphs by combining fractional time derivatives with Mellin-transformed d-path Laplacians. The analytical results, particularly the asymptotic scaling laws and the phase diagram separating normal, sub-, and superdiffusion, are clearly derived and constitute a useful contribution to the field of anomalous diffusion on networks. The application to protein-DNA diffusion is biologically motivated and the numerical results support the main theoretical predictions. However, several technical points require clarification, particularly regarding the interpretation of the superdiffusive regime, the convergence of the asymptotic analysis, and the robustness of the numerical fitting procedure. The biological implications are presented somewhat speculatively and would benefit from more quantitative grounding.

- **Who would be interested in the results, and why** Researchers in statistical physics, complex systems, and network science studying anomalous transport phenomena on discrete structures would find the generalized framework of direct interest. The community working on fractional calculus and its applications to physical systems would also value the analytical treatment. Additionally, biophysicists studying protein-DNA interactions, particularly those using coarse-grained or lattice models of facilitated diffusion, may find the modeling framework relevant, although the connection to experimental observables remains indirect.

- **Major strengths** The mathematical formulation is rigorous and the analytical solution of the generalized diffusion equation is a solid contribution. The asymptotic analysis leading to the phase diagram is elegant and provides clear predictions that are testable in simulations. The extension to time-dependent parameter alternation is conceptually interesting and the numerical results support the claim that alternating regimes can produce distinct global scaling behavior. The manuscript is generally well written and accessible to a broad interdisciplinary audience.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the GDE covers regimes of normal, sub-, and superdiffusion as a function of the two parameters α and s, and that the phase diagram in Fig. 3.1 fully characterizes these regimes.
- **Evidence pointer** Section 3.1, Theorem 6, Fig. 3.1
- **Concern** The derivation of the asymptotic scaling relies on the behavior of the function l_s(k) as k → 0, with the assumption that l_s(k) ∼ c|k|^β. However, the proof that this asymptotic form is sufficient to determine the long-time behavior of the full solution, including the validity of exchanging limits and the uniformity of the approximation, is not fully detailed. Specifically, the transition from the integral representation in Eq. (3.25) to the scaling in Theorem 6 involves a saddle-point or Tauberian argument that is not explicitly justified. The authors should clarify the mathematical conditions under which the asymptotic scaling is rigorous, particularly for the case β = 2 (s > 3) where the boundary between regimes may be sensitive to higher-order terms.
- **Why it matters** The central claim of the paper, namely that the model produces distinct diffusive regimes with precise scaling exponents, rests on this asymptotic analysis. If the approximation is not uniformly valid, the phase diagram could be inaccurate in certain parameter regions, undermining the practical utility of the framework.
- **Resolution test** Provide a more detailed derivation of the asymptotic expansion, including explicit error bounds or a statement of the Tauberian theorem used. Alternatively, verify the predicted scaling exponents numerically over a wider range of α and s values, including near the phase boundaries, and report the agreement or discrepancies.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors state that the alternation of subdiffusive and superdiffusive regimes, as modeled by the time-dependent GDE, offers "important advances" for protein-DNA interactions, specifically that a subdiffusive-superdiffusive alternation allows slower local exploration and faster global exploration compared to a subdiffusive-subdiffusive regime.
- **Evidence pointer** Section 5, Figs. 5.4 and 5.5
- **Concern** The biological interpretation is based on a single set of simulation parameters (α = 0.5 vs. α = 0.9, s₁ = 200, s₂ = 2) and the observed difference in the decay of f_max. However, the claim that this translates to a biological advantage for protein-DNA interactions is not quantitatively supported. The model does not include any target search efficiency metric, binding probabilities, or comparison with known experimental timescales for protein diffusion on DNA. The statement that "slower initial exploration" is advantageous is an assumption that requires justification in the context of target search theory.
- **Why it matters** The biological motivation is a key selling point of the paper. If the connection to protein-DNA interactions is only qualitative and speculative, the broader impact of the work is diminished, and the claim of "important advances" is overstated relative to the evidence provided.
- **Resolution test** Either temper the biological claims to be explicitly speculative, or add a more quantitative analysis, such as computing a search efficiency metric (e.g., mean first-passage time to a target site) for the different regimes and comparing them. If experimental data on protein diffusion on DNA are available, a direct comparison of the model predictions with those data would strengthen the case.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the numerical simulations confirm the theoretical scaling predictions, with fitted exponents γ matching the analytical values.
- **Evidence pointer** Section 5, Figs. 5.2 and 5.3
- **Concern** The fitting procedure is described only briefly: "We then fitted the time evolution of the maximum of the pdf and FWHM to a power law t^γ." No details are given on the fitting range, the number of data points, the statistical uncertainty of the fitted exponents, or how the asymptotic regime was identified. Given that the authors themselves note that "in the superdiffusive regime it is hard to precisely quantify the MSD, since the asymptotic behavior is reached for large times and erratic behaviors can appear in the transient regime," the reliability of the fitted exponents is unclear.
- **Why it matters** The numerical validation is a key component of the paper's evidence. Without a clear description of the fitting methodology and associated uncertainties, the reader cannot assess whether the agreement between theory and simulation is meaningful or coincidental.
- **Resolution test** Provide a detailed description of the fitting procedure, including the time range used, the number of independent runs, and the standard errors on the fitted exponents. If possible, show the fitted curves alongside the data in the figures, and report the residuals or goodness-of-fit statistics.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Section 2, definitions of d-path Laplacian and Mellin-transformed operator
- **Evidence pointer** Section 2, equations (2.1)–(2.4)
- **Issue** The definitions of the d-path Laplacian and the Mellin-transformed operator are presented in a compressed manner, with several equations stated without explicit derivation or intuitive explanation. A reader unfamiliar with the prior work of Estrada on path Laplacians may struggle to understand the physical meaning of the operator and why the Mellin transform is a natural construction.
- **Required correction** Add a brief intuitive explanation of what the d-path Laplacian measures (e.g., how it generalizes the standard graph Laplacian by considering longer-range interactions) and why the Mellin transform is used (e.g., to interpolate between different path lengths). A short paragraph or a remark after the definitions would suffice.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 4.2, periodic temporal alternation
- **Evidence pointer** Section 4.2, equations (4.8)–(4.12)
- **Issue** The proof of the solution for the periodic case is presented as an induction argument, but the base case and the transition from n to n+1 are not fully spelled out. In particular, the continuity conditions at the switching times are stated but the algebra leading to the final expression for f^(n)(t) is not shown.
- **Required correction** Expand the proof to show explicitly how the continuity conditions determine the integration constants, and verify that the expression in Eq. (4.12) satisfies the differential equation in each sub-interval. Alternatively, move the detailed derivation to an appendix and keep the main text concise.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Section 5, biological motivation
- **Evidence pointer** Section 5, Fig. 5.1
- **Issue** The mapping from the biological mechanisms (sliding, hopping, intersegmental transfer) to the model parameters (α and s) is stated but not justified. For example, why does hopping correspond to a specific value of s, and how is the trapping that produces subdiffusion related to α? A reader may accept the mapping as a modeling choice, but a brief justification would improve the credibility of the application.
- **Required correction** Add a short paragraph explaining the biological rationale for the parameter mapping, citing relevant experimental or theoretical work on protein-DNA diffusion where possible.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 3.1, Remark on MSD
- **Evidence pointer** Section 3.1, Remark
- **Issue** The remark states that the MSD diverges for superdiffusive processes due to infinite variance of the step size distribution, citing Levy flight literature. However, the connection between the GDE and Levy flights is not made explicit. It would be helpful to clarify whether the GDE is intended as a deterministic PDE approximation of a stochastic process, and if so, what the underlying stochastic process is.
- **Required correction** Add a brief comment on the relationship between the GDE and stochastic processes, or alternatively, state that the GDE is a phenomenological model and the MSD divergence is a known limitation of such models.

- **Technical failings that need to be addressed before the case is established** R1-M1 (rigor of asymptotic analysis) and R1-M2 (overstated biological claims) are the primary issues. R1-M3 (numerical fitting details) is also important for reproducibility. The minor comments are not blocking but should be addressed for clarity.

- **Assessment against Nature-style criteria**  
  *Originality*: The combination of fractional time derivatives with Mellin-transformed d-path Laplacians is a novel mathematical construction that has not, to my knowledge, been previously proposed. The analytical derivation of the phase diagram is a genuine contribution.  
  *Scientific importance*: The framework is potentially useful for modeling anomalous diffusion on networks, which is a topic of broad interest in physics and biology. However, the biological application is not yet quantitatively validated, and the practical impact beyond the mathematical formulation remains to be demonstrated.  
  *Interdisciplinary readership*: The paper bridges mathematics, physics, and biology, and the writing is generally accessible. However, the biological sections are somewhat speculative, and the mathematical sections may be challenging for nonspecialists without prior exposure to fractional calculus or spectral graph theory.  
  *Technical soundness*: The mathematical derivations appear correct, but the asymptotic analysis requires more rigor, and the numerical validation needs more detail.  
  *Readability for nonspecialists*: The structure is clear, but the introduction could better motivate the need for a generalized diffusion equation on graphs, and the biological application could be better contextualized.

- **Recommendation posture** Supportive if technical concerns are resolved. The core mathematical contribution is solid and the paper addresses a relevant problem. However, the rigor of the asymptotic analysis (R1-M1) and the quantitative support for the biological claims (R1-M2) must be improved before the case is fully established. The numerical fitting details (R1-M3) should also be clarified for reproducibility.

## Risk / unsupported claims
- The claim that the alternation of subdiffusive and superdiffusive regimes provides "important advances" for protein-DNA interactions is not quantitatively supported by the simulations presented.
- The assertion that the model parameters α and s directly correspond to specific biological mechanisms (sliding, hopping, intersegmental transfer) is a modeling assumption without direct empirical justification.
- The statement that the GDE "covers" all three diffusive regimes is supported only for the one-dimensional infinite path graph; the extension to general graphs is not demonstrated.
- The numerical fitting procedure is not described in sufficient detail to assess the reliability of the reported exponents.
- The relationship between the GDE and underlying stochastic processes (e.g., Levy flights) is not clarified, leaving the physical interpretation of the model partially open.