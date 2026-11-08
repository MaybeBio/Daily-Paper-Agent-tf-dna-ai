## Review setup

- **Input scope** Full manuscript text, including abstract, main text, methods, and supplementary table headings. Figures, tables, and supplementary data files were not provided.
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical soundness as presented in the provided text. No assessment of formatting, grammar, or editorial style beyond what affects scientific clarity.
- **Shared manuscript claim summary** The authors report that all four structural regions of the Matɑ1 transcription factor, not only the HMG box domain, contribute to species-specific DNA binding and transcriptional activation. This conclusion is based on chimeric protein experiments where each of four S. cerevisiae regions was replaced with the corresponding C. albicans sequence, and activity was measured using species-specific GFP reporters.
- **Visible evidence base** Methods descriptions for plasmid construction, yeast transformation, flow cytometry, structural modeling, and statistical analysis. Reference to Figure 1 panels A, B, and D. Reference to plasmid, strain, and oligonucleotide tables. GitHub repository for code and data.
- **Missing materials affecting confidence** Figure 1 (all panels), plasmid table, strain table, oligonucleotide table, raw flow cytometry data, AlphaFold3 model outputs, and statistical analysis outputs. These are essential for evaluating the strength of the reported results.

## Reviewer

- **Overall assessment** The manuscript addresses a relevant question in transcription factor evolution, namely how homologous proteins with conserved function diverge in DNA-binding specificity. The experimental approach using structure-guided chimeras is logical and the finding that all four regions contribute to specificity is potentially interesting. However, the evidence as presented is insufficient to fully support the conclusions. The key figure is not available, the statistical details are minimal, and the discrepancy with previously published results regarding C. albicans reporter activation is not adequately resolved. The manuscript would benefit from additional experiments or analyses to strengthen the claim that all four regions contribute to specificity rather than merely to overall protein stability or expression.
- **Who would be interested in the results, and why** Researchers studying transcription factor evolution, DNA-binding specificity, HMG box proteins, and fungal mating type regulation. The work may also be of interest to those developing computational predictions of transcription factor binding sites and interpreting the functional impact of sequence variation in regulatory proteins.
- **Major strengths** The question is well framed and biologically meaningful. The use of structure-guided chimera design based on AlphaFold3 predictions is a modern and appropriate approach. The inclusion of a positive control reporter (C. albicans) to assess chimeric protein functionality is a good experimental design element. The work addresses a gap in understanding how regions outside canonical DNA-binding domains contribute to specificity.
- **Major Concerns** The following concerns are identified.
- **Minor Comments** The following comments are identified.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4.
- **Assessment against Nature-style criteria** Originality: The question of how multiple protein regions contribute to transcription factor binding specificity is not entirely new, but the specific focus on Matɑ1 homologs and the systematic chimera approach provides a fresh angle. Scientific importance: The findings could inform broader understanding of transcription factor evolution and specificity determinants, which is of moderate to high importance. Interdisciplinary readership: The topic is primarily of interest to molecular biologists, evolutionary biologists, and computational biologists working on gene regulation. The broader readership appeal is limited. Technical soundness: The experimental design is reasonable, but the evidence base is incomplete as presented. Key data are missing and statistical details are insufficient. Readability for nonspecialists: The manuscript is generally clear, but assumes familiarity with yeast genetics and transcription factor biology. The abstract is accessible, but the main text would benefit from additional context for nonspecialists.
- **Recommendation posture** Currently not established from the provided evidence. The core claim that all four regions contribute to sequence specificity is plausible but not fully supported without the missing figure and additional experimental or analytical details.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "all four regions of Matɑ1 – not just the HMG box domain – are important for sequence specificity."
- **Evidence pointer** Figure 1D, described in the main text but not provided.
- **Concern** The central conclusion rests entirely on Figure 1D, which is not available for review. The text states that replacement of any of the four regions reduced activation from the S. cerevisiae reporter, but no quantitative data, effect sizes, or statistical comparisons are provided. Without the figure, it is impossible to assess whether the reductions are substantial, partial, or within noise.
- **Why it matters** The claim that all four regions contribute to specificity depends on demonstrating that each chimera shows a meaningful loss of function on the S. cerevisiae reporter while retaining function on the C. albicans reporter. Without the actual data, the strength of this effect cannot be evaluated.
- **Resolution test** Provide Figure 1D with raw data points, error bars, and statistical annotations. Report effect sizes and p-values for each chimera compared to full-length Sc Matɑ1 on both reporters.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design
- **Claim pointer** The authors state that "both Matɑ1 homologs could drive expression from the C. albicans TCCTTT sequence; while this differs from what Baker et al. observed."
- **Evidence pointer** Main text, Results section, location not provided.
- **Concern** The authors report a discrepancy with previously published results (Baker et al., 2011) regarding whether Sc Matɑ1 can activate the C. albicans reporter. They do not explain this discrepancy or address whether it affects the interpretation of their chimera results. If Sc Matɑ1 activates the C. albicans reporter in their system but not in the original study, the assay conditions or reporter constructs may differ in ways that could also affect the S. cerevisiae reporter results.
- **Why it matters** The C. albicans reporter is used as a positive control for chimeric protein functionality. If the assay system behaves differently from the published system, the validity of this control and the interpretation of the chimera results may be compromised.
- **Resolution test** Provide a detailed comparison of the reporter constructs and assay conditions used here versus those in Baker et al. (2011). Discuss potential reasons for the discrepancy and how it affects the interpretation of the results.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "Replacement of any of the four regions reduced activation from the S. cerevisiae CTATTG promoter relative to the full length S. cerevisiae Matɑ1."
- **Evidence pointer** Methods, Data analysis and statistics section.
- **Concern** The statistical analysis is described only as "Wilcoxon rank sum exact test" with no details on the number of biological replicates, how many cells were analyzed per replicate, whether the data were pooled or analyzed per replicate, or how multiple comparisons were handled. The percentage of GFP-positive cells is mentioned as the measured metric, but it is unclear whether this is the most appropriate metric or whether mean fluorescence intensity was also considered.
- **Why it matters** Without adequate statistical detail, it is not possible to determine whether the reported reductions are statistically significant and robust. The choice of metric and analysis approach can materially affect the conclusions.
- **Resolution test** Provide full statistical details, including number of replicates, number of cells analyzed, the exact test used, whether corrections for multiple comparisons were applied, and the raw data or a link to the data repository.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation
- **Claim pointer** The authors conclude that "all four regions of Matɑ1 – not just the HMG box domain – are important for sequence specificity."
- **Evidence pointer** Main text, Discussion section, location not provided.
- **Concern** The experiments measure transcriptional activation, not DNA binding directly. Reduced activation could result from decreased protein stability, impaired nuclear localization, disrupted Mcm1 interaction, or other indirect effects, rather than from a direct contribution to DNA sequence specificity. The authors acknowledge this possibility in the discussion but do not provide experiments to distinguish between these alternatives.
- **Why it matters** The claim is specifically about "sequence specificity," but the assay measures a downstream functional output. Without evidence that the chimeric proteins are expressed at comparable levels, properly localized, and able to interact with Mcm1, the conclusion that the regions contribute to specificity rather than to general protein function is not established.
- **Resolution test** Provide western blot or other expression data for the chimeric proteins, and ideally an in vitro DNA binding assay (e.g., EMSA or SELEX) to directly assess binding specificity of the chimeras.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that "all four regions of Matɑ1 – not just the HMG box domain – are important for sequence specificity." This is a strong claim that goes beyond what the experiments directly measure, as noted in R1-M4. The abstract could be more precise by stating that the regions are "important for species-specific transcriptional activation."
- **Required correction** Revise the abstract to reflect that the experiments measure transcriptional activation, and that the regions are important for species-specific activity, with the implication for binding specificity discussed as a hypothesis.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods
- **Evidence pointer** Methods, Plasmid construction section
- **Issue** The methods state that chimeras were "designed and synthesized by VectorBuilder" but do not provide details on how the chimeric junctions were chosen beyond "guided by AlphaFold3 structural predictions." The specific residues for each region are listed, but the rationale for these boundaries is not explained.
- **Required correction** Provide additional detail on how the AlphaFold3 models informed the choice of chimera boundaries, and whether alternative boundaries were considered or tested.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods, Flow cytometry section
- **Issue** The gating strategy for identifying GFP-positive cells is not described. The percentage of GFP-positive cells is reported, but it is unclear how the gate was set and whether it was consistent across experiments.
- **Required correction** Describe the gating strategy, including whether it was based on a negative control and whether the same gate was applied to all samples.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Main text, Discussion section, location not provided
- **Issue** The discussion mentions that regions outside the HMG box "may influence specificity by altering Matɑ1 conformation and DNA deformation, or they may contact DNA directly." These are plausible hypotheses, but no experiments or structural analyses are presented to support or distinguish between them.
- **Required correction** Either present additional data to support these hypotheses or clearly frame them as speculative directions for future work.

## Risk / unsupported claims

- The claim that "all four regions of Matɑ1 – not just the HMG box domain – are important for sequence specificity" is not fully supported because the assay measures transcriptional activation, not binding specificity, and the key figure is not available.
- The statement that "all four chimeras activated expression from that promoter above the level seen in the negative control" is reported without quantitative data or statistical support.
- The discrepancy with Baker et al. (2011) regarding C. albicans reporter activation by Sc Matɑ1 is noted but not explained, leaving the validity of the positive control uncertain.
- The structural models from AlphaFold3 are referenced as guiding the chimera design, but no model figures or confidence metrics are provided, making the structural rationale difficult to evaluate.
- The claim that regions outside the HMG box may contact DNA directly or alter DNA deformation is speculative and not supported by any experimental evidence in the provided text.