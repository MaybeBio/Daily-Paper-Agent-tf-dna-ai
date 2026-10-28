## Review setup
- **Input scope** Full manuscript text including abstract, introduction, materials and methods, results, discussion, and supplementary figure/table references
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and structural biology predictions as presented in the manuscript
- **Shared manuscript claim summary** The authors propose that KSHV ORF24, a viral TBP mimic, uses a noncanonical DNA-binding mode involving both its TBP-like domain and a C-terminal domain (CTD) to recognize viral late gene promoters. They further claim that ORF24 pre-assembles with RNAPII and ORF34 before stable DNA binding, representing an "assembly-first" mechanism distinct from stepwise eukaryotic transcription initiation.
- **Visible evidence base** AlphaFold3 structural predictions, luciferase reporter assays in HEK293T cells, BAC16 mutagenesis in iSLK cells, co-immunoprecipitation, immunofluorescence, and ChIP-qPCR
- **Missing materials affecting confidence** Supplementary figures and tables (S1-S4) referenced but not provided; raw ChIP-qPCR data not shown; AlphaFold3 prediction confidence metrics (pLDDT values) only partially reported; no experimental structure validation

## Reviewer

- **Overall assessment** This manuscript presents a compelling and well-executed study that advances our understanding of how a viral TBP mimic achieves promoter selectivity. The combination of AlphaFold3 predictions with systematic mutagenesis and infection-based assays is appropriate and largely convincing. The central claims regarding the extended DNA-binding interface and the assembly-first mechanism are supported by the data presented, though several technical limitations and missing controls temper the strength of the conclusions. The work will be of interest to virologists and transcription biologists, and the proposed mechanism represents a conceptually novel contribution to the field.

- **Who would be interested in the results, and why** Virologists studying herpesvirus gene regulation, particularly those focused on gammaherpesvirus transcription mechanisms. Transcription biologists interested in alternative initiation complex assembly strategies and TBP-like proteins. Structural biologists studying protein-DNA recognition, especially in the context of noncanonical binding modes. Researchers investigating viral mimicry of host factors and host-pathogen interactions at the transcriptional level.

- **Major strengths** The study addresses a significant gap in understanding KSHV late gene transcription by providing the first structural model of ORF24 in complex with DNA. The use of AlphaFold3 to generate testable hypotheses followed by experimental validation is a modern and effective approach. The systematic mutagenesis strategy covering the TBP-like domain, CTD, and interaction interfaces is thorough. The inclusion of infection-based assays (BAC16 mutants) strengthens the physiological relevance of the findings. The identification of an assembly-first mechanism is conceptually novel and has broad implications for understanding viral transcription strategies.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of structural predictions
- **Claim pointer** "AlphaFold3 generated a high confidence prediction (pLDDT > 70) of the structural architecture of ORF24 comprising four distinct domains" and the subsequent identification of CTD-DNA contacts
- **Evidence pointer** Results section "AlphaFold3 predicts an extended DNA binding domain for KSHV ORF24", Figures 1B-C, 2A, Table 1
- **Concern** The manuscript relies heavily on AlphaFold3 predictions to define the DNA-binding interface, yet no experimental structural validation (e.g., X-ray crystallography, cryo-EM, or even crosslinking) is provided. The pLDDT threshold of >70 is relatively permissive, and the authors do not report per-residue confidence for the specific CTD residues predicted to contact DNA. Given that the CTD-DNA interaction is a central novel claim, the lack of orthogonal structural validation is a significant limitation. Additionally, the DNA sequence used in the prediction is derived from the K8.1 promoter, but it is unclear whether predictions were tested with other late promoter sequences to assess generalizability.
- **Why it matters** The central claim of a noncanonical DNA-binding mode involving the CTD rests entirely on computational predictions. If the predicted CTD-DNA contacts are artifacts of the AlphaFold3 model, the mechanistic conclusions would be substantially weakened. The field requires more robust evidence for a novel DNA-binding mode before accepting this as established.
- **Resolution test** Provide per-residue confidence scores for the CTD-DNA interface, validate predictions with additional late promoter sequences, or obtain experimental structural data (even low-resolution) supporting the extended binding interface. Alternatively, demonstrate that CTD mutations specifically disrupt DNA binding without affecting protein folding or interactions through more direct biochemical assays (e.g., electrophoretic mobility shift assays with purified proteins).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence for assembly-first mechanism
- **Claim pointer** "ORF24 requires intact interactions with both RNAPII and ORF34 for stable promoter binding, demonstrating an assembly-first mechanism where multiprotein complex formation precedes DNA engagement"
- **Evidence pointer** Results section "ORF24 promoter occupancy in infected cells requires multiprotein complex pre-assembly", Figure 5B
- **Concern** The ChIP-qPCR data supporting the assembly-first model are presented only as a summary statement without showing the actual data. The authors state that Rpb1-interaction-deficient and ORF34-interaction-deficient mutants fail to bind late promoters, but the ChIP enrichment values, statistical significance, and appropriate controls (e.g., IgG controls, input normalization) are not displayed. Furthermore, the interpretation that complex formation precedes DNA binding is inferred from steady-state occupancy measurements, which cannot distinguish between a requirement for pre-assembly versus cooperative binding after initial DNA engagement. The claim of "assembly-first" is mechanistically strong and requires more direct evidence, such as kinetic measurements or single-molecule approaches.
- **Why it matters** The assembly-first model is presented as a "fundamental departure" from canonical transcription initiation. This is a strong claim that requires robust experimental support. If the conclusion is based solely on steady-state ChIP data without kinetic resolution, the interpretation may be overreaching.
- **Resolution test** Show the full ChIP-qPCR dataset with statistical analysis. Consider performing time-course experiments after reactivation to assess whether complex formation precedes promoter occupancy. Alternatively, use in vitro assays with purified components to demonstrate that the ORF24-ORF34-RNAPII complex forms prior to DNA binding.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Functional significance of CTD mutations
- **Claim pointer** "Mutations of residues predicted to directly contact DNA (K662A, Y670A, K685A) resulted in intermediate reductions in late gene reporter activity" and "N694A/N696A completely abolished late gene expression"
- **Evidence pointer** Results section "ORF24 vTBP and CTD residues predicted to bind DNA are necessary for late gene activation", Figure 2C-D
- **Concern** The distinction between "intermediate" and "complete" loss of function for CTD mutants is not clearly quantified. The authors do not report the magnitude of the intermediate reductions or the statistical significance of differences between mutant classes. Additionally, the N694A/N696A mutant is described as not predicted to directly contact DNA, yet it causes complete loss of function. The authors speculate this may be due to structural roles, but no structural analysis of this mutant is provided. The possibility that these mutations affect protein stability or folding is acknowledged but not directly tested beyond co-immunoprecipitation showing retained interactions.
- **Why it matters** The graded phenotypes of CTD mutants are used to support the model of an extended DNA-binding interface with both direct contact and structural contributions. Without clear quantification and additional characterization, the interpretation remains speculative.
- **Resolution test** Provide quantitative reporter assay data with effect sizes and statistical comparisons. Perform structural predictions or circular dichroism spectroscopy on the N694A/N696A mutant to assess folding. Consider testing additional CTD mutants to map the functional landscape more precisely.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of findings
- **Claim pointer** "ORF24 employs a noncanonical DNA-binding mode where the C-terminal domain (CTD) makes critical DNA contacts beyond the canonical TBP fold"
- **Evidence pointer** Results section "AlphaFold3 predicts an extended DNA binding domain for KSHV ORF24", Supplementary Figure S3
- **Concern** The authors demonstrate CTD conservation across beta- and gamma-herpesviruses but only test ORF24 from KSHV. The claim that this extended DNA-binding mode is likely conserved across herpesvirus subfamilies is based solely on sequence conservation, not functional validation. Given that the CTD is proposed to be critical for promoter specificity, testing at least one additional ORF24 homolog would substantially strengthen the generalizability claim.
- **Why it matters** The broader significance of the work depends on whether this mechanism is shared across herpesviruses. If the extended DNA-binding mode is unique to KSHV, the impact of the findings is more limited.
- **Resolution test** Test the corresponding CTD mutations in at least one additional herpesvirus ORF24 homolog (e.g., EBV BcRF1 or MHV68 ORF24) in the reporter assay.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1A
- **Evidence pointer** Results section "AlphaFold3 predicts an extended DNA binding domain for KSHV ORF24"
- **Issue** The schematic in Figure 1A is described as showing ORF24's role in late gene transcription, but the figure itself is not provided. The authors should ensure the figure clearly illustrates the domain architecture and the proposed DNA-binding mode.
- **Required correction** Provide the figure or describe the schematic in sufficient detail in the text so readers can follow the domain organization without the figure.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** ChIP-qPCR methods
- **Evidence pointer** Materials and methods section "Chromatin Immunoprecipitation and qPCR (ChIP-qPCR)"
- **Issue** The ChIP-qPCR section does not specify the number of biological replicates, the statistical test used, or how enrichment was calculated relative to input. The primers are listed in Supplementary Table S1, but the table is not provided.
- **Required correction** Add details on replicates, statistical analysis, and enrichment calculation. Ensure Supplementary Table S1 is available for review.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of co-immunoprecipitation data
- **Affected element** Supplementary Figure S4
- **Evidence pointer** Results section "ORF24 vTBP and CTD residues predicted to bind DNA are necessary for late gene activation"
- **Issue** The co-immunoprecipitation data are referenced as confirming that mutants retain interactions with ORF34 and Rpb1, but the data are not shown. The authors should clarify whether these are qualitative or quantitative assessments and whether any mutants showed reduced but not absent interactions.
- **Required correction** Show the co-immunoprecipitation data or provide a clear statement of the results, including any quantitative analysis.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section, paragraph 2
- **Issue** The discussion does not explicitly address the limitations of relying on AlphaFold3 predictions without experimental structural validation. Given the central role of these predictions, a more balanced discussion of the confidence limits would strengthen the manuscript.
- **Required correction** Add a paragraph acknowledging the limitations of computational structure prediction and outlining plans for experimental validation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract, Discussion section
- **Issue** The term "assembly-first" is used to describe the mechanism, but the data presented are steady-state measurements. The term implies a temporal order that is not directly demonstrated. Consider using more cautious language such as "assembly-dependent" or "pre-assembly requirement."
- **Required correction** Revise the terminology to accurately reflect the evidence level, or provide additional kinetic data to support the temporal claim.

## Risk / unsupported claims
- The claim that ORF24 "pre-assembles with RNAPII and ORF34 to achieve stable promoter binding" is inferred from steady-state ChIP data and is not directly supported by kinetic or single-molecule evidence. The temporal ordering of assembly versus DNA binding is not experimentally resolved.
- The identification of specific CTD residues as DNA-contacting is based solely on AlphaFold3 predictions without experimental structural validation. The functional data support involvement of these residues but do not establish direct DNA contact.
- The claim that the extended DNA-binding mechanism is "likely conserved across these herpesvirus subfamilies" is based on sequence conservation alone and has not been functionally tested in other homologs.
- The statement that ORF24 "may not directly interact with TFIIB" is supported by computational predictions and indirect evidence, but no direct biochemical or biophysical data are provided to confirm the absence of interaction.
- The assertion that the assembly-first mechanism "resembles a prokaryotic strategy" is an analogy that, while interesting, is not experimentally tested and should be framed as a conceptual comparison rather than an established similarity.