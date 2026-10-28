## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, experimental procedures, and figure legends
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical soundness as presented in the provided manuscript
- **Shared manuscript claim summary** The authors report that colorectal cancer-associated hotspot mutations at PCBP1 residues L100/L102 destabilize the protein, disrupt KH1-KH2 domain interactions, cause cytoplasmic mislocalization, and act in a dominant-negative manner to suppress wild-type PCBP1 expression
- **Visible evidence base** Figures 1-7, supplementary figures S1-S5, tables S1-S2, and associated legends as described in text
- **Missing materials affecting confidence** Actual figure images, supplementary data files, raw western blot images, statistical output details, and MD simulation trajectory data were not provided for direct inspection

## Reviewer

### Overall assessment
This manuscript addresses an important and timely question regarding the functional consequences of recurrent PCBP1 mutations in colorectal cancer. The authors present a coherent narrative from genomic observation to mechanistic characterization, including protein stability, conformational dynamics, subcellular localization, and dominant-negative effects. The work is potentially significant for understanding tumor suppressor inactivation in CRC. However, several technical concerns regarding the rigor of the evidence, particularly around the dominant-negative mechanism, quantification methods, and the interpretation of MD simulation data, need to be addressed before the conclusions are fully supported.

### Who would be interested in the results, and why
Cancer biologists studying tumor suppressor inactivation mechanisms, researchers focused on RNA-binding proteins in cancer, colorectal cancer genomics community, and investigators interested in dominant-negative mutations as a mode of tumor suppressor loss. The findings may also be relevant to clinical researchers developing biomarkers or therapeutic strategies targeting PCBP1-mutant tumors.

### Major strengths
1. The study addresses a clinically relevant and understudied question about recurrent PCBP1 hotspot mutations in CRC
2. The combination of public database analysis, cell-based assays, and computational modeling provides a multi-pronged approach
3. The use of CRISPR-edited cell lines with endogenous heterozygous mutations adds physiological relevance
4. The demonstration of dominant-negative effects on wild-type PCBP1 expression is a novel finding with potential broad implications
5. The authors include appropriate controls such as RNAse treatment in co-IP experiments and stable mutants (L100I/V) as negative controls

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of dominant-negative evidence
- **Claim pointer** "mutant PCBP1 physically interacts with wild type PCBP1 and suppresses its expression through a dominant-negative mechanism"
- **Evidence pointer** Figures 6 and 7, location not provided
- **Concern** The co-transfection experiments show that increasing amounts of mutant PCBP1 decrease HA-tagged wild-type PCBP1 levels. However, the total amount of PCBP1 protein (both Flag-tagged mutant and HA-tagged wild-type) in these experiments is not clearly reported. If the Flag-tagged mutant is expressed at much higher levels than the HA-tagged wild-type, the apparent "suppression" could reflect competition for limiting cellular resources (e.g., chaperones, translation machinery) rather than a specific dominant-negative interaction. Additionally, the authors state that plasmid amounts were adjusted based on Figure 4B to achieve similar expression levels, but the logic of this adjustment is unclear since Figure 4B shows total PCBP1 levels in CRISPR lines, not Flag-tagged plasmid expression levels.
- **Why it matters** The dominant-negative mechanism is the central novel claim of the manuscript. If the effect is due to nonspecific overexpression artifacts, the conclusion would be substantially weakened.
- **Resolution test** Provide quantification of total PCBP1 levels (both tagged forms) in the co-transfection experiments. Include a control where an unrelated Flag-tagged protein (e.g., Flag-GFP) is co-transfected at similar levels to rule out nonspecific effects. Show that the dominant-negative effect is dose-dependent and specific to the mutant forms.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of MD simulation interpretation
- **Claim pointer** "our molecular dynamics simulations show that mutations at these residues disrupt the secondary structure of PCBP1"
- **Evidence pointer** Figure 2C, location not provided
- **Concern** The MD simulations were performed using the PCBP2 KH1-KH2 structure (PDB 2JZX) as a model for PCBP1, which the authors acknowledge. However, the RMSF analysis measures inter-domain flexibility, not secondary structure disruption per se. The claim of "disrupted secondary structure" is not directly supported by the RMSF metric described. Furthermore, the correlation between RMSF and protein expression levels (Figure 2C) is presented without statistical analysis, and the relationship appears to be driven largely by the wild-type and stable mutants versus the destabilized ones, which may be a binary distinction rather than a graded correlation.
- **Why it matters** The MD simulations are used to provide a mechanistic rationale for the observed stability differences. If the simulations do not actually demonstrate secondary structure disruption, the mechanistic interpretation is overstated.
- **Resolution test** Provide additional MD analyses that directly assess secondary structure content over time (e.g., DSSP analysis) for wild-type and mutants. Report correlation coefficients and p-values for the RMSF-expression relationship. Clarify whether the RMSF differences are statistically significant across replicate trajectories.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Evidence quality for protein stability mechanism
- **Claim pointer** "cancer-associated mutations substituting leucine 100 and 102 with glutamine, proline, or arginine destabilize PCBP1"
- **Evidence pointer** Figures 2B, 4B, 4D-F, S1A, location not provided
- **Concern** The cycloheximide chase experiments show reduced half-life of PCBP1 in the L100Q/WT cells, but the authors do not directly demonstrate that the mutant protein itself is degraded. Since the antibody used for PCBP1 detection likely recognizes both wild-type and mutant forms, the reduced total PCBP1 levels could reflect degradation of the mutant protein, the wild-type protein, or both. The authors acknowledge this ambiguity in the discussion but do not provide experiments to distinguish between these possibilities. Additionally, the partial rescue with MG132 and bortezomib is not complete, suggesting other degradation pathways may be involved, but this is not explored.
- **Why it matters** The claim of mutant protein destabilization is central to the paper. Without distinguishing mutant from wild-type protein degradation, the mechanism remains incompletely defined.
- **Resolution test** Use a mutant-specific antibody or epitope tag to track mutant protein stability specifically. Alternatively, perform cycloheximide chase experiments with tagged constructs to compare wild-type and mutant protein half-lives directly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of findings
- **Claim pointer** "PCBP1 mutations have been recurrently reported in CRC genome-wide mutation studies and are associated with poor clinical outcomes"
- **Evidence pointer** Figure 1, location not provided
- **Concern** The analysis is based on cBioPortal data from a single database query. The authors report 77 PCBP1 mutations in CRC with 66 at L100/L102, but the total number of CRC samples queried is not stated, making it difficult to assess the true frequency of these mutations. The clinical outcome association is cited from prior literature (references 31, 32) but not directly analyzed here. The functional studies are limited to one CRC cell line (HCT116) and one murine line (MC38).
- **Why it matters** The clinical relevance and generalizability of the findings depend on the prevalence and significance of these mutations across the broader CRC patient population.
- **Resolution test** Report the total number of CRC samples in the cBioPortal query and the percentage of samples with L100/L102 mutations. Consider validating key findings in additional CRC cell lines or patient-derived models.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 2C
- **Evidence pointer** Figure 2C, location not provided
- **Issue** The y-axis label "relative root mean square fluctuation" is unclear. It is not specified relative to what baseline, and the units are not clearly indicated.
- **Required correction** Clarify the y-axis label, specify the reference state for "relative" RMSF, and indicate units.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Multiple figures
- **Evidence pointer** Figures 2B, 3B-C, 4B, 5A-B, location not provided
- **Issue** While p-values are indicated for some comparisons, effect sizes, confidence intervals, and exact n values for each experiment are not consistently reported.
- **Required correction** Provide effect sizes and confidence intervals where feasible, and clearly state n for each experiment in figure legends.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** MD simulation setup
- **Evidence pointer** Experimental procedures, location not provided
- **Issue** The description of the MD simulation setup lacks details on the number of replicates, total simulation time per replicate, and convergence criteria used.
- **Required correction** Provide these details to allow reproducibility and assessment of sampling adequacy.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of stress granule data
- **Affected element** Figure 5C-C'
- **Evidence pointer** Figure 5C-C', location not provided
- **Issue** The co-localization with G3BP1 is interpreted as stress granule localization, but the authors do not confirm stress granule induction conditions or provide evidence that these are bona fide stress granules rather than other G3BP1-positive structures.
- **Required correction** Clarify whether stress granules were induced and under what conditions, or temper the interpretation to "G3BP1-positive cytoplasmic puncta."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness of clinical data
- **Affected element** Figure 1
- **Evidence pointer** Figure 1, location not provided
- **Issue** The variant allele frequency data (Figure 1C) is presented as a range (0.3-0.5) but the number of samples with available VAF data and the distribution of VAFs is not shown.
- **Required correction** Provide a more detailed representation of VAF distribution, including sample numbers.

### Technical failings that need to be addressed before the case is established
R1-M1 (dominant-negative evidence), R1-M2 (MD simulation interpretation), and R1-M3 (mutant-specific stability) are the primary technical concerns that must be resolved. The current evidence is suggestive but not fully conclusive for the dominant-negative mechanism as the primary mode of action.

### Assessment against Nature-style criteria
- **Originality** The work is original in its focus on PCBP1 hotspot mutations and the proposed dominant-negative mechanism. While dominant-negative mutations are known for other tumor suppressors, this is a novel finding for PCBP1 in CRC.
- **Scientific importance** The findings have potential importance for understanding how PCBP1 mutations contribute to CRC, particularly given the recurrent nature of these mutations and their association with poor outcomes. The dominant-negative mechanism represents a distinct mode of tumor suppressor inactivation that could have therapeutic implications.
- **Interdisciplinary readership** The work bridges cancer genomics, protein biochemistry, and computational biology, making it of interest to multiple communities. However, the clinical translation aspects are limited.
- **Technical soundness** The experimental design is generally sound, but the concerns raised above regarding the dominant-negative evidence, MD simulation interpretation, and mutant-specific stability need to be addressed. The use of multiple cell lines and appropriate controls is commendable.
- **Readability for nonspecialists** The manuscript is generally well-written and accessible, though some sections (particularly the MD simulation description) may be challenging for non-computational readers. The figures are well-designed and support the narrative.

### Recommendation posture
Supportive if technical concerns are resolved. The manuscript addresses an important question and presents a coherent story, but the central claims regarding the dominant-negative mechanism and the molecular basis of destabilization require additional experimental support and clarification. The authors should be encouraged to address the concerns raised, particularly R1-M1, R1-M2, and R1-M3, through additional experiments and analyses.

## Risk / unsupported claims
1. The claim that MD simulations show "disrupted secondary structure" is not directly supported by the RMSF analysis described; this is an overinterpretation of the data presented.
2. The claim that the dominant-negative effect is specific to PCBP1 biology ("this phenomenon is likely unique to PCBP1 biology") is not fully supported, as only a limited number of related proteins were tested.
3. The statement that "PCBP1 mutations have been recurrently reported in CRC genome-wide mutation studies and are associated with poor clinical outcomes" relies on prior literature citations rather than direct analysis in this manuscript.
4. The assertion that the cytoplasmic puncta are stress granules is based on G3BP1 co-localization alone; additional markers or functional assays would strengthen this claim.
5. The conclusion that "CRC-associated PCBP1 mutations destabilize the protein and act as dominant-negative variants, revealing a novel mechanism of tumor suppressor inactivation" is partially supported but requires the additional experiments outlined in R1-M1 and R1-M3 to be fully established.