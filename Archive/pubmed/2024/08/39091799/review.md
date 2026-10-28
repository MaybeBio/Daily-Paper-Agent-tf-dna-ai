## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, data availability)
- **Assessment boundary** Scientific validity, technical soundness, and significance of the claims as presented in the provided manuscript text. No assessment of supplementary figures, tables, or data files beyond what is referenced in the text.
- **Shared manuscript claim summary** The authors present PepPrCLIP, a sequence-based pipeline combining Gaussian perturbation of ESM-2 peptide embeddings with a CLIP-style contrastive discriminator, to design de novo linear peptide binders for conformationally diverse protein targets. They report in silico benchmarking against RFDiffusion on structured targets and experimental validation of peptide-mediated inhibition of UltraID, degradation of β-catenin, and degradation of the SS18-SSX1 fusion oncoprotein.
- **Visible evidence base** Main text figures (Figures 1A-C, 2A-C, 3A-C, 4A-E, 5A-C), methods section, and references to supplementary materials (Supplementary Figures 1-4, Supplementary Tables 1-3, Supplementary Data)
- **Missing materials affecting confidence** Supplementary figures, tables, and data files are referenced but not provided. Experimental details for the UltraID inhibition assay, β-catenin degradation, and SS18-SSX1 experiments are only partially described in the methods. No structural validation data (e.g., co-crystal structures) is presented. The full peptide sequences and detailed statistical outputs are not visible in the provided text.

## Reviewer

### Overall assessment
The manuscript describes a conceptually interesting approach that combines protein language model embeddings with contrastive learning for peptide binder design. The core idea of using Gaussian perturbation in ESM-2 latent space to generate candidate peptides, followed by CLIP-based prioritization, is a reasonable and potentially useful contribution to the field of sequence-based binder design. The authors demonstrate that their pipeline can generate peptides that inhibit UltraID activity, degrade β-catenin, and degrade the SS18-SSX1 fusion oncoprotein in cellular assays. However, several technical concerns limit the strength of the conclusions as currently presented. The in silico benchmarking against RFDiffusion is described with a non-standard hit-rate metric that may not be directly comparable. The experimental validation, while promising, lacks key controls and quantitative details that would establish the specificity and mechanism of the designed peptides. The claim of a "CRISPR-like" programmable system is an overstatement given the limited number of targets tested and the lack of demonstrated generality. The manuscript would benefit from clearer presentation of the experimental data, additional controls, and a more measured interpretation of the results.

### Who would be interested in the results, and why
Researchers in the fields of protein design, targeted protein degradation, and chemical biology would find this work of interest. The approach of using language model embeddings for peptide generation is timely and could be adopted by groups working on binder design for challenging targets. The demonstration of peptide-mediated degradation of a fusion oncoprotein is particularly relevant to the targeted protein degradation community. The work may also appeal to computational biologists interested in contrastive learning applications in biology.

### Major strengths
1. The conceptual novelty of combining a generative step (Gaussian perturbation in ESM-2 space) with a discriminative step (CLIP-style contrastive learning) for peptide design is a genuine contribution.
2. The pipeline is purely sequence-based, which addresses a real limitation of structure-based methods for disordered or conformationally diverse targets.
3. The experimental validation across three different targets (an enzyme, a transcription factor, and a fusion oncoprotein) demonstrates the potential breadth of the approach.
4. The comparison with RFDiffusion, a state-of-the-art structure-based method, provides a useful benchmark even if the metric is non-standard.
5. The writing is generally clear and the figures are well-referenced in the text.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of the in silico benchmarking
- **Claim pointer** "PepPrCLIP performs comparably to RFDiffusion on structured targets in silico" (Results section, Figure 2B-C)
- **Evidence pointer** Results section, Figure 2B-C, Methods section "AlphaFold-Multimer benchmarking"
- **Concern** The hit-rate metric is defined as the percentage of generated peptides with an ipTM score ≥ that of the corresponding test set peptide. This is a non-standard and potentially misleading metric. The test set peptides are experimentally validated binders, and the ipTM threshold is relative to each individual test peptide. This makes the comparison between PepPrCLIP and RFDiffusion difficult to interpret, as the two methods are not evaluated against the same absolute threshold. Furthermore, the text states that RFDiffusion "performs strongly as expected" with a 30.1% hit-rate, but this is presented without a clear explanation of why this is expected or what a good hit-rate would be.
- **Why it matters** The in silico benchmarking is a key part of the paper's claim that PepPrCLIP is competitive with state-of-the-art structure-based methods. If the metric is not well-defined or is biased, the comparison is not meaningful. The reader cannot assess whether the 17.7% hit-rate for PepPrCLIP is actually good or poor without a more standard evaluation.
- **Resolution test** The authors should provide a more standard evaluation, such as the fraction of generated peptides with ipTM ≥ 0.7 (which is mentioned but not fully reported), or a direct comparison of ipTM distributions between PepPrCLIP and RFDiffusion on the same set of targets. They should also report the absolute ipTM values for the test set peptides to provide context for the hit-rate metric.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation and controls
- **Claim pointer** "PepPrCLIP-generated peptides inhibit the catalytic activity of UltraID" and "PepPrCLIP-generated ubiquibodies robustly bind and functionally degrade β-catenin" and "PepPrCLIP-generated uAbs robustly degrade the highly-disordered fusion oncoprotein SS18-SSX1" (Results sections, Figures 3-5)
- **Evidence pointer** Results sections, Figures 3-5, Methods sections "UltraID inhibition assay", "TOPFlash assay", "Flow cytometry analysis", "Cell fractionation and immunoblotting"
- **Concern** The experimental validation lacks critical controls. For the UltraID inhibition assay, it is unclear whether the observed inhibition is specific to the designed peptides or could be due to non-specific effects of overexpressing any peptide-fused protein. For the β-catenin degradation experiments, the text mentions a polyalanine peptide control for SS18-SSX1, but it is not clear if similar controls were used for the UltraID and β-catenin experiments. The specificity of the designed peptides for their intended targets is not demonstrated. Additionally, the quantification of degradation (e.g., ">50%" for β-catenin) is mentioned but the statistical analysis and the number of independent experiments are not fully described in the visible text.
- **Why it matters** The central claim of the paper is that PepPrCLIP can design specific, functional peptide binders. Without appropriate negative controls (e.g., scrambled peptides, peptides designed against unrelated targets) and clear demonstration of target specificity, the results could be explained by non-specific effects. The lack of detailed experimental replication and statistical analysis undermines the robustness of the conclusions.
- **Resolution test** The authors should include negative control peptides (e.g., scrambled sequences or peptides designed against an unrelated protein) in all experimental assays. They should also provide quantitative data with error bars and statistical tests for all reported effects, and clearly state the number of independent biological replicates.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Generality and scope of the claims
- **Claim pointer** "our design strategy provides a modular toolkit for designing short binding linear peptides to any target protein without the reliance on stable and ordered tertiary structure" (Abstract) and "a modular, CRISPR-like system for programmable TPD applications" (Introduction)
- **Evidence pointer** Abstract, Introduction, Discussion
- **Concern** The claim of generality is not supported by the data presented. Only three targets were tested experimentally, and all are relatively well-behaved in terms of being expressed and stable in cells. The SS18-SSX1 fusion is described as "highly-disordered," but no direct evidence of its conformational state is provided. The "CRISPR-like" analogy is an overstatement, as the system does not demonstrate the same level of programmability, efficiency, or versatility as CRISPR-based tools. The paper does not address potential limitations, such as the dependence on the quality of the training data or the generalizability to targets with very different sequence properties.
- **Why it matters** The significance of the work depends on its generality. If the approach only works for a narrow set of targets or requires extensive optimization for each new target, its impact is limited. The current claims overstate the demonstrated capabilities of the system.
- **Resolution test** The authors should temper their claims to match the evidence. They should either test additional targets with diverse properties (e.g., different subcellular localizations, different degrees of disorder) or clearly state the limitations of the current approach. The "CRISPR-like" analogy should be removed or substantially qualified.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness of the generative model
- **Claim pointer** "we propose a process to generate naturalistic peptide candidates through Gaussian perturbation of the peptidic latent space of the ESM-2 protein language model" (Abstract)
- **Evidence pointer** Methods section "Generation of peptide candidate sequences", Figure 2A
- **Concern** The method for generating peptide candidates is described briefly. The choice of Gaussian noise with variance scaled by the embedding variance is not well-justified. The relationship between the noise level (k) and the resulting sequence diversity is shown in Figure 2A, but the criteria for selecting the range of k values (5 to 22) are not clearly explained. It is unclear how the authors ensure that the generated peptides are "naturalistic" beyond the Hamming distance analysis. The manuscript does not discuss potential issues with the ESM-2 latent space, such as whether all regions of the space correspond to valid peptide sequences.
- **Why it matters** The generative step is a critical component of the pipeline. If the method for generating candidates is not well-characterized or is not reproducible, the overall approach is less useful. The lack of detail makes it difficult for others to implement or improve upon the method.
- **Resolution test** The authors should provide a more detailed description of the generative process, including the rationale for the noise model and the selection of k values. They should also provide examples of generated peptides and their properties (e.g., length distribution, amino acid composition) to demonstrate that they are indeed naturalistic.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of the CLIP model description
- **Affected element** Methods section "CLIP Architecture and Training"
- **Evidence pointer** Methods section
- **Issue** The description of the CLIP model architecture is brief. It is not clear what the "peptide encoder" and "target protein encoder" are (e.g., are they the same ESM-2 model? Are they fine-tuned?). The training procedure is described, but the hyperparameters (e.g., learning rate, batch size) are not provided.
- **Required correction** Provide a more detailed description of the model architecture, including the specific ESM-2 model used, the structure of the MLP layers, and the training hyperparameters.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Methods section "Statistical analysis and reproducibility"
- **Evidence pointer** Methods section
- **Issue** The statistical methods are described in general terms, but the specific tests used for each experiment are not clearly stated. For example, the text mentions "unpaired t test" but it is not clear which comparisons were made with this test.
- **Required correction** Clearly state which statistical test was used for each experimental comparison, and report the exact p-values.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and Materials Availability section
- **Evidence pointer** Data and Materials Availability section
- **Issue** The code is available on Hugging Face, but access requires signing a non-commercial, academic license. This may limit reproducibility for some researchers.
- **Required correction** Consider making the code freely available under a more permissive license, or at least provide a clear description of the code and its dependencies.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 3-5
- **Evidence pointer** Results sections
- **Issue** The text references figures but the figures themselves are not provided in the manuscript text. It is difficult to assess the quality of the data without seeing the figures.
- **Required correction** Ensure that all figures are clearly labeled and that the data presented in the figures is consistent with the text.

## Risk / unsupported claims
1. The claim that PepPrCLIP is a "generalizable algorithmic framework" is not fully supported, as only three targets were tested experimentally.
2. The claim that the system is "CRISPR-like" is an overstatement and not supported by the data.
3. The claim that the generated peptides are "naturalistic" is only supported by Hamming distance analysis, which is a limited measure.
4. The claim that PepPrCLIP "performs comparably to RFDiffusion" is based on a non-standard metric and may not be a fair comparison.
5. The specificity of the designed peptides for their intended targets is not demonstrated with appropriate negative controls.
6. The claim that the approach works "without the reliance on stable and ordered tertiary structure" is not directly tested, as the conformational state of the targets is not experimentally characterized.