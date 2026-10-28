## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose that light exposure increases cuticular wax terpenoid content in grape berries, reducing decay and abscission rates. They identify VvTPS12 and VvHMGR2 as biosynthetic targets and VvHYH and VvGATA24 as transcriptional activators, supported by ATAC-seq, RNA-seq, transient overexpression, dual luciferase assays, surface plasmon resonance, and molecular docking.
- **Visible evidence base** Abstract text only; no numerical data, statistical details, experimental replicates, or methodological specifics beyond those named in the abstract
- **Missing materials affecting confidence** Full text, all figures and tables, supplementary datasets, statistical analyses, experimental protocols, and raw sequencing data

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting mechanism linking light signaling to wax terpenoid biosynthesis in grape, with a plausible regulatory model involving two transcription factors and two target genes. However, the evidence as summarized is insufficient to fully evaluate the robustness of the claims. Key quantitative details, statistical support, and experimental controls are not visible. The molecular interaction data are promising but require confirmation of specificity and functional relevance in stable contexts.
- **Who would be interested in the results, and why** Researchers in plant cuticular wax biology, light signaling, terpenoid metabolism, and fruit postharvest physiology would find these results relevant. The work may also interest those studying transcriptional regulation of secondary metabolism and those applying chromatin accessibility approaches to non-model crops. The potential for breeding applications in grape and other fruit crops adds practical relevance.
- **Major strengths** The integration of ATAC-seq and RNA-seq to identify regulatory elements is a modern and appropriate approach. The combination of qualitative and quantitative binding assays, including surface plasmon resonance with reported dissociation constants, strengthens the interaction claims. The use of transient overexpression in both grape berries and Nicotiana benthamiana provides cross-species validation. The identification of specific amino acid residues involved in DNA binding via molecular docking adds mechanistic depth.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** Light exposure resulted in higher wax terpenoid content and lower decay and abscission rates than controls kept in darkness.
  - **Evidence pointer** Abstract, first paragraph; location not provided
  - **Concern** The abstract states that light exposure increased wax terpenoid content and reduced decay and abscission rates, but no quantitative data, effect sizes, statistical significance values, or replicate numbers are provided. It is unclear whether these differences are robust across biological replicates, developmental stages, or environmental conditions.
  - **Why it matters** This is the foundational phenotypic claim linking light to wax accumulation and postharvest outcomes. Without statistical support, the reader cannot assess whether the observed effects are reproducible or biologically meaningful.
  - **Resolution test** Provide mean values with standard errors or confidence intervals, sample sizes, statistical tests used, and p-values or equivalent measures for the light versus dark comparisons.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** VvHYH and VvGATA24 were identified as terpenoid biosynthesis activators, as more abundant wax crystals and higher wax terpenoid content were observed in transiently overexpressed grape berries and Nicotiana benthamiana leaves.
  - **Evidence pointer** Abstract, second paragraph; location not provided
  - **Concern** The abstract claims that overexpression of VvHYH and VvGATA24 increases wax crystals and terpenoid content, but no quantitative data, fold changes, or statistical comparisons are shown. The transient nature of the overexpression and the lack of loss-of-function experiments limit the strength of the activation claim.
  - **Why it matters** The functional assignment of these transcription factors as activators is central to the proposed model. Without quantitative phenotypic data and ideally complementary knockdown or mutant analysis, the claim remains correlative.
  - **Resolution test** Provide quantitative measurements of wax crystal density or coverage and terpenoid content with statistical comparisons between overexpression and control samples. Include loss-of-function data if available, or clearly state their absence as a limitation.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** VvHYH bound to the open chromatin of VvTPS12 with an equilibrium dissociation constant of 2.81 nm, and VvGATA24 bound to the open chromatin of VvHMGR2 with an equilibrium dissociation constant of 8.59 nm.
  - **Evidence pointer** Abstract, third paragraph; location not provided
  - **Concern** The surface plasmon resonance data are reported as single dissociation constant values without indication of replicates, error estimates, or experimental conditions. The dual luciferase assay is described only as qualitative. The molecular docking results are presented without validation of the predicted binding interfaces through mutagenesis or other functional tests.
  - **Why it matters** Binding affinity values are only meaningful with associated error and replicate information. The qualitative nature of the dual luciferase assay and the lack of mutagenesis validation weaken the claim that these interactions are specific and functionally relevant in vivo.
  - **Resolution test** Provide dissociation constants with standard deviations and replicate numbers, describe the surface plasmon resonance experimental conditions, and include mutagenesis data for the predicted amino acid residues to confirm their functional role in binding.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Terminology
  - **Evidence pointer** Abstract, first paragraph; location not provided
  - **Issue** The term "wax terpenoid" is used repeatedly but not defined. It is unclear whether this refers to terpenoid components within the cuticular wax mixture or a specific class of terpenoid wax compounds.
  - **Required correction** Define "wax terpenoid" explicitly in the abstract or introduction, specifying the chemical class and how it was measured.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Experimental scope
  - **Evidence pointer** Abstract, second paragraph; location not provided
  - **Issue** The abstract does not mention whether the identified transcription factors are light-responsive in their expression or activity. The title implies light responsiveness, but the abstract does not directly demonstrate that VvHYH or VvGATA24 respond to light.
  - **Required correction** Add a statement or data showing that VvHYH and VvGATA24 expression or activity changes with light exposure, or revise the title to avoid overclaiming.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods description
  - **Evidence pointer** Abstract, third paragraph; location not provided
  - **Issue** The molecular docking simulation is mentioned but no software, scoring function, or validation approach is described. This limits reproducibility.
  - **Required correction** Provide details of the docking method in the full manuscript and cite the software used. If space permits, include a brief note in the abstract or refer to methods.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The phenotypic and functional claims lack quantitative statistical support, and the binding data require replicate information and functional validation.
- **Assessment against Nature-style criteria**  
  Originality: The work appears to offer a novel link between light signaling and wax terpenoid biosynthesis via specific transcription factors, which is not well established in the literature. The use of ATAC-seq in grape is a methodological contribution.  
  Scientific importance: The findings could have implications for understanding cuticular wax regulation and for improving postharvest quality in grape and other fruits. The importance is moderate to high within plant biology, though the abstract does not fully demonstrate the breadth of impact.  
  Interdisciplinary readership: The topic is primarily of interest to plant molecular biologists, biochemists, and postharvest physiologists. The abstract is unlikely to attract a broad interdisciplinary audience beyond these fields.  
  Technical soundness: The combination of chromatin accessibility, transcriptomics, binding assays, and docking is technically sound in principle. However, the abstract lacks the quantitative and statistical detail needed to assess technical rigor.  
  Readability for nonspecialists: The abstract is reasonably clear but uses specialized terms without definition, which may limit accessibility for readers outside plant molecular biology.
- **Recommendation posture** Supportive if technical concerns are resolved. The proposed model is plausible and the methodological approach is appropriate, but the current abstract does not provide sufficient quantitative evidence to fully establish the claims. The authors should address the statistical and validation gaps before the case is considered robust.

## Risk / unsupported claims
- The claim that light exposure reduces decay and abscission rates is unsupported by quantitative data in the abstract.
- The functional assignment of VvHYH and VvGATA24 as activators is supported only by transient overexpression without quantitative phenotypic data or loss-of-function evidence.
- The binding affinities reported as single values without error or replicate information are not fully evaluable.
- The molecular docking predictions of specific amino acid residues are not validated experimentally.
- The light responsiveness of VvHYH and VvGATA24 is implied by the title but not demonstrated in the abstract.