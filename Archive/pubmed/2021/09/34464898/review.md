## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Molecular dynamics simulation study of SSBP1 variants; claims limited to in silico predictions of tetramer stability, intermonomer interactions, solvent accessible surface changes, and DNA binding surface mapping
- **Shared manuscript claim summary** The authors used molecular dynamics simulations to model wild-type and 31 variant SSBP1 tetramer systems (7 homotetramers, 24 heterotetramers) and report that all variants form stable tetramers, most with tighter intermonomer interactions, reduced solvent accessible surface areas, and reduced net positive surface charge. They further predict DNA binding surfaces using structural alignments and phosphate probing simulations, concluding that disease mechanisms likely involve subtle changes to DNA binding or wrapping rather than tetramer destabilization.
- **Visible evidence base** Full manuscript text including Abstract, Introduction, Materials and Methods, Results, Discussion, and references to figures and supplemental tables
- **Missing materials affecting confidence** Figures and supplemental tables referenced but not provided; no raw simulation data, force field parameter files, or trajectory analysis scripts; no experimental validation data for simulation predictions

## Reviewer
- **Overall assessment** This manuscript presents a systematic computational investigation of disease-associated SSBP1 variants, addressing an important gap in understanding the molecular mechanisms of recently identified mitochondrial disease mutations. The study is thoughtfully designed, with careful attention to the heterotetramer problem that has been largely unaddressed in prior work. The simulations appear technically sound, and the authors are appropriately cautious in interpreting their results as predictive rather than definitive. However, the manuscript would benefit from clearer presentation of some methodological details, and the conclusions, while reasonable, are necessarily limited by the computational nature of the study. The work represents a useful contribution to the field, though its impact is somewhat constrained by the lack of experimental validation and the inherent limitations of the simulation approach.

- **Who would be interested in the results, and why** Researchers studying mitochondrial DNA replication and maintenance, particularly those interested in SSBP1 structure-function relationships; clinical geneticists and molecular diagnosticians seeking mechanistic understanding of SSBP1-associated diseases; computational biologists working on protein-DNA interactions and molecular dynamics simulations of disease variants. The heterotetramer modeling approach may also interest those studying dominant-negative mechanisms in multimeric proteins.

- **Major strengths** The study addresses a clinically relevant and timely question with a systematic computational approach. The inclusion of heterotetramer systems is a significant strength, as this has been largely ignored in previous studies. The authors are appropriately cautious in their interpretations and acknowledge the limitations of their approach. The phosphate probing simulation strategy is creative and provides useful predictions for future experimental work.

- **Major Concerns** 
  - R1-M1: The manuscript does not provide sufficient validation of the simulation methodology or demonstrate convergence of the simulations. The authors state that simulations were run for 300 ns but do not provide evidence that this is sufficient for the systems studied, nor do they show convergence metrics or replicate simulations.
  - R1-M2: The phosphate probing simulations are used to make specific claims about DNA binding hotspots, but the relationship between dimethyl phosphate binding and actual ssDNA binding is not well established. The authors acknowledge this limitation but do not provide sufficient justification for the interpretation.
  - R1-M3: The claim that "nearly the entire surface of SSBP1 is available for DNA binding" is based on structural alignments with bacterial SSBs and phosphate probing, but the evidence presented is indirect and the interpretation may overreach the data.
  - R1-M4: The manuscript does not adequately address how the predicted subtle changes in DNA binding would translate to the disease phenotypes observed in patients, particularly the tissue-specific and late-onset nature of the disease.

- **Minor Comments**
  - R1-m1: The authors should clarify the temperature and pressure coupling methods used in the simulations, as these are not described in the Methods section.
  - R1-m2: The criteria for identifying "high frequency occupation sites" in the phosphate probing simulations should be more explicitly defined.
  - R1-m3: The manuscript would benefit from a more detailed description of how the heterotetramer systems were constructed, particularly regarding the orientation of variant monomers.
  - R1-m4: The authors should discuss potential limitations of using the E. coli SSB tetramer as a template for modeling the human SSBP1 tetramer, given the sequence divergence between these proteins.
  - R1-m5: The Discussion section could be strengthened by more explicitly connecting the simulation predictions to testable experimental hypotheses.

- **Technical failings that need to be addressed before the case is established** R1-M1 (simulation convergence and validation), R1-M2 (phosphate probe interpretation), R1-M3 (DNA binding surface claims)

- **Assessment against Nature-style criteria** 
  - Originality: The study is original in its systematic application of molecular dynamics to all reported SSBP1 disease variants and its inclusion of heterotetramer systems. The phosphate probing approach is creative, though not entirely novel.
  - Scientific importance: The work addresses an important clinical question and provides a framework for understanding SSBP1 disease mechanisms. However, the computational nature of the study limits its direct impact on clinical understanding.
  - Interdisciplinary readership: The work bridges computational biology, mitochondrial genetics, and clinical medicine, and would be of interest to researchers in these fields.
  - Technical soundness: The simulation methodology appears generally sound, but the lack of convergence validation and limited methodological detail reduce confidence in the results.
  - Readability for nonspecialists: The manuscript is generally well-written and accessible, though some sections (particularly the Methods) assume familiarity with molecular dynamics techniques.

- **Recommendation posture** Supportive if technical concerns are resolved. The study addresses an important question and provides useful predictions, but the lack of simulation validation and the indirect nature of the DNA binding surface predictions need to be addressed before the conclusions can be fully accepted.

## Risk / unsupported claims
- The claim that "all variants are stable" is based on 300 ns simulations, which may not capture longer timescale dynamics or rare conformational events
- The prediction of DNA binding hotspots from dimethyl phosphate probing is not directly validated against experimental DNA binding data
- The assumption that heterotetramers are equally abundant and randomly assembled in patient mitochondria is stated but not experimentally verified
- The conclusion that disease mechanisms involve "subtle changes to DNA binding, wrapping, or release" is speculative and not directly supported by the simulation data
- The claim that "nearly the entire surface of SSBP1 is available for DNA binding" extends observations from bacterial SSBs to human SSBP1 without direct experimental evidence