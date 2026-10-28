## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific claims, methodology, data interpretation, and conclusions as presented in the manuscript
- **Shared manuscript claim summary** The authors report that Oct4 binds a compact palindromic DNA element with a methylated CpG core (CpGpal) as a cooperative homodimer, mediated solely by the POU homeodomain, and that this binding is associated with methylated, closed chromatin during pluripotency reprogramming. They further propose that this binding modality is unique to Oct4 among POU factors and may contribute to its germline-related functions.
- **Visible evidence base** Abstract, full results, methods summary, figure legends referenced in text, supplementary figure references, data availability statement
- **Missing materials affecting confidence** Supplementary figures and tables referenced throughout (S1–S8, Tables S1–S8) are not provided; full methods for Spec-seq, retrovirus production, iPSC reprogramming, and molecular dynamics simulations are not available; raw ChIP-seq, WGBS, and RNA-seq processing details are incomplete; structural coordinates for the modeled Oct4/CpGpal complex are not deposited

## Reviewer
- **Overall assessment** The manuscript addresses an important and timely question regarding how a pioneer transcription factor interacts with methylated DNA elements. The finding that Oct4 can bind a methylated CpG-containing palindromic motif as a homeodomain-only dimer is potentially significant and would extend current understanding of POU factor DNA recognition. However, the evidence presented is incomplete in several critical respects. The structural model is not experimentally validated, the claim of Oct4 specificity relative to other POU factors rests on limited comparative data, and the functional relevance of CpGpal binding in cells remains correlative. The manuscript would benefit from additional experimental support, particularly structural data for the Oct4/CpGpal complex and functional assays linking CpGpal binding to transcriptional outcomes.
- **Who would be interested in the results, and why** Researchers studying transcription factor DNA binding specificity, pioneer factors, epigenetic regulation of pluripotency, and POU domain family biology. The finding that a homeodomain can independently dimerize on a methylated palindromic element would be of interest to structural biologists and those studying protein-DNA recognition mechanisms. The potential link to germline development and reprogramming would attract stem cell biologists.
- **Major strengths** The study combines multiple approaches including ChIP-seq re-analysis, biochemical binding assays, structural modeling, and molecular dynamics simulations. The identification of CpGpal as a distinct binding element enriched in Oct4 ChIP-seq datasets across multiple independent studies is compelling. The comparative analysis with Brn2 provides a useful contrast that highlights Oct4 specificity. The observation that CpGpal sites remain methylated during reprogramming, unlike canonical Oct4 enhancers, is novel and potentially important.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (structural model not experimentally validated), R1-M2 (specificity claim insufficiently supported), R1-M3 (functional relevance not established)
- **Assessment against Nature-style criteria** Originality: The finding of homeodomain-only dimeric binding to a methylated palindromic element is novel and would be of interest to a broad readership. Scientific importance: The potential link between Oct4 binding to methylated DNA and germline function is significant, but the current evidence is largely correlative. Interdisciplinary readership: The topic bridges structural biology, epigenetics, and stem cell biology, which would attract readers across these fields. Technical soundness: The biochemical and computational approaches are generally sound, but the lack of experimental structural validation and incomplete functional assays weaken the overall case. Readability for nonspecialists: The manuscript is clearly written and the main findings are accessible, though some sections assume familiarity with POU domain biology and ChIP-seq analysis.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly the need for experimental structural validation and functional assays linking CpGpal binding to transcriptional regulation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "dimeric Oct4-binding to CpGpal is driven by the POU-homeodomain whilst the POU-specific domain is detached from DNA" and present a structural model (Figure 6D–F) as the basis for this claim.
- **Evidence pointer** Results section "Basis for Oct4 dimerization on the CpGpal"; Figure 6D–F; Supplementary Figure S7E, S8A–E
- **Concern** The structural model of the Oct4/CpGpal complex is built by homology, not determined experimentally. The authors acknowledge this limitation but still use the model to make specific claims about protein-DNA contacts and the role of the RK motif. The model is not deposited in a public database, and the validation criteria for the model are not described.
- **Why it matters** The central mechanistic claim of the paper, that the homeodomain alone drives dimeric binding to CpGpal, rests on this model. Without experimental structural data (e.g., co-crystal structure, NMR, or cryo-EM) or at minimum a rigorously validated model with clear confidence metrics, the atomic-level interpretation remains speculative.
- **Resolution test** Provide experimental structural data for the Oct4 POUHD/CpGpal complex, or deposit the model with validation metrics (e.g., MolProbity scores, Ramachandran statistics) and demonstrate that the model is consistent with mutagenesis data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors claim that "binding to CpGpal is Oct4-specific as other POU factors expressed in somatic cells avoid this element" and that this distinguishes Oct4 from Brn2 and other POU family members.
- **Evidence pointer** Results section "Brn2 dimerizes poorly on the CpGpal and evades it in neural stem cells"; Figure 4E–G; Supplementary Table S6
- **Concern** The specificity claim is based on a comparison with only one other POU factor (Brn2) in biochemical assays and on ChIP-seq re-analysis of somatic POU factors. The ChIP-seq data for other POU factors come from different cell types and experimental conditions, making direct comparison problematic. The authors do not test other POU family members (e.g., Oct1, Oct6, Brn4) in their binding assays.
- **Why it matters** The claim that CpGpal binding is a unique feature of Oct4 is central to the paper's significance. If other POU factors can also bind this element under appropriate conditions, the uniqueness argument collapses, and the functional implications for pluripotency and germline development are weakened.
- **Resolution test** Test a panel of POU family members (at least Oct1, Oct6, Brn4) for CpGpal binding in vitro and in cells. Provide matched ChIP-seq datasets from the same cell type for direct comparison.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors state that "Oct4 exerts parts of its regulatory function in the context of methylated DNA through a DNA recognition mechanism that solely relies on its homeodomain" and suggest that CpGpal binding contributes to germline development.
- **Evidence pointer** Results sections "Oct4 binds CpGpal elements during pluripotency reprogramming" and "CpGpal sites show reduced demethylation and elevated de novo methylation in ESCs"; Figures 1–2; Discussion
- **Concern** The functional relevance of CpGpal binding is inferred from correlative ChIP-seq and methylation data. The authors do not provide direct evidence that Oct4 binding to CpGpal sites leads to transcriptional regulation, chromatin changes, or any measurable biological outcome. The claim that this binding modality contributes to germline development is speculative and not tested experimentally.
- **Why it matters** The paper's significance depends on the functional importance of CpGpal binding. Without functional assays (e.g., reporter assays, CRISPR-based perturbation of CpGpal sites, or mutation of the RK motif in cellular assays), the biological relevance remains unproven.
- **Resolution test** Perform functional assays such as reporter gene assays with wild-type and mutant CpGpal elements, or genome editing to mutate CpGpal sites and assess effects on gene expression and pluripotency.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "Oct4 cooperatively binds the CpGpal element as a homodimer" and report cooperativity factors (ω) for this interaction.
- **Evidence pointer** Results section "Oct4 cooperatively homodimerizes on the CpGpal motif"; Figure 4B–C; Supplementary Figure S4C
- **Concern** The cooperativity factor is calculated using a previously established model, but the details of the fitting procedure, the number of replicates, and the error estimates are not provided in the main text. The authors do not show the raw binding isotherms or the quality of the fits.
- **Why it matters** The claim of positive cooperativity is a key mechanistic finding. Without transparent reporting of the binding data and analysis, the reliability of the cooperativity factor cannot be assessed.
- **Resolution test** Provide raw binding data, fitting details, and error analysis in the supplementary materials.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, last sentence
- **Issue** The abstract states that Oct4 binds CpGpal "in alternative states of pluripotency and during cellular reprogramming towards induced pluripotent stem cells (iPSCs)" but does not specify which alternative states were examined.
- **Required correction** Specify the pluripotency states analyzed (e.g., naive, primed, or both) in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Re-analysis of genome-wide datasets"
- **Evidence pointer** Materials and Methods, "Re-analysis of genome-wide datasets"
- **Issue** The methods for ChIP-seq data processing are described, but the specific parameters for peak calling, motif discovery, and normalization are not fully detailed. The version numbers of software tools are not provided.
- **Required correction** Provide complete software versions, parameters, and analysis scripts or a link to a public repository.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 2
- **Evidence pointer** Figure 2C–D
- **Issue** The methylation status of CpGpal sites is shown as a percentage, but the number of sites analyzed and the statistical significance of differences between categories are not indicated in the figure legend.
- **Required correction** Add sample sizes and statistical test results to the figure legend.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, paragraph on germline development
- **Evidence pointer** Discussion, "One interesting possibility is that Oct4 may be directly involved in the maintenance or de novo methylation of CpGpal sites"
- **Issue** The discussion speculates about Oct4 involvement in germline development based on the methylation status of CpGpal in germ cells, but no direct evidence links Oct4 binding to these sites with germline function.
- **Required correction** Clearly distinguish speculation from evidence and suggest specific experiments to test this hypothesis.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Data availability
- **Evidence pointer** Data Availability section
- **Issue** The structural models of the Oct4/CpGpal complex are not deposited in a public repository, and the molecular dynamics simulation trajectories are only available as movies in the supplementary materials.
- **Required correction** Deposit the structural models in a public database (e.g., ModelArchive or Zenodo) and provide simulation input files and trajectories.

## Risk / unsupported claims
- The claim that Oct4 binding to CpGpal is "Oct4-specific" among POU factors is not sufficiently supported, as only Brn2 was tested in biochemical assays and the ChIP-seq comparison across POU factors is confounded by different cell types and conditions.
- The structural model of the Oct4/CpGpal complex is not experimentally validated, and specific atomic-level interactions (e.g., R105 with the CpG step, RK motif contacts) are presented with more certainty than the evidence warrants.
- The functional significance of CpGpal binding for germline development is speculative and not tested experimentally.
- The claim that Oct4 binding to CpGpal sites is associated with resistance to demethylation is based on correlative data and does not establish causality.
- The statement that "the pioneer transcription factor model may not apply to all Oct4 binding events" is an interpretation that goes beyond the data presented, as the authors do not directly test pioneer activity at CpGpal sites.