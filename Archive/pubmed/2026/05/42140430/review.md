## Review setup
- **Input scope** Full manuscript text including abstract, results, experimental procedures, and supporting information descriptions
- **Assessment boundary** Functional characterization of UHRF1 variants in DNA methylation rescue assays, including ICF-associated mutations, epitope tagging effects, isoform 2 activity, and structural predictions
- **Shared manuscript claim summary** The authors report that: (1) the ICF-associated R618X mutation creates a null allele and R296W is hypomorphic with 60-70% activity; (2) N-terminal tagging abolishes UHRF1 function in a length-dependent manner; (3) hUHRF1 isoform 2 with a 13-residue N-terminal extension is functionally inactive; (4) AlphaFold3 predictions suggest N-terminal extensions disrupt inter-domain interactions
- **Visible evidence base** Southern blot methylation assays at major/minor satellite repeats, bisulfite sequencing of IAP elements, pyrosequencing of five loci in HCT116 cells, Western blot expression controls, RT-qPCR variant quantification, CRISPR/Cas9 knockout generation, AlphaFold3 structural models
- **Missing materials affecting confidence** Supplementary figures S1 and S2, Tables S1-S3, raw pyrosequencing data, full Western blot images, AlphaFold3 model coordinates, detailed statistical analysis descriptions

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question regarding the functional activity of UHRF1 variants, with implications for both clinical genetics and experimental design in the DNA methylation field. The use of Uhrf1-deficient mESCs as a rescue system is well justified given their tolerance to methylation loss. The core findings, particularly the inactivity of N-terminally tagged UHRF1 and the hypomorphic nature of R296W, are potentially field-altering. However, several technical concerns regarding assay sensitivity, quantification rigor, and the strength of structural conclusions need to be addressed before the case is fully established.
- **Who would be interested in the results, and why** Researchers studying DNA methylation inheritance, epigenetic reprogramming, and UHRF1 biology. Clinical geneticists interested in ICF syndrome variants. Investigators using tagged UHRF1 constructs in their own work, as the findings have direct implications for experimental design and interpretation of prior published results.
- **Major strengths** The use of mESCs uniquely tolerant to methylation loss provides a clean system for assessing UHRF1 activity without confounding toxicity. The systematic approach to resolving literature discrepancies, including testing multiple tag configurations and isoform variants, is commendable. The combination of functional rescue assays with structural predictions provides complementary perspectives. The clinical relevance of characterizing ICF-associated mutations adds translational significance.
- **Major Concerns** 
  - R1-M1: The quantitative assessment of R296W activity relies on a single calculation from one bisulfite sequencing experiment, with no statistical replication or error estimation.
  - R1-M2: The AlphaFold3 structural predictions, while suggestive, are presented without experimental validation and may overstate the mechanistic conclusion.
  - R1-M3: The claim that N-terminal tagging abolishes UHRF1 function is based on a limited set of tag configurations, and the distinction between length and sequence effects is not fully resolved.
  - R1-M4: The absence of a positive control demonstrating that the rescue system can detect partial activity (e.g., a known hypomorphic allele) weakens the interpretation of R296W as hypomorphic.
- **Minor Comments**
  - R1-m1: The manuscript would benefit from a more detailed description of the Southern blot quantification methodology, including how band intensities were normalized and analyzed.
  - R1-m2: The statement that "low levels of UHRF1 are sufficient for activity" is based on only two clones and would benefit from a more systematic dose-response analysis.
  - R1-m3: The RT-qPCR data showing variant percentages sum to less than 100% in some cell lines is acknowledged but not fully explained; additional discussion of potential unannotated variants would strengthen the analysis.
  - R1-m4: The migration pattern of isoform 2 versus isoform 1 on Western blots is noted as unexpected; a brief discussion of why this might occur would be helpful.
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantification rigor), R1-M3 (tag configuration coverage), R1-M4 (positive control for partial activity)
- **Assessment against Nature-style criteria** 
  - Originality: High. The systematic characterization of UHRF1 variants, particularly the demonstration that N-terminal tagging abolishes function, challenges widely held assumptions in the field.
  - Scientific importance: High. The findings have direct implications for interpreting a large body of published work using tagged UHRF1 constructs and for understanding ICF syndrome pathogenesis.
  - Interdisciplinary readership: Moderate. The work will primarily interest epigeneticists and DNA methylation researchers, with some appeal to clinical geneticists.
  - Technical soundness: Moderate. The core experimental approach is sound, but quantification and replication concerns limit the strength of some conclusions.
  - Readability for nonspecialists: Good. The manuscript is clearly written and the logic is easy to follow, though some familiarity with DNA methylation assays is assumed.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding quantification rigor and the strength of structural conclusions.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "hUHRF1:R296W was modestly impaired, with its activity being estimated at 60 to 70% of the level of WT hUHRF1"
- **Evidence pointer** Figure 1D, bisulfite sequencing analysis
- **Concern** The 60-70% activity estimate for R296W is derived from a single calculation using one set of bisulfite sequencing data. The formula provided (Relative activity = (R296W-Uhrf1KO)/(WT-Uhrf1KO) = (67-25)/(91-25) = 64%) appears to use single values without replication. No error bars, confidence intervals, or statistical tests are reported for this key quantitative claim.
- **Why it matters** The classification of R296W as hypomorphic versus near-normal has clinical implications for understanding ICF syndrome severity and for interpreting the mechanism of the mutation. A single measurement without error estimation cannot support a precise activity estimate.
- **Resolution test** Provide replicate bisulfite sequencing experiments (at least 3 independent biological replicates) with statistical analysis demonstrating that R296W activity is significantly lower than WT but significantly higher than null. Alternatively, use an independent quantitative method (e.g., mass spectrometry or pyrosequencing) to confirm the activity level.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "AlphaFold3 structural predictions suggest that these additional residues at the N terminus disrupt essential inter-domain interactions"
- **Evidence pointer** Figure 5, AlphaFold3 predictions
- **Concern** The structural predictions are presented as supporting evidence for the mechanism of inactivation, but no experimental validation is provided. The pLDDT values for interdomain regions are reported as 50-70, indicating low confidence in exactly the regions that are central to the proposed mechanism. The claim that the N-terminal extension "forces a rearrangement" is a strong mechanistic statement based on computational prediction alone.
- **Why it matters** The structural mechanism is presented as a key explanatory finding, but the low confidence in the relevant regions and lack of experimental validation (e.g., mutagenesis, cross-linking, or NMR) means the mechanism remains speculative.
- **Resolution test** Either temper the mechanistic language to reflect the predictive nature of the findings, or provide experimental validation such as targeted mutagenesis of the predicted interaction interfaces, hydrogen-deuterium exchange, or cross-linking mass spectrometry to confirm the proposed conformational changes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "N-terminally tagged UHRF1 lacks activity" and "the deleterious effect correlates with N-terminal extension length"
- **Evidence pointer** Figures 1, 2, 3
- **Concern** The conclusion that N-terminal tagging abolishes UHRF1 function is based on testing Myc and 3xFlag tags, and alanine extensions of 1, 3, 7, and 10 residues. However, the manuscript does not test whether the effect is truly length-dependent or sequence-dependent. The 10-residue Myc tag and 22-residue 3xFlag tag both inactivate, but the alanine series shows a gradual effect. The claim that "length is the primary determinant" is not fully supported because only alanine was tested in the length series, and the sequence composition of the tags differs from alanine.
- **Why it matters** The conclusion that all N-terminal tags are problematic has broad implications for the field, as many researchers use N-terminally tagged UHRF1. If the effect is sequence-specific rather than purely length-dependent, some tags might be tolerated, and the field-wide implications would be different.
- **Resolution test** Test additional tags of similar length but different sequence (e.g., HA tag, 9 residues; or a scrambled Myc sequence) to determine whether the effect is purely length-based or has sequence specificity. Alternatively, test a shorter version of the Myc tag to establish a threshold.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design
- **Claim pointer** "hUHRF1:R296W is hypomorphic" and "hUHRF1:R618X a null mutation"
- **Evidence pointer** Figures 1C, 1D
- **Concern** The rescue experiments demonstrate that R296W restores methylation to a substantial but reduced extent compared to WT, and R618X shows no activity. However, there is no positive control demonstrating that the assay can detect partial activity. For example, a known hypomorphic UHRF1 allele or a titration of WT UHRF1 expression levels would establish the dynamic range of the assay and confirm that the reduced activity of R296W is not an artifact of expression level differences or assay insensitivity.
- **Why it matters** The classification of R296W as hypomorphic versus fully functional depends on the assay's ability to distinguish partial from complete rescue. Without a positive control for partial activity, the interpretation that R296W is hypomorphic rather than fully active (with the observed difference being due to experimental variation) is not fully supported.
- **Resolution test** Include a titration of WT UHRF1 expression (e.g., low, medium, high expressing clones) to establish the relationship between expression level and methylation rescue. This would demonstrate that the assay can detect partial activity and that the R296W phenotype is not simply due to lower expression.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Southern blot quantification
- **Evidence pointer** Figures 1C, 2C, 2E, 3C
- **Issue** The Southern blot data are described as "semi-quantitative," but no details are provided on how the band intensities were quantified or normalized. The representative blots show clear differences, but a more quantitative description would strengthen the conclusions.
- **Required correction** Provide a description of the quantification method (e.g., densitometry, phosphorimaging) and how the data were normalized (e.g., to loading controls or total DNA). If quantification was not performed, state this explicitly and describe the qualitative assessment criteria.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Experimental design
- **Affected element** Dose-response analysis
- **Evidence pointer** Figures 2B-E
- **Issue** The observation that "low levels of UHRF1 are sufficient for activity" is based on two clones (clone #12 for untagged, clone #5 for C-terminally tagged). This is a potentially important finding, but the sample size is limited.
- **Required correction** Either provide additional clones with varying expression levels to strengthen this conclusion, or temper the statement to reflect the limited data.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data interpretation
- **Affected element** RT-qPCR analysis
- **Evidence pointer** Figure 4C
- **Issue** The sum of variant percentages is substantially lower than 100% in MDA-MB-231 and HCT7 cells, which the authors attribute to possible additional variants. However, the primers used for total UHRF1 detection may not amplify all variants equally, which could affect the interpretation.
- **Required correction** Discuss the potential limitations of the total UHRF1 primer set and whether the primers were validated to amplify all known variants with equal efficiency.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Western blot migration
- **Evidence pointer** Figure 4D
- **Issue** The observation that isoform 2 (806 aa) and isoform 1 (793 aa) show no difference in migration is unexpected given the 13-amino acid difference. The authors suggest this may reflect structural changes, but this is speculative.
- **Required correction** Provide a brief discussion of why the migration might be similar, or consider whether the antibody used can distinguish between the two isoforms. If possible, include a control with a known size marker to confirm the expected migration pattern.

## Risk / unsupported claims
- The claim that "N-terminally tagged UHRF1 lacks activity" is supported for the specific tags tested (Myc, 3xFlag) but is generalized to all N-terminal tags without testing additional configurations.
- The statement that "the length of the N-terminal extension is the primary determinant of UHRF1 activity" is not fully supported because only alanine was tested in the length series, and the sequence composition of the tags differs from alanine.
- The AlphaFold3 structural predictions are presented as mechanistic evidence, but the low confidence in interdomain regions and lack of experimental validation mean this remains speculative.
- The claim that "isoform 2 does not play a role in regulating DNA methylation" is supported by the rescue and knockout experiments, but the possibility of context-dependent or cell-type-specific effects cannot be excluded.
- The statement that "results and conclusions from studies using such constructs warrant reevaluation" is a broad claim that extends beyond the direct experimental evidence presented.