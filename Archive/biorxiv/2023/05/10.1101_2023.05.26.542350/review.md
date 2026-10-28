## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends (as provided)
- **Assessment boundary** Scientific validity, technical rigor, and support for claims based solely on the provided manuscript content
- **Shared manuscript claim summary** The authors propose that ABI1, an actin regulatory protein, acts as a novel transcriptional co-regulator of Androgen Receptor (AR) through two mechanisms: direct DNA binding via its homeobox homology region (HHR) and protein-protein interaction with AR/ARv7 involving liquid-liquid phase separation (LLPS). They further claim clinical relevance through ABI1 exon 4 splicing associated with prostate cancer progression and survival.
- **Visible evidence base** Immunohistochemistry on clinical samples and mouse tissue; qPCR and ChIP-qPCR; ChIP-seq and RNA-seq data (described but not fully shown); in vitro DNA binding assays; NMR spectroscopy; LLPS assays; co-immunoprecipitation; proximity ligation assays; computational disorder predictions
- **Missing materials affecting confidence** Raw ChIP-seq and RNA-seq datasets not provided; full figure panels referenced but not all visible in text; NMR resonance assignment details partially provided; statistical details for some experiments incomplete; clinical cohort metadata limited

## Reviewer
- **Overall assessment** This manuscript presents a potentially interesting finding that ABI1, previously known for cytoskeletal regulation, may function in transcriptional control through direct DNA binding and AR interaction. The combination of clinical correlation, cell-based assays, and biophysical characterization is ambitious. However, several technical concerns and gaps in evidence weaken the current support for the central claims. The DNA binding specificity, the functional significance of the ABI1-AR interaction in transcriptional regulation, and the clinical relevance of exon 4 splicing require stronger experimental validation. The NMR data are intriguing but the mechanistic interpretation needs further support. Overall, the study has merit but is not yet fully established from the provided evidence.

- **Who would be interested in the results, and why** Researchers in prostate cancer biology, particularly those studying AR signaling and resistance mechanisms, would find this relevant. The potential link between cytoskeletal regulators and transcription could interest cell biologists studying nuclear actin functions. Those working on intrinsically disordered proteins and phase separation in transcriptional regulation would also find the LLPS aspect appealing. Clinically oriented investigators focused on biomarkers for prostate cancer progression and treatment response may be interested in the exon 4 splicing data.

- **Major strengths** The study addresses an under-explored connection between actin regulatory proteins and nuclear receptor signaling. The combination of clinical samples, cell models, and biophysical methods is commendable. The NMR-based demonstration of a fuzzy complex without disorder-to-order transition is technically rigorous. The identification of a specific DNA binding region (HHR) and the allosteric effect of exon 4 deletion are novel observations. The reciprocal regulation between ABI1 and AR provides a coherent framework for understanding tumor plasticity.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "ABI1 binds DNA through a binding mechanism involving the HHR region" and "ABI1 is a transcriptional co-regulator of AR"
- **Evidence pointer** Figure 5, in vitro binding assays, ChIP-seq data
- **Concern** The DNA binding specificity of ABI1-HHR is not rigorously established. Only a limited set of DNA probes was tested, and the physiological relevance of the identified binding sequences is unclear. The ChIP-seq data show ABI1 binding predominantly to promoter regions, but the overlap with AR binding sites and the functional consequence of this co-localization are not clearly demonstrated. The claim that ABI1 is a transcriptional co-regulator requires direct evidence that ABI1 binding to chromatin affects transcription of specific target genes, beyond correlative expression changes.
- **Why it matters** The central novelty of this work rests on ABI1 functioning as a DNA binding protein with transcriptional regulatory capacity. Without demonstrating sequence-specific binding with functional consequences, the claim remains speculative. The field requires clear evidence that ABI1 directly regulates transcription rather than indirectly affecting AR activity through cytoskeletal or signaling functions.
- **Resolution test** Provide comprehensive DNA binding specificity assays (e.g., SELEX, protein binding microarrays) to identify consensus binding motifs. Demonstrate that mutation of the HHR DNA binding region abolishes ABI1-dependent transcriptional regulation of specific target genes. Show that ABI1 and AR co-occupy regulatory regions and that ABI1 loss alters AR chromatin occupancy and target gene expression in a manner consistent with direct co-regulation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical rigor
- **Claim pointer** "ABI1 interacts with AR through a phase separation mechanism" and "co-liquid-liquid phase separation of the N-terminal intrinsically disordered regions of AR and ABI1"
- **Evidence pointer** Supplementary Figures S3-4, LLPS assays
- **Concern** The evidence for LLPS as a relevant mechanism in cells is indirect. The in vitro LLPS experiments use recombinant proteins at concentrations that may not reflect physiological conditions. The relevance of phase separation to ABI1-AR function in cells is not demonstrated. No cellular experiments showing ABI1-AR condensates, their properties, or their functional significance are presented. The claim that LLPS mediates ABI1-AR interaction and transcriptional regulation requires direct cellular evidence.
- **Why it matters** Phase separation is a rapidly evolving field with stringent criteria for demonstrating physiological relevance. The current evidence is insufficient to support the claim that LLPS is the mechanism underlying ABI1-AR interaction. Overinterpretation of in vitro LLPS data without cellular validation could mislead the field and weaken the overall credibility of the study.
- **Resolution test** Perform cellular experiments showing endogenous ABI1 and AR form condensates (e.g., using super-resolution microscopy, fluorescence recovery after photobleaching). Demonstrate that disruption of phase separation (e.g., through mutations in key residues or treatment with phase separation modulators) affects ABI1-AR interaction and transcriptional activity. Show that condensate formation correlates with transcriptional output in a physiologically relevant context.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Data availability and reproducibility
- **Claim pointer** "ABI1 ChIP-seq in the ABI1-Iso2 LNCaP cells mapped binding predominantly to promoter regions" and "disruption of ABI1 resulted in reprogramming of ∼20% of AR chromatin binding"
- **Evidence pointer** Figure 4D-G, ChIP-seq methods
- **Concern** The ChIP-seq data are described but not fully presented. Key quality metrics (e.g., number of peaks, reproducibility between replicates, peak calling thresholds) are not provided. The claim of 20% reprogramming of AR chromatin binding is striking but lacks supporting visualization or statistical analysis. The RNA-seq data are mentioned but differential expression results are not shown. Without access to these datasets or clear presentation of results, the conclusions cannot be independently evaluated.
- **Why it matters** Genome-wide analyses are central to the claim that ABI1 regulates AR transcriptional activity. The lack of detailed presentation prevents assessment of data quality and the robustness of the findings. Reproducibility is a cornerstone of scientific validity, and the current presentation does not allow for proper evaluation.
- **Resolution test** Provide comprehensive presentation of ChIP-seq and RNA-seq results, including peak counts, genomic annotations, heatmaps, and statistical analyses. Show overlap between ABI1 and AR binding sites with statistical significance. Present differential expression analysis with clear cutoffs and validation by qPCR. Make raw data publicly available and provide detailed methods for reproducibility.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Clinical relevance
- **Claim pointer** "ABI1-DNA binding activity predicts survival of prostate cancer patients" and "Exon 4 expression associated with high grade and stage of PCa tumors and lower survival"
- **Evidence pointer** Figure 5D-F, clinical cohort analysis
- **Concern** The clinical correlation between ABI1 exon 4 expression and patient outcomes is presented but the analysis appears limited. The cohort composition, statistical methods, and confounding factors are not fully described. The statement in the abstract that "ABI1-DNA binding activity predicts survival" is not directly supported by the data shown, which focus on exon 4 expression rather than DNA binding activity per se. The distinction between exon 4 expression and DNA binding capacity needs clarification.
- **Why it matters** Clinical claims have significant implications for biomarker development and patient stratification. Overstating the predictive value based on limited analysis could mislead future studies and clinical applications. The connection between the molecular mechanism and clinical outcomes needs to be more rigorously established.
- **Resolution test** Provide detailed description of the clinical cohort, including sample sizes, treatment history, and statistical models. Perform multivariate analysis controlling for known prognostic factors. Directly test whether ABI1 DNA binding activity (not just exon 4 expression) correlates with clinical outcomes. Validate findings in an independent cohort.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and statement of importance
- **Evidence pointer** Abstract, Statement of importance
- **Issue** The abstract states "ABI1-DNA binding activity predicts survival" but the data presented focus on exon 4 expression. This overstates the findings and could mislead readers.
- **Required correction** Revise the abstract to accurately reflect that exon 4 expression, which affects DNA binding, is associated with survival. Avoid implying direct measurement of DNA binding activity in clinical samples.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** NMR experiments
- **Evidence pointer** Methods, NMR section
- **Issue** The NMR titration experiments use a single protein concentration (80 µM) and a limited range of DNA ratios. The Kd values are not reported in the text, and the stoichiometry of binding is not clearly established.
- **Required correction** Report Kd values with errors from the titration experiments. Discuss the stoichiometry of binding and whether the observed affinity is consistent with physiological relevance. Consider performing additional experiments at lower protein concentrations to confirm the binding affinity.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 2, qPCR data
- **Evidence pointer** Figure 2A-B
- **Issue** The qPCR data show changes in ABI1 expression but statistical details (e.g., number of replicates, error bars definition, statistical tests used) are not fully described in the figure legends or text.
- **Required correction** Clearly state the number of biological and technical replicates, the definition of error bars, and the statistical tests used for each comparison. Ensure all data points are shown where feasible.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion of allosteric mechanism
- **Evidence pointer** Figure 5L, NMR data
- **Concern** The conclusion that exon 4 deletion affects DNA binding through an allosteric mechanism is based on NMR chemical shift changes in regions iv and v. However, the structural basis for this allosteric effect is not explored. The authors should consider whether the deletion could affect protein stability or oligomerization.
- **Required correction** Discuss alternative explanations for the observed effect, such as changes in protein stability or conformation. Consider performing additional experiments (e.g., circular dichroism, size exclusion chromatography) to rule out non-specific effects of the deletion.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The manuscript does not adequately discuss the existing literature on AR co-regulators and DNA binding proteins in prostate cancer. The novelty of the ABI1 mechanism should be positioned more clearly relative to known AR co-regulators.
- **Required correction** Add a more comprehensive discussion of known AR co-regulators and how ABI1's mechanism differs or complements existing knowledge. Cite relevant recent reviews and primary literature.

## Risk / unsupported claims
- The claim that "ABI1-DNA binding activity predicts survival" is not directly supported by the data presented, which show exon 4 expression correlation with survival.
- The statement that ABI1 is an "epigenetic regulator" is not supported by direct evidence of epigenetic modifications or chromatin remodeling activity.
- The claim of "novel DNA binding mechanism" is partially supported but requires more rigorous demonstration of specificity and functional relevance.
- The clinical relevance of the ABI1-AR interaction in tumor plasticity is inferred but not directly tested in functional in vivo models.
- The LLPS mechanism is demonstrated in vitro but not validated in cells, making the physiological relevance unsubstantiated.
- The 20% reprogramming of AR chromatin binding upon ABI1 loss is a strong claim that requires full data presentation and statistical validation.