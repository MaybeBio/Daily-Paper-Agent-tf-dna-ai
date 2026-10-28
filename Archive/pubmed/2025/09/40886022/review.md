## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, limitations) as provided.
- **Assessment boundary** Scientific content, methodological soundness, internal consistency, and support of claims by the presented evidence. Editorial and formatting issues are noted only where they affect comprehension.
- **Shared manuscript claim summary** The authors propose that a peptide (EXDDNMT1/ELK1) designed to disrupt the DNMT1/ELK1 interaction selectively demethylates the DGKI promoter without affecting MGMT, thereby restoring temozolomide sensitivity in glioblastoma with an MGMTmethylated/DGKImethylated profile. They further propose that DGKI methylation status in tumor and circulating cell-free DNA can serve as a dynamic biomarker for treatment response and resistance.
- **Visible evidence base** In vitro data from glioblastoma cell lines (U251, U373, U87, A172) and patient-derived primary cultures (PCTC-dGB); AlphaFold2-based structural predictions; chromatin immunoprecipitation (ChIP/reChIP); qMSRE methylation assays; ELISA; cell viability, doubling time, and invasion assays; in vivo subcutaneous xenograft studies in immunodeficient mice; clinical cohort data (22 patients for survival, 15 patients for paired resections, 5 patients for cfcDNA monitoring, 18 patients for cfcDNA correlation).
- **Missing materials affecting confidence** No raw data, statistical outputs, or figure panels are available for independent verification. The peptide sequence, control peptide details, and delivery/validation data are not fully described. The in vivo study lacks details on randomization, blinding, sample size justification, and statistical methods. The clinical cohorts are small and no power calculation is provided. The AlphaFold2 model confidence is reported as a single score without the underlying pTM and ipTM values.

## Reviewer
- **Overall assessment** This manuscript addresses a clinically relevant problem: improving temozolomide response in a subset of glioblastoma patients with a specific methylation profile. The central idea, that a peptide disrupting a DNMT1/ELK1 interaction can selectively demethylate DGKI, is novel and potentially impactful. However, the evidence as presented is insufficient to fully establish the mechanism, specificity, and therapeutic potential. Several claims are supported by indirect or incomplete data, and key experimental details are missing. The clinical observations are intriguing but based on very small cohorts. The work is promising but requires substantial additional validation and clarification before the conclusions can be considered robust.
- **Who would be interested in the results, and why** Neuro-oncologists and clinicians treating glioblastoma would be interested in a potential new therapeutic strategy for a patient subgroup with poor prognosis. Researchers in epigenetic therapy, DNA methylation, and drug resistance would be interested in the concept of targeting transcription factor-directed DNA methylation and the use of AlphaFold2 for peptide design. The proposed use of cfcDNA methylation as a dynamic biomarker would interest translational researchers and those developing liquid biopsy approaches.
- **Major strengths**
  - The clinical question is well-defined and addresses an unmet need in a specific patient subgroup.
  - The combination of computational prediction (AlphaFold2) with experimental validation is a modern and potentially powerful approach.
  - The study includes both in vitro and in vivo models, and attempts to correlate findings with patient samples.
  - The concept of a dynamic methylation shift associated with resistance is clinically relevant and novel.
- **Major Concerns**
  - **R1-M1** (Blocking: Yes)
  - **R1-M2** (Blocking: Yes)
  - **R1-M3** (Blocking: Yes)
  - **R1-M4** (Blocking: No)
  - **R1-M5** (Blocking: No)
- **Minor Comments**
  - **R1-m1**
  - **R1-m2**
  - **R1-m3**
  - **R1-m4**
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3 are blocking. The lack of peptide characterization, incomplete in vivo data, and insufficient mechanistic evidence are the primary technical failings.
- **Assessment against Nature-style criteria**
  - **Originality** High. The concept of a peptide disrupting a specific DNMT1/transcription factor interaction for selective demethylation is novel. The use of AlphaFold2 for this purpose is also innovative.
  - **Scientific importance** Potentially high. If validated, this could offer a new therapeutic option for a defined patient subgroup and introduce a new class of epigenetic drugs. The dynamic methylation shift as a resistance marker is also important.
  - **Interdisciplinary readership** Moderate. The topic is of interest to oncology, epigenetics, and structural biology communities. The clinical relevance is clear, but the direct applicability to a broad readership is limited by the specialized nature of the work.
  - **Technical soundness** Currently insufficient. The key claims are not fully supported by the presented data. The lack of peptide characterization, incomplete in vivo details, and the indirect nature of the mechanistic evidence are significant weaknesses.
  - **Readability for nonspecialists** The manuscript is generally well-written but uses specialized terminology. The logic is mostly clear, but the results section could be better structured to guide the reader through the evidence. The abstract is concise and accessible.
- **Recommendation posture** Currently not established from the provided evidence. The concept is promising and the work is potentially important, but the manuscript requires major revisions and additional experiments to address the blocking concerns. I would be supportive if the technical concerns are resolved.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that EXDDNMT1/ELK1 is a peptide that selectively disrupts the DNMT1/ELK1 interaction and induces DGKI demethylation.
- **Evidence pointer** Methods (peptide design), Results (Figure 2), location not provided
- **Concern** The manuscript does not provide sufficient characterization of the peptide EXDDNMT1/ELK1. The exact sequence, the cell-penetrating and nuclear localization sequences, and the control peptide (EXDctrl) are not described. There is no direct evidence that the peptide enters cells, localizes to the nucleus, and binds to the DNMT1/ELK1 interface as intended. The specificity of the peptide for the DNMT1/ELK1 interaction over other DNMT1 complexes is not demonstrated. The AlphaFold2 model is used to design the peptide, but the model confidence is only reported as a single score (82%) without the pTM and ipTM values, and the initial low-confidence prediction is not shown. The functional data (ChIP, methylation) are consistent with the hypothesis but do not prove that the peptide acts by disrupting the specific DNMT1/ELK1 interaction.
- **Why it matters** The entire premise of the study rests on the specificity and mechanism of action of this peptide. Without direct evidence of its binding, cellular uptake, and specificity, the conclusions cannot be validated. The peptide could be acting through off-target effects or non-specific disruption of protein-protein interactions.
- **Resolution test** Provide the full sequence and characterization of the peptide and control. Show direct binding data (e.g., pull-down, surface plasmon resonance, or cellular thermal shift assay) demonstrating that the peptide binds to the DNMT1/ELK1 interface. Demonstrate that the peptide disrupts the DNMT1/ELK1 interaction in cells (e.g., by co-immunoprecipitation). Show that a mutant or scrambled peptide does not have the same effect. Provide the pTM and ipTM scores for the AlphaFold2 model.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that EXDDNMT1/ELK1 enhances the anti-tumor effect of temozolomide in an in vivo PDX model.
- **Evidence pointer** Results (Figure 3B, 3C), Methods (In vivo experiments), location not provided
- **Concern** The in vivo experiment is described with insufficient detail. The number of mice per group is not stated. The method of randomization and blinding is not described. The statistical analysis for the tumor volume data is not specified. The tumor volume graph appears to show data from three distinct PDX models, but it is unclear if these are pooled or analyzed separately. The delivery method is intratumoral injection, which is not a clinically relevant route for a peptide therapeutic in glioblastoma, and the manuscript does not address the blood-brain barrier or systemic delivery. The figure shows a photograph of resected tumors, but it is unclear if this is representative. The claim that EXDDNMT1/ELK1 "prevents the acquisition of TMZ resistance" is based on a single in vitro experiment with A549 cells and is not validated in vivo.
- **Why it matters** The in vivo data are critical to support the therapeutic potential of the peptide. Without proper experimental design, sample sizes, and statistical analysis, the results are not reliable. The intratumoral delivery route limits the translational relevance of the findings.
- **Resolution test** Provide the number of mice per group, randomization and blinding procedures, and the statistical tests used. Show individual tumor growth curves for each mouse. Validate the findings in an orthotopic model with systemic delivery of the peptide. Provide a dose-response study.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the MGMTmethylated/DGKImethylated profile is a clinically relevant biomarker for poor response, and that DGKI methylation in cfcDNA can be used to monitor treatment response.
- **Evidence pointer** Results (Figure 1B, 4B, 4C, 4D, Supplementary Figure 5), location not provided
- **Concern** The clinical cohorts are very small (22 patients for survival, 15 for paired resections, 5 for cfcDNA monitoring, 18 for cfcDNA correlation). No power calculation is provided. The survival analysis is based on a small number of events. The classification of methylation status (methylated vs unmethylated) is based on a 50% cutoff, but the clinical validity of this cutoff is not established. The correlation between tumor DNA and cfcDNA methylation is based on a small cohort and the statistical method is not described. The claim that cfcDNA methylation can be used to identify patients who will benefit from treatment is speculative and not supported by the data, as no treatment decisions were made based on this biomarker.
- **Why it matters** The clinical relevance of the proposed biomarker is a key part of the manuscript's significance. The small sample sizes and lack of statistical rigor undermine the reliability of these conclusions. The cfcDNA data are preliminary and do not demonstrate clinical utility.
- **Resolution test** Validate the findings in a larger, independent cohort. Provide a pre-specified statistical analysis plan. Show that the cfcDNA methylation changes correlate with clinical outcomes (e.g., progression-free survival). Demonstrate that the biomarker can be used to guide treatment decisions in a prospective study.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that DGKI expression contributes to increased sensitivity to TMZ and irradiation-induced cell death.
- **Evidence pointer** Results (Figure 1C), location not provided
- **Concern** The evidence for this claim is based on a single experiment where DGKI is overexpressed in U251 cells. The effect of DGKI overexpression on cell death is shown, but the mechanism is not explored. It is not clear if the effect is specific to DGKI or if it is a general effect of overexpressing a protein. The authors do not show that knocking down DGKI in a DGKI-expressing cell line reduces sensitivity to TMZ/IR.
- **Why it matters** This is a central claim that links DGKI expression to treatment response. The evidence is correlative and does not establish a causal role for DGKI.
- **Resolution test** Perform loss-of-function experiments (e.g., siRNA or CRISPR) in DGKI-expressing cells to show that reducing DGKI expression decreases TMZ/IR sensitivity. Explore the downstream signaling pathways affected by DGKI expression.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that EXDDNMT1/ELK1 does not promote proliferation or invasion.
- **Evidence pointer** Results (Figure 3A), location not provided
- **Concern** The data for this claim are presented in a single figure panel. The assays used to measure proliferation (doubling time) and invasion are described, but the results are not shown in detail. It is not clear if the experiments were performed with appropriate controls. The claim that EXDDNMT1/ELK1 does not promote these phenotypes is important for its safety profile, but the evidence is limited.
- **Why it matters** A therapeutic agent that promotes tumor growth or invasion would be unsafe. The data supporting the lack of these effects are not presented in sufficient detail.
- **Resolution test** Provide the full data for the proliferation and invasion assays, including positive and negative controls. Show that the peptide does not affect these phenotypes in multiple cell lines.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states "EXDDNMT1/ELK1 did note promote cellular proliferation or invasion" which contains a typo ("note" should be "not").
- **Required correction** Correct the typo.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section
- **Evidence pointer** Results, Figure 1C, location not provided
- **Issue** The description of the PCTC-DGKI experiments is confusing. The text states "PCTC-dGB with an MGMTM/DGKIU signature were sensitive to TMZ/IR-induced cell death" but the figure legend is not clear about which cell lines correspond to which signature. The number of biological replicates is not stated.
- **Required correction** Clarify the figure legend and the text to clearly indicate which cell lines have which methylation signature and how many replicates were performed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section
- **Evidence pointer** Methods, Statistical analysis, location not provided
- **Issue** The statistical analysis section is very brief and does not specify which tests were used for which experiments. It is not clear if multiple testing corrections were applied.
- **Required correction** Provide a detailed description of the statistical tests used for each experiment, including corrections for multiple testing.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion, location not provided
- **Issue** The discussion mentions "the first proof-of-concept for an epimark/epidrug pairing" and "the first proof-of-concept for structure-guided design of an epidrug using AlphaFold2-predicted protein-protein interactions." These claims of priority are strong and should be supported by a thorough literature search or tempered.
- **Required correction** Soften the claims of priority or provide a more comprehensive review of the literature to support them.

## Risk / unsupported claims
- The claim that EXDDNMT1/ELK1 specifically disrupts the DNMT1/ELK1 interaction is not directly supported by binding or interaction data.
- The claim that the peptide's effects are due to selective DGKI demethylation is not fully established, as the authors do not rule out other off-target effects.
- The claim that the MGMTmethylated/DGKImethylated profile is a clinically relevant biomarker is based on a very small cohort and requires validation.
- The claim that cfcDNA methylation can be used to monitor treatment response and identify patients for therapy is speculative and not supported by the data.
- The claim that EXDDNMT1/ELK1 prevents the acquisition of TMZ resistance is based on a single in vitro experiment and is not validated in vivo.
- The in vivo efficacy data are not fully reported, and the intratumoral delivery route limits the translational relevance.