## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the supplied abstract text
- **Shared manuscript claim summary** The authors report a bioinformatic analysis of 103 tissue-specific human enhancers with facial expression, their orthologs in non-human primates, transcription factor binding site comparisons, and molecular docking of selected transcription factors with DNA to infer evolutionary and developmental significance.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials provided
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, supplementary data, statistical analyses, and validation experiments

## Reviewer

- **Overall assessment** The abstract presents a potentially interesting comparative genomics approach to craniofacial development, but the current evidence base is insufficient to evaluate the validity of the claims. Several statements are vague, some appear internally inconsistent, and the connection between the bioinformatic observations and the stated conclusions about evolutionary significance is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers in craniofacial development, evolutionary developmental biology, and comparative genomics may find the identification of transcription factor binding site differences between human and non-human primate facial enhancers of interest. Those studying cis-regulatory evolution and its role in human-specific traits could also be interested, provided the findings are validated experimentally.
- **Major strengths** The study addresses a relevant topic in evolutionary developmental biology. The use of publicly available resources such as VISTA Enhancer Browser and TRANSFAC is appropriate for an initial comparative screen. The focus on enhancers with facial expression is a reasonable strategy to investigate craniofacial variation.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The abstract states that 43 out of 190 transcription factors from TRANSFAC were seen as binding in both human and non-human primate enhancers, and that binding sites of 7 transcription factors were exclusively gained in human eye and nose enhancers.
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** The criteria for defining "binding" are not described. It is unclear whether this refers to predicted binding sites, experimentally validated binding, or some other metric. The claim of "exclusively gained" sites requires a clear definition of the comparison baseline, including how orthology of enhancers was established and how binding site presence or absence was determined across species.
  - **Why it matters** Without a clear methodological definition, the central comparative claim cannot be assessed. The distinction between predicted and validated binding is critical for interpreting evolutionary significance.
  - **Resolution test** Provide the computational pipeline, thresholds, and validation steps used to identify transcription factor binding sites. Clarify how orthology was assigned and how "exclusively gained" was determined, including whether loss events in non-human primates were considered.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The abstract states that molecular docking was performed using PyMol, with DNA and protein structures modelled by SCFBio and SWISSMODEL respectively, to observe interactions of transcription factors with DNA.
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** The description of the docking methodology is incomplete and potentially confused. PyMol is a visualization tool, not a docking program. The statement that docking was performed "through PyMol" is technically inaccurate. Additionally, the purpose of the docking in relation to the enhancer binding site analysis is not explained.
  - **Why it matters** The docking results appear to be a major component of the study, but the methodology as described is not reproducible and the tool attribution is incorrect. This undermines confidence in the structural interaction claims.
  - **Resolution test** Specify the actual docking software and parameters used. Clarify the role of PyMol in the workflow. Describe how docking results were scored and how they relate to the transcription factor binding site predictions.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Scientific importance
  - **Claim pointer** The abstract concludes that the findings provide information about "identification and genetic expression" and imply evolutionary significance for facial variation.
  - **Evidence pointer** Abstract text; location not provided
  - **Concern** The abstract does not present any functional validation, expression data, or population-level genetic association. The leap from computational binding site predictions and docking to conclusions about facial variation and evolutionary significance is not supported by the evidence described.
  - **Why it matters** The stated significance of the work depends on connecting sequence-level observations to phenotypic outcomes. Without experimental validation or association with facial variation data, the conclusions remain speculative.
  - **Resolution test** Provide experimental validation such as reporter assays, CRISPR perturbations, or expression analyses. Alternatively, connect the identified enhancers and transcription factors to known genetic variants associated with facial traits.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Opening statements
  - **Evidence pointer** Abstract text
  - **Issue** The opening statements about genome similarity and DNA study linking genetic variations to facial attributes are general and not clearly connected to the specific study design.
  - **Required correction** Provide a more focused introduction that directly frames the specific question addressed by the enhancer analysis.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Transcription factor list
  - **Evidence pointer** Abstract text
  - **Issue** The list of transcription factors (Oct, Pax, Sox, MyoD, Foxd3, cRel and Gata) is presented without context. It is unclear whether these are all known to be involved in craniofacial development and whether the list is exhaustive or representative.
  - **Required correction** Provide context for the selection of these factors and clarify whether the list is complete or a subset.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Scientific importance
  - **Affected element** Evolutionary significance claim
  - **Evidence pointer** Abstract text
  - **Issue** The phrase "exclusively gained in the human eye and nose enhancers" implies a human-specific evolutionary event, but the abstract does not specify which non-human primate species were included in the comparison.
  - **Required correction** Specify the non-human primate species analyzed and clarify whether the gains are human-specific or shared with some primates.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality: The approach of comparing transcription factor binding sites in facial enhancers across primates has some novelty, but the abstract does not demonstrate a sufficiently original conceptual advance. Scientific importance: The topic is important, but the current evidence does not establish a significant contribution. Interdisciplinary readership: The work could appeal to developmental biologists, geneticists, and evolutionary biologists, but the abstract is not framed to engage a broad audience. Technical soundness: Major methodological concerns regarding binding site identification and docking procedures prevent assessment of technical validity. Readability for nonspecialists: The abstract is partially accessible but contains jargon and unclear methodological descriptions that would hinder nonspecialist comprehension.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a potentially interesting bioinformatic screen, but the methodological descriptions are incomplete or inaccurate, and the central claims about evolutionary significance are not supported by the evidence presented. A revised manuscript with detailed methods, validation, and clearer framing could change this assessment.

## Risk / unsupported claims

- The claim that 7 transcription factors have binding sites "exclusively gained" in human eye and nose enhancers is unsupported without a clear definition of the comparison and validation.
- The claim that molecular docking was performed "through PyMol" is technically inaccurate and the docking results are not interpretable from the supplied description.
- The conclusion that the findings provide insight into "identification and genetic expression" related to facial variation is unsupported without functional or association data.
- The statement that non-coding sequences represent approximately 85% of human DNA under evolutionary restrictions is presented without citation and is not directly relevant to the study design as described.
- The overall evolutionary significance of the findings cannot be evaluated from the abstract alone.