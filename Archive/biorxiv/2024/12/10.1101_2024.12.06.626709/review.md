## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, runtime analysis, limitations, conclusion)
- **Assessment boundary** Scientific validity, technical soundness, reproducibility, and claims as presented in the provided manuscript text. No external data or code was accessed.
- **Shared manuscript claim summary** The authors propose a conditional Denoising Diffusion Probabilistic Model (DDPM) as a surrogate for the pyDNA-EPBD biophysical simulator, generating DNA breathing features from sequence alone. They claim >1000x speedup, high feature fidelity (MSE 0.0025), and comparable transcription factor binding prediction performance when features are integrated into EPBDxDNABERT-2.
- **Visible evidence base** Abstract, Sections 1–8, Figures 1–5 (referenced but not shown), Tables 1–2 (referenced but not shown), no code, no supplementary materials.
- **Missing materials affecting confidence** Figures and tables are referenced but not provided; no dataset description, no hyperparameter details beyond a few values, no baseline model specifications, no statistical significance tests, no code availability statement, no details on EPBDxDNABERT-2 architecture or training.

## Reviewer
- **Overall assessment** The manuscript addresses a genuinely important computational bottleneck in genomics: the prohibitive cost of biophysical DNA breathing simulations. The idea of using a conditional diffusion model as a surrogate is timely and potentially impactful. However, the current manuscript does not provide sufficient evidence to support the central claims. Key figures and tables are missing, the evaluation is incomplete, and several technical details are underspecified. The speedup claims are impressive but the fidelity and downstream utility claims rest on limited and partially contradictory evidence. The manuscript is not yet suitable for publication in a high-impact venue.
- **Who would be interested in the results, and why** Computational biologists, bioinformaticians, and researchers working on regulatory genomics, transcription factor binding prediction, and DNA biophysics. The work is also relevant to the broader machine learning community interested in surrogate modeling and generative models for scientific data. The potential for real-time genome-wide analysis would appeal to those studying gene regulation, disease variants, and therapeutic targets.
- **Major strengths** 1. The problem is well-motivated and practically important. 2. The methodological approach (conditional DDPM) is modern and appropriate for the task. 3. The reported speedup is substantial and could enable new types of analyses. 4. The integration with a downstream prediction model (EPBDxDNABERT-2) is a sensible validation strategy.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "The surrogate model significantly reduces computational time from months to hours–a speedup of over 1000 times" (Abstract) and "reduces computational time from days to hours" (Section 1, contributions).
  - **Evidence pointer** Section 5, Table 2, Figure 5 (not provided)
  - **Concern** The speedup claim is inconsistent between the abstract (>1000x) and the contributions (days to hours). The runtime analysis in Section 5 reports speedups of 172x–208x for batch sizes, and 833x–1663x for large workloads, but the basis for these numbers is unclear. Table 2 and Figure 5 are not provided, so the reader cannot verify the experimental setup, hardware configurations, or whether the comparisons are apples-to-apples (e.g., CPU vs GPU, single node vs multi-node, warm-up times, I/O overhead).
  - **Why it matters** The central value proposition of the surrogate model is its speed. If the speedup is not rigorously quantified and consistently reported, the main contribution is undermined.
  - **Resolution test** Provide the actual runtime data in a table and figure, specify hardware and software configurations for both methods, clarify whether the comparison is end-to-end (including I/O and preprocessing), and reconcile the inconsistent speedup numbers across the abstract, introduction, and results.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "The surrogate-generated features perform comparably to those obtained from the original EPBD framework" (Abstract) and "achieving a low mean squared error (MSE) of 0.0025, which indicates high fidelity" (Section 4.2).
  - **Evidence pointer** Section 4.2, Figure 4 (not provided), Table 1 (not provided)
  - **Concern** The fidelity evaluation is limited to a single MSE value and a qualitative visual comparison in Figure 4, which is not shown. The KS test in Section 4.1 is described but the results are only summarized in Figure 3 (not provided). The claim of "comparable" performance in TF binding prediction is based on AUROC/AUPR values in Table 1 (not provided), but no baselines are described, no confidence intervals are given, and no statistical tests are reported. The authors also acknowledge in Section 6 that the model fails to generate flipping features at 3.53 Å, which is a known limitation but raises questions about the generality of the fidelity claim.
  - **Why it matters** The downstream utility of the surrogate depends on the fidelity of the generated features. Without rigorous quantitative evaluation, including error distributions, per-feature accuracy, and comparison to alternative surrogate methods, the claim of "comparable" performance is not established.
  - **Resolution test** Provide the actual figures and tables. Report per-feature MSE, error distributions, and confidence intervals. Compare against a simpler baseline (e.g., linear interpolation or a variational autoencoder). Report AUROC/AUPR with standard deviations across multiple runs and include a statistical significance test (e.g., DeLong test for AUROC).
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility
  - **Claim pointer** "We trained the surrogate model on a dataset comprising more than a million DNA sequence of length 200 bases and EPBD feature pairs" (Section 3.4).
  - **Evidence pointer** Section 3.4, Section 3.7
  - **Concern** The dataset is described only as "randomly sampled from the human genome." No details are given on the genomic regions sampled, the chromosome distribution, the GC content balance, the number of sequences per chromosome, or the exact EPBD feature dimensions. The training procedure mentions hyperparameters (learning rate, batch size, etc.) but does not provide the actual values used. The code is not made available, and there is no statement about data availability.
  - **Why it matters** Reproducibility is a core requirement for scientific publication. Without detailed dataset and training descriptions, other researchers cannot replicate or build upon this work.
  - **Resolution test** Provide a detailed dataset description (e.g., genomic coordinates, filtering criteria, train/validation/test split sizes), list all hyperparameters, and make the code and trained models publicly available.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific context
  - **Claim pointer** "Our work is distinct in utilizing a conditional DDPM to generate EPBD features, bridging the gap between sequence data and biophysical properties" (Section 2).
  - **Evidence pointer** Section 2
  - **Concern** The related work section is brief and does not adequately position this work against existing surrogate models for biophysical simulations or other generative models for genomic features. No comparison is made to alternative approaches such as variational autoencoders, generative adversarial networks, or normalizing flows, which have been used for similar tasks.
  - **Why it matters** The novelty claim is weakened without a thorough comparison to existing methods. The reader cannot assess whether the diffusion model offers a meaningful advantage over simpler or more established generative approaches.
  - **Resolution test** Expand the related work section to include a systematic comparison with other generative models, and ideally include an empirical comparison in the results.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 3.2, sequence embedder description
  - **Evidence pointer** Section 3.2
  - **Issue** The equations for the embedding and positional encoding are referenced but not explicitly written out. The text says "where PE is defined as" but the formula is not shown.
  - **Required correction** Write out the full equations for the embedding projection and the positional encoding.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Consistency
  - **Affected element** Section 1 vs. Abstract
  - **Evidence pointer** Abstract, Section 1
  - **Issue** The speedup claim is stated as "over 1000 times" in the abstract but "from days to hours" in the introduction. These are not consistent.
  - **Required correction** Use a single, consistent speedup figure throughout the manuscript, or explain the discrepancy (e.g., different workloads).
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section 4.1, KS test description
  - **Evidence pointer** Section 4.1
  - **Issue** The KS test is described as being performed on "1,000 sampled examples" and repeated across "10 independent trials," but it is unclear whether the same 1,000 examples were used across trials or whether new samples were drawn each time.
  - **Required correction** Clarify the sampling procedure for the KS test.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical detail
  - **Affected element** Section 3.3, noise schedule
  - **Evidence pointer** Section 3.3
  - **Issue** The linear noise schedule is described with β values, but the relationship between β and α is not explicitly stated.
  - **Required correction** Define α_t in terms of β_t (e.g., α_t = 1 − β_t) and specify the cumulative product notation.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Presentation
  - **Affected element** Section 5, runtime analysis
  - **Evidence pointer** Section 5
  - **Issue** The runtime analysis mixes CPU and GPU comparisons without clearly stating whether the same batch sizes and sequence lengths were used for both methods. The text also jumps between different speedup numbers (172x, 208x, 833x, 1663x) without a clear summary.
  - **Required correction** Present a single, clear table with all runtime measurements and speedup calculations, and specify the exact hardware and software configurations for each row.
- **Technical failings that need to be addressed before the case is established** R1-M1 (inconsistent and unverifiable speedup claims), R1-M2 (insufficient fidelity and downstream evaluation), R1-M3 (lack of reproducibility details). These are blocking because the core claims of the manuscript cannot be assessed without addressing them.
- **Assessment against Nature-style criteria**  
  *Originality*: The application of a conditional diffusion model as a surrogate for biophysical DNA simulations is a novel combination, though the individual components (diffusion models, transformer-based sequence encoders) are established. The originality is moderate and would be strengthened by a clearer demonstration of why diffusion is superior to other generative approaches for this task.  
  *Scientific importance*: The problem is important. If the surrogate works as claimed, it would enable genome-wide analyses that are currently infeasible. However, the importance is contingent on the validity of the fidelity and speed claims, which are not yet established.  
  *Interdisciplinary readership*: The work bridges machine learning, biophysics, and genomics, which is appealing. However, the manuscript assumes familiarity with both diffusion models and DNA biophysics, and may not be accessible to a broad audience without additional background.  
  *Technical soundness*: The methodology is plausible but under-specified. The evaluation is incomplete, and the acknowledged failure at 3.53 Å raises concerns about the model's robustness. The lack of statistical rigor in the downstream evaluation is a significant weakness.  
  *Readability for nonspecialists*: The abstract is clear, but the methods section is dense and assumes prior knowledge. The manuscript would benefit from a more explicit explanation of what EPBD features represent and why they matter for TF binding.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, but the missing figures and tables, inconsistent speedup claims, and incomplete evaluation prevent a positive recommendation. I would be supportive if the authors provide the missing data, address the technical concerns, and strengthen the evaluation.

## Risk / unsupported claims
- The claim of "over 1000 times" speedup is not supported by the data presented in the text (which reports 172x–208x for batch sizes and 833x–1663x for large workloads, with no clear methodology).
- The claim of "comparable" TF binding prediction performance is not supported without baseline comparisons, confidence intervals, or statistical tests.
- The claim that the surrogate generates "high-fidelity" features is only partially supported by a single MSE value and a visual comparison (Figure 4 not provided). The acknowledged failure at 3.53 Å is not reconciled with this claim.
- The KS test results are described but not shown (Figure 3 not provided), making the statistical claim unverifiable.
- The dataset description ("more than a million sequences") is insufficient for reproducibility; no details on sampling strategy or feature dimensions are given.