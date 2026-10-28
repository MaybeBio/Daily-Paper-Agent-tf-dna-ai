## Review setup
- **Input scope** Full manuscript text, including abstract, background, methods, results, discussion, and conclusions. Supplementary file descriptions are referenced but not provided.
- **Assessment boundary** The review assesses the scientific claims, methodological rigor, and interpretive validity of the in silico study as presented. It does not evaluate the choice of target protein or the clinical relevance of pirin beyond what is stated.
- **Shared manuscript claim summary** The authors report a comprehensive in silico analysis of 153 missense variants of human pirin, identifying 45 as uniformly pathogenic by five tools, and prioritizing seven variants (R59P, L116P, L220P, F78V, G98D, R59Q, V151D) for further experimental study based on predicted effects on stability, structure, metal binding, and protein–protein interactions across two redox-dependent conformations.
- **Visible evidence base** Main text tables (Tables 1–5), figures (Figs. 1–2), and referenced supplementary files (Additional files 1–3). No raw data, tool output files, or structural coordinates are provided.
- **Missing materials affecting confidence** Supplementary tables (S1–S3) are referenced but not available for inspection. No details on template selection, model quality metrics (e.g., QMEAN, GMQE), or validation of the pirin-BCL3 and pirin-p65 docking poses are provided. No information on the statistical significance or confidence intervals for the predicted ΔΔG values is given.

## Reviewer
- **Overall assessment** This manuscript presents a systematic and reasonably comprehensive in silico prioritization of missense variants in human pirin, with a useful focus on two redox-dependent conformations. The workflow is logical and the use of multiple prediction tools is appropriate for a screening study. However, the scientific impact is limited by the absence of experimental validation, the lack of detailed model quality assessment, and the reliance on consensus predictions without clear benchmarks. The claims regarding functional impact are plausible but remain speculative. The manuscript is technically sound in its execution but does not provide sufficient evidence to establish the biological significance of the prioritized variants beyond computational inference.
- **Who would be interested in the results, and why** Researchers studying pirin biology, NF-κB signaling, and redox-dependent protein function may find the prioritized variant list useful for designing targeted mutagenesis or clinical association studies. The work may also be of interest to those developing in silico variant prioritization pipelines, particularly for proteins with conformation-dependent functions. However, the audience is likely narrow and specialized.
- **Major strengths** The study addresses a relevant gap by considering two distinct pirin conformations, which is biologically meaningful given the redox-dependent role of the iron cofactor. The use of five pathogenicity tools and five stability tools, with explicit consensus criteria, strengthens the reliability of the prioritization. The inclusion of protein–protein interaction predictions and dynamics simulations adds functional context. The haplotyping analysis is a useful addition for population-level interpretation.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that the 3D models of pirin in Fe2+ and Fe3+ bound states are reliable and suitable for downstream analyses, and that the docking poses for pirin-BCL3 and pirin-p65 are valid.
  - **Evidence pointer** Methods section "Determination of the effects of missense variants on the stability of pirin protein"; Results section "Effects of missense variants on protein–protein interactions"; Figure 1
  - **Concern** The manuscript does not report any model quality metrics (e.g., GMQE, QMEAN, MolProbity scores) for the SWISS-MODEL-generated structures, nor any validation of the docking poses from HDOCK. Without these, the structural basis for the predicted effects on stability, metal binding, and protein–protein interactions is not established. The authors also do not state whether the templates (1J1L and 4GUL) cover the full-length protein or only a domain, which could affect the interpretation of variant effects in the C-terminal region.
  - **Why it matters** The entire downstream analysis, including mCSM, DeepDDG, Missense3D, and mCSM-PPI2 predictions, depends on the accuracy of the input structures. If the models are of low quality or the docking poses are incorrect, the predicted ΔΔG values and structural damage calls are unreliable, undermining the prioritization of variants.
  - **Resolution test** Provide model quality metrics for all generated structures, including global and per-residue scores. Include a validation of the docking poses (e.g., comparison with known interface residues, docking scores, or re-docking of a positive control). If the templates are partial, state the coverage and discuss how missing regions might affect predictions.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Scientific importance
  - **Claim pointer** The authors conclude that seven variants (R59P, L116P, L220P, F78V, G98D, R59Q, V151D) should be prioritized for further experimental studies, implying these are the most likely to be functionally relevant.
  - **Evidence pointer** Results sections "Pathogenicity of the missense variants", "Determination of the effects of missense variants on the stability of pirin protein", "Structural changes caused by the potentially pathogenic variants", "Effects of missense variants on protein–protein interactions"; Discussion section
  - **Concern** The prioritization is based entirely on computational predictions without any experimental validation or comparison to known functional data. The authors do not discuss whether any of these variants have been previously reported in disease cohorts or functional assays. The criteria for "significant" effects (e.g., ΔΔG < −1 kcal/mol by at least four tools) are arbitrary and not benchmarked against experimental measurements. The biological relevance of the prioritized variants is therefore not established.
  - **Why it matters** The stated goal is to prioritize variants for experimental follow-up. Without any external validation or evidence that the computational predictions correlate with functional outcomes, the list may misdirect resources. The study does not demonstrate that the prioritized variants are more likely to be pathogenic than those not selected.
  - **Resolution test** Compare the prioritized variants against known disease-associated variants in ClinVar or other databases. Include a discussion of any experimental evidence for these variants. If none exists, temper the conclusions to reflect that the list is hypothesis-generating only.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The authors state that the haplotyping analysis shows no haplotype harboring more than one missense variant, and therefore combinatorial effects need not be explored.
  - **Evidence pointer** Results section "Haplotyping of the variants"; Table 5
  - **Concern** The haplotyping analysis is based on a limited set of SNPs with MAF > 0.001 from dbSNP, but the methodology for selecting these SNPs and the LD calculation parameters are not fully described. The absence of haplotypes with multiple missense variants may be an artifact of the SNP selection criteria or the reference population used. The conclusion that combinatorial effects are unlikely is therefore not robustly supported.
  - **Why it matters** If the analysis missed rare or population-specific haplotypes with multiple variants, the conclusion could be misleading. The authors' recommendation to focus only on individual variant effects may be premature.
  - **Resolution test** Provide details on the SNP selection process, LD thresholds, and population reference panels used. Consider including rare variants (MAF < 0.001) or using a more comprehensive haplotype estimation method. If the conclusion remains unchanged, state the limitations explicitly.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Abstract and Introduction
  - **Evidence pointer** Abstract; Background section
  - **Issue** The abstract and introduction assume familiarity with in silico prediction tools and protein structure concepts. Terms such as "cupin superfamily," "redox sensor," and "missense variants" are used without brief definitions, which may limit accessibility for readers outside structural biology or genomics.
  - **Required correction** Add brief explanations of key terms in the introduction and abstract, or provide a glossary. For example, define "missense variant" and explain why conformational differences matter for pirin function.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods section "Simulation of the dynamics of pirin variants"
  - **Evidence pointer** Methods section; Figure 2
  - **Issue** The CABS coarse-grained simulation is described as a "proper alternative" to all-atom molecular dynamics, but no justification is given for this claim in the context of this study. The choice of simulation length, temperature, and number of replicas is not reported.
  - **Required correction** Provide a brief justification for using CABS over all-atom MD, and report the simulation parameters (e.g., number of cycles, temperature, number of independent runs). If these details are not available, state that the simulations were exploratory.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Scientific importance
  - **Affected element** Discussion section
  - **Evidence pointer** Discussion section
  - **Issue** The discussion does not address the limitations of the in silico approach, such as the potential for false positives/negatives in pathogenicity prediction or the inability to capture post-translational modifications and cellular context.
  - **Required correction** Add a limitations paragraph acknowledging these issues and suggesting how they might be addressed in future work (e.g., experimental validation, inclusion of additional prediction tools).
- **Technical failings that need to be addressed before the case is established** R1-M1 (model quality and docking validation) and R1-M2 (lack of external validation for prioritized variants) are the primary technical issues. Without addressing these, the central claims of the manuscript are not fully supported.
- **Assessment against Nature-style criteria**  
  *Originality*: Moderate. The study applies established in silico tools to a specific protein, but the approach is not methodologically novel. The consideration of two conformations is a minor differentiator.  
  *Scientific importance*: Limited. The findings are hypothesis-generating and may be useful for the pirin research community, but the lack of experimental validation and the absence of disease association data reduce the significance.  
  *Interdisciplinary readership*: Narrow. The work is primarily relevant to computational biologists and researchers studying pirin or NF-κB signaling. It is unlikely to attract a broad readership.  
  *Technical soundness*: The workflow is logical and the use of multiple tools is appropriate, but the lack of model quality assessment and docking validation is a significant gap.  
  *Readability for nonspecialists*: The manuscript is generally clear but assumes familiarity with in silico prediction methods. Some terms and concepts could be better explained.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a reasonable computational screening, but the lack of model validation, external benchmarking, and experimental context prevents the conclusions from being fully supported. The authors should address the major concerns, particularly R1-M1 and R1-M2, before the case for prioritizing these variants is convincing.

## Risk / unsupported claims
- The claim that the seven prioritized variants are the most likely to be functionally relevant is unsupported without external validation or benchmarking against known functional data.
- The claim that the absence of haplotypes with multiple missense variants indicates combinatorial effects are unlikely is not robustly supported due to incomplete methodological details.
- The claim that the CABS simulation is a "proper alternative" to all-atom MD is not justified with specific evidence or parameters.
- The claim that the study is "the most comprehensive exploration of the effects of pirin missense variants so far" is not verifiable from the provided evidence, as no systematic comparison to prior studies is presented.