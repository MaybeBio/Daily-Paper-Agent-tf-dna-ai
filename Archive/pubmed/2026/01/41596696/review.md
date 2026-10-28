## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods, conclusions)
- **Assessment boundary** Computational design and in silico characterization of a Cas12j2-based gene editing system targeting HPV E6; no experimental validation data are presented
- **Shared manuscript claim summary** The authors report the rational in silico design of a Cas12j2 fusion construct (F2) with N- and C-terminal modifications, dual gRNA selection against HPV-16 E6, and computational evaluation of structural stability, gRNA binding, off-target potential, and pH sensitivity using ColabFold, CCTop, Cas-OFFinder, HADDOCK 2.4, and Amber MD simulations. They claim the F2 variant behaves similarly to wild-type Cas12j2 in structural metrics and is suitable for future in vitro validation.
- **Visible evidence base** Figures 1–11; Supplemental Figures S1–S17; Tables 1–4; Supplemental Table S1; Methods sections 4.1–4.9
- **Missing materials affecting confidence** Raw MD trajectory data, docking pose coordinates, per-replicate numerical values for RMSD/RMSF/Rg/BSA/H-bond metrics, gRNA target site coordinates within E6, off-target hit lists, plasmid maps, and any code or parameter files. No experimental validation is included.

## Reviewer
- **Overall assessment** This manuscript presents a purely computational pipeline for designing a Cas12j2-based gene editing system against HPV-16 E6. The work is methodical and the use of multiple established in silico tools is appropriate. However, the scientific advance is incremental: the F2 construct differs from F1 only by two additional N-terminal NLS sequences, and the core claims of "enhanced stability" and "theoretical optimal nuclear trafficking" are not supported by quantitative evidence presented in the manuscript. The off-target analysis is descriptive rather than quantitative, and the MD results are reported as ranges without statistical treatment. The manuscript would benefit from clearer presentation of numerical data, explicit comparison metrics, and a more cautious interpretation of what computational predictions can establish without experimental validation.
- **Who would be interested in the results, and why** Researchers working on compact CRISPR-Cas systems for therapeutic applications, particularly those interested in Cas12j family engineering, computational prediction of gRNA efficacy, and in silico pre-screening of gene editing constructs before wet-lab validation. The framework may be of interest to computational biologists developing pipelines for rational design of gene editing systems.
- **Major strengths** 1) Use of experimentally validated Cas12j2-gRNA interface residues to constrain docking, which increases biological relevance. 2) Multi-tool approach (ColabFold, CCTop, Cas-OFFinder, HADDOCK, Amber) covering structure prediction, off-target analysis, docking, and MD. 3) Consideration of pH conditions relevant to intracellular trafficking. 4) Clear description of the vector design strategy for future in vitro work.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (no quantitative comparison of F2 vs WT), R1-M2 (no statistical treatment of MD replicates), R1-M3 (off-target analysis lacks quantitative thresholds), R1-M4 (pH methodology unclear and potentially circular)
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The application of existing computational tools to a specific Cas12j2 variant is not conceptually novel. The F2 design is an incremental modification of a previously published F1 construct.  
  *Scientific importance*: Limited at present. The manuscript provides a computational framework but no experimental validation, and the clinical relevance to HPV-associated cancers is asserted rather than demonstrated.  
  *Interdisciplinary readership*: Narrow. The work is primarily of interest to computational biologists and CRISPR engineering specialists; the therapeutic claims would require substantial experimental support to attract a broader oncology audience.  
  *Technical soundness*: Partially adequate. The use of established tools is appropriate, but the lack of quantitative reporting, statistical analysis, and clear methodological details for pH-dependent protonation undermines the robustness of the conclusions.  
  *Readability for nonspecialists*: Acceptable but could be improved. The introduction and discussion are accessible, but the results section relies heavily on tool-specific terminology without sufficient context for readers unfamiliar with computational structural biology.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a reasonable computational workflow, but the central claims of enhanced stability and therapeutic potential are not supported by the quantitative data presented. Major revisions addressing the concerns below are required before the case is established.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence quality  
- **Claim pointer** The authors claim that "Cas12j2_F2, a Cas12j2 variant designed and evaluated in this study, behaves similarly to the wild-type Cas12j2 structure in terms of RMSD/RMSF profiles, compact Rg values, and minimal electrostatic perturbation" (Abstract) and that F2 "performed closer to the wild type than Cas12j2_F1" (Section 3.4).  
- **Evidence pointer** Section 2.5, Figures 5–11, Table 4  
- **Concern** The manuscript does not provide quantitative numerical values for RMSD, RMSF, Rg, BSA, or H-bond occupancy for any of the three variants. Figures 5–7 show representative plots, but no mean values, standard deviations, or statistical comparisons are reported in the text or tables. Table 4 reports HADDOCK scores but only as averages without dispersion measures. The claim that F2 "behaves similarly" to WT is therefore not quantitatively supported.  
- **Why it matters** Without numerical data and statistical comparison, the reader cannot assess whether F2 is statistically indistinguishable from WT, or merely within a broad range. The central claim of the manuscript depends on this comparison.  
- **Resolution test** Provide a supplementary table with mean ± SD for RMSD, RMSF, Rg, BSA, and ΣFrac for each variant at each pH, with appropriate statistical tests (e.g., ANOVA or permutation tests) comparing F2 to WT and F1.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim pointer** The authors state that "reported values represent the mean across three independent replicates" (Section 4.7).  
- **Evidence pointer** Section 4.7, Figures 5–11  
- **Concern** The manuscript states that three independent MD replicates were performed, but no per-replicate data, error bars, or measures of variability are shown in any figure or table. The reader cannot verify the consistency of the simulations or assess the uncertainty in the reported metrics.  
- **Why it matters** MD simulations are stochastic and sensitive to initial velocities. Without reporting variability, the robustness of the conclusions cannot be evaluated, and the results are not reproducible by other groups.  
- **Resolution test** Include per-replicate values in supplementary materials, add error bars or shaded regions to figures, and report the range or SD for all quantitative metrics.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence quality  
- **Claim pointer** The authors claim that gRNA5 and gRNA3 were selected because they "outperformed" other candidates based on off-target analysis (Section 3.3).  
- **Evidence pointer** Section 2.2, Tables 2–3  
- **Concern** The off-target analysis is presented descriptively. The manuscript does not provide a clear quantitative threshold for what constitutes an acceptable off-target profile. For example, gRNA5 for the 5' target has 1,083 DNA-mismatch off-targets at 4 mismatches and 13,511 RNA-mismatch off-targets, yet is selected. The rationale for why these numbers are acceptable is not stated. Additionally, the total number of off-targets for gRNA3 (3,542 in CCTop) is the highest among 3' candidates, yet it is selected. The decision criteria are not transparent.  
- **Why it matters** Off-target potential is a critical safety parameter for any therapeutic gene editing system. Without explicit thresholds or a scoring framework, the selection of gRNAs appears arbitrary and cannot be independently evaluated.  
- **Resolution test** Define a priori criteria for gRNA selection (e.g., maximum number of exonic off-targets, maximum total off-targets, minimum efficacy score) and show how the selected gRNAs meet these criteria. Provide the full off-target lists as supplementary data.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodology  
- **Claim pointer** The authors state that "pH-related differences should be interpreted relative to the assigned protonation states" (Section 4.5) and that pH conditions of 4–8 were tested.  
- **Evidence pointer** Section 4.5, Section 2.5, Figures 5–11  
- **Concern** The methodology for generating pH-specific protonation states is not described. The authors state that pdb2pqr was used, but do not specify which force field parameters, titration methods, or pH-dependent assignments were used. More critically, the manuscript does not explain why pH 4 and 5 are relevant to "potential intracellular conditions" when the physiological pH of the cytosol and nucleus is approximately 7.4. The authors acknowledge this in Section 3.4 but do not justify the inclusion of acidic conditions beyond a brief mention of "transient" exposure during trafficking.  
- **Why it matters** The pH range tested is central to the claim of environmental robustness. If the methodology for protonation is not reproducible, and if the relevance of acidic pH is not justified, the pH-dependent conclusions are not interpretable.  
- **Resolution test** Provide a detailed description of the protonation protocol, including software parameters and any validation steps. Justify the pH range with reference to the endosomal/lysosomal pathway or other relevant biology, and clarify whether the fixed protonation states are intended to model kinetic or thermodynamic stability.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Section 2.1, Figure 1  
- **Evidence pointer** Figure 1, Supplemental Figures S1–S2  
- **Issue** The text states that "AlphaFold2 first shows the associated multiple sequence alignment (MSA)" but does not explain what this means in practical terms. The MSA is not shown in any figure.  
- **Required correction** Clarify what is meant by "shows the MSA" and either include the MSA in supplementary material or remove the statement.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Section 2.2, Table 1  
- **Evidence pointer** Table 1  
- **Issue** Table 1 lists potential gRNA target sites but does not include the genomic coordinates or the exact position within the E6 gene. This limits the utility of the table for replication.  
- **Required correction** Add genomic coordinates (GRCh37/hg19) and the position within the E6 open reading frame for each gRNA target site.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** Section 3.4, HADDOCK scores  
- **Evidence pointer** Table 4  
- **Issue** The HADDOCK scores for F1 (108 and 95.6) are substantially higher than WT (30s), yet the text interprets this as "significantly higher" without discussing whether such differences are within the expected variability of HADDOCK scoring.  
- **Required correction** Provide context for interpreting HADDOCK score differences, such as reference values from the software documentation or published benchmarks, and discuss whether the observed differences are likely to be biologically meaningful.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Section 4.9, Vector design  
- **Evidence pointer** Section 4.9  
- **Issue** The description of the vector design mentions "a 50-nt non-coding sequence was included to separate the two-gRNA expression cassettes" but does not specify the rationale for this length or whether any functional testing was performed.  
- **Required correction** Briefly justify the choice of spacer length or cite literature supporting its use.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Presentation  
- **Affected element** Section 2.5.4, Electrostatic analysis  
- **Evidence pointer** Figures 8–9  
- **Issue** The electrostatic analysis is described qualitatively ("no detectable shift", "substantial pH-dependent variation") without any quantitative metric to support these statements.  
- **Required correction** Provide a quantitative measure of electrostatic difference (e.g., surface potential RMSD between pH conditions) or state clearly that the analysis is qualitative and should be interpreted as such.

## Risk / unsupported claims
- The claim that F2 has "enhanced stability" relative to F1 or WT is not supported by quantitative data.
- The claim that four SV40 NLS sequences "will theoretically ensure optimal trafficking to the nucleus" is speculative and not supported by any nuclear localization prediction or experimental data.
- The claim that the system has "therapeutic potential" for HPV-associated cancers is asserted without any functional validation, delivery efficiency data, or in vivo evidence.
- The statement that gRNA5 and gRNA3 have "low potential for off-target effects" is not supported by explicit thresholds or comparative benchmarks.
- The relevance of pH 4–5 conditions to intracellular trafficking is asserted but not justified with biological evidence.
- The claim that "each successfully transduced target cell would receive both components of the gene editing system" is presented as a design feature but is not experimentally verified.