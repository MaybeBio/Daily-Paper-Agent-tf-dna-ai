## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full methods, figures, tables, or supplementary material
- **Shared manuscript claim summary** The authors report a newly observed interaction between the armadillo-repeat domain of plakophilin 1 (ARM-PKP1) and the C-terminal sterile alpha motif of p73alpha (SAMp73), characterized by a dissociation constant of approximately 5 µM in the absence of NaCl, with the binding interface mapped to the "middle-loop-end-helix" region of SAMp73 via NMR, and supported by molecular docking and simulations. The authors suggest potential therapeutic relevance in tumour pathways involving PKP1 and possible p53 inactivation.
- **Visible evidence base** Abstract text only; no figures, tables, methods details, or numerical data beyond the stated dissociation constant and qualitative descriptions of biophysical measurements
- **Missing materials affecting confidence** Full methods, all experimental data (fluorescence, CD, NMR, ITC), docking and simulation parameters, statistical analyses, replicate numbers, buffer conditions, protein construct details, and any control experiments

## Reviewer

- **Overall assessment** The abstract describes a plausible and potentially interesting protein-protein interaction with relevance to p53-family signalling. However, the evidence as presented is insufficient to rigorously evaluate the strength of the claims. The dissociation constant is stated without error estimates or replicate information, the NMR mapping is described qualitatively, and the molecular modelling results are not detailed. The therapeutic relevance claim is speculative and not supported by functional data. The work may be of interest to structural biologists and cancer researchers, but the current abstract does not establish the case beyond a preliminary observation.
- **Who would be interested in the results, and why** Structural biologists studying protein-protein interactions involving p53-family members, researchers investigating desmosomal proteins in non-adhesive roles, and cancer biologists interested in p73 signalling pathways and potential therapeutic targets. The interaction between a desmosomal component and a transcription factor-associated domain could open new avenues for understanding cross-talk between cell adhesion and tumour suppression.
- **Major strengths** The use of multiple complementary biophysical techniques (fluorescence, CD, NMR, ITC) is appropriate for characterising a protein-protein interaction. The combination of experimental binding measurements with molecular modelling provides a multi-pronged approach. The identification of a specific binding region on SAMp73 via NMR adds mechanistic detail. The study addresses a potentially novel interaction with biological relevance.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Quantitative evidence
  - **Claim pointer** "Association was observed between the two proteins, with a dissociation constant of ~5 µM measured by ITC and fluorescence in the absence of NaCl."
  - **Evidence pointer** Abstract, Results section; location not provided
  - **Concern** The dissociation constant is reported as a single approximate value without error bars, replicate counts, or statistical treatment. It is unclear whether the ITC and fluorescence measurements are consistent within experimental uncertainty or whether they represent independent determinations. No information is provided on the stoichiometry of binding, which is critical for interpreting a Kd value.
  - **Why it matters** A reliable binding affinity is central to the claim of a specific interaction. Without error estimates and replicate information, the reader cannot assess the precision or reproducibility of the measurement. Stoichiometry is essential for distinguishing specific from non-specific binding.
  - **Resolution test** Provide the mean and standard deviation or standard error for at least three independent measurements for each technique, state the binding stoichiometry, and show representative raw data and fits in the full manuscript.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Structural evidence
  - **Claim pointer** "The binding region of SAMp73 involved residues of the so-called 'middle-loop-end-helix' binding region (i.e., comprising the third helix, together with the C terminus of the second one, and the N-cap of the fourth), as shown by (15)N, (1)H- HSQC-NMR spectra."
  - **Evidence pointer** Abstract, Results section; location not provided
  - **Concern** The NMR mapping is described only qualitatively. No information is provided on the magnitude of chemical shift perturbations, the number of residues affected, the criteria for defining the binding interface, or whether the assignments were available for SAMp73. Without these details, the specificity and extent of the mapped region cannot be evaluated.
  - **Why it matters** The identification of a specific binding interface is a key mechanistic claim. Qualitative description of NMR data is insufficient to establish that the interaction is localised to the stated region rather than involving a more extended surface or non-specific contacts.
  - **Resolution test** Provide a quantitative analysis of chemical shift perturbations with a defined threshold, list the specific residues affected, and show the mapped region on the structure of SAMp73 in the full manuscript.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Functional relevance
  - **Claim pointer** "This newly-observed interaction could have potential therapeutic relevance in the tumour pathways where PKP1 is involved, and under conditions when there is a possible inactivation of p53."
  - **Evidence pointer** Abstract, Conclusions section; location not provided
  - **Concern** The therapeutic relevance claim is speculative and not supported by any functional data in the abstract. No experiments are described that link the binding to cellular outcomes, signalling pathways, or p53 status. The phrase "could have potential" is appropriately cautious, but the claim is not testable from the presented evidence.
  - **Why it matters** The stated significance of the work rests partly on this claim. Without functional validation, the relevance to tumour pathways remains an untested hypothesis, which weakens the broader impact of the study.
  - **Resolution test** In the full manuscript, include cellular or in vivo experiments that modulate the interaction and assess effects on p73 or PKP1 function, or clearly reframe the claim as a hypothesis for future work.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Experimental conditions
  - **Affected element** Binding measurements
  - **Evidence pointer** Abstract, Methods section; location not provided
  - **Issue** The abstract states that binding was studied "in the absence and the presence of 100 mM NaCl," but the dissociation constant is only reported for the absence of NaCl. The effect of salt on the interaction is not described.
  - **Required correction** State whether binding was observed in the presence of NaCl and, if so, report the corresponding dissociation constant or explain why it could not be determined.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technique justification
  - **Affected element** Circular dichroism
  - **Evidence pointer** Abstract, Methods section; location not provided
  - **Issue** Far-UV CD is listed among the techniques used, but no results from CD are described in the abstract. It is unclear what information CD provided, such as secondary structure changes upon binding.
  - **Required correction** Briefly state the CD result, or clarify that CD was used for quality control of protein samples rather than for binding characterisation.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Modelling validation
  - **Affected element** Molecular docking and simulations
  - **Evidence pointer** Abstract, Results section; location not provided
  - **Issue** The abstract states that "molecular modelling provided additional information on the possible structure of the binding complex," but no details are given on the docking method, scoring function, simulation length, or convergence criteria.
  - **Required correction** In the full manuscript, describe the modelling protocol and provide validation metrics, such as docking scores, RMSD values, or comparison with experimental restraints.
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative binding data without error or stoichiometry), R1-M2 (qualitative NMR mapping without quantitative criteria), R1-M3 (unsupported therapeutic relevance claim)
- **Assessment against Nature-style criteria** Originality: The interaction between ARM-PKP1 and SAMp73 appears novel and could be of interest, but the abstract does not demonstrate how this finding advances beyond a preliminary observation. Scientific importance: The potential link between desmosomal proteins and p53-family signalling is intriguing, but the importance is not established without functional data. Interdisciplinary readership: The topic bridges structural biology and cancer biology, which could attract a broad audience, but the abstract is too technical and lacks context for non-specialists. Technical soundness: The use of multiple biophysical techniques is appropriate, but the lack of quantitative detail and error analysis prevents assessment of technical rigour. Readability for nonspecialists: The abstract assumes familiarity with domain names and techniques; the significance is not clearly framed for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a plausible interaction, but the quantitative and structural claims are not sufficiently supported, and the functional relevance is speculative. The authors should provide full experimental details, error analysis, and functional context in the manuscript before the case can be assessed.

## Risk / unsupported claims

- The dissociation constant of ~5 µM is reported without error estimates, replicate counts, or stoichiometry, making the value unverifiable from the abstract.
- The NMR mapping to the "middle-loop-end-helix" region is qualitative and lacks quantitative criteria, so the specific interface claim is not assessable.
- The therapeutic relevance claim is speculative and not supported by any functional or cellular data.
- The effect of 100 mM NaCl on binding is mentioned in the methods but not reported in the results, leaving the salt dependence claim incomplete.
- The molecular modelling results are described only as "additional information" without details, making the structural model unverifiable.