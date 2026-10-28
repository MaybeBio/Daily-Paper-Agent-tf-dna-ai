## Review setup
- **Input scope** Full manuscript text, including abstract, background, methods, results, discussion, conclusions, and supplementary figure/table legends.
- **Assessment boundary** Scientific validity of the claims, experimental design, data interpretation, and technical soundness. Editorial and stylistic issues are noted only where they affect clarity or reproducibility.
- **Shared manuscript claim summary** The authors report that TBP and SNAP50 from Trypanosoma cruzi bind specifically to the Pr77 promoter sequence of non-LTR retrotransposons. TBP binds directly and cooperatively (Hill coefficient = 1.67) to double-stranded and single-stranded Pr77 DNA, with preferential binding to the DPE motif and downstream region. SNAP50 shows weak direct binding that is stabilized by UV crosslinking, suggesting protein-protein interactions mediate its recruitment. Both proteins are proposed as components of the Pr77 transcriptional complex.
- **Visible evidence base** Figures 1–9, Supplementary Figures S1–S2, Supplementary Table S3, methods section, results section, discussion section.
- **Missing materials affecting confidence** Raw quantification data for EMSA band intensities, full Western blot images with molecular weight markers, negative control data for antibody specificity (e.g., pre-immune sera or knockout validation), and statistical analysis details for Hill coefficient fitting. The manuscript does not provide the full sequence of the Pr77 probe or the exact coordinates of the DPE motif relative to the transcription start site in the figure legends.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant gap in trypanosomatid transcription biology by identifying candidate transcription factors for the Pr77 promoter. The experimental approach is straightforward and the data are largely consistent with the conclusions. However, several technical concerns regarding binding specificity, antibody validation, and quantitative rigor need to be addressed before the case is fully established.
- **Who would be interested in the results, and why** Researchers studying trypanosomatid gene regulation, retrotransposon biology, and RNA polymerase II transcription in protozoan parasites. The findings may also interest those working on the evolution of promoter elements and transcription factor networks in kinetoplastids.
- **Major strengths** The study is the first to identify specific transcription factors binding the Pr77 promoter. The use of multiple complementary approaches (protein capture, EMSA, competition assays, UV crosslinking) strengthens the conclusions. The Hill coefficient analysis provides quantitative support for cooperative binding. The inclusion of multiple control proteins (BSA, KMP11, T-GP63) in EMSA experiments is commendable.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (antibody specificity), R1-M2 (SNAP50 binding interpretation), R1-M3 (quantitative rigor of competition assays), R1-M4 (nuclear complex composition).
- **Assessment against Nature-style criteria**  
  - *Originality*: Moderate. The identification of TBP and SNAP50 as Pr77-binding factors is novel, but the conceptual framework (transcription factors binding retrotransposon promoters) is not unprecedented.  
  - *Scientific importance*: Moderate. The findings advance understanding of trypanosomatid transcription, but the broader impact beyond parasitology is limited.  
  - *Interdisciplinary readership*: Limited. The work is primarily of interest to parasitologists and molecular biologists specializing in trypanosomatids.  
  - *Technical soundness*: Adequate but with notable gaps in antibody validation and quantitative analysis.  
  - *Readability for nonspecialists*: Acceptable. The manuscript is generally clear, though some methods and figure legends could be more explicit.
- **Recommendation posture** Supportive if technical concerns are resolved.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that the generated monoclonal antibodies specifically recognize TBP and SNAP50 in T. cruzi extracts.  
- **Evidence pointer** Figure 1b, 1c; Methods section "Hybridoma generation and production of αTBP and αSNAP50 monoclonal antibodies (mAbs)"  
- **Concern** The manuscript does not provide sufficient validation of antibody specificity. The Western blots in Figure 1b and 1c show bands at expected molecular weights, but no negative controls (e.g., pre-immune serum, isotype control, or knockdown/knockout lysates) are shown. Given that the antibodies are used for immunodetection in complex protein mixtures (Figures 2, 8, 9), cross-reactivity with other proteins could confound the interpretation of the results.  
- **Why it matters** The central claims of the paper depend on the reliable detection of TBP and SNAP50 in parasite extracts and in DNA-bound complexes. Without demonstrated specificity, the identification of these proteins as Pr77-binding factors is not fully supported.  
- **Resolution test** Provide additional validation data, such as Western blots using pre-immune sera, peptide competition assays, or analysis of lysates from cells with reduced TBP/SNAP50 expression (e.g., RNAi or CRISPR-based knockdown). Alternatively, show that the antibodies do not cross-react with recombinant proteins from related trypanosomatid species.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Interpretation of results  
- **Claim pointer** The authors state that SNAP50 exhibits weak direct binding to the Pr77 sequence and that its recruitment is likely mediated by protein-protein interactions.  
- **Evidence pointer** Figure 4b, 4c, 4d; Results section "T. cruzi TBP and SNAP50 proteins bind to the Pr77 promoter sequence"  
- **Concern** The evidence for SNAP50 binding is indirect and somewhat contradictory. In Figure 4b, no shifted complex is observed with SNAP50 alone in native EMSA. Only after UV crosslinking (Figure 4c, 4d) is a weak band detected. The authors interpret this as weak direct binding, but it could also reflect non-specific crosslinking of SNAP50 to DNA or the presence of a contaminating DNA-binding protein in the recombinant SNAP50 preparation. The claim that SNAP50 is part of the Pr77 complex in parasite extracts (Figure 8c) relies on the antibody detection, which is subject to the specificity concerns raised in R1-M1.  
- **Why it matters** The conclusion that SNAP50 participates in the Pr77 transcriptional complex is a key finding. If the binding is not specific or is an artifact of the experimental conditions, the model proposed by the authors is weakened.  
- **Resolution test** Perform EMSA with purified SNAP50 in the presence of competitor DNA (e.g., unlabeled Pr77, non-specific DNA) to demonstrate specificity. Use a different crosslinking approach (e.g., formaldehyde or chemical crosslinking) to confirm the interaction. Additionally, test whether SNAP50 binding is enhanced in the presence of TBP or other nuclear proteins, which would support the protein-protein interaction model.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** Quantitative rigor  
- **Claim pointer** The authors report a Hill coefficient of 1.67 for TBP binding to Pr77, indicating positive cooperativity.  
- **Evidence pointer** Figure 4a (bottom panel); Supplementary Figure S1; Results section "T. cruzi TBP and SNAP50 proteins bind to the Pr77 promoter sequence"  
- **Concern** The Hill coefficient is derived from fitting data from three independent experiments, but the manuscript does not provide error estimates or confidence intervals for the fitted parameters. The R² value of 0.97 is reported, but this alone does not establish the reliability of the Hill coefficient. Additionally, the concentration range of TBP used (0.32–6.35 µM) may not be sufficient to define the binding curve accurately, particularly at the lower end where binding is minimal.  
- **Why it matters** The claim of cooperative binding is used to support the model of TBP multimerization on the Pr77 promoter. Without robust statistical analysis, this conclusion is not fully supported.  
- **Resolution test** Provide the mean and standard deviation (or standard error) for the Hill coefficient and Kd from the three independent experiments. Show the individual data points on the binding curve. Consider performing additional experiments at lower and higher TBP concentrations to better define the curve.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Interpretation of results  
- **Claim pointer** The authors conclude that TBP and SNAP50 are part of a protein complex that binds to Pr77, based on UV crosslinking and immunodetection.  
- **Evidence pointer** Figure 8a–d; Results section "T. cruzi TBP and SNAP50 are part of a protein complex that binds to Pr77"  
- **Concern** The UV crosslinking experiments show that TBP is detected in a high-molecular-weight complex (~90 kDa) when parasite nuclear extracts are incubated with Pr77 DNA. However, the composition of this complex is not characterized. The authors suggest that SNAP50 is also part of the complex, but the SNAP50 immunodetection (Figure 8c) does not show a clear shifted band corresponding to a DNA-bound complex. The absence of a shifted SNAP50 band in the crosslinked samples is not adequately explained.  
- **Why it matters** The claim that SNAP50 is part of the Pr77-bound complex is central to the paper's conclusions. If SNAP50 is not present in the complex, the model of cooperative recruitment is not supported.  
- **Resolution test** Perform supershift assays with anti-SNAP50 antibodies in native EMSA to demonstrate that SNAP50 is part of the DNA-protein complex. Alternatively, use a two-step approach: immunoprecipitate the crosslinked complex with anti-SNAP50 and probe for Pr77 DNA by PCR or Southern blot.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Figure 7a  
- **Evidence pointer** Figure 7a; Results section "T. cruzi TBP and SNAP50 proteins bind to the Pr77 promoter sequence"  
- **Issue** The sequence of Pr77 and the positions of the overlapping oligonucleotide pairs are not clearly annotated. The DPE motif is shaded, but the exact nucleotide positions relative to the transcription start site are not indicated in the figure or legend.  
- **Required correction** Add nucleotide numbering to the Pr77 sequence in Figure 7a and indicate the boundaries of each oligonucleotide pair. Provide the exact coordinates of the DPE motif in the figure legend.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Methods section "Cloning and purification of the rTBP and rSNAP50 recombinant proteins"  
- **Evidence pointer** Methods section; Supplementary Table S3  
- **Issue** The methods describe the cloning of TBP and SNAP50 coding sequences but do not specify the expression vector details beyond pQE30, nor the purification tag (presumably His-tag). The elution conditions for Ni²⁺ affinity chromatography are not described.  
- **Required correction** Provide details on the expression and purification protocol, including the imidazole concentration used for elution, and confirm the presence of the His-tag in the recombinant proteins.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Statistical reporting  
- **Affected element** Figure 4a (bottom panel)  
- **Evidence pointer** Figure 4a; Results section "T. cruzi TBP and SNAP50 proteins bind to the Pr77 promoter sequence"  
- **Issue** The binding curve in Figure 4a shows error bars, but the figure legend does not specify what the error bars represent (e.g., standard deviation, standard error) or the number of replicates.  
- **Required correction** Clarify in the figure legend the type of error bars and the number of independent experiments.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Discussion section  
- **Evidence pointer** Discussion section  
- **Issue** The discussion mentions that "further studies are required to elucidate the basic mechanisms required for functional RNA polymerase II-dependent transcription in Trypanosoma cruzi," but does not suggest specific experiments or approaches to address this.  
- **Required correction** Add a brief paragraph outlining potential future directions, such as mutational analysis of the Pr77 promoter, chromatin immunoprecipitation, or in vitro transcription assays.

## Risk / unsupported claims
- The claim that SNAP50 is part of the Pr77-bound complex is not fully supported by the data, as the SNAP50 immunodetection in crosslinked samples does not show a clear shifted band (Figure 8c).
- The claim that TBP binding is cooperative (Hill coefficient = 1.67) lacks statistical validation (no confidence intervals or error estimates).
- The claim that TBP binds to both strands of Pr77 and is independent of secondary structure is based on EMSA with denatured probes, but the authors do not rule out the possibility that the single-stranded probes adopt alternative structures under the assay conditions.
- The functional relevance of TBP and SNAP50 binding to Pr77 for retrotransposon transcription is not directly tested; the manuscript only demonstrates binding, not transcriptional activity.