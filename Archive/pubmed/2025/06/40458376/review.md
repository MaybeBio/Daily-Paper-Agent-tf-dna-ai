## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, materials and methods, and supplementary declarations.
- **Assessment boundary** The review is confined to the scientific content, methodology, and claims presented in the provided manuscript. No external data, replication, or verification of bioinformatics outputs was performed.
- **Shared manuscript claim summary** The authors report an in silico characterization of promoter regions and regulatory elements for 15 chicken IGF and VIP genes, identifying transcription start sites, common motifs, transcription factor families, CpG islands, tandem repeats, and gene–gene interaction networks, with the stated aim of informing future experimental studies on reproductive traits.
- **Visible evidence base** Results sections 2.1–2.4, Tables 1–8, Figures 1–4, and the Materials and Methods section 4.1–4.5.
- **Missing materials affecting confidence** Supplementary data files, raw sequence accession numbers, complete MEME/TOMTOM output tables, detailed parameter settings for each tool, and any statistical significance thresholds beyond those mentioned in the text. The manuscript does not provide accession numbers for the 15 gene sequences, which limits reproducibility.

## Reviewer
- **Overall assessment** The manuscript presents a straightforward in silico analysis of promoter regions for a set of candidate genes in chicken. The work is descriptive and largely confirmatory of known regulatory features, but it lacks experimental validation and contains several methodological ambiguities that weaken the strength of the claims. The central conclusion, that these regulatory elements are "associated with reproductive traits," is inferred rather than demonstrated, as no phenotypic or functional data are presented. The manuscript would benefit from clearer reporting of sequence identifiers, tool parameters, and a more cautious interpretation of the biological significance of the findings.
- **Who would be interested in the results, and why** Researchers working on chicken genomics, reproductive biology, and livestock genetics may find the descriptive catalog of promoter features useful as a starting point for targeted functional studies. The identification of specific transcription factor families and Wnt pathway involvement could be of interest to those studying gene regulatory networks in avian species. However, the lack of experimental validation limits the audience to those seeking preliminary in silico data rather than definitive regulatory mechanisms.
- **Major strengths** The manuscript addresses a relevant topic in livestock genomics. The use of multiple bioinformatics tools is appropriate for a descriptive study. The authors provide a clear description of the methods used, and the results are presented in a structured manner with tables and figures. The discussion appropriately acknowledges the need for experimental validation.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility and data availability
  - **Claim pointer** The study claims to analyze 15 specific IGF and VIP gene sequences, but the manuscript does not provide accession numbers or sequence identifiers for these genes.
  - **Evidence pointer** Section 4.1, Table 8
  - **Concern** The Materials and Methods state that sequences were retrieved from NCBI, but no accession numbers, gene IDs, or genome build information are provided. Table 8 is referenced but not described in the text, and its contents are not visible in the provided material.
  - **Why it matters** Without sequence identifiers, the work cannot be reproduced or verified. This is a fundamental requirement for any genomic analysis.
  - **Resolution test** The authors must provide a supplementary table listing the official gene symbols, NCBI accession numbers, and the specific sequence version used for each of the 15 genes.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Claim substantiation
  - **Claim pointer** The title and abstract state that the promoter regions and regulatory elements are "associated with reproductive traits," and the discussion concludes that these elements "play important roles in the chicken reproductive traits."
  - **Evidence pointer** Abstract, Section 3 (Discussion)
  - **Concern** The manuscript presents no direct evidence linking the identified regulatory elements to reproductive traits. The genes were selected based on prior literature, but no phenotypic data, expression data, or genetic association analysis is presented. The claim of association is therefore unsupported by the data shown.
  - **Why it matters** The central claim of the paper is not substantiated. The study is descriptive and does not establish any functional or statistical link between the identified elements and reproductive traits.
  - **Resolution test** The authors should either (a) revise the title, abstract, and discussion to clearly state that the study is a descriptive in silico characterization without direct evidence of association, or (b) include additional data, such as expression analysis or genetic association, to support the claim.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Methodological rigor
  - **Claim pointer** The study identifies "the best common motif, Motif II," and states that it "resembles three major transcription factor families."
  - **Evidence pointer** Section 2.2, Table 3, Figure 2
  - **Concern** The criteria for selecting Motif II as "best" are not defined. The statistical significance of the motif discovery (e-values from MEME) is not reported. The match to transcription factor families is based on TOMTOM, but the p-values and q-values for these matches are not provided.
  - **Why it matters** Without reporting statistical thresholds and significance values, the reader cannot assess the confidence in the motif identification or the transcription factor family assignments.
  - **Resolution test** The authors should report the MEME e-values for all discovered motifs, the TOMTOM p-values and q-values for the matches, and clearly state the criteria used to select Motif II as the "best."
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretation of results
  - **Claim pointer** The study states that "62.5% of the candidate transcription factors have interaction with the Wnt signalling pathway to regulate transcription."
  - **Evidence pointer** Section 2.2, Section 3 (Discussion)
  - **Concern** The basis for this claim is unclear. It is not stated how the interaction with the Wnt pathway was determined. If this is based on literature or a database, the source is not cited. If it is based on the TOMTOM results, the specific transcription factors and their known pathway associations are not listed.
  - **Why it matters** The claim about Wnt pathway involvement is a key finding of the paper, but it is not traceable to a specific analysis or source, making it impossible to evaluate.
  - **Resolution test** The authors should specify the method used to determine Wnt pathway interaction, list the specific transcription factors involved, and provide appropriate citations or database references.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 2.1, Table 1
  - **Evidence pointer** Section 2.1
  - **Issue** The text states that "seven (46.7%) TSSs are located at a distance below −500 bp from the start codon," but the total number of TSSs is not explicitly stated. The percentage implies a total of 15, but the text mentions 11 out of 15 sequences have multiple TSSs, which is inconsistent.
  - **Required correction** Clarify the total number of TSSs identified and ensure the percentage is calculated correctly.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section 2.4, Figures 3 and 4
  - **Evidence pointer** Section 2.4
  - **Issue** The gene–gene interaction network is described, but the figures are not visible in the provided material. The text mentions specific interaction types (physical, genetic, coexpression) but does not provide quantitative details.
  - **Required correction** Ensure the figures are legible and provide a brief description of the network properties, such as the number of nodes and edges, in the text.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Language
  - **Affected element** Section 3 (Discussion)
  - **Evidence pointer** Section 3
  - **Issue** The phrase "as we revealed from the UniProt database" is informal and could be rephrased for clarity.
  - **Required correction** Rephrase to "as indicated in the UniProt database" or similar.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Consistency
  - **Affected element** Section 2.3, Tables 4 and 6
  - **Evidence pointer** Section 2.3
  - **Issue** The text states that CpG islands were found in 11 out of 15 promoters, but then mentions 13 CpG islands in gene body regions. The relationship between these numbers and the total number of genes is not clear.
  - **Required correction** Clarify whether multiple CpG islands can be found in a single promoter or gene body region, and present the data in a way that avoids ambiguity.

## Technical failings that need to be addressed before the case is established
- R1-M1: Lack of sequence accession numbers prevents reproducibility.
- R1-M2: The central claim of association with reproductive traits is not supported by the data.
- R1-M3: Statistical significance of motif discovery and transcription factor matching is not reported.

## Risk / unsupported claims
- The claim that the identified regulatory elements are "associated with reproductive traits" is unsupported by any direct evidence presented in the manuscript.
- The claim that "62.5% of the candidate transcription factors have interaction with the Wnt signalling pathway" is not traceable to a specific analysis or source.
- The statement that the identified CpG islands are "very rich" is subjective and not supported by a comparative analysis with other genomic regions.
- The biological significance of the identified tandem repeats is speculative, as no functional data are provided.

## Assessment against Nature-style criteria
- **Originality** Low. The application of standard in silico tools to a set of known candidate genes is not novel. Similar analyses have been reported for other genes and species.
- **Scientific importance** Moderate. The genes studied are relevant to chicken reproduction, but the descriptive nature of the findings limits their impact. The study does not provide new mechanistic insights or testable hypotheses beyond what is already known.
- **Interdisciplinary readership** Limited. The work is primarily of interest to poultry geneticists and computational biologists. It is unlikely to attract a broad readership.
- **Technical soundness** The methods are standard, but the reporting is incomplete. The lack of sequence identifiers, statistical thresholds, and clear criteria for key claims undermines the technical rigor.
- **Readability for nonspecialists** The manuscript is generally readable, but the results section is dense and would benefit from clearer explanations of the bioinformatics outputs. The discussion is somewhat repetitive and could be more focused.

## Recommendation posture
Currently not established from the provided evidence. The manuscript is a descriptive in silico study with significant reporting gaps. The central claim of association with reproductive traits is not supported. The authors should address the major concerns, particularly the lack of sequence identifiers and the unsupported interpretation of the results, before the work can be considered for publication.