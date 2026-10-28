## Review setup
- **Input scope** Full manuscript text, including abstract, results, figures (as referenced), methods, and supplementary figure/table legends as described in the text.
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency of the presented evidence. No assessment of editorial fit or journal-specific policy.
- **Shared manuscript claim summary** The authors propose that intracellular pH (pHi) oscillations during carbon starvation in Saccharomyces cerevisiae act as a signal for transcriptional reprogramming, and that the SWI/SNF chromatin remodeling complex, via a glutamine-rich low-complexity domain (QLC) in its SNF5 subunit containing pH-sensitive histidines, functions as a molecular pH sensor to mediate this response.
- **Visible evidence base** Abstract, full results section, discussion, materials and methods, and references to figures and supplementary materials. No raw data files, uncropped blots, or full supplementary tables were provided for independent verification.
- **Missing materials affecting confidence** Raw RNA-seq data, full lists of differentially expressed genes, uncropped Western blots, complete ChIP-qPCR datasets, and detailed simulation output parameters were not available for direct inspection. The manuscript relies heavily on supplementary figures and tables that were not fully accessible in the provided material.

## Reviewer
- **Overall assessment** This manuscript presents a compelling and novel hypothesis that a low-complexity domain within a chromatin remodeling complex acts as a direct pH sensor. The combination of in vivo single-cell pH measurements, genetic analysis, in vitro biochemistry, and computational simulations is ambitious and largely well-executed. The central claim that the SNF5 QLC and its histidines are required for proper transcriptional reprogramming during carbon starvation is supported by the data presented. However, several concerns regarding the mechanistic depth, the specificity of the pH-sensing model, and the interpretation of the in vitro and simulation data need to be addressed to fully establish the case.
- **Who would be interested in the results, and why** This work will be of significant interest to researchers in the fields of chromatin biology, gene regulation, cellular stress responses, and biophysics of intrinsically disordered proteins. The concept of a chromatin remodeler directly sensing a metabolic byproduct (pH) to modulate transcription is conceptually novel and will likely stimulate further investigation into similar mechanisms in other systems. The study also contributes to the growing appreciation of IDPs as dynamic sensors of the cellular environment.
- **Major strengths**
    1.  The study addresses a fundamental and underexplored question: how do cells positively sense and respond to intracellular acidification during stress? The identification of a specific, evolutionarily relevant protein domain as a putative sensor is a significant conceptual advance.
    2.  The combination of single-cell pH imaging with a transcriptional reporter is powerful and reveals heterogeneity in the stress response that would be missed by population-averaged methods.
    3.  The genetic separation of the QLC deletion and histidine-to-alanine point mutants provides strong evidence that the observed phenotypes are due to the specific loss of histidine-mediated pH sensing, rather than a general disruption of SNF5 function.
    4.  The in vitro reconstitution experiments are a critical step in demonstrating a direct, pH-dependent biochemical function of the QLC, moving beyond purely correlative in vivo observations.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Mechanistic Link
    - **Claim pointer** The manuscript claims that the SNF5 QLC acts as a pH sensor that directly mediates pH-dependent recruitment of SWI/SNF to transcription factors, thereby driving transcriptional reprogramming.
    - **Evidence pointer** Results section "The SNF5 QLC mediates a pH-sensitive transcription factor interaction in vitro", Figure 5.
    - **Concern** The in vitro recruitment assay demonstrates that the wild-type SNF5 QLC mediates pH-dependent interaction with the Gal4-VP16 activator, and that this is lost in the mutants. However, the manuscript does not establish a direct, physical interaction between the QLC and the transcription factor. The assay measures the outcome of a multi-step process (recruitment, remodeling, FRET change) and does not rule out indirect effects, such as pH-dependent changes in the nucleosome substrate or the Gal4-VP16 protein itself. The claim of a "pH-sensitive transcription factor interaction" is therefore an interpretation that is not directly supported by the data.
    - **Why it matters** The central model of the paper rests on the idea that the QLC is a pH-sensitive interaction module. If the pH sensitivity is due to another component of the assay, or if the QLC's effect is on a downstream step (e.g., remodeling processivity) rather than initial binding, the proposed mechanism would be incorrect.
    - **Resolution test** To strengthen this claim, the authors should perform a direct binding assay, such as pull-downs or biolayer interferometry, with the purified QLC (or SNF5 subcomplex) and the Gal4-VP16 activation domain at different pH values. This would definitively demonstrate a direct, pH-dependent physical interaction.
    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** No
    - **Axis** Specificity of pH Sensing
    - **Claim pointer** The manuscript proposes that the SNF5 QLC specifically senses pH changes via histidine protonation, leading to conformational expansion and altered interactions.
    - **Evidence pointer** Results section "Protonation of histidines leads to conformational expansion of the SNF5 QLC", Figure 6.
    - **Concern** The all-atom simulations show that protonation of histidines in the isolated QLC peptide leads to an increase in radius of gyration. While this is a plausible biophysical mechanism, the manuscript does not demonstrate that this conformational change is necessary or sufficient for the functional effects observed in vivo or in vitro. The simulations are performed on a short peptide fragment, and it is unclear if this behavior is representative of the full-length QLC within the context of the entire SNF5 protein and the SWI/SNF complex. Furthermore, the model is purely correlative; no experiments are presented that test the functional importance of the predicted conformational change.
    - **Why it matters** The paper proposes a specific biophysical mechanism. Without experimental validation, the simulation data remain a hypothesis-generating observation. The link between the simulated conformational change and the actual functional output (transcription factor interaction) is a critical gap.
    - **Resolution test** The authors could test the functional importance of the conformational change by engineering mutations that are predicted to alter the conformational response to pH (e.g., by changing the spacing or number of histidines) and testing their effect on in vitro recruitment and in vivo transcriptional activation. Alternatively, they could use a technique like FRET or NMR to experimentally measure the conformational change of the QLC in response to pH.
    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Causal Relationship
    - **Claim pointer** The manuscript states that "a nucleocytoplasmic pH oscillation was required for the transcriptional response to carbon starvation."
    - **Evidence pointer** Results section "Induction of ADH2 upon glucose starvation requires the SNF5 glutamine-rich low-complexity sequence with native histidines", Figure 2.
    - **Concern** The data show a strong correlation between pHi dynamics and ADH2 expression. The experiments with pHclamp or mutants that fail to recover pHi demonstrate that pH recovery is necessary for expression. However, the manuscript does not fully exclude the possibility that the failure to recover pHi in the SNF5 mutants is a secondary consequence of a broader failure in transcriptional reprogramming, rather than the primary cause. The causal direction (pH change -> SNF5 -> transcription) is inferred but not definitively proven. For example, if the SNF5 mutants fail to express genes required for pH recovery, the observed phenotype would be downstream of the initial sensing event.
    - **Why it matters** The paper's title and central claim are that SWI/SNF "senses" carbon starvation via pH. To firmly establish this, it must be shown that the pH change is the upstream signal that directly acts on SWI/SNF, and not a downstream consequence of SWI/SNF's failure to activate other genes.
    - **Resolution test** A more direct test would be to acutely manipulate pHi independently of carbon starvation (e.g., by adding a weak acid/base) and show that this is sufficient to trigger SNF5-dependent transcriptional changes in the presence of glucose. Conversely, preventing the pH drop in a wild-type cell should block the response. The current experiments are largely correlative or involve long-term genetic perturbations.
- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Data Presentation
    - **Affected element** Figure 2
    - **Evidence pointer** Results section "The SNF5 QLC is required for ADH2 expression and recovery of neutral pH"
    - **Issue** The manuscript describes a bimodal population of cells in the wild-type strain, with one population recovering pH and expressing ADH2, and another that does not. The representative flow cytometry plots are mentioned, but the quantitative analysis of the fraction of cells in each population across time and genotypes is not fully clear from the text.
    - **Required correction** Please provide a clear quantification of the percentage of cells in the "recovered" vs "non-recovered" populations for each strain and time point, with appropriate statistical analysis. This will strengthen the claim that the mutants are specifically defective in the transition to the recovered state.
    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Methodological Clarity
    - **Affected element** Materials and Methods, "Nucleosome remodeling assays"
    - **Evidence pointer** Materials and Methods section "Nucleosome remodeling assays"
    - **Issue** The description of the FRET-based recruitment assay is somewhat brief. It is not entirely clear how the "recruitment" is distinguished from the subsequent "remodeling" step, and how the FRET signal is specifically attributed to the recruitment of SWI/SNF to the nucleosome via the Gal4-VP16 interaction.
    - **Required correction** Please expand the methods to clarify the exact experimental design, including the concentrations of all components, the order of addition, and the specific FRET changes that are interpreted as recruitment versus remodeling. A schematic diagram of the assay would be helpful.
    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Interpretation of Mutant Phenotype
    - **Affected element** Results section "Induction of ADH2 upon glucose starvation requires the SNF5 glutamine-rich low-complexity sequence with native histidines"
    - **Evidence pointer** Figure 1D, Figure 1—figure supplement 6
    - **Issue** The manuscript shows that the ΔQsnf5 and HtoAsnf5 strains have a stronger defect in ADH2 induction than the snf5Δ strain. This is an interesting and somewhat counterintuitive result. The text offers a possible explanation (dual role for SNF5), but it is not discussed in detail.
    - **Required correction** Please expand the discussion of this result. Why would a partial loss-of-function mutant have a stronger phenotype than a complete knockout? A more detailed model for the dual role of SNF5 in both repression and activation would be valuable for the reader.
    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Generalizability
    - **Affected element** Discussion
    - **Evidence pointer** Discussion section
    - **Issue** The manuscript focuses on S. cerevisiae and the ADH2 gene. While the authors mention that QLCs are enriched for histidines across eukaryotes, they do not discuss the potential generalizability of this mechanism to other organisms or other SWI/SNF subunits.
    - **Required correction** A brief discussion on the potential for this mechanism to be conserved in other eukaryotes, and whether other QLC-containing proteins might function as pH sensors, would significantly broaden the impact of the work.

## Risk / unsupported claims
- The claim that the SNF5 QLC directly interacts with transcription factors in a pH-dependent manner is not directly supported by the data, as the in vitro assay is indirect.
- The claim that histidine protonation-induced conformational expansion is the mechanism for functional regulation is a reasonable hypothesis but is not experimentally validated.
- The causal relationship between the pHi oscillation and SWI/SNF function is strongly suggested but not definitively proven, as the experiments do not fully exclude alternative models where the pH defect is a downstream consequence of the transcriptional failure.
- The statement that "pH changes are a second messenger for transcriptional reprogramming" is a strong conclusion. While the data support a role for pH, the term "second messenger" implies a specific signaling role that is not fully established.