## Review setup
- **Input scope** Full manuscript text (abstract, main text, figure legends referenced but not provided in full)
- **Assessment boundary** Scientific claims, methodology, evidence quality, and presentation as presented in the supplied text
- **Shared manuscript claim summary** The authors introduce iMAX FRET, a single-molecule FRET method using stochastic exchange of weakly binding DNA imagers to measure multiple pairwise distances simultaneously, enabling ab initio 3D reconstruction of up to four points per molecule. They demonstrate this on DNA nanostructures, streptavidin multimers, and a ligand-binding protein conformational change.
- **Visible evidence base** Main text descriptions, figure references (Figures 1–5, S1–S5), tables (S1, S2), and supplementary methods referenced but not provided
- **Missing materials affecting confidence** Full figures and figure legends, supplementary methods, Monte Carlo simulation details, machine learning implementation details, bootstrap analysis specifics, and raw data traces

## Reviewer
- **Overall assessment** The manuscript presents a conceptually appealing extension of single-molecule FRET methodology, with a clear potential to simplify multipoint distance measurements. The demonstrations on DNA nanostructures and streptavidin are plausible and internally consistent. However, the evidence as presented is insufficient to fully establish the method's general utility, particularly for protein conformational dynamics, and several technical details require clarification or additional validation.
- **Who would be interested in the results, and why** Researchers in single-molecule biophysics, structural biology, and molecular nanotechnology would find this method attractive for its potential to obtain multiple distance constraints from a single experiment without complex multi-color labeling. Those working on protein complexes and conformational dynamics may also be interested, though the protein demonstrations are less complete.
- **Major strengths** The stochastic exchange scheme is a clever and practical solution to the problem of measuring multiple distances with only two colors. The method's one-pot, rapid measurement format is a genuine practical advantage. The demonstration of 3D reconstruction from FRET-derived distances, including handling of degenerate peaks, is thoughtful and well-articulated.
- **Major Concerns**
  - R1-M1: The claim of "ab initio 3D profiling" is not fully supported by the evidence presented. The reconstruction appears to rely on known or assumed structural constraints (e.g., DNA nanostructure geometry, streptavidin symmetry), and the text does not clearly demonstrate a fully unguided reconstruction.
  - R1-M2: The protein conformational change demonstration (Gln PQ SBD2) is presented as a proof-of-concept, but the evidence is limited to two FRET values (0.31 to 0.45 and 0.31 to 0.34). This is a single-distance measurement, not a multipoint structural analysis, and does not demonstrate the method's core advantage.
  - R1-M3: The treatment of FRET value degeneracy and its impact on reconstruction uniqueness is underdeveloped. The text mentions that degenerate peaks complicate interpretation but does not provide a rigorous analysis of how many solutions are consistent with a given set of distances, nor how the method distinguishes between them.
  - R1-M4: The accuracy of the 3D reconstruction is not quantitatively assessed in the main text. The claim of "subangstrom accuracy" for the DNA helix fit is mentioned, but the metric, error analysis, and comparison to ground truth are not described in sufficient detail.
  - R1-M5: The method's applicability to proteins is asserted but not thoroughly validated. The text acknowledges that DNA conjugation may alter protein structure, but the control experiments to rule out such effects (e.g., activity assays, structural validation) are not described in the main text.
- **Minor Comments**
  - R1-m1: The abstract states "one-pot method" but the text later describes multiple experimental steps (labeling, immobilization, measurement). Clarify what "one-pot" refers to.
  - R1-m2: The Monte Carlo simulation is referenced but not described in the main text. A brief summary of the simulation parameters and validation would help the reader assess the optimization claims.
  - R1-m3: The machine learning classifier accuracy of 74% is presented without a baseline or chance level. Reporting the expected accuracy for random classification would strengthen this result.
  - R1-m4: The text mentions "weak binders" but does not define the binding affinity range or how it was tuned. This is critical for reproducibility.
  - R1-m5: The statement that iMAX FRET "can replace cumbersome biochemical assays" is speculative and not supported by the data presented.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria**  
  - Originality: The stochastic exchange scheme is a novel and creative approach to multipoint FRET, distinct from existing multi-color or sequential labeling methods.  
  - Scientific importance: If fully validated, the method could significantly streamline structural studies of biomolecules, particularly for dynamic systems. However, the current demonstrations are limited in scope and depth.  
  - Interdisciplinary readership: The method bridges single-molecule biophysics, structural biology, and nanotechnology, with potential appeal across these fields.  
  - Technical soundness: The core concept is sound, but several technical details (reconstruction uniqueness, accuracy metrics, protein validation) are insufficiently addressed.  
  - Readability for nonspecialists: The text is generally clear, but the reconstruction algorithm and degeneracy handling are described at a level that may be challenging for readers without a computational background.

## Risk / unsupported claims
- "Ab initio 3D profiling" is not fully demonstrated; reconstructions appear to rely on prior structural knowledge.
- The protein conformational change demonstration does not show multipoint analysis and is therefore not a full validation of the method's core claim.
- The claim of "subangstrom accuracy" is not substantiated with sufficient detail on the fitting procedure and error analysis.
- The assertion that iMAX FRET can replace biochemical assays for multimer characterization is speculative.
- The statement that iMAX FRET can be combined with AlphaFold for improved predictions is forward-looking but not demonstrated.